# 보안 정책 조건(Security policy conditions)

조건은 규칙을 설정하는 변수입니다.

조건 카테고리를 선택하면 **포함(Includes)** 또는 **포함하지 않음(Does not include)**을 선택하고 원하는 조건(예: 성숙, CWE-1234)을 선택하라는 메시지가 표시됩니다.

**AND** 함수를 사용하여 동일한 규칙에 여러 조건을 쌓을 수 있습니다.

<table data-header-hidden><thead><tr><th width="210"></th><th></th></tr></thead><tbody><tr><td><strong>조건 카테고리</strong></td><td><strong>조건 정의 및 변수</strong></td></tr><tr><td>Exploit Maturity</td><td>지정된 exploit 만기 값을 포함하는 모든 이슈를 일치시킵니다. 여러 값을 선택하면 선택한 값을 포함하는 모든 이슈에 조건이 적용됩니다. 값에는 <code>Mature</code>, <code>Proof of Concept</code>, <code>No known exploit</code>, and <code>No data available</code>이 포함됩니다.</td></tr><tr><td>CWE</td><td>지정된 CWE가 포함된 모든 이슈를 일치시킵니다. 여러 CWE를 지원합니다.</td></tr><tr><td>CVE</td><td>지정된 CVE가 포함된 모든 이슈와 일치합니다. 여러 CVE를 지원합니다.</td></tr><tr><td>Snyk ID</td><td>지정된 Snyk ID가 포함된 모든 이슈와 일치합니다. 여러 Snyk ID를 지원합니다. 모든 이슈에 CVE가 있는 것은 아니므로 이를 지정하는 좋은 방법입니다.</td></tr></tbody></table>
