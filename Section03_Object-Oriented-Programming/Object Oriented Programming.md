# Object Oriented Programming (OPP)



## Basics of Object Oriented Programming 

*** Learning Goals **

1. Eclipse IDE를 사용해 Java project를 생성하고 간단한 프로그램을 작동시키기
2. 객체지향 프로그래밍 원칙의 캡슐화(Encapsulation), 상속(Inheritance)를 이해하기
3. 이 두가지 원칙을 적용하기



*** 왜 통합 개발 환경(IDE)가 필요한가? **

1. 다른 폴더에 존재하는 다수의 소스코드를 컴파일 할 때 (with Maven/Ant)
   - 우리는 다른 폴더 또는 패키지에 존재하거나, 다양한 소스파일에 적용되는 프로젝트에 대한 컴파일을 시도한다. 이 때 발생하는 Classpath 문제를 다루는 것,  컴파일 하는 동안 모든 dependency가 사용되도록 하는 것은 매우 어렵다.
2. Syntax Highlighting
   - 컴파일 타임 에러 탐지기, 자동완성기를 이용해 효율적이고 빠르게 개발 가능
3. 기타
   - 에러 탐지, 팀과 협업, 코드의 리팩토링과 구조화를 쉽고 간편하게 함



*** 객체 지향 프로그래밍의 4가지 원칙 **

- Encapsulation(캡슐화)
- Inheritance(상속)
- Polymorphism(다형성)
- Abstraction(추상화)



### Encapsulation

- 캡슐화 : Class를 생성하고 정의함

  - Attribute을 이용해 구조화

  - Method를 제공해 기능화

Java는 클래스를 사용함으로써 캡슐화를 지원함. 클래스는 구조화를 위한 속성, 기능 설명을 위한 메소드를 포함.

![01](./img/03_01.png)

`ex)` Student 클래스 - 속성: `majorSubject`, `minorSubject`, `courseList`

​									- 메소드 : `joinCourse`, `dropCourse`



- Java는 Constructor라는 특별한 메소드를 사용함으로써 Class의 구체적인 Instance/Object를 생성함
  - return 타입 없음
  - 클래스의 이름을 전달
  - 객체의 특정 속성을 인스턴스화

![01](./img/03_02.png)



- 각각의 Class는 내포된 Default Constructor가 존재함

이러한 생성자들은 속성들을 효율적으로 초기화 시킴



### Inheritance

- 상속 : Inheritance Hierarchy를 이용하여 Data Structure의 재사용을 가능하게 함
  - Super-class의 속성에 접근하여 이 구조를 재사용
  - Super-class의 메소드에 접근하여 이 기능을 재사용

- `ex)` 

  - Each car is a vehicle.

  - Each motorbike is a vehicle.

    -> Both share structural information e.g. wheels.

    -> Both share functionality e.g. move().

    -> Both both can have additional attributes and functionality.

    

- Java는 Sub-class를 정의하고 Super-class를 연관시킴으로써 상속을 지원함
- `extends` 키워드를 이용해 상속시킴

![1568481776256](./img/03_03.png)



- Sub-class는 Super-class 생성자에게 초기화를 위임함
- Sub-class 안에  `super()`을 호출하여 값들을 Super-class로 전달함

![1568482594149](./img/03_04

.png)



- Sub-class는 (non-private한) Super-class의 속성과 메소드에 접근 가능
- 만약 Sub-class가 메소드를 정의하고 있지 않다면, 컴파일러는 자동으로 Super-class의 Hierarchy를 검색함

![1568483066553](./img/03_04.png)



- 상속 관계는 한 방향으로만 이루어짐
  - <u>Every</u> student is a person.
  - But, not <u>every</u> person is a student.

