---
layout: post
title:  "【アルゴリズム勉強】JavaでReverse Vowels of a Stringアルゴリズム解決"
date:   2019-02-25
tags:
image:
comments: true
---

LeetCodeでアルゴリズムを解決！

# 課題
Write a function that takes a string as input and reverse only the vowels of a string.

Example 1:
```shell
Input: "hello"
Output: "holle"
Example 2:
```

```shell
Input: "leetcode"
Output: "leotcede"
```

```shell
Note:
The vowels does not include the letter "y".
```

# 解決コード
Java

```shell
class Solution {
    public String reverseVowels(String s) {
        char[] resultS = s.toCharArray();
        int rear = resultS.length-1;
        char temp = 0;
        
        for(int i = 0; i<resultS.length;i++){
            if(checkVowels(resultS[i])){
                for(int j = rear; j > i; j--){
                    if(checkVowels(resultS[j])){
                        rear = j-1;
                        temp = resultS[i];
                        resultS[i] = resultS[j];
                        resultS[j] = temp;
                        break;
                    }
                }
            }
        }
        return String.valueOf(resultS);
        
    }
    
    public boolean checkVowels(char v){
        return 'a' == v || 'A' == v || 'e' == v || 'E' == v || 'i' == v ||
            'I' == v || 'o' == v || 'O' == v || 'u' == v || 'U' == v;
    }
}


```



# 参考
- https://leetcode.com/problems/reverse-vowels-of-a-string/
