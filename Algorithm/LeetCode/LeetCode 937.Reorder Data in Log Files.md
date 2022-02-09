> https://leetcode.com/problems/reorder-data-in-log-files/



# LeetCode : 937. Reorder Data in Log Files

﻿

: You are given an array of logs. Each log is a space-delimited string of words, where the first word is the **identifier**.



There are two types of logs:

Letter-logs: All words (except the identifier) consist of lowercase English letters.

Digit-logs: All words (except the identifier) consist of digits.



Reorder these logs so that:

\1. The letter-logs come before all digit-logs.

\2. The letter-logs are sorted lexicographically by their contents. If their contents are the same, then sort them lexicographically by their identifiers.

\3. The digit-logs maintain their relative ordering.

Return *the final order of the logs*.



**:** **로그 배열이 주어집니다. 각 로그는 공백으로 구분된 단어 문자열이며, 첫 번째 단어는 식별자입니다.**



**: 로그에는 두가지 유형이 있습니다.**

**letter-logs : 식별자를 제외한 모든 단어는 소문자로 구성되어 있습니다.**

**digit-logs : 식별자를 제외한 모든 단어는 숫자로 구성되어 있습니다.**



**: 다음과 같이 로그의 순서를 변경하세요.**

**1. letter-logs가 digit-logs보다 앞에 온다.**

**2. letter-logs는 내용을 기준, 사전순으로 정렬합니다. 단, 문자가 동일한 경우 식별자 순으로 정렬합니다.**

**3. digit-logs는 입력 순서대를 유지합니다.**



**Example 1:**

```python
Input: logs = ["dig1 8 1 5 1","let1 art can","dig2 3 6","let2 own kit dig","let3 art zero"]
Output: ["let1 art can","let3 art zero","let2 own kit dig","dig1 8 1 5 1","dig2 3 6"]
Explanation:
The letter-log contents are all different, so their ordering is "art can", "art zero", "own kit dig".
The digit-logs have a relative order of "dig1 8 1 5 1", "dig2 3 6".
```

**Example 2:**

```python
Input: logs = ["a1 9 2 3 1","g1 act car","zo4 4 7","ab1 off key dog","a8 act zoo"]
Output: ["g1 act car","a8 act zoo","ab1 off key dog","a1 9 2 3 1","zo4 4 7"]
```



**Constraints:**

1 <= logs.length <= 100

3 <= logs[i].length <= 100

All the tokens of logs[i] are separated by a **single** space.

logs[i] is guaranteed to have an identifier and at least one word after the identifier.

---



**Submissions Code:**

```python
class Solution:
    def reorderLogFiles(self, logs: List[str]) -> List[str]:
        letter_logs, digit_logs = [], []
        
        for l in logs:
            if l.split()[1].isnumeric():
                digit_logs.append(l)
            else:
                letter_logs.append(l)
        
        letter_logs.sort(key = lambda x: (x.split()[1:], x.split()[0]))
        
        return letter_logs + digit_logs
```

split()을 통해 공백을 기준으로 주어진 문자열을 리스트로 바꾼다. 이 때 1번째 요소가 숫자인지 아닌지로 letter_logs와 digit_logs를 구별하는데, 이때 isnumeric()을 통해 구분한다.

isnumeric()과, isdigit(),isdecimal()등 모두 사용 가능하지만, 이 중 isnumeric()을 사용했다.



letter_logs와 digit_logs를 구분하고, letter_logs의 정렬은 람다식을 사용하였다.

정렬 sort()를 사용하는데, 식별자를 제외하고 정렬해야 하므로, key 값으로 x.split()[1:]를 사용했다.

그리고, 후순위로 식별자를 통해 정렬하므로 x.split()[0]을 사용했다.



최종적으로 letter_logs가 앞에 와야하므로 letter_logs + digit_logs로 두 리스트를 합쳐서 반환하였다.



**Using Keyword**

isnumeric() - 숫자값 표현에 해당하는 문자열까지 인정한다.(제곱근 및 분수, 거듭제곱 특수문자)

isdigit() - 숫자처럼 생긴 '모든 글자'를 숫자로 친다

isdecimal() - 주어진 문자열이 int형으로 변환이 가능한지 알아내는 함수, 특수문자 중 숫자모양을 숫자로 치지않는다.

> https://it-neicebee.tistory.com/33 [IT's Portfolio]



rambda x - 람다 표현식

list1 + list2 - 리스트 이어 붙이기

