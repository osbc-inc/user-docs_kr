# Snyk Broker와의 연결

이 페이지의 정보는 Snyk과 Broker 클라이언트 간의 연결 및 허용된 요청에 대한 세부 정보를 제공합니다

## Snyk Broker로 인바운드 및 아웃바운드 연결 사용

Broker 클라이언트는 내부 네트워크 내에서 실행됩니다.

### Snyk에서 Broker 클라이언트로의 인바운드 연결

Snyk에서 Broker 클라이언트로 직접 인바운드 연결은 없습니다.

Broker 클라이언트는 [https://broker.snyk.io](https://broker.snyk.io)에 아웃바운드 연결을 설정합니다. 이렇게 하면 웹소켓 연결이 설정되어 Broker 서버와 통신할 수 있습니다.

따라서 Snyk IP 주소를 허용 목록에 추가할 필요가 없습니다. 대신 Broker 클라이언트 IP/포트를 허용할 수 있습니다.

### Broker 클라이언트에서 아웃바운드 연결

Broker 클라이언트는 아웃바운드 연결을 시작하여 웹소켓을 설정합니다.

Broker 클라이언트에 의해 시작된 웹소켓 연결이 설정된 후 Snyk은 웹소켓을 통해 Broker 클라이언트로 인바운드 요청을 보낼 수 있습니다.

따라서 Snyk 전용 IP 주소 또는 기타 외부 IP 주소에서 Broker 클라이언트로의 인바운드 연결을 허용할 필요가 없습니다.

## Snyk Broker에 대한 승인된 데이터 목록

Broker 클라이언트는 인바운드 및 아웃바운드 요청에 대해 승인된 데이터 목록을 유지합니다. 이 승인된 목록에 있는 데이터만 요청할 수 있습니다. 이렇게 하면 Snyk이 리포지토리를 모니터링하는 데 필요한 최소한의 권한으로 액세스 권한이 좁혀집니다.

### 인바운드 요청 허용

Snyk 오픈소스의 경우:

* Snyk.io는 종속성 매니페스트 파일과 `.snyk` 정책 파일만 가져오고 볼 수 있습니다.
* 다른 소스 코드는 조회, 추출 또는 수정할 수 없습니다.
* Snyk 패치 메커니즘을 지원하고 취약성 정책에 포함된 무시 지침을 확인하기 위해 추가`.snyk` 파일을 체크인할 수 있습니다.

Snyk Code 및 Snyk IaC는 전체 리포지토리에 액세스할 수 있어야 합니다.

자세한 내용은 [Snyk이 데이터를 처리하는 방법](../../working-with-snyk/how-snyk-handles-your-data.md)을 참조하세요 Snyk Container와 함께 Snyk Broker를 사용하는 방법 및 오픈 소스, 코드 분석 및 IaC에 대한 요구 사항에 대한 자세한 내용은 [Snyk Broker를 사용하여 코드 스캔하기](connections-with-snyk-broker.md#using-snyk-broker-to-scan-your-code)를 참조하세요.

### 아웃바운드 요청 허용

Broker 클라이언트 설정을 구성하면 개발자가 새 풀 리퀘스트를 제출하거나 이벤트를 병합할 때 트리거되는 자동 Snyk 스캔을 사용하도록 Git 리포지토리 Webhook이 설정됩니다.

Webhook 알림은 Broker 클라이언트를 통해 Snyk 작업과 관련된 이벤트(브랜치로 푸시 및 풀 리퀘스트 열기)에 대해서만, **그리고** 이벤트 데이터에 종속성 매니페스트 파일 또는 .`snyk`정책 파일도 포함된 **경우에만** Snyk에 전달됩니다.

### 기본 승인 데이터 목록 및 `accept.json` 파일

\
경우에 따라 Broker 배포에 [`accept.json`](snyk-broker-infrastructure-as-code-detection/)[ 파일을 추가하고 구성](snyk-broker-infrastructure-as-code-detection/)해야 할 수도 있습니다. 이렇게 하면 Broker를 시작할 때 ACCEPT 규칙을 적용하는 기능이 제거됩니다.

승인된 데이터 목록과 `accept.json` 파일에 대해 자세히 알아보려면, [사용자 지정 승인 목록 필터](https://docs.snyk.io/snyk-admin/snyk-broker/install-and-configure-broker-using-docker/advanced-configuration-for-snyk-broker-docker-installation#custom-approved-listing-filter)를 참조하세요.
