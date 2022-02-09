> https://leetcode.com/problems/odd-even-linked-list/



# LeetCode : 328. Odd Even Linked List﻿

﻿

: Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return *the reordered list*.

The **first** node is considered **odd**, and the **second** node is **even**, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in O(1) extra space complexity and O(n) time complexity.

**: 하나의 연결 리스트의 헤드가 주어진다. 홀수 인덱스를 가진 모든 노드를 그룹화한 후, 짝수 인덱스를 가진 노드를 이어 재정렬된 연결 리스트를 반환하라.**

**첫 번째 노드는 홀수로, 두 번째 노드는 짝수로 간주한다.**

**짝수와 홀수의 그룹 내부의 순서는 입력값과 동일하게 유지해야 한다.**

**O(1)의 공간복잡도와 O(n)의 시간복잡도로 문제를 해결해야 한다.**



**Example 1:**

```python
Input: head = [1,2,3,4,5]
Output: [1,3,5,2,4]
```

**Example 2:**

```python
Input: head = [2,1,3,5,6,4,7]
Output: [2,3,6,7,1,5,4]
```



**Constraints:**

n == number of nodes in the linked list

0 <= n <= 104

-106 <= Node.val <= 106

---



**Submissions Code (Accepted):**

```python
class Solution:
    def oddEvenList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        odd_root = odd = ListNode()
        even_root = even = ListNode()
        num = 1
        while head:
            if num % 2 == 1:
                odd.next = ListNode(head.val)
                odd = odd.next
                head = head.next
            else:
                even.next = ListNode(head.val)
                even = even.next
                head = head.next
            num += 1

        odd.next = even_root.next
        return odd_root.next
```

Runtime: 68 ms, faster than 5.26% of Python3 online submissions for Odd Even Linked List.

Memory Usage: 17.4 MB, less than 5.30% of Python3 online submissions for Odd Even Linked List.



직관적으로 해결해 본 코드로는 홀수, 짝수 노드를 생성하여 헤드를 탐색하며, num을 통해 홀수 번째와 짝수번째를 구분하여, 분류하며 각각의 노드로 이어주고, 마지막에 홀수 노드와 짝수 노드를 연결한 후, 홀수의 첫번째 노드를 반환하는 방법이다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def oddEvenList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        if head is None:
            return None
        
        odd = head
        even = even_head = head.next
        
        while even and even.next:
            odd.next, even.next = odd.next.next, even.next.next
            odd, even = odd.next, even.next
            
        odd.next = even_head
        return head
```

Runtime: 36 ms, faster than 94.44% of Python3 online submissions for Odd Even Linked List.

Memory Usage: 16.4 MB, less than 55.50% of Python3 online submissions for Odd Even Linked List.



따로 홀수와 짝수를 저장하는 노드를 새로 생성하지 않고, head를 그대로 사용한다.

먼저 헤드가 비어있을 경우 예외적으로 None을 반환한다.

odd = head, even = even_head = head.next로 선언한 후 even과 even.next가 있을 경우 반복문을 반복한다.

odd.next = odd.next.next를 통해서 홀수번째 노드가 다다음 노드를 가리키도록 한다. even.next역시 마찬가지이다. 그 후 odd를 한 칸 이동시킨다.

이렇게 반복문이 종료 될 때까지 반복하면 odd는 홀수 노드의 끝을 가리키며, even은 짝수 노드의 끝을 가리킨다.

그러므로 odd.next = even_head로 홀수의 마지막과 짝수의 처음을 연결한다.

최종적으로 head를 반환하면 정렬된 연결 리스트가 반환된다.



**Using Keyword**

```python
class ListNode:
	def __init__(self, val=0, next=None):
		self.val = val
		self.next = next
```







﻿