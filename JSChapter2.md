## JavaScript 문법

### 1. 삼항연산자

- 삼항연산자는 2중 중복 가능하지만 코드상 보기 힘드니 한번만 사용을 권장

### 2. Truthy와 Falsy

> Truthy : true로 평가되는 값
> true, {}, [], 1, "0", "false", new Date(), -1, 12n, 3.14, Infinity, -Infinity

> Falsy : false로 평가되는 값 
> false, 0, -0, 0n, -0n, "", '', ``, null, undefined, NaN, 문자 :

### 3. 단축 평가 논리 계산법
> #### AND 연산자
> - 연산자 앞에 오는 값이 **truthy**한 값일 경우 연산자 **뒤**에 값을 출력
> 
```
  true && "dog"
  => dog 출력

  "hello" && "dog"
  => dog 출력
```       

> - 연산자 앞에 오는 값이 **falsy**한 값일 경우 연산자 **앞**에 값을 출력
>
```
  false && "dog"
  => false 출력

  0 && "dog"
  => 0 출력
```

> - 단축 코드 예시
```javascript
const getName = (animal) => {
  if (animal) {
    return animal.name;
  }
  return undefined;
};
```  
> - 코드 단축
```javascript
  const getName = (animal) => {
    return animal && animal.name
  };
```

> #### OR 연산자
> - 특정 값이 없을 경우 다른 값을 줄 때 사용을 많이 사용함

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
> - 단축 코드 예시
```javascript
const getName = (animal) => {
  const name = animal && animal.name;
  if (!name) {
    return "이름 없음";
  }
  return name;
};
```  
> - 코드 단축
```javascript
  const getName = (animal) => {
    const name = animal && animal.name;
    
    return name || "이름 없음"
  };
```

### 4. 함수의 기본 파라미터
> - 함수의 파라미터 사용 시 함수 호출 때 파라미터를 넣어 주지 않았을 경우 에러 방지하기 위해 사용
> 
```javascript
  const calculateCircleArea = (r) => {
    const radius = r || 1;
    return Math.PI * radius * radius;
  };
  
  calculateCircleArea();
```
> - 파라미터 없을 시 기본값으로 r = 1을 사용하는 단축 코드
```javascript
  const calculateCircleArea = (r = 1) => {
    return Math.PI * r * r;
  };
  
  calculateCircleArea();
```

### 5. 스마트한 조건문 사용
> - 특정 값이 여러 값중에 하나인지 확인하는 경우
> 
```javascript
  const isAnimal = (text) => {
    return text === "고양이" || text === "개" || text === "너구리";
  };
```
> - 배열의 내장 함수 includes를 사용한 smart code
```javascript
  const isAnimal = (text) => {
    const animals = ["고양이", "개", "너구리"];

    return animals.includes(text);
  };
```

```javascript
const isAnimal = (text) => ["고양이", "개", "너구리"].includes(text);
```

> - 특정 값에 따라 리턴 값이 다른 경우
```javascript
  const getSound = (animal) => {
    if (animal === "개") return "멍멍";
    if (animal === "고양이") return "야옹";
    if (animal === "참새") return "짹짹";
    return "...?";
  };
```
> - 객체를 사용한 smart code
```javascript
  const getSound = (animal) => {
    const sounds = {
      개: "멍멍",
      고양이: "야옹",
      참새: "짹짹",
    };
    return sounds[animal] || "...?";
  };
```
> - 특정 값에 따라 다른 코드 실행하기 위한 경우
```javascript
  const makeSound = (animal) => {
    const tasks = {
      개: () => {
        console.log("멍멍");
      },
      고양이() {
        console.log("야옹");
      },
      참새() {
        console.log("짹짹");
      },
    };

    const task = tasks[animal];
    if (!task) {
      console.log("...?");
      return;
    }

    task();
  };
  
  makeSound("개")
```























