# Q: localStorage와 sessionStorage의 차이점에 대해서 설명해주세요.
> `localStorage`와 `sessionStorage`는 브라우저에서 제공하는 클라이언트 측 저장소로, 둘 다 데이터를 키-값 쌍 형태로 저장합니다.

브라우저 저장소는 데이터를 암호화하거나 보호할 방법이 기본적으로 제공되지 않기 때문에 **민감한 데이터를 직접 저장하지 않는 것이 가장 중요합니다.**

예를들어, 인증 토큰이나 사용자 비밀번호는 `localStorage` 또는 `sessionStorage`에 저장하지 않고, **`HTTP-Only` 쿠키를 사용**합니다.

이렇게 하면 자바크스립트에서 접근할 수 없으므로 XSS 공격에 대한 위험을 줄일 수 있습니다.

### [✅ 브라우저 웹 스토리지 정리글](https://velog.io/@hongdongk/%EC%9B%B9%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80-%EC%BA%90%EC%8B%9C)





