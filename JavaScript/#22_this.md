# 💡 this

### ✔ this 키워드
- `this`는 자신이 속한 객체 또는 자신이 생성할  인스턴스를 가리키는 자기 참조 변수이다
- `this`를 통해 자신이  속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조 할 수 있다
- `this`가 가리키는 값, 즉 `this`바인딩은 함수 호출 방식에 의해 동적으로 결정된다

```
// 전역에서 this는 전역 객체 window를 가리킨다.
console.log(this); // window

// 일반 함수 내부에서 this는 전역 객체 window를 가리킨다.
function square(number) {
  console.log(this); // window
  return number*number;
}

//메서드 내부에서 this는 메서드를 호출한 객체를 가리킨다.
const person = {
  name: "Lee",
  getName() {
    console.log(this); // {name: "Lee", getName: ƒ}
    return this.name;
  }
};
console.log(person.getName()); // Lee

// 생성자 함수 내부에서 this는 생성자 함수가 생성할 인스턴스를 가리킨다.
function Person(name) {
  this.name = name;
  console.log(this); // Person {name: "Lee"}
};
const me = new Person("Lee")
```

### ✔ 함수 호출 방식과 this 바인딩
- `this` 바인딩은 함수 호출 방식, 즉 함수가 어떻게 호출되었는지에 따라 동적으로 결정된다

#### 1. 일반 함수 호출
- 기본적으로 this에는 전역 객체가 바인딩된다
- 전역 함수는 물론이고 중첩 함수를 일반 함수로 호출하면 함수 내부의 this에는 전역 객체가 바인딩된다
- 하지만 this는 객체의 프로퍼티나 메서드를 참조하기 위한 자기 참조 변수이므로 객체를 생성하지 않는 일반 함수에서 this는 의미가 없다
- 그리고 strict mode가 적용된 일반 함수 내부의 this에는 undefined가 바인딩된다
```
var value = 1;

const obj = {
  value: 100,
  foo() {
    console.log("foo's this", this); // {value: 100, foo: ƒ}
    setTimeout(function() {
      console.log("callback's this", this); // window
      console.log("callback's this.value", this.value); // 1
    }, 1000)
  }
}
```

#### 2. 메서드 호출
- 메서드 내부의 `this`에는 메서드를 호출한 객체, 즉 메서드를 호춣할 때 메서드 이름 앞의 마침표 연산자 앞에 기술한 객체가 바인딩된다
```
function Person(name) {
  this.name = name;
}

Person.prototype.getName = function() {
  return this.name;
}

const me = new Person("Kim");
console.log(me.getName()); // Kim

Person.prototype.name = "LEE"
console.log(Person.prototype.getName()); // LEE
```

#### 3. 생성자 함수 호출
- 생성자 함수 내부의 `this`에는 생성자 함수가 생성할 인스턴스가 바인딩된다
