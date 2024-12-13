# 고가용성 모드 (High availability mode)

Snyk Broker는 서버와 클라이언트 모두에 고가용성 기능을 제공하여 현재 Broker는의 확장성을 높일 수 있으며, 처음에는 Snyk 코드에 대한 “git-clone-through-broker” 플로우 추가를 지원할 예정입니다.

고가용성 모드를 사용하면 여러 Broker 클라이언트가 서로 독립적으로 별도의 연결을 가질 수 있습니다. Snyk 플랫폼은 요청을 연결 전체에 고르게 분산하여 각 클라이언트의 부하를 완화하고 한 클라이언트가 오프라인인 경우 진정한 중복성을 제공합니다. 또한 고가용성 모드는 매우 드물게 발생하는 Broker 서버 구성 요소 업그레이드 시 다운타임을 방지합니다.

<figure><img src="../../.gitbook/assets/snyk-broker-ha-mode.png" alt="Operation of multiple Broker clients in high availability"><figcaption><p>고가용성에서 여러 Broker 클라이언트 운영</p></figcaption></figure>

고가용성 모드를 사용하려면, 둘 이상의 컨테이너를 실행하거나 쿠버네티스 배포에서 replica 수를 늘려서 둘 이상의 **replica**를 배포하세요. 각 컨테이너에는 **정확히 동일한 파라미터**가 있어야 합니다.

고가용성 모드에서 동시에 실행되는 Broker 클라이언트는 최대 4개까지 허용됩니다. 다섯 번째 터널은 무기한 연결을 시도합니다.

## 고가용성(HA) 모드를 사용하도록 설정하기

고가용성 모드는 기본적으로 비활성화되어 있습니다. 활성화하려면 컨테이너 또는 배포에 표시된 대로 다음 환경 변수를 설정하세요:

```
BROKER_HA_MODE_ENABLED=true
```

**Helm 차트 배포**는 설정 인수를 사용하여 모드를 활성화하여 이러한 값을 설정할 수 있다. Helm 차트 버전 1.7.0 이상이 필요하다.

```
--set highAvailabilityMode.enabled=true
```

차트 값 파일을 검토하여 복제본 수 증가, broker 디스패처 기본 URL 업데이트 등과 같은 추가 구성을 조정하세요.

## 설정 관련 중요 참고 사항

지역 Snyk 플랫폼을 사용하는 경우 디스패처 기본 URL은 해당 지역에 고유해야 합니다(예: api.eu.snyk.io). 자세한 내용은 [지역 hosting 및 데이터 레지던시](../../working-with-snyk/regional-hosting-and-data-residency.md)를 참조하세요.

app.snyk.io를 사용하는 경우 다음 항목은 필요하지 않습니다. 이는 지역 Snyk 플랫폼에만 적용됩니다.

```
BROKER_DISPATCHER_BASE_URL=https://api.snyk.io
```

api.snyk.io 또는 해당 API 호스트 이름에 대한 아웃바운드 연결이 허용되어야 합니다. 그렇지 않으면 Broker 클라이언트가 시작될 때 비행 전 검사에서 실패로 표시됩니다.

**고가용성 세트의 모든 Broker 클라이언트에서 `BROKER_CLIENT_URL` 값이 동일하게 유지되어야 합니다. 또한 동일한 BROKER\_TOKEN을 사용해야 합니다.**\
이 URL이 특정 클라이언트로 확인되는 것은 허용됩니다.

여러 터널은 주로 Snyk=>You 흐름을 지원합니다. You=>Snyk로 가는 웹훅은 어떤 터널도 사용할 수 있습니다.

가급적이면 로드 밸런서를 도입할 수도 있습니다. 각 브로커 클라이언트 앞에 서비스를 배치하는 쿠버네티스 배포는 이를 자동으로 배포합니다.

다음 클라이언트 로그 행은 고가용성 모드가 활성화되어 있음을 보여줍니다.

> ```shell
> ...
> checking for HA mode (enabled=true)
> received server id (serverId=0)
> broker client is connecting to broker server (url=https://broker.snyk.io, serverId=0)
> ...
> ```

고가용성 모드를 사용하면 각 클라이언트에 할당된 터널 개념을 도입하여 예측 가능한 Broker 서버 집합에서 터널을 예약하여 고유한 클라이언트가 올바른 포드에 연결될 수 있도록 합니다.
