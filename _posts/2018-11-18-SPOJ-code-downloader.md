---  
layout: post  
title: SPOJ Code Downloader  
description: Those who have done or doing competitive programming, is somehow familiar with SPOJ online judge...  
image: https://i.imgur.com/lfwR9e9.jpg  
date: 2018-11-18  
tags: [programming, competitive-programming]  
share: true  
---  
  
Those who have done or doing competitive programming, is somehow familiar with SPOJ online judge. Some of the people have solved a lot of problems there. But there are many people who have not started in a structured way or somehow lost all of their accepted codes. But there is a special feature in SPOJ, that we can see or download all of our accepted solutions from our submission page. But it will be really cumbersome to download them manually.  
  
So here is I am to rescue. I have developed a python script to download all of your accepted codes in a structured way. The features of the script are —  
  
1. Download all of your accepted codes on SPOJ.  
2. If there are multiple submission for a single problem, then it downloads all.  
3. The file name architecture will be “problemName_submissionId”  
4. File extensions will be cpp for c++ programs, others are on development.  
5. If you have downloaded now and later solve more problems, then if you execute the script in the same place, it wont download the previous codes. The submission ids will be saved on a text file name “downloaded” on the same folder.  
  
You can find the script in this [link](https://github.com/dipta007/spoj-code-downloader), all the instructions to run the script are given there.  
  
I have also developed another script to download Codeforces code, but recently found some bugs in it. I will repost after solving the bugs.  
  
If you find any bugs or problems regarding the script or want new features, just comment here or open an issue on [Github](https://github.com/dipta007/spoj-code-downloader/issues). I will try to response as soon as possible.  
      
  
[LightOJ-code-downloader]({% link _posts/2018-11-19-LightOJ-code-downloader.md %})  
[How-I-Cracked-170-170-On-GRE-Quant-In-Just-37-Days > How to Practice]({% link _posts/2020-05-21-How-I-Cracked-170-170-On-GRE-Quant-In-Just-37-Days.md %}#how-to-practice)