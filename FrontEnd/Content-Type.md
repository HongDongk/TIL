# Q: Content-Type 헤더에 대해서 설명해주세요.
> `Content-Type`은 **HTTP 요청과 응답에서 전송되는 데이터의 타입을 명시하는 헤더**입니다.
> 서버와 클라이언트가 데이터를 주고받을 때, 올바르게 해석할 수 있도록 하기 위해 사용합니다.

예를 들어, JSON 데이터를 전송할 경우 `Content-Type: application/json`을 사용하면, 서버는 해당 데이터가 JSON 형식이라는 것을 알고 적절한 방식으로 해석할 수 있습니다. 혹은 서버가 클라이언트에게 HTML을 응답할 때 `Content-Type: text/html`을 지정하면 브라우저는 이를 HTML로 렌더링할 수 있습니다.

`Content-Type` 헤더는 **MIME 타입을 기반으로 하며**, `[type]/[subtype]` 형식으로 구성됩니다. 예를 들어, JSON 데이터는 `application/json`, HTML 문서는 `text/html`를 사용합니다. 만약 파일을 업로드하는 경우에는 `multipart/form-data`를 사용합니다.

`Content-Type` 헤더를 정확하게 지정하지 않으면, 클라이언트나 서버에서 데이터를 올바르게 해석하지 못할 수 있습니다. 예를 들어, JSON 데이터를 전송하면서 `Content-Type: application/x-www-form-urlencoded`로 설정하면 서버는 데이터를 잘못된 방식으로 처리하거나, `415 Unsupported Media Type`를 반환할 수 있습니다.

<img width="500" height="485" alt="image" src="https://github.com/user-attachments/assets/485f4f31-ec9a-4a37-9b08-574f812a1b29" />


<br />

# Q: Content-Type과 Accept 헤더의 차이는 무엇인가요?

`Content-Type` 헤더는 **전송되는 데이터의 타입**을 지정하는 반면, `Accept` 헤더는 **응답으로 받고자 하는 데이터의 타입**을 지정합니다. 

예를 들어, 클라이언트가 JSON 응답을 원할 경우 `Accept: application/json`을 설정하면, 서버는 가능하면 JSON 형식으로 응답을 반환하게 됩니다.


