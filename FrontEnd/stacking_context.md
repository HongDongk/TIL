# Q: 쌓임 맥락에 대해 설명해주세요.
> 쌓임 맥락(Stacking Context)은 **가상의 z축을 상정하여 HTML 요소들을 3차원으로 개념화**한 것입니다.  
> 쌓임 맥락은 요소들이 쌓이는 순서에 영향을 미칩니다.

기본적으로 HTML 요소는 DOM 순서에 따라 쌓입니다. HTML 상에서 위쪽에 위치할수록 아래쪽에 쌓이는 방식입니다. 또한, `position` 속성이 적용되어 있는 요소들은 `z-index` 값이 낮을수록 아래쪽으로, 높을수록 위쪽으로 쌓입니다.

그런데 **특정 조건이 충족되면 새로운 쌓임 맥락이 생성**됩니다. 이 쌓임 맥락은 독립적인 3차원 공간을 만들며, 부모 쌓임 맥락의 영향을 받지 않고 해당 쌓임 맥락 내에서만 비교가 이뤄져 쌓임 순서가 결정됩니다.

대표적으로 쌓임 맥락이 생성되는 조건은 다음과 같습니다. 

- `position` 속성이 `relative` 또는 `absolute`이고 `z-index` 값이 auto가 아닌 경우
- `position` 속성이 `fixed` 또는 `sticky`인 경우
- `display`가 `flex` 또는 `grid`이고, `z-index`가 설정된 경우
- `opacity` 값이 1 미만인 경우
- `transform`, `filter`, `backdrop-filter` 등의 속성이 적용되는 경우

<br/>

쌓임 맥락이 동작하는 간단한 예시를 설명드리겠습니다.

```html
<div style="position: relative; z-index: 1;">
    A 요소 (z-index: 1)
    <div style="position: absolute; z-index: 999;">
        A-1 요소 (z-index: 999)
    </div>
</div>

<div style="position: relative; z-index: 2;">
    B 요소 (z-index: 2)
</div>
```
위 예시에서 가장 위쪽에 쌓이는 요소는 B 요소입니다. 그 다음 A-1 요소, A 요소 순으로 쌓입니다.

- 최상위 쌓임 맥락 내의 요소들인 A 요소와 B 요소의 `z-index` 값을 비교했을 때, B 요소가 크기 때문에 가장 위쪽에 쌓입니다.
- 그리고 A 요소가 형성한 쌓임 맥락 내에서 `z-index` 값을 비교했을 때, A 요소보다 `z-index`가 큰 A-1 요소가 더 위쪽에 쌓이게 됩니다.
- 이런 예시를 보면 `z-index` 값이 더 크다고 무조건 위쪽에 쌓이는 것이 아니며, 쌓임 맥락을 고려해야 한다는 사실을 알 수 있습니다.
