# SCM 토큰 받기

통합 SCM 토큰은 [Broker 클라이언트 구성 요소를 설정](../step-5-setting-up-the-broker-client/step-5.2a-running-the-broker-client-without-the-code-snippet-display.md)하는 데 필요하며,`-e <SCM>_TOKEN`에 사용됩니다, (예:  `-e GITHUB_TOKEN=xxx…`). 이 토큰은 Broker 및 Snyk 코드의 작동에 필요한 특정 권한으로 SCM에 액세스하는 데 필요합니다.

**SCM 토큰을 받으려면,** Snyk Broker와 통합하려는 SCM에서 제공하는 지침에 따라 필요한 권한이 있는 토큰을 생성합니다.

다른 SCM에는 다음 SCM 토큰이 필요합니다:

**GitHub 및 GitHub Enterprise:**

`GITHUB_TOKEN=` - GitHub 개인 액세스 토큰. 범위: **`repo, read:org`** and **`admin:repo_hook`**.

GitHub 문서 - [_개인 엑세스 토큰 만들기_](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)\_\_를 참조하세요.

**Gitlab**:

**`GITLAB_TOKEN=`** - GitLab 개인 액세스 토큰입니다. **`Maintainer`** 권한이 있는 깃랩 계정. 범위: **`api`**.

Gitlab 설명서 - [_개인 엑세스 토큰_](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)\_\_을 참조하세요.

**Azure Repos**:

**`AZURE_REPOS_TOKEN=`** - an Azure Repos 개인 액세스 토큰입니다. 범위: **`Custom defined`, \*\* `Code:` \*\* `Read & write`**_._

Azure Repos 설명서 - [_개인 액세스 토큰 사용_](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops\&tabs=Windows)\_\_을 참조하세요.

**Bitbucket 서버/데이터 센터:**

**`BITBUCKET_USERNAME=`**, **`BITBUCKET_PASSWORD=`** – Bitbucket Server 사용자 이름 및 비밀번호 또는 Bitbucket Server 개인 액세스 토큰입니다. 범위: **`Repository admin`**.

Bitbucket Server 설명서 - [_개인 액세스 토큰_](https://confluence.atlassian.com/bitbucketserver/http-access-tokens-939515499.html)\을 참조하세요.
