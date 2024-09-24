# Jira - Helm을 사용하여 설치 및 구성하기

Snyk Broker Helm 차트 사용에 대한 지침은 [Helm을 사용하여 Broker 설치 및 구성하기](../install-and-configure-broker-using-helm.md)를 참조하세요.

## Jira 통합을 설치하는 명령

사용할 명령은 다음과 같습니다. 환경 변수에 대한 정의는 [Jira - Snyk Broker의 환경 변수](jira-environment-variables-for-snyk-broker.md)를 참조하세요.

참고: `jiraHostname`값에 `https://`포함하지 않기.

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=jira \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set jiraUsername=<ENTER_JIRA_USERNAME> \
             --set jiraPassword=<ENTER_JIRA_PASSWORD>  \
             --set jiraHostname=<ENTER_JIRA_HOSTNAME>  \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             -n snyk-broker --create-namespace
```

## SSO 지원 JIRA를 위한 Jira PAT 인증

SSO가 활성화된 경우, JIRA는 일반적으로 사용자 이름과 비밀번호 사용을 금지하고 개인용 액세스 토큰(PAT)을 사용하도록 요구합니다.

SSO를 사용하도록 설정한 경우 무기명 토큰과 함께 권한 부여 헤더를 대신 사용하는 특정 Jira 버전을 사용해야 합니다. 이 버전을 사용하려면 다음 구성을 제공하세요:

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=jira-bearer-auth \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set jiraPat=<ENTER_JIRA_PAT> \
             --set jiraHostname=<ENTER_JIRA_HOSTNAME>  \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             -n snyk-broker --create-namespace
```

{% hint style="info" %}
helm 차트 버전 2.2.0 이상을 사용해야 합니다.
{% endhint %}
