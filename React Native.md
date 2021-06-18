## React Native

### Native APP vs WEB APP vs Hybrid APP
#### Native APP 
- application을 의미
- 모바일 기기에 최적화 된 언어로 개발된 APP
- 안드로이드 SDK(소프트웨어 개발 키트)를 이용해 Java, Kotlin 언어로 만드는 APP과 iOS 기반 SDK를 이용해 Swift (스위프트)로 만드는 APP이 있음    

- Native APP의 장점
  - 성능이 WEB APP, Hybrid APP에 비하여 가장 높음
  - 네이티브 API를 호출하여 사용함으로 플랫폼과 밀착되어 있음
  - Java, Swift 등 네이티브 언어에 익숙한 사용자라면 쉽게 사용할 수 있음

- Native APP의 단점
  - 플랫폼에 한정적임
  - PC에서 접근하려면 모바일 어플 구동 프로그램이 별도로 필요힘
  - 해당 플랫폼에서 요구하는 언어에 제약적임
    - 따라서 해당 언어(자바나 스위프트)와 플랫폼의 API를 다루는데 익숙해야 함
  - 앱 업데이트는 앱스토어를 통해 업데이트를 해야함

#### WEB APP
- Mobile Web 과 Native APP을 결합한 형태로 Mobile Web의 특징을 가지면서 Native APP의 장점을 갖고 있음
- 모바일에 최적화 된 APP을 의미 
- WEB APP도 Mobile Web처럼 일반적인 Web 기술로 개발되고 모바일 브라우저에서 실행되지만 풀 브라우저 방식이 아닌 단일 페이지 방식으로 화면을 진화해 속도가 빠르다는 장점이 있음

- Mobile Web
  - 모바일에서 PC용 사이트의 글자폰트와 이미지, 터치 아이콘, 플래시 등 데스크탑 브라우저에서 실행되는 기능을 모바일에 맞추어 표현한 사이트를 의미
    ( PC용 홈페이지를 모바일 스크린의 크기에 맞춰 줄여 놓은 것 )

- Mobile Web APP의 장점
  - 웹사이트를 보는 것이기 때문에 따로 설치할 필요가 없음
  - 별도 설치 및 승인과정이 필요치 않아 유지보수가 용이
  - 모든 기기와 브라우저에서 접근할 수 있음
  - 플랫폼의 제약이 없음
  - 비교적 저렴
  - html, css, JSP, PHP, .net 등의 언어로 개발

- Mobile Web APP의 단점
  - 플랫폼 API (카메라 등)를 사용할 수 없고 오로지 브라우저 API만을 사용할 수 있음
  - 친화적인 터치 앱을 개발하기가 약간 번거로운 점이 있음 ( 까다로움 )
  - Native, Hybrid APP보다 실행이 까다로움 ( 브라우저를 열고 검색해 들어가야 함 )
  - Native에 비해 속도가 느림
  - 인터넷 상태에 따라 접속 장애가 날 수 있음

#### Hybrid APP
- 'Native APP + WEB APP'
- Native APP에 Web view를 띄워 WEB APP을 실행 시키는 것이 보편적이며 양쪽의 API를 모두 사용할 수 있는것이 큰 장점 입

- Hybrid APP의 장점
  - 네이티브 API 와 브라우저 API 를 이용한 다양한 개발이 가능함
  - Web개발 기술을 사용해 APP을 개발할 수 있음
  - 한번의 개발로 다수의 플랫폼에 대응할 수 있음
  - 하나의 소스로 아이폰, 안드로이드에 맞게 포장이 가능

- Hybrid APP의 단점
  - 네이티브 기능에 접근하기 위해선 네이티브 개발 지식이 결국 필요함
  - 웹뷰에서 APP을 실행하는 경우이기 때문에 APP의 성능이 곧 브라우저의 성능임
  - UI 프레임워크 도구를 사용하지 않는다면 개발자가 UI를 제작해야 

### React Native
- Native APP을 제작하기 위한 오픈 소스 프레임워크
    - iOS
      - 개발 프로그램으로 Eclipse, Android studio가 있음  
      - Objective-C, Swift 코드를 iOS platform에 타겟팅해주는 컴파일러가 있음
      
    - Android
      - 개발 프로그램으로 XCODE가 있음  
      - Java, Kotlin을 Android platform에 타겟팅해주는 컴파일러가 있음
    
- 자바스크립트 코드를 각 OS platform에 타겟팅해줌

- App을 빌드할 때 App의 전체 로직을 가지고 있는 JS 번들 만들고 이 번들을 각 platform에 삽입
  - JS 번들은 JS Thread에 의해 실행이되는데 각 platform에서 app을 실행하기 위한 native threads는 
    js thread와 직접 커뮤니케이션할 수 없고 react native에서 제공하는 bridge에 의해 상호작용을 하게됨

<img src="https://user-images.githubusercontent.com/53929446/122493017-e0dcd880-d021-11eb-8e9d-0058053c6be4.png" width="600px" height="400px"></img>








```react

```
