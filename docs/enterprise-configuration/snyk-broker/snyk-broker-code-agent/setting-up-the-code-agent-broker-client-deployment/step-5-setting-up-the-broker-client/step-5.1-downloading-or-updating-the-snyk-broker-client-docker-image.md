# 5.1단계: Snyk Broker 클라이언트 다운로드 또는 업데이트 - Docker 이미지

{% hint style="info" %}
Broker 클라이언트 Docker 이미지를 다운로드하기 전에 컴퓨터가 Docker 컨테이너를 실행할 수 있는지 확인하세요.
{% endhint %}

Broker 클라이언트 설정의 첫 번째 단계는 [Docker Hub](https://hub.docker.com/r/snyk/broker)에서 Broker 클라이언트 Docker 이미지를 가져오는 것입니다. Broker 클라이언트를 실행할 각 머신에 Broker 클라이언트 이미지를 다운로드합니다. 다운로드한 후 이 이미지는 호스트 머신에 캐시됩니다.

{% hint style="info" %}
코드 에이전트는 Broker 클라이언트 버전 4.108.0 이상 버전에서만 지원됩니다. 이미 실행 중인 Broker 클라이언트가 있는 경우 최신 업데이트를 가져오세요.
{% endhint %}

**코드 에이전트 Docker 이미지를 가져오려면** 실행합니다:

```
docker pull snyk/broker:<SCM_tag>
```

여기서`SCM_tag`는 다음과 같이 각 통합 SCM에 대한 특정 태그입니다:

**GitHub**:

```
docker pull snyk/broker:github-com
```

**GitHub Enterprise**:

```
docker pull snyk/broker:github-enterprise
```

**GitLab**:

```
docker pull snyk/broker:gitlab
```

**Bitbucket 서버/데이터 센터:**

```
docker pull snyk/broker:bitbucket-server
```

**Azure Repo**:

```
docker pull snyk/broker:azure-repos
```

예를 들어 클라이언트 Broker 이미지의 Docker 이미지에 대한 다운로드 프로세스가 시작됩니다:

<figure><img src="../../../../../.gitbook/assets/Client Broker - Pull image - example.png" alt="Download for Docker image of Client Broker"><figcaption><p>클라이언트 Broker의 Docker용 이미지 다운로드</p></figcaption></figure>

다운로드가 완료되면 Broker 클라이언트 이미지가 컴퓨터에 성공적으로 다운로드되었는지 확인할 수 있습니다.

**Broker 클라이언트의 Docker 이미지가 성공적으로 다운로드되었는지 확인하려면** Docker 목록 명령을 실행합니다:

```
docker image ls
```

출력은 다음과 비슷합니다:

```
REPOSITORY           TAG                 IMAGE ID       CREATED       SIZE
snyk/broker          github-com          e999988aa7b7   7 days ago    252MB
snyk/broker          github-enterprise   0a8b4e6f518d   7 days ago   252MB
```
