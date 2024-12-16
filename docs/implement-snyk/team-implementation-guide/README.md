# 팀 구현 가이드

to teams of up to 10 members. Snyk을 사용하여 팀 성과를 가속화하세요. 이 가이드는 팀을 위해 Snyk을 구현하는 데 도움을 드리기 위한 것입니다. 팀 플랜은 최대 10명의 팀원에게 적용됩니다.

우리는 대부분의 비즈니스가 이러한 인식을 가지고 있다는 것부터 시작합니다:

* 기존 소프트웨어에 백로그 이슈가 있는 경우
* 지속적으로 새로운 소프트웨어를 만들고 있으며 새로운 코드를 보호해야 하는 경우

## 일반적인 타임라인

며칠 안에 팀을 위해 Snyk를 구현할 수 있습니다. 구현 후 곧바로 Git 통합을 사용하여 Snyk로 스캔을 시작할 수 있습니다. 자세한 내용은 [Getting started](../../getting-started/) 및 [Start scanning using the CLI, Web UI, or API](../../scan-with-snyk/start-scanning-using-the-cli-web-ui-or-api.md)를 참조하세요. 팀이 Snyk를 배포하기 위한 주요 지침은 프로젝트를 온보딩하고, 중요한 프로젝트에 Snyk 기능을 시범 적용하여 워크플로에 가장 적합한지 확인한 다음, 다른 프로젝트에 활성화하여 정기적인 커뮤니케이션을 통해 팀에 기대치를 알려주는 것입니다.

## Implementation strategy overview

This guide is composed of multiple phases, outlining a series of actions configuring your account, as well as actions outside the system, that align with the following goals:

* [Achieve visibility](./#achieve-visibility)
* [Achieve prevention and drive developer adoption](./#achieve-prevention-and-drive-developer-adoption)
* [Fix the backlog and triage issues](./#fix-the-backlog-and-triage-issues)

### Achieve visibility

If you focus on visibility first, you can get a clear sense of the security issues, but without always fixing them.

{% hint style="info" %}
This does not stop you from fixing issues using Snyk. You can start fixing issues early, but the emphasis is to avoid blocking development early on, build trust, and slowly introduce gating in later phases, usually the prevention phase. This is true of the smallest or largest teams - communication is key.
{% endhint %}

Visibility achieves a broad view of security across your application portfolio, avoids Snyk scans being seen as a blocker, and minimizes impact on development processes.

This visibility helps build trust while rolling out Snyk. With the Team plan, this equates to onboarding your projects through Git repository and disabling PR Checks/Auto PRs in the integration settings. Choose an important project and enable PR checks after communicating with the relevant team members. This guide details this later on.

### Achieve prevention and drive developer adoption

Next is the prevention stage. You should stop new security issues from being added to your applications. During this stage, you can put controls in place to allow developers to see issues in their pipelines using Pull Request (PR)/Merge Request (MR) checks, and checks in the pipeline that may block.

As part of this, developers may use IDE plugins and other tools like [Snyk Advisor](https://snyk.io/advisor) to select secure packages and [Snyk Learn](https://learn.snyk.io/) to educate on secure coding, security, and the product. It's quite common to see developers download and use IDE plugins. Provide guides indicating the settings they should use and guidelines on what they should fix to start often Criticals and Highs, where fixes are available.

### Fix the backlog and triage issues

Finally, you can focus on fixing your backlog of security issues. This can take several forms:

* As part of the initial rollout, security or initial stakeholder may triage the initial results for the existing portfolio, create tickets for priority items to investigate or address, or have the teams do that for their applications as part of the weekly triage process.
* After getting visibility and achieving prevention, you can look at your backlog of issues. For example, a weekly triage process with the key stakeholders can guide the teams on what to address.

## Use enhanced resources with Snyk

Snyk was built with developers in mind, providing:

* Tools to create secure applications using integrations for IDE, Git, and CI/CD.
* [Snyk Advisor](https://snyk.io/advisor) and other tools to make decisions.
* [Snyk Learn](https://learn.snyk.io) training materials on products, securing code, and best practices.
