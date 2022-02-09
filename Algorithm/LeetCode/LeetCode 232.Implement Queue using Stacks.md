> https://leetcode.com/problems/implement-queue-using-stacks/



# LeetCode : 232. Implement Queue using Stacks﻿

﻿

: Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (push, peek, pop, and empty).

**: 두 개의 스택만 사용하여 큐를 구현하라. 구현된 큐는 일반 큐의 모든 기능(push, peek, pop, empty)를 지원해야 한다.**



**Example 1:**

```python
Input
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 1, 1, false]

Explanation
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false
```



**Constraints:**

1 <= x <= 9

At most 100 calls will be made to push, pop, peek, and empty.

All the calls to pop and peek are valid.



**Submissions Code (Accepted):**

```python
class MyQueue:

    def __init__(self):
        self.input = []
        self.output = []
        

    def push(self, x: int) -> None:
        self.input.append(x)
        

    def pop(self) -> int:
        self.peek()
        return self.output.pop()
        

    def peek(self) -> int:
        if not self.output:
            while self.input:
                self.output.append(self.input.pop())
        return self.output[-1]
        

    def empty(self) -> bool:
        return not self.input and not self.output
```

Runtime: 32 ms, faster than 56.20% of Python3 online submissions for Implement Queue using Stacks.

Memory Usage: 14.3 MB, less than 44.31% of Python3 online submissions for Implement Queue using Stacks.



두 개의 스택으로 구현해야 하므로, 큐 클래스의 생성자로 input과 output 스택을 초기화 해주었다.

push에서는 단순히 input 스택에 갑을 append 해준다.

pop을 하기 전에 먼저 peek를 본다. peek는 단순히 마지막 값을 반환하는 기능으로

먼저 출력할 output이 비어있다면 input의 모든 값들을 순서대로 꺼내서 output으로 집어 넣는다.

그러면 제일 앞에 있는 값이 output의 맨 뒤로 가게 된다. 이때, [-1]을 통해서 마지막 값을 반환한다.

다음으로 pop을 보면, pop을 하기 전에 output이 비어있을 경우를 대비해서 peek()을 한번 실행한다.

그 후 output에서 pop()을 하면 처음 값이 반환되게 되며, 스택에서 사라진다.

empty는 단순히 input 과 output이 모두 비어있을 경우에만 True를 반환한다.



**Using Keyword**

stack

queue

﻿