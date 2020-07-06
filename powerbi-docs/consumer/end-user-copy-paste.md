---
title: Power BI 서비스에서 시각화 복사하여 붙여넣기
description: Power BI 서비스에서 시각화 복사하여 붙여넣기
author: mihart
ms.reviewer: maggie tsang
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 06/25/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4ff249002248b438b189b59defffd3c61d981b70
ms.sourcegitcommit: 46a340937d9f01c6daba86a4ab178743858722ec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85398325"
---
# <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>시각적 개체를 이미지로 클립보드에 복사

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

Power BI 보고서 또는 대시보드에서 이미지를 공유하려고 했습니까? 이제 시각적 개체를 복사하여 붙여넣기를 지원하는 다른 애플리케이션에 붙여넣을 수 있습니다. 

시각적 개체의 정적 이미지를 복사하는 경우 메타데이터와 함께 시각적 개체의 복사본을 가져옵니다. 다음 내용이 포함됩니다.
* Power BI 보고서 또는 대시보드에 다시 연결
* 보고서 또는 대시보드의 제목
* 이미지에 기밀 정보가 포함되어 있는지 주의
* 마지막으로 업데이트된 타임스탬프
* 시각적 개체에 적용되는 필터

### <a name="copy-from-a-dashboard-tile"></a>대시보드 타일에서 복사

1. 복사하려는 대시보드로 이동합니다.

2. 시각적 개체의 오른쪽 위 모서리에서 **기타 작업(...)** 을 선택하고 **시각적 개체를 이미지로 복사**를 선택합니다. 

    ![시각적 개체를 표시되는 이미지 아이콘으로 복사](media/end-user-copy-paste/power-bi-copy-dashboard.png)

3. **시각적 개체를 복사할 준비가 되고** 대화 상자가 표시되면 **클립보드로 복사**를 선택합니다.

    ![클립보드로 복사 옵션을 사용하는 대화 상자](media//end-user-copy-paste/power-bi-copied.png)

4. 시각적 개체를 복사한 후 **Ctrl + V** 또는 오른쪽 단추로 클릭 > 붙여넣기를 사용하여 다른 애플리케이션에 붙여넣습니다. 아래 스크린샷에서는 시각적 개체를 Microsoft Word에 붙여넣었습니다. 

    ![Outlook에 붙여넣은 시각적 개체](media//end-user-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>보고서 시각적 개체에서 복사 

1. 복사하려는 보고서로 이동합니다.

2. 시각적 개체의 오른쪽 위 모퉁이에서 **시각적 개체를 이미지로 복사** 아이콘을 선택합니다. 

    ![시각적 개체를 표시되는 이미지 아이콘으로 복사](media/end-user-copy-paste/power-bi-copy-icon.png)

3. **시각적 개체를 복사할 준비가 되고** 대화 상자가 표시되면 **클립보드로 복사**를 선택합니다.

    ![클립보드로 복사 옵션을 사용하는 대화 상자](media//end-user-copy-paste/power-bi-copied.png)


4. 시각적 개체를 복사한 후 **Ctrl + V** 또는 오른쪽 단추로 클릭 > 붙여넣기를 사용하여 다른 애플리케이션에 붙여넣습니다. 아래 스크린샷에서는 시각적 개체를 전자 메일에 붙여넣었습니다.

    ![Outlook에 붙여넣은 시각적 개체](media//end-user-copy-paste/power-bi-copy-email.png)

5. 보고서에 데이터 민감도 레이블이 적용된 경우에는 복사 아이콘을 선택할 때 경고가 표시됩니다.  

    ![중요한 데이터 경고](media//end-user-copy-paste/power-bi-sensitive.png)

    민감도 레이블은 붙여넣은 시각적 개체 아래의 메타데이터에 추가됩니다. 

    ![기밀 정보 레이블을 사용하는 시각적 개체](media//end-user-copy-paste/power-bi-confidential.png)



## <a name="considerations-and-troubleshooting"></a>고려 사항 및 문제 해결

   ![복사를 사용할 수 없음](media//end-user-copy-paste/power-bi-copy-grey.png)


Q: 시각적 개체에서 복사 아이콘을 사용하지 않도록 설정하는 이유는 무엇인가요?    
A: 현재 네이티브 Power BI 시각적 개체와 인증된 사용자 지정 시각적 개체를 지원합니다. 다음을 비롯한 특정 시각적 개체에 대한 지원이 제한됩니다. 
- ESRI 및 기타 지도 시각적 개체 
- Python 시각적 개체 
- R 시각적 개체 
- PowerApps    

A: 시각적 개체를 복사하는 기능은 IT 부서 또는 Power BI 관리자에 의해 해제될 수 있습니다.


Q: 시각적 개체를 제대로 붙여넣지 않는 이유는 무엇인가요?    
A: 사용자 지정 시각적 개체 및 애니메이션 시각적 개체에 대한 제한 사항이 있습니다. 



## <a name="next-steps"></a>다음 단계
[Power BI 보고서의 시각화](end-user-visual-type.md)에 대해 자세히 알아보기

궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)

