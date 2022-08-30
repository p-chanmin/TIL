> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [2022 KAKAO BLIND RECRUITMENT](https://school.programmers.co.kr/learn/challenges)
> 3. 양궁대회



###### 문제 설명

##### 문제 설명

카카오배 양궁대회가 열렸습니다.
`라이언`은 저번 카카오배 양궁대회 우승자이고 이번 대회에도 결승전까지 올라왔습니다. 결승전 상대는 `어피치`입니다.
카카오배 양궁대회 운영위원회는 한 선수의 연속 우승보다는 다양한 선수들이 양궁대회에서 우승하기를 원합니다. 따라서, 양궁대회 운영위원회는 결승전 규칙을 전 대회 우승자인 라이언에게 불리하게 다음과 같이 정했습니다.

1. 어피치가 화살 `n`발을 다 쏜 후에 라이언이 화살 `n`발을 쏩니다.

2. 점수를 계산합니다.

   1. 과녁판은 아래 사진처럼 생겼으며 가장 작은 원의 과녁 점수는 10점이고 가장 큰 원의 바깥쪽은 과녁 점수가 0점입니다. ![01_2022_공채문제_양궁대회_01.png](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/2c73b8f8-c938-4b6e-9bc3-e3a3784d6a41/01_2022_%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8E%E1%85%A2%E1%84%86%E1%85%AE%E1%86%AB%E1%84%8C%E1%85%A6_%E1%84%8B%E1%85%A3%E1%86%BC%E1%84%80%E1%85%AE%E1%86%BC%E1%84%83%E1%85%A2%E1%84%92%E1%85%AC_01.png)

   2. 만약, k(k는 1~10사이의 자연수)점을 어피치가 a발을 맞혔고 라이언이 b발을 맞혔을 경우 더 많은 화살을 k점에 맞힌 선수가 k 점을 가져갑니다. 단, a = b일 경우는 어피치가 k점을 가져갑니다.

       

      k점을 여러 발 맞혀도 k점 보다 많은 점수를 가져가는 게 아니고 k점만 가져가는 것을 유의하세요. 또한 a = b = 0 인 경우, 즉, 라이언과 어피치 모두 k점에 단 하나의 화살도 맞히지 못한 경우는 어느 누구도 k점을 가져가지 않습니다.

      - 예를 들어, 어피치가 10점을 2발 맞혔고 라이언도 10점을 2발 맞혔을 경우 어피치가 10점을 가져갑니다.
      - 다른 예로, 어피치가 10점을 0발 맞혔고 라이언이 10점을 2발 맞혔을 경우 라이언이 10점을 가져갑니다.

   3. 모든 과녁 점수에 대하여 각 선수의 최종 점수를 계산합니다.

3. 최종 점수가 더 높은 선수를 우승자로 결정합니다. 단, 최종 점수가 같을 경우 어피치를 우승자로 결정합니다.

현재 상황은 어피치가 화살 `n`발을 다 쏜 후이고 라이언이 화살을 쏠 차례입니다.
라이언은 어피치를 가장 큰 점수 차이로 이기기 위해서 `n`발의 화살을 어떤 과녁 점수에 맞혀야 하는지를 구하려고 합니다.

화살의 개수를 담은 자연수 `n`, 어피치가 맞힌 과녁 점수의 개수를 10점부터 0점까지 순서대로 담은 정수 배열 `info`가 매개변수로 주어집니다. 이때, 라이언이 가장 큰 점수 차이로 우승하기 위해 `n`발의 화살을 어떤 과녁 점수에 맞혀야 하는지를 10점부터 0점까지 순서대로 정수 배열에 담아 return 하도록 solution 함수를 완성해 주세요. 만약, 라이언이 우승할 수 없는 경우(무조건 지거나 비기는 경우)는 `[-1]`을 return 해주세요.

------

##### 제한사항

- 1 ≤ `n` ≤ 10
- `info`의 길이 = 11
  - 0 ≤ `info`의 원소 ≤ `n`
  - `info`의 원소 총합 = `n`
  - `info`의 i번째 원소는 과녁의 `10 - i` 점을 맞힌 화살 개수입니다. ( i는 0~10 사이의 정수입니다.)
- 라이언이 우승할 방법이 있는 경우, return 할 정수 배열의 길이는 11입니다.
  - 0 ≤ return할 정수 배열의 원소 ≤ `n`
  - return할 정수 배열의 원소 총합 = `n` (꼭 n발을 다 쏴야 합니다.)
  - return할 정수 배열의 i번째 원소는 과녁의 `10 - i` 점을 맞힌 화살 개수입니다. ( i는 0~10 사이의 정수입니다.)
  - 라이언이 가장 큰 점수 차이로 우승할 수 있는 방법이 여러 가지 일 경우, 가장 낮은 점수를 더 많이 맞힌 경우를 return 해주세요.
    - 가장 낮은 점수를 맞힌 개수가 같을 경우 계속해서 그다음으로 낮은 점수를 더 많이 맞힌 경우를 return 해주세요.
    - 예를 들어, `[2,3,1,0,0,0,0,1,3,0,0]`과 `[2,1,0,2,0,0,0,2,3,0,0]`를 비교하면 `[2,1,0,2,0,0,0,2,3,0,0]`를 return 해야 합니다.
    - 다른 예로, `[0,0,2,3,4,1,0,0,0,0,0]`과 `[9,0,0,0,0,0,0,0,1,0,0]`를 비교하면`[9,0,0,0,0,0,0,0,1,0,0]`를 return 해야 합니다.
- 라이언이 우승할 방법이 없는 경우, return 할 정수 배열의 길이는 1입니다.
  - 라이언이 어떻게 화살을 쏘든 **라이언의 점수가 어피치의 점수보다 낮거나 같으면 `[-1]`을 return 해야 합니다.**



`[solution.kt]`

```kotlin
class Solution {
    fun solution(n: Int, info: IntArray): IntArray {

        var idx = listOf<List<Int>>()
        (n downTo 1).forEach{
            idx += combi((0 until 11).toList(), it)
        }
        
        var rInfo = listOf<List<Int>>()
        idx.forEach{ idx ->
            rInfo += listOf( info.mapIndexed{ i,v -> if (i in idx) v + 1 else 0 } ).filter{ it.sum() <= n }
                .map{
                    if(it.sum() < n){
                        var tmp = it.toMutableList()
                        tmp[10] += n - it.sum()
                        tmp.toList()
                    }
                    else it
                }
        }
        
        var scoreIdx = rInfo.mapIndexed{ i,v -> listOf(i, compare(v, info)) }
        var maxScore = scoreIdx.maxOf{ it[1] }
        
        if (maxScore <= 0) return intArrayOf(-1)
        
        rInfo = scoreIdx.filter{ it[1] == maxScore }.map{ rInfo[it[0]] }
        if (rInfo.size == 1) return rInfo[0].toIntArray()
        
        for(i in 10 downTo 0){
            var tmp = rInfo.filter{ it[i] == rInfo.maxOf{ it[i] } }
            if( tmp.size == 1 ){
                rInfo = tmp
                break
            }
        }
        return rInfo.flatMap{ it }.toIntArray()
    }
    fun compare(l: List<Int>, info: IntArray): Int{
        var scoreR = 0
        var scoreA = 0
        (0 .. 10).forEach{ i ->
            when{
                l[i] > info[i] -> scoreR += 10 - i
                info[i] > l[i] -> scoreA += 10 - i
                info[i] == l[i] && l[i] != 0 -> scoreA += 10 - i
            }            
        }
        return scoreR - scoreA
    }
    
    fun combi(l: List<Int>, n: Int, result: List<Int> = listOf<Int>(), idx: Int = 0): List<List<Int>>{
        return if(result.size >= n) listOf(result)
        else l.slice(idx until l.size).flatMapIndexed{i,v -> combi(l, n, result + v, idx + i + 1)}
    }
}
```

