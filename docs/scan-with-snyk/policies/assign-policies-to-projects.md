# 프로젝트에 정책(policies) 할당

프로젝트에 [프로젝트 속성](../../snyk-admin/snyk-projects/project-attributes.md)을 적용한 후에는 해당 속성에 적용되는 정책을 만들 수 있습니다. 프로젝트와 정책은 정책이 적용된 속성을 기반으로 연결됩니다.

{% hint style="info" %}
프로젝트 속성에 적용되는 정책은 항상 조직에 적용되는 정책보다 우선합니다.
{% endhint %}

정책은 하나 또는 여러 프로젝트 속성에 적용할 수 있지만, 속성 집합에는 하나의 정책만 적용할 수 있습니다. 예를 들어 `Critical`**,** `Production`,`Frontend`에 적용되는 정책이 있는 경우 이러한 정확한 속성에만 적용되는 다른 정책을 만들 수 없습니다.

{% hint style="info" %}
프로젝트 속성에 적용된 정책은 프로젝트 속성이 할당된 CLI 프로젝트에서 실행된다는 가정 하에 CLI 명령 snyk 모니터에 영향을 줍니다. 정책에 적용된 프로젝트 속성은 snyk 테스트에는 영향을 미치지 않습니다.
{% endhint %}

## 프로젝트 속성에 정책을 적용하고 정책을 제거합니다.

속성에 정책을 적용하려면, 속성 선택기 패널(attribute selector panel)에서 정책을 적용하려는 속성의 확인란을 선택합니다.

그룹의 프로젝트에서 이미 생성된 태그를 검색할 수도 있습니다. 정책에 대해 둘 이상의 태그를 선택할 수 있습니다.

<figure><img src="../../.gitbook/assets/Screenshot 2023-07-28 at 17.28.18.png" alt="Attribute selector panel"><figcaption><p>속성 선택기 패널(Attribute selector panel)</p></figcaption></figure>

속성에서 정책을 제거하려면 정책을 제거하려는 속성 옆의 확인란(□)을 선택 취소합니다.

태그를 제거하려면 태그 옆에 있는 X를 클릭합니다.

{% hint style="info" %}
예를 들어 정책을 적용할 속성을 아직 결정하지 않은 경우 속성을 선택하지 않은 상태에서 정책을 만들고 저장할 수 있습니다. 모든 속성을 비워두면 프로젝트에 정책을 적용할 수 없습니다.
{% endhint %}

## 정책에 프로젝트 할당

정책을 할당받으려면 프로젝트에 정책에 나열된 모든 속성이 프로젝트에 적용되어 있어야 합니다. 프로젝트에 정책에 나열되지 않은 속성이 있을 수도 있습니다.

{% hint style="info" %}
속성을 기반으로 프로젝트에 정책이 적용되는 경우 **그룹 관리자(Group Admins)**만 프로젝트 속성을 편집할 수 있습니다. 프로젝트에 적용 가능한 정책이 없는 경우, **조직 관리자(Org Admins)**는 프로젝트에 정책이 적용되도록 하는 속성을 추가할 수 있습니다. 그러나 조직 관리자는 정책이 이미 적용된 프로젝트의 속성을 편집할 수 없습니다.
{% endhint %}

정책에 여러 개의 태그가 추가된 경우 프로젝트는 프로젝트 태그 중 하나만 일치하면 됩니다. 그러나 다른 속성도 정책에 나열된 경우 프로젝트에는 모든 속성과 나열된 태그 중 하나 이상이 있어야 합니다.

예를 들어 `Critical`, `External` 및 `Frontend`에 정책이 적용된 경우 이 정책은 동일한 속성을 가진 프로젝트에는 할당되지만 `Critical`및 `External`속성만 있는 프로젝트에는 할당되지 않습니다.

다음은 정책 예시입니다. 이 정책은 **비즈니스 중요도(Business Criticality)** 섹션의 속성인`Critical`와 **환경(Environment)** 섹션의 속성인 `Frontend` 및 `External`에 적용됩니다. 이 정책에는 두 개의 프로젝트 태그도 있습니다. 첫 번째 태그에는 `PCI`키가 있고 값은`Compliant`입니다. 두 번째 태그에는 키`owner`가 있고 값은 `fred`입니다.

<div align="center" data-full-width="true">

<figure><img src="../../.gitbook/assets/sample-policy.png" alt="Sample policy"><figcaption><p>샘플 정책 (Sample policy)</p></figcaption></figure>

</div>

다음 프로젝트는 `Frontend`, `External`, `Critical`속성을 가지고 있으며 일치하는 태그`PCI:Compliant`를 하나 이상 가지고 있습니다. 따라서 이 프로젝트는 정책을 상속받게 됩니다. 즉, 정책이 이 프로젝트에 할당됩니다.

<div align="left">

<figure><img src="../../.gitbook/assets/screenshot_2021-03-11_at_12.26.02_pm.png" alt="Project inheriting a policy"><figcaption><p>정책 상속 프로젝트(Project inheriting a policy)</p></figcaption></figure>

</div>

프로젝트에 `External` 환경 속성이 없기 때문에 다음 프로젝트는 정책을 상속받지 못합니다.

<div align="left">

<figure><img src="../../.gitbook/assets/screenshot_2021-03-11_at_12.29.03_pm.png" alt="Project not inheriting a policy"><figcaption><p>정책을 상속받지 않는 프로젝트</p></figcaption></figure>

</div>

## 프로젝트에 여러 정책 할당

프로젝트에 여러 정책을 지정할 수 있습니다.  예를 들어, `Critical` 및`External` 속성에 정책이 적용되고 `Critical` 및`Production`속성에 다른 정책이 적용될 수 있습니다.`Critical`, `External` 및 `Production`속성이 있는 프로젝트가 있는 경우 두 정책이 모두 할당됩니다.

프로젝트에 여러 정책이 할당된 경우 정책 관리자 페이지에 있는 정책의 순서에 따라 우선 순위가 결정됩니다. 목록 맨 위에 가장 가까운 정책이 그 뒤에 할당된 다른 정책보다 우선합니다. 정책 순서를 변경하려면 정책을 원하는 순서로 끌어서 놓거나 오른쪽에 있는 3개의 점을 사용하여 목록에서 정책을 위 또는 아래로 이동합니다.

<div align="left">

<figure><img src="../../.gitbook/assets/screenshot_2021-03-11_at_12.51.25_pm.png" alt="Change policy order"><figcaption><p>정책 순서 변경</p></figcaption></figure>

</div>
