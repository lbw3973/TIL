# 💡 RegExp

### ✔ 정규 표현식이란?
- 정규 표현식은 일정한 패턴을 가진 문자열의 집합을 표현하기 위해  사용하는 형식 언어다
- 정규 표현식은 문자열을 대상으로 **패턴 매칭 기능**을 제공한다
---

### ✔ 정규 표현식의 생성
- 정규 표현식 객체를 생성하기 위해서는 정규 표현식 리터럴과 RegExp 생성자 함수를 사용할 수 있다
- 정규 표현식 리터럴은 패턴과 플래그로 구성된다
```
const target = "Is this all there is?';

// 패턴: is
// 플래그: i => 대소문자를 구별하지 않고 검색한다
const regexp = /is/i;

// test 메서드는 target 문자열에 대해 정규 표현식 regexp의 패턴을 검색하여 매칭 결과를 불리언 값으로 반환한다
regexp.test(target); // true
```

- RegExp 생성자 함수를 사용하여 RegExp 객체를 생성할 수도 있다
```
const target = 'Is this all there is?';

const regexp = new RegExp(/is/i); // ES6
// const regexp = new RegExp(/is/, 'i');
// const regexp = new RegExp('is', 'i');

regexp.test(target); // true
```
---

### ✔ RegExp 메서드

#### 1. RegExp.prototype.exec
- `exec` 메서드는 인수로 전달받은 문자열에 대해 정규 표현식의 패턴을 검색하여 매칭 결과를 배열로 반환한다
- 매칭 결과가 없는 경우 `null`을 반환한다
```
const target = 'Is this all there is?';
const regExp = /is/;

regExp.exec(target);
// ["is", index: 5, input: "Is this all there is?", groups: undefined]
```
- exec 메서드는 문자열 내의 모든 패턴을 검색하는 g 플래그를 지정해도 첫 번째 매칭 결과만 반환하므로 주의하기 바란다

#### 2. RegExp.prototype.test
- `test` 메서드는 인수로 전달받은 문자열에 대해 정규 표현식의 패턴을 검색하여 매칭 결과를 불리언 값으로 반환한다
```
const target = 'Is this all there is?';
const regExp = /is/;

regExp.test(target); // true
```

#### 3. String.prototype.match
- `String` 표준 빌트인 객체가 제공하는 `match` 메서드는 대상 문자열과 인수로 전달받은 정규 표현식과의 매칭 결과를 배열로 반환한다
```
const target = 'Is this all there is?';
const regExp = /is/;

target.match(regExp);
// ["is", index: 5, input: "Is this all there is?", groups: undefined]
```
- exec 메서드는 문자열 내의 모든 패턴을 검색하는 g 플래그를 지정해도 첫 번째 매칭 결과만 반환하지만, String.prototype.match 메서드는 g 플래그가 지정되면 모든 매칭 결과를 배열로 반환한다
---

### ✔ 플래그
- 패턴과 함께 정규 표현식을 구성하는 플래그는 정규 표현식의 검색 방식을 설정하기 위해 사용한다
  1. `i`(ignore case) : 대소문자를 구별하지 않고 패턴을 검색한다
  2. `g`(Grobal) : 대상 문자열 내에서 패턴과 일치하는 모든 문자열을 전역 검색한다
  3. `m`(Multi line) : 문자열의 행이 바뀌더라도 패턴 검색을 계속한다
- 플래그는 옵션이므로 선택적으로 사용할 수 있으며, 순서와 상관없이 하나 이상의 플래그를 동시에 설정할 수도 있다
---

### ✔ 패턴
- 정규 표현식의 패턴은 문자열의 일정한 규칙을 표현하기 위해 사용하며, 정규 표현식의 플래그는 정규 표현식의 검색 방식을 설정하기 위해 사용한다
- 패턴은 `/`로 열고 닫으며 문자열의 따옴표는 생략한다

#### 1. 문자열 검색
- 정규 표현식의 패턴에 문자 또는 문자열을 지정하면 검색 대상 문자열에서 패턴으로 지정한 문자 또는 문자열을 검색한다
- 검색 대상 문자열과 플래그를 생략한 정규 표현식의 매칭 결과를 구하면 대소문자를 구별하여 정규 표현식에 매치한 첫 번째 결과만 반환한다
```
const target = 'Is this all there is?';

// 'is' 문자열과 매치하는 패턴. 플래그가 생략되었으므로 대소문자를 구별한다
const regExp = /is/;

// target과 정규 표현식이 매치하는지 테스트한다
regExp.test(target); // true

// target과 정규 표현식의 매칭 결과를 구한다
target.match(regExp);
// ["is", index: 5, input: "Is this all there is?", groups: undefined]
```
- 대소문자를 구별하지 않고 검색하려면 플래그를 i를 사용하고, 검색 대상 문자열 내에서 패턴과 매치하는 모든 문자열을 전역 검색하려면 플래그 g를 사용한다

#### 2. 임의의 문자열 검색
- `.`은 임의의 문자 한 개를 의마한다
```
const target = 'Is this all there is?';

// 임의의 3자리 문자열을 대소문자를 구별하여 전역 검색한다
const regExp = /.../g;

target.match(regExp); // ["Is ", "thi", "s a", "ll ", "the", "re ", "is?"]
```

#### 3. 반복 검색
- {m,n}은 앞선 패턴(다음 예제의 경우 A)이 최소 m번, 최대 n번 반복되는 문자열을 의미한다
- 콤마 뒤에 공백이 있으면 정상 동작하지 않으므로 주의하여야 한다
```
const target = 'A AA B BB Aa Bb AAA';

// 'A'가 최소 1번, 최대 2번 반복되는 문자열을 전역 검색한다
const regExp = /A{1,2}/g;

target.match(regExp); // ["A", "AA", "A", "AA", "A"]
```

- {n}은 앞선 패턴이 n번 반복되는 문자열을 의미한다. 즉, {n}은 {n, n}과 같다
```
const target = 'A AA B BB Aa Bb AAA';

// 'A'가 2번 반복되는 문자열을 전역 검색한다
const regExp = /A{2}/g;

target.match(regExp); // ["AA", "AA"]
```

- {n,}은 앞선 패턴이 최소 n번 이상 반복되는 문자열을 의미한다
```
const target = 'A AA B BB Aa Bb AAA';

// 'A'가 최소 2번 이상 반복되는 문자열을 전역 검색한다
const regExp = /A{2,}/g;

target.match(regExp); // ["AA", "AAA"]
```

- +는 앞선 패턴이 최소 한번 이상 반복되는 문자열을 의미한다. 즉, +는 {1,}과 같다
```
const target = 'A AA B BB Aa Bb AAA';

// 'A'가 최소 한 번 이상 반복되는 문자열('A', 'AA', 'AAA', ...)을 전역 검색한다
const regExp = /A+/g;

target.match(regExp); // ["A", "AA', "A", "AAA"]
```

- ?는 앞선 패턴이 최대 한 번(0번 포함) 이상 반복되는 문자열을 의미한다. 즉, ?는 {0, 1}과 같다
```
const target = 'color colour';

// 'colo' 다음 'u'가 최대 한번(0번 포함) 이상 반복되고 'r'이 이어지는
// 문자열 'color', 'colour'를 전역 검색한다.
const regExp = /colou?r/g;

target.match(regExp); // ["color", "colour"]
```

#### 4. OR 검색
- `|`는 or의 의미를 갖는다
```
const target = 'A AA B BB Aa Bb';

// 'A' 또는 'B'를 전역 검색한다
const regExp = /A|B/g;

target.match(regExp); // ["A", "A", "A", "B", "B", "B", "A", "B"]
```

- 분해되지 않은 단어 레벨로 검색하기 위해서는 +를 함께 사용한다. [ ] 내의 문자는 or로 동작한다
```
const target = "A AA B BB Aa Bb";

// 'A' 또는 'B'가 한 번 이상 반복되는 문자열을 전역 검색한다
// 'A', 'AA', 'AAA', ... 또는 'B', 'BB', 'BBB', ...
const regExp = /[AB]+/g;

target.match(regExp); // -> ["A", "AA", "B", "BB", "A", "B"]
```

- 범위를 지정하려면 [ ] 내에 - 를 사용한다
```
const target = "AA BB ZZ Aa Bb";

// 'A' ~ 'Z'가 한 번 이상 반복되는 문자열을 전역 검색한다
const regExp = /[A-Z]+/g;

target.match(regExp); // -> ["A", "AA", "BB", "ZZ", "A", "B"]
```

- \d는 숫자를 의미한다. 즉, \d는 [0-9]와 같다
- \D는 \d와 반대로 동작한다. 즉, \D는 숫자가 아닌 문자를 의미한다
```
const target = "AA BB 12,345";

// '0' ~ '9' 또는 ','가 한 번 이상 반복되는 문자열을 전역 검색한다
let regExp = /[\d,]+/g;

target.match(regExp); // -> ["12,345"]

// '0' ~ '9'가 아닌 문자(숫자가 아닌 문자) 또는 ','가 한 번 이상 반복되는 문자열을 전역 검색한다
regExp = /[\D,]+/g;

target.match(regExp); // -> ["AA BB ", ","]
```

- \w는 알파벳, 숫자, 언더스코어를 의미한다. 즉, \w는 [A-Za-z0-9_]와 같다 
- \W는 \w와 반대로 동작한다. 즉, \W는 알파벳, 숫자, 언더스코어가 아닌 문자를 의미한다
```
const target = "Aa Bb 12,345 _$%&";

// 알파벳, 숫자, 언더스코어, ','가 한 번 이상 반복되는 문자열을 전역 검색한다
let regExp = /[\w,]+/g;

target.match(regExp); // -> ["Aa", "Bb", "12,345", "_"]

// 알파벳, 숫자, 언더스코어가 아닌 문자 또는 ','가 한 번 이상 반복되는 문자열을 전역 검색한다
regExp = /[\W,]+/g;

target.match(regExp); // -> [" ", " ", ",", " $%&"]
```

#### 5. NOT 검색
- [...] 내의 `^`은 not의 의미를 갖는다
```
const target = "AA BB 12 Aa Bb";

// 숫자를 제외한 문자열을 전역 검색한다
const regExp = /[^0-9]+/g;

target.match(regExp); // -> ["AA BB ", " Aa Bb"]
```

#### 6. 시작 위치로 검색
- [...] 밖의 `^`은 문자열의 시작을 의미한다
```
const target = "https://poiemaweb.com";

// 'https'로 시작하는지 검사한다.
const regExp = /^https/;

regExp.test(target); // -> true
```

#### 7. 마지막 위치로 검색
- `$`은 문자열의 마지막을 의미한다
```
const target = "https://poiemaweb.com";

// 'com'으로 끝나는지 검사한다
const regExp = /com$/;

regExp.test(target); // -> true
```
---

### ✔ 자주 사용하는 정규 표현식

#### 1. 특정 단어로 시작하는지 검사
```
const url = 'https://example.com';

// 'http://' 또는 'https://'로 시작하는지 검사한다
/^https:?\/\//.test(url); // true
/^(http|https):\/\//.test(url); // true
```

#### 2. 특정 단어로 끝나는지 검사
```
const fileName = 'index.html';

// 'html'로 끝나는지 검사한다
/html$/.test(fileName); // true
```

#### 3. 숫자로만 이루어진 문자열인지 검사
```
const target = '12345';

// 숫자로만 이루어진 문자열인지 검사한다.
/^\d+$/.test(target); // true
```

#### 4. 하나 이상의 공백으로 시작하는지 검사
```
const target = ' Hi!';

// 하나 이상의 공백으로 시작하는지 검사한다
/^[\s]+/.test(target); // true
```

#### 5. 아이디로 사용 가능한지 ㅈ검사
```
const id = 'abc123';

// 알파벳 대소문자 또는 숫자로 시작하고 끝나며 4~10자리인지 검사한다.
/^[A-Za-z0-9]{4,10}$/.test(id); // true
```

#### 6. 메일 주소 형식에 맞는지 검사
```
const email = 'ungmo@gmail.com'

/^[0-9a-zA-Z]([-_\.]?[0-9a-zA-Z])*@[0-9a-zA-Z]([-_\.]?[0-9a-zA-Z])*\.[a-zA-Z]{2,3}$/.test(email); // true
```

#### 7. 핸드폰 번호 형식에 맞는지 검사
```
const cellphone = '010-5033-1643';

/^\d{3}-\d{3,4}-\d{4}$/.test(cellphone); // true
```

#### 8. 특수 문자 포함 여부 검사
```
const target = "abc#123";

// A-Za-z0-9 이외의 문자가 있는지 검사한다
/[^A-Za-z0-9]/gi.test(target); // true
```