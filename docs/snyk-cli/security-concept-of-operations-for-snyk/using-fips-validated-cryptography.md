# FIPS 지원 암호화 사용

## Snyk에서 FIPS 지원 암호화 사용 가능 범위

FIPS 지원 암호화 사용 기능은 Windows 및 Linux 운영 체제로만 지원됩니다.

| Operating System | FIPS 지원 |
| ---------------- | ------- |
| Windows          | ✅       |
| Linux            | ✅       |
| Alpine           | ⛔       |
| macOS            | ⛔       |

## Snyk CLI 및 Snyk Language Server에서의 FIPS 지원 암호화 지원 및 사용

개발자 경험을 최적화하기 위해 Snyk은 [Snyk Language Server](../../integrate-with-snyk/ide-tools/snyk-language-server.md)와 [Snyk CLI](../getting-started-with-the-snyk-cli.md)를 결합하고 있습니다. 첫 번째 단계로, Snyk은 하나의 애플리케이션에서 FIPS 바이너리를 제공합니다. 추후에는 FIPS 이외의 CLI 바이너리도 Snyk Language Server에 사용될 예정입니다.

이제 Snyk Language Server를 CLI 명령으로 실행할 수 있습니다.

```bash
> snyk language-server

# instead of 
> snyk-ls
```

따라서 FIPS 지원 암호화를 사용하기 위한 방법은 CLI와 Language Server에서 동일합니다.

### CLI 및 Snyk Language Server에서 FIPS 암호화를 위한 전제 조건

**Linux 운영 체제**

Linux에서 Snyk은 OpenSSL 및 검증된 FIPS 제공업체를 통해 FIPS 검증 암호화를 지원합니다.

Linux 시스템에 OpenSSL이 설치되어 있고 FIPS 유효성 검사 요구 사항을 충족하도록 구성되어 있는지 확인하세요. 이를 수행하는 방법에 대한 자세한 내용은 [OpenSSL project](https://www.openssl.org/docs/fips.html)의 설명서를 참조하세요.

**Windows 운영 체제**

Windows에서 Snyk은 Windows CNG API를 통해 FIPS 검증 암호화를 지원합니다.

Windows에서 FIPS를 활성화하려면 [Windows FIPS 정책](https://learn.microsoft.com/en-us/windows/security/security-foundations/certification/fips-140-validation#step-3-enable-the-fips-security-policy)을 사용하세요.

테스트를 위해 레지스트리 키`HKLM\SYSTEM\CurrentControlSet\Control\Lsa\FipsAlgorithmPolicy` 를 사용하여 `Enabled` 값을 1로 설정하여 FIPS를 활성화할 수 있습니다.

#### FIPS 지원 바이너리 다운로드

Snyk 바이너리는 FIPS 지원 여부와 관계없이 사용할 수 있습니다. 모두 static.snyk.io에서 호스팅되며 기본 URL로 구분됩니다.

**FIPS Base URL:** https://static.snyk.io/fips/

**Regular Base URL:** https://static.snyk.io/

[Snyk 설치 및 사용 방법](../install-or-update-the-snyk-cli/)에 대한 모든 지침은 동일하게 유지됩니다. 필요한 유일한 변경 사항은 적절한 기본 URL을 사용하는 것입니다.

### FIPS 지원 Snyk CLI 다운로드 및 실행 방법

다음 예시에서는 [Microsoft Mariner](https://mcr.microsoft.com/en-us/product/cbl-mariner/base/core/about) 이미지를 사용하여 FIPS 인증 Snyk CLI를 다운로드하고 실행합니다.

```bash
docker run -it mcr.microsoft.com/cbl-mariner/base/core:2.0 bash
> tdnf install -y ca-certificates
> curl --compressed https://static.snyk.io/fips/cli/latest/snyk-linux-arm64 -o snyk
> chmod +x snyk
> ./snyk -d
...
2023-09-13T11:02:49Z main - Features:
2023-09-13T11:02:49Z main -   oauth:               Disabled
2023-09-13T11:02:49Z main -   fips:                Enabled
...
```

### Snyk CLI에서 FIPS 암호화 문제 해결

`not in FIPS mode` 오류는 기본 암호화 라이브러리가 FIPS 모드가 아님을 나타냅니다. 이러한 문제를 해결하려면 [전제 조건](using-fips-validated-cryptography.md#snyk-fips)이 충족되는지 확인하세요.

## IDE 연동에서 FIPS 인증 암호화 지원 및 사용

### Visual Studio Code

[Snyk Visual Studio Code 연동](../../integrate-with-snyk/ide-tools/visual-studio-code-extension/)에서 FIPS 인증된 암호화를 사용하려면 다음과 같이 하세요:

* [전제 조건](using-fips-validated-cryptography.md#snyk-fips)이 충족되는지 확인합니다.
* [적절한 FIPS 지원 바이너리를 다운로드합니다.](using-fips-validated-cryptography.md#fips)
* Snyk 설정에서 자동 바이너리 관리를 비활성화합니다.
* 언어 서버 경로와 CLI 경로를 동일한 바이너리로 설정하여 바이너리를 사용하도록 연동 서비스를 구성합니다.

### Eclipse

[Snyk Eclipse integration](../../integrations/ide-tools/eclipse-plugin/)에서 FIPS 검증 암호화를 사용하려면 다음을 수행하세요:

* [전제 조건](using-fips-validated-cryptography.md#snyk-fips)이 충족되는지 확인합니다.
* [적절한 FIPS 지원 바이너리를 다운로드합니다.](using-fips-validated-cryptography.md#fips)
* Snyk 설정에서 자동 바이너리 관리를 비활성화합니다.
* Language Server 경로와 CLI 경로를 동일한 실행 파일로 설정하여 바이너리를 사용하도록 통합을 구성합니다.
* FIPS 검증[ JCE (Java Cryptography Extension)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search?SearchMode=Basic\&ModuleName=java\&CertificateStatus=Active\&ValidationYear=0)를 사용하도록 Java 런타임을 구성합니다.

### JetBrains

[Snyk JetBrains integration](../../integrate-with-snyk/ide-tools/jetbrains-plugins/)에서 FIPS 검증 암호화를 사용하려면 다음을 수행하세요:

* [전제 조건](using-fips-validated-cryptography.md#snyk-fips)이 충족되는지 확인합니다.
* [적절한 FIPS 지원 바이너리를 다운로드합니다.](using-fips-validated-cryptography.md#fips)
* Snyk 설정에서 자동 바이너리 관리를 비활성화합니다.
* CLI 경로를 설정하여 바이너리를 사용하도록 통합을 구성합니다.
* Configure the Java Runtime to use a FIPS-validated[ JCE (Java Cryptography Extension)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search?SearchMode=Basic\&ModuleName=java\&CertificateStatus=Active\&ValidationYear=0).

### Visual Studio

[Snyk Visual Studio integration](../../integrate-with-snyk/ide-tools/visual-studio-extension/)에서 FIPS 검증 암호화를 사용하려면 다음을 수행하세요:

* [전제 조건](using-fips-validated-cryptography.md#snyk-fips)이 충족되는지 확인합니다.
* [적절한 FIPS 지원 바이너리를 다운로드합니다.](using-fips-validated-cryptography.md#fips)
* Snyk 설정에서 자동 바이너리 관리를 비활성화합니다.
* CLI 경로를 설정하여 바이너리를 사용하도록 통합을 구성합니다.

## CI/CD 연동에서 FIPS 검증 암호화 지원 및 사용

[CI/CD 연동](../../integrate-with-snyk/snyk-ci-cd-integrations/)에서 FIPS는 FIPS가 활성화된 CLI를 직접 사용해야만 사용할 수 있습니다.

## 패키지 리포지토리에서 FIPS 검증 암호화 지원 및 사용

The [Snyk Nexus Repository Manager Gatekeeper plugin](../../integrate-with-snyk/gatekeeper-plugins/nexus-repository-manager-gatekeeper-plugin.md)과 [Artifactory Gatekeeper plugin](../../integrate-with-snyk/gatekeeper-plugins/artifactory-gatekeeper-plugin.md)은 Snyk API를 사용하며 Java VM에서 실행됩니다. FIPS 검증 암호화를 사용하려면 FIPS 검증[ JCE (Java Cryptography Extension)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search?SearchMode=Basic\&ModuleName=java\&CertificateStatus=Active\&ValidationYear=0)를 사용하도록 Java 런타임을 구성하세요.
