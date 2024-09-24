# Docker를 사용한 사용자 지정 승인 목록 필터

기본 승인 목록 필터는 Snyk에서 지원하는 모든 리포지토리에서 작동하기 위한 최소한의 기능을 지원합니다. 승인 목록 필터를 사용자 지정하려면 `snyk-broker`r를 설치하고 `broker init [Git type]`을 실행하여 로컬에서 기본 필터를 만듭니다. 생성된`accept.json`이 선택한 Git 유형에 대한 기본 필터가 됩니다. 파일을 `./private/accept.json`과 같은 별도의 폴더에 저장하고, 폴더를 마운트하고 `ACCEPT` 환경 변수를 사용하여 Docker 컨테이너에 제공하세요:

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

**헤더를 기준으로 필터링하려면,** 다음 키와 값을 사용하여 유효성 검사 블록을 추가합니다:

| Key    | Value                                                              | Value Type     | Example                             |
| ------ | ------------------------------------------------------------------ | -------------- | ----------------------------------- |
| header | 필터링하려는 헤더의 이름입니다. 정의된 경우 명명된 헤더가 요청에 명시적으로 존재해야 하며, 그렇지 않으면 차단됩니다. | String         | `accept`                            |
| values | 헤더 값은 정의된 문자열 중 하나와 일치해야 합니다.                                      | Array\<String> | `["application/vnd.github.v4.sha"]` |

예시: \
GitHub 커밋 API에 대한 요청에 대해서만 SHA 미디어 유형 허용 헤더를 허용하려면 다음을 추가합니다:

```
{
    "method": "GET",
    "path": "/repos/:name/:repo/commits/:ref",
    "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}",
    "valid": [
        {
            "header": "accept",
            "values": ["application/vnd.github.v4.sha"]
        }
    ]
}
```
