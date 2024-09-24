# Docker를 통한 프록시 지원

프록시 구성에 대해서는 [프록시 서버를 사용하도록 Docker 구성](https://docs.docker.com/network/proxy/)을 참조하세요.

```
 -e HTTP_PROXY=http://my.proxy.address:8080
 -e HTTPS_PROXY=http://my.proxy.address:8080
 -e NO_PROXY=*.test.example.com,.example2.com,127.0.0.0/8
```

프록시에 사용자 이름 및 비밀번호 인증이 필요한 경우 다음과 같은 추가 환경 변수를 제공하세요:

```
-e PROXY_AUTH=userID:userPass
```
