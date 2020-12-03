---
title: Power BI의 폭포 차트
description: Power BI의 폭포 차트
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 12/5/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 1a651afd0aee0777f8f4c945f208eec8c46db047
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416672"
---
# <a name="waterfall-charts-in-power-bi"></a>Power BI의 폭포 차트

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

폭포 차트는 Power BI가 값을 더하거나 뺄 때의 누계를 보여 줍니다. 초기 값(예: 순수입)이 일련의 양수 및 음수 변경에 어떻게 영향을 받는지 이해하는 데 유용합니다.

세로형 막대는 색으로 구분되어 증가 및 감소를 빠르게 구분할 수 있습니다. 중간 값은 부동 세로 막대인 반면, 초기 및 최종 값 세로 막대는 [가로 축에서 시작](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "가로 축에서 시작")하는 경우가 많습니다. 이러한 스타일로 인해, 폭포 차트는 교량 차트라고도 합니다.

## <a name="when-to-use-a-waterfall-chart"></a>폭포 차트를 사용하는 경우

다음과 같은 경우 폭포 차트를 사용하는 것이 좋습니다.

* 시계열 또는 다른 범주에 걸쳐 측정값의 변화가 있는 경우

* 합계 값에 영향을 주는 주요 변경을 감사하는 경우

* 다양한 수익원과 총수익(또는 손실)을 표시하여 회사의 연간 수익을 그리려는 경우

* 1년 동안 회사의 시작 및 종료 인력을 나타내기 위해

* 매달 벌고 쓰는 금액이 얼마인지 그리고 계좌의 잔고가 얼마인지를 시각화하기 위해

## <a name="prerequisite"></a>필수 조건

이 자습서는 [소매점 분석 샘플 PBIX 파일](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)을 사용합니다.

1. 메뉴 모음의 왼쪽 위 섹션에서 **파일** > **열기** 를 선택합니다.
   
2. **소매점 분석 샘플 PBIX 파일** 을 찾습니다.

1. **소매점 분석 샘플 PBIX 파일** 을 보고서 보기 아이콘 ![보고서 보기 아이콘 스크린샷](media/power-bi-visualization-kpi/power-bi-report-view.png)으로 엽니다.

1. 새 페이지를 추가하기 위해 ![노란색 탭 스크린샷](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) 탭을 선택합니다.

> [!NOTE]
> Power BI 동료와 보고서를 공유하려면 개별 Power BI Pro 라이선스가 있거나 보고서가 Premium 용량에 저장되어 있어야 합니다.    

## <a name="create-a-waterfall-chart"></a>폭포 차트 만들기

월별 매출 편차(실제 매출과 예상 매출의 편차)를 표시하는 폭포 차트를 만들겠습니다.

### <a name="build-the-waterfall-chart"></a>폭포 차트 만들기

1. **필드** 창에서 **판매량** > **총판매액 차이** 를 선택합니다.

   ![선택된 판매량 > 총판매액 차이에 해당하는 시각적 개체의 스크린샷](media/power-bi-visualization-waterfall-charts/power-bi-bar.png)

1. 폭포 아이콘 ![폭포 아이콘의 스크린샷](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png)

    ![시각화 템플릿](media/power-bi-visualization-waterfall-charts/convert-waterfall.png)

1. **시간** > **FiscalMonth** 를 선택하여 **범주** 영역에 추가합니다.

    ![폭포](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-month.png)

### <a name="sort-the-waterfall-chart"></a>폭포 차트 정렬

1. Power BI에서 폭포 차트가 시간(월)순으로 정렬되도록 합니다. 차트의 오른쪽 위에서 **추가 옵션**(...)을 선택합니다.

    이 예에서는 **정렬 기준** 을 선택하고 **FiscalMonth** 를 선택합니다. 선택 항목 옆에 있는 노란색 표시기는 선택 옵션이 적용 중인 경우에 나타납니다.

    ![정렬 기준 > FiscalMonth 선택](media/power-bi-visualization-waterfall-charts/power-bi-sort-by-fiscalmonth.png)
    
    월을 시간순으로 표시하려면 **오름차순 정렬** 을 선택합니다. 이전 단계와 마찬가지로, **오름차순 정렬** 왼쪽 옆에 노란색 표시기가 있는지 확인합니다. 이는 선택한 옵션이 적용되고 있음을 나타냅니다.

    ![정렬 기준 > 오름차순 선택](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-ascending.png)

    

    FiscalMonth에 대해 1월부터 8월까지 차트가 정렬됩니다.  

### <a name="explore-the-waterfall-chart"></a>폭포 차트 탐색

조금 더 세부적으로 들어가 월간 편차의 가장 큰 요인을 살펴봅니다.

1.  **매장** > **지역** 을 선택하면 **분석** 버킷에 **지역** 이 추가됩니다.

    ![스크린샷은 지역을 분석 결과 영역에 추가하는 것을 보여 줍니다.](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Power BI는 **분석** 의 값을 사용하여 시각화에 데이터를 추가합니다. 각 회계 월에 대해 증가하거나 감소하는 상위 5개 요인을 추가합니다. 예를 들어, 2월에는 1개가 아닌, 6개의 데이터 요소가 있음을 의미합니다.  

    ![분석 버킷의 매장 표시](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-default.png)

    상위 2개 요인에만 관심이 있는 경우입니다.

1. **서식** 창에서 **분석 결과** 를 선택하고 **최대 분석 결과** 를 **2** 로 설정합니다.

    ![서식 > 분석 결과](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-two.png)

    간단히 살펴보면 오하이오 및 펜실베이니아 지역이 폭포 차트의 증감에 가장 큰 영향을 주는 지역인 것으로 보입니다.

    ![폭포 차트](media/power-bi-visualization-waterfall-charts/power-bi-axis-waterfall.png)

## <a name="next-steps"></a>다음 단계

* [Power BI 보고서에서 시각적 개체가 조작되는 방식 변경](../create-reports/service-reports-visual-interactions.md)

* [Power BI의 시각화 유형](power-bi-visualization-types-for-reports-and-q-and-a.md)

