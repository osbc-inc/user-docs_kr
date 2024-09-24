# Helm 설치를 위한 사용자 정의 accept.json 추가하기

사용자 정의 `accept.json` 파일을 추가하려면, `values.yaml`에 포함하세요.

[Snyk Broker Helm 리포지토리 클라이언트 템플릿](https://github.com/snyk/broker/tree/master/client-templates)에 있는 `accept.json` 파일 예시를 참조하세요.

`values.yaml` 파일을 다음과 같이 구조화하세요:

```
scmType: github-com
brokerToken: <ENTER_BROKER_TOKEN>
scmToken: <ENTER_REPO_TOKEN>
acceptJson: |-
  {
    "public": [
      {
        "//": "used for pushing up webhooks from github",
        "method": "POST",
        "path": "/webhook/github",
        "valid": [
          {
            "//": "accept all pull request state changes (these don't have files in them)",
            "path": "pull_request.state",
            "value": "open"
          },
          {
            "path": "commits.*.added.*",
            "value": "package.json"
          },
  ...
    ]
  }
```

그런 다음 설치할 수 있습니다:

```
helm install snyk-broker-gitub-com snyk-broker/snyk-broker -f values.yaml -n snyk-broker --create-namespace
```
