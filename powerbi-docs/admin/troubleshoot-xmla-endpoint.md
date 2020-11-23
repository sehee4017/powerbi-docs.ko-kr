---
title: Power BI에서 XMLA 엔드포인트 연결 문제 해결
description: Power BI Premium에서 XMLA 엔드포인트를 통한 연결 문제를 해결하는 방법을 설명합니다.
author: minewiskan
ms.author: owend
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 11/16/2020
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: 5100a2a693bbabacd5659c6e805031339d188555
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94668123"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>XMLA 엔드포인트 연결 문제 해결

Power BI Premium의 XMLA 엔드포인트는 Power BI 데이터 세트에 액세스하기 위해 네이티브 Analysis Services 통신 프로토콜을 사용합니다. 이로 인해 XMLA 엔드포인트 문제 해결은 일반적인 Analysis Services 연결 문제를 해결하는 것과 거의 같습니다. 그러나 Power BI 관련 종속성에서 일부 차이점이 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

XMLA 엔드포인트 시나리오의 문제를 해결하기 전에 [XMLA 엔드포인트를 사용한 데이터 세트 연결](service-premium-connect-tools.md)에 설명된 기본 사항을 검토해야 합니다. 가장 일반적인 XMLA 엔드포인트 사용 사례가 설명되어 있기 때문입니다. [게이트웨이 문제 해결 - Power BI](../connect-data/service-gateway-onprem-tshoot.md) 및 [Excel에서 분석 문제 해결](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)과 같은 다른 Power BI 문제 해결 가이드도 도움이 될 수 있습니다.

## <a name="enabling-the-xmla-endpoint"></a>XMLA 엔드포인트 사용

Power BI Premium 및 Power BI Embedded 용량 모두에서 XMLA 엔드포인트를 사용하도록 설정할 수 있습니다. 2\.5GB 메모리를 사용하는 A1 용량과 같이 더 작은 용량에서는 XMLA 엔드포인트를 **읽기/쓰기** 로 설정하고 **적용** 을 선택하려고 하면 용량 설정 오류가 발생할 수 있습니다. 오류는 "워크로드 설정에 문제가 있습니다. 잠시 후에 다시 시도하세요."입니다.

시도해 볼 수 있는 작업은 다음과 같습니다.

- 데이터 흐름 등 다른 서비스에 대한 메모리 소비를 40% 이하로 제한하거나 불필요한 서비스를 완전히 사용하지 않도록 설정합니다.  
- 용량을 더 큰 SKU로 업그레이드합니다. 예를 들어 A1에서 A3 용량으로 업그레이드하면 데이터 흐름을 사용하지 않도록 설정하지 않고도 이 구성 문제를 해결할 수 있습니다.

또한 Power BI 관리 포털에서 테넌트 수준 [데이터 내보내기 설정](service-premium-connect-tools.md#security)을 사용하도록 설정해야 합니다. 이 설정은 Excel에서 분석 기능에도 필요합니다.

## <a name="establishing-a-client-connection"></a>클라이언트 연결 설정

XMLA 엔드포인트를 사용하도록 설정한 후에는 용량에서 작업 영역에 대한 연결을 테스트하는 것이 좋습니다. 자세한 내용은 [프리미엄 작업 영역에 연결](service-premium-connect-tools.md#connecting-to-a-premium-workspace)을 참조하세요. 또한 현재 XMLA 연결 제한 사항에 대한 유용한 팁과 정보는 [연결 요구 사항](service-premium-connect-tools.md#connection-requirements) 섹션을 참조하세요.

### <a name="connecting-with-a-service-principal"></a>서비스 주체로 연결

테넌트 설정에서 서비스 주체가 Power BI API를 사용할 수 있도록 설정한 경우 [서비스 주체 사용](service-premium-service-principal.md#enable-service-principals)에 설명된 대로 서비스 주체를 사용하여 XMLA 엔드포인트에 연결할 수 있습니다. 서비스 주체에는 작업 영역 또는 데이터 세트 수준에서 일반 사용자와 동일한 수준의 액세스 권한이 필요합니다.

서비스 주체를 사용하려면 연결 문자열에서 다음과 같이 애플리케이션 ID 정보를 지정해야 합니다.

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

예:

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

다음과 같은 오류가 표시되는 경우

"계정 정보가 불완전하기 때문에 데이터 세트에 연결할 수 없습니다. 서비스 주체의 경우 app:\<appId>@\<tenantId> 형식을 사용하여 앱 ID와 함께 테넌트 ID를 지정한 후 다시 시도하세요."

올바른 형식을 사용하여 앱 ID와 함께 테넌트 ID를 지정해야 합니다.

테넌트 ID 없이 앱 ID를 지정하는 것도 유효합니다. 그러나 이 경우 데이터 원본 URL의 `myorg` 별칭을 실제 테넌트 ID로 바꾸어야 합니다. 그러면 Power BI가 올바른 테넌트에서 서비스 주체를 찾을 수 있습니다. 하지만 모범 사례로 `myorg` 별칭을 사용하고 사용자 ID 매개 변수에 앱 ID와 함께 테넌트 ID를 지정합니다.

### <a name="connecting-with-azure-active-directory-b2b"></a>Azure Active Directory B2B를 사용하여 연결

Power BI에서 Azure AD(Azure Active Directory) B2B(기업 간) 지원을 통해 외부 게스트 사용자에게 XMLA 엔드포인트를 통해 데이터 세트에 대한 액세스를 제공할 수 있습니다. Power BI 관리 포털에서 [외부 사용자와 콘텐츠 공유](service-admin-portal.md#export-and-sharing-settings) 설정이 사용하도록 설정되어 있는지 확인합니다. 자세한 내용은 [Azure AD B2B에서 외부 게스트 사용자에게 Power BI 콘텐츠 배포](service-admin-azure-ad-b2b.md)를 참조하세요.

## <a name="deploying-a-dataset"></a>데이터 세트 배포

Visual Studio(SSDT)의 테이블 형식 모델 프로젝트를 Azure Analysis Services와 거의 동일하게 Power BI Premium 작업 영역에 배포할 수 있습니다. 그러나 Power BI Premium 작업 영역에 배포하는 경우 몇 가지 추가 고려 사항이 있습니다. XMLA 엔드포인트를 사용하여 데이터 세트 연결 문서의 [Visual Studio에서 모델 프로젝트 배포(SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) 섹션을 검토해야 합니다.

### <a name="deploying-a-new-model"></a>새 모델 배포

기본 구성에서 Visual Studio는 데이터 원본에서 데이터 세트로 데이터를 로드하는 배포 작업의 일부로 모델을 처리하려고 합니다. [Visual Studio에서 모델 프로젝트 배포(SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt)에 설명된 것처럼, 배포 작업의 일부로 데이터 원본 자격 증명을 지정할 수 없기 때문에 이 작업이 실패할 수 있습니다. 대신, 데이터 원본에 대한 자격 증명이 아직 기존 데이터 세트에 대해 정의되지 않은 경우 Power BI 사용자 인터페이스를 사용하여 데이터 세트 설정에서 데이터 원본 자격 증명을 지정해야 합니다(**데이터 세트** > **설정** > **데이터 원본 자격 증명** > **자격 증명 편집**). 데이터 원본 자격 증명을 정의하면 Power BI가 메타데이터 배포에 성공하고 데이터 세트를 만든 후 모든 새 데이터 세트에 대해 자동으로 이 데이터 원본에 대한 자격 증명을 적용할 수 있습니다.

Power BI가 새 데이터 세트를 데이터 원본 자격 증명에 바인딩할 수 없는 경우 아래와 같이 "데이터베이스를 처리할 수 없습니다. 이유: 수정 내용을 서버에 저장하지 못했습니다."라는 오류가 오류 코드 "DMTS_DatasourceHasNoCredentialError"와 함께 표시됩니다.

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="모델 배포 오류":::

처리 실패를 방지하려면 다음 그림에 표시된 것처럼 **배포 옵션** > **처리 옵션** 을 **처리 안 함** 으로 설정합니다. 그러면 Visual Studio에서 메타데이터만 배포합니다. 그런 다음 데이터 원본 자격 증명을 구성하고 Power BI 사용자 인터페이스의 데이터 세트에 대해 **지금 새로 고침** 을 클릭할 수 있습니다. 처리 문제를 해결하는 방법에 대한 자세한 내용은 이 문서의 뒷부분에 나오는 [데이터 세트 새로 고침](#refreshing-a-dataset) 섹션을 참조하세요.

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="처리 안 함 옵션":::

### <a name="new-project-from-an-existing-dataset"></a>기존 데이터 세트의 새 프로젝트

Power BI Premium 작업 영역의 기존 데이터 세트에서 메타데이터를 가져와서 Visual Studio에 새 테이블 형식 프로젝트를 만들 수는 없습니다. 그러나 SQL Server Management Studio를 사용하여 데이터 세트에 연결하고 메타데이터를 스크립팅한 다음 다른 테이블 형식 프로젝트에서 다시 사용할 수 있습니다.

## <a name="migrating-a-dataset-to-power-bi"></a>데이터 세트를 Power BI로 마이그레이션

테이블 형식 모델에 대해 호환성 수준을 1500 이상으로 지정하는 것이 좋습니다. 이 호환성 수준은 대부분의 기능과 데이터 원본 유형을 지원합니다. 이후 호환성 수준은 이전 수준과 호환됩니다.

### <a name="supported-data-providers"></a>지원되는 데이터 공급자

1500 호환성 수준에서 Power BI는 다음과 같은 데이터 원본 유형을 지원합니다.

- 공급자 데이터 원본(모델 메타데이터에 연결 문자열이 있는 레거시)
- 구조적 데이터 원본(1400 호환성 수준에서 도입됨)
- 데이터 원본의 인라인 M 선언(Power BI Desktop의 선언을 따름)

데이터 가져오기 흐름을 진행하는 경우 Visual Studio에서 기본적으로 만드는 구조적 데이터 원본을 사용하는 것이 좋습니다. 그러나 공급자 데이터 원본을 사용하는 기존 모델을 Power BI로 마이그레이션하려는 경우 공급자 데이터 원본이 지원되는 데이터 공급자를 사용하는지 확인합니다. 특히 Microsoft OLE DB Driver for SQL Server 및 타사 ODBC 드라이버가 있습니다. OLE DB Driver for SQL Server의 경우 데이터 원본 정의를 .NET Framework Data Provider for SQL Server로 전환해야 합니다. Power BI 서비스에서 사용할 수 없는 타사 ODBC 드라이버의 경우 구조적 데이터 원본 정의로 전환해야 합니다.

또한 SQL Server 데이터 원본 정의에서 오래된 Microsoft OLE DB Driver for SQL Server(SQLNCLI11)를 .NET Framework Data Provider for SQL Server로 바꾸는 것이 좋습니다.

다음 표에는 .NET Framework Data Provider for SQL Server 연결 문자열이 OLE DB Driver for SQL Server에 해당하는 연결 문자열을 대체하는 예제가 나와 있습니다.

|SQL Server용 OLE DB 드라이버  |.NET Framework Data Provider for SQL Server   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>파티션 원본 상호 참조

데이터 원본 유형이 여러 개인 것과 마찬가지로 한 테이블 형식 모델이 테이블에 데이터를 가져오기 위해 포함할 수 있는 파티션 원본 유형도 여러 개입니다. 특히 파티션은 쿼리 파티션 원본 또는 M 파티션 원본을 사용할 수 있습니다. 이러한 파티션 원본 유형은 공급자 데이터 원본 또는 구조적 데이터 원본을 참조할 수 있습니다. Azure Analysis Services의 테이블 형식 모델은 이러한 다양한 데이터 원본 및 파티션 유형을 상호 참조하는 것을 지원하지만 Power BI는 보다 엄격한 관계를 적용합니다. 쿼리 파티션 원본은 공급자 데이터 원본을 참조해야 하고, M 파티션 원본은 구조적 데이터 원본을 참조해야 합니다. 다른 조합은 Power BI에서 지원되지 않습니다. 상호 참조하는 데이터 세트를 마이그레이션하려면 다음 표에 지원되는 구성이 설명되어 있습니다.  

|데이터 원본   |파티션 원본   |주석   |XMLA 엔드포인트를 사용하는 Power BI Premium에서 지원   |
|---------|---------|---------|---------|
|공급자 데이터 원본      |   쿼리 파티션 원본      |   AS 엔진은 카트리지 기반 연결 스택을 사용하여 데이터 원본에 액세스합니다.       |     예     |
|공급자 데이터 원본      |   M 파티션 원본       |   AS 엔진은 공급자 데이터 원본을 일반 구조적 데이터 원본으로 변환한 다음 매시업 엔진을 사용하여 데이터를 가져옵니다.       |    아니요     |
|구조적 데이터 동기화      |     쿼리 파티션 원본     |    AS 엔진은 파티션 원본에 대한 기본 쿼리를 M 식으로 래핑한 다음 매시업 엔진을 사용하여 데이터를 가져옵니다.      |    아니요     |
|구조적 데이터 동기화      |    M 파티션 원본      |     AS 엔진은 매시업 엔진을 사용하여 데이터를 가져옵니다.     |   예      |

## <a name="refreshing-a-dataset"></a>데이터 세트 새로 고침

XMLA 엔드포인트를 사용하면 테이블 형식 모델뿐만 아니라 Power BI Desktop에서 만든 데이터 세트에 대해 새로 고침 작업을 수행할 수 있습니다. 후자를 지원하려면 강화된 스토리지 형식 설정을 지정해야 합니다. 이 설정은 XMLA 엔드포인트를 사용하여 처리 또는 기타 읽기/쓰기 작업을 수행하려는 경우에 필요합니다. Power BI Desktop의 미리 보기 기능에서 설정을 찾을 수 있습니다. 설정이 완료되면 PBIX 솔루션을 Power BI Premium 작업 영역에 다시 게시합니다.  

강화된 메타데이터가 없는 모델에 대해 XMLA 엔드포인트를 통해 새로 고침을 수행하는 경우 Power BI는 다음 오류를 반환합니다. "이 작업은 Power BI Premium에서 'DefaultPowerBIDataSourceVersion' 속성이 'PowerBI_V3'로 설정된 모델에서만 지원됩니다."

### <a name="data-sources-and-impersonation"></a>데이터 원본 및 가장

공급자 데이터 원본에 대해 정의할 수 있는 가장 설정은 Power BI와 관련이 없습니다. Power BI는 데이터 세트 설정에 따라 다른 메커니즘을 사용하여 데이터 원본 자격 증명을 관리합니다. 따라서 공급자 데이터 원본을 만드는 경우 **서비스 계정** 을 선택해야 합니다.

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="서비스 계정 가장":::

### <a name="fine-grained-processing"></a>세분화된 처리

Power BI에서 예약된 새로 고침 또는 요청 시 새로 고침을 트리거하는 경우 Power BI는 일반적으로 전체 데이터 세트를 새로 고칩니다. 대부분의 경우 더 선택적으로 새로 고침을 수행하는 것이 더 효율적입니다. 아래와 같이 SSMS(SQL Server Management Studio)에서 세분화된 처리 작업을 수행하거나 타사 도구 또는 스크립트를 사용할 수 있습니다.

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="SSMS의 프로세스 테이블":::

### <a name="overrides-in-refresh-tmsl-command"></a>Refresh TMSL 명령의 재정의

[ 명령(TMSL)](/analysis-services/tmsl/refresh-command-tmsl)의 재정의를 통해 사용자는 새로 고침 작업의 다른 파티션 쿼리 정의 또는 데이터 원본 정의를 선택할 수 있습니다. 현재 Power BI Premium에서는 **재정의가 지원되지 않습니다**. “Power BI Premium에서는 확장 바인딩이 허용되지 않습니다. 자세한 내용은 제품 설명서의 ‘XMLA 읽기/쓰기 지원’을 참조하세요.” 가 반환됩니다.

## <a name="errors-in-ssms---premium-gen-2"></a>SSMS의 오류 - Premium Gen2

### <a name="query-execution"></a>쿼리 실행

[Premium Gen2](service-premium-what-is.md#power-bi-premium-generation-2-preview) 용량의 작업 영역에 연결된 경우 SQL Server Management Studio에 다음 오류가 표시될 수 있습니다.

```
Executing the query ...
Error -1052311437:
```

이는 SSMS v18.7.1과 함께 설치된 클라이언트 라이브러리가 세션 추적을 지원하지 않기 때문에 발생합니다. 이 문제는 SSMS의 향후 릴리스에서 해결될 예정입니다.

### <a name="refresh-operations"></a>새로 고침 작업

SSMS v18.7.1 이하를 사용하여 Premium Gen2 용량의 데이터 세트에서 장기 실행(1분 초과) 새로 고침 작업을 수행하는 경우, 새로 고침 작업이 성공하더라도 SSMS에서 다음과 같은 오류를 표시할 수 있습니다.

```
Executing the query ...
Error -1052311437:
The remote server returned an error: (400) Bad Request.

Technical Details:
RootActivityId: 3716c0f7-3d01-4595-8061-e6b2bd9f3428
Date (UTC): 11/13/2020 7:57:16 PM
Run complete
```

이는 새로 고침 요청의 상태가 올바르지 않게 추적되는 클라이언트 라이브러리의 알려진 문제 때문입니다. 이 문제는 SSMS의 향후 릴리스에서 해결될 예정입니다.

## <a name="see-also"></a>참고 항목

[XMLA 엔드포인트로 데이터 세트 연결](service-premium-connect-tools.md)  
[서비스 주체를 사용하여 Premium 작업 영역 및 데이터 세트 작업 자동화](service-premium-service-principal.md)  
[Excel에서 분석 문제 해결](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)  
[테이블 형식 모델 솔루션 배포](/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current&preserve-view=true)
