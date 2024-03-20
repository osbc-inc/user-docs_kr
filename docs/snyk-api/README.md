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

예를 들어 API를 사용하는 많은 패키지 관리자의 경우 Snyk CLI를 빌드 파이프의 일부로 실행하거나 패키지에서 로컬로 실행하는 것보다 정확성이 떨어집니다. 둘 이상의 패키지 버전이 매니페스트 파일의 요구 사항에 맞을 수 있습니다. CLI를 로컬에서 실행하면 실제 배포된 코드를 테스트하고 사용 중인 종속성 버전의 정확한 스냅샷을 얻을 수 있습니다. API는 정확도가 떨어지는 스냅샷을 추론합니다. Snyk CLI는 기계가 읽을 수 있는 JSON (`snyk test --json`)을 출력할 수 있습니다.

Snyk 통합을 사용하여 Snyk가 개발 흐름에 액세스하도록 허용할 수 있습니다. 장점은 Snyk이 모든 새로운 풀 요청을 모니터링하고 새로운 풀 요청을 열어 수정 사항을 제안한다는 것입니다. Snyk를 소스 코드 관리(SCM) 도구와 직접 통합하거나 Broker를 사용하여 보안 및 감사 가능성을 높일 수 있습니다.

특정 워크플로우의 일부로 Snyk 보안을 사용자 정의, 통합 및 자동화하려는 경우 API를 사용하십시오.
