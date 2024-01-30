---  
layout: post  
title: Clean Code - Naming  
description: Hello Dirty Coders (including ME, aren't we all? 🤔), welcome to the 1st part of Clean Code Series. This series will be highly inspired...  
image:   
date: 2020-06-16  
tags: [clean-coding, programming]  
share: true  
---  
  
Hello Dirty Coders (including ME, aren't we all? 🤔), welcome to the 1st part of Clean Code Series. This series will be highly inspired by and sometimes embarrassingly copied from the [**Clean Code**](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/ref=sr_1_2?dchild=1&amp;keywords=clean+code&amp;qid=1592311719&amp;sr=8-2) book by **Uncle Bob** (Robert C. Martin). I highly recommend reading the book. This series is nowhere near to the original book.  
  
The book has a lot of code examples and most of them are provided on Java. I will not go through all the code examples, but if I do, I will translate or make examples using Python.  
  
## What is Clean Code?  
  
The clean code should have -  
  
- Full test coverage  
- Complete error handling  
- No duplications  
- High expressiveness  
- A minimal number of entities such as class, function, methods and ...  
- Performance close to optimal  
- Minimal dependencies on 3rd parties  
  
## Meaningful Names  
  
Name is the smallest building block of a code. Name is everywhere. Function, class, file, component, container all have names. It is also the basic building block of clean code. There are some hard and fast rules to give a good name.  
  
### Use Intention Revealing Names  
  
A good name should answer only 3 questions  
  
1. Why it exists  
2. What it does  
3. How it is used  
  
I know it sounds simple, but it takes much time to get a good name, but it will save more than that in the long run.  
  
A name should not have comments to express its intentions. Look at this example -  
  
```python  
# Dirty Code  
d = 100 # elapsed time in days  
  
  
# Clean Code  
elapsed_time_in_days = 100  
```  
  
In the first case, you need to go through the comment. It is okay for one time. But whenever you will use the variable `d`, you have to come to the initialization to get the intention of the variable. But on the 2nd case, `elapsed_time_in_days` is expressive on its own.  
  
Don't give your variable one letter name. One letter name is never expressive. They fail to reveal their intention. There are some exceptions like `i`, `j`, `k` on the for loop. Though never use small letter l (el), capital letter I (eye), capital letter O (o) as a name because they tend to confuse the programmers with one and zero respectively.  
  
### Avoid Disinformation  
  
1. Avoid names that are platform-specific like `htop`, `hp`  
2. Don't use names with a small changes like `dataset_generator_for_cat_with_user_mobile_1`, `dataset_generator_for_cat_with_user_mobile_2`. In this case, you don't get the difference until the last letter and most of the time, we will ignore that difference.  
  
### Make Meaningful Distinctions  
  
There should be enough distinctions in the variable naming. Just don't append a number as you have a variable with the same name in the scope. `a1`, `a2` is the opposite of intention revealing.  
  
Don't use names with similar meaning. Like `product_data` and `product_info` do not have proper distinction. Just by looking at the name, you can't assume the intentions of these two variables. These are called noise words. `a`, `an`, `the` are some of the other noise words  
  
Don't append variable type to the variable name. Make the variable name so much expressive, that only by the name you can assume the type uniquely. Like `account_name` can never be a floating-point number. It must and should be a string. There are some exceptions like `id`, it can be a string or a number. But that convention should be followed all over the project. So the programmer working on that project will know if the `id` is a number or a string or something else 🤷🏻‍♂️.  
  
### Use Pronounceable Names  
  
> If you can't pronounce it, you can't discuss it without sounding like an idiot.  
  
Sometimes a short example is better than a lot of texts  
  
```python  
# Poor Name  
gen_ymdhms = "1591442356268" # Generation year, month, date, hour, min, sec  
  
  
# Good Name  
genration_timestamp = "1591442356268"  
```  
  
### Use Searchable Names  
  
Avoid using one letter name as much as possible. If you need to use it, only use it on a local scope rather than a global scope.  
  
Avoid using common words like `sum`, `temp`, `flag`, as they seem to be used by a lot of methods and classes and thus not a search-friendly name.  
  
### Avoid Encodings  
  
Avoid using encodings like **Hungarian Notation** or **Member Prefixes**. They were used before when the IDE was not as smart as it is now. Current IDEs are smarter enough to give us suggestions about the type or the member variable of a class. We don't want to clutter our brains with some more information.  
  
On the other hand, language-specific encodings should be maintained throughout the project. Like [snake_case](snake_case) in python and [camelCase](camelCase) in javascript.  
  
### Avoid Mental Mapping  
  
Programmers indeed are really smart (including Me 😇). But code is not a place to show off your smartness. You can obviously remember that `r` is the variable name for an URL with the host and scheme removed. But the person who will be reading your codes would not know that mental mapping. Use names that properly express the intention of that variable.  
  
### Class Name  
  
Class name should be a **Noun** or **Noun phase**. By design, classes are an encapsulation of the same type methods and variables, thus they should have a common name. Classes should not be a verb in any way.  
  
### Function/Method Name  
  
Functions should be **Verb** or **Verb phase**. By design, a function should have only one responsibility to be done. So if the name is anything other than verb, then either you are naming it wrong or there are some problems in the architecture level.  
  
### Pick One Word Per Concept  
  
Avoid using different similar words to define the same concepts. Like, don't use `fetch`, `get` and `retrieve` in the same project for the same responsibility.  
  
### Don't Use Same Word For Different Concepts  
  
Avoid using same word for totally different concepts. When you are intending to follow the previous rule, you will end up with a lot of variables with the same name. Like `add` is used throughout the project to add or concatenating two existing values. But if we use it to append a new value to an existing variable, it would be confusing. `append` seems a more reasonable name for this method.  
  
### Use Solution Domain Names  
  
The code will be read and maintained by the programmers. So it's okay to use solution domain names. Like in the Machine Learning context, `data_generator` is a good name and whoever sees this name will know that it is a data generator which is an iterator to loop on.  
  
### Use Problem Domain Name  
  
If there are no Solution domain names available, then use a domain-specific name. In that case, the programmer can ask a domain expert to know the meaning.  
  
### Add Meaningful Context  
  
As a programmer, our first duty is to choose the names as expressive as it can be. But sometimes, it is not possible to give context on a variable name. In that case, first try to enclose the variables in a meaningful class or function, like `name`, `city`, `district` should be enclosed in a class name `Address`. If it's not possible at all, prefix the variable with the name of the context. But remember it is the last resort. So use it after meticulous thinking.  
  
---  
  
I know that's a lot of Dos And Don'ts for a simple thing (***Naming***). But trust me in my past years, that is the toughest problem I faced in my *small* Software Engineering career.  
