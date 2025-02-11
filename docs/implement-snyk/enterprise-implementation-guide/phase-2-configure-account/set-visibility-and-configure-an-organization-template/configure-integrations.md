# 통합 구성

## SDLC 통합 지점(IDE, Git 저장소, CI/CD, 컨테이너 레지스트리)을 구성하세요.

{% hint style="info" %}
프로젝트 가져오기에 대한 자세한 내용은 [Import Projects](../../phase-3-gain-visibility/import-projects.md) 및 [Rollout](../../phase-5-initial-rollout-to-team/)을 참조하세요.
{% endhint %}

조직을 만들 때 소프트웨어 개발 수명 주기(SDLC)에서 Snyk를 추가할 위치를 결정해야 합니다.

Snyk은 처음에는 게이팅과 관련된 기능을 비활성화한 상태에서 취약점에 대한 가시성을 확보할 것을 권장합니다.

첫 번째 단계는 사용 가능한 방법 중 하나를 사용하여 프로젝트를 임포트한 다음, 기존 이슈와 취약점을 완전히 파악한 후 코드베이스에 새로운 이슈가 추가되는 것을 방지하기 위해 게이팅 방법을 점진적으로 도입할 수 있습니다.

{% hint style="info" %}
**알림 설정(이메일 알림)**

* 프로젝트를 가져오는 동안 사용자가 많은 알림을 받지 않도록 처음에는 모든 이메일 알림을 비활성화하는 것이 좋습니다.
* 새 조직의 경우 그룹 수준에서, 모든 기존 조직의 경우 조직 수준에서 이 기능을 비활성화할 수 있습니다.
{% endhint %}

## 통합 도구

가시성을 확보하기 위해 Snyk을 SDLC에 통합하는 가장 일반적인 도구는 여기에 설명되어 있습니다.

### Git 리포지토리

Snyk은 여러 Git 리포지토리와 통합하여 코드의 문제와 취약점을 추적, 모니터링 및 수정할 수 있습니다. 리포지토리를 가져올 때 Snyk은 기본 브랜치에 취약점이 있는지 스캔하고 모니터링합니다.

모니터링은 다음과 같은 형태로 이루어집니다.

* 작업하지 않을 때에도 지정된 브랜치를 매일 스캔할 수 있습니다,
* 풀 리퀘스트 및 병합 검사

Git 리포지토리의 소스 제어 스캔은 지원되는 대부분의 언어에 적합하지만, Artifactory와 같은 비공개 패키지 관리자를 사용하는 경우 비공개 패키지를 스캔하려면 Snyk과 통합해야 합니다.

Git 리포지토리 통합을 통한 프로젝트 가져오기는 브라우저를 통해 수동으로 수행할 수도 있고, API를 활용하여 [snyk-api-import](../../../../snyk-api-info/other-tools/tool-snyk-api-import/) 도구를 사용하여 리포지토리를 대량으로 가져오거나 [Import Targets](https://snyk.docs.apiary.io/#reference/import-projects/import/import-targets) API v1 엔드포인트를 사용하여 특정 리포지토리를 가져와서 파이프라인에 삽입할 수 있습니다.

{% hint style="info" %}
Snyk 엔터프라이즈 고객의 경우, Snyk 통합 페이지에서 **GitHub Enterprise 통합 카드**를 사용할 것을 강력히 권장합니다. 이 옵션을 사용하기 위해 GitHub Enterprise 고객이 아니어도 되지만, 이 옵션을 사용하면 개인 액세스 토큰(PAT)을 사용할 수 있는 반면, GitHub 통합 카드를 통해 제공되는 OAUTH는 인터페이스에서 액세스 측면에서 일관되지 않은 경험을 제공합니다.
{% endhint %}

Git 리포지토리에서 프로젝트를 가져오면 Snyk [PR Checks](../../../../scan-with-snyk/run-pr-checks/) 및 PR 자동 수정 기능을 구성할 수도 있습니다. 이 기능을 사용하면 Git 리포지토리에 PR을 제출할 때마다 코드 변경 사항을 실시간으로 자동으로 스캔하여 새로운 보안 문제가 코드베이스에 유입되는 것을 방지할 수 있습니다.

이를 통해 제출된 모든 PR에 보안 문제가 있는지 확인하여 소프트웨어 개발 수명 주기 초기에 스캔하고 가시성을 확보할 수 있습니다.

{% hint style="info" %}
게이팅을 처음에 비활성화하려면 Snyk에서 프로젝트가 온보딩될 때 자동으로 구성되는 일일 모니터링을 사용하고 구성에서 PR/MR 확인을 비활성화하세요.

* Snyk이 제공할 수 있는 자동 수정
  * 자동 수정 PR
  * 자동 종속성 업그레이드 PR
  * Snyk 취약점 패치
* PR 점검을 사용할 수 있는 대상
  * 오픈 소스 보안 및 라이선스
  * 코드 분석(베타)
{% endhint %}

마찬가지로 PR 기능을 수정 및 업그레이드하지 않도록 설정할 수 있습니다.

### CI/CD (빌드 파이프라인)

파이프라인의 한 단계로 빌드에 Snyk를 추가하여 취약한 애플리케이션 또는 구성 요소(레지스트리)의 배포를 방지하여 애플리케이션의 보안을 유지하세요.

CLI는 다음을 제공합니다.

* Scala, Gradle, GO 등 여러 특정 패키지 관리자에 대한 최적의 정확도 지원
* 빌드 환경에서 비공개 패키지에 액세스할 수 있으므로 추가 통합을 구성할 필요 없이 비공개 패키지를 지원합니다.
* 빌드를 중단하고 Snyk에 보고하거나 Snyk에 보고하는 것만으로 프로덕션에 푸시되는 컴포넌트에 대한 가시성.

사용할 수 있는 여러 가지 [CI/CD 통합](../../../../integrate-with-snyk/snyk-ci-cd-integrations/)이 있으며, 파이프라인의 일부로 [Snyk CLI](../../../../snyk-cli/)를 사용하여 실행 중인 테스트에 유연성을 더할 수 있습니다.

이미 소스 제어 통합을 사용하여 리포지토리를 가져오지 않는 한, 초기 단계에서는 `monitor`기능을 사용하여 발견된 이슈를 확인할 수 있도록 Snyk로 정보를 가져오는 것이 좋습니다. 나중에 새로운 취약점이 추가되는 것을 차단하고 게이팅을 시작하려는 경우 `test` 기능을 도입하여 처음에는 중요한 이슈에 대해 빌드를 실패시킨 다음 시간이 지남에 따라 실패 기준을 점진적으로 조정할 수 있습니다.

{% hint style="info" %}
`snyk iac test --report` 및 `snyk code test --report` (베타)의 경우 문제를 발견하면 응답 코드가 0이 아닌 상태로 빌드가 중지될 수 있습니다.\
\
이를 수동적으로 테스트하려면 `--report` 옵션을 포함하여 빌드 단계를 항상 계속하도록 설정하거나 다음과 같거나 `or true`인 로직을 연결하는 것과 같은 대안, 즉 `snyk code test --report || true.` 를 사용해야 합니다. 정확한 구문은 CLI가 실행 중인 에코시스템에 따라 달라집니다.
{% endhint %}

고급 필터링을 위한 [Snyk Filter](https://docs.snyk.io/snyk-api/other-tools/tool-snyk-filter)와 새로운 이슈를 강조하기 위한 [Snyk Delta](https://docs.snyk.io/snyk-api/other-tools/tool-snyk-delta)와 같은 플러그인은 파이프라인 구성에 매우 인기가 있습니다.

다양한 파이프라인 통합에 대한 데모는 [Snyk-Labs](https://github.com/snyk-labs/snyk-cicd-integration-examples)에서 확인할 수 있습니다.
