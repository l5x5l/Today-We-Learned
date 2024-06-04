https://www.inflearn.com/pages/infcon-2023-tech-oopfp

# OOP(Object-Oriented Programming)

## WHAT

- 프로그램을 객체들의 집합으로 무엇을 어떻게 할 것인지에 집중하여 결과를 만들어내는 명령형 프로그래밍 방법

    - **객체** 
     
        - **[사전적 의미](https://yeo0616.tistory.com/211)** : 실생활에서 우리가 인식할 수 있는 사물이나 개념으로 속성과 동작을 갖고 있다.
      
            - **속성** : 모델, 제조사, 색상 / **동작** : 주행, 가속, 제동
            
        - **[컴퓨터 과학](https://ko.wikipedia.org/wiki/%EA%B0%9D%EC%B2%B4_(%EC%BB%B4%ED%93%A8%ED%84%B0_%EA%B3%BC%ED%95%99))** : 클래스에서 정의한 것을 메모리에 할당된 것으로 데이터나 식별자에 의해 참조되는 공간

            - **[클래스](https://ko.wikipedia.org/wiki/%ED%81%B4%EB%9E%98%EC%8A%A4_(%EC%BB%B4%ED%93%A8%ED%84%B0_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D))** : 객체를 생성하기 위해 변수와 메소드를 정의하는 일종의 틀 

        - 각 객체는 속성과 함께 관련 동작을 갖고, 서로 상호작용하며 프로그램을 구성한다. 
    
            - **[프로그램](https://ko.wikipedia.org/wiki/%EC%BB%B4%ED%93%A8%ED%84%B0_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8)** : 컴퓨터에서 실행될 때 특정 작업을 수행하는 일련의 명령어들의 모음
    
    - **[객체와 인스턴스의 차이점](https://velog.io/@0sunset0/%ED%81%B4%EB%9E%98%EC%8A%A4-%EA%B0%9D%EC%B2%B4-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4-%EC%B0%A8%EC%9D%B4)**
    
        - **[인스턴스](https://f-lab.kr/insight/understanding-class-and-instance)** : 클래스에 의해 생성된 실체로, 클래스의 정의를 바탕으로 실제 메모리 상에 할당된 객체를 의미한다.

> [객체지향 프로그래밍](https://pienguin.tistory.com/entry/JAVA-%EC%9E%90%EB%B0%94%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80)은 객체를 만들기 위해 설계도인 클래스를 작성하고, 부품에 해당하는 객체들을 만든 후, 이것들을 하나씩 조립 및 연결하여 전체 프로그램을 완성하는 것이다.

<br/>

## [객체 지향 프로그래밍의 장점](https://www.codestates.com/blog/content/%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8A%B9%EC%A7%95)

1. 코드의 재사용을 통해 반복적인 코드를 최소화하고, 코드를 최대한 간결하게 표현할 수 있다.

    - **WHY** : 코드를 객체 단위로 구성하므로, 같은 기능을 하는 코드를 여러 번 작성할 필요가 없다.

2. 코드의 변경을 최소화하고 유지보수를 하는 데 유리하다.

    - **WHY** :  각 객체가 독립적으로 작동하므로, 코드의 유지보수가 쉬워진다.

<br/>

## [객체 지향 프로그래밍의 단점](https://velog.io/@koyo/development-common-sense-0#%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EC%9D%98-%EC%9E%A5%EB%8B%A8%EC%A0%90%EC%9D%84-%EA%B0%84%EB%8B%A8%ED%95%98%EA%B2%8C-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)

1. 처리속도가 상대적으로 느리다.

2. 객체가 많으면 용량이 커질 수 있다.

3. 설계시 많은 시간과 노력이 필요하다.

<br/>

## [객체지향 프로그래밍의 특징](https://www.codestates.com/blog/content/%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8A%B9%EC%A7%95)

### 추상화(Abstration)

- **사전적 의미** : 사물이나 표상을 어떤 성질, 공통성, 본질에 착안하여 그것을 추출하여 파악하는 것

- 불필요한 세부 사항들은 제거하고 가장 본질적이고 공통적인 부분만을 추출하여 표현하는 것

> 추상화는 객체의 공통적인 속성과 동작을 추출하여 정의하는 과정이다.

![image](https://github.com/Android-Master-Class/Today-We-Learned/assets/96613859/cacae68f-dc3a-4aa9-872c-6ebd8cfd081e)

- **HOW** : 추상 클래스와 인터페이스를 통해 어떤 객체가 수행해야 하는 핵심적인 역할만을 규정해두고, 실제적인 구현은 해당 인터페이스를 구현하는 각각의 객체들에서 하도록 프로그램을 설계하는 것

```kotlin
// 자동차와 오토바이의 공통적인 기능 추출하여 이동 수단 인터페이스에 정의
interface Vehicle {
    abstract fun start() // abstract 키워드 생략 가능
    fun moveForward()
    fun moveBackward()
}

class Car : Vehicle {
    override fun start() {
        println("자동차가 시동을 건다")
    }

    override fun moveForward() {
        println("자동차가 앞으로 전진한다")
    }

    override fun moveBackward() {
        println("자동차가 뒤로 후진한다")
    }
}

class MotorBike : Vehicle {
    override fun start() {
        println("오토바이가 시동을 건다")
    }

    override fun moveForward() {
        println("오토바이가 앞으로 전진한다")
    }

    override fun moveBackward() {
        println("오토바이가 뒤로 후진한다")
    }
}

fun main() {
    val car = Car()
    car.start() // 자동차가 시동을 건다
    car.moveForward() // 자동차가 앞으로 전진한다
    car.moveBackward() // 자동차가 뒤로 후진한다

    val motorBike = MotorBike()
    motorBike.start() // 오토바이가 시동을 건다
    motorBike.moveForward() // 오토바이가 앞으로 전진한다
    motorBike.moveBackward() // 오토바이가 뒤로 후진한다
}
```

**[abstract class와 interface의 차이점](https://f-lab.kr/insight/difference-between-java-interface-and-abstract-class?gad_source=1&gclid=CjwKCAjwjeuyBhBuEiwAJ3vuoQyN02uAV3WOGXPyZj3odqi4rGWjgAphwhdUFZLEIl-IJqmaqvJL6hoC_UEQAvD_BwE)**

- 둘 다 객체 지향 프로그래밍의 추상화와 다형성을 구현하는 데 사용된다.

- **abstract class**

    - 하나 이상의 추상 메소드를 포함할 수 있는 클래스로, 구현 코드를 포함한 일반 메소드도 가질 수 있다.

    - 단일 상속만을 지원한다.
    
    - 공통된 기능을 재사용하면서도 일부 메소드의 구현을 자식 클래스에 위임하고자 할 때 주로 사용된다.

- **interface**
    
    - 구현 코드 없이 선언만 있는 메소드의 집합
    
    - 다중 구현을 지원하여 여러 인터페이스를 동시에 구현할 수 있다.
    
    - 애플리케이션의 다양한 구현체간의 호환성을 보장하는 계약 역할을 한다.

<br/>

### 상속(Inheritance)

- 상위 클래스로부터 확장된 여러 개의 하위 클래스들이 모두 상위 클래스의 속성과 기능들을 간편하게 사용할 수 있다.

- 반복적인 코드를 최소화하고 공유하는 속성과 기능에 간편하게 접근하여 사용할 수 있도록 한다.

> 상속은 하나의 자식 클래스가 상위에 있는 부모 클래스의 속성과 동작을 물려받는 개념이다.

**BEFORE**

![image](https://github.com/Android-Master-Class/Today-We-Learned/assets/96613859/3b5b7b61-12b3-4f1e-a58d-0289b5c8c91f)

```kotlin
class Car {
    var model = ""
    var color = ""
    var wheels = 0
    
    // Car 클래스 고유의 속성
    var isConvertible = false
    
    fun moveForward() {
        println("앞으로 전진한다")
    }
    
    fun moveBackward() {
        println("뒤로 후진한다")
    }
    
    // Car 클래스 공유의 기능
    fun openWindow() {
        println("모든 창문을 연다")
    }
}
```
```kotlin
class MotorBike {
    var model = ""
    var color = ""
    var wheels = 0
    
    // MotorBike 클래스 고유의 속성
    var isRaceable = false
    
    fun moveForward() {
        println("앞으로 전진한다")
    }
    
    fun moveBackward() {
        println("뒤로 후진한다")
    }
    
    // MotorBike 클래스 공유의 기능
    fun stunt() {
        println("오토바이로 묘기를 부린다")
    }
}
```

**AFTER**
![image](https://github.com/Android-Master-Class/Today-We-Learned/assets/96613859/f5697441-8443-43d1-b109-caab4e43fa80)

```kotlin
open class Vehicle() {
    var model = ""
    var color = ""
    var wheels = 0

    open fun moveForward() {
        println("전진한다")
    }

    fun moveBackward() {
        println("후진한다")
    }
}

class Car() : Vehicle() {
    var isConvertible = false

    fun openWindow() {
        println("모든 창문을 연다")
    }
}

class MotorBike : Vehicle() {
    var isRaceable = false

    // 메소드 오버라이딩을 사용하여 상위 클래스의 기능을 재정의
    override fun moveForward() {
        println("오토바이가 앞으로 전진한다")
    }

    fun stunt() {
        println("오토바이가 묘기를 부린다")
    }
}

fun main() {
    val car = Car()
    val motorBike = MotorBike()

    car.model = "테슬라"
    car.color = "빨강색"

    println(car.color) // 빨강색
    println(car.model) // 테슬라

    car.moveForward() // 전진한다
    motorBike.moveForward() // 오토바이가 앞으로 전진한다

    car.openWindow() // 모든 창문을 연다
    motorBike.stunt() // 오토바이가 묘기를 부린다
}
```

**[오버로딩과 오버라이딩의 차이점](https://f-lab.kr/insight/inheritance-overloading-overriding?gad_source=1&gclid=CjwKCAjwjeuyBhBuEiwAJ3vuoZqzr4pishKz8E06vE1lSHB5DSywS2zsUJ7N0_w_AGOjeJLZwHSycxoCxXUQAvD_BwE)**

- **오버로딩** : 같은 이름의 메소드를 매개변수의 타입이나 개수를 다르게 하여 여러 번 정의하는 것

- **오버라이딩** : 상속받은 메소드의 내용을 자식 클래스에서 변경하는 것

<br/>

### 다형성(polymorphism)

- 어떤 객체의 속성이나 기능이 상황에 따라 여러 가지 형태(역할)를 가질 수 있는 성질

![image](https://github.com/Android-Master-Class/Today-We-Learned/assets/96613859/a681d1a6-28d9-43b0-a360-801c6c598dff)

> 다형성은 한 타입(상위 클래스 타입)의 참조변수를 통해 여러 타입(하위 클래스)의 객체를 참조할 수 있도록 만드는 것이다.

**BEFORE**
```kotlin
class Driver {
    fun drive(car: Car) {
        car.moveForward()
        car.moveBackward()
    }
    
    fun drive(motorBike: MotorBike) {
        motorBike.moveForward()
        motorBike.moveBackward()
    }
}

fun main() {
    val car = Car()
    val motorBike = MotorBike()
    val driver = Driver()
    
    driver.drive(car)
    driver.drive(motorBike)
}
```
- 하나의 객체가 다른 객체의 속성과 기능에 접근하여 어떤 기능을 사용할 때, `의존하다`라고 표현한다.
- 즉, Driver 클래스와 다른 두 개의 클래스가 서로 직접적인 관계를 가지고 있는데, 이러한 상황은 객체들 간의 결합도가 높다.
    
    - **결합도가 높으면** : 변경하고 검토해야 하는 모듈의 수가 많아져서 유지보수하기 어렵다.
      
        - **[모듈](https://velog.io/@ruddnjs5816/%EB%AA%A8%EB%93%88Module%EA%B3%BC-%EB%AA%A8%EB%93%88%ED%99%94Modularization)** : 프로그램을 구성하는 시스템을 기능 단위로 독립적인 부분으로 분리한 것

        - **[결합도](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EA%B2%B0%ED%95%A9%EB%8F%84-%EC%9D%91%EC%A7%91%EB%8F%84-%EC%9D%98%EB%AF%B8%EC%99%80-%EB%8B%A8%EA%B3%84-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EC%89%BD%EA%B2%8C-%EC%A0%95%EB%A6%AC#%EA%B2%B0%ED%95%A9%EB%8F%84coupling)** : 모듈 간의 상호 의존 정도
  
            - **응집도** : 한 모듈 내의 구성 요소들 간의 연관 정도
          
            - **핵심** : 좋은 소프트웨어는 결합도를 낮춰 모듈 간의 독립성을 높이고, 한 모듈에 하나의 기능(책임)과 관련있는 속성과 동작을 정의하여 높은 응집도를 유지하는 것이다.  

    - **해결책** : 역할과 구현을 구분하여 객체들 간의 직접적인 결합을 피하고, 느슨한 관계 설정을 통해 보다 유연하고 변경이 용이한 프로그램을 설계해야한다.

**AFTER**
```kotlin
interface Vehicle {
    fun moveForward()
    fun moveBackward()
}

class Car : Vehicle {
    override fun moveForward() {
        println("자동차가 앞으로 전진한다")
    }

    override fun moveBackward() {
        println("자동차가 뒤로 후진한다")
    }
}

class MotorBike : Vehicle {
    override fun moveForward() {
        println("오토바이가 앞으로 전진하다")
    }

    override fun moveBackward() {
        println("오토바이가 뒤로 후진한다")
    }
}

class Driver {
    fun drive(vehicle: Vehicle) {
        vehicle.moveForward()
        vehicle.moveBackward()
    }
}

fun main() {
    val car: Vehicle = Car() // 높은 결합도
    val motorBike: Vehicle = MotorBike() // 높은 결합도
    val driver = Driver()
    
    // 자동차가 앞으로 전진한다
    // 자동차가 뒤로 후진한다
    driver.drive(car) 

    // 오토바이가 앞으로 전진하다  
    // 오토바이가 뒤로 후진한다
    driver.drive(motorBike) 
}
```
- **결과** : 각각의 클래스 내부의 변경이나 다른 객체가 새롭게 교체되는 것을 신경 쓰지 않아도 인터페이스에만 의존하여 수정이 있을 때마다 코드 변경을 하지 않아도 된다.


- **BUT** : 여전히 실행 클래스의 코드에서 객체를 생성할 때, Vehicle 객체가 Car과 MotorBike 객체에 직접적으로 의존하고 있어서, 해당 객체를 다른 객체로 변경할 시 코드의 변경이 불가피하다.
-  **HOW** : 의존성 주입

<br/>

### 캡슐화(Encapsulation)

![image](https://github.com/Android-Master-Class/Today-We-Learned/assets/96613859/19e6bb5e-57b1-42c9-9ea6-9eed1a700649)

- 클래스 안에 서로 연관있는 속성과 기능들을 하나의 캡슐로 만들어 데이터를 외부로부터 보호하는 것

- **WHY**

    - **데이터 보호(data protection)** : 외부로부터 클래스에 정의된 속성과 기능들을 보호
  
    - **데이터 은닉(data hiding)** : 내부의 동작을 감추고 외부에는 필요한 부분만 노출


- **목적** : 외부로부터 클래스에 정의된 속성과 기능들을 보호하고, 필요한 부분만 외부로 노출될 수 있도록 하여 각 객체 고유의 독립성과 책임 영역을 안전하게 지키는 것

<br/>

**해당 클래스나 멤버들을 외부에서 접근하지 못하도록 접근을 제한하는 방법**

1. 접근제어자

```kotlin
package package1

open class SuperClass {
    private val a = 1
    protected val b = 2
    internal val c = 3
    public val d = 4

    open fun printEach() {
        println(a)
        println(b)
        println(c)
        println(d)
    }
}

fun main() {
    val superClass = SuperClass()

    // private 멤버에 접근 불가능(에러)
    println(superClass.a)
    // protected 멤버에 접근 불가능(에러)
    println(superClass.b)
    println(superClass.c) // 3
    println(superClass.d) // 4
}
```
```kotlin
package package2

import package1.SuperClass

class SubClass : SuperClass() {
    override fun printEach() {
        // private 멤버에 접근 불가능(에러) 
        println(a)
        println(b)
        println(c)
        println(d)
    }
}

fun main() {
    val parent = SuperClass()

    // private 멤버에 접근 불가능(에러)
    println(parent.a)
    // protected 멤버에 접근 불가능(에러)
    println(parent.b)
    println(parent.c)
    println(parent.d)
}
```

2. getter/setter 메소드

**BEFORE**
- Drvier 클래스가 Car 클래스의 세부적인 내부 로직을 알고 있다. 즉, 객체 간의 결합도가 높다.
```kotlin
class Car(private var name: String, private var color: String) {
    fun startEngine() {
        println("시동을 건다")
    }
    
    fun moveForward() {
        println("자동차가 앞으로 전진한다")
    }
    
    fun openWindow() {
        println("모든 창문을 연다")
    }
}

class Driver(private val name: String, private val car: Car) {
    fun drive() {
        car.startEngine()
        car.moveForward()
        car.openWindow()
    }
}

fun main() {
    val car = Car("테슬라 모델X", "레드")
    val driver = Driver("김코딩", car)

    // 시동을 건다
    // 자동차가 앞으로 전진한다
    // 모든 창문을 연다
    driver.drive()
}
```

**AFTER**
- Car 클래스와 관련된 기능들은 온전히 Car 클래스에서만 관리되도록 하고, 불필요한 내부 동작의 노출을 최소화한다.
```kotlin
class Car(private var name: String, private var color: String) { 
    private fun startEngine() {
        println("시동을 건다")
    }

    private fun moveForward() {
        println("자동차가 앞으로 전진한다")
    }

    private fun openWindow() {
        println("모든 창문을 연다")
    }
    
    fun operate() {
        startEngine()
        moveForward()
        openWindow()
    }
}

class Driver(private val name: String, private val car: Car) {
    fun getName() {
        return name
    }
    
    fun drive() {
        car.operate()
    }
}

fun main() {
    val car = Car("테슬라 모델X", "레드")
    val driver = Driver("김코딩", car)

    // 시동을 건다
    // 자동차가 앞으로 전진한다
    // 모든 창문을 연다
    driver.drive()
}
```

<br/>

- - -

# [객체 지향 원칙](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%EC%84%A4%EA%B3%84%EC%9D%98-5%EA%B0%80%EC%A7%80-%EC%9B%90%EC%B9%99-SOLID)

- SOLID 원칙은 총 5가지 원칙으로 구성되어 있다.

- **장점** : 코드를 확장하고 유지 보수 관리하기가 더 쉬워지며, 불필요한 복잡성을 제거해 리팩토링에 소요되는 시간을 줄임으로써 프로젝트 개발의 생산성을 높일 수 있다.

**5가지 원칙이 필수인가요?**

- 프로젝트에 적용할 원칙의 수는 코드의 구성에 따라 다르다.
- 각 원칙은 특정 문제를 해결하기 위한 지침일 뿐이며, 만일 코드에 해당 문제가 없으면 원칙을 적용할 이유가 없다.

## 1. SRP(Single Responsibility Principle)

- 단일 책임 원칙은 클래스(객체)는 단 하나의 책임(기능)만 가져야 한다는 원칙이다.

- 즉, 하나의 클래스는 하나의 기능만을 담당하여 하나의 책임을 수행하는 데 집중되도록 클래스를 따로따로 여러개 설계하라는 원칙이다.

- **WHY** : 만일 하나의 클래스에 기능(책임)이 여러개 있다면 기능 변경(수정)이 일어났을때 수정해야할 코드가 많아진다.

<br/>

**BEFORE**
- 서버에 데이터를 보내는 동작과 작업 결과를 파일에 기록하는 동작은 서로 관련된 동작이 아니다.
```kotlin
class EmployeeManagement {
    // Create 작업을 담당하는 CRUD 메소드
    fun addEmployee(employee: String) {
        if (employee == "") {
            postServer(employee) // 서버에 직원 정보를 보냄
            logResult("[LOG] EMPLOYEE ADDED") // 로그 출력
        } else {
            logResult("[ERROR] NAME MUST NOT BE EMPTY")
        }
    }

    // 서버에 데이터를 전달하는 메소드
    fun postServer(employees: String) {}

    // 로그를 출력하는 메소드
    fun logResult(message: String) {
        println(message) // 로그를 콘솔에 출력
        writeToFile(message) // 로그 내용을 로그 파일에 저장
    }

    // 파일에 내용을 저장하는 메소드
    fun writeToFile(msg: String) {}
}
```

**AFTER**
- 로깅만을 담당하는 클래스를 따로 분리하고, EmployeeManagement 클래스에서 합성하여 사용한다.

    - **[합성](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5%EC%9D%98-%EC%83%81%EC%86%8D-%EB%AC%B8%EC%A0%9C%EC%A0%90%EA%B3%BC-%ED%95%A9%EC%84%B1Composition-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0)** : 필드로 클래스의 인스턴스를 참조하게 만드는 설계

```kotlin
class EmployeeManagement {
    private val logger = Logger() // 합성

    // Create 작업을 담당하는 CRUD 메소드
    fun addEmployee(employee: String) {
        if (employee == "") {
            postServer(employee) // 서버에 직원 정보를 보냄
            logger.logResult("[LOG] EMPLOYEE ADDED") // 로그 출력
        } else {
            logger.logResult("[ERROR] NAME MUST NOT BE EMPTY")
        }
    }

    // 서버에 데이터를 전달하는 메소드
    fun postServer(employees: String) {}
}

class Logger {
    // 로그를 출력하는 메소드
    fun logResult(message: String) {
        println(message) // 로그를 콘솔에 출력
        writeToFile(message) // 로그 내용을 로그 파일에 저장
    }

    // 파일에 내용을 저장하는 메소드
    fun writeToFile(msg: String) {}
}
```


## 2. OCP(Open Closed Principle)

- 개방 폐쇄 원칙은 클래스는 확장에 열려있어야 하며, 수정에는 닫혀있어야 한다는 원칙이다.
  
    - **확장에 열려있다** : 새로운 변경 사항이 발생했을 때 유연하게 코드를 추가함으로써 큰 힘을 들이지 않고 애플리케이션의 기능을 확장할 수 있다.
  
    - **변경에 닫혀있다** : 새로운 변경 사항이 발생했을 때 객체를 직접적으로 수정을 제한한다.

- 추상화 사용을 통한 관계 구축을 권장한다는 의미이다.

<br/>

**BEFORE**
- 고양이와 개 외에 양이나 사자를 추가하면 각 객체의 필드 변수에 맞게 when문을 분기하여 구성해줘야 한다.
```kotlin
class Animal(val type: String)

// 동물 타입을 받아 각 동물에 맞춰 울음소리를 내게 하는 클래스 모듈
class HelloAnimal {
    fun hello(animal: Animal) {
        when (animal.type) {
            "Cat" -> println("냐옹")
            "Dog" -> println("멍멍")
            else -> println("알 수 없는 동물")
        }
    }
}

fun main() {
    val hello = HelloAnimal()

    val cat = Animal("Cat")
    val dog = Animal("Dog")

    hello.hello(cat) // 냐옹
    hello.hello(dog) // 멍멍
}
```

**AFTER**
- 추상화 클래스를 구성하고 이를 상속하여 확장시키는 관계로 형성한다.
```kotlin
abstract class Animal {
    abstract fun speak()
}

class Cat : Animal() {
    override fun speak() {
        println("냐옹")
    }
}

class Dog : Animal() {
    override fun speak() {
        println("멍멍")
    }
}

class Sheep : Animal() {
    override fun speak() {
        println("매에에")
    }
}

class Lion : Animal() {
    override fun speak() {
        println("어흥")
    }
}

// 기능 확장으로 인한 클래스가 추가되어도, 더이상 수정할 필요가 없어진다 (closed)
class HelloAnimal {
    fun hello(animal: Animal) {
        animal.speak()
    }
}

fun main() {
    val hello = HelloAnimal()

    val cat: Animal = Cat()
    val dog: Animal = Dog()

    val sheep: Animal = Sheep()
    val lion: Animal = Lion()

    hello.hello(cat) // 냐옹
    hello.hello(dog) // 멍멍
    hello.hello(sheep) // 매에에
    hello.hello(lion) // 어흥
}
```


## 3. LSP(Liskov Substitution Principle)
- 리스코프 치환 원칙은 서브 타입은 언제나 기반(부모) 타입으로 교체할 수 있어야 한다는 원칙이다.

- 다형성 원리를 이용하기 위한 원칙

-  다형성의 특징을 이용하기 위해 상위 클래스 타입으로 객체를 선언하여 하위 클래스의 인스턴스를 받으면, 업캐스팅된 상태에서 부모의 메소드를 사용해도 동작이 의도대로 흘러가야 하는 것을 의미하는 것

<br/>

**BEFORE**
- Fish 물고기 클래스에 Animal 추상 클래스를 상속하면, 물고기는 행할 수 없는 speak() 메소드를 구현해야 한다.
```kotlin
abstract class Animal {
    abstract fun move()
    abstract fun speak()
}

class Cat : Animal() {
    override fun move() {
        println("고양이가 움직이다.")
    }

    override fun speak() {
        println("냐옹")
    }
}

class Dog : Animal() {
    override fun move() {
        println("개가 움직이다.")
    }

    override fun speak() {
        println("멍멍")
    }
}

class Fish : Animal() {
    override fun move() {
        println("물고기가 헤엄치다.")
    }

    override fun speak() {
        throw Exception("물고기는 말할 수 없다.")
    }
}
```

**AFTER**
- 인터페이스로 분리하는 작업을 통해 수정해야 한다.
```kotlin
abstract class Animal {
    abstract fun move()
}

interface Speakable {
    fun speak()
}

class Cat : Animal(), Speakable {
    override fun move() {
        println("고양이가 움직이다.")
    }

    override fun speak() {
        println("냐옹")
    }
}

class Dog : Animal(), Speakable {
    override fun move() {
        println("개가 움직이다.")
    }

    override fun speak() {
        println("멍멍")
    }
}

class Fish : Animal() {
    override fun move() {
        println("물고기가 헤엄치다.")
    }
}
```


## 4. ISP(Interface Segregation Principle)

- 인터페이스 분리 원칙은 인터페이스를 각각 사용에 맞게 끔 잘게 분리해야 한다는 원칙이다.

- 인터페이스의 단일 책임을 강조하는 것으로 인터페이스 분리를 통해 설계하는 원칙이다.

- 인터페이스를 사용하는 클라이언트를 기준으로 분리함으로써, 클라이언트의 목적과 용도에 적합한 인터페이스 만을 제공하는 것이 목표이다.

<br/>

**BEFORE**
- 최신 기종 스마트폰 뿐만 아니라 구형 기종 스마트폰 클래스도 다뤄야 할 상황처럼 갤럭시 S3 클래스를 구현해야 한다면 무선 충전, 생체인식과 같은 기능은 포함되어 있지 않다.
```kotlin
interface ISmartPhone {
    fun call(number: String)
    fun message(number: String, text: String)
    fun wirelessCharge()
    fun AR()
    fun biometrics()
}

class S21 : ISmartPhone {
    override fun call(number: String) { /*...*/ }

    override fun message(number: String, text: String) { /*...*/ }

    override fun wirelessCharge() { /*...*/ }

    override fun AR() { /*...*/ }

    override fun biometrics() { /*...*/ }
}

class S3 : ISmartPhone {
    override fun call(number: String) { /*...*/ }

    override fun message(number: String, text: String) { /*...*/ }

    override fun wirelessCharge() {
        println("지원하지 않는 기능입니다.")
    }

    override fun AR() {
        println("지원하지 않는 기능입니다.")
    }

    override fun biometrics() {
        println("지원하지 않는 기능입니다.")
    }
}
```

**AFTER**
- 각각의 기능에 맞게 인터페이스를 잘게 분리하도록 구성한다.
```kotlin
interface IPhone {
    fun call(number: String) // 통화 기능
    fun message(number: String, text: String) // 문제 메세지 전송 기능
}

interface WirelessChargable {
    fun wirelessCharge() // 무선 충전 기능
}

interface ARable {
    fun AR() // 증강 현실(AR) 기능
}

interface Biometricsable {
    fun biometrics() // 생체 인식 기능
}

class S21 : IPhone, WirelessChargable, ARable, Biometricsable {
    override fun call(number: String) { /*...*/ }

    override fun message(number: String, text: String) { /*...*/ }
    
    override fun wirelessCharge() { /*...*/ }
    
    override fun AR() { /*...*/ }
    
    override fun biometrics() { /*...*/ }
}

class S3 : IPhone {
    override fun call(number: String) { /*...*/ }
    
    override fun message(number: String, text: String) { /*...*/ }
}
```


## 5. DIP(Dependency Inversion Principle)

- 의존성 역전 원칙은 어떤 Class를 참조해서 사용해야하는 상황이 생긴다면, 그 Class를 직접 참조하는 것이 아니라 그 대상의 상위 요소(추상 클래스 or 인터페이스)로 참조하라는 원칙이다.

- 구현 클래스에 의존하지 말고, 인터페이스에 의존하라는 뜻이다.

**BEFORE**
- 이미 완전하게 구현된 하위 모듈을 의존하고 있다.
```kotlin
class OneHandSword(val name: String, val damage: Int) {
    fun attack(): Int {
        return damage
    }
}

class TwoHandSword { /*...*/ }

class BattleAxe { /*...*/ }

class WarHammer { /*...*/ }

class Character(
    val name: String,
    var health: Int,
    var weapon: OneHandSword // 의존 저수준 객체
) {

    fun attack(): Int {
        return weapon.attack()
    }

    fun changeWeapon(newWeapon: OneHandSword) {
        weapon = newWeapon
    }

    fun getInfo() {
        println("이름: $name")
        println("체력: $health")
        println("무기: $weapon")
    }
}
```

**AFTER**
- 구체 모듈을 의존하는 것이 아닌 추상적인 고수준 모듈을 의존하도록 리팩토링 한다.
```kotlin
interface Weaponable {
    fun attack(): Int
}

class OneHandSword(val name: String, val damage: Int) : Weaponable {
    override fun attack(): Int {
        return damage
    }
}

class TwoHandSword : Weaponable { /*...*/ }

class BattleAxe : Weaponable { /*...*/ }

class WarHammer : Weaponable { /*...*/ }

class Character(val name: String, var health: Int, var weapon: Weaponable) {

    fun attack(): Int {
        return weapon.attack()
    }

    fun changeWeapon(newWeapon: Weaponable) {
        weapon = newWeapon
    }

    fun getInfo() {
        println("이름: $name")
        println("체력: $health")
        println("무기: $weapon")
    }
}
```