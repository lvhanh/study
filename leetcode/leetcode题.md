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