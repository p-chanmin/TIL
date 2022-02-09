> https://leetcode.com/problems/trapping-rain-water/



# ﻿LeetCode : 42. Trapping Rain Water﻿

﻿

: Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

**:** **각 막대의 폭이 1인 지도를 나타내는 음이 아닌 정수 n이 주어졌을 때**

**비가 내린 후 가둘 수 있는 물의 양을 계산하라.**



**Example 1:**

![img](https://blogfiles.pstatic.net/MjAyMTA4MDNfMTM5/MDAxNjI3OTY4ODA0NDgz.QPLNR4blf1TCAYzy5ZsQpU0uidDnS0e9smSsSw8E550g.alLhUb3QTdIAMELkbNFqCPhFvtwggKQwQTDLB-0-3gYg.PNG.pc_m111/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2021-08-03_%EC%98%A4%ED%9B%84_2.33.05.png?type=w1)

```python
Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented
by array [0,1,0,2,1,0,1,3,2,1,2,1].
In this case, 6 units of rain water (blue section) are being trapped.
```

**Example 2:**

```python
Input: height = [4,2,0,3,2,5]
Output: 9
```



**Constraints:**

n == height.length

0 <= n <= 3 * 104

0 <= height[i] <= 105

---



**Submissions Code:**

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        if not height:
            return 0
        
        result = 0
        for h in range(1,max(height)+1):
            left, right = 0, len(height)-1

            while not left==right:
                if height[left]<h:
                    left+=1
                elif height[right]<h:
                    right-=1
                else:
                    break

            for i in range(h):
                result+=height[left:right+1].count(i)

        return result
```

첫 제출로 투 포인터를 사용하여 높이별로 계산하도록 하였다. 이렇게 코딩했을 경우 높이가 낮은 값들은 계산이 가능하나, 주어진 높이가 커질수록 소요되는 시간이 더 길어진다. 결국 시간초과를 내버렸다.



**Other Submissions Code:**

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        
        result = 0
        
        if not height:
            return result
    
        left, right = 0, len(height)-1
        left_max , right_max = height[left], height[right]
        
        while left < right:
            left_max = max(left_max, height[left])
            right_max = max(right_max, height[right])
            
            if left_max <= right_max:
                result += left_max - height[left]
                left+=1
            else:
                result += right_max - height[right]
                right-=1
                
        return result
```

높이 별로 분류하지 않고, 투 포인터를 사용하여 최고 높이에서 현재 높이를 빼는 방식이다.

먼저 height가 비어있을 경우, 바로 0을 리턴한다.

그리고 투 포인터를 사용하여 점점 height의 최고값으로 이동한다.

현재 height[left]와 height[right]의 값과 left_max, right_max를 비교하여 각각 큰 값을 _max에 저장한다.

그리고 포인터를 옮기기 전에 left_max 에서 현재 height[left] 값을 빼서 빗물이 쌓이는 만큼만 result에 더한다.

왼쪽의 높이가 더 높아지면, 오른쪽을 포인터 이동을 하여 똑같이 계산해준다.

결국 두 포인터는 최고점에서 만나게 되고 반복문이 종료된 후, 최종적으로 result를 반환한다.



**Using Keyword**

max(list) - 리스트 안의 값 중 최대값 반환



﻿