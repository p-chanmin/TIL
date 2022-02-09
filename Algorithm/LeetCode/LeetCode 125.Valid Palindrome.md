> https://leetcode.com/problems/valid-palindrome/



# LeetCode : 125. Valid Palindrome

﻿

: Given a string s, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

**: 주어진 문자열 s가 팰린드롬인지 확인하라. 대소문자를 구분하지 않으며, 영문자와 숫자만을 대상으로 한다.**



*** 팰린드롬(Palindrome)**

**palindrome은 "회문(回文)"이다. "eye", "madam", "level", "Hannah" 등처럼 역순으로 읽어도 같은 말이 되는 말을 말한다.**



**Example 1:**

```python
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

**Example 2:**

```python
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

**Constraints:**

1 <= s.length <= 2 * 105

s consists only of printable ASCII characters.

---



**Submissions Code:**

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        strs=[]
        for i in s:
            if i.isalnum():
                strs.append(i.lower())

        for i in range(len(strs)//2):
            if strs[i]!=strs[len(strs)-1-i]:
                return False

        return True
```

.isalnum()은 영문자, 숫자 여부를 판별하는 함수로 해당하는 문자만 strs에 추가한다.

이때, 대소문자를 구분하지 않으므로 .lower()로 소문자로 변환한다.

그 후 strs 길이의 절반만큼 반복문을 돌면서 팰린드롬 여부를 판별한다.

반복문이 종료될 때까지 False 값이 return 되지 않으면 True를 반환한다.



**Other Submissions Code 1**:

**- Using Deque**

```python
import collections

class Solution:
    def isPalindrome(self, s: str) -> bool:
        strs = collections.deque()

        for i in s:
            if i.isalnum():
                strs.append(i.lower())

        while len(strs) > 1:
            if strs.popleft() != strs.pop():
                return False

        return True
```

.popleft() 와 .pop()을 사용해서 비교한다.



**Other Submissions Code 2**:

**- Using Slicing**

```python
import re

class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = s.lower()

        s = re.sub('[^a-z0-9]', '', s)

        return s == s[::-1]
```

먼저 대소문자 구문을 하지 않으므로 s를 모두 소문자로 변환한다.

re.sub를 통해서 정규 표현식으로 불필요한 문자열을 필터링한다.

re.sub(검색 패턴, 변경 문자, 검색할 문자열)으로 위는 s에서 a-z0-9가 아닌 문자열을 공백으로 변환한다.

만약 s가 팰린드롬이라면 s를 뒤집은 것도 동일하므로 슬라이싱을 사용하여 뒤집은 경우와 아닌 경우가 같은지 아닌지를 결과로 출력한다. s[::-1]은 문자열을 뒤집는 슬라이싱이다.



**Using keyword**

char.isalnum() - 문자가 알파벳 또는 숫자인지 판별

str.lower() - 문자 또는 문자열을 소문자로 변경

collections.deque() - 덱 생성

deque.popleft() - 제일 왼쪽 데이터 반환

re.sub(검색 패턴(졍규 표현식), 변경 문자, 검색할 문자열) - 정규 표현식으로 문자열 반환

s[::-1] - 문자열을 뒤집음



﻿