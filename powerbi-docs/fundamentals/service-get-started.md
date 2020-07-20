---
title: '자습서:  Power BI 서비스에서 만들기 시작'
description: Power BI 온라인 서비스 시작(app.powerbi.com)
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.date: 07/08/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 7b9f69607d2fef823ba67d5af035e1e2064a9a72
ms.sourcegitcommit: c18130ea61e67ba111be870ddb971c6413a4b632
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86162393"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>자습서:  Power BI 서비스에서 만들기 시작
이 자습서는 *Power BI 서비스* 기능 중 일부를 소개합니다. 자습서를 통해 데이터에 연결하고, 보고서 및 대시보드를 만들고, 데이터에 대해 질문할 수 있습니다. Power BI 서비스에서 훨씬 더 많은 작업을 수행할 수 있습니다. 이 자습서는 의욕을 높여줍니다. Power BI 서비스를 다른 Power BI 제품에 적용하는 방법을 이해하려면 [Power BI란?](power-bi-overview.md)을 읽어 보시기 바랍니다.

보고서 작성자가 아니라 보고서 ‘읽기 권한자’인 경우 [Power BI 서비스 살펴보기](../consumer/end-user-experience.md)를 확인하여 시작하면 좋습니다.

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="재무 샘플 대시보드의 스크린샷":::

이 자습서에서 수행하는 단계는 다음과 같습니다.

> [!div class="checklist"]
> * Power BI 온라인 계정에 로그인하거나, 계정이 아직 없는 경우 등록합니다.
> * Power BI 서비스를 엽니다.
> * 일부 데이터를 가져와 보고서 뷰에서 엽니다.
> * 해당 데이터를 사용하여 시각화를 만들고 보고서로 저장합니다.
> * 보고서에서 타일을 고정하여 대시보드를 만듭니다.
> * 질문 및 답변 자연어 도구를 사용하여 대시보드에 다른 시각화를 추가합니다.
> * 대시보드의 타일 크기를 조정하고, 타일을 다시 정렬하고, 세부 정보를 편집합니다.
> * 데이터 세트, 보고서 및 대시보드를 삭제하여 리소스를 정리합니다.

## <a name="sign-up-for-the-power-bi-service"></a>Power BI 서비스에 등록
Power BI에서 콘텐츠를 만들려면 Power BI Pro 라이선스가 필요합니다. Power BI 계정이 없는 경우, 시작하기 전에 [Power BI Pro 평가판에 등록](https://app.powerbi.com/signupredirect?pbi_source=web)합니다.

## <a name="step-1-get-data"></a>1단계: 데이터 가져오기

Power BI 보고서를 만들고자 하는 경우 Power BI Desktop에서 시작하는 경우가 많습니다. Power BI Desktop은 더 많은 기능을 제공합니다. 보고서 디자인을 시작하기 전에 데이터를 변환하고 셰이핑하고 모델링할 수 있습니다. 하지만 이번에는 Power BI 서비스에서 처음부터 보고서를 만들기 시작합니다.

이 자습서에서는 간단한 Microsoft Excel 파일에서 데이터를 가져옵니다. 함께 진행해볼까요? [Financial Sample 파일을 다운로드합니다](https://go.microsoft.com/fwlink/?LinkID=521962).

1. 시작하려면 브라우저에서 Power BI 서비스(app.powerbi.com)를 엽니다. 

    계정이 없는 경우 [Power BI Pro 무료 평가판에 등록](https://app.powerbi.com/signupredirect?pbi_source=web)할 수 있습니다.

1. 탐색 창에서 **내 작업 영역**을 선택합니다.

1. **내 작업 영역**에서 **새로 만들기** > **파일 업로드**를 선택합니다.

    **데이터 가져오기** 페이지가 열립니다.   

3. **새 콘텐츠 만들기** 섹션에서 **파일**이 선택되어 있는지 확인한 후 Excel 파일을 저장한 위치를 선택합니다.
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="새 콘텐츠 만들기 > 파일의 스크린샷":::

5. 컴퓨터에서 파일을 찾은 다음 **열기**를 선택합니다.

5. 이 자습서에 대해 **가져오기**를 선택하여 Excel 파일을 데이터 세트로 추가합니다. 그런 다음, 보고서와 대시보드를 만드는 데 사용할 수 있습니다. **업로드**를 선택하면 전체 Excel 통합 문서가 Power BI에 업로드되고, Excel Online에서 열어 편집할 수 있습니다.
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="가져오기 선택의 스크린샷":::
6. 데이터 세트가 준비되면 재무 샘플 데이터 세트 옆에 있는 **추가 옵션(...)** 을 선택한 다음 **보고서 만들기**를 선택합니다.
1. 보고서 편집기를 엽니다. 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="모든 콘텐츠 > 보고서 만들기의 스크린샷":::

    보고서 캔버스가 비어 있습니다. 오른쪽에는 **필터**, **시각화** 및 **필드** 창이 있습니다.

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="빈 보고서 캔버스의 스크린샷":::

    > [!TIP]
    > 왼쪽 위 모서리에 있는 전역 탐색 단추를 선택하여 탐색 창을 축소합니다. 이렇게 하면 캔버스의 공간이 많아집니다.
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="전역 탐색 단추":::
    >

7. 현재 편집용 보기입니다. 메뉴 모음에서 **읽기용 보기** 옵션을 볼 수 있습니다. 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="읽기용 보기 옵션의 스크린샷":::

    편집용 보기에서는 자신이 보고서의 ‘소유자’ 및 ‘작성자’이므로 보고서를 수정할 수 있습니다.  동료와 보고서를 공유하는 경우, 동료는 종종 읽기용 보기에서 보고서를 조작할 수만 있으며 **내 작업 영역**에서 보고서 ‘소비자’입니다. 

## <a name="step-2-create-a-chart-in-a-report"></a>2단계: 보고서에서 차트 만들기
데이터에 연결되었으므로 탐색을 시작합니다. 흥미로운 항목을 발견하면 보고서 캔버스에 저장할 수 있습니다. 그런 다음 대시보드에 고정하여 모니터링하고 시간이 지남에 따라 어떻게 변경되는지 확인할 수 있습니다. 하지만 먼저 해야 할 일이 있습니다.
    
1. 보고서 편집기에서 페이지의 오른쪽에 있는 **필드** 창을 사용하여 시각화를 구축합니다. **Gross Sales** 필드를 선택한 다음 **Date** 필드를 선택합니다.
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="필드 목록의 스크린샷":::

    Power BI에서 데이터를 분석하고 세로 막대형 차트 시각화를 만듭니다. 

    > [!NOTE]
    > **Gross Sales** 필드 대신 **Date** 필드를 먼저 선택한 경우 테이블이 표시됩니다. 염려하지 마세요. 다음 단계에서 시각화를 변경할 예정입니다.

    일부 필드에는 옆에 시그마 기호가 있습니다. Power BI에서 숫자 값이 포함된 것으로 검색되었기 때문입니다.

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="시그마 기호가 있는 필드":::

2. 이 데이터를 표시하는 다른 방법으로 전환해 보겠습니다. 꺾은선형 차트는 시간에 따른 값을 표시하는 데 유용한 시각적 개체입니다. **시각화** 창에서 **꺾은선형 차트** 아이콘을 선택합니다.
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="꺾은선형 차트가 선택된 보고서 편집기의 스크린샷":::

3. 이 차트가 흥미로워 보이므로 대시보드에 *고정*해 보겠습니다. 시각화를 마우스로 가리키고 고정 아이콘을 선택합니다.
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="고정 아이콘의 스크린샷":::

4. 이 보고서는 새로운 항목이므로, 먼저 저장해야 시각화를 대시보드에 고정할 수 있다는 메시지가 표시됩니다. 보고서에 이름을 ‘재무 샘플 보고서’ 등으로 지정하고 **저장**을 선택합니다. 

    이제 보고서가 읽기용 보기에서 표시됩니다. 

6. **고정** 아이콘을 다시 선택합니다.
 
5. **새 대시보드**를 선택하고 ‘재무 샘플 대시보드’로 이름을 지정합니다. 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="대시보드 이름 지정의 스크린샷":::
  
    오른쪽 위에 표시되는 성공 메시지를 통해 시각화가 타일로 대시보드에 추가되었음을 알 수 있습니다.
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="대시보드에 고정 대화 상자의 스크린샷":::

    이 시각적 개체를 고정했으므로 이제 이 시각적 개체는 대시보드에 저장되었습니다. 데이터가 최신 상태로 유지되므로, 최신 값을 한눈에 추적할 수 있습니다. 그러나 보고서의 시각화 형식을 변경하는 경우 대시보드의 시각화는 변경되지 않습니다.

7. **대시보드로 이동**을 선택하여 새 대시보드에 타일로 고정한 꺾은선형 차트를 확인합니다. 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="시각적 개체가 고정된 대시보드의 스크린샷":::
   
8. 대시보드에서 새 타일을 선택합니다. Power BI가 읽기용 보기에서 보고서로 돌아갑니다.

1. 편집용 보기로 다시 전환하려면 메뉴 모음에서 **추가 옵션**(...) > **편집**을 선택합니다.

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="편집을 선택하여 보고서 편집의 스크린샷":::

    편집용 보기로 돌아가 타일을 계속 탐색하고 고정할 수 있습니다.

## <a name="step-3-explore-with-qa"></a>3단계: 질문 및 답변을 사용한 탐색

데이터의 빠른 탐색을 위해 질문 및 답변 상자에 질문을 합니다. 질문 및 답변을 사용하면 데이터에 대한 자연 언어 쿼리를 만들 수 있습니다. 대시보드에서 질문 및 답변 상자는 상단 메뉴 모음 아래에 있습니다(**데이터에 대해 질문하기**). 보고서에서는 위쪽 메뉴 모음에 있습니다(**질문하기**).

1. 대시보드로 돌아가려면 검은색 **Power BI** 막대에서 **내 작업 영역** 머리글 표시줄을 선택합니다.

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="내 작업 영역으로 돌아가기의 스크린샷":::

1. **내 작업 영역**에서 대시보드를 선택합니다.

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="대시보드 선택의 스크린샷":::

1. **데이터에 대해 질문하기**를 선택합니다. 질문 및 답변에서 자동으로 몇 가지 제안을 제공합니다. 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="질문 및 답변 캔버스의 스크린샷":::

    > [!NOTE]
    > 제안이 표시되지 않는 경우 **새 질문 및 답변 환경**을 켭니다.

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="새 질문 및 답변 환경 설정의 스크린샷":::

1. 일부 제안은 단일 값을 반환합니다. 예를 들어 **what is the average cog**를 선택합니다.

    질문 및 답변에서 답변을 검색하고 *카드* 시각화 형태로 제공합니다.

3. **시각적 개체 고정**을 선택하여 이 시각화를 재무 샘플 대시보드에 고정합니다.

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="시각적 개체 고정의 스크린샷":::

1. 질문 및 답변으로 돌아가 **모든 제안 표시**를 선택합니다.
1. **total profit by country**를 선택합니다. 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="국가별 총 수익의 스크린샷":::

1. 지도도 재무 샘플 대시보드에 고정합니다.

1. 대시보드에서 방금 고정한 지도를 선택합니다. 질문 및 답변을 다시 여는 방법을 확인하실 수 있죠? 
1. 질문 및 답변 상자의 *by country* 뒤에 커서를 놓고 *as bar*를 입력합니다. Power BI에서 결과가 포함된 막대형 차트가 만들어집니다.

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="막대형 차트 시각화의 스크린샷":::

1. 막대형 차트도 재무 샘플 대시보드에 고정합니다.

4. **질문 및 답변 끝내기**를 선택하여 대시보드로 돌아가면 만들어진 새 타일이 표시됩니다. 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="질문과 답변 시각적 개체가 고정된 대시보드의 스크린샷":::

   질문 및 답변에서 지도를 막대 차트로 변경한 경우에도 타일이 지도로 유지된 것을 볼 수 있습니다. 고정한 것은 지도였기 때문입니다. 

## <a name="step-4-reposition-tiles"></a>4단계: 타일 위치 변경

타일을 재정렬하여 대시보드 공간을 더 효율적으로 사용할 수 있습니다.

1. 판매 타일과 같은 높이로 맞춰질 때까지 *총 판매량* 꺾은선형 차트 타일의 오른쪽 아래 모퉁이를 위로 끈 다음 놓습니다.

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="타일 크기 조정의 스크린샷":::

    이제 두 타일의 높이가 같습니다.

1. Average of COGS 타일에 대해 **추가 옵션(...)** 을 선택한 후 **세부 정보 편집**을 선택합니다. 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="타일에 대한 추가 옵션 메뉴의 스크린샷":::

1. **제목** 상자에 ‘평균 판매 제품 원가’ 입력 > **적용**을 선택합니다.

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="세부 정보 편집 대화 상자의 스크린샷":::

1. 다른 시각적 개체를 함께 다시 정렬합니다.

    이편이 훨씬 낫습니다.

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="다시 정렬된 대시보드의 스크린샷":::


## <a name="clean-up-resources"></a>리소스 정리
자습서를 완료했으므로 데이터 세트, 보고서 및 대시보드를 삭제할 수 있습니다. 

1. 검은색 **Power BI** 머리글 표시줄에서 **내 작업 영역**을 선택합니다.
2. 재무 샘플 데이터 세트 옆에서 **추가 옵션(...)** 을 선택한 후 **삭제**를 선택합니다.

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="데이터 세트 삭제의 스크린샷":::

    **이 데이터 세트의 데이터를 포함하는 모든 보고서 및 대시보드 타일이 삭제됩니다**라는 경고가 표시됩니다.

4. **삭제**를 선택합니다.

## <a name="next-steps"></a>다음 단계

Power BI에 관한 다음 Microsoft Learn 콘텐츠 컬렉션을 살펴봅니다.

- [Power BI 학습](https://docs.microsoft.com/users/microsoftpowerplatform-5978/collections/r52to235xrjxk)
- [Power BI 데이터 분석가 되기](https://docs.microsoft.com/users/microsoftpowerplatform-5978/collections/djwu3eywpk4nm)
