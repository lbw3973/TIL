# 💡 String
- 표준 빌트인 객체인 `String`은 원시 타입인 문자열을 다룰 때 유용한 프로퍼티와 메서드를 제공한다

### ✔ String 생성자 함수
- 표준 빌트인 객체인 `String` 객체는 생성자 함수 객체다. 따라서 `new` 연산자와 함께 호출하여 `String` 인스턴스를 생성할 수 있다
- String 생성자 함수에 인수를 전달하지 않고 `new` 연산자와 함께 호출하면 `[[StringData]]` 내부 슬롯에 빈 문자열을 할당한 `String` 래퍼 객체를 생성한다
```
const strObj = new String();
console.log(strObj); // String {length: 0, [[PrimitiveValue]]: ""}
```

- String 생성자 함수의 인수로 문자열을 전달하면서 `new` 연산자와 함께 호출하면 `[[StringData]]` 내부 슬롯에 인수로 전달받은 문자열을 할당한 `String` 래퍼 객체를 생성한다
```
const strObj = new String('Lee');
console.log(strObj);
// String {0: "L", 1: "e", 2: "e", length: 3, [[PrimitiveValue]]: "Lee"}
```

- `String` 래퍼 객체는 배열과 마찬가지로 `legnth` 프로퍼티와 인덱스를 나타내는 숫자 형식의 문자열을 프로퍼티 키로, 각 문자를 프로퍼티 값으로 갖는 유사 배열 객체이면서 이터러블이다. 따라서 배열과 유사하게 인덱스를 사용하여 각 문자에 접근할 수 있다
```
console.log(strObj[0]); // L
```

- 단, 문자열은 원시 값이므로 변경할 수 없다. 이때 에러가 발생하지 않는다
```
strObj[0] = 'S';
console.log(strObj); // 'Lee'
```

- `string` 생성자 함수의 인수로 문자열이 아닌 값을 전달하면 인수를 문자열로 강제 변환한 후, `[[StringData]]` 내부 슬롯에 변환된 문자열을 할당한 `String` 래퍼 객체를 생성한다
```
let strObj = new String(123);
console.log(strObj);
// String {0: "1", 1: "2", 2: "3", length: 3, [[PrimitiveValue]]: "123"}

strObj = new String(null);
console.log(strObj);
// String {0: "n", 1: "u", 2: "l", 3: "l", length: 4, [[PrimitiveValue}}: "null"}
```

- new 연산자를 사용하지 않고 String 생성자 함수를 호출하면 String 인스턴스가 아닌 문자열을 반환한다. 이를 이용하여 명시적으로 타입을 변환하기도 한다
```
// 숫자 타입 => 문자열 타입
String(1); // "1"
String(NaN); // "NaN"
String(Infinity); // "Infinity"

// 불리언 타입 => 문자열 타입
String(true); // "true"
String(false); // "false"
```
---

### ✔ length 프로퍼티
- `length` 프로퍼티는 문자열의 문자 개수를 반환한다
```
'Hello'.length; // 5
'안녕하세요!'.length; // 6
```
- String 래퍼 객체는 배열과 마찬가지로 length 프로퍼티를 갖는다. 그리고 인덱스를 나타내는 숫자를 프로퍼티 키로, 각 문자를 프로퍼티 값으로 가지므로 String 래퍼 객체는 유사 배열 객체다
---

### ✔ String 메서드
- 배열에는 원본 배열(배열 메서드를 호출한 배열)을 직접 변경하는 메서드와 원본 배열을 직접 변경하지 않고 새로운 배열을 생성하여 반환하는 메서드가 있다
- 하지만 String 객체에는 원본 String 래퍼 객체(String 메서드를 호출한 String 래퍼 객체)를 직접 변경하는 메서드는 존재하지 않는다. 즉, String 객체의 메서드는 언제나 새로운 문자열을 반환한다
```
const strObj = new String('Lee');

console.log(Object.getOwnPropertyDescriptors(strObj));
/* String 래퍼 객체는 읽기 전용 객체다. 즉, writable 프로퍼티 어트리뷰트 값이 false다
{
	0: {value: 'L', writable: false, enumerable: true, configurable: false}
	1: {value: 'e', writable: false, enumerable: true, configurable: false}
	2: {value: 'e', writable: false, enumerable: true, configurable: false}
	length: {value: 3, writable: false, enumerable: false, configurable: false}
	[[Prototype]]: Object
}
*/
```

#### 1. String.prototype.indexOf
- `indexOf` 메서드는 대상 문자열(메서드를 호출한 문자열)에서 인수로 전달받은 문자열을 검색하여 첫 번째 인덱스를 반환한다. 검색에 실패하면 -1을 반환한다
```
const str = 'Hello World';

// 문자열 str에서 'l'을 검색하여 첫 번째 인덱스를 반환한다
str.indexOf('l'); // 2

// 문자열 str에서 'or'를 검색하여 첫 번째 인덱스를 반환한다
str.indexOf('or'); // 7

// 문자열 str에서 'x'를 검색하여 첫 번째 인덱스를 반환한다
str.indexOf('x'); // -1
```

- `indexOf` 메서드의 2번째 인수로 검색을 시작할 인덱스를 전달할 수 있다
```
// 문자열 str의 인덱스 3부터 'l'을 검색하여 첫 번째 인덱스를 반환한다.
str.indexOf('l', 3 ); // 3
```

#### 2. String.prototype.search
- `search` 메서드는 대상 문자열에서 인수로 전달받은 정규 표현식과 매치하는 문자열을 검색하여 일치하는 문자열의 인덱스를 반환한다. 검색에 실패하면 -1을 반환한다
```
const str = 'Hello world';

// 문자열 str에서 정규 표현식과 매치하는 문자열을 검색하여 일치하는 문자열의 인덱스를 반환한다.
str.search(/o/); // 4
str.search(/x/); // -1
```

#### 3. String.prototype.includes
- ES6에서 도입된 `includes` 메서드는 대상 문자열에 인수로 전달받은 문자열이 포함되어 있는지 확인하여 그 결과를 `true` 또는 `false`로 반환한다
- `includes` 메서드의 2번째 인수로 검색을 시작할 인덱스를 전달할 수 있다
```
const str = 'Hello world';

str.includes('Hello'); // true
str.includes(''); // true
str.includes('x'); // false
str.includes(); // false
```

#### 4. String.prototype.startsWith
- ES6에서 도입된 `startsWith` 메서드는 대상 문자열이 인수로 전달받은 문자열로 시작하는지 확인하여 그 결과를 `true` 또는 `false`로 반환한다
- `startsWith` 메서드의 2번째 인수로 검색을 시작할 인덱스를 전달할 수 있다
```
const str = 'Hello world';

// 문자열 str이 'He'로 시작하는지 확인
str.startsWith('He'); // true
// 문자열 str이 'x'로 시작하는지 확인
str.startsWith('x'); // false
```

#### 5. String.prototype.endsWith
- ES6에서 도입된 `endsWith` 메서드는 대상 문자열이 인수로 전달받은 문자열로 끝나는지 확인하여 그 결과를 `true` 또는 `false`로 반환한다.

#### 6. String.prototype.charAt
- `charAt` 메서드는 대상 문자열에서 인수로 전달받은 인덱스에 위치한 문자를 검색하여 반환한다
```
const str = 'Hello';

for (let i = 0; i < str.length; i++) {
  console.log(str.charAt(i)); // H e l l o
}
```
- 인덱스가 문자열의 범위를 벗어난 정수인 경우 빈 문자열을 반환한다

#### 7. String.prototype.substring
- `substring` 메서드는 대상 문자열에서 첫 번째 인수로 전달받은 인덱스에 위치하는 문자부터 두 번째 인수로 전달받은 인덱스에 위치하는 문자의 바로 이전 문자까지의 부분 문자열을 반환한다
```
const str = 'Hello World';

// 인덱스 1부터 인덱스 4 이전까지의 부분 문자열을 반환한다
str.substring(1, 4); // ell
```

- `substring` 메서드의 두 번째 인수는 생략할 수 있다
- 이때 첫 번째 인수로 전달한 인덱스에 위치하는 문자부터 마지막 문자까지 부분 문자열을 반환한다
```
const str = 'Hello World'

// 인덱스 1부터 마지막 문자까지 부분 문자열을 반환한다
str.substring(1); // 'ello World'
```

#### 8. String.prototype.slice
- `slice` 메서드는 `substring` 메서드와 동일하게 동작한다. 단, `slice` 메서드에는 음수인 인수를 전달할 수 있다
- 음수인 인수를 전달하면 대상 문자열의 가장 뒤에서부터 시작하여 문자열을 잘라내어 반환한다
```
const str = "hello world";

// substring과 slice 메서드는 동일하게 동작한다
// 0번째부터 5번째 이전 문자까지 잘라내어 반환
str.substring(0, 5); // -> 'hello'
str.slice(0, 5); // -> 'hello'

// 인덱스가 2인 문자부터 마지막 문자까지 잘라내어 반환
str.substring(2); // -> 'llo world'
str.slice(2); // -> 'llo world'

// 인수 < 0 또는 NaN인 경우 0으로 취급된다
str.substring(-5); // -> 'hello world'
// slice 메서드는 음수인 인수를 전달할 수 있다. 뒤에서 5자리를 잘라내어 반환한다
str.slice(-5); // ⟶ 'world'
```

#### 9. String.prototype.toUpperCase
- `toUpperCase` 메서드는 대상 문자열을 모두 대문자로 변경한 문자열을 반환한다
```
const str = 'Hello World!';

str.toUpperCase(); // 'HELLO WORLD!'
```

#### 10. String.prototype.toLowerCase
- `toUpperCase`와 반대로 대상 문자열을 모두 소문자로 변경한 문자열을 반환한다

#### 11. String.prototype.trim
- `trim` 메서드는 대상 문자열 앞뒤에 공백 문자가 있을 경우 이를 제거한 문자열을 반환한다
```
const str = '   foo   ';

str.trim(); // 'foo'
```

#### 12. String.prototype.repeat
- ES6에서 도입된 `repeat` 메서드는 대상 문자열을 인수로 전달받은 정수만큼 반복해 연결한 새로운 문자열을 반환한다
- 인수로 전달받은 정수가 0이면 빈 문자열을 반환하고, 음수이면 `RangeError`를 발생시킨다
- 인수를 생략하면 기본값 0이 설정된다
```
const str = 'abc';

str.repeat(); // ''
str.repeat(0); // ''
str.repeat(1); // 'abc'
str.repeat(2); // 'abcabc'
str.repeat(2.5); // 'abcabc'
str.repeat(-1); // RangeError: Invalid count value
```

#### 13. String.prototype.replace
- `replace` 메서드는 대상 문자열에서 첫 번째 인수로 전달받은 문자열 또는 정규 표현식을 검색하여 두 번째 인수로 전달한 문자열로 치환한 문자열을 반환한다
```
const str = 'Hello world';

// str에서 첫 번째 인수 'world'를 검색하여 두 번째 인수 'Lee'로 치환한다
str.replace('world', 'Lee'); // 'Hello Lee'
```

#### 14. String.prototype.split
- `split` 메서드는 대상 문자열에서 첫 번째 인수로 전달한 문자열 또는 정규 표현식을 검색하여 문자열을 구분한 후 분리된 각 문자열로 이루어진 배열을 반환한다
- 인수로 빈 문자열을 전달하면 각 문자를 모두 분리하고, 인수를 생략하면 대상 문자열 전체를 단일 요소로 하는 배열을 반환한다
```
const str = 'How are you doing?';

// 공백으로 구분(단어로 구분)하여 배열로 반환한다
str.split(' '); // ["How", "are", "you", "doing?"]

// \s는 여러 가지 공백 문자(스페이스, 탭 등)를 의미한다. 즉, [\t\r\n\v\f]와 같은 의미다
str.split(/\s/); // ["How", "are", "you", "doing?"]

// 인수로 빈 문자열을 전달하면 각 문자를 모두 분리한다
str.split('');
// [ "H", "o", "w", "", "a", "r", "e", "", "y", "o, "u", "", "d", "o", "i", "n", "g", "?"]

// 인수를 생략하면 대상 문자열 전체를 단일 요소로 하는 배열을 반환한다
str.split(); // ["How are you doing?"]
```