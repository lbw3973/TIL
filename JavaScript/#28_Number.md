# 💡 Number
- 표준 빌트인 객체인 `Number`는 원시 타입인 숫자를 다룰 때 유용한 프로퍼티와 메서드를 제공한다

### ✔ Number 생성자 함수
- 표준 빌트인 객체인 `Number`객체는 생성자 함수 객체다. 따라서 `new` 연산자와 함께 호출하여 `Number` 인스턴스를 생성할 수 있다

### ✔ Number 프로퍼티

#### 1. Number.EPSILON
- 1과 1보다 큰 숫자 중에서 가장 작은 숫자와의 차이와 같다
- `Number.EPSILON`은 이러한 오차를 해결하기 위해 사용한다
```
function isEqual(a, b){
  // a와 b를 뺀 값의 절대값이 Number.EPSILON보다 작으면 같은 수로 인정한다
  return Math.abs(a - b) < Number.EPSILON;
}

isEqual(0.1 + 0.2, 0.3); // -> true
```

#### 2. Number.MAX_VALUE
- `Number.MAX_VALUE`는 자바스크립트에서 표현할 수 있는 가장 큰 양수 값이다
- `Number.MAX_VALUE`보다 큰 숫자는 `Infinity`다
```
Number.MAX_VALUE; // -> 1.7976931348623157e+308
Infinity > Number.MAX_VALUE; // -> true
```

#### 3. Number.MIN_VALUE
- `Number.MIN_VALUE`는 자바스크립트에서 표현할 수 있는 가장 작은 양수 값이다
- `Number.MIN_VALUE`보다 작은 숫자는 0이다

#### 4. Number.MAX_SAFE_INTEGER
- `Number.MAX_SAFE_INTEGER`는 자바스크립트에서 안전하게 표현할 수 있는 가장 큰 정수값이다
```
Number.MAX_SAFE_INTEGER; // -> 9007199254740991
```

#### 5. Number.MIN_SAFE_INTEGER
- `Number.MIN_SAFE_INTEGER`는 자바스크립트에서 안전하게 표현할 수 있는 가장 작은 정수값이다
```
Number.MIN_SAFE_INTEGER; // -> -9007199254740991
```

#### 6. Number.POSITIVE_INFINITY
- `Number.POSITIVE_INFINITY`는 양의 무한대를 나타내는 숫자값 `Infinity`와 같다

#### 7. Number.NEGATIVE_INFINITY
- `Number.POSITIVE_INFINITY`는 음의 무한대를 나타내는 숫자값 `-Infinity`와 같다

#### 8. Number.NaN
- `Number.NaN`은 숫자가 아님을 나타내는 숫자값이다
---

### ✔ Number 메서드

#### 1. Number.isFinite
- `Number.isFinite`는 인수로 전달된 숫자값이 정상적인 유한수, 즉 `Intifiny` 또는 `-Infinity`가 아닌지 검사하여 그 결과를 불리언 값으로 반환한다

#### 2. Number.isInteger
- `Number.isInteger`는 인수로 전달된 숫자값이 정수인지 검사하여 그 결과를 불리언 값으로 반환한다

#### 3. Number.NaN
- `Number.NaN` 메서드는 인수로 전달된 숫자값이 `NaN`인지 검사하여 그 결과를 불리언 값으로 반환한다

#### 4. Number.isSafeInteger
- `Number.isSafeInteger` 메서드는 인수로 전달된 숫자값이 안전한 정수인지 검사하여 그 결과를 불리언 값으로 반환한다
- 안전한 정수값은 -(2의 53승 - 1) ~ (2의53승 - 1) 사이의 정수값이다

#### 5. Number.prototype.toExponential
- `Number.prototype.toExponential` 메서드는 숫자를 지수 표기법으로 반환하여 문자열로 반환한다
- 지수 표기법이란 매우 크거나 작은 숫자를 표기할 때 주로 사용하며 **e**앞에 있는 숫자에 10의 n승을 곱하는 형식으로 수를 나타내는 방식이다
```
(77.1234).toExponential();  // -> "7.71234e+1"
(77.1234).toExponential(4); // -> "7.7123e+1"
(77.1234).toExponential(2); // -> "7.71e+1"

77.toExponential(); // -> SyntaxError: Invalid or unexpected token
```

#### 6. Number.prototype.toFixed
- `toFixed` 메서드는 숫자를 반올림하여 문자열로 반환한다
- 반올림하는 소수점 이하 자릿수를 나타내는 0~20 사이의 정수값을 인수로 전달한다
```
(12345.6789).toFixed(); // -> "12346"
// 소수점 이하 1자리수 유효, 나머지 반올림
(12345.6789).toFixed(1); // -> "12345.7"
// 소수점 이하 2자리수 유효, 나머지 반올림
(12345.6789).toFixed(2); // -> "12345.68"
// 소수점 이하 3자리수 유효, 나머지 반올림
(12345.6789).toFixed(3); // -> "12345.679"
```

### 7. Number.prototype.toPrecision
- `toPrecision` 메서드는 인수로 전달받은 전체 자릿수까지 유효하도록 나머지 자릿수를 반올림하여 문자열로 반환한다
- 인수로 전달받은 전체 자릿수로 표현할 수 없을때는 지수 표기법으로 결과를 반환한다
```
// 전체 자리수 유효. 인수를 전달하지 않으면 기본값 0이 지정된다
(12345.6789).toPrecision(); // -> "12345.6789"
// 전체 1자리수 유효, 나머지 반올림
(12345.6789).toPrecision(1); // -> "1e+4"
// 전체 2자리수 유효, 나머지 반올림
(12345.6789).toPrecision(2); // -> "1.2e+4"
// 전체 6자리수 유효, 나머지 반올림
(12345.6789).toPrecision(6); // -> "12345.7"
```

#### 8. Number.prototype.toString
- `toString` 메서드는 숫자를 문자열로 변환하여 반환한다
- 진법을 나타내는 2~36 사이의 정수값을 인수로 전달한다
- 인수 생략시, 기본값은 10진법이 지정된다
```
// 인수를 생략하면 10진수 문자열을 반환한다
(10).toString(); // -> "10"
// 2진수 문자열을 반환한다
(16).toString(2); // -> "10000"
// 8진수 문자열을 반환한다
(16).toString(8); // -> "20"
// 16진수 문자열을 반환한다
(16).toString(16); // -> "10"
```