## 30장. React

### Hook

> #### useMemo()
> - 연산한 값 재사용
> - 함수와 관련 없는 값의 변경으로 컴포넌트가 리렌더링될 경우에도 함수가 동작되는 비효율적인 상황을 useMemo()를 사용하여 해결
> > - 특정 값이 변경될 때만 함수를 실행해서 연산을 처리하도록 하고 특정 값이 바뀌지 않았을 때 리렌더링하면 이전에 만든 값을 재사용하여 사용할 수 있게 해줌
> - return 값을 기억
> - 숫자, 문자, 객체처럼 일반 값을 재사용 시 효율적임

> #### useCallback()
> - 함수가 렌더링 될 때마다 재생성 되는 것을 방지
> - 자식 컴포넌트에 함수를 props로 내릴 때는 useCallback을 반드시 사용 ( 자식 리렌더링 방지 )
> - 함수 reference를 기억
> - 함수 재사용 시 효율적

> #### React.memo()
> -	컴포넌트의 props가 변경되지 않으면 리렌더링하지 않도록 설정하여 리렌더링 성능을 최적화 시킴

> - 컴포넌트 성능 최적화 ( 함수가 계속 만들어지는 상황 방지 )
> > - useState의 함수형 업데이트 사용

```javascript
const [number, setNumber] = useState(0);

const onIncease = useCallback( ()=>{
  setNumber(number + 1);
 }, [number] );
```

```javascript
// 함수형 업데이트 사용
const [number, setNumber] = useState(0);

const onIncease = useCallback( ()=>{
  setNumber( number => number + 1);
 }, [])
```

### styled-components

> #### polished
> > - 스타일 관련 유틸 함수
> > > - lighten(), darken(), ... 같은 함수 사용
> > > - $ yarn add polished 설치하여 사용
> > - 

```javascript
 background: ${lighten(0.1, '#228be6')};
 
 background: ${darken(0.1, '#228be6')};
```

```css
 background: ${lighten(0.1, '#228be6')};
 
 background: ${darken(0.1, '#228be6')};
```





