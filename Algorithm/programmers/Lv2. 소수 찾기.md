> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [완전탐색](https://school.programmers.co.kr/learn/courses/30/parts/12230)
> 3. 소수 찾기



###### 문제 설명

한자리 숫자가 적힌 종이 조각이 흩어져있습니다. 흩어진 종이 조각을 붙여 소수를 몇 개 만들 수 있는지 알아내려 합니다.

각 종이 조각에 적힌 숫자가 적힌 문자열 numbers가 주어졌을 때, 종이 조각으로 만들 수 있는 소수가 몇 개인지 return 하도록 solution 함수를 완성해주세요.

##### 제한사항

- numbers는 길이 1 이상 7 이하인 문자열입니다.
- numbers는 0~9까지 숫자만으로 이루어져 있습니다.
- "013"은 0, 1, 3 숫자가 적힌 종이 조각이 흩어져있다는 의미입니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(numbers: String): Int {
        var number = (1 .. numbers.toList().size).flatMap { combi(numbers.toList(), it) }
        return number.map{ it.joinToString("").toInt() }.toSet().filter { sosu(it) }.size
    }
    
    fun combi(l: List<Char>, n:Int, result: List<Char> = listOf(), self: Int = -1): List<List<Char>> {
        return if (result.size >= n){
            listOf(result)
        }else{
            val list = l.filterIndexed{ i, v -> i != self }
            list.flatMapIndexed { i, v -> 
                combi(list, n, result+ v, i)
            }
        }
    }
    
    fun sosu(n: Int): Boolean{
        if ( n <= 1 ) return false
        for (i in 2 .. Math.sqrt(n.toDouble()).toInt()){
            if (n % i == 0) return false
        }
        return true
    }
}
```

