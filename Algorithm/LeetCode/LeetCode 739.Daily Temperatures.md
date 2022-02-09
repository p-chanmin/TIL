> https://leetcode.com/problems/daily-temperatures/



# ﻿LeetCode : 739. Daily Temperatures﻿

﻿

: Given an array of integers temperatures represents the daily temperatures, return *an array* answer *such that* answer[i] *is the number of days you have to wait after the* ith *day to get a warmer temperature*. If there is no future day for which this is possible, keep answer[i] == 0 instead.

**: 일일 온도를 나타내는 정수 배열 temperatures가 주어진다. anwer[i]가 이후 따뜻한 온도를 얻기위해 대기해야하는 일 수를 저장한 answer를 반환하라. 가능한 미래의 날짜가 없는 경우 0으로 한다.**



**Example 1:**

```javascript
Input: temperatures = [73,74,75,71,69,72,76,73]
Output: [1,1,4,2,1,1,0,0]
```

**Example 2:**

```javascript
Input: temperatures = [30,40,50,60]
Output: [1,1,1,0]
```

**Example 3:**

```javascript
Input: temperatures = [30,60,90]
Output: [1,1,0]
```



**Constraints:**

1 <= temperatures.length <= 105

30 <= temperatures[i] <= 100

---



**Submissions Code (Accepted):**

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        
        answer = [0] * len(temperatures)
        stack = []
        
        for i in range(len(temperatures)):
            
            while stack and temperatures[i] > temperatures[stack[-1]]:
                a = stack.pop()
                answer[a] = i - a
            
            stack.append(i)
                
        return answer
```

Runtime: 1212 ms, faster than 78.28% of Python3 online submissions for Daily Temperatures.

Memory Usage: 25.5 MB, less than 47.92% of Python3 online submissions for Daily Temperatures.



먼저 0으로 이루어진 temperatures의 길이와 똑같은 answer 배열을 만들어준다.

그리고 빈 스택을 생성한다.

스택이 비어있거나, 스택의 마지막 값이 가리키는 온도가 현재 온도보다 크다면, while문을 건너 뛰고, 스택에 현재차례 인덱스 값이 삽입된다.

스택이 비어있지 않고, 현재 온도가 스택의 마지막 값이 가리키는 온도보다 크다면, while문으로 들어가서 스택의 마지막 요소를 제거하고 현재 인덱스에서 마지막 요소의 인덱스를 빼서 날짜를 구하고, 이를 마지막 요소 번째의 answer에 저장한다. 그리고 위에서부터 현재 온도보다 큰 온도를 만나거나, 스택이 빌 때까지 반복하게 된다.

for 문이 종료되며녀 stack에 남은 값은 미래에 따뜻해지는 온도가 없는 인덱스 번호들이며, 따로 처리해주지 않아도, answer에서 미리 0으로 초기화 되었기에 상관없다.

최종적으로 answer을 반환하면 원하는 결과를 얻을 수 있다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        
        answer = [0] * len(temperatures)
        stack = []
        
        for i, t in enumerate(temperatures):
            
            while stack and t > temperatures[stack[-1]]:
                a = stack.pop()
                answer[a] = i - a
            
            stack.append(i)
                
        return answer
```

Runtime: 1220 ms, faster than 72.45% of Python3 online submissions for Daily Temperatures.

Memory Usage: 25.4 MB, less than 62.36% of Python3 online submissions for Daily Temperatures.



enumerate를 통해서 조금 더 간편하게 볼 수있다.

원리는 위와 같다.



**Using Keyword**

stack



﻿