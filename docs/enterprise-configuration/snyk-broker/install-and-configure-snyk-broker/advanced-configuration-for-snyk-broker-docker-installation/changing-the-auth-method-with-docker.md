# Docker로 인증 방법 변경하기

각 연동 서비스에는 기본적으로 설정된 인증 방법이 있으며, 정확한 방법은 서비스마다 다릅니다.

예를 들어 BitBucket Server 및 Data Center는 `accept.json`파일에 사용자 이름과 비밀번호가 포함된 기본 인증을 사용합니다:

```json
{
  "private": [
    {
      ...,
      "auth": {
         "scheme": "basic",
         "username": "${BITBUCKET_USERNAME}",
         "password": "${BITBUCKET_PASSWORD}"
      }
    },
    ...
  ]
}
```

아티팩토리의 경우 인증 메서드는 기본적으로 `.env` 파일에 구성됩니다:

```shell
# The URL to your artifactory
# If not using basic auth this will only be "<yourdomain.artifactory.com>/artifactory"
ARTIFACTORY_URL=<username>:<password>@<yourdomain.artifactory.com>/artifactory
```

GitHub의 경우 인증 메트릭은`accept.json`파일의 `origin` 필드에 있습니다:

```json
{
  "private": [
    {
      ...,
      "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}"
    },
    ...
  ]
}
```

0

```json
{
  "private": [
    {
      ...,
      "auth": {
        "scheme": "bearer",
        "token": "${BEARER_TOKEN}"
      }
    },
    ...
  ]
}
```

`private` 배열의 모든 개별 개체에 대해 설정해야 한다는 점에 유의하세요.

`scheme`가 `bearer` 또는 `token`인 경우, `token`을 제공해야 하며, `scheme` 가 `basic`인 경우, `username` 과`password`를 제공해야 합니다.

이렇게 하면 `origin` 필드 또는`.env` 파일에 토큰을 설정하는 등 구성된 다른 모든 인증 방법이 재정의됩니다.

{% hint style="info" %}
Snyk Broker는 mTLS 방식의 인증을 지원하지 않습니다.
{% endhint %}
