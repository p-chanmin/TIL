# UML (Unified Modeling Language)

**통합 모델링 언어**(UML : Unified Modeling Language)는 소프트웨어 공학에서 사용되는 표준화된 범용 모델링 언어이다.

이런 UML은 소프트웨어를 설계하며 필요에 의해서 사용되는데 일반적으로 아래 3가지의 목적을 가지고 만듭니다.

- 의사소통 또는 설계 논의를 위해
- 전체 시스템의 구조 및 클래스의 의존성 파악을 위해
- 유지보수를 위한 설계의 back-end 문서 제작을 위해



[TOC]



## 클래스 ( class )

클래스 다이어그램은 정적 다이어그램으로 클래스의 구성요소 및 클래스간의 관계를 표한하는 대표적인 UML



### 목적

* 문제 해결을 위한 도메인 구조를 나타내어 보이지 않는 도메인 안의 개념과 같은 추상적인 개념을 기술하기 위해

* 소프트웨어의 설계 혹은 완성된 소프트웨어의 구현 설명을 목적



### 구성요소

* **접근 제어자**

  | 접근 제어자 | 의미      |
  | :---------: | --------- |
  |      +      | public    |
  |      -      | private   |
  |      #      | protected |
  |      ~      | default   |

  {readonly} 가 붙으면 **final**을 의미한다.

  밑줄은 **static**을 의미한다.

  {abstract}는 **추상 클래스**를 의미한다.

  [*] 나 [0...1]은 리스트와 같은 변수에 지정된 사이즈를 의미한다.

  

  ![img](https://blog.kakaocdn.net/dn/dpDiUW/btrb8T3sAU9/USvKxTjpTNuNzT4drkr3ek/img.png)

* **형식**

  * **속성(Attribute)**

    {접근 제어자}{필드명} : {타입} = {기본값}

  * **메서드(Method)**

    {접근 제어자}{메소드명}({파라미터 타입}) : {반환 타입}



* **클래스 다이어그램을 이용한 관계 표현**

  ![img](https://www.nextree.co.kr/content/images/2021/01/--6-----------.png)



### 예시

* **Generalization ( 일반화 )**

  ![img](https://www.nextree.co.kr/content/images/2021/01/--7-Generalization1.png)

  Generalization은 우리가 일반적으로 알고 있는 상속을 의미

  클래스 다이어그램에서는 **실선에 비어있는 화살표로 표시**



* **Realization ( 실체화 )**

  ![img](https://www.nextree.co.kr/content/images/2021/01/--8-Realization.png)

  Realization은 interface에 있는 spec을 오버라이딩하여 실제로 구현하는 것

  **Realization은 점선과 비어있는 화살표로 표현**한다.



* **Dependency ( 의존 )**

  ![img](https://www.nextree.co.kr/content/images/2021/01/--9-Dependency.png)

  ![img](https://www.nextree.co.kr/content/images/2021/01/--10-Dependency2.png)

  Dependency는 클래스간의 참조가 일어나는 것으로 **Dependency 참조는 메서드 내에서 대상 클래스의 객체를 생성하거나 사용, 리턴받아 사용하는 것**이다.

  **이 참조는 해당 클래스와의 관계를 계속 유지하지 않는다.**

  dependency는 점선과 화살표로 이루어져 있다.



* **Association & Direct Association ( 연관 )**

  ![img](https://www.nextree.co.kr/content/images/2021/01/--11-Assocication.png)

  **Association은 다른 객체의 참조를 가지는 필드**를 의미한다.

  실선으로 표현되며 방향성이 존재하는 경우에는 화살표를 넣어 표시한다.

  둘의 연관관계가 어떻게 되는지 숫자로 표시할 수 있다.

  - 1 - 1개의 표현
  - \* - 0 ~ n 개의 표현
  - n...m : n 부터 m까지 연관관계를 맺음



* **Aggregation ( 집합 )**

  ![img](https://www.nextree.co.kr/content/images/2021/01/--16-Aggregation.png)

  **Aggregation은 Association의 집합관계를 나타내는 것으로 Collection이나 Array를 이용하는 관계**이다.

  Aggregation 관계는 일반적인 Association으로도 충분히 나타낼 수 있는 관계

  Aggregation은 실선에 빈 다이아몬드로 나타낸다.



* **Composigiton ( 합성 )**

  ![img](https://www.nextree.co.kr/content/images/2021/01/--19-Composition1.png)

  **Composigiton은 클래스 연관관계에서 강한 결합의 관계를 의미**

  **참조하는 클래스의 라이프 사이클이 종속적이다.**

  다이어그램으로는 실선에 채워져있는 다이아몬드로 표시한다.



## 유스케이스( use case )

시스템과 사용자의 상호작용을 다이어그램으로 표현한 것



### 목적

* 사용자의 관점에서 시스템의 서비스 혹은 기능 및 그와 관련한 외부 요소를 보여주기 위해
* 사용자가 시스템 내부에 있는 기능 중에 어떤 기능을 사용 할 수 있는지 나타내기 위해
* 고객과 개발자가 요구사항에 대한 의견을 조율하기 위해
* 사용자랑 시스템사이에 관계를 나타내기 위해



### 구성요소 및 예시

* **System ( 시스템 )**

  ![img](https://t1.daumcdn.net/cfile/tistory/21214C4E594FDAA112)

  만들고자 하는 프로그램을 나타낸다.

  유스케이스들을 둘러싼 사각형 틀로 시스템 명칭을 안쪽 상단에 작성한다.



* **Actor ( 액터 )**

  ![img](https://t1.daumcdn.net/cfile/tistory/2550854E594FDAA108)

  시스템의 외부에 있고 시스템과 상호작용을 하는 사람, 시스템을 의미한다.

  원과 선을 조합하여 사람모양으로 표현한다.

  액터명은 위나 아래에 표시하며 액터의 역할을 작성한다.



* **Usecase ( 유스케이스 )**

  ![img](https://t1.daumcdn.net/cfile/tistory/23218C4E594FDAA225)

  사용자 입장에서 바라본 시스템의 기능

  시스템이 액터에게 제공해야 하는 기능으로 시스템의 요구사항을 의미한다.

  타원으로 표시하고 안쪽에 유스케이스명을 작성한다.

  유스케이스명은 "~한다"와 같이 동사로 표현한다.



* **Relation ( 관계 )**

  연관(Association), 의존(Dependency), 일반화(Generalization)이 있으며 의존관계는 포함(Include), 확장(Extend)로 나눠진다.

  * **연관관계(Association)**

    ![img](https://t1.daumcdn.net/cfile/tistory/2614D049594FD59419)

    유스케이스와 액터간의 상호작용이 있음을 표현

    유스케이스와 액터를 실선으로 연결

    

  * **의존(Dependency)**

    ![img](https://t1.daumcdn.net/cfile/tistory/256EC949594FD5951C)

    포함 관계(Include)는 하나의 유스케이스가 다른 유스케이스의 실행을 전제로 할 때 형성되는 관계

    포함되는 유스케이스는 포함하는 유스케이스를 실행하기 위해 반드시 실행되어야 하는 경우에 적용

    ![img](https://t1.daumcdn.net/cfile/tistory/26341449594FD59535)

    확장 관계(Extend)는 확장 기능 유스케이스와 확장 대상 유스케이스 사이에 형성 되는 관계

    확장 대상 유스케이스를 수행 할 때 특정 조건에 따라 확장 기능 유스케이스를 수행하는 경우에 적용

    

  * **일반화 관계(Generalization)**

    ![img](https://t1.daumcdn.net/cfile/tistory/22262A49594FD59636)

    일반화 관계(Generalization)는 유사한 유스케이스 또는 액터를 모아 추상화한 유스케이스 또는 액터와 연결시켜 그룹을 만들어 이해도를 높이기 위한 관계

    구체적인 유스케이스에서 추상적인 유스케이스 방향으로 끝부분이 삼각형으로 표현된 화살표를 실선으로 연결하여 표현한다.



## 순차(sequence)











## 출처

> https://www.nextree.co.kr/p6753/
>
> https://brownbears.tistory.com/577
>
> https://googry.tistory.com/2