## Gradle이란
- 소프트웨어 빌드, 테스트 및 배포를 자동화해주는 툴
- 여기서 빌드는 코드를 컴파일하여 실행/설치 가능한 파일(exe, apk, aab등)로 만드는 과정을 의미한다.

<br/>

## Gradle의 핵심 개념
[Gradle Basics](https://docs.gradle.org/current/userguide/gradle_basics.html)
### 프로젝트
- 빌드될 수 있는, 소프트웨어의 한 조각을 의미하며 application 혹은 library가 그 예시이다.
- 단일 프로젝트는 루트 프로젝트라고 불리는 하나의 모듈을 포함하고 있다.
- 멀티 프로젝트는 하나의 루트 프로젝트와 다수의 서브 프로젝트를 포함하고 있다.

### 빌드 스크립트
- 프로젝트를 빌드하기 위해 수행해야 할 단계를 Gradle에 알려주는 역할을 수행한다.
- 프로젝트를 분석하고 이를 기반으로 하여 Project 객체를 설정한다.
- 분석한 프로젝트의 자식 프로젝트에 대한 Project 객체도 같이 설정한다.

### Dependency Management
- 프로젝트에서 사용하는 외부 의존성을 검색하고, 가져오는 것에 대한 자동화된 기술을 의미한다.

### Task
- Gradle이 프로젝트에서 수행할 수 있는 작업
- 컴파일, 테스트 실행과 같은 기본적인 작업 단위를 의미한다.
- task는 빌드 스크립트 또는 플러그인에 정의되어 있다.

### 플러그인
- gradle의 기능을 확장하고, 프로젝트에 task를 추가하는데 사용한다.
- 안드로이드 프로젝트에서 사용하는 AGP(Android Gradle Plugin)도 플러그인의 일종이다.

<br/>

## Gradle 빌드 단계
[Gradle Build Lifecycle](https://docs.gradle.org/current/userguide/build_lifecycle.html)
gradle은 아래 3단계 빌드 절차를 가지고 있다.
### 1. 초기화
- settings.gradle파일을 감지하고, 해당 파일에 대한 Settings 인스턴스를 생성한다.
    - Settings는 빌드에 포함되는 프로젝트 인스턴스의 계층을 구성하고, 선언하는 역할을 수행한다.  
      [Settings 설명](https://docs.gradle.org/current/dsl/org.gradle.api.initialization.Settings.html)
- 어떤 프로젝트를 빌드할 것인지를 결정한다.
- 모든 프로젝트에 대한 Project 인스턴스를 생성한다.

### 2. 구성
- 빌드 과정에 포함되는 모든 프로젝트의 build.gradle을 분석한다.
- task 그래프를 생성한다.

### 3. 실행
- 선택된 task들을 수행하기 위한 스케쥴링 작업 이후 task를 실행한다.
- task의 실행 순서는 task 그래프를 통해 분석한 task간 의존성을 결정되며, task는 병렬적으로 실행될 수 있다.

<br/>

## Gradle Warpper
[Gradle Warpper](https://junilhwang.github.io/TIL/Gradle/GradleWrapper/#build-gradle-%E1%84%8C%E1%85%A1%E1%86%A8%E1%84%89%E1%85%A5%E1%86%BC)
- Gradle 빌드를 실행하는데 권장되는 방법으로, 각 개발자나 다른 개발 환경에서 별도의 설치 과정 없이 프로젝트에 함께 포함시켜 배포할 수 있는 방법을 제공
- 이를 통해 개발 환경에 종속되지 않고 Gradle wrapper를 사용한 프로젝트를 바로 빌드할 수 있다.

<br/>

## 안드로이드에서 사용하는 Gradle 파일 분석   
[UnderStand the Android build system](https://developer.android.com/build#settings-file)
### Settings.gradle  
- 빌드를 진행할 프로젝트/모듈을 결정하고, 각 프로젝트에 대한 인스턴스 객체를 생성하기 위해 사용  
- 이후 언급될 빌드 과정 3단계 중 첫번째 단계인 초기화 단계에서 이 파일에 대해 Settings라는 객체를 생성  
- 프로젝트 수준 저장소 설정을 정의하고, 앱을 빌드할 때 포함해야 하는 모듈을 gradle에 추가  
``` groovy
pluginManagement {
    repositories {
        google()
        mavenCentral()
        gradlePluginPortal()
    }
}
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
    }
    versionCatalogs {

    }
}
rootProject.name = "app_name"
include ':app'
```
- pluginManagement  
  gradle에서 task를 수행할 때 사용해야 하는 플러그인 또는 이 플러그인을 제공해야 하는 레포지토리를 정의하는 부분  
- dependencyResolutionManagement
  프로젝트 전체의 종속성을 해결(=검색하고 가져오는 작업)하기 위해 선언  
  저장소, 의존 라이브러리 버젼 관리, 캐싱 전략 등 다양한 설정을 제어 가능  
  version catalog도 여기에 선언할 수 있으므로, 멀티 모듈 프로젝트에서 외부 라이브러리의 버젼을 일관되게 관리하는데 유용하다.  
  - repositoryMode  
    [공식문서](https://docs.gradle.org/current/javadoc/org/gradle/api/initialization/resolve/RepositoriesMode.html)  
    라이브러리를 받아오는 저장소는 프로젝트 혹은 모듈 단위의 gradle 파일에서도 선언할 수 있는데,
    프로젝트의 규모가 커져 굉장히 많은 모듈을 가지게 된다면 각 모듈마다 어떤 저장소를 사용하는지 파악하기 어려워 관리가 힘들 수 있다. 이에 대한 옵션을 설정하는데 사용한다.
    - PREFER_PROJECT (기본값)  
      settings.gradle에 선언된 repositories을 무시하고, project내 선언된 repositories를 사용한다.
    - PREFER_SETTINGS  
      project내 선언된 repositories를 무시하고 settings.gradle에 선언된 reposiroeis를 사용한다.
    - **FAIL_ON_PROJECT_REPOS**  
      project내 repositories가 선언되어 있을 경우 빌드 타임에 에러를 발생시킨다.
      Android Studio bumblebee 이후 기본값으로 생성한 프로젝트에서 settings.gradle에서 이 값을 사용하기에, 만약 이전 블로그나 참고 자료를 보고 project단위의 buidl.gradle에 repositories를 선언하게 되면 이 옵션으로 인해 빌드 과정에서 에러가 발생할 수 있다.

### 프로젝트 단위의 build.gradle
프로젝트의 모든 모듈에 적용되는 빌드 구성을 정의한다.
``` groovy
plugins {
    id("com.android.application") version "8.2.2" apply false
    id("org.jetbrains.kotlin.android") version "1.9.0" apply false
}
```

### 모듈 단위의 build.gradle
해당 모듈에 대한 빌드 구성을 정의한다.
```
plugins {
    id("com.android.application")
    id("org.jetbrains.kotlin.android")
}

android {
    namespace = "com.strayalpaca.sample"
    compileSdk = 34

    defaultConfig {
        applicationId = "com.strayalpaca.sample"
        minSdk = 24
        targetSdk = 34
        versionCode = 1
        versionName = "1.0"

        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
        vectorDrawables {
            useSupportLibrary = true
        }
    }

    buildTypes {
        release {
            isMinifyEnabled = false
            proguardFiles(
                getDefaultProguardFile("proguard-android-optimize.txt"),
                "proguard-rules.pro"
            )
        }
    }
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_1_8
        targetCompatibility = JavaVersion.VERSION_1_8
    }
    kotlinOptions {
        jvmTarget = "1.8"
    }
    buildFeatures {
        compose = true
    }
    composeOptions {
        kotlinCompilerExtensionVersion = "1.5.1"
    }
    packaging {
        resources {
            excludes += "/META-INF/{AL2.0,LGPL2.1}"
        }
    }
}

dependencies {
    implementation("androidx.core:core-ktx:1.13.1")
    // 나머지 라이브러리는 생략
}
```
- plugins
  본 모듈을 빌드할 때 사용하는 plugin을 정의한다.
  만약 별도의 버젼을 지정하지 않은 경우, project단위의 build.gradle의 plugin에서 정의한 버젼이 사용된다.
- android  
  안드로이드와 관련된 모든 빌드 설정들을 정의한다.  
  com.android.application 플러그인에 정의되어 있으므로, 이 플러그인을 plugins에 정의하지 않는다면 사용할 수 없다.  

## compileSdk, targetSdk
[compileSdkVersion and targetSdkVersion - what is the difference?](https://proandroiddev.com/compilesdkversion-and-targetsdkversion-what-is-the-difference-b4227c663ba8)
### compileSdk
- gradle에서 어떤 android sdk 버젼을 사용하여 컴파일을 수행할지를 결정한다.
    - android studio에서 코드를 작성할 때, compileSdk 를 기준으로 하여 기능을 제공해준다.
        - 예를 들어, compileSdk를 31 미만으로 설정한 경우, manifest 파일에서 BLUETOOTH_SCAN 권한을 선언한 경우, 해당 권한을 찾을 수 없다는 경고 메세지가 표시된다.

### targetSdk
- 앱이 설계되고 테스트된 안드로이드 버젼을 시스템에 알려준다.
- compileSdk과 관련하여, 컴파일을 수행하지 않은 버젼을 "설계되고 테스트됨"이라고는 말할 수 없기 때문에, targetSdkVersion은 compileSdk버젼보다 항상 낮거나 같아야 한다.
- targetSdk 보다 높은 버전을 가진 기기에서 실행하는 경우, 역호환성을 제공하여 앱이 이전 방식으로 동작하게 한다.
    - 예를 들어, android 12(sdk 31)에서는 사용자 지정 알림의 모양이 뱐경되었는데, target sdk를 31 미만으로 설정한 앱의 경우 android 12의 알림 모양이 아닌, 이전 버전의 알림 모양을 사용한다.
    - 단, 이는 "앱 동작 변경 사항" 중 "target sdk과 관계없이 모든 애플리케이션에 대한 변경 사항에 대한 것은 이전 버전을 사용할 수 없으므로 반드시 버전에 따른 추가적인 작업을 수행해야 한다.
 
#### 안드로이드의 버전 별 변경 내용 (추가사항)
안드로이드 변경 내용은 2개의 그룹으로 나누어져 있다.
- 특정 Android 버전을 대상으로 하는 앱에 대한 동작 변경
- target sdk과 관계없이 모든 애플리케이션에 대한 동작 변경
이 2가지에 대한 정보는 안드로이드 개발자 홈페이지에서 조회 가능하며, 버전 별 화면에서 우측 메뉴의 "앱 동작 변경사항 검토"를 통해 확인할 수 있다.  
[android 14 공식 사이트](https://developer.android.com/about/versions/14?hl=ko&_gl=1*1levgnm*_up*MQ..*_ga*MTk1Nzc4ODk0My4xNzE4MDk5Mzk5*_ga_6HH9YJMN9M*MTcxODA5OTM5OC4xLjAuMTcxODA5OTM5OC4wLjAuMA..)
