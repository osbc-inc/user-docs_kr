# 코드 스니펫 표시 없이 Broker 클라이언트를 실행하는 예제

## 통합 GitHub 서버용 Broker 클라이언트 실행하기

다음 명령을 입력하여 통합 GitHub 서버용 Broker 클라이언트를 실행했습니다:

```
docker run --restart=always \
   -p 8000:8000 \
   -e BROKER_TOKEN=b1dcxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx \
   -e GITHUB_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxx \
   -e BROKER_CLIENT_URL=http://localhost:8000 \
   -e PORT=8000 \
   -e GIT_CLIENT_URL=http://code-agent:3000 \
   --network mySnykBrokerNetwork \
snyk/broker:github-com
```

어디에:

* `-p 8000:8000` 은 호스트 머신의 포트 번호`8000`이며, Broker 클라이언트 컨테이너의 포트 번호 `8000` 에 매핑됩니다. 이 포트는 Broker 클라이언트 컨테이너와 Broker 서버 및 코드 에이전트 간의 통신에 사용됩니다.
* `-e BROKER_TOKEN`은 특정 조직 및 GitHub와 연결된 Broker 토큰입니다.
* `-e GITHUB_TOKEN`은 GitHub 리포지토리에 액세스하기 위한 GitHub 토큰입니다.
* `-e BROKER_CLIENT_URL`은 Broker 클라이언트의 호스트 컴퓨터 URL(`http://localhost:8000`)입니다.
* `-e PORT`는 Broker 클라이언트 컨테이너가 연결을 수락하는 로컬 포트이며,`8000`입니다.
* `-e GIT_CLIENT_URL=http://code-agent:3000`은 실행 중인 코드 에이전트 컨테이너의 포트에 대한 URL입니다. URL에는 코드 에이전트 컨테이너의 이름(`code-agent`)과 해당 포트 번호(`3000`)가 포함됩니다.
* `--network`는 클라이언트 Broker인 `mySnykBrokerNetwork`와의 통신에 사용되는 Docker 브리지 네트워크의 이름입니다.
* `snyk/broker:github-com`은 GitHub용 Broker 클라이언트의 Docker 이미지입니다.

## 통합 Azure Repos 서버용 Broker 클라이언트 실행하기

다음 명령을 입력하여 통합 Azure Repos 서버용 Broker 클라이언트를 실행했습니다:

```
docker run --restart=always \
   -p 8000:8001 \
   -e BROKER_TOKEN=fe5bxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx \
   -e AZURE_REPOS_TOKEN=brmyxxxxxxxxxxxxxxxx \
   -e AZURE_REPOS_ORG=snyktest \
   -e AZURE_REPOS_HOST=dev.azure.com \
   -e BROKER_CLIENT_URL=http://localhost:8000 \
   -e PORT=8001 \
   -e GIT_CLIENT_URL=http://code-agent:3000 \
   --network mySnykBrokerNetwork \
snyk/broker:azure-repos
```

어디에:

* `-p 8000:8001`은 호스트 머신의 포트 번호 `8000` 으로, Broker 클라이언트 컨테이너의 포트 번호 `8001`에 매핑됩니다. 이 포트는 Broker 클라이언트 컨테이너와 Broker 서버 및 코드 에이전트 간의 통신에 사용됩니다.
* `-e BROKER_TOKEN`은 특정 조직 및 Azure Repos와 연결된 Broker 토큰입니다.
* `-e AZURE_REPOS_TOKEN`은 Azure Repos 리포지토리에 액세스하기 위한 Azure Repo 토큰입니다.
* `-e AZURE_REPOS_ORG` - Azure Repos 조직의 이름인`snyktest`입니다.
* `-e AZURE_REPOS_HOST` 는 Azure Repos 서버의 도메인 이름인`dev.azure.com`입니다.
* `-e BROKER_CLIENT_URL`은 Broker 클라이언트의 호스트 컴퓨터 URL(`http://localhost:8000`)입니다.
* `-e PORT` - Broker 클라이언트 컨테이너가 연결을 수락하는 로컬 포트(`8001`)입니다.
* `-e GIT_CLIENT_URL=http://code-agent:3000`은 실행 중인 코드 에이전트 컨테이너의 포트에 대한 URL입니다. URL에는 코드 에이전트 컨테이너의 이름( `code-agent`)과 해당 포트 번호(`3000`)가 포함됩니다.
* `--network`는 클라이언트 Broker와의 통신에 사용되는 Docker 브리지 네트워크의 이름이며, `mySnykBrokerNetwork`입니다.
* `snyk/broker:azure-repos`는 Azure Repos용 Broker 클라이언트의 Docker 이미지입니다.
