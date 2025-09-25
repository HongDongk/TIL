# Q: Server Action이란 무엇인가요?

`Server Action`은 Next.js에서 제공하는 기능으로, **서버에서 실행되며 브라우저에서 호출할 수 있는 비동기 함수**입니다. 

이 기능은 서버 로직을 직접 호출함으로써 클라이언트와 서버 간의 상호작용을 간소화할 수 있게 해줍니다. 

예를 들면 **백엔드 서버와 API 통신을 하는 대신 Next 서버에서 데이터베이스에 직접 접근**하는 식으로 활용할 수 있습니다.

```javascript
"use server";

export async function createReviewAction(data: FormData) {
  const content = data.get("content");
  // 데이터베이스 저장 등의 작업
}
```

```javascript
// 컴포넌트에서 사용
<form action={createReviewAction}>
  <textarea name="content" required />
  <button type="submit">Submit</button>
</form>
```
이처럼 `Server Action`을 이용하면 폼이 제출될 때 해당 정보를 가지고 데이터베이스 저장과 같은 서버 작업을 수행할 수 있습니다.

<br/>

# Q: Server Action의 장점은 무엇인가요? 

### ✅ 첫째, 클라이언트와 서버 간 상호작용을 간소화할 수 있습니다. 
기존에는 데이터베이스와 관련된 처리를 위해 백엔드 API와 통신하는 방식을 사용했습니다. 만약 `Server Action`을 이용한다면 백엔드 API와 통신하지 않고, Next 서버에서 직접 데이터베이스 작업을 수행할 수 있습니다. 

이러한 점은 개발 생산성 향상에 도움이 될 수 있습니다. 또한 네트워크 통신을 줄여 성능 면에서도 이점이 있을 수 있습니다.

### ✅ 둘째, Server Action 로직은 클라이언트에 전송되지 않습니다. 이는 보안에 도움이 될 수 있습니다. 
외부에 노출되면 안 되는 정보나 로직을 숨기는 데 활용할 수 있습니다. 더불어 클라이언트 단의 일부 로직을 `Server Action`으로 옮긴다면 번들의 크기가 줄어드는 데도 기여할 수 있습니다.

### ✅ 셋째, JS가 로드되기 이전의 시점에도 서버와 상호작용할 수 있게 됩니다. 
`Server Action`은 html `<form>`의 `action` 속성을 이용하여 폼 데이터를 서버에 전송합니다. 따라서 JS가 로드되지 않거나 비활성화되어도 서버와 통신이 가능하다는 장점이 있습니다.









