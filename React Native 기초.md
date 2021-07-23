## React Native

### React Native 기초
- React Native에서 hook은 v0.59 이상부터 사용 가능

#### React Native Component
- View
  - 다른 컴포넌트 감싸는 역할로 div 요소 와 동일한 것임
  - 중첩 사용 가능
 
- Text
  - text를 사용하기 위해선 Text 컴포넌트로 감싸서 사용해야함

- styleSheet
  - 

```
<View style={styles.mainView}>
  ...
</View>
const styles = StyleSheet.create({
  mainView : { ... }
})
```

Picker
- selectBox 기능

// 설치 react-native v0.59은 picker v1.15.0 사용해야됨
$ npm install @react-native-picker/picker@1.15.0 --save

ios 디렉토리에서  
$ npx pod-install
=> cocoapods is not supported in this project

$ pod init
=> Podfile 생성됨

$ npx pod-install
=> The target '프로젝트명-tvOSTests' is declared multiple times.

Podfile 열어서 아래 부분 주석처리 후 저장
```
target '프로젝트명-tvOS' do
  ...
 # target '프로젝트명-tvOSTests' do
 #   ...
 # end
end 
```
// 다시 실행
$ npx pod-install
=> 성공

// React-Native 0.60 미만 실행
$ react-native link @react-native-picker/picker

Picker 코드 기입 후 ios 시뮬레이터 실행
```
import {Picker} from '@react-native-picker/picker';
...

<Picker
  selectedValue={selectedLanguage}
>
  <Picker.Item label="Java" value="java" />
  <Picker.Item label="JavaScript" value="js" />
</Picker>
```

$ npm start
$ react-native run-ios

=> Picker 렌더링되지 않음...


ActivityIndicator
- loading 이미지 사용

Image
- 이미지 렌더링
  ```
  <Image 
     source={EImage}       // 로컬에서 이미지 가져올 경우
     source={{uri:"주소"}}  // 서버에서 이미지 가져올 경우
  />
  ```

#### React Navigation

```
// 설치
$ npm install @react-navigation/native

// dependencies 설치
$ npm install react-native-reanimated react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view

React Native v0.60 미만 시 link 해줘야됨
참조 https://reactnavigation.org/docs/getting-started/

// ios 디렉토리에 가서 pod install 실행
$ cd ios
$ npx pod-install ios
$ cd ../

// App.js에 import 
import 'react-native-gesture-handler';

stack navigator library 설치
$ npm install @react-navigation/stack

drawer navigator library 설치
$ npm install @react-navigation/drawer

tab navigator library 설치
$ npm install @react-navigation/bottom-tabs

```
- NavigationContainer
  - 네비게이션 구조랑 상태 관리하는 컴포넌트
  - 모든 네비게이션 구조는 NavigationContainer 태그 안에 들어가야 함
  
- createStackNavigation()
  - 스크린, 네비게이터 프로퍼티를 리턴하는 함수
  - Header Bar 사용
 
 ```
 import { createStackNavigation } from "@react-navigation/stack"
 
 const Stack = createStackNavigation()
 
 ...
 
 <NavigationContainer>
  <Stack.Navigator>                              // stack navigator로 동작하는 부분이라고 알려주는 구분자
    <Stack.Screen name="Home" component={Home}/> // stack navigator로 동작하는 화면이 추가될 
  </Stack.Navigator>
 </NavigationContainer>
 ```

 - createDrawerNavigation()
  - 스크린, 네비게이터 프로퍼티를 리턴하는 함수
  - Side Bar 사용
  - Header Bar 와 같이 사용할 수 없음
  
 ```
 import { createDrawerNavigation } from "@react-navigation/drawer"
 
 const Drawer = createDrawerNavigation()
 
 ...
 
 <NavigationContainer>
  <Drawer.Navigator>                              // Drawer navigator로 동작하는 부분이라고 알려주는 구분자
    <Drawer.Screen name="Home" component={Home}/> // Drawer navigator로 동작하는 화면이 추가될 
  </Drawer.Navigator>
 </NavigationContainer>
 ```


 - createBottomTabNavigation()
  - 스크린, 네비게이터 프로퍼티를 리턴하는 함수
  - 화면 상단이나 하단에 tab을 생성해서 터치 시 해당 스크린으로 이동하게 도와주는 네비게이터

 ```
 import { createBottomTabNavigation } from "@react-navigation/bottom-tabs"
 
 const Tab = createBottomTabNavigation()
 
 ...
 
 <NavigationContainer>
  <Tab.Navigator>                              // Drawer navigator로 동작하는 부분이라고 알려주는 구분자
    <Tab.Screen name="Home" component={Home}/> // Drawer navigator로 동작하는 화면이 추가될 
  </Tab.Navigator>
 </NavigationContainer>
 ```

- Vector Icon
  - icon 통일성을 위해 사용
 
```
https://github.com/oblador/react-native-vector-icons

// 설치
$ npm install --save react-native-vector-icons


// IOS
1. Xcode에서 프로젝트 오픈
2. 프로젝트 이름 폴더에서 마우스 우클릭 -> New Group -> Fonts 폴더 생성
3. 프로젝트 폴더 -> node_modules -> react-native-vector-icons -> Fonts -> Ionicons.ttf 파일을 2번에서 생성한 폴더로 옮김
  - Add to taegets 에서 프로젝트 이름 파일 선택 ( Tests, -tvOS, -tvOSTests 아님 )
4. Xcode의 프로젝트 이름 폴더에 있는 info.plist 선택 -> Information Property List에 Fonts Provided by application 입력 후 그 안에 있는 item 0 의 value에 Ionicons.ttf 입력
5. shift + commend + k 눌러서 clean
6. commend + b 눌러서 빌드하기

// Android
1. Vsconde에서 프로젝트 경로에서 android/app/build.gradle 파일의 맨 아래에 아래 코드 추가하여 저장

project.ext.vectoricons = [
    iconFontNames: [ 'Ionicons.ttf' ] // Name of the font files you want to copy, 추가할 ttf 파일 입력
]

apply from: "../../node_modules/react-native-vector-icons/fonts.gradle"

2. android/settings.gradle 파일의 맨 아래에 아래 코드 추가하여 저장

include ':react-native-vector-icons'
project(':react-native-vector-icons').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-vector-icons/android')

3. android/app/build.gradle 파일의 dependencies 에 아래 코드 추가

dependencies {
 ...
 implementation project(':react-native-vector-icons')
}


// iOS, Android 설치 후 컴포넌트에서 Icon import해서 사용

import Icon from "react-native-vector-icons/dist/Ionicons"

```
  - icon 확인 및 사용 방법
    1. https://github.com/oblador/react-native-vector-icons 주소에서 Bundled Icon Sets의 Browse All에 들어가서 Icon 확인
    2. home 검색
    3. Ionicons 에 있는 icon들의 icon name 사용 ( 예) home_outline
    4. 아래와 같이 Ionicons 태그로 사용하여 icon 렌더링

```
<Ionicons name="home_outline" size={20} />
```

- navigator 혼합 사용
  - Stack, Tab 혼합
    - 아래와 같은 구조로 사용 가능
      ```
      Stack Navigator
        - Tab Navigator
          - Tab Screen 1
          - Tab Screen 2
          - Tab Screen 3
        - Stack Screen 1
        - Stack Screen 2
      ```

















