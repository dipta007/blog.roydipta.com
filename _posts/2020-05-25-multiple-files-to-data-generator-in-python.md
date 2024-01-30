---  
layout: post  
title: Multiple Files To Data Generator - Less RAM, Fast Training  
description: In the current era of Deep Learning, Data is the biggest problem. If the data size is small, then it's obviously a big problem...  
image: https://i.imgur.com/LKmuYnL.jpg  
date: 2020-05-25  
tags: [data-science, python, programming]  
share: true  
---  
  
In the current era of Deep Learning, Data is the biggest problem. If the data size is small, then it's obviously a big problem for training a Deep Neural Network. Even if the data size is huge, then it's also a big problem for the people who don't have enough resources.  
  
The problem that comes with a huge amount of data is that there are not enough resources to load the data into memory. Most of us train our models in Colab and colab only gives us 12 GB of memory initially (Sometimes 25/35 GB). Recently I have faced the same kind of problem, where just only loading the half amount of data was crashing my runtime. Most of us know the obvious solution -  
  
> Use a Python Generator  
  
Python generator is a function that does not load the whole input into the memory. It takes only the amount of data that we need for that moment. Like for deep learning, we do not need the whole data on a single moment. We need the `batch_size` amount of data at a particular time. So it actually returns an iterator, which gives the data as we need.  
  
Think that, you have a `CSV` file which is 80 GB in size, so you can't load the whole dataset into the memory. In python, we have a [csv](https://docs.python.org/3/library/csv.html) lib, which can open the CSV file and read line by line. We will use that to make our generator  
  
```python  
import csv  
  
def data_generator():  
  with open('nlp.csv') as fp:  
	reader = csv.reader(fp)  
	for row in reader:  
	yield row  
  
for row in data_generator():  
  print(row)  
```  
  
This code block will print each row of the CSV file. But unlike our traditional method, it won't load the whole data into memory. It will read line by line and throw us that line for our usage.  
  
I know some people are bored as F⭐️⭐️K. Everyone knows about python generator. But thats not the blog is all about. The above solution works for a single file. But what will you do when you have 3/4/**n** CSV files?  
  
> Use a Python Generator Again 😅  
  
That was the problem I faced earlier. So by my little python experience, I have implemented 1/2/3 function(s) which I will share with you today.  
  
```python  
def get_all(*args, chunksize):  
  pds = []  
  args = args[0]  
  for arg in args:  
	pds.append(pd.read_csv(f'{BASE_PATH}/{arg}', chunksize=chunksize))  
  return pds  
    
def merge_all(*args):  
  merged = None  
  args = args[0]  
  for arg in args:  
	if merged is None:  
	  tmp = arg  
	else:  
	  merged = pd.merge(tmp, arg, how='inner', on=['protein', 'index'])  
  return merged  
  
def data_generator():  
  total_row = NUMBER_OF_ROWS  
  files = [  
	'a.csv',  
	'b.csv',  
	'c.csv',  
	'd.csv',  
  ]  
  
  pds = get_all(files, chunksize=batch_size)  
  cnt = 0  
  
  while True:  
	data_frames = []  
	for reader in pds:  
	  data_frames.append(reader.get_chunk())  
  
	cnt += batch_size  
	  
	merged = merge_all(data_frames)  
	x = merged.iloc[:, 1:].to_numpy()  
	y = merged.iloc[:, 0].to_numpy()  
  
	if cnt >= total_row:  
	  pds = get_all(files, chunksize=batch_size)  
	  cnt = 0  
  
	yield x, y  
```  
  
This was the code I used on my recent research to merge all the 4 files (total 47 GB) and get only the `batch_size` of data (16, 32, 64, 128, ...). Don't be overwhelmed by the size of the code. I will explain it step by step.  
  
```python  
def get_all(*args, chunksize):  
  pds = []  
  args = args[0]  
  for arg in args:  
	pds.append(pd.read_csv(f'{BASE_PATH}/{arg}', chunksize=chunksize))  
  return pds  
```  
  
On this part of the code, I have passed all the file names as the parameter and the `batch_size`. I have used pandas (`pd`) to read CSV, but unlike the traditional way we passed the `chunksize` parameter on `read_csv`. It will then return a reader object instead of a dataframe. We have appended all the reader objects in a list and return that. We will use it in later parts of our code.  
  
```python  
def merge_all(*args):  
  tmp = None  
  args = args[0]  
  for arg in args:  
	if tmp is None:  
	  tmp = arg  
	else:  
	  tmp = pd.merge(tmp, arg, how='inner', on=['id'])  
  return tmp  
```  
  
On this part, all the dataframe objects were sent. And for my case, I had to merge all the dataframe objects on a single dataframe, using the `id` as the primary value. Pandas already has a built-in function for that `pd.merge`. On this function you need to send the left and right dataframe, the join type and the variable(s) which need(s) to be used as the primary variable(s).  
  
```python  
def data_generator():  
  total_row = NUMBER_OF_ROWS  
  files = [  
	'a.csv',  
	'b.csv',  
	'c.csv',  
	'd.csv',  
  ]  
  
  pds = get_all(files, chunksize=batch_size)  
  cnt = 0  
  
  while True:  
	data_frames = []  
	for reader in pds:  
	  data_frames.append(reader.get_chunk())  
  
	cnt += batch_size  
	  
	merged = merge_all(data_frames)  
	x = merged.iloc[:, 1:].to_numpy()  
	y = merged.iloc[:, 0].to_numpy()  
  
	if cnt >= total_row:  
	  pds = get_all(files, chunksize=batch_size)  
	  cnt = 0  
  
	yield x, y  
```  
  
Now this is the main generator function, which I had used on my model fit function. At first, I used the `get_all` function to get all the readers. Now the function will run for an infinite time. How much data it needs will be dependent on the model, not on the amount of dataset or the generator function. So it will run for infinite time and circularly serve the data.  
  
`reader.get_chunk()` will return the dataframe of `chunksize`. We have got all the chunks from all the reader objects and merged them using our previous `merge_all` function. Then I have separated the values and target and return them using the `yield` keyword on the end of the code.  
  
```python  
cnt += batch_size  
  
if cnt >= total_row:  
  pds = get_all(files, chunksize=batch_size)  
  cnt = 0  
```  
  
Now, what have I done with this part of the code? In a deep learning model, it does not train on the data for just one time. It reads the data repeatedly, traditionally once per epoch. If we use the data from a numpy array, it manages the data repetition on its own. But now, as we are using a generator, we have to handle it manually. So by the 1st line, I am tracking the number of data I have read already, and on the if condition, I checked if I have reached the end of the data. If yes, then I just get all the reader objects again and reset `cnt` to 0. So it will start to serve me data from the start of the file again.  
  
I suffered a lot on this topic and came up with this solution after a lot of Google searches 🤯 🤣. I hope this blog will save some of your time and internet bandwidth. 🤣  
