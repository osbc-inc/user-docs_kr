# Snyk Broker 클라이언트 업그레이드

Snyk는 새로운 기능, 버그 수정 등을 제공하기 위해 브로커 클라이언트를 정기적으로 업데이트합니다. 릴리스 노트가 포함된 전체 버전 목록은 [Snyk Broker GitHub](https://github.com/snyk/broker/releases). 에서 확인할 수 있습니다. Snyk는 해당 페이지의[RSS 피드를 구독하여](https://github.com/snyk/broker/releases.atom) 버전이 릴리스될 때마다 정보를 받아볼 것을 권장합니다.

Broker를 업그레이드하면 Snyk가 올바르게 작동하는 데 필요한 몇 가지 새로운 규칙이 추가될 수 있습니다. 따라서 API 허용 목록을 다시 초기화해야 합니다. 예를 들어 1Mb보다 큰 파일을 지원하기 위해 [허용 목록을 사용자 정의하기 위해](https://docs.snyk.io/snyk-admin/snyk-broker/how-to-install-and-configure-your-snyk-broker-client/advanced-configuration-for-snyk-broker-docker-installation#custom-approved-listing-filter) 규칙을 추가하거나 제거한 경우, 이러한 변경 사항을 새 허용 목록에 다시 적용해야 한다. 이는 Helm으로 설치하든 도커로 설치하든 관계없이 적용된다.
