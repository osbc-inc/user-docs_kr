# 분류 정책 - Use case

Policies view에서 자산 클래스 설정 작업을 사용하여 중요도에 따라 자산을 분류할 수 있습니다. 여기서 클래스 A가 가장 중요하고 클래스 D가 가장 덜 중요합니다.

자산 클래스는 다음을 기준으로 설정할 수 있습니다:

* 저장소 이름
* 자산 태그

{% hint style="info" %}
Snyk AppRisk는 GitHub 및 GitLab 항목을 자산 태그로 식별합니다.
{% endhint %}

분류 정책을 사용하여 애플리케이션에 비즈니스 컨텍스트를 제공합니다. 분류 정책을 설정하면 모든 자산이 자동으로 분류됩니다.

분류 정책을 막 사용하기 시작한 경우 클래스 D 자산은 가장 중요하지 않으므로 먼저 집중하는 것이 좋습니다.

다음 예제에서는 이름에 `sandbox`, `test`및 `to-delete` 을 필터링합니다. Snyk AppRisk에서 GitHub 및 GitLab 항목은 SCM 통합에서 가져온 후 저장소 자산에 적용되므로 SCM의 저장소에`PCI-Compliance` 와 같은 항목이 추가된 경우 Snyk는 Snyk AppRisk에서 해당 태그를 가져와 해당 자산을 클래스 A로 분류할 수 있습니다.

<figure><img src="../../../../.gitbook/assets/image (7).png" alt="AppRisk - Setting up filters for a classification policy"><figcaption><p>Snyk AppRisk - Setting up filters for a classification policy</p></figcaption></figure>

필터를 설정한 후 해당 자산에 클래스 D 자산 분류를 적용해야 합니다.

<figure><img src="../../../../.gitbook/assets/image (8).png" alt="AppRisk - Setting up actions for a classification policy"><figcaption><p>Snyk AppRisk - Setting up actions for a classification policy</p></figcaption></figure>

동일한 정책 내에서 클래스 A, B 및 C 자산에 대해 유사한 패턴을 적용하고 작업을 생성할 수 있습니다.

<figure><img src="../../../../.gitbook/assets/image (9).png" alt="AppRisk - Setting up multiple actions for a classification policy"><figcaption><p>Snyk AppRisk - Setting up multiple actions for a classification policy</p></figcaption></figure>
