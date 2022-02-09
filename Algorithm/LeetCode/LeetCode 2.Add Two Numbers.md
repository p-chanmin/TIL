> https://leetcode.com/problems/add-two-numbers/



# ﻿LeetCode : 2. Add Two Numbers﻿

﻿

: You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**: 음이 아닌 정수를 가지는 두개의 비어있지 않은 연결 리스트가 주어진다. 숫자는 역순으로 저장되어 있으며, 각각의 노드는 한자리 수가 포함된다. 두 숫자를 추가하고, 연결리스트의 합을 반환하라.**

**숫자 0을 제외하고, 숫자의 맨 처음에 0이 오지 않는다고 가정한다.**



**Example 1:**

```python
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```

**Example 2:**

```python
Input: l1 = [0], l2 = [0]
Output: [0]
```

**Example 3:**

```python
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```



**Constraints:**

The number of nodes in each linked list is in the range [1, 100].

0 <= Node.val <= 9

It is guaranteed that the list represents a number that does not have leading zeros.

---



**Submissions Code (Accpeted):**

```python
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        num_l1, num_l2 = "", ""
        
        while l1:
            num_l1 = str(l1.val)+num_l1
            l1 = l1.next
        while l2:
            num_l2 = str(l2.val)+num_l2
            l2 = l2.next
            
        num = int(num_l1)+int(num_l2)
        
        result = None
        
        for a in str(num):
            node = ListNode(int(a))
            node.next = result
            result = node
        
        return result
```

Runtime: 68 ms, faster than 74.71% of Python3 online submissions for Add Two Numbers.

Memory Usage: 14.2 MB, less than 90.73% of Python3 online submissions for Add Two Numbers.



자료형을 변형해서 해결한 풀이이다.

먼저 공백으로 num_l1, num_l2를 생성하고, 각각 연결 리스트를 돌면서 정수값으로 숫자를 저장합니다.

정수형으로 변환하면서 두개의 합을 num에 저장한다.

result를 None으로 생성해 놓고, num을 문자열로 변경하여 한자리씩 연결리스트에 추가한다.

반복문 안에서 node를 생성하고, node의 값을 다시 정수형으로 넣어준다. 그 후에 노드를 result로, result를 node로 지정해주면, 연결리스트에 역순으로 저장이 된다.

최종적으로 result를 반환한다.



**Other Submissions Code (Accpeted):**

```python
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        root = head = ListNode(0)
        
        carry = 0
        
        while l1 or l2 or carry:
            sum = 0
            
            if l1:
                sum += l1.val
                l1 = l1.next
            if l2:
                sum += l2.val
                l2 = l2.next
            
            carry, val = divmod(sum + carry, 10)
            head.next = ListNode(val)
            head = head.next
        
        return root.next
```

Runtime: 68 ms, faster than 74.71% of Python3 online submissions for Add Two Numbers.

Memory Usage: 14 MB, less than 98.13% of Python3 online submissions for Add Two Numbers.



맨 처음, root와 head으로 노드로 생성한다.

그리고 올림수를 나타내는 carry를 0으로 초기화한다.

l1, l2, carry 중 하나라도 존재한다면 반복문을 계속 돌게 하여, 반복문을 시작한다.

sum을 0으로 초기화 하고, l1이 있을 때 l1의 값을 sum에 더하고, l2가 있을 때 l2의 값을 sum에 더하고,

l1, l2의 위치를 다음 위치로 이동시킨다.

divmod(sum+carry, 10)을 통해서 자리수의 합과, 올림수 carry를 합한 값을 10으로 나누면, (올림수, 자리수)가

반환되며, 이 때 자리수를 노드로 head.next에 추가하고 헤드의 위치를 옮긴다.

최종적으로 root를 반환하면 역순으로 정렬된 합이 반환된다.



**Using Keyword**

divmod(값, 나눌 수) - 몫과 나머지를 한번에 반환하는 함수





﻿