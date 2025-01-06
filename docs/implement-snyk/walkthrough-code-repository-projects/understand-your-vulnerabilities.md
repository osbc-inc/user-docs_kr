# 취약점 파악

{% hint style="info" %}
**요약**\
[스캔된 프로젝트를 보고 이해했으니](view-your-first-snyk-projects.md) 이제 해당 프로젝트의 취약점에 대한 세부 정보를 살펴볼 수 있습니다.
{% endhint %}

## 취약점 세부 정보 보기

먼저 대상을 열어 Snyk 프로젝트를 확인합니다:

<figure><img src="../../.gitbook/assets/image (354).png" alt="View imported Projects"><figcaption><p>가져온 프로젝트 보기</p></figcaption></figure>

그런 다음 해당 목록에서 프로젝트를 선택하면 해당 프로젝트에서 발견된 취약점에 대한 세부 정보를 볼 수 있습니다.

예를 들어 Snyk Code로 스캔한 **코드 분석** 프로젝트를 예로 들어 보겠습니다:

<figure><img src="../../.gitbook/assets/image (149) (1) (1) (2).png" alt="Vulnerability example - Code analysis"><figcaption><p>Vulner취약점 예시 - 코드 분석</p></figcaption></figure>

자세한 내용은 [프로젝트 정보 보기](../../snyk-admin/snyk-projects/view-project-information.md)를 참조하세요.

## 발급 카드 보기

이제 이슈 카드에서 제공되는 각 Snyk 프로젝트에 대한 취약점 정보를 살펴보세요:

<figure><img src="../../.gitbook/assets/image (101) (2).png" alt="Vulnerability details Issue Card"><figcaption><p>취약점 세부 정보 이슈 카드</p></figcaption></figure>

다시 말하지만, 이해해야 할 정보가 많으므로 시간을 들여 이 모든 정보가 취약성과 어떤 관련이 있는지 이해하여 어떤 수정 조치를 취할지 결정하세요.

자세한 내용은 [카드 정보 발급하기](../../snyk-admin/snyk-projects/issue-card-information.md)를 참조하세요.

## 더 많은 취약성 정보에 액세스

Snyk은 카드에서 바로 액세스할 수 있는 취약점에 대한 자세한 리소스를 제공합니다:

* [**Snyk Vulnerability Database**](../../scan-with-snyk/snyk-open-source/manage-vulnerabilities/snyk-vulnerability-database.md): 특정 취약점에 대한 세부 정보에 액세스합니다.
* [**Snyk Learn**](../../getting-started/snyk-learn.md): 해당 취약점 유형에 대한 일반 정보에 액세스합니다.

### Snyk 취약점 데이터베이스에 액세스

오픈 소스 및 컨테이너 취약점의 경우 심각도 레벨 오른쪽에 있는 Snyk 취약점 식별자를 클릭하면 Snyk에서 정의한 해당 취약점에 대한 자세한 [Snyk Vulnerability Database](../../scan-with-snyk/snyk-open-source/manage-vulnerabilities/snyk-vulnerability-database.md) 정보에 액세스할 수 있습니다. 예를 들어:

<figure><img src="../../.gitbook/assets/image (174) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (1).png" alt="Access Snyk Vulnerability Database"><figcaption><p>Snyk 취약점 데이터베이스에 액세스</p></figcaption></figure>

이 예제에서는 Snyk 취약점 식별자를 클릭하여 Hibernate 코어와 해당 라이브러리가 SQL 인젝션에 어떻게 취약한지 확인합니다:

<figure><img src="../../.gitbook/assets/image (149) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (2).png" alt="Snyk Vulnerability Database example entry"><figcaption><p>Snyk 취약점 데이터베이스 예제 항목</p></figcaption></figure>

{% hint style="info" %}
[Snyk Code](../../scan-with-snyk/snyk-code/) 및 [Snyk IaC](../../scan-with-snyk/scan-infrastructure/scan-your-iac-source-code/) 발급 카드에는 이러한 영역에 대한 별도의 정보 세트가 있습니다.
{% endhint %}

### Snyk Learn에 액세스

**이 유형의 취약점에 대해 자세히 알아보기**를 클릭하여 [Snyk Learn](https://learn.snyk.io/) 보안 교육 자료에 액세스합니다:

<figure><img src="../../.gitbook/assets/image (119) (1).png" alt="Access Snyk Learn from a vulnerability card"><figcaption><p>취약점 카드에서 Snyk Learn에 액세스하기</p></figcaption></figure>

이 유형의 취약점에 대한 자세한 내용은 [Snyk Learn SQL injection](https://learn.snyk.io/lessons/sql-injection/javascript/)을 참조하십시오.

{% hint style="info" %}
일부 카드에는 Snyk Learn 강의가 없을 수 있으며, 이 경우 링크가 표시되지 않습니다.
{% endhint %}

## Snyk 우선순위 점수 이해하기

0\~1,000점 범위의 [Snyk 우선순위 점수](../../scan-with-snyk/find-and-manage-priority-issues/priority-score.md)는 취약점의 심각성에 대한 평가입니다. Snyk 우선순위 점수에는 [CVSS](https://www.first.org/cvss/calculator/3.1) (공통 취약점 점수 시스템) 정보와 공격 복잡성 및 알려진 익스플로잇과 같은 기타 요소가 포함됩니다. 예를 들어, 이 **최대 절전 모드** 취약점은 공격자가 해당 취약점을 악용할 수 있는 알려진 익스플로잇이 없습니다.

다른 요인도 점수에 영향을 미칩니다. 예를 들어 SQL 인젝션은 실행하기 쉬우므로(웹 브라우저와 양식 제출만 있으면 됩니다) 점수가 높아지지만, 해당 공격의 결과를 이해하고 악용하는 데 더 많은 작업이 필요하므로 점수가 낮아집니다.

## 오픈 소스 취약점: 수정 및 종속성 정보

Snyk 오픈 소스로 오픈 소스 라이브러리를 스캔한 경우 프로젝트 결과의 수정 사항 및 종속성 탭에서 **수정 사항** 및 **종속성** 정보에 액세스할 수도 있습니다.

### 수정 탭

프로젝트의 전이적 종속성에 대한 지식이 있으면 **수정** 탭에서 Snyk이 수정 조언을 제공할 수 있습니다:

<figure><img src="../../.gitbook/assets/Screenshot 2021-10-19 at 11.57.07.png" alt="Fix advice for Open Source vulnerabilities"><figcaption><p>오픈 소스 취약점에 대한 수정 조언erabilities</p></figcaption></figure>

자세한 내용은 [첫 번째 취약점 수정](fix-your-first-vulnerability.md)을 참조하세요.

### 종속성 탭

Snyk은 애플리케이션의 패키지 관리자를 사용하여 종속성 트리를 빌드하고 프로젝트 보기의 **종속성** 탭에 표시합니다:

<figure><img src="../../.gitbook/assets/image (119) (1) (1).png" alt="Dependencies for Open Source vulnerabilities"><figcaption><p>오픈 소스 취약점에 대한 종속성</p></figcaption></figure>

파일 트리 아이콘 (![](<../../.gitbook/assets/image (201) (1) (1) (1) (1) (1) (1) (2).png>)) 을 클릭하여 종속성 트리를 작성하여 어떤 구성 요소가 취약성을 도입했는지 표시합니다. 이를 통해 종속성이 애플리케이션에 어떻게 도입되었는지 이해하는 데 도움이 됩니다:

<figure><img src="../../.gitbook/assets/image23 (1) (1).png" alt="Dependency tree details"><figcaption><p>종속성 트리 세부 정보</p></figcaption></figure>

예를 들어, 위의 스크린샷은 직접 종속성 **body-parser@ 1.9.0**에서 가져온 전이 종속성(**qs@2.2.4**)에 기반한 취약점을 보여줍니다.

이제 취약점 정보를 이해했으니 취약점을 어떻게 수정할지 결정할 수 있습니다.

[첫 번째 취약점 수정](fix-your-first-vulnerability.md)을 계속 진행합니다.
