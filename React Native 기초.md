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






