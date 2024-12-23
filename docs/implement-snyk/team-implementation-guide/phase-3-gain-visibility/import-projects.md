# 프로젝트 가져오기

구성한 통합 및 기술 스택의 언어/패키지 관리자에 따라 다음을 사용하여 프로젝트를 Snyk으로 가져올 수 있습니다:

* Git 리포지토리와 소스 제어 통합
* CI/CD가 포함된 Snyk CLI.

가장 좋은 가져오기 경로는 기술 스택의 언어와 패키지 관리자에 따라 다릅니다.

다음은 최적의 시작점을 결정하기 위한 몇 가지 핵심 사항입니다. 자세한 내용은 [Git 리포지토리 및 CI/CD 비교](../../../integrate-with-snyk/git-repository-and-ci-cd-integrations-comparisons.md)를 참조하세요.

## Snyk 시작하기

{% hint style="info" %}
자세한 내용은 [시작하기](../../../getting-started/) 및 [스캔 시작하기](../../../scan-with-snyk/start-scanning-using-the-cli-web-ui-or-api.md)를 참조하세요.
{% endhint %}

필요에 따라 Snyk은 다양한 통합 방법을 제공합니다:

### Git 통합

자세한 내용은 [Git 리포지토리(SCMs)와 Snyk 통합](../../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/)을 참조하세요.

자동 스캔을 위해 리포지토리를 연결하세요.

일반적으로 100개 미만의 적은 수의 애플리케이션에 적합합니다:

1. Snyk 웹 UI의 **설정(Settings)-연동(Integrations)** 페이지에서 Git 코드 리포지토리에 연결합니다.&#x20;
2. 통합 설정에서:
   1. 프로젝트를 처음 온보딩할 때 자동 수정 및 PR/병합 확인을 비활성화합니다.
   2. 안정 상태에 도달하고 차단을 원하면 활성화합니다..
3. **프로젝트(Projects)** 페이지에서 프로젝트를 추가합니다.
4. Git 코드 리포지토리에서 결과를 모니터링합니다.

수백, 수천 개의 리포지토리에 적용됩니다:

* 규모에 따라 Snyk은 API 사용을 권장합니다. API는 Snyk Enterprise 요금제에서 사용할 수 있습니다.
  * [Snyk API](../../../snyk-api/) 를 사용하여 프로젝트를 가져오세요. 이는 기존 소스 제어 통합을 활용하며 프로세스를 자동화하는 데 사용할 수 있습니다.
  * [snyk-api-import](../../../snyk-api-info/other-tools/tool-snyk-api-import/) 도구는 API를 사용하여 대규모 엔터프라이즈에서 대규모로 온보딩을 관리하며 대규모로 사용하도록 권장되는 도구입니다. 소스 제어 구조를 미러링해야 합니다.

## Snyk CLI

자세한 내용은 [Snyk CLI](../../../snyk-cli/)를 참조하세요.

CLI를 사용하면 개별 프로젝트를 세밀하게 스캔할 수 있습니다.

{% hint style="info" %}
수행할 각 테스트 유형(오픈 소스, 코드, 코드형 인프라, 컨테이너)에 대한 명령을 공식화해야 합니다.
{% endhint %}

Snyk CLI를 사용하려면:

1. 빌드 스크립트의 일부로 적절한 방법 중 하나를 사용하여 [CLI를 설치](https://docs.snyk.io/snyk-cli/install-or-update-the-snyk-cli)합니다.
2. 스크립트에서 프로젝트 폴더로 이동합니다.
3. 실행하려는 스캔 유형에 적합한 `snyk test` 또는`snyk monitor` 명령 및 옵션을 실행합니다.\
   \
   스크립트에서 테스트를 구현하는 위치는 일반적으로 유연하지만 일반적으로 배포 전에 구현하는 것이 가장 일반적입니다. 수동적으로 보고하려면 Snyk 오픈 소스 및 Snyk 컨테이너의 경우 모니터 명령만 사용하세요. 테스트 명령을 통해 게이팅을 사용하는 경우,`--severity-threshold` 와 같은 특정 기준 또는 CLI 또는 snyk-filter 플러그인의 여러 옵션을 충족하는 문제가 발견되면 빌드를 중단하는 것이 목적입니다.\
   \
   일반적으로 Snyk 오픈 소스는 일반적으로 빌드 시스템에 종속성을 설치한 후 테스트 및/또는 모니터에서 실행됩니다.\
   \
   일반적인 명령은 다음과 같습니다:
   * 코드: `snyk code test --org=[org-id]`
   * 오픈소스스:
     * `snyk test --all-projects --org=[org-id]`
     * `snyk monitor --all-projects --org=[org-id]`\
       `[org-id]`를 조직의 ID로 바꿉니다.
   * 컨테이너 및 코드형 인프라 스캔은 스캔하는 유형에 따라 다르므로 [컨테이너](../../../scan-with-snyk/snyk-container/scan-container-images.md) 및 [코드형 인프라 스캔 ](../../../scan-with-snyk/scan-infrastructure/)을 참조하세요.
4. `snyk test`를 실행할 때는 로컬에서, 모니터 또는 보고서를 사용할 때는 Snyk 웹 UI를 통해 결과를 검토합니다.

다양한 파이프라인 통합에 대한 데모는 [Snyk-Labs](https://github.com/snyk-labs/snyk-cicd-integration-examples)를 참조하세요.
