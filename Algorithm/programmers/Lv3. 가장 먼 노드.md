> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
> 2. [그래프](https://school.programmers.co.kr/learn/courses/30/parts/14393)
> 3. 가장 먼 노드



###### 문제 설명

n개의 노드가 있는 그래프가 있습니다. 각 노드는 1부터 n까지 번호가 적혀있습니다. 1번 노드에서 가장 멀리 떨어진 노드의 갯수를 구하려고 합니다. 가장 멀리 떨어진 노드란 최단경로로 이동했을 때 간선의 개수가 가장 많은 노드들을 의미합니다.

노드의 개수 n, 간선에 대한 정보가 담긴 2차원 배열 vertex가 매개변수로 주어질 때, 1번 노드로부터 가장 멀리 떨어진 노드가 몇 개인지를 return 하도록 solution 함수를 작성해주세요.

##### 제한사항

- 노드의 개수 n은 2 이상 20,000 이하입니다.
- 간선은 양방향이며 총 1개 이상 50,000개 이하의 간선이 있습니다.
- vertex 배열 각 행 [a, b]는 a번 노드와 b번 노드 사이에 간선이 있다는 의미입니다.



`[solution.kt]`

```kotlin
import java.util.*
class Solution {
    fun solution(n: Int, edge: Array<IntArray>): Int {
        
        var graph = Array<ArrayList<Pair<Int, Int>>>(n+1){ arrayListOf() }
        edge.forEach{
            graph[it[0]].add(Pair(it[1], 1))
            graph[it[1]].add(Pair(it[0], 1))
        }
        var dist = IntArray(n+1){ 1234567890 }
        dist[1] = 0
        
        var q = PriorityQueue<Pair<Int, Int>>{ a,b -> a.second - b.second }
        q.add(Pair(1, 0))
        
        while(!q.isEmpty()){
            var head = q.poll()
            
            if(head.second > dist[head.first]) continue
            
            for(i in graph[head.first]){
                var nextNum = i.first
                var cost = i.second
                if(dist[nextNum] > dist[head.first] + cost){
                    dist[nextNum] = dist[head.first] + cost
                    q.add(Pair(nextNum, dist[nextNum]))
                }
            }
        }
        val max = dist.slice(1 until dist.size).maxOf{ it }
        return dist.count{ it == max }
    }
}
```

