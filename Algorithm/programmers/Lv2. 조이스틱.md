> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [탐욕법(Greedy)](https://school.programmers.co.kr/learn/courses/30/parts/12244)
> 3. 조이스틱



###### 문제 설명

조이스틱으로 알파벳 이름을 완성하세요. 맨 처음엔 A로만 이루어져 있습니다.
ex) 완성해야 하는 이름이 세 글자면 AAA, 네 글자면 AAAA

조이스틱을 각 방향으로 움직이면 아래와 같습니다.

```
▲ - 다음 알파벳
▼ - 이전 알파벳 (A에서 아래쪽으로 이동하면 Z로)
◀ - 커서를 왼쪽으로 이동 (첫 번째 위치에서 왼쪽으로 이동하면 마지막 문자에 커서)
▶ - 커서를 오른쪽으로 이동 (마지막 위치에서 오른쪽으로 이동하면 첫 번째 문자에 커서)
```

예를 들어 아래의 방법으로 "JAZ"를 만들 수 있습니다.

```
- 첫 번째 위치에서 조이스틱을 위로 9번 조작하여 J를 완성합니다.
- 조이스틱을 왼쪽으로 1번 조작하여 커서를 마지막 문자 위치로 이동시킵니다.
- 마지막 위치에서 조이스틱을 아래로 1번 조작하여 Z를 완성합니다.
따라서 11번 이동시켜 "JAZ"를 만들 수 있고, 이때가 최소 이동입니다.
```

만들고자 하는 이름 name이 매개변수로 주어질 때, 이름에 대해 조이스틱 조작 횟수의 최솟값을 return 하도록 solution 함수를 만드세요.

##### 제한 사항

- name은 알파벳 대문자로만 이루어져 있습니다.
- name의 길이는 1 이상 20 이하입니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(name: String): Int {
 
        val alpha = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        var n = name.map{ 
            var idx = alpha.indexOf(it)
            if (idx > 13) 26 - idx
            else idx
        }
        if (n.count{ it == 0 } == n.size ) return 0
        
        var move = listOf( n.size - 1 ) 
        var toMove = n.slice(1 until n.size)
        var zeroIdx = (toMove.indices).map { if (toMove[it] == 0) it else -1 }.filter { it != -1 }
        var list = zeroIdx.map{ listOf(toMove.slice(0 until it), toMove.slice(it until toMove.size)) }
        
        move += list.map{
            var toR = it[0].toMutableList()
            var toL = it[1].toMutableList()
            while( toR.size != 0 && toR.last() == 0 ) toR.removeAt(toR.size - 1)
            while( toL.size != 0 && toL.first() == 0 ) toL.removeAt(0)
            listOf( toR, toL )
        }.toSet().map{
            it.minOf{ it.size } * 2 + it.maxOf{ it.size }            
        }

        return n.sum() + move.minOf{ it }

    }
}
```

