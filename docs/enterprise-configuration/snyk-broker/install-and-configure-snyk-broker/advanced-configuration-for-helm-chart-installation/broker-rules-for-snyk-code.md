# Snyk 코드에 대한 Broker 규칙

Broker를 Snyk 코드와 함께 사용하려면 특정 Broker 규칙이 필요합니다.

Broker는 `ACCEPT_CODE=true` 환경 변수를 통해 이러한 규칙을 쉽게 삽입할 수 있다.

이 Helm 차트에서는 기본적으로 `ACCEPT_CODE=true` 로 설정되어 있으므로 Snyk 코드와 관련된 규칙에 대해 추가 조치가 필요하지 않습니다.
