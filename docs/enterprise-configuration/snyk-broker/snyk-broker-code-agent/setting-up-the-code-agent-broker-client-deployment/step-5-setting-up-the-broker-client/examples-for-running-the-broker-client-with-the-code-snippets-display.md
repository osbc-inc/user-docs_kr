# 코드 스니펫을 사용하여 Broker 클라이언트를 실행하는 예제 표시

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
   -e ACCEPT=/private/accept.json \
   -v /private:/private \
   --network mySnykBrokerNetwork \
snyk/broker:github-com
```

어디에:

* `-p 8000:8000`은 호스트 머신의 포트 번호 `8000`, Broker 클라이언트 컨테이너의 포트 번호 `8000`에 매핑됩니다. 이 포트는 Broker 클라이언트 컨테이너와 브로커 서버 및 코드 에이전트 간의 통신에 사용됩니다.
* `-e BROKER_TOKEN`은 특정 조직 및 GitHub와 연결된 Broker 토큰입니다.
* `-e GITHUB_TOKEN` is the GitHub token for accessing the GitHub repositories.
* `-e BROKER_CLIENT_URL` is the URL to the host machine of the Broker Client, `http://localhost:8000`.
* `-e PORT` is the local port, where the Broker Client container accepts connections, `8000`.
* `-e GIT_CLIENT_URL=http://code-agent:3000` is the URL to the port of the running Code Agent container. The URL includes the name of the Code Agent container – `code-agent` - with its port no. - `3000`.
* `-e ACCEPT=/private/accept-github.json` is the name of the folder that stores the downloaded `accept.json` file, `private`, and the name of the file for GitHub, `accept.json`.
* `-v /private:/private` is the path to the folder that stores the `accept-github.json` file, private, and the name of the folder, private.
* `--network` is the name of the Docker bridge network, used for the communication with the Client Broker, `mySnykBrokerNetwork`.
* `snyk/broker:github-com` is the Docker image of the Broker Client for GitHub.

## **Running the Broker Client for an integrated Azure Repos Server**

The following command was entered to run the Broker Client for an integrated Azure Repos Server:

```
docker run --restart=always \
   -p 8001:8001 \
   -e BROKER_TOKEN=fe5bxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx \
   -e AZURE_REPOS_TOKEN=brmyxxxxxxxxxxxxxxxx \
   -e AZURE_REPOS_ORG=snyktest \
   -e AZURE_REPOS_HOST=dev.azure.com \
   -e BROKER_CLIENT_URL=http://localhost:8001 \
   -e PORT=8001 \
   -e GIT_CLIENT_URL=http://code-agent:3000 \
   -e ACCEPT=/private/accept.json \
   -v ./private:/private \
   --network mySnykBrokerNetwork \
snyk/broker:azure-repos
```

where:

* `-p 8001:8001` is port number `8001` on the host machine, mapped to port number `8001` on the Broker Client container, for communication between the Broker Client container and the Broker Server and Code Agent.
* `-e BROKER_TOKEN` is the Broker token associated with the specific Organization and Azure Repos.
* `-e AZURE_REPOS_TOKEN` is the Azure Repo token for accessing the Azure Repos repositories.
* `-e AZURE_REPOS_ORG` is the name of the Azure Repos organization, `snyktest`.
* `-e AZURE_REPOS_HOST` is the domain name of the Azure Repos Server, `dev.azure`.com.
* `-e BROKER_CLIENT_URL` is the URL of the host machine of the Broker Client, `http://localhost:8001`.
* `-e PORT` is the local port, where the Broker Client container accepts connections, `8001`.
* `-e GIT_CLIENT_URL=http://code-agent:3000` is the URL to the port of the running Code Agent container. The URL includes the name of the Code Agent container, `code-agent`, with its port number, `3000`.
* `-e ACCEPT=/private/accept.json` is the name of the folder that stores the downloaded `accept.json` file, private, and the name of the file for GitHub, `accept.json`.
* `-v ./private:/private` is the path to the folder that stores the `accept.json` file, `private`, and the name of the folder. `private`.
* `--network` is the name of the Docker bridge network, used for communication with the Client Broker, `mySnykBrokerNetwork`.
* `snyk/broker:azure-repos` is the Docker image of the Broker Client for Azure Repos.
