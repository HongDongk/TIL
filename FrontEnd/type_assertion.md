# Q: 타입 단언이란 무엇이며 언제 사용하나요?
> **컴파일러에게 특정 값이 어떤 타입인지 개발자가 더 잘 알고 있다고 알려주는 방법**

- **개발자가 `as`를 이용해 타입을 단언하면, 자동 추론된 타입을 덮어쓰게 됩니다.**
- 이는 컴파일러가 타입을 자동으로 추론하지 못하거나 잘못 추론하는 상황에서 사용됩니다.


예를 들어, DOM 요소를 가져오는 `document.getElementById()` 메서드의 반환 타입은 `HTMLElement | null`로 정의되어 있습니다. 하지만 개발자가 해당 요소가 `HTMLDivElement`임을 확신한다면, `as HTMLDivElement`를 사용해 컴파일러에게 명시적으로 알려줄 수 있습니다. 이를 통해 타입 오류 없이 안전하게 속성에 접근할 수 있습니다.

```javascript
const element = document.getElementById("myElement") as HTMLDivElement;

element.style.backgroundColor = "blue"; 
```
타입 단언은 주로 **API나 외부 라이브러리의 반환 타입을 확실히 알고 있을 때** 사용됩니다. 컴파일러가 타입 추론에 실패하거나 경고를 발생시키는 경우에 타입 단언을 통해 올바른 타입을 지정할 수 있습니다.

<br/>

# Q: 타입 단언을 사용할 때 주의할 점은 무엇인가요? 
타입 단언은 **컴파일러의 타입 검사를 우회하기 때문에, 실제 값이 단언한 타입과 다를 경우 런타임 에러가 발생할 수 있습니다.** 

따라서 타입 단언은 해당 타입을 확실히 알고 있을 때만 사용하는 것이 중요하며, 가능한 한 타입 추론과 타입 가드를 우선적으로 사용하는 것이 바람직합니다. 잘못된 사용은 타입스크립트의 장점을 훼손하며, 오히려 코드의 안정성을 해칠 수 있습니다.

<br/>

# Q: 타입 단언을 더 안전하게 활용하기 위한 원칙이 있나요? 


### ✅ 타입 단언보다는 타입 내로잉(narrowing)을 우선적으로 활용하는 것이 좋습니다. 
- 타입스크립트는 조건문과 타입 체크를 통해 자동으로 타입을 좁힐 수 있으므로, 가능한 한 단언 없이 타입을 명확히 하는 방식이 권장됩니다.
- 조건문이나 타입 체크를 통해 실제 값의 타입을 점점 좁혀 나가는 것

```javascript
function printLength(value: string | string[]) {
  if (Array.isArray(value)) {
    console.log(value.length); // 타입 내로잉으로 배열로 안전하게 처리
  } else {
    // 문자열로 처리
  }
}
```

### ✅ type predicate을 활용한 타입 가드를 통해서도 타입 안전성을 높일 수 있습니다. 
- type predicate을 통해 데이터 구조를 확인하여 런타임 오류를 줄이는 방식입니다.

```javascript
function isFish(pet: Fish | Bird): pet is Fish {
    return (pet as Fish).swim !== undefined;
}

if (isFish(pet)) {
    pet.swim();
}
```

### ✅ 타입 단언은 최소한의 범위에서만 사용하는 것이 좋습니다.
- 전체 객체보다는 필요한 속성이나 특정 부분만 단언하는 방식으로 불필요한 위험을 줄이는 것이 바람직합니다.

```javascript
const element = document.getElementById("myElement");
if (element) {
  (element as HTMLDivElement).style.backgroundColor = "blue"; // 필요한 부분만 단언
}
```

<br/>

