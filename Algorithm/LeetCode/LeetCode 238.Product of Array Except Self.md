> https://leetcode.com/problems/product-of-array-except-self/



# LeetCode : 238. Product of Array Except Self﻿

﻿

: Given an integer array nums, return *an array* answer *such that* answer[i] *is equal to the product of all the elements of* nums *except* nums[i].

The product of any prefix or suffix of nums is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

**: 정수 배열 nums가 주어질 때, answer[i]가 nums[i]를 제외한 모든 요소의 곱과 같도록 하는 answer을 반환하라. 숫자의 곱들은 32비트 정수에 맞도록 보장한다. 나눗셈을 하지 않고 O(n)의 복잡도에 풀이 하라.**



**Example 1:**

```python
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```

**Example 2:**

```python
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```



**Constraints:**

2 <= nums.length <= 105

-30 <= nums[i] <= 30

The product of any prefix or suffix of nums is **guaranteed** to fit in a **32-bit** integer.

---



**Submissions Code (Accepted):**

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        answer = []
        l = [1]
        r = [1]
        for i in range(len(nums)-1):
            l.append(l[-1]*nums[i])
            r.append(r[-1]*nums[len(nums)-1-i])
        r = r[::-1]
        for i in range(len(l)):
            answer.append(l[i]*r[i])
        return answer
```

1을 시작으로 0번째 요소부터 마지막 하나 전 요소까지의 순차적인 곱을 l 배열에 추가하고,

1을 시작으로 마지막 요소부터 1번째 요소까지의 순차적인 곱을 r 배열에 추가한다.

그리고 r 배열을 뒤집어준다. 그러면 각 요소끼리 더하면 해당 순번째의 요소를 제외한 곱들이 된다.

이들은 answer배열에 저장하고 최종적으로 answer을 반환한다.



**Other Submissions Code:**

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        out = []
        
        p = 1
        for i in range(0, len(nums)):
            out.append(p)
            p = p*nums[i]
            
        p=1
        for i in range(len(nums)-1, 0 - 1, -1):
            out[i] = out[i]*p
            p = p*nums[i]
            
        return out
```

위 코드는 처음부터 한 배열에 저장해서 왼쪽부터 시작하여 곱한 값들을 저장하고, 오른쪽부터 시간하여 곱한 값들을 기존 요소에 곱하면서 종료된다. 그리고 마지막으로 out을 반환한다.



**Using Keyword**

list[::-1] - 리스트 뒤집기

idea



﻿