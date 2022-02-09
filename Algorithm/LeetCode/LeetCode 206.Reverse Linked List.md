> https://leetcode.com/problems/reverse-linked-list/



# LeetCode : 206. Reverse Linked List﻿

﻿

: Given the head of a singly linked list, reverse the list, and return *the reversed list*.

**: 하나의 연결 리스트의 헤드가 주어졌을 때, 리스트를 뒤집어라. 그리고 뒤집힌 리스트를 반환하라.**



**Example 1:**

```python
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

**Example 2:**

```python
Input: head = [1,2]
Output: [2,1]
```

**Example 2:**

```python
Input: head = []
Output: []
```



**Constraints:**

The number of nodes in the list is the range [0, 5000].

-5000 <= Node.val <= 5000

---



**Submissions Code (Accepted):**

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        reverse = None
        
        if head:
            reverse = ListNode(head.val)
            head = head.next
            
        while head:
            node = ListNode()
            node.val = head.val
            node.next = reverse
            reverse = node
            head = head.next
            
        return reverse
```

Runtime: 32 ms, faster than 87.10% of Python3 online submissions for Reverse Linked List.

Memory Usage: 16.4 MB, less than 23.29% of Python3 online submissions for Reverse Linked List.



먼저 head가 주어지지 않았을 경우를 위해 reverse를 None으로 선언한다.

head가 있다면, reverse에 head의 첫번째 값을 가지는 새로운 리스트 노드를 생성한다. 그리고 head를 이동한다.

그 후 head가 비어있을 때까지 반복하며 나머지 값들을 이동시킨다.

새로운 리스트 노드를 생성하고, 그 노드에 현재 head의 값을 저장, 노드의 다음을 reverse를 가리키면 reverse의 첫번째가 가리키게 되고, 그 노드를 다시 reverse로 한다.

최종적으로 reverse를 반환하면, 역순으로 된 연결 리스트가 반환된다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        def reverse(node: ListNode, prev: ListNode = None):
            if not node:
                return prev
            next, node.next = node.next, prev
            return reverse(next, node)
        
        return reverse(head)
```

Runtime: 36 ms, faster than 65.43% of Python3 online submissions for Reverse Linked List.

Memory Usage: 20.3 MB, less than 5.07% of Python3 online submissions for Reverse Linked List.



재귀 구조로 reverse() 함수를 생성하여 첫번째 노드를 prev에 연결하고, 나머지 노드를 next로 넘겨서 이를 반복하는 형식이다. prev의 디폴트 값을 None을 설정하여 첫번째 값 다음이 None으로 이어지도록 하고, next가 None 값일 경우 prev를 바로 반환하게 된다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        node, prev = head, None
        
        while node:
            next, node.next = node.next, prev
            prev, node = node, next
        
        return prev
```

Runtime: 32 ms, faster than 87.10% of Python3 online submissions for Reverse Linked List.

Memory Usage: 15.5 MB, less than 77.00% of Python3 online submissions for Reverse Linked List.



처음부터 node와 prev를 사용하여 별도의 연결리스트를 만들지 않고 반복하느 과정이다.

node를 head로, prev를 None으로 초기화 하고 시작한다.

node가 없어질 때까지 next에 node의 첫번째 요소를 제외한 node.next를 저장하고, 동시에 node.next를 prev로 지정한다. 이렇게 되면 첫번째 요소일 경우 초기화 됐던 None이 입력된다.

그 후 prev를 node로, node에 next를 저장하면 새로운 노드에는 나머지 요소들이 있고, prev에는 역순이 취해진 연결 리스트들이 존재한다.

최종적으로 node가 비어있게 되면 반복문이 종료되고, prev를 반환하면 역순된 연결 리스트가 반환된다.



**Using Keyword**

```python
class ListNode:
	def __init__(self, val=0, next=None):
		self.val = val
		self.next = next
```

호출

다중할당

﻿