https://incheol-jung.gitbook.io/docs/study/kotlin-in-action/1

## 코틀린

1. 간결하고 실용적이며, 자바 코드와의 상호운용성을 중시하는 정적 타입 지정 언어

- **[상호운용성](https://ko.wikipedia.org/wiki/%EC%83%81%ED%98%B8%EC%9A%B4%EC%9A%A9%EC%84%B1)** : 하나의 시스템이 다른 시스템과 아무런 제약없이 서로 호환되어 사용할 수 있는 성질

- **정적 타입 지정 언어** : 모든 프로그램 구성 요소의 타입을 컴파일 시점에 알 수 있고, 프로그램 안에서 객체의 필드나 메소드를 사용할 때마다 컴파일러가 타입을 검증해주는 언어

    - **[동적 타입 지정 언어](https://velog.io/@hahan/%EC%A0%95%EC%A0%81%ED%83%80%EC%9E%85-%EC%96%B8%EC%96%B4-vs-%EB%8F%99%EC%A0%81%ED%83%80%EC%9E%85-%EC%96%B8%EC%96%B4)** : 타입과 관계없이 모든 값을 변수에 넣을 수 있고, 메소드나 필드 접근에 대한 검증이 런타임에 일어나는 언어

    - **[컴파일 시점(Compile Time)](https://yeko90.tistory.com/entry/compile-time%EC%BB%B4%ED%8C%8C%EC%9D%BC-%ED%83%80%EC%9E%84-vs-runtime%EB%9F%B0%ED%83%80%EC%9E%84-%EC%B0%A8%EC%9D%B4)** : 소스 코드를 컴퓨터가 이해하고 실행할 수 있는 기계어로 변환하는 과정

        - **[런타임 시점](https://ko.wikipedia.org/wiki/%EB%9F%B0%ED%83%80%EC%9E%84)** : 컴파일 과정을 마친 프로그램이 실행되고 있는 동안의 시간

<br/>

2. 함수형 프로그래밍과 객체 지향 프로그래밍을 모두 지원하는 다중 패러다임 언어

- **[함수형 프로그래밍](https://www.inflearn.com/pages/infcon-2023-tech-oopfp)** : 프로그램을 순수 함수들의 조합으로 무엇을 할 것인지에 주목하여 결과를 만들어내는 선언형 프로그래밍 방법

    - **[순수 함수](https://codingpracticenote.tistory.com/180)**

        - 입력값에 대해 항상 동일한 출력값을 반환하는 함수

        - 외부 상태에 동작을 의존하거나 영향을 끼치는 부수 효과가 없는 함수

            - **불변성[[설명1](https://velog.io/@wlsrhkd4023/Kotlin-%EB%B6%88%EB%B3%80%EC%84%B1Immutability%EA%B3%BC-%EA%B0%80%EB%B3%80%EC%84%B1Mutability), [설명2](https://velog.io/@rudans987/%EB%B6%88%EB%B3%80%EC%84%B1%EC%9D%B4%EB%9E%80)]** : 값이나 상태를 변경할 수 없는 것을 의미하며, 기존의 상태 값을 유지하면서 새로운 상태 값을 추가한다.


<br/>

### 자바와 코틀린의 차이점

코틀린은 컴파일러가 문맥으로부터 변수 타입을 자동으로 유추할 수 있기 때문에 타입 선언을 생략해도 된다. (타입 추론)

코틀린은 널이 될 수 있는 타입을 지원하여 컴파일 시점에 NullPointerException이 발생할 수 있는지 여부를 검사할 수 있어서 좀 더 프로그램의 신뢰성을 높일 수 있다. (널 안정성)

<br/>

### 정적 타입 지정 언어의 장점

실행 시점에 어떤 메소드를 호출할지 알아내는 과정이 필요 없으므로 메소드 호출이 더 빠르다.

컴파일러가 프로그램의 정확성을 검증하기 때문에 실행 시 프로그램이 오류로 중단될 가능성이 더 작아진다.

<br/>

### 함수형 프로그래밍의 특징

**[1. 일급 시민인 함수](https://coinpipe.tistory.com/264)**

함수(프로그램의 행동을 나타내는 코드 조각)를 일반 값처럼 다룰 수 있다.

함수를 변수에 저장할 수 있고, 함수를 인자로 다른 함수에 전달할 수 있으며, 함수에서 새로운 함수를 만들어서 반환할 수 있다.

**2. 불변성**

함수형 프로그래밍에서는 일단 만들어지고 나면 내부 상태가 절대로 바뀌지 않는 불변 객체를 사용해 프로그램을 작성한다.

```kotlin
data class Person(val name: String, val age: Int)

fun main() {
    val person1 = Person("Alice", 30)
    val person2 = person1.copy(name = "Bob")

    println(person1) // Person(name=Alice, age=30)
    println(person2) // Person(name=Bob, age=30)
}
```

**3. 부수 효과 없음**

함수형 프로그래밍에서는 입력이 같으면 항상 같은 출력을 내놓고 다른 객체의 상태를 변경하지 않으며, 함수 외부나 다른 바깥 환경과 상호작용하지 않는 순수 함수를 사용한다.

<br/>

### 함수형 프로그래밍의 이점

**1. 간결성**

함수형 코드는 명령형 코드에 비해 더 간결하다.

(순수) 함수를 값처럼 활용할 수 있으면 더 강력한 추상화를 할 수 있고 강력한 추상화를 사용해 코드 중복을 막을 수 있다.

- **[고차 함수](https://incheol-jung.gitbook.io/docs/study/kotlin-in-action/8)** : 다른 함수를 인자로 받거나 함수를 반환하는 함수
- **[추상화](https://ko.wikipedia.org/wiki/%EC%B6%94%EC%83%81%ED%99%94_(%EC%BB%B4%ED%93%A8%ED%84%B0_%EA%B3%BC%ED%95%99))** : 복잡한 자료, 모듈, 시스템 등으로부터 핵심적인 개념 또는 기능을 간추려 내는 것

```kotlin
fun calculate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

fun operationChoice(operator: String): (Int, Int) -> Int {
    return when (operator) {
        "add" -> ::add
        "subtract" -> ::subtract
        else -> { a, b -> a * b }
    }
}

fun add(x: Int, y: Int): Int {
    return x + y
}

fun subtract(x: Int, y: Int): Int {
    return x - y
}

fun main() {
    val result1 = calculate(10, 5, ::add)
    println(result1) // 15

    val result2 = calculate(10, 5, ::subtract)
    println(result2) // 5

    val operation = operationChoice("add")
    val result3 = operation(10, 5)
    println(result3) // 15
}
```

**2. 다중 스레드를 사용해도 안전하다**

불변 데이터 구조를 사용하고 순수 함수를 그 데이터 구조에 적용한다면 다중 스레드 환경에서 같은 데이터를 여러 스레드가 변경할 수 없다.

**3. 테스트하기 쉽다**

부수 효과가 있는 함수는 그 함수를 실행할 때 필요한 전체 환경을 구성하는 준비 코드가 따로 필요하지만, 순수 함수는 그런 준비 코드 없이 독립적으로 테스트할 수 있다.

- - -

## [얕은 복사 vs 깊은 복사](https://seosh817.tistory.com/163)

### 얕은 복사

주소값을 복사하는 것

원본 객체의 인스턴스와 같은 메모리 주소를 참조한다.

같은 메모리 주소값을 참조하기 때문에 복사된 객체의 값이 변경되면 원본 객체의 값도 변경된다.

### 깊은 복사

새로운 메모리 공간에 객체의 모든 값을 복사하는 것

원본 객체는 그대로 두고, 새로운 메모리 공간에 원본 객체의 값들을 모두 복사한다.

다른 메모리 주소값을 참조하기 때문에 복사된 객체가 변경되어도 원본 객체는 영향을 받지 않는다.

- - -

## [val vs var](https://incheol-jung.gitbook.io/docs/study/kotlin-in-action/untitled#undefined-3) vs const

### val(value)

변경 불가능한 참조를 저장하는 변수

val로 선언된 변수는 일단 초기화하고 나면 재대입이 불가능하다.

val 참조 자체는 불변일지라도 그 참조가 가리키는 객체의 내부 값은 변경될 수 있다.

### var(variable)

변경 가능한 참조를 저장하는 변수

### const

상수, 한 번 초기화하면 내부의 값을 사용할 수는 있지만, 바꿀 수는 없는 것

val과 같은 특성을 갖고 있지만, 불변성의 차이 존재한다.

## [val vs const val](https://velog.io/@dabin/Kotlin%EB%B3%80%EC%88%98%EC%84%A0%EC%96%B8-val-var)

### val

불완전한 불변성, 값이 런타임 시에 결정되는 상수

### const val

불변성, 값이 컴파일 시에 결정되는 상수

클래스의 생성자에 할당될 수 없으며, String을 포함한 기본 자료형으로만 선언이 가능하다.

함수 내의 지역변수나 클래스의 속성으로 사용할 수 없다.

<br/>

const val의 경우, 컴파일 시에 데이터가 메모리에 존재하기 때문에 사용 시 객체를 생성해서 이에 접근하는 것이 아니고, 클래스명.상수명의 형태를 사용해서 직접 접근한다.

- 클래스의 객체를 생성한 뒤 사용해야 하는 클래스 속성의 소요시간을 줄임으로 성능이 향상된다.

- 값을 참조할 때마다 상수에 접근하면서 발생하는 오버헤드를 줄일 수 있다는 장점

    - **[오버헤드](https://ko.wikipedia.org/wiki/%EC%98%A4%EB%B2%84%ED%97%A4%EB%93%9C)** : 어떤 처리를 하기 위해 들어가는 간접적인 처리 시간과 메모리 등을 말한다.

https://itstory1592.tistory.com/104

```kotlin
// val 키워드를 통해 상수를 선언
object Constants {
    val NAME = "BuNa"
}

// Kotlin
fun testValWithoutConst() {
    val name = Constants.NAME
}

// Decompiled Java
public final void testValWithoutConst() {
    String name = Constants.INSTANCE.getNAME();
}
```
```kotlin
// const val 키워드를 통해 상수를 선언
object Constants {
    const val NAME = "BuNa"
}

// Kotlin
fun testValWithoutConst() {
    val name = Constants.NAME
}

// Decompiled Java
public final void testValWithoutConst() {
    String name = "BuNa"
}
```

- - -

## [!! vs ?](https://jaeyeong951.medium.com/kotlin-%EC%BD%94%ED%8B%80%EB%A6%B0-%ED%83%80%EC%9E%85-%EC%8B%9C%EC%8A%A4%ED%85%9C-ebfb7bdbe746)

### !!(non-null 단언 연산자)

nullable 타입의 값을 강제로 가져오기 위해 사용한다.

만약 값이 null 이면, NullPointerException이 발생한다.

### ?(Elvis 연산자)

안전하게 nullable 타입의 값을 가져오기 위해 사용한다.

<br/>

**[NullPointerException](https://seagence.com/blog/java-null-pointer-exception-how-to-avoid-and-fix/)**

프로그램이 null 값 으로 설정된 객체 참조를 사용하려고 할 때 발생하는 일종의 런타임 예외

초기화되지 않은 개체에 액세스하거나 수정하려고 할 때 발생한다.

### [NullPointerException을 방지할 수 있는 방법](https://choidev-1.tistory.com/92)

**1. 안전 호출 연산자(?.)**

함수 호출에 사용되는 변수나 다른 함수의 반환값이 null이 아닐때만 다음 함수를 호출할 수 있도록 한다.

안전 호출 연산자와 함께 let 함수를 사용하여 null 값에 따른 결과를 처리한다.

**2. 엘비스 연산자(?:)** : 검사값이 null일 때, null 대신 기본값을 제공하는 방법

**3. 값이 null인지 if로 검사하기, 예외 처리 등**

- - -

## [가시성 변경자(접근 제어자)](https://velog.io/@changhee09/%EC%BD%94%ED%8B%80%EB%A6%B0-%EA%B0%80%EC%8B%9C%EC%84%B1-%EB%B3%80%EA%B2%BD%EC%9E%90)

클래스 외부에서 선언된 요소들에 대한 접근을 제어한다.

클래스의 내부 구현에 대한 접근을 제한함으로써, 외부 코드에 영향을 주지 않고 클래스 내부를 변경할 수 있다.

- 자바와 달리, 코틀린의 기본 가시성은 public이다.

- 자바의 기본 가시성인 패키지 전용(package-private)은 코틀린에 없다.

    - 틀린은 패키지를 네임스페이스를 관리하기 위한 용도로만 사용한다.

<br/>

https://thebook.io/080250/0132/

- **public(공개)** : 멤버를 어디서나 볼 수 있다.

- **internal(모듈 내부)** : 멤버를 멤버가 속한 클래스가 포함된 컴파일 모듈 내부에서만 볼 수 있다.

- **protected(보호)** : 멤버를 멤버가 속한 클래스와 멤버가 속한 클래스의 모든 하위 클래스 안에서 볼 수 있다.

- **private(비공개)** : 멤버를 멤버가 속한 클래스 내부에서만 볼 수 있다.

<table>
  <tr>
    <th>변경자</th>
    <th>클래스 멤버</th>
    <th>최상위 선언</th>
  </tr>
  <tr>
    <td>public(기본 가시성)</td>
    <td>모든 곳에서 볼 수 있다.</td>
    <td>모든 곳에서 볼 수 있다.</td>
  </tr>
  <tr>
    <td>internal</td>
    <td>같은 모듈 안에서만 볼 수 있다.</td>
    <td>같은 모듈 안에서만 볼 수 있다.</td>
  </tr>
  <tr>
    <td>protected</td>
    <td>하위 클래스 안에서만 볼 수 있다.</td>
    <td>(최상위 선언에 적용할 수 없음)</td>
  </tr>
  <tr>
    <td>private</td>
    <td>하위 클래스 안에서만 볼 수 있다.</td>
    <td>같은 파일 안에서만 볼 수 있다.</td>
  </tr>
</table>

```kotlin
open class Parent {
    // protected로 선언하였기에 자기 자신 또는 하위 클래스에서 사용 가능
    protected open val name = "코틀린"
    // class의 private으로 선언해서 클래스 내에서만 접근 가능
    private val address = "대한민국"
    // 아무런 가시성이 없기에 public에 해당
    open val tel = "00000"
}

// Parent 클래스를 상속 받음
class Child: Parent() {
    fun call() {
        // protected 멤버에 접근
        println(name) // 코틀린
        // public 멤버에 접근
        println(tel) // 00000
        // private 멤버에 접근 불가능(에러)
        println(address)
    }
}

fun main() {
    val parent: Parent = Parent()
    // protected 멤버에 접근 불가능(에러)
    println(parent.name)
    // private 멤버에 접근 불가능(에러)
    println(parent.address)
    // public 멤버에 접근 가능
    println(parent.tel) // 00000
    
    val child: Child = Child()
    child.call()
}
```

- - -

## [lateinit vs by lazy](https://todaycode.tistory.com/171)

둘 다 객체의 초기화를 늦게 할 때 사용한다.

### lateinit

var로 선언해야 하며, 값을 수정할 수 있다.

선언 이후 아무때나 초기화를 할 수 있다.

Primitive Type (Int, Float, Double, Long 등) 에는 사용할 수 없다.

### by lazy

val로 선언해야 하며, 한 번 초기화를 하면 값을 수정할 수 없다.

변수를 호출할 때, 최초 한 번만 초기화를 할 수 있다.

- - -

## [data class](https://velog.io/@haero_kim/Kotlin-%EA%B0%90%EB%8F%99-%EC%8B%A4%ED%99%94-Data-Class-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0)

데이터를 다루는데 최적화된 클래스

equals(), hashCode(), toString(), copy(), componentN() 5가지 유용한 함수들을 내부적으로 자동으로 생성해준다.

자바와 달리, 변수마다 getter/setter를 설정하지 않고 toString(), hashCode(), copy() 함수를 직접 override 하지 않아도 된다.

### [equals + hashcode의 이유](https://jaehun2841.github.io/2019/01/12/effective-java-item11/#%EC%84%9C%EB%A1%A0)
equals는 객체의 동등성을 비교하는 메소드로, 두 객체가 동일한 값을 가지고 있는지를 비교한다.

만약 equals()만 재정의하면, 동등한 객체들이 다른 해시 코드 값을 반환하여 다른 객체로 취급한다.

따라서, equals()를 재정의할 경우, hashCode()도 함께 재정의하여 두 객체가 메모리 상에서 같은 위치에 있는지도 비교해줘야 한다.

- **해시 코드** : 객체를 식별하는 하나의 정수값

- - -

## [scope function](https://hyeon9mak.github.io/using-kotlin-scope-function-correctly/)

객체의 이름을 사용하지 않고 객체의 접근을 가능하게 하는 함수

### let

람다 내부에서 수신 객체를 it으로 받아 사용하고, 람다의 마지막 표현식을 결과로 반환한다.

null이 아닌 객체에 대한 작업을 수행하거나, 지역 변수를 명시적으로 표현할 때 유용하다.

### run

람다 내부에서 수신 객체를 this로 받아서 사용하고, 람다의 마지막 표현식을 결과로 반환한다.

객체를 생성하거나 사용할 때 여러 작업을 수행하고 그 결과를 반환받고자 할 때 유용하다.

### with

람다 내부에서 인자로 받은 객체를 this로 받아서 사용하고, 람다의 마지막 표현식을 결과로 반환한다.

이미 생성된 객체에 일괄적인 작업을 처리할 때 유용하다.

### apply

람다 내부에서 수신 객체를 this로 받아서 사용하고, 수신 객체 자체를 반환한다.

코드 블록이 모두 수행된 후 인스턴스가 할당되기 때문에 객체 생성시점에서 초기화를 할 때 유용하다.

### also

람다 내부에서 수신 객체를 it으로 받아서 사용하고, 수신 객체 자제를 반환한다.

추가적인 작업을 함께 수행시키고 싶을 때 유용하다.

<table>
  <tr>
    <th>Function</th>
    <th>Object reference</th>
    <th>Return value</th>
    <th>Is extension function</th>
  </tr>
  <tr>
    <td>let</td>
    <td>it</td>
    <td>Lambda result</td>
    <td>Yes</td>
  </tr>
  <tr>
    <td>run</td>
    <td>this</td>
    <td>Lambda result</td>
    <td>Yes</td>
  </tr>
  <tr>
    <td>run</td>
    <td>-</td>
    <td>Lambda result</td>
    <td>No: called without the context object</td>
  </tr>
  <tr>
    <td>with</td>
    <td>this</td>
    <td>Lambda result</td>
    <td>No: takes the context object as an argument.</td>
  </tr>
  <tr>
    <td>apply</td>
    <td>this</td>
    <td>Object reference</td>
    <td>Yes</td>
  </tr>
  <tr>
    <td>also</td>
    <td>it</td>
    <td>Object reference</td>
    <td>Yes</td>
  </tr>
</table>

<br/>

## this vs it

### this

암시적으로 수신 객체를 참조하여 객체의 멤버에 직접 접근할 수 있다.

객체의 속성을 초기화하거나 설정하는 등의 작업을 수행할 때 유용하다.

apply, run, with 함수에서 사용된다.

### it

명시적으로 수신 객체를 참조하여 객체의 멤버에 접근한다.

람다 내부에서 수신 객체를 명확히 구분하고자 할 때 유용하다.

let, also 함수에서 사용된다.

- - -

## [Sealed Class vs Enum Class](https://velog.io/@ddyy094/Enum-class%EC%99%80-Sealed-class)

[Sealed Class와 Enum Class의 특징](https://medium.com/depayse/kotlin-%ED%81%B4%EB%9E%98%EC%8A%A4-9-%EB%B4%89%EC%9D%B8%EB%90%9C-%ED%81%B4%EB%9E%98%EC%8A%A4-sealed-class-%EC%97%B4%EA%B1%B0%ED%98%95-%ED%81%B4%EB%9E%98%EC%8A%A4-enum-class-44a49465a3d)

둘 다 타입 분기로 사용될 때, when 표현식에서 반드시 모든 가능한 경우를 처리해야 한다.

이 경우, when 표현식은 값을 반환해야 하며, 나눠지는 조건은 모든 하위 클래스나 모든 열거형 값을 포함해야 한다.

그렇기 때문에 else 분기가 없어도 정상적으로 작동한다.

### Sealed Class

상태를 나타내는 여러 인스턴스를 가질 수 있으며, 각 인스턴스는 고유한 데이터를 포함하고, 서로 다른 생성자를 가질 수 있다.

```kotlin
sealed class Result {
    data class Success(val data: String) : Result() // data를 포함하는 생성자
    data class Error(val errorMessage: String) : Result()
    object Loading : Result() // 데이터를 포함하지 않는 단일 객체
}

fun handleResult(result: Result) {
    when (result) {
        is Result.Success -> {
            println("Success: ${result.data}")
        }
        is Result.Error -> {
            println("Error: ${result.errorMessage}")
        }
        is Result.Loading -> {
            println("Loading...")
        }
    }
}

fun main() {
    // 다양한 Result 인스턴스 생성
    val success = Result.Success("Data loaded successfully")
    val error = Result.Error("An error occurred")
    val loading = Result.Loading

    handleResult(success) // Success: Data loaded successfully
    handleResult(error) // Error: An error occurred
    handleResult(loading) // Loading...
}
```

### Enum Class

-  특정 값들을 열거하여 싱글턴 인스턴스로써 하나의 객체만 제한적으로 사용하고, 이러한 객체들은 동일한 생성자 형태를 가진다.

```kotlin
enum class Color(
    val r: Int, val g: Int, val b: Int // 상수의 프로퍼티를 정의한다.
) {
    RED(255, 0, 0), ORANGE(255, 165, 0), // 각 상수를 생성할 때, 그에 대한 프로퍼티 값을 지정한다.
    YELLOW(255, 255, 0), GREEN(0, 255, 0), BLUE(0, 0, 255),
    INDIGO(75, 0, 130), VIOLET(238, 130, 238); // 여기 반드시 세미콜론을 사용해야 한다.

    fun rgb() = (r * 256 + g) * 256 + b // enum 클래스 안에서 메소드를 정의한다.
}

fun main() {
    val c1 = Color.BLUE
    val c2 = Color.RED

    println(c1.rgb()) // 255
    println(c1.javaClass) // class Color

    println(c2.rgb()) // 16711680
    println(c2.javaClass) // class Color
}
```