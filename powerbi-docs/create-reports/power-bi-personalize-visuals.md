---
title: 사용자가 보고서에서 시각적 개체를 개인 설정할 수 있습니다.
description: 보고서를 읽는 사람이 편집하지 않고 보고서를 직접 만들 수 있습니다.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867119"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>사용자가 보고서에서 시각적 개체를 개인 설정할 수 있습니다.

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

광범위한 대상 그룹과 보고서를 공유하는 경우 일부 사용자는 특정 시각적 개체를 약간 다르게 보고 싶어 할 수 있습니다. 축에 있는 항목을 교환하거나, 시각적 개체 유형을 변경하거나, 도구 설명에 항목을 추가하려고 합니다. 모든 사용자의 요구 사항을 충족하는 하나의 시각적 개체를 만드는 것은 어렵습니다. 이 새로운 기능을 사용하면 보고서 읽기용 보기에서 시각적 개체를 탐색하고 개인 설정할 수 있습니다. 시각적 개체를 원하는 방식으로 조정하고, 책갈피로 저장하여 다시 돌아올 수 있습니다. 보고서에 대한 편집 권한이 필요 없거나, 변경하기 위해 보고서 작성자에게 다시 돌아갈 필요가 없습니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="시각적 개체 개인 설정":::
 
## <a name="what-report-consumers-can-change"></a>보고서 소비자가 변경할 수 있는 내용

이 기능을 통해 소비자는 Power BI 보고서에서 시각적 개체의 임시 탐색을 통해 추가 정보를 얻을 수 있습니다. 이 기능은 보고서 읽기 권한자가 기본 탐색 시나리오를 사용하도록 허용하려는 보고서 작성자에게 적합합니다. 보고서 읽기 권한자는 다음과 같은 수정 작업을 수행할 수 있습니다.

- 시각화 유형 변경
- 측정값 또는 차원 교환
- 범례 추가 또는 제거
- 두 개 이상의 측정값 비교
- 집계 변경 등

이 기능을 통해 새로운 탐색 기능을 사용할 수 있습니다. 또한 소비자가 변경 내용을 캡처 및 공유하는 방법도 포함되어 있습니다.

- 변경 내용 캡처
- 변경 내용 공유
- 보고서의 모든 변경 내용 다시 설정
- 시각적 개체의 모든 변경 내용 다시 설정
- 최근 변경 내용 지우기

## <a name="turn-on-the-preview-feature"></a>미리 보기 기능 설정

이 기능은 미리 보기 상태이므로 먼저 기능 스위치를 설정해야 합니다. **파일** > **옵션 및 설정** > **옵션**으로 이동합니다. **전역** 설정 > **미리 보기 기능**에서 **시각적 개체 개인 설정**을 선택했는지 확인합니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="시각적 개체 개인 설정 사용":::

현재 파일의 설정에서 Power BI Desktop을 다시 시작해야 할 수도 있습니다.

## <a name="enable-personalization-in-a-report"></a>보고서에서 개인 설정 사용

미리 보기 스위치를 설정한 후에는 소비자가 시각적 개체를 개인 설정하도록 하려는 보고서에 대해 특별히 사용하도록 설정해야 합니다.

Power BI Desktop 또는 Power BI 서비스에서 기능을 사용하도록 설정할 수 있습니다.

### <a name="in-power-bi-desktop"></a>Power BI Desktop

Power BI Desktop에서 이 기능을 사용하도록 설정하려면 **파일** > **옵션 및 설정** > **옵션** > **현재 파일** > **보고서 설정**으로 이동합니다. **시각적 개체 개인 설정(미리 보기)** 이 설정되어 있는지 확인합니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="보고서에서 개인 설정 사용":::

### <a name="in-the-power-bi-service"></a>Power BI 서비스에서 다음을 수행합니다.

대신 Power BI 서비스 기능을 사용하도록 설정하려면 보고서의 **설정**으로 이동합니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Power BI 서비스의 보고서 설정":::

**시각적 개체 개인 설정(미리 보기)**  > **저장**을 설정합니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="서비스에서 시각적 개체 개인 설정 사용":::

## <a name="select-visuals-that-can-be-personalized"></a>개인 설정할 수 있는 시각적 개체 선택

지정된 보고서에 이 설정을 사용하도록 하면 기본적으로 해당 보고서의 모든 시각적 개체를 개인 설정할 수 있습니다. 모든 시각적 개체를 개인 설정하지 않으려면 시각적 개체에 대한 설정을 사용하거나 해제할 수 있습니다.

시각적 개체를 선택하고 > **시각화** 창에서 **서식**을 선택한 다음 > **시각적 개체 헤더**를 확장합니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="시각적 개체 헤더 선택":::
 
**시각적 개체 개인 설정** >  을 **사용** 또는 **해제**로 밉니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="시각적 개체 개인 설정 사용 또는 해제로 밀기":::

## <a name="personalize-visuals-in-the-power-bi-service"></a>Power BI 서비스에서 시각적 개체 개인 설정

사용자는 시각적 개체를 개인 설정하여 보고서 읽기용 보기를 종료하지 않고도 다양한 방법으로 데이터를 탐색할 수 있습니다. 다음 예에서는 사용자가 자신의 요구에 맞게 시각화를 수정할 수 있는 다양한 방법을 보여줍니다. 

1. Power BI 서비스의 읽기용 보기에서 보고서를 엽니다.

2. 시각적 개체의 오른쪽 위 모서리에서 **이 시각적 개체 개인 설정** ![이 시각적 개체 개인 설정 아이콘](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png) 아이콘을 선택합니다. 

### <a name="change-the-visualization-type"></a>시각화 유형 변경

**시각화 유형**을 변경하여 다른 표현에 대한 시각화를 볼 수 있습니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="시각화 유형 변경":::
 
### <a name="swap-out-a-measure-or-dimension"></a>측정값 또는 차원 교환
바꾸려는 필드를 선택한 다음 다른 측정값 또는 차원을 선택하여 X축의 측정값 또는 차원을 바꿀 수 있습니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="축 변경":::
 
### <a name="add-or-remove-a-legend"></a>범례 추가 또는 제거
범례를 추가하여 범주를 기반으로 시각적 개체의 색을 구분할 수 있습니다. **개인 설정** 창에서 **범례** 상자의 선택을 취소하여 범주 색 구분을 제거할 수 있습니다. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="범례 추가 또는 제거":::

### <a name="compare-two-or-more-different-measures"></a>두 개 이상의 다른 측정값 비교
\+ 아이콘으로 시각적 개체에 대한 여러 측정값을 추가하여 여러 측정값에 대한 및 대비 값을 비교할 수 있습니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="측정값 비교":::

### <a name="change-aggregations"></a>집계 변경
**개인 설정** 창에서 집계를 변경하여 측정값이 계산되는 방식을 변경할 수 있습니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="집계 변경":::

### <a name="capture-changes"></a>변경 내용 캡처 
개인 책갈피를 사용하여 개인 설정된 보기로 돌아갈 수 있도록 변경 내용을 캡처합니다. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="책갈피 만들기":::
 
책갈피를 기본 보기로 만들 수도 있습니다.

### <a name="share-changes"></a>변경 내용 공유 
읽기 및 다시 공유 권한이 있는 경우 보고서를 공유하면 변경 내용을 포함하도록 선택할 수 있습니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="변경 내용 공유":::
 
### <a name="reset-all-your-changes-to-a-report"></a>보고서에 대한 모든 변경 내용 재설정

**기본으로 재설정**을 선택하여 보고서의 모든 변경 내용을 제거하고 작성자 보고서의 마지막으로 저장된 보기로 다시 설정합니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="모든 변경 내용 재설정":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>시각적 개체에 대한 모든 변경 내용 재설정

특정 시각적 개체에 대한 변경 내용을 모두 제거하고 해당 시각적 개체의 마지막으로 저장된 보기로 재설정하려면 **이 시각적 개체 재설정**을 선택합니다.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="모든 시각적 변경 내용 재설정":::
 
### <a name="clear-recent-changes"></a>최근 변경 내용 지우기

**개인 설정** 창을 연 이후 변경한 최근 내용을 모두 지우려면 지우개 아이콘을 선택합니다.  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="최근 변경 내용 되돌리기":::

## <a name="limitations-and-known-issues"></a>제한 사항 및 알려진 문제

현재 이 기능에는 몇 가지 주의 사항이 있습니다.

- 이 기능은 웹에 게시와 같은 포함 시나리오에 대해 지원되지 않습니다.
- 사용자 탐색은 자동으로 유지되지 않습니다. 변경 내용을 캡처하려면 개인 책갈피로 보기를 저장해야 합니다.
- Power BI 모바일 앱에 있는 동안에는 시각적 개체를 변경할 수 없습니다. 그러나 Power BI 서비스 중에 개인 책갈피에 저장한 시각적 개체 변경 내용은 모바일 앱에서 적용됩니다.

또한 해결 중인 알려진 문제가 몇 가지 있습니다.

- 계층 구조 추가는 지원되지 않습니다. 개별 자식 항목을 추가해야 합니다.
- 날짜 계층 구조를 날짜로 변경하거나 그 반대로 변경할 수 없습니다. 
- 개인 책갈피를 사용하면 선택한 시퀀스에 따라 약간 다른 결과를 얻을 수 있습니다. 보고서의 전체 상태가 아닌 수정된 내용만 캡처하기 때문에 불일치가 발생할 수 있습니다. 해결 방법으로 **기본으로 재설정**을 선택하고 볼 책갈피를 선택합니다. 

## <a name="next-steps"></a>다음 단계

새 시각적 개체 개인 설정 환경을 사용해보세요. [Power BI Ideas 사이트](https://ideas.powerbi.com/forums/265200-power-bi)에서 이 기능에 대한 피드백을 제공하고 기능을 계속 개선할 방법을 알려주세요. 

궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)

