---
layout:     post
title:      驾照考试答题软件
subtitle:   python&PyQt5&API的完美融合
date:       2019-04-20
author:     HT
header-img: img/post-bg-pyGUI.jpg
catalog: true
tags:
    - Python
---

>基于python3.7语言，调用PyQt5等标准库，并通过API获取驾照题库与建立本地存储文档，来构建有随机测试、顺序练习、错题复习等功能的驾照考试题目练习GUI界面。

# 代码阐释

在代码中创建了三个类分别为存储及操作题库的类Question_bank、实现子窗口的类Question_solvingUI(QWidget)、实现主窗口的类menu(QMainWindow)，小技巧结合类中函数阐释<br/>
<br/>
1. Question_bank <br/>
Question_bank用来获取、存储和操作题库。其中，Qlist存储API获得的题库，Wqlist存储本地获得题库，param存储参数，path为本地保存路径。<br/>
request函数获取API题库，使用r.json()将返回值转换为dict。<br/>
write_file函数将题目写入本地文档，模式不同写入方式分为单个和全部写入<br/>
read_file函数将本地文档存储的题目读入Wqlist，其中使用了os.path.exists函数判断路径是否存在；for line in f.readlines()语句利用了f.readlines()读取文件按行返回list的特性；line.split()函数可以将每行按空格分割，返回为list。<br/>
down_loadimg函数用来下载并保存图片，并返回其存储路径。<br/>
read_appkey函数用来在文本文档中读取appkey。<br/>
2.	Question_solvingUI(QWidget)<br/>
Question_solvingUI(QWidget)用来实现子窗口。其中，param用来保存参数，img用来保存需要输出的题目图片，Q为一个Question_bank类，list用来存放当前题目列表，dict用来存放当前题目，order用来存放当前题目序号。<br/>
initUI函数初始化子窗口界面和题库。其中使用了self.explainlabel.setWordWrap(True)设置解释文本自动换行；QMessageBox.information来输出提示信息；使用信号与槽将按钮与槽函数连接。<br/>
center函数通过获取屏幕大小，将窗口显示在屏幕中央。<br/>
practice函数更新每次题目信息，点击按钮“下一题”执行practice函数。<br/>
refreshShowimg函数获取并显示图片。其中，使用了cv.imread读取图片；使用QImage .rgbSwapped()将opencv下的image转换成Qimage；使用imglabel.setPixmap显示图片。<br/>
buttonclicked函数为点击选项按钮的响应，判断对错，显示解释，并根据模式对题目进行操作，清除缓存图片。其中，使用了sender=self.sender()函数获取信号的发出者来判断对错。<br/>
read_progress函数读取order模式下的学习进度。<br/>
toclose函数为“结束做题”按钮的响应。根据模式不同，更新错题文档，写入学习进度。<br/>
remove函数删除图片缓存。其中，使用了os.remove函数删除文件。<br/>
3.	menu(QMainWindow)<br/>
menu(QMainWindow)用来实现主窗口。其中，info1、info2用来存储选项结果，status_selected存储选项状态，param存储参数。<br/>
initUI函数初始化主窗口。其中创建了状态栏statusBar；创建四个事件exitAction、randAction、orderAction、wrongAction；创建工具栏toolbar；设置了radiobutton和单选分组self.bg1 = QButtonGroup(self)<br/>
rbclicked函数为选择radiobutton的响应，会改变info1与info2的值。<br/>
submit函数提交选项内容至param，主要为了保证提交参数的有效，所以设置submit函数。<br/>
QrUI、QoUI、QwUI函数都为槽函数，为点击工具栏的响应，打开子窗口。<br/>
Mkdir函数根据所选模式在当前目录下创建文件夹。<br/>
<br/>
# 详细功能<br/>
<br/>
1.	选择驾照考试类型<br/>
运行程序后，出现主界面如下，可通过界面中两组单选按钮选中自己所需的考试科目和驾照类型，选择完成点“提交”后，弹出确认弹窗。之后会根据所选内容在当前目录下建立子目录用来存储，同时可开始选择工具栏中的答题模式。如果在未选中或未提交时选择答题模式，会出现指示弹窗。<br/>
 <br/>
2.	随机测试答题模式<br/>
随机答题模式为在所选类型的驾照题库中随机选取100道题目做答。连接网络后，导入“appkey.txt”，选中工具栏“随机测试”，会弹出子窗口如下。点击选项按钮之后窗口底部会显示正确信息和题目解释，如果做错题目，错题会保存到本地文档，反之，会删除本地题目图片缓存。点击“下一题”可以切换题目，点击“结束答题”可随时结束。如果随机测试题目已做完，会弹出提示框。若未连接网络或未导入“appkey.txt”，在点击“随机测试”时会出现错误提示信息。<br/>
 <br/>
3.	顺序练习答题模式<br/>
顺序答题模式为在所选类型的驾照题库中选取所有题目依次练习。顺序模式会保存此前的做题记录到“progress.txt”中，每次打开顺序模式时，会先从“progress.txt”中读取顺序做题进度的题号，再从此题开始作答。连接网络后，导入“appkey.txt”，选中工具栏“顺序练习”，会弹出子窗口如下。点击选项按钮之后窗口底部会显示正确信息和题目解释，如果做错题目，错题会保存到本地文档，反之，会删除本地题目图片缓存。点击“下一题”可以切换题目，点击“结束答题”可随时结束。如果顺序练习题目已做完，会弹出提示框。若未连接网络或未导入“appkey.txt”，在点击“顺序练习”时会出现错误提示信息。<br/>
 <br/>
4.	复习错题模式<br/>
复习错题模式为练习在“随机测试”与“顺序练习”中做错的题目。点击复习错题后，会根据所选类型，从对应文件夹中读取错题信息（错题模式无需连接网络），并弹出子窗口如下。点击选项按钮之后窗口底部会显示正确信息和题目解释，若做对题目，标记题目“id”为“right”，并删除本地图片缓存。点击“下一题”可以切换题目，点击“结束答题”可随时结束，结束后会更新本地错题文档。如果错题已做完，会弹出提示框。若还没有做错过题，点击“复习错题”时会弹窗显示信息。<br/>


>最后附上GitHub：<https://github.com/zht1999/py_work1>
