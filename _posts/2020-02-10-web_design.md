---
layout:     post
title:      HTML页面布局
subtitle:   html
date:       2020-02-10
author:     HT
header-img: img/post-bg-htmldemo.jpg
catalog: true
tags:
    - html
---

<hr>
# 1.基础
<hr/>
## 1.1布局方式

|布局方式|解释|
|:---:|:---:|
|自然布局|无任何修饰，自动向左|
|响应布局|流动布局，采用浮动方法|
|定位布局|相对于div标签定位|

<hr/>
## 1.2布局结构
HTML5有三种典型布局结构

|布局结构|应用场景|
|:---:|:---:|
|div-ul-li|分类导航或菜单|
|table-tr-td|图文布局或显示数据|
|frameset-frame|一个浏览器串口显示多个网页|

<hr/>
## 1.3布局属性
无论采用何种布局方式和结构，都会用到CSS常用的布局属性功能，包括对象尺寸、边距、颜色背景、字体等
<hr/>
## 1.4布局工具
布局工具有div、table、frameset、HTML5新元素和Bootstrap，Bootstrap是一个web前端框架
<hr/>
<hr/>
# 2.div-ul-li布局
根据设计需求可以设计框的尺寸
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>DSP课程实验</title>
    <style type="text/css">
        div.layout {border:2px solid # ffffff;padding:3px;width:528px;height:396px;margin:auto;background-color:# e5dfdf}
        ul.hreflist {padding:0px;margin:auto;width:528px;overflow:hidden}
        ul.hreflist li{list-style-type:none;float:left;padding:4px 8px;width:160px;text-decoration-style:none}
        ul.hreflist li img{display:block;width:160px;height:160px;border:none}
        ul.hreflist li span{display:block;width:100%;height:30px;line-height:30px;background:# ffffff;text-align:center;text-decoration-style:none}
        a:link {text-decoration:none;color:black}
        a:hover{text-decoration:underline;color:red}
    </style>
</head>
<body>
    <div class="layout">
        <ul class="hreflist">
            <li>
                <a href="实验一.pdf">
                    <img src="5a22349010586bb1-8478480ac02d3810-8069f1de41b401f7fbf61fd08384accd.jpg" alt="" />
                    <span>实验一</span>
                </a>
            </li>
            <li>
                <a href="实验二.pdf">
                    <img src="5a22349010586bb1-873f74c49cdd8d90-642b56a90fbd5f90484d0a61c2164937.jpg" alt="" />
                    <span>实验二</span>
                </a>
            </li>
            <li>
                <a href="实验三.pdf">
                    <img src="b37d57d0bbfab194-9429aa682b55e7aa-19c5cec3537e8bc9d09acabc6629652a.jpg" alt="" />
                    <span>实验三</span>
                </a>
            </li>
            <li>
                <a href="dsp-exp-basic-lab1.pdf">
                    <img src="5a22349010586bb1-8478480ac02d3810-8069f1de41b401f7fbf61fd08384accd.jpg" alt="" />
                    <span>实验一要求</span>
                </a>
            </li>
            <li>
                <a href="dsp-exp-basic-lab2.pdf">
                    <img src="5a22349010586bb1-873f74c49cdd8d90-642b56a90fbd5f90484d0a61c2164937.jpg" alt="" />
                    <span>实验二要求</span>
                </a>
            </li>
            <li>
                <a href="dsp-exp-basic-lab3.pdf">
                    <img src="b37d57d0bbfab194-9429aa682b55e7aa-19c5cec3537e8bc9d09acabc6629652a.jpg" alt="" />
                    <span>实验三要求</span>
                </a>
            </li>
        </ul>
    </div>
</body>
</html>
```
<hr/>
## 3.table-tr-td布局
table-tr-td布局的分区基于表进行，一级分区指直接隶属于body元素的table，被称为主表。二级分区指隶属于主表内的一个td的表。
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>中科大信院二班</title>
    <style type="text/css">
        table{
            width:100%;
        }
        # school {
            font-family: 'Microsoft YaHei';
            font-size: 20px;
            font-weight: 400;
            color: # 3257a2;
            line-height: 22px;
            letter-spacing: .5em;
        }
        # name {
        font-family:'Microsoft YaHei';font-size:30px;font-weight:700;
        color:# 3257a2;
        line-height:40px;
        letter-spacing:1em;
        }
        .navtext {
            font-family: 'Microsoft YaHei';
            font-size: 20px;
            font-weight: 400;
        }
        # navigation td {border-bottom:1px solid # 808080}
        # navigation a {
            font-family: 'Microsoft YaHei';
            font-size: 20px;
            font-weight: 500;
            color:black;
            line-height:16px;
            letter-spacing:.1em;
            text-decoration:none;
            display:block;
            padding:8px 6px 8px 22px;
        }
            # navigation a:hover {
            color:# 3257a2;
            font-weight:bold;
            background-color:white;
            }
    </style>

</head>
<body>
    <table cellpadding="0" cellspacing="0">
        <tr style="background-color:# 70e4e8">
            <td width="150" rowspan="2" colspan="2">
                <img src="logo1702.png" alt="班徽" width="150" height="150" border="0"/>
            </td>
            <td width="350" colspan="2" height="50"  nowrap="nowrap" valign="bottom">
                <pre id="school">中国科学技术大学</pre>
            </td>
            <td width="200">
                <img src="sistlogo_w.png" alt="中科大信院" width="200" height="50"/>
            </td>
        </tr>
        <tr style="background-color:# 70e4e8">
            <td height="100" colspan="2" nowrap="nowrap"  valign="top">
                <pre id="name">信息学院本科1702班</pre>
            </td>
            <td>
            </td>
        </tr>
        <tr style="background-color:# e1ebeb">
            <td colspan="5" style="height:10px"></td>
        </tr>
        <tr>
            <td width=" 120" height="700" valign="top">
                <br/>
                <table border="0" cellpadding="0" cellspacing="0" width="125" id="navigation">
                    <tr><td width="120"><pre class="navtext">班级信息</pre></td></tr>
                    <tr><td width="120"><pre class="navtext">班级活动</pre></td></tr>
                    <tr><td width="120"><pre class="navtext">班级公告</pre></td></tr>
                    <tr><td width="120"><pre class="navtext">新闻稿</pre></td></tr>
                </table>
            </td>
            <td width="30"></td>
            <td width="100%" colspan="3"valign="top">
                <br/><br/><br/>
                <h1 style="text-align:center">舌尖上的2020</h1>
                <p>2019年12月31日，信息学院本科17级2班
                        于科技实验楼会议室举办了“舌尖上的2020”主题晚会。
                        本次晚会由杨昊、卢志颖同学进行主持，准备了吃货飞花令、生死时速、小说家、
                        演技炸裂、材猜菜等五个游戏环节，以及《二零三》、《一路向北》、《我怀念的》、
                        《同桌的你》等歌曲节目，以及作为主题的美食自制环节。同学们来到这里，
                        在2019年的最后一晚，共享一场游戏与美食的盛宴，迎接崭新的2020年。
                </p>
            </td>
        </tr>
    </table>
</body>
</html>
```
<hr/>
# 4.frameset布局
使用框架可以在同一个浏览器窗口中显示多个页面，每份HTML文档称为一个框架，并且每个框架独立于其他框架。但使用框架的缺点时开发人员必须同时跟踪更多HTML文档，而且很难打印整张页面。在frameset中使用ifame实现常规的一些分栏布局。
```
<!--frameset.html-->
<html>
<frameset cols="25%,75%">
    <frame name="left" src="left.html">
    <frame name="right" src="right.html">
</frameset>
</html>
```
```
<!--left.html-->
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>frameset-left</title>
</head>
<body>
    <p>这是左半部分</p>
    <a target="right" href="right_2.html">切换右半部分</a>
</body>
</html>
```
```
<!--right.html-->
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>frameset-right</title>
</head>
<body>
    <p>这里是右半部分</p>
</body>
</html>
```
```
<!--right_2html-->
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>framset-right_2</title>
</head>
<body>
    <p>这是切换后的右半部分<p>
</body>
</html>
```
<hr/>
# 5.Bootstrap布局

bootstrap是一个快速开发web的应用程序和网站的前端框架。其提供了基本结构、CSS特性、组件和插件。在编写html文件时使用bootstrap库中的样式或组件可以降低代码量提高效率。
可以参考https://v3.bootcss.com/getting-started/# download和https://www.runoob.com/bootstrap/bootstrap-tutorial.html
```
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>
    <!-- Bootstrap -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- HTML5 shim 和 Respond.js 是为了让 IE8 支持 HTML5 元素和媒体查询（media queries）功能 -->
    <!-- 警告：通过 file:// 协议（就是直接将 html 页面拖拽到浏览器中）访问页面时 Respond.js 不起作用 -->
    <!--[if lt IE 9]>
     <script src="https://cdn.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>        
      <script src="https://cdn.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
    <![endif]-->
</head>
<body>
    <ul class="nav nav-pills">
        <li class="active"><a href="# ">Home</a></li>
        <li><a href="# " onclick="ActiveXObject();">SVN</a></li>
        <li><a href="# ">iOS</a></li>
        <li><a href="# ">VB.Net</a></li>
        <li><a href="# ">Java</a></li>
        <li><a href="# ">PHP</a></li>
    </ul>
    <!-- jQuery (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@1.12.4/dist/jquery.min.js"></script>
    <!-- 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js"></script>
</body>
</html>
```
<hr/>

# 6.HTML5新元素布局

|标签|描述|
|:---:|:---:|
|header|定义文档或节的页眉|
|nav|定义导航链接的容器|
|section|定义文档中的节|
|article|定义独立的自包含文章|
|asiide|定义内容之外的内容(侧栏)|
|footer|定义文档或节的页脚|
|details|定义额外细节|
|summary|定义detail元素的标题|
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title></title>
    <style type="text/css">
        header,footer{
            background-color: black;
            color: white;
            clear:both;
            text-align: center;
            padding:5px;
        }
        nav {
            background-color: # eeeeee;
            height: 300px;
            width: 100px;
            float: left;
            line-height: 30px;
            padding: 5px
        }
        ul{
            padding-left:0px;
            margin-left:6px;
        }
        ul>li{
            list-style-type:none;
        }
    </style>
</head>
<body>
    <header><h1>Hello World！</h1></header>
    <nav>
        <ul>
            <li>A</li>
            <li>B</li>
            <li>C</li>
        </ul>
    </nav>
    <section>
        hhhhhhhh
    </section>
    <footer>copyright</footer>
</body>
</html>
```
<hr/>

