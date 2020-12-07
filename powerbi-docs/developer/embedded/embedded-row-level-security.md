---
title: Power BI Embedded 콘텐츠에서 행 수준 보안 사용
description: 애플리케이션 내에서 Power BI 콘텐츠를 포함하는 데 필요한 단계에 대해 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/10/2019
ms.openlocfilehash: 09489c3dbb33e1c5fb289cc1cc132eae0083a95f
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96120793"
---
# <a name="row-level-security-with-power-bi-embedded"></a>Power BI Embedded를 사용하는 행 수준 보안

**RLS(행 수준 보안)** 를 사용하여 대시보드, 타일, 보고서 및 데이터 세트 내 데이터에 대한 사용자 액세스를 제한할 수 있습니다. 여러 사용자가 다른 데이터를 보면서 동일한 아티팩트로 작업할 수 있습니다. RLS 포함이 지원됩니다.

일반적으로 ISV 시나리오인 Power BI 비사용자(앱 소유 데이터)에 포함되는 경우 이 문서를 참조하세요. 사용자 및 역할을 설명하기 위해 포함 토큰을 구성합니다.

조직 내에서 Power BI 사용자(사용자 소유 데이터)에 포함되는 경우 RLS는 Power BI 서비스 내에서와 마찬가지로 직접 작동합니다. 애플리케이션에서 추가로 수행해야 하는 작업은 없습니다. 자세한 내용은 [Power BI에서 RLS(행 수준 보안)](../../admin/service-admin-rls.md)를 참조하세요.

![행 수준 보안과 관련된 항목입니다.](media/embedded-row-level-security/powerbi-embedded-rls-components.png)

RLS를 활용하려면 세 가지 주요 개념인 사용자, 역할 및 규칙을 이해해야 합니다. 해당 개념에 대해 더 자세히 살펴보겠습니다.

**사용자** – 아티팩트(대시보드, 타일, 보고서 또는 데이터 세트)를 보는 최종 사용자입니다. 사용자는 Power BI Embedded에서 포함된 토큰에 있는 사용자 이름 속성에 의해 식별됩니다.

**역할** - 사용자 역할에 속합니다. 역할은 규칙에 대한 컨테이너로써 *판매 관리자* 또는 *영업 담당자* 와 같은 이름을 지정할 수 있습니다. Power BI Desktop 내에서 역할을 만듭니다. 자세한 내용은 [Power BI Desktop에서 RLS(행 수준 보안)](../../create-reports/desktop-rls.md)을 참조하세요.

**규칙** – 역할에는 규칙이 있고 이러한 규칙은 데이터에 적용되는 실제 필터입니다. 규칙은 “국가 = 미국”처럼 간단하거나 훨씬 동적일 수 있습니다.
이 문서의 나머지 부분에는 RLS를 작성하고 포함된 애플리케이션 내에서 사용하는 예제가 있습니다. 예제에서는 [소매점 분석 샘플](https://go.microsoft.com/fwlink/?LinkID=780547) PBIX 파일을 사용합니다.

![보고서 예제](media/embedded-row-level-security/powerbi-embedded-report-example.png)

## <a name="adding-roles-with-power-bi-desktop"></a>Power BI Desktop에서 규칙 추가

**소매점 분석 샘플** 에서는 소매 체인에 있는 모든 상점의 판매량을 보여줍니다. RLS를 사용하지 않으면 어떤 구역 관리자가 로그인하고 보고서를 보는지에 상관없이 동일한 데이터가 표시됩니다. 고위 경영진은 각 지역 관리자가 자신이 관리하는 매장의 매출만 볼 수 있어야 한다고 결정했습니다. 고위 경영진은 RLS를 사용하여 지역 관리자를 기준으로 데이터를 제한할 수 있습니다.

RLS는 Power BI Desktop에서 작성됩니다. 데이터 세트 및 보고서를 열 때 스키마를 보려면 다이어그램 뷰로 전환할 수 있습니다.

![Power BI Desktop 내에서 다이어그램 보기](media/embedded-row-level-security/powerbi-embedded-schema.png)

이 스키마에서 기억해야 할 몇 가지 사항은 다음과 같습입니다.

* **Total Sales** 과 같은 모든 측정값 **Sales** 팩트 테이블에 저장됩니다.
* 관련 추가 차원 테이블에는 **Item**, **Time**, **Store** 및 **District** 이라는 네 가지 항목이 있습니다.
* 관계선의 화살표는 필터가 테이블 간에 이동할 수 있는 방식을 나타냅니다. 예를 들어, 필터가 **Time[Date]** 에 배치되면 현재 스키마에서는 **Sales** 테이블에 있는 값만을 필터링합니다. 관계선에 있는 모든 화살표가 다른 방향이 아닌 판매 테이블을 가리키기 때문에 다른 테이블은 이 필터의 영향을 받지 않습니다.
* **District** 테이블은 각 지역에 있는 관리자를 나타냅니다.
  
    ![구역 테이블 내의 행](media/embedded-row-level-security/powerbi-embedded-district-table.png)

이 스키마에 따라 **District** 테이블의 **District Manager** 열에 필터를 적용하는 경우 및 해당 필터가 보고서를 보는 사용자와 일치하는 경우 해당 필터는 **Store** 및 **Sales** 테이블을 필터링하여 해당 지역 관리자에게 데이터를 표시합니다.

방법은 다음과 같습니다.

1. **모델링** 탭에서 **역할 관리** 를 선택합니다.

    ![Power BI Desktop 내의 모델링 탭](media/embedded-row-level-security/powerbi-embedded-manage-roles.png)
2. **관리자** 라는 새 역할을 만듭니다.

    ![새 역할 만들기](media/embedded-row-level-security/powerbi-embedded-new-role.png)
3. **District** 테이블에서 다음의 DAX 식을 입력합니다. **[District Manager] = USERNAME()**

    ![RLS 규칙의 DAX 문](media/embedded-row-level-security/powerbi-embedded-new-role-dax.png)
4. 규칙이 작동하는지 확인하려면 **모델링** 탭에서 **역할로 보기** 를 선택하고 앞서 만든 **관리자** 역할과 함께 **다른 사용자** 를 선택합니다. **Andrew Ma** 를 사용자로 입력합니다.

    ![역할 대화 상자로 보기](media/embedded-row-level-security/powerbi-embedded-new-role-view.png)

    마치 **Andrew Ma** 로 로그인한 것처럼 보고서에 데이터가 표시됩니다.

필터링을 적용하면 여기에서 수행한 방식으로 **District**, **Store** 및 **Sales** 테이블에서 모든 레코드를 필터링합니다. 그러나 **Sales** 와 **Time** 간 관계의 필터 방향으로 인해 **Sales** 와 **Item** 및 **Item** 과 **Time** 테이블이 필터링되지 않습니다. 양방향 교차 필터링에 대한 자세한 내용은 [SQL Server Analysis Services 2016 및 Power BI Desktop에서 양방향 교차 필터링](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) 백서를 다운로드합니다.

## <a name="applying-user-and-role-to-an-embed-token"></a>포함된 토큰에 사용자 및 역할 적용

이제 Power BI Desktop 역할을 구성했으므로 역할을 활용하기 위해 애플리케이션에서 몇 가지 작업을 수행해야 합니다.

사용자가 애플리케이션에 의해 인증되고 권한을 부여 받고 포함된 토큰을 사용하여 특정 Power BI Embedded 보고서에 대한 사용자 액세스 권한을 부여합니다. Power BI Embedded에는 사용자에 대한 특정 정보가 없습니다. RLS가 작동하려면 ID 양식에서 포함 토큰의 일부로 몇 가지 추가 컨텍스트를 통과해야 합니다. [포함 토큰](/rest/api/power-bi/embedtoken) API를 사용하여 ID를 전달할 수 있습니다.

API는 관련 데이터 세트가 표시된 ID 목록을 수락합니다. RLS를 실행하려면 ID의 일부로 다음 내용을 전달해야 합니다.

* **사용자 이름(필수)** – RLS 규칙을 적용할 때 사용자를 식별하는 데 사용할 수 있는 문자열입니다. 단일 사용자만 나열할 수 있습니다. 사용자 이름은 *ASCII* 문자로 만들 수 있습니다.
* **역할(필수)** – 행 수준 보안 규칙을 적용할 때 선택하는 역할을 포함하는 문자열입니다. 둘 이상의 역할을 전달하는 경우 문자열 배열로 전달되어야 합니다.
* **데이터 세트(필수)** - 포함하는 아티팩트에 적용할 수 있는 데이터 집합입니다.

**PowerBIClient.Reports** 에서 **GenerateTokenInGroup** 메서드를 사용하여 포함된 토큰을 만들 수 있습니다.

예를 들어 [PowerBI-Developer-Samples](https://github.com/Microsoft/PowerBI-Developer-Samples) > .NET Framework > 고객에 대한 콘텐츠 포함 > **PowerBIEmbedded_AppOwnsData** 샘플을 변경할 수 있습니다.

_ *변경 전**

```csharp
// Generate Embed Token with effective identities.
generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view", identities: new List<EffectiveIdentity> { rls });

// Generate Embed Token for reports without effective identities.
generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
```

**변경 후**

```csharp
var generateTokenRequestParameters = new GenerateTokenRequest("View", null, identities: new List<EffectiveIdentity> { new EffectiveIdentity(username: "username", roles: new List<string> { "roleA", "roleB" }, datasets: new List<string> { "datasetId" }) });

var tokenResponse = await client.Reports.GenerateTokenInGroupAsync("groupId", "reportId", generateTokenRequestParameters);
```

이제 REST API를 호출하는 경우 업데이트된 API는 **identities** 라는 추가 JSON 배열을 수용하고 사용자 이름, 문자열 역할 목록 및 문자열 데이터 세트 목록을 포함합니다. 

다음 코드를 예제로 사용하세요.

```json
{
    "accessLevel": "View",
    "identities": [
        {
            "username": "EffectiveIdentity",
            "roles": [ "Role1", "Role2" ],
            "datasets": [ "fe0a1aeb-f6a4-4b27-a2d3-b5df3bb28bdc" ]
        }
    ]
}
```

이제 모든 작업을 함께 수행하여 사용자가 이 아티팩트를 보기 위해 애플리케이션에 로그인할 경우 행 수준 보안에 정의된 대로 보도록 허용된 데이터만을 볼 수 있습니다.

## <a name="working-with-analysis-services-live-connections"></a>Analysis Services 라이브 연결 사용

행 수준 보안은 온-프레미스 서버에 대해 Analysis Services 라이브 연결에서 사용할 수 있습니다. 이러한 종류의 연결을 사용하는 경우 이해해야 하는 몇 가지 특정 개념이 있습니다.

사용자 이름 속성에 제공되는 유효한 ID는 Analysis Services 서버에 대한 사용 권한이 있는 Windows 사용자여야 합니다.

>[!NOTE]
> [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) 데이터 원본과 함께 서비스 주체를 사용하는 경우 서비스 주체 자체에 Azure Analysis Services 인스턴스 권한이 있어야 합니다. 서비스 주체가 포함된 보안 그룹을 이 목적으로 사용할 수는 없습니다.

### <a name="on-premises-data-gateway-configuration"></a>온-프레미스 데이터 게이트웨이 구성

[온-프레미스 데이터 게이트웨이](../../connect-data/service-gateway-onprem.md)는 Analysis Services 라이브 연결을 사용할 경우에 사용됩니다. 나열된 ID를 사용하여 embed 토큰을 생성할 경우 마스터 계정은 게이트웨이의 관리자로 나열되어야 합니다. 마스터 계정이 나열되지 않으면 행 수준 보안이 데이터 속성에 적용되지 않습니다. 게이트웨이 관리자 이외의 역할을 제공할 수 있지만 유효한 ID에 대한 고유한 사용자 이름을 지정해야 합니다.

### <a name="use-of-roles"></a>역할 사용

역할은 embed 토큰의 ID로 제공할 수 있습니다. 역할이 제공되지 않은 경우 제공된 사용자 이름을 사용하여 관련 역할을 확인할 수 있습니다.

### <a name="using-the-customdata-feature"></a>CustomData 기능 사용

CustomData 기능은 **Azure Analysis Services** 에 상주하는 모델에 대해서만 작동하고 **라이브 연결** 모드에서만 작동합니다. 사용자 및 역할과 달리 .pbix 파일 내에 사용자 지정 데이터 기능을 설정할 수 없습니다. 사용자 지정 데이터 기능을 사용하여 토큰을 생성할 때 사용자 이름이 필요합니다.

>[!NOTE]
>CustomData 사용자 이름은 최대 256자입니다.

CustomData 기능을 사용하면 **Azure Analysis Services** 를 데이터 원본으로 사용하여 애플리케이션에서 Power BI 데이터를 볼 때(애플리케이션의 Azure Analysis Services에 연결된 Power BI 데이터 보기) 행 필터를 추가할 수 있습니다.

CustomData 기능을 사용하면 CustomData 연결 문자열 속성을 사용하여 일반 텍스트(문자열)를 전달할 수 있습니다. Analysis Services는 *CUSTOMDATA()* 함수를 통해 이 값을 사용합니다.

**Azure Analysis Services** 에서 동적 RLS(필터 평가에 동적 값을 사용)를 사용하는 유일한 방법은 *CUSTOMDATA()* 함수를 사용하는 것입니다.

역할 DAX 쿼리 내에서 사용할 수 있고 측정값 DAX 쿼리에서 역할 없이 사용할 수 있습니다.
CustomData 기능은 대시보드, 보고서 및 타일과 같은 아티팩트에서 토큰 생성 기능의 일부입니다. 대시보드에는 여러 CustomData ID가 있을 수 있습니다(타일/모델 당 하나씩).

#### <a name="customdata-sdk-additions"></a>CustomData SDK 추가

CustomData 문자열 속성은 토큰 생성 시나리오에서 유효 ID에 추가되었습니다.

```json
[JsonProperty(PropertyName = "customData")]
public string CustomData { get; set; }
```

해당 ID는 다음과 같은 호출을 사용하는 사용자 지정 데이터로 만들 수 있습니다.

```csharp
public EffectiveIdentity(string username, IList<string> datasets, IList<string> roles = null, string customData = null);
```

#### <a name="customdata-sdk-usage"></a>CustomData SDK 사용

REST API를 호출하는 경우 각 ID 내에 사용자 지정 데이터를 추가할 수 있습니다. 예:

```json
{
    "accessLevel": "View",
    "identities": [
        {
            "username": "EffectiveIdentity",
            "roles": [ "Role1", "Role2" ],
            "customData": "MyCustomData",
            "datasets": [ "fe0a1aeb-f6a4-4b27-a2d3-b5df3bb28bdc" ]
        }
    ]
}
```

다음은 Power BI Embedded 애플리케이션을 사용하여 CustomData() 기능을 설정하기 위한 단계입니다.

1. Azure Analysis Services 데이터베이스를 만듭니다. 그런 다음, [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms)를 통해 Azure Analysis Services 서버에 로그인합니다.

    ![Azure Analysis Services 데이터베이스 만들기](media/embedded-row-level-security/azure-analysis-services-database-create.png)

    ![Analysis Services 데이터베이스](media/embedded-row-level-security/azure-analysis-services-database.png)

2. Analysis Services 서버에서 역할을 만듭니다.

    ![역할 만들기](media/embedded-row-level-security/azure-analysis-services-database-create-role.png)

3. **일반** 설정을 지정합니다.  여기서 **역할 이름** 을 지정하고 데이터베이스 권한을 **읽기** 전용으로 설정합니다.

    ![역할 만들기 - 일반 설정 지정](media/embedded-row-level-security/azure-analysis-services-database-create-role-general-settings.png)

4. **멤버 자격** 설정을 지정합니다. 여기서 이 역할의 영향을 받는 사용자를 추가합니다.

    ![역할 만들기 - 멤버 자격 설정 지정](media/embedded-row-level-security/azure-analysis-services-database-create-role-membership.png)

5. *CUSTOMDATA()* 함수를 사용하여 **행 필터** DAX 쿼리를 설정합니다.

    ![역할 만들기 - 행 필터 설정](media/embedded-row-level-security/azure-analysis-services-database-create-role-row-filters.png)

6. PBI 보고서를 빌드하고 용량이 있는 작업 영역에 게시합니다.

    ![PBI 보고서 샘플](media/embedded-row-level-security/rls-sample-pbi-report.png)

7. Power BI API를 통해 애플리케이션에서 CustomData 기능을 사용합니다.  사용자 지정 데이터 기능을 사용하여 토큰을 생성할 때 사용자 이름이 필요합니다. 사용자 이름은 마스터 사용자의 UPN과 같아야 합니다. 마스터 사용자는 생성한 역할의 구성원이어야 합니다. 역할을 지정하지 않으면 마스터 사용자가 구성원인 모든 역할이 RLS 평가에 사용됩니다.

    [서비스 주체](embed-service-principal.md)를 사용하는 경우 마스터 계정을 사용하는 대신 위의 단계를 수행해야 합니다. 포함 토큰을 생성할 때 [서비스 주체 개체 ID](embed-service-principal.md)를 사용자 이름으로 사용합니다.

    > [!Note]
    > 애플리케이션을 프로덕션에 배포할 준비가 되면 마스터 사용자 계정 필드 또는 옵션이 최종 사용자에게 표시되지 않아야 합니다.

    CustomData 기능을 추가하기 위한 [코드](#customdata-sdk-additions)를 봅니다.

8. 이제 보고서에 포함된 모든 데이터를 보기 위해 사용자 지정 데이터 값을 적용하기 전에, 애플리케이션에서 보고서를 볼 수 있습니다.

    ![사용자 지정 데이터가 적용되기 전](media/embedded-row-level-security/customdata-before.png)

    그런 다음, 사용자 지정 데이터 값을 적용하여 보고서가 다른 데이터 세트를 표시하는 방법을 확인할 수 있습니다.
    ![CustomData가 적용된 후](media/embedded-row-level-security/customdata-after.png)

## <a name="using-rls-vs-javascript-filters"></a>RLS 대 JavaScript 필터 사용

보고서에서 데이터 필터링을 결정할 때 **RLS(행 수준 보안)** 또는 **JavaScript 필터** 를 사용할 수 있습니다.

[행 수준 보안](../../admin/service-admin-rls.md)은 데이터 모델 수준에서 데이터를 필터링하는 기능입니다. 백엔드 데이터 원본이 RLS 설정을 제어합니다. 데이터 모델에 따라 포함 토큰 생성이 사용자 이름과 세션의 역할을 설정합니다. 클라이언트 쪽 코드로 이를 대체, 제거 또는 제어할 수 없으므로 안전한 것으로 간주됩니다. 데이터를 안전하게 필터링하기 위해 RLS를 사용할 것을 권장합니다. 아래 옵션 중 하나를 사용하여 RLS로 데이터를 필터링할 수 있습니다.

* [Power BI 보고서에서 역할을 구성](../../create-reports/desktop-rls.md).
* 데이터 원본 수준(Analysis Services 실시간 연결 전용)에서 역할을 구성합니다.
* `EffectiveIdentity`를 사용하여 [포함 토큰](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)을 통해 프로그래밍 방식으로 필터링. 포함 토큰을 사용하는 경우, 실제 필터는 특정 세션에서 포함 토큰을 통과합니다.

[JavaScript 필터](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#page-level-and-visual-level-filters)는 사용자가 축소되고 범위가 지정되고 필터링된 데이터 보기를 사용하도록 허용하기 위해 사용됩니다. 그러나 사용자는 여전히 모델 스키마 테이블, 열 및 측정값에 대한 액세스 권한을 가지고 있으며 데이터에도 액세스할 수 있습니다. 데이터에 대한 제한된 액세스는 클라이언트 측 필터링 API를 통해서가 아니라 RLS로만 적용할 수 있습니다.

## <a name="token-based-identity-with-azure-sql-database"></a>Azure SQL Database를 사용한 토큰 기반 ID

**토큰 기반 ID** 를 사용하면 **Azure SQL Database** 에 **AAD(Azure Active Directory)** 액세스 토큰을 사용하여 포함 토큰에 유효한 ID를 지정할 수 있습니다.

데이터를 **Azure SQL Database** 에 저장하는 고객은 이제 **Power BI Embedded** 와 통합될 때 Azure SQL에서 사용자 및 데이터 액세스 권한을 관리하는 새로운 기능을 사용할 수 있습니다.

포함 토큰을 생성하는 경우 Azure SQL에서 사용자의 유효 ID를 지정할 수 있습니다. 서버에 AAD 액세스 토큰을 전달하여 사용자의 유효 ID를 지정할 수 있습니다. 액세스 토큰은 해당 특정 세션을 위해 Azure SQL에서 해당 사용자의 관련 데이터를 끌어오는 데만 사용됩니다.

Azure SQL에서 각 사용자의 보기를 관리하거나 다중 테넌트 DB의 특정 고객으로 Azure SQL에 로그인하는 데 사용할 수 있습니다. Azure SQL에서 해당 세션에 행 수준 보안을 적용하고 해당 세션의 관련 데이터만 검색하여 Power BI에서 RLS를 관리할 필요성을 제거할 수도 있습니다.

이러한 유효 ID 문제는 Azure SQL Server의 RLS 규칙에 직접 적용됩니다. Power BI Embedded는 Azure SQL Server에서 데이터를 쿼리할 때 제공된 액세스 토큰을 사용합니다. 액세스 토큰이 제공된 사용자의 UPN은 USER_NAME() SQL 함수의 결과로 액세스할 수 있습니다.

토큰 기반 ID는 AAD 인증을 허용하도록 구성된 Azure SQL Database에 연결된 용량의 DirectQuery 모델에서만 작동합니다([Azure SQL Database의 AAD 인증에 대한 자세한 정보](/azure/sql-database/sql-database-manage-logins)). 데이터 세트의 데이터 원본은 토큰 기반 ID를 사용하기 위해 최종 사용자의 OAuth2 자격 증명을 사용하도록 구성해야 합니다.

   ![Azure SQL Server 구성](media/embedded-row-level-security/token-based-configure-azure-sql-db.png)

### <a name="token-based-identity-sdk-additions"></a>토큰 기반 ID SDK 추가

ID Blob 속성은 토큰 생성 시나리오에서 유효 ID에 추가되었습니다.

```JSON
[JsonProperty(PropertyName = "identityBlob")]
public IdentityBlob IdentityBlob { get; set; }
```

IdentityBlob 형식은 값 문자열 속성을 포함하는 간단한 JSON 구조체임

```JSON
[JsonProperty(PropertyName = "value")]
public string value { get; set; }
```

EffectiveIdentity는 다음 호출을 사용하여 ID Blob을 통해 만들 수 있습니다.

```C#
public EffectiveIdentity(string username, IList<string> datasets, IList<string> roles = null, string customData = null, IdentityBlob identityBlob = null);
```

다음 호출을 사용하여 ID Blob을 만들 수 있습니다.

```C#
public IdentityBlob(string value);
```

### <a name="token-based-identity-rest-api-usage"></a>토큰 기반 ID REST API 사용

[REST API](/rest/api/power-bi/embedtoken/reports_generatetokeningroup#definitions)를 호출하는 경우 각 ID 내에 ID Blob을 추가할 수 있습니다.

```JSON
{
    "accessLevel": "View",
    "identities": [
        {
            "datasets": ["fe0a1aeb-f6a4-4b27-a2d3-b5df3bb28bdc"],
        "identityBlob": {
            "value": "eyJ0eXAiOiJKV1QiLCJh…."
         }
        }
    ]
}
```

ID Blob에 제공된 값은 Azure SQL Server에 유효한 액세스 토큰이어야 합니다(<https://database.windows.net/>의 리소스 URL 포함).

   > [!Note]
   > Azure SQL의 액세스 토큰을 만들 수 있으려면 애플리케이션에는 Azure Portal의 AAD 앱 등록 구성에서 **Azure SQL Database** API에 대한 **Access Azure SQL DB 및 Data Warehouse** 위임 권한이 있어야 합니다.

   ![앱 등록](media/embedded-row-level-security/token-based-app-reg-azure-portal.png)

## <a name="on-premises-data-gateway-with-service-principal"></a>서비스 주체가 있는 온-프레미스 데이터 게이트웨이

SSAS(SQL Server Analysis Services) 온-프레미스 라이브 연결 데이터 원본을 사용하여 RLS(행 수준 보안)를 구성하는 고객은 **Power BI Embedded** 와 통합할 때 SSAS에서 사용자와 해당 데이터 액세스를 관리할 수 있는 새로운 [서비스 주체](embed-service-principal.md) 기능을 사용할 수 있습니다.

[Power BI REST API](/rest/api/power-bi/)를 통해 [서비스 주체 개체](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)를 사용하여 포함 토큰에 대한 SSAS 온-프레미스 라이브 연결을 위한 유효한 ID를 지정할 수 있습니다.

지금까지 SSAS 온-프레미스 라이브 연결을 위한 유효한 ID를 지정하려면 포함 토큰을 생성하는 마스터 사용자가 게이트웨이 관리자여야 했습니다. 이제 사용자를 게이트웨이 관리자로 요구하는 대신 게이트웨이 관리자는 사용자가 포함 토큰을 생성할 때 유효한 ID를 재정의할 수 있도록 해당 데이터 원본에 대한 전용 권한을 사용자에게 부여할 수 있습니다. 이 새로운 기능을 통해 라이브 SSAS 연결에 서비스 주체를 포함시킬 수 있습니다.

이 시나리오를 사용하기 위해 게이트웨이 관리자는 [데이터 원본 사용자 REST API 추가](/rest/api/power-bi/gateways/adddatasourceuser)를 사용하여 서비스 주체에게 Power BI Embedded에 대한 *ReadOverrideEffectiveIdentity* 권한을 부여합니다.

관리 포털을 사용하여 이 권한을 설정할 수 없습니다. 이 사용 권한은 API로만 설정됩니다. 관리 포털에서 이러한 사용 권한이 있는 사용자 및 SPN에 대한 표시를 볼 수 있습니다.

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항

* Power BI 서비스 내에서 역할에 사용자를 할당하면 포함 토큰을 사용할 때 RLS에 영향을 주지 않습니다.
* Power BI 서비스는 편집 권한이 있는 관리자나 구성원에게 RLS 설정을 적용하지 않는 반면, 포함 토큰을 사용하여 ID를 제공할 경우 데이터에 적용합니다.
* 온-프레미스 서버에 대해 Analysis Services 라이브 연결이 지원됩니다.
* Azure Analysis Services 라이브 연결은 역할별 필터링을 지원합니다. CustomData를 사용하여 동적 필터링을 수행할 수 있습니다.
* 기본 데이터 세트에서 RLS가 필요하지 않은 경우 GenerateToken 요청은 유효 ID를 포함하지 **않아야** 합니다.
* 기본 데이터 세트가 클라우드 모델(캐시된 모델 또는 DirectQuery)이면 유효 ID는 하나 이상의 역할을 포함해야 합니다. 그렇지 않으면 역할 할당이 이루어지지 않습니다.
* ID 목록은 대시보드 포함을 위한 여러 ID 토큰을 구현합니다. 다른 모든 아티팩트는 목록에 단일 ID가 포함됩니다.

### <a name="token-based-identity-limitations"></a>토큰 기반 ID 제한 사항

* 용량이 있는 경우에만 RLS를 사용할 수 있습니다.
* RLS는 SQL Server 온-프레미스에서 작동하지 않습니다.

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)