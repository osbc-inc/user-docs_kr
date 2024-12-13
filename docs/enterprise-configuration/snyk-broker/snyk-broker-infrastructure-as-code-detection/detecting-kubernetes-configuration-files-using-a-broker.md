# Snyk Broker (사용자 정의)를 사용하여 Kubernetes 구성 파일 감지하기

## Snyk Broker의 Kubernetes 구성 파일

기본적으로, 코드형 인프라(IaC)에서 사용하는 일부 파일 형식은 활성화되지 않는다. Broker에 리포지토리의 IaC 파일(예: Kubernetes 구성 파일)에 대한 액세스 권한을 부여하려면 환경 변수 `ACCEPT_IAC` 를 `tf,yaml,yml,json,tpl`의 임의 조합으로 추가하면 됩니다.

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

그렇지 않으면 `accept.json`, 을 편집하고 관련 IaC 특정 규칙을 추가한 다음 사용자 정의된 수락 파일을 컨테이너에 로드할 수 있습니다. 별도의 폴더에 있는 사용자 지정 허용 파일을 사용하는 경우( `ACCEPT` 환경 변수를 사용하는 경우) `ACCEPT_IAC` 메커니즘을 사용할 수 없다는 점에 유의하세요.

다음은 사용자 지정 허용 목록이 필요하고 Snyk이 검사할 수 있는 파일에 Kubernetes 구성 파일을 추가하려는 경우의 지침입니다.

## 구성 작성하기

Broker에게 리포지토리의 특정 파일에 대한 액세스 권한을 부여해야 합니다. 이를 위해서는 특정 API 권한이 필요합니다. 이러한 API 권한은 사용 중인 소스 제어 시스템에 따라 약간 다릅니다. 다음 구성은 파일 확장자 `.yaml`, `.yml`, 및`.json`. 에 대한 구성입니다. 이를 통해 Broker가 잠재적인 Kubernetes 및 CloudFormation 파일에 액세스할 수 있지만 필요에 따라 구성을 조정할 수 있습니다. 예를 들어, Terraform HCL 파일을 스캔하기 위해 `.tf` 파일에 대한 구성을 추가할 수 있습니다.

1. 소스 제어 시스템에 적합한 `accept.json` 샘플 파일을 찾아서 [Broker 리포지토리에서](https://github.com/snyk/broker/tree/master/client-templates) 다운로드합니다.
2. 파일 이름을 `accept.json` 으로 바꾸고 JSON 파일의 **비공개(private)** 배열에 다음 규칙을 SCM에 적절히 추가합니다.
3. [Broker 구성](detecting-kubernetes-configuration-files-using-a-broker.md#configuring-broker)지침을 따릅니다.

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
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/repos/:name/:repo/contents/:path*/*.tpl",
  "origin": "https://${GITHUB_TOKEN}@${GITHUB_API}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/repos/:name/:repo/contents/:path*%2F*.tpl",
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
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/projects/:project/repos/:repo/browse*/*.tpl",
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
  "path": "/projects/:project/repos/:repo/browse*%2F*.tpl",
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
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/api/v4/projects/:project/repository/files*/*.tpl",
  "origin": "https://${GITLAB}"
},
{
  "//": "used to determine Infrastructure as Code issues",
  "method": "GET",
  "path": "/api/v4/projects/:project/repository/files*%2F*.tpl",
  "origin": "https://${GITLAB}"
},
```

### Azure Repo 규칙

```
{
  "public": [
    {
      "//": "used for pushing up webhooks from Azure",
      "method": "POST",
      "path": "/webhook/azure-repos/:webhookId"
    }
  ],
  "private": [
    {
      "//": "get list of projects for given organization",
      "method": "GET",
      "path": "/_apis/projects",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "get specific repository for given organization",
      "method": "GET",
      "path": "/:owner/_apis/git/repositories/:repo",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "get list of repositories for given organization",
      "method": "GET",
      "path": "/:owner/_apis/git/repositories",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "get list of refs",
      "method": "GET",
      "path": "/:owner/_apis/git/repositories/:repo/refs",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "search through repositories of given organization",
      "method": "GET",
      "path": "_apis/git/repositories",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "create hook",
      "method": "POST",
      "path": "/_apis/hooks/subscriptions",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "delete hook",
      "method": "DELETE",
      "path": "/_apis/hooks/subscriptions/:subscriptionId",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "get file content. restrict by file types",
      "method": "GET",
      "path": "/:owner/_apis/git/repositories/:repo/items",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "valid": [
        {
          "queryParam": "path",
          "values": [
            "**/package.json",
            "**%2Fpackage.json",
            "**/yarn.lock",
            "**%2Fyarn.lock",
            "**/package-lock.json",
            "**%2Fpackage-lock.json",
            "**/Gemfile",
            "**%2FGemfile",
            "**/Gemfile.lock",
            "**%2FGemfile.lock",
            "**/pom.xml",
            "**%2Fpom.xml",
            "**/*req*.txt",
            "**%2F*req*.txt",
            "**/requirements/*.txt",
            "**%2Frequirements%2F*.txt",
            "**/build.gradle",
            "**%2Fbuild.gradle",
            "**/gradle.lockfile",
            "**%2Fgradle.lockfile",
            "**/build.sbt",
            "**%2Fbuild.sbt",
            "**/.snyk",
            "**%2F.snyk",
            "**/packages.config",
            "**%2Fpackages.config",
            "**/*.csproj",
            "**%2F*.csproj",
            "**/*.vbproj",
            "**%2F*.vbproj",
            "**/*.fsproj",
            "**%2F*.fsproj",
            "**/project.json",
            "**%2Fproject.json",
            "**/Gopkg.toml",
            "**%2FGopkg.toml",
            "**/Gopkg.lock",
            "**%2FGopkg.lock",
            "**/vendor.json",
            "**%2Fvendor.json",
            "**/composer.lock",
            "**%2Fcomposer.lock",
            "**/composer.json",
            "**%2Fcomposer.json",
            "**/project.assets.json",
            "**%2Fproject.assets.json",
            "**/Podfile",
            "**%2FPodfile",
            "**/Podfile.lock",
            "**%2FPodfile.lock",
            "**/go.mod",
            "**%2Fgo.mod",
            "**/go.sum",
            "**%2Fgo.sum",
            "**/Dockerfile",
            "**%2FDockerfile"
          ]
        },
        {
          "queryParam": "recursionLevel",
          "values": ["none"]
        },
        {
          "queryParam": "download",
          "values": ["true"]
        },
        {
          "queryParam": "includeContent",
          "values": ["true"]
        }
      ],
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "get list of files for given repository",
      "method": "GET",
      "path": "/:owner/_apis/git/repositories/:repo/items",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "valid": [
        {
          "queryParam": "recursionLevel",
          "values": ["full"]
        },
        {
          "queryParam": "download",
          "values": ["false"]
        },
        {
          "queryParam": "includeContent",
          "values": ["false"]
        }
      ],
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "get list of commits for given repository",
      "method": "GET",
      "path": "/:owner/_apis/git/repositories/:repo/commits",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "update status of given commit",
      "method": "POST",
      "path": "/:owner/_apis/git/repositories/:repo/commits/:commitId/statuses",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "update status of given pull request",
      "method": "POST",
      "path": "/:owner/_apis/git/repositories/:repo/pullRequests/:pullRef/statuses",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "find PR for given repository",
      "method": "GET",
      "path": "/:owner/_apis/git/repositories/:repo/pullrequests",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "create new PR in given repository",
      "method": "POST",
      "path": "/:owner/_apis/git/repositories/:repo/pullrequests",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "update existing PR in given repository",
      "method": "PATCH",
      "path": "/:owner/_apis/git/repositories/:repo/pullrequests/:pullRef",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "push new commit in given repository",
      "method": "POST",
      "path": "/:owner/_apis/git/repositories/:repo/pushes",
      "origin": "https://${AZURE_REPOS_HOST}/${AZURE_REPOS_ORG}",
      "auth": {
        "scheme": "basic",
        "token": "${BROKER_CLIENT_VALIDATION_BASIC_AUTH}"
      }
    },
    {
      "//": "used to redirect requests to snyk git client",
      "method": "any",
      "path": "/snykgit/*",
      "origin": "${GIT_CLIENT_URL}"
    }
  ]
}
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
  -e ACCEPT=/private/accept.json \
  -v /local/path/to/private:/private \
  snyk/broker:github-com
```

Note that this gives Snyk the ability to query for any `.yaml`, `.yml` or `.json` files. If you would prefer to be stricter, you can alter the paths in the preceding examples to be more restrictive for certain projects or file layouts.
