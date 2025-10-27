# Q: 타입스크립트의 infer 키워드에 대해서 설명해주세요.
> **`infer` 키워드는 조건부 타입에서 특정 타입을 추론하는 데 사용됩니다.**  

즉, 타입을 직접 지정하는 것이 아니라 타입스크립트가 해당 타입을 유추할 수 있도록 돕는 역할을 합니다. `infer`는 `extends`를 사용하는 조건부 타입 안에서 활용되며, 특정 타입을 분해하여 사용할 수 있습니다.

간단한 예시를 설명드리겠습니다.

```javascript
type GetReturnType<T> = T extends (...args: any[]) => infer R ? R : never;
```
위 코드는 함수 타입 `T`의 반환 타입을 추출하는 유틸리티 타입입니다. `T`가 함수 타입이라면 infer R을 통해 반환 타입을 R로 추론하고, 그렇지 않다면 `never`을 반환합니다.

```javascript
type ReturnType = GetReturnType<() => string>; // string
```
주의할 점은, `infer`는 반드시 조건부 타입 안에서 사용되어야 합니다. 독립적으로 사용하면 문법 오류가 발생합니다.

<br/>

# Q: 설명 중에 언급하신 extends 키워드는 무엇인가요? 
`extends` 키워드는 타입스크립트에서 두 가지 주요 용도로 사용됩니다.

### ✅ 첫째, 제네릭에서 타입을 제한하는 역할을 합니다. 
예를 들어, 특정 타입이 반드시 string을 확장해야 한다면 다음과 같이 정의할 수 있습니다.

```javascript
type Example<T extends string> = T;
```

### ✅ 둘째, 조건부 타입에서 특정 타입이 다른 타입을 포함하는지를 확인하는 역할을 합니다.

```javascript
type Check<T> = T extends string ? '문자열' : '다른 타입';

type Example1 = Check<'hello'>; // '문자열'
type Example2 = Check<42>; // '다른 타입'
```

### 📚 제너릭이란?
> **타입을 변수처럼 사용하는 문법**  
> 즉, 함수나 클래스, 타입에서 입력되는 타입에 따라 동적으로 타입이 바뀌도록 만드는 기능

#### 제네릭 예시
```javascript
function identity<T>(value: T): T {
  return value;
}

const result2 = identity("hello"); // T가 string으로 추론됨 → 반환 타입도 string
```

#### 제네릭 + extends 예시
```javascript
function logLength<T extends { length: number }>(value: T): number {
  return value.length;
}

logLength("hello"); // ✅ string은 length 속성을 가짐
logLength([1, 2, 3]); // ✅ 배열도 length 속성을 가짐
logLength(123); // ❌ number는 length가 없음
```
여기서 `T extends { length: number }`는 "T가 length 속성을 가진 타입이어야 한다"는 제약조건입니다.
