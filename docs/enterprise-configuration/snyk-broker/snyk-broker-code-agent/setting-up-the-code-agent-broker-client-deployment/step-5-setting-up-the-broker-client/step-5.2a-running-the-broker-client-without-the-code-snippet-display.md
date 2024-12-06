# 5.2a 단계 - 코드 스니펫 표시 없이 Broker 클라이언트 실행하기

{% hint style="info" %}
**중요!** 이 섹션에서 설명하는 Broker 클라이언트 실행을 위한 설정 명령에는 모든 SCM에 사용되는 공통 명령이 포함되어 있습니다. 그러나 일부 SCM은 Broker 클라이언트 설정에 추가 매개 변수가 필요합니다.

이러한 추가 매개변수가 필요한 경우 이 섹션에 표시되지만 특정 SCM에 대한 Broker 클라이언트를 설정할 때는 해당 SCM에 해당하는 섹션도 사용합니다. 자세한 내용은 [Snyk Broker 연동 설정](broken-reference/)을 참조하세요.
{% endhint %}

Broker 클라이언트 이미지가 머신에 저장되면 docker 실행 명령을 사용하여 이미지를 실행하고 이를 기반으로 하는 Broker 클라이언트 컨테이너를 시작합니다.

다음은 웹 UI에 Snyk 코드 결과의 코드 스니펫을 표시하지 않는 방식으로 Broker 클라이언트를 설정하는 방법에 대해 설명합니다:

<figure><img src="../../../../../.gitbook/assets/Broker - Results - without code snippets (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (4) (1).png" alt="Broker Client run with no display of code snippets"><figcaption><p>코드 스니핑 표시 없이 Broker 클라이언트 실행</p></figcaption></figure>

코드 조각을 표시하려면 [코드 조각을 표시하여 Broker 클라이언트 실행하기](step-5.2b-running-the-broker-client-with-the-code-snippets-display.md)를 참조하세요.

**Broker 클라이언트 컨테이너를 실행하려면,** 터미널에서 다음 명령을 입력하여 Snyk Broker 클라이언트 이미지를 기반으로 컨테이너를 실행합니다:

```
docker run --restart=always \
   -p <host_machine_port_no._mapped to>:<Broker_Client_container_port_ no.> \
   -e BROKER_TOKEN=<Broker_token> \
   -e <SCM>_TOKEN=<SCM_token> \
   -e <SCM_domain>=<my.SCM.domain.com_(without_http/s)> \  
   -e BROKER_CLIENT_URL=<http://my.broker.client:<host_machine_port_no.> \
   -e PORT=<Broker_Client_container_port_no.> \
   -e GIT_CLIENT_URL=http://<Code_Agent_container_name:Code_Agent_port_no.> \
   --network mySnykBrokerNetwork \
   snyk/broker:<SCM_tag>
```

어디에:

* `-- restart=always` 는 종료 상태와 관계없이 Broker 클라이언트 컨테이너가 항상 다시 시작되도록 결정하는 Docker 명령입니다.
* `-p <host_machine_port_no._mapped to>:<Broker_Client_container_port_ no.>` 는 호스트 머신의 실제 열린 포트를 Broker 클라이언트 컨테이너의 포트에 매핑하는 것입니다. 호스트 컴퓨터와 컨테이너의 포트 번호가 동일할 필요는 없습니다(예: `8001:8000`).\
  호스트 컴퓨터의 포트 번호는 고유해야 합니다.
* `-e BROKER_TOKEN`은 특정 조직 및 특정 통합 SCM과 연결된 [Broker 토큰](../step-1-obtaining-the-required-tokens-for-the-setup-procedure/obtaining-your-broker-token.md)입니다.
* `-e <SCM_TOKEN>`은 특정 통합 SCM에 대한 [SCM 토큰](../step-1-obtaining-the-required-tokens-for-the-setup-procedure/obtaining-your-scm-token.md)입니다.&#x20;
* `-e <SCM_domain>=` 는 http/https를 제외한 SCM 도메인 이름입니다(예:`snyk.git.com`). 각 SCM에 대해. SCM에 대해 이 매개 변수를 사용합니다:
  * **GitHub** - `-e <SCM_domain>`매개 변수는 필요하지 않습니다.
  * **GitHub Enterprise**: `-e GITHUB`\
    [GitHub Enterprise](../../../install-and-configure-snyk-broker/github-enterprise-install-and-configure-broker/setup-broker-with-github-enterprise.md)의 경우 다음 매개변수도 추가하세요:\
    `-e GITHUB_API=<your.ghe.domain.com/api/v3_(without_http/s)> \`\
    `-e GITHUB_GRAPHQL=<your.ghe.domain.com/api_(without_http/s)> \`
  * **Azure Repos**: `-e AZURE_REPOS_HOST`\
    [Azure Repos](../../../install-and-configure-snyk-broker/azure-repos-install-and-configure-broker/setup-broker-with-azure-repos.md)의 경우 다음 매개 변수도 추가합니다:\
    `-e AZURE_REPOS_ORG=<azure_repo_org_name> \`
  * **Bitbucket 서버/데이터 센터**: `-e BITBUCKET`\
    [Bitbucket 서버/데이터 센터](../../../install-and-configure-snyk-broker/bitbucket-server-data-center-install-and-configure-broker/data-center.md)의 경우 다음 매개변수도 추가합니다:\
    `-e BITBUCKET_API=<your.bitbucket-server.domain.com/rest/api/1.0_(without http/s)> \`
  * **GitLab**: `-e GITLAB`
* \[선택 사항] `-e BROKER_CLIENT_URL=`은 Broker 클라이언트의 호스트 컴퓨터에 대한 URL입니다. URL에는 호스트 컴퓨터의 포트 번호가 포함된 IP 주소 또는 DNS (예: `http://localhost:8000`)를 포함할 수 있습니다.\
  이 매개변수는 다른 Snyk 제품에 동일한 Broker 클라이언트를 사용하고 있고 자동 PR 확인 기능을 활성화하려는 경우에만 추가하세요. 현재 자동 PR 확인 기능은 코드 에이전트에서 지원되지 않으므로 코드 에이전트에는 이 파라미터를 사용할 필요가 없습니다.
* `-e PORT` 는 외부 연결을 수락하는 Broker 클라이언트 컨테이너의 포트 번호입니다. 기본값은 `8000`.입니다. 이 포트 번호는 위의 `-p`파라미터의 `<Broker_Client_container_port_ no.>` 와 동일해야 합니다.
* 실행 중인 코드 에이전트 컨테이너의 포트에 대한 URL을 `-e GIT_CLIENT_URLis`로 입력합니다. URL에는 코드 에이전트 컨테이너의 이름과 해당 포트 번호(예:`http://code-agent:3000`)가 포함되어야 합니다.
* `--network` 는 코드 에이전트와의 통신에 사용되는 [Docker   bridge network](../step-3-creating-a-network-for-the-broker-client-and-code-agent-communication.md)의 이름입니다.
* `snyk/broker:<SCM_tag>` 는 특정 통합 SCM을 위한 [Broker 클라이언트의 Docker 이미지](step-5.1-downloading-or-updating-the-snyk-broker-client-docker-image.md)입니다.

Broker 클라이언트 설정이 성공적으로 완료되면 터미널에 다음 메시지가 표시됩니다:

`{ ..., "msg":"successfully established a websocket connection to the broker server", ... }`

<figure><img src="../../../../../.gitbook/assets/Broker Client - Setup success message.png" alt="Confirmation message for Broker Client setup"><figcaption><p>Broker 클라이언트 설정 확인 메시지</p></figcaption></figure>

**Broker 클라이언트 컨테이너의 설정 및 세부 정보를 확인하려면,** 실행합니다:

```
docker ps
```

출력은 다음과 비슷합니다:

```
CONTAINER ID   IMAGE                     COMMAND                  CREATED             STATUS             PORTS                    NAMES
7d9a410e7eaa   snyk/broker:azure-repos   "broker --verbose"       About an hour ago   Up About an hour   0.0.0.0:8000->8000/tcp   sweet_williams
6216e27b8d28   snyk/code-agent           "docker-entrypoint.s…"   2 hours ago         Up 2 hours         0.0.0.0:3000->3000/tcp   code-agent
```
