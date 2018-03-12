

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

5.delete不可配置的属性报错

```
!function(a){
  var obj={};
  Object.defineProperty(obj,'a',{configurable:false});
  console.log(delete obj.a);
}(1);
//false  删除失败
```

6.对象字面量重复属性名报错

```
!function(){
  var obj={x:1,x:2};
  console.log(obj.x);
}();
//取最后一个，值为2

!function(){
  'use strict';
  var obj={x:1,x:2};
}();
//SyntaxError
```

7.禁止八进制字面量

8.eval,arguments变为关键字，不能作为变量、函数名

```
!function(){
  function eval(){}
  console.log(eval);
}();
//输出function eval(){}

!function(){
  'use strict';
  function eval(){}
}();
//SyntaxError
```

9.eval独立作用域

```
!function(){
  eval('var evalVal=2;');
  console.log(typeof evalVal);
}();
//number

!function(){
  'use strict';
  eval('var evalVal=2;');
  console.log(typeof evalVal);
}();
//undefined
```

10.一般函数调用时（不是对象的方法调用，也不使用apply/call/bind等修改this）this指向null，而不是全局对象。若使用apply/call，当传入null或undefined时，this将指向null或undefined，而不是全局对象。

11.试图修改不可写属性（writeable=false），在不可扩展的对象上添加属性时报TypeError，而不是忽略。

12.arguments.caller,arguments.callee被禁用

## 第四章 对象

### 4.1 对象概述

对象中包含一系列属性，这些属性是无序的。每个属性都有一个字符串key和对应的value。

```
var obj={x:1,y:2};
obj.x;	//1
obj.y;	//2
```

<img src='https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180301103551.png' style="zoom:70%">

### 4.2 创建对象、原型链

创建对象：

####字面量

```
var obj1={x:1,y:2};
var obj2={
  x:1,
  y:2,
  o:{
    z:3,
    n:4
  }
};
```

####new/原型链

```
function foo(){}
foo.prototype.z=3;
```

定义一个函数对象，这个对象默认带prototype属性

![img](https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180301145638.png)

如图，每个对象都有[proto]标签

```
var obj=new foo();
obj.y=2;
obj.x=1;
```

![img](https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180301154914.png)

```
obj.x;//1
obj.y;//2
obj.z;//3
typeof obj.toString;// 'function'
'z' in obj;//true
obj.hasOwnProperty('z');//false
```

**注意：**JS中默认的对象都会有toString方法，因为他们原型链上的末端在null之前都会有个Object.prototype，toString是Object.prototype上的。

当给对象赋值时，不会向原型链查找

```
obj.z=5;
obj.hasOwnProperty('z');//true
foo.prototype.z;//still 3
obj.z;//5
obj.z=undefined;
obj.z;//undefined
delete obj.z;//true
obj.z;//3
```

![img](https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180301160640.png)

#### Object.create

```
var obj=Object.create({x:1});
obj.x //1
typeof obj.toString	//"function"
obj.hasOwnProperty('x'); //false

var obj=Object.create(null);
obj.toString //undefined
```

![img](https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180301161851.png)

### 4.3 属性操作

读写对象属性：属性异常、删除属性、检测属性、枚举属性。

#### 属性读写

```
var obj={x:1,y:2};
obj.x; //1
obj["y"]; //2
```

中括号的情况：

```
var obj={x1:1,x2:2};
var i=1,n=2;
for(;i<=n;i++){
  console.log(obj['x'+1]);
}//输出1,2

var p;
for(p in obj){
  console.log(obj[p]);
}
```

#### 属性读写-异常

```
var obj={x:1};
obj.y; //undefined
//直接查到原型链顶端null
var yz=obj.y.z; 
//TypeError:cannot read property 'z' of undefined

var yz;
if(obj.y){
  yz=obj.y.z;
}

var yz=obj&&obj.y&&obj.y.z;
```

#### 属性删除

```
var person={age:28,title:'fe'};
delete person.age; //true
delete person['title']; //true
person.age; //undefined
delete person.age; //true

delete Object.prototype; //false
//不允许被删除

var descriptor=Object.getOwnPropertyDescriptor(Object,'prototype');
descriptor.configurable; //false
//configurable 是否可配置
```

**注意：**用var定义的全局变量和局部变量不能被删除

```
var globalVal=1;
delete globalVal; //false

(function(){
  var localVal=1;
  return delete localVal;
}()); //false

ohNo=1;
window.ohNo; //1
delete ohNo; //true
```

#### 属性检测

```
var cat=new Object;
cat.legs=4;
cat.name="ketty";

'legs' in cat; //true
'abc' in cat; //false
'toString' in cat; //true,inherited property!!!

cat.hasOwnProperty('legs'); //true
cat.hasOwnProperty('toString'); //false

cat.propertyIsEnumerable('true'); //true
cat.propertyIsEnumerable('toString'); //false
```

enumerable：枚举

```
Object.defineProperty(cat,'price',{enumerable:false,value:1000});
//defineProperty默认所有标签false
cat.propertyIsEnumerable('price'); //false
cat.hasOwnProperty('price'); //true

if(cat&&cat.legs){
  cat.legs*=2;
}

if(cat.legs!=undefined){
  //!==undefined or !==null
}

if(cat.legs!==undefined){
  //only if cat.legs is not undefined
}
```

#### 属性枚举

```
var o={x:1,y:2,z:3};
'toString' in o; //true
o.propertyIsEnumerable('toString'); //false
var key;
for(key in o){
  console.log(key); //x,y,z
}

var obj=Object.create(o);
obj.a=4;
var key;
for(key in obj){
  console.log(key); //a,x,y,z
}

var obj=Object.create(o);
obj.a=4;
var key;
for(key in obj){
  if(obj.hasOwnProperty(key)){
    console.log(key); //a
  }
}
```

### 4.4 get/set方法

####属性getter/setter方法

```
var man={
  name:'A',
  weibo:'@A',
  get age(){
    return new Date().getFullYear()-1988;
  },
  set age(val){
    console.log('Age can\'t be set to'+val);
  }
}
console.log(man.age); //27
man.age=100; //Age can't be set to 100
console.log(man.age); //still 27
```

```
var man={
  weibo:'@A',
  $age:null,
  get age(){
    if(this.$age==undefined){
      return new Date().getFullYear()-1988;
    }else{
      return this.$age;
    }
  },
  set age(val){
    val=+val; //+val表示转换为数字
    if(!isNaN(val)&&val>0&&val<150){
      this.$age=+val;
    }else{
      throw new Error('Incorrect val='+val);
    }
  }
}
console.log(man.age); //27
man.age=100;
console.log(man.age); //100
man.age='abc'; //error:Incorrect val=NaN
```

#### get/set与原型链

```
function foo(){}
Object.defineProperty(foo.property,'z',{get:function(){return 1;}});
var obj=new foo();

obj.z; //1
obj.z=10;
obj.z; //still 1
```

![img](https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180307104420.png)

当原型链上有get/set方法时，赋值时会走原型链上的get/set方法。

若要实现修改，可以用defineProperty()

```
Objext.defineProperty(obj,'z',{value:100,configurable:true});
obj.z; //100
delete obj.z;
obj.z; //back to 1
```

**注意：**defineProperty()中属性标签都为false

```
var o={};
Object.defineProperty(o,'x',{value:1}); //writable=false,configurable=false
var obj=Object.create(o);
obj.x; //1
obj.x=200;
obj.x; //still 1,can't change it

Object.defineProperty(obj,'x',{writable:true,configurable:true,value:100});
obj.x; //100
obj.x=500;
obj.x; //500
```

### 4.5 属性标签

#### 属性级的权限标签

1.``Object.getOwnPropertyDescriptor(包含属性的对象,属性的名称)``，返回属性的描述符

2.``Object.defineProperty(要在其上定义属性的对象,要定义或修改的属性的名称,将被定义或修改的属性描述符)``返回被传递给函数的对象，被定义的属性描述符默认false。

   ``Object.defineProperties(要在其上定义属性的对象，该对象的一个或多个键值对定义了将要为对象添加或修改的属性的具体配置)``返回该对象。

3.``Object.keys(要返回其枚举自身属性的对象)``返回一个表示给定对象的所有可枚举属性的字符串数组。返回的数组中属性名的排列顺序和使用for...in时返回的顺序一致。

```
Object.getOwnPropertyDescriptor({pro:true},'pro');
//Object{value:true,writable:true,enumerable:true,configurable:true}
Object.getOwnPropertyDescriptor({pro:true},'a');
//undefined

var person={};
Object.defineProperty(person,'name',{
  configurable:false,
  writable:false,
  enumerable:true,
  value:'a'
});
person.name; //a
person.name=1;
person.name; //still a
delete person.name; //false

Object.defineProperty(person,'type',{
  configurable:true,
  writable:true,
  enumerable:false,
  value:"Object"
});
Object.keys(person); //["name"]

Object.defineProperties(person,{
  title:{value:'fe',enumerable:true},
  corp:{value:'baba',enumerable:true},
  salary:{value:50000,enumerable:true,writable:true}
});
```

<img src="https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180308134035.png" style="zoom:70%">

### 4.6 对象标签、对象序列化

#### 对象标签

对象标签包括：``[[proto]]``，``[[class]]``，``[[extensible]]``

1.\_proto\_ 原型标签

<img src="https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180308140559.png" style="zoom:80%">



2.class标签

表示对象的类型，没有直接查看的方式，可以通过``Object.prototype.toString``间接获取。

```
var toString=Object.prototype.toString;
function getType(o){return toString.call(o).slice(8,-1);};

toString.call(null); //"[object Null]"
getType(null); //"Null"
getType(undefined); //"Undefined"
getType(1); //"Number"
getType(new Number(1)); //"Number"
typeof new Number(1); //"object"
getType(true); //"Boolean"
getType(new Boolean(true)); //"Boolean"
```

3.extensible标签

表示对象是否可扩展，即对象的属性是否可添加

```
var obj={x:1,y:2};
Object.isExtensible(obj); //true
Object.preventExtensions(obj); //阻止添加新属性
Object.isExtensible(obj); //false
obj.z=1;
obj.z; //undefined,add new property failed
Object.getOwnPropertyDescriptor(obj,'x');
//Object{value:1,writable:true,enumerable:true,configurable:true}

Object.seal(obj); //在preventExtensions()基础上再将configurable设为false
Object.getOwnPropertyDescriptor(obj,'x');
//Object{value:1,writable:true,enumerable:true,configurable:false}
Object.isSealed(obj); //true

Object.freeze(obj);
Object.getOwnPropertyDescriptor(obj,'x');
//Object{value:1,writable:false,enumerable:true,configurable:false}
Object.isFrozen(obj); //true
```

#### 序列化

对象序列化是指将对象的状态转换为字符串，也可将字符串还原为对象。ES5提供了内置函数``JSON.stringify()``和``JSON.parse()``用来序列化和还原JavaScript对象。这些方法都使用JSON作为数据交换格式。

```
var obj={x:1,y:true,z:[1,2,3],nullVal:null};
JSON.stringify(obj); //"{"x":1,"y":true,"z":[1,2,3],"nullVal":null}"

obj={val:undefined,a:NaN,b:Infinity,c:new Date()};
JSON.stringify(obj); //"{"a":null,"b":null,"c":"2015-01-20****"}"

obj=JSON.parse('{"x":1}');
obj.x; //1
```

自定义序列化：

```
var obj={
  x:1,
  y:2,
  o:{
    o1:1,
    o2:2,
    toJSON:function(){
      return this.o1+this.o2;
    }
  }
};
JSON.stringify(obj); //"{"x":1,"y":2,"o":3}"
```

#### 其它对象方法

1.toString()方法：返回一个表示调用这个方法的对象的字符串，在需要将对象转化为字符串的时候调用这个方法。

2.valueOf()方法：将对象转化为某种原始值而非字符串的时候调用，尤其是转化为数字时候。

上述两种方法JS都会自动调用

```
var obj={x:1,y:2};
obj.toString(); //"[object Object]"
obj.toString=function(){return this.x+this.y};
"Result"+obj; //"Result3",by toString

+obj; //3,from toString

obj.valueOf=function(){return this.x+this.y+100;};
+obj; //103,from valueOf

"Result"+obj; //still "Result 103"
```

**注意：**

toString和valueOf都存在的时候，在做操作的时候都会把对象转换为基本类型，先找valueOf如果valueOf返回基本类型就以valueOf的值作为结果，反之如果valueOf不存在或者返回对象就会找toString

## 第五章 数组

### 5.1 创建数组、数组操作

数组概述：数组是值的有序集合。每个值叫做元素，每个元素在数组中都有数字位置编号，也就是索引。JS中的数组是弱类型的，数组中可以含有不同类型的元素。数组元素甚至可以是对象或其它数组。

```
var arr=[1,true,null,undefined,{x:1},[1,2,3]];
```

#### 创建数组

1.直接创建

```
var arr=['Nunnly','is','big','keng']

var commasArr1=[1,,2]; //1,undefined,2
var commasArr2=[,,]; //undefined*2
```

2.new Array

```
var arr=new Array();
var arrWithLength=new Array(100);
var arrLikesLiteral=new Array(true,false,null,1,2,"hi");
```

#### 数组操作

1.数组元素读写

```
var arr=[1,2,3,4,5];
arr[1]; //2
arr.length; //5
```

 2.数组元素增删

JavaScript中的数组是动态的，不需要指定大小。length属性会根据情况更新

```
var arr=[];
arr[0]=1;
arr[1]=2;
arr.push(3);
arr; //[1,2,3]

arr[arr.length]=4; //equal to arr.push(4)
arr; //[1,2,3,4]

arr.unshift(0);
arr; //[0,1,2,3,4]

delete arr[2];
arr; //[0,1,undefined,3,4]
arr.length; //5
2 in arr; //false

arr.length-=1;
arr; //[0,1,undefined,3],4 is removed

arr.pop(); //3 returned by pop
arr; //[0,1,undefined],3 is removed

arr.shift(); //0 returned by shift
arr; //[1,undefined]
```

3.数组迭代

```
var i=0,n=10;
var arr=[1,2,3,4,5];
for(;i<n;i++){
  console.log(arr[i]); //1,2,3,4,5
}
for(i in arr){
  console.log(arr[i]); //1,2,3,4,5
}

Array.prototype.x='inherited';
for(i in arr){
  console.log(arr[i]); //1,2,3,4,5,inherited
}
for(i in arr){
  if(arr.hasOwnProperty(i)){
    console.log(arr[i]); //1,2,3,4,5
  }
}
```

### 5.2 二维数组、稀疏数组

#### 二维数组

```
var arr=[[0,1],[2,3],[4,5]];
var i=0,j=0;
var row;
for(;i<arr.length;i++){
  row=arr[i];
  console.log('row'+i);
  for(j=0;j<row.length;j++){
    console.log(row[j]);
  }
}
```

#### 稀疏数组

稀疏数组并不含有从0开始的连续索引，一般length属性值比实际元素个数大。

```
var arr1=[undefined];
var arr2=new Array(1);
0 in arr1; //true
0 in arr2; //false
arr1.length=100;
arr1[99]=123;
99 in arr1; //true
98 in arr1; //false

var arr=[,,];
0 in arr; //false
```

### 5.3 数组方法

{}=>Object.prototype

[]=>Array.prototype

#### Array.prototype.join

将数组转换为字符串

```
var arr=[1,2,3];
arr.join(); //"1,2,3"
arr.join("_"); //"1_2_3"
```

用join可以创建一个函数，重复某个字符串n次

```
function repeatString(str,n){
  return new Array(n+1).join(str);
}
repeatString("a",3); //"aaa"
```

#### Array.prototype.reverse

将数组逆序，**原数组会被修改**

```
var arr=[1,2,3];
arr.reverse(); //[3,2,1]
arr; //[3,2,1]
```

#### Array.prototype.sort

数组排序，默认按照字母顺序排序，**原数组会被修改**。

```
var arr=["a","d","c","b"];
arr.sort(); //["a","b","c","d"]

arr=[13,24,51,3];
arr.sort(); //[13,24,3,51]
arr; //[13,24,3,51]

arr.sort(
	function(a,b){
      return a-b;
	}
); //[3,13,24,51]
```

#### Array.prototype.concat

数组合并，**原数组不会被修改**。可以把数组元素作为参数，其中数组元素会被拉平。

注意：若参数数组中还有数组，只会拉平一次。

```
var arr=[1,2,3];
arr.concat(4,5); //[1,2,3,4,5]
arr; //1,2,3

arr.concat([10,11],13); //[1,2,3,10,11,13]

arr.concat([1,[2,3]]); //[1,2,3,1,[2,3]]
```

#### Array.prototype.slice

返回数组的片段，**不会修改原数组**

```
var arr=[1,2,3,4,5];
arr.slice(1,3); //[2,3]
arr.slice(1); //[2,3,4,5]
arr.slice(1,-1); //[2,3,4]
arr.slice(-4,-3); //[2]
```

#### Array.prototype.splice

数组拼接，**原数组会被修改**

```
var arr=[1,2,3,4,5];;
arr.splice(2); //returns [3,4,5]
arr; //[1,2];

arr=[1,2,3,4,5];
arr.splice(2,2); //returns [3,4]
arr; //[1,2,5]

arr=[1,2,3,4,5];
arr.splice(1,1,'a','b'); //returns [2]
arr; //[1,"a","b",3,4,5]
```

#### Array.prototype.forEach(ES5)

数组遍历

```
var arr=[1,2,3,4,5];
arr.forEach(function(x,index,a){
  console.log(x+'|'+index+'|'+(a===arr));
}
);
//1|0|true
//2|1|true
//3|2|true
//4|3|true
//5|4|true
```

#### Array.prototype.map(ES5)

数组映射，**原数组不会被修改**

```
var arr=[1,2,3];
arr.map(function(x){
  return x+10;
}); //[11,12,13]
arr; //[1,2,3]
```

#### Array.prototype.filter(ES5)

数组过滤，**原数组不会被修改**

```
var arr=[1,2,3,4,5,6,7,8,9,10];
arr.filter(function(x,index){
  return index%3===0||x>=8;
}); //returns[1,4,7,8,9,10]
arr; //[1,2,3,4,5,6,7,8,9,10]
```

#### Array.prototype.every&some(ES5)

数组判断

```
var arr=[1,2,3,4,5];
arr.every(function(x){
  return x<10;
}); //true
arr.every(function(x){
  return x<3;
}); //false

var arr=[1,2,3,4,5];
arr.some(function(x){
  return x===3;
}); //true
arr.some(function(x){
  return x===100;
}); //false
```

#### Array.prototype.reduce&reduceRight

reduce:数组中元素两两之间操作，最后得到唯一的值。

```
var arr=[1,2,3];
var sum=arr.reduce(function(x,y){
  return x+y
},0); //6
arr; //[1,2,3]

arr=[3,9,6];
var max=arr.reduce(function(x,y){
  console.log(x+"|"+y);
  return x>y?x:y;
});
// 3|9
// 9|6
max; //9
```

<img src="https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180309164331.png" style="zoom:80%">

reduceRight:从右到左开始遍历

```
max=arr.reduceRight(function(x,y){
  console.log(x+"|"+y);
  return x>y?x:y;
});
//6|9
//9|3
max; //9
```

#### Array.prototype.indexOf&lastIndexOf(ES5)

数组检索

indexOf(查找的元素,起始位置)

```
var arr=[1,2,3,2,1];
arr.indexOf(2); //1
arr.indexOf(99); //-1
arr.indexOf(1,1); //4
arr.indexOf(1,-3); //4
arr.lastIndexOf(2); //3
arr.lastIndexOf(2,-2); //3
arr.lastIndexOf(2,-3); //1
```

#### Array.isArray

判断是否为数组

```
Array.isArray([]); //true

[] instancrof Array; //true
({}).toString.apply([])==='[object Array]'; //true
```

#### 数组与对象、字符串的比较

数组--一般对象

相同点：1.都可以继承2.数组是对象，对象不一定是数组3.都可以当做对象添加删除属性

不同点：1.数组自动更新length2.按索引访问数组常常比访问一般对象属性明显迅速3.数组对象继承Array.prototype上的大量数组操作方法

数组--字符串

字符串是类数组的元素

通过``Array.prototype.XX.call()``的方法使用数组方法

```
var str="hello world";
str.charAt(0); //"h"
str[1]; //e

Array.prototype.join.call(str,"_");
//"h_e_l_l_o__w_o_r_l_d"
```

## 第六章 函数和作用域（上）

函数是一块JavaScript代码，被定义一次，但可执行和调用多次。JS中的函数也是对象，所以JS函数可以像其它对象那样操作和传递，所以我们也常叫JS中的函数为函数对象。

### 6.1 函数定义

函数使用function来定义，其后跟随一些组成部分：函数名称标识符、一对圆括号、一对花括号

```
//输出o的每个属性的名称和值，返回undefined
function printprops(o){
  for(var p in o)
  console.log(p+":"+o[p]+"\n");
}
//计算两个笛卡尔坐标(x1,y1)和(x2,y2)之间的距离
function distance(x1,y1,x2,y2){
  var dx=x2-x1;
  var dy=y2-y1;
  return Math.sqrt(dx*dx+dy*dy);
}
```

可以把函数赋值给变量

```
var square=function(x){return x*x;}
```

函数表达式可以包含名称，这在递归时很有用

```
var f=function fact(x){
  if (x<=1) return 1;
  else return x*fact(x-1);
}
```

函数表达式也可以作为参数传给其它函数

```
data.sort(function(a,b){
  return a-b;
});
```

函数表达式有时定义后立即调用

```
var tensquared=(function(x){
  return x*x;
}(10));
```

函数声明语句“被提前”到外部脚本或外部函数作用域的顶部时可以被在它定义之前出现的代码调用。以表达式形式定义的函数在定义之前无法调用。

在JS里，函数可以嵌套在其他函数里。

```
function hypotenuse(a,b){
  function square(x){return x*x;}
  return Math.sqrt(square(a)+square(b));
}
```

嵌套函数可以访问嵌套他们的函数的参数和变量。如上面代码中square()可以读写外部函数hypotenuse()定义的a,b.

### 6.2 函数调用

有4种方法调用JavaScript函数：

1.作为函数2.作为方法3.作为构造函数4.通过它们的call()和apply()方法间接调用

使用调用表达式可以进行普通的函数调用也可进行方法调用。如果函数表达式是一个属性访问表达式，即该函数是一个对象的属性或数组中的一个元素，那么它就是一个方法调用表达式。

```
printprops({x:1});
var total=distance(0,0,2,1)+distance(2,1,3,5);
```

以函数形式调用的函数通常不使用this关键字。不过，"this"可以用来判断当前是否是严格模式。

```
var strict=(function(){return !this;}());
```

#### 方法调用

```
o.m=f;
o.m();
o.m(x,y);
```

对方法调用的参数和返回值的处理，和普通函数调用完全一致。但是，方法调用和函数调用有一个重要区别，即：调用上下文。属性访问表达式由两部分组成：一个对象(o)和属性名称(m)。像这样的方法调用表达式里，对象o成为调用上下文，函数体可以使用关键字this引用该对象。

```
var calculator={ //对象直接量
  operand1:1,
  operand2:1,
  add:function(){
  //this指代当前对象
    this.result=this.operand1+this.operand2;
  }
};
calculator.add(); //2
calculator.result; //2
```

<img src="https://github.com/lvhanh/study/raw/master/picture/QQ%E6%88%AA%E5%9B%BE20180312165931.png" style="zoom:80%">



