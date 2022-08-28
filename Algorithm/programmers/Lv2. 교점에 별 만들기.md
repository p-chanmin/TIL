> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [위클리 챌린지](https://school.programmers.co.kr/learn/challenges)
> 3. 교점에 별 만들기



###### 문제 설명

`Ax + By + C = 0`으로 표현할 수 있는 `n`개의 직선이 주어질 때, 이 직선의 교점 중 정수 좌표에 별을 그리려 합니다.

예를 들어, 다음과 같은 직선 5개를

- `2x - y + 4 = 0`
- `-2x - y + 4 = 0`
- `-y + 1 = 0`
- `5x - 8y - 12 = 0`
- `5x + 8y + 12 = 0`

좌표 평면 위에 그리면 아래 그림과 같습니다.

![RisingStarGraphBox.jpg](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/d440b8f4-91c3-4272-8a81-876e9aaffb9c/RisingStarGraphBox.jpg)

이때, 모든 교점의 좌표는 `(4, 1)`, `(4, -4)`, `(-4, -4)`, `(-4, 1)`, `(0, 4)`, `(1.5, 1.0)`, `(2.1, -0.19)`, `(0, -1.5)`, `(-2.1, -0.19)`, `(-1.5, 1.0)`입니다. 이 중 정수로만 표현되는 좌표는 `(4, 1)`, `(4, -4)`, `(-4, -4)`, `(-4, 1)`, `(0, 4)`입니다.

만약 정수로 표현되는 교점에 별을 그리면 다음과 같습니다.

![RisingStarGraphStar.jpg](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/15ffe460-62dc-48df-82a2-7d7636809454/RisingStarGraphStar.jpg)

위의 그림을 문자열로 나타낼 때, 별이 그려진 부분은 `*`, 빈 공간(격자선이 교차하는 지점)은 `.`으로 표현하면 다음과 같습니다.

```
"..........."  
".....*....."  
"..........."  
"..........."  
".*.......*."  
"..........."  
"..........."  
"..........."  
"..........."  
".*.......*."  
"..........."  
```

이때 격자판은 무한히 넓으니 모든 별을 포함하는 최소한의 크기만 나타내면 됩니다.

따라서 정답은

```
"....*...."  
"........."  
"........."  
"*.......*"  
"........."  
"........."  
"........."  
"........."  
"*.......*"  
```

입니다.

직선 `A, B, C`에 대한 정보가 담긴 배열 `line`이 매개변수로 주어집니다. 이때 모든 별을 포함하는 최소 사각형을 return 하도록 solution 함수를 완성해주세요.

------

##### 제한사항

- line의 세로(행) 길이는 2 이상 1,000 이하인 자연수입니다.
  - line의 가로(열) 길이는 3입니다.
  - line의 각 원소는 [A, B, C] 형태입니다.
  - A, B, C는 -100,000 이상 100,000 이하인 정수입니다.
  - 무수히 많은 교점이 생기는 직선 쌍은 주어지지 않습니다.
  - A = 0이면서 B = 0인 경우는 주어지지 않습니다.
- 정답은 1,000 * 1,000 크기 이내에서 표현됩니다.
- 별이 한 개 이상 그려지는 입력만 주어집니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(line: Array<IntArray>): Array<String> {
        
        val idx = combi((0 until line.size).toList(), 2)
        var p = mutableSetOf<Pair<Long, Long>>()
        
        idx.forEach{
            val a = line[it[0]][0].toDouble()
            val b = line[it[0]][1].toDouble()
            val e = line[it[0]][2].toDouble()
            val c = line[it[1]][0].toDouble()
            val d = line[it[1]][1].toDouble()
            val f = line[it[1]][2].toDouble()
            if((a * d) - (b * c) != 0.0){
                var x = ((b*f)-(e*d))/((a*d)-(b*c))
                var y = ((e*c)-(a*f))/((a*d)-(b*c))
                if( x == x.toLong().toDouble() && y == y.toLong().toDouble()){
                    p.add(Pair(x.toLong(), y.toLong()))
                }
            }
        }
        val minX = p.minOf{ it.first }
        val minY = p.minOf{ it.second }
        val xSpace = (p.maxOf{ it.first } - minX + 1).toInt()
        val ySpace = (p.maxOf{ it.second } - minY + 1).toInt()
        var s = Array(ySpace){ Array(xSpace){"."} }
        
        p.forEach{ 
            var x = (it.first - minX).toInt()
            var y = (it.second - minY).toInt()
            s[y][x] = "*"
        }

        return s.map{ it.joinToString("") }.reversed().toTypedArray()
    }
    fun combi(l: List<Int>, n: Int, result: List<Int> = listOf<Int>(), idx: Int = 0): List<List<Int>>{
        return if( result.size >= n ) listOf(result)
        else l.slice(idx until l.size).flatMapIndexed{i,v -> combi(l, n, result + v, idx + i + 1)}
    }
}
```

