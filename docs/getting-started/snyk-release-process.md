# Snyk Release 프로세스

Snyk 기능은 다음 유형의 릴리스에서 사용자에게 제공됩니다.

{% hint style="info" %}
모든 기능이 이러한 단계를 모두 따르는 것은 아니며, 각 기능의 단계 이동 일정은 기능에 따라 다릅니다.
{% endhint %}

## Alpha

<table><thead><tr><th width="240">설명</th><th>사용 가능한 사용자</th><th>접근</th><th>문서</th></tr></thead><tbody><tr><td>내부 릴리스에만 해당됩니다.</td><td>Snyk 내부 사용자, 잠재적으로 일부 디자인 파트너.</td><td>통제됨</td><td>제공된 문서가 없습니다.</td></tr></tbody></table>

## 비공개 Beta

<table><thead><tr><th width="243">설명</th><th>사용 가능한 사용자</th><th>접근</th><th>문서</th></tr></thead><tbody><tr><td>고객을 대상으로 하는 기능의 첫 번째 출시입니다.</td><td>미리 선택된 사용자 그룹입니다.</td><td>Snyk의 초대로.</td><td>제공되지만 공개되지 않을 수 있습니다.</td></tr></tbody></table>

### 비공개 Beta의 Snyk 기능

* [Customize PR templates](../scan-with-snyk/snyk-open-source/automatic-and-manual-prs-with-snyk-open-source/customize-pr-templates/)
* [Configure PR Checks](../scan-with-snyk/run-pr-checks/configure-pr-checks.md)
* [Publish Snyk Code CLI results](../snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-snyk-code/publish-snyk-code-cli-results-and-ignore-issues.md)
* [Enterprise Analytics](../manage-risk/enterprise-analytics.md)
* [Automatically created Project collections](../snyk-admin/introduction-to-snyk-projects/automatically-created-project-collections.md)
* [Snyk Code - Clone capability with Broker for Docker](../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/advanced-configuration-for-snyk-broker-docker-installation/snyk-code-clone-capability-with-broker-for-docker.md)

## Early Access

<table><thead><tr><th width="246">설명</th><th>사용 가능한 사용자</th><th>접근</th><th>문서</th></tr></thead><tbody><tr><td>기능은 테스트를 거쳐 사용할 준비가 되었지만, 기본적으로는 사용할 수 없습니다.</td><td>모든 사용자는 선택적으로 참여합니다. 여기에는 추가 구매 비용이 포함될 수 있습니다.</td><td>Opt-in: Snyk 계정 팀 또는 Snyk Preview를 통해 요청 시</td><td>공개 문서.</td></tr></tbody></table>

### Snyk 기능 in Early Access

* [Insights](broken-reference/)
* [Snyk GitHub Cloud App](../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/snyk-github-cloud-app.md)
* [Use Custom Base Image Recommendations](../scan-with-snyk/snyk-container/use-snyk-container-from-the-web-ui/use-custom-base-image-recommendations/)
* [REST API endpoints: Test an SBOM document for vulnerabilities](../snyk-api/rest-api-endpoints-test-an-sbom-document-for-vulnerabilities.md)
* [Custom rules](../scan-with-snyk/snyk-code/custom-rules/)
* [Risk Score](../manage-issues/risk-score.md)
* [Reachable vulnerabilities](../scan-with-snyk/find-and-manage-priority-issues/reachable-vulnerabilities.md)
* [Group projects by branch or version for monitoring](../snyk-cli/scan-and-maintain-projects-using-the-cli/group-projects-by-branch-or-version-for-monitoring.md)
* [Git repository cloning](../snyk-admin/manage-settings/snyk-preview.md#enable-git-repository-cloning)
* [Fix code vulnerabilities automatically](../scan-with-snyk/snyk-code/manage-code-vulnerabilities/fix-code-vulnerabilities-automatically.md)
* [Snyk broker commit signing](../enterprise-configuration/snyk-broker/snyk-broker-commit-signing.md)

## 일반 가용성 (General Availability)

<table><thead><tr><th width="249">설명</th><th>사용 가능한 사용자</th><th>접근</th><th>문서</th></tr></thead><tbody><tr><td>기능이 완전히 활성화되었습니다.</td><td>모든 사용자는 표준 기능 가용성에 따라 달라질 수 있습니다.</td><td>기본적으로 사용 가능합니다.</td><td>전체 공개 문서.</td></tr></tbody></table>

## 더 이상 사용되지 않음 (Deprecated)

<table><thead><tr><th width="256">설명</th><th>사용 가능한 사용자</th><th>접근</th><th>문서</th></tr></thead><tbody><tr><td>이 기능을 사용할 수 있지만, 사용하지 않는 것이 좋습니다.</td><td>현재 사용자만</td><td>기본적으로 사용 가능합니다.</td><td>전체 공개 문서(적절하게 마크업됨)</td></tr></tbody></table>

## 유지 관리 모드 (Maintenance mode)

<table><thead><tr><th width="256">설명</th><th>사용 가능한 사용자</th><th>접근</th><th>문서</th></tr></thead><tbody><tr><td>이 기능에 대한 새로운 개발이나 업데이트는 이루어지지 않습니다.</td><td>현재 사용자만</td><td>기본적으로 사용 가능합니다.</td><td>전체 공개 문서(적절하게 마크업됨)</td></tr></tbody></table>

## 지원 종료 (End of Support)

<table><thead><tr><th width="256">설명</th><th>사용 가능한 사용자</th><th>접근</th><th>문서</th></tr></thead><tbody><tr><td>새로운 지원 티켓에는 응답하지 않습니다.</td><td>현재 사용자만</td><td>기본적으로 사용 가능합니다.</td><td>전체 공개 문서(적절하게 마크업됨)</td></tr></tbody></table>

### End of life

<table><thead><tr><th width="256">설명</th><th>사용 가능한 사용자</th><th>접근</th><th>문서</th></tr></thead><tbody><tr><td>이 기능은 더 이상 사용할 수 없습니다.</td><td>사용자 없음</td><td>사용 불가</td><td>사용 가능한 문서가 없습니다.</td></tr></tbody></table>
