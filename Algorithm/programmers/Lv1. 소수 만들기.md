> 1. [코딩테스트 연습](https://programmers.co.kr/learn/challenges)
> 2. [Summer/Winter Coding(~2018)](https://programmers.co.kr/learn/challenges)
> 3. 소수 만들기



###### 문제 설명

주어진 숫자 중 3개의 수를 더했을 때 소수가 되는 경우의 개수를 구하려고 합니다. 숫자들이 들어있는 배열 nums가 매개변수로 주어질 때, nums에 있는 숫자들 중 서로 다른 3개를 골라 더했을 때 소수가 되는 경우의 개수를 return 하도록 solution 함수를 완성해주세요.

##### 제한사항

- nums에 들어있는 숫자의 개수는 3개 이상 50개 이하입니다.
- nums의 각 원소는 1 이상 1,000 이하의 자연수이며, 중복된 숫자가 들어있지 않습니다.



`[solution.py]`

```python
import itertools
def sosu(n):
    result = True
    for i in range(2,n):
        if n%i==0:
            result=False
            break
    return result

def solution(nums):
    answer = 0
    combi=list(itertools.combinations(nums,3))
    for i in range(len(combi)):
        if(sosu(sum(combi[i]))):
            answer+=1

    return answer
```

