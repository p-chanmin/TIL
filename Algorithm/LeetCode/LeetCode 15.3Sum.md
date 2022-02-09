> https://leetcode.com/problems/3sum/



# LeetCode : 15. 3Sum﻿

﻿

: Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

**: 정수 배열이 주어지면, 합으로 0을 만들 수 있는 3개의 요소를 반환하라. 중복된 요소는 포함되지 않는다.**



**Example 1:**

```python
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
```

**Example 2:**

```python
Input: nums = []
Output: []
```

**Example 3:**

```python
Input: nums = [0]
Output: []
```

**Constraints:**

0 <= nums.length <= 3000

-105 <= nums[i] <= 105

---



**Submissions Code (wrong):**

```python
class Solution:
    def threeSum(self, nums: list[int]):
        result = []

        if len(nums) < 3:
            return result

        nums.sort()
        l, r = 0, len(nums)-1
        if (nums[l]>0 and nums[r]>0) or (nums[l]<0 and nums[r]<0):
            return result
        
        while nums[l]<=0:
            if -(nums[l]+nums[r]) in nums[l+1:r]:
                if [nums[l],-(nums[l]+nums[r]), nums[r]] not in result:
                    result.append([nums[l],-(nums[l]+nums[r]), nums[r]])
            if nums[r]>0:
                r-=1
            elif l==r:
                break
            else:
                l+=1
                r=len(nums)-1
        return result
```

투포인터를 사용해보았지만, 최적화가 되지 않고, 시간초과를 면할 수 없었다.



**Other Submissions Code (wrong):**

```python
class Solution:
    def threeSum(self, nums: list[int]):
        result=[]
        nums.sort()
        
        for i in range(len(nums)-2):
            
            if i > 0 and nums[i]==nums[i-1]:
                continue
            for j in range(i+1, len(nums)-1):
                if j > i+1 and nums[j]==nums[j-1]:
                    continue
                for k in range(j+1, len(nums)):
                    if k < j+1 and nums[k]==nums[k-1]:
                        continue
                    if nums[i]+nums[j]+nums[k]==0 and [nums[i],nums[j],nums[k]] not in  result:
                        result.append([nums[i],nums[j],nums[k]])
                        
        return result
```

역시 세개의 포인터를 사용하여 접근해도 시간초과로 풀지 못 한다.



**Other Submissions Code (Accepted):**

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result=[]
        nums.sort()
        
        for i in range(len(nums)-2):
            
            if i>0 and nums[i]==nums[i-1]:
                continue
            
            l,r = i+1, len(nums)-1
            while l<r:
                if nums[i]+nums[l]+nums[r]<0:
                    l+=1
                elif nums[i]+nums[l]+nums[r]>0:
                    r-=1
                else:
                    result.append([nums[i],nums[l],nums[r]])
                    while l<r and nums[l]==nums[l+1]:
                        l+=1
                    while l<r and nums[r]==nums[r-1]:
                        r-=1
                    l+=1
                    r-=1
        return result
                    
```

처음 시도했던 투포인터와 달리 첫번째 요소에서 반복문을 돌면서 두번째 세번째 요소들을 투포인터로 찾는다.

그리고 첫번째 요소의 반복문은 다음으로 넘어가면서 전 요소와 같다면 continue를 사용하여 건너뛰면서 최적화 시켜주고, 두번째, 세번째 요소는 투포인터로 0인 경우 추가되고, 그 때 탐색할 다음 요소가 같은 요소라면, 포인터 위치를 옮기면서 계산을 생략하며 최적화 한다.

최종적으로 result 값을 반환하면, 시간초과 없이 문제가 해결된다.



**Using Keyword**

투포인터, 최적화



﻿