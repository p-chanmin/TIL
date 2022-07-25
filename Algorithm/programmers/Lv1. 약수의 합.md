> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
>2. [연습문제](https://school.programmers.co.kr/learn/challenges)
> 3. 약수의 합



###### 문제 설명

정수 n을 입력받아 n의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.

##### 제한 사항

- `n`은 0 이상 3000이하인 정수입니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(n: Int): Int {
        
        return (1..n).filter{ n % it == 0 }.sum()
        
    }
}
```

