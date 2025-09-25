# Q: CORS 설정 없이 SOP를 우회하여 외부 서버와 통신할 수 있는 방법이 있을까요?
> **프록시 서버**를 이용한다면 CORS 설정 없이도 SOP를 우회할 수 있습니다. 여기서 이야기하는 프록시 서버는 **브라우저 대신 외부 서버에 요청을 보내고 응답을 받는 역할을 대리 수행하는 서버**입니다.

브라우저 측에서 직접 외부 서버에 요청을 보내지 않고, 클라이언트와 동일한 origin의 프록시 서버를 통해 요청을 보내면 SOP(Same-Origin Policy)의 제한을 피할 수 있습니다.

- 예를 들어, 클라이언트 측 도메인이 `client.com`이고, 서버 측 도메인이 `server.com`라고 가정하겠습니다.
- 이때 CORS 설정을 별도로 하지 않았다면, 도메인이 다르므로 브라우저 단에서 SOP에 의해 통신이 차단됩니다.
- 그런데 이때 만약 브라우저가 아닌 클라이언트 서버를 통해 `server.com`에 요청을 보낸다면 응답을 받을 수 있게 됩니다.
- 서버와 서버 간의 통신에는 SOP가 적용되지 않기 때문입니다.
- 이후, 클라이언트 서버는 `client.com/api/xxx`와 같은 경로로 `server.com`으로부터 받은 응답을 브라우저(클라이언트)에 반환합니다.
- 이렇게 하면 클라이언트 측 origin과 서버 측 origin이 `client.com`으로 일치하기 때문에 정상적으로 응답을 수신할 수 있게 됩니다.

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/1bd3ab99-2bb5-4516-993c-1990de0aca7b" />


### ✅ [Proxy Server 정리내용](https://velog.io/@hongdongk/Nginx%EC%99%80-Web-Server)

