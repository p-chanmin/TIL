> https://leetcode.com/problems/two-sum/



# LeetCode : 1. Two Sum﻿



: Given an array of integers nums and an integer target, return *indices of the two numbers such that they add up to* *target*.

You may assume that each input would have ***exactly*** **one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

**: 정수 배열 nums와 정수 target이 주어진다. 두 수를 더해서 target이 되는 인덱스 번호를 반환하라.**

**각 입력값에 하나의 명확한 솔루션이 있고, 하나의 요소를 두 번 사용할 수 없다.**

**답은 어떤 순서로든 반환해도 무관하다.**



**Example 1:**

```python
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```python
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```python
Input: nums = [3,3], target = 6
Output: [0,1]
```



**Constraints:**

2 <= nums.length <= 104

-109 <= nums[i] <= 109

-109 <= target <= 109

**Only one valid answer exists.**

---



**Submissions Code:**

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                if nums[i]+nums[j]==target:
                    return [i,j]
```

시작값 부터 반복 시작하고, 그 안에 시작값 + 1부터 반복을 시작하도록 한다.

그러면 i, j가 각 배열에서 두 수를 고르는 모든 경우의 수를 검색하므로, 이때 nums[i]와 nums[j]가 target과 같으면, 바로 인덱스 넘버인 i, j 를 반환한다.

무차별 대입 방식인 브루트 포스(Brute-Force) 방식이라고 한다.



**Other Submissions Code:**

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i, n in enumerate(nums):
            if target-n in nums[i+1:]:
                return [i, nums[i+1:].index(target-n)+(i+1)]
```

enumerate()를 통해서 i 와 n에 인덱스넘버와 값을 반환한다.

target에서 값을 빼고, 그 뺀 값이 나머지 배열에 존재하는지 확인한다.

존재하면, 첫번째 인덱스와 뺀 값의 인덱스를 반환하는데, 뺀 값의 인덱스는 슬라이싱한 배열에서 인덱스 값을 구해서 빠진 인덱스 값인 (i + 1)을 더해준다.



**Other Submissions Code:**

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_dict={}
        
        for i, n in enumerate(nums):
            nums_dict[n]=i
            
        for i, n in enumerate(nums):
            if target-n in nums_dict and i != nums_dict[target-n]:
                return [i, nums_dict[target-n]]
```

딕셔너리를 사용한 방법이다. 각 값을 딕셔너리에 저장하고, 타겟에서 뺀 값이 딕셔너리에 키값으로 존재하고, 그 값이 현재 인덱스가 아닐 경우 두 인덱스를 반환한다.



**Other Submissions Code:**

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_dict={}
        
        for i, n in enumerate(nums):
            if target-n in nums_dict and i != nums_dict[target-n]:
                return [i, nums_dict[target-n]]
            nums_dict[n]=i
```

위 코드를 한 번에 합칠 수도 있다.



**Using Keyword**

enumerate(list) - 반복문에서 index 값과 value 값을 한 번에 얻을 수 있음.

﻿