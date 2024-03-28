# Level 3: 우선순위 설정

위험 기반 우선순위 지정과 Snyk AppRisk용 Kubernetes 커넥터를 설정하고 배포하는 방법에 대해 확인할 수 있습니다.

위험 기반 우선 순위 지정은 Snyk AppRisk가 애플리케이션의 컨텍스트를 이해하고 보안 문제의 우선 순위를 보다 잘 지정할 수 있도록 지원하는 기능입니다.

[Snyk Risk-Based prioritization](../risk-based-prioritization-for-snyk-apprisk/prioritization-setup/)은 취약점에 대한 여러 가지 위험 요소에 중점을 둡니다:

* **OS 상태**: 해당 취약점이 운영 체제에 적용됩니까?
* **배포**: 내 코드가 배포된 컨테이너 이미지에 있습니까?
* **공용 사용**: 컨테이너 이미지에 인터넷 경로가 구성되어 있습니까?

Snyk Risk 기반 우선순위 지정의 목적은 애플리케이션이 배포되고 구성되는 방식을 이해함으로써 오픈 소스, 코드 및 컨테이너 문제에 대한 애플리케이션 컨텍스트를 제공하는 것입니다. 이를 통해 애플리케이션에 미치는 위험을 기반으로 문제의 우선순위를 지정할 수 있습니다.

핵심 개념에 대한 자세한 내용과 이해는[Assets](../risk-based-prioritization-for-snyk-apprisk/how-risk-based-prioritization-works/assets.md) 및 [Risk factors](../risk-based-prioritization-for-snyk-apprisk/how-risk-based-prioritization-works/risk-factors/) 페이지를 중심으로 [How risk-based prioritization works](../risk-based-prioritization-for-snyk-apprisk/how-risk-based-prioritization-works/)를 참조하십시오.

이 Level의 목적은 Snyk Container 문제나 취약점에 대한 컨텍스트를 제공하는 것입니다. Kubernetes 커넥터를 클러스터에 배포한 후 컨테이너가 배포 및 공개 측면에 있는지 식별할 수 있으므로 컨테이너 취약점의 우선 순위를 지정할 수 있습니다.

Kubernetes 커넥터 설정 방법에 대한 자세한 내용은 [Prioritization setup: Kubernetes connector](../risk-based-prioritization-for-snyk-apprisk/prioritization-setup/prioritization-setup-kubernetes-connector.md)를 참조하십시오.
