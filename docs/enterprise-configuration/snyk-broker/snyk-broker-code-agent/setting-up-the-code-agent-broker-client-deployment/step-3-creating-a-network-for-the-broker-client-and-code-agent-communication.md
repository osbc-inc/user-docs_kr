# 3단계: Broker 클라이언트와 코드 에이전트 통신을 위한 네트워크 만들기

코드 에이전트로 Snyk Broker 를 실행하려면 두 에이전트 간에 네트워크 연결을 설정해야 합니다. 이를 위해 여기에 설명된 대로 Docker 브리지 네트워크를 생성할 수 있습니다.

{% hint style="info" %}
도커 브리지 네트워크에 대한 자세한 내용은  [Docker 문서](https://docs.docker.com/network/bridge/)를 참조하세요.

Broker 클라이언트와 코드 에이전트 간에 이 네트워크 연결을 설정하려면 Ngrok과 같은 다른 방법과 도구를 사용할 수도 있습니다.
{% endhint %}

**Docker 브리지 네트워크 실행을 만들려면** 다음과 같이 하세요:

```
docker network create <network_name>
```

여기서 `network_name`은 Broker 클라이언트와 코드 에이전트 간의 새 네트워크 이름입니다(예: Broker 클라이언트와 코드 에이전트):

```
docker network create mySnykBrokerNetwork
```

여기서 `mySnykBrokerNetwork`는 새 네트워크의 이름입니다.

**네트워크 생성을 확인하려면** 실행합니다:

```
docker network ls
```

출력은 다음과 비슷합니다:

```
NETWORK ID     NAME                  DRIVER    SCOPE
cb352a803eb0   mySnykBrokerNetwork   bridge    local
```
