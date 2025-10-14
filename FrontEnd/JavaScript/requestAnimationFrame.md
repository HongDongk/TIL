# Q: requestAnimationFrame에 대해서 설명해주세요.
> `requestAnimationFrame()`은 **브라우저의 화면 갱신 주기에 맞춰 콜백 함수를 실행하도록 요청하는 API입니다.**  
> 이를 통해 애니메이션을 보다 부드럽게 렌더링하고 성능을 최적화할 수 있습니다.

`requestAnimationFrame()`의 목적은 **애니메이션을 위한 프레임 렌더링을 브라우저의 화면 갱신 속도에 맞추는 것입니다.** 

브라우저는 화면의 프레임을 1초당 60번(60fps)이나 120번(120fps) 갱신하는 것이 일반적인데, `requestAnimationFrame()`은 이러한 갱신 주기에 맞춰 콜백을 실행해줍니다.   
이를 통해 브라우저가 최적의 시점에 프레임을 렌더링하도록 보장하여 부드러운 사용자 경험을 제공하고, 불필요한 연산을 줄일 수 있습니다.

사용 예시를 들면, 반복 애니메이션 동작을 다음과 같은 형태로 구현할 수 있습니다.

```javascript
const animate = () => {
  /* 애니메이션을 위한 동작 */

  if (일정시간이지나면) {
    return;
  }
  
  requestAnimationFrame(animate)
}

requestAnimationFrame(animate)
```

물론, `setTimeout()`이나 `setInterval()`을 사용해도 일정한 간격으로 함수를 실행할 수 있지만, 브라우저의 화면 갱신 주기와 맞지 않는 경우가 발생합니다. 그리고 이로 인해 프레임 드롭 및 애니메이션의 끊김 현상이 발생할 수 있습니다. 반면, `requestAnimationFrame()`은 화면 갱신 주기에 맞춰 실행되므로 프레임 드롭 없이 애니메이션이 매끄럽게 보여지고, 성능 측면에서도 유리합니다.

<br/>

# Q: 이외에 추가적인 장점은 없나요? 

이외에도, **디스플레이의 주사율에 맞게 콜백의 실행 주기가 동적으로 조정된다**는 장점이 있습니다. 60Hz, 120Hz, 144Hz 등 여러 주사율의 디스플레이에서 최적의 타이밍을 찾아 실행됩니다. 

더불어, **백그라운드 탭이나 `hidden` 상태일 때는 실행을 중지한다는** 장점이 있습니다. 이는 사용자의 배터리 수명과 시스템 리소스 절약에 도움이 됩니다.

<br/>

# Q: requestAnimationFrame 콜백은 태스크 큐에서 관리되나요? 

`requestAnimationFrame()`의 콜백은 **태스크 큐나 마이크로태스크 큐와는 다른 곳에서 관리됩니다.** 

`requestAnimationFrame()`의 콜백은 **"map of animation frame callbacks"** 이라 불리는 map 형태의 자료구조에서 별도로 관리되며 독자적인 실행 주기를 갖습니다.








