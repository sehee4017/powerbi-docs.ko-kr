---
title: '자습서:  Power BI Desktop에서 Excel 통합 문서를 통해 깔끔한 보고서 작성'
description: 해당 자습서에서는 Excel 통합 문서를 통해 깔끔한 보고서를 빠르게 만드는 방법을 보여 줍니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 10/13/2020
LocalizationGroup: Data from files
ms.openlocfilehash: b984c0f6ebee6cdcc9982956701f3a112be74ab7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413199"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>자습서:  Power BI Desktop에서 Excel 통합 문서를 통해 깔끔한 보고서 작성

이 자습서에서는 20분 만에 깔끔한 보고서를 완성하는 단계를 처음부터 끝까지 설명합니다. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="완료된 Power BI 보고서의 스크린샷."::: 

최근 매출 및 이익 통계에 관한 보고서를 상사에게 제출해야 합니다. 보고서에는 다음 사항을 요약해야 합니다. 

- 가장 큰 이익을 낸 월과 연도 
- 가장 큰 성과를 낸 국가 
- 지속적으로 투자해야 할 제품 및 세그먼트 

샘플 재무 통합 문서를 사용하여 보고서를 즉시 작성할 수 있습니다. 최종 보고서의 모양은 다음과 같습니다. 이제 시작하겠습니다. 

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다.

> [!div class="checklist"]
> * 두 가지 방법으로 샘플 데이터 다운로드
> * 몇 가지 변환을 사용하여 데이터 준비
> * 제목, 세 개의 시각적 개체 및 슬라이서를 사용하여 보고서 작성
> * 동료와 공유할 수 있도록 Power BI 서비스에 보고서 게시

## <a name="prerequisites"></a>필수 조건

- 시작하기 전에 [Power BI Desktop을 다운로드](https://powerbi.microsoft.com/desktop/)해야 합니다.
- Power BI 서비스에 보고서를 게시하고 아직 가입하지 않은 경우 [평가판에 가입](https://app.powerbi.com/signupredirect?pbi_source=web)합니다.

## <a name="get-data"></a>데이터 가져오기 

두 가지 방법 중 하나를 사용하여 이 자습서에 대한 데이터를 가져올 수 있습니다.

### <a name="get-data-in-power-bi-desktop"></a>Power BI Desktop에서 데이터 가져오기

Power BI Desktop을 열 때 빈 캔버스에서 **샘플 데이터 세트 사용해 보기** 를 선택합니다.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-desktop-canvas-sample-dataset.png" alt-text="캔버스에서 샘플 데이터 세트 사용해 보기의 스크린샷."::: 

Power BI Desktop에서 이 자습서를 배치한 경우 계속하여 **데이터 로드** 를 선택합니다.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-two-ways-load-data.png" alt-text="샘플 데이터 > 데이터 로드를 사용하는 두 가지 방법의 스크린샷.":::

### <a name="download-the-sample"></a>샘플 다운로드

샘플 통합 문서를 직접 다운로드할 수도 있습니다. 

1. [재무 샘플 Excel 통합 문서](https://go.microsoft.com/fwlink/?LinkID=521962)를 다운로드합니다.
1. Power BI Desktop을 엽니다.
1. **홈** 리본의 **데이터** 섹션에서 **Excel** 을 선택합니다.
1. 샘플 통합 문서를 저장한 위치로 이동하고 **열기** 를 선택합니다.

## <a name="prepare-your-data"></a>데이터 준비 

**탐색기** 에서 데이터를 ‘변환’ 또는 ‘로드’하는 옵션을 사용할 수 있습니다.  탐색기는 올바른 범위의 데이터가 있는지 확인할 수 있도록 데이터의 미리 보기를 제공합니다. 숫자 데이터 형식은 기울임꼴로 표시됩니다. 변경해야 하는 경우 로드하기 전에 데이터를 변환합니다. 나중에 시각화를 더 쉽게 읽을 수 있도록 지금 데이터를 변환하려고 합니다. 각 변환을 수행하면 **적용된 단계** 의 **쿼리 설정** 아래 목록에 변환이 추가된 것을 확인할 수 있습니다. 

1. **Financials** 테이블을 선택하고 **데이터 변환** 을 선택합니다. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="재무 샘플 데이터가 포함된 Power BI 탐색기의 스크린샷."::: 

1. **Units Sold** 열을 선택합니다. **홈** 탭에서 **데이터 형식** 을 선택한 다음, **정수** 를 선택합니다. **현재 전환 바꾸기** 를 선택하여 열 형식을 변경합니다. 

    사용자가 가장 자주 수행하는 데이터 정리 단계는 데이터 형식 변경입니다. 이 경우 판매 단위는 10진수 형식입니다. 판매 단위의 0.2 또는 0.5를 포함하는 것은 적절하지 않습니다. 따라서 판매 단위를 정수로 변경하겠습니다. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="10진수를 정수로 변경하는 스크린샷."::: 

1. **Segment** 열을 선택합니다. **변환** 탭에서 **형식** 을 선택한 다음, **대문자** 를 선택합니다.

    나중에 차트에서 세그먼트를 더 쉽게 확인할 수 있도록 설정하려고 합니다. Segment 열에 서식을 지정하겠습니다. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="제목을 소문자에서 대문자로 변경하는 스크린샷.":::

1. 열 이름을 **Month Name** 에서 **Month** 로 줄이겠습니다. **Month Name** 열을 두 번 클릭하고 **Month** 로 바꾸면 됩니다.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="열 이름을 줄이는 스크린샷.":::

1. **Product** 열에서 드롭다운을 선택하고 **Montana** 옆에 있는 확인란의 선택을 취소합니다. 

     Montana 제품이 지난달에 중단되었다는 것을 알고 있으므로 보고서에서 해당 데이터를 필터링하여 혼동을 피하려고 합니다. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="Montana 값을 삭제하는 스크린샷.":::

1. **적용된 단계** 의 **쿼리 설정** 아래 목록에 변환이 추가된 것을 확인할 수 있습니다.

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="적용된 단계 목록의 스크린샷.":::

1. **홈** 으로 돌아가서 **닫기 및 적용** 을 선택합니다. 보고서를 작성할 데이터가 거의 준비되었습니다. 

    필드 목록에 시그마 기호가 표시됩니까? Power BI는 해당 필드가 숫자임을 검색했습니다. 또한 Power BI는 일정 기호가 있는 날짜 필드를 표시합니다.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="숫자 필드 및 날짜 필드가 있는 필드 목록의 스크린샷.":::

### <a name="extra-credit-write-a-measure-in-dax"></a>추가 혜택: DAX로 측정값 작성

*DAX* 수식 언어로 ‘측정값’을 작성하는 것은 매우 강력한 데이터 모델링 기능입니다. Power BI 설명서에서 DAX에 관해 자세히 알아볼 수 있습니다. 지금은 기본 측정값을 작성하고 두 테이블을 조인하겠습니다. 

1. 왼쪽에서 **데이터 보기** 를 선택합니다. 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="데이터 보기 아이콘의 스크린샷":::

1. **홈** 리본에서 **새 테이블** 을 선택합니다. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="새 테이블 아이콘의 스크린샷.":::

1. 이 측정값을 입력하여 2013년 1월 1일과 2014년 12월 31일 사이 모든 날짜의 Calendar 테이블을 생성합니다.  

    `Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))` 

2. 커밋할 확인 표시를 선택합니다.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="DAX 식의 스크린샷.":::

1. 이제 왼쪽에서 **모델 뷰** 를 선택합니다. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="모델 뷰 아이콘의 스크린샷.":::

1. Financials 테이블의 **Date** 필드를 Calendar 테이블의 **Date** 필드로 끌어 테이블을 조인하고 두 테이블 간에 ‘관계’를 만듭니다.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="날짜 필드 간 관계의 스크린샷.":::

## <a name="build-your-report"></a>보고서 작성 

데이터를 변환하고 로드했으므로 이제 보고서를 만들겠습니다. 오른쪽 필드 창에 사용자가 만든 데이터 모델의 필드가 표시됩니다. 

한 번에 하나의 시각적 개체를 작성하여 최종 보고서를 작성합니다. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="숫자별 모든 보고서 요소의 스크린샷.":::

### <a name="visual-1-add-a-title"></a>시각적 개체 1: 제목 추가 

1. **삽입** 리본에서 **텍스트 상자** 를 선택합니다. “Executive Summary – Finance Report”를 입력합니다. 
1. 입력한 텍스트를 선택합니다. 글꼴 크기를 20으로 설정하고 굵게를 설정합니다. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="제목 서식 지정의 스크린샷.":::

1. 시각화 창에서 **배경** 을 **끄기** 로 전환합니다. 
1. 상자 크기를 한 줄에 맞게 조정합니다. 

### <a name="visual-2-profit-by-date"></a>시각적 개체 2: 날짜별 수익 

이제 수익이 가장 높은 월 및 연도를 표시하는 꺾은선형 차트를 만듭니다. 

1. 필드 창에서 **Profit** 필드를 보고서 캔버스의 빈 영역으로 끌어서 놓습니다. 기본적으로 Power BI는 Profit 열을 포함하는 세로 막대형 차트를 표시합니다. 
1. **Date** 필드를 동일한 시각적 개체로 끌어서 놓습니다. Power BI는 세로 막대형 차트를 업데이트하여 2년 기준 수익을 표시합니다.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="수익 세로 막대형 차트의 스크린샷.":::

1. 시각화 창의 **필드** 섹션에서 **축** 값의 드롭다운을 선택합니다. **Date** 를 **Date Hierarchy** 에서 **Date** 로 변경합니다.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="날짜 계층 구조를 날짜로 변경하는 스크린샷.":::

    Power BI는 세로 막대형 차트를 업데이트하여 매월 수익을 표시합니다.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="월별 세로 막대형 차트의 스크린샷.":::

1. 시각화 창에서 시각화 유형을 **꺾은선형 차트** 로 변경합니다. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="열을 가로 막대형 차트로 변경하는 스크린샷.":::

    이제 2014년 12월의 수익이 가장 높았음을 쉽게 알 수 있습니다.

### <a name="visual-3-profit-by-country"></a>시각적 개체 3: 국가별 수익 

지도를 만들어 수익이 가장 높은 국가를 확인합니다.

1. 필드 창에서 **Country** 필드를 보고서 캔버스의 빈 영역으로 끌어서 놓아 지도를 만듭니다.
1. **Profit** 필드를 지도로 끌어서 놓습니다.

    Power BI가 각 위치의 상대 수익을 나타내는 거품이 포함된 맵 시각적 개체를 만듭니다. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="지도 차트 만들기의 스크린샷.":::

    유럽이 북아메리카보다 성과가 더 좋은 것 같습니다. 

### <a name="visual-4-sales-by-product-and-segment"></a>시각적 개체 4: 제품 및 세그먼트별 판매액 

가로 막대형 차트를 만들어 투자할 회사 및 세그먼트를 결정합니다.

1. 직접 만든 두 개의 차트를 캔버스의 위쪽 절반으로 끌어서 나란히 놓습니다. 캔버스 왼쪽에 공간을 남겨 둡니다. 
1. 보고서 캔버스의 아래쪽에서 빈 영역을 선택합니다. 

1. 필드 창에서 **Sales**, **Product**, **Segment** 필드를 선택합니다. 

    Power BI는 묶은 세로 막대형 차트를 자동으로 만듭니다. 

1. 차트를 끌어서 놓습니다. 그러면 차트가 위쪽 두 개의 차트 아래 공간에 맞는 넓이로 채워집니다.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="묶은 세로 막대형 차트의 스크린샷.":::

    회사는 계속해서 Paseo 제품에 투자하고 중소기업 및 정부 세그먼트를 대상으로 해야 하는 것 같습니다.  

### <a name="visual-5-year-slicer"></a>시각적 개체 5: 연도 슬라이서 

슬라이서는 보고서 페이지의 시각적 개체를 특정 선택 항목으로 필터링하는 데 유용한 도구입니다. 이 경우 각 월 및 연도의 성과로 범위를 좁히는 슬라이서를 만들 수 있습니다.  

1. 필드 창에서 **Date** 필드를 선택하고 캔버스 왼쪽의 빈 영역으로 끌어서 놓습니다. 
2. 시각화 창에서 **슬라이서** 를 선택합니다. 
3. 시각화 창의 필드 섹션에서 **필드** 의 드롭다운을 선택합니다. Year 및 Month만 남아 있도록 Quarter 및 Day를 제거합니다. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="날짜 계층 구조를 변경하는 스크린샷.":::

4. 각 연도를 확장하고 시각적 개체의 크기를 조정합니다. 그러면 모든 월이 표시됩니다.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="날짜 계층 구조 슬라이서의 스크린샷.":::

이제 관리자가 2013년 데이터를 확인하도록 요청하면 슬라이서를 사용하여 연도 간에 전환하거나 각 연도의 특정 월 간에 전환할 수 있습니다. 

### <a name="extra-credit-format-the-report"></a>추가 혜택: 보고서 형식 지정

보고서에서 몇 가지 간단한 서식을 지정하여 보고서를 세련되게 만들려면 몇 가지 간단한 단계를 수행합니다. 

**테마**

- **보기** 리본에서 테마를 **Executive** 로 변경합니다.  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="Executive 테마 선택의 스크린샷."::: 

**시각적 개체 꾸미기** 

시각화 창의 **서식** 탭에서 다음과 같이 변경합니다.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="시각화 창, 서식 탭의 스크린샷.":::

1. 시각적 개체 2를 선택합니다. **제목** 섹션에서 **제목 텍스트** 를 “Profit by Month and Year”로 변경하고 **텍스트 크기** 를 **16pt** 로 변경합니다. **그림자** 를 **켜기** 로 전환합니다. 

1. 시각적 개체 3을 선택합니다. **지도 스타일** 섹션에서 **테마** 를 **회색조** 로 변경합니다. **제목** 섹션에서 제목 **텍스트 크기** 를 **16pt** 로 변경합니다. **그림자** 를 **켜기** 로 전환합니다.

1. 시각적 개체 4를 선택합니다. **제목** 섹션에서 제목 **텍스트 크기** 를 **16pt** 로 변경합니다. **그림자** 를 **켜기** 로 전환합니다.

1. 시각적 개체 5를 선택합니다. **선택 컨트롤** 섹션에서 **“모두 선택” 옵션 표시** 를 **켜기** 로 전환합니다. **슬라이서 머리글** 섹션에서 **텍스트 크기** 를 **16pt** 로 늘립니다. 

**제목의 배경 셰이프 추가**

1. **삽입** 리본에서 **셰이프** > **사각형** 을 선택합니다. 사각형을 페이지 위쪽에 배치하고 페이지의 너비 및 제목의 높이에 맞게 늘입니다. 
1. **도형 서식** 창의 **선** 섹션에서 **투명도** 를 **100%** 로 변경합니다. 
1. **채우기** 섹션에서 **채우기 색** 을 **테마 색 5 #6B91C9**(파란색)로 변경합니다. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="테마 색 5의 스크린샷":::

1. **서식** 탭에서 **뒤로 보내기** > **맨 뒤로 보내기** 를 선택합니다. 
1. 시각적 개체 1, 제목에서 텍스트를 선택하고 글꼴 색을 **흰색** 으로 변경합니다. 

**시각적 개체 2 및 3의 배경 셰이프 추가**

1. **삽입** 리본에서 **셰이프** > **사각형** 을 선택하고 시각적 개체 2 및 3의 너비와 높이에 맞게 늘립니다. 
1. **도형 서식** 창의 **선** 섹션에서 **투명도** 를 **100%** 로 변경합니다. 
1. **서식** 탭에서 **뒤로 보내기** > **맨 뒤로 보내기** 를 선택합니다. 

### <a name="finished-report"></a>완성된 보고서

다음은 세련된 최종 보고서의 모양입니다.  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="서식이 지정된 최종 보고서의 스크린샷.":::

요약하면, 해당 보고서는 다음과 같은 관리자의 가장 중요한 질문에 답을 제공합니다. 

- 가장 큰 이익을 낸 월과 연도 

    2014년 12월 

- 회사가 확인한 가장 성공한 국가는 어디입니까? 

    유럽에서 특히 프랑스와 독일입니다. 

- 지속적으로 투자해야 할 제품 및 세그먼트 

    회사는 계속해서 Paseo 제품에 투자하고 중소기업 및 정부 세그먼트를 대상으로 해야 합니다. 

## <a name="save-your-report"></a>보고서 저장

- **파일** 메뉴에서 **저장** 을 선택합니다.

## <a name="publish-to-the-power-bi-service-to-share"></a>Power BI 서비스에 게시하여 공유 

관리자 및 동료와 보고서를 공유하려면 Power BI 서비스에 게시합니다. Power BI 계정이 있는 동료와 공유하면 동료는 보고서와 상호 작용할 수 있지만 변경 내용을 저장할 수는 없습니다. 

1. Power BI Desktop의 **홈** 리본에서 **게시** 를 선택합니다. 

    Power BI 서비스에 로그인해야 할 수 있습니다. 아직 계정이 없으면 [평가판에 가입](https://app.powerbi.com/signupredirect?pbi_source=web)할 수 있습니다.

1. Power BI 서비스에서 **내 작업 영역** 과 같은 대상을 선택한 다음, **선택** 을 선택합니다.
1. **Power BI에서 '파일 이름' 열기** 를 선택합니다.

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="Power BI 서비스에서 보고서를 여는 스크린샷.":::

    완성된 보고서가 브라우저에서 열립니다.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Power BI 서비스에서 완료된 Power BI 보고서의 스크린샷."::: 

1. 보고서 위쪽에서 **공유** 를 선택하여 보고서를 다른 사용자와 공유합니다.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="Power BI 서비스에서 보고서를 공유하는 스크린샷.":::

## <a name="next-steps"></a>다음 단계

- [자습서: Excel 및 OData 피드의 판매 데이터 분석](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용](https://community.powerbi.com/)하세요.
