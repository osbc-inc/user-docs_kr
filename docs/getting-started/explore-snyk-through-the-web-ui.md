# Web UI를 통해 Snyk 확인

{% hint style="success" %}
아직 계정을 만들지 않았다면, [계정을 만들](quickstart/create-or-log-in-to-a-snyk-account.md)어야 합니다.
{% endhint %}

## Snyk 웹 UI 및 지원되는 브라우저 소개

Snyk 웹 UI를 통해 브라우저에서 전체 Snyk 기능을 실행할 수 있습니다. 자세한 내용은 [supported browsers](quickstart/#supported-browsers) 를 참조하세요.

<figure><img src="../.gitbook/assets/Screenshot 2023-07-13 at 11.06.29 AM.png" alt="Snyk Dashboard, the view when you log in"><figcaption><p>Snyk 대시보드, 로그인 시 보이는 화면</p></figcaption></figure>

{% hint style="info" %}
&#x20;[Snyk CLI](../snyk-cli/), [IDE](../integrate-with-snyk/ide-tools/) 및 [Snyk API](../snyk-api/) 통해, Snyk 기능을 사용할 수도 있습니다.
{% endhint %}

코드 리포지토리를 연결한 다음, Snyk를 사용하여 애플리케이션 코드, 오픈 소스 라이브러리, 컨테이너 레지스트리 및 구성 파일을 검사하고 보호할 수 있습니다.

이 페이지에서는 웹 UI를 통해 사용할 수 있는 Snyk의 다음 기능을 설명합니다.

* [Explore the Dashboard](explore-snyk-through-the-web-ui.md#dashboard)
* [View reports](explore-snyk-through-the-web-ui.md#view-reports)
* [Manage your Projects](explore-snyk-through-the-web-ui.md#manage-your-projects)
* [Manage your integrations](explore-snyk-through-the-web-ui.md#manage-your-integrations)
* [Manage Organization or Group members](explore-snyk-through-the-web-ui.md#manage-organization-or-group-members)
* [Snyk Organization and Group settings](explore-snyk-through-the-web-ui.md#snyk-organization-or-group-settings)
* [View Snyk updates](explore-snyk-through-the-web-ui.md#view-snyk-updates)
* [View helpful resources](explore-snyk-through-the-web-ui.md#view-helpful-resources)
* [Manage account preferences and settings](explore-snyk-through-the-web-ui.md#manage-account-preferences-and-settings)

## 대시보드 살펴보기

기존 계정에 로그인하면 웹 UI에서 대시보드가 열립니다. pending tasks와 vulnerable Projects를 보고, 팀 구성원을 초대하고, 새 프로젝트를 추가할 수 있습니다.

다음 예에서는 Enterprise 계정용 Snyk 대시보드에 pending tasks와 vulnerable Projects가 표시됩니다.

<figure><img src="../.gitbook/assets/Screenshot 2023-07-13 at 11.09.02 AM.png" alt="Snyk dashboard for an Enterprise account"><figcaption><p>기업 계정용 Snyk 대시보드</p></figcaption></figure>

### 대기 중인 작업(Pending tasks)

**Pending tasks** 섹션에는 Snyk 조직의 프로젝트에 대해 처리할 다음 작업이 표시됩니다. 이 정보에는 다음이 포함됩니다.

* 가장 취약한 일부 프로젝트의 취약점을 수정하기 위해 제기할 수 있는 PR(Pull Request)
* (Snyk에 의해 또는 Snyk를 통해) 이미 제기되어 검토를 기다리고 있는PR (Pull Request).

현재 Snyk은 GitHub, GitHub Enterprise 및 Bitbucket Cloud에서만, 가장 취약한 프로젝트에 대해서만 PR을 추적하고 플래그를 지정합니다. 다른 SCM을 사용하는 경우 **Pending task** 섹션에는 이미 제기된 PR이 아닌 제기될 수 있는 PR만 표시됩니다.

<figure><img src="../.gitbook/assets/image (109) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (1).png" alt="Pending tasks and Vulnerable Projects listed on the Dashboard"><figcaption><p>대시보드에 나열된 Pending tasks 및 Vulnerable Projects</p></figcaption></figure>

### 프로젝트 추가

[Snyk Projects](../snyk-admin/snyk-projects/)를 추가하려면 대시보드의 **프로젝트 추가(Add Project)** 링크를 사용하세요. 드롭다운에서 프로젝트를 추가하는 방법을 선택하세요.

대시보드의 프로젝트 링크를 사용하여 프로젝트의 대상 파일에 대한 메타데이터를 탐색 및 관리하고, 다시 테스트하고, 옵션을 수정하세요. 각 링크는 프로젝트 **개요(Overview)**를 보거나 **기록(History)** 및 **설정(Settings)** 탭으로 전환할 수 있는 프로젝트 세부 정보 페이지를 엽니다.

* **취약성 수정(Fix vulnerabilities)** 링크가 있는 프로젝트의 경우, 링크를 사용하여 **Open a Fix PR** 옵션이 포함된 프로젝트 세부 정보를 확인하세요**.** 문제를 해결하는 GitHub의 업그레이드 및 패치를 구현하기 위해 Fix PR을 열려면 이 옵션을 사용합니다.
* **View PR** 링크가 있는 프로젝트의 경우, GitHub에서 Snyk 생성 PR 수정 사항을 열고 확인하세요.

<figure><img src="../.gitbook/assets/demo-project-details-options (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (9).gif" alt="Demo, add project and Project details tabs"><figcaption><p>데모, 프로젝트 추가 및 프로젝트 세부정보 탭</p></figcaption></figure>

## 보고서 보기

[reports](../manage-issues/reporting/) 를 보고 모든 프로젝트 상태, 취약점 및 라이선스 문제에 대한 가시성과 통찰력을 얻을 수 있습니다. Reporting 사용자 인터페이스의 도구 설명(tool tips)에서 보고서(reports) 정보에 대한 자세한 정의를 찾을 수 있습니다.

{% hint style="info" %}
**기능 가용성 (Feature availability)**\
보고(Reporting)는 Enterprise 플랜에서 사용할 수 있습니다.
{% endhint %}

## 프로젝트 관리

대시보드 탐색에서 **프로젝트** 링크를 선택하여 **프로젝트** 목록 페이지를 엽니다. 여기서 다음을 수행할 수 있습니다.

* 프로젝트를 추가합니다. 드롭다운에서 프로젝트를 추가하려는 방법을 선택하세요.
* 프로젝트를 필터링, 그룹화, 정렬하세요.
* 프로젝트에 대한 팁과 최신 가져오기(import) 로그를 확인하세요.
* 요약 및 이슈 정보가 포함된 프로젝트 세부 정보 페이지를 보려면, 각 프로젝트에 대한 링크를 선택하세요.
* 프로젝트가 Target별로 그룹화되면 더하기 아이콘을 사용하고 사용자 정의 위치에서 Target을 추가합니다. 이를 통해 목록의 다른 Target에 있는 프로젝트를 그룹화할 수 있습니다.
* 그룹 해제된 **프로젝트(Projects)** 목록의 설정 아이콘이나 프로젝트 세부 정보 페이지의 **설정(Settings)** 탭을 사용하여 알림, 프로젝트 테스트 및 풀 요청(PR) 빈도에 대한 일반 및 GitHub 통합 설정을 구성합니다. 고유한 프로젝트 ID를 조회하고 설정 탭에서 프로젝트를 비활성화하거나 삭제할 수도 있습니다.
* **기록 탭(History)**에서 프로젝트 기록을 봅니다.

<figure><img src="../.gitbook/assets/Project listing add projects.gif" alt="Options on the Projects listing page"><figcaption><p>프로젝트 목록 페이지의 옵션</p></figcaption></figure>

## 통합 관리

대시보드 탐색에서 **통합(Integrations)**을 선택하여 다음을 수행할 수 있는 통합 페이지([Integrations](../integrate-with-snyk/))를 엽니다.

* 취약성 모니터링을 위해 Snyk에 연결할 수 있는 [SCM 통합](../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/)을 설정하고 확인하세요.
* [Cloud platforms](../integrate-with-snyk/cloud-platforms-integrations/) 과 [Container integrations](../integrate-with-snyk/snyk-container-integrations/)을 설정합니다.
* &#x20;[CI/CD 연동](../integrate-with-snyk/snyk-ci-cd-integrations/), [IDE plugins](../integrate-with-snyk/ide-tools/), [Gatekeeper plugins](../integrate-with-snyk/gatekeeper-plugins/)을 설정합니다.
* [Notifications](../integrate-with-snyk/notification-and-ticketing-systems-integraitons/), [Cloud events](../integrate-with-snyk/event-forwarding/) 통합을 설정합니다.

<figure><img src="../.gitbook/assets/image (123) (1) (2) (1).png" alt="Integrations page"><figcaption><p>통합 페이지</p></figcaption></figure>

## 조직 또는 그룹 구성원 관리

대시보드 탐색에서 **Members**를 선택하면 Snyk [Organization](../snyk-admin/manage-users-in-organizations-and-groups/manage-users-in-organizations.md) 또는[Group](../snyk-admin/manage-users-in-organizations-and-groups/manage-users-in-a-group.md)에서 사용자, 역할, 사용자 인증 방법을 보고 관리할 수 있습니다.

{% hint style="info" %}
**Members** 탭에서 변경을 수행하려면 [required Admin roles and permissions](broken-reference/)을 할당받아야 합니다.
{% endhint %}

## Snyk 조직 또는 그룹 설정

**설정(Settings)** 옵션을 사용하면 조직(팀) 또는 그룹(회사 전체) 설정을 보고 관리할 수 있습니다.

<figure><img src="../.gitbook/assets/Manage-settings-intro.png" alt="Group and Organization settings"><figcaption><p>그룹 및 조직 설정</p></figcaption></figure>

자세한 내용은 [Manage settings](../snyk-admin/manage-settings/)를 참조하세요.

## Snyk 업데이트 보기

대시보드 탐색에서 **도움말(Help)**을 선택한 다음 **제품 업데이트(Product updates)**를 선택하여 [snyk.io updates](https://updates.snyk.io/)를 방문하세요.&#x20;

## 유용한 리소스 보기

대시보드 탐색에서 **도움말(Help)**을 선택한 다음 Snyk에 대한 정보가 포함된 리소스를 보는 옵션을 선택하세요.

## 계정 기본 설정 및 설정 관리

대시보드 탐색에서 **이름(name)**을 선택한 다음 계정 설정을 선택하여 [account settings](https://app.snyk.io/account) 페이지를 엽니다. 여기에서 **사용자 계정 설정(Account settings)**과 알림 및 공유 기본 설정을 보고 구성할 수 있습니다.

계정 설정에서 다음 정보와 옵션에 액세스할 수 있습니다.

* 무료 계정의 API 토큰 또는 인증 토큰을 보고 관리하세요. 모든 애플리케이션 및 도구에 적용되는 지침은 [Snyk API 토큰 획득](how-to-obtain-and-authenticate-with-your-snyk-api-token.md) 참조하세요.
* **승인된 애플리케이션** 목록을 확인하세요.
* 선호하는 조직을 설정하세요. [Manage Organizations: Set your preferred Organization](../snyk-admin/manage-groups-and-organizations/create-and-delete-organizations.md#set-your-preferred-organization).
* 계정을 **삭제**하세요.
* 문제 이메일 알림, 주간 보고서 이메일, 사용 알림 등 이메일 **알림**(왼쪽 탐색 링크)에 대한 계정 설정을 관리하고, 보고서 사용 가능 시 이메일 알림과 영업 및 마케팅 커뮤니케이션 기본 설정을 관리하세요. 이메일 알림에 대한 자세한 내용과 알림에 대한 개인 기본 설정을 지정하는 방법은 [Manage notifications](../snyk-admin/manage-notifications.md) 페이지를 참조하세요.
* **친구와 공유**할 수 있는 추천 링크를 받으세요. 링크는 계정 설정의 왼쪽 탐색 메뉴에 있습니다.
