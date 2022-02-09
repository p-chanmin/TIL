> https://leetcode.com/problems/palindrome-linked-list/submissions/



# LeetCode : 234. Palindrome Linked List﻿

﻿

: Given the head of a singly linked list, return true if it is a palindrome.

**: 연결리스트 헤드가 주어졌을 때, 팰린드롬이라면 true를 반환하라.**



**Example 1:**

```python
Input: head = [1,2,2,1]
Output: true
```

**Example 2:**

```python
Input: head = [1,2]
Output: false
```



**Constraints:**

The number of nodes in the list is in the range [1, 105].

0 <= Node.val <= 9

---



**Submissions Code (Accepted):**

```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        data = []
        temp = head
        while temp != None:
            data.append(temp.val)
            temp = temp.next
        if data == data[::-1]:
            return True
        else:
            return False
```

순서대로 데이터를 담을 리스트를 생성하고, 연결 리스트를 탐색할 temp에 head를 부여한다.

그리고 temp가 None이 될 때까지 반복문을 돌면서, 현재 위치의 값을 리스트에 추가하고, 다음 노드로 넘어간다.

연결 리스트의 모든 값이 리스트에 저장되었다면 슬라이싱을 통해, 리스트와 역순의 리스트를 비교하여

팰린드롬 여부를 반환한다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        rev = None
        slow = fast = head
        
        while fast and fast.next:
            fast = fast.next.next
            rev, rev.next, slow = slow, rev, slow.next
        if fast:
            slow = slow.next
            
        while rev and rev.val == slow.val:
            slow, rev = slow.next, rev.next
            
        return not rev
```

rev라는 연결 리스트를 None으로 생성하고 slow와 fast포인트를 만든다.

fast 포인트는 한 번에 두 칸씩 이동하며, slow 포인터는 한 번에 한 칸씩 이동하면서 역순으로 rev에 값을 저장한다. fast 포인트가 마지막에 도착했을 때, slow 포인터는 중간에 도착하게 된다. 이 때 연결 리스트의 개수가 홀수개라면 fast가 None이 아니게 되고 가장 가운데 있는 값이 1개로 무시해야하기 때문에, fast가 있다면 slow 포인터를 한 칸 이동한다.

그 후 현재 위치의 slow 포인터와 rev 포인터의 값들이 일치하면 팰린드롬이고, 그렇지 않으면 팰린드롬이 아니다.

따라서 최종적으로 rev 에 값이 없다면 True, 있다면 False가 된다.



**Using Keyword**

list[::-1] - 리스트 뒤집기

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
```