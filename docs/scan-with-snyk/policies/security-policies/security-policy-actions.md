# 보안 정책 조치(Security policy actions)

작업은 [보안 정책 조건(security policy conditions)](security-policies-conditions.md) 이 일치할 때 수행하려는 작업을 정의합니다.

{% hint style="info" %}
동일한 규칙에 여러 개의 작업을 쌓을 수 없습니다. 하나의 규칙에 여러 개의 작업을 포함하려면 동일한 조건으로 새 규칙 블록을 만들고 다른 작업을 지정하세요.
{% endhint %}

현재 적용할 수 있는 작업은 다음과 같습니다:

<table><thead><tr><th width="164">Action</th><th>정의</th></tr></thead><tbody><tr><td>심각도(severity)를...로 변경</td><td><p>조건에 해당하는 문제의 심각도를 변경합니다. <code>Low</code>, <code>Medium</code>, <code>High</code>, or <code>Critical</code>으로 설정할 수 있습니다.<br></p><p>심각도가 변경된 이슈는 새 심각도를 반영하여 우선 순위 점수(<a href="../../find-and-manage-priority-issues/priority-score.md">priority score</a>)가 업데이트됩니다.<a href="../../../snyk-admin/snyk-projects/issue-card-information.md">issue card</a>에 정책으로 인해 이슈의 심각도가 변경되었음을 나타내는 메모가 나타납니다. 심각도 아이콘도 '스택'으로 표시되어 새 심각도 뒤에 원래의 심각도가 표시됩니다.</p></td></tr><tr><td>현재 및 향후 instances 무시</td><td><p>조건과 일치하는 모든 취약점을 무시(Ignore)하세요. 예를 들어, <code>business</code> <code>criticality</code> 속성이 <code>low</code>인 프로젝트에서 알려진 익스플로잇이 없는 모든 이슈를 무시합니다.</p><p>무시 정책을 적용한 후에는 관련 프로젝트를 다시 스캔할 때마다 무시 작업이 수행되며 무시된 이슈는<code>ignored by Security Policy</code>으로 표시됩니다.</p><p>동작을 설정할 때 무시 유형으로 <code>won't fix</code> 과 <code>not vulnerable</code>을 선택하고 이유를 추가하면 이슈 카드에 무시와 함께 표시됩니다.</p><p>정책 기반 무시(Policy-based ignores)는 수동으로 무시되는 이슈와 동일한 동작을 합니다. 수동 무시와 마찬가지로 보안 정책에 의해 무시된 이슈에 대해서는 자동 PR이 발생하거나 리포팅의 이슈 수에 포함되지 않습니다.</p></td></tr></tbody></table>
