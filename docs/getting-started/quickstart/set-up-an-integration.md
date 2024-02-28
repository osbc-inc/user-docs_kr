# 통합 설정

{% hint style="info" %}
**요약**\
[Snyk 계정을 생성한 이후,](create-or-log-in-to-a-snyk-account.md)  Snyk에게 스캔할 위치를 알려주어야 합니다.
{% endhint %}

Snyk이 해당 환경을 스캔 하려면, Snyk에게 귀하의 환경에 대한 액세스 권한을 부여해야 합니다. 필요한 통합 유형은 사용하는 시스템과 스캔하려는 대상에 따라 다릅니다. 사용 가능한 통합자에 대한 자세한 내용은 [Snky 연동](../../integrate-with-snyk/)을 참조하세요.

이 통합을 설정할 수 있습니다.

* Snyk 계정을 만든 직후, [Following a guided process](set-up-an-integration.md#guided-process-after-signup)을 따릅니다.
* 언제든지 수동으로 가능합니다.

## 안내 과정(가입 후)

[Snyk 계정 생성](create-or-log-in-to-a-snyk-account.md) 직후, 시작 안내 메시지가 표시됩니다. Snyk이 귀하의 경험을 안내하는 데 도움이 되는 몇 가지 정보를 제공하도록 선택한 다음, 프롬프트에 따라 코드 저장소를 통합하여 원활한 경험을 할 수 있습니다.

예는 다음과 같습니다.

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-16 at 9.36.53 AM.png" alt="Choose integration method"><figcaption><p>통합 방법 선택</p></figcaption></figure>

선택한 통합에 대한 세부정보를 입력하세요. **GitHub**를 선택하는 경우 표시된 대로 세부사항을 입력하십시오.

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-16 at 9.37.34 AM.png" alt="Set access permissions"><figcaption><p>액세스 권한 설정</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-16 at 9.39.45 AM.png" alt="Configure automation settings &#x26; authenticate"><figcaption><p>자동화 설정 구성 및 인증</p></figcaption></figure>

{% hint style="info" %}
이 설정 단계에서는 Snyk GitHub 통합에 대해 Snyk Code가 기본적으로 활성화됩니다. 이 과정에서 활성화하지 않으려면, 나중에 조직 **설정**에서 활성화할 수 있습니다.
{% endhint %}

완료하려면, 스캔할 [프로젝트를 가져옵니다.](import-a-project.md)

<figure><img src="../../.gitbook/assets/image (248) (1).png" alt="Add your first project"><figcaption><p>첫 번째 프로젝트 추가</p></figcaption></figure>

소스 코드 저장소에 인증하지 않고 코드를 스캔하려는 경우에는CLI 통합을 선택할 수 있습니다. 이를 통해 로컬 컴퓨터에서 스캔을 실행하고 결과를 Snyk의 조직에 업로드할 수 있습니다.

GitHub, Bitbucket Cloud 및 CLI는 전용 타일로 표시되지만 **모든 통합 보기(View all integrations)** 링크를 통해 다른 많은 통합을 사용할 수 있습니다.

## 수동 프로세스(언제든지)

언제든지 Snyk에 통합을 수동으로 추가할 수 있습니다. 자세한 내용은 [Snyk 연동을](../../integrate-with-snyk/) 참조하세요.

Git 저장소 통합을 보여주는 예는 다음과 같습니다.

Git 기반 소스 코드 저장소에서 코드를 스캔하려면, Snyk를 [Git 저장소와 통합](../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/)해야 합니다. Snyk에는 GitHub, GitHub Enterprise, Bitbucket Cloud 및 기타 리포지토리에 대한 통합이 사전 구축되어 있습니다.

먼저 Snyk 웹 UI([app.snyk.io](https://app.snyk.io))에 로그인하고, **통합(Integrations) > 소스 제어(Source control)**를 선택합니다.

<div align="left">

<figure><img src="../../.gitbook/assets/Screenshot 2022-07-26 at 13.26.22.png" alt="Select Source control integrations"><figcaption><p>소스 제어 통합 선택</p></figcaption></figure>

</div>

{% hint style="info" %}
조직에 통합이 이미 구성되어 있으면 **구성됨(Configured)**으로 표시됩니다.
{% endhint %}

Snyk를 GitHub 리포지토리와 연결하려면 다음을 수행하세요.

1. Snyk에 공개 및 비공개 저장소 모두에 대한 액세스 권한을 부여할지 아니면 공개 저장소에만 액세스할 것인지 선택합니다.\
   GitHub 인증 화면이 열립니다.
2. GitHub 인증 화면에서, **Authorize Snyk**를 클릭하여 Snyk에 리포지토리에 대한 액세스 권한을 제공합니다.
3. 계정 자격 증명을 입력하고 메시지가 나타나면 세부 정보를 저장합니다.

자세한 내용은 [Snky와  SCM(Git Repository) 통합](../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/)을 참조하세요.&#x20;

## 다음은 무엇인가?

[Snyk 프로젝트를 가져온 후](import-a-project.md), Snyk에게 문제를 검색할 항목을 알려줄 수 있습니다.
