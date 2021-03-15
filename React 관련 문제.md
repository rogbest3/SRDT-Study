## React 관련 문제

### LifeCycle 함수 두번 호출
> - StrictMode에서 호출시 자동으로 문제를 찾아주는것은 불가능하다. 하지만 조금 더 부작용을 예측할 수 있게끔 만들어서 문제가 되는 부분을 발견할 수 있도록 도와준다. 그래서 React는 아래의 함수를 의도적으로 두번씩 호출한다.
* 클래스 컴포넌트의 constructor, render 그리고 shouldComponentUpdate 메서드
  + 클래스 컴포넌트의 getDerivedStateFromProps static 메서드
  - 함수 컴포넌트 바디
  * State updater 함수 (setState의 첫 번째 인자)
> > - useState, useMemo 그리고 useReducer에 전달되는 함수
 
> > * Strict 모드는 개발 모드에서만 활성화되기 때문에, 프로덕션 빌드에는 영향을 끼치지 않습니다

```react
  ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root'),
);
```
> > * <React.StrictMode> 삭제하면 문제 해결
