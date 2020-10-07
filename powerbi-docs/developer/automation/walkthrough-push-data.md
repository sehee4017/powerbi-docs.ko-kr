---
title: 데이터 세트에 데이터 푸시
description: Power BI 데이터 세트에 데이터 푸시
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/22/2019
ms.openlocfilehash: 792afe42cf302ae552b7f8f1c14d5f232ade320f
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746703"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Power BI 데이터 세트에 데이터 푸시

Power BI API를 사용하면 데이터를 Power BI 데이터 세트에 푸시할 수 있습니다. 이 문서에서는 Product 테이블을 포함하는 Sales Marketing 데이터 세트를 기존 데이터 세트에 푸시하는 방법을 알아봅니다.

시작하기 전에 Azure AD(Azure Active Directory) 및 [Power BI 계정](../embedded/create-an-azure-active-directory-tenant.md)이 필요합니다.

## <a name="steps-to-push-data-into-a-dataset"></a>데이터 세트에 데이터를 푸시하는 단계

* 1단계: [Azure AD에 앱 등록](../embedded/register-app.md)
* 2단계: [인증 액세스 토큰 가져오기](walkthrough-push-data-get-token.md)
* 3단계: [Power BI에서 데이터 세트 만들기](walkthrough-push-data-create-dataset.md)
* 4단계: [Power BI 테이블에 행을 추가할 데이터 세트 가져오기](walkthrough-push-data-get-datasets.md)
* 5단계: [Power BI 테이블에 행 추가](walkthrough-push-data-add-rows.md)

다음 섹션에서는 데이터를 푸시하는 Power BI API 작업에 대한 일반적인 내용을 설명합니다.

## <a name="power-bi-api-operations-to-push-data"></a>데이터를 푸시하는 Power BI API 작업

Power BI REST API를 사용하여 데이터 원본을 Power BI로 푸시할 수 있습니다. 앱이 데이터 세트에 행을 추가하면 대시보드 타일이 자동으로 새 데이터로 업데이트됩니다. 데이터를 푸시하려면 [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset) 및 [PostRows](/rest/api/power-bi/pushdatasets/datasets_postrows) 작업을 사용합니다. 데이터 세트를 찾으려면 [데이터 세트 가져오기](/rest/api/power-bi/datasets/getdatasets) 작업을 사용합니다. 이러한 작업에서는 그룹 ID를 전달하여 그룹으로 작업할 수 있습니다. 그룹 ID 목록을 가져오려면 [그룹 가져오기](/rest/api/power-bi/groups/getgroups) 작업을 사용합니다.

데이터 세트에 데이터를 푸시하는 작업은 다음과 같습니다.

* [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [데이터 세트 가져오기](/rest/api/power-bi/datasets/getdatasets)
* [행 게시](/rest/api/power-bi/pushdatasets/datasets_postrows)
* [그룹 가져오기](/rest/api/power-bi/groups/getgroups)

Power BI에서 데이터 세트를 만들려면 Power BI 서비스에 JSON(JavaScript Object Notation) 문자열을 전달합니다. JSON에 대한 자세한 내용은 [JSON 소개](https://json.org/)를 참조하세요.

데이터 세트에 대한 JSON 문자열의 형식은 다음과 같습니다.

**Power BI 데이터 세트 JSON 개체**

```json
{"name": "dataset_name", "tables":
    [{"name": "", "columns":
        [{ "name": "column_name1", "dataType": "data_type"},
         { "name": "column_name2", "dataType": "data_type"},
         { ... }
        ]
      }
    ]
}
```

Sales Marketing 데이터 세트 예제에서는 아래와 같은 JSON 문자열을 전달합니다. 이 예제에서 **SalesMarketing**은 데이터 세트의 이름이고 **Product**는 테이블의 이름입니다. 테이블을 정의한 후 테이블 스키마를 정의합니다. **SalesMarketing** 데이터 세트의 경우 테이블 스키마는 다음 열을 포함합니다. ProductID, Manufacturer, Category, Segment, Product 및 IsCompete.

**예제 데이터 세트 개체 JSON**

```json
{
    "name": "SalesMarketing",
    "tables": [
        {
            "name": "Product",
            "columns": [
            {
                "name": "ProductID",
                "dataType": "int"
            },
            {
                "name": "Manufacturer",
                "dataType": "string"
            },
            {
                "name": "Category",
                "dataType": "string"
            },
            {
                "name": "Segment",
                "dataType": "string"
            },
            {
                "name": "Product",
                "dataType": "string"
            },
            {
                "name": "IsCompete",
                "dataType": "bool"
            }
            ]
        }
    ]
}
```

Power BI 테이블 스키마에는 다음과 같은 데이터 형식을 사용할 수 있습니다.

## <a name="power-bi-table-data-types"></a>Power BI 테이블 데이터 형식

| **데이터 형식** | **제한 사항** |
| --- | --- |
| Int64 |Int64.MaxValue 및 Int64.MinValue는 허용되지 않습니다. |
| Double |Double.MaxValue 및 Double.MinValue 값은 허용되지 않습니다. NaN은 지원되지 않습니다.+Infinity 및 -Infinity는 일부 함수(예: Min, Max)에서 지원되지 않습니다. |
| Boolean |없음 |
| Datetime |데이터 로드 동안 일 분수가 포함된 값을 1/300초(3.33ms)의 배수로 양자화합니다. |
| String |현재 최대 128K자를 허용합니다. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Power BI에 데이터 푸시에 대해 자세히 알아보기

데이터 세트에 데이터 푸시를 시작하려면 왼쪽 탐색 창에서 [1단계: Azure AD에 앱 등록](../embedded/register-app.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

* [Power BI에 등록](../embedded/create-an-azure-active-directory-tenant.md)  
* [JSON 개요](https://json.org/)  
* [Power BI REST API 개요](overview-of-power-bi-rest-api.md)  

궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)