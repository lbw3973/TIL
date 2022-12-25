# CSS Layout

## CSS Flex
- 1차원 레이아웃 구조를 위한 속성이다
- Fexible box라고 부르기도 한다
- 정렬을 할 요소들의 부모요소의 display 속성에 flex라는 값을 넣어주어야 한다
- Container와 Items, 2개의 개념으로 나뉜다

### Flex Container 의 속성들

#### 1. display
- display 속성으로 Flex Container를 정의한다
&nbsp;&nbsp;1. `flex` : Block형식의 Flex Container를 정의
&nbsp;&nbsp;2. `inline-flex` : inline형식의 Flex Container를 정의

#### 2. flex-flow
- Flex Items의 main 축을 설정하고 줄바꿈도 설정한다.
- 단축 속성이다.
&nbsp;&nbsp;1. flex-direction : items의 주 축을 설정 (default value : row)
    - **`row`** : items를 좌->우, 수평으로 표시 
    - `row-reverse` : row를 역방향으로 표시
    - `col` : items를 상->하, 수직으로 표시
    - `col-reverse` : col을 역방향으로 표시
&nbsp;&nbsp;2. flex-wrap: items의 줄바꿈을 설정 (default value : nowrap)
    - `nowrap` : items를 줄바꿈 하지 않음, 한 줄에 표시
    - `wrap` : items를 여러줄로 표시
    - `wrap-reverse` : `wrap`의 역방향으로 표시



### flex

#### flex-grow (defualt : 0)
- 증가 너비 비율
- 숫자가 크면 클수록 증가하는 너비가 커진다

#### flex-shrink (defualt : 1)
- 감소 너비 비율
- 숫자가 작을수록 감소하는 너비가 커진다

#### flex-basis (defualt : auto)

### align-self
- align items를 개별적으로 지정하는 속성 

## Grid
