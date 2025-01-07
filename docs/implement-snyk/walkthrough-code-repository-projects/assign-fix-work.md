# 수정 작업 할당

{% hint style="info" %}
**요약**\
취약점을 파악하고 수정했습니다.
{% endhint %}

이 섹션에서는 팀 전체에서 애플리케이션에 대한 이 수정 프로세스가 어떻게 작동하는지에 대해 설명합니다.

* [먼저 수정할 항목 결정하기](assign-fix-work.md#decide-what-to-fix-first): 팀의 수정 우선 순위를 결정합니다.
* [수정 워크플로 결정](assign-fix-work.md#example-workflow-team-lead-driven-using-jira): 예를 들어 Jira 기반 프로세스를 사용합니다.

## 먼저 수정할 항목 결정

수정 우선순위는 워크플로와 비즈니스 프로세스에 따라 달라집니다. 팀마다 사용하는 도구, 워크플로 성숙도, 경쟁하는 업무 우선순위에 따라 수정에 접근하는 방식이 다릅니다.

일반적으로 소규모 팀일수록 프로세스가 적고 엔터프라이즈급 팀은 더 형식적입니다. 예를 들어, 팀의 개별 개발자가 케이스별로 수정할 이슈를 결정하거나 팀 리더가 스프린트 계획 프로세스의 일부로 수정 작업을 할당하는 등 보다 통제된 프로세스가 있을 수 있습니다.

### 분류 프로세스 예시

예를 들어, 팀에서는 주로 문제의 심각도에 따라 각 문제에 대해 분류 기반 프로세스를 따를 수 있습니다:

<figure><img src="../../.gitbook/assets/image (23) (2) (1).png" alt="Using a triage process for issues"><figcaption><p>문제 분류 프로세스 사용</p></figcaption></figure>

### 워크플로 예시: 팀 리더 주도, Jira 사용

{% hint style="info" %}
**기능 사용 가능성**\
Jira 통합은 모든 유료 플랜에서 사용할 수 있습니다. 자세한 내용은 [가격 플랜](https://snyk.io/plans/)을 참조하세요.
{% endhint %}

일부 팀은 모든 작업을 Jira 작업을 중심으로 진행하는데, 이를 예로 살펴보겠습니다.

개발팀이 스프린트를 기반으로 수정 작업을 할당하고 다음 개발 스프린트에서 취약점 수정 작업을 전담하기로 결정했다고 가정해 보겠습니다.

이 스프린트 계획의 일환으로 팀 리더는 다음과 같이 할 수 있습니다:

* 프로젝트의 취약점을 검토합니다.
* 수정할 취약점을 결정합니다.
* 각 취약점에 대해 Jira 이슈를 만듭니다.
* 이러한 취약점을 수정하기 위해 개발자에게 이러한 Jira 이슈를 작업으로 할당합니다.
* 스프린트 기간 동안 이러한 작업의 진행 상황을 추적합니다.

Snyk [Jira 통합](../../integrate-with-snyk/notification-and-ticketing-systems-integrations/jira-integration.md)을 통해 Snyk 웹 UI에서 이 프로세스를 실행할 수 있습니다.

### Jira 이슈 지정

수정하기로 결정한 이슈로 이동한 다음 **Jira 이슈 만들기**를 클릭합니다:

<figure><img src="../../.gitbook/assets/image (158) (1) (2).png" alt="Create a Jira issue"><figcaption><p>Jira 이슈 만들기</p></figcaption></figure>

그런 다음 이 수정 사항에 대한 Jira 작업 세부 정보를 정의할 수 있습니다:

<figure><img src="../../.gitbook/assets/image (483).png" alt="Create a Jira issue details"><figcaption><p>Jira 이슈 세부 정보 만들기</p></figcaption></figure>

팀의 일반적인 스프린트 프로세스에 따라 이 작업을 팀 내 개발자에게 할당할 수 있습니다.

{% hint style="info" %}
이슈를 지정하면 팀에서 코드 변경 사항을 관리, 정당화 및 추적할 수 있으므로 아주 사소한 업그레이드인 경우에도 Jira 이슈를 만들고 싶을 수 있습니다.
{% endhint %}

## 자세한 정보 및 다음 단계

작업 추적에 대한 자세한 내용은 [Jira issues](https://learn.snyk.io/lesson/jira-issue/)비디오를 참조하세요. 이슈의 전반적인 관리에 대한 자세한 내용은 문서에서 [위험 관리](../../manage-risk/)를 참조하세요.

다음으로 [Snyk 리포트를 사용하여 팀의 작업을 관리하는 방법](use-reports-in-managing-risk.md)을 살펴보세요.
