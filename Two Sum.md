# [1. Two Sum](https://leetcode.com/problems/two-sum/)

## 题目

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```



## 题目大意

在数组中找到 2 个数之和等于给定值的数字，结果返回 2 个数字在数组中的下标。
1.使用for循环将对依次取出整个数组的值nums[i]; 0 <= i < numsSize.

2.在for循环内再进行for循环nums[j]查找是否有满足nums[i] + nums[j] == target; i+1 <= j <n umsSize.

3.如果有满足条件的将它们的次序放入Return数组 返回

4.如果将所有的都遍历后都没有返回NULL.

## 解题方法

```
int* twoSum(int* nums, int numsSize, int target, int* returnSize){
    int i , j, num1;
    *returnSize = 2;
    int* Return = (int*)malloc(sizeof(int)*2);  //分配空间
    for(i = 0; i < numsSize; i++){
      num1 = target - nums[i]; 
        for(j = i+1 ; j < numsSize; j++){
            if(num1 == nums[j])
            {
            Return[0] = i;
            Return[1] = j;
            return Return;
            }
        }
    }
    return NULL;
}
```

## 时间复杂度
此种算法时间复杂度为O(n^2)

大佬算法时间复杂度为O(n)[halfrost](https://github.com/halfrost/LeetCode-Go)
