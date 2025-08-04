# Q: Promise의 resolve()와 fulfilled에 대해서 설명해주세요.

`resolve()`와 `fulfilled`는 `Promise`에서 비동기 처리시 사용되는 값들이지만, 차이점이 존재합니다. 

- `resolve()`는 **Promise를 완료시키는 함수**이고
- `fulfilled`는 **Promise가 완료된 상태**를 뜻합니다.


**resolve()는 Promise가 성공적으로 끝났을 때 결과 값을 넘겨주는 함수입니다.**

- 예를 들어 어떤 비동기 작업이 잘 끝났을 때, `resolve()`를 호출해서 "이 작업이 끝났고 결과는 이것이다"라고 전달하게 됩니다.     
- 이렇게 `resolve()`가 호출되면, Promise의 상태는 '이행됨' 상태로 바뀌는데, 이를 fulfilled라고 부릅니다.

- 예를 들어, `new Promise((resolve, reject) => { resolve('완료'); })`처럼 `resolve()`를 호출하면, 이 Promise의 상태는 fulfilled로 변경됩니다.
- 이처럼 `resolve()`는 fulfilled 상태로 전환시키는 역할을 합니다.

**따라서 `resolve()`는 Promise를 성공적으로 마무리 짓는 행위라고 볼 수 있고, `fulfilled`는 그 결과로 발생하는 완료된 상태를 의미합니다.**

<br/>

# Q: resolve에서 작업이 실패할 수도 있나요?

#### `resolve()`가 실패하는 상황은 발생하지 않습니다.   

- `resolve()`는 Promise를 '이행'으로 만드는 함수이기 때문에, 성공적인 결과를 전달할 때 사용되며 실패 자체와는 관련이 없습니다.
- **만약 Promise가 실패한다면, `resolve()`가 호출조차 되지 않고 `reject()`가 호출됩니다.**

비동기 작업이 성공적으로 완료되면 `resolve()`가 호출되어 fulfilled 상태가 되고,    
오류나 실패가 발생하면 `resolve()`가 아닌 `reject()`가 호출되어 rejected 상태가 됩니다.

추가로, `then()`은 `resolve()`된 값을 처리하고, catch()는 reject()된 오류를 처리하는 식으로 Promise의 결과를 다루게 됩니다.


