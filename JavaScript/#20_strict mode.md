# π‘ strict mode

### β strict modeλ?
```
function foo() {
  x = 10;
}
foo();

console.log(x); // 10
```
- μλ°μ€ν¬λ¦½νΈ μμ§μ foo ν¨μμ μ€μ½νμμλΆν° μΆλ°νμ¬ μ μ­ μ€μ½νκΉμ§ xλ₯Ό μ°Ύκ² λλ€
- μ΄λμλ μλ x λ³μλ‘ μΈν΄ μλ¬κ° λ°μν  κ² κ°μ§λ§ μλ°μ€ν¬λ¦½νΈ μμ§μ μλ¬΅μ μΌλ‘ μ μ­ κ°μ²΄μ x νλ‘νΌν°λ₯Ό λμ  μμ±νλ€
- μ΄λ μ μ­ κ°μ²΄μ x νλ‘νΌν°λ λ§μΉ μ μ­ λ³μμ²λΌ μ¬μ©ν  μ μκ³ , μ΄λ¬ν νμμ μλ¬΅μ  μ μ­μ΄λΌ νλ€
- strict modeλ μλ°μ€ν¬λ¦½νΈ μΈμ΄μ λ¬Έλ²μ μ’ λ μκ²©ν μ μ©νμ¬ μ€λ₯λ₯Ό λ°μμν¬ κ°λ₯μ±μ΄ λκ±°λ μλ°μ€ν¬λ¦½νΈ μμ§μ μ΅μ ν μμμ λ¬Έμ λ₯Ό μΌμΌν¬ μ μλ μ½λμ λν΄ λͺμμ μΈ μλ¬λ₯Ό λ°μμν¨λ€

### β strict modeμ μ μ©
- strict modeλ₯Ό μ μ©νλ €λ©΄ μ μ­μ μ λ, νΉμ ν¨μ λͺΈμ²΄μ μ λμ `'use strict';`λ₯Ό μΆκ°νλ€

### β μ μ­μ strict modeλ₯Ό μ μ©νλ κ²μ νΌνμ
- μ μ­μ μ μ©ν strict modeλ μ€ν¬λ¦½νΈ λ¨μλ‘ μ μ©λλ€
- strict mode μ€ν¬λ¦½νΈμ non-strict mode μ€ν¬λ¦½νΈλ₯Ό νΌμ©νλ κ²μ μ€λ₯λ₯Ό λ°μμν¬ μ μλ€
- νΉν, μΈλΆ μλνν° λΌμ΄λΈλ¬λ¦¬λ₯Ό μ¬μ©νλ κ²½μ° λΌμ΄λΈλ¬λ¦¬κ° non-strict modeμΈ κ²½μ°λ μκΈ° λλ¬Έμ μ μ­μ strict modeλ₯Ό μ¬μ©νλ κ²μ λ°λμ§νμ§ μλ€

### β ν¨μ λ¨μλ‘ strict modeλ₯Ό μ μ©νλ κ²λ νΌνμ
- μ΄λ€ ν¨μλ strict modeλ₯Ό μ μ©νκ³ , μ΄λ€ ν¨μλ μ μ©νμ§ μλ κ²λ λ°λμ§νμ§ μλ€ λν μΌμΌν μ μ©νλ κ²μ΄ λ²κ±°λ‘­κΈ°λ νλ€.
```
(function() {
  var let = 10; // non-strict modeμμλ μλ¬κ° λ°μνμ§ μμ
  function foo() {
    'use strict';
    let = 20 // syntaxError
  }
  foo();
};)()
```

### strict modeκ° λ°μμν€λ μλ¬
- strict modeλ₯Ό μ μ©νμ λ μλ¬κ° λ°μνλ λνμ μΈ μ¬λ‘

#### 1. μλ¬΅μ  μ μ­
- μ μΈνμ§ μμ λ³μλ₯Ό μ°Έμ‘°νλ©΄ ReferenceErrorκ° λ°μνλ€
```
(function () {
  'use strict';
  
  x = 10;
  console.log(x); // ReferenceError
})()
```

#### 2. λ³μ, ν¨μ, λ§€κ°λ³μμ μ­μ 
- delete μ°μ°μλ‘ λ³μ, ν¨μ, λ§€κ°λ³μλ₯Ό μ­μ νλ©΄ SyntaxErrorκ° λ°μνλ€
```
(function () {
  'use strict';
  
  x = 10;
  delete x; // SyntaxError
})()
```

#### 3. λ§€κ°λ³μ μ΄λ¦μ μ€λ³΅
- μ€λ³΅λ λ§€κ°λ³μ μ΄λ¦μ μ¬μ©νλ©΄ SyntaxErrorκ° λ°μνλ€
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

#### 4. withλ¬Έμ μ¬μ©
- with λ¬Έμ μ¬μ©νλ©΄ SyntaxErrorκ° λ°μνλ€
- with λ¬Έμ μ λ¬λ κ°μ²΄λ₯Ό μ€μ½ν μ²΄μΈμ μΆκ°νλ€
- withλ¬Έμ λμΌν κ°μ²΄μ νλ‘νΌν°λ₯Ό λ°λ³΅ν΄μ μ¬μ©ν  λ κ°μ²΄ μ΄λ¦μ μλ΅ν  μ μμ΄μ μ½λκ° κ°λ¨ν΄μ§λ ν¨κ³Όκ° μμ§λ§, μ±λ₯κ³Ό κ°λμ±μ΄ λλΉ μ§λ λ¬Έμ κ° μλ€
```
(function () {
  'use strict';
  
  // SyntaxError
  with({x: 1}) {
    console.log(x);
  }
})()
```

### β strict mode μ μ©μ μν λ³ν

#### 1. μΌλ° ν¨μμ this
- strict modeμμ ν¨μλ₯Ό μΌλ° ν¨μλ‘μ νΈμΆνλ©΄ thisμ undefinedκ° λ°μΈλ©λλ€
- μμ±μ ν¨μκ° μλ μΌλ° ν¨μ λ΄λΆμμλ thisλ₯Ό μ¬μ©ν  νμκ° μκΈ° λλ¬Έμ΄λ€, μ΄λ μλ¬λ λ°μνμ§ μλλ€

#### 2. arguments κ°μ²΄
- strict modeμμλ λ§€κ°λ³μμ μ λ¬λ μΈμλ₯Ό μ¬ν λΉνμ¬ λ³κ²½ν΄λ arguments κ°μ²΄μ λ°μλμ§ μλλ€
- μ΄κΈ°κ°μ μ μ§νλ λ― νλ€.
```
function foo(a) {
  'use strict';
  
  a = 2;
  console.log(arguments); // {0: 1, length: 1}
}

foo(1);
```