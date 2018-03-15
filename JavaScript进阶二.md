

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

**注意：**this是一个关键字，不是变量也不是属性名，不允许给this赋值。

关键字this没有作用域的限制，嵌套的函数不会从调用它的函数中继承this。如果嵌套函数作为方法调用，其this的值指向调用它的对象。如果嵌套函数作为函数调用，其this的值不是全局对象（非严格模式下）就是undefined（严格模式下）。

```
var o={
  m:function(){
    var self=this; //将this的值保存至一个变量中
    console.log(this===o); //true，this就是这个对象o
    f();
    function f(){
      console.log(this===o); //false,this的值是全局对象或undefined
      console.log(self===o); //true,self指外部函数的this值
    }
  }
};
```

#### 构造函数调用

构造函数调用和普通函数调用以及方法调用在实参处理、调用上下文和返回值方面都有不同。

如果构造函数没有形参，JavaScript构造函数调用的语法是允许省略实参列表和圆括号的。

```
var o=new Object();
var o=new Object;
```

#### 间接调用

函数也是对象，函数对象也可以包含方法，其中两个方法call()和apply()可以用来间接地调用函数。

### 6.3 函数的实参和形参

#### 可选形参

当调用函数的时候传入的实参比函数申明时指定的少，剩下的形参都将设置为undefined。因此应该给省略的参数赋一个默认值。

```
//将对象o中可枚举的属性名追加至数组a中，并返回这个数组a
//如果省略a，则创建一个新数组并返回这个新数组
function getPropertyNames(o,/*optional*/ a){
  if(a===undefined) a=[]; //如果未定义，则使用新数组
  for(var property in o)a.push(property);
  return a;
}
//这个函数调用可以传入1或2个实参
var a=getPropertyNames(o); //将o的属性存储到一个新数组中
getPropertyNames(p,a); //将p的属性追加至数组a中
```

**注意：**当用可选实参来实现函数时，需要将可选实参放在实参列表的最后，使用注释/*optional\*/来强调形参时可选的。

#### 可变长的实参对象

当调用函数的时候传入的实参个数超过形参时，没有办法直接获得未命名值得引用。在函数体内，标识符arguments时指向实参对象的引用，实参对象时一个类数组对象，这样可以通过下标访问传入函数的实参值。

```
function f(x,y,z){
//首先验证传入实参的个数
  if(arguments.length!=3){
    throw new Error("function f called with"+arguments.length+"arguments,but it expects 3 arguments.");
  }
  //执行其他逻辑
}
```

实参对象有重要的用处就是让函数可以操作任意数量的实参

```
function max(/*...*/){
  var max=Number.NEGATIVE_INFINITY;
  //遍历实参，查找并记住最大值
  for(var i=0;i<arguments.length;i++)
  	if(arguments[i]>max) max=arguments[i];
  return max;
}
var largest=max(1,10,100,2,3,1000)
```

```
function f(x){
  console.log(x); //输出实参的初始值
  arguments[0]=null; //修改实参数组的元素会改变x的值
  console.log(x);	//输出null
}
```

通过实参名字修改实参值的话，通过arguments[]数组也可以获取到更改后的值。

**注意：**在ES5中移除了实参对象的这个特殊特性。在非严格模式中，函数里的arguments仅仅是标识符，在严格模式中它变成了保留字。严格模式中的函数无法使用arguments作为形参名或局部变量名，也不能赋值。

callee和caller属性：

除了数组元素，实参对象还定义了callee和caller属性。

callee属性指代当前正在执行的函数，caller是非标准的，指代调用当前正在执行的函数的函数，通过caller属性可以访问调用栈。

```
var factorial=function(x){
  if(x<=1) return 1;
  return x*arguments.callee(x-1);
}
```

#### 将对象属性用作实参

通过名/值对的形式来传入参数，这样参数的顺序就无关紧要了。定义函数的时候，传入的参数都写入一个单独的对象之中，在调用的时候传入一个对象，对象中的名/值对是真正需要的实参数据。

```
//将原始数组的length元素复制至目标数组
//开始复制原数组的from_start元素
//并且将其复制至目标数组的to_start中
function arraycopy(/*array*/ from,/*index*/ from_start,/*array*/ to,/*index*/ to_start,/*integer*/ length){
  //代码
}
//效率低，但不必记住实参的顺序
//并且from_sart和to_start都默认为0
function easycopy(args){
  arrcopy(args.from,
  args.from_start||0,
  args.to,
  args.to_start||0,
  args.length
  );
  var a=[1,2,3,4],b=[];
  easycopy({from:a,to:b,length:4});
}
```

#### 实参类型检测

JavaScript方法的形参并未申明类型，在形参传入函数体之前也未做任何类型检查。

```
//返回数组（或类数组对象）a的元素的累加和
//数组a中必须为数字，null和undefined的元素都将忽略
function sum(a){
  if(isArrayLike(a)){
    var total=0;
    for(var i=0;i<arguments.length;i++){
      var element=a[i];
      if(element==null) continue; //跳过null和undefined
      if（isFinite(element)) total+=element;
      else throw new Eror("sum():element must be finite numbers");
    }
    return total;
  }
  else throw new Error("sum():argument must be array-like");
}
```

### 6.4 作为值的函数

函数不仅是语法也是值。可以将函数赋值给变量，存储在对象的属性或数组的元素中，作为参数传入另外一个函数等。

```
function square(x){return x*x;}
//创建一个新的函数对象，并将其赋值给变量square
var s=square;
square(4); // 16
s(4);  // 16
```

除了赋值给变量，还可以将函数赋值给对象的属性。

```
var o={square:function(x){return x*x;}};
var y=o.square(16); //256
```

函数甚至不需要带名字，当把他们赋值给数组元素时

```
var a=[function(x){return x*x;},20];
a[0](a[1]); //400
```

```
//定义一些简单函数
function add(x,y){return x+y;}
function subtract(x,y){return x-y;}
function multiply(x,y){return x*y;}
function divide(x,y){return x/y;}

//这里函数以上面某个函数作为参数，并给它传入两个操作数然后调用它
function operate(operator,operand1,operand2){
  return operator(operand1,operand2);
}
var i=operate(add,operate(add,2,3),operate(multiply,4,5));
//使用函数直接量，重复实现
var operators={
  add:function(x,y){return x+y;},
  subtract:function(x,y){return x-y;},
  multiply:function(x,y){return x*y;},
  divide:function(x,y){return x/y;},
  pow:Math.pow //使用预定义函数
};
function operate2(operation,operand1,operand2){
  if(typeof operators[operation]==="function")
  return operators[operation](operand1,operand2);
  else throw "unknown operator";
}
var j=operate2("add","hello",operate2("add","","world"));
var k=operate2("pow",10,2)
```

#### 自定义函数属性

JavaScript中的函数是一种特殊对象，可以拥有属性。如果一个信息仅仅是函数本身用到，最好将这个信息保存到函数对象的一个属性中。

```
uniqueInteger.counter=0;
function uniqueInteger(){
  return uniqueInteger.counter++; //先返回计数器的值，然后自增1
}
```

### 6.5 作为命名空间的函数

在JavaScript中无法声明只在一个代码块内可见的变量，所以我们可以定义一个函数用作临时的命名空间，在这个命名空间内定义的变量不会污染到全局命名空间。

```
function mumodule(){
  //模块代码
  //这个模块所使用的所有变量都是局部变量
}
mymodule(); //调用这个函数
```

还可以直接定义一个匿名函数，并在单个表达式中调用它

```
(function(){
  //模块代码
}()); //结束函数定义并立即调用它
```

function之前的圆括号是必须的，不写圆括号解释器会试图将关键字function解析为函数声明语句，使用圆括号才会正确地将其解析为函数定义表达式。

特定场景下返回带补丁的extend()版本：

```
//定义一个扩展函数，用来将第二个以及后续参数复制至第一个参数
//如果o的属性拥有一个不可枚举的同步属性，则for/in循环
//不会枚举对象o的可枚举属性，也就是说不会正确处理诸如toString的属性
//除非我们显式检测它
var extend=(function(){
  //在修复之前先检测是否存在bug
  for(var p in {toString:null}){
    //如果代码执行到这里，那么for/in循环会正确工作并返回
    //一个简单版本的extend()函数
    return function extend(o){
      for(var i=1;i<arguments.length;i++){
        var source=arguments[i];
        for(var prop in source) o[prop]=source[prop];
      }
      return o;
    };
  }
  //如果代码执行到这里，说明for/in循环不会枚举测试对象的toString属性
  //因此返回另一个版本的extend()函数，这个函数显式测试
  //Object.property中的不可枚举属性
  return function patched_extend(o){
    for(var i=1;i<arguments.length;i++){
      var source=arguments[i];
      //复制所有的可枚举属性
      for(var prop in source) o[prop]=source[prop];
      //现在检查特殊属性
      for(var j=0;j<protoprops.length;j++){
        prop=protoprops[j];
        if(source.hasOwnProperty(prop)) o[prop]=source[prop];
      }
    }
    return o;
  };
  //这个列表列出了需要检查的特殊属性
  var protoprops=["toString","valueOf","constructor","hasOwnProperty","isPrototypeOf"]
}());
```

### 6.6 闭包

函数的执行依赖于变量作用域，这个作用域是在函数定义时决定的，而不是函数调用时决定的。为了实现这种词法作用域，JavaScript函数对象的内部状态不仅包含函数的代码逻辑，还必须引用当前的作用域链。

```
var scope="global scope"; //全局变量
function checkscope(){
  var scope="local scope"; //局部变量
  function f(){return scope;} //在作用域中返回这个值
  return f();
}
checkscope() //"local scope"
```

```
var scope="global scope";
function checkscope(){
  var scope="local scope";
  function f(){return scope;}
  return f;
}
checkscope()()
```

这段代码将函数内的一对圆括号移动到了checkscope()之后。checkscope()现在仅仅返回函数内嵌套的一个函数对象，而不是直接返回结果。嵌套的函数f()定义在这个作用域链里，其中的变量scope一定是局部变量，不管在何时何地执行函数f()，这种绑定在执行f()时依然有效。

```
function counter(){
  var n=0;
  return{
    count:function(){return n++;},
    reset:function(){n=0}
  };
}
var c=counter(),d=counter(); //创建两个计数器
c.count(); //0
d.count(); //0
c.reset(); //reset()和count()方法共享状态
c.count(); //0
d.count(); //1
```

counter()函数返回了一个计数器对象，两个方法都可以访问私有变量n。每次调用counter()都会创建一个新的作用域链和一个新的私有变量。因此，如果调用counter()两次，则会得到两个计数器对象，而且彼此包含不同的私有变量，调用其中一个计数器对象的count()或reset()不会影响另外一个对象。

用属性存取器方法getter和setter实现：

```
function counter(n){
  return{
    get count(){reutrn n++;},
    set count(m){
      if(m>=n) n=m;
      else throw Error("...")
    }
  };
}

```

利用闭包实现私有属性存取器方法：

```
function addPrivateProperty(o,name,predicate){
  var value; //这是一个属性值
  //getter方法简单地将其返回
  o["get"+name]=function(){return value;};
  //setter方法首先检查值是否合法，合法就将其存储起来
  o["set"+name]=function(v){
    if(predicate&&!predicate(v))
    throw Error("set"+name+":invalid value"+v);
    else
    value=v;
  };
}
//展示addPrivateProperty()方法
var o={}; //设置一个空对象
//增加属性存取器方法getName()和setName()
//确保只允许字符串值
addPrivateProperty(o,"Name",function(x){return typeof x=="string";});
o.setName("Frank"); //设置属性值
console.log(o.getName()); //得到属性值
o.setName(0); //试图设置一个错误类型值
```

**注意：**1.不要试图将循环代码移入定义这个闭包的函数内。

```
//返回一个函数组成的数组，他们的返回值是0~9
function constfuncs(){
  var funcs=[];
  for(var i=0;i<10;i++)
  funcs[i]=function(){return i;};
  return funcs;
}
var funcs=constfuncs();
funcs[5]() //
```

上面的代码创建了10个闭包，并将它们存储到一个数组中，这些闭包都是在一个函数调用中定义的，所以它们可以共享变量i。当constfuncs()返回时，变量i的值是10，所有的闭包都共享这个值。因此结果返回10.

2。this是JavaScript的关键字，不是变量。如果闭包在外部函数里是无法访问this的，除非外部函数将this转存为一个变量。arguments同理。

### 6.7 函数属性、方法和构造函数

#### length属性

函数的length属性是只读属性，它代表函数实参的数量，这里的参数指的是“形参”而非“实参”，也就是在函数定义时给出的实参个数，通常也是在函数调用时期望传入函数的实参个数。

```
function check(args){
  var actual=args.length; //实参的真实个数
  var expected=args.callee.length; //期望的实参个数
  if(actual!==expected)
  throw Error("Expected"+expected+"args;got"+actual);
}
function f(x,y,z){
  check(arguments); //检查实参个数和期望的实参个数是否一致
  return x+y+z; //再执行函数的后续逻辑
}
```

#### prototype属性

每一个函数都包含prototype属性，这个属性指向一个对象的引用，称做“原型对象”。





