> https://leetcode.com/problems/longest-palindromic-substring/



# LeetCode : 5. Longest Palindromic Substring﻿

﻿

: Given a string s, return *the longest palindromic substring* in s.

**: 문자열 s가 주어진다. 문자열 s 안에 가장 긴 팰린드롬 부분 문자열을 반환하라.**



**Example 1:**

```python
Input: s = "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

**Example 2:**

```python
Input: s = "cbbd"
Output: "bb"
```

**Example 3:**

```python
Input: s = "a"
Output: "a"
```

**Example 4:**

```python
Input: s = "ac"
Output: "a"
```

**Constraints:**

1 <= s.length <= 1000

s consist of only digits and English letters.

---



**Submissions Code:**

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        
        for j in range(len(s),-1,-1):
            
            for i in range(len(s)):
                if i+j<=len(s):
                    a = s[i:i+j]
                    if a[:]==a[::-1]:
                        return a
                else:
                    break
```

전체 길이에서 1씩 줄여가며 비교할 크기를 정한다.

그리고 시작값과 비교할 크기를 더했을 때 전제길이보다 작으면 비교를 시작한다.

슬라이싱으로 앞에서부터 크기만크 비교를 하고, 이를 a에 저장한다.

a를 뒤집었을 때 같다면, 팰린드롬이므로 바로 반환한다.

런타임을 줄이기 위해서 비교할 길이를 넘어가면 반복문 하나를 종료한다.



**Other Submissions Code:**

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        
        def expand(left, right):
            while left >= 0 and right<len(s) and s[left]==s[right]:
                left-=1
                right+=1
            return s[left+1 : right]
        
        if len(s)<2 or s[:]==s[::-1]:
            return s
        
        result = ''
        
        for i in range(len(s)-1):
            result = max(result, expand(i,i+1), expand(i,i+2), key=len)
            
        return result
```

expand함수를 정의하여 왼쪽값과 오른쪽 값을 입력받아 팰린드롬인지 확인하면서 점차적으로 확장해간다.

먼저 입력 문자열이 팰린드롬이거나, 입력 문자열의 길이가 1이하일 때는 바로 입력값을 반환한다.

expand(i,i+1), expand(i,i+2)를 통해서 짝수일 경우, 홀수일 경우 모두를 고려한다.

result='' 를 통해 초기화 해준 후, 반복문을 돌면서 길이가 가장 긴 문자열을 result에 저장한다.

최종적으로 result를 반환한다.



**Using Keyword**

range(시작값,끝값-1,-1) - 1씩 줄어듦

key=len - 기준 키값, 길이를 기준으로

﻿