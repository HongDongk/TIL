# Q: useRef는 언제 사용하나요?

`useRef()`는 React의 훅 중 하나로, **컴포넌트 내에서 변경 가능한 값을 저장하고 관리**할 수 있게 해줍니다.   
`useRef()`는 주로 두 가지 목적에 사용됩니다. **DOM 요소에 접근하거나, 값을 유지하면서도 렌더링을 트리거하지 않기 위해** 사용됩니다.

### ✅ 첫째, `useRef()`는 DOM 요소에 접근할 때 사용됩니다. 
- 예를 들어, **특정 DOM 요소에 직접 접근하고 싶을 때** `useRef()`를 사용하여 해당 요소의 참조를 얻을 수 있습니다.   
- 이는 `useEffect()`나 이벤트 핸들러 내에서 해당 DOM 요소에 직접 작업을 수행할 때 유용합니다. 예를 들어, 입력 필드에 포커스를 설정하고 싶을 때, `useRef()`를 사용해 input 요소에 접근할 수 있습니다.

```javascript
const inputRef = useRef(null);

useEffect(() => {
  inputRef.current.focus(); // 컴포넌트 마운트 시 input에 포커스를 맞춘다.
}, []);

return <input ref={inputRef} />;
```

### ✅ 둘째, useRef는 값을 유지하면서도 렌더링을 트리거하지 않기 위해 사용됩니다. 
- 일반적으로 상태 값을 관리할 때 사용하는 `useState()`는 상태 변화가 리렌더링을 트리거하는 반면, `useRef()`는 값이 변경되어도 리렌더링을 트리거하지 않습니다.
- 예를 들어, 타이머 id를 추적할 때 `useRef()`를 사용할 수 있습니다.

```javascript
const timerRef = useRef(null);

const startTimer = () => {
  timerRef.current = setInterval(() => {
    console.log('타이머 실행')
  }, 1000);
};

const stopTimer = () => {
  clearInterval(timerRef.current); // 타이머를 정지한다.
};
```

위 예시에서 `useRef()`를 이용하여 타이머의 id를 추적하면서도 해당 상태 값이 업데이트될 때 컴포넌트를 리렌더링하지 않습니다.

