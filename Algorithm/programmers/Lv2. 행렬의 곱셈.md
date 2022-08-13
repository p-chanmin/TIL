> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [연습문제](https://school.programmers.co.kr/learn/challenges)
> 3. 행렬의 곱셈

###### 문제 설명

2차원 행렬 arr1과 arr2를 입력받아, arr1에 arr2를 곱한 결과를 반환하는 함수, solution을 완성해주세요.

##### 제한 조건

- 행렬 arr1, arr2의 행과 열의 길이는 2 이상 100 이하입니다.
- 행렬 arr1, arr2의 원소는 -10 이상 20 이하인 자연수입니다.
- 곱할 수 있는 배열만 주어집니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(arr1: Array<IntArray>, arr2: Array<IntArray>): Array<IntArray> {
        var arr2 = (0 until arr2[0].size).map{ idx -> arr2.flatMap{ it.filterIndexed{ i, v -> i == idx } } } 
        return arr1.map{ v ->
            arr2.map{ it.mapIndexed{ i, k -> k * v[i] }.sum() }.toIntArray()
        }.toTypedArray()
    }
}
```

