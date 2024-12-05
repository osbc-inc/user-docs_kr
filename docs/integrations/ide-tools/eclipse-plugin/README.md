# Eclipse plugin

Snyk Eclipse plugin은 Code, Container 및 infrastructure as code 구성을 제공합니다.

Snyk는 다음 유형의 문제를 검사합니다:

* [**Open Source Security**](https://snyk.io/product/open-source-security-management/) - Snyk 프로젝트에 가져온 direct 및 indirect(transitive) 오픈 소스 dependencies 모두에서 보안 취약점 및 라이선스 문제를 검사합니다. [`Open Source docs`](https://docs.snyk.io/products/snyk-open-source) 참조하세요.
* [**Code Security**](https://snyk.io/product/snyk-code/) - 코드의 보안 취약점을 파악합니다. [Snyk Code docs](https://docs.snyk.io/products/snyk-code) 참조하세요.
* [**Infrastructure as Code (IaC) Security**](https://snyk.io/product/infrastructure-as-code-security/) -  IaC 템플릿의 구성 문제를 확인하세요: Terraform, Kubernetes, CloudFormation 및 Azure 리소스 관리자의 구성 문제를 다룹니다. [Snyk Infrastructure as Code docs](https://docs.snyk.io/products/snyk-infrastructure-as-code) 참조하세요.

Eclipse plugin은 다이렉트 디펜던시와 트랜지시브 디펜던시 모두에 대해 자동화된 알고리즘 기반 수정 제안을 제공합니다. 이 단일 plugin은 Java 취약성 스캐너와 오픈 소스 보안 스캐너를 제공합니다.

Eclipse plugin을 설치하고 구성한 후에는 실행하거나 파일을 열거나 자동 저장할 때마다 프로젝트의 매니페스트 파일, 전용 코드 및 구성 파일을 스캔합니다. Snyk은 실행 가능한 보안 취약점, 라이선스 또는 잘못된 구성 문제에 대한 세부 정보를 제공하고 그 결과를 Eclipse UI에 표시합니다.

이 페이지에서는 지원되는 환경, 지원 및 피드백 제공에 대해 설명하고 설치 지침을 제공합니다. 이 페이지의 단계를 완료한 후에는 다른 Eclipse plugin 문서의 지침을 따라 계속 진행하면 됩니다:

* [Download the CLI and language server with the Eclipse plugin](https://docs.snyk.io/ide-tools/eclipse-plugin/download-the-cli-and-language-server-with-the-eclipse-plugin)
* [Authentication for the Eclipse plugin](https://docs.snyk.io/ide-tools/eclipse-plugin/authentication-for-the-eclipse-plugin)
* [Configuration of the Eclipse plugin](https://docs.snyk.io/ide-tools/eclipse-plugin/configuration-of-the-eclipse-plugin)
* [Environment variables for the Eclipse plugin](https://docs.snyk.io/ide-tools/eclipse-plugin/environment-variables-for-the-eclipse-plugin)
* [Use the Snyk plugin to secure your Eclipse projects](https://docs.snyk.io/ide-tools/eclipse-plugin/use-the-snyk-plugin-to-secure-your-eclipse-projects)
* [SAST scanning results (SAST, Snyk Code)](https://docs.snyk.io/ide-tools/eclipse-plugin/sast-scanning-results-sast-snyk-code)
* [Misconfiguration scanning results (Snyk Infrastructure as Code)](https://docs.snyk.io/ide-tools/eclipse-plugin/misconfiguration-scanning-results-snyk-infrastructure-as-code)
* [Third party dependency scanning (SCA, Snyk Open Source)](https://docs.snyk.io/ide-tools/eclipse-plugin/third-party-dependency-scanning-sca-snyk-open-source)
* [Troubleshooting for the Eclipse plugin](https://docs.snyk.io/ide-tools/eclipse-plugin/troubleshooting-for-the-eclipse-plugin)

## Eclipse plugin을 다운로드할 수 있는 링크

* **Eclipse Marketplace(권장)**: [https://marketplace.eclipse.org/content/snyk-security-code%E2%80%8B-open-source%E2%80%8B-iac-configurations](https://marketplace.eclipse.org/content/snyk-security-code%E2%80%8B-open-source%E2%80%8B-iac-configurations)
* 프리뷰 업데이트 사이트 (CI/CD, on commit): [https://storage.googleapis.com/snyk-eclipse-plugin-test/preview-2.1/repository/](https://storage.googleapis.com/snyk-eclipse-plugin-test/preview-2.1/repository/)
* 업데이트 사이트(주간): [https://storage.googleapis.com/snyk-eclipse-plugin/weekly-2.1/repository/](https://storage.googleapis.com/snyk-eclipse-plugin-test/weekly-2.1/repository/)
* 매뉴얼 다운로드: [https://github.com/snyk/snyk-eclipse-plugin/releases](https://github.com/snyk/snyk-eclipse-plugin/releases)

**Jars의 서명 정보**

다운로드의 정확한 출처를 확인하려면 이 데이터로 Eclipse 팝업 화면에서 서명 세부 정보를 확인합니다.

<figure><img src="../../../.gitbook/assets/image (134) (2) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="The signing key details to verify the integrity and origin of the download plugin"><figcaption><p>The signing key details to verify the integrity and origin of the download plugin</p></figcaption></figure>

플러그인은 다음 OS에서 실행됩니다.

* macOS
* Linux
* Windows

## 지원하는 Eclipse 버전

* 2023-03
* 2022-12
* 2022-09
* 2022-06
* 2022-03
* 2021-12
* 2021-09
* 2021-06
* 2021-03

## 지원 언어, 패키지 매니저 및 프레임워크

* Snyk Open Source의 경우, Eclipse plugin은 C/C++를 제외한 모든 언어 및 패키지 관리자와 Snyk Open Source 및 CLI에서 지원하는 패키지 매니저를 지원합니다. 자세한 내용은 [Supported languages, frameworks, and feature availability overview, Open Source section](https://docs.snyk.io/scan-applications/supported-languages-and-frameworks/supported-languages-frameworks-and-feature-availability-overview#open-source-and-licensing-snyk-open-source)을 참조하세요.
* Snyk Code의 경우, Eclipse plugin은 Snyk Code에서 지원하는 언어 및 프레임워크를 지원합니다. 자세한 내용은 [Supported languages, frameworks, and feature availability overview, Snyk Code section](https://docs.snyk.io/scan-applications/supported-languages-and-frameworks/supported-languages-frameworks-and-feature-availability-overview#code-analysis-snyk-code)을 참조하세요.
* Snyk IaC의 경우 Eclipse plugin은 다음 IaC 템플릿을 지원합니다: Terraform, Kubernetes, CloudFormation 및 Azure Resource Manager.

## 지원하는 운영 체제 및 아키텍처

다음 환경에서 Eclipse plugin을 사용할 수 있습니다:

* Linux: AMD64 및 ARM64
* Windows: 386 및 AMD64
* MacOS: AMD64 및 ARM64

## Snyk Eclipse plugin을 설치하는 방법

실행 중인 Eclipse 인스턴스에서 마켓플레이스로 이동합니다. Snyk를 검색하고 Install을 클릭합니다.

<figure><img src="../../../.gitbook/assets/Screenshot 2022-05-17 at 16.29.29.png" alt="Eclipse Marketplace search showing Snyk plugin and Install button"><figcaption><p>Eclipse Marketplace search showing Snyk plugin and Install button</p></figcaption></figure>

메시지가 표시되면 라이선스 계약에 동의하고 Snyk Security 인증서를 추가하여 설치를 완료합니다(이 작업은 한 번만 수행됩니다).

Eclipse 인스턴스를 다시 시작합니다:

<figure><img src="../../../.gitbook/assets/Screenshot 2022-05-13 at 09.16.37.png" alt="Restart Eclipse"><figcaption><p>Restart Eclipse</p></figcaption></figure>

Eclipse가 재시작되면 Snyk 마법사가 실행되며, 이 마법사가 Snyk API 엔드포인트와 인증 토큰을 설정합니다.

Snyk 설정 마법사가 실행되면 지침에 따라 Snyk API를 설정합니다:

<figure><img src="../../../.gitbook/assets/eclipseSnykWizard (1).png" alt="Snyk configuration wizard"><figcaption><p>Snyk configuration wizard</p></figcaption></figure>

Snyk을 구성했다면, Eclipse 환경설정으로 이동하여 Snyk이 목록에 표시되는지 확인합니다:

<figure><img src="../../../.gitbook/assets/Screenshot 2022-05-17 at 16.36.07.png" alt="Eclipse preferences showing Snyk."><figcaption><p>Eclipse preferences showing Snyk.</p></figcaption></figure>

환경설정을 열면 플러그인 설치를 통한 CLI 다운로드를 선택 해제하여 직접 설치한 CLI를 사용할 수 있습니다.

[Download the CLI and language server with the Eclipse plugin](https://docs.snyk.io/ide-tools/eclipse-plugin/download-the-cli-and-language-server-with-the-eclipse-plugin)단계를 계속 진행하세요.

## Support

도움이 필요하면 Snyk 지원팀에 [request](https://support.snyk.io/hc/en-us/requests/new)를 제출하세요.
