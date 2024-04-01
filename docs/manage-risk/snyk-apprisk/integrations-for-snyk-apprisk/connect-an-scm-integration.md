# SCM integration 연결

Integration 페이지에는 자동으로 동기화되고 Integrations Hub에 대해 접근이 가능한 기존 Snyk Organization의 데이터를 포함하여 모든 활성 integration이 표시됩니다.

다음 SCM을 사용할 수 있는 **Integrations Hub**에서 AppRisk integration을 사용자 정의할 수 있습니다:

* [GitHub](connect-an-scm-integration.md#github-setup-guide)
* [GitLab](connect-an-scm-integration.md#gitlab-setup-guide)
* [Azure DevOps](connect-an-scm-integration.md#azure-devops-setup-guide)
* [BitBucket](connect-an-scm-integration.md#bitbucket-setup-guide)

## GitHub 설치 가이드

### Pulled entities

* Repositories
* Builds - GitHub Actions를 사용하는 경우에만 작성합니다.
* Scans - 코드 보안을 사용하는 경우에만 검색합니다.

### 필수 파라미터

* Organization Name - GitHub 조직 이름.
* Profile name - 저장소를 읽는 데 사용된 GitHub 사용자입니다.
* API Token - 다음 권한을 가진 API access token:
  * `repo`
  * `read:packages`
  * `read:org`
  * `read:user`
  * `user:email`

SAML SSO를 구성한 경우 개인 access token을 승인합니다.

소유한 저장소만 pull하려면 Integrations Hub 페이지에서 **Pull personal repositories** 확인란을 선택합니다.

{% hint style="info" %}
세분화된 개인 access token은 지원하지 않습니다.
{% endhint %}

### GitHub enterprise 추가 파라미터

호스트 주소 GitHub 서버의 IP/URL로 사용할 수 있습니다. 기본 URL은 [`https://api.github.com`](https://api.github.com)입니다.

### GitHub code security 추가 파라미터

Token과 연결된 사용자는 스캔 문제의 내역을 수집하기 위해 관련 저장소에 대한 쓰기 권한이 있어야 합니다.

### API 버전

[GitHub REST API](https://docs.github.com/en/rest?apiVersion=2022-11-28) 저장소를 통해 API에 대한 정보를 접근할 수 있습니다.

### API token 설정

1. GitHub를 열고 프로필의 Settings 메뉴를 클릭합니다.
2. 왼쪽 사이드바에서 Developer settings를 선택합니다.
3. 개인 access token을 선택한 다음 tokens(classic)를 선택합니다.
4. Generate new token을 클릭하고 드롭다운 화면에서 Generate new token (classic)을 선택합니다.
5. Note field에 token에 대한 설명을 추가합니다.
6. 필요한 권한을 선택합니다: `repo`, `read:packages`, `read:org`, `read:user`, `user:email`.
7. Generate token을 클릭합니다.
8. 표시된 키를 복사하여 저장합니다.

{% hint style="info" %}
세분화된 개인 액세스 토큰은 지원되지 않습니다.
{% endhint %}

## GitLab 설치 가이드

### Pulled entities

* Users
* Repositories

### 필수 파라미터

* Host address - GitLab 서버의 IP/URL입니다.
* Personal API token - 사용자 및 저장소를 가져올 수 있는 권한이 있는 사용자 계정에 연결되어 있습니다. URL은 다음 예시를 따라야 합니다: `https://gitlab.com/-/profile/personal_access_tokens`.
* 권한:
  * `read_api` - 모든 그룹 및 프로젝트, 컨테이너 레지스트리 및 패키지 레지스트리를 포함하여 API에 대한 읽기 접근 권한을 부여합니다.
  * `read_repository` - Git-over HTTP 또는 Repository Files API를 사용하여 개인 프로젝트의 저장소에 대한 읽기 전용 접근 권한을 부여합니다.

SAML SSO를 구성한 경우 개인 access token을 승인합니다.

소유한 저장소만 pull하려면 Integrations Hub 페이지에서 **Pull personal repositories** 확인란을 선택합니다.

### API 버전

[GitLab REST API v4](https://docs.gitlab.com/ee/api/index.html) 저장소를 통해 API에 대한 정보를 접근할 수 있습니다.

## Azure DevOps 설치 가이드

### Pulled entities

* Repositories

### 필수 파라미터

* Azure DevOps PAT - 개인 access token 생성
  * Permissions
    * **Code** - read
      * **Project and Team** - read
      * **Graph** - read
      * **Analytics** - read
      * **Build** - read
      * **Release** - read
      * **Security** - manage
  * Organization -  **All accessible organizations** 또는 a specific organization을 선택합니다.
* Azure DevOps organization names - 관련된 Azure DevOps 조직의 이름입니다.
* API URL - 공개적으로 접근할 수 있는 사용자 정의 URL을 사용할 수 있습니다. 예시는 다음과 같습니다: [`https://dev.azure.com/`](https://dev.azure.com/).&#x20;

### API 버전

[Azure DevOps REST API v6](https://learn.microsoft.com/en-us/rest/api/azure/devops/core/?view=azure-devops-rest-6.0) 저장소를 통해 API에 대한 정보를 접근할 수 있습니다.

### 개인 access token 생성

1. Azure DevOps를 열고 프로필의 **Settings** 메뉴를 클릭합니다.
2. **Personal access tokens**를 클릭한 다음 **New token**을 클릭합니다.
3. **Code, Project and Team, Graph** 및 **Analytics read scopes**를 선택합니다.
4. 유효기간을 12개월로 설정합니다.
5. 생성된 개인 access token을 복사하여 secured vault를 통해 공유합니다.

### 권한

다음 권한을 사용합니다:

* **Graph** - Read
* **Security** - Manage
* **Scopes** - Custom defined
* **Analytics** - Read
* **Build** - Read
* **Code** - Read
* **Project and Team** - Read
* **Release** - Read

## BitBucket 설치 가이드

{% hint style="info" %}
BitBucket Server 및 BitBucket Cloud는 자동 언어 탐지를 지원하지 않습니다.

BitBucket Cloud를 사용하는 경우 언어 태그를 저장소에 수동으로 추가할 수 있습니다.

BitBucket Server의 경우 수동으로 저장소에 언어 태그를 추가할 수 없습니다.
{% endhint %}

### Pulled entities

* Users
* Repositories

### 필수 파라미터

* API URL - Bitbucket API의 URL
* Username - [Bitbucket username](https://bitbucket.org/account/settings/)
* App password - 다음 권한을 가진 BitBucket 계정에서 [API token](https://developer.atlassian.com/cloud/bitbucket/rest/intro/#app-passwords)을 생성합니다:
  * **Workspace membership** - Read
  * **Account** - Read
  * **Projects** - Read
  * **Repositories** - Read
  * **Issues** - Read

{% hint style="info" %}
다음 단계를 수행하여 BitBucket app password를 생성합니다:

1. BitBucket account 열기
2. Settings 옵션을 클릭합니다
3. Personal BitBucket settings 옵션을 클릭합니다
4. ACCESS MANAGEMENT 섹션에서 App password 하위 섹션으로 이동합니다.
{% endhint %}

* Workspaces - Bitbucket Workspace 이름, 인증 후 액세스 가능

### API 버전

[BitBucket REST API V2](https://developer.atlassian.com/bitbucket/api/2/reference/resource/) 저장소를 통해 API에 대한 정보를 접근할 수 있습니다.\
