# 프로젝트 가져오기

구성한 연동 기능과 기술 스택의 언어 및 패키지 관리자에 따라 다음을 사용하여 프로젝트를 Snyk으로 가져올 수 있습니다:

* Git 리포지토리와 소스 제어 통합.
* CI/CD가 포함된 Snyk CLI.

가장 적합한 가져오기 경로는 기술 스택의 언어와 패키지 관리자에 따라 달라집니다.

음은 최적의 시작점을 결정하기 위한 몇 가지 핵심 사항입니다. 자세한 내용은 [Git 리포지토리 및 CI/CD 비교](../../../integrate-with-snyk/git-repository-and-ci-cd-integrations-comparisons.md)를 참조하세요.

## Snyk을 시작하는 방법

{% hint style="info" %}
자세한 내용은 [시작하기](../../../getting-started/) 섹션과 [CLI, Web UI 또는 AP를 사용하여 스캔 시작하기](../../../scan-with-snyk/start-scanning-using-the-cli-web-ui-or-api.md)를 참조하세요.
{% endhint %}

여기에 설명된 대로 Snyk은 사용자의 요구 사항을 충족하는 다양한 통합 방법을 제공합니다.

### Git 통합

자동 스캔을 위해 리포지토리를 연결할 수 있습니다. 자세한 내용은 [Git  리포지토리(SCMs)와 Snyk의 통합](../../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/)을 참조하세요.

일반적으로 100개 미만의 적은 수의 애플리케이션의 경우 다음 단계를 따르세요.

1. **설정(Settings)**&#xC73C;로 이동한 다음 **연동(Integrations)**&#xC73C;로 이동하고 연동 페이지의 타일을 사용하여 Git 코드 리포지토리에 연결합니다.
2. 연동 설정에서
   * 프로젝트를 처음 온보딩할 때 자동 수정 및 PR/병합 확인을 비활성화합니다.
   * 안정 상태에 도달하여 차단을 원하는 경우 활성화합니다.
3. 프로젝트 목록에서 웹 UI를 사용하여 프로젝트를 추가합니다.
4. Git 코드 리포지토리에서 결과를 모니터링합니다.

수백 또는 수천 개의 리포지토리의 경우, [Snyk API v1 Import targets endpointI](https://snyk.docs.apiary.io/#reference/import-projects/import/import-targets) 를 사용하여 프로젝트를 가져올 수 있습니다. 이는 기존 소스 제어 통합을 활용하며 프로세스를 자동화하는 데 사용할 수 있습니다.

[snyk-api-import](../../../snyk-api-info/other-tools/tool-snyk-api-import/) 도구는 API를 사용하여 대규모 기업에서 대규모로 온보딩을 관리하기 위한 도구로, 대규모로 사용하도록 권장되는 도구입니다. snyk-api-import 도구를 사용할 때는 소스 제어 구조를 미러링해야 합니다.

### Snyk CLI

[Snyk CLI](../../../snyk-cli/)를 사용하면 개별 프로젝트를 세밀하게 스캔할 수 있습니다.

{% hint style="info" %}
오픈 소스, 코드, 코드형 인프라, 컨테이너 테스트 등 수행할 각 테스트 유형에 대한 명령을 공식화해야 합니다.
{% endhint %}

CLI를 사용하려면 다음 단계를 따르세요:

1. 빌드 스크립트의 일부로 적절한 방법 중 하나를 사용하여 [CLI를 설치합니다.](../../../snyk-cli/install-or-update-the-snyk-cli/)
2. 스크립트에서 프로젝트 폴더로 이동합니다.
3. 실행 중인 검사 유형에 적합한 옵션을 사용하여 적절한`snyk test` 또는`snyk monitor` 명령을 실행합니다.\
   스크립트에서 테스트를 구현하는 위치는 일반적으로 유연하지만 일반적으로 배포 전에 테스트를 수행합니다. 수동적으로 취약점을 보고하려면 Snyk 오픈 소스 및 Snyk 컨테이너에 대해 `monitor` 명령만 사용합니다. 테스트 명령과 함께 게이팅을 사용할 때는 `--severity-threshold`와 같은 특정 기준을 충족하는 문제가 발견되거나 CLI 또는 snyk-filter 플러그인의 여러 옵션을 충족하는 경우 빌드를 중단하는 것이 아이디어입니다.\
   \
   일반적으로 `test` 또는`monitor` 명령 또는 둘 다는 일반적으로 빌드 시스템에 종속성이 설치된 후 오픈 소스에 대해 실행됩니다.\
   \
   일반적인 명령은 다음 중 하나와 비슷할 수 있습니다:
   * 코드: `snyk code test --org=[org-id]`
   * 오픈 소스:
     * `snyk test --all-projects --org=[org-id]`
     * `snyk monitor --all-projects --org=[org-id]`
   * 이러한 유형의 프로젝트를 스캔하는 방법에 대한 자세한 내용은 [container](../../../snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-snyk-container/) 및 [infrastructure 코드](../../../snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-iac/) 스캔 설명서를 참조하세요.
4. `snyk test`를 실행할 때는 로컬에서, 모니터 또는 보고서 기능을 사용할 때는 웹 UI에서 결과를 검토합니다.

{% hint style="info" %}
다양한 파이프라인 통합 데모는 [Snyk-Labs](https://github.com/snyk-labs/snyk-cicd-integration-examples)에서 확인할 수 있습니다.
{% endhint %}

## Snyk API

[Snyk API](../../../snyk-api/)를 사용하여 스캔할 수 있습니다. 이를 통해 대규모 자동 스캔이 가능합니다.

그 과정은 다음과 같습니다:

1. **설정(Settings)** 및 **서비스 계정(Service Accounts)**&#xC73C;로 이동하여 API 토큰을 생성합니다.
2. 파이프라인에서 Snyk API를 호출합니다.
3. 결과를 프로그래밍 방식으로 처리합니다.
4. 필요한 경우 코드를 변경합니다.

API를 사용하여 스캔하면 다음과 같은 작업을 수행하는 데 유용합니다:

* 파이프라인을 통해 스캔을 트리거하세요.
* 프로젝트 포트폴리오 전반으로 확장하세요.
* 새로운 이슈를 실시간으로 파악하세요.
