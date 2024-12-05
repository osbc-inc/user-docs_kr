# 2단계: 기존 Broker 클라이언트 제거하기

{% hint style="info" %}
This section applies only if you already have a running Broker Client. If you do not have a 이 섹션은 이미 실행 중인 Broker 클라이언트가 있는 경우에만 적용됩니다. 아직 Broker 클라이언트가 없는 경우 [3단계 - Broker 클라이언트 및 코드 에이전트 통신을 위한 네트워크 생성](step-3-creating-a-network-for-the-broker-client-and-code-agent-communication.md)으로 진행하세요.
{% endhint %}

동일한 조직 및 동일한 통합에 대해 실행 중인 Broker 클라이언트가 있는 경우, 코드 에이전트에 대한 새 Broker 클라이언트를 설정하기 전에 Broker 클라이언트를 중지하고 제거하세요. Broker 클라이언트는 코드 에이전트와 통신해야 하며 이 통신은 Broker 클라이언트 컨테이너의 설정 명령에서 구성되므로 기존 Broker 클라이언트 컨테이너를 코드 에이전트 작업에 사용할 수 없습니다.

{% hint style="info" %}
코드 에이전트에 대해 설정한 새 Broker 클라이언트는 동일한 Snyk 조직 및 동일한 SCM에 대한 Snyk 오픈 소스 및 Snyk IaC용 Broker 배포에도 서비스를 제공할 수 있습니다. [Snyk 컨테이너](../../snyk-broker-container-registry-agent/)의 경우 추가 Broker 클라이언트를 설정해야 합니다.
{% endhint %}

**실행 중인 Broker 클라이언트가 있는지 확인하려면**, 머신에서 실행 중인 모든 컨테이너의 목록을 제공하는 Docker 프로세스 상태 명령을 사용하세요.

{% hint style="info" %}
실행 중인 Broker 클라이언트가 있는 경우, 이 명령은 실행 중인 Broker 클라이언트를 제거하는 데 필요한 세부 정보도 제공합니다. 실행 중인 Broker 클라이언트를 발견한 경우 코드 에이전트와 동일한 Snyk 조직 및 동일한 SCM에 대해 구성된 경우에만 제거하면 됩니다.
{% endhint %}

다음을 실행합니다:

```
docker ps
```

실행 중인 Broker 클라이언트가 있는 경우 출력은 다음과 비슷합니다:

```
CONTAINER ID   IMAGE                    COMMAND                  CREATED        STATUS        PORTS                    NAMES
6eab097879cc   snyk/broker:github-com   "broker --verbose"       18 hours ago   Up 18 hours   0.0.0.0:8001->8000/tcp   suspicious_banzai
```

**Broker 클라이언트 컨테이너를 제거하려면** 다음을 실행합니다:

```
docker rm -f <Broker_Client_container_ID_or_name)
```

여기서`container_ID_or_name` 은 실행 중인 Broker 클라이언트의 컨테이너 ID 또는 이름입니다. 이러한 세부 정보는 예를 들어 `docker ps` 명령을 사용하여 얻을 수 있습니다:

<figure><img src="../../../../.gitbook/assets/Broker Client - removing.png" alt="Example of docker ps command"><figcaption><p>도커 ps 명령의 예</p></figcaption></figure>
