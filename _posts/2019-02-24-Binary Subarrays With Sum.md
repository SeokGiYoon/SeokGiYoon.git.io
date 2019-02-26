---
layout: post
title:  "【アルゴリズム勉強】JavaでBinary Subarrays With Sumアルゴリズム解決"
date:   2019-02-19
tags:
image:
comments: true
---

LeetCodeでアルゴリズムを解決！

# 課題
In an array A of 0s and 1s, how many non-empty subarrays have sum S?

 

Example 1:
```shell
Input: A = [1,0,1,0,1], S = 2
Output: 4
Explanation: 
The 4 subarrays are bolded below:
[1,0,1,0,1]
[1,0,1,0,1]
[1,0,1,0,1]
[1,0,1,0,1]
```

Note:
```shell
A.length <= 30000
0 <= S <= A.length
A[i] is either 0 or 1.

```

# 解決コード
Java

```shell
class Solution {
    public int numSubarraysWithSum(int[] A, int S) {
        int sumTemp = 0;
        int result = 0;
        
        
        
        for(int i = 0 ; i<A.length ; i++){
           int sum = 0;
            for(int j = i; j < A.length ; j ++){
                sum += A[j];
                if(sum == S){
                    ++result;
                }
            }
        }
        return result;
    }

}

```



# 参考
- https://leetcode.com/problems/binary-subarrays-with-sum/
