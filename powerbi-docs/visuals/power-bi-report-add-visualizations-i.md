---
title: 1부, Power BI 보고서에 시각화 추가
description: 1부, Power BI 보고서에 시각화 추가
author: msftrien
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/06/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 3a2002c9f17428c84704d68f621cf18443252557
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93411892"
---
# <a name="add-visuals-to-a-power-bi-report-part-1"></a>Power BI 보고서에 시각적 개체 추가(1부)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

이 문서는 보고서에서 시각화를 만드는 방법에 대해 간단히 소개합니다. 이 문서는 Power BI 서비스 및 Power BI Desktop 모두에 적용됩니다. 고급 콘텐츠를 보려면 이 시리즈의 [2부를 참조](power-bi-report-add-visualizations-ii.md)하세요.

## <a name="prerequisites"></a>필수 조건

이 자습서는 [영업 및 마케팅 PBIX 파일](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix)을 사용합니다.

1. Power BI Desktop 메뉴 모음의 왼쪽 위 섹션에서 **파일** > **열기** 를 선택합니다.
   
2. **영업 및 마케팅 샘플 PBIX 파일** 의 복사본을 찾습니다.

1. 보고서 뷰 ![보고서 뷰 아이콘 스크린샷](media/power-bi-visualization-kpi/power-bi-report-view.png)에서 **영업 및 마케팅 샘플 PBIX 파일** 을 엽니다.

1. 새 페이지를 추가하기 위해 ![노란색 탭 스크린샷](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) 탭을 선택합니다.

> [!NOTE]
> Power BI 동료와 보고서를 공유하려면 개별 Power BI Pro 라이선스가 있거나 보고서가 Premium 용량에 저장되어 있어야 합니다. [보고서 공유](../collaborate-share/service-share-reports.md)를 참조하세요.

## <a name="add-visualizations-to-the-report"></a>시각화 요소를 보고서에 추가

1. **필드** 창에서 필드를 선택하여 시각화를 만듭니다.

    **Sales** > **TotalSales** 와 같은 숫자 필드에서 시작합니다. Power BI에서 단일 열이 포함된 열 차트를 만듭니다.

    ![단일 열이 포함된 열 차트의 스크린샷](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    또는 **Name** 또는 **Product** 와 같은 범주 필드부터 시작합니다. Power BI에서 테이블이 생성되고 이 필드가 **값** 영역에 추가됩니다.

    ![네 개의 범주가 있는 테이블 스크린샷](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    또는 **Geo** > **City** 와 같은 지리 필드부터 시작합니다. Power BI 및 Bing Maps는 지도 시각화를 만듭니다.

    ![지도 시각화의 스크린샷](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>시각화 유형 변경

 시각화를 만든 다음 해당 유형을 변경합니다. 
 
 1. **Product** > **Category** 를 선택한 후 **Product** > **Count of Product** 를 선택하여 둘 다 **값** 영역에 추가합니다.

    ![Values 웰이 호출되는 필드 창의 스크린샷](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. **누적 세로 막대형 차트** 아이콘을 선택하여 세로 막대형 차트에 대한 시각화를 변경합니다.

   ![누적 세로 막대형 차트 아이콘이 호출된 시각화 창의 스크린샷](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. 시각적 개체의 정렬 방법을 변경하려면 **추가 작업** (...)을 선택합니다.  정렬 옵션을 사용하여 정렬 방향(오름차순 또는 내림차순)을 변경하고 정렬에 사용되는 열( **정렬 기준** )을 변경합니다.

   ![추가 작업 드롭다운 스크린샷](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>다음 단계

 이제

* [2부: Power BI 보고서에 시각화 추가](power-bi-report-add-visualizations-ii.md)로 계속 진행합니다.

* 보고서에서 [시각화와 상호 작용](../consumer/end-user-reading-view.md)합니다.
