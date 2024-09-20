# Helm을 사용한 설치 및 구성 - GitHub Enterprise

Snyk Broker Helm 차트 사용에 대한 지침은 [Helm을 사용하여  Broker 설치 및 구성하기](../install-and-configure-broker-using-helm.md)를 참조하세요. 사용할 명령어는 다음과 같습니다. 환경 변수에 대한 정의는 [GitHub Enterprise - Snyk Broker의 환경 변수](github-enterprise-environment-variables-for-snyk-broker.md)를 참조하세요.

참고: `github`의 경우, `githubApi` 및`githubGraphQl` 값에는 https://이 포함되지 않습니다.

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=github-enterprise \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set scmToken=<ENTER_REPO_TOKEN> \
             --set github=<ENTER_GHE_ADDRESS> \
             --set githubApi=<ENTER_GHE_API_ADDRESS> \
             --set githubGraphQl=<ENTER_GRAPHQL_ADDRESS> \
             --set enabledAppRisk=true \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             -n snyk-broker --create-namespace
```
