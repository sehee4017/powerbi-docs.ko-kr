---
title: Power BI Desktop에서 추천 테이블 설정(미리 보기)
description: Excel의 데이터 형식 갤러리에 표시되도록 Power BI Desktop에서 추천 테이블을 만듭니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 09/17/2020
LocalizationGroup: Share your work
ms.openlocfilehash: d2d87f16b8100424b47277360354d79ee834d467
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411934"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>Power BI Desktop에서 추천 테이블 설정(미리 보기)

Excel의 데이터 형식 갤러리에서 사용자는 Power BI 데이터 세트의 ‘추천 테이블’에서 데이터를 찾을 수 있습니다. 이 문서에서는 테이블을 데이터 세트의 ‘추천’ 테이블로 설정하는 방법을 알아봅니다. 해당 태그를 사용하면 사용자가 Excel 시트에 엔터프라이즈 데이터를 더 쉽게 추가할 수 있습니다. 추천 테이블을 설정 및 공유하는 기본 단계는 다음과 같습니다.

1. Power BI Desktop에서 데이터 세트의 추천 테이블을 식별합니다(이 문서).
1. 추천 테이블이 포함된 데이터 세트를 새 작업 영역 중 하나에 저장합니다. 보고서 작성자는 관련 추천 테이블을 사용하여 보고서를 만들 수 있습니다. 
1. 조직의 나머지 부분은 관련되거나 새로 고칠 수 있는 데이터를 사용하기 위해 Excel에서 ‘데이터 형식’이라고도 하는 해당 추천 테이블에 연결할 수 있습니다. [Excel에서 Power BI 추천 테이블에 액세스(미리 보기)](service-excel-featured-tables.md) 문서에서는 Excel에서 해당 추천 테이블을 사용하는 방법을 설명합니다.

> [!NOTE]
> [Power BI에서 데이터 세트를 승격하거나 인증](../collaborate-share/service-endorse-content.md)할 수 있습니다. 이를 ‘보증’이라고 합니다. Excel은 데이터 형식 갤러리에서 보증된 데이터 세트에 있는 테이블을 우선시합니다. Excel은 먼저 인증된 데이터 세트에 있는 주요 테이블을 나열한 후에 승격된 데이터 세트에 있는 테이블을 나열합니다. 그다음에 보증되지 않은 데이터 세트에 있는 주요 테이블을 나열합니다. 

## <a name="turn-on-the-featured-table-preview"></a>주요 테이블 미리 보기 설정

1. Power BI Desktop에서 **파일** > **옵션 및 설정** > **옵션** > **미리 보기 기능** 을 선택합니다.
2. **주요 테이블** 확인란을 선택합니다.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="미리 보기 주요 테이블 옵션":::

3. Power BI Desktop을 다시 시작합니다.

## <a name="select-a-table"></a>테이블 선택

1. Power BI Desktop에서 모델 뷰로 이동합니다.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="모델 뷰":::
 
2. 테이블을 선택하고 **주요 테이블** 을 **예** 로 설정합니다.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="주요 테이블을 예로 설정":::

4. **이 주요 테이블 설정** 에서 필수 필드를 제공합니다.

    - **설명**. 
        > [!TIP]
        > Power BI 보고서 작성자가 식별하는 데 도움이 되도록 “추천 테이블”로 설명을 시작합니다.
    - **행 레이블** 필드 값은 사용자가 행을 쉽게 식별할 수 있도록 Excel에서 사용됩니다. 이 값은 **데이터 선택기** 창 및 **정보** 카드에 연결된 셀의 셀 값으로 표시됩니다. 
    - **키 열** 필드 값은 행의 고유 ID를 제공합니다. Excel이 이 값을 사용하여 셀을 테이블의 특정 행에 연결할 수 있습니다.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="주요 테이블 설정":::

1. 데이터 세트를 Power BI 서비스에 게시하거나 가져오면 Excel 데이터 형식 갤러리에 추천 테이블이 표시됩니다. 사용자 및 기타 보고서 작성자는 해당 데이터 세트를 기반으로 작성되는 보고서를 만들 수도 있습니다.

1. Excel: 
    - Excel은 데이터 형식 목록을 캐시합니다. 그러므로 새로 게시된 주요 테이블을 보려면 Excel을 다시 시작해야 합니다.
    - 일부 데이터 세트는 미리 보기에서 지원되지 않으며, 이러한 데이터 세트에 정의된 주요 테이블은 Excel에 표시되지 않습니다. 자세한 내용은 다음 섹션, 고려 사항 및 제한 사항을 참조하세요.

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항

초기 미리 보기의 제한 사항은 다음과 같습니다.

- 다음 기능을 사용하는 Power BI 데이터 세트의 주요 테이블은 Excel에 표시되지 않습니다.

    - DirectQuery 데이터 세트
    - 라이브 연결을 사용하는 데이터 세트

- Excel에서는 주요 테이블의 열 및 계산 열의 데이터만 표시합니다. 관련 테이블에 정의된 측정값 및 관계에서 계산된 암시적 측정값은 초기 미리 보기에서 제공되지 않습니다.
- Excel에서는 새 Power BI 작업 영역에 저장된 주요 테이블만 표시합니다. 클래식 작업 영역에 저장된 추천 테이블은 Excel에서 데이터 형식으로 표시되지 않습니다. Power BI에서 [클래식 작업 영역을 새 작업 영역으로 업그레이드](service-upgrade-workspaces.md)할 수 있습니다.
- 기타 Excel 고려 사항을 확인하려면 “Excel에서 Power BI 추천 테이블에 액세스” 문서에서 [고려 사항 및 제한 사항](service-excel-featured-tables.md#considerations-and-limitations)을 참조하세요.

## <a name="next-steps"></a>다음 단계

- [Excel에서 Power BI 추천 테이블에 액세스](service-excel-featured-tables.md)
- Excel 설명서에서 [Power BI의 Excel 데이터 형식](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)을 사용하는 방법에 대해 알아보세요.
- 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)

