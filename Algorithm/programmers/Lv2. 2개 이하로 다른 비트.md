> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [월간 코드 챌린지 시즌2](https://school.programmers.co.kr/learn/challenges)
> 3. 2개 이하로 다른 비트



###### 문제 설명

양의 정수 `x`에 대한 함수 `f(x)`를 다음과 같이 정의합니다.

- `x`보다 크고 `x`와 **비트가 1~2개 다른** 수들 중에서 제일 작은 수

예를 들어,

- `f(2) = 3` 입니다. 다음 표와 같이 2보다 큰 수들 중에서 비트가 다른 지점이 2개 이하이면서 제일 작은 수가 3이기 때문입니다.

| 수   | 비트         | 다른 비트의 개수 |
| ---- | ------------ | ---------------- |
| 2    | `000...0010` |                  |
| 3    | `000...0011` | 1                |

- `f(7) = 11` 입니다. 다음 표와 같이 7보다 큰 수들 중에서 비트가 다른 지점이 2개 이하이면서 제일 작은 수가 11이기 때문입니다.

| 수   | 비트         | 다른 비트의 개수 |
| ---- | ------------ | ---------------- |
| 7    | `000...0111` |                  |
| 8    | `000...1000` | 4                |
| 9    | `000...1001` | 3                |
| 10   | `000...1010` | 3                |
| 11   | `000...1011` | 2                |

정수들이 담긴 배열 `numbers`가 매개변수로 주어집니다. `numbers`의 모든 수들에 대하여 각 수의 `f` 값을 배열에 차례대로 담아 return 하도록 solution 함수를 완성해주세요.

------

##### 제한사항

- 1 ≤ `numbers`의 길이 ≤ 100,000
- 0 ≤ `numbers`의 모든 수 ≤ 10<sup>15</sup>



`[solution.kt]`

```kotlin
class Solution {
    fun solution(numbers: LongArray): LongArray {
        return numbers.map{ f(it) }.toLongArray()
    }
    fun f(x: Long): Long{
        var x = x.toString(2)
        val idx = x.lastIndexOf('0')
        when{
            idx == -1 -> {
                x = "10" + x.slice(1 until x.length)
            }
            idx == x.length - 1 -> {
                x = x.slice(0 until idx) + "1"
            }
            else -> {
                x = x.slice(0 until idx) + "10" + x.slice(idx + 2 until x.length)
            }
        }
        return x.toLong(2)
    }
}
```

