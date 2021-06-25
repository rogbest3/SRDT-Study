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
  - JS 번들은 JS Thread에 의해 실행이되는데 각 platform에서 APP을 실행하기 위한 Native Threads는 
    JS Thread와 직접 커뮤니케이션할 수 없고 React Native에서 제공하는 Bridge에 의해 상호작용을 하게됨
     - React Native로 각 platform의 Native APP 제작이 가능한 이유는 Bridge라는 개념을 제공하기 때문

<img src="https://user-images.githubusercontent.com/53929446/122493017-e0dcd880-d021-11eb-8e9d-0058053c6be4.png" width="600px" height="400px"></img>


#### APP을 실행시키기 위한 방법
- Expo CLI
  - 장점
    - 개발 환경 구축이 용이
    - 실제 개발이 쉽고 편함
    
  - 단점
    - OS Layer와 직접 상호작용 불가능 ( Jave, Kotlin, obj-C, Swift로 추가 작성 불가 )
    - Expo에서 제공해주는 모듈만 사용 가능
    - Expo Client에서는 잘 동작하지만 실제 Simulator 및 단말기에서 잘 동작하지 않을 수 있음
    - 개발 관점에서의 자유도 낮음

- React Native CLI
  - 장점
    - Expo로 접근하지 못하는 Native 기능에 접근 가능 ( Native 모듈 사용 자유도 높음 )
    - 원하는 언어로 추가 작성 가능 ( Custom Native 모듈 사용 가능 )
    - 필요한 기능이 있는 경우 모듈을 직접 제작 가능
    - OS Layer와 직접적인 상호작용 가능
    
  - 단점
    - 초기 개발환경 구축 및 실제 APP 개발 시 다소 시간 소요
    - Mac일 경우에만, IOS / Android 지원

- React Native CLI 사용 시 Mac 환경에서 개발 권장
  - Window에서는 지원이 빈약 ( 새로운 업데이트 사항들이 Mac에서만 반영되는 경우 발생 )
  - iOS, Android Simulator가 Mac에서만 모두 사용 가능 ( Window에서 iOS simulator 사용 X )
    - 각 platform 별로 native 모듈 기능이 상이하기 때문에 각 platform별 simulator를 기동시켜서 결과를 확인해야 됨
  - iOS APP를 개발해서 배포하려면 XCODE를 사용해야 하며 XCODE는 Mac에서만 사용 가능


#### 개발 환경 구축 ( Installation )
**1. nvm ( Node Version Manager )**
  - NodeJs의 버전 관리자, NodeJs 설치 Tool
  - 하나의 컴퓨터에서 여러 NodeJs를 사용하기 위해 버전별로 NodeJs 환경을 격리시키는 역할을 함
  - nvm을 통해서 원하는 특정 버전의 NodeJs를 원하는 조건에 따라 복수 설치하는 방법이 권장됨
  - nvm 설치
    - mac os nvm 설치
```
// nvm 설치
$ sudo curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.37.2/install.sh | bash

// 확인
$ nvm ls

-bash: nvm: command not found

// 결과로 위처럼 나오면
$ vi ~/.bash_profile

vi 에디터로 아래 코드가 있는지 확인
i 입력하면 insert 모드 동작

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm

입력 후 esc 누르고 :wq 입력하여 빠져 나옴

// 재시작
$ source ~/.bash_profile

// 재확인
$ nvm ls

->       system
node -> stable (-> N/A) (default)
iojs -> N/A (default)

// nvm 버전 확인
$ nvm --version
0.37.2
```

**2. node.js**
  - nvm을 이용한 nodejs 설치
```
// nvm을 이용한 nodejs 설치
$ nvm install 10.15.1

// nodejs 버전 확인
$ node -v
v10.15.1

// 다른 버전 설치
$ nvm install 14.17.0

// 설치한 버전이 여려개 확인됨
$ nvm ls
-> v10.15.1
   v14.17.0
  
// 사용할 버전 선택
$ nvm use 14.17.0
-> v10.15.1  ( 선택된 상태 )
  v14.17.0  
  
// 완료
$ nvm ls
     v10.15.1
->   v14.17.0

// system 버전 ( default )로 변경 방법
$ nvm alias default system
default -> system
```
**3. npm ( Node Package Manager )**
  - nodeJs로 개발된 프로그램을 편리하게 설치, 업데이트, 삭제해주는 프로그램
    ( nodeJs로 작성된 package를 관리해주는 프로그램 )
  - nodeJs 설치 시 자동 설치됨
```
// npm 설치 확인
$ npm --version
6.14.13
```

**4. Android Studio**
  - SDK, AVD 설정
    1. configure -> SDK Manager 선택
    2. Android SDK의 SDK Platforms에서 Android (Q)버전 선택
    3. show Package Details 체크박스 선택
    4. 아래 그림과 같이 항목 체크 후 Apply 클릭
    ![image](https://user-images.githubusercontent.com/53929446/122508589-278bfc00-d03d-11eb-875e-46478aae2e91.png)
    5. configure -> AVD Manager 선택 ( Virtual devices )
    6. Create Virtual Device 클릭
    7. Phone에서 선택

  - 환경 변수 설정
```
// vi editor 
$ vi ~/.bash_profile

// insert mode로 변경
$ i

// 환경 변수 설정할 아래의 코드 입력
// ANDROID_HOME의 주소와 Android Studio의 Android SDK Location 과 같아야 함
export ANDROID_HOME=/Users/mac/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools

// ecs 누르고 :wq 입력하여 저장
$ esc
$ :wq

// 재시작
$ source ~/.bash_profile

// 환경 변수 설정 확인
$ adb
Android Debug Bridge version 1.0.41
Version 31.0.2-xxxxxxx
```

**5. JAVA**
  - JDK ( JAVA Development Kit ) 설치
    - orcle java 검색하여 JDK 다운받아 설치
      - 오라클 Java SE 유상 버전
        - Java6 version 45 이후 (6u45~)
        - Java7 version 80 이후 (7u80~)
        - Java8 version 211 이후 (8u211~)
        - Java11이후 버전 모두 (11, 12, 13, 14, 15)

      - 오라클 Java 무료 버전
        - Java SE 4: 1.4.2._30
        - Java SE 5: 1.5.22
        - Java SE 6: 1.6.45
        - Java SE 7: 1.7.80
        - Java SE 8: 1.8.0_202

        - 무료버전은 아래의 링크에서 다운
          - https://www.oracle.com/java/technologies/oracle-java-archive-downloads.html
 ```
 // Java 설치 확인
 $ java -version
 java xx.x.x
 
 // JDK 위치로 이동
 $ cd /Library/Java/JavaVirtualMAchines/
 $ ls
 jdk-xx.x.x.jdk
 ```
 
**6. XCode**
  - App Store에서 Xcode 검색 후 설치
    - Mac OS 버전에 따라 Xcode 사용할 수 있는 버전이 다름
    - 현재 Mac OS가 v10.12.6으로 Xcode는 v8.3.3 사용 가능
      ( cocoaPod 설치 시 v9.2로 업데이트하라고 경고 -> OS v10.12.6으로 **v9.2**까지 사용 가능 )
  - Xcode -> Preferences -> Locations 에서 Command Line Tools가 선택되어 있는지 확인
  - macOS는 기본적으로 gcc, make와 같은 컴파일 도구가 설치되어 있지 않기 때문에 명령어 도구 Command Line Tools를 설치해야 합니다. 예전에는 Xcode를 전체 설치하고 추가로 명령어 도구를 설치해야 했으나 Xcode용량이 꽤 크고 모든 사람이 IDE가 필요한 게 아니기 때문에 명령어 도구만 따로 설치할 수 있게 변경되었습니다.
  
 ```
// homebrew를 설치하면 자동으로 Xcode 명령어 도구를 설치함. 따로 설치하지 않아도 됨.
$ xcode-select --install

 ```
 
  - homebrew
brewhomebrew는 각종 커맨드라인 프로그램과 일반 프로그램(크롬..)을 손쉽게 설치해주는 맥용 패키지 매니저입니다.(최근에 리눅스도 지원하기 시작했습니다.) 리눅스의 apt나 yum과 비슷하며 brew외에 MacPorts 라는 패키지 메니저가 있는데 몇몇 단점으로 요즘은 거의 brew를 사용하는 추세입니다. 다양한 프로그램을 복잡한 빌드과정 없이 손쉽게 설치할 수 있고 업데이트, 관리도 간단하므로 안쓸 이유가 없는 필수 프로그램입니다. 
 
```
// 설치
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

// 확인
# brew test
$ brew doctor
Your system is ready to brew.

```

**7. Visual Studio Code**
  - mac용으로 다운받아 설치
  - v1.56.2
  
**8. CocoaPod**
  - Objective-C, Swift로 개발된 오픈 라이브러리들을 내프로젝트에 간편하게 확장시킬 수 있도록 도와주는 iOS용 프로그램
  - 설치
 ```
$ sudo gem install cocoapods
// 설치 중 에러가 발생하면 os 버전과 xcode 버전에 맞는 cocoapods 특정 버전을 설치해야 함
// $ sudo gem install cocoapods -v 1.8.4

// "sudo gem install cocoapods"로 설치시 오류가 발생
// rudy의 버전 문제인 듯 추측. 간단한 해결방법은 brew를 사용하여 cocoapods를 설치 
// $ brew cleanup -d -v
// $ brew install cocoapods
// 링크 관련하여 오류 발생시 "brew link cocoapods" 실행이 필요할 수 있음
// => Xcode 버전 9.2로 업데이트하라고 경고뜸
//    Xcode 버전 9.2 os 사양 10.12.6 및 이후 버전으로 설치하면 됨

// 버전 확인
$ pod --version
1.10.1
```

**9. React Native CLI**
  - 설치
 ```
 // 설치
$ npm install -g react-native-cli
// MAC 터미널에서 npm install 사용 시 EACCES 에러 권한오류가 발생하면
// sudo ( 관리자 권한 ) 명령어를 붙여주면 정상동작함

// $ sudo npm install -g react-native-cli

// 버전 확인
$ react-native --version
2.0.1
 ```

#### Simulator 구동
- **프로젝트 생성**
```
// home 디렉토리
$ cd 

// react-native 폴더 생성
$ cd mkdir react-native

// react_native_project 프로젝트 생성
// 강의에서는 0.61.5로 사용하지만 Xcode 버전이 낮아 실행되지 않음
$ react-native init **-version 0.59.4** react_native_project


// 생성한 프로젝트 폴더로 이동
$ cd react_native_project

// 새로운 프로젝트를 시작할 때는 최신 버전을 권장하지만, 기존 프로젝트를 이어 받을 때는 버전에 주의
$ react-native init [project name] // 최신 버전
$ react-native init -version 0.59.4 [project name] // 특정 버전 설치

// 생성한 프로젝트 폴더로 이동
$ cd [project name]
```
  - 프로젝트 생성 시 에러 발생할 경우
```
UnhandledPromiseRejectionWarning: Error: Failed to install CocoaPods dependencies for iOS project, which is required by this template. Please try again manually: "cd ./react_native_project/ios && pod install".

// 위와 같이 에러 발생할 경우 지시한 대로 실행
$ cd ./react_native_project/ios
$ pod install
```

```
// pod install 시 아래와 같은 에러 발생 시 
// => Xcode 인식이 되지 않은 문제로 Xcode.app 를 Xcode_9.2.app으로 이름 변경 후 1번이나 2번 수행 후 pod install
//   => 1. Xcode -> Preferences -> Locations 에서 Command Line Tools가 선택
//   => 2. $ sudo xcode-select --switch /Applications/Xcode_9.2.app 

[!] /bin/bash -c set -e 
#!/bin/bash 
# Copyright (c) Facebook, Inc. and its affiliates. 
# 
# This source code is licensed under the MIT license found in the 
# LICENSE file in the root directory of this source tree. 
set -e 

PLATFORM_NAME="${PLATFORM_NAME:-iphoneos}" 
CURRENT_ARCH="${CURRENT_ARCH}" 

...

xcrun: error: SDK "iphoneos" cannot be located 
xcrun: error: unable to lookup item 'Path' in SDK 'iphoneos' /Users/jaeseok-pc/Library/Caches/CocoaPods/Pods/Release/Flipper-Glog/0.3.6-1dfd6/missing: Unknown `--is-lightweight' option 
Try `/Users/jaeseok-pc/Library/Caches/CocoaPods/Pods/Release/Flipper-Glog/0.3.6-1dfd6/missing --help' for more information 
configure: WARNING: 'missing' script is too old or missing 
configure: error: in `/Users/jaeseok-pc/Library/Caches/CocoaPods/Pods/Release/Flipper-Glog/0.3.6-1dfd6': 
configure: error: C compiler cannot create executables 
See `config.log' for more details
```
   
  - add 폴더하여 생성한 프로젝트 불러오기

- **iOS Simulator 구동**
  - 프로젝트 구동
```
// vs code 터미널에서 
$ npm start

// simulator 구동, 새로운 터미널에서 입력
$ react-native run-ios

// react-native run-ios 에러 시
 ( Failed to build iOS project. We ran "xcodebuild" command but it exited with error code 65. 
   import <UIKit/UIUserActivity.h/> 에러 )
=> 현재 Xcode 버전이 낮아 되지 않음 Xcode 10.2.1 이상으로 사용해야하지만 MacOs 버전이 낮아 사용하지 못함
  해서 react-native 버전을 0.59.4로 사용해야 됨
  
  $ react-native init -version 0.59.4 react_native_project
```
  - simulator 단축키
    - command + R : 수정된 코드를 반영시키는 단축키 ( reload )
    - reload하지 않고 코드 저장 시 바로 반영 시키는 방법
      - command + D -> Enable Fast Refresh 선택

  - 다른 simulator 구동
```
// simulator 구동한 터미널에서 입력
$ react-native run-ios --simulator="iPhone 8 Plus"
```
    - device 모델명
      - hardware -> Device -> iOS 13.3 에 들어가면 있음
      
- **Android Simulator 구동**

















