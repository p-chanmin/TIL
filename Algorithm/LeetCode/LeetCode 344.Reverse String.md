> https://leetcode.com/problems/reverse-string/



# LeetCode : 344. Reverse String

﻿

: Write a function that reverses a string. The input string is given as an array of characters s.

**: 문자열을 뒤집는 함수를 작성하라. 입력값은 문자 배열이다.**

: Do not return anything, modify s in-place instead.

**: 리턴 하지말고, 리스트 내부를 수정하라.**



**Example 1:**

```python
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

**Example 2:**

```python
Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

**Constraints:**

1 <= s.length <= 105

s[i] is a printable ascii character.

---



**Submissions Code:**

```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        
        s.reverse()
```

list에서 .reverse()를 사용하면 순서를 뒤집을 수 있다.





**Other Submissions Code:**

```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        l, r = 0, len(s)-1
        while l < r:
            s[l], s[r] = s[r], s[l]
            l+=1
            r-=1
```

왼쪽 시작값을 0, 오른쪽 값을 전체 길이-1을 통해서 동시에 왼쪽값과 오른쪽 값을 스왑한다.

그리고 왼쪽 값을 +1, 오른쪽 값을 -1하며, 왼쪽 값이 오른쪽 값보다 커질 때 까지 반복한다.



**Using Keyword**

list.reverse() - 리스트를 뒤집는다.

문자열 뒤집기

s = s[::-1]

or

s[:] = s[::-1]

﻿