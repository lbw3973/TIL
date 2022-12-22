# 💡 선택자 (Selector)

## ⬛ 기본 선택자

### ✔ 전체 선택자

- *(asterisk) : 모든 요소를 선택

```
* {
  color: red;
}
```

### ✔ 태그 선택자

- 태그의 이름으로 요소를 선택하는 선택자

```
li {
  color: red;
}
```

### ✔ 클래스 선택자

- HTML 파일 내, class속성의 값으로 선택하는 선택자
- 클래스 선택자를 의미하는 "."을 class이름 앞에 붙혀준다

```
.class_value {
  color: red;
}
```

### ✔ 아이디 선택자

- HTML 파일 내, id속성의 값으로 선택하는 선택자
- 아이디 선택자를 의미하는 "#"을 id이름 앞에 붙혀준다

```
#id_value{
  color: red;
}

```

---

## ⬛ 복합 선택자
- 기본 선택자를 조합하여 선택하는 선택자

### ✔ 일치 선택자 (Basic Combinator)
- 선택자 A,B를 동시에 만족하는 요소를 선택하는 구조

```
EX) class의 값이 "value"인 span tag내의 요소
span.value {
  color: red;
}
```

### ✔ 자식 선택자 (Child Combinator)
- 선택자 A의 자식요소 B를 선택하는 구조
- ">"가 선택자의 기호이다

```
EX) class의 값이 "value"인 ul의 자식요소
ul > .value{
  color: red;
}
```

### ✔ 하위(후손) 선택자 (Descendant Combinator)
- 선택자 A의 하위요소 B를 선택하는 구조
- "띄어쓰기"가 선택자의 기호이다

```
EX) class의 값이 "value"인 div의 하위요소
div .value {
  color: red;
}
``` 

### ✔ 인접 형제 선택자 (Adjacent Sibling Combinator)
- 선택자 A의 **다음** 형제요소 B를 선택하는 구조
- "+"가 선택자의 기호이다

```
EX) class의 값이 "value"인 요소의 바로 다음 div 요소 '하나'
.value + div {
  color: red;
}
```

### ✔ 일반 형제 선택자 (General Sibling Combinator)
- 선택자 A의 **다음** 형제요소를 **모두** 선택하는 구조
- "~"가 선택자의 기호이다

```
EX) class의 값이 "value"인 요소의 다음 div 요소 '모두'
.value ~ div {
  color: red;
}
```

---

## ⬛ 가상 클래스 선택자 - 동작 관련 (Pseudo-Classes)
- 각 요소들의 상태에 따른 선택이 이루어지는 선택자를 의미한다

### ✔ :hover
- 마우스 커서를 올렸을 때 동작한다

```
EX) A tag위에 마우스를 올리면 빨간색으로 변경
A:hover{
  color: red;
}
```

### ✔ :active
- 요소에 마우스 클릭을 하고 있는 동안 동작한다

```
EX) A tag를 클릭하고 있는 동안 빨간색으로 변경
A:active {
  color: red;
}
```

### ✔ :focus
- 요소가 포커스되면 선택
- 포커스가 가능한 요소에서만 동작한다

```
EX) input tag가 포커스되면 backgrount color를 빨간색으로 변경
input:focus {
  background-color: red;
}
```

---

## ⬛ 가상 클래스 선택자 - 특정 요소 선택 관련

### ✔ :first-child
- 선택자의 형제 요소 중 첫째라면 선택

```
EX) Class A의 자식 요소 중, 첫번째 요소가 span이라면 color 변경
.A span:first-child {
  color: red;
}
```
### ✔ :last-child
- 선택자의 형제 요소 중 마지막이라면 선택

```
EX) Class A의 자식 요소 중, 마지막 요소가 span이라면 color 변경
.A span:last-child {
  color: red;
}
```

### ✔ :nth-child(n)
- 선택자의 형제 요소 중 n번째라면 선택
- 상수를 사용해도 되지만 2n, 2n+1, n+3 등의 방식으로 사용할 수 있다
  - 위와 같이 사용할 때, n은 0부터 시작한다

```
EX1) Class A의 자식 요소 중, 3번째 요소가 span이라면 color 변경
.A span:nth-child(3) {
  color: red;
}

EX2) Class A의 자식 요소 중, 3번째 요소의 color 변경
.A *:nth-child(3) {
  color: red;
}

EX3) Class A의 자식 요소 중, (2 x n) 번째 요소의 color 변경
.A *:nth-child(2n) {
  color: red;
}
```

### ✔ :not(X)
- 부정선택자
- 선택자 X가 아닌 다른 요소들을 선택

```
EX) Class A의 자식 요소 중, span을 제외한 요소들의 color 변경
.A *:not(span) {
  color: red;
}
```

---

## ⬛ 가장 요소 선택자
- 콜론(":") 2개를 사용한다
- 반드시 Content 라는 속성을 사용하여야 한다

### ✔ ::before
- 선택자 요소 내부의 **앞에** 내용(Content)을 삽입
- 가상의 인라인 요소를 만들어 삽입한다

```
EX) Class A 내부의 앞에 "앞"이라는 텍스트를 출력
.A::before {
  content: "앞";
}
```

### ✔ ::after
- 선택자 요소 내부의 **뒤에** 내용(Content)을 삽입
- 가상의 인라인 요소를 만들어 삽입한다

```
EX) Class A 내부의 뒤에 "뒤"이라는 텍스트를 출력
.A::before {
  content: "뒤";
}
```

---

## ⬛ 속성 선택자 (Attribute)
- 대괄호를 포함하여 사용

### ✔ disabled
- 비활성화가 되어있는 속성들을 선택

```
EX) 비활성화 되어있는 속성들의 color를 변경
[disabled] {
  color: red;
}
```

### ✔ type
- type 속성을 가지고 있는 속성들을 선택
- type의 value를 특정하여 선택 할 수도 있다

```
EX) type의 값이 "value"인 것들의 color를 변경
[type="value"] {
  color: red;
}
```


