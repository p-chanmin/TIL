> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
>2. [월간 코드 챌린지 시즌1](https://school.programmers.co.kr/learn/challenges)
> 3. 3진법 뒤집기



###### 문제 설명

자연수 n이 매개변수로 주어집니다. n을 3진법 상에서 앞뒤로 뒤집은 후, 이를 다시 10진법으로 표현한 수를 return 하도록 solution 함수를 완성해주세요.

------

- ##### 제한사항

  - n은 1 이상 100,000,000 이하인 자연수입니다.



`[solution.py]`

```python
def solution(n):
    answer = []
    while (n >= 3):
        answer.append(n % 3)
        n = n // 3
    answer.append(n)
    
    result = 0
    for i in range(len(answer)):
        result += (answer[::-1])[i] * (3 ** i)
    
    return result
```

