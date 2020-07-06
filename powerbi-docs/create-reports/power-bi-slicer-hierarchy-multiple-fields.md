---
title: 계층 구조 슬라이서에 여러 필드 추가
description: 계층 구조에 여러 필드를 포함하는 계층 구조 슬라이서를 만드는 방법을 알아봅니다.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/11/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 2b9c4a8f4695f8d701eba535180194d29dd8bdec
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238180"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>계층 구조 슬라이서에 여러 필드 추가

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

단일 슬라이서에서 여러 개의 관련 필드를 필터링하려는 경우 계층 구조 슬라이서를 빌드하면 됩니다. 이러한 슬라이서는 Power BI Desktop 또는 Power BI 서비스에서 만들 수 있습니다.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Power BI의 계층 구조 슬라이서":::

슬라이서에 여러 필드를 추가하면 기본적으로 항목 옆에 화살표 또는 펼침 단추가 표시되며, 펼치면 다음 수준의 항목을 표시할 수 있습니다.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Power BI의 계층 구조 슬라이서 드롭다운":::
 
 
항목의 자식 요소를 하나 이상 선택하면 최상위 항목의 부분 선택된 원이 표시됩니다.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Power BI의 단일 선택 계층 구조 슬라이서":::

## <a name="format-the-slicer"></a>슬라이서의 서식을 지정합니다.

슬라이서의 동작은 변경되지 않았습니다. 원하는 방식으로 슬라이서의 스타일을 지정할 수도 있습니다. 예를 들어 단일 선택 모드로 설정할 수 있습니다. 또는 목록과 드롭다운 간에 전환할 수 있습니다. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="드롭다운 슬라이서로 형식이 지정된 계층 구조 슬라이서":::

### <a name="change-the-expandcollapse-icon"></a>확장/축소 아이콘 변경

계층 구조 슬라이서에는 그 밖의 몇 가지 서식 지정 옵션이 있습니다. 기본 화살표에서 확장/축소 아이콘을 더하기/빼기 기호 또는 캐럿으로 변경할 수 있습니다.

1. 슬라이서를 선택한 다음 **형식**을 선택합니다.
1. **항목**을 확장하고 **확장/축소 아이콘**을 선택합니다.
1. **펼침 단추**, **더하기/빼기** 또는 **캐럿** 중에서 선택합니다.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="계층 구조 슬라이서의 확장/축소 아이콘 선택":::
 
### <a name="change-the-indentation"></a>들여쓰기 변경

보고서에 공간 여유가 없으면 자식 요소의 들여쓰기 크기를 줄이는 것이 좋습니다. 기본적으로 들여쓰기는 15픽셀이지만 늘리거나 줄일 수 있습니다. 

1. 슬라이서를 선택한 다음 **형식**을 선택합니다.
1. **항목**을 확장한 다음 **계단형 레이아웃 들여쓰기**를 끌어 작게 또는 크게 조정합니다. 상자에 숫자를 입력할 수도 있습니다.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="계층 구조 슬라이서 들여쓰기 설정":::

## <a name="next-steps"></a>다음 단계

- [Power BI의 슬라이서](../visuals/power-bi-visualization-slicers.md)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)