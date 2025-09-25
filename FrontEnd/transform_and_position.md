# Q: 위치를 동적으로 변경할 때 css 속성 중 transform과 position 중 어떤 것을 선호하시나요?

`transform`과 `position`은 각각 적합한 경우가 다른데, **애니메이션이나 동적인 위치 변경이 필요한 경우 `transform`을 선호**합니다.

#### ✅ `transform`을 선호하는 이유는 성능 때문입니다. 
- `transform`은 브라우저의 `composite` 단계에서 실행됩니다. 따라서 reflow나 repaint를 유발하지 않아 성능 상 이점이 있습니다.

#### ✅ 반면, `position` 관련 속성을 이용한 위치 변경은 reflow, repaint를 유발합니다. 
- 예를 들어 top, left 등의 속성을 변경하면 브라우저는 주변 요소들의 위치를 다시 계산하는 과정부터 다시 수행하며, 이는 성능 부하를 높입니다.

<br/>

두 방식을 사용하여 버튼 호버 시 살짝 위로 올라가는 효과를 구현하면 각각 다음과 같습니다.

```css
/* transform: 성능이 더 좋음 */
.button:hover {
  transform: translateY(-5px);
}

/* position: 성능이 상대적으로 떨어짐 */
.button {
  position: relative;
}
.button:hover {
  top: -5px;
}
```

<br/>

# Q: 그렇다면 position 관련 속성은 사용하지 않나요? 

아닙니다. **레이아웃의 구조를 잡거나, 부모를 기준으로 위치를 조정**할 때에는 `position`을 사용합니다. 

`transform`은 시각적인 위치만 변경할 뿐 실제 문서 흐름과는 무관하게 동작하기 때문에, 문서 흐름에 따라 조정되는 경우에는 사용할 수 없기 때문입니다.




