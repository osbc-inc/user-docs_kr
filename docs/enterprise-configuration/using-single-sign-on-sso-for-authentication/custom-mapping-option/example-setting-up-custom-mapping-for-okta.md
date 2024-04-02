# 예: Okta에 대한 사용자 지정 매핑 설정

다음은 Okta 역할의 [Custom Mapping Options](./)에 대한 두 가지 옵션을 보여줍니다.

{% hint style="info" %}
이 두 가지 옵션이 모두 작동하려면, **반드시** Snyk SSO 애플리케이션을 사용자 수준이 아닌 그룹 수준에서 할당해야 합니다.
{% endhint %}

## 옵션 1: 사용자 역할로 사용자 지정 매핑 할당

다음은 사용자 역할을 사용한 사용자 정의 매핑에 대해 설명합니다.

* Okta 그룹은 Snyk 조직에 매핑됩니다.
* 사용자 프로필은 Okta 그룹이 아닌 각 사용자와 연결되어 있습니다.

단계는 다음과 같습니다.

{% hint style="info" %}
참고: Snyk SSO 애플리케이션은 **반드시** 사용자 수준이 아닌 그룹 수준에서 할당되어야 합니다.

사용자의 애플리케이션 할당을 보면 다음 이미지와 유사하게 나타나야 하며, **Add Another**가 회색으로 표시된 **Snyk-Roles 그룹**에 의해 설정되어야 합니다.
{% endhint %}

<figure><img src="../../../.gitbook/assets/snyk-roles.png" alt="Roles set on group level"><figcaption><p>그룹 수준에서 설정된 역할</p></figcaption></figure>

### 관련 Snyk 조직의 이름이 포함된 앱 속성을 만듭니다.

Snyk 그룹과 사용자가 설정되면, 다음 단계를 따르세요.

1. Okta 메인 페이지에서 **Directory -> Profile Editor -> your Snyk SSO app.**
2. **+Add Attribute**를 선택합니다.
3. 해당 필드에서 첫 번째 속성에 대해 다음 세부정보를 추가합니다 :\
   **Data type**: 문자열 배열(string array)\
   **Display name**: Snyk Orgs\
   **Variable name**: snyk\_orgs\
   **Group Priority**: 그룹 전체의 값 결합
4. 완료되면 **Save and Add Another** 선택합니다.

### 역할을 포함하는 두 번째 앱 속성 생성

1. 해당 필드에 두 번째 속성에 대한 다음 세부정보를 추가합니다 : \
   **Data type**: 문자열(String)\
   **Display name**: Snyk User Role\
   **Variable name**: user\_role\
   **Enum**: **Define enumerated list of values** 선택합니다.\
   **Attribute members Collaborator:** collaborator or collab\
   **Attribute members Admin**: administrator or admin\
   **Attribute members GroupAdmin**: groupadmin\
   **Attribute required**: Yes\
   **Scope**: User personal
2. When you are finished, select **Save**.

### Okta 그룹에 첫 번째 속성을 할당합니다.

1. Okta 메인 페이지에서 **Directory -> Groups.**
2. **그룹**을 선택하고, **애플리케이션** 탭으로 이동한 후, 아직 할당되지 않은 경우 **애플리케이션 할당**을 클릭하고 Snyk SSO 앱을 선택합니다. 그런 다음 표시된 Snyk 앱 옆에 있는 **연필**을 클릭하세요.
3. **Edit App Assignment** 에서 Okta 그룹과 연결할 Snyk 조직 이름을 추가합니다(공백이나 대문자 없음).
4. 이전 단계를 반복하여 Snyk 앱을 적용 가능한 모든 Okta 그룹에 할당하고 필요에 따라 Snyk 조직 이름을 수정합니다.

### 사용자에게 두 번째 속성을 할당합니다.

1. Okta 메인 페이지에서 **Directory -> People.**
2. **사용자**를 선택하고**,** **애플리케이션** 탭으로 이동한 후 애플리케이션 옆에 있는 **연필**을 클릭합니다.
3. 그룹(사용자 역할)에서 올바른 사용자 유형(**협력자, 관리자 또는 그룹 관리자**)을 선택합니다.

### Snyk로 전송될 역할 배열의 문자열 값으로 이 두 속성을 연결하는 값 표현식을 구성합니다.

1. **Applications -> Applications** 으로 이동하여 구성한 **Snyk 앱**을 클릭하세요.
2. General **Tab -> SAML Settings -> Edit**을 선택하고 **다음**을 클릭하여 Configure SAML 단계로 이동합니다.
3. **Attribute Statements** -> **이름 형식이 지정되지 않음**과 **값**을 다음 표현식으로 사용하여 **역할**이라는 속성을 추가합니다.\
   `appuser.user_role == "groupadmin" ? "snyk-groupadmin" : Arrays.flatten(String.replace(String.replace(String.append("snyk-",String.append(Arrays.toCsvString(appuser.snyk_orgs),"-"+appuser.user_role)),",",",snyk-"),",","-"+appuser.user_role+","))`
4. **Next -> Finish**을 클릭합니다.
5. 구성을 완료할 수 있도록 Snyk 담당자에게 문의하세요. 이 과정은 4\~5일이 걸릴 수 있습니다.

역할 표현에 대한 설명 :&#x20;

* 역할이 groupadmin이면 표현식은 다른 모든 것을 무시하고 `snyk-groupadmin`을 전달합니다.
* 역할이 groupadmin이 아니면, 모든 그룹에 나열된 각 snyk 조직에 대해 표현식이 자동으로 실행됩니다.
  1. 접두사 "`snyk-`"를 snyk 조직 슬러그와 연결
  2. 각 조직 슬러그 끝에 `user_role` 추가

역할의 예는 다음과 같습니다:`[ "snyk-groupadmin", "snyk-org1-admin", "snyk-org2-admin" ]`

## 옵션 2: 그룹에 사용자 지정 매핑 할당

이 구성에서:

* Okta 그룹은 Snyk 조직에 매핑됩니다.
* Okta 그룹은 Snyk 조직 멤버십 역할에 매핑됩니다.
* Snyk의 사용자 역할은 해당 그룹의 모든 구성원에 대해 각 Okta 그룹에 사전 설정되어 있습니다.

단계는 다음과 같습니다.

{% hint style="info" %}
참고: Snyk SSO 애플리케이션은 사용자 수준이 아닌 그룹 수준에서 할당되어야 합니다.

사용자의 애플리케이션 할당을 보면 다음 이미지와 유사하게 나타나야 하며, **Add Another**가 회색으로 표시된 **Snyk-Roles** 그룹에 의해 설정되어야 합니다.
{% endhint %}

<figure><img src="../../../.gitbook/assets/snyk-roles.png" alt="Roles set on group level"><figcaption><p>그룹 수준에서 설정된 역할</p></figcaption></figure>

### Snyk 조직 이름과 역할을 모두 포함하는 단일 앱 속성을 생성합니다.

1. Okta 메인 페이지에서 **Directory -> Profile Editor -> your Snyk SSO app**을 선택합니다.
2. **+Add Attribute**를 선택합니다.
3. 해당 필드에 이 속성에 대한 다음 세부정보를 추가 :\
   **Data type**: 문자열 배열(string array)\
   **Display name**: Snyk Orgs\
   **Variable name:** snyk\_orgs\
   **Group Priority**: 그룹 전체의 값 결합
4. 완료되면 **Save**을 선택합니다.

### 관련 Okta 그룹에 속성을 할당합니다.

1. On Okta 메인 페이지에서 **Directory -> Groups**을 선택합니다.
2. **그룹**을 선택하고, **애플리케이션** 탭으로 이동한 후, 아직 할당되지 않은 경우 **애플리케이션 할당**을 클릭하고 Snyk SSO 앱을 선택합니다. 그런 다음 표시된 Snyk SSO 앱 옆에 있는 **연필**을 클릭하세요.
3. **Edit App Assignment** 에서 [Example roles array mapping](./#example-roles-array-mapping)에 설명된 구문에 따라, Snyk 조직 이름 + Okta 그룹과 연결된 역할(공백이나 대문자 없음)을 추가합니다. (예: `snyk-org-role)`
4. 해당하는 모든 Okta 그룹에 대해 이전 단계를 반복하여 구성된 각 그룹 내의 각 사용자에게 조직 이름과 역할 조합을 할당합니다

### Snyk으로 보낼 역할 배열을 생성하는 값 표현식을 구성합니다.

1. **Applications -> Applications** 로 이동하여 구성한 **Snyk 앱**을 클릭하세요.
2. **General Tab -> Edit SAML Settings** -> **다음**을 클릭하여 **Configure SAML**로 이동합니다.
3. 지정되지 않은 유형의 "roles"라는 **속성 설명(Attribute Statement)**을 추가합니다.
4.  **속성 설명(Attribute Statement)**을 선택하고 **이름 형식**이 **지정되지 않은** **이름** 필드와 다음 표현식의 **값**으로 **역할**을 설정합니다.

    `Arrays.flatten(appuser.snyk_orgs)`
5. 구성을 완료할 수 있도록 Snyk 담당자에게 문의하세요.
