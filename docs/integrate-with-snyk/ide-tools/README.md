# IDE와 연동하여 Snyk 사용

다음 Snyk 플러그인 및 확장을 사용할 수 있습니다.

* [Eclipse plugin](../../integrations/ide-tools/eclipse-plugin/)
* [JetBrains plugins](jetbrains-plugins/)
* [Visual Studio extension](visual-studio-extension/)
* [Visual Studio Code extension](visual-studio-code-extension/)
* [Language Server](snyk-language-server.md)

Snyk Security 플러그인 및 확장 프로그램은 Snyk 프로젝트의 보안 취약점과 문제를 찾아 수정합니다. 이를 통해 개별 개발자, 오픈 소스 기여자 및 코드 유지관리자는 보안 검토를 통과하고, 개발 후반에 비용이 많이 드는 수정을 방지하고, 보안 코드 개발 및 제공에 소요되는 시간을 단축할 수 있습니다.

취약점 스캔 결과에는 IDE의 컨텍스트, 영향 및 수정 지침과 관련된 문제가 표시되며, 여기서 취약점 수정은 IDE 자체에서 바로 수행할 수 있습니다.

Snyk IDE 플러그인 및 확장은 Snyk CLI를 사용하여 많은 기능을 수행합니다. 자세한 내용은 각 IDE의 설명서를 참조하세요. 문제를 해결할 때 디버그 옵션 `-d.`를 사용하여 동일한 작업에 대해 CLI를 실행하는 것이 항상 도움이 됩니다.

Snyk IDE 플러그인 및 확장도 [Snyk Vulnerability Database](https://security.snyk.io/)에 의존합니다. 자세한 내용은 [Snyk Vulnerability Database](../../scan-with-snyk/snyk-open-source/manage-vulnerabilities/snyk-vulnerability-database.md) 설명서를 참조하세요.

Snyk가 기본 지역이 아닌 다른 지역에서 데이터를 호스팅하는 경우 IDE에서 사용자 정의 `Custom endpoint` 를 설정해야 합니다. 자세한 내용은 [Regional hosting and data residency](../../working-with-snyk/regional-hosting-and-data-residency.md) 페이지에서 [IDEs URLS](../../working-with-snyk/regional-hosting-and-data-residency.md#ides-urls) 을 참조하세요.

**교육** 이용 가능: [**Introduction to using Snyk in an IDE**](https://learn.snyk.io/lesson/snyk-in-an-ide/)
