# Helm 차트 설치를 위한 multi-tenant 설정

## Broker multi-tenant 설정

다른 멀티테넌트 환경에서 Helm 차트를 사용하려면 사용 중인 환경에 따라 `brokerServerUrl` 을 다음 URL 중 하나로 설정한다:

유럽: `https://broker.eu.snyk.io`\
오스트레일리아: `https://broker.au.snyk.io`

```
--set brokerServerUrl=<BROKER_SERVER_URL>
```

## **Code Agent multi-tenant** 설정

Code Agent를 사용하는 경우, 사용 중인 환경에 따라 `upstreamUrlCodeAgent` 값은 다음 URL 중 하나여야 합니다:

유럽: `https://deeproxy.eu.snyk.io`\
오스트레일리아: `https://deeproxy.au.snyk.io`

```
--set upstreamUrlCodeAgent=<UPSTREAM_URL>
```
