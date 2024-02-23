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

## Key Concepts

**Asset**: An asset is an identifiable entity that is part of an application, and relevant for security and developers.

**Controls**: The security controls associated with the asset. Navigate to the [Coverage controls](policies-for-snyk-apprisk/use-cases-for-policies/coverage-control-policy-use-case.md) section to see all available statuses for security controls.

**Coverage**: An assessment of whether applicable assets are scanned and tested by security tools (like Snyk Open Source, for instance), as it relates to an application security program. A type of policy that allows you to specify what controls should be applied and, optionally, how often it needs to be run.

**Tags**: A way to categorize assets. Helps you recognize or handle assets differently according to mutual properties. Assets can be filtered by their tags in the inventory or when creating policy rules. A tag can be automatically assigned to an asset, or the asset can be tagged by a policy you created. GitHub and GitLab topics are treated as asset tags and you can use them for creating policies.

**Class**: A way to assign business context to assets and categorize an asset based on the business criticality. Assets can be assigned Classes A, B, C, or D, where Class A (assets that are business critical, deal with sensitive data, subject to compliance, and so on) is the most important and Class D (test apps, sandbox environments, and so on) the least important. Assets are assigned Class C by default. A class can be used in policies as well as defined in a policy.

**Policy**: A way to automate actions in certain conditions, like classifying and tagging assets with business context. You can also use a policy to configure actions like sending a message or setting the coverage gap control using a Policy builder UI.

## Scanning methods

You can initiate a scan from the Web UI, the CLI, the API, or with PR Checks. See the [Start scanning using the CLI, Web UI, or API](../../scan-with-snyk/start-scanning-using-the-cli-web-ui-or-api.md) page for more details.

If you initiate your scans using the CLI, you might encounter one of the following situations:

1. If you have a `.git` folder available in the directory that the CLI is scanning, then the `git remoteurl` is picked up automatically for Snyk Open Source, Snyk Container, and Snyk IaC.

{% hint style="info" %}
Snyk Code does not automatically pick up the `git remoteurl`, even if the `.git` folder is available in the directory scanned by the CLI.
{% endhint %}

2. If you do not have a `.git` folder available in the directory that the CLI is scanning, you can use different test or monitor commands to achieve the same result:
   * [`snyk monitor`](../../snyk-cli/commands/monitor.md#remote-repo-url-less-than-url-greater-than), for Snyk Open Source
   * [`snyk iac test`](../../snyk-cli/commands/iac-test.md#remote-repo-url-less-than-url-greater-than) - also requires the `--report` command
   * `snyk container monitor` - momentarily, no options are available.
   * `snyk code test` - momentarily, no options are available.

\\

\\
