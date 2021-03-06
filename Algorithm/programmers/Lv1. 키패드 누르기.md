> 1. [코딩테스트 연습](https://programmers.co.kr/learn/challenges)
>2. [2020 카카오 인턴십](https://programmers.co.kr/learn/challenges)
> 3. 키패드 누르기



###### 문제 설명

스마트폰 전화 키패드의 각 칸에 다음과 같이 숫자들이 적혀 있습니다.

![kakao_phone1.png](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/4b69a271-5f4a-4bf4-9ebf-6ebed5a02d8d/kakao_phone1.png)

이 전화 키패드에서 왼손과 오른손의 엄지손가락만을 이용해서 숫자만을 입력하려고 합니다.
맨 처음 왼손 엄지손가락은 `*` 키패드에 오른손 엄지손가락은 `#` 키패드 위치에서 시작하며, 엄지손가락을 사용하는 규칙은 다음과 같습니다.

1. 엄지손가락은 상하좌우 4가지 방향으로만 이동할 수 있으며 키패드 이동 한 칸은 거리로 1에 해당합니다.
2. 왼쪽 열의 3개의 숫자 `1`, `4`, `7`을 입력할 때는 왼손 엄지손가락을 사용합니다.
3. 오른쪽 열의 3개의 숫자 `3`, `6`, `9`를 입력할 때는 오른손 엄지손가락을 사용합니다.
4. 가운데 열의 4개의 숫자 `2`, `5`, `8`, `0`을 입력할 때는 두 엄지손가락의 현재 키패드의 위치에서 더 가까운 엄지손가락을 사용합니다.
   4-1. 만약 두 엄지손가락의 거리가 같다면, 오른손잡이는 오른손 엄지손가락, 왼손잡이는 왼손 엄지손가락을 사용합니다.

순서대로 누를 번호가 담긴 배열 numbers, 왼손잡이인지 오른손잡이인 지를 나타내는 문자열 hand가 매개변수로 주어질 때, 각 번호를 누른 엄지손가락이 왼손인 지 오른손인 지를 나타내는 연속된 문자열 형태로 return 하도록 solution 함수를 완성해주세요.

##### **[제한사항]**

- numbers 배열의 크기는 1 이상 1,000 이하입니다.

- numbers 배열 원소의 값은 0 이상 9 이하인 정수입니다.

- hand는

   

  ```
  "left"
  ```

   

  또는

   

  ```
  "right"
  ```

   

  입니다.

  - `"left"`는 왼손잡이, `"right"`는 오른손잡이를 의미합니다.

- 왼손 엄지손가락을 사용한 경우는 `L`, 오른손 엄지손가락을 사용한 경우는 `R`을 순서대로 이어붙여 문자열 형태로 return 해주세요.



`[solution.py]`

```python
def close_position(now, dest):
    n = abs(now - dest)
    if n == 0:
        return 0
    elif n in [1, 3]:
        return 1
    elif n in [2, 4, 6]:
        return 2
    elif n in [5, 7, 9]:
        return 3
    elif n in [8, 10]:
        return 4
    elif n in [11]:
        return 5

def solution(numbers, hand):
    answer = ''
    lp = 10
    rp = 12
    
    for i in numbers:
        if i in [1,4,7]:
            answer += 'L'
            lp = i
        elif i in [3,6,9]:
            answer += 'R'
            rp = i
        elif i in [2,5,8,0]:
            if i == 0:
                i = 11
            if close_position(lp, i) < close_position(rp, i):
                answer += 'L'
                lp = i
            elif close_position(lp, i) > close_position(rp, i):
                answer += 'R'
                rp = i
            else:
                if hand == 'right':
                    answer += 'R'
                    rp = i
                else:
                    answer += 'L'
                    lp = i
    
    return answer
```

