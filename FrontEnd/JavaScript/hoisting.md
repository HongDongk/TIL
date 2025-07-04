# Q: 자바스크립트 호이스팅에 대해서 설명해주세요.
> 호이스팅은 자바스크립트가 **코드를 실행하기 전에 변수와 함수 선언이 코드의 최상단으로 끌어올리는 것처럼 동작**하는 것입니다.  
> 이 때문에 코드의 선언된 위치보다 상단에서 변수에 접근할 수 있는 것처럼 보일 수 있습니다. 

- 한편, 호이스팅은 값 할당까지 끌어올리지는 않습니다. 
- 예를 들어 `var`로 선언된 변수는 선언과 초기화는 끌어올려지지만 값 할당은 끌어올려지지 않기 때문에,
- 값 할당이 이뤄지기 전까지는 `undefined`로 평가됩니다. 예시는 다음과 같습니다.

 ```javascript
 console.log(myVar); // undefined

 var myVar = 10;
 console.log(myVar); // 10
 ```

- 반면, 함수 선언식은 함수 자체가 호이스팅되기 때문에, 함수 호출을 선언 이전에 해도 문제가 없습니다.

 ```javascript
 console.log(myFunction()); // 'Hello World' 출력

 function myFunction() {
   return 'Hello World';
 }
 ```

- 초기화: 변수를 선언하면서 기본값을 자동으로 설정하는 것 `var x;` → x는 `undefined`로 초기화됨  
- 값 할당: 변수에 원하는 값을 대입하는 것	`x = 5;`

**단, ES6에서 도입된 let과 const는 선언문 이전에 접근하려고 하면 `ReferenceError`가 발생합니다.**

- 이는 `Temporal Dead Zone(TDZ)` 이라는 개념 때문입니다. **TDZ는 변수가 선언되었지만 초기화되기 전까지의 구간**을 말합니다. 
- let과 const로 선언된 변수에는 `TDZ`가 존재하며, 이 구간에서는 변수에 접근할 경우 `ReferenceError`가 발생합니다. 
- `TDZ`는 코드에서 변수가 선언된 시점부터 초기화될 때까지의 구간에서 변수를 사용하지 못하게 막아주는 역할을 합니다.

 ```javascript
 console.log(myLet); // ReferenceError 발생

 let myLet = 10;
 ```
참고로, let 변수는 선언 자체는 호이스팅되지만 초기화가 호이스팅되지 않습니다. 선언 즉시 `undefined`로 초기화되는 var와 다르게, let은 해당 라인의 코드가 실행될 때까지 초기화가 이루어지지 않는 것입니다.

지금까지의 내용을 정리하면, 호이스팅은 변수와 함수 선언을 코드 상단으로 끌어올리는 것처럼 동작하는 특징을 가리킵니다.   
var는 초기화 전에 접근 시 `undefined`로 나타나며, let과 const는 `TDZ`로 인해 초기화 전에 접근하면 `ReferenceError`를 발생시킵니다.
