---
layout: post
title:  "【アルゴリズム勉強】JavaでMultiply Stringsアルゴリズム解決"
date:   2019-02-19
tags:
image:
comments: true
---

LeetCodeでアルゴリズムを解決！

# 課題
Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.

Example 1:

```shell
Input: num1 = "2", num2 = "3"
Output: "6"
Example 2:
```
```shell
Input: num1 = "123", num2 = "456"
Output: "56088"
```
Note:

The length of both num1 and num2 is < 110.
Both num1 and num2 contain only digits 0-9.
Both num1 and num2 do not contain any leading zero, except the number 0 itself.
You must not use any built-in BigInteger library or convert the inputs to integer directly.

# 解決コード
Java

```shell
class Solution {
    public String multiply(String num1, String num2) {
        
        char[] num1Arr = num1.toCharArray();
        char[] num2Arr = num2.toCharArray();
    
        int n1Length = num1Arr.length;
        int n2Length = num2Arr.length;
        int n1result = 0;
        int n2result = 0;
        int n1resultTemp = 0;
        int n2resultTemp = 0;
        int result = 0;
        
        int maxLength = (n1Length>n2Length) ? n1Length:n2Length;
        int carry = 1;
        
        for(int i = maxLength ;i>0 ; i--){
            
            
            if(n1Length > 0){
                n1resultTemp = (((int)num1.charAt(n1Length-1))-48) * carry;
            }else{
                n1resultTemp = 0;
            }
            
            if(n2Length > 0){
                n2resultTemp = (((int)num2.charAt(n2Length-1))-48) * carry;
            }else{
                n2resultTemp = 0;
            }
            
            carry = carry * 10;
            
            n1result += n1resultTemp;
            n2result += n2resultTemp;
            
            n1Length--;
            n2Length--;
        }
        
        
        result = n1result * n2result;
        
        return result+"";
        
    }
}

```



# 参考
- https://leetcode.com/problems/multiply-strings/
