# Q: CSS 전처리기(CSS preprocessor)란 무엇인가요?
> CSS 전처리기는 **CSS를 더 효율적이고 체계적으로 작성할 수 있도록 도와주는 도구**입니다.

- CSS는 기본적으로 스타일 규칙을 선언하는 데 필요한 문법만 제공하기 때문에 반복적인 작업이나 코드의 재사용성이 떨어지는 단점이 있습니다.  
- CSS 전처리기는 이러한 한계를 극복하고 CSS에 프로그래밍적 기능을 추가하는 역할을 합니다.
- 대표적인 CSS 전처리기로는 `Sass`, `Less`, `Stylus`가 있습니다.

기본적으로, CSS에는 변수, 함수, 조건문과 같은 기능이 없습니다. 하지만 CSS 전처리기를 사용하면 이러한 기능들을 구현할 수 있습니다. CSS 전처리기를 사용하여 작성한 코드는 일반 CSS로 컴파일되어 브라우저에서 사용됩니다.

실제 사용 예시는 다음과 같습니다.

### ✅ 일반 CSS

```css
.primary-button {  
  background-color: #007bff;  
  color: white;  
  padding: 10px 20px;  
  border-radius: 4px;  
}  

.secondary-button {  
  background-color: #6c757d;  
  color: white;  
  padding: 10px 20px;  
  border-radius: 4px;  
}  
```

### ✅ Sass(SCSS)

```css
$button-padding: 10px 20px;  
$border-radius: 4px;  

@mixin button($bg-color) {  
  background-color: $bg-color;  
  color: white;  
  padding: $button-padding;  
  border-radius: $border-radius;  
}  

.primary-button {  
  @include button(#007bff);  
}  

.secondary-button {  
  @include button(#6c757d);  
}  
```
<br/>

# Q: CSS 전처리기와 Zero Runtime CSS의 차이는 무엇인가요?

두 도구는 컴파일 타임에 CSS를 생성한다는 점에서 공통점이 있지만, 등장 배경과 목적에서 차이가 있습니다.

#### CSS 전처리기는 순수 CSS만으로 구현하기 어려운 프로그래밍적인 기능(변수, 중첩, 믹스인 등)을 지원하기 위해 등장했습니다. 
- 이를 통해 코드 재사용성을 높이고, 스타일 관리의 복잡성을 줄이는 것이 주요 목표입니다.

#### `Zero Runtime CSS`는 CSS in JS의 성능 문제를 해결하기 위해 탄생했습니다. 
- CSS in JS는 런타임에서 CSS 관련 연산을 수행하며 성능 오버헤드를 발생시킬 수 있는데, `Zero Runtime CSS`는 이를 컴파일 타임에 미리 처리함으로써 런타임 비용을 제거하고 성능을 최적화합니다.

<br/>

이러한 등장 배경 차이로 인해 문법 형태도 다릅니다. CSS 전처리기는 CSS와 유사한 문법을 사용하며, 전통적인 CSS 스타일을 확장합니다.  
반면 `Zero Runtime CSS`는 CSS in JS와 유사하게 JS 문법을 기반으로 작성하며, 컴포넌트 중심의 스타일링을 지원합니다.



