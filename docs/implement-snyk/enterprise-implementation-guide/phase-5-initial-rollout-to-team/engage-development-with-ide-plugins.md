# IDE 플러그인으로 개발 참여

## 개발자에게 Snyk IDE 플러그인 소개하기

개발자에게 [Snyk IDE plugin](../../../integrate-with-snyk/ide-tools/)을 설치하도록 장려하는 것은 개발자의 채택을 개선하고 풀 리퀘스트에 커밋하거나 빌드에 추가하기 전에 개발자가 더 많은 권한과 책임을 가지고 문제를 해결하는 '시프트 레프트'를 달성하는 데 있어 핵심적인 단계입니다.

Snyk IDE 플러그인은 개발자가 보안 취약점과 문제를 찾아서 수정하는 데 도움이 됩니다. 이를 통해 개별 개발자는 보안 검토를 통과하고, 개발 후반에 비용이 많이 드는 수정을 피하며, 안전한 코드를 개발하고 제공하는 시간을 단축할 수 있습니다.

웨비나 [IDE 및 CLI에서 Snyk을 사용하는 개발자를 위한 워크플로](https://www.youtube.com/watch?v=jzUJS6S6H48)에서는 IDE 플러그인을 사용하여 이슈를 검토하는 데모를 비롯하여 IDE 사용법을 자세히 다룹니다.

## 구현 팁

보안을 막 시작한 기업은 가시성 및 예방 단계부터 시작하여 어떤 문제를 해결해야 하는지에 대한 명확한 방향을 제시해야 합니다. 개발자가 우선순위가 지정된 문제를 해결하거나 새로운 작업을 시작하면 자연스럽게 IDE를 도입하여 수정 사항을 검증하고 사전에 테스트하여 보안 게이트에서 발생할 수 있는 잠재적 마찰을 제거할 수 있는 기회가 생깁니다. 이 때 앱 보안 프로그램은 사후 대응 방식에서 사전 예방적 접근 방식으로 전환하는 경우가 많습니다.

성숙한 AppSec 프로그램을 갖춘 회사는 개발자가 이미 보안 개념에 익숙하기 때문에 개발자에게 Snyk IDE 플러그인에 대한 액세스 권한을 더 일찍 제공할 수 있습니다. 따라서 롤아웃은 백로그 해결보다는 새로운 문제를 예방하고 수정 사항을 검증하는 데 더 중점을 둡니다.

## 사용 가능한 플러그인

다음과 같은 Snyk 플러그인 및 확장 프로그램을 사용할 수 있습니다:

* [Eclipse 플러그인](../../../integrations/ide-tools/eclipse-plugin/)
* [JetBrains 플러그인](../../../integrate-with-snyk/ide-tools/jetbrains-plugins/)
* [Visual Studio 확장 프로그램](../../../integrate-with-snyk/ide-tools/visual-studio-extension/)
* [Visual Studio Code 확장](../../../integrate-with-snyk/ide-tools/visual-studio-code-extension/)

[IDE에서 Snyk 사용 소개](https://learn.snyk.io/lesson/snyk-in-an-ide/) 교육 세션에서 자세한 지침을 확인할 수 있습니다..

{% hint style="info" %}
Snyk 애플리케이션이 Snyk EU 또는 AU 데이터 센터에서 호스팅되는 경우 IDE 플러그인 설정에서 [해당 지역과 관련된 URL](../../../working-with-snyk/regional-hosting-and-data-residency.md#ides-urls)을 사용하여 이를 지정해야 합니다.\
자세한 내용은 [지역 호스팅 및 데이터 레지던스](../../../working-with-snyk/regional-hosting-and-data-residency.md)를 참조하세요.
{% endhint %}
