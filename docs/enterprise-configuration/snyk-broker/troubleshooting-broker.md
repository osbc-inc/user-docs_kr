# 문제 해결(Troubleshooting) Broker

{% hint style="info" %}
**멀티테넌트 설정 (Multi-tenant settings)**\
멀티테넌트 환경에서 사용하기 위해 브로커 및/또는 코드 에이전트를 설정하는 경우 추가 변수가 필요합니다. 자세한 내용은 [지역 hosting 및 데이터 레지던시](../../working-with-snyk/regional-hosting-and-data-residency.md)를 참조하세요.
{% endhint %}

이 페이지에는 다음에 대한 정보와 지침이 있습니다:

* [Broker 클라이언트로 로깅](troubleshooting-broker.md#logging-with-the-broker-client)
* 모니터링 기능인 [상태 확인(Healthcheck) ](troubleshooting-broker.md#monitoring-healthcheck) [시스템 확인(Systemcheck)](troubleshooting-broker.md#monitoring-systemcheck)을 통한 기본 문제 해결
* [독립 실행형 Broker 문제 해결](troubleshooting-broker.md#troubleshooting-standalone-broker)
* [GitHub 및 GitHub Enterprise용 대용량 매니페스트 파일(> 1Mb) 지원](troubleshooting-broker.md#support-of-big-manifest-files-greater-than-1mb-for-github-and-github-enterprise)
* [코드 에이전트를 사용한 Broker 문제 해결](troubleshooting-broker.md#troubleshooting-broker-with-code-agent)
* [host에서 로그아웃할 때, 컨테이너가 온라인 상태를 유지하도록 하기](troubleshooting-broker.md#containers-go-down-when-you-log-out-of-the-host)

보다 자세한 문제 해결 정보는 [Broker 문제해결 FAQs](https://support.snyk.io/hc/en-us/articles/4404288846353-Broker-Troubleshooting)를 참조하세요.

## Broker Client로 로깅

기본적으로 Broker의 로그 수준은 INFO로 설정되어 있습니다. HTTP 상태 코드에 관계없이 모든 SCM 응답은 Broker 클라이언트에 의해 기록됩니다. 로깅 동작을 변경하려면 다음 환경 변수를 설정하세요:

| Key               | Default | 참고                                    |
| ----------------- | ------- | ------------------------------------- |
| LOG\_LEVEL        | info    | 모든 로그에 대해 “debug”로 설정합니다.             |
| LOG\_ENABLE\_BODY | false   | 클라이언트 로그에 응답 본문을 포함하려면 “true”로 설정합니다. |

정상 작동 시 로그를 간결하게 유지하기 위해 Snyk는 INFO 수준에서 최소한의 정보를 생성하며, Snyk에서 클라이언트로 들어오는 요청과 대상 시스템, Github, Gitlab, JIRA 등으로 이루어진 다운스트림 요청을 추적하고 조회된 URL과 수신된 응답 코드를 기록합니다.

`LOG_INFO_VERBOSE="true"`로 설정하면 디버그를 사용하지 않아도 환경 변수가 이러한 로그 줄에 헤더를 추가합니다.

## 모니터링: 건강 상태(Healthcheck) 확인

Broker는 실행 중인 애플리케이션의 상태를 모니터링하는 데 사용할 수 있는`/healthcheck`엔드포인트를 노출합니다. 이 엔드포인트는 내부 요청이 성공하면 상태 코드 `200 OK` 로 응답하고 응답 본문에서 `{ ok: true }` 를 반환합니다.

Broker 클라이언트의 경우, 이 엔드포인트는 Broker 웹소켓 연결 상태도 보고합니다. 웹소켓 연결이 열려 있지 않으면 이 엔드포인트는 상태 코드`500 Internal Server Error`와 응답 본문에`{ ok: false }` 로 응답합니다.

이 상태는 Broker에 연결하고 기본 설정으로[http://localhost:8000/healthcheck](http://localhost:8000/healthcheck)을 실행하여 테스트할 수 있습니다.

상태 확인 엔드포인트의 위치를 변경하려면 환경 변수에 대체 경로를 지정하면 됩니다:

```dockerfile
ENV BROKER_HEALTHCHECK_PATH /path/to/healthcheck
```

## 모니터링: 시스템 점검

Broker 클라이언트는 `/systemcheck`에 엔드포인트를 노출하여 Broker 서비스, Git 또는 다른 SCM 또는 Broker 컨테이너 레지스트리의 연결 및 자격 증명을 검증하는 데 사용할 수 있습니다. 이 엔드포인트는 Broker 클라이언트가 미리 구성된 URL에 요청을 하고 요청 성공 여부를 보고하도록 합니다. 지원되는 구성은 다음과 같습니다:

* `BROKER_CLIENT_VALIDATION_URL` -  요청이 이루어질 URL입니다.
* `BROKER_CLIENT_VALIDATION_AUTHORIZATION_HEADER` - \[선택 사항] 요청의 `Authorization` 헤더 값입니다.`BROKER_CLIENT_VALIDATION_BASIC_AUTH`와 상호 배타적입니다.
* `BROKER_CLIENT_VALIDATION_BASIC_AUTH` - \[선택 사항] 기본 인증 자격 증명 (`username:password`)을 base64로 인코딩하여 요청의 `Authorization` 헤더 값에 넣을 값입니다. `BROKER_CLIENT_VALIDATION_AUTHORIZATION_HEADER`와 상호 배타적입니다.
* `BROKER_CLIENT_VALIDATION_METHOD` \[선택 사항] 요청의 HTTP 메소드(기본값은 `GET`).
* `BROKER_CLIENT_VALIDATION_TIMEOUT_MS` - \[선택 사항] 요청 시간 제한(밀리초 단위)(기본값은 5000ms).

이 엔드포인트는 내부 요청이 성공하면 상태 코드 `200 OK` 으로 응답하고 응답 본문에 자격증명당 배열의 객체 하나씩`{ ok: true }`를 반환합니다([Credential pooling](install-and-configure-snyk-broker/advanced-configuration-for-snyk-broker-docker-installation/credential-pooling-with-docker-and-helm.md) 참조). 내부 요청이 실패하면 이 엔드포인트는 상태 코드 `500 Internal Server Error` 와 응답 본문에 `{ ok: false }` 로 응답합니다.

이 상태는 Broker에 연결하고 기본 설정으로[http://localhost:8000/systemcheck](http://localhost:8000/systemcheck)을 실행하여 테스트할 수 있습니다.

broker와 넥서스 간의 연결을 확인하기 위해 `/systemcheck` 기능을 활성화하는 예제입니다:\
`-e BROKER_CLIENT_VALIDATION_URL=https://[username:password]@acme.com/service/rest/v1/status[/check] /`\
`snyk/broker:nexus`

시스템체크 엔드포인트의 위치를 변경하려면 환경 변수에 대체 경로를 지정하면 됩니다:

```dockerfile
ENV BROKER_SYSTEMCHECK_PATH /path/to/systemcheck
```

{% hint style="info" %}
Snyk Broker는 mTLS 방식의 인증을 지원하지 않습니다.
{% endhint %}

## 독립 실행형 Broker 문제 해결

Broker를 실행한 후에도 온프레미스 Git에 연결할 때 오류가 계속 발생하면 다음 문제 해결 단계를 따르세요.

1. Broker 컨테이너에 관련 로그가 있는지 확인합니다. 이를 위해 온프레미스 Git에 연결을 시도합니다. 통합 탭으로 이동하여 가져오기를 시도합니다. 그러면 Broker 로그에 로그가 생성됩니다.
2. 컨테이너의 로그를 검토합니다. Docker에서`docker logs <container id>`를 실행하여 이 작업을 수행할 수 있습니다.
3. 로그를 검토하여 문제가 발생한 위치를 확인합니다.

### 독립형 Broker의 일반적인 문제

* 이전 단계를 수행한 후 로그가 없는 경우 고객에게 올바른 Broker 토큰이 있는지 확인하세요. 그렇다면 웹소켓이 설정되었는지 확인하세요. 일부 방화벽은 이를 차단합니다.
* 온프레미스 Git에 대한 요청의 HTTP 코드를 검토합니다.
  * **404 - Not found** - 도커 실행 명령에 올바른 정보가 있는지 확인합니다.
  * **401/403** - 자격 증명을 확인합니다.
  * SSL에 대한 참조가 있는 경우 자체 서명된 인증서로 인해 발생할 수 있습니다. 올바른 인증서를 마운트했는지 확인하거나 플래그 `-e NODE_TLS_REJECT_UNAUTHORIZED=0`을 사용하세요.

### 독립형 Broker 연결 테스트

Broker와 에이전트의 이미지에 `curl` 이 없습니다. 에이전트나 컨테이너 레지스트리 또는 SCM과 같은 엔드포인트에 대한 연결을 테스트하려면 다음 명령을 사용할 수 있습니다:

```
#start node
node

#test a url with http
http = require("http")
http.get("<URL_HERE>", res => {console.log(`statusCode: ${res.statusCode}`)})

#test a url with https
https = require("https")
https.get('<URL_HERE>', res => {console.log(`statusCode: ${res.statusCode}`)})
```

## GitHub 및 GitHub Enterprise용 대용량 매니페스트 파일(> 1Mb) 지원

대용량 매니페스트 파일(> 1Mb) 가져오기 실패로 인해 오픈 수정/업그레이드 PR 또는 PR/반복 테스트가 실패할 수 있습니다. 이 문제를 해결하려면 [Docker](https://docs.snyk.io/enterprise-setup/snyk-broker/install-and-configure-snyk-broker/advanced-configuration-for-snyk-broker-docker-installation/snyk-open-source-scans-sca-of-large-manifest-files-docker-setup) 또는 [Helm](https://docs.snyk.io/enterprise-setup/snyk-broker/install-and-configure-snyk-broker/advanced-configuration-for-helm-chart-installation/snyk-open-source-scans-sca-of-large-manifest-files-helm-setup) 지침에 따라 대용량 매니페스트 파일을 허용하세요.

## 코드 에이전트를 사용한 Broker 문제 해결

<figure><img src="https://lh3.googleusercontent.com/r_qtONpOOEW35gdyoBcWDAiC6j04M76q8mh922SHor4bdNZdt83sj2kP7d5hbzYcWVXp4Q2hZEiCeAVOmcj4Bu1yFPdnyp3rK7kKeBK8DZEd9S133Xn3YdjddclVf5maEbP23Jor" alt="Snyk Code Analysis workflow with Broker"><figcaption><p>Broker를 사용한 Snyk 코드 분석 워크플로</p></figcaption></figure>

코드 에이전트로 Broker의 문제를 해결하는 가장 좋은 방법은 통신 흐름을 이해하는 것입니다. 트래픽은 Snyk > Broker Client > Code Agent > On-premise Git > Code Agent > Snyk 순으로 이동합니다.

코드 에이전트에서 발생하는 대부분의 문제는 이러한 지점 중 한 곳에서 트래픽이 중단되어 발생합니다.

### 코드 에이전트 문제 해결

독립형 Broker의 경우 코드 에이전트 문제를 해결하려면 로그를 생성해야 합니다. 리포지토리 가져오기를 시도하여 로그를 생성합니다.

1. Broker가 올바르게 작동하고 리포지토리를 나열할 수 있는지 확인합니다. 그래도 문제가 해결되지 않으면 독립형 Broker 문제 해결 단계를 검토하세요.
2. 리포지토리를 가져오려고 시도한 후 `Bundle Creation Failed`라는 오류 메시지가 표시되면 컨테이너의 로그를 검토합니다.
3. Broker 컨테이너부터 시작합니다. `docker logs <container id>`실행
4. Look for the string `snykgit`을 찾습니다. 이것은 Broker 컨테이너에서 코드 에이전트 컨테이너로의 API 호출입니다. 200 코드가 아닌 다른 코드가 반환되면 브로커와 코드 에이전트 간의 통신에 문제가 있는 것입니다. 도커 실행 명령에 적절한 플래그가 설정되어 있는지 확인하세요. 또한 도커 네트워크를 설정했는지 확인하세요.
5. `docker logs <container id>`를 실행하여 코드 에이전트의 로그를 검토합니다.

### 코드 에이전트의 일반적인 문제

* 온프레미스 Git과의 통신이 작동하지 않습니다. 코드 복제를 시도할 때 404 오류가 발생합니다. SSL에 대한 참조가 있는 경우 자체 서명된 인증서로 인해 발생할 수 있습니다. 올바른 인증서를 마운트했는지 확인하거나 플래그 `-e NODE_TLS_REJECT_UNAUTHORIZED=0`을 사용하세요.
* 메시지가 표시되면 `“Uploaded Repo”`라는 메시지가 표시되면 코드 에이전트 및 브로커가 올바르게 구성된 것입니다. 가져오기 로그에 여전히 오류가 있는 경우,  [Snyk Support](https://support.snyk.io/hc/en-us) 문의하세요.

## 호스트에서 로그아웃하면 컨테이너가 다운됩니다.

호스트에서 분리할 때 컨테이너와 함께 Broker 에코시스템이 다운되는 경우, 로그아웃할 때 컨테이너가 온라인 상태를 유지하도록 다음을 실행하세요:

`loginctl enable-linger $(whoami)`
