# Snyk Jumpstart 서비스 설명

## Snyk Jumpstart 개요

Snyk컨설턴트가 계정 구성 지원 서비스(“Jumpstart 서비스”)를 통해 고객이 Snyk 제품을 빠르게 설정할 수 있도록 도와주는 서비스를 제공합니다. 이 서비스는 팀을 위한 구성 안내와 함께 지식 전달로 구성됩니다.

목표는 애플리케이션 보안 노력을 계속할 수 있도록 잘 준비된 Snyk와 고객 팀의 작업 환경을 구축하는 것입니다.

## 권장 대상

* Snyk 제품 설정에 도움이 필요한 팀
* Snyk를 처음 사용하고 보안 스캔에 대한 경험이 부족한 팀
* 계약 후에도 스스로 Snyk을 확장하고 유지 관리하는 데 익숙한 초보자

## Jumpstart Services 설명

Snyk 컨설턴트는 고객에게 Jumpstart서비스의 일부로 원격으로 Snyk 설치와 관련된 다음 서비스를 제공합니다. 점프스타트 서비스는 이 서비스와 동시에 주문 양식에서 구매한 Snyk 애플리케이션에 대해서만 제공됩니다. 고객이 구매하지 않은 Snyk 서비스에 대한 언급은 달리 명시되지 않는 한 생략됩니다.

1. [사전 참여 계획 및 준비](snyk-jumpstart-services-description.md#pre-engagement-planning-and-preparation)
   1. 제품 모듈별 결과물 검토
   2. 제품 모듈별 사전 요구 사항 검토
   3. 고객 전제 조건에 따라 고객 연락처의 풀타임 사용 가능 여부 확인
2. [Snyk 플랫폼 구성 ](snyk-jumpstart-services-description.md#snyk-platform-configuration)
3. [Snyk 오픈소스 구성 ](snyk-jumpstart-services-description.md#snyk-open-source-configuration)
4. [Snyk 코드 구성 ](snyk-jumpstart-services-description.md#snyk-code-configuration)
5. [Snyk 컨테이너  구성 ](snyk-jumpstart-services-description.md#snyk-container-configuration)
6. [Snyk IaC+ 구성 ](snyk-jumpstart-services-description.md#snyk-iac-configuration)
7. [Snyk 앱리스크 에센셜 우선순위 구성 ](snyk-jumpstart-services-description.md#snyk-apprisk-essentials-prioritization-configuration)

## 사전 참여 계획 및 준비

### 사전 참여 통화

고객이 참여 기간 동안 완료된 결과물과 함께 참여 시작에 필요한 전제 조건을 이해할 수 있도록 여기에 나열된 Jumpstart Service를 시작하기 전에 사전 참여 통화를 진행합니다. 각 제품 모듈의 리소스, 가용성 및 결과물을 포함한 고객 전제 조건이 검토 및 확인됩니다. 고객은 이러한 전제 조건을 준수하는 것이 전적으로 자신의 책임임을 인정하며, Snyk은 고객이 이러한 전제 조건을 충족하지 못하여 점프스타트 서비스를 제공하지 못하거나 지연되는 것에 대해 책임을 지지 않습니다.

## Snyk 플랫폼  구성&#x20;

### 제공 방식 - Snyk 플랫폼 구성

Snyk 전달 방식은 Snyk을 통해 신속한 가치 실현을 보장하도록 설계되었습니다.양사의 협업을 통해 Snyk은 고객이 기본 구성을 설정할 수 있도록 안내하고 이 설정을 다른 애플리케이션 및 통합으로 확장할 수 있도록 지원합니다. 처음부터 Snyk을 올바르게 설정하면 개발자의 채택률이 향상되고 장기적인 성공의 기반을 마련할 수 있습니다.

#### 기본SSO 구성 및 사용자 지정 매핑

Snyk 컨설턴트는 고객과 협력하여 원하는 ID 공급자(IdP)가 제공한 데이터를 기반으로 동적으로 할당된 사용자를 Snyk 그룹 및 조직에 사용자 지정 매핑하는 것과 함께 SAML, Azure AD, OIDC 또는 ADFS 연결을 통해 SSO를 구성하여 확장된 사용자 프로비저닝 및 액세스 모델을 설정합니다.

#### 템플릿 조직 구성

Snyk 컨설턴트는 고객과 협력하여 알림 설정, 언어 설정, Snyk 계정 구조를 구성합니다. 고객이 구성 세부 사항을 이해하고 유지 관리할 수 있도록 고객과 함께 구성 세부 사항을 검토하는 데 시간을 할애합니다.

#### 관리자 교육

고객 관리자 사용자가 보안 프로그램의 성숙도에 따라 Snyk에서 필수 설정을 구성하는 방법을 알 수 있도록 60분간 교육 세션을 진행합니다.

교육 주제는 다음과 같습니다:

* Snyk UI 탐색하기
* 통합 설정
* 알림 설정
* 새로운 기능 사용
* 사용자 역할 및 권한
* 이슈 필터링 및 우선 순위 지정
* Snyk 보고에서 결과 보기
* 문제 해결 워크플로우
* Ignoring issues in the Snyk UI
* PR Check walkthrough
* Security and license policie
* Accessing additional training materials (learn.snyk.io)
* Project Collections and views

### Target Initiatives - Snyk Platform configuration

<table><thead><tr><th width="248">Platform - initial setup</th><th width="410">Outcome</th><th>Hours</th></tr></thead><tbody><tr><td>Base SSO connection configuration</td><td>Users can access Snyk based on role.</td><td>1</td></tr><tr><td>SSO Custom Mapping</td><td>Users can access Snyk based on role.</td><td>4</td></tr><tr><td>(Template Org) Custom Roles and service account configuration</td><td>Provide a templated organization to replicate and scale your setup of Snyk quickly.</td><td>.5</td></tr><tr><td>(Template Org) Notification configuration</td><td>Provide a templated organization to replicate and scale your setup of Snyk quickly.</td><td>.5</td></tr><tr><td>(Template Org) Language settings configuration</td><td></td><td>.5</td></tr><tr><td>(Template Org) Jira or Slack App configuration</td><td></td><td>1</td></tr><tr><td>(Template Org) Account Organization and Group configuration</td><td></td><td>.5</td></tr><tr><td>Admin training</td><td></td><td>1</td></tr><tr><td><strong>TOTAL HOURS</strong></td><td></td><td><strong>9</strong></td></tr></tbody></table>

## Snyk Open Source configuration

### Delivery approach - Snyk Open Source configuration

The Snyk delivery method is designed to ensure rapid value realization with Snyk. Throughout our collaboration, Snyk will guide the Customer in setting up a foundational configuration and equip the Customer to expand this setup to other applications and integrations. Ensuring Snyk is correctly set up from the outset improves developer adoption and paves the way for long-term success.

#### Repository import

The Snyk Consultant will work with the Customer to import their repositories into Snyk (up to 50 targets) either through the UI import functionality or through the [API Import tool](../../snyk-api-info/other-tools/tool-snyk-api-import/).

#### SCM integration settings

The Snyk Consultant will work with the Customer to configure SCM integration settings based on the Customer’s desired gating strategy.

#### SCM Broker installation

The Snyk Consultant will work with the Customer to install the Snyk Broker in a pre-determined environment that follows the [Snyk Broker system requirements](../../enterprise-configuration/snyk-broker/prepare-snyk-broker-for-deployment.md).

#### Snyk API Import and SCM snyc

The Consultant will review the Snyk API Import script to ensure the Customer understands how to import additional Projects into Snyk and keep their SCM integration in sync with incoming changes to manifests.

#### Single pipeline configuration (dIrect Integration or CLI)

The Snyk Consultant will work with the Customer to configure a single pipeline to run the `snyk test` and `snyk monitor` commands to provide the Customer with an understanding of how to configure additional pipeline scans.

#### SBOM walkthrough (API and CLI)

The Snyk Consultant will educate the Customer on creating an SBOM through the Snyk API and the Snyk CLI.

#### Interpreting and actioning Open Source results

The Snyk Consultant will educate the Customer on understanding Snyk Open Source results through the CLI and Snyk UI and how to manage Snyk Open Source results using Snyk Reporting.

#### Documentation close-out

The Customer will be provided with a document that provides a comprehensive overview of the professional services rendered by Snyk during the engagement. Spanning the period from the engagement's start to its conclusion, the document offers insights into account configuration, repository onboarding, and integrations. More than just a retrospective, the document puts forth practical recommendations and actionable next steps that will aid the Customer in optimizing their use of Snyk for improved application security. By detailing both the accomplishments and the roadmap ahead, this document provides an essential guide for Customers to realize the full potential of their investment in Snyk.

### Target initiatives - Snyk Open Source

<table><thead><tr><th width="300">Snyk Open Source configuration</th><th width="306">Outcome</th><th>Hours</th></tr></thead><tbody><tr><td>Repository import (SCM-only up to 50 targets)</td><td>Import a maximum of 50 targets into Snyk using a <a href="../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/">supported SCM integration</a> (GitHub, Azure Repos, Bitbucket, GitLab).</td><td>2</td></tr><tr><td>SCM integration settings</td><td>Configure SCM integration settings to the Customer’s desired gating settings.</td><td>.5</td></tr><tr><td>SCM Broker installation</td><td>Install SCM Broker in a pre-determined customer environment based on Snyk system requirements.</td><td>2</td></tr><tr><td>Snyk Tools - API Import and SCM Sync</td><td>Gain an understanding of how to use the Snyk API Import script to import additional targets and keep repos in Sync (GHE only).</td><td>2</td></tr><tr><td>Single pipeline configuration (direct integration OR CLI)</td><td>Configure a pipeline to run <code>snyk test</code> and <code>snyk monito</code>r.</td><td>3</td></tr><tr><td>SBOM Walkthrough (CLI and API)</td><td>Gain an understanding of generating an SBOM through Snyk using the CLI and API.</td><td>1</td></tr><tr><td>Interpreting and actioning Open Source results</td><td>Gain an understanding of how to view Open Source results in Snyk Reporting along with managing issues.</td><td>1.5</td></tr><tr><td>Documentation close-out</td><td>Gain an understanding of work completed along with a runbook for onboarding additional projects.</td><td>2</td></tr><tr><td><strong>TOTAL HOURS</strong></td><td></td><td><strong>14</strong></td></tr></tbody></table>

## Snyk Code configuration

### Delivery approach - Snyk Code configuration

The Snyk delivery method is tailored to ensure rapid value realization with Snyk. Throughout our collaboration, Snyk will guide the Customer in setting up a foundational configuration and equip the Customer to expand this setup to other applications and integrations. Ensuring Snyk is correctly set up from the outset improves developer adoption and paves the way for long-term success.

#### Repository import

The Snyk Consultant will work with the Customer to import their repositories into Snyk (up to 50 targets) either through the UI import functionality or through the [API Import tool](../../snyk-api-info/other-tools/tool-snyk-api-import/). Repos will be imported into Snyk Organizations that either mirror the Customer’s SCM organization structure or through custom Organizations configured in the API-import script.

#### SCM integration settings

The Snyk Consultant will work with the Customer to configure SCM integration settings based on the Customer’s desired gating strategy.

#### SCM Broker installation

The Snyk Consultant will work with the Customer to install the Snyk Broker in a pre-determined environment that follows the [Snyk Broker system requirements](../../enterprise-configuration/snyk-broker/prepare-snyk-broker-for-deployment.md).

#### Snyk API Import and SCM Sync

The Consultant will review the Snyk API Import script to ensure the Customer understands how to import additional Projects into Snyk and keep their SCM integration in sync with incoming changes to manifests.

#### Interpreting and actioning Code results

The Snyk Consultant will educate the Customer on understanding Snyk Code results through the CLI and Snyk UI and how to manage Snyk Code results using Snyk Reporting.

#### Documentation close-out

The Customer will be provided with a document that provides a comprehensive overview of the professional services rendered by Snyk during the engagement. Spanning the period from the engagement's start to its conclusion, the document offers insights into account configuration, repository onboarding, and integrations. More than just a retrospective, the document puts forth practical recommendations and actionable next steps that will aid the Customer in optimizing their use of Snyk for improved application security. By detailing both the accomplishments and the roadmap ahead, this document provides an essential guide for customers to realize the full potential of their investment in Snyk.

### Target initiatives - Snyk Code

<table><thead><tr><th width="250">Snyk Code Configuration</th><th>Outcome</th><th>Hours</th></tr></thead><tbody><tr><td>Repository import (SCM-only up to 50 targets)</td><td>Import a maximum of 50 targets into Snyk using a <a href="../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/">supported SCM Integration</a>.</td><td>2</td></tr><tr><td>SCM integration settings</td><td>Configure SCM integration settings to the Customer’s desired gating settings.</td><td>.5</td></tr><tr><td>SCM Broker installation</td><td>Install SCM Broker in a pre-determined customer environment based on Snyk system requirements.</td><td>2</td></tr><tr><td>Snyk Tools - API Import and SCM Sync</td><td>Gain an understanding of how to use the Snyk API Import script to import additional targets and keep their repos in sync (GHE only).</td><td>2</td></tr><tr><td>Interpreting and actioning Code results</td><td>Gain an understanding of how to view Code results in Snyk Reporting along with managing issues.</td><td>1.5</td></tr><tr><td>Documentation close-out</td><td>Gain an understanding of work completed along with a runbook for onboarding additional projects.</td><td>2</td></tr><tr><td><strong>TOTAL HOURS</strong></td><td></td><td><strong>10</strong></td></tr></tbody></table>

## Snyk Container configuration

### Delivery approach - Snyk Container configuration

The Snyk delivery method is tailored to ensure rapid value realization with Snyk. Throughout our collaboration, Snyk will guide the Customer in setting up a foundational configuration and equip them to expand this setup to other applications and integrations. Ensuring Snyk is correctly set up from the outset improves developer adoption and paves the way for long-term success.

#### Single Broker Container Registry installation and configuration

The Snyk Consultant will work with the Customer to configure and install Snyk Broker if needed for a single [supported Container Registry](https://snyk.io/integrations/?type=container-registries) integration.

#### Container Registry import

The Snyk Consultant will work with the Customer to import their container images into Snyk (up to 50 targets) through the UI import functionality.

#### Interpreting and actioning Snyk Container results

The Snyk Consultant will educate the Customer on understanding Snyk Container results through the CLI and Snyk UI and how to manage Snyk Container results using Snyk Reporting.

#### Single CI/CD CLI configuration

The Snyk Consultant will work with the Customer to configure a single pipeline to run the snyk test and `snyk container monitor` commands to provide the Customer with an understanding of how to configure additional pipeline scans.

#### Custom Base Images walkthrough (UI and CLI)

The Snyk Consultant will educate the Customer on how to use the Snyk Custom Base Image Recommendation functionality both in the Snyk UI and CLI.

#### Documentation close-out

The Customer will be provided with a document that provides a comprehensive overview of the professional services rendered by Snyk during the engagement. Spanning the period from the engagement's start to its conclusion, the document offers insights into account configuration, repository onboarding, and integrations. More than just a retrospective, the document puts forth practical recommendations and actionable next steps that will aid Customer in optimizing their use of Snyk for improved application security. By detailing both the accomplishments and the roadmap ahead, this document provides an essential guide for customers to realize the full potential of their investment in Snyk.

### Target initiatives - Snyk Container

<table><thead><tr><th width="269">Snyk Container Configuration</th><th>Outcome</th><th>Hours</th></tr></thead><tbody><tr><td>Single Broker Container Registry installation and configuration</td><td>Single Broker installed and configured for a <a href="https://snyk.io/integrations/?type=container-registries">Supported Container Registry</a>.</td><td>3</td></tr><tr><td>Container Registry import (up to 50 targets)</td><td>Import a maximum of 50 targets into Snyk using a <a href="https://snyk.io/integrations/?type=container-registries">Supported Container Registry</a>.</td><td>2</td></tr><tr><td>Interpreting and actioning Container results</td><td>Gain an understanding of how to view Container results in Snyk Reporting along with managing issues.</td><td>2</td></tr><tr><td>Single CI/CD CLI rntegration</td><td>Configure a single pipeline to <code>test</code> and <code>monitor</code> for Snyk Container.</td><td>3</td></tr><tr><td>Custom Base Images walkthrough (UI and CLI)</td><td>Gain an understanding of how to use the Custom Base Image Recommendations functionality through the UI and CLI.</td><td>2</td></tr><tr><td>Documentation close-out</td><td>Gain an understanding of work completed along with a runbook for onboarding additional projects.</td><td>2</td></tr><tr><td><strong>TOTAL HOURS</strong></td><td></td><td><strong>14</strong></td></tr></tbody></table>

## Snyk IAC+ Configuration

### Delivery approach - Snyk IAC+ configuration

#### Repository import

The Snyk Consultant will work with the Customer to import their repositories into Snyk (up to 50 targets) using the UI import functionality to import into the Customer’s SCM integration.

#### Interpreting and actioning IAC+ results

The Snyk Consultant will educate the Customer on understanding Snyk IaC+ results through the CLI and Snyk UI and how to manage Snyk IAC+ results using Snyk Reporting.

#### SCM integration settings

The Snyk Consultant will work with the Customer to configure SCM Integration settings based on the Customer’s desired gating strategy.

#### SCM Broker installation

The Snyk Consultant will work with the Customer to install the Snyk Broker in a predetermined environment that follows the [Snyk Broker system requirements](../../enterprise-configuration/snyk-broker/prepare-snyk-broker-for-deployment.md).

#### Single pipeline CI/CD CLI configuration

The Snyk Consultant will work with the Customer to configure a single pipeline to run the `snyk iac test` command to provide the Customer with an understanding of how to configure additional pipeline scans and fix cloud issues.

#### Configure cloud environments (up to three environments)

The Snyk Consultant will work with the Customer to configure up to three (3) Cloud environments (Azure, GCP, AWS) in Snyk using the UI.

#### Documentation close-out

The customer will be provided with a document that provides a comprehensive overview of the professional services rendered by Snyk during the engagement. Spanning the period from the engagement's start to its conclusion, the document offers insights into account configuration, repository onboarding, and integrations. More than just a retrospective, the document puts forth practical recommendations and actionable next steps that will aid the Customer in optimizing their use of Snyk for improved application security. By detailing both the accomplishments and the roadmap ahead, this document provides an essential guide for customers to realize the full potential of their investment in Snyk.

### Target initiatives - Snyk IAC+ configuration

| Snyk IAC+ configuration                                 | Outcome                                                                                                             | Hours  |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------ |
| Repository import (SCM only up to 50 targets)           | Import a maximum of 50 targets into Snyk via a [supported SCM Integration](https://snyk.io/integrations/?type=scm). | 2      |
| Interpreting and actioning IAC+ Results                 | Gain an understanding of how to view IaC+ results in Snyk Reporting along with managing misconfigurations.          | 1.5    |
| SCM integration settings                                | Configure SCM integration settings to the Customer’s desired gating settings.                                       | .5     |
| SCM Broker installation                                 | Install SCM Broker in a pre-determined customer environment based on Snyk System Requirements.                      | 2      |
| Single Pipeline CI/CD CLI configuration                 | Configure a single pipeline to test and provide a report for Snyk IAC+.                                             | 4      |
| Configure Cloud environments (up to three environments) | Customer will configure up to three Cloud Eenvironments (Azure, GCP, AWS) with Snyk.                                | 3      |
| Documentation close-out                                 | Gain an understanding of work completed along with a runbook for onboarding additional projects.                    | 2      |
| **TOTAL HOURS**                                         |                                                                                                                     | **15** |

## Snyk AppRisk Essentials prioritization configuration

This portion of the Jumpstart service is applicable to Customers looking to achieve [risk-based prioritization](../../manage-risk/snyk-apprisk/risk-based-prioritization-for-snyk-apprisk/).

### Delivery approach - Snyk AppRisk Essentials configuration

#### Coverage and visibility configuration

The Snyk Consultant will work with the Customer to configure their Source Code Management system integration(s) and create two starter policies to show coverage gaps and asset classification, respectively.

#### **Walkthrough of coverage and visibility use cases in AppRisk**

The Snyk Consultant will educate the Customer on how to identify assets that are not currently being scanned by Snyk, as well as how to group assets and issues based on asset classification.

#### Snyk Container - single CICD CLI configuration

The Snyk Consultant will work with the Customer to configure a single pipeline to run the `snyk container test` and `snyk container monitor` commands and provide the Customer with an understanding of how to configure additional pipeline scans.

#### **Snyk Container - single Broker Container Registry installation and configuration**

The Snyk Consultant will work with the Customer to configure and install Broker, if needed, for a single [supported Container Registry](https://snyk.io/integrations/?type=container-registries) integration.

#### **Snyk Container - Container Registry Import**

The Snyk Consultant will work with the Customer to import the set of Container Rargets for container images running in a single Kubernetes cluster either through UI Import functionality or using the Snyk API Import tool.

#### **Single Kubernetes Connector for AppRisk Installation**

The Snyk Consultant will work with the Customer to install the [Kubernetes Connector for AppRisk](../../manage-risk/snyk-apprisk/risk-based-prioritization-for-snyk-apprisk/prioritization-setup/prioritization-setup-kubernetes-connector.md) on a predetermined Kubernetes Cluster that meets the Snyk system requirements.

#### **Walkthrough of Prioritized Issues in AppRisk Dashboard**

The Snyk Consultant will educate the Customer on how to filter and prioritize issues in the AppRisk Dashboard using deployed and public-facing risk factors.

#### Documentation close-out

The Customer will be provided with a document that provides a comprehensive overview of the professional services rendered by Snyk during the engagement. Spanning the period from the engagement's start to its conclusion, it offers insights into account configuration, repository onboarding, and integrations. More than just a retrospective, the document puts forth practical recommendations and actionable next steps that will aid Customer in optimizing their use of Snyk for improved application security. By detailing both the accomplishments and the roadmap ahead, this document is an essential guide for customers to realize the full potential of their investment in Snyk.

### Target initiatives - Snyk AppRisk Essentials prioritization

<table><thead><tr><th width="322">Snyk AppRisk Essentials Prioritization Configuration</th><th width="299">Outcome</th><th>Hours</th></tr></thead><tbody><tr><td>Coverage and visibility configuration</td><td>SCM integration is configured in AppRisk and two starter policies are created to show coverage gaps and asset classifications respectively.</td><td>2</td></tr><tr><td>Walk-through of coverage and visibility use cases in AppRisk</td><td>Gain an understanding of how to identify assets that are not currently being scanned by one more Snyk controls, as well as how to group assets and issues based on asset classification</td><td>.5</td></tr><tr><td><p>Snyk Container for AppRisk *</p><p>Setup of one of the following integration methods</p><ul><li>Single Broker Container Registry installation and donfiguration</li><li>Single CI/CD CLI Integration</li></ul></td><td><p>One of:</p><p>Single Broker installed and configured for a <a href="https://snyk.io/integrations/?type=container-registries">Supported Container Registry</a> or</p><p>configure a single pipeline to <code>test</code> and <code>monitor</code> for Snyk Container, including application of component tags according to the <a href="../../manage-risk/snyk-apprisk/risk-based-prioritization-for-snyk-apprisk/prioritization-setup/prioritization-setup-associating-snyk-open-source-code-and-container-projects.md">product requirements</a>.</p></td><td>2</td></tr><tr><td><p>Snyk Container for AppRisk *</p><p>Container Registry import</p></td><td><p>Import the set of Container targets</p><p>into Snyk via a <a href="https://snyk.io/integrations/?type=container-registries">Supported Container Registry</a>.</p></td><td>2</td></tr><tr><td>Single Kubernetes Connector for AppRisk installation</td><td><a href="../../manage-risk/snyk-apprisk/risk-based-prioritization-for-snyk-apprisk/prioritization-setup/prioritization-setup-kubernetes-connector.md">Kubernetes connector for AppRisk</a> is installed in a single Kubernetes cluster</td><td>3</td></tr><tr><td>Component tagging automation</td><td>Tagging rules are configured for Snyk Open Source, Code, and Container projects (if using Container Registry integration) according to the <a href="../../manage-risk/snyk-apprisk/risk-based-prioritization-for-snyk-apprisk/prioritization-setup/prioritization-setup-associating-snyk-open-source-code-and-container-projects.md">product requirements</a>.<br>Application of tags is automed through the<a href="https://github.com/snyk-labs/snyk-tags-tool/blob/main/docs/components.md"> snyk-tags</a> tool in the Customer environment to tag new projects periodically.</td><td>8</td></tr><tr><td>Walk-through of prioritized issues in AppRisk</td><td>Gain an understanding of how to filter and prioritize issues in the AppRisk Dashboard using deployed and public-facing risk factors.</td><td>1.5</td></tr><tr><td>Documentation close-out</td><td>Gain an understanding of work completed along with a runbook for onboarding additional projects.</td><td>2</td></tr><tr><td><strong>TOTAL HOURS</strong></td><td></td><td><strong>21</strong></td></tr></tbody></table>

{% hint style="info" %}
\* _Snyk Container for AppRisk_ steps are required when the Customer does not already have Snyk Container on contract.
{% endhint %}

## Timeline for Snyk Jumpstart delivery

Snyk Jumpstart delivery will include initial platform configuration and each product module that has been purchased. Modules have been designed to be delivered consecutively and over consecutive hours.

| Product                                | Total time   |
| -------------------------------------- | ------------ |
| Snyk Platform configuration            | 9 hours      |
| Snyk Open Source                       | 14 hours     |
| Snyk Code                              | 10 hours     |
| Snyk Container                         | 14 hours     |
| Snyk IAC+                              | 15 hours     |
| Snyk AppRisk Essentials Prioritization | 21 hours     |
| **TOTAL HOURS**                        | **83 hours** |

## Additional terms

The fees for this project will be a fixed price. Services will be invoiced in full at the time of purchase and are non-refundable.

The Customer will engage Snyk for a kickoff call within 30 days of the contract start date at a time that is mutually agreed upon by the parties. Snyk Jumpstart must be delivered within 120 days of execution of the applicable Order Form, regardless of when or if the Customer engages Snyk for the kickoff call.

Unless otherwise agreed to by the parties in writing, a) services must be scheduled over consecutive hours; b) product modules will be delivered consecutively; and c) scheduled during normal business hours.

All services will be performed remotely. Any onsite time requires Snyk’s prior consent and will be subject to additional fees and expenses to be paid in accordance with the Snyk Travel and Expense Policy.

## Key assumptions

The following assumptions are reflected in the services outlined in this Jumpstart Services description:

1. All services will be performed remotely using video conferencing software such as Zoom.
2. The Customer must provide prompt feedback on all deliverables.
3. The Customer’s Snyk subject matter expert must be available to work remotely with the Snyk consultant for the entirety of the engagement.
4. The Customer will provide Snyk with documentation and access to subject matter experts for non-Snyk systems and software if required within the scope of the engagement.
5. The Customer will have identified key personnel prior to the beginning of the engagement.
6. Services will be scheduled and delivered during Snyk’s normal business hours, 8 am to 5 pm local time.
7. The Customer will provide prompt access to all systems and resources that Snyk will need in order to complete the work.
8. Snyk does not provide support for third-party software that is used as part of the Snyk solution, such as version control systems, repository management, trouble ticketing systems, packaging, and other software that is not part of the Snyk stack.
9. If a Broker is required, the Customer will have all system requirements before services start.
