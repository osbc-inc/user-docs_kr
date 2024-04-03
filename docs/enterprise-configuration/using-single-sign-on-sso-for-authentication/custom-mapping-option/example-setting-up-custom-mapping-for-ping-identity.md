# 예: Ping Identity에 대한 사용자 지정 매핑 설정

이 페이지에서는 [Custom Mapping Option](./)을 사용하여 Ping Identity에 대한 사용자 정의 역할 매핑을 구성하는 방법을 설명합니다.

{% hint style="info" %}
이 가이드에서는 Ping Identity 애플리케이션이 구성되어 작동한다고 가정합니다.
{% endhint %}

{% hint style="info" %}
셀프 서비스 SSO는 사용자 지정 매핑을 수용하지 않으므로 Snyk 담당자가 Enterprise 애플리케이션 설정 시 Snyk 측의 모든 단계를 수행해야 합니다.
{% endhint %}

1.  In your application configuration, select **Attribute mappings** and click the pencil to edit the attributes.

    <figure><img src="../../../.gitbook/assets/6 (3).png" alt="Edit mapping attributes"><figcaption><p>Edit mapping attributes</p></figcaption></figure>
2.  Select **+Add** and enter the following attribute, then save the change,\
    **roles**: `Group Names`\\

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-09-05 at 12.02.30 PM.png" alt="Add roles array"><figcaption><p>Add roles array</p></figcaption></figure>
3.  In the left menu, select **Identities/Groups** and add the Snyk Groups needed following the syntax explained on the [Cusom Mapping Option](./) page.

    <figure><img src="../../../.gitbook/assets/12 (2).png" alt="Adding an example Group"><figcaption><p>Adding an example Group</p></figcaption></figure>
4. If you so not select a **Population** at the bottom of the previous screen, ensure that you assign the Group to the user(s) who should be part of the role assignment in Snyk. If you select a **Population**, all users in that population will inherit the permissions of the assigned Snyk role.
5. To finalize the process, reach out to your Snyk contact to validate that the SAML payload contains the role array and to enable the custom mapping feature.
