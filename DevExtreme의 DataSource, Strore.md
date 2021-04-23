## DevExtreme

### Data Layer
- DevExtreme 프레임 워크
  - 데이터를 읽고 쓸 수있는 일련의 보완 구성 요소 인 데이터 계층이 포함됨
  - 핵심 데이터 레이어 개체
    - DataSource 및 Stores
    
 - DataSource와 Store가 상호 작용하는 방식
![](https://js.devexpress.com/Content/images/doc/20_2/PhoneJS/scheme-data-layer.png)

### DataSource
- 데이터 작업을 단순화하기 위한 것으로 정렬, 그룹화, 필터링을 유지하고 데이터 변환 속성을 유지하고 데이터가로드 될 때마다 적용하는 stateful object 임
  - stateful 
    - 유지 관리하는 memory (state)가 있음
    
```javascript
// 함수에 의해 state가 유지됩   

private int _number = 0; //initially zero 

function int addOne()
{
    _number++;
    return _number;
}
```
- DataSource 기본 데이터 액세스 logic은 저장소에서 격리됨

### Strore
- 데이터를 읽고 수정하기 위한 범용 인터페이스를 구현하는 stateless object 임
  - stateful 
    - 유지 관리하는 memory (state)가 없음
    
```javascript
// state는 함수에 전달되는 것에 의해 파생됩    

function int addOne(int number)
{
    return number + 1;
}
```
- 각 store에는 동일한 메소드 세트가 있음
