# 대용량 매니페스트 파일의 Snyk 오픈 소스 스캔(SCA), Docker 설정

대용량 매니페스트 파일이 Snyk에 의해 감지되면 다른 방법(다른 SCM 엔드포인트)을 사용하여 파일을 검색해야 하는 경우가 있습니다. 대체 방법에는 보다 허용적인 규칙이 필요하므로 기본적으로 비활성화되어 있습니다.

{% hint style="info" %}
이는 Github 및 Github Enterprise Broker 통합에만 적용됩니다.
{% endhint %}

이 규칙을 쉽게 추가하여 Broker 클라이언트가 다른 엔드포인트를 사용하여 더 큰 매니페스트 파일을 검색할 수 있도록 하려면 다음 환경 변수를 추가하세요:

```console
-e ACCEPT_LARGE_MANIFESTS=true
```

ACCEPT 환경 변수 대신 [사용자정의 accept.json](https://docs.snyk.io/enterprise-setup/snyk-broker/install-and-configure-snyk-broker/advanced-configuration-for-snyk-broker-docker-installation/custom-approved-listing-filter-with-docker)을 사용하는 경우, 비공개 섹션의 accept.json에 이 변수를 추가하세요.

```
{
    "//": "used to get given manifest file",
    "method": "GET",
    "path": "/repos/:owner/:repo/git/blobs/:sha",
    "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}"
}
```

{% hint style="info" %}
이 엔드포인트를 사용하면 경로에 허용된 특정 파일 이름이 포함되어 있지 않기 때문에 이론적으로 이 리포지토리에 있는 모든 파일에 액세스할 수 있으므로 최대한의 보안을 보장하기 위해 Snyk는 이 규칙을 기본적으로 활성화하지 않습니다
{% endhint %}
