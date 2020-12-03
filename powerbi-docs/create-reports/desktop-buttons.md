---
title: Power BI에서 단추 사용
description: 보고서를 앱처럼 동작하도록 만들고 사용자가 추가로 상호 작용할 수 있는 단추를 Power BI 보고서에 추가할 수 있습니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/21/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 77f16bedb45b0730a7007da19a427b1832bc9969
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414464"
---
# <a name="use-buttons-in-power-bi"></a>Power BI에서 단추 사용
Power BI의 **단추** 를 사용하여 보고서가 앱과 유사하게 동작하도록 만들고, 매력적인 환경을 만들어 사용자가 Power BI 콘텐츠를 마우스로 가리키고, 클릭하고, 추가로 상호 작용할 수 있습니다. **Power BI Desktop** 및 **Power BI 서비스** 에서 보고서에 단추를 추가할 수 있습니다. Power BI 서비스에서 보고서를 공유하면 해당 보고서는 사용자를 위한 앱과 유사한 환경을 제공합니다.

![Power BI의 단추](media/desktop-buttons/power-bi-buttons.png)

## <a name="create-buttons-in-reports"></a>보고서에서 단추 만들기

### <a name="create-a-button-in-power-bi-desktop"></a>Power BI Desktop에서 단추 만들기

**Power BI Desktop** 에서 단추를 만들기 위해 **삽입** 리본에서 **단추** 를 선택하면 드롭다운 메뉴가 나타납니다. 여기에서 다음 이미지에 나와 있는 대로 옵션의 컬렉션에서 원하는 단추를 선택할 수 있습니다. 

![Power BI Desktop에서 단추 컨트롤 추가](media/desktop-buttons/power-bi-button-dropdown.png)

### <a name="create-a-button-in-the-power-bi-service"></a>Power BI 서비스에서 단추 만들기

**Power BI 서비스** 에서 단추를 만들려면 편집용 보기에서 보고서를 엽니다. 맨 위 메뉴 모음에서 **단추** 를 선택하면 드롭다운 메뉴가 나타납니다. 여기에서 다음 이미지에 나와 있는 대로 옵션의 컬렉션에서 원하는 단추를 선택할 수 있습니다. 

![Power BI 서비스에서 단추 컨트롤 추가](media/desktop-buttons/power-bi-button-service-dropdown.png)

## <a name="customize-a-button"></a>단추 사용자 지정

Power BI Desktop 또는 Power BI 서비스에서 단추를 만드는지 여부에 관계없이 나머지 프로세스는 동일합니다. 보고서 캔버스에서 단추를 선택하는 경우 **시각화** 창은 요구 사항에 맞게 단추를 사용자 지정할 수 있는 여러 가지 방법을 표시합니다. 예를 들어 **시각화** 창의 카드에서 슬라이더를 토글하여 **단추 텍스트** 를 켜거나 끌 수 있습니다. 다른 속성과 함께 단추의 아이콘, 단추 채우기, 제목 및 사용자가 보고서에서 단추를 선택할 때 수행되는 동작을 변경할 수 있습니다.

![Power BI 보고서에서 단추 서식 지정](media/desktop-buttons/power-bi-button-properties.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>유휴 상태이거나, 마우스로 가리키거나, 선택된 경우 단추 속성 설정

Power BI의 단추에는 기본(마우스로 가리키거나 선택하는 경우 표시되는 방법), 마우스로 가리키는 경우 또는 선택되는 경우(*클릭됨* 이라고도 함)라는 세 가지 상태가 있습니다. 이러한 세 가지 상태에 따라 **시각화** 창에서 많은 카드를 개별적으로 수정하여 단추를 사용자 지정하기 위한 많은 유연성을 제공할 수 있습니다.

**시각화** 창의 다음과 같은 카드를 통해 세 가지 상태에 따라 서식 지정 또는 단추의 동작을 조정할 수 있습니다.

* 단추 텍스트
* 아이콘
* 윤곽선
* 채우기

각 상태에 대해 단추가 표시되는 방법을 선택하려면 해당 카드 중 하나를 확장하고 카드의 맨 위쪽에 나타나는 드롭다운을 선택합니다. 다음 이미지에서는 다음과 같은 세 가지 상태를 표시하도록 선택한 드롭다운 목록에서 **아이콘** 카드가 확장됩니다.

![Power BI 보고서에 있는 단추의 세 가지 상태](media/desktop-buttons/power-bi-button-format.png)

## <a name="select-the-action-for-a-button"></a>단추에 대한 작업 선택

사용자가 Power BI에서 단추를 선택할 때 수행되는 작업을 선택할 수 있습니다. **시각화** 창의 **작업** 카드에서 단추 작업에 대한 옵션에 액세스할 수 있습니다.

![Power BI의 단추에 대한 작업](media/desktop-buttons/power-bi-button-action.png)

단추 작업의 옵션은 다음과 같습니다.

- **뒤로** 를 선택하면 보고서의 이전 페이지로 사용자를 반환합니다. 이는 드릴스루 페이지에 유용합니다.
- **책갈피** 를 선택하면 현재 보고서에 대해 정의된 책갈피와 연결된 보고서 페이지를 표시합니다. [Power BI의 책갈피](desktop-bookmarks.md)에 대해 자세히 알아보세요. 
- **드릴스루** 를 선택하면 책갈피를 사용하지 않고 선택 영역으로 필터링된 드릴스루 페이지로 이동합니다. [보고서의 드릴스루 단추](desktop-drill-through-buttons.md)에 대해 자세히 알아보세요.
- **페이지 탐색** 을 선택하면 책갈피를 사용하지 않고 보고서 내의 다른 페이지로 이동합니다. 자세한 내용은 이 문서의 [페이지 탐색 만들기](#create-page-navigation)를 참조하세요.
- **Q&A** 를 선택하면 **Q&A 탐색기** 창이 열립니다. 

특정 단추는 기본 동작을 자동으로 선택합니다. 예를 들어 **질문 및 답변** 단추 형식은 자동으로 **질문 및 답변** 을 기본 동작으로 선택합니다. [이 블로그 게시물](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer)을 확인하여 **질문 및 답변 탐색기** 에 대해 자세히 알아볼 수 있습니다.

사용하려는 *CTRL+클릭* 단추를 사용하여 보고서에 만들 단추를 사용하거나 테스트할 수 있습니다. 

## <a name="create-page-navigation"></a>페이지 탐색 만들기

**작업** 유형 **페이지 탐색** 을 사용하면 책갈피를 저장하거나 관리하지 않고도 전체 탐색 환경을 빌드할 수 있습니다.

페이지 탐색 단추를 설정하려면 작업 유형으로 **페이지 탐색** 을 사용하여 단추를 만들고 **대상** 페이지를 선택합니다.

![페이지 탐색 작업](media/desktop-buttons/power-bi-page-navigation.png)

사용자 지정 탐색 창을 빌드하고 여기에 탐색 단추를 추가할 수 있습니다. 탐색 창에 표시할 페이지를 변경하기 위해 책갈피를 편집하고 관리할 필요가 없도록 합니다.

![탐색 페이지 만들기](media/desktop-buttons/power-bi-build-navigation-pane.png)

또한 다른 단추 유형으로 할 수 있는 것처럼 조건부로 도구 설명의 서식을 지정할 수 있습니다.

## <a name="set-the-navigation-destination-conditionally"></a>조건부로 탐색 대상 설정

측정값의 출력에 따라 조건부 서식을 사용하여 탐색 대상을 설정할 수 있습니다. 예를 들어 사용자의 선택에 따라 다른 페이지로 이동하는 단일 단추를 사용하여 보고서 캔버스의 공간을 절약할 수 있습니다.

:::image type="content" source="media/desktop-buttons/button-navigate-go.png" alt-text="이동 단추를 사용하여 탐색":::
 
위에 표시된 예제를 만들려면 먼저 탐색 대상의 이름을 포함하는 단일 열 테이블을 만듭니다.

:::image type="content" source="media/desktop-buttons/button-create-table.png" alt-text="테이블 만들기":::

Power BI는 정확한 문자열 일치를 사용하여 드릴스루 대상을 설정하므로 입력한 값이 드릴스루 페이지 이름과 정확하게 일치하는지 재차 확인하세요.

테이블을 만든 후에는 단일 선택 슬라이서로 페이지에 추가합니다.

:::image type="content" source="media/desktop-buttons/button-navigate-slicer.png" alt-text="탐색 슬라이서":::

그런 다음 페이지 탐색 단추를 만들고 대상에 대한 조건부 서식 옵션을 선택합니다.

:::image type="content" source="media/desktop-buttons/button-set-page-nav-destination.png" alt-text="페이지 탐색 단추":::
 
앞서 만든 열의 이름을 선택합니다. 이 경우 **Select a destination** 입니다.

:::image type="content" source="media/desktop-buttons/button-select-destination.png" alt-text="Select a destination":::

이제 단추를 사용하여 사용자의 선택에 따라 다른 페이지로 이동할 수 있습니다.

:::image type="content" source="media/desktop-buttons/button-navigate-go.png" alt-text="이동 단추를 사용하여 탐색":::
 
### <a name="shapes-and-images-for-navigation"></a>탐색을 위한 셰이프 및 이미지

페이지 탐색 작업은 단추뿐만 아니라 셰이프 및 이미지에 대해서도 지원됩니다. 기본 제공 셰이프 중 하나를 사용하는 예제는 다음과 같습니다.

:::image type="content" source="media/desktop-buttons/button-navigation-arrow.png" alt-text="탐색에 화살표 사용":::
 
이미지를 사용하는 예제는 다음과 같습니다.

:::image type="content" source="media/desktop-buttons/button-navigation-image.png" alt-text="탐색에 이미지 사용":::
 
## <a name="buttons-support-fill-images"></a>단추에서 채우기 이미지 지원

단추는 채우기 이미지를 지원합니다. 기본 제공 단추 상태, 즉 기본값, 가리킴, 누름 및 사용 안 함(드릴스루의 경우)과 결합된 채우기 이미지를 사용하여 단추의 모양과 느낌을 사용자 지정할 수 있습니다.

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-fill-images.png" alt-text="드릴스루 단추 채우기 이미지":::

**채우기** 를 **켜짐** 으로 설정하고 각 상태에 대한 이미지를 만듭니다.

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-fill-state-settings.png" alt-text="채우기 이미지 설정":::


## <a name="next-steps"></a>다음 단계
단추와 유사하거나 상호 작용하는 기능에 대한 자세한 내용은 다음 아티클을 살펴보겠습니다.

* [Power BI 보고서에서 드릴스루 사용](desktop-drillthrough.md)
* [책갈피를 사용하여 Power BI에서 정보 공유 및 스토리 빌드](desktop-bookmarks.md)
* [드릴스루 단추 만들기](desktop-drill-through-buttons.md)

