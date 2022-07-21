> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [월간 코드 챌린지 시즌3](https://school.programmers.co.kr/learn/challenges)
> 3. 나머지가 1이 되는 수 찾기



###### 문제 설명

자연수 `n`이 매개변수로 주어집니다. `n`을 `x`로 나눈 나머지가 1이 되도록 하는 가장 작은 자연수 `x`를 return 하도록 solution 함수를 완성해주세요. 답이 항상 존재함은 증명될 수 있습니다.

------

##### 제한사항

- 3 ≤ `n` ≤ 1,000,000



`[solution.kt]`

```kotlin
class Solution {
    fun solution(n: Int): Int {

        for (i in 2 until n){
            if (n % i == 1) return i
        }
        return 0
        
    }
}
```

