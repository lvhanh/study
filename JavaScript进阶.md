# JavaScript进阶篇

## 第一章  JS基础语法

### 1.1  什么是变量

什么是变量? 从字面上看，变量是可变的量；从编程角度讲，变量是用于存储某种/某些数值的存储器。我们可以把变量看做一个盒子,盒子用来存放物品,物品可以是衣服、玩具、水果...等。

<img src="http://img.mukewang.com/529860210001304d04700234.jpg" style="zoom:90%" />

### 1.2  变量命名

我们赶快给变量取个好名字吧!**变量名字可以任意取，**只不过取名字要遵循一些规则:

1.必须以字母、下划线或美元符号开头，后面可以跟字母、下划线、美元符号和数字。如下:

```
正确:           
    mysum            
    _mychar         
    $numa1          
```

```
错误:
  6num  //开头不能用数字
  %sum //开头不能用除(_ $)外特殊符号,如(%  + /等)
  sum+num //开头中间不能使用除(_ $)外特殊符号，如(%  + /等)

```

2.变量名区分大小写，如:A与a是两个不同变量。

3.不允许使用JavaScript关键字和保留字做变量名。

![img](http://img.mukewang.com/529c07c000014f5103080447.jpg)

### 2.3  变量声明

``声明变量语法：var 变量名;``

var在JavaScript中是关键字（即保留字），这个关键字的作用是声明变量，并为“变量”准备位置（即内存）。

``var mynum; //声明一个变量mynum``

var还可以一次声明多个变量，变量之间用“,”逗号隔开。

``var num1,num2;``

**注意：变量也可以不声明，直接使用，但为了规范，需要先声明。**

### 2.4  变量赋值

使用``"="``号给变量存储内容

``var mynum = 5; //声明变量并赋值。`` 

可以把任何东西存储在变量里；如数值、字符串、布尔值。

###2.5  表达式  

指具有一定的值、用操作符把常数和变量连接起来的代数式。**一个表达式可以包含常数或变量。**

![img](http://img.mukewang.com/52b9227d0001acc703000174.jpg)

![img](http://img.mukewang.com/529c21600001d02302800228.jpg)

![img](http://img.mukewang.com/52b922a00001445b02920187.jpg)

![img](http://img.mukewang.com/529c218f000101d402980228.jpg)

### 2.6  +号操作符

操作符是用于在JavaScript中指定一定动作的符号。

（1）操作符

看下面这段JavaScript代码。

```
sum = numa + numb;
```

其中的`"="`和`"+"`都是操作符。

JavaScript中还有很多这样的操作符，例如，算术操作符(+、-、*、/等)，比较操作符(<、>、>=、<=等)，逻辑操作符(&&、||、！)。

**注意: “=” 操作符是赋值，不是等于。**

(2) `"+"`操作符

算术运算符主要用来完成类似加减乘除的工作，在JavaScript中，“+”不只代表加法，还可以连接两个字符串，例如：

```
mystring = "Java" + "Script"; // mystring的值“JavaScript”这个字符串
```

### 2.7  ++和- -

算术操作符除了(+、-、*、/)外，还有两个非常常用的操作符，自加一`“++”`；自减一`“--”`。首先来看一个例子：

```
mynum = 10;
mynum++; //mynum的值变为11
mynum--; //mynum的值又变回10
```

上面的例子中，mynum++使mynum值在原基础上增加1，mynum--使mynum在原基础上减去1,其实也可以写成:

```
mynum = mynum + 1;//等同于mynum++
mynum = mynum - 1;//等同于mynum--
```

### 2.8  比较操作符

![img](http://img.mukewang.com/532a3c150001c65802010207.jpg)

### 2.9  逻辑与操作符

![img](http://img.mukewang.com/52a16f880001d27803770180.jpg)

![img](http://img.mukewang.com/530a9d2b0001a33e03770178.jpg)

![img](http://img.mukewang.com/52a1760c000159a702330111.jpg)

### 2.10  操作符优先级

**操作符之间的优先级（高到低）:**

算术操作符 → 比较操作符 → 逻辑操作符 → "="赋值符号

如果同级的运算是按从左到右次序进行,多层括号由里向外。

## 第二章  数组

###2.1  数组定义

![img](http://img.mukewang.com/52c9ff5c0001085a05460266.jpg)

数组是一个值的集合，每个值都有一个索引号，从0开始，每个索引都有一个相应的值，根据需要添加更多数值。

### 2.2  如何创建数组

**创建数组语法：**

``var myarray=new Array();``

![img](http://img.mukewang.com/52ca004b0001c81103980228.jpg)

我们创建数组的同时，还可以为数组指定长度，长度可任意指定。

``var myarray=new Array(8) //创建数组，存储8个数据``

**注意：**
1.创建的新数组是空数组，没有值，如输出，则显示undefined。
2.虽然创建数组时，指定了长度，但实际上数组都是变长的，也就是说即使指定了长度为8，仍然可以将元素存储在规定长度以外。

### 2.3  数组赋值

**数组的表达方式：**

```
第一步：创建数组var myarr=new Array();
第二步：给数组赋值
		myarr[1]="张三";
		myarr[2]="李四";
```

下面创建一个数组，用于存储5个人的数学成绩。

```
var myarray=new Array(); //创建一个新的空数组
myarray[0]=66; //存储第1个人的成绩
myarray[1]=80; //存储第2个人的成绩
myarray[2]=90; //存储第3个人的成绩
myarray[3]=77; //存储第4个人的成绩
myarray[4]=59; //存储第5个人的成绩
```

**注意：**数组每个值有一个索引号，从0开始。

我们还可以用简单的方法创建上面的数组和赋值：

第一种方法：

```
var myarray= new Array(66,80,90,77,59); //创建数组同时赋值
```

第二种方法：

``var myarray= [66,80,90,77,59]; //直接输入一个数组（称“字面量数组”）``

**注意：**数组存储的数据可以是任何类型（数字、字符、布尔值等）

只需使用下一个未用的索引，任何时刻可以不断向数组增加新元素。

```
myarray[5]=88; //使用一个新索引，为数组增加一个新元素
```

### 2.4  使用数组元素

要得到一个数组元素的值，只需引用数组变量并提供一个索引，如：
**第一个人的成绩表示方法：**`myarray[0]`
**第三个人的成绩表示方法:** `myarray[2]`

### 2.5  数组属性length

如果要知道数组的大小，只需引用数组属性length。length属性表示数组的长度，即数组中元素的个数。

**语法：**

``myarray.length; //获取数组myarray的长度``

**注意：**因为数组的索引总是由0开始，所以一个数组的上下限分别是：0和length-1。如数组的长度是5，数组的上下限分别是0和4。

```
var arr=[55,32,5,90,60,98,76,54];//包含8个数值的数组arr 
document.write(arr.length); //显示数组长度8
document.write(arr[7]); //显示第8个元素的值54
```

同时，length长度可变

数组随元素的增加，长度也会改变。

```
var arr=[98,76,54,56,76]; // 包含5个数值的数组
document.write(arr.length); //显示数组的长度5
arr[15]=34;  //增加元素，使用索引为15,赋值为34
alert(arr.length); //显示数组的长度16
```

### 2.6  二维数组

``二维数组的表示：myarray[][]``

**注意: **二维数组的两个维度的索引值也是从0开始，两个维度的最后一个索引值为长度-1。 

**1.二维数组的定义方法一**

```
var myarr=new Array(); 	//先声明一维
for(var i=0;i<2;i++){  	//一维长度为2
  myarr[i]=new Array();	//再声明二维
  for(var j=0;j<3;j++){	//二维长度为3
    myarr[i][j]=i+j;	//赋值，每个数组元素的值为i+j
  }
}
```

将上面二维数组用表格的方式表示：

|      |        0        |        1        |        2        |
| :--: | :-------------: | :-------------: | :-------------: |
|  0   | myarr\[0][0]值:0 | myarr\[0][0]值:1 | myarr\[0][0]值:2 |
|  1   | myarr\[0][0]值:1 | myarr\[0][0]值:2 | myarr\[0][0]值:3 |

**2.二维数组的定义方法二**

``var Myarr=[[0,1,2],[1,2,3]]``

**3.赋值**

``myarr[0][1]=5; //将5的值传入到数组中，覆盖原有值。``

**说明：**myarr\[0][1]，0表示表的行，1表示表的列

## 第三章  流程控制语句

### 3.1  if语句

**语法****:**

```
if(条件)
{ 条件成立时执行代码}
```

**注意：if小写，大写字母（IF）会出错！**

### 3.2  if...else语句

if...else语句是在指定的条件成立时执行代码，在条件不成立时执行else后的代码。

**语法****:**

```
if(条件)
{ 条件成立时执行的代码}
else
{条件不成立时执行的代码}
```

### 3.3  if...else嵌套语句

要在多组语句中选择一组来执行，使用if..else嵌套语句。

**语法****:**

```
if(条件1)
{ 条件1成立时执行的代码}
else  if(条件2)
{ 条件2成立时执行的代码}
...
else  if(条件n)
{ 条件n成立时执行的代码}
else
{ 条件1、2至n不成立时执行的代码}
```

```
<script>
	var myscore=86;
	if(myscore<60){
      document.write("加油");
	}
	else if(myscore<75){
      document.write("不错");
	}
	else if(myscore<85){
      document.write("很棒");
	}
	else{
      document.write("超级棒");
	}
</script>
```

### 3.4  Switch语句

当有很多种选项的时候，switch比if else使用更方便。

**语法：**

```
switch(表达式)
{
  case值1:
  执行代码块1
  break;
  case值2:
  执行代码块2
  break;
  ...
  case值n:
  执行代码块n
  break;
  default:
  与case值1、case值2...case值n 不同时执行的代码
}
```

**语法说明：**

```
Switch必须赋初始值，值与每个case值匹配。满足执行该case后的所有语句，并用break语句来阻止运行下一个case。如所有case值都不匹配，执行default后的语句。
```

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>switch</title>
  <script>
  	var myweek=3;
    Switch(myweek){
      case 1:
      case 2:
      document.write("理论知识");
      break;
      case 3:
      case 4:
      document.write("企业实践");
      break;
      case 5:
      document.write("总结经验");
      break;
      case 6:
      case 7:
      document.write("休息和娱乐");
    }
  </script>
</head>
<body></body>
</html>
```

### 3.5  for循环

**for****语句结构：**

```
for(初始化变量;循环条件;循环迭代)
{     
    循环语句 
 }
```

假如，一个盒子里有6个球，我们每次取一个，重复从盒中取出球，直到球取完为止。

```
<script type="text/javascript">
var num=1;
for (num=1;num<=6;num++)  //初始化值；循环条件；循环后条件值更新
{   document.write("取出第"+num+"个球<br />");
}
</script>
```

### 3.6  while循环

和for循环有相同功能的还有while循环, while循环重复执行一段代码，直到某个条件不再满足。

**while****语句结构：**

```
while(判断条件)
{
    循环语句
 }
```

### 3.7  Do...while循环

do while结构的基本原理和while结构是基本相同的，但是它保证循环体至少被执行一次。因为它是先执行代码，后判断条件，如果条件为真，继续循环。

**do...while****语句结构：**

```
do
{
    循环语句
 }
while(判断条件)
```

### 3.8  退出循环break

在while、for、do...while、while循环中使用break语句退出当前循环，直接执行后面的代码。

**格式如下：**

```
for(初始条件;判断条件;循环后条件值更新)
{
  if(特殊情况)
  {break;}
  循环代码
}
```

```
<script>
	var num;
	for(num=1;num<=10;num++)
	{
      if(num==5)
      {break; //如果num是5，退出循环。}
      document.write(num+"<br />");
	}
</script>
```

### 任务

考试成绩输出，如果成绩及格继续输出下个成绩，如果成绩不及格，退出并且后面成绩不输出， 我们使用break语句，退出循环。补充第14行代码。

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>break</title>
  <script>
  	var myscore=new Array(90,80,79,59,78);
    var i=0;
    while(i<myscore.length)
    {
      if(myscore[i]<60)
      {
        document.write("不及格，不用循环");
        break;
      }
      document.write("及格，继续循环"+"<br />");
      i++;
    }
  </script>
</head>
  <body></body>
</html>
```

### 3.9  继续循环continue

continue的作用是仅仅跳过本次循环，而整个循环体继续执行。

**语句结构：**

```
for(初始条件;判断条件;循环后条件值更新)
{
  if(特殊情况)
  { continue; }
 循环代码
}
```

上面的循环中，当特殊情况发生的时候，本次循环将被跳过，而后续的循环则不会受到影响。好比输出10个数字，如果数字为5就不输出了。

上面的循环中，当特殊情况发生的时候，本次循环将被跳过，而后续的循环则不会受到影响。好比输出10个数字，如果数字为5就不输出了。

```
<script>
	var num;
	for(num=1;num<=10;num++)
	{
      if(num==5)
      {
        continue;
      }
      document.write("num"+"<br />");
	}
</script>
```

### 3.10  练习

在一个大学的编程选修课班里，我们得到了一组参加该班级的学生数据，分别是姓名、性别、年龄和年级，接下来呢，我们要利用JavaScript的知识挑出其中所有是大一的女生的的名字哦。

**学生信息如下：**

​    ('小A','女',21,'大一'),  ('小B','男',23,'大三'),

​    ('小C','男',24,'大四'),  ('小D','女',21,'大一'),

​    ('小E','女',22,'大四'),  ('小F','男',21,'大一'),

​    ('小G','女',22,'大二'),  ('小H','女',20,'大三'),

​    ('小I','女',20,'大一'),  ('小J','男',20,'大三')

```html
<!DOCTYPE  HTML>
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>流程控制语句</title>
<script type="text/javascript">

 //第一步把之前的数据写成一个数组的形式,定义变量为 infos
 
 
 //第一次筛选，找出都是大一的信息
 
  
 //第二次筛选，找出都是女生的信息
 var infos=[['A','女','21','大一'],['B','男','23','大三'],['C','男','24','大四'],['D','女','21','大一'],['E','女','22','大四'],['F','男','21','大一'],['G','女','22','大二'],['H','女','20','大三'],['I','女','20','大一'],['J','男','20','大三']];
 for(var i=0;i<infos.length;i++)
 {
     for(var j=0;j<infos[i].length;j++)
     {
        if(infos[i][j]=="大一"&&infos[i][1]=="女")
        document.write(infos[i][0]+"<br />");
     }
 }
</script>
</head>
<body>
</body>
</html>
```

## 第四章  函数

### 4.1  什么是函数

函数的作用：可以写一次代码，然后反复地重用这个代码。

如：完成多组数和的功能

```
function add2(a,b){
  sum=a+b;
  alert(sum);
}

add2(3,2);
add2(7,8);
...
```

### 4.2  定义函数

如何定义一个函数呢？看看下面的格式：

```
function  函数名( )
{
     函数体;
}
```

function定义函数的关键字，“函数名”你为函数取的名字，“函数体”替换为完成特定功能的代码。

我们完成对两个数求和并显示结果的功能。并给函数起个有意义的名字：“add2”，代码如下：

```
<script type="text/javascript">
  function add2(){
    sum = 3 + 2;
    alert(sum);
  }
  add2();
</script>
```

### 4.3  函数调用

函数定义好后，是不能自动执行的，需要调用它,直接在需要的位置写函数名。

**第一种情况:在\<script>标签内调用。**

```
  <script type="text/javascript">
    function add2()
    {
         sum = 1 + 1;
         alert(sum);
    }
  add2();//调用函数，直接写函数名。
</SCRIPT>
```

**第二种情况:**在HTML文件中调用，如通过点击按钮后调用定义好的函数。

```
<html>
<head>
<script type="text/javascript">
   function add2()
   {
         sum = 5 + 6;
         alert(sum);
   }
</script>
</head>
<body>
<form>
<input type="button" value="click it" onclick="add2()">  //按钮,onclick点击事件，直接写函数名
</form>
</body>
</html>
```

### 4.4  有参数的函数

定义函数还可以如下格式：

```
function 函数名(参数1,参数2)
{
     函数代码
}
```

**注意:参数可以多个，根据需要增减参数个数。参数之间用(逗号，）隔开。**

```
function add2(x,y)
{
  sum=x+y;
  docunment.write(sum);
}
```

x和y则是函数的两个参数，调用函数的时候，我们可通过这两个参数把两个实际的加数传递给函数了。

例如，add2(3，4)会求3+4的和，add2(60,20)则会求出60和20的和。

###4.5  返回值的函数

**思考:**上一节函数中，通过"document.write"把结果输出来，如果想对函数的结果进行处理怎么办呢？

我们只要把"document.write(sum)"这行改成如下代码：

```
function add2(x,y)
{
   sum = x + y;
   return sum; //返回函数值,return后面的值叫做返回值。
}
```

还可以通过变量存储调用函数的返回值，代码如下:

```
result = add2(3,4);//语句执行后,result变量中的值为7。
```

**注意:函数中参数和返回值不只是数字，还可以是字符串等其它类型。 **

## 第五章  事件响应，让网页交互

### 5.1  什么是事件

JavaScript创建动态页面。事件是可以被JavaScript侦测到的行为。网页中的每个元素都可以产生某些可以触发JavaScript函数或程序的事件。

比如说，当用户单机按钮或者提交表单数据时，就发生一个鼠标单机（onClick）事件，需要浏览器做出处理，返回给用户一个结果。

**主要事件表:**

|     事件      |     说明     |
| :---------: | :--------: |
|   onclick   |   鼠标单机事件   |
| onmouseover |   鼠标经过事件   |
| onmouseout  |   鼠标移开事件   |
|  onchange   | 文本框内容改变事件  |
|  onselect   | 文本框内容被选中事件 |
|   onfocus   |    光标聚集    |
|   onblur    |    光标离开    |
|   onload    |    网页导入    |
|  onunload   |    关闭网页    |

### 5.2  鼠标单击事件（onclick）

onclick是鼠标单击事件，当在网页上单击鼠标时，就会发生该事件。同时onclick事件调用的程序块就会被执行，通常与按钮一起使用。

比如，我们单击按钮时，触发 onclick 事件，并调用两个数和的函数add2()。代码如下：

```html
<html>
  <head>
    <script>
      function add2(){
        var numa,numb,sum;
        numa=6;
        numb=8;
        sum=numa+numb;
        document.write("两数和为："+sum);
      }
    </script>
  </head>
  <body>
    <form>
    	<input name="button" type="button" value="点击提交" onclick="add2()" />
    </form>
  </body>
</html>
```

**注意: **在网页中，如使用事件，就在该元素中设置事件属性。

### 5.3  鼠标经过事件（onmouseover）

鼠标经过事件，当鼠标移到一个对象上时，该对象就触发onmouseover事件，并执行onmouseover事件调用的程序。

现实鼠标经过"确定"按钮时，触发onmouseover事件，调用函数info()，弹出消息框，代码如下:

```html
<!DOCTYPE  HTML>
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>onmouseover</title>
  <script>
    function info(){
      confirm("请输入姓名后，再单击确定！");
    }
  </script>
</head>
  <body>
    <form>
    密码:<input name="password" type="text">
    <input name="button" type="button" value="确定" onmouseover="info()">
 	<!--当鼠标经过“确定”按钮时，触发onmouseover="info()"-->
    </form>
  </body>
</html>
```

**运行结果:**

![img](http://img.mukewang.com/53e196fd00017d8704870416.jpg)

### 5.4  鼠标移开事件（onmouseout）

鼠标移开事件，当鼠标移开当前对象时，执行onmouseout调用的程序。

当把鼠标移动到"登录"按钮上，然后再移开时，触发onmouseout事件，调用函数message()，代码如下:

```html
<!DOCTYPE  HTML>
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>onmouseout</title>
  <script>
    function message(){
      confirm("不要离开，只要输入密码，再单击登录，就ok了！");
    }
  </script>
</head>
  <body>
    <form>
    密码：<input name="password" type="text">
      <input name="button" type="button" value="登录" onmouseout="message()">
    </form>
  </body>
</html>
```

**运行结果:**

![img](http://img.mukewang.com/53e195bf00010d1804760385.jpg)

### 5.5  光标聚焦事件（onfocus）

当网页中的对象获得聚点时，执行onfocus调用的程序就会被执行。

如下代码, 当将光标移到文本框内时，即焦点在文本框内，触发onfocus 事件，并调用函数message()。

```html
<!DOCTYPE  HTML>
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>onfocus</title>
  <script>
    function message(){
      alert("请在此输入姓名！");
    }
  </script>
</head>
  <body>
    <form>
    密码：<input name="username" type="text" value="请输入姓名！" onfocus="message()">
    </form>
  </body>
</html>
```

**运行结果：**

![img](http://img.mukewang.com/5312c5660001821a04300326.jpg)



### 5.6  失焦事件（onblur）

onblur事件与onfocus是相对事件，当光标离开当前获得聚焦对象的时候，触发onblur事件，同时执行被调用的程序。

如下代码, 网页中有用户和密码两个文本框。当前光标在用户文本框内时（即焦点在文本框），在光标离开该文本框后（即失焦时），触发onblur事件，并调用函数message()。

```html
<!DOCTYPE  HTML>
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>onblur</title>
  <script>
    function message(){
      alert("请确定已输入用户名后，再离开！");
    }
  </script>
</head>
  <body>
    <form>
    用户：<input name="username" type="text" value="请输入用户名！" onblur="message()">
    密码：<input name="password" type="text" value="请输入密码！">
    </form>
  </body>
</html>
```

**运行结果：**

![img](http://img.mukewang.com/5312da710001968704410319.jpg)

### 5.7  内容选中事件（onselect）

选中事件，当文本框或者文本域中的文字被选中时，触发onselect事件，同时调用的程序就会被执行。

如下代码,当选中用户文本框内的文字时，触发onselect 事件，并调用函数message()。

```html
<!DOCTYPE  HTML>
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>onselect</title>
  <script>
    function message(){
      alert("您触发了选中事件！");
    }
  </script>
</head>
  <body>
    <form>
    用户：<input name="username" type="text" value="请输入用户名！" onselect="message()">
    </form>
  </body>
</html>
```

**运行结果：**

![img](http://img.mukewang.com/5312d7ba00013fff03950319.jpg)

### 5.8  文本框内容改变事件（onchange）

通过改变文本框的内容来触发onchange事件，同时执行被调用的程序。

### 5.9  加载事件（onload）

事件会在页面加载完成后，立即发生，同时执行被调用的程序。
注意：1. 加载页面时，触发onload事件，事件写在\<body>标签内。

2. 此节的加载页面，可理解为打开一个新页面时。

### 5.10  卸载事件（onunload）

当用户退出页面时（页面关闭、页面刷新等），触发onUnload事件，同时执行被调用的程序。

**注意：不同浏览器对onunload事件支持不同。**

如下代码,当退出页面时，弹出对话框“您确定离开该网页吗？”。

```html
<!DOCTYPE  HTML>
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>onunload</title>
  <script>
  	window.onunload=onunload_message;
    function onunload_message(){
      alert("您确定离开该网页吗？");
    }
  </script>
</head>
  <body>
  欢迎学习JavaScript.
  </body>
</html>
```

### 5.11  练习

使用JS完成一个简单的计算器功能。实现2个输入框中输入整数后，点击第三个输入框能给出2个整数的加减乘除。

提示：获取元素的值设置和获取方法为：例：赋值：document.getElementById(“id”）.value = 1； 取值：var = document.getElementById(“id”）.value；

```html
<!DOCTYPE  HTML>
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>练习</title>
  <script>
    function count(){
      var text1=document.getElementById("txt1").value;
      var sc=document.getElementById("select").value;
      var text2=document.getElementById("txt2").value;
      var text3=""; //不加空值为未定义类型，后面会把运算符“+”更改为两个字符串的拼接
      switch(sc){
        case "+":text3=text1+text2;
          break;
        case "-":text3=text1-text2;
          break;
        case "*":text3=text1*text2;
          break;
        case "/":text3=text1/text2;
          break;
      }
      document.getElementById("fruit").value=text3;
    }
  </script>
</head>
<body>
	<input type="text" id="txt1" />
    <select id="select">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
  	</select>
  	<input type="text" id="txt2" />
  	<input type="button" value="=" onclick="count()" />
  	<input type="text" id="fruit" />
</body>
</html>
```

## 第六章  JavaScript内置对象

### 6.1  什么是对象

JavaScript中的所有事物都是对象，如：字符串、数值、数组、函数等，每个对象带有**属性**和**方法**。

**对象的属性：**反映该对象某些特定的性质的，如：字符串的长度、图像的长宽等；

**对象的方法：**能够在对象上执行的动作。例如，表单的“提交”（Submit），时间的“获取”（getYear）等；

JavaScript提供多个内建对象，比如String、Date、Array等等，使用对象前先定义，如下使用数组对象：

```
var objectName=new Array();//使用new关键字定义对象
或者
var objectName=[];
```

**访问对象属性的语法：**

``objectName.propertyName``

如使用Array对象的length属性来获得数组的长度：

```
var myarray=new Array(6);//定义数组对象
var my1=myarray.length;//访问数组长度length属性
```

**以上代码执行后，my1的值将是：6**

**访问对象的方法：**

``objectName.methodName()``

如使用string对象的toUpperCase()方法来将文本转换为大写：

```
var mystr="Hello world!";//创建一个字符串
var request=mystr.toUpperCase();//使用字符串对象方法
```

以上代码执行后，request的值是：**HELLO WORLD!**

```html
<html>
  <head>
    <script>
      var myarray=new Array(5);
      var mynum=myarray.length;
      document.write("数组长度："+mynum);
    </script>
  </head>
  <body>
  </body>
</html>
```

### 6.2  Date日期对象

日期对象可以存储任意一个日期，并且可以精确到毫秒数（1/1000秒）。

定义一个时间对象

``var Udate=new Date();``

**注意：**使用关键字new，Date()的首字母必须大写。

使Udate成为日期对象，并且已有初始值：**当前时间（当前电脑系统时间）。**

如果要自定义初始值，可以用以下方法：

```
var d=new Date(2012,10,1);
var d=new Date('Oct 1,2012');
```

**访问方法语法：**"<日期对象>.<方法>"

Date对象中处理时间和日期的常用方法：

| 方法名称              | 功能描述                         |
| ----------------- | ---------------------------- |
| get/setDate()     | 返回/设置日期                      |
| get/setFullYear() | 返回/设置年份，用四位数表示               |
| get/setYear()     | 返回/设置年份                      |
| get/setMonth()    | 返回/设置月份。0：一月....11：十二月，所以加一。 |
| get/setHours()    | 返回/设置小时，24小时制。               |
| get/setMinutes()  | 返回/设置分钟数                     |
| get/setSeconds()  | 返回/设置秒钟数                     |
| get/setTime()     | 返回/设置时间（毫秒为单位）               |

#### **返回/设置年份方法：**

``get/setFullYear()``返回/设置年份，用四位数表示。

```
var mydate=new Date();				//当前时间2014年3月6日
document.write(mydate+"<br>");		//输出当前时间
document.write(mydate.getFullYear()+"<br>"); //输出当前年份
mydate.setFullYear(81);				//设置年份
document.write(mydate+"<br>");		//输出年份被设定为0081年
```

注意：不同浏览器，mydate.setFullYear(81)结果不同，年份被设定为0081或81两种情况。

结果：

```
Thu Mar 06 2014 10:57:47 GMT+0800
2014
Thu Mar 06 0081 10:57:47 GMT+0800
```

注意：

1.结果格式依次为：星期、月、日、年、时、分、秒、时区。

2.不同浏览器，时间格式有差异。

#### 返回星期方法

**getDay()**返回星期，返回的是0-6的数字，0表示星期天。如果要返回相对应"星期"，通过数组完成，代码如下：

```html
<script>
	var mydate=new Date(); //定义日期对象 2014年3月7日星期五
  	var weekday=["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
  //定义数组对象，给每个数组项赋值
  	var mynum=mydate.getDay(); //返回值存储在变量mynum中
  	document.write(mydate.getDay()); //输出getDay()获取值
  	document.write("今天是："+weekday[mynum]);
</script>
```

结果：

```
5
今天是：星期五
```

#### 返回/设置时间方法

**get/setTime()**返回/设置时间，单位毫秒数，计算从1970年1月1日零时到日期对象所指的日期的毫秒数。

如果将目前日期对象的时间推迟1小时，代码如下：

```html
<script>
	var mydate=new Date();
  	document.write("当前时间："+mydate+"<br>");
  	mydate.setTime(mydate.getTime()+60*60*1000);
  	document.write("推迟一小时时间："+mydate);
</script>
```

结果：

当前时间：Thu Mar 6 11:46:27 UTC+0800 2014

推迟一小时时间：Thu Mar 6 12:46:27 UTC+0800 2014

**注意:**

1.一小时 60 分，一分 60 秒，一秒 1000 毫秒

2.时间推迟 1 小时,就是: “x.setTime(x.getTime() + 60 * 60 * 1000);”

### 6.3 String字符串对象

在之前的学习中已经使用字符串对象了，定义字符串的方法就是直接赋值。比如：

```
var mystr = "I love JavaScript!"
```

定义mystr字符串后，我们就可以访问它的属性和方法。

**访问字符串对象的属性length:**

stringObject.length; 返回该字符串的长度。

```
var mystr="Hello World!";
var myl=mystr.length;
```

以上代码执行后，myl 的值将是：12

**访问字符串对象的方法：**

使用 String 对象的 toUpperCase() 方法来将字符串小写字母转换为大写：

```
var mystr="Hello world!";
var mynum=mystr.toUpperCase();
以上代码执行后，mynum 的值是：HELLO WORLD!
```

转换为小写：toLowerCase()

#### 返回指定位置的字符charAt()

charAt()方法可返回指定位置的字符。返回的字符是长度为1的字符串。

**语法：**

``stringObject.charAt(index)``

**参数说明：**

| 参数    | 描述                            |
| ----- | ----------------------------- |
| index | 必需。表示字符串中某个位置的数字，即字符在字符串中的下标。 |

**注意：**1.字符串中第一个字符的下标是0.最后一个字符的下标为字符串长度减一（string.length-1）。

​	    2.如果参数index不在0与string.length-1之间，该方法将返回一个空字符串。

如：在字符串"I love JavaScript!"中，返回位置2的字符：

```html
<script>
	var mystr="I love JavaScript!";
  	document.write(mystr.charAt(2));
</script>
```

**注意：**一个空格也算一个字符。

以上代码的运行结果：

```
l
```

```html
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>string对象 </title>
  <script type="text/javascript">
  var mystr="I love JavaScript!"
  document.write(mystr.charAt(mystr.length-1));
</script>
</head>
<body>
</body>
</html>
```

#### 返回指定的字符串首次出现的位置indexOf()

indexOf()方法可返回某个指定的字符串值在字符串中首次出现的位置。

**语法：**

``stringObject.indexOf(substring,startpos)``

**参数说明：**

| 参数        | 描述                                       |
| --------- | ---------------------------------------- |
| substring | 必需。规定需检查的字符串值                            |
| startpos  | 可选的整数参数。规定在字符串中开始检索的位置。它的合法取值是0到stringObject.length-1。如省略该参数，则将从字符串的首字符开始检索 |

**说明：**

1.该方法将从头到尾地检索字符串stringObject，看他是否含有子串substring。

2.可选参数，从stringObject的startpos位置开始查找substring，如果没有此参数将从stringObject的开始位置查找。

3.如果找到一个substring，则返回substring的第一次出现的位置。stringObject中的字符位置是从0开始的。

**注意：**

1.indexOf()方法区分大小写。

2.如果要检索的字符串值没有出现，则该方法返回-1.

例如：对"I love JavaScript!"字符串内进行不同的检索：

```html
<script>
	var str="I love JavaScript!";
  	document.write(str.indexOf("I")+"<br />");
    document.write(str.indexOf("v")+"<br />");
  	document.write(str.indexOf("v",8)>");
</script>"
```

以上代码的输出：

```
0
4
9
```

#### 字符串分割split()

split()方法将字符串分割为字符串数组，并返回此数组。

**语法：**

``stringObject.split(separator,limit)``

**参数说明：**

| 参数        | 描述                                       |
| --------- | ---------------------------------------- |
| separator | 必需。从该参数指定的地方分割stringObject               |
| limit     | 可选参数，分割的次数，如设置该参数，返回的子串不会多于这个参数指定的数组，如果无此参数为不限制次数 |

**注意：**如果把空字符串（""）用作separator，那么stringObject重的每个字符之间都会被分割。

使用指定符号分割字符串：

```
var mystr="www.imooc.com";
document.write(mystr.split(".")+"<br>");
document.write(mystr.split(".",2)+"<br>");
```

**运行结果:**

```
www,imooc,com
www,imooc
```

将字符串分割为字符，代码如下：

```
document.write(mystr.split("")+"<br>");
document.write(mystr.split("", 5));
```

运行结果:

```
w,w,w,.,i,m,o,o,c,.,c,o,m
w,w,w,.,i
```

#### 提取字符串substring()

substring() 方法用于提取字符串中介于两个指定下标之间的字符。

**语法:**

```
stringObject.substring(startPos,stopPos) 
```

**参数说明:**

![img](http://img.mukewang.com/532bf1bb000151af04450082.jpg)

**注意：**

\1. 返回的内容是从 start开始(包含start位置的字符)到 stop-1 处的所有字符，其长度为 stop 减start。

\2. 如果参数 start 与 stop 相等，那么该方法返回的就是一个空串（即长度为 0 的字符串）。

\3. 如果 start 比 stop 大，那么该方法在提取子串之前会先交换这两个参数。

使用 substring() 从字符串中提取字符串，代码如下：

```
<script type="text/javascript">
  var mystr="I love JavaScript";
  document.write(mystr.substring(7));
  document.write(mystr.substring(2,6));
</script>
```

**运行结果:**

```
JavaScript
love
```

#### 提取指定数目的字符substr()

substr() 方法从字符串中提取从 startPos位置开始的指定数目的字符串。

**语法:**

```
stringObject.substr(startPos,length)

```

**参数说明:**

![img](http://img.mukewang.com/532bf2e00001105305100098.jpg)

**注意：**如果参数startPos是负数，从字符串的尾部开始算起的位置。也就是说，-1 指字符串中最后一个字符，-2 指倒数第二个字符，以此类推。

如果startPos为负数且绝对值大于字符串长度，startPos为0。

使用 substr() 从字符串中提取一些字符，代码如下：

```
<script type="text/javascript">
  var mystr="I love JavaScript!";
  document.write(mystr.substr(7));
  document.write(mystr.substr(2,4));
</script>
```

**运行结果：**

```
JavaScript!
love
```

### 6.4 Math对象

Math对象，提供对数据的数学计算。

使用 Math 的属性和方法，代码如下：

### 

```
<script type="text/javascript">
  var mypi=Math.PI; 
  var myabs=Math.abs(-15);
  document.write(mypi);
  document.write(myabs);
</script>
```

**运行结果:**

```
3.141592653589793
15
```

**注意：**Math 对象是一个固有的对象，无需创建它，直接把 Math 作为对象使用就可以调用其所有属性和方法。这是它与Date,String对象的区别。

Math 对象属性

![img](http://img.mukewang.com/532fe7cf0001e7b505170269.jpg)

Math 对象方法

![img](http://img.mukewang.com/532fe841000174db05160622.jpg)

#### 向上取整ceil()

ceil() 方法可对一个数进行向上取整。

**语法:**

```
Math.ceil(x)
```

**参数说明:**

![img](http://img.mukewang.com/532fe8e00001e4e605230063.jpg)

**注意：**它返回的是大于或等于x，并且与x最接近的整数。

我们将把 ceil() 方法运用到不同的数字上，代码如下：

```
<script type="text/javascript">
  document.write(Math.ceil(0.8) + "<br />")
  document.write(Math.ceil(6.3) + "<br />")
  document.write(Math.ceil(5) + "<br />")
  document.write(Math.ceil(3.5) + "<br />")
  document.write(Math.ceil(-5.1) + "<br />")
  document.write(Math.ceil(-5.9))
</script>
```

**运行结果：**

```
1
7
5
4
-5
-5
```

#### 向下取整floor()

floor() 方法可对一个数进行向下取整。

**语法:**

```
Math.floor(x)
```

**参数说明：**

![img](http://img.mukewang.com/532fe8e00001e4e605230063.jpg)

**注意：**返回的是小于或等于x，并且与 x 最接近的整数。

我们将在不同的数字上使用 floor() 方法，代码如下:

```
<script type="text/javascript">
  document.write(Math.floor(0.8)+ "<br>")
  document.write(Math.floor(6.3)+ "<br>")
  document.write(Math.floor(5)+ "<br>")
  document.write(Math.floor(3.5)+ "<br>")
  document.write(Math.floor(-5.1)+ "<br>")
  document.write(Math.floor(-5.9))
</script>
```

**运行结果：**

```
0
6
5
3
-6
-6
```

#### 四舍五入round()

round() 方法可把一个数字四舍五入为最接近的整数。

**语法:**

```
Math.round(x)
```

**参数说明：**

![img](http://img.mukewang.com/532feb70000180ab03210059.jpg)

**注意：**

\1. 返回与 x 最接近的整数。

\2. 对于 0.5，该方法将进行上舍入。(5.5 将舍入为 6)

**注意：**

\1. 返回与 x 最接近的整数。

\2. 对于 0.5，该方法将进行上舍入。(5.5 将舍入为 6)

3. 如果 x 与两侧整数同等接近，则结果接近 +∞方向的数字值 。(如 -5.5 将舍入为 -5; -5.52 将舍入为 -6),如下图:

![img](http://img.mukewang.com/53fc4cc8000169a907530196.jpg)

#### 随机数random()

```
random() 方法可返回介于 0 ~ 1（大于或等于 0 但小于 1 )之间的一个随机数。
```

**语法：**

```
Math.random();
```

**注意：**返回一个大于或等于 0 但小于 1 的符号为正的数字值。

我们取得介于 0 到 1 之间的一个随机数，代码如下：

```
<script type="text/javascript">
  document.write(Math.random());
</script>
```

**运行结果：**

```
0.190305486195328  
```

**注意:**因为是随机数，所以每次运行结果不一样，但是0 ~ 1的数值。

获得0 ~ 10之间的随机数，代码如下:

```
<script type="text/javascript">
  document.write((Math.random())*10);
</script>
```

**运行结果：**

```
8.72153625893887
```

### 6.5 数组对象

数组对象是一个对象的集合，里边的对象可以是不同类型的。数组的每一个成员对象都有一个“下标”，用来表示它在数组中的位置，是从零开始的

**数组定义的方法：**

\1. 定义了一个空数组:

```
var  数组名= new Array();
```

\2. 定义时指定有n个空元素的数组：

```
var 数组名 =new Array(n);
```

3.定义数组的时候，直接初始化数据：

```
var  数组名 = [<元素1>, <元素2>, <元素3>...];
```

我们定义myArray数组，并赋值，**代码如下：**

```
var myArray = [2, 8, 6]; 
```

**数组元素使用：**

```
数组名[下标] = 值;
```

**注意**: 数组的下标用方括号括起来，从0开始。

length 用法：<数组对象>.length；返回：数组的长度，即数组里有多少个元素。它等于数组里最后一个元素的下标加一。

**数组方法：**

![img](http://img.mukewang.com/533295ab0001dead05190599.jpg)

#### 数组连接concat()

concat() 方法用于连接两个或多个数组。此方法返回一个新数组，不改变原来的数组。

**语法**

```
arrayObject.concat(array1,array2,...,arrayN)
```

**参数说明：**

![img](http://img.mukewang.com/5332968d0001d39b05010137.jpg)

**注意:  **该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本。

我们创建一个数组，将把 concat() 中的参数连接到数组 myarr 中，代码如下：

```
<script type="text/javascript">
  var mya = new Array(3);
  mya[0] = "1";
  mya[1] = "2";
  mya[2] = "3";
  document.write(mya.concat(4,5)+"<br>");
  document.write(mya); 
</script>
```

**运行结果：**

```
1,2,3,4,5
1,2,3
```

我们创建了三个数组，然后使用 concat() 把它们连接起来，代码如下：

```
<script type="text/javascript">
  var mya1= new Array("hello!")
  var mya2= new Array("I","love");
  var mya3= new Array("JavaScript","!");
  var mya4=mya1.concat(mya2,mya3);
  document.write(mya4);
</script>
```

**运行结果：**

```
hello!,I,love,JavaScript,!
```

#### 指定分隔符连接数组元素join()

join()方法用于把数组中的所有元素放入一个字符串。元素是通过指定的分隔符进行分隔的。

**语法：**

```
arrayObject.join(分隔符)
```

**参数说明:**

![img](http://img.mukewang.com/533297ff0001516905150059.jpg)

注意：返回一个字符串，该字符串把数组中的各个元素串起来，用<分隔符>置于元素与元素之间。这个方法不影响数组原本的内容。 

```
<script type="text/javascript">
  var myarr = new Array(3);
  myarr[0] = "I";
  myarr[1] = "love";
  myarr[2] = "JavaScript";
  document.write(myarr.join());
</script>
```

**运行结果：**

```
I,love,JavaScript
```

我们将使用分隔符来分隔数组中的元素，代码如下：

```
<script type="text/javascript">
  var myarr = new Array(3)
  myarr[0] = "I";
  myarr[1] = "love";
  myarr[2] = "JavaScript";
  document.write(myarr.join("."));
</script>
```

**运行结果：**

```
I.love.JavaScript
```

#### 颠倒数组元素顺序reverse()

reverse() 方法用于颠倒数组中元素的顺序。

**语法：**

```
arrayObject.reverse()
```

**注意：**该方法会改变原来的数组，而不会创建新的数组。

#### 选定元素slice()

slice() 方法可从已有的数组中返回选定的元素。

**语法**

```
arrayObject.slice(start,end)
```

**参数说明：**

![img](http://img.mukewang.com/533299680001637b05160145.jpg)

1.返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。

2. 该方法并不会修改数组，而是返回一个子数组。

#### 数组排序sort()

**sort()**方法使数组中的元素按照一定的顺序排列。

**语法:**

```
arrayObject.sort(方法函数)
```

**参数说明：**

![img](http://img.mukewang.com/53329a2a000127f705170060.jpg)

1.如果不指定<方法函数>，则按unicode码顺序排列。

2.如果指定<方法函数>，则按<方法函数>所指定的排序方法排序。

```
myArray.sort(sortMethod);
```

**注意: **该函数要比较两个值，然后返回一个用于说明这两个值的相对顺序的数字。比较函数应该具有两个参数 a 和 b，其返回值如下： 

  若返回值<=-1，则表示 A 在排序后的序列中出现在 B 之前。
  若返回值>-1 && <1，则表示 A 和 B 具有相同的排序顺序。
  若返回值>=1，则表示 A 在排序后的序列中出现在 B 之后。

```
<script type="text/javascript">
  function sortNum(a,b) {
  return a - b;
 //升序，如降序，把“a - b”该成“b - a”
}
 var myarr = new Array("80","16","50","6","100","1");
  document.write(myarr + "<br>");
  document.write(myarr.sort(sortNum));
</script>
```

**运行结果：**

```
80,16,50,6,100,1
1,6,16,50,80,100
```

### 6.6 练习

某班的成绩出来了，现在老师要把班级的成绩打印出来。

**效果图:**

```
XXXX年XX月X日 星期X--班级总分为:81
```

**格式要求：**

1、显示打印的日期。 格式为类似“XXXX年XX月XX日 星期X” 的当前的时间。

2、计算出该班级的平均分（保留整数）。

**同学成绩数据如下：**

"小明:87; 小花:81; 小红:97; 小天:76;小张:74;小小:94;小西:90;小伍:76;小迪:64;小曼:76"

```html
<!DOCTYPE  HTML>
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>系好安全带,准备启航</title>

<script type="text/javascript">
    var mydate=new Date();
    var myyear=mydate.getFullYear();
    var mymonth=mydate.getMonth()+1;
    var myday=mydate.getDate();
    var weekend=['星期天','星期一','星期二','星期三','星期四','星期五','星期六'];
    var myweek=weekend[mydate.getDay()];
  //通过javascript的日期对象来得到当前的日期，并输出。
  //成绩是一长窜的字符串不好处理，找规律后分割放到数组里更好操作哦
  var scoreStr = "小明:87;小花:81;小红:97;小天:76;小张:74;小小:94;小西:90;小伍:76;小迪:64;小曼:76";
    var d=new Array();
    var e=new Array();
    var sum=0;
    var avg;
    d=scoreStr.split(";");
    for(var i=0;i<d.length;i++)
    {
        e[i]=d[i].split(":");
        sum=sum+parseInt(e[i][1]);
    }
    avg=Math.floor(sum/d.length);
  //从数组中将成绩撮出来，然后求和取整，并输出。
  document.write(myyear+"年"+mymonth+"月"+myday+"日"+" "+myweek+"--班级总分为："+avg)


</script>
</head>
<body>
</body>
</html>
```

## 第七章 浏览器对象

### 7.1 window对象

window对象是BOM的核心，window对象指当前的浏览器窗口。

**window对象方法:**

| 方法              | 描述                      |
| --------------- | ----------------------- |
| alter()         | 显示带有一段消息和一个确认按钮的警告框     |
| prompt()        | 显示可提示用户输入的对话框           |
| confirm()       | 显示带有一段消息以及确认按钮和取消按钮的对话框 |
| open()          | 打开一个新的浏览器窗口或查找一个已命名的窗口  |
| close()         | 关闭浏览器窗口                 |
| print()         | 打印当前窗口的内容               |
| focus()         | 把键盘焦点给予一个窗口             |
| blur()          | 把键盘焦点从顶层窗口移开            |
| moveBy()        | 可相对窗口的当前坐标把它移动指定的像素     |
| moveTo()        | 把窗口的左上角移动到一个指定的坐标       |
| resizeBy()      | 按照指定的像素调整窗口的大小          |
| resizeTo()      | 把窗口的大小调整到指定的宽度和高度       |
| scrollBy()      | 按照指定的像素值来滚动内容           |
| scrollTo()      | 把内容滚动到指定的坐标             |
| setInterval()   | 每隔指定的时间执行代码             |
| setTimeout()    | 在指定的延迟时间之后来执行代码         |
| clearInterval() | 取消setInterval()的设置      |
| clearTimeout()  | 取消setTimeout()的设置       |

### 7.2  JavaScript计时器

在JavaScript中，我们可以在设定的时间间隔之后来执行代码，而不是在函数被调用后立即执行。

**计时器类型：**

一次性计时器：仅在指定的延迟时间之后触发一次。

间隔性触发计时器：每隔一定的时间间隔就触发一次。

**计时器方法：**

| 方法              | 说明                |
| --------------- | ----------------- |
| setTimeout()    | 指定的延迟时间之后来执行代码    |
| clearTimeout()  | 取消setTimeout()设置  |
| setInterval()   | 每隔指定的时间执行代码       |
| clearInterval() | 取消setInterval()设置 |

### 7.3  计时器setInterval()

在执行时,从载入页面后每隔指定的时间执行代码。

**语法:**

```
setInterval(代码,交互时间);
```

**参数说明：**

1.代码：要调用的函数或要执行的代码串

2.交互时间：周期性执行或调用表达式之间的时间间隔，以毫秒计（1s=1000ms）

**返回值：**

一个可以传递给clearInterval()从而取消对“代码”的周期性执行的值。

**调用函数格式**（假设有一个clock()函数）：

```
setInterval("clock()",1000)
或
setInterval(clock,1000)
```

我们设置一个计时器，每隔100毫秒调用clock()函数，并将时间显示出来，代码如下：

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>计时器</title>
  <script>
  	var int=setInterval(clock,100)
    function clock(){
      var time=new Date();
      document.getElementById("clock").value=time;
    }
  </script>
</head>
  <body>
    <form>
    	<input type="text" id="clock" size="50" />
    </form>
  </body>
</html>
```

#### 练习

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>定时器</title>
<script type="text/javascript">
  var attime;
  function clock(){
    var time=new Date();          
    var attime= time.getHours()+":"+time.getMinutes()+":"+time.getSeconds();
    document.getElementById("clock").value = attime;
  }
  setInterval(clock,1000)
</script>
</head>
<body>
<form>
<input type="text" id="clock" size="50"  />
</form>
</body>
</html>
```

### 7.4 取消计时器clearInterval()

clearInterval() 方法可取消由 setInterval() 设置的交互时间。

**语法：**

```
clearInterval(id_of_setInterval)
```

**参数说明：**

id_of_setInterval：由setInterval()返回的ID值。

每隔100毫秒调用clock()函数，当点击按钮时，停止时间，代码如下：

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>计时器</title>
  <script>
    function clock(){
      var time=new Date();
      document.getElementById("clock").value=time;
    }
    var i=setInterval("clock()",100);
    //每隔100毫秒调用clock函数，并将返回值赋值给i
  </script>
</head>
<body>
  <form>
    <input type="text" id="clock" size="50"  />
    <input type="button" value="Stop" onclick="clearInterval(i)"  />
  </form>
</body>
</html>
```

### 7.5 计时器setTimeout()

setTimeout()计时器，在载入后延迟指定时间后,去执行一次表达式,仅执行一次。

**语法:**

```
setTimeout(代码,延迟时间);
```

**参数说明：**

1.要调用的函数或要执行的代码串。

2.延时时间：在执行代码前需等待的时间，以毫秒为单位（1s=1000ms)。

要创建一个运行于无穷循环中的计数器，我们需要编写一个函数来调用其自身。在下面的代码，当按钮被点击后，输入域便从0开始计数。

```html
<!DOCTYPE HTML>
<html>
<head>
  <script>
  	var num=0;
    function numcount(){
      document.getElementById('txt').value=num;
      num=num+1;
      setTimeout("numcount()",1000);
    }
  </script>
</head>
  <body>
    <form>
    <input type="text" id="txt" />
    <input type="button" value="Start" onclick="numcount()" />
    </form>
  </body>
</html>
```

#### 练习

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>计时器</title>
<script type="text/javascript">
  var num=0;
  function startCount() {
    document.getElementById('count').value=num;
    num=num+1;
    setTimeout("startCount()",1000); 
  }
  setTimeout("startCount()",1000); //外部触发
</script>
</head>
<body>
<form>
<input type="text" id="count" />
</form>
</body>
</html>
```

### 7.6 取消计时器clearTimeout()

setTimeout()和clearTimeout()一起使用，停止计时器。

**语法:**

```
clearTimeout(id_of_setTimeout)
```

**参数说明:**
**id_of_setTimeout：**由 setTimeout() 返回的 ID 值。该值标识要取消的延迟执行代码块。

### 7.7 History对象

history对象记录了用户曾经浏览过的页面（URL），并可以实现浏览器前进与后退相似导航的功能。

**注意：**从窗口被打开的那一刻开始记录，每个浏览器窗口、每个标签页乃至每个框架，都有自己的history对象与特定的window对象关联。

**语法：**

``window.history.[属性][方法]``

**注意：**window可以省略。

**History 对象属性**

| 属性     | 描述               |
| ------ | ---------------- |
| length | 返回浏览器历史列表中的URL数量 |

**History对象方法**

| 方法        | 描述                   |
| --------- | -------------------- |
| back()    | 加载history列表中的前一个URL  |
| forward() | 加载history列表中的下一个URL  |
| go()      | 加载history列表中的某个具体的页面 |

使用length属性，当前窗口的浏览历史总长度，代码如下：

```
<script>
	var HL=window.history.length;
	document.write(HL);
</script>
```

#### 返回前一个浏览的页面

back()方法，加载history列表中的前一个URL。

**语法：**

```
window.history.back();
```

比如，返回前一个浏览的页面，**代码如下：**

```
window.history.back();
```

**注意：等同于点击浏览器的倒退按钮。**

back()相当于go(-1),**代码如下:**

```
window.history.go(-1);
```

#### 返回下一个浏览的页面

forward()方法，加载 history 列表中的下一个 URL。

如果倒退之后，再想回到倒退之前浏览的页面，则可以使用forward()方法,**代码如下:**

```
window.history.forward();
```

**注意：等价点击前进按钮。**

forward()相当于go(1),**代码如下:**

```
window.history.go(1);
```

#### 返回浏览历史中的其他页面

go()方法，根据当前所处的页面，加载 history 列表中的某个具体的页面。

**语法：**

```
window.history.go(number);
```

**参数：**

![img](http://img.mukewang.com/5354947e00011a9a06490153.jpg)

### 7.8 Location对象

location用于获取或设置窗体的URL，并且可以用于解析URL。

**语法：**

``location.[属性][方法]``

**location对象属性图示:**

![img](http://img.mukewang.com/53605c5a0001b26909900216.jpg)

**location 对象属性：**

| 属性       | 描述                       |
| -------- | ------------------------ |
| hash     | 设置或返回从井号（#）开始的URL（锚）     |
| host     | 设置或返回主机名和当前URL的端口号       |
| hostname | 设置或返回当前URL的主机名           |
| href     | 设置或返回完整的URL              |
| pathname | 设置或返回当前URL的路径部分          |
| port     | 设置或返回当前URL的端口号           |
| protocol | 设置或返回当前URL的协议            |
| search   | 设置或返回从问好（?）开始的URL（查询的部分） |

**location 对象方法:**

| 属性        | 描述          |
| --------- | ----------- |
| assign()  | 加载新的文档      |
| reload()  | 重新加载当前文档    |
| replace() | 用心的文档替换当前文档 |

#### 练习

获取当前显示文档的URL,并输出。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>location</title>
</head>
 <script type="text/javascript">
    document.write(location.href);    
     
 </script>

<body>
</body>
</html>
```

### 7.9 Navigator对象

Navigator对象包含有关浏览器的信息，通常用于检测浏览器与操作系统的版本。

**对象属性：**

| 属性          | 描述                         |
| ----------- | -------------------------- |
| appCodeName | 浏览器代码名的字符串表示               |
| appName     | 返回浏览器的名称                   |
| appVersion  | 返回浏览器的平台和版本信息              |
| platform    | 返回运行浏览器的操作系统平台             |
| userAgent   | 返回由客户机发送服务器的user-agent头部的值 |

查看浏览器的名称和版本，代码如下：

```
<script>
	var browser=navigator.appName;
	var b_version=navigator.appVersion;
	document.write("Browser name"+browser);
	document.write("<br>");
	document.write("Browser version"+b_version);
</script>
```

#### userAgent

返回用户代理头的字符串表示（就是包括浏览器版本信息等的字符串）

**语法**

```
navigator.userAgent
```

几种浏览的user_agent.，像360的兼容模式用的是IE、极速模式用的是chrom的内核。

![img](http://img.mukewang.com/535a3a4a0001e03f06870189.jpg)

使用userAgent判断使用的是什么浏览器(假设使用的是IE8浏览器),**代码如下:**

```javascript
function validB(){
  var u_agent=navigator.userAgent;
  var B_name="Failed to identify the browser";
  if(u_agent.indexOf("Firefox")>-1)
  {
    B_name="Firefox";
  }
  else if(u_agent.indexOf("Chrome")>-1)
  {
    B_name="Chrome";
  }
  else if(u_agent.indexOf("MSIE")>-1&&u_agent.indexOf("Trident")>-1)
  {
    B_name="IE(8-10)";
  }
  document.write("B_name:"+B_name+"<br>");
  document.write("u_agent:"+u_agent+"<br>");
}
```

### 7.10 screen对象

screen对象用于获取用户的屏幕信息。

**语法：**

``window.screen.属性``

**对象属性：**

| 属性          | 描述                                    |
| ----------- | ------------------------------------- |
| availHeight | 窗口可以使用的屏幕高度，单位像素                      |
| availWidth  | 窗口可以使用的屏幕宽度，单位像素                      |
| colorDepth  | 用户浏览器表示的颜色位数，通常为32位（每像素的位数）           |
| pixelDepth  | 用户浏览器表示的颜色位数，通常为32位（每像素的位数）（IE不支持此属性） |
| height      | 屏幕的高度，单位像素                            |
| width       | 屏幕的宽度，单位像素                            |

#### 屏幕分辨率的高和宽

window.screen对象包含有关用户屏幕的信息。

1.screen.height返回屏幕分辨率的高

2.screen.width返回屏幕分辨率的宽

**注意：**

1.单位以像素计

2.window.screen对象在编写时可以不使用window这个前缀。

```html
<script>
	document.write("屏幕宽度："+screen.width+"px<br />");
  	document.write("屏幕高度："+screen.height+"px<br />");
</script>
```

#### 屏幕可用高和宽度

1.screen.availWidth属性返回访问者屏幕的宽度，以像素计，减去界面特性，比如任务栏。

2.screen.availHeight属性返回访问者屏幕的高度，以像素计，减去界面特性，比如任务栏。

**注意：**

不同系统的任务栏默认高度不一样，及任务栏的位置可在屏幕上下左右任何位置，所以有可能可用宽度和高度不一样。

### 7.11 练习

制作一个跳转提示页面：

**要求：**

1.如果打开该页面后，如果不做任何操作则5秒后自动跳转到一个新的地址。

2.如果点击“返回”按钮则返回前一个页面。

```html
<!DOCTYPE html>
<html>
 <head>
  <title>浏览器对象</title>  
  <meta http-equiv="Content-Type" content="text/html; charset=gkb"/>   
 </head>
 <body>
  <!--先编写好网页布局-->
    <h1>操作成功</h1>
    <p><span id="second"></span>秒后回到主页<a href="window.history.back()">返回</a></p>
 
  <script type="text/javascript">  
    var mysc=5;
    function startcount(){
        document.getElementById("second").innerHTML=mysc;
        mysc--;
        if(mysc==0){
            window.location.assign("http://www.imooc.com");
        }
        setTimeout("startcount()",1000);
    }
    setTimeout("startcount()",1000);
   //获取显示秒数的元素，通过定时器来更改秒数。

   //通过window的location和history对象来控制网页的跳转。
   
 </script> 
</body>
</html>
```

## 第八章 DOM对象，控制HTML元素

### 8.1 认识DOM

文档对象模型DOM（Document Object Model）定义访问和处理HTML文档的标准方法。DOM 将HTML文档呈现为带有元素、属性和文本的树结构（节点树）。

![img](http://img.mukewang.com/5375ca640001c67307860420.jpg)

**将HTML代码分解为DOM节点层次图:**

![img](http://img.mukewang.com/5375ca7e0001dd8d04830279.jpg)

**HTML****文档可以说由节点构成的集合，DOM节点有:**

**1. ****元素节点：**上图中<html>、<body>、<p>等都是元素节点，即标签。

**2. ****文本节点:**向用户展示的内容，如<li>...</li>中的JavaScript、DOM、CSS等文本。

**3. ****属性节点:**元素属性，如<a>标签的链接属性href="http://www.imooc.com"。

**节点属性:**

![img](http://img.mukewang.com/5375c953000117ee05240129.jpg)

**遍历节点树:**

![img](http://img.mukewang.com/53f17a6400017d2905230219.jpg)

**以上图ul为例，它的父级节点body,它的子节点3个li,它的兄弟结点h2、P。**

**DOM操作:**

![img](http://img.mukewang.com/538d29da000152db05360278.jpg)

**注意:**前两个是document方法。

### 8.2 getElementByName()方法

返回带有指定名称的节点对象的集合。

**语法：**

```
document.getElementsByName(name)
```

与getElementById() 方法不同的是，通过元素的 name 属性查询元素，而不是通过 id 属性。

**注意:**

1. 因为文档中的 name 属性可能不唯一，所有 getElementsByName() 方法返回的是元素的数组，而不是一个元素。

2.和数组类似也有length属性，可以和访问数组一样的方法来访问，从0开始。

```html
<!DOCTYPE HTML>
<html>
<head>
<script type="text/javascript">
function getnum(){
  var mynode= document.getElementsByName("myt");  
  alert(mynode.length);
}
</script>
</head>
<body>
<input name="myt" type="text" value="1">
<input name="myt" type="text" value="2">
<input name="myt" type="text" value="3">
<input name="myt" type="text" value="4">
<input name="myt" type="text" value="5">
<input name="myt" type="text" value="6">

<br />
<input type="button" onclick="getnum()" value="看看有几项？" />
</body>
</html>
```

### 8.3 getElementsByTagName()方法

返回带有指定标签名的节点对象的集合。返回元素的顺序是它们在文档中的顺序。

**语法:**

```
document.getElementsByTagName(Tagname)
```

**说明:**

1.Tagname是标签的名称，如p、a、img等标签名。

2.和数组类似也有length属性，可以和访问数组一样的方法来访问，所以从0开始。

```html
<!DOCTYPE HTML>
<html>
  <head>
    <title>JavaScript</title>
    <meta http-equiv="Content-Type" content="text/html;charset=UTF-8" />
  </head>
  <body>
    <p id="intro">我的课程</p>
    <ul>
      <li>JavaScript</li>
      <li>JQuery</li>
      <li>HTML</li>
      <li>JAVA</li>
      <li>PHP</li>
    </ul>
    <script>
      //获取所有的li集合
      var list=document.getElementsByTagName("li");
      //访问无序列表：[0]索引
      li=list[0];
      //获取list的长度
      document.write(list.length);
      //弹出li节点对象的内容
      document.write(li.innerHTML);
    </script>
  </body>
</html>
```

#### 练习

**使用三种获取节点的方法**

```html
<!DOCTYPE HTML>
<html>  
<head>  
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
<title>JavaScript</title>  
</head>  
<body>  
    
        <form name="Input">
            <table align="center" width="500px" height="50%" border="1">
                <tr>
                    <td align="center" width="100px">
                        学号:
                    </td>
                    <td align="center" width="300px">
                        <input type="text" id=userid name="user" onblur="validate();">
                        <div id=usermsg></div>
                    </td>
                </tr>
                <tr>
                    <td align="center" width="100px">
                        姓名:
                    </td>
                        <td align="center">
                        <input type="text" name="name">
                    </td>
                </tr>
                <tr>
                    <td align="center" width="%45">
                        性别:
                    </td>
                    <td align="center">
                        <input type="radio" name="sex" value="男">
                        男
                        <input type="radio" name="sex" value="女">
                        女
                    </td>
                </tr>
                <tr>
                    <td align="center" width="30%">
                        年龄:
                    </td>
                    <td align="center" width="300px">
                        <input type="text" name="age">
                    </td>
                </tr>
                <tr>
                    <td align="center" width="100px">
                        地址:
                    </td>
                    <td align="center" width="300px">
                        <input type="text" name="addr">
                    </td>
                </tr>

            </table>
        </form>
        <h1 id="myHead" onclick="getValue()">
            看看三种获取节点的方法?
        </h1>
        <p>
            点击标题弹出它的值。
        </p>
        <input type="button" onclick="getElements()"
            value="看看name为sex的节点有几个?" />
        <Br>
        <input type="button" onclick="getTagElements()"
            value="看看标签名为input的节点有几个?" />
            
     <script type="text/javascript">
         function getValue()
          {
              var myH=document.getElementById("myHead");
              alert(myH.innerHTML)
          }
          function getElements()
          {
              var myS=document.getElementsByName("sex");
              alert(myS.length);
          }

          function getTagElements()
          {
              var myI=document.getElementsByTagName("input")
              alert(myI.length);
          }
         
     </script>        

    </body>
</html>
```

### 8.4 区别getElementByID,getElementsByName,getElementsByTagName

1.ID是一个人的身份证，是唯一的，可以通过getElementById获取的是指定的一个人

2.Name是他的名字，可以重复。所以通过getElementsByName获取名字相同的人集合。

3.TagName可看似某类，getElementsByTagName获取相同类的人集合。

```
<input type="checkbox" name="hobby" id="hobby1"> 音乐
```

input标签是类别，name属性是姓名，id属性是身份证

| 方法                   | 说明               | 获得   |
| -------------------- | ---------------- | ---- |
| getElementById       | 通过指定id获得元素       | 一个   |
| getElementsByName    | 通过元素名称name属性获得元素 | 一组   |
| getElementsByTagName | 通过标签名称获得元素       | 一组   |

**注意：**方法区分大小写

#### 练习

1.在第27行处补充完整，实现当点击"全选"按钮时，将选中所有的复选项。

```
提示:document.getElementsByTagName("input")获取的是所有input标签，包括复选项和按钮，所以要判断是否是复选项，如是选中。
```

2.在第33行处补充完整，实现当点击"全不选"按钮时，将取消所有选中的复选项。

3.在第40行处补充完整，在文本框中输入输入1-6数值，当点击"确定"按钮时，根据输入的数值，通过id选中相应的复选项。

```html
<!DOCTYPE HTML>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=gb2312">
        <title>无标题文档</title>
    </head>
    
    <body>
        <form>
          请选择你爱好:<br>
          <input type="checkbox" name="hobby" id="hobby1">  音乐
          <input type="checkbox" name="hobby" id="hobby2">  登山
          <input type="checkbox" name="hobby" id="hobby3">  游泳
          <input type="checkbox" name="hobby" id="hobby4">  阅读
          <input type="checkbox" name="hobby" id="hobby5">  打球
          <input type="checkbox" name="hobby" id="hobby6">  跑步 <br>
          <input type="button" value = "全选" onclick = "checkall();">
          <input type="button" value = "全不选" onclick = "clearall();">
          <p>请输入您要选择爱好的序号，序号为1-6:</p>
          <input id="wb" name="wb" type="text" >
          <input name="ok" type="button" value="确定" onclick = "checkone();">
        </form>
        <script type="text/javascript">
        function checkall(){
            var hobby = document.getElementsByTagName("input");
            {
                for(var i=0;i<hobby.length;i++){
                    if(hobby[i].type=="checkbox")
                    {hobby[i].checked=true;}
                }
            }
          // 任务1 
        }
        function clearall(){
            var hobby = document.getElementsByName("hobby");
            for(var i=0;i<hobby.length;i++){
                hobby[i].checked=false;
            }
         // 任务2    
        }
        
        function checkone(){
            var j=document.getElementById("wb").value;
            if(j>=1&&j<=6)
            {
                var hobby=document.getElementsByTagName("input");
                hobby[j-1].checked=true;
            }
           else
           {alert("输入的数字不合法");}
         // 任务3
        }
        
        </script>
    </body>
</html>
```

### 8.5 getAttribute()方法

通过元素节点的属性名称获取属性的值

**语法：**

``elementNode.getAttribute(name)``

**说明：**

1.elementNode：使用getElementById()、getElementsByTagName()等方法，获取到的元素节点。

2.name：要想查询的元素节点的属性名字

```html
<!DOCTYPE HTML>
<html>
  <head>
  	<meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
    <title>getAttribute</title>
  </head>
  <body>
    <h1 id="alink" title="getAttribute()获取标签的属值" onclick="hattr()">点击我，获取标签的属值</h1>
    <script>
      function hattr(){
        var anode=document.getElementById("alink");
        var attr1=anode.getAttribute("id");
        var attr2=anode.getAttribute("title");
        document.write("h1标签的ID："+attr1+"<br>");
        document.write("h1标签的title："+attr2);
      }
    </script>
  </body>
</html>
```

**运行结果:**

h1标签的ID ：alink
h1标签的title ：getAttribute()获取标签的属值

### 8.6 setAttribute()方法

setAttribute() 方法增加一个指定名称和值的新属性，或者把一个现有的属性设定为指定的值。

**语法：**

```
elementNode.setAttribute(name,value)
```

**说明：**

1.name: 要设置的属性名。

2.value: 要设置的属性值。

**注意：**

1.把指定的属性设置为指定的值。如果不存在具有指定名称的属性，该方法将创建一个新属性。

2.类似于getAttribute()方法，setAttribute()方法只能通过元素节点对象调用的函数。

### 8.7 节点属性

在文档对象模型（DOM）中，每个节点都是一个对象。DOM节点有三个重要的属性：

1.nodeName：节点的名称

2.nodeValue：节点的值

3.nodeType：节点的类型

**一.nodeName属性：**节点的名称，是只读的。

1.元素节点的nodeName与标签名相同

2.属性节点的nodeName是属性的名称

3.文本节点的nodeName永远是#text

4.文档节点的nodeName永远是#document

**二.nodeValue属性：**节点的值

1.元素节点的nodeValue是undefined或null

2.文本节点的nodeValue是文本自身

3.属性节点的nodeValue是属性的值

**三.nodeType属性：**节点的类型，是只读的。以下常用的几种节点类型：

| 元素类型 | 节点类型 |
| ---- | ---- |
| 元素   | 1    |
| 属性   | 2    |
| 文本   | 3    |
| 注释   | 8    |
| 文档   | 9    |

#### 练习

试一试，在\<script>的标签内容，获取所有LI标签，并输出相应节点的名称、节点的值、节点的类型。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>节点属性</title>
</head>
<body>
  <ul>
     <li>javascript</li>
     <li>HTML/CSS</li>
     <li>jQuery</li>     
  </ul>
  <script type="text/javascript">
    var a=document.getElementsByTagName("li");
    for(var i=0;i<a.length;i++)
    {
        document.write("节点名："+a[i].nodeName+"<br />");
        document.write("节点值："+a[i].nodeValue+"<br />");
        document.write("节点类型："+a[i].nodeType+"<br />");
    }
  </script>
</body>
</html>
```

### 8.8 访问子节点childNodes

访问选定元素节点下的所有子节点的列表，返回的值可以看作是一个数组，他具有length属性。

**语法：**

``elementNode.childNodes``

**注意：**

如果选定的节点没有子节点，则该属性返回不包含节点的NodeList。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>节点属性</title>
</head>
  <body>
    <ul>
      <li>javascript</li>
      <li>jQuery</li>
      <li>PHP</li>
    </ul>
    <script>
    	var x=document.getElementsByTagName("ul")[0].childNodes; //getElementsByTagName("ul")得到的是数组，需要数组中的元素所以需要[0]
      document.write("UL子节点个数："+x.length+"<br />");
      document.write("节点类型："+x[0].nodeType);
    </script>
  </body>
</html>
```

**运行结果:**

**IE:**

```
  UL子节点个数:3
  节点类型:1
```

**其它浏览器:**

```
   UL子节点个数:7
   节点类型:3
```

**注意：**

1.IE全系列、firefox、chrome、opera、safari兼容问题

2.节点之间的空白符，在firefox、chrome、opera、safari浏览器是文本节点，所以IE是3，其他浏览器是7

![img](http://img.mukewang.com/538d2b8a000163e303430127.jpg)

### 8.9 访问子节点的第一和最后项

一.  ``firstChild``属性返回'childNodes'数组的第一个子节点。如果选定的节点没有子节点，则该属性返回null。

**语法：**

``node.firstChild``

说明：与elementNode.childNodes[0]是同样的效果。

二.``lastChild``属性返回'childNodes'数组的最后一个子节点。如果选定的节点没有子节点，则该属性返回nul。

**语法：**

``node.lastChild``

说明：与elementNode.childNodes[elementNode.childNodes.length-1]是同样的效果。

**注意: **我们知道Internet Explorer 会忽略节点之间生成的空白文本节点，而其它浏览器不会。我们可以通过检测节点类型，过滤子节点。 

### 8.10 访问父节点parentNode

获取指定节点的父节点

``elementNode.parentNode``

**注意：父节点只能有一个**

```
<div id="text">
	<p id="con">parentNode获取指定节点的父节点</p>
</div>
<script>
	var mynode=document.getElementById("con");
	document.write(mynode.parentNode.nodeName);
</script>
```

运行结果:

```
parentNode 获取指点节点的父节点
DIV
```

**访问祖节点:**

```
elementNode.parentNode.parentNode
```

```
<div id="text">  
  <p>
    parentNode      
    <span id="con"> 获取指点节点的父节点</span>
  </p>
</div> 
<script type="text/javascript">
  var mynode= document.getElementById("con");
  document.write(mynode.parentNode.parentNode.nodeName);
</script>
```

运行结果:

```
parentNode获取指点节点的父节点
DIV
```

注意: 浏览器兼容问题，chrome、firefox等浏览器标签之间的空白也算是一个文本节点。

#### 练习

**试一试，通过获取的mylist节点，使用访问父节点parentNode，将"HTML/CSS"课程内容输出。**

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>无标题文档</title>
</head>
<body>
<ul id="con">
<li id="lesson1">javascript
  <ul> 
      <li id="tcon"> 基础语法</li>
      <li>流程控制语句</li>
      <li>函数</li>
      <li>事件</li>
      <li>DOM</li>
  </ul>
</li>
<li id="lesson2">das</li>
<li id="lesson3">dadf</li>
<li id="lesson4">HTML/CSS 
  <ul>
    <li>文字</li>
    <li>段落</li>
    <li>表单</li>
    <li>表格</li>  
  </ul> 
</li></ul>  
<script  type="text/javascript">    
   var mylist = document.getElementById("tcon"); 
  document.write(mylist.parentNode.parentNode.parentNode.lastChild.innerHTML)
</script> 

</body>
</html>
```

### 8.11 访问兄弟节点

1.nextSibling属性可返回某个节点之后紧跟的节点（处于同一树层级中）。

**语法：**

```
nodeObject.nextSibling
```

**说明：**如果无此节点，则该属性返回 null。

2.previousSibling属性可返回某个节点之前紧跟的节点（处于同一树层级中）。

**语法：**

``nodeObject.previousSibling``

**说明：**如果无此节点，则该属性返回 null。

注意: 两个属性获取的是节点。Internet Explorer 会忽略节点间生成的空白文本节点（例如，换行符号），而其它浏览器不会忽略。

**解决问题方法:**

判断节点nodeType是否为1, 如是为元素节点，跳过。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>nextSibling</title>
</head>
<body>
  <ul id="ul">
    <li id="a">javascript</li>
    <li id="b">jquery</li>
    <li id="c">html</li>
  </ul>
  <ul id="u2">
    <li id="d">css3</li>
    <li id="e">php</li>
    <li id="f">java</li>
  </ul>
  <script>
  function get_nextSibling(n)
    {
      var x=n.nextSibling;
      while(x.nodeType!=1)
      {
        x=x.nextSibling;
      }
      return x;
    }
    var x=document.getElementsByTagName("li")[0];
    document.write(x.nodeName);
    document.write("=");
    document.write(x.innerHTML);
    var y=get_nextSibling(x);
    document.write("<br />nextSibling:");
    document.write("=");
    document.write(y.innerHTML);
  </script>
</body>
</html>
```

**运行结果:**

```
LI = javascript
nextsibling: LI = jquery
```

### 8.12 插入节点appendChild()

在指定节点的最后一个子节点列表之后添加一个新的子节点。

**语法：**

``appendChild(newnode)``

参数：

newnode：指定追加的节点。

```
<div id="test"><p id="x1">HTML</p><p>JavaScript</p></div>
<script>
	var otest=document.getElementById("test");
	var newnode=document.createElement("p");
	newnode.innerHTML="this is a new p";
	// appendChild方法添加节点
	otest.appendChild(newnode);
</script>
```

**运行结果:**

```
HTML
JavaScript
This is a new p
```

### 8.13 插入节点insertBefore()

insertBefore()方法可在已有的子节点前插入一个新的子节点。

**语法：**

``insertBefore(newnode,node)``

参数：

newnode：要插入的新节点。

node：指定此节点前插入节点。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title></title>
</head>
<body>
  <div id="div1"><p id="x1">JavaScript</p><p>HTML</p</div>
  <script>
    var otest=document.getElementById("div1");
    var node=document.getElementById("x1");
    var newnode=document.createElement("p");
    newnode.innerHTML="this is a new p";
    otest.insertBefore(newnode,node);
  </script>
</body>
</html>
```

**运行结果:**

```
This is a new p
JavaScript
HTML
```

**注意:** otest.insertBefore(newnode,node); 也可以改为:  otest.insertBefore(newnode,otest.childNodes[0]); 

### 8.14 删除节点removeChild()

removeChild()方法从子节点列表中删除某个节点。如删除成功，此方法可返回被删除的节点，如失败，则返回null。

**语法：**

`nodeObject.removeChild(node)`

参数：

node：必需，指定需要删除的节点。

```html
<!DOCTYPE HTML>
<html>
  <head>
    <title>Untitled</title>
  </head>
  <body>
    <div id="div1"><h1>HTML</h1><h2>javascript</h2></div>
  <script>
  	var otest=document.getElementById("div1");
    var x=otest.removeChild(otest.childNodes[1]);
    document.write("删除节点的内容："+x.innerHTML);
  </script>
  </body>
</html>
```

**运行结果:**

```
HTML
删除节点的内容: javascript
```

**注意:** 把删除的子节点赋值给 x，这个子节点不在DOM树中，但是还存在内存中，可通过 x 操作。如果要完全删除对象，给 x 赋 null 值

```
var otest=document.getElementById("div1");
var x=otest.removeChild(otest.childNodes[1]);
x=null;
```

#### 练习

试一试，定义clearText()函数，完成节点内容的删除。

1.删除该节点的内容，先要获取子节点。

2.然后使用循环遍历每个子节点。

3.使用removeChild()删除节点。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>无标题文档</title>
</head>

<body>
<div id="content">
  <h1>html</h1>
  <h1>php</h1>
  <h1>javascript</h1>
  <h1>jquery</h1>
  <h1>java</h1>
</div>

<script type="text/javascript">
function clearText() {
  var content=document.getElementById("content");
  // 在此完成该函数
  var node=content.childNodes;
  var n=node.length;  //因为删除后节点数量会变化，所以取固定值
  for(var i=0;i<n;i++){
    content.removeChild(node[0]); //循环删除第一个直到删除为止
  }
  // 加上clearText() 全部删除
  /*
  while(content.childNodes.length != 0){
            var x=content.removeChild(content.childNodes[0]);
        }
  */
}
</script>

<button onclick="clearText()">清除节点内容</button>
</body>
</html>
```

### 8.15 替换元素节点replaceChild()

replaceChild实现子节点（对象）的替换。返回被替换对象的引用。

**语法：**

`node.replaceChild(newnode,oldnew)`

参数：

newnode：必需，用于替换oldnew的对象。

oldnew：必需，被newnode替换的对象。

````html
<!DOCTYPE HTML>
<html>
  <head>
  <meta http-equiv="Content-Type" content="text/html;charset=utf-8">
    <title>无标题文档</title>
  </head>
  <body>
    <script>
      function replaceMessage(){
        var newnode=document.createElement("p");
        var newnodeText=document.createTextNode("JavaScript");
        newnode.appendChild(newnodeText);
        var oldNode=document.getElementById("oldnode");
        oldNode.parentNode.replaceChild(newnode,oldNode)
      }
    </script>
    <h1 id="oldnode">Java</h1>
    <a href="javascript:replaceMessage()">"Java"替换"JavaScript"</a>
  </body>
</html>
````

效果: 将文档中的 Java 改为 JavaScript。

**注意: **

1.当 oldnode 被替换时，所有与之相关的属性内容都将被移除。 

2.newnode 必须先被建立。 

#### 练习

试一试，补充函数 replaceMessage() 代码，实现将 b 标签替换成 i 标签。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>无标题文档</title>
</head>
<body>


  <div><b id="oldnode">JavaScript</b>是一个很常用的技术，为网页添加动态效果。</div>
  <a href="javascript:replaceMessage()"> 将加粗改为斜体</a>
  
    <script type="text/javascript">
      function replaceMessage(){
        var newnode=document.createElement("i");
        var newnodeText=document.createTextNode("JavaScript");
        newnode.appendChild(newnodeText);
		var oldnode=document.getElementById("oldnode");
		oldnode.parentNode.replaceChild(newnode,oldnode);
       }    
  </script>
  
 </body>
</html>
```

### 8.16 创建元素节点createElement

createElement()方法可创建元素节点。此方法可返回一个 Element 对象。

**语法：**

```
document.createElement(tagName)
```

**参数:**

tagName：字符串值，这个字符串用来指明创建元素的类型。

**注意：**要与appendChild() 或 insertBefore()方法联合使用，将元素显示在页面中。

我们来创建一个按钮，代码如下：

```
<script type="text/javascript">
   var body = document.body; 
   var input = document.createElement("input");  
   input.type = "button";  
   input.value = "创建一个按钮";  
   body.appendChild(input);  
 </script>  
```

我们也可以使用setAttribute来设置属性，代码如下：

```
<script type="text/javascript">  
   var body= document.body;             
   var btn = document.createElement("input");  
   btn.setAttribute("type", "text");  
   btn.setAttribute("name", "q");  
   btn.setAttribute("value", "使用setAttribute");  
   btn.setAttribute("onclick", "javascript:alert('This is a text!');");       
   body.appendChild(btn);  
</script>  
```

### 8.17 创建文本节点createTextNode

createTextNode() 方法创建新的文本节点，返回新创建的 Text 节点。

**语法：**

```
document.createTextNode(data)
```

**参数：**

data : 字符串值，可规定此节点的文本。

#### 练习

创建一个P标签，设置className属性，使用createTextNode创建文本节点"I love JavaScript!"。

```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>无标题文档</title>
<style type="text/css">

.message{    
	width:200px;
	height:100px;
	background-color:#CCC;}
	
</style>
</head>
<body>
<script type="text/javascript">
    var node=document.createElement("p");
    var nodeText=document.createTextNode("I love JavaScript!");
    node.className="message";
    node.appendChild(nodeText);
    document.body.appendChild(node);
</script> 

</body>
</html>
```

### 8.18 浏览器窗口可视区域大小

获得浏览器窗口的尺寸（浏览器的视口，不包括工具栏和滚动条）的方法：

一.对于IE9+、chrome、Firefox、Opera以及Safari：

`window.innerHeight` - 浏览器窗口的内部高度

`window.innerWidth` - 浏览器窗口的内部宽度

二.对于Internet Explorer8、7、6、5：

`document.documentElement.clientHeight`表示HTML文档所在窗口的当前高度。

`document.documentElement.clientWidth`表示HTML文档所在窗口的当前宽度。

或者

Document对象的body属性对应HTML文档的\<body>标签

`document.body.clientHeight`

`document.body.clientWidth`

**在不同浏览器都实用的JavaScript方案：**

```
var w=document.documentElement.clientWidth || document.body.clientWidth;
var h=document.documentElement.clientHeight || document.body.clientHeight;
```

### 8.19 网页尺寸scrollHeight

scrollHeight和scrollWidth，获取网页内容高度和宽度。

一.针对IE、Opera：

scrollHeight是网页内容实际高度，可以小于clientHeight。

二.针对NS、FF：

scrollHeight是网页内容高度，不过最小值是clientHeight。也就是说网页内容实际高度小于clientHeight时，scrollHeight返回clientHeight。

三.浏览器兼容

```
var w=document.documentElement.scrollWidth
   || document.body.scrollWidth;
var h=document.documentElement.scrollHeight
   || document.body.scrollHeight;
```

**注意：**区分大小写

scrollHeight和scrollWidth还可获取DOM元素中内容实际占用的高度和宽度。

### 8.20 网页尺寸offsetHeight

offsetHeight和offsetWidth，获取网页内容高度和宽度（包括滚动条等边线，会随窗口的显示大小改变）。

一.值

offsetHeight=clientHeight+滚动条+边框。

二.浏览器兼容性

```
var w= document.documentElement.offsetWidth
    || document.body.offsetWidth;
var h= document.documentElement.offsetHeight
    || document.body.offsetHeight;
```

#### 图解窗口大小

无滚动条时，dom对象的offsetWidth、clientWidth和scrollWidth

![img](http://img.blog.csdn.net/20150605074220093?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbHpkaW5n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

有滚动条时：

![img](http://img.blog.csdn.net/20150606063107756?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbHpkaW5n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

window对象的outerWidth、innerWidth、pageXOffset和screenLeft（screenX）

![img](http://img.blog.csdn.net/20150606171022202?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbHpkaW5n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

https://www.cnblogs.com/sunnywindycloudy/p/7381378.html

![img](https://images2017.cnblogs.com/blog/1219513/201708/1219513-20170817141747443-425001125.png)

### 8.21 网页卷去的距离与偏移量

![img](http://img.mukewang.com/5347b2b10001e1a307520686.jpg)

scrollLeft：设置或获取位于给定对象左边界与窗口中目前可见内容的最左端之间的距离，即左边灰色的内容。

scrollTop：设置或获取位于对象最顶端与窗口中可见内容的最顶端之间的距离，即上边灰色的内容。

offsetLeft：获取指定对象相对于版面或由offsetParent属性指定的父坐标的计算左侧位置。

offsetTop：获取指定对象相对于版面或由offsetParent属性指定的父坐标的计算顶端位置。

**注意：**

1.区分大小写

2.offsetParent：布局中设置position属性（relative、Absolute、fixed）的父容器，从最近的父节点开始，一层层向上找，直到HTML的body。

#### 练习

调整横竖滚动条后，点击按钮后，查看offsetTop、offsetLeft、scrollTop、scrollLeft值的变化。

```html
<!DOCTYPE HTML>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<script type="text/javascript">
    function req(){
          var div = document.getElementById("div1");
          document.getElementById("li1").innerHTML = (div.offsetTop)+"px";//div1距离屏幕顶部的距离
          document.getElementById("li2").innerHTML = (div.offsetLeft)+"px";//div1距离屏幕左部的距离
          document.getElementById("li3").innerHTML = (div.scrollTop)+"px";//div1纵向滚动条滚动的距离
          document.getElementById("li4").innerHTML = (div.scrollLeft)+"px";//div1横向滚动条滚动的距离
     }
</script>
</head>
<body style="border:10px solid #ccc;padding:0px 0px;margin:5px 10px">
    <div style="width:60%;border-right:1px dashed red;float:left;">
        <div style="float:left;">
            <div id="div1" style="border:5px red solid;height:300px;width:200px;overflow:auto">
                <div style="height:500px;width:400px">请调整横竖滚动条后，点击按钮后查看offsetTop、offsetLeft、scrollTop、scrollLeft值。</div>
            </div>
            <input type="button" value="点击我!" onclick="req()" style="border: 1px solid purple;height: 25px;"/>
        </div>
        
    </div>
    <div style="width:30%;float:left;">
        <ul style="list-style-type: none; line-height:30px;">结果：
            <li>offsetTop : <span id="li1"></span></li>
            <li>offsetLeft : <span id="li2"></span></li>
            <li> scrollTop : <span id="li3"></span></li>
            <li>scrollLeft : <span id="li4"></span></li>
        </ul>
        
    </div>
    <div style="clear:both;"></div>    
</body>
</html>
```

### 8.22 编程练习

制作一个表格，显示班级的学生信息。

**要求：**

1.鼠标移到不同行上时背景色改为色值为 #f2f2f2，移开鼠标时则恢复为原背景色 #fff

2.点击添加按钮，能动态在最后添加一行

3.点击删除按钮，则删除当前行

```html
<!DOCTYPE html>
<html>
 <head>
  <title> new document </title>  
  <meta http-equiv="Content-Type" content="text/html; charset=gbk"/>   
  <script type="text/javascript"> 
  
      window.onload = function(){
                  
     // 鼠标移动改变背景,可以通过给每行绑定鼠标移上事件和鼠标移除事件来改变所在行背景色。
        var trcolor=document.getElementsByTagName("tr"); 
		for(i=0;i<trcolor.length;i++){
		    trcolor[i].onmouseover=function(){this.style.backgroundColor="#f2f2f2"};
		    trcolor[i].onmouseout=function(){this.style.backgroundColor="#fff"};
		}
	 }
     
      // 编写一个函数，供添加按钮调用，动态在表格的最后一行添加子节点；
     function add(){
        var mytr=document.createElement("tr");
        var mytab=document.getElementById("table");
        //var rl=document.getElementsByTagName("tr")[0].childNodes.length;
        for(i=0;i<3;i++){
            var mytd=document.createElement("td");
            if(i==2){
                mytd.innerHTML="<a href='javascript:;' onclick='remove(this)' >删除</a>"
            }
            else{
                mytd.innerHTML=""
            }
            mytr.appendChild(mytd);
        }
        mytab.appendChild(mytr);
        var rl=document.getElementById("table").childNodes.length;
        var mytr1=document.getElementById("table").childNodes[rl-1];
        mytr1.onmouseover=function(){this.style.backgroundColor="#f2f2f2"};
        mytr1.onmouseout=function(){this.style.backgroundColor="#fff"};
     }
    		
     // 创建删除函数
     function remove(a){
         var x=a.parentNode.parentNode
         var b=a.parentNode.parentNode.parentNode;
         b.removeChild(x);
     }


  </script> 
 </head> 
 <body> 
	   <table border="1" width="50%" id="table">
	   <tr>
		<th>学号</th>
		<th>姓名</th>
		<th>操作</th>
	   </tr>  

	   <tr>
		<td>xh001</td>
		<td>王小明</td>
		<td><a href="javascript:;" onclick="remove(this)" >删除</a></td>   <!--在删除按钮上添加点击事件  -->
	   </tr>

	   <tr>
		<td>xh002</td>
		<td>刘小芳</td>
		<td><a href="javascript:;" onclick="remove(this)" >删除</a></td>   <!--在删除按钮上添加点击事件  -->
	   </tr>  

	   </table>
	   <input type="button" value="添加一行" onclick="add()" />   <!--在添加按钮上添加点击事件  -->
 </body>
</html>		
```

## 编程练习

现在利用之前我们学过的JavaScript知识，实现选项卡切换的效果。

**文字素材:**

房产：

​    275万购昌平邻铁三居 总价20万买一居
​    200万内购五环三居 140万安家东三环
​    北京首现零首付楼盘 53万购东5环50平
​    京楼盘直降5000 中信府 公园楼王现房

家居:

​     40平出租屋大改造 美少女的混搭小窝
​     经典清新简欧爱家 90平老房焕发新生
​     新中式的酷色温情 66平撞色活泼家居
​     瓷砖就像选好老婆 卫生间烟道的设计

二手房：

​     通州豪华3居260万 二环稀缺2居250w甩
​     西3环通透2居290万 130万2居限量抢购
​     黄城根小学学区仅260万 121平70万抛!
​     独家别墅280万 苏州桥2居优惠价248万

代码1：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>实践题 - 选项卡</title>
    <style type="text/css">
     /* CSS样式制作 */  
    *{
        padding:0px;
        margin:0px;
        font-size:18px;
    }   
    .ul{
        width:290px;
        height:20px;
        list-style:none;
        display:block;
        margin:10px 12px;
    }
    .ul li{
        height:20px;
        width:60px;
        display:inline-block;
        border:1px solid #8B4500;
        padding:12px;
        text-align:center;
    }
    .ul li a{text-decoration:none;}
    #text div{
        border:1px solid;
        width:360px;
        height:150px;
        margin:25px 10px;
        padding:10px;
    }
    #text1{
        display:block;
    }
    #text2,#text3{
        display:none;
    }
    </style>
    <script type="text/javascript">
    function f1(){
        document.getElementById("text1").style.display="block";
        document.getElementById("text2").style.display="none";
        document.getElementById("text3").style.display="none";
    }
    function f2(){
        document.getElementById("text1").style.display="none";
        document.getElementById("text2").style.display="block";
        document.getElementById("text3").style.display="none";
    }
    function f3(){
        document.getElementById("text1").style.display="none";
        document.getElementById("text2").style.display="none";
        document.getElementById("text3").style.display="block";
    }
    // JS实现选项卡切换
    </script>
 
</head>
<body>
<!-- HTML页面布局 -->
<div id="text">
    <ul class="ul">
        <li><a id="fc" onclick="f1()" href="#">房产</a></li>
        <li><a id="jj" onclick="f2()" href="#">家居</a></li>
        <li><a id="esf" onclick="f3()" href="#">二手房</a></li>
    </ul>
    <div id="text1">
        <p>275万购昌平邻铁三居 总价20万买一居</p>
        <p>200万内购五环三居 140万安家东三环</p>
        <p>北京首现零首付楼盘 53万购东5环50平</p>
        <p>京楼盘直降5000 中信府 公园楼王现房</p>
    </div>
    <div id="text2">
        <p>40平出租屋大改造 美少女的混搭小窝</p>
        <p>经典清新简欧爱家 90平老房焕发新生</p>
        <p>新中式的酷色温情 66平撞色活泼家居</p>
        <p>瓷砖就像选好老婆 卫生间烟道的设计</p>
    </div>
    <div id="text3">
        <p>通州豪华3居260万 二环稀缺2居250w甩</p>
        <p>西3环通透2居290万 130万2居限量抢购</p>
        <p>黄城根小学学区仅260万 121平70万抛!</p>
        <p>独家别墅280万 苏州桥2居优惠价248万</p>
    </div>
</div>
</body>
</html>
```

代码2：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>实践题 - 选项卡</title>
    <style type="text/css">
     /* CSS样式制作 */  
    *{margin:0px;padding:0px;font-size:12px;font-family:"微软雅黑";}   
    #tabs{
        margin:10px;
        width:300px;
        height:150px;
    }
    #tabs ul{
        list-style:none;
        width:300px;
        height:30px;
        display:block;
    }
    #tabs ul li{
        margin:0px 3px;
        width:60px;
        height:28px;
        line-height:28px;
        border:1px solid #aaa;
        border-bottom:none; //不设下边框
        text-align:center;
        list-style:none;
        display:inline-block;
        cursor:pointer;
    }
    #tabs ul li.select{ 
        border-top:2px solid saddlebrown; //激活显示边框
        border-bottom:2px solid #fff;
    }
    #tabs div{
        width:290px;
        line-height:25px;
        border:1px solid #00BFFF;
        border-top:2px solid saddlebrown;
        padding:5px;
    }
    .text{display:none;}
    </style>
    <script type="text/javascript">
    // JS实现选项卡切换
    window.onload=function(){
        var tab=document.getElementById("tabs");
        var li=document.getElementsByTagName("li");
        var div=tab.getElementsByTagName("div");
        for(var i=0;i<li.length;i++){
            li[i].index=i; //定义index对li编号
            li[i].onclick=function(){
               for(var j=0;j<li.length;j++){
                   li[j].className="";
                   div[j].className="text";
               }
                this.className="select";
                div[this.index].className="";
            }
        }
    }
    </script>
 
</head>
<body>
<!-- HTML页面布局 -->
<div id="tabs">
    <ul>
        <li class="select">房产</li>
        <li>家居</li>
        <li>二手房</li>
    </ul>
    <div>
        <p>275万购昌平邻铁三居 总价20万买一居</p>
        <p>200万内购五环三居 140万安家东三环</p>
        <p>北京首现零首付楼盘 53万购东5环50平</p>
        <p>京楼盘直降5000 中信府 公园楼王现房</p>
    </div>
    <div class="text">
        <p>40平出租屋大改造 美少女的混搭小窝</p>
        <p>经典清新简欧爱家 90平老房焕发新生</p>
        <p>新中式的酷色温情 66平撞色活泼家居</p>
        <p>瓷砖就像选好老婆 卫生间烟道的设计</p>
    </div>
    <div class="text">
        <p>通州豪华3居260万 二环稀缺2居250w甩</p>
        <p>西3环通透2居290万 130万2居限量抢购</p>
        <p>黄城根小学学区仅260万 121平70万抛!</p>
        <p>独家别墅280万 苏州桥2居优惠价248万</p>
    </div>
</div>

 
</body>
</html>
```

