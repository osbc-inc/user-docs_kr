# 첫 번째 Snyk 프로젝트 보기

하나 이상의 프로젝트를 가져온 후에는 스캔 결과를 볼 수 있습니다.

{% hint style="info" %}
In the Snyk Web UI, you see information specific to your Organization, such as your team), Snyk 웹 UI에서는 회사와 같은 그룹에 속해 있는 팀과 같은 조직과 관련된 정보를 볼 수 있습니다. 이를 통해 회사에서 팀이 수행하는 업무에 대한 데이터를 정리하고 수집할 수 있습니다. 자세한 내용은 [조직에서 사용자 관리하기](../../snyk-admin/manage-users-in-organizations-and-groups/manage-users-in-organizations.md)를 참조하세요.
{% endhint %}

## 가져오기 보기

코드가 아닌 정보를 가져오는 경우 Snyk 웹 UI에서 **프로젝트** 페이지로 이동하여 가져온 리포지토리 또는 대상을 살펴봅니다. 다음은 예제입니다.

<figure><img src="../../.gitbook/assets/Target-list.png" alt="List of imported Targets"><figcaption><p>가져온 대상 목록</p></figcaption></figure>

각 항목에 대해 아이콘은 각 항목에 있는 Snyk 프로젝트의 수와 프로젝트를 가져온 Git 기반 리포지토리를 표시합니다.

## 비공개 리포지토리와 공개 리포지토리: 잠금 기호

[GitHub 연동을 설정](../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/snyk-github-integration.md)할 때 Snyk이 공개 및 비공개 리포지토리에 액세스할 수 있는지, 아니면 공개 리포지토리에만 액세스할 수 있는지 선택할 수 있습니다:

<figure><img src="../../.gitbook/assets/image (405) (1).png" alt="Set whether Snyk will have access to a private repository"><figcaption><p>Snyk이 비공개 리포지토리에 액세스할 수 있는지 여부를 설정합니다.</p></figcaption></figure>

프로젝트를 가져오면 비공개 리포지토리는 가져온 스캔 세부 정보에서 잠금 기호로 식별됩니다:

<figure><img src="../../.gitbook/assets/image (125) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2).png" alt="Private repos with lock symbol"><figcaption><p>잠금 기호가 있는 비공개 리포지토리</p></figcaption></figure>

무료 요금제를 사용하는 고객의 경우 비공개 리포지토리 스캔은 테스트 횟수 제한에 포함됩니다.

{% hint style="info" %}
일반적으로 개별 개발자가 아닌 팀 리더가 원래의 통합 설정 및 프로젝트 가져오기를 수행합니다.
{% endhint %}

## 프로젝트 목록 보기

항목을 열면 해당 항목에서 스캔한 다양한 Snyk 프로젝트가 표시됩니다.

{% hint style="info" %}
**참고: 프로젝트란 무엇인가요?**\
예를 들어, 모든 오픈 소스 라이브러리를 종속성으로 나열하는 매니페스트 파일과 같이 Snyk에서 스캔한 항목이 바로 Snyk 프로젝트입니다. [Snyk Projects](../../snyk-admin/snyk-projects/)를 참조하세요.
{% endhint %}

다음은 예시입니다:

<figure><img src="../../.gitbook/assets/image (180) (1) (1) (1) (1) (1) (1).png" alt="List of scanned Projects"><figcaption><p>스캔한 프로젝트 목록</p></figcaption></figure>

## 프로젝트 정보 이해

### 여기에 여러 항목이 있는 이유는 무엇인가요? 무슨 뜻인가요? 어떤 것을 사용해야 하나요?

Snyk 프로젝트를 처음 가져오면 많은 정보가 표시됩니다. 정보를 살펴보면서 사용 방법을 알 수 있습니다.

애플리케이션을 작성할 때 직접 코드를 작성하고, 종속성이 있는 오픈 소스 라이브러리를 가져오고, 배포를 위해 이 모든 것을 컨테이너에 빌드할 수 있습니다.

Snyk은 이 라이프사이클의 여러 부분을 검사하며, 각 작업의 각 부분에 대한 결과를 다른 아이콘과 항목으로 표시합니다:

| 예                                                                                               | 설명                                                                                                                                                                       |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <img src="../../.gitbook/assets/image (297) (1).png" alt="" data-size="line">                   | [Snyk Code](../../scan-with-snyk/snyk-code/)가 스캔한 나만의 코드 분석 결과.                                                                                                          |
| <img src="../../.gitbook/assets/Screenshot 2022-07-20 at 11.14.02.png" alt="" data-size="line"> | [Snyk Open Source](../../scan-with-snyk/snyk-open-source/)에서 스캔한 오픈 소스 라이브러리와 이러한 라이브러리에 대한 **pom.xml**, **package.json** 및 기타 매니페스트와 같이 감지된 각 매니페스트의 결과 표시를 확인할 수 있습니다. |
| <img src="../../.gitbook/assets/image (307) (1).png" alt="" data-size="line">                   | 컨테이너에 빌드된 항목(예: Docker 파일)에 대해 [Snyk Container](../../scan-with-snyk/snyk-container/)에서 스캔한 컨테이너 결과입니다.                                                                  |
| <img src="../../.gitbook/assets/image (206) (1) (1).png" alt="" data-size="original">           | [Snyk Infrastructure코드화(IaC)](../../scan-with-snyk/scan-infrastructure/scan-your-iac-source-code/)하여 스캔한 Kubernetes 배포 파일, Terraform 및 기타 IaC 파일.                        |

{% hint style="info" %}
다른 파일 및 유형이 표시될 수 있습니다. 자세한 내용은 [프로젝트 정보 보기](../../snyk-admin/snyk-projects/view-project-information.md)를 참조하세요.
{% endhint %}

### 프로젝트 설정 보기

Snyk은 이 목록의 각 항목을 별도의 **프로젝트**로 취급합니다.

따라서 톱니바퀴 아이콘을 클릭하여 해당 프로젝트의 설정을 제어하여 해당 프로젝트의 스캔 방식을 정의할 수 있습니다:

<figure><img src="../../.gitbook/assets/image (208) (1) (1) (1) (1) (1) (1) (1).png" alt="Click cog icon to edit settings"><figcaption><p>Click cog icon to edit Project settings</p></figcaption></figure>

예를 들어, 스캔 빈도를 변경하여 기본적으로 스캔이 실행되는 빈도를 설정할 수 있습니다. 자세한 내용은 [프로젝트 설정 보기](https://docs.snyk.io/introducing-snyk/introduction-to-snyk-projects/view-project-settings)를 참조하세요.

### 스캔 결과

스캔 결과를 다시 살펴보세요:

<figure><img src="../../.gitbook/assets/image (167) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="Project scan results"><figcaption><p>프로젝트 스캔 결과</p></figcaption></figure>

이 검사는 애플리케이션의 모든 측면에 있는 모든 취약점을 보여줍니다. 물론 이 목록의 모든 항목에 대해 책임이 있는 것은 아니지만 전체 상황을 파악하는 것이 중요합니다.

Snyk 오픈 소스 검사에서 오픈 소스 라이브러리에 취약점이 발견되지 않았다면 다행이지만 컨테이너와 같은 다른 검사에서 여전히 많은 문제가 있을 수 있습니다. 팀의 개발자가 이러한 문제를 만들거나 관리하지 않았더라도 이러한 문제에 대해 알고 있어야 합니다.

## 자세한 정보 및 다음 단계

오픈 소스, 코드, 컨테이너 및 인프라 파일 스캔의 결과를 검토하는 방법에 대해 자세히 알아보려면 [Snyk UI 소개](https://learn.snyk.io/lesson/intro-to-snyk-ui/) 과정을 참조하세요.

이제 결과를 이해했다면 [취약점 자체를 이해](understand-your-vulnerabilities.md)해야 합니다.
