> https://leetcode.com/problems/array-partition-i/



# LeetCode : 561. Array Partition I﻿

﻿

: Given an integer array nums of 2n integers, group these integers into n pairs (a1, b1), (a2, b2), ..., (an, bn) such that the sum of min(ai, bi) for all i is **maximized**. Return *the maximized sum*.

**: 2n 개의 정수를 가진 배열 nums가 주어질 때, n 개의 페어를 이용한 모든 min(a, b)들의 합 중에서 가장 큰 값을 반환하라.**



**Example 1:**

```python
Input: nums = [1,4,3,2]
Output: 4
Explanation: All possible pairings (ignoring the ordering of elements) are:
1. (1, 4), (2, 3) -> min(1, 4) + min(2, 3) = 1 + 2 = 3
2. (1, 3), (2, 4) -> min(1, 3) + min(2, 4) = 1 + 2 = 3
3. (1, 2), (3, 4) -> min(1, 2) + min(3, 4) = 1 + 3 = 4
So the maximum possible sum is 4.
```

**Example 2:**

```python
Input: nums = [6,2,6,5,1,2]
Output: 9
Explanation: The optimal pairing is (2, 1), (2, 5), (6, 6). min(2, 1) + min(2, 5) + min(6, 6) = 1 + 2 + 6 = 9.
```



**Constraints:**

1 <= n <= 104

nums.length == 2 * n

-104 <= nums[i] <= 104

---



**Submissions Code (Accepted):**

```python
class Solution:
    def arrayPairSum(self, nums: List[int]) -> int:
        nums.sort()
        sum = 0
        for i in range(0,len(nums),2):
            sum+=nums[i]
        return sum
        
```

문제 해결의 아이디어는 min(a, b)의 합들이 최대가 돼야 하므로, a, b 즉 페어는 작은 수는 작은 수끼리, 큰 수는 큰 수끼리 묶여서 페어를 이루어야 한다는 점이다. 작은 수와 큰 수가 페어를 이루면 작은 수가 반환되므로, 합이 최대가 되기 위해서는 큰 수는 큰 수와 묶여야 더하는 값도 커지게 될 것이다.

먼저 nums를 오름차순으로 정렬한다. 그리고 각 합을 저장할 sum 변수를 0으로 초기화한다.

for 문을 돌되 0부터 nums의 길이까지 2의 간격으로 돌게 된다. 현재 배열에서 2개씩 짝을 지었을 경우 결국 min(a, b)에서 반환되는 값은 짝수 차례의 요소뿐이다. min(nums[0]. nums[1])을 해도 정렬했기 때문에 무조건 nums[0]이 반환되므로, nums[0] 다음으로는 nums[2], nums[4] ... 차례로 이어갈 것이다.

이것을 계속 반복하여 모든 페어를 계산하고, 최종적으로 sum을 반환한다.



**Other Submissions Code:**

```python
class Solution:
    def arrayPairSum(self, nums: List[int]) -> int:
        return sum(sorted(nums)[::2])
```

위 내용을 한줄에 정리할 수 있다.



**Using Keyword**

sort(), sorted(list) - 정렬

list[::2] - 짝수 값만 추출

sum() - 합 계산



﻿