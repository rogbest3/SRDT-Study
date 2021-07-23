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
npm install @react-navigation/drawer

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

