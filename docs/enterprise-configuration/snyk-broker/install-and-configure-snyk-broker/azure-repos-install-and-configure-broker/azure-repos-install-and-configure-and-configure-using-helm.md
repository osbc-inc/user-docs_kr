# Azure Repos - Helm을 사용한 설치 및 구성 및 구성

Snyk Broker Helm 차트 사용에 대한 지침은 [Helm을 사용하여 Broker 설치 및 구성하기](../install-and-configure-broker-using-helm.md)를 참조하세요. 사용할 명령은 다음과 같습니다. 환경 변수에 대한 정의는 [Azure Repos - Snyk Broker의 환경 변수](azure-repos-environment-variables-for-snyk-broker.md)를 참조하세요.

참고: `azureReposHost` 값에 `https://`포함하지 않기

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=azure-repos \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set azureReposToken=<ENTER_REPO_TOKEN> \
             --set azureReposOrg=<ENTER_REPO_ORG> \
             --set azureReposHost=<ENTER_REPO_HOST> \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             --set enabledAppRisk=true \
             -n snyk-broker --create-namespace
```

{% hint style="info" %}
Snyk AppRisk는 기본적으로**`false`**로 설정되어 있습니다. 플래그를 **`true`**로 설정하여 사용하도록 설정합니다.
{% endhint %}
