---
title: "【アルゴリズム勉強】Javaで Remove Duplicates from Sorted Arrayアルゴリズム解決"
layout: post
date: 2019-03-22
tag: jekyll
projects: true
category: project
author: Seokgi
externalLink: false
---



LeetCodeでアルゴリズムを解決！

# 課題

Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

Example 1:
```shell

Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```
Example 2:
```shell
Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.
```
Clarification:

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by reference, which means modification to the input array will be known to the caller as well.

Internally you can think of this:
```shell
// nums is passed in by reference. (i.e., without making a copy)
int len = removeDuplicates(nums);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```
# 説明
주어진 배열에서 index 0 부터 차례대로 찾아가며 다른 숫자가 나오면 그 숫자를 nums배열에 inIndex배열이 가르키는 위치에 넣고 inIndex는 +1을 한다.
그리고 리턴은 따로 저장하여 +1 한 int변수를 리턴한다.

# 解決コード
Java

```shell
class Solution {
    public int removeDuplicates(int[] nums) {
        int inIndex = 1;

        for(int i = 0 ; i < nums.length-1 ; i++){
            if(nums[i] != nums[i+1]){

                nums[inIndex++] = nums[i+1];

            }
        }
        return inIndex;
    }

}

```



# 参考
- https://leetcode.com/problems/add-to-array-form-of-integer/
