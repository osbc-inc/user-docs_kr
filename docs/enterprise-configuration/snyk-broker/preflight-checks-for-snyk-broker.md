# Snyk Broker 비행 전 점검(Preflight checks)

비행 전 점검의 주요 목적은 사용 중이 아닌 Broker 클라이언트 시작 시 오류와 잘못된 구성을 조기에 발견하는 것입니다. 검사 성공 여부에 관계없이 Broker 클라이언트가 시작됩니다. 다음과 같은 점검을 사용할 수 있습니다.

## `broker-server-status`

Broker 서버 상태 확인은 브로커 서버에 대한 연결의 유효성을 검사합니다. Broker 서버 상태 확인은`{BROKER_SERVER_URL}/healthcheck`에 GET 요청을 수행합니다.

지정하지 않으면, BROKER\_SERVER\_URL은 [https://broker.snyk.io](https://broker.snyk.io/) 입니다.

## `rest-api-status`

REST API 상태 확인은  [Snyk REST API](https://apidocs.snyk.io/)에 대한 연결의 유효성을 검사합니다. `{API_BASE_URL}/rest/openapi`. 에 대한 GET 요청을 수행합니다. 이 검사는 조건부 검사이며 고가용성 모드가 활성화된 경우에만 실행됩니다.

지정하지 않으면, the `API_BASE_URL` 은 [https://api.snyk.io](https://api.snyk.io/)입니다.

## `broker-client-url-validation`

Broker 클라이언트 구성 검사는`BROKER_CLIENT_URL`값의 유효성을 최대한 검증합니다. 이 값에 스키마 (`http or https`) 가 포함되어 있는지, https인 경우 SSL 인증서+키가 로드되었거나 업스트림에서 TLS가 종료되었는지 확인합니다.

TLS 종료를 사용하고 Broker 클라이언트에서 인증서+키가 필요하지 않은 경우, 환경 변수 `BROKER_CLIENT_URL_TLS_TERMINATED`를 추가하여 비행 전 검사에서 TLS 종료를 알립니다.

기본값은 없습니다.

{% hint style="info" %}
You can use the environment variable 환경 변수 PREFLIGHT\_CHECKS\_ENABLED=false를 사용하여 비행 전 검사 기능을 비활성화하면 Broker 클라이언트가 시작될 때 검사를 실행하지 않을 수 있습니다.
{% endhint %}
