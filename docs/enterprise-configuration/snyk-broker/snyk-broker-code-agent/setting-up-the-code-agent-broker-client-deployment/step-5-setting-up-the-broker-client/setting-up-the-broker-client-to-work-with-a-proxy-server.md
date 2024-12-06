# Proxy 서버와 함께 작동하도록 Broker 클라이언트 설정하기

{% hint style="info" %}
이 지침은 코드 스니펫을 사용한 Broker 클라이언트 설정에도 적용됩니다.
{% endhint %}

프록시를 사용하는 인프라에서 코드 에이전트 - Broker 클라이언트 배포를 사용하려면 코드 에이전트에 대한 요청이 프록시를 통해 전송되지 않고 우회하는지 확인합니다.

Broker 클라이언트 컴포넌트의 경우, docker 실행 명령에 다음 환경 변수와 코드 에이전트를 우회하는 명령을 추가합니다:

```
-e HTTP_PROXY=http://my.proxy.address:<port_no.>
-e HTTPS_PROXY=http://my.proxy.address:<port_no.>
-e NO_PROXY=<code_agent_container_name>
```

프록시에 사용자 이름 및 비밀번호 인증이 필요한 경우 다음 환경 변수도 추가하세요:

```
-e PROXY_AUTH=userID:userPass
```

또한 이러한 환경 변수를 코드 에이전트 컴포넌트에 추가합니다. [Proxy 서버와 함께 작동하도록 코드 에이전트 설정하기](../step-4-setting-up-the-code-agent/setting-up-the-code-agent-to-work-with-a-proxy-server.md)를 참조하세요.

프록시와 함께 Docker 컨테이너를 사용하는 방법에 대한 자세한 내용은 [프록시 서버를 사용하도록 Docker 구성하기](https://docs.docker.com/network/proxy/)를 참조하세요.
