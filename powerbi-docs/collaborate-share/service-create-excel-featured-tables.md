---
title: Power BI Desktop에서 추천 테이블 설정
description: Excel 조직 데이터 형식 갤러리에 표시되도록 Power BI Desktop에서 추천 테이블을 만듭니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 8c03263e7cc3a8833c06523601fcc12ef14484e1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906891"
---
# <a name="set-featured-tables-in-power-bi-desktop-to-show-in-excel-organization-data-types-gallery"></a>Excel 조직 데이터 형식 갤러리에 표시되도록 Power BI Desktop에서 추천 테이블 설정

Excel의 데이터 형식 갤러리에서 사용자는 Power BI 데이터 세트의 ‘추천 테이블’에서 데이터를 찾을 수 있습니다. 이 문서에서는 테이블을 데이터 세트의 ‘추천’ 테이블로 설정하는 방법을 알아봅니다. 해당 태그를 사용하면 사용자가 Excel 시트에 엔터프라이즈 데이터를 더 쉽게 추가할 수 있습니다. 추천 테이블을 설정 및 공유하는 기본 단계는 다음과 같습니다.

1. Power BI Desktop에서 데이터 세트의 추천 테이블을 식별합니다(이 문서).
1. 추천 테이블이 포함된 데이터 세트를 새 작업 영역 중 하나에 저장합니다. 보고서 작성자는 관련 추천 테이블을 사용하여 보고서를 만들 수 있습니다. 
1. 조직의 나머지 부분은 관련되거나 새로 고칠 수 있는 데이터를 사용하기 위해 Excel에서 ‘데이터 형식’이라고도 하는 해당 추천 테이블에 연결할 수 있습니다. [Excel에서 Power BI 추천 테이블에 액세스](service-excel-featured-tables.md) 문서에서는 Excel에서 해당 추천 테이블을 사용하는 방법을 설명합니다.

> [!NOTE]
> [Power BI에서 데이터 세트를 승격하거나 인증](../collaborate-share/service-endorse-content.md)할 수 있습니다. 이를 ‘보증’이라고 합니다. Excel은 데이터 형식 갤러리에서 보증된 데이터 세트에 있는 테이블을 우선시합니다. Excel은 먼저 인증된 데이터 세트에 있는 주요 테이블을 나열한 후에 승격된 데이터 세트에 있는 테이블을 나열합니다. 그다음에 보증되지 않은 데이터 세트에 있는 주요 테이블을 나열합니다. 

> [!NOTE]
> Power BI Desktop 2020년 12월 버전부터 추천 테이블 만들기는 기본적으로 제공됩니다. 이전 버전을 사용하는 경우 Power BI Desktop을 업그레이드하거나 **파일** > **옵션 및 설정** > **옵션** > **미리 보기 기능** 옵션을 통해 **Featured tables**(추천 테이블) 기능을 사용하도록 설정합니다.

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
    - 일부 데이터 세트는 지원되지 않습니다. 해당 데이터 세트에 정의된 추천 테이블은 Excel에 표시되지 않습니다. 자세한 내용은 다음 섹션, 고려 사항 및 제한 사항을 참조하세요.

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항

현재 제한 사항은 다음과 같습니다.

- 통합은 현재 채널의 Excel에서 사용할 수 있습니다.
- 다음 기능을 사용하는 Power BI 데이터 세트의 주요 테이블은 Excel에 표시되지 않습니다. 

    - DirectQuery 데이터 세트
    - 라이브 연결을 사용하는 데이터 세트

- Excel에서는 추천 테이블의 열, 계산 열, 추천 테이블에 정의된 측정값의 데이터만 표시합니다. 다음은 제공되지 않습니다.
   
    - 관련 테이블에 정의된 측정값
    - 관계에서 계산된 암시적 측정값

- Excel에서는 새 Power BI 작업 영역에 저장된 추천 테이블(‘데이터 형식’)만 표시합니다. 클래식 작업 영역에 저장된 추천 테이블은 Excel에서 데이터 형식으로 표시되지 않습니다. Power BI에서 [클래식 작업 영역을 새 작업 영역으로 업그레이드](service-upgrade-workspaces.md)할 수 있습니다.

Excel의 데이터 형식 환경은 조회 함수와 유사합니다. Excel 시트에서 제공하는 셀 값을 사용하여 Power BI 주요 테이블에서 일치하는 행을 검색합니다. 검색 환경에는 다음과 같은 동작이 있습니다.

- 행 일치는 주요 테이블의 텍스트 열을 기반으로 합니다. Power BI Q&A와 동일한 인덱싱을 사용하며 영어 검색에 최적화되어 있습니다. 다른 언어로 검색하면 정확하게 일치되지 않을 수 있습니다. 
- 대부분의 숫자 열은 일치에 고려되지 않습니다. 행 레이블이나 키 열이 숫자인 경우 일치에 포함됩니다.
- 일치는 개별 검색어에 대한 정확한 일치 및 접두사 일치를 기반으로 합니다. 셀의 값은 공백 또는 탭 등의 기타 공백 문자를 기준으로 분할됩니다. 그러면 각 단어가 검색어로 간주됩니다. 정확한 일치 및 접두사 일치를 위해 행의 텍스트 필드 값을 각 검색어와 비교합니다. 행의 텍스트 필드가 검색어로 시작하는 경우 접두사 일치가 반환됩니다. 예를 들어 셀에 "Orange County"가 포함된 경우 "Orange" 및 "County"는 별개의 검색어입니다. 

    - 값이 “Orange” 또는 “County”와 정확히 일치하는 텍스트 열이 있는 행이 반환됩니다. 
    - 값이 “Orange” 또는 “County”로 시작하는 텍스트 열이 있는 행이 반환됩니다. 
    - 중요한 점은 "Orange" 또는 "County"를 포함하지만 이러한 단어로 시작하지 않는 행은 반환되지 않는다는 것입니다.

- Power BI는 각 셀에 대해 최대 100개의 행 제안을 반환합니다.
- 일부 기호는 지원되지 않습니다.
- 추천 테이블 설정 또는 업데이트는 XMLA 엔드포인트에서 지원되지 않습니다.
- 데이터 모델이 있는 Excel 파일을 사용하여 주요 테이블을 게시할 수 있습니다. Power BI Desktop에 데이터를 로드한 다음 추천 테이블을 게시합니다.
- 추천 테이블에서 테이블 이름, 행 레이블 또는 키 열을 변경하면 테이블의 행에 연결된 셀이 있는 Excel 사용자에게 영향을 줄 수 있습니다. 
- Excel은 Power BI 데이터 세트에서 데이터를 검색한 시간을 표시합니다. 이번에는 데이터가 반드시 Power BI에서 데이터를 새로 고친 시간 또는 데이터 세트에서 가장 최근인 데이터 요소의 시간은 아닙니다. 예를 들어 Power BI의 데이터 세트가 일주일 전에 새로 고쳐졌지만 새로 고침이 발생했을 때 기본 원본 데이터는 일주일이 지난 상태일 수 있습니다. 실제 데이터는 2주가 지난 것이지만 Excel은 데이터를 Excel로 가져온 날짜/시간에 데이터가 검색된 것으로 표시합니다.
- 기타 Excel 고려 사항을 확인하려면 “Excel에서 Power BI 추천 테이블에 액세스” 문서에서 [고려 사항 및 제한 사항](service-excel-featured-tables.md#considerations-and-limitations)을 참조하세요.

## <a name="next-steps"></a>다음 단계

- [Excel에서 Power BI 추천 테이블에 액세스](service-excel-featured-tables.md)
- Excel 설명서에서 [Power BI의 Excel 데이터 형식](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)을 사용하는 방법에 대해 알아보세요.
- 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)

