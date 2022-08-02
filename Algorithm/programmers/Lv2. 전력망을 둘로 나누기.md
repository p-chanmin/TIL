> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [완전탐색](https://school.programmers.co.kr/learn/courses/30/parts/12230)
> 3. 전력망을 둘로 나누기



###### 문제 설명

n개의 송전탑이 전선을 통해 하나의 [트리](https://en.wikipedia.org/wiki/Tree_(data_structure)) 형태로 연결되어 있습니다. 당신은 이 전선들 중 하나를 끊어서 현재의 전력망 네트워크를 2개로 분할하려고 합니다. 이때, 두 전력망이 갖게 되는 송전탑의 개수를 최대한 비슷하게 맞추고자 합니다.

송전탑의 개수 n, 그리고 전선 정보 wires가 매개변수로 주어집니다. 전선들 중 하나를 끊어서 송전탑 개수가 가능한 비슷하도록 두 전력망으로 나누었을 때, 두 전력망이 가지고 있는 송전탑 개수의 차이(절대값)를 return 하도록 solution 함수를 완성해주세요.

------

##### 제한사항

- n은 2 이상 100 이하인 자연수입니다.
- wires는 길이가`n-1`인 정수형 2차원 배열입니다.
  - wires의 각 원소는 [v1, v2] 2개의 자연수로 이루어져 있으며, 이는 전력망의 v1번 송전탑과 v2번 송전탑이 전선으로 연결되어 있다는 것을 의미합니다.
  - 1 ≤ v1 < v2 ≤ n 입니다.
  - 전력망 네트워크가 하나의 트리 형태가 아닌 경우는 입력으로 주어지지 않습니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(n: Int, wires: Array<IntArray>): Int {
        
        return (0 until wires.size).map{ index -> wires.filterIndexed{ i, v -> i != index }.map{ it.toSet() }.toMutableList() }.map{
            var arr = it
            while ( arr.size > 2 ){
                var start = arr[0]
                arr = arr.slice(1 until arr.size).toMutableList()
                for ( i in 0 until arr.size ) {
                    if (start.intersect(arr[i]).size == 0 && i == arr.size - 1) arr.add(start)
                    else if (start.intersect(arr[i]).size == 0) continue
                    else {
                        arr.add(start.union(arr[i]))
                        arr.removeAt(i)
                        break
                    }
                }
            }
            if (arr[0].intersect(arr[1]).size == 0) Math.abs(arr[0].size - arr[1].size)
            else {
                arr[0].union(arr[1]).size * 2 - n
            }
        }.minOf{it}

    }
}
```

