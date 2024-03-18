# Snyk API

{% hint style="info" %}
Snyk API는 Enterprise 요금제에서만 사용할 수 있습니다.

자세한 내용은 [Plans and pricing plans](https://snyk.io/plans)을 참조하세요.
{% endhint %}

Snyk [extensibility and the Snyk API](https://snyk.io/blog/extensibility-and-the-snyk-api/)를 통해 개발자는 Snyk 보안 자동화를 특정 워크플로에 맞게 조정하여 개발자 경험과 플랫폼 거버넌스 모두에서 일관성을 보장할 수 있습니다. [Snyk API v1](./#snyk-api-v1) 및 [Snyk REST API](./#snyk-rest-api)는 [use an API rather than the CLI or an integration](./#when-to-use-the-api-versus-the-cli-or-an-integration)로 결정한 경우 사용할 수 있습니다.

## Snyk API v1

[**Snyk API v1**](https://snyk.docs.apiary.io/) 에는 Snyk에서 정의한 문제에 대해 패키지를 테스트하고 Snyk 제품의 보안 프로세스에 제약을 받지 않고 자체 워크플로에 따라 Snyk 보안 자동화를 제공하는 기능이 있습니다. \
고객과 파트너는 다음과 같은 기능을 수행할 수 있습니다 :

* 취약점 데이터에 액세스
* 프로젝트 및 애플리케이션 스캔
* 교정 조언 받기
* 사용자 데이터를 확인하여 맞춤형 보안 솔루션 구축

## Snyk REST API

{% hint style="info" %}
Snyk REST API는 이전에 Snyk API v3으로 알려졌습니다.
{% endhint %}

[**Snyk REST API**](https://apidocs.snyk.io/)는 엔드포인트가 출시되면 시험해 볼 수 있습니다. 이는 OpenAPI 및 JSON:API 표준을 기반으로 하며 각 엔드포인트 버전이 지정된 API 개발에 대한 혁신적인 접근 방식을 나타냅니다. 자세한 내용은 참조 문서의 [Versioning](https://apidocs.snyk.io/#overview) 를 참조하세요. Snyk REST API는 궁극적으로 API v1을 대체합니다.

## API와 CLI 또는 통합을 사용해야 하는 경우

API, CLI 및 통합의 출력에는 차이가 있을 수 있습니다.

For example, for many package managers using the API will be less accurate than running the Snyk CLI as part of your build pipe or locally on your package. More than one version of a package may fit the requirements in manifest files. Running the CLI locally tests the actual deployed code, and has an accurate snapshot of the dependency versions in use. The API infers a snapshot, with inferior accuracy. Note that the Snyk CLI can output machine-readable JSON (`snyk test --json`).

You can allow Snyk access to your development flow by using Snyk integrations. The advantage is having Snyk monitor every new pull request and suggest fixes by opening new pull requests. You can integrate Snyk directly with your source code management (SCM) tool, or by using a Broker to allow greater security and auditability.

Use the API when you want to customize, integrate, and automate Snyk security as part of your specific workflows.
