# Broker Helm 차트 설치를 위한 사용자 지정 추가 옵션

환경 변수를 사용하여 추가 옵션을 삽입해야 하는 경우 `override.yaml` 값 파일을 사용하여 필요한 추가 환경 변수를 추가하세요.

`override.yaml`에 `--values`를 추가하면 해당 값이 배포에 로드됩니다. 예를 들어:

```
helm install snyk-broker-chart . \
             --set scmType=github-com \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set scmToken=<ENTER_REPO_TOKEN> \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             --values override.yaml \
             -n snyk-broker --create-namespace
```

더 편리하다면 override.yaml 파일 없이 인라인으로 동일한 작업을 수행할 수 있습니다.

```
helm install snyk-broker-chart . \
             --set scmType=github-com \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set scmToken=<ENTER_REPO_TOKEN> \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             --set env[0].name=myEnvVarName \
             --set env[0].value=myEnvVarValue \
             --set env[1].name=myOtherEnvVarName \
             --set env[1].value=myOtherEnvVarValue \
             -n snyk-broker --create-namespace
```

값 파일에 추가하여 사용자 정의 Kubernetes 리소스 및 오브젝트를 차트에 추가할 수 있습니다.

다양한 수준의 사양 계층, 배포, 컨테이너 및 파드별로 다양한 조합의 Kubernetes 옵션과 오브젝트를 사용할 수 있습니다. 이러한 옵션은 기본 [default `values.yaml` ](https://github.com/snyk/snyk-broker-helm/blob/a805f97235ba6b004df7a38c93ee94e399b699b7/charts/snyk-broker/values.yaml#L403)파일에 `extraObjects`, `extraVolumes`, `extraVolumeMounts` 및`extraPodSpecs`로 나열되어 있다.

올바른 구문을 사용하고 `helm template`명령을 사용하여 렌더링된 `yaml`의 유효성을 검사하도록 주의하세요.
