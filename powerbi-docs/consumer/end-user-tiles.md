---
title: 비즈니스 사용자용 Power BI 서비스의 대시보드 타일
description: 비즈니스 사용자용 Power BI의 대시보드 타일에 대한 모든 정보. SSRS(SQL Server Reporting Services)에서 만들어진 타일을 포함합니다.
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 12/06/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: 36b1ad58b1ee93f0876de8bf7f7ed7331671abfd
ms.sourcegitcommit: 0bf42b6393cab7a37d21a52b934539cf300a08e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96781904"
---
# <a name="dashboard-tiles-in-power-bi"></a>Power BI의 대시보드 타일

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-ynny.md)]


타일은 *디자이너* 가 대시보드에 고정한 데이터의 스냅샷입니다. *디자이너* 는 보고서, 데이터 세트, 대시보드, 질문 및 답변의 질문하기 상자, Excel, SSRS(SQL Server Reporting Services) 등에서 타일을 만들 수 있습니다.  이 스크린샷은 대시보드에 고정된 여러 타일을 보여 줍니다.

![Power BI 대시보드](./media/end-user-tiles/power-bi-dashboard.png)


*설계자* 는 **타일 추가** 를 사용하여 보고서에 고정된 타일 외에 다른 독립 실행형 타일을 대시보드에 직접 추가할 수 있습니다. 독립 실행형 타일에는 텍스트 상자, 이미지, 동영상, 스트리밍 데이터 및 웹 콘텐츠가 포함됩니다.

Power BI의 구성 요소를 이해하는 데 도움이 필요한 경우  [Power BI - 기본 개념](end-user-basic-concepts.md)을 참조하세요.


## <a name="interacting-with-tiles-on-a-dashboard"></a>대시보드에서 타일 조작

1. 타일을 가리켜서 줄임표을 표시합니다.
   
    ![타일 줄임표](./media/end-user-tiles/power-bi-ellipsis.png)
2. 줄임표를 선택하여 타일 동작 메뉴를 엽니다. 사용 가능한 옵션은 권한, 시각적 개체 및 타일을 만드는 데 사용되는 방법에 따라 다릅니다. 예를 들어 질문 및 답변에서 고정된 타일에 사용할 수 있는 메뉴 항목은 보고서에서 고정된 타일과 다릅니다. 다음은 질문 및 답변을 사용하여 만든 타일의 작업 메뉴입니다.


   
    ![스크린샷은 아홉 가지 옵션이 있는 메뉴를 보여줍니다.](./media/end-user-tiles/power-bi-qna-menu.png)

   
    이러한 메뉴에서 사용할 수 있는 작업 중 일부는 다음과 같습니다.
   
   * [타일을 만드는 데 사용된 보고서 열기](end-user-reports.md) ![보고서 아이콘](./media/end-user-tiles/chart-icon.jpg)  
   
   * [타일을 만드는 데 사용된 질문 및 답변의 질문 열기 ](end-user-reports.md) ![질문 및 답변 아이콘](./media/end-user-tiles/qna-icon.png)  
   

   * [타일을 만드는 데 사용된 통합 문서 열기](end-user-reports.md) ![워크시트 아이콘](./media/end-user-tiles/power-bi-open-worksheet.png)  
   * [포커스 모드로 타일 보기](end-user-focus.md) ![포커스 아이콘](./media/end-user-tiles/fullscreen-icon.jpg)  
   * [인사이트 보기](end-user-insights.md) ![인사이트 아이콘](./media/end-user-tiles/power-bi-insights.png)
   * [댓글 추가 및 토론 시작](end-user-comment.md) ![댓글 아이콘](./media/end-user-tiles/comment-icons.png)
   * [대시보드 타일에 설정된 경고 관리](end-user-alerts.md) ![경고 아이콘](./media/end-user-tiles/power-bi-alert-icon.png)
   * [Excel에서 데이터 열기](end-user-export.md) ![내보내기 아이콘](./media/end-user-tiles/power-bi-export-icon.png)


3. 동작 메뉴를 닫으려면 캔버스의 빈 영역을 선택합니다.

### <a name="select-click-a-tile"></a>타일 선택(클릭)
타일을 선택하는 경우 다음 작업은 타일을 만든 방법 및 타일에 [사용자 지정 링크](../create-reports/service-dashboard-edit-tile.md)가 있는지 여부에 따라 달라집니다. 사용자 지정 링크가 있는 경우 타일을 선택하면 해당 링크로 이동합니다. 링크가 없는 경우 타일을 선택하면 타일을 만드는 데 사용되는 보고서, Excel Online 통합 문서, 온-프레미스인 SSRS 보고서 또는 질문 및 답변의 질문으로 이동됩니다.

> [!NOTE]
> 이에 대한 예외는 *디자이너* 가 대시보드에 추가한 비디오 타일입니다. 이러한 방식으로 만든 동영상 타일을 선택하면 동영상이 대시보드에서 바로 재생됩니다.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>고려 사항 및 문제 해결
* 타일을 선택(클릭)할 때 아무 작업도 수행되지 않거나 오류 메시지가 표시되는 경우 몇 가지 가능한 이유는 다음과 같습니다.
  - 시각화를 만드는 데 사용된 보고서가 저장되지 않았거나 삭제되었습니다.
  - 타일이 Excel Online의 통합 문서에서 만들어졌으며 해당 통합 문서에 대한 읽기 이상의 권한이 없습니다.
  - SSRS에서 타일이 생성되었고 SSRS 보고서에 대한 권한이 없거나 SSRS 서버가 있는 네트워크에 대한 액세스 권한이 없는 경우
* **타일 추가** 를 사용하여 대시보드에서 직접 만든 파일에서는, 사용자 지정 하이퍼링크가 설정된 경우 제목, 부제목 및/또는 타일을 선택하면 해당 URL이 열립니다.  그렇지 않은 경우 이미지, 웹 코드 또는 텍스트 상자에 대한 대시보드에서 직접 만든 다음 타일 중 하나를 선택하면 기본적으로 동작을 생성하지 않습니다.
* 원래 시각화를 사용하여 타일을 변경한 경우 타일이 변경되지 않습니다.  예를 들어 *설계자* 가 보고서에서 꺾은선형 차트를 고정한 다음, 꺾은선형 차트를 막대형 차트로 변경하면 대시보드 타일에 꺾은선형 차트가 계속 표시됩니다. 데이터는 새로 고쳐지지만 시각화 유형은 새로 고쳐지지 않습니다.

## <a name="next-steps"></a>다음 단계
[데이터 새로 고침](../connect-data/refresh-data.md)

[Power BI - 기본 개념](end-user-basic-concepts.md)


