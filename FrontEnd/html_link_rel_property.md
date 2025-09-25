# Q: HTML link 요소의 rel 속성 값 preconnect, preload, prefetch에 대해 설명해주세요.

`<link>`는 외부 리소스와의 연결을 돕는 요소이며, rel 속성 값인 `preconnect`, `preload`, `prefetch`는 리소스 로드의 우선순위를 설정하여 로드 성능을 최적화하기 위해 사용됩니다.

### ✅ preconnect
**브라우저가 특정 origin에 대한 네트워크 연결을 미리 설정하도록 지시합니다.**
- 이를 통해 DNS 조회, TLS 핸드셰이크, TCP 연결을 미리 완료하여 리소스 로드 지연을 줄일 수 있습니다. 
- 외부 API나 CDN의 리소스를 사용할 경우 `preconnect`를 사용하면 첫 번째 요청의 대기 시간을 줄일 수 있습니다.

```
<link rel="preconnect" href="https://external-resource.com" crossorigin="anonymous">
```

### ✅ preload
**특정 리소스를 미리 가져오도록 브라우저에 지시합니다.**
- 예를 들어, 웹 폰트를 `preload`하면 해당 리소스가 실제로 사용되기 전에 다운로드가 완료됩니다.
```
<link rel="preconnect" href="https://external-resource.com" crossorigin="anonymous">
```

### ✅ prefetch
**브라우저가 향후 필요할 가능성이 있는 리소스를 미리 가져오도록 지시합니다.**
- `preload`와는 다르게, 현재 화면에 즉시 필요하지 않지만 다음에 필요할 가능성이 있는 리소스를 미리 로드하는 역할을 합니다.
- `prefetch`는 다른 속성 값에 비해 우선순위가 상대적으로 낮습니다.
```
<link rel="prefetch" href="/next-page.css" as="style">
```

<br/>

사용자가 페이지에서 버튼을 클릭해 다음 화면으로 이동할 가능성이 높을 경우, 다음 화면에 필요한 css 리소스를 미리 준비하는 방식으로 사용할 수 있습니다.

