---
layout:     post
title:      Anaconda安装pytorch&tensorflower
subtitle:   Python--env
date:       2020-02-15
author:     HT
header-img: img/post-bg-conda.jpg
catalog: true
tags:
    - Python
---

tensorflow与pytorch都是机器学习常用的工具，本文用anaconda为tensorflow与pytorch创建两个环境
<hr/>
# 0.准备
首先需要有安装过anaconda，并且会使用anaconda，可以参考https://www.jianshu.com/p/3ab52e7d96f9
其次如果需要使用gpu版本的tensorflow或者pytorch，需要先安装CUDA，某些电脑的显卡并不支持cuda，可以去英伟达官网看看，我是很早之前装的，步骤也都忘了。如果显卡不支持cuda就只能装cpu版本了
<hr/>
# 安装tensorflow
<hr/>
## 1.查看版本
我安装的cuda版本是9.0，在tensorflow官网https://tensorflow.google.cn/install/source_windows上查看对应的版本号，选择安装1.13版本。cuda9.2版本可以安装tensorflow-gpu1.14和1.15版
![version](https://upload-images.jianshu.io/upload_images/21104637-605e42a5d2ce2e84.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如果安装的cuda版本是10.0以上的，可以安装新版本>2.0.0
![version_new](https://upload-images.jianshu.io/upload_images/21104637-e3000c661b65aef4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
没有cuda，可以安装cpu版本
注意：不同版本tensorflow对于python版本有要求，我选择的1.13版要求python为3.5-3.6，由于python3.6在安装时出了问题，保守起见选择python3.5
<hr/>
## 2.创建环境
```
(my_env) C:\Users\dell>conda create -n tensorflow_2 python=3.5
```
可以使用命令查看环境
```
conda info --envs
```
激活环境
```
(my_env) C:\Users\dell>conda activate tensorflow_2
(tensorflow_2) C:\Users\dell>
```
安装gpu版本的tensorflow
```
(tensorflow_2) C:\Users\dell>conda install tensorflow-gpu=1.13
```
也可使用pip安装
```
(tensorflow_2) C:\Users\dell>pip install tensorflow-gpu==1.13.1
```
查看列表安装完成
```
(tensorflow_2) C:\Users\dell>conda list
#  packages in environment at C:\Users\dell\Anaconda3\envs\tensorflow_2:
# 
#  Name                    Version                   Build  Channel
absl-py                   0.9.0                    pypi_0    pypi
astor                     0.8.1                    pypi_0    pypi
certifi                   2016.2.28                py35_0    https://mirrors.ustc.edu.cn/anaconda/pkgs/free
gast                      0.3.3                    pypi_0    pypi
grpcio                    1.27.2                   pypi_0    pypi
h5py                      2.10.0                   pypi_0    pypi
keras-applications        1.0.8                    pypi_0    pypi
keras-preprocessing       1.1.0                    pypi_0    pypi
markdown                  3.2.1                    pypi_0    pypi
mock                      3.0.5                    pypi_0    pypi
numpy                     1.18.1                   pypi_0    pypi
pip                       9.0.1                    py35_1    https://mirrors.ustc.edu.cn/anaconda/pkgs/free
protobuf                  3.11.3                   pypi_0    pypi
python                    3.5.4                         0    https://mirrors.ustc.edu.cn/anaconda/pkgs/free
setuptools                36.4.0                   py35_1    https://mirrors.ustc.edu.cn/anaconda/pkgs/free
six                       1.14.0                   pypi_0    pypi
tensorboard               1.13.1                   pypi_0    pypi
tensorflow                1.13.1                   pypi_0    pypi
tensorflow-estimator      1.13.0                   pypi_0    pypi
termcolor                 1.1.0                    pypi_0    pypi
vc                        14                            0    https://mirrors.ustc.edu.cn/anaconda/pkgs/free
vs2015_runtime            14.0.25420                    0    https://mirrors.ustc.edu.cn/anaconda/pkgs/free
werkzeug                  1.0.0                    pypi_0    pypi
wheel                     0.29.0                   py35_0    https://mirrors.ustc.edu.cn/anaconda/pkgs/free
wincertstore              0.2                      py35_0    https://mirrors.ustc.edu.cn/anaconda/pkgs/free
```
<hr/>
## 3.测试
在tensorflow环境下，进入python模式进行测试
```
(tensorflow_2) C:\Users\dell>python
Python 3.5.4 |Continuum Analytics, Inc.| (default, Aug 14 2017, 13:41:13) [MSC v.1900 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
2020-02-16 17:16:36.110484: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2
>>>  print sess.run(hello)
>>> print sess.run(hello)
>>> print(sess.run(hello))
b'Hello, TensorFlow!'
>>> a = tf.constant(10)
>>> b = tf.constant(21)
>>> print sess.run(a+b)
>>> print(sess.run(a+b))
31
```
测试成功，安装完成
<hr/>
<hr/>
# 安装pytorch
<hr/>
## 1.查看版本
在pytorch官网可以查看需要的版本https://pytorch.org/![version](https://upload-images.jianshu.io/upload_images/21104637-41cbfc3bfccb8b34.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如果没有对应的版本，可以查看pytorch的历史版本https://pytorch.org/get-started/previous-versions/，找到了合适的版本1.1.0
![version_pre](https://upload-images.jianshu.io/upload_images/21104637-1351d355bc88d084.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
注意：pytorch官网给出的命令，下载链接指向的是pytorch官网，要使用国内镜像不可以加-c
<hr/>
## 2.创建环境
创建环境与安装tensorflow类似安装python3.7，在安装pytorch包时键入
```
conda install pytorch==1.1.0 torchvision==0.3.0 cudatoolkit=9.0
```
<hr/>
## 3.测试
```
(E:\local\pytorch) C:\Users\dell>python
Python 3.7.6 (default, Jan  8 2020, 20:23:39) [MSC v.1916 64 bit (AMD64)] :: Anaconda, Inc. on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> x = torch.empty(5, 3)
>>> print(x)
tensor([[9.0919e-39, 9.9184e-39, 1.0286e-38],
        [1.0653e-38, 1.0469e-38, 9.5510e-39],
        [9.9184e-39, 9.0000e-39, 1.0561e-38],
        [1.0653e-38, 4.1327e-39, 8.9082e-39],
        [9.8265e-39, 9.4592e-39, 1.0561e-38]])
```
测试成功
<hr/>


