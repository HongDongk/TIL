# Q: 왜 useState를 조건문 안에서 사용하면 안 되나요?

`useState()`를 조건문 안에서 사용하면 안 되는 이유는 **리액트가 state를 관리하는 방식이 `useState`를 호출하는 순서과 연관되어 있기 때문입니다.**

리액트는 **컴포넌트 내부에서 `useState()`가 호출된 순서를 기준으로 state를 저장하고 업데이트합니다.**   

그런데 `useState()`를 조건문 안에서 호출하면 특정 렌더링 시에는 호출되고, 다른 렌더링에서는 호출되지 않을 가능성이 생깁니다. 이렇게 되면 리액트가 호출 순서를 기반으로 state를 추적하는 과정에서 혼동이 발생하게 됩니다.

<br/>

예를 들어, 다음과 같은 코드가 있다고 가정해 보겠습니다.

```javascript
function Example() {
  const [count, setCount] = useState(0);   // #1
  const [name, setName] = useState("아무개"); // #2

  return <div>{count} - {name}</div>;
}
```
위 코드에서 React는 아래처럼 기억합니다 

> 첫 번째  `useState` → count  
> 두 번째  `useState` → name

즉, 1번째 state는 count, 2번째는 name 이런 식으로 ‘순서 기반 테이블’을 만들어서 저장해둡니다.

### 그런데 `useState`를 조건문 안에 넣으면?

```javascript
function Example({ show }) {
  if (show) {
    const [count, setCount] = useState(0); // 조건부 호출
  }

  const [name, setName] = useState("아무개");
  return <div>Example</div>;
}
```
위 코드에서 `show` 값이 true일 때만 `useState()`가 호출됩니다. 문제는, `show`가 false로 바뀌는 경우입니다.  
`show = false` 라면, `useState(0)`이 아예 호출되지 않고 바로 `useState("아무개")`가 호출되어 첫 번째로 인식됩니다.

React 입장에서는 아래처럼 동작해 내부적으로 state 매칭이 꼬여 버그가 납니다.

> 잠깐, 1번째 state는 count였는데 왜 갑자기 name이 들어오지?  
> 그럼 기존 count 값은 어디로 갔지?

<br/>

이러한 문제를 방지하기 위해서는 **`useState()`가 항상 컴포넌트의 최상위에서 호출되어야 합니다.**   
즉, 조건문이나 반복문, 함수 내부에서 호출하지 않아야 합니다.
