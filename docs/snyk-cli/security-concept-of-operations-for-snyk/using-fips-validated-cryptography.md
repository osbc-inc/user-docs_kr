# FIPS 인증 암호화 사용

## Snyk에서 FIPS 인증 암호화 사용 가능 범위

FIPS 인증 암호화 사용 기능은 Windows 및 Linux 운영 체제로만 지원됩니다.

| Operating System | FIPS 지원 |
| ---------------- | ------- |
| Windows          | ✅       |
| Linux            | ✅       |
| Alpine           | ⛔       |
| macOS            | ⛔       |

## Snyk CLI 및 Snyk Language Server에서의 FIPS 검증 암호화 지원 및 사용

개발자 경험을 최적화하기 위해 Snyk은 [Snyk Language Server](../../integrate-with-snyk/ide-tools/snyk-language-server.md)와 [Snyk CLI](../getting-started-with-the-snyk-cli.md)를 결합하고 있습니다. 첫 번째 단계로, Snyk은 하나의 애플리케이션에서 FIPS 바이너리를 제공합니다. 추후에는 FIPS 이외의 CLI 바이너리도 Snyk Language Server에 사용될 예정입니다.

이제 Snyk Language Server를 CLI 명령으로 실행할 수 있습니다.

```bash
> snyk language-server

# instead of 
> snyk-ls
```

따라서 FIPS 인증 암호화를 사용하기 위한 방법은 CLI와 Language Server에서 동일합니다.

### CLI 및 Snyk Language Server에서 FIPS 암호화를 위한 전제 조건

**Linux 운영 체제**

Linux에서 Snyk은 OpenSSL 및 검증된 FIPS 제공업체를 통해 FIPS 검증 암호화를 지원합니다.

Linux 시스템에 OpenSSL이 설치되어 있고 FIPS 유효성 검사 요구 사항을 충족하도록 구성되어 있는지 확인하세요. 이를 수행하는 방법에 대한 자세한 내용은 [OpenSSL project](https://www.openssl.org/docs/fips.html)의 설명서를 참조하세요.

**Windows 운영 체제**

Windows에서 Snyk은 Windows CNG API를 통해 FIPS 검증 암호화를 지원합니다.

Windows에서 FIPS를 활성화하려면 [Windows FIPS 정책](https://learn.microsoft.com/en-us/windows/security/security-foundations/certification/fips-140-validation#step-3-enable-the-fips-security-policy)을 사용하세요.

테스트를 위해 레지스트리 키`HKLM\SYSTEM\CurrentControlSet\Control\Lsa\FipsAlgorithmPolicy` 를 사용하여 `Enabled` 값을 1로 설정하여 FIPS를 활성화할 수 있습니다.

#### Download FIPS-enabled binaries

Snyk binaries are available with and without FIPS support. They are all hosted on static.snyk.io, differentiated by their Base URL.

**FIPS Base URL:** https://static.snyk.io/fips/

**Regular Base URL:** https://static.snyk.io/

All instructions on [how to install and use Snyk](../install-or-update-the-snyk-cli/) remain the same. The only required change is using the appropriate Base URL.

### Example of downloading and running the FIPS-enabled Snyk CLI

The example that follows uses a [Microsoft Mariner](https://mcr.microsoft.com/en-us/product/cbl-mariner/base/core/about) image to download and run the FIPS-enabled Snyk CLI.

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

### Troubleshooting FIPS-cryptography in the Snyk CLI

`not in FIPS mode` errors indicate that the underlying cryptography library is not in FIPS mode. To solve these issues ensure that the [prerequisites](using-fips-validated-cryptography.md#prerequisites-for-fips-cryptography-in-the-cli-and-snyk-language-server) are met.

## FIPS-validated cryptography support and use in IDE Integrations

### Visual Studio Code

To make use of FIPS-validated cryptography in the [Snyk Visual Studio Code integration](../../integrate-with-snyk/ide-tools/visual-studio-code-extension/), do the following:

* Ensure the [prerequisites](using-fips-validated-cryptography.md#prerequisites-for-fips-cryptography-in-the-cli-and-snyk-language-server) are met.
* [Download the appropriate FIPS-enabled binaries](using-fips-validated-cryptography.md#download-fips-enabled-binaries).
* Disable automatic binary management in the Snyk settings.
* Configure the integration to use the binary by setting the Language Server Path and the CLI Path to the same binary.

### Eclipse

To make use of FIPS-validated cryptography in the [Snyk Eclipse integration](../../integrations/ide-tools/eclipse-plugin/), do the following:

* Ensure the [prerequisites](using-fips-validated-cryptography.md#prerequisites-for-fips-cryptography-in-the-cli-and-snyk-language-server) are met
* [Download the appropriate FIPS-enabled binaries.](using-fips-validated-cryptography.md#download-fips-enabled-binaries)
* Disable automatic binary management in the Snyk preferences.
* Configure the integration to use the binary by setting the Language Server Path and the CLI Path to the same executable.
* Configure the Java Runtime to use a FIPS-validated[ JCE (Java Cryptography Extension)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search?SearchMode=Basic\&ModuleName=java\&CertificateStatus=Active\&ValidationYear=0).

### JetBrains

To make use of FIPS-validated cryptography in the [Snyk JetBrains integration](../../integrate-with-snyk/ide-tools/jetbrains-plugins/), do the following:

* Ensure the [prerequisites](using-fips-validated-cryptography.md#prerequisites-for-fips-cryptography-in-the-cli-and-snyk-language-server) are met.
* [Download the appropriate FIPS-enabled binaries](using-fips-validated-cryptography.md#download-fips-enabled-binaries).
* Disable automatic binary management in the Snyk preferences.
* Configure the integration to use the binary by setting the CLI Path.
* Configure the Java Runtime to use a FIPS-validated[ JCE (Java Cryptography Extension)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search?SearchMode=Basic\&ModuleName=java\&CertificateStatus=Active\&ValidationYear=0).

### Visual Studio

To make use of FIPS-validated cryptography in the [Snyk Visual Studio integration](../../integrate-with-snyk/ide-tools/visual-studio-extension/) do the following:

* Ensure the [prerequisites](using-fips-validated-cryptography.md#prerequisites-for-fips-cryptography-in-the-cli-and-snyk-language-server) are met.
* [Download the appropriate FIPS-enabled binaries](using-fips-validated-cryptography.md#download-fips-enabled-binaries).
* Disable automatic binary management.
* Configure the integration to use the binary, by setting the CLI Path.

## FIPS-validated cryptography support and use in CI/CD Integrations

FIPS in [CI/CD Integrations](../../integrate-with-snyk/snyk-ci-cd-integrations/) is available only by using a FIPS-enabled CLI directly.

## FIPS-validated cryptography support and use in Package Repositories

The [Snyk Nexus Repository Manager Gatekeeper plugin](../../integrate-with-snyk/gatekeeper-plugins/nexus-repository-manager-gatekeeper-plugin.md) and the [Artifactory Gatekeeper plugin](../../integrate-with-snyk/gatekeeper-plugins/artifactory-gatekeeper-plugin.md) use the Snyk API and run on a Java VM. To make use of FIPS-validated cryptography, configure the Java Runtime to use a FIPS-validated[ JCE (Java Cryptography Extension)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search?SearchMode=Basic\&ModuleName=java\&CertificateStatus=Active\&ValidationYear=0).
