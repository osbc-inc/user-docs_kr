# Snyk Code - Docker용 브로커를 통한 복제 기능

{% hint style="warning" %}
**릴리스 상태**

Git 복제 기능을 활성화하는 환경 변수는 [Closed Beta](../../../../getting-started/snyk-release-process.md) 버전입니다. 그러나 브로커를 통해 Snyk 코드 분석을 실행하는 데 선호되는 방법이며 충분히 사용할 수 있습니다.&#x20;

이 기능 사용에 관심이 있으시면 Snyk 계정 팀에 문의하세요.
{% endhint %}

브로커링된 Snyk 코드를 사용하면 Broker가 코드 파일을 수락할 수 있으며, Broker는 SCM 시스템과 Snyk 사이를 스캔합니다.

기본적으로 Snyk Code에 필요한 Git 클론 기능은 비활성화되어 있습니다.

## 구성 수락

리포지토리의 Git 복제를 수행할 수 있는 Broker 액세스 권한을 부여하려면 환경 변수를 추가하세요: `ACCEPT_CODE=true`

예시:

```
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=secret-broker-token \
           -e GITHUB_TOKEN=secret-github-token \
           -e PORT=8000 \
           -e BROKER_CLIENT_URL=http://my.broker.client:8000 \
           -e ACCEPT_CODE=true
       snyk/broker:github-com
```

이렇게 하면 Git 서버에 필요한 `accept`규칙이 추가됩니다.

이 작업이 완료되면 SCM 시스템에 대한 Broker 지침을 따를 수 있습니다. 자세한 내용은 [Snyk Broker 설치 및 구성하기](../)를 참조하세요.

## 사용자 지정 수락 구성

기본 규칙은 [Broker GitHub 리포지토리의 클라이언트 템플릿](https://github.com/snyk/broker/tree/master/client-templates)에 있습니다.

사용자 지정 `accept`규칙이 필요한 경우 사용자 지정`accept.json`을 제공할 수 있습니다.

예시:

```console
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=secret-broker-token \
           -e GITHUB_TOKEN=secret-github-token \
           -e PORT=8000 \
           -e BROKER_CLIENT_URL=http://my.broker.client:8000 \
           -e ACCEPT=/myFolder/accept.json
       snyk/broker:github-com
```

별도의 폴더에서 사용자 정의 `accept` 파일을 사용하는 경우,  `ACCEPT` 환경 변수를 사용하면 `ACCEPT_CODE` 또는`ACCEPT_IAC`와 같은 다른 `ACCEPT`메커니즘을 사용할 수 없습니다.

`accept.json`을 사용자 지정하려면 사용자 지정 `accept.json`에 다음 스니펫을 추가하세요.

```
{
    "//": "used to redirect requests to snyk git client",
    "method": "any",
    "path": "/snykgit/*",
    "origin": "${GIT_CLIENT_URL}"
}
```

이 스니펫은 모든 Git 통합에 유효합니다.
