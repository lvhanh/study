# JavaScript入门阶段

##第一章  准备部分  

### 1.1  展示JavaScript

JavaScript易学，只要有文本编辑器就能编写JavaScript程序。

先学习基础语法和如何使用DOM进行简单操作。

```html
<!DOCTYPE HTML>
<html>
  <head>
  <meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
    <title>热身</title>
  </head>
  <body>
    <p id="p1">我是第一段文字</p>
    <p id="p2">我是第二段文字</p>
    
    <script type="text/javascript">
    document.write("hello");
    document.getElementById("p1").style.color="blue";
    </script>>
  </body>
</html>
```

### 2.2  如何插入JS

​	使用<script>标签在HTML网页中插入JavaScript代码。注意，<script>标签药成对出现，并把JavaScript代码写在`<script></script>`之间。

![img](http://img.mukewang.com/52e31ea8000149f406440218.jpg)

`<script type="text/javascript">`表示在<script></script>之间的是文本类型（text）,javascript是为了告诉浏览器里面的文本是属于javascript语言。

```html
<!DOCTYPE HTML>
<html>
  <head>
  <meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
    <title>插入js代码</title>
    <script type="text/javascript">
    document.write("开启JS之旅");
    </script>
  </head>
  <body>
  </body>
</html>  
```

### 1.3  引用JS外部文件

​	我们可以把HTML文件和JS代码分开，并单独创建一个JavaScript文件（简称JS文件），其文件后缀通常为.js，然后将JS代码直接写在JS文件中。

![img](http://img.mukewang.com/52898b400001d04005500266.jpg)

**注意：在JS文件中，不需要<script>标签，直接编写JavaScript代码就可以了。**

JS文件不能直接运行，需嵌入到HTML文件中执行，我们需在HTML中添加如下代码：

`<script src="script.js"></script>`



![img](http://img.mukewang.com/52898b6900018aeb05540284.jpg)

index.html:

```html
<!DOCTYPE HTML>
<html>
  <head>
  <meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
    <title>引用JS文件</title>
    <script src="script.js">document.write("引用JS文件！");</script>>
  </head>
  <body>
  </body>
</html>
```

script.js

`//请写入JS代码`

### 1.4  JS在页面中的位置

​	我们可以将JavaScript代码放在html文件中任何位置，但是我们一般放在网页的head或者body部分。

**放在<head>部分**

最常用的方式是在页面中head部分放置<script>元素

**放在<body>部分**

JavaScript代码在网页读取到该语句的时候就会执行。

![img](http://img.mukewang.com/52a6ad240001086506440600.jpg)

**注意: **javascript作为一种脚本语言可以放在html页面中任何位置，但是浏览器解释html时是按先后顺序的，所以前面的script就先被执行。比如进行页面显示初始化的js必须放在head里面，因为初始化都要求提前进行（如给页面body设置css等）；而如果是通过事件调用执行的function那么对位置没什么要求的。

### 1.5  认识语句和符号

​	一行的结束就被认定为语句的结束，通常在结尾加上一个分号";"来表示语句的结束。

```
<script type="text/javascript">
	document.write("I");
	document.write("love");
	document.write("JavaScript");
</script>
```

**注意:**

1. “;”分号要在英文状态下输入，同样，JS中的代码和符号都要在英文状态下输入。

2.虽然分号“;”也可以不写，但我们要养成编程的好习惯，记得在语句末尾写上分号。

### 1.6  变量

![img](http://img.mukewang.com/52e32dc90001140c04120228.jpg)

定义变量的关键字var

`var 变量名`

变量名可以任意取名，但要遵循命名规则：

1.变量必须使用字母、下划线（_）或者美元符（$）开始。

2.然后可以使用任意多个英文字母、数字、下划线(_)或者美元符($)组成。

3.不能使用JavaScript关键词与JavaScript保留字。

**变量要先声明再赋值，如下：**

```
var mychar;
mychar="javascript";
var mynum = 6;
```

**变量可以重复赋值，如下：**

```
var mychar;
mychar="javascript";
mychar="hello";
```

**注意:**

1.在JS中区分大小写，如变量mychar与myChar是不一样的，表示是两个变量。

2.变量虽然也可以不声明，直接使用，但不规范，需要先声明，后使用。

```html
<!DOCTYPE HTML>
<html>
  <head>
  <meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
    <title>变量</title>
    <script type="text/javascript">
    var mynum;
    mynum = 6;
    document.write(mynum);
    </script>>
  </head>
</html>
```

### 1.7  判断语句（if...else）

**语法：**

```
if(条件)
{ 条件成立时执行的代码 }
else
{ 条件不成立时执行的代码 }
```

假设我们通过年龄来判断是否为成年人，如年龄大于等于18岁，是成年人，否则不是成年人。**代码表示如下：**

```
<script type="text/javascript">
   var myage = 18;
   if(myage>=18)  //myage>=18是判断条件
   { document.write("你是成年人。");}
   else  //否则年龄小于18
   { document.write("未满18岁，你不是成年人。");}
</script>
```

### 1.8  什么是函数

​	**函数定义：**

```
function 函数名()
{
     函数代码;
}
```

**说明:**

1. function定义函数的关键字。
2. "函数名"你为函数取的名字。
3. "函数代码"替换为完成特定功能的代码。

我们来编写一个实现两数相加的简单函数,并给函数起个有意义的名字：“add2”，代码如下：

```
function add2(){
   var sum = 3 + 2;
   alert(sum);
}
```

![img](http://img.mukewang.com/5419430400012de808370459.jpg)

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>函数调用</title>
  <script type="text/javascript">
  function contxt() //定义函数
    {
      alert("哈哈，调用函数了！")
    }
  </script>
</head>
  <body>
    <form>
    <input type="button" value="点击我" onclick="contxt()" />
    </form>
  </body>
</html>
```

##  第二章  常用互动方法

### 2.1  输出内容（document.write）

​	`document.write()` 可用于直接向 HTML 输出流写内容。简单的说就是直接在网页中输出内容。

**第一种：输出内容用""括起，直接输出""号内的内容。**

```
<script type="text/javascript">
  document.write("I love JavaScript！"); //内容用""括起来，""里的内容直接输出。
</script>
```

**第二种：通过变量，输出内容**

```
<script type="text/javascript">
  var mystr="hello world!";
  document.write(mystr);  //直接写变量名，输出变量存储的内容。
</script>
```

**第三种：输出多项内容，内容之间用+号连接**

```
<script>
	var mystr="hello";
	document.write(mystr+"I love javascript");//多项内容之间用+号连接
</script>
```

**第四种：输出HTML标签，并起作用，标签使用""括起来**

```
<script type="text/javascript">
  var mystr="hello";
document.write(mystr+"<br>");//输出hello后，输出一个换行符
  document.write("JavaScript");
</script>
```



```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>document.write</title>
  <script type="text/javascript">
  	var mystr="我是";
    var mychar="JavaScript";
    document.write(mychar+"<br>");
    document.write(mystr+mychar+"的忠实粉丝！");
  </script>
</head>
</html>  
```

### 2.2  消息对话框

**语法：**

`alert(字符串或变量);`

**代码演示**

```
<script type="text/javascript">
	var mynum = 30;
	alert("hello!");
	alert(mynum);
</script>
```

**注：**alter弹出消息对话框（包含一个确定按钮）

**结果：按顺序弹出消息框**

![img](http://img.mukewang.com/52e362430001bdd204850354.jpg)

![img](http://img.mukewang.com/52e362850001024d04840353.jpg)

**注意：**

1. 在点击对话框"确定"按钮前，不能进行任何其它操作。
2. 消息对话框通常可以用于调试程序。
3. alert输出内容，可以是字符串或变量，与document.write 相似。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>alert</title>
  <script type="text/javascript">
    function rec(){
      var mychar="I love javascript";
      alert(mychar);
    }
  </script>
</head>
  <body>
    <form>
    <input type="button" name="button" onClick="rec()" value="点击我" />
    </form>
  </body>
</html>
```

### 2.3  confirm消息对话框

confirm消息对话框通常用于允许用户做选择的动作。弹出对话框（包括一个确定按钮和一个取消按钮）。

**语法:**

```
confirm(str);
```

**参数说明:**

```
str：在消息对话框中要显示的文本
返回值: Boolean值
```

**返回值:**

```
当用户点击"确定"按钮时，返回true
当用户点击"取消"按钮时，返回false
```

**注:** **通过返回值可以判断用户点击了什么按钮**

```
<script type="text/javascript">
	var mymessage=confirm("你喜欢javascript吗？");
	if(mymessage==true)
	{
      document.write("很好，加油！");
	}
	else
	{document.write("JS功能强大，要学习噢！");}
<script>
```

**结果：**

![img](http://img.mukewang.com/52e35bc60001f01a04230353.jpg)

**注: 消息对话框是排它的，即用户在点击对话框按钮前，不能进行任何其它操作。**



```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>confirm</title>
  <script type="text/javascript">
    function rec(){
      var mymessage=confirm("你是女士吗？");
      if(mymessage==true)
        {document.write("你是女士！");}
      else
        {document.write("你是男士！");}
    }
  </script>
</head>
<body>
	<input type="button" name="button" value="点击我" onClick="rec()" />  
</body>
</html>
```

### 2.4  prompt消息对话框

`prompt`弹出消息对话框，通常用于询问一些需要与用户交互的信息。弹出消息对话框（包含一个确定按钮、取消按钮与一个文本输入框）。

**语法：**

`prompt(str1,str2);`

**参数说明：**

```
str1:要显示在消息对话框中的文本，不可修改
str2:文本框中的内容，可以修改
```

**返回值：**

```
1.点击确定按钮，文本框中的内容将作为函数返回值
2.点击取消按钮，将返回null
```

```
var myname=prompt("请输入你的姓名：");
if(myname!=null)
{alert("你好"+myname);}
else
{alert("你好 my friend.");}
```

**结果:**

<img src="http://img.mukewang.com/52e360780001ede107090353.jpg" style="zoom:80%" />

**注:在用户点击对话框的按钮前，不能进行任何其它操作。**

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>prompt</title>
  <script type="text/javascript">
    function rec(){
      var score=prompt("请输入你的成绩：");
      if(score>=90)
      { document.write("你很棒！");}
      else if(score>=75)
      {document.write("不错！");}
      else if(score>=60)
      {document.write("加油！");}
      else
      {document.write("要努力！");}
    }
  </script>
</head>
<body>
	<input type="button" value="点击我" name="button" onClick="rec()" />
</body>
</html>
```

### 2.5  打开新窗口（window.open）

open()方法可以查找一个已经存在或者新建的浏览器窗口。

**语法：**

`window.open([URL],[窗口名称],[参数字符串])`

**参数说明：**

**URL：**可选参数，在窗口中要显示网页的网址或路径。如果省略，或者为空，那么窗口就不显示任何文档。

**窗口名称：**可选参数，被打开窗口的名称。

​		   1.该名称由字母、数字和下划线字符组成。

​		   2."\_top"、"\_blank"、"_self"具有特殊意义的名称。

​		    \_blank：在新窗口显示目标网页

​		    \_self：在当前窗口显示目标网页

​		    \_top：框架网页中在上部窗口中显示目标网页

​		   3.相同name的窗口只能创建一个，想创建多个窗口则name不能相同。

​		   4.name不能包含空格。

**参数字符串：**可选参数，设置窗口参数，各参数用逗号隔开。

**参数表：**

![img](http://img.mukewang.com/52e3677900013d6a05020261.jpg)

例如：打开``http://www.imooc.com``网站，大小为300px*200px，无菜单，无工具栏，无状态栏，有滚动条窗口：

```
<script type="text/javascript">
window.open('http://www.imooc.com','_blank','width=300,height=200,menubar=no,toolbar=no,status=no,scrollbars=yes')
</script>
```

**注意：**运行结果考虑浏览器兼容问题。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>window.open</title>
  <script type="text/javascript">
    function Wopen(){      window.open('http://www.imooc.com','_blank','width=600,height=400,top=100,left=0')
    }
  </script>
</head>
<body>
	<input type="button" name="button" value="点击我" onClick="Wopen()" />
</body>
</html>
```

###2.6  窗口关闭（window.close）

**用法：**

``window.close();  //关闭本窗口 ``

或

``<窗口对象>.close();  //关闭指定的窗口``

例如：关闭新建的窗口。

```
<script type="text/javascript">
	var mywin=window.open('http://www.imooc.com');
	//将新打的窗口对象，存储在变量mywin中
	mywin.close();
</script>
```

**注意:上面代码在打开新窗口的同时，关闭该窗口，看不到被打开的窗口。**

### 2.7  练习

**任务**

1、新窗口打开时弹出确认框，是否打开

```
提示: 使用 if 判断确认框是否点击了确定，如点击弹出输入对话框，否则没有任何操作。
```

2、通过输入对话框，确定打开的网址，默认为 http：//www.imooc.com/

3、打开的窗口要求，宽400像素，高500像素，无菜单栏、无工具栏。

```html
<!DOCTYPE html>
<html>
 <head>
  <title> new document </title>  
  <meta http-equiv="Content-Type" content="text/html; charset=gbk"/>   
  <script type="text/javascript">  
    function openWindow(){
        var mywin=confirm("是否打开？");
        if(mywin==true)
        {
            var mysecwin;
            mysecwin=prompt("请输入网址","http://www.imooc.com");
            if(mysecwin!="")  //此处若mysecwin!=null则会弹出个空页面不会触发else
            {             window.open(mysecwin,'_blank','width=400,height=500,menubar=no,toolbar=no');
            }
            else
            {
                alert("请输入一个网址！");
            }
        }
    }
    // 新窗口打开时弹出确认框，是否打开

    // 通过输入对话框，确定打开的网址，默认为 http：//www.imooc.com/

    //打开的窗口要求，宽400像素，高500像素，无菜单栏、无工具栏。
    
    
  </script> 
 </head> 
 <body> 
	  <input type="button" value="新窗口打开网站" onclick="openWindow()" /> 
 </body>
</html>
```

## 第三章  DOM操作

### 3.1  认识DOM

文档对象模型DOM（Document Object Model）定义访问和处理HTML文档的标准方法。DOM将HTML文档呈现为带有元素、属性和文本的树结构（节点树）。

![img](http://img.mukewang.com/52e4be610001c67307860420.jpg)

**将HTML代码分解为DOM节点层次图**

![img](http://img.mukewang.com/52e4bd0f0001dd8d04830279.jpg)

**HTML文档可以说由节点构成的集合，三种常见的DOM节点：**

**1.元素节点：**上图中\<html>、\<body>、\<p>等都是元素节点，即标签。

**2.文本节点：**向用户展示的内容，如\<li>....\<li>中的JavaScript、DOM、CSS等文本。

**3.属性节点：**元素属性，如\<a>标签的链接属性``href="http://www.imooc.com"``。

**看下面代码:**

```
<a href="http://www.imooc.com">JavaScript DOM</a>

```

<img src="http://img.mukewang.com/52e4bdb80001064c04480196.jpg" style="zoom:110%" />



### 3.2  通过ID获取元素

学过HTML/CSS样式，都知道，网页由标签将信息组织起来，而标签的id属性值是唯一的，就像是每人有一个身份证号一样，只要通过身份证号就可以找到相对应的人。那么在网页中，我们通过id先找到标签，然后进行操作。

**语法:**

```
 document.getElementById(“id”) 

```

<img src="http://img.mukewang.com/52e4c5950001054207900423.jpg" style="zoom:90%" />

**结果:null或[object HTMLParagraphElement]**

**注:获取的元素是一个对象，如想对元素进行操作，我们要通过它的属性或方法。**

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>document.getElementById</title>
</head>
<body>
<p id="con">JavaScript</p>
<script type="text/javascript">
  var mychar= document.getElementById("id");
  document.write("结果:"+mychar); //输出获取的P标签。 
</script>
</body>
</html>
```

``document.getElementById("con") ``得到的是一个p标签的对象；``document.getElementById("con").innerHTML``才是获取的p标签对象的值。

### 3.3  innerHTML属性

innerHTML属性用于获取或替换HTML元素的内容。

**语法：**

``Object.innerHTML``

**注意：**

1.Object是获取的元素对象，如通过document.getElementById("ID")获取的元素。

2.注意书写，innerHTML区分大小写。

**我们通过id="con"获取\<p> 元素，并将元素的内容输出和改变元素内容，代码如下:**

<img src="http://img.mukewang.com/52e4cd080001f01507220418.jpg" style="zoom:80%" />

**结果:**

![img](http://img.mukewang.com/52e4cb5c000187ce03740251.jpg)

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>innerHTML</title>
</head>
<body>
  <h1 id="con">javascript</h1>
  <p>javascript是一种基于。。。</p>
  <script>
  	var mychar=document.getElementById("con");
  	document.write("原标题："+mychar.innerHTML+<br>);
    mychar.innerHTML="Hello World";
    document.write("现标题："+mychar.innerHTML);
  </script>
</body>
</html>
```

### 3.4  改变HTML样式

HTML DOM允许JavaScript改变HTML元素的样式。

**语法：**

``Object.style.property=new style;``

**注意：**Object是获取的元素对象，如通过document.getElementById("id")获取的元素。

**基本属性表（property）:**

![img](http://img.mukewang.com/52e4d4240001dd6c04850229.jpg)

**注意:**该表只是一小部分CSS样式属性，其它样式也可以通过该方法设置和修改。

改变 \<p> 元素的样式，将颜色改为红色，字号改为20,背景颜色改为蓝：

```html
<p id="pcon">Hello World!</p>
<script>
	var mychar = document.getElementById("pcon");
  	mychar.style.color="red";
  	mychar.style.fontSize="20"; //s要大写
  	mychar.style.backgroundColor="blue"; //c要大写
</script>
```

**结果:**

![img](http://img.mukewang.com/52e4d6ae000177d203770253.jpg)

### 3.5  显示和隐藏（display属性）

网页中经常会看到显示和隐藏的效果，可通过display属性来设置。

**语法：**

``Object.style.display = value``

**注意：**Object是获取的元素对象，如通过document.getElementById("id")获取的元素。

**value取值：**

![img](http://img.mukewang.com/52e4dba5000179da04110095.jpg)

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>display</title>
  <script>
    function hidetext(){
      document.getElementById("con").style.display="none";
    }
    function showtext(){
      document.getElementById("con").style.display="block";
    }
  </script>
</head>
<body>
  <h1>JavaScript</h1>
  <p id="con">
    做为一个web开发师来说，。。。
  </p>
  <form>
  	<input type="button" onClick="hidetext()" value="不显示" />
    <input type="button" onClick="showtext()" value="显示"/>
  </form>
</body>
</html>
```

### 3.6  控制类名（className属性）

className属性设置或返回元素的class属性。

**语法：**

``object.className = classname`

**作用：**

1.获取元素的class属性

2.为网页内的某个元素指定一个css样式来更改该元素的外观

获得\<p>元素的class属性和改变className:

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>className属性</title>
  <style type="text/css">
    input{
      font-size:10px;
    }
    .one{
      width:200px;
      background-color=#ccc;
    }
    .two{
      font-size:18px;
      color:#F00;
    }
  </style>
</head>
<body>
  <p id="con" class="one">JavaScript</p>
  <form>
  	<input type="button" value="点击更改" onClick="modifyclass()"/>
  </form>
  <script>
  	var mychar=document.getElementById("con");
    document.write("p元素Class值为："+mychar.className+"<br>");
    function modifyclass(){
      mychar.className="two" //改变className
    }
  </script>
</body>
</html>
```

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=gb2312">
<title>className属性</title>
<style>
  body{font-size:16px;}
  .one{
    border:1px solid #eee;
    width:230px;
    height:50px;
    background:#ccc;
    color:red;
  }
  .two{
    border:1px solid #ccc;
    width:230px;
    height:50px;
    background:#9CF;
    color:blue;
  }
</style>
</head>
<body>
  <p id="p1">JavaScript使网页显示动态效果</p>
  <input type="button" value="添加样式" onClick="add()" />
  <p id="p2" class="one">JavaScript使网页显示动态效果</p>
  <input type="button" value="更改外观" onClick="modify()" />
  <script>
    function add(){
      var p1=document.getElementById("p1");
      p1.className="one";
    }
    function modify(){
      var p2=document.getElementById("p2");
      p2.className="two";
    }
  </script>
</body>
</html>  
```

##  第四章  练习

### 任务

一、定义"改变颜色"的函数

```
提示:
obj.style.color
obj.style.backgroundColor 
```

二、定义"改变宽高"的函数

```
提示:
obj.style.width
obj.style.height 
```

三、定义"隐藏内容"的函数

```
提示:
obj.style.display="none";
```

四、定义"显示内容"的函数

```
提示:
obj.style.display="block";
```

五、定义"取消设置"的函数

```
提示: 
使用confirm()确定框，来确认是否取消设置。
如是将以上所有的设置恢复原始值,否则不做操作。

```

六、当点击相应按钮，执行相应操作，为按钮添加相应事件

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" Content="text/html; charset=utf-8" />
<title>javascript</title>
<style type="text/css">
body{font-size:12px;}
#txt{
    height:400px;
    width:600px;
	border:#333 solid 1px;
	padding:5px;}
p{
	line-height:18px;
	text-indent:2em;}
</style>
</head>
<body>
    <script>
        function color(){
            var color=document.getElementById("txt");
            color.style.color="#ccc";
            color.style.backgroundColor="#blue";
        }
        function wh(){
            var wh=document.getElementById("txt");
            wh.style.width="500px";
            wh.style.height="300px";
        }
        function hide(){
            var hide=document.getElementById("txt");
            hide.style.display="none";
        }
        function show(){
            var show=document.getElementById("txt");
            show.style.display="block";
        }
        function cancel(){
            var mychar=confirm("是否要恢复？")
            if(mychar==true)
            {
                var cancel=document.getElementById("txt");
                cancel.removeAttribute('style');
            }
        }
    </script>
  <h2 id="con">JavaScript课程</H2>
  <div id="txt"> 
     <h5>JavaScript为网页添加动态效果并实现与用户交互的功能。</h5>
        <p>1. JavaScript入门篇，让不懂JS的你，快速了解JS。</p>
        <p>2. JavaScript进阶篇，让你掌握JS的基础语法、函数、数组、事件、内置对象、BOM浏览器、DOM操作。</p>
        <p>3. 学完以上两门基础课后，在深入学习JavaScript的变量作用域、事件、对象、运动、cookie、正则表达式、ajax等课程。</p>
  </div>
  <form>
  <!--当点击相应按钮，执行相应操作，为按钮添加相应事件-->
    <input type="button" value="改变颜色" onClick="color()" />  
    <input type="button" value="改变宽高" onClick="wh()" />
    <input type="button" value="隐藏内容" onClick="hide()" />
    <input type="button" value="显示内容" onClick="show()" />
    <input type="button" value="取消设置" onClick="cancel()" />
  </form>
  <script type="text/javascript">
//定义"改变颜色"的函数


//定义"改变宽高"的函数


//定义"隐藏内容"的函数


//定义"显示内容"的函数


//定义"取消设置"的函数



  </script>
</body>
</html>
```

