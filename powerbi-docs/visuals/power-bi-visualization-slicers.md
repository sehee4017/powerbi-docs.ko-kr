---
title: Power BI의 슬라이서
description: Power BI 슬라이서는 디자인하는 보고서의 다른 시각화에 표시되는 데이터 세트 부분을 좁히는 대체 필터링 방법입니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 07/07/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: d3e0c75a50fb103414a874c4455de775bc20e1a9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387577"
---
# <a name="slicers-in-power-bi"></a>Power BI의 슬라이서

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

보고서를 보는 사람이 전체 판매액 메트릭을 확인하고 개별 구역 관리자 및 다른 시간 프레임에 대한 성과를 강조 표시할 수 있도록 하려 합니다. 별도의 보고서나 비교 차트를 만들 수 있습니다. 필터 창에 필터를 추가할 수 있습니다. 또는 ‘슬라이서’를 사용할 수 있습니다. 슬라이서는 필터링의 다른 방법입니다. 슬라이서는 다른 보고서 시각화에 표시된 데이터 세트의 부분을 좁힙니다. 

![작업 중인 슬라이서의 애니메이션입니다.](media/power-bi-visualization-slicers/slicer2.gif)

이 문서에서는 무료 [소매점 분석 샘플](../create-reports/sample-retail-analysis.md)을 사용하여 기본 슬라이서를 만들고 서식을 지정하는 과정을 안내합니다. 또한 슬라이서의 영향을 받는 시각적 개체를 제어하고, 다른 페이지의 슬라이서와 동기화하고, 슬라이서를 필터링 및 서식 지정하는 방법을 설명합니다.

특정 유형의 슬라이서를 만드는 방법을 설명하는 다른 문서는 다음과 같습니다.

- [숫자 범위 슬라이서](../create-reports/desktop-slicer-numeric-range.md)
- [상대 날짜 슬라이서](desktop-slicer-filter-date-range.md)
- [상대 시간 슬라이서](../create-reports/slicer-filter-relative-time.md)
- [크기 조정 가능한 반응형 슬라이서](../create-reports/power-bi-slicer-filter-responsive.md)
- [계층 구조 슬라이서](../create-reports/power-bi-slicer-hierarchy-multiple-fields.md)(여러 필드 포함)

## <a name="when-to-use-a-slicer"></a>슬라이서를 사용하는 경우
다음과 같은 경우 슬라이서를 사용하는 것이 좋습니다.

* 보고서 캔버스에서 자주 사용되거나 중요한 필터를 표시하여 더 쉽게 액세스할 수 있게 하려는 경우
* 드롭다운 목록을 열지 않고도 현재 필터링된 상태를 더 쉽게 보려는 경우 
* 데이터 테이블에서 불필요하고 숨겨진 열 필터링.
* 중요한 시각적 개체 옆에 슬라이서를 배치하여 보다 집중화된 보고서 만들기.

Power BI 슬라이서는 다음을 지원하지 않습니다.

- 입력 필드
- 드릴다운

## <a name="create-a-slicer"></a>슬라이서 만들기

이 슬라이서는 구역 관리자로 데이터를 필터링합니다. 이 절차를 수행하려면 [소매점 분석 샘플 PBIX 파일](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)을 다운로드합니다.

1. Power BI Desktop을 열고 메뉴 모음에서 **파일** > **열기** 를 선택합니다.
   
1. **소매점 분석 샘플 PBIX.pbix** 파일을 찾은 다음, **열기** 를 선택합니다.

1. 왼쪽 창에서 **보고서** 아이콘 ![보고서 아이콘의 스크린샷](media/power-bi-visualization-kpi/power-bi-report-view.png)을 선택하여 보고서 뷰에서 파일을 엽니다.

1. **개요** 페이지에서, 보고서 캔버스에서 아무것도 선택하지 않은 상태로 시각화 창의 **슬라이서** 아이콘 ![슬라이서 아이콘의 스크린샷](media/power-bi-visualization-slicers/slicer-icon.png)을 선택하여 새 슬라이서를 만듭니다. 

1. 새 슬라이서를 선택한 상태로 **필드** 창에서 **구역** > **DM** 을 선택하여 슬라이서를 채웁니다. 

    이제 새 슬라이서가 구역 관리자 이름 목록과 해당 선택 상자로 채워집니다.
    
    ![구역 관리자 이름으로 채워진 슬라이서의 스크린샷](media/power-bi-visualization-slicers/power-bi-new-slicer.png)
    
1. 캔버스에서 요소의 크기를 조정하고 끌어서 슬라이서에 사용할 공간을 만듭니다. 슬라이서 크기를 너무 작게 조정하면 해당 항목이 잘립니다. 

1. 슬라이서에서 이름을 선택하고 페이지의 다른 시각화 요소에 미치는 영향을 확인합니다. 이름을 다시 선택하여 선택을 취소하고 **Ctrl** 키를 누른 채로 둘 이상의 이름을 선택합니다. 모든 이름을 선택하면 아무것도 선택하지 않은 것과 동일한 효과가 있습니다. 

1. 또는 **시각화** 창에서 **서식**(페인트 롤러 아이콘)을 선택하여 슬라이서의 서식을 지정합니다. 

   너무 많은 옵션이 있어서 여기에서 모두 설명할 수는 없습니다. 직접 실험해 보고 가장 적합한 슬라이서를 만드세요. 다음 이미지에서 첫 번째 슬라이서는 항목에 대해 색이 지정된 배경과 가로 방향을 사용합니다. 두 번째 슬라이서는 세로 방향과 색이 지정된 텍스트를 사용하여 보다 표준적인 모양을 제공합니다.

   ![서식이 지정된 슬라이서의 스크린샷](media/power-bi-visualization-slicers/power-bi-filter-examples.png)

   >[!TIP]
   >슬라이서 목록 항목은 기본적으로 오름차순으로 정렬됩니다. 정렬 순서를 내림차순으로 바꾸려면 슬라이서의 오른쪽 위에 있는 줄임표( **...** )를 선택하고 **내림차순 정렬** 을 선택합니다.

## <a name="control-which-page-visuals-are-affected-by-slicers"></a>슬라이서의 영향을 받는 페이지 시각적 개체 제어
기본적으로 보고서 페이지의 슬라이서는 서로를 포함하여 해당 페이지의 다른 모든 시각화에 영향을 줍니다. 방금 만든 목록 및 날짜 슬라이더에서 값을 선택할 때 다른 시각화에 미치는 영향을 확인하세요. 필터링된 데이터는 두 슬라이서에서 선택한 값의 교차 영역입니다. 

시각적 개체 상호 작용을 사용하여 일부 페이지 시각화가 다른 시각화의 영향을 받지 않도록 제외할 수 있습니다. **개요** 페이지의 **회계 월 및 구역 관리자별 총 판매액 차이** 차트에는 항상 표시하려고 하는 월별 지역 관리자에 대한 전체 비교 데이터가 표시됩니다. 시각적 개체 상호 작용을 사용하여 슬라이서 선택 항목이 이 차트를 필터링하지 못하도록 합니다. 

1. 보고서의 **개요** 페이지로 이동한 후 이전에 만든 **DM** 슬라이서를 선택합니다.

1. Power BI Desktop 메뉴에서 **시각적 개체 도구** 아래의 **서식** 메뉴를 선택하고 **상호 작용 편집** 을 선택합니다.
   
   필터 컨트롤 ![필터 컨트롤의 스크린샷](media/power-bi-visualization-slicers/filter-controls.png)(각각 **필터** 및 **없음** 옵션이 있음)은 페이지의 모든 시각적 개체 위에 표시됩니다. 처음에는 모든 컨트롤에서 **필터** 옵션이 미리 선택되어 있습니다.
   
1. **회계 월 및 구역 관리자별 총 판매액 차이** 차트 위의 필터 컨트롤에서 **없음** 옵션을 선택하여 **DM** 슬라이서가 필터링하지 않도록 합니다. 

1. **OpenDate** 슬라이서를 선택한 다음, **회계 월 및 구역 관리자별 총 판매액 차이** 차트 위에 있는 **없음** 옵션을 선택하여 이 슬라이서가 필터링하지 않도록 합니다. 

   이제 슬라이서에서 이름과 날짜 범위를 선택할 때 **회계 월 및 구역 관리자별 총 판매액 차이** 차트가 변경되지 않습니다.

상호 작용 편집에 대한 자세한 내용은 [Power BI 보고서에서 시각적 개체가 조작되는 방식 변경](../create-reports/service-reports-visual-interactions.md)을 참조하세요.

## <a name="sync-and-use-slicers-on-other-pages"></a>다른 페이지에서 슬라이서 동기화 및 사용
슬라이서를 동기화하고 보고서의 일부 또는 모든 페이지에서 사용할 수 있습니다. 

현재 보고서에서 **구역 월별 판매액** 페이지에 **구역 관리자** 슬라이서가 있는데, 이 슬라이서를 **신규 매장** 페이지에도 포함하면 어떻게 될까요? **신규 매장** 페이지에 슬라이서가 있지만 **매장 이름** 정보만 제공합니다. **슬라이서 동기화** 창을 사용하여 **구역 관리자** 슬라이서를 이러한 페이지에 동기화할 수 있으므로 한 페이지에서 슬라이서를 선택하면 세 페이지 모두의 시각화에 영향을 줍니다.

1. Power BI Desktop **보기** 메뉴에서 **슬라이서 동기화** 를 선택합니다.

    ![슬라이서 동기화 선택의 스크린샷](media/power-bi-visualization-slicers/power-bi-slicer-view-sync.png)

    **슬라이서 동기화** 창은 **필터** 창과 **시각화** 창 사이에 표시됩니다.

    ![슬라이서 동기화 창의 스크린샷](media/power-bi-visualization-slicers/power-bi-slicer-sync-pane.png)

1. 보고서의 **구역 월별 판매액** 페이지에서 **구역 관리자** 슬라이서를 선택합니다. 

    **개요** 페이지에서 **구역 관리자**(**DM**) 슬라이서를 이미 만들었으므로 **슬라이서 동기화** 창이 다음과 같이 표시됩니다.
    
    ![구역 월별 매출액 슬라이서 동기화의 스크린샷](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
1. **슬라이서 동기화** 창의 **동기화** 열에서 **개요**, **구역 월별 판매액** 및 **신규 매장** 페이지를 선택합니다. 

    이렇게 선택하면 **구역 월별 판매액** 슬라이서가 이러한 세 페이지에서 동기화됩니다. 
    
1. **슬라이서 동기화** 창의 **표시** 열에서 **신규 매장** 페이지를 선택합니다. 

    이렇게 선택하면 **구역 월별 판매액** 슬라이서가 이러한 세 페이지에 표시됩니다. 이제 **슬라이서 동기화** 창이 다음과 같이 표시됩니다.

    ![슬라이서 동기화의 선택 페이지 스크린샷](media/power-bi-visualization-slicers/power-bi-sync-slicer-finished.png)

1. 슬라이서를 동기화하여 다른 페이지에 표시되도록 설정한 결과를 관찰합니다. **구역 월별 판매액** 페이지의 **구역 관리자** 슬라이서에 **개요** 페이지와 동일한 선택 항목이 표시됩니다. 이제 **신규 매장** 페이지에서 **구역 관리자** 슬라이서가 표시되고 이 선택 항목은 **매장 이름** 슬라이서에 표시되는 선택 항목에 영향을 줍니다. 
    
    >[!TIP]
    >슬라이서는 처음에는 원래 페이지와 같은 크기 및 위치로 동기화된 페이지에 표시되지만 다양한 페이지에서 동기화된 슬라이서를 개별적으로 이동하고, 크기를 조정하고, 서식을 지정할 수 있습니다. 

    >[!NOTE]
    >슬라이서를 페이지에 동기화하지만 해당 페이지에 표시되지 않도록 설정할 경우 다른 페이지에서 선택한 슬라이서에 따라 페이지의 데이터가 필터링됩니다.
 
## <a name="filtering-slicers"></a>슬라이서 필터링
슬라이서에 표시되는 값 목록을 줄이기 위해 슬라이서에 시각적 수준 필터를 적용할 수 있습니다. 예를 들어 목록 슬라이서에서 빈 값을 필터링하거나 범위 슬라이서에서 특정 날짜를 필터링할 수 있습니다. 이렇게 하면 섹션을 만들 때 ‘슬라이서에 표시된 값’에만 영향을 주며, ‘슬라이서가 다른 시각적 개체에 적용하는 필터’에 영향을 주지 않습니다.  예를 들어 범위 슬라이서에 필터를 적용하여 특정 날짜만 표시해보겠습니다. 슬라이서의 선택 항목은 해당 범위의 처음 날짜와 마지막 날짜만 표시하지만 다른 시각적 개체에서 다른 날짜를 볼 수 있습니다. 슬라이서에서 선택한 범위를 변경하면 다른 시각적 개체 업데이트가 표시됩니다. 슬라이서를 지우면 모든 날짜가 다시 표시됩니다.

시각적 개체 수준 필터에 대한 자세한 내용은 [필터 형식](../create-reports/power-bi-report-filter-types.md)을 참조하세요.

## <a name="format-slicers"></a>슬라이서 서식 지정
슬라이서 유형에 따라 다양한 서식 옵션을 사용할 수 있습니다. **가로** 방향, **반응형** 레이아웃 및 **항목** 색 지정을 사용하면 표준 목록 항목이 아닌 단추 또는 타일을 생성하고 슬라이서 항목 크기가 다양한 화면 크기 및 레이아웃에 맞게 조정되도록 설정할 수 있습니다.  

1. 페이지에서 **구역 관리자** 슬라이서가 선택되면 **시각화** 창에서 **서식** 아이콘 ![서식 아이콘의 스크린샷](media/power-bi-visualization-slicers/power-bi-paintroller.png)을 선택하여 서식 컨트롤을 표시합니다. 
    
    ![서식 선택의 스크린샷](media/power-bi-visualization-slicers/3-format.png)
    
1. 각 범주 옆에 있는 드롭다운 화살표를 선택하여 옵션을 표시하고 편집합니다. 

### <a name="general-options"></a>일반 옵션
1. **서식** 에서 **일반** 을 선택하고 **윤곽선 색** 아래에서 빨간색을 선택한 다음, **윤곽선 두께** 를 *2* 로 변경합니다. 

    이렇게 설정하면 머리글 및 항목 윤곽선과 밑줄의 색 및 두께가 변경됩니다.

1. **방향** 의 경우 **세로** 가 기본적으로 선택되어 있습니다. **가로** 를 선택하여 가로로 정렬된 타일이나 단추 및 스크롤 화살표(슬라이서에 맞지 않는 항목에 액세스)가 있는 슬라이서를 생성합니다.
    
    ![일반 선택의 스크린샷](media/power-bi-visualization-slicers/4-horizontal.png)
    
1. **반응형** 레이아웃을 **켜기** 로 설정하여 보기 화면 및 슬라이서 크기에 따라 슬라이서 항목의 크기와 정렬을 변경합니다. 

    목록 슬라이서의 경우 반응형 레이아웃을 사용하면 작은 화면에서 항목이 잘리지 않습니다. 이 레이아웃은 가로 방향으로만 사용할 수 있습니다. 범위 슬라이더 슬라이서의 경우 반응형 서식에 따라 슬라이더의 스타일이 변경되고 이 서식을 사용하면 더 유연하게 크기를 조정할 수 있습니다. 두 슬라이서 유형 모두 작은 크기의 필터 아이콘이 됩니다.
    
    ![반응형 레이아웃 설정의 스크린샷](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >반응형 레이아웃의 변경 내용은 사용자가 설정한 특정 제목 및 항목 서식을 재정의할 수 있습니다. 
    
1. **X 위치**, **Y 위치**, **너비** 및 **높이** 에서 슬라이서 위치와 크기를 숫자 정밀도로 설정하거나 캔버스에서 직접 슬라이서를 이동하고 크기를 조정합니다. 

    다양한 항목 크기와 정렬을 사용해 보고 반응형 서식이 이에 따라 어떻게 변경되는지 확인하세요. 이러한 옵션은 가로 방향을 선택하는 경우에만 사용할 수 있습니다. 

    ![가로 옵션의 스크린샷](media/power-bi-visualization-slicers/6-buttons.png)

가로 방향 및 반응형 레이아웃에 대한 자세한 내용은 [Power BI에서 크기를 조정할 수 있는 반응형 슬라이서 만들기](../create-reports/power-bi-slicer-filter-responsive.md)를 참조하세요.

### <a name="selection-controls-options-list-slicers-only"></a>선택 컨트롤 옵션(목록 슬라이서만 해당)
1. **선택 컨트롤** 에서 **“모두 선택” 옵션 표시** 를 **켜기** 로 설정하여 **모두 선택** 항목을 슬라이서에 추가합니다. 

    **“모두 선택” 옵션 표시** 는 기본적으로 **끄기** 로 설정되어 있습니다. 이 옵션을 사용하도록 설정한 경우 토글하면 모든 항목을 선택하거나 선택 취소합니다. 모든 항목이 선택된 경우 한 항목을 선택하면 선택이 취소되고 *is-not* 형식의 필터를 허용합니다.
    
    ![선택 컨트롤의 스크린샷](media/power-bi-visualization-slicers/7-select-all.png)
    
1. **단일 선택** 을 **끄기** 로 설정하면 **Ctrl** 키를 누른 상태로 유지하지 않고도 여러 항목을 선택할 수 있습니다. 

    **단일 선택** 은 기본적으로 **켜기** 로 설정되어 있습니다. 항목을 선택하면 해당 항목이 선택되고 **Ctrl** 를 누른 상태로 선택하면 여러 항목이 선택됩니다. 항목을 다시 선택하면 선택이 취소됩니다.

### <a name="title-options"></a>제목 옵션
**제목** 은 기본적으로 **켜기** 로 설정되어 있습니다. 이렇게 선택하면 슬라이서 맨 위에 데이터 필드 이름이 표시됩니다. 제목을 편집할 수도 있습니다. 이 기능은 계층 구조 슬라이서에 특히 유용합니다. 자세한 내용은 "계층 구조 슬라이서에 여러 필드 추가" 문서에서 [제목 변경](../create-reports/power-bi-slicer-hierarchy-multiple-fields.md#change-the-title)을 참조하세요.

- 이 문서에서는 다음과 같이 제목 텍스트의 서식을 지정합니다. 
   - **글꼴색**: 빨강
   - **텍스트 크기**: **14pt**
   - **맞춤**: **가운데**
   - **글꼴 제품군**: **Arial Black**


### <a name="items-options"></a>항목 옵션

항목 옵션은 목록 슬라이서에만 사용할 수 있습니다.

1. 이 문서에서는 다음과 같이 **항목** 옵션의 서식을 지정합니다.
    - **글꼴색**: 검정
    - **배경**: 연한 빨강
    - **텍스트 크기**: **10pt**
    - **글꼴 제품군**: **Arial**
 
1. **윤곽선** 에서 **프레임** 을 선택하여 **일반** 옵션에서 설정한 크기와 색으로 각 항목 둘레에 테두리를 그립니다. 
    
    ![프레임 윤곽선 옵션의 스크린샷](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- **일반** > **방향** > **가로** 를 선택하면 선택 취소된 항목은 선택된 텍스트와 배경색으로 표시되고, 선택된 항목은 시스템 기본값(일반적으로 흰색 텍스트의 검은색 배경)으로 표시됩니다.
    >- **일반** > **방향 > 세로** 가 선택되어 있으면 항목에는 항상 선택한 색이 표시되고 확인란은 선택하면 항상 검은색으로 표시됩니다. 

### <a name="datenumeric-inputs-and-slider-options"></a>날짜/숫자 입력 및 슬라이더 옵션

날짜/숫자 입력 및 슬라이더 옵션은 범위 슬라이더 슬라이서에만 사용할 수 있습니다.

- 목록 슬라이서의 경우 날짜/숫자 입력 옵션은 윤곽선이나 밑줄 옵션이 없다는 점을 제외하면 **항목** 옵션과 동일합니다.
- **슬라이더** 옵션을 사용하면 범위 슬라이더의 색을 설정하거나 슬라이더를 **끄기** 로 설정하여 숫자 입력만 남겨 둘 수 있습니다.

### <a name="other-formatting-options"></a>다른 서식 지정 옵션
다른 서식 옵션은 기본적으로 **끄기** 로 설정되어 있습니다. 이러한 옵션을 **켜기** 로 설정하여 제어합니다. 

- **배경**: 슬라이서에 배경색을 추가하고 투명도를 설정합니다.
- **가로 세로 비율 잠금**: 크기를 조정한 경우 슬라이서의 상대 높이와 너비를 유지합니다.
- **테두리**: 슬라이서 둘레에 테두리를 추가하고 색을 설정합니다. 이 슬라이서 테두리는 **일반** 설정과 별개이며 영향을 받지 않습니다.
- **그림자**: 슬라이더에 그림자 효과를 추가합니다.

## <a name="next-steps"></a>다음 단계
슬라이서에 대한 자세한 내용은 다음 문서를 참조하세요.

- [숫자 범위 슬라이서](../create-reports/desktop-slicer-numeric-range.md)
- [상대 날짜 슬라이서](desktop-slicer-filter-date-range.md)
- [상대 시간 슬라이서](../create-reports/slicer-filter-relative-time.md)
- [크기 조정 가능한 반응형 슬라이서](../create-reports/power-bi-slicer-filter-responsive.md)
- [계층 구조 슬라이서](../create-reports/power-bi-slicer-hierarchy-multiple-fields.md)(여러 필드 포함)
