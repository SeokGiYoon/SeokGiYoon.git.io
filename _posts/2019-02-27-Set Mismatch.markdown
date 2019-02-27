---
title: "【アルゴリズム勉強】JavaでSet Mismatchアルゴリズム解決"
layout: post
date: 2016-02-27
tag: jekyll
projects: true
category: project
author: Seokgi
externalLink: false
---



LeetCodeでアルゴリズムを解決！

# 課題
The set S originally contains numbers from 1 to n. But unfortunately, due to the data error, one of the numbers in the set got duplicated to another number in the set, which results in repetition of one number and loss of another number.

Given an array nums representing the data status of this set after the error. Your task is to firstly find the number occurs twice and then find the number that is missing. Return them in the form of an array.

Example 1:
```shell
Input: nums = [1,2,2,4]
Output: [2,3]
```

Note:
The given array size will in the range [2, 10000].
The given array's numbers won't have any order.


# 解決コード
Java

```shell
class Solution {
    public int[] findErrorNums(int[] nums) {
        int duCount = 0;
        int du = 0;
        int empty = 0;
        for(int i = 1; i < nums.length+1 ; i++){
            for(int j = 0 ; j < nums.length ; j++){
                if(i == nums[j]){
                    duCount++;
                }
            }


            if(duCount == 2){
                du = i;
            }

            if(duCount == 0){
                empty = i;
            }

            duCount = 0;


        }

        int []result = {du,empty};

        return result;
    }
}

```



# 参考
- https://leetcode.com/problems/binary-subarrays-with-sum/
