---
title: "【アルゴリズム勉強】Javaで Add to Array-Form of Integerアルゴリズム解決"
layout: post
date: 2019-03-05
tag: jekyll
projects: true
category: project
author: Seokgi
externalLink: false
---



LeetCodeでアルゴリズムを解決！

# 課題

For a non-negative integer X, the array-form of X is an array of its digits in left to right order.  For example, if X = 1231, then the array form is [1,2,3,1].

Given the array-form A of a non-negative integer X, return the array-form of the integer X+K.



Example 1:
```shell
Input: A = [1,2,0,0], K = 34
Output: [1,2,3,4]
Explanation: 1200 + 34 = 1234
```

Example 2:
```shell
Input: A = [2,7,4], K = 181
Output: [4,5,5]
Explanation: 274 + 181 = 455
```

Example 3:
```shell
Input: A = [2,1,5], K = 806
Output: [1,0,2,1]
Explanation: 215 + 806 = 1021
```

Example 4:
```shell
Input: A = [9,9,9,9,9,9,9,9,9,9], K = 1
Output: [1,0,0,0,0,0,0,0,0,0,0]
Explanation: 9999999999 + 1 = 10000000000
```

Note：
```shell
1 <= A.length <= 10000
0 <= A[i] <= 9
0 <= K <= 10000
If A.length > 1, then A[0] != 0
```

# 説明
우선 K를 string형으로 바꿔줍니다. 바꿈으로써의 이점은 길이를 구할 수 있다는 것과 인덱스 별로 한 숫자씩 취득을 할 수 있다는 것입니다.

while문의 조건을 lengthA > 0 || lengthK > 0 이라는 조건을 주고 A와 K의 마지막인덱스부터 1씩 작아지면서 숫자 한글 자씩 가져옵니다.
두 변수 전부 길이가 0보다 클경우에는 length-1 번쨰의 숫자를 가져옵니다.
하지만 K는 string형식으로 변환하여 charAt함수를 이용했기 때문에 lengthK-1의 변수를 그대로 int형 변수(numK)에 넣으면 유니코드가 들어가기
떄문에 '0'만큼을 차감해 줍니다. 반대로 길이가 0 보다 작아 졌을 떄는 0을 넣어 합에서 0을 더하도록 합니다.
두 수의 합이 10보다 클경우는 다음 수에 carry를 더할 수 있도록 carry에 1을 넣어주고 다음수에 carry를 더할 것이기 때문에 합에서 10을 뻅니다.
반대로 10보다 작을 경우는 carry에 0을 넣어줍니다.
그리고 ArrayList에 값을 넣어줍니다.
마지막으로 수를 다 더한 후 carry가 1일 경우가 있으므로 1일 경우 ArrayList에 carry를 넣어줍니다.

Arraylist의 add메소드에는 두수의 합의 1의 단위부터 들어갔기 떄문에 숫자가 역순이 됩니다.
Collections.reverse를 이용하여 ArrayList의 값을 역으로 만들어주고 리턴합니다.


# 解決コード
Java

```shell
class Solution {
    public List<Integer> addToArrayForm(int[] A, int K) {
        List<Integer> result = new ArrayList<>();
        int lengthA = A.length;
        String stk = Integer.toString(K);
        int lengthK = stk.length();

        int carry = 0;
        int numA = 0;
        int numK = 0;
        int sum = 0;

        while(lengthA > 0 || lengthK > 0){

            numA = lengthA > 0 ? A[lengthA-1] : 0;
            numK = lengthK > 0 ? stk.charAt(lengthK-1) - '0' : 0;

            lengthA--;
            lengthK--;

            sum = numA + numK + carry;

            if(sum >= 10){
                carry = 1;
                sum -= 10;
            }else{
                carry = 0;
            }

            result.add(sum);
        }

        if(carry > 0) result.add(carry);


        Collections.reverse(result);

        return result;
    }
}

```



# 参考
- https://leetcode.com/problems/add-to-array-form-of-integer/
