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

## Access more vulnerability information

Snyk provides detailed resources for more information about vulnerabilities, accessible directly from the card:

* [**Snyk Vulnerability Database**](../../scan-with-snyk/snyk-open-source/manage-vulnerabilities/snyk-vulnerability-database.md): access details on a specific vulnerability.
* [**Snyk Learn**](../../getting-started/snyk-learn.md): access general information about that type of vulnerability.

### Access Snyk Vulnerability Database

For Open Source and Container vulnerabilities, click on the Snyk vulnerability Identifier (on the right of the Severity Level) to access detailed [Snyk Vulnerability Database](../../scan-with-snyk/snyk-open-source/manage-vulnerabilities/snyk-vulnerability-database.md) information for that vulnerability, as defined by Snyk. For example:

<figure><img src="../../.gitbook/assets/image (174) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (1).png" alt="Access Snyk Vulnerability Database"><figcaption><p>Access Snyk Vulnerability Database</p></figcaption></figure>

For this example, click on the Snyk vulnerability Identifier to see how Hibernate core and its libraries are vulnerable to SQL injection:

<figure><img src="../../.gitbook/assets/image (149) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (2).png" alt="Snyk Vulnerability Database example entry"><figcaption><p>Snyk Vulnerability Database example entry</p></figcaption></figure>

{% hint style="info" %}
[Snyk Code](../../scan-with-snyk/snyk-code/) and [Snyk IaC](../../scan-with-snyk/scan-infrastructure/scan-your-iac-source-code/) issue cards have separate information sets for these areas.
{% endhint %}

### Access Snyk Learn

Click **Learn about this type of vulnerability** to access [Snyk Learn](https://learn.snyk.io/) security educational materials:

<figure><img src="../../.gitbook/assets/image (119) (1).png" alt="Access Snyk Learn from a vulnerability card"><figcaption><p>Access Snyk Learn from a vulnerability card</p></figcaption></figure>

For example, see [Snyk Learn SQL injection](https://learn.snyk.io/lessons/sql-injection/javascript/) for more details about this type of vulnerability.

{% hint style="info" %}
Some cards may not have Snyk Learn lessons available - if so, no links are presented..
{% endhint %}

## Understand the Snyk Priority Score

The [Snyk Priority Score](../../scan-with-snyk/find-and-manage-priority-issues/priority-score.md), ranging from 0 - 1,000, is our evaluation of the seriousness of the vulnerability. The Snyk Priority Score includes [CVSS](https://www.first.org/cvss/calculator/3.1) (Common Vulnerability Scoring System) information, plus other factors such as attack complexity and known exploits. For example, this **Hibernate** vulnerability has no known exploit allowing attackers to take advantage of that vulnerability.

Other factors also affect the score. For example, SQL injections are easy to run (you just need a web browser and submit a form), so increasing the score, but it takes more work to understand and exploit the results for that attack, so decreasing the score.

## Open source vulnerabilities: fixes and dependency information

For open-source library scans by Snyk Open Source, you can also access fix and dependency information in the **Fixes** and **Dependencies** tabs of your Project results.

### Fixes tab

Snyk's knowledge of the transitive dependencies in your project make it possible for Snyk to offer fix advice, in the **Fixes** tab:

<figure><img src="../../.gitbook/assets/Screenshot 2021-10-19 at 11.57.07.png" alt="Fix advice for Open Source vulnerabilities"><figcaption><p>Fix advice for Open Source vulnerabilities</p></figcaption></figure>

See [Fix your first vulnerability](fix-your-first-vulnerability.md) for more details.

### Dependencies tab

Snyk uses the package manager of your application to build the dependency tree and display it in the **Dependencies** tab of the Project view:

<figure><img src="../../.gitbook/assets/image (119) (1) (1).png" alt="Dependencies for Open Source vulnerabilities"><figcaption><p>Dependencies for Open Source vulnerabilities</p></figcaption></figure>

Click the file tree icon (![](<../../.gitbook/assets/image (201) (1) (1) (1) (1) (1) (1) (2).png>)) to build the dependency tree, showing which components introduce a vulnerability. This helps you understand how the dependency was introduced to the application:

<figure><img src="../../.gitbook/assets/image23 (1) (1).png" alt="Dependency tree details"><figcaption><p>Dependency tree details</p></figcaption></figure>

For example, the above screenshot shows a vulnerability based on the transitive dependency **qs@2.2.4**, brought in from the direct dependency **body-parser@ 1.9.0**.

Now you understand your vulnerability information, you can decide how to fix it.

Continue with [Fix your first vulnerability](fix-your-first-vulnerability.md).
