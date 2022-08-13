> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [월간 코드 챌린지 시즌1](https://school.programmers.co.kr/learn/challenges)
> 3. 삼각 달팽이



###### 문제 설명

정수 n이 매개변수로 주어집니다. 다음 그림과 같이 밑변의 길이와 높이가 n인 삼각형에서 맨 위 꼭짓점부터 반시계 방향으로 달팽이 채우기를 진행한 후, 첫 행부터 마지막 행까지 모두 순서대로 합친 새로운 배열을 return 하도록 solution 함수를 완성해주세요.

![examples.png](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/e1e53b93-dcdf-446f-b47f-e8ec1292a5e0/examples.png)

------

##### 제한사항

- n은 1 이상 1,000 이하입니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(n: Int): IntArray {
        var snail = (1 .. n).map{ (1..n).map{ 0 }.toMutableList() }
        var x = -1
        var y = 0
        var num = 1
        
        (0 until n).forEach{ i ->
            (i until n).forEach{ j ->
                when(i % 3){
                    0 -> x++
                    1 -> y++
                    2 ->{
                        x--
                        y--
                    }
                }
                snail[x][y] = num++
            }
        }
        return snail.flatMap{ it.filter{ it != 0 } }.toIntArray()
    }
}
```

