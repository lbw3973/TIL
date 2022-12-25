# 💡 CSS Layout

## ⬛ CSS Flex
- 1차원 레이아웃 구조를 위한 속성이다
- Fexible box라고 부르기도 한다
- 정렬을 할 요소들의 부모요소의 display 속성에 flex라는 값을 넣어주어야 한다
- Container와 Items, 2개의 개념으로 나뉜다

### ✔ Flex Container 의 속성들

#### 1. display
- display 속성으로 Flex Container를 정의한다
  1. `flex` : Block형식의 Flex Container를 정의
  2. `inline-flex` : inline형식의 Flex Container를 정의

#### 2. flex-flow
- Flex Items의 main 축을 설정하고 줄바꿈도 설정한다.
- 단축 속성이다.
  1. `flex-direction` : items의 주 축을 설정 **(default value : row)**
      - **`row`** : items를 좌->우, 수평으로 표시 
      - `row-reverse` : row를 역방향으로 표시
      - `col` : items를 상->하, 수직으로 표시
      - `col-reverse` : col을 역방향으로 표시
  2. `flex-wrap`: items의 줄바꿈을 설정 **(default value : nowrap)**
      - `nowrap` : items를 줄바꿈 하지 않음, 한 줄에 표시
      - `wrap` : items를 여러줄로 표시
      - `wrap-reverse` : `wrap`의 역방향으로 표시
      
#### 3. justify-content
- main축의 정렬 방법을 설정한다 **(default value : flex-start)**
  1. **`flex-start`** : items를 container의 시작점에서 부터 정렬
  2. `flex-end` : items를 container의 끝에서 부터 정렬
  3. `center` : items를 container의 가운데 정렬
  4. `space-between` : 첫 item과 마지막 item은 container의 양쪽에 배치되고, 사이에 있는 나머지 items는 모두 간격이 일정하게 정렬
  5. `space-around` : items를 모두 동일한 여백으로 정렬

#### 4. align-content
- 교차축의 정렬 방법을 설정 **(default value : stretch)**
- items가 여러 줄 이상이여야 사용 가능하다. (`flex-wrap`이 `nowrap`이면 사용 불가)
- `justify-content` 속성과 비슷하다
  1. **`stretch`** : Container의 교차 축을 채우기 위해 items의 width가 늘어난다
  2. `flex-start` : items를 Container의 시작점에서 부터 정렬
  3. `flex-end` : items를 Container의 끝에서 부터 정렬
  4. `center` : items를 Contatiner의 가운데 정렬
  5. `space-between` : 첫 item과 마지막 item은 container의 위아래에 배치되고, 사이에 있는 나머지 items는 모두 간격이 일정하게 정렬
  6.  `space-around` : itmes를 모두 동일한 여백으로 정렬

#### 5. align-items
- 교차축의 정렬 방법을 설정 (items가 한 줄 일때) **(default value : stretch)**
- **`flex-wrap`이 기본값(`stretch`) 일때만 사용 가능**
  1. **`stretch`** : Container의 교차 축을 채우기 위해 items를 늘린다
  2. `flex-start` : align-content와 동일
  3. `flex-end` : align-content와 동일
  4. `center` : align-content와 동일
  5. `baseline` : 문자의 기준선에 정렬

### ✔ Flex Items 의 속성들

#### 1. order **(default value : 0)**
- items의 순서를 설정한다
- items에 숫자를 지정하면, 숫자가 클수록 순서가 뒤로 가게된다
- 음수도 설정할 수 있다

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
