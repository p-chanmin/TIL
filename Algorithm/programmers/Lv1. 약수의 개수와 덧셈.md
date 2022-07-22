> 1. [코딩테스트 연습](https://programmers.co.kr/learn/challenges)
>2. [월간 코드 챌린지 시즌2](https://programmers.co.kr/learn/challenges)
> 3. 약수의 개수와 덧셈



###### 문제 설명

두 정수 `left`와 `right`가 매개변수로 주어집니다. `left`부터 `right`까지의 모든 수들 중에서, 약수의 개수가 짝수인 수는 더하고, 약수의 개수가 홀수인 수는 뺀 수를 return 하도록 solution 함수를 완성해주세요.

------

##### 제한사항

- 1 ≤ `left` ≤ `right` ≤ 1,000



`[solution.py]`

```python
import collections
def divisorNum(num):
    d = 2
    result = []
    while d <= num:
        if num % d == 0:
            result.append(d)
            num = num / d
        else:
            d += 1
    c = collections.Counter(result)
    n = 1
    for i in c:
        n *=(c[i]+1)
    return n
    
def solution(left, right):
    answer = 0
    
    for i in range(left, right+1):
        if divisorNum(i) % 2 == 0:
            answer += i
        else:
            answer -= i

    return answer
```

`[solution.py]`

```python
def solution(left, right):
    answer = 0
    for i in range(left,right+1):
        if int(i**0.5)==i**0.5:
            answer -= i
        else:
            answer += i
    return answer
```

