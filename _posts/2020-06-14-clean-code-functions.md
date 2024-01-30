---  
layout: post  
title: Clean Code - Functions  
description: Clean functions are the first line of organization in any program...  
image: https://i.imgur.com/KyMggLl.jpg  
date: 2020-06-14  
tags: [clean-coding, programming]  
share: true  
featured: true  
---  
  
Hello coders, so today, you want to learn something that will help you and your colleagues. It is the second part of a long series. You can find the first part [here]({% link _posts/2020-06-16-clean-code-naming.md %}). So let's jump in and learn to code clean functions 🙏  
  
### Small  
The first rule of the function is that they should be small. How small should they be? There is no hard and fast number for this. But as [Uncle Bob](https://en.wikipedia.org/wiki/Robert_C._Martin) suggests, it should hardly ever be 20 lines long.  
  
### Do One Thing  
> Functions should do one thing.  
> They should do it well.  
> They should do it only.  
  
A function should perform just one responsibility. How can we understand if the function is performing more than one responsibility? If the function is doing the steps that are **just one step** below the stated name of the function, then the function is doing one thing. Otherwise, the function needs some refactoring.  
  
### The Step-Down Rule  
  
Functions should be a chapter or passage of a non-fiction book. You can read the story just by going from the start to the end of the function. The story must have just one work to do: **maintaining the Single Responsibility Rule**.  
  
### Avoid Switch Statement  
  
The switch statement is ugly. Even a switch statement only with 2 cases is longer than 10 lines. Moreover, Switch cases perform N responsibilities by its design. They should be avoided as long as possible. But there are some cases, where we can't. In that case, bury the switch case to a lower level class and never repeat it.  
  
### Use Descriptive Names  
  
Again, naming is the most necessary thing for writing clean codes. Developers will read your code by names of variables, functions, classes, methods, and interfaces. The name should sound like a story, not something enigmatic. A long descriptive name is better than an enigmatic name. Spend time on choosing a name, even sometimes more than writing the function. By design, function names should be a **Verb**.  
  
### Function Arguments  
  
The ideal number of arguments for a function is **Zero**. Next comes **One**, followed closely by **Two**. Three arguments should be avoided where possible. More than three is intolerable. In most cases, they can be extracted into a class.  
  
**Avoid output arguments**  
By habit, we are used to the idea that a function will take some inputs and return outputs. So, don't call functions by output arguments. Instead, use the return value to replace the argument.  
  
```python  
# Ugly code  
def call(arr):  
  arr.append(1)  
  
call(arr)  
  
# Clean Code  
def call(arr):  
  arr.append(1)  
  return arr  
  
arr = call(arr)  
```  
  
**Common Forms of One Argument Functions**  
There are three common forms of one argument function -  
  
1. **Ask Question**: A function can ask questions about the input argument. `file_exists = file_exists('myfile')` - this simple function checks if the file named `myfile` exists or not and returns a boolean value.  
2. **Transform & Return**: A function can transform the input argument and return it.  
3. **Event**: A function can change the state of the program by the value of the input argument.  
  
Try to avoid any one argument function that doesn't follow the above pattern. Most likely, you are doing it wrong, or you have given birth to another pattern. But who wants a new pattern? We already have a lot of patterns to learn 🤯  
  
**Avoid Flag Arguments**  
Avoid flag arguments. By design, they are doing more than one thing. If the flag is true, then run a block. Otherwise, another. Extract the function into two different functions and call them.  
  
**Two Argument Functions**  
Two argument functions are harder to interpret than the one argument ones. But there are sometimes, where we can't ignore two argument functions. One example can be the cartesian point function. They should have two arguments by their design (x, y). Even we will be surprised to see a cartesian point with one argument.  
  
Again, it's difficult to interpret the ordering in two argument functions. Like `assert(expected, actual)` - every time, I had to check if the expected was the first argument or the second.  
  
Two argument functions are not evil. Just use them when it's necessary and arguments have a natural cohesion and order.  
  
**Three Argument Functions**  
The issues of ordering and cohesion that we described in the two argument functions is doubled here. So we have to avoid them as far as possible and meticulously think before using them.  
  
**Argument Objects**  
When the function requires three or more arguments, most of the cases they can be extracted into a class of their own.  
  
```python  
# Ugly Code  
add_address(road, block, city, state, country)  
  
# Clean Code  
add_address(address: Address)  
```  
  
**Argument Lists**  
Sometimes function can take a variable number of arguments. Consider the `print` function of Python. It can take a variable number of arguments to print. But even in this case, all the rules should be followed as stated before.  
  
```python  
def one_argument(*args):  
  pass  
  
def two_arguemnts(name, *args):  
  pass  
    
def three_arguments(name, count, *args):  
  pass  
```  
  
### No Side Effects  
  
Again, a function should only have a responsibility to fulfill. There should be no hidden changes that the function name doesn't suggest.  
  
```python  
def check_password(username, password):  
  user = user_model.find_by_username(username)  
  if user.password != password:  
	user.increase_wrong_attempt() # Side Effect  
	return False  
  return True  
```  
  
On the example, the function should only check the password and return a boolean value. But it's increasing the number of wrong attempts, which is a side effect. There are some cases, where maybe we don't want to increase the number of wrong attempts. Maybe we just want to check the password to validate the permission. The side effect creates **temporal coupling**.  
  
### Command Query Separation  
  
A function should either ask something or do something, but not both. This creates confusion for your colleagues and your future self.  
  
```python  
# Ugly Code  
def set(var, val):  
  if var not in mp:  
	return False  
  mp[var] = val  
  return True  
  
if set(count, 1):  
  pass  
  
# Clean Code  
def check(var):  
  return var in mp  
  
def set(var, val):  
  mp[var] = val  
    
if check(count):  
  set(count, 1)  
```  
  
### Prefer Exceptions to Returning Error Codes  
  
Returning error codes are a clear violation of our last rule - Command Query Separation. Instead, we should use try-catch and throw to handle errors.  
  
### Extract Try Catch  
  
Try catch block should be extracted to the lower level of functions than the higher level.  
  
### Don't Repeat Yourself (DRY)  
  
You never should repeat the same code. If you need to change the logic anywhere, you need to find all the places and change the logic everywhere.  
  
There is a nice rule to maintain DRY -  
  
1. If this is the first time, code it  
2. If this is the second time, copy it  
3. If this is the third time, extract it (to function or class)  
  
## How to Write Clean Functions  
  
There are a lot of rules to maintain, and it's hard to think about those with the business logic implementation. And nobody can maintain all of them in their first try to write a function. Functions are like writing a story. There is a first draft, second draft ... third draft, and finally, the Final Version. **Final Version** So don't be afraid to write messy long functions. When it works (pass all tests), refine it, refactor it until it sounds like a [Harry Potter](https://en.wikipedia.org/wiki/Harry_Potter) book.  
