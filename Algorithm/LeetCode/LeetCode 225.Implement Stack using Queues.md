> https://leetcode.com/problems/implement-stack-using-queues/



# LeetCode : 225. Implement Stack using Queues﻿

﻿

: Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (push, top, pop, and empty).

Implement the MyStack class:

void push(int x) Pushes element x to the top of the stack.

int pop() Removes the element on the top of the stack and returns it.

int top() Returns the element on the top of the stack.

boolean empty() Returns true if the stack is empty, false otherwise.

**: 두 개의 큐를 사용하여 스택을 구현하라. 구현된 스택은 일반 스택의 모든 기능을 지원해야 한다.**

**push(x) : 요소 x를 스택에 삽입한다.**

**pop() : 스택의 첫 번째 요소를 삭제한다**

**top() : 스택의 첫 번째 요소를 가져온다.**

**empty() : 스택이 비어있는지 여부를 반환한다.**



**Example 1:**

```python
Input
["MyStack", "push", "push", "top", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 2, 2, false]

Explanation
MyStack myStack = new MyStack();
myStack.push(1);
myStack.push(2);
myStack.top(); // return 2
myStack.pop(); // return 2
myStack.empty(); // return False
```



**Constraints:**

1 <= x <= 9

At most 100 calls will be made to push, pop, top, and empty.

All the calls to pop and top are valid.

---



**Submissions Code (Accepted):**

```python
class MyStack:

    def __init__(self):
        self.a = collections.deque()
        

    def push(self, x: int) -> None:
        self.a.appendleft(x)
        

    def pop(self) -> int:
        return self.a.popleft()
        

    def top(self) -> int:
        return self.a[0]
        

    def empty(self) -> bool:
        return len(self.a) == 0
```

Runtime: 34 ms, faster than 14.94% of Python3 online submissions for Implement Stack using Queues.

Memory Usage: 14.4 MB, less than 44.22% of Python3 online submissions for Implement Stack using Queues.



큐를 사용해서 스택을 구현하는 문제이다.

왼쪽으로 값이 들어가고, 왼쪽으로 값이 나간다. 이때 스택에서 제일 먼저 나가야 하는 값은 0번째 요소이므로

top()에서도 0번째 요소를 리턴한다.

