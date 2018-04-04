## 两数之和

给定一个整数数列，找出其中和为特定值的那两个数。

你可以假设每个输入都只会有一种答案，同样的元素不能被重用。

**示例:**

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

```
var twoSum = function(nums, target) {
    var m=[];
    for(var i=0;i<nums.length;i++){
        for(var j=i+1;j<nums.length;j++){
            if(nums[i]+nums[j]==target){
                m.push(i,j);
                break;
            }
        }
    }
    return m;
};
```

从第一个开始遍历

## 两数之和 II - 输入有序数组

给定一个已按照**升序排列** 的有序数组，找到两个数使得它们相加之和等于目标数。

函数应该返回这两个下标值 index1 和 index2，其中 *index1* 必须小于 *index2。*请注意，返回的下标值（index1 和 index2）不是从零开始的。

你可以假设每个输入都只有一个解决方案，而且你不会重复使用相同的元素。

**输入：**数组 = {2, 7, 11, 15}, 目标数 = 9
**输出：***index1* = 1, *index2* = 2

```
var twoSum = function(numbers, target) {
    var m=[];
    for(var i=0;i<numbers.length;i++){
        for(var j=i+1;j<numbers.length;j++){
            if(numbers[i]+numbers[j]==target){
                m.push(i+1,j+1);
                break;
            }
        }
    }
    return m;
};
```

同一

```
var twoSum = function(numbers, target) {
    var i=0,j=numbers.length-1;
    var m=[];
    while(i<j){
        if(numbers[i]+numbers[j]==target){
            m.push(i+1,j+1);
            break;
        }
        else if(numbers[i]+numbers[j]>target){
            j--;
        }
        else{
            i++;
        }
    }
    return m;
};
```

因为是升序排列，所以取头尾两数，如果相同则输出，如果相加大于要求数则末尾数向左移一位，如果小于要求数则开头数向右移一位。

## 从排序数组中删除重复项

给定一个有序数组，你需要**原地**删除其中的重复内容，使每个元素只出现一次,并返回新的长度。

不要另外定义一个数组，您必须通过用 O(1) 额外内存**原地修改**输入的数组来做到这一点。

**示例：**

```
给定数组: nums = [1,1,2],

你的函数应该返回新长度 2, 并且原数组nums的前两个元素必须是1和2
不需要理会新的数组长度后面的元素
```

一.

```
var removeDuplicates = function(nums) {
   for(var i=0;i<nums.length;){
       if(nums[i]===nums[i+1])
           nums.splice(i,1);
       else
           i++;
   }
    return i;
};
```

因为是排序数组，所以只需两两比较，有相同的去掉前一个没相同的i+1

二.

```
var removeDuplicates = function(nums) {
    if (nums.length <= 1) return;
    var i=1,j=1,m=nums[0];
    while(i<nums.length){
        if(nums[i]!==m){
            nums[j]=nums[i];
            j++;
        }
        m=nums[i];
        i++;
    }
    return j;
};
```

若有相同的数字，由后一位替换前一位数字。

## 颠倒整数

给定一个范围为 32 位 int 的整数，将其颠倒。

**例 1:**

```
输入: 123
输出:  321 
```

**例 2:**

```
输入: -123
输出: -321
```

**例 3:**

```
输入: 120
输出: 21
```

**注意:**

假设我们的环境只能处理 32 位 int 范围内的整数。根据这个假设，如果颠倒后的结果超过这个范围，则返回 0。

一.

```
var reverse = function(x) {
    var i=0;
    var sign=(x>0)?1:-1;
    x=Math.abs(x);
    while(x>0){
        i=i*10+x%10;
        x=Math.floor(x/10);
    }
    if(i>2147483647) return 0;
    return i*sign;
};
```

运用除法的整数余数，用到Math对象。

二.

```
var reverse = function(x) {
    var i;
    var sign=(x>0)?1:-1;
    x=Math.abs(x);
    i=x.toString().split("").reverse().join("");
    if(i>2147483647) return 0;
    return i*sign;
};
```

将数字转换为数组，用reverse()颠倒后再转换为数字

## 回文数

判断一个整数是否是回文数。不能使用辅助空间。

**一些提示:**

负整数可以是回文数吗？（例如 -1）

如果你打算把整数转为字符串，请注意不允许使用辅助空间的限制。

你也可以考虑将数字颠倒。但是如果你已经解决了 “颠倒整数” 问题的话，就会注意到颠倒整数时可能会发生溢出。你怎么来解决这个问题呢？

本题有一种比较通用的解决方式。

```
var isPalindrome = function(x) {
    var i=0;
    var t=x;
    if(x<0||i>2147483647) return false;
    while(t>0){
        i=i*10+t%10;
        t=Math.floor(t/10);
        }
    if(i===x) return true;
    else return false;
};
```

需要注意的是将x赋值给一个变量，不然最后x一直为0.