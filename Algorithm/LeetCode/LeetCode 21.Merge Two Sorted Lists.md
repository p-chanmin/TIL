> https://leetcode.com/problems/merge-two-sorted-lists/submissions/



# LeetCode : 21. Merge Two Sorted Lists﻿

﻿

: Merge two sorted linked lists and return it as a **sorted** list. The list should be made by splicing together the nodes of the first two lists.

**: 정렬된 두 연결 리스트를 합병하고 그것을 정렬된 리스트로 반환하라. 리스트는 처음의 두 리스트를 함께 연결시켜야 합니다.**



**Example 1:**

```python
Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

**Example 2:**

```python
Input: l1 = [], l2 = []
Output: []
```

**Example 2:**

```python
Input: l1 = [], l2 = [0]
Output: [0]
```



**Constraints:**

The number of nodes in both lists is in the range [0, 50].

-100 <= Node.val <= 100

Both l1 and l2 are sorted in **non-decreasing** order.

---



**Submissions Code (Accepted):**

```python
class Solution:
    def mergeTwoLists(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        result= ListNode()
        tmp = result
        while l1 and l2:

            if l1.val >= l2.val:
                tmp.next = l2
                l2 = l2.next
            else:
                tmp.next = l1
                l1 = l1.next
            tmp = tmp.next
        
        if l1:
            tmp.next = l1
        elif l2:
            tmp.next = l2
        
        return result.next
```

Runtime: 36 ms, faster than 75.25% of Python3 online submissions for Merge Two Sorted Lists.

Memory Usage: 14.3 MB, less than 62.25% of Python3 online submissions for Merge Two Sorted Lists.



새로운 연결 리스트를 생성하여, l1, l2 중 둘 중 하나라도 비었을 때까지 반복문을 반복한다.

값이 작은 쪽을 tmp.next에 삽입하고 연결리스트를 이동한 후, tmp를 이동한다.

둘 중 하나라도 비었을 경우 l1과 l2 중 나머지 값들을 tmp의 마지막에 추가한다.

최종적으로 result.next를 반환한다. 왜냐하면 처음부터 값을 tmp.next에 넣었기 때문에 result의 처음의 val은 0이므로 result.next를 반환해야 한다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def mergeTwoLists(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        if (not l1) or (l2 and l1.val > l2.val):
            l1, l2 = l2, l1
        if l1:
            l1.next = self.mergeTwoLists(l1.next, l2)
        return l1
```

Runtime: 32 ms, faster than 91.54% of Python3 online submissions for Merge Two Sorted Lists.

Memory Usage: 14.4 MB, less than 31.98% of Python3 online submissions for Merge Two Sorted Lists.



재귀 구조를 활용한 코드로 l1을 유용하게 사용한 코드이다.

l1이 존재하지 않거나, l2가 있고, l2의 값이 더 작을경우 작은 쪽을 l1으로 변경해주는 if문이 처음에 등장한다.

그 후 l1이 존재한다면, l1의 next는 다시 재귀호출로 mergeTwoLists(l1.next, l2)로 이어준다.

즉, l1과 l2를 비교해 제일 작은 값을 l1의 맨 앞에 두고, l1.next와 l2를 다시 비교하여 다음으로 작은 값을 이어준다. 이렇게 되면 재귀 호출을 거듭하면서, l1에는 최종적으로 정렬된 연결리스트가 생성된다.



**Using Keyword**

```python
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
```

재귀호출

