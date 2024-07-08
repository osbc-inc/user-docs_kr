# 예: Ping Identity에 대한 사용자 지정 매핑 설정

이 페이지에서는 [Custom Mapping Option](./)을 사용하여 Ping Identity에 대한 사용자 정의 역할 매핑을 구성하는 방법을 설명합니다.

{% hint style="info" %}
이 가이드에서는 Ping Identity 애플리케이션이 구성되어 작동한다고 가정합니다.
{% endhint %}

{% hint style="info" %}
셀프 서비스 SSO는 사용자 지정 매핑을 수용하지 않으므로 Snyk 담당자가 Enterprise 애플리케이션 설정 시 Snyk 측의 모든 단계를 수행해야 합니다.
{% endhint %}

1.  애플리케이션 구성에서 **Attribute mappings**을 선택하고, 연필 아이콘을 클릭하여 속성을 편집합니다.

    <figure><img src="../../../.gitbook/assets/6 (3).png" alt="Edit mapping attributes"><figcaption><p>Edit mapping attributes</p></figcaption></figure>
2.  **+Add**를 선택하고 다음 속성을 입력한 후 변경 사항을 저장합니다.\
    **roles**: `Group Names`\\

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-09-05 at 12.02.30 PM.png" alt="Add roles array"><figcaption><p>Add roles array</p></figcaption></figure>
3.  왼쪽 메뉴에서 **Identities/Groups**을 선택하고 [Cusom Mapping Option](./) 페이지에 설명된 구문에 따라 필요한 Snyk 그룹을 추가합니다.

    <figure><img src="../../../.gitbook/assets/12 (2).png" alt="Adding an example Group"><figcaption><p>Adding an example Group</p></figcaption></figure>
4. 이전 화면 하단에서 **Population**을 선택하지 않은 경우, Snyk에서 역할 할당에 참여해야 하는 사용자에게 그룹을 할당했는지 확인하세요. **Population**을 선택하면, 해당 Population의 모든 사용자는 할당된 Snyk 역할의 권한을 상속받습니다.
5. 프로세스를 완료하려면 Snyk 담당자에게 연락하여 SAML 페이로드에 역할 배열이 포함되어 있는지 확인하고 사용자 지정 매핑 기능을 활성화하세요.

