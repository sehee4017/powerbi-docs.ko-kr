---
title: 계층 구조 슬라이서에 여러 필드 추가
description: 계층 구조에 여러 필드를 포함하는 계층 구조 슬라이서를 만드는 방법을 알아봅니다.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 07/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 5fbaeaafb14fc935e26b4a2d13acf9dc09ea188f
ms.sourcegitcommit: 11deeccf596e9bb8f22615276a152614f7579f35
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86409578"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>계층 구조 슬라이서에 여러 필드 추가

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

단일 슬라이서에서 여러 개의 관련 필드를 필터링하려는 경우 계층 구조 슬라이서를 빌드하면 됩니다. 이러한 슬라이서는 Power BI Desktop 또는 Power BI 서비스에서 만들 수 있습니다.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Power BI의 계층 구조 슬라이서 스크린샷":::

슬라이서에 여러 필드를 추가하면 기본적으로 항목 옆에 화살표 또는 펼침 단추가 표시되며, 펼치면 다음 수준의 항목을 표시할 수 있습니다.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Power BI의 계층 구조 슬라이서 드롭다운 스크린샷":::
 
 
항목의 자식 요소를 하나 이상 선택하면 최상위 항목의 부분 선택된 원이 표시됩니다.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Power BI의 단일 선택 계층 구조 슬라이서 스크린샷":::

## <a name="format-the-slicer"></a>슬라이서의 서식을 지정합니다.

슬라이서의 동작은 변경되지 않았습니다. 원하는 방식으로 슬라이서의 스타일을 지정할 수도 있습니다. 예를 들어 단일 선택 모드로 설정할 수 있습니다. 또는 목록과 드롭다운 간에 전환할 수 있습니다. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="드롭다운 슬라이서로 서식 지정된 계층 구조 슬라이서의 스크린샷":::

다음과 같이 서식을 변경할 수도 있습니다.

### <a name="change-the-title"></a>제목 변경

슬라이서의 제목을 편집할 수 있지만, 이 기능은 계층 구조 슬라이서에 특히 유용합니다. 기본적으로 계층 구조 슬라이서 이름은 계층 구조의 필드 이름 목록입니다.

이 예제에서 슬라이서의 제목에는 계층 구조에 있는 다음 세 필드가 나열됩니다. 유형, 플랫폼, 이름.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="유형, 플랫폼 및 이름 필드를 포함하는 계층 구조 슬라이서의 스크린샷":::

이름을 변경하려면 슬라이서를 선택하고 **서식** 창을 선택합니다. **슬라이서 헤더**에서 **제목 텍스트** 상자에 슬라이서의 현재 이름이 표시됩니다.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="현재 제목이 있는 서식 창의 스크린샷":::

텍스트를 선택하고 새 이름을 추가합니다.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="계층 구조 슬라이서의 새 제목 스크린샷":::


### <a name="change-the-expandcollapse-icon"></a>확장/축소 아이콘 변경

계층 구조 슬라이서에는 그 밖의 몇 가지 서식 지정 옵션이 있습니다. 기본 화살표에서 확장/축소 아이콘을 더하기/빼기 기호 또는 캐럿으로 변경할 수 있습니다.

1. 슬라이서를 선택한 다음 **형식**을 선택합니다.
1. **항목**을 확장하고 **확장/축소 아이콘**을 선택합니다.
1. **펼침 단추**, **더하기/빼기** 또는 **캐럿** 중에서 선택합니다.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="계층 구조 슬라이서의 확장/축소 아이콘 선택 스크린샷":::
 
### <a name="change-the-indentation"></a>들여쓰기 변경

보고서에 공간 여유가 없으면 자식 요소의 들여쓰기 크기를 줄이는 것이 좋습니다. 기본적으로 들여쓰기는 15픽셀이지만 늘리거나 줄일 수 있습니다. 

1. 슬라이서를 선택한 다음 **형식**을 선택합니다.
1. **항목**을 확장한 다음 **계단형 레이아웃 들여쓰기**를 끌어 작게 또는 크게 조정합니다. 상자에 숫자를 입력할 수도 있습니다.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="계층 구조 슬라이서 들여쓰기 설정 스크린샷":::

## <a name="next-steps"></a>다음 단계

- [Power BI의 슬라이서](../visuals/power-bi-visualization-slicers.md)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)