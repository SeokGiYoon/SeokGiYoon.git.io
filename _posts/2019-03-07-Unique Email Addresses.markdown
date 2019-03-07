---
title: "【アルゴリズム勉強】Javaで Unique Email Addressesアルゴリズム解決"
layout: post
date: 2019-03-07
tag: jekyll
projects: true
category: project
author: Seokgi
externalLink: false
---



LeetCodeでアルゴリズムを解決！

# 課題

Every email consists of a local name and a domain name, separated by the @ sign.

For example, in alice@leetcode.com, alice is the local name, and leetcode.com is the domain name.

Besides lowercase letters, these emails may contain '.'s or '+'s.

If you add periods ('.') between some characters in the local name part of an email address, mail sent there will be forwarded to the same address without dots in the local name.  For example, "alice.z@leetcode.com" and "alicez@leetcode.com" forward to the same email address.  (Note that this rule does not apply for domain names.)

If you add a plus ('+') in the local name, everything after the first plus sign will be ignored. This allows certain emails to be filtered, for example m.y+name@email.com will be forwarded to my@email.com.  (Again, this rule does not apply for domain names.)

It is possible to use both of these rules at the same time.

Given a list of emails, we send one email to each address in the list.  How many different addresses actually receive mails?



Example 1:
```shell
Input: ["test.email+alex@leetcode.com","test.e.mail+bob.cathy@leetcode.com","testemail+david@lee.tcode.com"]
Output: 2
Explanation: "testemail@leetcode.com" and "testemail@lee.tcode.com" actually receive mails
```

Note:
```shell
1 <= emails[i].length <= 100
1 <= emails.length <= 100
Each emails[i] contains exactly one '@' character.
```


# 説明
중복을 제거하여 유니크한 데이터를 처리해야하고 중복이 허용 되지않는 자료구조 Set을 선택한다. 그 중에서도
데이터의 순서에 상관없고 가장빠른 HashSet을 사용합니다.
일단 emails배열에서 name부븐을 추출하여 .을 없애고 최초의 + 앞의 문자까지만 처리 한 후 domailName과 합쳐줍니다.
그 후 선언된 HashSet에 넣어줍니다.
※String의 replaceAll에서 .을 제거 할 때는 .만 입력했을 경우 모든 문자로 인식되므로 \\을 추가하여 처리합니다.


# 解決コード
Java

```shell
class Solution {
    public int numUniqueEmails(String[] emails) {

        Set<String> result = new HashSet();

        for(int i = 0 ; i<emails.length ; i++){

            String[] sep = emails[i].split("@");
            sep[0] = sep[0].replaceAll("\\.","");

            if(sep[0].indexOf('+') != -1){
                int plusIndex = sep[0].indexOf('+');

                sep[0] = sep[0].substring(0 , plusIndex);
            }
            emails[i] = sep[0] + "@" + sep[1];

            result.add(emails[i]);

        }
        return result.size();
    }
}

```



# 参考
- https://leetcode.com/problems/unique-email-addresses/
