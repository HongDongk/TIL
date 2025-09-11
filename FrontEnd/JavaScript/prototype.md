# Q: 프로토타입 상속의 동작 방식에 대해 설명해주세요.
> 프로토타입은 JS에서 **객체 간의 상속**을 구현하는 메커니즘입니다.  
> JS의 모든 객체는 기본적으로 `[[Prototype]]`이라는 숨김 프로퍼티를 가지고 있으며, 이 프로퍼티는 다른 객체를 참조하거나 null 값을 가집니다.  
> 프로토타입 연결은 `Object.create()`나 함수 생성자의 `prototype` 프로퍼티를 통해 이루어집니다.

프로토타입 상속이 동작하는 방식은 프로토타입 체인을 기반으로 합니다. 객체에서 어떤 프로퍼티를 접근하려고 할 때, 자바스크립트 엔진은 해당 객체에서 프로퍼티를 찾습니다.  

그리고 만약 찾을 수 없다면, 객체의 `[[Prototype]]`이 가리키는 프로토타입 객체에서 프로퍼티를 탐색합니다. 만약 프로토타입 객체에서도 해당 프로퍼티를 찾지 못하면, 그 다음에는 프로토타입의 프로토타입을 탐색합니다.   

탐색 과정을 계속 반복하면서 결국 원하는 프로퍼티를 찾거나, 프로토타입이 null이 되는 단계에 도달할 때까지 프로토타입 체인을 타고 올라가는 방식으로 탐색합니다. 이런 식으로 프로토타입이 꼬리에 꼬리를 물고 연결된 형태를 두고 **프로토타입 체인**이라고 부르는 것입니다.

```javascript
// 1) Object.create()를 이용한 방식
const dog = {
  greet() {
    console.log('Hello from dog!');
  }
};

const maru = Object.create(dog); // maru의 프로토타입이 dog로 설정됨
maru.greet(); // "Hello from dog!" 출력
```

```javascript
// 2) prototype 프로퍼티를 이용한 방식
function Dog() {}
Dog.prototype.greet = function () {
  console.log('Hello from Dog!');
};

const maru = new Dog(); // maru의 프로토타입이 dog로 설정됨
maru.greet(); // "Hello from Dog!" 출력
```

객체 `maru`가 `dog`를 프로토타입으로 갖는다고 가정해봅시다. 
- 만약 `maru.greet()`을 호출했을 시 `maru`에 `greet()`이 없으면 프로토타입인 `dog`에 `greet()`이 존재하는지 탐색합니다.
- 이때 `dog`에 `greet()`이 존재하면 탐색을 멈추고 해당 메서드를 호출합니다.
- 만약 `dog`에도 존재하지 않는다면 프로토타입 체인의 끝에 도달할 때까지 상위 프로토타입을 계속 탐색해 나갑니다.


