# 커버리지 제어 정책 - Use case

정책 보기에서 **적용 범위 제어 설정** 작업을 사용하여 응용 프로그램 자산을 식별하고 이를 모니터링하며 위험의 우선 순위를 지정할 수 있습니다. 하나 또는 여러 보안 제품을 선택할 수 있으며 마지막 검색이 수행되어야 하는 기간을 지정할 수도 있습니다.

적용 범위 정책을 식별하고 설정하면 팀에서 특정 보안 제어가 필요한 위치를 정의할 수 있습니다.

다음 예제에서는 Snyk Open Source 및 Snyk Code 보안 컨트롤이 있어야 하는 자산을 필터링한 다음 적용 범위 정책을 설정합니다.

<figure><img src="../../../../.gitbook/assets/image (2) (10).png" alt="AppRisk - Setting up a Coverage Control policy"><figcaption><p>Snyk AppRisk - Setting up a Coverage Control policy</p></figcaption></figure>

예시에서 적용해야 하는 필터가 다음과 같습니다:

* **Filter 1**: 저장소인 자산만 포함합니다.

<figure><img src="../../../../.gitbook/assets/image (3) (5).png" alt="Filter configuration for asset type" width="350"><figcaption><p>Filter configuration for asset type</p></figcaption></figure>

* **Filter 2**: 응용 프로그램과 관련된 코딩 언어 태그가 있는 자산 (Apex, ASP, C, C#, C++, CMake, Go, HTML, Java, JavaScript, Kotlin, PHP, Python, Ruby, Scala, Swift, TypeScript, VisualBasic, Handlebars, Makefile, Objective-C).

<figure><img src="../../../../.gitbook/assets/image (4) (7).png" alt="Filter configuration for tags" width="354"><figcaption><p>Filter configuration for tags</p></figcaption></figure>

다음으로 두 가지 작업을 정의해야 합니다. 하나는 Snyk Open Source이고 다른 하나는 Snyk Code입니다. 예는 이 두 가지 보안 컨트롤에 초점을 맞추고 있기 때문입니다.

* **Action 1**: Snyk Open Source를 선택한 상태에서 Set Coverage Control Policy 액션을 추가합니다. Snyk에서는 기본적으로 SCM 통합을 사용하여 가져온 Open Source 매니페스트 파일을 일 단위로 검사합니다. 적용 범위 제어 정책에서는 해당 리포지토리에 대해 지난 이틀 동안 Snyk Open Source 검사가 발생했는지 확인해야 합니다.

<figure><img src="../../../../.gitbook/assets/image (5) (3).png" alt="Filter configuration for coverage control" width="352"><figcaption><p>Filter configuration for coverage control</p></figcaption></figure>

* **Action 2**: Snyk Code가 선택한 Set Coverage Control Policy 작업을 추가합니다. Snyk Code의 경우 기본적으로 일주일에 한 번 또는 변경 사항이 모니터링되는 지점으로 push되었을 때 검색이 수행됩니다. 커버리지 제어 정책은 해당 저장소에 대한 Snyk Code 검색이 지난 주에 발생했는지 확인해야 합니다.

<figure><img src="../../../../.gitbook/assets/image (6) (6).png" alt="Filter configuration for coverage control" width="350"><figcaption><p>Filter configuration for coverage control</p></figcaption></figure>

인벤토리 보기에서 모든 커버리지 갭은 제어 커버리지 아이콘을 통해 스트라이크로 표시됩니다. [인벤토리 기능](../../inventory-for-snyk-apprisk/inventory-capabilities.md) 페이지에서 각 아이콘에 대한 자세한 내용을 확인하십시오.
