# 💡 strict mode

### ✔ strict mode란?
```
function foo() {
  x = 10;
}
foo();

console.log(x); // 10
```
- 자바스크립트 엔진은 foo 함수의 스코프에서부터 출발하여 전역 스코프까지 x를 찾게 된다
- 어디에도 없는 x 변수로 인해 에러가 발생할 것 같지만 자바스크립트 엔진은 암묵적으로 전역 객체에 x 프로퍼티를 동적 생성한다
- 이때 전역 객체의 x 프로퍼티는 마치 전역 변수처럼 사용할 수 있고, 이러한 현상을 암묵적 전역이라 한다
- strict mode는 자바스크립트 언어의 문법을 좀 더 엄격히 적용하여 오류를 발생시킬 가능성이 높거나 자바스크립트 엔진의 최적화 작업에 문제를 일으킬 수 있는 코드에 대해 명시적인 에러를 발생시킨다

### ✔ strict mode의 적용
- strict mode를 적용하려면 전역의 선두, 혹은 함수 몸체의 선두에 `'use strict';`를 추가한다

### ✔ 전역에 strict mode를 적용하는 것은 피하자
- 전역에 적용한 strict mode는 스크립트 단위로 적용된다
- strict mode 스크립트와 non-strict mode 스크립트를 혼용하는 것은 오류를 발생시킬 수 있다
- 특히, 외부 서드파티 라이브러리를 사용하는 경우 라이브러리가 non-strict mode인 경우도 있기 때문에 전역에 strict mode를 사용하는 것은 바람직하지 않다

### ✔ 함수 단위로 strict mode를 적용하는 것도 피하자
- 어떤 함수는 strict mode를 적용하고, 어떤 함수는 적용하지 않는 것도 바람직하지 않다 또한 일일히 적용하는 것이 번거롭기도 하다.
```
(function() {
  var let = 10; // non-strict mode에서는 에러가 발생하지 않음
  function foo() {
    'use strict';
    let = 20 // syntaxError
  }
  foo();
};)()
```

### strict mode가 발생시키는 에러
- strict mode를 적용했을 때 에러가 발생하는 대표적인 사례

#### 1. 암묵적 전역
- 선언하지 않은 변수를 참조하면 ReferenceError가 발생한다
```
(function () {
  'use strict';
  
  x = 10;
  console.log(x); // ReferenceError
})()
```

#### 2. 변수, 함수, 매개변수의 삭제
- delete 연산자로 변수, 함수, 매개변수를 삭제하면 SyntaxError가 발생한다
```
(function () {
  'use strict';
  
  x = 10;
  delete x; // SyntaxError
})()
```

#### 3. 매개변수 이름의 중복
- 중복된 매개변수 이름을 사용하면 SyntaxError가 발생한다
```
(function () {
  'use strict';
  
  // SyntaxError
  function foo(x, x) {
    return x + x;
  }
  console.log(foo(1, 2));
})()
```

#### 4. with문의 사용
- with 문을 사용하면 SyntaxError가 발생한다
- with 문은 전달된 객체를 스코프 체인에 추가한다
- with문은 동일한 객체의 프로퍼티를 반복해서 사용할 때 객체 이름을 생략할 수 있어서 코드가 간단해지는 효과가 있지만, 성능과 가독성이 나빠지는 문제가 있다
```
(function () {
  'use strict';
  
  // SyntaxError
  with({x: 1}) {
    console.log(x);
  }
})()
```

### ✔ strict mode 적용에 의한 변화

#### 1. 일반 함수의 this
- strict mode에서 함수를 일반 함수로서 호출하면 this에 undefined가 바인딩된다
- 생성자 함수가 아닌 일반 함수 내부에서는 this를 사용할 필요가 없기 때문이다, 이때 에러는 발생하지 않는다

#### 2. arguments 객체
- strict mode에서는 매개변수에 전달된 인수를 재할당하여 변경해도 arguments 객체에 반영되지 않는다
- 초기값을 유지하는 듯 하다.
```
function foo(a) {
  'use strict';
  
  a = 2;
  console.log(arguments); // {0: 1, length: 1}
}

foo(1);
```