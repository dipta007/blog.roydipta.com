---  
layout: post  
title: LightOJ Code Downloader  
description: Download all codes by one code...  
image: https://i.imgur.com/GTgpe1G.jpg  
date: 2018-11-19  
tags: [competitive-programming, programming, lightoj]  
share: true  
---  
  
[here]({% link _posts/2018-11-18-SPOJ-code-downloader.md %}). Today I have developed another script to download all of your accepted solutions from **LightOJ**. It will download all of yours accepted solutions using crawling. The features of the script are —  
  
1. Download all of your accepted codes on LightOJ.  
2. If there are multiple submission for a single problem, then it downloads all.  
3. The file name architecture will be ProblemId-ProblemName-SubmissionId  
4. File extensions will be cpp for C++ programs, c for C programs and java for JAVA programs.  
5. If you download now and later solve more problems, then if you execute the script in the same place, it wont download the previous codes. The submission ids will be saved on a text file name “downloaded” on the same folder.  
  
You can find the script in this [link](https://github.com/dipta007/lightoj-code-downloader), all the instructions to run the script are given there.  
  
If you find any bugs or problems regarding the script or want new features, just comment here or open an issue on [Github](https://github.com/dipta007/lightoj-code-downloader/issues). I will try to response as soon as possible.  
