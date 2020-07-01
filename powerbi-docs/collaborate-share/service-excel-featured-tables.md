---
title: Excel에서 Power BI 주요 테이블에 액세스(미리 보기)
description: Excel의 데이터 형식 갤러리에서 Power BI 데이터 세트의 주요 테이블에서 데이터를 찾을 수 있습니다.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/20/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a872c0ada80a7168ebc6bb545de1ad474c4561b7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85226352"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Excel에서 Power BI 주요 테이블에 액세스(미리 보기)

Excel의 데이터 형식 갤러리에서 Power BI 데이터 세트의 주요 테이블에서 데이터를 찾을 수 있습니다. 주요 테이블을 사용하면 보다 쉽게 엔터프라이즈 데이터를 Excel 시트에 추가할 수 있습니다. 조직에서는 Power BI 인증 및 승격된 데이터 세트 기능을 사용하여 더 많은 사용자가 관련 있고 새로 고칠 수 있는 데이터를 찾아 더 나은 결정을 내릴 수 있습니다. Excel 설명서에서 [Power BI의 Excel 데이터 형식](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)을 사용하는 방법에 대해 자세히 알아보세요.

데이터 형식 갤러리에는 모델러가 Power BI 데이터 세트에서 큐레이팅한 주요 테이블만 표시됩니다. 또한 Power BI에서 액세스할 수 있는 모든 데이터 세트를 Excel에서 찾아볼 수 있습니다. Excel의 **데이터 리본**에서 **데이터 가져오기** 아래에 있는 **Power BI 데이터 세트** 옵션을 선택합니다.

## <a name="access-power-bi-data-through-the-excel-data-types-gallery"></a>Excel 데이터 형식 갤러리를 통해 Power BI 데이터에 액세스
Power BI 데이터 세트의 주요 테이블은 데이터 리본의 Excel 데이터 형식 갤러리에 표시됩니다.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Excel 데이터 리본":::

이 리본을 확장하면 갤러리에서 사용 가능한 상위 데이터 형식이 표시됩니다.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Excel 데이터 형식 갤러리":::
 
Power BI 주요 테이블에서 데이터를 조회하려면 Excel 시트에서 셀 또는 범위를 선택합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-select-cell.png" alt-text="셀 선택":::
 
사용자가 액세스할 수 있는 인증된 데이터 세트의 주요 테이블에서 데이터를 검색하려면 갤러리에서 **조직 데이터** 옵션을 선택합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data.png" alt-text="Excel 조직 데이터":::
 
검색하는 데이터의 종류를 알고 있거나 조직 데이터 옵션을 사용하여 일치하는 행을 찾을 수 없는 경우 특정 데이터 형식을 선택합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-select-data-type.png" alt-text="데이터 형식 선택":::
 
검색할 때 일치하는 행이 높은 신뢰도로 검색되는 경우 셀이 행에 즉시 연결됩니다. 연결된 항목 아이콘은 셀이 Power BI의 행에 연결되어 있음을 나타냅니다.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="연결된 항목 아이콘":::

셀에 잠재적으로 일치하는 행이 여러 개 있으면 데이터 선택기 창이 표시됩니다. 이 셀에는 물음표 아이콘이 표시됩니다. 이 아이콘을 클릭하면 해당 행에 대한 데이터 선택기 창이 열립니다. 다음은 사용자가 A2:A7 범위를 선택하고 Power BI 추천 테이블을 검색한 예입니다.

:::image type="content" source="media/service-excel-featured-tables/excel-multiple-matches.png" alt-text="여러 개의 잠재적으로 일치하는 행":::

**데이터 선택기** 창에는 잠재적으로 일치하는 행이 표시됩니다.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Excel 데이터 선택기 창":::
 
조직 데이터 옵션은 여러 데이터 형식의 행을 반환할 수 있습니다. Excel은 잠재적으로 일치하는 행을 원래 데이터 형식에 따라 그룹화합니다. Excel은 가장 근사하게 일치하는 행을 기준으로 데이터 형식을 정렬합니다. 갈매기형 화살표를 사용하여 데이터 형식을 일치하는 행으로 축소/확장합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Excel 데이터 선택기 창":::
 
올바른 행을 선택할 수 있도록 각 행에서 행 이름을 선택하여 행 세부 정보를 확인합니다. 행을 찾았으면 **선택**을 눌러 Excel의 셀에 행을 연결합니다. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-select.png" alt-text="데이터 선택기 세부 정보":::
 
행이 선택되면 셀이 행에 연결되고 해당 값이 Power BI 주요 테이블의 **행 레이블** 필드 값에 연결됩니다. 

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Excel 연결된 항목":::
 
**연결된 셀** 아이콘을 선택하면 주요 테이블의 모든 필드 및 계산 필드의 데이터가 포함된 카드가 표시됩니다. 카드의 제목에는 주요 테이블의 행 레이블 필드 값이 표시됩니다.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="연결된 항목 세부 정보":::

**데이터 삽입** 아이콘을 선택하여 필드 값을 표에 추가합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-insert-data.png" alt-text="데이터 삽입"::: 

필드 목록에서 필드 이름을 선택하여 해당 값을 표에 추가합니다.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="필드 이름 선택":::

필드 값이 인접한 셀에 배치됩니다. 셀 수식은 연결된 셀 및 필드 이름을 참조하므로 Excel 함수에서 데이터를 사용할 수 있습니다.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel 셀 수식":::
 
데이터를 Excel 테이블로 서식 지정하는 경우 필드를 추가하면 테이블이 확장되고 열 머리글이 필드 이름과 일치하도록 설정됩니다. 동일한 데이터 형식에 연결된 행도 해당 값으로 채워집니다.

:::image type="content" source="media/service-excel-featured-tables/excel-field-column-name.png" alt-text="필드는 열 이름"::: 

## <a name="cell-formulas"></a>셀 수식

Excel 테이블을 사용하는 경우 연결된 테이블 열을 참조한 다음 `.`(마침표) 참조를 사용하여 데이터 필드를 추가할 수 있습니다.

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Excel 마침표 참조":::

마찬가지로 셀을 사용하는 경우 셀을 참조하고 `.`(마침표) 참조를 사용하여 필드를 검색할 수 있습니다.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="셀 마침표 참조":::
 
## <a name="data-caching-and-refresh"></a>데이터 캐싱 및 새로 고침

Excel이 셀을 Power BI 주요 테이블의 행에 연결할 때 Excel 파일의 모든 필드 값을 검색하고 저장합니다. 이 파일을 공유하는 모든 사용자는 Power BI에서 데이터를 요청하지 않고 모든 필드를 참조할 수 있습니다.  

**데이터** 리본의 **모두 새로 고침** 단추를 사용하여 연결된 셀의 데이터를 새로 고칩니다. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="모두 새로 고침":::
 
개별 셀을 새로 고칠 수도 있습니다. 셀을 마우스 오른쪽 단추로 클릭하고 **데이터 형식** > **새로 고침**을 선택합니다.

## <a name="show-a-card-change-or-convert-to-text"></a>카드 표시, 변경 또는 텍스트로 변환

연결된 셀에는 오른쪽 클릭 메뉴 옵션이 추가되었습니다. 셀을 마우스 오른쪽 단추로 클릭하고 **데이터 형식** >  

- **카드 표시**
- **새로 고침**
- **변경** 
- **텍스트로 변환**을 선택합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="마우스 오른쪽 단추 클릭, 텍스트로 변환":::
 
**텍스트로 변환**은 Power BI 주요 테이블의 행에 대한 링크를 제거합니다. 중요한 점은 셀의 텍스트가 연결된 셀의 행 레이블 값이라는 것입니다. 셀을 의도하지 않는 행에 연결한 경우 Excel에서 **실행 취소**를 선택하여 초기 셀 값을 복원합니다.

## <a name="licensing"></a>라이선싱
Excel 데이터 형식 갤러리와 Power BI 주요 테이블에 대한 연결된 환경은 Excel E5 및 G5 고객만 사용할 수 있습니다. 

## <a name="security"></a>보안

Power BI에서 사용 권한이 있는 데이터 세트의 주요 테이블만 볼 수 있습니다. 데이터를 새로 고칠 때 행을 검색하기 위해 Power BI의 데이터 세트에 액세스할 수 있는 권한이 있어야 합니다. 이를 위해 데이터 세트에 대한 빌드 또는 쓰기 권한이 필요합니다. Excel은 전체 행에 대해 반환되는 데이터를 캐시합니다. Excel 파일을 공유하는 모든 사용자는 모든 연결된 셀의 모든 필드에 대한 데이터를 볼 수 있습니다.

Power BI 데이터 세트에 행 수준 보안 또는 Microsoft Information Protection 민감도 레이블이 적용된 경우 해당 데이터 세트의 주요 테이블이 Excel 데이터 형식 갤러리에 포함되지 않습니다. 이는 초기 미리 보기의 제한 사항입니다.

## <a name="curate-a-featured-table-in-power-bi-desktop"></a>Power BI Desktop에서 주요 테이블 큐레이팅
Excel 데이터 형식 갤러리에는 Power BI 서비스에 업로드된 데이터 세트의 주요 테이블이 표시됩니다. Power BI Desktop을 사용하여 데이터 모델에서 주요 테이블을 큐레이팅한 다음 Power BI 서비스에 업로드합니다.

### <a name="turn-on-the-featured-table-preview"></a>주요 테이블 미리 보기 설정

1. Power BI Desktop에서 **파일** > **옵션 및 설정** > **옵션** > **미리 보기 기능**을 선택합니다.
2. **주요 테이블** 확인란을 선택합니다.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="미리 보기 주요 테이블 옵션":::

### <a name="select-a-table"></a>테이블 선택

1. Power BI Desktop에서 모델 뷰로 이동합니다.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="모델 뷰":::
 
2. 테이블을 선택하고 **주요 테이블**을 **예**로 설정합니다.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="주요 테이블을 예로 설정":::

4. **이 주요 테이블 설정**에서 필수 필드를 제공합니다.

    - **설명**.
    - **행 레이블** 필드 값은 사용자가 행을 쉽게 식별할 수 있도록 Excel에서 사용됩니다. 이 값은 **데이터 선택기** 창 및 **정보** 카드에 연결된 셀의 셀 값으로 표시됩니다. 
    - **키 열** 필드 값은 행의 고유 ID를 제공합니다. Excel이 이 값을 사용하여 셀을 테이블의 특정 행에 연결할 수 있습니다.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="주요 테이블 설정":::

데이터 세트를 Power BI 서비스에 게시하거나 가져오면 Excel 데이터 형식 갤러리에 주요 테이블이 표시됩니다.

- Excel은 데이터 형식 목록을 캐시합니다. 그러므로 새로 게시된 주요 테이블을 보려면 Excel을 다시 시작해야 합니다.
- 일부 데이터 세트는 미리 보기에서 지원되지 않으며, 이러한 데이터 세트에 정의된 주요 테이블은 Excel에 표시되지 않습니다. 자세한 내용은 고려 사항 및 제한 사항을 참조하세요.

## <a name="administrative-control"></a>관리 제어

Power BI 관리자는 조직에서 Excel 데이터 형식 갤러리의 주요 테이블을 사용할 수 있는 사용자를 제어할 수 있습니다. 자세한 내용은 관리 포털 문서의 [주요 테이블 설정](../admin/service-admin-portal.md#featured-tables-settings)을 참조하세요. 
 
### <a name="auditing"></a>감사

관리 감사 로그에는 다음과 같은 주요 테이블 이벤트가 표시됩니다.

- **AnalyzedByExternalApplication**: 관리자에게 어떤 사용자가 어떤 주요 테이블에 액세스하는지 보여 줍니다.
- **UpdateFeaturedTables**: 관리자에게 어떤 사용자가 주요 테이블을 게시 및 업데이트하는지 보여 줍니다.

감사 로그 이벤트의 전체 목록은 [Power BI에서 사용자 활동 추적](../admin/service-admin-auditing.md)을 참조하세요.

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항

초기 미리 보기의 제한 사항은 다음과 같습니다.

- 통합은 Excel 참가자 빌드에서 사용할 수 있습니다.
- Excel 데이터 형식 갤러리에는 Power BI Desktop 및 Power BI 서비스에 적절한 라이선스가 있는 사용자를 위한 주요 테이블이 포함되어 있습니다. Power BI 서비스에 대한 지원은 미리 보기를 릴리스할 때 사용하지 못할 수 있지만 추가될 예정입니다.
- 다음 기능을 사용하는 Power BI 데이터 세트의 주요 테이블은 Excel에 표시되지 않습니다. 

    - 행 수준 보안 데이터 세트
    - Microsoft Information Protection 설정 데이터 세트
    - DirectQuery 데이터 세트
    - 라이브 연결을 사용하는 데이터 세트

- Excel에서는 주요 테이블의 열 및 계산 열의 데이터만 표시합니다. 다음은 초기 미리 보기에서 제공하지 않습니다.

    - 추천 테이블에 정의된 측정값
    - 관련 테이블에 정의된 측정값 및 관계에서 계산된 암시적 측정값

- Excel에서는 새 Power BI 작업 영역에 저장된 주요 테이블만 표시합니다. 클래식 작업 영역 또는 내 작업 영역에 저장된 주요 테이블은 Excel에서 데이터 형식으로 표시되지 않습니다. Power BI에서 [클래식 작업 영역을 새 작업 영역으로 업그레이드](service-upgrade-workspaces.md)할 수 있습니다.

Excel의 데이터 형식 환경은 조회 함수와 유사합니다. Excel 시트에서 제공하는 셀 값을 사용하여 Power BI 주요 테이블에서 일치하는 행을 검색합니다. 검색 환경에는 다음과 같은 동작이 있습니다.

- **조직 데이터** 단추를 사용하여 검색할 때 Excel에서는 인증된 데이터 세트의 주요 테이블만 검색합니다.
- 행 일치는 주요 테이블의 텍스트 열을 기반으로 합니다. Power BI Q&A와 동일한 인덱싱을 사용하며 영어 검색에 최적화되어 있습니다. 다른 언어로 검색하면 정확하게 일치되지 않을 수 있습니다. 숫자 열은 일치에 고려하지 않습니다.
- 일치는 개별 검색어에 대한 정확한 일치 및 접두사 일치를 기반으로 합니다. 셀의 값은 공백 또는 탭 등의 기타 공백 문자를 기준으로 분할됩니다. 그러면 각 단어가 검색어로 간주됩니다. 정확한 일치 및 접두사 일치를 위해 행의 텍스트 필드 값을 각 검색어와 비교합니다. 행의 텍스트 필드가 검색어로 시작하는 경우 접두사 일치가 반환됩니다. 예를 들어 셀에 "Orange County"가 포함된 경우 "Orange" 및 "County"는 별개의 검색어입니다. 

    - 값이 "Orange" 또는 "County"와 정확히 일치하는 텍스트 열이 있는 행이 반환됩니다. 
    - 값이 "Orange" 또는 "County"로 시작하는 텍스트 열이 있는 행이 반환됩니다. 
    - 중요한 점은 "Orange" 또는 "County"를 포함하지만 이러한 단어로 시작하지 않는 행은 반환되지 않는다는 것입니다.

- Power BI는 각 셀에 대해 최대 100개의 행 제안을 반환합니다.
- 주요 테이블 설정 또는 업데이트는 XMLA 엔드포인트에서 지원되지 않습니다.
- 데이터 모델이 있는 Excel 파일을 사용하여 주요 테이블을 게시할 수 있습니다. Power BI Desktop에 데이터를 로드한 다음 주요 테이블을 게시합니다.
- 테이블 이름, 행 레이블 또는 키 열을 변경하면 주요 테이블이 테이블의 행에 연결된 셀이 있는 Excel 사용자에게 영향을 줄 수 있습니다. 
- Excel은 Power BI 데이터 세트에서 데이터를 검색한 시간을 표시합니다. 이 데이터가 반드시 Power BI에서 데이터를 새로 고친 시간 또는 데이터 세트에서 가장 최근인 데이터 요소의 시간은 아닙니다. 예를 들어 Power BI의 데이터 세트가 일주일 전에 새로 고쳐졌지만 새로 고침이 발생했을 때 기본 원본 데이터는 일주일이 지난 상태일 수 있습니다. 실제 데이터는 2주가 지난 것이지만 Excel은 데이터를 Excel로 가져온 날짜/시간에 데이터가 검색된 것으로 표시합니다.

## <a name="next-steps"></a>다음 단계

- 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)

