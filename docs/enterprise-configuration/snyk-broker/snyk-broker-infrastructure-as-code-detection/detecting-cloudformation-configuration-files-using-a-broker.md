# Snyk Broker(사용자 지정)를 사용하여 CloudFormation 구성 파일 감지하기

## Snyk Broker의 CloudFormation

기본적으로 IaC(코드형 인프라)에서 사용하는 일부 파일 유형은 사용하도록 설정되어 있지 않습니다. 브로커에 리포지토리의 IaC 파일(예: CloudFormation)에 대한 액세스 권한을 부여하려면 환경 변수`ACCEPT_IAC`를 `tf,yaml,yml,json,tpl`의 임의 조합으로 추가하면 됩니다.

예시:

```
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=secret-broker-token \
           -e GITHUB_TOKEN=secret-github-token \
           -e PORT=8000 \
           -e BROKER_CLIENT_URL=http://my.broker.client:8000 \
           -e ACCEPT_IAC=tf,yaml,yml,json,tpl
       snyk/broker:github-com
```

그렇지 않으면 `accept.json`을 편집하고 관련 IaC 특정 규칙을 추가한 다음 사용자 정의된 수락 파일을 컨테이너에 로드할 수 있습니다. 별도의 폴더에 있는 사용자 지정 허용 파일을 사용하는 경우(`ACCEPT`환경 변수를 사용하는 경우)`ACCEPT_IAC`메커니즘을 사용할 수 없습니다.

사용자 지정 허용 목록이 필요하고 Snyk가 스캔할 수 있는 파일에 CloudFormation 파일을 추가하려는 경우의 지침입니다.

## 구성 작성하기

CloudFormation 스캔 기능을 사용하려면 리포지토리에 있는 YAML 또는 JSON 파일에 액세스할 수 있어야 합니다. 이를 위해서는 특정 API 권한이 필요합니다. 이러한 API 권한은 소스 제어 시스템에 따라 약간씩 다릅니다.

1. 올바른 소스 제어 시스템에 적합한 accept.json 샘플 파일을 찾아 [Broker 리포지토리에서](https://github.com/snyk/broker/tree/master/client-templates)다운로드합니다.
2. `accept.json`파일의 이름을 바꾸고 JSON 파일의 **비공개(private)** 배열에 추가한 다음 다음 규칙을 SCM에 적절하게 추가합니다.
3. [Broker 구성](detecting-cloudformation-configuration-files-using-a-broker.md#configuring-broker)지침을 따릅니다.

### GitHub 및 GitHub Enterprise 규칙

```
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/repos/:name/:repo/contents/:path*/*.yaml",
  "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/repos/:name/:repo/contents/:path*%2F*.yaml",
  "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/repos/:name/:repo/contents/:path*/*.yml",
  "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/repos/:name/:repo/contents/:path*%2F*.yml",
  "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/repos/:name/:repo/contents/:path*/*.json",
  "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/repos/:name/:repo/contents/:path*%2F*.json",
  "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}"
},
```

### Bitbucket 규칙

```
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/projects/:project/repos/:repo/browse*/*.yaml",
  "origin": "https://${BITBUCKET_API}",
  "auth": {
    "scheme": "basic",
    "username": "${BITBUCKET_USERNAME}",
    "password": "${BITBUCKET_PASSWORD}"
  }
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/projects/:project/repos/:repo/browse*%2F*.yaml",
  "origin": "https://${BITBUCKET_API}",
  "auth": {
    "scheme": "basic",
    "username": "${BITBUCKET_USERNAME}",
    "password": "${BITBUCKET_PASSWORD}"
  }
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/projects/:project/repos/:repo/browse*/*.yml",
  "origin": "https://${BITBUCKET_API}",
  "auth": {
    "scheme": "basic",
    "username": "${BITBUCKET_USERNAME}",
    "password": "${BITBUCKET_PASSWORD}"
  }
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/projects/:project/repos/:repo/browse*%2F*.yml",
  "origin": "https://${BITBUCKET_API}",
  "auth": {
    "scheme": "basic",
    "username": "${BITBUCKET_USERNAME}",
    "password": "${BITBUCKET_PASSWORD}"
  }
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/projects/:project/repos/:repo/browse*/*.json",
  "origin": "https://${BITBUCKET_API}",
  "auth": {
    "scheme": "basic",
    "username": "${BITBUCKET_USERNAME}",
    "password": "${BITBUCKET_PASSWORD}"
  }
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/projects/:project/repos/:repo/browse*%2F*.json",
  "origin": "https://${BITBUCKET_API}",
  "auth": {
    "scheme": "basic",
    "username": "${BITBUCKET_USERNAME}",
    "password": "${BITBUCKET_PASSWORD}"
  }
},
```

### GitLab 규칙

```
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/api/v4/projects/:project/repository/files*/*.yaml",
  "origin": "https://${GITLAB}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/api/v4/projects/:project/repository/files*%2F*.yaml",
  "origin": "https://${GITLAB}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/api/v4/projects/:project/repository/files*/*.yml",
  "origin": "https://${GITLAB}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/api/v4/projects/:project/repository/files*%2F*.yml",
  "origin": "https://${GITLAB}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/api/v4/projects/:project/repository/files*/*.json",
  "origin": "https://${GITLAB}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/api/v4/projects/:project/repository/files*%2F*.json",
  "origin": "https://${GITLAB}"
},
```

## Broker 구성

Broker는 ACCEPT 환경 변수에 해당 규칙이 추가된 accept.json 파일의 경로를 가져옵니다. 다음은 해당 변수를 GitHub Broker에 전달하는 예제입니다.

```
docker run --restart=always \
  -p 8000:8000 \
  -e BROKER_TOKEN=secret-broker-token \
  -e GITHUB_TOKEN=secret-github-token \
  -e PORT=8000 \
  -e BROKER_CLIENT_URL=https://my.broker.client:8000 \
  -e ACCEPT=/private/accept.json
  -v /local/path/to/private:/private \
  snyk/broker:github-com
```

이렇게 하면 Snyk이 모든`.yaml`, `.yml`, 또는`.json`파일을 쿼리할 수 있습니다. 더 엄격하게 하려면 앞의 예제에서 특정 프로젝트나 파일 레이아웃에 대해 더 제한적으로 경로를 변경할 수 있습니다.
