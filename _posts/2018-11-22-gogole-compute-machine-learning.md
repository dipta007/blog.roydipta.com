---  
toc: true  
layout: post  
title: চল গুগল থেকে ধার করা পিসি নিয়ে মেশিন লার্নিং করি 😃 😆  
description: আমরা অনেকেই এখন মেশিন লার্নিং অথবা ডিপ লার্নিং নিয়ে কাজ করি। কিন্তু আমরা সচরাচর যে প্রবলেমে পড়ি সেটা হল আমাদের পিসি নিয়ে। আমরা খুব হাই কনফিগারড পিসি ব্যবহার করি না যে...  
image: https://i.imgur.com/KqTxK2P.jpg  
date: 1018-11-22  
tags: [machine-learning, data-science, gcp]  
share: true  
featured: true  
---  
  
আমরা অনেকেই এখন মেশিন লার্নিং অথবা ডিপ লার্নিং নিয়ে কাজ করি। কিন্তু আমরা সচরাচর যে প্রবলেমে পড়ি সেটা হল আমাদের পিসি নিয়ে। আমরা খুব হাই কনফিগারড পিসি ব্যবহার করি না যে আমরা চাইলেই আমাদের মডেল রান করতে পারব। তো Google আমাদের জন্য খুব সুন্দর একটা ব্যবস্থা করে দিয়েছে। আমরা চাইলেই আমাদের মডেল গুগলে রান করতে পারি। এই জন্য আমাদের পর্যায়ক্রমে নিচের স্টেপ গুলা ফলো করতে হবে।  
  
### ১। গুগলে একাউন্ট ওপেন করতে হবে  
  
প্রথমত আমাদের গুগলে একটা একাউন্ট ওপেন করতে হবে। গুগল প্রতি নতুন একাউন্ট এর সাথে আমাদেরকে ৩০০ ডলার ফ্রি দেই। কিন্তু এখানে প্রবলেম হলে আমাদের একাউন্ট টা একটিভেট করার জন্য একটা ক্রেডিট কার্ড থাকতে হবে। তো আমরা এই লিঙ্কে যেয়ে [একাউন্ট](https://cloud.google.com/) একটিভেট করে নেই। *কার যদি অনেকগুলা ক্রেডিট কার্ড থাকে তাহলে সে চাইলে অনেক গুলা গুগল একাউন্ট খুলে প্রতি বার ৩০০$ ফ্রি পেতে পারে।*  
  
### ২। নতুন প্রজেক্ট ওপেন করা  
  
এখন আমাদের এই [লিঙ্কে](https://console.cloud.google.com/) যেতে হবে। এর পর নিচের চিহ্নিত যায়গায় ক্লিক করতে হবে।  
  
![](https://miro.medium.com/v2/resize:fit:700/1*cCwLi8ohSJNc74P8u_Jd2w.png)  
  
তাহলে আমাদের সামনে একটা ডায়ালগ বক্স আসবে। ঐ টায় আমাদের new project বাটনে ক্লিক করতে হবে। এর পর আমাদের প্রজেক্ট এর একটা নাম দিয়ে create project বাটনে ক্লিক করি। তাহলে আমাদের প্রজেক্ট ওপেন করা হয়ে গেল।  
  
### ৩। গুগল থেকে পিসি ধার নেওয়া  
  
এখন যেহুতু আমাদের প্রজেক্ট ওপেন হয়ে গিয়েছে, এখন আমাদের কাজ হল গুগল থেকে আমাদের মেশিন লার্নিং এর জন্য এক টা পিসি ধার নেওয়া। একে গুগল এর ভাষায় instance বলে। তো এর জন্য আমরা প্রথমে একদম বামে উপড়ে তিন দাগ দেওয়া বাটনে ক্লিক করব। ওই খান থেকে আমরা নিচের ছবি এর মত করে vm instances সিলেক্ট করব।  
  
![](https://miro.medium.com/v2/resize:fit:463/1*rZodQQa-9Xyo0rtyspdUQw.png)  
  
এর পরের পেজ থেকে আমরা create বাটনে ক্লিক করলে আমরা আমাদের ধার করা পিসি কনফিগার করার জন্য option পাব। নিচের ছবি এর মত করে আমারা আমাদের ধার করা পিসি কনফিগার করি। এইখানে কোন ফিল্ডে কি বলসে তা তোমরা নিজেরাই বুঝতে পারবে। এবার আস আমরা আমাদের সিপিউ (CPU) আর জিপিউ (GPU) কনফিগার করি। এর জন্য আমরা নিচের চিহ্নিত জায়গায় ক্লিক করব।  
  
![](https://miro.medium.com/v2/resize:fit:456/1*hWKFw_lfixyZj4oiML2OgQ.png)  
  
এখন আমাদের সামনে সিপিউ আর জিপিউ কনফিগার করার জন্য option পাব, এই খানে নিচের ১ নং চিহ্নিত জায়গা থেকে আমরা সিপিউ আর ২ নং চিহ্নিত জায়গা থেকে আমারা আমাদের জিপিউ কনফিগার করি।  
  
![](https://miro.medium.com/v2/resize:fit:448/1*7noU-DhSNlFTI88TNH6NoA.png)  
  
বর্তমানে জাস্ট দেখানর জন্য আমরা নিচের মত করে কনফিগার করলাম।  
  
![](https://miro.medium.com/v2/resize:fit:440/1*b9UWOEwhD0Dl-brv8VEVFQ.png)  
  
এর পর পালা আমাদের ওএস সিলেক্ট করার। এর জন্য আমরা নিচের চিহ্নিত জায়গাই ক্লিক করি। তাহলে আমরা আমাদের ওএস সিলেক্ট করার জন্য option পাব।  
  
![](https://miro.medium.com/v2/resize:fit:443/1*vqcn3pUaVOe8n6CNhjDcmg.png)  
  
এই খান থেকে আমরা এখন এর জন্য নিচের মত করে কনফিগার করে নেই।  
  
![](https://miro.medium.com/v2/resize:fit:481/1*qFLS_zuKOZFiLKSC5Ri1dw.png)  
  
নিচের মত করে আমাদের ফায়ারওয়াল সেটআপ করব।  
  
![](https://miro.medium.com/v2/resize:fit:460/1*m3TvepujCLIdnj6ygeiOsQ.png)  
  
সব কিছু সেটআপ করলে নিচের মত একটা কনফিগারেশন পাব আমরা।  
  
![](https://miro.medium.com/v2/resize:fit:700/1*1Zq29qDAFENhR2mcjQaFYw.png)  
  
উপরের ছবি এর চিহ্নিত অংশ থেকে আমরা দেখতে পাচ্ছি আমাদের এই instance এর জন্য monthly এবং hourly rate কত হবে। তো আমরা monthly rate দেখে ভয় পাব না, যেহুতু আমরা বেশিরভাগ সময় আমাদের instance stop করে রাখব। কিভাবে স্টপ করতে হয় তা আমি পরে দেখাচ্ছি।  
  
![](https://miro.medium.com/v2/resize:fit:700/1*epG2reJXJ0Hll8bhzCcdwA.png)  
  
উপড়ের ছবি এর মত সবুজ টিক চিহ্ন আসলে আমরা বুঝতে পারব যে আমাদের কাজ সম্পূর্ণ হয়েছে।  
  
### ৩। আইপি ফিক্সড করা  
  
এবার আমাদের কে এই ধার করা পিসি এর আইপি ফিক্সড করতে হবে, যেন এটা কিছুক্ষণ পর পর চেঞ্জ না হয়। এর জন্য আমাদের নিচের ছবি এর মত করে একটার পর একটা স্টেপ করতে হবে।  
  
![](https://miro.medium.com/v2/resize:fit:438/1*HcW3l9NDiLndn9E0g7mHLA.png)  
  
এর পর আমরা আমাদের আইপি চেঞ্জ করে static করে দিব নিচের ছবি এর মত করে।  
  
![](https://miro.medium.com/v2/resize:fit:700/1*M3boRiOVyvkN3KFBCsi21g.png)  
  
### ৪। ফায়ারওয়াল সেটিং ঠিক করা  
  
এখন আমাদের ফায়ারওয়াল সেটিং ঠিক করতে হবে যেন আমরা যেকোন জায়গা থেকে আমাদের নোটবুককে access করতে পারি। এর জন্য প্রথমে আমাদের নিচের ছবি এর মত করে Firewall rules এ যেতে হবে।  
  
![](https://miro.medium.com/v2/resize:fit:439/1*3fcSxVcp7y4ZCbSRppu6bw.png)  
  
তারপর create firewall rules বাটনে ক্লিক করব। তারপর নিচের ছবি এর মত করে ২ টা ফিল্ড চেঞ্জ করে ফায়ারওয়াল রুল তৈরি করব।  
  
![](https://miro.medium.com/v2/resize:fit:484/1*3iFnj8kchPQC3nOGGUi0IA.png)  
  
এই ২টা ফিল্ড দিয়ে মেইনলি আমরা যেকোন জায়গা থেকে access করার পার্মিশন দিলাম, এবং পরের টা দিয়ে কোন পোর্ট টা ওপেন থাকবে তা বলে দিলাম। এই পোর্ট নাম্বার টা পরে এক জায়গায় দিতে হবে। সো এটা মনে রাইখ।  
  
### ৫। আমাদের ধার করা পিসি ওপেন করা 😃  
  
আমাদের পিসি এর নাম এর পাশে নিচের ছবি এর মত করে সবুজ টিক চিহ্ন দেখা মানেই আমাদের পিসি ঠিক মত কনফিগার করা হয়েছ এবং এটা এখন ওপেন আছে। এখন আমরা এর পাশের ssh বাটনে ক্লিক করে আমাদের পিসি ওপেন করি  
  
![](https://miro.medium.com/v2/resize:fit:686/1*xrFkV3qHmkBRmljCScnYtw.png)  
  
এখন আমাদের কাজ হল আমাদের এই পিসি তে jupyter notebook এবং আর দরকারি লাইব্রেরী ইন্সটল করা। আমাদের instance ওপেন হলে একটা কমান্ড লাইন এর মত স্ক্রীন পাব। ঐ খানে আমরা নিচের কমান্ড গুলো রান করব। মেইনলি আমরা নিচের কমান্ড গুলো দিয়ে anaconda ইন্সটল করতেসি। anaconda হল এমন একটা লাইব্রেরী যেটা এর মধ্যে মেশিন লার্নিং এর অনেক লাইব্রেরী ইনক্লুড করা আছে।  
  
```bash  
wget [http://repo.continuum.io/archive/Anaconda3-4.0.0-Linux-x86_64.sh](http://repo.continuum.io/archive/Anaconda3-4.0.0-Linux-x86_64.sh)  
bash Anaconda3-4.0.0-Linux-x86_64.sh  
```  
      
  
যদি এই কমান্ড রান করার পর কোন option এ ইয়েস দিতে বলে তাহলে ওই খানে আমরা yes দিয়ে আমাদের সম্মতি জানাব। তাহলে আমাদের পিসিতে anaconda ইন্সটল হয়ে গেল। এখন আমাদের কাজ হল anconda রান করা। এর জন্য আমরা নিচের কমান্ডটি রান করব।  
  
```bash  
source ~/.bashrc  
```  
  
### ৬। জুপিটার নোটবুক কনফিগার করা  
  
এখন তো আমরা আমাদের পিসি কনফিগার করে ফেলসি এবং আমাদের নোটবুক ও ইন্সটল করে ফেলেছি। এখন আমরা আমাদের নোটবুককে কনফিগার করব যাতে আমরা নোটবুককে আমাদের নিজেদের পিসি থেকে access করতে পারি। এর জন্য আমাদের আগে জুপিটার নোটবুক কনফিগারেশন ফাইল তৈরি করতে হবে। এর জন্য আমরা নিচের কমান্ডটা রান করি।  
  
```bash  
jupyter notebook --generate-config  
```  
  
এখন আমাদের কনফিগারেশন ফাইলে কিছু চেঞ্জ করতে হবে। এর জন্য আমরা উবুন্টু এর nano কমান্ড এর হেল্প নিতে পারি। এর জন্য আমরা নিচের কমান্ড টা রান করব।  
  
```bash  
sudo nano ~/.jupyter/jupyter_notebook_config.py  
```  
  
তাহলে আমরা নিচের ছবি এর মত করে একটা কমান্ড লাইন পাব।  
  
![](https://miro.medium.com/v2/resize:fit:683/1*NmhkrLUpcJobdhg3Xqf7LA.png)  
  
ওই খানে আমারা নিচের কিছু লাইন এড করব যাতে করে আমরা বাইরে থেকে নোটবুককে access করতে পারি। নিচে এর জায়গায় নিজের পছন্দ মত port number দিবা। আমি নরমালী এখানে ৫০০০ দেই। উপড়ের ছবি তে দেখা যাচ্ছে যে আমারটায় এই লাইন গুলা এড করা আছে ।  
  
```python  
c = get_config()  
c.NotebookApp.ip = '*'  
c.NotebookApp.open_browser = False  
c.NotebookApp.port = <Port Number>  
```  
  
### ৭। জুপিটার নোটবুক চালু করব 😅 😅  
  
এখন আমাদের লাস্ট স্টেপ হল জুপিটার নোটবুক চালু করা। এর জন্য আমরা নিচের কমান্ড টা রান করব।  
  
```bash  
jupyter-notebook --no-browser --port=<PORT-NUMBER>  
```  
  
এখন আমাদের পিসি এর browser ওপেন করে ওই খান থেকে নিচের লিঙ্কে ঢুকলেই আমরা আমাদের নোটবুক ব্যবহার করতে পারব।  
  
```  
http://<External Static IP Address>:<Port Number>  
```  
  
এখানে External Static Ip Address হল আমাদের ধার করা পিসি এর আইপি এড্রেস, এবং port number হল আমরা লাস্ট স্টেপে যে port number দিয়েছিলাম ওইটা।  
  
যদি আমরা নিচের মত কোন স্ক্রিন দেখতে পারি তাহলেই আমরা বুঝব যে আমরা সফল ভাবে আমাদের জুপিটার নোটবুক ইন্সটল করতে পেরেছি।  
  
> ***আমরা সব সময় আমাদের কাজ শেষ হলে নিচের ছবি এর লাল চিহ্নিত জায়গা থেকে আমাদের instance স্টপ করে রাখব। নয়ত গুগল আমাদের থেকে প্রতি ঘণ্টায় টাকা নিতে থাকবে।***  
  
![](https://miro.medium.com/v2/resize:fit:700/1*TiMCeoU4gHGhNk7743Ckng.png)  
### যদি চাই জিপিউ এর পূর্ণ ব্যবহারঃ  
  
কিন্তু আমরা যে এত কষ্ট করে যে জিপিউ নিলাম তা কিন্তু আমরা চাইলেই ব্যবহার করতে পারব না। এর জন্য আগে আমাদের কে উবুন্টু কনফিগার করে নিতে হবে, গ্রাফিক্স ড্রাইভার ইন্সটল করতে হবে। এটা নিয়ে পরে কোন এক পর্বে আলোচনা করব। যদি কার খুব দরকার হয় সে চাইলে নিচের কোড গুলা পর্যায়ক্রমে রান করে কনফিগার করে নিতে পারে। তবে নিচের কোড কিন্তু শুধুমাত্র ubuntu 16.04 এবং tensorflow-gpu এর জন্য কাজ করবে। অন্য কোন ভার্শন অথবা লাইব্রেরী এর জন্য এটা ব্যবহার করা যাবে না।  
  
```bash  
sudo apt-get update  
sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub  
wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.1.85-1_amd64.deb  
sudo apt install ./cuda-repo-ubuntu1604_9.1.85-1_amd64.deb  
  
wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/nvidia-machine-learning-repo-ubuntu1604_1.0.0-1_amd64.deb  
sudo apt install ./nvidia-machine-learning-repo-ubuntu1604_1.0.0-1_amd64.deb  
  
sudo apt update  
sudo apt-get update  
sudo apt install cuda9.0 cuda-cublas-9-0 cuda-cufft-9-0 cuda-curand-9-0 \  
	cuda-cusolver-9-0 cuda-cusparse-9-0 libcudnn7=7.2.1.38-1+cuda9.0 \  
	libnccl2=2.2.13-1+cuda9.0 cuda-command-line-tools-9-0  
  
sudo apt-get update  
sudo apt update  
sudo apt install libnvinfer4=4.1.2-1+cuda9.0  
  
sudo add-apt-repository ppa:graphics-drivers/ppa  
  
sudo apt update  
sudo apt install nvidia-390  
  
sudo apt-get -y install python3-pip  
pip3 install --upgrade tensorflow-gpu  
  
nvidia-smi  
  
  
# Check if GPU available  
python3  
from tensorflow.python.client import device_lib  
print(device_lib.list_local_devices())  
```  
  
উপড়ের কোন কিছুতে সমস্যা পেলে অথবা কোন কাজ না করতে পারলে প্লিজ কমেন্ট এর মাধ্যমে জানাবেন।  
