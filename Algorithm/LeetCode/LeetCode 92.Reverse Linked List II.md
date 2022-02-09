> https://leetcode.com/problems/reverse-linked-list-ii/



# LeetCode : 92. Reverse Linked List II﻿

﻿

: Given the head of a singly linked list and two integers left and right where left <= right, reverse the nodes of the list from position left to position right, and return *the reversed list*.

**: 하나의 연결 리스트 head가 주어지고, 두 정수 left와 right가 left <= righ로 주어집니다. left의 위치에서 right의 위치까지의 노드들을 뒤집어라. 그리고 뒤집어진 리스트를 반환하라.**



**Example 1:**

```python
Input: head = [1,2,3,4,5], left = 2, right = 4
Output: [1,4,3,2,5]
```

**Example 2:**

```python
Input: head = [5], left = 1, right = 1
Output: [5]
```



**Constraints:**

The number of nodes in the list is n.

1 <= n <= 500

-500 <= Node.val <= 500

1 <= left <= right <= n

---



**Submissions Code (Accepted):**

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        
        def reverseList(self, head: Optional[ListNode], tail: Optional[ListNode]):
            node, prev = head, tail
            while node:
                next, node.next = node.next, prev
                prev, node = node, next

            return prev
        
        n = 1
        node = head
        while node:
            if n+1 == left:
                start = tmp = node.next
                for _ in range(right - left):
                    tmp = tmp.next
                next = tmp.next
                tmp.next = None
                
                node.next = reverseList(self, start, next)
                return head
            
            elif 1 == left:
                start = tmp = node
                for _ in range(right - left):
                    tmp = tmp.next
                next = tmp.next
                tmp.next = None
                
                return reverseList(self, start, next)
            
            else:
                node = node.next
                n += 1
```

Runtime: 48 ms, faster than 7.21% of Python3 online submissions for Reverse Linked List II.

Memory Usage: 14.6 MB, less than 13.54% of Python3 online submissions for Reverse Linked List II.



먼저 전에 풀었던 전체 연결리스트를 역순으로 하는 reverseList() 함수를 구현했다. 이때, prev를 tail로 선언하므로써 역순으로 정렬된 연결리스트 후에 이어주도록 했다.

그리고 첫번째 요소부터 시작하여 역순으로 정렬되는 부분을 찾는다.

현재 노드의 다음 요소가 정렬되야하는 차례일 때와, 첫 요소부터 정렬되야하는 요소일 경우 두가지가 있다.

이는 정렬하기 전 연결리스트가 존재 하는지, 아닌지 차이이다.

첫 요소부터 정렬해야 한다면, 정렬 시작 요소를 node로 시작하며, 아닐경우 node.next로 시작한다.

이는 node.next로 정렬된 후 연결 리스트를 잇기 위함이다.

tmp를 통해 정렬의 마지막 요소까지 이동하며 tmp.next를 next에 저장하여 정렬 후 이어줄 연결리스트를 저장하고, tmp.next는 None으로 저장하여 start를 만들어 준다.

마지막으로 reverseList(self, start, next)를 통해서 start를 역순으로 정렬하고, next를 이어준다.

앞에 이어줄 요소가 있다면 node.next에 정렬된 연결리스트를 연결하여 반환한다.

하지만, 코드 중복이 많고, 깔끔한 코드라고 하긴 어렵다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        
        def reverseList(self, head: Optional[ListNode], tail: Optional[ListNode]):
            node, prev = head, tail
            while node:
                next, node.next = node.next, prev
                prev, node = node, next

            return prev
        
        root = node = ListNode()
        root.next = head
        
        for _ in range(left - 1):
            node = node.next
        
        start = tmp = node.next
        for _ in range(right - left):
            tmp = tmp.next
        next = tmp.next
        tmp.next = None

        node.next = reverseList(self, start, next)
        return root.next
```

Runtime: 49 ms, faster than 5.85% of Python3 online submissions for Reverse Linked List II.

Memory Usage: 14.3 MB, less than 90.63% of Python3 online submissions for Reverse Linked List II.



첫번째 코드에서 중복된 코드를 수정해보았다. root라는 연결리스트를 생성하여 root.next에 head를 이어주었다.

이렇게 하면, 무조건 앞에 이어줄 연결 리스트가 생성되게 된다. 1번째 요소부터 정렬을 시작하더라도, root를 이어아하기 때문이다.

위치를 탐색하는 while문을 지우고 for문을 사용하여, 바로 정렬될 위치 직전까지 찾아가준다.

시작을 root로 시작하기 때문에 node는 left 위치의 바로 전 값을 기리키므로 start를 node.next로 지정하도록 한다. 위와 똑같은 방법으로 정렬과 뒷 부분을 이어주고, 앞부분은 node.next로 이어준다. 최종적으로 root.next를 반환하면 원하는 결과를 얻을 수 있다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        
        if not head or left == right:
            return head
        
        root = start = ListNode(None)
        root.next = head
        
        for _ in range(left-1):
            start = start.next
        end = start.next
        
        for _ in range(right - left):
            tmp, start.next, end.next = start.next, end.next, end.next.next
            start.next.next = tmp
        return root.next
```

Runtime: 28 ms, faster than 84.37% of Python3 online submissions for Reverse Linked List II.

Memory Usage: 14.4 MB, less than 43.59% of Python3 online submissions for Reverse Linked List II.



이번에는 자체적으로 역순 정렬하는 방법이다.

start와 tmp, end를 사용해서 for문을 횟수로 돌면서 바뀐다.

입력값에 따라 빠르게 처리하기 위에 예외처리를 했다.

위와 똑같이 root 를 사용하여 첫 노드를 허수로 만들어준고 반복문으로 정렬 직전의 노드로 이동한다.

그리고 변경 직전의 노드가 start, 그 다음 노드를 end로 시작한다.

start의 다음 노드를 tmp로 지정하고, end의 다음 노드를 start의 다음으로 만들며, end의 다다음을 end의 다음으로 설정한다.

end의 다음 노드를 start의 바로 다음으로, tmp부터 end 까지는 계속 이어진다. right- left 횟수 만큼 반복하면 원하는 결과를 root에 얻을 수 있으며, 최종적으로 root.next를 반환하면 된다.



**Using Keyword**

```python
class ListNode:
	def __init__(self, val=0, next=None):
		self.val = val
		self.next = next
```



