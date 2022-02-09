> https://leetcode.com/problems/swap-nodes-in-pairs/



# LeetCode : 24. Swap Nodes in Pairs﻿

﻿

: Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

**: 연결 리스트가 주어질 때, 인접한 두 노드를 스왑하고, 이것의 헤드를 반환하라. 연결리스트의 노드의 값을 수정하지 않고, 문제를 해결해야 한다.(즉, 노드 자체만 변경 되도록 함)**



**Example 1:**

```python
Input: head = [1,2,3,4]
Output: [2,1,4,3]
```

**Example 2:**

```python
Input: head = []
Output: []
```

**Example 3:**

```python
Input: head = [1]
Output: [1]
```



**Constraints:**

The number of nodes in the list is in the range [0, 100].

0 <= Node.val <= 100

---



**Submissions Code (Accepted):**

```python
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        prev = tmp = ListNode()

        while head:
            next = head.next
            if next:
                head.next, next.next = next.next, head
                tmp.next = next
                tmp = tmp.next.next
                head = head.next
            else:
                tmp.next = head
                head = head.next
                
        return prev.next
```

Runtime: 28 ms, faster than 85.62% of Python3 online submissions for Swap Nodes in Pairs.

Memory Usage: 14.3 MB, less than 48.49% of Python3 online submissions for Swap Nodes in Pairs.



먼저 스왑한 노드들을 차례대로 저장할 연결 리스트 prev와 마지막을 노드를 나타내는 tmp를 생성합니다.

그리고 head를 탐색하는데, next를 헤드의 다음노드로 하고, 이때 next가 존재하면 스왑이 가능하다는 의미로

head.next, next.next = next.next, head 를 통해 스왑합니다.

그 후 tmp의 다음에 값을 연결하고, tmp를 두번 이동시켜 마지막 노드로 이동합니다.

그리고 한칸 이동 시켜, 다음 스왑할 값을 찾습니다.

next가 존재하지 않는다면, 연결리스트의 노드가 홀수라는 의미로, 스왑하지 않고 값을 prev에 집어 넣어줍니다.

그리고 head를 이동시켜 반복문이 종료 됩니다.

prev의 첫번째 값은 0으로 초기화 된 값이기 때문에, 최종적으로 prev.next를 반환합니다



**Other Submissions Code (Accepted):**

```python
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        tmp = head
        
        while tmp and tmp.next:
            tmp.val, tmp.next.val = tmp.next.val, tmp.val
            tmp = tmp.next.next
            
        return head
```

Runtime: 28 ms, faster than 85.62% of Python3 online submissions for Swap Nodes in Pairs.

Memory Usage: 14 MB, less than 92.50% of Python3 online submissions for Swap Nodes in Pairs.



직관적으로 값만 교환하는 코드. 문제를 해결할 수 있지만, 문제에서 단순히 값만 교환하지 말라고 명시하기 때문에 이 풀이는 정답이라고 할 수는 없을 것 같다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        root = prev = ListNode(None)
        prev.next = head
        
        while head and head.next:
            
            b = head.next
            head.next = b.next
            b.next = head
            
            prev.next = b
            
            head = head.next
            prev = prev.next.next
        
        return root.next
```

Runtime: 28 ms, faster than 85.62% of Python3 online submissions for Swap Nodes in Pairs.

Memory Usage: 14.3 MB, less than 48.49% of Python3 online submissions for Swap Nodes in Pairs.



첫 번째 풀이와 비슷한 구조이지만, if문을 사용하지 않고, 조금 더 깔끔하게 정리할 수 있다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        if head and head.next:
            p = head.next
            
            head.next = self.swapPairs(p.next)
            p.next = head
            return p
        
        return head
```

Runtime: 20 ms, faster than 99.17% of Python3 online submissions for Swap Nodes in Pairs.

Memory Usage: 14.3 MB, less than 48.49% of Python3 online submissions for Swap Nodes in Pairs.



재귀 구조를 사용하여 풀이 할 수도 있다. 앞서 반복 구조에서는 중간 값들을 스왑하면서 이전 값들의 연결이 어려워 새로운 노드를 생성하여 이어주는 풀이였다면, 이 재귀 방법은 이들을 계속 재귀하면서 연결한다.



**Using Keyword**

```python
class ListNode:
	def __init__(self, val=0, next=None):
		self.val = val
		self.next = next
```



