---
title: 대시보드 및 보고서에 댓글 추가
description: 이 문서에서는 대시보드, 보고서 또는 시각적 개체에 댓글을 추가하는 방법과 댓글을 사용하여 공동 작업자와 대화하는 방법을 보여 줍니다.
author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 09/25/2020
ms.author: mihart
LocalizationGroup: Consumer
ms.openlocfilehash: 6f7e640669b53d67a635083d3ae48e23720c9e61
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2020
ms.locfileid: "91375102"
---
# <a name="add-comments-to-a-dashboard-or-report"></a>대시보드 또는 보고서에 댓글 추가

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

개별 댓글을 추가하거나 동료와 대시보드 또는 보고서에 관한 대화를 시작합니다. **주석** 기능은 비즈니스 사용자가 다른 사용자와 협업할 수 있는 방법 중 하나입니다. 

![댓글 비디오](media/end-user-comment/comment.gif)

> [!NOTE]
> 공유된 보고서에 주석을 추가하는 것을 포함하여 다른 사용자와 협업하려면 Power BI Pro 라이선스가 필요하거나 콘텐츠가 Power BI Premium 용량에 호스트되어야 합니다. [사용 중인 라이선스 유형 확인](end-user-license.md)

## <a name="how-to-use-the-comments-feature"></a>의견 기능 사용 방법
전체 대시보드, 대시보드의 개별 시각적 개체, 보고서 페이지, 페이지를 매긴 보고서 및 보고서 페이지의 개별 시각적 개체에 설명을 추가할 수 있습니다. 일반 주석을 추가하거나 특정 동료를 대상으로 하는 주석을 추가합니다.  

보고서에 댓글을 추가할 때 Power BI는 현재 필터 및 슬라이서 값을 캡처하고 [책갈피](end-user-bookmarks.md)를 만듭니다. 즉, 댓글을 선택하거나 응답하면 보고서 페이지 또는 보고서 시각적 개체가 변경되어 댓글을 처음 추가할 때 활성화된 필터 및 슬라이서 선택 항목을 표시할 수 있습니다.  

![필터가 있는 보고서 동영상](media/end-user-comment/power-bi-comment.gif)

이 기능이 왜 중요할까요? 동료가 팀과 공유하려는 흥미로운 인사이트를 표시하는 필터를 적용했다고 가정한다면, 해당 필터를 선택하지 않을 경우 댓글이 적합하지 않을 수 있습니다.

페이지를 매긴 보고서를 사용하는 경우 보고서에 관한 일반적인 설명만 추가할 수 있습니다.  개별 페이지를 매긴 보고서 시각적 개체에 관한 설명을 추가하는 기능은 지원되지 않습니다.

### <a name="add-a-general-comment-to-a-dashboard-or-report"></a>대시보드 또는 보고서에 일반 댓글 추가
대시보드 또는 보고서에 댓글을 추가하는 프로세스는 비슷합니다.  이 예제에서는 대시보드를 사용합니다. 

1. Power BI 대시보드 또는 보고서를 열고 **주석** 아이콘을 선택합니다. 이렇게 하면 댓글 대화 상자가 열립니다.

    ![메뉴 모음의 주석 아이콘](media/end-user-comment/power-bi-comment-icon.png)

    여기서는 대시보드 작성자가 이미 일반 댓글을 추가한 것을 볼 수 있습니다.  이 대시보드에 대한 액세스 권한이 있는 사용자는 누구나 이 댓글을 볼 수 있습니다.

    ![주석 섹션이 선택된 대시보드의 스크린샷](media/end-user-comment/power-bi-first-comments.png)

2. 응답하려면 **회신**을 선택하고 응답을 입력한 다음, **게시**를 선택합니다.  

    ![회신 선택 화면](media/end-user-comment/power-bi-comments-reply.png)

    기본적으로 Power BI는 댓글 스레드를 시작한 동료(이 경우 Aaron)에게 응답을 보냅니다. 

    ![응답 주석](media/end-user-comment/power-bi-respond.png)

 3. 기존 스레드의 일부가 아닌 댓글을 추가하려면 위쪽 텍스트 필드에 댓글을 입력합니다.

    ![새 스레드를 보여 주는 스크린샷](media/end-user-comment/power-bi-new-commenting.png)

    이 대시보드에 대한 댓글은 이제 다음과 같습니다.

    ![주석 대화](media/end-user-comment/power-bi-conversation.png)

### <a name="add-a-comment-to-a-specific-dashboard-or-report-visual"></a>특정 대시보드 또는 보고서 시각적 개체에 댓글 추가
전체 대시보드 또는 전체 보고서 페이지에 댓글을 추가하는 것 외에도, 개별 대시보드 타일과 개별 보고서 시각적 개체에 댓글을 추가할 수 있습니다. 프로세스는 비슷하며, 이 예제에서는 보고서를 사용합니다.

1. 시각적 개체를 마우스로 가리키고 **추가 작업**(...)을 선택합니다.    
2. 드롭다운에서 **댓글 추가**를 선택합니다.

    ![댓글 추가가 첫 번째 옵션입니다.](media/end-user-comment/power-bi-comment-reports.png)  

3.  **댓글** 대화 상자가 열리고, 페이지의 다른 시각적 개체는 회색으로 표시됩니다. 이 시각적 개체에는 아직 댓글이 없습니다. 

    ![선택된 시각적 개체와 열린 주석 대화 상자의 스크린샷](media/end-user-comment/power-bi-comments-column.png)  

4. 댓글을 입력하고 **게시**를 선택합니다.

    ![새 메시지가 포함된 주석 대화 상자](media/end-user-comment/power-bi-comment-spikes.png)  

    - 보고서 페이지에서 시각적 개체에 생성된 주석을 선택하면 해당 시각적 개체가 강조 표시됩니다(아래 참조).

    - 대시보드에서 차트 아이콘 ![차트 아이콘으로 주석 달기](media/end-user-comment/power-bi-comment-chart-icon.png) 을 통해 댓글이 특정 시각적 개체에 연결되어 있음을 확인할 수 있습니다. 전체 대시보드에 적용되는 댓글에는 특별한 아이콘이 없습니다. 차트 아이콘을 선택하면 대시보드에서 관련 시각적 개체가 강조 표시됩니다.
    

    ![관련 시각적 개체 강조 표시](media/end-user-comment/power-bi-highlights.png)

5. **닫기**를 선택하여 대시보드 또는 보고서로 돌아갑니다.

### <a name="get-your-colleagues-attention-by-using-the--sign"></a>@ 기호를 사용하여 동료의 주의 유도
대시보드, 보고서, 타일 또는 시각적 개체 댓글을 만드는지와 관계없이 “\@” 기호를 사용하여 동료의 주의를 끕니다.  “\@” 기호를 입력하면 Power BI는 조직에서 개인을 검색하고 선택할 수 있는 드롭다운을 엽니다. "\@" 기호로 나타나는 확인된 이름은 파란색 글꼴로 표시됩니다. @mentioned 개인은 즉시 받은 편지함에 메일을 받으며, Power BI 모바일 앱을 사용하는 경우 디바이스에서 푸시 알림을 받습니다. 알림에서 직접 댓글을 열고, 데이터를 확인하고, 그에 따라 회신할 수 있습니다.

다음은 시각화 ‘디자이너’와 나누는 대화입니다. @ 기호를 사용하여 댓글을 보도록 유도합니다. 알림을 받고 링크를 선택하여 해당 대시보드 및 관련 대화를 엽니다.  

![댓글 멘션 추가](media/end-user-comment/power-bi-comment-conversation.png)  

## <a name="considerations-and-troubleshooting"></a>고려 사항 및 문제 해결

- 대화에 회신할 때는 책갈피가 캡처되지 않습니다. 대화의 첫 번째 댓글만 책갈피를 만듭니다.
- 페이지를 매긴 보고서를 사용하는 경우 보고서에 관한 일반적인 설명만 추가할 수 있습니다.  개별 페이지를 매긴 보고서 시각적 개체에 관한 설명을 추가하는 기능은 지원되지 않습니다.

## <a name="next-steps"></a>다음 단계
[비즈니스 사용자를 위한 시각화](end-user-visualizations.md)로 돌아가기    
[시각화를 선택하여 보고서 열기](end-user-report-open.md)
