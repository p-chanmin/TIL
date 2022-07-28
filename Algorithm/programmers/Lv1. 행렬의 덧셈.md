> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [연습문제](https://school.programmers.co.kr/learn/challenges)
> 3. 행렬의 덧셈



###### 문제 설명

행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다. 2개의 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환하는 함수, solution을 완성해주세요.

##### 제한 조건

- 행렬 arr1, arr2의 행과 열의 길이는 500을 넘지 않습니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(arr1: Array<IntArray>, arr2: Array<IntArray>): Array<IntArray> {
        var answer = arrayListOf<IntArray>()
        for ( i in 0 until arr1.size ){
            var arr = intArrayOf()
            for (j in 0 until arr1[0].size){
                arr += arr1[i][j] + arr2[i][j]
            }
            answer.add(arr)
        }
        return answer.toTypedArray()
    }
}
```

