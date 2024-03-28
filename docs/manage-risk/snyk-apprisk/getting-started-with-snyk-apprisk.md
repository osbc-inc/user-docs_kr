# Snyk AppRisk 시작하기

## 전제조건

Snyk AppRisk를 시작하기 전에 다음 전제 조건을 충족해야 합니다:

* Snyk Enterprise를 사용합니다.
* 귀하의 계정에는 Snyk AppRisk Essentials에 대한 액세스 권한이 있습니다.
* Snyk AppRisk와 연결된 Group의 Group 관리자이거나 View Group 및 Edit AppRisk에 대한 권한이 있는 Group level을 할당합니다.
* Snyk AppRisk와 관련된 그룹에는 Snyk 애플리케이션 보안 제품이 포함되어 있습니다.
* 저장소 자산 검색을 위해 클라우드 기반 SCM 툴(Azure DevOps, GitHub, GitLab 등)을 Snyk AppRisk에 온보드할 수 있는 권한이 필요합니다.

{% hint style="info" %}
Git code repository를 Snyk AppRisk와 연동할 때 Snyk으로 가져온 것뿐만 아니라 code repository에 대한 광범위하고 완전한 view 권한이 있는 보조 토큰을 사용해야 합니다.\
보조 토큰을 사용하여 연동한 Snyk에서 온보드에 포함된 모든 것의 카운터뷰를 볼 수 있습니다.\
보조 토큰을 사용하면 Organization level 구성에서 제한된 토큰에서 사각지대가 발생할 가능성이 줄어듭니다.\
첫 번째 가져오는 동기화는 완료하는 데 최대 24시간이 걸릴 수 있습니다.
{% endhint %}

## 권한

아래에 설명된 Group level 역할 권한 중 하나로 Snyk AppRisk에 액세스할 수 있습니다. 권한에 액세스하려면 **View groups**로 이동한 다음 **Snyk AppRisk permissions** 옵션을 선택합니다.

1. View AppRisk - AppRisk에 대한 읽기 전용 액세스 권한을 부여합니다.
2. Edit AppRisk - AppRisk에 대한 편집 권한(예: 정책 편집, 자산 분류 편집, 추가 연동)을 부여합니다.

Group 관리자는 기본적으로 **Edit AppRisk** 권한을 할당받고, 그룹 뷰어는 기본적으로 **View AppRisk** 권한을 할당받습니다.

{% hint style="info" %}
기본 사용자 역할 및 권한에 대한 자세한 내용은 [기본 사용자 역할](../../snyk-admin/user-roles-and-permissions/pre-defined-roles.md)을 참조하십시오.
{% endhint %}

## 로그인 및 인증

SSO, Google SAML 등을 사용하여 Snyk에 로그인하고 인증합니다.

## Snyk AppRisk 접근

Snyk AppRisk가 활성화된 Group을 선택합니다. 왼쪽 탐색 메뉴에 Snyk AppRisk에 대한 링크가 나타납니다. 이 링크를 클릭하면 새 브라우저 화면에서 프로그램이 열립니다.

{% hint style="info" %}
Keep both Snyk Web UI and Snyk AppRisk tabs open to ensure optimal functionality.
{% endhint %}

## 주요 내용

**Asset**: Asset은 애플리케이션의 일부인 식별 가능한 엔티티로 보안 및 개발자와 관련이 있습니다.

**Controls**: 자산과 관련된 보안 컨트롤입니다. [Coverage controls](policies-for-snyk-apprisk/use-cases-for-policies/coverage-control-policy-use-case.md) 섹션으로 이동하여 보안 컨트롤에 사용 가능한 모든 상태를 확인합니다.

**Coverage**: 응용프로그램 보안 프로그램과 관련하여 보안 도구(예: Snyk Open Source)에 의해 검사 및 테스트 여부를 평가합니다. 적용해야 할 컨트롤과 선택적으로 실행해야 할 빈도를 지정할 수 있는 정책 유형입니다.

**Tags**: Asset을 분류하는 방법입니다. 속성에 따라 Asset을 다르게 인식하거나 처리할 수 있도록 도와줍니다. Asset은 인벤토리에 있는 tags로 필터링하거나 정책을 만들 때 필터링할 수 있습니다. 태그를 Asset에 자동으로 할당하거나 사용자가 만든 정책에 따라 tags를 지정할 수 있습니다. GitHub 및 GitLab 항목은 Asset tags로 처리되어 정책을 만드는 데 사용할 수 있습니다.

**Class**: Asset에 비즈니스 컨텍스트를 할당하고 비즈니스 중요도에 따라 Asset을 분류하는 방법입니다. Asset은 클래스 A, B, C 또는 D로 할당할 수 있습니다. 여기서 클래스 A(비즈니스 중요, 중요한 데이터 처리, 규정 준수 대상 등의 자산)가 가장 중요하고 클래스 D(테스트 앱, 샌드박스 환경 등)가 가장 중요도가 떨어집니다. 자산은 기본적으로 클래스 C로 할당됩니다. 클래스는 정책에서 정의된 것뿐만 아니라 정책에서도 사용할 수 있습니다.

**Policy**: 비즈니스 상황에 따라 자산을 분류하고 tags를 지정하는 것과 같은 특정 조건에서 작업을 자동화하는 방법입니다. policy 빌드 UI를 사용하여 메시지를 보내거나 커버리지 갭 컨트롤을 설정하는 등의 작업을 구성할 수도 있습니다.

## 스캔 방법

웹 UI, CLI, API 또는 PR Checks에서 스캔을 시작할 수 있습니다. 자세한 내용은 [Start scanning using the CLI, Web UI, or API](../../scan-with-snyk/start-scanning-using-the-cli-web-ui-or-api.md)을 참조하십시오.

CLI를 사용하여 검색을 시작하는 경우 다음과 같은 상황이 발생할 수 있습니다:

1. CLI가 검색 중인 디렉토리에서 `.git` 폴더를 사용할 수 있는 경우, Snyk Open Source, Snyk Container 및 Snyk IaC에 대해 `git remoteurl` 이 자동으로 선택됩니다.

{% hint style="info" %}
CLI에서 스캔한 디렉토리에서 `.git` 폴더를 사용할 수 있는 경우에도 Snyk Code는`git remoteurl`을 자동으로 픽업하지 않습니다.
{% endhint %}

2. CLI가 검색 중인 디렉토리에 `.git` 폴더를 사용할 수 없는 경우 다른 test 또는 monitor 명령을 사용하여 동일한 결과를 얻을 수 있습니다:
   * [`snyk monitor`](../../snyk-cli/commands/monitor.md#remote-repo-url-less-than-url-greater-than), Snyk 오픈 소스용
   * [`snyk iac test`](../../snyk-cli/commands/iac-test.md#remote-repo-url-less-than-url-greater-than) -  `--report` 옵션도 필요합니다
   * `snyk container monitor` - 일시적으로 옵션을 사용할 수 없습니다.
   * `snyk code test` - 일시적으로 옵션을 사용할 수 없습니다.
