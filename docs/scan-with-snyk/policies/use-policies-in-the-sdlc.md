# SDLC의 정책 사용

개발자의 로컬 개발 환경, IDE 또는 CLI, Git 기반 워크플로 및 CI/CD, 프로덕션에 이르기까지 SDLC의 모든 단계에 걸쳐 정책을 적용할 수 있습니다.

이러한 다양한 보안 및 규정 준수 제어를 통해 문제를 해결하는 데 비용과 시간이 가장 적게 드는 개발 프로세스 초기에 문제를 파악할 수 있습니다.

{% hint style="info" %}
또한`.snyk`파일은 Snyk가 특정 분석 동작을 정의하고 CLI 및 CI/CD 플러그인에 대한 패치를 지정하는 데 사용하는 정책 파일입니다. 자세한 내용은[ .snyk 파일](the-.snyk-file.md)을 참조하세요.
{% endhint %}

## 프로젝트 또는 조직에 정책 할당

[보안 정책(security policies)](security-policies/) 과 [라이선스 정책(license policies)](license-policies/) 모두에 대해 프로젝트 속성 및 조직에 정책을 적용할 수 있습니다.이렇게 하면 프로젝트와 조직에 정책을 할당할 수 있습니다. 자세한 내용은[프로젝트에 정책(policies) 할당](assign-policies-to-projects.md) 및 [조직에 정책 할당하기](assign-a-policy-to-an-organization.md)를 참조하세요.

### 예: 프로젝트에 라이선스 정책 할당하기

시나리오: \
회사의 법무팀은 업무상 중요한 프런트엔드(front-end) 애플리케이션에 대해서는 엄격한 라이선스 규정 준수 제어를 요구하지만 내부 개발 프로젝트에 대해서는 덜 신경 쓰는 경우.

이 요구 사항을 충족하려면 먼저 이 정책을 적용하려는 Snyk 프로젝트에 `Critical`, `Production`, 및 `Frontend`속성을 추가하세요:&#x20;

<figure><img src="../../.gitbook/assets/image (1) (3).png" alt="Add relevant attributes to a Project from the Issues tab"><figcaption><p>Issues 탭에서 프로젝트에 관련 속성을 추가합니다.</p></figcaption></figure>

그런 다음, 새 라이선스 정책을 만들고 해당 속성에 정책을 적용합니다:

<figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt="Apply license policy to selected attributes"><figcaption><p>선택한 속성에 라이선스 정책 적용</p></figcaption></figure>

{% hint style="info" %}
정책 자체에서 [**GPL-3.0**](https://snyk.io/learn/what-is-gpl-license-gplv3-explained/) 및 [**AGPL-3.0 licenses**](https://snyk.io/learn/agpl-license/) 라이선스와 같이 프로젝트에서 식별되는 모든 copyleft 라이선스에 높은 심각도를 적용할 수 있습니다.\
라이선스 정책을 만들 때 Snyk는 테스트에 불합격하는 이유를 설명할 것을 권장합니다. 따라서 예를 들어 GPL 라이선스로 인해 빌드가 실패하는 경우 개발자는 설명을 볼 수 있으며 어떤 조치를 취해야 하는지 알 수 있습니다. 자세한 내용은 라이선스 정책 및 규칙 만들기를 참조하세요.
{% endhint %}

이제 이 정책은 선택한 속성이 적용된 모든 프로젝트에 할당되며 다음에 Snyk가 해당 프로젝트를 스캔할 때 적용됩니다.

자세한 내용은 [라이선스 정책(License policies)](license-policies/) 을 참조하세요.

### 예: 프로젝트에 보안 정책 할당하기

이전 예제와 유사한 프로세스를 사용하여 알려진 exploit이 없는`FrontEnd` 환경의 모든 `Medium`심각도 취약점을 자동으로 무시하도록 보안 정책을 정의할 수 있습니다:

<div align="left">

<figure><img src="../../.gitbook/assets/image (14) (3).png" alt="Snyk security policy - specify vulnerabilities to ignore"><figcaption><p>Snyk 보안 정책 - 무시할 취약점 지정</p></figcaption></figure>

</div>

이제 이 정책은 선택한 속성이 적용된 모든 프로젝트에 할당되며 다음에 Snyk이 해당 프로젝트를 스캔할 때 적용됩니다.

자세한 내용은 [보안 정책(Security policies)](security-policies/)을 참조하세요.

## GitHub 리포지토리에 정책 적용

Snyk이 모니터링하는 GitHub 프로젝트의 경우, 기여 개발자의 모든 새 pull request를 해당 프로젝트에 할당된 정책과 대조하여 확인할 수 있습니다. 이렇게 하면 정책을 위반하는 코드가 repository에 committ 될 수 없습니다.

{% hint style="info" %}
Snyk의 PR 확인 기능에 대한 자세한 내용은  [PR Checks](../run-pr-checks/)을 참조하세요.
{% endhint %}

다음은 JavaScript 패키지 라이선스에 대한 PR check의 예입니다.

이 예는 JavaScript 애플리케이션에 `fullpage.js` 패키지를 추가하는 pull request를 보여줍니다. 이 변경 사항은 보안 정책 검사를 통과하지만, 최신 버전의 패키지에는 알려진 취약점이 없기 때문에 라이선스 정책 검사에서는 GPLv3 라이선스가 회사의 라이선스 정책을 위반하여 포함되었으므로 라이선스 정책 검사에 실패합니다.

<figure><img src="../../.gitbook/assets/image (5) (1) (1) (2).png" alt="PR Check fails on license compliance"><figcaption><p>라이선스 준수에 대한 PR Check 실패</p></figcaption></figure>

## CI/CD에서 정책 적용

할당된 정책은 CI/CD에 적용되어 빌드가 보안 및 규정 준수 경계를 준수하도록 보장합니다.

다음은 워크플로우의 심각도가 높은 취약점에 대한 예시입니다.

이 예는 Snyk 테스트에서 확인된 심각도가 높은 취약점으로 인해 실패한 GitHub Action 빌드 워크플로우를 보여줍니다:

<figure><img src="../../.gitbook/assets/image (6) (4).png" alt="CI/CD check fails on security policy breach"><figcaption><p>보안 정책 위반에 대한 CI/CD check 실패</p></figcaption></figure>
