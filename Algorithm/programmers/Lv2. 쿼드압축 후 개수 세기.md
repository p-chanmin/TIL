> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [월간 코드 챌린지 시즌1](https://school.programmers.co.kr/learn/challenges)
> 3. 쿼드압축 후 개수 세기



###### 문제 설명

0과 1로 이루어진 2n x 2n 크기의 2차원 정수 배열 arr이 있습니다. 당신은 이 arr을 [쿼드 트리](https://en.wikipedia.org/wiki/Quadtree)와 같은 방식으로 압축하고자 합니다. 구체적인 방식은 다음과 같습니다.

1. 당신이 압축하고자 하는 특정 영역을 S라고 정의합니다.
2. 만약 S 내부에 있는 모든 수가 같은 값이라면, S를 해당 수 하나로 압축시킵니다.
3. 그렇지 않다면, S를 정확히 4개의 균일한 정사각형 영역(입출력 예를 참고해주시기 바랍니다.)으로 쪼갠 뒤, 각 정사각형 영역에 대해 같은 방식의 압축을 시도합니다.

arr이 매개변수로 주어집니다. 위와 같은 방식으로 arr을 압축했을 때, 배열에 최종적으로 남는 0의 개수와 1의 개수를 배열에 담아서 return 하도록 solution 함수를 완성해주세요.

------

##### 제한사항

- arr의 행의 개수는 1 이상 1024 이하이며, 2의 거듭 제곱수 형태를 하고 있습니다. 즉, arr의 행의 개수는 1, 2, 4, 8, ..., 1024 중 하나입니다.
  - arr의 각 행의 길이는 arr의 행의 개수와 같습니다. 즉, arr은 정사각형 배열입니다.
  - arr의 각 행에 있는 모든 값은 0 또는 1 입니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(arr: Array<IntArray>): IntArray {
        var zero = 0
        var zeroTmp = 0
        var one = 0
        var oneTmp = 0
        
        if (arr[0].size == 1){
            when(arr[0][0]){
                0 -> zero++
                1 -> one++
            }
            return intArrayOf(zero, one)
        }
        
        var arr = arr.flatMap{ it.toList().chunked(arr[0].size / 2) }.chunked(arr.size)
        var a1 = arr[0].filterIndexed{i,v -> i % 2 == 0}
        var a2 = arr[0].filterIndexed{i,v -> i % 2 == 1}
        var a3 = arr[1].filterIndexed{i,v -> i % 2 == 0}
        var a4 = arr[1].filterIndexed{i,v -> i % 2 == 1}

        if((1 in a1.flatMap{it}) && (0 in a1.flatMap{it})){
            var result = solution(a1.map{ it.toIntArray() }.toTypedArray() )
            zero += result[0]
            one += result[1]
        } else{
            when(a1[0][0]){
                0 -> zeroTmp++
                1 -> oneTmp++
            }
        }
        if((1 in a2.flatMap{it}) && (0 in a2.flatMap{it})){
            var result = solution(a2.map{ it.toIntArray() }.toTypedArray() )
            zero += result[0]
            one += result[1]
        } else{
            when(a2[0][0]){
                0 -> zeroTmp++
                1 -> oneTmp++
            }
        }
        if((1 in a3.flatMap{it}) && (0 in a3.flatMap{it})){
            var result = solution(a3.map{ it.toIntArray() }.toTypedArray() )
            zero += result[0]
            one += result[1]
        } else{
            when(a3[0][0]){
                0 -> zeroTmp++
                1 -> oneTmp++
            }
        }
        if((1 in a4.flatMap{it}) && (0 in a4.flatMap{it})){
            var result = solution(a4.map{ it.toIntArray() }.toTypedArray() )
            zero += result[0]
            one += result[1]
        } else{
            when(a4[0][0]){
                0 -> zeroTmp++
                1 -> oneTmp++
            }
        }
        if(zeroTmp == 4) zeroTmp = 1
        else if(oneTmp == 4) oneTmp = 1
        return intArrayOf(zero + zeroTmp, one + oneTmp)
    }
}
```

