## JavaScript 문법

### 1. 삼항연산자

- 삼항연산자는 2중 중복 가능하지만 코드상 보기 힘드니 한번만 사용을 권장

### 2. Truthy와 Falsy

> Truthy : true로 평가되는 값
> - true, {}, [], 1, "0", "false", new Date(), -1, 12n, 3.14, Infinity, -Infinity

> Falsy : false로 평가되는 값 
> - false, 0, -0, 0n, -0n, "", '', ``, null, undefined, NaN, 문자 :

### 3. 단축 평가 논리 계산법
> AND 연산자
  - 연산자 앞에 오는 값이 **truthy**한 값일 경우 연산자 **뒤**에 값을 출력
```
  true && "dog"
  => dog 출력

  "hello" && "dog"
  => dog 출력
```       
> - 연산자 앞에 오는 값이 **falsy**한 값일 경우 연산자 **앞**에 값을 출력
```
  false && "dog"
  => false 출력

  0 && "dog"
  => 0 출력
```
> OR 연산자
> - 해당 값이 없을 경우 다른 값을 줄 때 사용을 많이 사용함

> - 연산자 앞에 오는 값이 **truthy**한 값일 경우 연산자 **앞**에 값을 출력
```
  true || "dog"
  => true 출력

  "hello" || "dog"
  => dog 출력
```        
> - 연산자 앞에 오는 값이 **falsy**한 값일 경우 연산자 **뒤**에 값을 출력
```
  false || "dog"
  => dog 출력

  0 || "dog"
  => dog 출력
```        
> 단축 코드 예시
```javascript
const getName = (animal) => {
  const name = animal && animal.name;
  if (!name) {
    return "이름 없음";
  }
  return name;
};
```  
> => 코드 단축
```javascript
  const getName = (animal) => {
    const name = animal && animal.name;
    
    return name || "이름 없음"
  };
```
