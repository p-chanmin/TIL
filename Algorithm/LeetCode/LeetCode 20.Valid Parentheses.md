> https://leetcode.com/problems/valid-parentheses/



# ﻿LeetCode : 20. Valid Parentheses﻿

﻿

: Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

\1. Open brackets must be closed by the same type of brackets.

\2. Open brackets must be closed in the correct order.

**: '(', ')', '{', '}', '[', ']'만을 포함한 문자열 s가 주어진다. 입력 문자열이 유요한지 확인하라.**

**입력문자열은 다음 경우에 유효하다.**

**1. 열린 괄호는 동일한 유형의 괄호로 닫아야 한다.**

**열린 괄호는 올바른 순서로 닫아야 한다.**



**Example 1:**

```python
Input: s = "()"
Output: true
```

**Example 2:**

```python
Input: s = "()[]{}"
Output: true
```

**Example 3:**

```python
Input: s = "(]"
Output: false
```

**Example 4:**

```python
Input: s = "([)]"
Output: false
```

**Example 5:**

```python
Input: s = "{[]}"
Output: true
```

**Constraints:**

1 <= s.length <= 104

s consists of parentheses only '()[]{}'.

---



**Submissions Code (Accepted):**

```python
class Solution:
    def isValid(self, s: str) -> bool:
        
        stack = []
        
        for i in s:
            
            if i == '(' or i == '{' or i == '[':
                stack.append(i)
                
            elif len(stack) != 0:
                a = stack.pop()
                if a == '(' and i != ')':
                    return False
                elif a == '{' and i != '}':
                    return False
                elif a == '[' and i != ']':
                    return False
                
            else:
                return False
                        
        if len(stack) == 0:
            return True
        else:
            return False
        
            
```

Runtime: 49 ms, faster than 7.81% of Python3 online submissions for Valid Parentheses.

Memory Usage: 14.1 MB, less than 87.03% of Python3 online submissions for Valid Parentheses.



먼저 스택을 생성한다. 그리고 문자열을 돌면서 열린괄호가 들어왔을 경우 스택에 삽입한다.

닫힌 괄호가 들어왔을 경우 스택이 비어있으면, 바로 False를 반환하고, 스택에 요소가 있다면 pop하여 a에 저장한다. 이때 a와 i가 일치하지 않는 괄호일 경우 바로 False를 반환한다.

문자열을 모두 돌았다면, 마지막으로 스택에 남아있는 요소가 있는지 검사한다.

이때, 스택에 남아있는 요소가 없다면 최종적으로 True를 반환하고, 아니라면 False를 반환한다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def isValid(self, s: str) -> bool:
        
        stack = []
        table = {
            ')': '(',
            '}': '{',
            ']': '['
        }
        
        for i in s:
            if i not in table:
                stack.append(i)
            elif not stack or table[i] != stack.pop():
                return False
        
        return len(stack) == 0
```

Runtime: 32 ms, faster than 62.49% of Python3 online submissions for Valid Parentheses.

Memory Usage: 14 MB, less than 99.67% of Python3 online submissions for Valid Parentheses.



딕셔너리를 통해 코드 중복을 줄이고, 더 간단하게 만들 수 있다.

table라는 딕셔너리는 닫힌괄호를 key로 하고, 열린괄호를 value로 하도록 한다.

문자열을 돌면서 문자가 table 안에 없다면, 열린괄호 이므로 스택에 추가한다.

문자열이 닫힌 괄호라면, 스택이 비어있는지 확인하고, key와 value가 일치한지 확인한다.

스택이 비어있거나, 일치하지 않으면 바로 False를 반환한다.

문자열을 다 돌았다면 스택이 비어있는지 여부를 바로 반환한다.



**Using Keyword**

stack.pop() - 리스트의 마지막 요소를 반환, 리스트에서는 값 삭제

﻿