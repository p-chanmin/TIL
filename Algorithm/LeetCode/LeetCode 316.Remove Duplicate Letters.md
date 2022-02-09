> https://leetcode.com/problems/remove-duplicate-letters/



# LeetCode : 316. Remove Duplicate Letters﻿

﻿

: Given a string s, remove duplicate letters so that every letter appears once and only once. You must make sure your result is **the smallest in lexicographical order** among all possible results.

**: 문자열 s가 주어집니다. 문자열에서 모든 문자가 한 번만 나타나도록 중복 문자를 제거합니다. 사전식 순서로 나열하여야 합니다.**



**Example 1:**

```python
Input: s = "bcabc"
Output: "abc"
```

**Example 2:**

```python
Input: s = "cbacdcbc"
Output: "acdb"
```



**Constraints:**

1 <= s.length <= 104

s consists of lowercase English letters.

---



**Submissions Code (Accepted):**

```python
class Solution:
    def removeDuplicateLetters(self, s: str) -> str:
        
        for char in sorted(set(s)):
            suffix = s[s.index(char):]
            
            if set(s) == set(suffix):
                return char + self.removeDuplicateLetters(suffix.replace(char, ''))
        return ''
```

Runtime: 52 ms, faster than 20.64% of Python3 online submissions for Remove Duplicate Letters.

Memory Usage: 14.5 MB, less than 21.63% of Python3 online submissions for Remove Duplicate Letters.



재귀를 이용하여 문제를 해결할 수 있다. set를 통해 중복이 제거된 집합을 만들 수 있다. 이를 정렬하여 반복문을 시작한다. 사전순으로 제일 처음에 오는 값 부터 char로 반복문을 돌게 된다.

이때, char을 기준으로 슬라이싱 하여 suffix에 저장한다. 이는 분리된 문자열과, 기존 문자열의 집합, 즉 사용된 문자가 같다면 사전순으로 제일 앞에 있는 문자열인 char이 올 자리임을 명시한다.

그것을 set(s) == set(suffix)로 판단한다. 문자 char 그리고 그 다음은 재귀적으로 suffix에서 char문자열을 제거한 문자열을 넣어 다시 똑같은 방법으로 찾는 것이다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def removeDuplicateLetters(self, s: str) -> str:
        
        counter, stack = collections.Counter(s), []
        
        for char in s:
            counter[char] -= 1
            if char in stack:
                continue
                
            while stack and char < stack[-1] and counter[stack[-1]] > 0:
                stack.pop()
            stack.append(char)
            
        return ''.join(stack)
```

Runtime: 36 ms, faster than 74.44% of Python3 online submissions for Remove Duplicate Letters.

Memory Usage: 14.2 MB, less than 92.14% of Python3 online submissions for Remove Duplicate Letters.



스택과 카운터를 사용한 풀이이다. 먼저 collections.Counter를 통해 s 문자열의 카운터를 생성하고 빈 스택을 생성한다.

그리고 반복문을 돌면서 카운터의 값들을 하나씩 줄여준다. 이때 스택에 이미 들어있는 문자라면 스킵한다.

안에서 while문은 스택이 존재하고, 스택의 맨 위 요소가 해당 문자열보다 뒤에 와야하며, 맨 위 요소가 뒤에 더 존재할 경우 이것들을 스택에서 제거해준다.

그 후 스택에 추가한다. 이 과정을 반복하면 stack에는 최종적으로 원하는 결과를 가진 리스트가 되는데,

이를 join을 통해 합쳐서 반환해준다. 재귀 구조보다 빠른 속도를 보인다.



**Using Keyword**

collections.Counter(s) - 카운터, key = 값, value = 중복개수

s.replace(a, b) - 문자열 s에서 a를 b로 대체함