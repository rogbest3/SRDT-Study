## DevExtreme

### Data Layer
- DevExtreme 프레임 워크
  - 데이터를 읽고 쓸 수있는 일련의 보완 구성 요소 인 데이터 계층이 포함됨
  - 핵심 데이터 레이어 개체
    - DataSource 및 Stores
    
  - DataSource와 Store가 상호 작용하는 방식
![](https://js.devexpress.com/Content/images/doc/20_2/PhoneJS/scheme-data-layer.png)

#### DataSource
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

#### Strore
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
  - load (options) -데이터를 로드. 이 함수는 정렬, 그룹화, 필터링 및 데이터 변환 속성을 지정하는 객체를 받음
  - insert (values) -전달 된 값으로 새 항목을 추가
  - remove (key) - key가 지정한 데이터 항목을 제거
  - update (key, values) - key가 지정하는 데이터 항목에 새 값을 설정
  - byKey (key, extraOptions) - key가 지정하는 데이터 항목을 로드. extraOptions의 인수는 필요한 아이템을 얻기 위해 추가로 구현 속성을 필요로 함
  - totalCount (options) - 로드하지 않고 지정된 조건을 충족하는 항목의 총 개수를 가져올 수 있음. options object는 터링 및 그룹화 속성을 지정하는 필터 및 그룹 필드가 포함될 수 있음.

#### Asynchrony
- data layer의 모든 데이터 전송 작업은 원격 서비스에 대한 액세스이든 로컬 데이터에 대한 액세스이든 비동기식임
- 액세스하는 데이터 소스에 관계없이 범용 Store 인터페이스를 지원하도록 만들어졌음

#### Creating DataSource
- DataSource 인스턴스를 만들려면 DataSource 생성자를 호출하고 필요한 configuration object가 생성자에 전달함 

- 필요한 데이터를 생성중인 DataSource 인스턴스와 연결하는 방법
> - From Array
>   - 필요한 Array을 DataSource 생성자에 전달

```javascript
import DataSource from 'devextreme/data/data_source';
 
const dataSource = new DataSource({
    // array of data
    store: array,
 
    // additional configuration properties
    sort: "name",
    pageSize: 10
});
```

> - From Store
>   - 필요한 Store를 DataSource 생성자에 전달
>   - Store 인스턴스는 store configuration property에 전달
```javascript
import ArrayStore from 'devextreme/data/array_store';
import DataSource from 'devextreme/data/data_source';
 
const store = new ArrayStore({
    key: 'id',
    data: states,
    // Other ArrayStore properties go here
});
 
// ===== or inside the DataSource =====
const dataSource = new DataSource({
    store: new ArrayStore({
        key: 'id',
        data: states,
        // Other ArrayStore properties go here
    }),
    // Other DataSource properties go here
});
```





