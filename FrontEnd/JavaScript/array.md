# Q: 자바스크립트 배열에 대해서 설명해주세요.

> 자바스크립트의 배열은 **순서가 있는 리스트형 객체**로, 여러 값을 하나의 자료구조에 저장할 수 있습니다.  
> 배열은 **제로 인덱스 기반**으로, 배열의 각 값은 인덱스를 통해 접근할 수 있습니다. 

- 자바스크립트 배열의 중요한 특징 중 하나는 `동적 배열`이라는 점입니다.
- 이는 배열의 크기를 미리 지정하지 않아도 되고, 요소를 추가할 때마다 배열의 크기가 자동으로 조정됩니다.

 ```javascript
 const arr = [1, 2, 3];
 arr.push(4);
 console.log(arr); // [1, 2, 3, 4]
 ```

또한, 배열의 특정 인덱스에 값을 할당하면, 배열이 자동으로 확장됩니다.

 ```javascript
 arr[5] = 6;
 console.log(arr); // [1, 2, 3, undefined, undefined, 6]
 console.log(arr.length); // 6
 ```
- 이처럼 자바스크립트 배열은 동적으로 크기가 조정되는 유연성을 제공합니다.
- 요소를 추가하거나 특정 인덱스에 값을 할당하면, 배열은 자동으로 확장됩니다.

또한, 배열은 자바스크립트의 **객체**와 유사한 방식으로 관리되며, **해시 테이블과 같은 자료구조**로 구현되어 있습니다. 

이 덕분에 배열 요소들은 메모리 상에서 연속적이지 않아도 되며, 배열 크기를 미리 지정하지 않고 유연하게 사용할 수 있습니다.
