---
title: 임베디드 분석 애플리케이션에 Power BI 콘텐츠를 포함하도록 앱 등록
description: Power BI 콘텐츠 포함에 사용하기 위해 Azure Active Directory 내에서 애플리케이션을 등록하는 방법에 대해 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 04/02/2019
ms.openlocfilehash: 98956beb3e5a106b885ecbca187521f85917f25e
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098217"
---
# <a name="register-an-azure-ad-application-to-use-with-power-bi"></a>Power BI와 함께 사용할 Azure AD 애플리케이션 등록

Power BI Embedded 분석을 사용하려면 Azure에서 Azure AD(Azure Active Directory) 애플리케이션을 등록해야 합니다. Azure AD 앱은 Power BI REST 리소스에 대한 사용 권한을 설정하고 [Power BI REST API](/rest/api/power-bi/)에 대한 액세스를 허용합니다.

## <a name="determine-your-embedding-solution"></a>포함 솔루션 결정

앱을 등록하기 전에 다음 중 가장 적합한 솔루션을 결정합니다.

* 고객에 대한 콘텐츠 포함
* 조직에 대한 콘텐츠 포함

### <a name="embed-for-your-customers"></a>고객에 대한 콘텐츠 포함

고객을 위해 설계된 애플리케이션을 만들 계획인 경우 ‘앱 소유 데이터’라고도 하는 [고객에 대한 콘텐츠 포함](embed-sample-for-customers.md) 솔루션을 사용합니다. 사용자는 애플리케이션을 사용하기 위해 Power BI에 로그인하거나 Power BI 라이선스를 가질 필요가 없습니다. 애플리케이션은 다음 방법 중 하나를 사용하여 Power BI에 대해 인증합니다.

* **마스터 사용자** 계정(Power BI에 로그인하는 데 사용되는 Power BI Pro 라이선스)

* [서비스 주체](embed-service-principal.md)

고객에 대한 콘텐츠 포함 솔루션은 일반적으로 타사를 위한 애플리케이션을 만드는 ISV(독립 소프트웨어 공급업체) 및 개발자에 의해 사용됩니다.

### <a name="embed-for-your-organization"></a>조직에 대한 콘텐츠 포함

사용자가 Power BI에 대한 인증을 위해 자격 증명을 사용해야 하는 애플리케이션을 만들 계획인 경우 ‘사용자 소유 데이터’라고도 하는 솔루션에 [조직에 대한 콘텐츠 포함](embed-sample-for-your-organization.md)을 사용합니다.

조직 솔루션에 대한 포함은 일반적으로 기업 및 대규모 조직에서 사용되며 내부 사용자를 위한 것입니다.

## <a name="register-an-azure-ad-app"></a>Azure AD 앱 등록

Azure AD 앱을 등록하는 가장 쉬운 방법은 [Power BI 포함 설정 도구](https://app.powerbi.com/embedsetup)를 사용하는 것입니다. 이 도구는 간단한 그래픽 인터페이스를 사용하여 두 포함 솔루션을 위한 빠른 등록 프로세스를 제공합니다.

*조직에 대한 콘텐츠 포함* 애플리케이션을 만드는 경우 Azure AD 앱에 대한 추가 제어를 원하면 Azure Portal에서 수동으로 등록할 수 있습니다.

> [!IMPORTANT]
> Power BI 앱을 등록하려면 먼저 [Azure Active Directory 테넌트 및 조직 사용자](create-an-azure-active-directory-tenant.md)가 있어야 합니다.

# <a name="embed-for-your-customers"></a>[고객에 대한 콘텐츠 포함](#tab/customers)

다음 단계에서는 Power BI [고객에 대한 콘텐츠 포함](embed-sample-for-customers.md) 솔루션을 위해 Azure AD 애플리케이션을 등록하는 방법을 설명합니다.

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. ‘Choose an embedding solution’(포함 솔루션 선택) 섹션에서 **고객에 대한 콘텐츠 포함** 을 선택합니다.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. ‘2단계 - 애플리케이션 등록’에서 다음 필드를 입력합니다.

    * **애플리케이션 이름** - 애플리케이션에 이름을 지정합니다.

    * **API 액세스** - 애플리케이션에 필요한 Power BI API(범위라고도 함)를 선택합니다. *모두 선택* 을 사용하여 모든 API를 선택할 수 있습니다. Power BI 액세스 권한에 대한 자세한 내용은 [Microsoft ID 플랫폼 엔드포인트의 권한 및 동의](/azure/active-directory/develop/v2-permissions-and-consent)를 참조하세요.

5. **등록** 을 선택합니다.

    Azure AD 앱의 **애플리케이션 ID** 가 *요약* 상자에 표시됩니다. 나중에 사용하도록 이 값을 복사합니다.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. *5 단계 - 사용 권한 부여* 에서 **‘사용 권한 부여’** 를 선택하고 팝업 창에서 **수락** 을 선택합니다. 이렇게 하면 선택한 API(범위라고도 함)에 Azure AD 앱에서 로그인한 사용자로 액세스할 수 있습니다. 이 사용자는 **마스터 사용자** 라고도 합니다.

9. (선택 사항) 도구를 사용하여 Power BI 작업 영역을 만들고 콘텐츠를 업로드한 경우 이제 **애플리케이션 예제 다운로드** 를 선택할 수 있습니다. ‘요약’ 상자의 모든 정보를 복사해야 합니다.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="embed-for-your-organization"></a>[조직에 포함](#tab/organization)

다음 단계에서는 Power BI [조직에 대한 콘텐츠 포함](embed-sample-for-your-organization.md) 솔루션을 위해 Azure AD 애플리케이션을 등록하는 방법을 설명합니다.

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. ‘Choose an embedding solution’(포함 솔루션 선택) 섹션에서 **조직에 대한 콘텐츠 포함** 을 선택합니다.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. ‘2단계 - 애플리케이션 등록’에서 다음 필드를 입력합니다.

    * **애플리케이션 이름** - 애플리케이션에 이름을 지정합니다.

    * **홈페이지 URL** - 홈페이지의 URL을 입력합니다.

    * **리디렉션 URL** - 애플리케이션 사용자는 로그인하면 애플리케이션이 Azure에서 인증 코드를 수신하는 동안 이 주소로 리디렉션됩니다. 다음 옵션 중 하나를 선택합니다.

        * **Use a default URL**(기본 URL 사용) - 이 옵션은 샘플 임베디드 분석 애플리케이션을 자동으로 만들고 다운로드합니다. 기본 URL은 http://localhost:13526/ 입니다.

        * **Use a custom URL**(사용자 지정 URL 사용) - 임베디드 분석 애플리케이션이 이미 있고 리디렉션 URL로 사용할 항목을 알고 있는 경우 이 옵션을 선택합니다.

    * **API 액세스** - 애플리케이션에 필요한 Power BI API(범위라고도 함)를 선택합니다. *모두 선택* 을 사용하여 모든 API를 선택할 수 있습니다. Power BI 액세스 권한에 대한 자세한 내용은 [Microsoft ID 플랫폼 엔드포인트의 권한 및 동의](/azure/active-directory/develop/v2-permissions-and-consent)를 참조하세요.

5. **등록** 을 선택합니다.

    Azure AD 앱의 **애플리케이션 ID** 및 **애플리케이션 비밀** 값이 *요약* 상자에 표시됩니다. 나중에 사용하도록 이 값을 복사합니다.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. (선택 사항) 도구를 사용하여 Power BI 작업 영역을 만들고 콘텐츠를 업로드한 경우 이제 **애플리케이션 예제 다운로드** 를 선택할 수 있습니다. ‘요약’ 상자의 모든 정보를 복사해야 합니다.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="manual-registration"></a>[수동 등록](#tab/manual)

다음 솔루션 중 하나를 만드는 경우에만 Azure AD 수동 앱 등록을 사용합니다.

* ‘조직에 대한 콘텐츠 포함’ 애플리케이션.

* ‘서비스 주체’가 있는 ‘고객에 대한 콘텐츠 포함’ 애플리케이션. 

    >[!NOTE]
    >이 옵션을 선택하는 경우 Azure AD 앱을 등록한 후에 앱에 [Power BI 권한을 추가](#change-your-azure-ad-apps-permissions)해야 합니다.

Azure Active Directory에 애플리케이션을 등록하는 방법에 대한 자세한 내용은 [Azure Active Directory에 앱 등록](/azure/active-directory/develop/quickstart-v2-register-an-app)을 참조하세요.

1. [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. 페이지의 오른쪽 위에서 사용자 계정을 선택하여 Azure AD 테넌트를 선택합니다.

3. **앱 등록** 을 선택합니다. 이 옵션이 표시되지 않는 경우 검색합니다.
 
4. *앱 등록* 에서 **새 등록** 을 선택합니다.

5. 다음 필드를 작성합니다.

    * **이름** - 애플리케이션에 이름을 지정합니다.

    * **지원되는 계정 유형** - 애플리케이션을 사용할 수 있는 사용자를 선택합니다.

6. (선택 사항) **리디렉션 URI** 에서 리디렉션 URL을 추가합니다.

7. **등록** 을 선택합니다. 앱이 등록되면 앱의 개요 페이지로 리디렉션됩니다. 여기서 *애플리케이션 ID* 를 가져올 수 있습니다.

---

## <a name="change-your-azure-ad-apps-permissions"></a>Azure AD 앱의 사용 권한 변경

애플리케이션을 등록한 후에는 해당 사용 권한을 변경할 수 있습니다. 프로그래밍 방식으로 또는 Azure Portal에서 사용 권한을 변경할 수 있습니다.

>[!NOTE]
>Azure AD 앱 권한은 ‘마스터 사용자’ 인증 방법을 사용하여 ‘고객에 대한 콘텐츠 포함’ 솔루션에만 적용할 수 있습니다. 

# <a name="azure"></a>[Azure](#tab/Azure)

Azure Portal에서 앱을 보고 사용 권한을 변경할 수 있습니다.

1. [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. 페이지의 오른쪽 위에서 사용자 계정을 선택하여 Azure AD 테넌트를 선택합니다.

3. **앱 등록** 을 선택합니다. 이 옵션이 표시되지 않는 경우 검색합니다.

4. **소유한 애플리케이션** 탭에서 앱을 선택합니다. 애플리케이션은 ‘개요’ 탭에서 열리며, 여기서 ‘애플리케이션 ID’를 검토할 수 있습니다. 

5. **API 사용 권한** 탭을 선택합니다.

6. 사용 권한을 추가하려면 다음 단계를 수행합니다.

    1. **사용 권한 추가** 를 선택한 다음 **Power BI 서비스** 를 선택합니다.

    2. **위임된 권한** 을 선택하고 필요한 특정 권한을 추가 또는 제거합니다.

    3. 완료되면 **사용 권한 추가** 를 선택하여 변경 내용을 저장합니다.

7. 사용 권한을 제거하려면 다음 단계를 수행합니다.

    1. 사용 권한 오른쪽에 있는 줄임표(...)를 선택합니다.
    
    2. **권한 제거** 를 선택합니다.
    
    3. ‘권한 제거’ 팝업 창에서 **예, 제거합니다** 를 선택합니다.

# <a name="http"></a>[HTTP](#tab/HTTP)

프로그래밍 방식으로 Azure AD 앱 사용 권한을 변경하려면 테넌트 내에서 기존 서비스 주체(사용자)를 가져와야 합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [servicePrincipal](/graph/api/resources/serviceprincipal)을 참조하세요.

1. 테넌트 내에서 모든 서비스 주체를 가져오려면 `{ID}` 없이 `Get servicePrincipal` API를 호출합니다.

2. `appId` 속성으로 앱 ‘애플리케이션 ID’가 있는 서비스 주체를 확인합니다.

    ```json
    Post https://graph.microsoft.com/v1.0/servicePrincipals HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

    >[!NOTE]
    >`displayName`는 선택 사항입니다.

3. `consentType`에 다음 값 중 하나를 할당하여 앱에 대한 Power BI 사용 권한을 부여합니다.

    * `AllPrincipals` - Power BI 관리자가 테넌트의 모든 사용자를 대신하여 권한을 부여하는 데만 사용할 수 있습니다.

    * `Principal` - 특정 사용자를 대신하여 권한을 부여하는 데 사용됩니다. 이 옵션을 사용하는 경우 `principalId={User_ObjectId}` 속성을 요청 본문에 추가합니다.

     ```json
     Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    >[!NOTE]
    >* **마스터 사용자** 를 사용하는 경우 Azure AD에서 동의 여부를 묻는 메시지가 표시되지 않게 하려면 마스터 계정에 대한 사용 권한을 부여해야 합니다.
    >* `resourceId` *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* 는 전역적이지 않고 테넌트 종속입니다. 이 값은 Azure AD에서 ‘Power BI 서비스’ 애플리케이션의 *objectId* 입니다. Azure Portal에서 이 값을 얻으려면 [엔터프라이즈 애플리케이션 > 모든 애플리케이션](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps)으로 이동하여 ‘Power BI 서비스’를 검색합니다.

4. `consentType`에 값을 할당하여 Azure AD에 앱 사용 권한을 부여합니다.

    ```json
    Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

# <a name="c"></a>[C#](#tab/CSharp)

C#을 사용하여 Azure AD 앱 사용 권한을 변경할 수도 있습니다. 자세한 내용은 [oAuth2PermissionGrant](https://docs.microsoft.com/graph/api/oauth2permissiongrant-get) API를 참조하세요. 이 방법은 일부 프로세스를 자동화하려는 경우에 유용할 수 있습니다.

HTTP 요청에 대한 자세한 내용은 [HTTP 탭](register-app.md?tabs=customers%2CHTTP#change-your-azure-ad-apps-permissions)을 참조하세요.

```csharp
var graphClient = GetGraphClient();

currentState.createdApp = await graphClient.Applications
    .Request()
    .AddAsync(application);

System.Threading.Thread.Sleep(2000);

var passwordCredential = new PasswordCredential
{
    DisplayName = "Client Secret Created in C#"
};

currentState.createdSecret = await graphClient.Applications[currentState.createdApp.Id]
    .AddPassword(passwordCredential)
    .Request()
    .PostAsync();

var servicePrincipal = new ServicePrincipal
{
    AppId = currentState.createdApp.AppId
};

currentState.createdServicePrincipal = await graphClient.ServicePrincipals
    .Request()
    .AddAsync(servicePrincipal);

GraphServiceClient graphClient = new GraphServiceClient(authProvider);

// Use oAuth2PermissionGrant to change permissions
var oAuth2PermissionGrant = await graphClient.Oauth2PermissionGrants["{id}"]
               .Request()
               .GetAsync();
```

---

## <a name="next-steps"></a>다음 단계

>[!div class="nextstepaction"]
>[Power BI 애플리케이션의 Azure AD 액세스 토큰 얻기](get-azuread-access-token.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)