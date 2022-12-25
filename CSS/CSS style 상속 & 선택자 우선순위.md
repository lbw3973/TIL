# 💡 CSS style 상속 & 선택자 우선순위

## ⬛ CSS Style 상속
- 부모(조상)요소의 속성이 하위요소까지 영향을 받는것을 뜻함

### ✔ 상속되는 CSS의 속성들..
- 모두 **글자/문자 관련 속성들**이다
- **모든** **글자/문자 관련 속성들**은 아니다
- 예시
  1. `font-style` : 글자 스타일
  2. `font-weight` : 굴자 두께
  3. `font-size` : 글자 크기
  4. `line-height` : 줄 높이
  5. `font-family` : 폰트(서체)
  6. `color` : 글자 색상
  7. `text-align` : 글자 정렬

---

### 강제 상속
- inherit : 부모의 속성 값을 상속한다

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

## ⬛ 선택자 우선순위
- 같은 요소가 여러 선언의 대상이 된 경우, 어떤 선언이 CSS 속성을 **우선 적용할지 결정하는 방법**

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

- 우선순위
1. !important
2. inline 선언
3. id 선택자
4. class 선택자
5. tag 선택자
6. 전체선택자
