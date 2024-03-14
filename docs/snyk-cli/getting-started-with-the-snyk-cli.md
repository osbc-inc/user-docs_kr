# Snyk CLI 시작하기

## Snyk 및 Snyk CLI 소개

[Snyk](https://snyk.io/)는 소프트웨어 개발 프로젝트에서 보안 취약점을 검사하고 모니터링하는 개발자 중심의 클라우드 기반 보안 도구입니다. Snyk는 보안 문제에 대해 여러 콘텐츠 유형을 검사합니다.

* [**Snyk Open Source**](https://docs.snyk.io/scan-using-snyk/snyk-open-source): 오픈 소스 취약점을 찾아 자동으로 수정
* [**Snyk Code**](https://docs.snyk.io/scan-using-snyk/snyk-code): 애플리케이션 코드의 취약점을 실시간으로 찾아 수정합니다.
* [**Snyk Container**](https://docs.snyk.io/scan-using-snyk/snyk-container): 컨테이너 이미지 및 Kubernetes 애플리케이션의 취약점을 찾아 수정합니다.
* [**Snyk Infrastructure as Code**](https://docs.snyk.io/scan-using-snyk/scan-infrastructure): Terraform 및 Kubernetes 코드에서 안전하지 않은 구성을 찾아 수정

[Learn more about what Snyk can do and sign up for a free account](https://snyk.io/).

**Snyk CLI는 Snyk의 기능을 개발 워크플로에 도입합니다**. 명령줄이나 IDE에서 로컬로 CLI를 실행할 수 있습니다. CI/CD 파이프라인에서 CLI를 실행할 수도 있습니다. 다음은 Snyk CLI 테스트 명령 출력의 예를 보여줍니다.

<figure><img src="../.gitbook/assets/snyk-cli-screenshot.png" alt="Snyk CLI test command output example"><figcaption><p>Snyk CLI 테스트 명령 출력</p></figcaption></figure>

Snyk CLI 스캐닝은 **다양한 언어와 도구를 지원**합니다. 자세한 내용은 [summary of supported environments](https://docs.snyk.io/getting-started/introducing-snyk#how-can-snyk-work-in-my-environment)을 참조하세요.

이 페이지에서는 CLI를 사용하여 설치, 인증 및 스캔을 시작하는 방법을 설명합니다. Snyk에는 이러한 단계를 안내하는 온보딩 마법사도 있습니다. 데모를 보려면 [Starting with Snyk: an overview of the CLI onboarding flow](https://www.youtube.com/watch?v=adj3VF82-v8).

## Snyk CLI를 설치하고 시스템을 인증하세요.

CLI를 사용하려면, CLI를 설치하고 시스템을 인증해야 합니다.  [Install or update the Snyk CLI](https://docs.snyk.io/snyk-cli/install-the-snyk-cli) 및 [Authenticate the CLI with your account](https://docs.snyk.io/snyk-cli/authenticate-the-cli-with-your-account)을 참조하세요. 각 릴리스의 변경 사항 요약은[release notes](https://github.com/snyk/cli/releases) 를 참조하세요. 코드를 스캔하기 전에, [Code execution warning for Snyk CLI](https://docs.snyk.io/snyk-cli/code-execution-warning-for-snyk-cli)를 검토하세요.

**참고:** 오픈 소스 검사에 CLI를 사용하려면, 먼저 패키지 관리자를 설치해야 합니다. Gradle 또는 Maven과 같은 필요한 타사 도구가 `PATH`에 있어야 합니다.

IDE 또는 CI/CD 환경에서 CLI를 사용할 수 있습니다. 자세한 내용은, [Install as part of a Snyk integration](https://docs.snyk.io/snyk-cli/install-the-snyk-cli#install-as-a-part-of-a-snyk-integration)를 참조하세요.

## 설치 테스트

인증 후, **설치를 테스트**할 수 있습니다. 빠른 테스트를 위해, `snyk --help`를 실행하세요.

또는, `snyk test ionic`과 같은 공개 npm 패키지에서 **빠른 테스트**를 수행할 수 있습니다.

터미널에서 `test` 명령 **보고서**를 살펴보세요. 보고서에는 Snyk이 패키지에서 발견한 취약점이 표시됩니다. 발견된 각 문제에 대해 Snyk는 문제의 심각도를 보고합니다. 자세한 설명에 대한 링크를 제공하며, 취약한 모듈이 시스템에 유입된 경로를 보고하고, 문제 해결 방법에 대한 지침을 제공합니다.

## 개발 프로젝트 스캔

**참고:** Snyk CLI를 사용하여 오픈 소스 프로젝트의 취약점을 테스트하기 전에, 제한된 예외를 제외하고, **프로젝트를 빌드**해야 합니다. 자세한 내용은, [Which Projects must be built before testing with CLI?](https://support.snyk.io/hc/en-us/articles/360015552617-Which-projects-must-be-built-before-testing-with-CLI-)를 참조하세요.

또한, Snyk CLI를 사용하기 전에 오픈 소스 프로젝트의 언어에 따라 **언어 환경을 설정**해야 할 수도 있습니다. 자세한 내용은 [Supported languages, frameworks, and feature availability overview](https://docs.snyk.io/scan-using-snyk/supported-languages-and-frameworks/supported-languages-frameworks-and-feature-availability-overview)를 참조하세요.

CLI를 설치하고 시스템을 인증한 후, **오픈 소스 프로젝트를 스캔하려면** `cd /my/project/` 를 사용하여 현재 디렉터리를 `package.json`, `pom.xml`, `composer.lock`과 같은 지원되는 패키지 매니페스트 파일이 포함된 `a`폴더로 변경합니다. 그런 다음 `snyk test`를 실행하십시오. 경로 및 수정 지침을 포함하여 식별된 모든 취약점이 나열됩니다.

**소스 코드**를 스캔하려면 `snyk code test`를 실행하세요.

실행 중인 태그로 **Docker 이미지를 스캔**할 수 있습니다, (예: `snyk container test ubuntu:18.04`)

Kubernetes(K8s) 파일을 스캔하려면 다음을 실행하세요 :\
`snyk iac test /path/to/kubernetes_file.yaml`

Snyk CLI를 사용하여 각 콘텐츠 유형을 검사하는 방법에 대한 자세한 내용은 다음을 참조하세요:

* [Snyk CLI for Snyk Open Source](https://docs.snyk.io/snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-open-source)와 [`test`](https://docs.snyk.io/snyk-cli/commands/test) 및 [`monitor`](https://docs.snyk.io/snyk-cli/commands/monitor) 명령에 대한 CLI 도움말
* [Snyk CLI for Snyk Code](https://docs.snyk.io/snyk-cli/commands/code) 및 [Snyk Code CLI help](https://docs.snyk.io/snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-snyk-code)
* Docker 스캐닝을 포함한, [Snyk CLI for Snyk Container](https://docs.snyk.io/snyk-cli/commands/container) 및 [Snyk Container CLI help](https://docs.snyk.io/snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-snyk-container)
* Terraform 및 Kubernetes(K8s) 프로젝트를 포함한 [Snyk CLI for Snyk IaC](https://docs.snyk.io/snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-iac) 및 [Snyk IAC CLI help](https://docs.snyk.io/snyk-cli/commands/iac)

## 오픈 소스 또는 컨테이너 프로젝트 모니터링

Snyk는 오픈 소스 또는 컨테이너 통합 SCM 프로젝트를 주기적으로 모니터링하고 새로운 취약점에 대해 경고할 수 있습니다. 모니터링할 프로젝트를 설정하려면,`snyk monitor` 또는 `snyk container monitor`를 실행하세요.

이렇게 하면 Snyk가 정기적으로 코드를 스캔할 수 있도록 현재 종속성에 대한 스냅샷이 생성됩니다. 그런 다음 Snyk는 새로 공개된 취약점이 도입되거나 이전에 사용할 수 없었던 패치 또는 업그레이드 경로가 생성될 때 이에 대해 경고할 수 있습니다. 다음 코드는 `snyk monitor` 의 출력 예를 보여줍니다.

```
> snyk monitor
Monitoring /project (project-name)...

Explore this snapshot at 
https://app.snyk.io/org/my-org/project/29361c2c-9005-4692
-8df4-88f1c040fa7c/history/e1c994b3-de5d-482b-9281-eab4236c851e

Notifications about newly disclosed issues related to these 
dependencies will be emailed to you.
```

You can log in to your Snyk account and navigate to the [Projects page](https://app.snyk.io/projects) to find the latest snapshot and scan results:

<figure><img src="../.gitbook/assets/monitor (1).png" alt="Snyk monitor snapshot and scan results"><figcaption><p>Snyk monitor snapshot and scan results</p></figcaption></figure>

For more information, see [Monitor your Projects at regular intervals](https://docs.snyk.io/snyk-cli/scan-and-maintain-projects-using-the-cli/monitor-your-projects-at-regular-intervals).

## Running out of tests

Snyk allows unlimited tests for public repositories. If you are on the Free plan, you have a limited number of tests per month. Paid plans have unlimited tests on private and public repositories. If you are on the Free plan and notice that your test count is quickly being used, even with public repositories, you can remedy this by telling Snyk the public url of the repository that is being scanned by the Snyk CLI. This ensures that Snyk does not count a public repository towards the test limits.

If you run out of tests on an open-source Project, follow these steps:

* Run `snyk monitor`.
* Open the Snyk UI and navigate to the **settings** of the Project.
* Enter the URL of your open-source repository in **Git remote URL**.

## Additional information about the Snyk CLI

Run `snyk help` or see the [CLI commands and options summary](https://docs.snyk.io/snyk-cli/cli-commands-and-options-summary).

See the course [Introduction to the Snyk CLI](https://learn.snyk.io/lesson/snyk-cli/https://learn.snyk.io/lesson/snyk-cli/) for a quick video training session.

Snyk also provides a [cheat sheet](https://res.cloudinary.com/snyk/image/upload/v1664236143/cheat-sheets/cheat-sheet-snyk-cli-v3.pdf) ([blog post](https://snyk.io/blog/snyk-cli-cheat-sheet/)) and a [video tutorial](https://www.youtube.com/watch?v=xp\_LtchEkT8).

In particular, see the information about the following options that you may find useful:

* `--severity-threshold=low|medium|high|critical`: Report only vulnerabilities of the specified level or higher.
* `--json`: Print results in JSON format.
* `--all-projects`: Auto-detect all Projects in the working directory.

For detailed information about the CLI, see the [CLI docs](https://docs.snyk.io/snyk-cli).

## Getting support for the Snyk CLI

[Submit a ticket](https://support.snyk.io/hc/en-us/requests/new) to Snyk support whenever you need help with the Snyk CLI or Snyk in general. Note that Snyk support does not actively monitor GitHub Issues on any [Snyk development project](https://github.com/snyk).

## Contributing to the Snyk CLI

The Snyk CLI project is open-source, but Snyk does not encourage outside contributors.

You may look into [design decisions for the Snyk CLI](https://github.com/snyk/snyk/blob/master/help/\_about-this-project/README.md).

The Snyk CLI repository is a monorepo that also covers other projects and tools, such as [@snyk/protect](https://github.com/snyk/snyk/tree/master/packages/snyk-protect), also available at [npm package for snyk-protect command](https://www.npmjs.com/package/@snyk/protect).

## Security

For any security issues or concerns, see the [SECURITY.md](https://github.com/snyk/snyk/blob/master/SECURITY.md) file in the GitHub repository.
