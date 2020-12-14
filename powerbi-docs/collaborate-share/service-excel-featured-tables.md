---
title: Excel에서 Power BI 추천 테이블에 액세스
description: Excel의 조직 데이터 형식 갤러리에서 Power BI 데이터 세트의 추천 테이블에서 데이터를 찾을 수 있습니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: b5f84f67231393dfed78bd9f90142fbd1b4f6c91
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96907060"
---
# <a name="access-power-bi-featured-tables-in-excel-organization-data-types"></a>Excel 조직 데이터 형식에서 Power BI 추천 테이블 액세스

‘주요 테이블’은 Excel의 데이터를 Power BI의 데이터에 연결하는 한 가지 방법입니다. 주요 테이블을 사용하면 더욱 쉽게 엔터프라이즈 데이터를 Excel 시트에 추가할 수 있습니다. Excel의 데이터 형식 갤러리에 있는 Power BI 데이터 세트의 추천 테이블에서 데이터를 찾을 수 있습니다. 이 문서에서는 등록 방법을 설명합니다.

Power BI에서 데이터 세트를 만드십니까? [Power BI Desktop에서 주요 테이블 설정](service-create-excel-featured-tables.md) 방법을 알아보세요.

> [!NOTE]
> Excel에서 Power BI로 액세스할 수 있는 Power BI 데이터 세트의 데이터를 분석할 수도 있습니다. 자세한 내용은 “Power BI용 Excel 분석” 문서의 [Excel에서 Power BI 데이터 세트에 액세스하는 다른 방법](service-analyze-in-excel.md#other-ways-to-access-power-bi-datasets-from-excel)을 참조하세요.
> 

## <a name="the-excel-data-types-gallery"></a>Excel 데이터 형식 갤러리
Power BI 데이터 세트의 추천 테이블은 **데이터** 리본에 있는 Excel **데이터 형식** 갤러리에 ‘데이터 형식’으로 표시됩니다.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Excel 데이터 리본에 있는 데이터 형식 갤러리의 스크린샷.":::

확장된 갤러리에는 **주식** 및 **지리** 와 같은 일반 데이터 형식과 Power BI 데이터 세트의 추천 테이블인 사용 가능한 상위 10개 **조직** 데이터 형식이 표시됩니다.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Excel 데이터 형식 갤러리의 스크린샷.":::

## <a name="search-for-power-bi-data-in-the-data-types-gallery"></a>데이터 형식 갤러리에서 Power BI 데이터 검색

Power BI 추천 테이블에서 데이터를 검색하려면 추천 테이블의 값과 일치하는 값을 포함하는 Excel 시트의 셀 또는 범위를 선택합니다. 데이터 형식 갤러리 옆에 있는 **자세히** 화살표를 선택합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-more.png" alt-text="Excel 데이터 형식 갤러리의 자세히 아이콘 스크린샷.":::

찾고 있는 테이블이 보이면 선택합니다. 보이지 않으면 **조직의 더 많은 항목** 을 선택합니다. Excel은 액세스할 수 있는 모든 추천 테이블을 창에 표시합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-more-your-organization.png" alt-text="조직에서 선택(미리 보기) 스크린샷.":::
 
Excel은 액세스할 수 있는 모든 추천 테이블을 표시합니다. **데이터 선택기** 창에서 **필터** 상자에 입력하여 옵션 범위를 좁힙니다. 사용할 테이블을 선택합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-store.png" alt-text="Excel 조직 데이터, 공급자 데이터 형식 테이블의 스크린샷.":::
 
Excel이 신뢰도가 높은 일치하는 행을 찾으면 셀이 해당 행에 즉시 연결됩니다. 연결된 항목 아이콘은 셀이 Power BI의 행에 연결되어 있음을 나타냅니다.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="연결된 항목 아이콘의 스크린샷.":::

셀에 잠재적으로 일치하는 행이 두 개 이상 있는 경우 셀에 물음표 아이콘이 표시되고 **데이터 선택기** 창이 열립니다. 다음 예제에서는 B3:B9의 범위를 선택하고 Power BI 주요 테이블 **Store** 를 선택합니다. 셀 B9 “508 - Pasadena Lindseys”를 제외한 모든 행에 일치 항목이 있습니다. **데이터 선택기** 는 두 개의 일치 가능한 항목을 보여 줍니다. 이는 두 개의 테이블에 있는 값과 동일합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-question-mark-featured-table.png" alt-text="Excel 데이터 선택기 창의 스크린샷.":::
 
조직 데이터 옵션은 여러 추천 테이블의 행을 반환할 수 있습니다. Excel은 잠재적으로 일치하는 행을 원래 데이터 형식에 따라 그룹화합니다. Excel은 가장 근사하게 일치하는 행을 기준으로 데이터 형식을 정렬합니다. 갈매기형 화살표를 사용하여 데이터 형식을 일치하는 행으로 축소/확장합니다.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="여러 가능성이 있는 Excel 데이터 선택기 창의 스크린샷.":::
 
올바른 행을 선택할 수 있도록 각 제안에서 **데이터 선택기** 창의 행 이름을 선택하여 행 세부 정보를 확인합니다. 행을 찾았으면 **선택** 을 눌러 Excel의 셀에 행을 연결합니다. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="데이터 선택기 세부 정보의 스크린샷.":::

## <a name="explore-related-data"></a>관련 데이터 탐색

Excel 시트에 있는 값과 Power BI 주요 테이블에 있는 데이터 사이에 연결을 만들었으니 이제 데이터를 탐색할 수 있습니다. 데이터를 사용하여 Excel 보고를 향상해 보세요.

### <a name="view-related-data-in-a-card"></a>카드에서 관련 데이터 보기 
 
셀의 **카드** 아이콘을 선택하면 추천 테이블의 모든 필드 및 계산 필드의 데이터가 포함된 카드가 표시됩니다. 카드의 제목에는 주요 테이블의 행 레이블 필드 값이 표시됩니다.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="연결된 항목 세부 정보의 스크린샷.":::

### <a name="insert-related-data-from-power-bi"></a>Power BI에서 관련 데이터 삽입 

**데이터 삽입** 아이콘을 선택한 다음, 필드 목록에서 필드 이름을 선택하여 해당 값을 표에 추가합니다.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="필드 이름 선택의 스크린샷.":::

필드 값이 인접한 셀에 배치됩니다. 셀 수식은 연결된 셀 및 필드 이름을 참조하므로 Excel 함수에서 데이터를 사용할 수 있습니다.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel 셀 수식의 스크린샷.":::

### <a name="use-cell-formulas"></a>셀 수식 사용

Excel 테이블에서는 연결된 테이블 열을 참조한 다음 `.`(마침표) 참조를 사용하여 데이터 필드를 추가할 수 있습니다.

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Excel 기간 참조의 스크린샷.":::

마찬가지로 셀에서는 셀을 참조하고 `.`(마침표) 참조를 사용하여 필드를 검색할 수 있습니다.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="셀 기간 참조의 스크린샷.":::

### <a name="show-a-card-change-or-convert-to-text"></a>카드 표시, 변경 또는 텍스트로 변환

연결된 셀에는 오른쪽 클릭 메뉴 옵션이 추가되었습니다. 셀을 마우스 오른쪽 단추로 클릭합니다. 일반 옵션과 함께 다음도 표시됩니다.

- **데이터 형식 카드 표시**.
- **데이터 형식** > **텍스트로 변환**.
- **데이터 형식** > **변경**.
- **새로 고침**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="마우스 오른쪽 단추 클릭, 텍스트로 변환의 스크린샷.":::
 
**텍스트로 변환** 은 Power BI 주요 테이블의 행에 대한 링크를 제거합니다. 중요한 점은 셀의 텍스트가 연결된 셀의 행 레이블 값이라는 것입니다. 셀을 의도하지 않는 행에 연결한 경우 Excel에서 **실행 취소** 를 선택하여 초기 셀 값을 복원합니다.
 
## <a name="data-caching-and-refresh"></a>데이터 캐싱 및 새로 고침

Excel이 셀을 Power BI 주요 테이블의 행에 연결할 때 Excel 파일의 모든 필드 값을 검색하고 저장합니다. 이 파일을 공유하는 모든 사용자는 Power BI에서 데이터를 요청하지 않고 모든 필드를 참조할 수 있습니다.  

**데이터** 리본의 **모두 새로 고침** 단추를 사용하여 연결된 셀의 데이터를 새로 고칩니다. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="모두 새로 고침의 스크린샷.":::
 
개별 셀을 새로 고칠 수도 있습니다. 셀을 마우스 오른쪽 단추로 클릭하고 **데이터 형식** > **새로 고침** 을 선택합니다.

## <a name="licensing"></a>라이선싱

Excel 데이터 형식 갤러리와 Power BI 추천 테이블에 대한 연결된 환경은 Power BI Pro 서비스 플랜을 이용하는 Excel 구독자만 사용할 수 있습니다. 

## <a name="security"></a>보안

Power BI에서 사용 권한이 있는 데이터 세트의 주요 테이블만 볼 수 있습니다. 데이터를 새로 고칠 때 행을 검색하기 위해 Power BI의 데이터 세트에 액세스할 수 있는 권한이 있어야 합니다. Power BI에서 [데이터 세트에 대한 빌드 또는 쓰기 권한](../connect-data/service-datasets-build-permissions.md)이 필요합니다.
 
Excel은 전체 행에 대해 반환되는 데이터를 캐시합니다. Excel 파일을 공유하는 모든 사용자는 모든 연결된 셀의 모든 필드에 대한 데이터를 볼 수 있습니다.

## <a name="administrative-control"></a>관리 제어

Power BI 관리자는 조직에서 Excel 데이터 형식 갤러리의 주요 테이블을 사용할 수 있는 사용자를 제어할 수 있습니다. 자세한 내용은 관리 포털 문서의 [주요 테이블에 대한 연결 허용](../admin/service-admin-portal.md#allow-connections-to-featured-tables)을 참조하세요. 
 
### <a name="auditing"></a>감사

관리 감사 로그에는 다음과 같은 주요 테이블 이벤트가 표시됩니다.

- **AnalyzedByExternalApplication**: 관리자에게 어떤 사용자가 어떤 주요 테이블에 액세스하는지 보여 줍니다.
- **UpdateFeaturedTables**: 관리자에게 어떤 사용자가 주요 테이블을 게시 및 업데이트하는지 보여 줍니다.

감사 로그 이벤트의 전체 목록은 [Power BI에서 사용자 활동 추적](../admin/service-admin-auditing.md)을 참조하세요.

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
- 데이터 모델이 있는 Excel 파일을 사용하여 주요 테이블을 게시할 수 있습니다. Power BI Desktop에 데이터를 로드한 다음 주요 테이블을 게시합니다.
- 테이블 이름, 행 레이블 또는 키 열을 변경하면 주요 테이블이 테이블의 행에 연결된 셀이 있는 Excel 사용자에게 영향을 줄 수 있습니다. 
- Excel은 Power BI 데이터 세트에서 데이터를 검색한 시간을 표시합니다. 이번에는 데이터가 반드시 Power BI에서 데이터를 새로 고친 시간 또는 데이터 세트에서 가장 최근인 데이터 요소의 시간은 아닙니다. 예를 들어 Power BI의 데이터 세트가 일주일 전에 새로 고쳐졌지만 새로 고침이 발생했을 때 기본 원본 데이터는 일주일이 지난 상태일 수 있습니다. 실제 데이터는 2주가 지난 것이지만 Excel은 데이터를 Excel로 가져온 날짜/시간에 데이터가 검색된 것으로 표시합니다. 

## <a name="next-steps"></a>다음 단계

- [Power BI Desktop에서 추천 테이블 설정](service-create-excel-featured-tables.md)
- Excel 설명서에서 [Power BI의 Excel 데이터 형식](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)을 사용하는 방법에 대해 알아보세요.
- 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)

