# 동일한 네임스페이스에 여러 Broker 배포하기

## Helm 차트 버전 2.x.x

Helm 차트 버전 2.x.x는 릴리스 이름에 따라 모든 오브젝트 이름에 접미사를 자동으로 추가한다. 동일한 네임스페이스에 추가하려는 각 broker에 대해 다른 릴리스 이름을 사용하기만 하면 된다

{% hint style="info" %}
이전 버전과의 호환성을 위해 2.1.0에서는 값 파일에 --set disableSuffixes=true 또는 disableSuffixes=true를 추가하여 아래 나열된 1.x.x 동작으로 되돌리는 disableSuffixes 플래그가 도입되었습니다.
{% endhint %}

## Helm 차트 버전 1.x.x

기존 Broker와 동일한 네임스페이스에 추가 Broker를 배포하려면 다음 예제를 따르세요.

### 기존 서비스 계정으로 배포

```
helm install <ENTER_UNIQUE_CHART_NAME> snyk-broker/snyk-broker \
             --set scmType=github-com \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set scmToken=<ENTER_REPO_TOKEN> \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             --set serviceAccount.create=false \
             --set serviceAccount.name=<EXISTING_SERVICE_ACCOUNT> \
             -n <EXISTING_NAMESPACE>
```

### 새 서비스 계정으로 배포

```
helm install <ENTER_UNIQUE_CHART_NAME> snyk-broker/snyk-broker \
             --set scmType=github-com \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set scmToken=<ENTER_REPO_TOKEN> \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             --set serviceAccount.name=<NEW_SERVICE_ACCOUNT_TO_BE_CREATED> \
             -n <EXISTING_NAMESPACE>
```
