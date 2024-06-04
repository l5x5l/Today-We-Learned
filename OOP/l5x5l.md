## 객체 지향 프로그래밍이란
프로그래밍에서 필요한 데이터를 추상화화여 변수와 메서드를 가진 객체를 만들고, 객체간의 유기적인 상호작용을 통해 로직을 구현하는 프로그래밍 방법
- 클래스의 정의
  - "공통된 특징을 가지는 집단"에 속하는 속성과 행위를 변수와 메서드로 정의한 것
- 객체의 정이
  - 클래스에서 정의한 것을 기반으로 실제 메모리에 올라간 데이터를 의미

<br/>

## 추상화, 캡슐화
#### 추상화
- 데이터나 프로세스를 어떤 성질, 공통성, 본질을 모아 추출하는 것
- 세부적인 구현 사항보다는 어떤 기능인지 측면에서 클래스를 **설계**하는 것
- 추상화의 주 목적은 클래스의 주요 기능과 내부 세부 구현을 분리하는 것으로, 추상화를 적용하면 세부적인 내용을 구현하기 앞서 먼저 해당 클래스의 본질과 핵심 기능을 정의하고 파악할 수 있다

#### 캡슐화
- 클래스의 내부적인 **구현**을 감추는 것
- 변경 가능성이 높은 구현부는 내부에 숨기고, 외부에는 상대적으로 안정된 부분만을 공개한다.
- 이를 통해 변경 가능성이 높은 클래스의 내부 구현을, 이 클래스를 사용하는 외부에 미치는 영향 없이 수정할 수 있다.

#### 추상화, 캡슐화의 차이
- 추상화의 경우, 클래스를 설계하는 과정에서 주요 핵심 기능을 정의하는 것으로, 인터페이스를 설계하는 과정에서 적용된다
- 캡슐화의 경우, 추상화를 통해 정의된 인터페이스를 구현하는 과정에서 내부 로직을 숨김으로써 적용된다.
- 즉, 추상화는 설계 단계에서, 캡슐화는 구현 단계에사 적용된다고 생각한다.

#### 추상화, 캡슐화 적용 예시
- IOT 어플리케이션을 개발한다고 가정했을 때, 스마트폰 앱과 하드웨어 간 통신은 바이트코드로 이루어진다고 가정한다.
- 이 상황에서 하드웨어와 통신하는 책임을 가진 클래스를 구현한다.

1. 클래스 설계 (추상화)
  - 해당 클래스가 제공하는 본질이 무엇인가?라는 기준 하에 제공할 주요 메서드를 정의한다.
``` kotlin
interface DeviceCommunicationHandler {
  fun connect(deviceId : String)
  fun disconnect()
  fun sendCommand(message : String)
}
```
2. 클래스 구현 (캡슐화)
  - 추상화에서 정의한 인터페이스의 세부적인 구현은 private하게 정의하여 이를 사용하는 타 클래스에서는 이를 알지 못하도록 한다.
``` kotlin
class DeviceCommunicationHandleImpl(
  private val interfaceType : InterfaceType
) : DeviceCommunicationHandler {
  fun connect(deviceId : String) {
    // deviceId를 가진 기기와 연결
    // 연결시에는 interfaceType (블루투스, 와이파이, usb 등)에 따라 다른 방식으로 연결
    when (interfaceType) {
      InterfaceType.BLUETOOTH -> {}
      InterfaceType.WIFI -> {}
      InterfaceType.USB -> {}
    }
  }
  
  fun disconnect() {
    // 기기와 연결 중단
  }
  
  fun sendCommand(message : String) {
    /* 기기와 연결되어있는지 확인하는 것 같은 사전 작업 */
    
    val byteArrayCommand = stringToByteCommand(message)
    
    /* byteArrayCommand를 기기에 전송 */
  }
  
  private fun stringToByteCommand(message : String) {
    val commandHeader = "[HEAD]"
    
    val byteList = (commandHeader + message).map{
      it.code.toByte()
    }
    return byteList.toByteArray()
  }
}
```

<br/>

## 객체지향 5원칙
#### 단일 책임 원칙
- 클래스는 단 하나의 책임만을 가지고 있어야 한다.
- 클래스가 변경되는 이유는 단 한 가지여야 하며, 만약 다양한 이유로 인해 해당 클래스가 변경되는 경우에는 해당 클래스가 너무 많은 채임을 가지고 있는 상황일 수 있다.
  - 예시  
    위 캡슐화 예제에서, DeviceCommunicationHandleImpl는 기기에 전송하는 헤더의 형식이 변경될 경우에도 stringToByteCommand 메서드를 수정해야 한다.  
    그러나, 헤더 형식의 변경으로 인해 기기와의 통신을 책임지는 클래스의 메서드가 수정된다는 점은 단일 책임 원칙에 위배될 수 있다  
    (단, 하나의 책임이 어느 정도의 범위를 가지는지는 개발자마다 다르기 때문에 반드시 위배되었다는 것은 아님)   
    해당 예제를 단일 책임 원칙에 적합하게 수정한 내용은 아래와 같다.
``` kotlin
class DeviceCommunicationHandleImpl(
  private val interfaceType : InterfaceType,
  private val commandMapper : CommandMapper
) : DeviceCommunicationHandler {
  // ...
  fun sendCommand(message : String) {
    /* 기기와 연결되어있는지 확인하는 것 같은 사전 작업 */
    val byteArrayCommand = commandMapper.stringToByteCommand(message)
    /* byteArrayCommand를 기기에 전송 */
  }
}

class CommandMapper() {
  private fun stringToByteCommand(message : String) {
    val header = "[HEAD]"
  
    val byteList = (header + message).map{
      it.code.toByte()
    }
    return byteList.toByteArray()
  }
}
```

#### 개방 폐쇄 원칙
- 수정에는 닫혀 있고, 기능 확장에는 열려 있어야 한다는 원칙
  - 예시
    위 캡슐화 예제에서, DeviceCommunicationHandleImpl 의 connect 부분은 연결 타입이 추가될 때마다 해당 타입에 맞는 분기처리가 추가되어야 함.  
    이는 개방 폐쇄 원칙에 맞지 않으며, 이를 수정하기 위해서 연결부분을 담당하는 ConnectionManager를 별도로 분리
    이렇게 분리함으로서 연결 타입이 추가될 때마다 해당 연결 타입에 맞는 클래스를 선언한 후 DeviceCommunicationHandleImpl에 인자로 넘겨주면 된다.
``` kotlin
interface ConnectionManager {
  fun connect(deviceId : String)
  fun disconnect()
}

// 구현부 생략
class BluetoothConnectionManager : ConnectionManager
class WifiConnectionManager : ConnectionManager
class USBConnectionManager : ConnectionManager

class DeviceCommunicationHandleImpl(
  private val commandMapper : CommandMapper,
  private val connectionManager : ConnectionManager
) : DeviceCommunicationHandler {
  fun connect(deviceId : String) {
    connectionManager(deviceId)
  } 
  //..
}
```

#### 리스코프 치환 원칙
- 자식 클래스는 부모 클래스를 대체하여 사용할 수 있어야 한다는 원칙
- java나 kotlin에서 상속/구현을 사용하고 있다면, 리스코프 치환 원칙을 지키면서 코드를 작성하고 있을 가능성이 높다.
  따라서, 이번에는 원칙을 위반한 예시만을 제시한다.
  - 리스코프 치환 원칙을 위반한 예시
    아래 코드에서 SimlessSmartPhone은 Phone의 call메서드를 override하여 에러를 리턴하고 있다.
    만약 Phone 타입의 변수를 사용하여 call 메서드를 호출하는 부분이 있고 Phone타입 변수에 할당된 객체가 SimlessPhone이라면, call메서드를 호출할 때 에러를 발생시키게 된다.
    이는 자식 클래스가 부모 클래스를 대체하여 사용했을 때 에러가 발생한 상황이므로, 리스코프 치환 원칙에 어긋난다.
``` kotlin
open class Phone() {
  open fun call() {
    /* 전화와 관련된 로직 */
  }
}

class SimlessSmartPhone : Phone() {
  override fun call() {
    throw Exception("not supported")
  }
}
```

#### 인터페이스 분리 원칙
- 하나의 범용적인 인터페이스 대신, 세분화된 여러 개의 인터페이스로 분리해야 한다는 원칙
- 인터페이스를 구현한 구현체에서 인터페이스의 모든 기능을 사용하지 않는다면, 해당 인터페이스는 큰 범용적인 인터페이스일 가능성이 있으며, 이 경우 인터페이스를 각 사용처에 맞게끔 분리해야 함
- 만약 이를 무시할 경우, 인터페이스를 구현한 클래스에서 사용하지도 않는 메서드를 억지로 구현하게 될 수 있음  
  만약 억지로 구현하는게 싫어 에러를 리턴하는 방식으로 한다면, 리스코프 치환 원칙에 어긋나게 됨
  - 인터페이스 분리 원칙을 위반한 예시
``` kotlin
interface Display() {
  fun powerOn()
  fun powerOff()
  fun mirroring()
  fun multipleDisplays()
}

// hdmi를 통한 멀티 모니터 사용은 가능하지만, 미러링은 지원하지 않는 모니터
class OldDisplay() : Display() {
  override fun powerOn() { /*구현부 생략*/ }
  
  override fun powerOff() { /*구현부 생략*/ }
  
  override fun mirroring() {
    throw Exception("not supported")
  }
  
  override fun multipleDisplays() { /*구현부 생략*/ }
}
```
  - 인터페이스 분리 원칙을 적용하여 수정한 예시  
    Mirroring 기능에 대해 인터페이스 MirroringDevice로 분리하여 적용하였다.  
    이를 통해, 미러링을 지원하는 기기에만 MirroringDevice를 구현함으로써 인터페이스 분리 원칙을 만족시킬 수 있다.
``` kotlin
interface Display() {
  fun powerOn()
  fun powerOff()
  fun multipleDisplays()
}

interface MirroringDevice() {
  fun mirroring()
}

// hdmi를 통한 멀티 모니터 사용은 가능하지만, 미러링은 지원하지 않는 모니터
class OldDisplay() : Display {
  override fun powerOn() { /*구현부 생략*/ }
  
  override fun powerOff() { /*구현부 생략*/ }
  
  override fun multipleDisplays() { /*구현부 생략*/ }
}

// 미러링까지 지원하는 모니터
class NewDisplay() : Display, MirroringDevice() {
   /*구현부 생략*/
}
```

#### 의존성 역전 원칙
- 구현체에 의존하지 않고, 인터페이스에 의존해야 한다는 원칙
- 대게 추상화된 인터페이스보다는 클래스 구현체가 더 변화될 가능성이 높기에 만약 특정 클래스를 의존성을 가지게 된다면, 인터페이스를 의존성을 가졌을 때보다 더 많은 수정사항이 발생할 수 있다.
  - 예시  
    KakaoLoginRepository와 같은 구현체 대신, LoginRepository 인터페이스에 의존해야 한다.
``` kotlin
interface LoginRepository {
	suspend fun login(id : String, password : String) : Boolean
}

class KakaoLoginRepository : LoginRepository { /*구현부 생략*/ }
class NaverLoginRepository : LoginRepository { /*구현부 생략*/ }
class EmailLoginRepository : LoginRepository { /*구현부 생략*/ }

class LoginViewModel constructor(
  // LoginRepository의 구현체에 의존하지 말고, 인터페이스에 의존
  private val loginRepository : LoginRepository
) : ViewModel() {
  private val _id = MutableStateFlow<String>()
  val id : StateFlow<String> = _id.asStateFlow()
  
  private val _password = MutableStateFlow<String>()
  val password : StateFlow<String> = _password.asStateFlow()
  
  private val _loginSuccess = MutableEventFlow<Boolean>()
  val loginSuccess : StateFlow<Boolean> = _loginSuccess.asEventFlow()

  fun login() {
    viewModelScope.launch(Dispatcher.IO) {
      val result = loginRepository.login(id.value, password.value)
      _loginSuccess.emit(result)
    }
  }
}
```
- eventFlow : [단일 이벤트를 처리할 때 좋은 eventFlow 설명](https://medium.com/prnd/mvvm의-viewmodel에서-이벤트를-처리하는-방법-6가지-31bb183a88ce)

<br/>

## 다형성
- 어떤 객체의 속성(변수)이나 기능(메서드)이 상황(override, overload)에 따라 다양하게 동작할 수 있는 성질

#### override
- 상위 클래스에서 정의한 메서드를 하위 클래스에서 재정의 하는 행위
``` kotlin
open class Android11() {
    open fun runApp() {
        /* 앱의 시작 지점 Activity 실행 */
    }
    
    //...
}

open class Android12() : Android11() {

    // 함수 override
    override fun runApp() {
        showDefaultSplash()
        super.runApp()
    }
    
    private fun showDefaultSplash() {
        /* 안드로이드 12 이후부터 보여지는 기본 스플래시 화면 */
    }

    //...
}
```

#### overload
- 동일한 이름을 가진 메서드의 인자의 개수, 인자의 타빙을 다르게 하여 여러 번 선언하는 것
- java의 경우, 함수 인자에 기본값을 주는게 안되기 때문에, 만약 kotlin에서 기본값을 적용하듯이 메서드를 정의하고 싶을 때 overload를 사용하기도 합니다!
``` java
public class Logger {
    private final Context context;
    
    public Logger(Context context) {
        this.context = context;
    }

    // 동일한 이름, 서로 다른 인자
    public void logToFile(String message, String filePath) {
        /* filePath에 있는 파일에 로그용 message를 기록 */
    }
    
    public void logToFile(String message) {
        String defaultFilePath = getDefaultLogFilePath();
        logToFile(message, defaultFilePath);
    }
    
    // 기억에 의존한 코드라, 정확하지 않을 수 있습니다!
    private String getDefaultLogFilePath() {
        File[] dirs = context.getExternalMediaDirs();
        if (dirs[0] != null && dirs[0].length() > 0) {
            return dirs[0].getPath();    
        } else {
            return context.getFilesDir().getParent();
        }
    }
}
```
