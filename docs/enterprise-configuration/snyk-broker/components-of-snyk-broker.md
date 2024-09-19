# Snyk Broker의 구성 요소

Broker 클라이언트와 서버는 코드에 대한 터널 역할을 함께 수행하여 [snyk.io](http://snyk.io/) 에서 Git 리포지토리로 프록시로 요청을 보내고, 모니터링되는 리포지토리에서 매니페스트 파일을 가져오고, Git 서비스에서 게시한 webhooks을 사용하여 결과를 가져옵니다. Broker 클라이언트는 내부 네트워크 내에서 실행되어 Git 토큰과 같은 민감한 데이터를 네트워크 경계 내에 보관합니다. 터널을 사용하면 승인된 데이터 목록의 요청만 사용하여 스캔할 수 있습니다. 이렇게 하면 Snyk가 리포지토리를 모니터링하는 데 필요한 최소한의 권한으로 액세스 권한이 좁혀집니다. 자세한 내용은 [Snyk Broker의 승인된 데이터 목록](https://docs.snyk.io/snyk-admin/snyk-broker/connections-with-snyk-broker#approved-data-list-for-snyk-broker)을 참조하세요.

Snyk 코드 에이전트, Snyk 컨테이너 레지스트리 에이전트 및 코드형 인프라를 위한 Snyk 브로커를 사용하는 데 필요한 구성 요소에 대한 자세한 내용은 [Broker 배포 구성 요소 정의하기](https://docs.snyk.io/snyk-admin/snyk-broker/prepare-snyk-broker-for-deployment#define-your-broker-deployment-components)를 참조하세요.

다음 다이어그램은 기본 구성 요소의 작동 방식을 보여줍니다.

* 전송 중이거나 미사용 중인 모든 데이터는 암호화됩니다.
* 클라이언트와 서버 간의 통신은 보안 웹소켓 연결을 통해 이루어집니다.
* 통신이 아웃바운드에서 시작되므로 들어오는 포트를 열 필요가 없습니다.
* 연결이 시작되면 WebSocket 연결은 양방향으로 이루어집니다.

<figure><img src="../../.gitbook/assets/Snyk Broker diagram.png" alt="Snyk Broker WebSocket initiated by Client over HTTPS"><figcaption><p>HTTPS를 통해 클라이언트에 의해 시작된 Snyk Broker 웹소켓</p></figcaption></figure>

Snyk과 Broker 클라이언트 간의 연결 및 허용된 요청에 대한 자세한 내용은 [Snyk Broker와의 연결](connections-with-snyk-broker.md)을 참조하세요.&#x20;
