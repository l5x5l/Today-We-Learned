## 1. 등장배경
- kotlin은 2011년 jetbrains에 의해 개발되었으며, 자바의 복잡성과 반복적인 보일러 플레이트 코드 문제를 해결하기 위해 등장했습니다.
- 코틀린은 자바와 100% 상호 운용이 가능하면서도 더 간결하고 직관적인 문법을 제공함으로써 개발자가 더 적은 코드로 더 많은 작업을 수행할 수 있도록 설계되었습니다.

## 2. Java와의 차이점
**null safety**
- 코틀린은 null 안정성을 제공하며, 기본적으로 모든 타입이 널이 될 수 없습니다.
- nullable한 변수의 경우, null이 가능하다는 것을 명시적으로 선언해야 합니다.

**Default Argument, Named Argument 지원**
- 자바의 경우 메서드를 호출할 때 기본 인자값을 지원하지 않습니다.
- 또한, 인자명을 사용할 수 없어 인자가 많은 메서드의 경우 가독성이 크게 떨어질 수 있습니다.

``` Java
public class Display {
  int showMessage(String message) {
    int defaultDisplayTime = 3;
    return semdMessage(message, defaultDisplayTime);
  }
  
  int showMessage(String message, int displayTime) {
    // 메세지를 디스플레이에 표시
  }
  
  int showImage(
    int width, int height, int x, int y,
    String filePath, boolean useColorMode,
    int displayTime, int filterType, ...
  ) {
    // 이미지를 디스플레이에 표시
  }
}
```
``` Java
// 사용자 입장
public static void main(String[] args) {
  Display display = new Display();
  int filterType = 1;
  display.showImage(512, 512, 0, 0, "path/image.png", true, 3, filterType, ...);
}
```
``` Kotlin
// 만약 kotlin 이었다면?
fun main() {
  val display = Display()
  val filterType = 1;
  display.showImage(
    width = 512, height = 512,
    x = 0, y = 0,
    filePath = "path/image.png",
    useColorMode = true, displayTime = 3,
    filterType = filterType,...
  )
}
```
> 너무 많은 인자로 인해 가독성이 크게 떨어지는 문제는 이는 인자가 너무 많은 생성자를 가진 클래스에서도 동일하게 발생할 수 있습니다. 이런 경우 java에서는 [빌더 패턴](https://inpa.tistory.com/entry/GOF-%F0%9F%92%A0-%EB%B9%8C%EB%8D%94Builder-%ED%8C%A8%ED%84%B4-%EB%81%9D%ED%8C%90%EC%99%95-%EC%A0%95%EB%A6%AC)을 사용하여 이 문제를 해결하였지만, kotlin의 경우 named argument를 사용하여 가독성이 크게 떨어지지 않으므로 빌더 패턴의 사용 빈도가 줄었습니다.


**확장 함수 지원**
- 클래스 상속이나 별도의 패턴을 적용하지 않고도 String과 같은 기존 클래스에 새로운 메서드를 확장할 수 있습니다.
- 단, 너무 많이 사용할 경우 기능들이 남발하게 되며, 메서드의 선언부가 여기저기 퍼져 있을 수 있어 가독성이 저하될 수 있습니다.

``` kotlin
class Original {
  fun onlyOneFunction(){
    println("Only One")
  }
}

fun Original.myExtension(): String {
  return "Original 클래스에 멤버 함수가 추가된 것처럼"
}

fun String.lastChar() : Char = this.get(this.length - 1)

fun main(){
  val originalObj = Original
  val result = originalObj.myExtension()
  println(result) // "Original 클래스에 맴버 함수가 추가된 것처럼"

  println("12345".lastChar()) // '5'
}

```


## 3. Scope function
**Scope 함수 정의**
- 더 제한된 범위를 지정함으로써 코드를 더 간결하게 만들어주는 함수로, 해당 범위 내 전달된 객체를 it 또는 this라는 context object를 통해서 접근할 수 있습니다.
- 종류로는 apply, also, let, run, with가 존재합니다.

**apply**
- 수신 객체의 메서드를 호출하지 않고, 수신 객체 자기 자신을 반환하고자 할 때 사용하며, 객체의 추가적인 초기화 작업을 수행할 때 유용합니다.
``` kotlin
val me = Person().apply {
  name = "l5x5l"
  age = 26 // ㅠㅠ
}
```

**also**
- 수신 객체를 전혀 사용하지 않거나, 수신 객체의 속성을 변경하지 않을 때 사용하며, 객체 생성시 발생하는 side Effect를 확인하거나 객체 인자의 유효성을 검사할 때 유용합니다.
``` kotlin
val baby = Person().also{
  requireNotNull(it.age) // 유효성을 검사하거나
  print("hello world!") // 객체 생성에 대한 side effect를 발생시키거나
}
```

**let**
- 지정된 값이 null이 아닌 경우에 호출해야 하는 경우, nullable 객체를 다른 nullable 객체로 반환하고자 하는 경우, 단일 지역 변수의 범위를 제한하고자 하는 경우에 유용합니다.
``` kotlin
warningMessage?.let { text ->
  binding.tvWarning.text = text
}
```

**run**
- 특정 값을 계산할 때 사용 변수의 범위를 최소화하고자 할 때, 매개변수로 수신한 값을 암시적 수신 객체로 변환할 때 사용합니다.
- 특정 값을 계산할 때만 사용하는 변수를 run 스코프 내에 선언함으로써 가독성에 도움이 될 수 있습니다. (해당 변수는 여기에서만 사용되는구나를 빠르게 파악 가능)
``` kotlin
val rollerCoasterAvailable : boolean = person.run {
  (height in 140..200) && (weight <= 150)
}
```

**with**
- nullable하지 않은 수신 객체를 사용함과 동시에 run처럼 사용 변수의 범위를 최소화하고자 할 때 사용합니다.
- 객체 메서드 혹은 변수를 여러 번 호출할 때 유용하다고 합니다.
- 또한 run과 달리, 별다른 반환값이 필요하지 않을 떄 사용된다고 합니다.
``` kotlin
with(bitmap) {
  resize(height = height / 2, width = width / 2)
  val file = toFile()
  useCaseSendFileToServer(file)
}
```


+ 위와 같은 범위 지정 함수는 중첩해서 사용할 경우, 가독성 문제를 야기할 수 있기에 chain 형태로 사용하는 것이 함수형 언어의 취지 와 가독성 향상 측면에서 더 적합하다고 합니다.
``` kotlin
val book = BookDeatil().apply {
  totalPage = 150
  currentPage = 0
}.also {
  requireNotNull(it.bookId)
}
```


## 4. Sealed class
- 추상 클래스로, 상속받는 자식 클래스의 종류를 제한할 때 사용합니다.
- 단 하나의 인스턴스만 가질 수 있는 Enum class와는 달리, sealed class를 상속받은 클래스들은 각기 다른 데이터를 가진 인스턴스를 생성할 수 있습니다.
  - enum class는 색상, 지역과 같이 하나의 클래스가 하나의 고유한 값을 가지는 경우
  - sealed class는 서버 응답 결과, 시간위 단위와 같이 클래스의 각 인스턴스가 각각의 값을 가질 수 있는 경우에 사용하면 될 것 같습니다.
``` kotlin
sealed class ApiResponse<out T>{
  data class Success<out T>(val data : T) : ApiResponse<T>()
  data class Failure(val errorCode : Int) : ApiResponse<Nothing>()
}

enum class Color(val r : Int, val g : Int, val b : Int) {
  RED(255, 0, 0), GREEN(0, 255, 0), BLUE(0, 0, 255)
}
```
