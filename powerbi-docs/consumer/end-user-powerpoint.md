---
title: PowerPoint로 전체 보고서 내보내기
description: Power BI 보고서를 PowerPoint로 내보내는 방법을 알아봅니다.
author: mihart
ms.reviewer: mihart
ms.custom: contperfq4
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 07/01/2020
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: d49d92261b141a66021bb0809c214e712bd687c8
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2020
ms.locfileid: "86263734"
---
# <a name="export-reports-to-powerpoint"></a>PowerPoint로 보고서 내보내기

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]


Power BI 서비스(app.powerbi.com)를 사용하여 보고서를 Microsoft PowerPoint에 게시하고 Power BI 보고서에 따라 슬라이드 모음을 쉽게 만들 수 있습니다. PowerPoint로 내보내는 경우 다음이 발생합니다.

* Power BI 보고서의 각 페이지는 PowerPoint에서 개별 슬라이드를 생성합니다.
* Power BI 보고서의 각 페이지는 PowerPoint에서 단일 고해상도 이미지로 내보내집니다.
* 보고서에 추가한 필터와 슬라이서 설정을 유지할 수 있습니다.
* Power BI 보고서로 연결되는 링크가 PowerPoint에서 만들어집니다.

**Power BI 보고서**를 **PowerPoint**로 빠르게 내보낼 수 있습니다. 다음 섹션에서 설명하는 단계를 수행합니다.

Power BI 서비스에서 한 번에 하나의 시각적 개체를 복사하여 PowerPoint(또는 붙여넣기를 지원하는 다른 프로그램)에 붙여넣을 수도 있습니다. **이미지로 복사** 아이콘을 선택하여 시각적 개체를 클립보드에 복사합니다. 그런 다음 PowerPoint를 열고 시각적 개체를 붙여넣습니다. 자세한 내용은 [시각적 개체를 정적 이미지로 복사](../visuals/power-bi-visualization-copy-paste.md)를 참조하세요.

![이미지로 복사 아이콘 선택](media/end-user-powerpoint/power-bi-copy.png)

## <a name="export-your-power-bi-report-to-powerpoint"></a>Power BI 보고서를 PowerPoint로 내보내기
**Power BI 서비스**에서 보고서를 선택하여 캔버스에 표시합니다. **홈**, **앱** 또는 탐색 창의 다른 컨테이너에서 보고서를 선택할 수도 있습니다.

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

PowerPoint로 내보내려는 보고서가 캔버스에 표시되면 메뉴 모음에서**파일** > **PowerPoint로 내보내기**를 선택합니다.

![메뉴 모음에서 내보내기 선택](media/end-user-powerpoint/power-bi-export.png)

**현재 값** 또는 **기본 값**을 선택할 수 있는 옵션이 있는 팝업이 표시됩니다. **현재 값**은 슬라이서 및 필터 값에 대한 활성 변경 내용을 포함하는 현재 상태의 보고서를 내보냅니다.  대부분의 사용자는 이 옵션을 선택합니다. 스크롤한 경우 **현재 값**이 시각적 개체의 스크롤 상태를 포함하지 않는 대신 데이터의 위쪽 부분을 내보냅니다. 또는 **기본 값**을 선택하면 보고서가 원래 상태(*디자이너*가 공유한 상태)로 내보내지고 사용자가 원래 상태에서 변경한 내용이 반영되지 않습니다.

![내보낼 항목 선택](media/end-user-powerpoint/power-bi-current-values.png)
 
또한 보고서의 숨겨진 탭을 내보낼지 여부를 선택하는 확인란이 있습니다. 브라우저에 표시되는 보고서 탭만 내보내려면 이 확인란을 선택합니다. 모든 숨겨진 탭을 보고서의 일부로 가져오려면 이 확인란을 선택하지 않은 상태로 둡니다. 확인란이 회색으로 표시되면 보고서에 숨겨진 탭이 포함되지 않습니다. 숨겨진 탭의 예로는 도구 설명 탭이 있습니다. [사용자 지정 도구 설명](../create-reports/desktop-tooltips.md)은 보고서 *디자이너*에서 만들어지고 *소비자*의 Power BI 서비스에서 보고서 탭으로 표시되지 않습니다. 

항목을 선택한 후 **내보내기**를 선택하여 계속 진행합니다. Power BI 서비스 브라우저 창의 오른쪽 위 모서리에 보고서가 PowerPoint로 내보내지고 있다는 알림 배너가 표시됩니다. 



![PowerPoint로 내보내기 진행 중 알림](media/end-user-powerpoint/power-bi-export-progress.png)

내보내기가 완료되려면 몇 분 정도 걸릴 수 있습니다. 소요 시간에 영향을 줄 수 있는 요소에는 보고서의 구조, Power BI 서비스의 현재 부하 등이 있습니다. 보고서를 내보내는 동안 Power BI에서 계속 작업을 진행할 수 있습니다.

Power BI 서비스가 내보내기 작업을 완료하면 알림 배너에서 메시지를 통해 내보내기 프로세스가 완료되었음을 알려줍니다. 브라우저가 다운로드한 파일을 표시하면 파일을 사용할 수 있습니다. 다음 이미지에서는 브라우저 창 하단의 다운로드 배너로 표시됩니다.

![화면 맨 아래에 브라우저 알림 표시](media/end-user-powerpoint/power-bi-browsers.png)

이제 필요한 항목이 모두 준비되었습니다. 파일을 다운로드하고 PowerPoint로 연 다음 다른 PowerPoint 모음에서 원하는 대로 수정하거나 개선할 수 있습니다.

## <a name="open-the-powerpoint-file"></a>PowerPoint 파일 열기
Power BI가 내보낸 PowerPoint 파일을 열면 훌륭하고 유용한 요소가 있습니다. 다음 이미지를 살펴보고 이러한 유용한 기능 중 일부에 대해 설명하는 몇몇 요소를 확인합니다. PowerPoint의 페이지는 Power BI 보고서의 원래 페이지 크기에 관계 없이 항상 표준 9:16 크기로 만들어집니다.

![PowerPoint가 표시됩니다.](media/end-user-powerpoint/power-bi-powerpoint-numbered.png)

1. 슬라이드 모음의 첫 번째 페이지에는 보고서의 이름 및 링크가 포함되어 슬라이드 모음의 기반이 되는 보고서를 **Power BI에서 볼** 수 있습니다.
2. 보고서에 대한 유용한 정보도 확인할 수 있습니다. **마지막 데이터 새로 고침**에는 내보내진 보고서의 기준 날짜와 시간이 표시됩니다. **다운로드됨**에는 Power BI 보고서가 PowerPoint 파일로 내보내진 날짜와 시간이 표시됩니다. **다운로드됨** 시간은 내보내기 시점에서 컴퓨터의 표준 시간대로 설정됩니다.


3. 각 보고서 페이지는 탐색 창에서 표시된 것과 같이 별도 슬라이드입니다. 
4. 게시되는 보고서는 Power BI 설정 또는 브라우저의 로캘 설정에 따른 언어로 렌더링됩니다. 언어 기본 설정을 보거나 설정하려면 ![톱니바퀴 아이콘](media/end-user-powerpoint/power-bi-settings-icon.png) > **설정** > **일반** > **언어**를 선택합니다. 로캘 정보는 [Power BI에 지원되는 언어 및 국가 또는 지역](../fundamentals/supported-languages-countries-regions.md)을 참조하세요.


개별 슬라이드를 보면 각 보고서 페이지가 독립적인 이미지라는 것을 알 수 있습니다. 각 슬라이드가 정적 이미지이므로 PowerPoint에서 스크롤할 수 없습니다.

![각 시각적 개체를 개별 이미지로 보여 주는 화면](media/end-user-powerpoint/power-bi-images.png)

거기에서 PowerPoint 모음이나 고해상도 이미지로 원하는 작업을 수행할 수 있습니다.

## <a name="considerations-and-troubleshooting"></a>고려 사항 및 문제 해결
**PowerPoint로 내보내기** 기능을 사용할 때 유의해야 할 고려 사항 및 제한 사항이 있습니다.
 

* **내보내기** 옵션이 표시되지 않으면 “새 디자인”이 사용하도록 설정되어 있고 보고서(대시보드 아님)가 표시되어 있는지 확인합니다.

    ![새 디자인 토글의 스크린샷](media/end-user-powerpoint/power-bi-new-look.png)

* 현재는 내보내기에서 **현재 값**을 선택할 경우 [URL 필터](../collaborate-share/service-url-filters.md)가 적용되지 않습니다.

* PowerPoint로 내보내는 보고서에 사용자 지정 글꼴이 사용된 경우 해당 글꼴은 기본 글꼴로 바뀝니다.

* 다음 시각적 개체 형식은 지원되지 않으며 PowerPoint로 내보내지지 않습니다.
   - [인증되지 않은 사용자 지정 시각적 개체](../developer/visuals/power-bi-custom-visuals-certified.md)는 지원되지 않습니다. 
   - [ESRI ArcGIS 시각적 개체](../visuals/power-bi-visualizations-arcgis.md)는 지원되지 않습니다.
   - R 및 Python 시각적 개체는 지원되지 않습니다.
   - 배경 이미지는 차트의 경계 영역에서 잘립니다. PowerPoint로 내보내기 전에 배경 이미지를 제거하는 것이 좋습니다.

* 일부 보고서는 내보낼 수 없습니다. 내용은 다음과 같습니다.
    - Power BI 테넌트 도메인 외부의 사용자가 소유한 보고서(예: 조직 외부 사람이 소유한 보고서 및 사용자와 공유한 보고서).
    - 조직 외부의 사람, 즉 Power BI 테넌트에 없는 사용자와 대시보드를 공유하면 해당 사용자는 공유 대시보드에 연결된 보고서를 PowerPoint로 내보낼 수 없습니다. 예를 들어 aaron@contoso.com은 david@cohowinery.com과 공유할 수 있지만, david@cohowinery.com은 연결된 보고서를 PowerPoint로 내보낼 수 없습니다.
    - 30페이지를 초과하는 보고서. 처음 30페이지만 내보내집니다.
    - 이전 버전의 PowerPoint로 내보내는 보고서.
    - 처리하는 데 1시간 이상 걸리는 보고서. 
    - 로드하는 데 6분 이상 걸리는 보고서 페이지. 

* **PowerPoint로 내보내기** 메뉴 항목을 Power BI 서비스에서 사용할 수 없다면 테넌트 관리자가 이 기능을 사용하지 않도록 설정했을 가능성이 큽니다. 자세한 내용은 테넌트 관리자에게 문의하세요.
* Power BI 서비스는 PowerPoint 내보내기에 대한 언어로 Power BI 언어 설정을 사용합니다. 언어 기본 설정을 보거나 설정하려면 ![톱니바퀴 아이콘](media/end-user-powerpoint/power-bi-settings-icon.png) > **설정** > **일반** > **언어**를 선택합니다.



## <a name="next-steps"></a>다음 단계
[시각적 개체를 정적 이미지로 복사](../visuals/power-bi-visualization-copy-paste.md)    
[보고서 인쇄](end-user-print.md)
