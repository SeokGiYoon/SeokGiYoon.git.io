---
title: "【アルゴリズム勉強】Javaで Jewels and Stonesアルゴリズム解決"
layout: post
date: 2019-03-19
tag: jekyll
projects: true
category: project
author: Seokgi
externalLink: false
---



LeetCodeでアルゴリズムを解決！

# 課題

You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

Example 1:
```shell
Input: J = "aA", S = "aAAbbbb"
Output: 3
Example 2:
```

```shell
Input: J = "z", S = "ZZ"
Output: 0
```
Note:

S and J will consist of letters and have length at most 50.
The characters in J are distinct.



# 解決コード
Java

```shell
class Solution {
    public int numJewelsInStones(String J, String S) {
        char [] j = J.toCharArray();
        char [] s = S.toCharArray();
        int result = 0;

        for(int i = 0 ; i<j.length ; i++){
            for(int t = 0 ; t < s.length ; t++){
                if(j[i] == s[t]){
                    result++;
                }
            }
        }
        return result;
    }
}
```



# 参考
- https://leetcode.com/problems/jewels-and-stones/
