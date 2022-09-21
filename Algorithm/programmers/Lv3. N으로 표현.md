> 1. [코딩테스트 연습](https://school.programmers.co.kr/learn/challenges)
>2. [동적계획법(Dynamic Programming)](https://school.programmers.co.kr/learn/courses/30/parts/12263)
> 3. N으로 표현



###### 문제 설명

아래와 같이 5와 사칙연산만으로 12를 표현할 수 있습니다.

12 = 5 + 5 + (5 / 5) + (5 / 5)
12 = 55 / 5 + 5 / 5
12 = (55 + 5) / 5

5를 사용한 횟수는 각각 6,5,4 입니다. 그리고 이중 가장 작은 경우는 4입니다.
이처럼 숫자 N과 number가 주어질 때, N과 사칙연산만 사용해서 표현 할 수 있는 방법 중 N 사용횟수의 최솟값을 return 하도록 solution 함수를 작성하세요.

##### 제한사항

- N은 1 이상 9 이하입니다.
- number는 1 이상 32,000 이하입니다.
- 수식에는 괄호와 사칙연산만 가능하며 나누기 연산에서 나머지는 무시합니다.
- 최솟값이 8보다 크면 -1을 return 합니다.



`[solution.kt]`

```kotlin
class Solution {
    fun solution(N: Int, number: Int): Int {
        
        var result = mutableListOf<MutableList<Int>>()
        var tmp = mutableListOf<Int>()
        var cnt = 1
        while(cnt <= 8){
            if (result.isEmpty()) tmp.add(N)
            else{
                for (i in result[cnt-2].indices){
                    if(i == 0)tmp.add( (result[cnt-2][i].toString() + N.toString()).toInt() )
                    tmp.add( result[cnt-2][i] + N )
                    tmp.add( result[cnt-2][i] - N )
                    tmp.add( N - result[cnt-2][i] )
                    tmp.add( result[cnt-2][i] * N )
                    tmp.add( result[cnt-2][i] / N )
                    if(result[cnt-2][i] != 0) tmp.add( N / result[cnt-2][i] )
                }
                if(cnt >= 4){
                    for( i in 2 until cnt){
                        if(i <= cnt-i){
                            
                            for( j in result[i-1].toSet() ){
                                for(k in result[cnt-i-1].toSet()){
                                    tmp.add(j+k)
                                    tmp.add(j-k)
                                    tmp.add(k-j)
                                    tmp.add(j*k)
                                    if(k != 0)tmp.add(j/k)
                                    if(j != 0)tmp.add(k/j)
                                }
                            }
                        }
                        else break
                    }
                    
                }
            }
            if (number in tmp) return cnt
            result.add(tmp)
            tmp = mutableListOf<Int>()
            cnt++
        }
        return -1
    }
}
```

