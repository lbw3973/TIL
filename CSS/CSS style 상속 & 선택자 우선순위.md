# π‘ CSS style μμ & μ νμ μ°μ μμ

## β¬ CSS Style μμ
- λΆλͺ¨(μ‘°μ)μμμ μμ±μ΄ νμμμκΉμ§ μν₯μ λ°λκ²μ λ»ν¨

### β μμλλ CSSμ μμ±λ€..
- λͺ¨λ **κΈμ/λ¬Έμ κ΄λ ¨ μμ±λ€**μ΄λ€
- **λͺ¨λ ** **κΈμ/λ¬Έμ κ΄λ ¨ μμ±λ€**μ μλλ€
- μμ
  1. `font-style` : κΈμ μ€νμΌ
  2. `font-weight` : κΈμ λκ»
  3. `font-size` : κΈμ ν¬κΈ°
  4. `line-height` : μ€ λμ΄
  5. `font-family` : ν°νΈ(μμ²΄)
  6. `color` : κΈμ μμ
  7. `text-align` : κΈμ μ λ ¬

---

### κ°μ  μμ
- inherit : λΆλͺ¨μ μμ± κ°μ μμνλ€

```
.parent {
  width: 300px;
  height : 200px;
  background-color: red;
}
.child {
  width: 100px;
  height: inherit;
  background-color: orange;
}
```

---

## β¬ μ νμ μ°μ μμ
- κ°μ μμκ° μ¬λ¬ μ μΈμ λμμ΄ λ κ²½μ°, μ΄λ€ μ μΈμ΄ CSS μμ±μ **μ°μ  μ μ©ν μ§ κ²°μ νλ λ°©λ²**

```
<div 
  id="color_yellow" 
  class="color_green" 
  style="color: pink">
  Hello World!
</div>
```

```
div {
  color: red !important;
}
#color_yellow {
  color: yellow;
}
.color_green {
  color: green;
}
div {
  color: blue;
}
* {
  color: darkblue;
}
body {
  color: violet;
}
```

- μ°μ μμ
1. !important
2. inline μ μΈ
3. id μ νμ
4. class μ νμ
5. tag μ νμ
6. μ μ²΄μ νμ
