---
description: Usage of this mode is discouraged.
---

# 안전하지 않은 다운스트림 모드

일부 상황에서는 다운스트림 연결에 http만 사용해야 할 수도 있습니다. 일반적으로 이러한 경우는 비교적 드물게 발생하며, 대신 https를 사용하도록 업그레이드하는 것이 좋습니다.

단기간에 이것이 불가능한 경우, 안전하지 않은 다운스트림 모드에서는 SCM/JIRA 등에 대한 다운스트림 요청이 https 대신 http를 통해 이루어지도록 강제하는 방법을 도입합니다.

이 모드는 대부분의 경우 사용하지 않는 것이 좋으며 옵트인 상태로 유지해야 합니다. \
이 모드에서는 모든 요청이 http를 통해 이루어지므로 TLS 암호화의 안전성을 활용할 수 없습니다. 즉, 모든 자격 증명과 데이터가 암호화되지 않은 상태로 표시되며, 이는 보안이 엄격한 네트워크에서만 허용됩니다.

[Broker Helm 차트 설치에 대한 사용자 지정 추가 옵션](custom-additional-options-for-broker-helm-chart-installation.md)을 사용하여 이 환경 변수를 주입하세요:

`--set env[0].name=INSECURE_DOWNSTREAM --set env[0].value="true"`

{% hint style="danger" %}
HTTP 사용은 매우 안전하지 않습니다! 사용자의 데이터와 자격 증명이 네트워크 교환을 통해 투명하게 전송됩니다.

이 모드 사용으로 인해 발생할 수 있는 자격증명 유출에 대해 **Snyk는 책임을 지지 않습니다**.
{% endhint %}
