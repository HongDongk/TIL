# Q: 다음 Promise 코드의 실행 결과를 설명해주세요.

```javascript
setTimeout(() => {
    console.log('1')
    
    setTimeout(() => {console.log('2')} )

    Promise.resolve().then(()=> console.log('3'))
    
    console.log('4')
})

Promise.resolve().then(() => {
    console.log('5')
    
    setTimeout(() => {console.log('6')} )

    Promise.resolve().then(()=> console.log('7'))
    
    console.log('8')
})

console.log('9')
```
답: `9 → 5 → 8 → 7 → 1 → 4 → 3 → 6 → 2`

이벤트 루프는 아래와 같은 과정을 반복하여 태스크를 처리합니다.
- 동기 코드를 순차적으로 처리
- 마이크로태스크 큐의 모든 태스크를 처리 (큐가 비워질 때까지)
- 매크로태스크 큐에서 하나의 태스크를 가져와 처리
- 다시 1번으로 돌아감

<br/>

위 규칙에 따라 처리되었을 때 구체적인 실행 과정은 다음과 같습니다.

전역 실행 컨텍스트 내 동기 코드인 `console.log('9')`가 가장 먼저 실행되어 1️⃣ 9가 출력됩니다.

그 후 전역 실행 컨텍스트의 `Promise.then()` 핸들러가 마이크로태스크 큐에서 처리되며 내부의 동기 코드가 실행되어 2️⃣ 5와 3️⃣ 8이 출력됩니다.

이어서 동일 `Promise.then()` 핸들러 내부의 `Promise.then()` 핸들러가 마이크로태스크 큐에서 처리되어 `console.log('7')`이 실행되며 4️⃣ 7이 출력됩니다.

그 다음 첫 번째 `setTimeout()`의 콜백이 매크로태스크 큐에서 처리되며 내부의 동기 코드가 순차 실행되어 5️⃣ 1과 6️⃣ 4가 출력됩니다.

그 후 동일 `setTimeout()` 콜백 내부의 `Promise.then()`이 마이크로태스크 큐에서 처리되며 `console.log('3')`이 실행되어 7️⃣ 3이 출력됩니다.

이어서 남은 매크로태스크 중에서 먼저 등록된 `console.log('6')`이 처리되어 8️⃣ 6이 출력되며, 끝으로 9️⃣ 2가 출력됩니다.

따라서 최종 출력 순서는 `9 → 5 → 8 → 7 → 1 → 4 → 3 → 6 → 2`가 됩니다.





