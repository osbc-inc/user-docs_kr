# 프로젝트 가져오기

{% hint style="info" %}
**요약**\
[Snyk 계정을  생성](create-or-log-in-to-a-snyk-account.md)하고 [소스 코드(Git) 저장소와 통합하여](set-up-an-integration.md) 스캔을 위해 코드에 액세스할 수 있도록 했습니다. 이제 검사를 실행할 수 있습니다.
{% endhint %}

**Snyk 프로젝트**는 Snyk가 문제를 검색하는 항목입니다(예: 오픈 소스 종속성을 나열하는 매니페스트 파일).

프로젝트를 가져올 때, Snyk는 가져온 프로젝트를 스캔하고, 사용자가 검토할 수 있도록 결과를 표시합니다.

다음 비디오는 Snyk 프로젝트를 가져오는 방법을 보여줍니다.

{% embed url="https://thoughtindustries-1.wistia.com/medias/9hwr0bnvko" %}
Snyk 웹 UI를 통해 프로젝트 가져오기에 대한 비디오 데모
{% endembed %}

프로젝트를 가져오는 단계는 다음과 같습니다.

* **프로젝트(Projects) > 프로젝트 추가(Add Project)**를 선택하고 프로젝트를 가져올 위치를 선택합니다. 예를 들어, **GitHub를 선택하여** GitHub 리포지토리에서 가져오거나 **CLI를 선택하여**  [Snyk CLI](../../snyk-cli/) 를 로컬로 사용합니다.

<div align="left">

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-20 at 15.23.55.png" alt="Add Project choices"><figcaption><p>Add Project choices</p></figcaption></figure>

</div>

* 사용할 저장소를 선택하십시오. 그런 다음 **선택한 저장소 추가(Add selected repositories)**를 클릭하여 선택한 저장소를 프로젝트로 가져옵니다. \
  가져오는 프로젝트에 대한 선택적 설정을 선택할 수 있습니다. **사용자 정의 파일 위치 추가**(**Add custom file location)** 및 **폴더 제외(Exclude folders)**는 Snyk Open Source 및 Snyk Container에서만 지원됩니다. 자세한 내용은Azure 리포지토리 통합 설명서에서 [Adding custom file locations and excluding folders](https://docs.snyk.io/integrations/git-repository-scm-integrations/snyk-azure-repositories-tfs-integration#adding-custom-file-locations-and-excluding-folders) 를 참조하세요.

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-20 at 15.20.49.png" alt="Select GitHub repositories to import"><figcaption><p>가져올 GitHub 저장소를 선택하세요.</p></figcaption></figure>

{% hint style="info" %}
가져오기 위해 선택한 프로젝트는 다음과 같이 표시됩니다.  ![Check mark in check box](<../../.gitbook/assets/image (7) (2).png>)\
이전에 가져온 프로젝트는 다음과 같이 표시됩니다.  ✔\
개인 저장소는 다음과 같이 표시됩니다. ![Padlock](<../../.gitbook/assets/Screenshot 2023-05-11 at 23.05.30.png>)\
포크된 저장소는 다음과 같이 표시됩니다. ![Fork symbol](<../../.gitbook/assets/Screenshot 2023-05-11 at 23.15.46.png>)
{% endhint %}

## 프로젝트 가져오기 설정

**설정(Settings)**에서 선택적으로 다음을 선택합니다.

* 사용자 정의 경로에서 추가 종속성을 추가하려면, **사용자 정의 파일 위치(Add custom file location)를 추가하세요.**
* 예를 들어 검색 시간을 단축하기 위해 가져오는 동안 검색에서 제외할 폴더를 최대 10개까지 나열하려면 **폴더를 제외하세요**. 각 폴더 이름은 100자를 초과할 수 없습니다. 이 기능은 Snyk Open Source 및 Snyk Container에서 지원됩니다.

## 가져오기 진행 상황

가져오는 동안 진행률 표시줄이 나타납니다. 로그 결과를 보려면 **마지막 가져오기 로그 보기(View last import log)** 를 선택합니다.

<figure><img src="../../.gitbook/assets/Screenshot 2023-01-23 at 13.23.59.png" alt="Import Projects progress and option to view import log"><figcaption><p><strong>Import Projects progress and option to view import log</strong></p></figcaption></figure>

가져오는 동안, Snyk는 전체 디렉터리 트리에서 종속성을 나열하는 `package.json` 파일과 같은 관련 파일에 대해 선택한 저장소를 검색하기 시작하고, 이러한 파일을 Snyk 프로젝트로 가져옵니다.

## 결과 가져오기

상태 메시지와 함께 프로젝트 가져오기가 완료됩니다.

<figure><img src="../../.gitbook/assets/Screenshot 2023-01-23 at 13.24.35.png" alt="Project import success message"><figcaption><p>프로젝트 가져오기 성공 메시지</p></figcaption></figure>

이제 선택한 프로젝트를 성공적으로 가져오고 스캔했습니다.

{% hint style="success" %}
가져오는 동안 오류가 발생하면, [Project import errors](https://support.snyk.io/hc/en-us/articles/360001373118)를 참조하세요.
{% endhint %}

## 프로젝트 가져오기의 추가 이점

프로젝트 가져오기는 다음 작업도 수행합니다.

* 해당 프로젝트에서 문제를 정기적으로 검사하도록 Snyk를 설정합니다. 기본값은 [Test frequency settings](../../snyk-admin/manage-settings/usage-settings.md#test-frequency-settings) 을 참조하세요.
* 일부 자동화, 특히 풀 및 병합 요청에 대한 기본 Snyk 테스트를 시작하여 취약점이 프로젝트에 추가되는 것을 방지합니다. 이 자동화는 조건에 따라 빌드에 실패하며 [Snyk와  SCM(Git Repository) 통합](../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/)에서 비활성화하거나 사용자 정의할 수 있습니다.

{% hint style="info" %}
자동화 사용 모범 사례에 대한 교육을 받으려면, Snyk 과정 [Source Code Manager Configurations](https://learn.snyk.io/lesson/configure-snyk-scm/)을 방문하세요.
{% endhint %}

## 다음은 무엇인가?

이제 [Snyk 스캔 결과를 확인](view-snyk-scan-results.md) 수 있습니다.
