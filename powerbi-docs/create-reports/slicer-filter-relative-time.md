---
title: Power BI에서 상대 시간 슬라이서 또는 필터 사용
description: Power BI에서 슬라이서 또는 필터를 사용하여 상대 시간 범위를 제한하는 방법을 알아봅니다.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 04/22/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 056d69a866b0b56e83557e77462e03e3e00a2c8d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85218542"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Power BI에서 상대 시간 슬라이서 및 필터 사용

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

빠른 새로 고침 시나리오가 등장하면서 더 작은 기간으로 필터링하는 기능이 유용할 수 있습니다. 상대 시간 슬라이서 또는 상대 시간 필터를 사용하면 데이터 모델의 모든 날짜 또는 시간 열에 시간 기반 필터를 적용할 수 있습니다. 예를 들어 상대 시간 슬라이서를 사용하여 지난 분 또는 시간 단위의 비디오 보기만 표시할 수 있습니다. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="상대 시간 예제":::

[자동 페이지 새로 고침](../create-reports/desktop-automatic-page-refresh.md) 기능과 함께 이 기능을 사용할 필요가 없습니다. 그러나 많은 상대 시간 시나리오는 자동 페이지 새로 고침 기능과 함께 사용됩니다.  

> [!NOTE]
> 페이지 또는 보고서 수준에서 상대 시간 필터 또는 슬라이서를 적용하면 공유 *앵커* 시간을 사용하여 해당 페이지 또는 보고서의 모든 시각적 개체가 정확히 같은 시간 범위로 필터링됩니다. 시각적 개체는 실행 시간이 약간 다를 수 있기 때문에 이 공유 앵커 시간을 사용하면 페이지 또는 보고서 전체에서 시각적 개체를 동기화할 수 있습니다. 이 문서에서 [앵커 시간](#understanding-anchor-time)에 대한 자세한 내용을 알아보세요.

## <a name="turn-on-relative-time-preview"></a>상대 시간 미리 보기 설정

상대 시간 필터가 미리 보기 상태이므로 기능 스위치를 설정해야 합니다. **파일** > **옵션 및 설정** > **옵션**으로 이동합니다. **전역 설정** > **미리 보기 기능**에서 **상대 시간 필터**가 선택되어 있는지 확인합니다.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-preview.png" alt-text="상대 시간 미리 보기 옵션 설정":::

## <a name="create-a-relative-time-slicer-or-filter"></a>상대 시간 슬라이서 또는 필터 만들기

기능을 사용하도록 설정한 후 날짜 또는 시간 필드를 슬라이서의 필드 또는 필터 창의 드롭 영역에 끌어서 놓을 수 있습니다. 

### <a name="create-a-slicer"></a>슬라이서 만들기

1. 날짜 또는 시간 필드를 캔버스에 끌어서 놓습니다.

2. **슬라이서** 시각화 유형을 선택합니다.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="시간 슬라이서 만들기":::

### <a name="create-a-filter"></a>필터 만들기
 
- **이 시각적 개체**, **이 페이지** 또는 **모든 페이지**에 대해 날짜 또는 시간 필드를 필터 창으로 끌어옵니다.

### <a name="set-relative-time"></a>상대 시간 설정 

다음으로 필터 형식을 **상대 시간**으로 변경합니다.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="상대 시간으로 변경":::
 
슬라이서에 다음과 같이 표시됩니다.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="슬라이서의 상대 시간":::

필터 카드에 다음과 같이 표시됩니다. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="필터의 상대 시간":::
 
이 새 필터 형식을 사용하면 **마지막**, **다음** 또는 **이 기간**을 기준으로 필터링하는 옵션이 있습니다. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="마지막, 다음 또는 이 기간 선택":::
 
정수 및 시간 단위를 사용하여 기간을 지정합니다. **분** 또는 **시**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="분 또는 시 선택":::

캔버스에 공간을 저장해야 하는 경우 필터 창에서 상대 시간 필터를 필터 카드로 만들 수도 있습니다.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="대신 필터에서 상대 시간 설정":::
 
## <a name="understanding-anchor-time"></a>앵커 시간 이해

페이지 또는 보고서 수준에 필터를 적용하면 해당 페이지 또는 보고서의 모든 시각적 개체가 정확히 같은 시간 범위로 동기화됩니다. 이러한 쿼리는 *앵커 시간*이라는 시간에 대해 모두 발급됩니다. 앵커 시간은 다음 조건에서 자동으로 새로 고쳐집니다.

- 초기 페이지 로드
- 수동 새로 고침
- 자동 또는 변경 내용 검색 페이지 새로 고침
- 모델 변경

### <a name="anchor-time-exceptions"></a>앵커 시간 예외

- 질문 및 답변 시각적 개체를 사용한 상대 시간 필터링은 질문 및 답변 시각적 개체를 표준 시각적 개체로 변환할 때까지 이 앵커 시간을 기준으로 하지 않습니다. 그러나 주요 영향 요인 및 분해 트리와 같은 다른 AI 시각적 개체는 앵커 시간과 동기화됩니다. 
- 또한 상대 시간 필터가 있지 않으면 상대 날짜 필터 또는 슬라이서는 앵커 시간을 기준으로 하지 않습니다. 상대 날짜 및 상대 시간 필터가 같은 페이지에 있으면 상대 날짜 필터는 앵커 시간을 적용합니다.

## <a name="limitations-and-considerations"></a>제한 사항 및 고려 사항

다음 제한 사항 및 고려 사항은 현재 상대 시간 슬라이서와 필터에 적용되는 것입니다.

- **표준 시간대 고려 사항**: Power BI의 데이터 모델에는 표준 시간대 정보가 포함되어 있지 않습니다. 모델에서 시간은 저장할 수 있지만 해당 표준 시간대가 표시되지 않습니다. 슬라이서 및 필터는 항상 UTC의 시간을 기반으로 합니다. 보고서에 필터를 설정하고 다른 표준 시간대에 있는 동료에게 보내면 둘 다 같은 데이터를 볼 수 있습니다. 사용자와 동료가 UTC 표준 시간대에 있지 않은 경우 둘 다 발생하는 시간 오프셋을 고려해야 합니다. 쿼리 편집기를 사용하여 현지 표준 시간대에서 캡처된 데이터를 UTC로 변환합니다.
- 이 새 필터 형식은 Power BI Desktop, Power BI 서비스, Power BI Embedded 및 Power BI 모바일 앱에서 지원됩니다. 그러나 다음과 같은 몇 가지 알려진 지원 제한이 있습니다.

    - 포함 API를 통해 지원되지 않습니다.
    - 웹에 게시는 지원되지 않습니다.

- **쿼리 캐싱**: 클라이언트 캐시를 활용합니다. 따라서 "최근 1분" 및 "지난 5분"을 차례로 지정한 다음 "지난 1분"으로 다시 지정한다고 가정합니다. 이때 페이지를 수동 또는 자동으로 새로 고치는 경우가 아니면 처음 실행했을 때와 같은 결과가 표시됩니다.

## <a name="next-steps"></a>다음 단계

- [Power BI에서 상대 날짜 슬라이서 및 필터 사용](../visuals/desktop-slicer-filter-date-range.md)
- [Power BI의 슬라이서](../visuals/power-bi-visualization-slicers.md)
