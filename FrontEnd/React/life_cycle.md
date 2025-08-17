# Q: 리액트의 생명주기란 무엇인가요?
> 리액트 컴포넌트는 기본적으로 브라우저 상에서 나타되고, 업데이트되며, 사라지는 과정을 거치게 됩니다.  
> 이러한 과정을 생명주기라 하며, 리액트의 모든 컴포넌트에는 생명주기가 존재합니다.

생명주기 내에서는 여러 메서드가 호출되며 이를 사용할 수 있는데 **클래스형 컴포넌트**에서는 생명주기 메서드를 사용하고, **함수형 컴포넌트**에서는 `Hook`을 사용할 수 있는 점에서 서로 차이가 있습니다.

<img width="1280" height="671" alt="image" src="https://github.com/user-attachments/assets/d1e584a6-09bd-4d5f-bf3c-b004bec6151d" />

## ✅ Mounting
**처음 컴포넌트가 생성되는 것을 마운팅(mounting)이라 합니다. 컴포넌트가 마운팅이 시작되면 아래와 같은 과정을 거칩니다.**

- 컴포넌트가 처음 마운팅 될 때 React는 컴포넌트의 `constructor`를 호출합니다.
- 다음으로 React는 컴포넌트의 `render()` 메서드를 호출합니다. `render()` 메서드를 통해 React는 화면에 표시되어야 할 내용(JSX)을 알게 되며, DOM을 업데이트합니다.
- 마지막으로 컴포넌트의 출력값(JSX)이 DOM에 삽입되면, React는 `componentDidMount()` 생명주기 메서드를 호출합니다. 

## ✅ Updating
**새로운 props를 받거나, setState()메서드로 state가 업데이트되는 등의 상황에서 리액트 컴포넌트는 업데이트됩니다.**

- `setState` 등으로 `state`가 변경된 상황을 React가 인지하면 화면에 표시될 내용을 알아내기 위해 `render()` 메서드를 다시 호출합니다.
- `render()` 메서드가 호출되면 마운팅 될 때와 마찬가지로 DOM을 업데이트 하고, `componentDidUpdate()`메서드를 호출합니다. 이를 이용해 컴포넌트가 업데이트 되었을때의 작업을 지정할 수 있습니다.

## ✅ Unmounting
**리액트 컴포넌트가 삭제되는 것, 즉 화면에서 사라지는 것을 의미 합니다.** 
- `componentWillUnmount()` 메서드는 컴포넌트가 화면에서 사라지기 직전에 호출됩니다.
- 이 메서드를 이용하여 API 연결을 해제하거나, 이전에 `setInterval` 함수를 이용하여 함수를 반복 호출했다면 `clearInterval`함수로 중단하는 등의 작업을 할 수 있습니다.

<br/>

## 🌈 함수형 컴포넌트에서의 생명주기
함수형 컴포넌트에는 별도의 생명주기 메서드가 없고,  
👉 `useEffect` 훅을 활용해 같은 역할을 수행합니다.

```javascript
useEffect(() => {
  // Mount 시 실행
  console.log("컴포넌트 마운트됨");

  return () => {
    // Unmount 시 실행 (cleanup)
    console.log("컴포넌트 언마운트됨");
  };
}, []); // 의존성 배열이 비어있으면 Mount/Unmount에만 실행

useEffect(() => {
  // 특정 값이 바뀔 때 실행 (Update)
  console.log("state나 props가 변경됨");
}, [someState]);
```

