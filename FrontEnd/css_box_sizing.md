# Q: css box-sizing 속성에 대해 설명해주세요.
> `box-sizing`은 CSS에서 **요소의 크기를 어떻게 계산할지**를 결정하는 속성입니다.  
> 레이아웃을 스타일링할 때 예상치 못한 크기(너비, 높이) 변화가 발생하곤 하는데요. 그런 상황에서 `box-sizing` 속성이 도움이 될 수 있습니다.


## ✅ `box-sizing: content-box` (기본값)
`content-box`는 `box-sizing` 속성의 기본값으로, 적용 시 요소의 `width`와 `height` 값이 내용 영역만의 크기를 나타냅니다. 

**즉, `width`와 `height`는 요소의 실제 콘텐츠 크기만을 정의하고, 그 안에 추가되는 `padding`과 `border`는 크기에 포함되지 않습니다.**

- 예를 들어, `width: 200px`로 설정된 요소에 `padding: 20px`과 `border: 2px solid black`이 있으면, 요소의 실제 너비는 `200px + 20px * 2 (padding) + 2px * 2 (border)`로, 총 `244px`가 됩니다. 

이 방식은 `padding`과 `border`가 요소의 총 크기에 영향을 미친다는 점에서 때때로 예측하기 어려운 결과를 초래하기도 합니다.

<img width="500" height="500" alt="image" src="https://garden.bradwoods.io/images/contentBox.svg" />

<br/>

## ✅ `box-sizing: border-box`
`border-box`를 적용하면 `width`와 `height` 값이 내용 영역, `padding`, `border`를 모두 포함하는 크기를 나타냅니다. 

**즉, `width`와 `height`는 실제 콘텐츠의 크기뿐만 아니라 패딩과 테두리까지 포함된 크기로 설정됩니다.** 

- 예를 들어, `width: 200px`로 설정된 요소에 `padding: 20px`과 `border: 2px solid black`이 있으면, 콘텐츠의 크기는 자동으로 `200px - 20px * 2 - 2px * 2`로 계산되어, 실제 콘텐츠 영역의 크기는 156px가 됩니다. 

이 방식은 직관적으로 레이아웃의 크기를 예측하기 용이합니다.

<img width="500" height="500" alt="image" src="https://garden.bradwoods.io/images/borderBox.svg" />


