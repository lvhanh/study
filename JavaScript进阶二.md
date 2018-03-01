## 第一章 数据类型

### 1.1 JavaScript六中数据类型

原始类型：number、string、boolean、null、undefined

object（对象类型）：Function、Array、Date....

### 1.2 JavaScript隐式转换

**1.+和-**

"37" - 7  //30

"37" + 7 //377

巧用+/-规则转换类型

**2.a==b**

类型不同时，尝试类型转换和比较

"1.23" == 1.23  //string转number

0==false  //boolean转number

null == undefined

new Object() == new Object()

**3.a===b**

严格等于

先判断等号两边的类型

类型不同，返回false

类型相同：

null === null

undefined === undefined

NaN != NaN

new Object != new Object

### 1.3 包装对象

```
var a="string";
alert(a.length);  //6
a.t=3;
alert(a.t);     //undefined
```

当尝试把基本类型（str）当做对象一样访问时，例如：str.length。解释器会创建一个临时的包装对象，用完就销毁。重复访问会重复创建这个临时对象，每次创建的临时包装对象都是不同的。

### 1.4 类型检测

```
typeof
instanceof
Object.prototype.toString
constructor
duck type
```

1.typeof

返回一个字符串，常用来判断基本类型和函数对象

```
typeof 100	"number"
typeof true  "boolean"
typeof function	"function"
typeof null		"object"
```

2.instanceof

判断对象类型，基于原型链去判断

```
obj instanceof Object
判断左边对象的原型链上是否有右边构造函数的prototype属性(对象属性)
[1,2] instanceof Array === true
new Object() instanceof Array === false
```

```
function person(){}
function student(){}
student.prototype = new person()
var a=new student()
a instanceof student  //true
var one=new person()
one instanceof person  //true
one instance student  //false
a instanceof person  //true
```

注意：不同window或iframe间的对象类型检测不能使用instanceof

3.Object.prototype.toString

```
Object.prototype.toString.apply([]); ==="[object Array]";
Object.prototype.toString.apply(function(){}); ==="[object Function]"
Object.prototype.toString.apply(null); ==="[object Null]"
Object.prototype.toString.apply(undefined); ==="[object Undefined]"
```

**小结：**

1.typeof：适合基本类型及function检测，遇到null失效。

2.[[Class]]：通过{}.toString拿到，适合内置对象和基元类型，遇到null和undefined失效（IE678等返回[object Object]）。

3.instanceof：适合自定义对象，也可以用来检测原生对象，在不同iframe和window间检测时失效。

##第二章 表达式和运算符

###2.1 表达式

####原始表达式

常量、直接量：3.14，"test"

关键字：null,this,true

变量：i,k,j

####数组、对象的初始化表达式

[1,2]		new Array(1,2);

[1,,,4]		\[1,undefined,undefined,4];

{x:1,y:2}		var o=new Object();

​			o.x=1;o.y=2;

####函数表达式

var fe=function(){};

(function(){console.log('hello world');})();

####属性访问表达式

var o={x:1};

​	o.x

​	o['x']

####调用表达式

func();

####对象创建表达式

new Func(1,2);

new Object;

###2.2 运算符

按操作数分：

一元运算符：+num

二元运算符：a+b

三元运算符：c?a:b

按功能分：

赋值：x+=1

比较：a==b

算术：a-b

位：a|b

逻辑：exp1&&exp2

字符串："a"+"b"

特殊：delete obj.x

####条件运算符 ?:

c?a:b

var val=true?1:2; //val=1

//如果true取冒号前面的，false取后面的

####逗号运算符 ,

var val=(1,2,3);  //val=3

//从左到后依次计算表达式的值，最后取最右边的。用逗号隔开表示每个表达式都会被计算

####delete运算符

delete obj.x;

var obj={x:1};

obj.x;	//1

delete obj.x;

obj.x;	//undefined

**注意：**ie9开始新增defineProperty属性，标签configurable为true时delete才能删除。

```
var obj={};
Object.defineProperty(obj,'x',{
  configurable:false,
  value:1
});
delete obj.x; //false
obj.x		//1
```

####in运算符

window.x=1;

'x' in window;	//true

####运算符  instanceof,typeof

{}instanceof Object	//true

typeof 100=== 'number'	//true

####运算符 new

```
function Foo(){}
Foo.prototype.x=1;
var obj=new Foo();
obj.x;	//1
obj.hasOwnProperty('x');	//false
obj._proto_.hasOwnProperty('x');	//true
```

####运算符 this

```
this;	//window(浏览器)
var obj={
  func:function(){return this;}
};
obj.func();	//obj
```

####运算符 void

void 0	//undefined

void (0)	//undefined

##第三章 语句和严格模式 

### 3.1 block语句、var语句

**1.block语句**

块语句常用于组合0~多个语句。块语句用一对花括号定义。

语法：

```
{
  语句1；
  语句2；
  。。。
}
```

```
{
  var str="hi";
  console.log(str);
}
```

```
if(true){
  console.log("hi");
}
```

**注意：**没有块级的作用域

```
for(var i=0;i<10;i++){}
等于
var i=0
for(;i<10;i++){}
```

**2.var语句**

var a=1

var a=1,b=1

### 3.2 try-catch语句

```
try{
  throw "test";
}catch(ex){
  console.log(ex);	//test
}finally{
  console.log('finally');
}
```

try后面必须接着catch或者finally，所以try-catch有三种形式：

try-catch,try-finally,try-catch-finally

```
try{
  try{
    throw new Error("oops");
  }
  finally{
    console.log("finally");
  }
}
catch(ex){
  console.error("outer",ex.message);
}
```

结果为：

```
"finally"
"outer" "opps"
```

```
try{
  try{
    throw new Error("oops");
  }
  catch(ex){
    console.error("inner",ex.message);
  }
  finally{
    console.log("finally");
  }
}
catch(ex){
  console.error("outer",ex.message);
}
```

结果为：

```
"inner" "oops"
"finally"
try内部已经处理了异常所以不会再抛出给外部catch
```

```
try{
  try{
    throw new Error("oops");
  }
  catch(ex){
    console.error("inner",ex.message);
    throw ex;	//再抛出异常给外部catch接收
  }
  finally{
    console.log("finally");
  }
}
catch(ex){
  console.error("outer",ex.message);
}
```

结果为：

```
"inner" "oops"
"finally"
"outer" "oops"
```

### 3.3 函数、switch、循环

**1.function语句**

function语句用来定义函数对象。

用function语句定义的函数对象叫函数申明。

```
fd();	//true
function fd(){
  //do sth.
  return true;
}
```

另一种叫函数表达式

```
fe();	//TypeError
var fe=function(){
  //do sth.
};
```

两者主要的区别为：

函数申明会被预先处理，或者叫函数前置。

**2.for...in语句**

遍历对象中的属性

```
var p;
var obj={x:1,y:2}
for(p in obj){	//遍历obj对象中的属性
}
```

**注意：**

1.顺序不确定

2.enumerable为false时不会在for in中出现

3.for in的对象会受原型链影像

**3.switch语句**

```
var val=2;
switch(val){
  case 1:
    console.log(1);
    break;
  case 2:
    console.log(2);
    break;
  default:
    console.log(0);
    break;
}
//结果为2
```

```
var val=2;
switch(val){
  case 1:
    console.log(1);
  case 2:
    console.log(2);
  default:
    console.log(0);
}
//结果为2,0
```

```
var val=2;
switch(val){
  case 1:
  case 2:
  case 3:
  	console.log(123);
  	break;
  case 4:
  case 5:
  	console.log(45);
  	break;
  default:
  	console.log(0);
}
//结果为123
```

**4.循环语句**

```
while(isTrue){
  //do sth.
}
```

```
do{
  //do sth.
}while(isTrue)
```

```
var i;
for(i=0;i<n;i++){
  //do sth.
}
```

**5.with语句**

可以修改当前的作用域

```
with({x:1}){
  console.log(x);
}
with(document.forms[0]){
  console.log(name.value);
  //document.forms[0].name.value
}
等同于
var form=document.forms[0];
console.log(form.name.value);
```

1.让JS引擎优化更难

2.可读性差

3.可被变量定义代替

4.严格模式下被禁用

### 3.4 严格模式

严格模式是一种特殊的执行模式，它修复了部分语言上的不足，提供更强的错误检查，并增强安全性。

```
function func(){
  'use strict'
}
或者
'use strict'
function func(){
  
}
```

**注意：**

1.严格模式下不允许用with

2.不允许未声明的变量被赋值

3.arguments变为参数的静态副本

```
!function(a){
  srguments[0]=100;
  console.log(a);
}(1);
//输出值为100 1=>100
//如果1不传值为undefined，不会受arguments影响

!function(a){
  'use strict';
  arguments[0]=100;
  console.log(a);
}(1);
//输出值为1

!function(a){
  'use strict';
  arguments[0].x=100;
  console.log(a.x);
}({x:1})
//输出值为100
//修改的是对象，对象属性会受影响
```

4.delete参数、函数名报错

```
!function(a){
  console.log(delete a);
}(1);
//false

!function(a){
  'use strict';
  delete a;
}(1);
//SyntaxError
```



