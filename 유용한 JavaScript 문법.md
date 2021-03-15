## 유용한 JavaScript 문법

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
> - 함수의 파라미터 사용 시 함수 호출 때 파라미터를 넣어 주지 않았을 경우 에러 방지하기 위한 코드
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

### 6. 비구조화 할당 ( 구조 분해 )
> 1. 함수의 파라미터 비구조 할당 기본 값 설정 ( 값이 없을 경우 에러 방지하기 위한 코드 )
> 
```javascript
  const object = { a: 1, b : 2 }
 
  const print = ({ a, b }) => {
    console.log(a);
    console.log(b);
  };

  print(object);
```
> 
```javascript
  const object = { a: 1 }
  
  const print = ({ a, b = 2 }) => {
    console.log(a);
    console.log(b);
  };

  print(object);
```

> - 비구조 할당 기본 값 설정
```javascript
  const object = { a: 1 }
  
  const { a, b = 2 } = object;
  
  console.log(a);
  console.log(b);
```


> 2. 비구조 할당 시 이름 변경
```javascript
  const animal = {
    name: "댕댕이",
    type: "개",
  };
  const nickname = animal.name;

  console.log(nickname);
```

```javascript
  const animal = {
    name: "댕댕이",
    type: "개",
  };

  // 앞에는 원래 이름, 뒤에는 새로 짓는 이름
  const { name: nickname } = animal;

  console.log(nickname);
```

> 3. 배열 비구조 할당
```javascript
  const array = [1];

  const { one, two = 2 } = array;

  console.log(one);
  console.log(two);
```

> 4. 객체의 깊은 값 확인
```javascript
  const deepObject = {
    state: {
      information: {
        name: "velopert",
        languages: ["korean", "english", "chinese"],
      },
    },
    value: 5,
  };

  const { name, languages } = deepObject.state.information;
  const { value } = deepObject;

  // 특정 객체를 만들 때 특정 key로 선언된 값이 이미 있으면 name : name에서 value 값 설정( : name )을 생략해도 됨
  const extracted = {
    name,
    languages,
    value,
  };
  console.log(extracted);
```
> - 비구조화 할당 한번에 여러값 확인
```javascript
  const deepObject = {
    state: {
      information: {
        name: "velopert",
        languages: ["korean", "english", "chinese"],
      },
    },
    value: 5,
  };

  const {
    state: {
      // information: { name, languages },
      information: {
          name,
          languages: [firstLang, secondLang],
        },
      value,
    },
  } = deepObject

  // 특정 객체를 만들 때 특정 key로 선언된 값이 이미 있으면 name : name에서 value 값 설정( : name )을 생략해도 됨
  const extracted = {
    name,
    // languages,
    firstLang,
    secondLang,
    value,
  };
  console.log(extracted);
```

### 7. spread와 rest - spread 연산자 ( 특정 객체나 배열의 값들을 퍼트림 ) 
> 1. 기존에 만들었던 객체를 참고하여 새로운 객체를 만들 경우
> 
```javascript
  const slime = {
    name: "슬라임",
  };
  const cuteSlime = {
    name: "슬라임",
    attribute: "cute",
  };
  const purpleCuteSlime = {
    name: "슬라임",
    attribute: "cute",
    color: "purple",
  };
  console.log(slime);
  console.log(cuteSlime);
  console.log(purpleCuteSlime);
```

> - spread를 사용하지 않고 프로퍼티 추가로 만든 객체는 같음 ( slime === purpleCuteSlime, 서로 같은 객체 )
```javascript
  const slime = {
    name: "슬라임",
  };
  const cuteSlime = slime;
  cuteSlime.attribute = "cute";

  const purpleCuteSlime = cuteSlime;
  purpleCuteSlime.color = "purple";
  
  console.log(slime);
  console.log(cuteSlime);
  console.log(purpleCuteSlime);
```

> - spread를 사용해 만든 객체는 같지 않음 ( slime !== purpleCuteSlime, 서로 다른 객체 )
```javascript
  const slime = {
    name: "슬라임",
  };
  const cuteSlime = {
    ...slime,
    attribute: "cute",
  };
  const purpleCuteSlime = {
    ...cuteSlime,
    color: "purple",
  };
  console.log(slime);
  console.log(cuteSlime);
  console.log(purpleCuteSlime);
```

> 2. 기존에 만들었던 배열을 참고하여 새로운 배열을 만들 경우
```javascript
  const animals = ["고양이", "개", "너구리"];
  const anotherAnimals = [...animals, "참새"];
  // const anotherAnimals = animals.concat("참새");

  console.log(animals);
  console.log(anotherAnimals);
```

> 3. spreat 연산자 중복 사용
```javascript
  const numbers = [1, 2, 3, 4, 5];

  const spreadNumbers = [...numbers, 1000, ...numbers];

  console.log(spreadNumbers);
  // [1, 2, 3, 4, 5, 1000, 1, 2, 3, 4, 5] 출력
```


### 8. spread와 rest - rest ( 특정 객체나 배열의 값들을 모음 ) 
> 1. 기존에 만들었던 객체의 특정 값을 제외한 나머지 값들을 모음
> 
```javascript
  const purpleCuteSlime = {
    name: "슬라임",
    attribute: "cute",
    color: "purple",
  };
  
  const { color, ...cuteSlime } = purpleCuteSlime;

  console.log(color);
  // purple 출력
  console.log(cuteSlime);
  // {name: "슬라임", attribute: "cute"} 출력

  const { attribute, ...slime } = cuteSlime;

  console.log(attribute);
  // cute 출력
  console.log(slime);
  // {name: "슬라임"} 출력
```

> 2. 기존에 만들었던 배열의 특정 값을 제외한 나머지 값들을 모음
> 
```javascript
  const numbers = [0, 1, 2, 3, 4, 5, 6];

  // 주의 사항 - 배열에서 ...rest는 맨 마지막에 와야됨
  const [one, two, ...rest] = numbers;

  console.log(one);
  // 0 출력
  console.log(two);
  // 1 출력
  console.log(rest);
  // [1, 2, 3, 4, 5, 6] 출력
```

### 9. spread와 rest - 함수 파라미터에서의 rest 
> - 여러 값을 파라미터로 받아 작업을 수행하는 경우
> 
```javascript
  const sum = (a, b, c, d, e, f, g) => {
    let result = 0;
    if (a) result += a;
    if (b) result += b;
    if (c) result += c;
    if (d) result += d;
    if (e) result += e;
    if (f) result += f;
    if (g) result += g;
    return result;
  };
  
  console.log(sum(1, 2, 3, 4, 5, 6, 7, 8));
  // 28 출력 ( 1 ~ 7까지 더한 값 )
```
> - 파라미터를 ...rest로 받으면 하나의 배열로 만들어 받음
```javascript
  const sum = (...rest) => {
    return rest.reduce((acc, current) => acc + current, 0);
  };
  
  console.log(sum(1, 2, 3, 4, 5, 6, 7, 8));
  // 36 출력 ( 1 ~ 8까지 인자를 전부 더한 값 )
```

### 10. spread와 rest - 함수 인자에서의 spread 
> - 여러 값을 인자로 넘겨주는 작업을 수행하는 경우
> 
```javascript
  const sum = (...rest) => {
    return rest.reduce((acc, current) => acc + current, 0);
  };
  
  const numbers = [1, 2, 3, 4, 5, 6, 7, 8];
  console.log(sum(...numbers));
```

```javascript
    const subtract = (x, y) => {
      return x - y;
    };
    const numbers1 = [1, 2];
    const result = subtract(...numbers1);
    // const result = subtract(numbers[0], numbers[1])
    
    console.log(result);
```

### 10-1. spread와 rest - max() 코딩
> - 숫자 n개의 인자가 주어질 경우 최대 값 출력
```javascript
  const max = (...rest) => {
    return rest.reduce((max, current) => Math.max(max, current, 0));
  };
  const numbers = [1, 2, 10, 3, 20, 8, 9]; 
  console.log(...numbers);
  // 20 출력
```

### 11. Scope
> - 선언한 해당 변수 또는 함수의 유효한 범위
> > * global scope ( 전역, 모든 곳에서 사용 가능 ) 
> > * function scope ( 특정 함수 내부만 사용 가능 )
> > * block scope ( if, for 같은 {}로 감싸진 block 내부에서만 사용 가능 )
> - 예시 1
```javascript
  // global scope
  const value = "hello";

  const myFunction = () => {
    console.log("myFunction : ", value);
  };

  const otherFunction = () => {
    // function scope
    const value = "bye";
    console.log("otherFunction : ", value);
  };

  myFunction();
  // hello 출력
  otherFunction();
  // bye 출력

  console.log("global scope : ", value);
  // hello 출력
```

> - 예시 2
```javascript
  const value = "hello";

  const myFunction = () => {
    const value = "bye";
    const anotherValue = "world";

    const functionInside = () => {
      console.log("functionInside : ", value, anotherValue);
      // hello world 출력
    };

    functionInside();
  };

  myFunction();

  console.log("global scope : ", value);
  // hello 출력
  console.log(anotherValue);
  // is not definde 에러
```

> - 예시 3
```javascript
  const value = "hello";

  const myFunction = () => {
    const value = "bye";

    if (true) {
      const value = "world";
      console.log("block scope : ", value);
      // world 출력
    }
    console.log("function scope : ", value);
    // bye 출력
  };

  myFunction();
  console.log("global scope : ", value);
  // hello 출력
```

> - 예시 4
> > * var를 사용하여 변수를 선언한 경우 변수 명이 같으면 scope 구분이 정확하게 나뉘지 않게 될 수 있으니 const나 let으로 사용
> > * if block에서 선언한 변수의 scope가 block scope가 아니라 function scope로 변경되어 기존의 있는 값에 영향이 감
```javascript
  var value = "hello";

  const myFunction = () => {
    var value = "bye";

    if (true) {
      var value = "world";
      console.log("block scope : ", value);
      // world 출력
    }
    console.log("function scope : ", value);
    // world 출력
  };

  myFunction();
  console.log("global scope : ", value);
  // hello 출력
```

### 11. Hoisting
> - 선언되지 않은 함수, 변수를 끌어올려서 사용하는 작동 방식
> > * const나 let은 호이스팅이 발생하지 않지만 var, function은 호이스팅 발생함
> > * 호이스팅은 코드 헷갈림, 유지보수, 의도치 않은 동작 등 좋지 않기 때문에 피해야 함
