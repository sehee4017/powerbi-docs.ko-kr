---
title: Power BI 서비스에서 페이지를 매긴 보고서에 대한 매개 변수 만들기
description: 이 문서에서는 Power BI 서비스에서 페이지를 매긴 보고서에 대한 매개 변수를 만드는 방법을 알아봅니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 09/28/2020
ms.openlocfilehash: 3a755b2b4eeba407178d7afa0a0250b6897e6dac
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91526355"
---
# <a name="create-parameters-for-paginated-reports-in-the-power-bi-service"></a>Power BI 서비스에서 페이지를 매긴 보고서에 대한 매개 변수 만들기

이 문서에서는 Power BI 서비스에서 페이지를 매긴 보고서에 대한 매개 변수를 만드는 방법을 알아봅니다.  보고서 매개 변수는 보고서 데이터를 선택하고 보고서 프레젠테이션에 변화를 주는 방법을 제공합니다. 기본값과 사용 가능한 값 목록을 제공할 수 있습니다. 보고서 리더는 선택 항목을 변경할 수 있습니다. 매개 변수 텍스트 상자에 입력하여 값을 검색할 수도 있습니다. 비즈니스 사용자가 Power BI 서비스의 매개 변수와 상호 작용하는 방식을 확인하려면 [페이지를 매긴 보고서에 대한 매개 변수 보기](../consumer/paginated-reports-view-parameters.md)를 참조하세요.  

다음 그림에서는 Power BI 보고서 작성기에서 @BuyingGroup, @Customer, @FromDate 및 @ToDate 매개 변수를 가진 보고서에 대한 디자인 뷰를 보여줍니다. 
  
![보고서 작성기의 매개 변수](media/paginated-reports-parameters/power-bi-paginated-parameters-report-builder.png)
  
1.  보고서 데이터 창의 보고서 매개 변수  
  
2.  데이터 세트에 있는 매개 변수 중 하나가 사용된 테이블입니다.  
  
3.  매개 변수 창 매개 변수 창에서 매개 변수 레이아웃을 사용자 지정할 수 있습니다. 
  
4.  @FromDate 및 @ToDate 매개 변수는 **날짜/시간** 데이터 형식입니다. 보고서를 볼 때 텍스트 상자에 날짜를 입력하거나 달력 컨트롤에서 날짜를 선택할 수 있습니다. 

5.  **데이터 세트 속성** 대화 상자의 매개 변수 중 하나입니다.  

  
## <a name="create-or-edit-a-report-parameter"></a>보고서 매개 변수 만들기 또는 편집  
  
1.  Power BI 보고서 작성기에서 페이지를 매긴 보고서를 엽니다.

1. **보고서 데이터** 창에서 **매개 변수** 노드 > **매개 변수 추가**를 마우스 오른쪽 단추로 클릭합니다. **보고서 매개 변수 속성** 대화 상자가 열립니다.  
  
2.  **이름**에 매개 변수의 이름을 입력하거나 기본 이름을 그대로 사용합니다.  
  
3.  **프롬프트**에는 사용자가 보고서를 실행할 때 매개 변수 텍스트 상자 옆에 표시할 텍스트를 입력합니다.  
  
4.  **데이터 형식**에서 매개 변수 값에 대한 데이터 형식을 선택합니다.  
  
5.  매개 변수에 빈 값을 포함할 수 있는 경우 **빈 값 허용**을 선택합니다.  
  
6.  매개 변수에 Null 값을 포함할 수 있는 경우 **Null 값 허용**을 선택합니다.  
  
7.  사용자가 매개 변수 값을 둘 이상 선택할 수 있도록 하려면 **다중 값 허용**을 선택합니다.  
  
8.  표시 여부 옵션을 설정합니다.  
  
    -   보고서 위쪽의 도구 모음에 매개 변수를 표시하려면 **표시**를 선택합니다.  
  
    -   도구 모음에 표시되지 않도록 매개 변수를 숨기려면 **숨김**을 선택합니다.  
  
    -   매개 변수를 숨겨서 보고서가 게시된 후 보고서 서버에서 수정되지 않도록 하려면 **내부**를 선택합니다. 그러면 보고서 매개 변수는 보고서 정의에서만 볼 수 있습니다. 이 옵션을 사용하려면 기본값을 설정하거나 Null 값을 허용하도록 설정해야 합니다.  
  
9. **확인**을 선택합니다. 

## <a name="considerations-and-troubleshooting"></a>고려 사항 및 문제 해결

- Power BI 데이터 세트 또는 Analysis Services 모델을 데이터 원본으로 사용하는 경우 1000개가 넘는 매개 변수 값을 단일 요청으로 전달할 수 없습니다. DAX는 매개 변수를 1,000개의 값으로 제한합니다. 

 
## <a name="next-steps"></a>다음 단계

Power BI 서비스에서 매개 변수가 표시되는 방법을 확인하려면 [페이지를 매긴 보고서에 대한 매개 변수 보기](../consumer/paginated-reports-view-parameters.md)를 참조하세요.

페이지를 매긴 보고서의 매개 변수에 대한 자세한 내용은 [Power BI 보고서 작성기의 보고서 매개 변수](report-builder-parameters.md)를 참조하세요.
