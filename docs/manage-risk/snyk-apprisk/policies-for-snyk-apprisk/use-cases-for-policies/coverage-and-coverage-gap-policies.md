# 커버리지 및 커버리지 갭 정책  - Use case

커버리지 필터를 사용하여 자산이 제품에서 테스트된 적이 있는지 확인하고 커버리지 갭 필터를 사용하여 자산이 커버리지 설정 제어 정책에 설정된 적용 범위 요구 사항을 충족하는지 확인할 수 있습니다.

{% hint style="info" %}
Coverage Gap 필터는 Coverage 필터와 반대가 아닙니다.

자산은 (한 달 전에 스캔한 경우) 보상받을 수 있지만, 동시에 매일 스캔해야 하는 경우에도 적용 범위가 있을 수 있습니다.
{% endhint %}

## 주요 사용 사례

### 커버리지

#### 선택한 모든 제품 포함

Snyk Code와 Snyk Open Source에서 동시에 스캔한 자산을 식별합니다. 이러한 자산을 식별한다고 해서 보장 요건을 충족하는 것은 아닙니다.

<figure><img src="https://lh7-us.googleusercontent.com/1aKKSl4O03NT8YL3qR0K1vpcfEMtlCw9pLYrKJ3Q2OdtVYTqdMbsbtWr7Jq32TzMBKEo1t53c7gaEndbiFVqLObxPcUcw7vmmaaSHO5K7UsgtjVu6FO3kLCp6cT_-CX1CzX5Anst0acYqVom89K9y14" alt=""><figcaption></figcaption></figure>

#### 선택한 제품 중 하나 이상 포함

Snyk Code 또는 Snyk Open Source에서 스캔한 자산을 식별합니다. 이러한 자산을 식별한다고 해서 보장 요건을 충족하는 것은 아닙니다.

<figure><img src="https://lh7-us.googleusercontent.com/V9uzAQdi6GRne6GXxQ5cQLYXrMD6BD-HMcDIX5ebRk6OWpgxgkU7JSWf49CsNwciu2WZtCoKY7Eg4gk_7mQOXtsGRRns-Z0z96L4aDQQzT_CD17RVEVr57TJK-mMgYiCZW64z4EK71BjvldkWF8iLe4" alt=""><figcaption></figcaption></figure>

### 커버리지 갭

#### 모든 제품 제외

정책에 포함되지 않은 모든 자산을 식별합니다. 이를 위해서는 사용 가능한 모든 제품을 커버하는 커버리지 갭 필터를 만들어야 합니다.

<figure><img src="https://lh7-us.googleusercontent.com/RcfoCkR_1a6-L44Bf55ed7xSX8Loyr57KKyI4oX4yh0j6ce3Oj4fu0XL67v9Ij1XKTES-uwTMgqJBFicBtLwaHKilj1orTi_LU0_dEllCvUE2jhfpJimlXIfRON8-0_DF_Qe__tmFLuKmSTOJoFOxCk" alt=""><figcaption></figcaption></figure>

#### 비준수 자산 필터링

Snyk Code 또는 Snyk Open Source 또는 둘 다의 커버리지 요구 사항을 충족하지 못하는 자산을 동시에 식별합니다.

<figure><img src="https://lh7-us.googleusercontent.com/guCzWVv9SP7H1h6WYSFGwHEVvW3c0DVvg26mHAdxkorPgZI3gYCIH93QN0fXNl71ZDZxucfpROkkjruxuQ_vu5QCjS7_ImROEZlBTYIh-hxZnsM3comPaQpQbsy7s_3MDuFVEiljw2G8szWddXjqPgQ" alt=""><figcaption></figcaption></figure>

\
Snyk Code 및 Snyk Open Source의 커버리지 요구 사항을 모두 충족하는 자산을 식별합니다.

<figure><img src="https://lh7-us.googleusercontent.com/-Ys7HZ5UcthgyDyPbBNG572CTM04RJ_Tcc1JTa9GrltfSVUM5gvFLrxpNRlV6ZNqRJQOw5hL0QFworAAOVbGYCMM4J-H4z9G8L3BiU3-PEU79GqxAalKB5UvdXxKUIgNEszwH0jUN_7kpos8HLSXvo8" alt=""><figcaption></figcaption></figure>
