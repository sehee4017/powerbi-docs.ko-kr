---
title: 동적 바인딩을 사용하여 데이터 세트에 보고서 연결
description: 동적 바인딩을 사용하여 보고서를 포함하는 방법을 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: ba63b8be32600428075b9304a5a29fef62a9d6c8
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236848"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>동적 바인딩을 사용하여 데이터 세트에 보고서 연결 

보고서가 데이터 세트에 연결된 경우 동적 바인딩을 사용할 수 있습니다. 보고서와 데이터 세트 간의 연결을 *바인딩*이라고 합니다. 포함 시 바인딩이 결정되면, 이전에 미리 결정되는 것과 달리, 이 바인딩을 동적 바인딩이라고 합니다.

‘동적 바인딩’을 사용하여 Power BI 보고서를 포함하는 경우, 사용자의 자격 증명에 따라 동일한 보고서를 여러 데이터 세트에 연결할 수 있습니다.

즉, 연결된 데이터 세트에 따라 한 보고서를 사용하여 여러 정보를 표시할 수 있습니다. 예를 들어 소매 판매 값을 표시하는 보고서를 여러 소매업체 데이터 세트에 연결하고, 연결된 소매업체의 데이터 세트에 따라 여러 결과를 생성할 수 있습니다.

보고서와 데이터 세트가 동일한 작업 영역에 있지 않아도 됩니다. 두 작업 영역(보고서가 포함된 작업 영역과 데이터 세트가 포함된 작업 영역)을 [용량](azure-pbie-create-capacity.md)에 모두 할당해야 합니다.

포함된 프로세스의 일부로, *충분한 권한이 있는 토큰을 생성하고* *구성 개체를 조정*하세요.

## <a name="generating-a-token-with-sufficient-permissions"></a>충분한 권한이 있는 토큰 생성

동적 바인딩은 ‘조직에 대해 포함’ 및 ‘고객에 대해 포함’의 두 가지 시나리오에서 모두 지원됩니다.  아래 표에는 각 시나리오의 고려 사항이 설명되어 있습니다.

|시나리오  |데이터 소유권  |토큰  |요구 사항  |
|---------|---------|---------|---------|
|‘조직에 대해 포함’    |사용자 소유 데이터         |Power BI 사용자의 액세스 토큰         |사용하는 Azure AD 토큰의 사용자에게 모든 아티팩트에 대한 적절한 권한이 있어야 합니다.         |
|‘고객에 대해 포함’     |앱 소유 데이터         |비 Power BI 사용자의 액세스 토큰         |보고서와 동적으로 바인딩된 데이터 세트에 대한 사용 권한을 모두 포함해야 합니다. 여러 아티팩트를 지원하는 포함 토큰을 생성하려면 [여러 항목에 대한 포함 토큰을 생성하기 위한 API](embed-sample-for-customers.md#multiEmbedToken)를 사용합니다.         |

## <a name="adjusting-the-config-object"></a>구성 개체 조정
구성 개체에 `datasetBinding`을 추가합니다. 아래 예제를 참조로 사용합니다.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>다음 단계

Power BI의 포함 기능을 처음 사용하는 경우, 다음 자습서를 검토하여 Power BI 콘텐츠를 포함하는 방법을 알아보세요.
* [자습서: 고객의 애플리케이션에 Power BI 콘텐츠 포함](embed-sample-for-customers.md)
* [자습서: 조직의 애플리케이션에 Power BI 콘텐츠 포함](embed-sample-for-your-organization.md)