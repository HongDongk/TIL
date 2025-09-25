# Q: 상황에 따라 this 바인딩이 어떻게 이뤄지는지 설명해주세요.
> 자바스크립트에서 `this`는 함수가 호출되는 방식에 따라 값이 달라집니다.  
> 다양한 상황에서 `this`가 어떻게 바인딩되는지 크게 6가지 상황으로 나누어 설명드리겠습니다.

### 1. 전역호출

전역에서 함수가 호출되면, `this`는 **전역 객체를 참조**합니다. 브라우저 환경에서는 `window` 객체를, Node.js 환경에서는 `global` 객체를 가리킵니다.

```javascript
function globalFunc() {
  console.log(this);
}
globalFunc(); // 브라우저: window, Node.js: global
```

### 2. 메서드 호출

객체의 메서드로 호출된 함수에서는 `this`가 **해당 객체를 참조**합니다.

```javascript
const obj = {
  name: "Alice",
  greet: function () {
    console.log(this.name);
  },
};
obj.greet(); // "Alice"
```

### 3. 생성자 함수와 클래스

생성자 함수나 클래스에서 `this`는 **새로 생성되는 객체, 즉 인스턴스를 참조합니다.**

```javascript
function Person(name) {
  this.name = name;
}
const person = new Person("Alice");
console.log(person.name); // "Alice"
```

### 4. 명시적 바인딩

`call()`, `apply()`, `bind()` 메서드를 사용하면 **`this`를 명시적으로 설정할 수 있습니다.**

```javascript
function greet() {
  console.log(this.name);
}
const user = { name: "Alice" };
greet.call(user); // "Alice"
```

### 5. 화살표 함수

화살표 함수는 **상위 스코프의 `this`를 상속**받습니다. 자체적인 this를 가지지 않으므로, 사용 위치에 따라 this가 결정됩니다.

```javascript
const obj = {
  name: "Alice",
  greet: () => console.log(this.name),
};
obj.greet(); // undefined (전역 `this`)
```

### 6. DOM 이벤트 핸들러

DOM 요소의 이벤트 핸들러에서 `this`는 기본적으로 **이벤트를 발생시킨 요소를 참조**합니다. 하지만 화살표 함수를 사용하면 상위 스코프의 this를 참조합니다.

```javascript
button.addEventListener("click", function () {
  console.log(this); // 클릭된 button 요소
});
```

<br/>

지금까지 설명드린 것과 같이 this는 함수 호출 방식에 따라 값이 달라집니다. 따라서 상황에 따른 동작을 이해하고 적절한 방식을 사용해야 합니다. 특히, 화살표 함수와 명시적 바인딩은 this를 제어하는 데 유용합니다.

### [📚 this 바인딩 관련 정리글](https://velog.io/@hongdongk/JavaScript%EC%9D%98-this%EC%9D%98)

