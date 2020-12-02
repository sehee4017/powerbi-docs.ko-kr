---
title: Power BI 보고서의 설정 변경
description: Power BI 서비스에서 보고서 설정 변경
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: dbb173c65ecfc5d1ca464387ed43ae615cdcbca1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396179"
---
# <a name="change-settings-for-power-bi-reports"></a>Power BI 보고서의 설정 변경

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Power BI Desktop 및 Power BI 서비스의 보고서 설정을 사용하여 보고서 읽기 권한자가 보고서를 조작하는 방법을 제어할 수 있습니다. 예를 들어 보고서에 대한 필터를 저장하거나, 보고서의 시각적 개체를 맞춤 설정하거나, 보고서 페이지를 측면이 아닌 보고서 아래쪽의 탭으로 표시하도록 할 수 있습니다.

:::image type="content" source="media/power-bi-report-settings/service-report-settings-pane.png" alt-text="Power BI 서비스의 보고서 설정 창 스크린샷":::

먼저 다음 문서를 읽어 보면 도움이 될 수 있습니다.

- [데이터 세트를 가져와 Power BI 서비스에서 보고서 만들기](service-report-create-new.md) - 보고서 작성 환경을 이해합니다.
- [Power BI의 보고서](../consumer/end-user-reports.md) - 보고서 읽기 권한자의 환경을 이해합니다.

 그럼 시작하겠습니다.

## <a name="prerequisites"></a>필수 조건

- Power BI Desktop을 사용하여 보고서를 만드는 경우 [Desktop 보고서 보기](desktop-report-view.md)를 참조하세요.
- [Power BI 서비스에 등록](../fundamentals/service-self-service-signup-for-power-bi.md)합니다. 
- Power BI 서비스의 보고서에 대한 편집 권한이 있어야 합니다. 권한에 대한 자세한 내용은 [새 작업 영역의 역할](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)을 참조하세요.
- Power BI 서비스에 보고서가 아직 없는 경우 대시보드, 보고서 및 데이터 세트를 포함하는 [샘플 콘텐츠 팩을 설치](sample-datasets.md#install-built-in-content-packs)할 수 있습니다.

## <a name="open-the-settings-pane-in-power-bi-desktop"></a>Power BI Desktop에서 설정 창 열기

1. **파일** > **옵션 및 설정** > **옵션** 을 선택합니다.
1. **현재 파일** 에서 **보고서 설정** 을 선택합니다.

    :::image type="content" source="media/power-bi-report-settings/desktop-report-settings-pane.png" alt-text="Power BI Desktop의 보고서 설정 창 스크린샷":::

    이 문서의 나머지 부분에서는 특정 보고서 설정 중 일부를 살펴봅니다.

## <a name="open-the-settings-pane-in-the-power-bi-service"></a>Power BI 서비스에서 설정 창 열기

1. 보고서 읽기용 보기에서 **파일** > **설정** 을 선택합니다.

    :::image type="content" source="media/power-bi-report-settings/service-report-file-settings.png" alt-text="파일 메뉴의 설정 스크린샷":::

1. **설정** 창에는 이 보고서에 대해서만 설정할 수 있는 여러 가지 토글이 표시됩니다. 이 문서의 나머지 부분에서는 그중 일부를 살펴봅니다.

## <a name="set-featured-content"></a>추천 콘텐츠 설정

대시보드, 보고서 및 앱이 동료 Power BI 홈페이지의 추천 섹션에 표시되도록 추천할 수 있습니다. [콘텐츠 추천 방법](../collaborate-share/service-featured-content.md)에 대해 자세히 알아보세요.

## <a name="set-the-pages-pane"></a>페이지 창 설정

현재 Power BI 서비스에서만 페이지 창 설정을 변경할 수 있습니다. **페이지 창** 을 설정하면 읽기용 보기 보고서의 측면이 아닌 아래쪽으로 보고서 페이지 탭이 보고서 읽기 권한자에게 표시됩니다. 편집 보기에서 보고서 페이지 탭은 이미 보고서의 아래쪽에 있습니다.

:::image type="content" source="media/power-bi-report-settings/report-settings-pages-pane.png" alt-text="페이지 창 설정의 스크린샷":::

## <a name="control-filters"></a>제어 필터

보고서 **설정** 창에는 보고서에서 필터를 사용하여 읽기 권한자 조작을 제어하는 세 가지 설정이 있습니다. 각 설정에 대한 자세한 내용을 보려면 다음 링크를 통해 [Power BI 보고서에서 필터 디자인](power-bi-report-filter.md) 문서로 이동합니다.

- **영구 필터** 를 통해 읽기 권한자는 [보고서에서 필터를 저장](power-bi-report-filter.md#allow-saving-filters)할 수 있습니다.
- **필터링 환경** 에는 두 가지 추가 설정이 있습니다.
    
    보고서 읽기 권한자가 [필터 형식을 변경](power-bi-report-filter.md#restrict-changes-to-filter-type)하도록 허용합니다.

    [필터 창에서 검색을 사용](power-bi-report-filter.md#filters-pane-search)하도록 설정합니다.

## <a name="export-data"></a>데이터 내보내기

기본적으로 [보고서 읽기 권한자는 보고서의 시각적 개체에서 요약된 데이터나 기본 데이터를 내보낼](../consumer/end-user-export.md) 수 있습니다. **데이터 내보내기** 를 사용하여 요약된 데이터만 내보내도록 하거나 보고서에서 데이터를 내보내지 않도록 할 수 있습니다.

## <a name="personalize-visuals"></a>시각적 개체 개인 설정

읽기 권한자가 보고서에서 시각적 개체를 변경하고 맞춤 설정할 수 있도록 합니다. [보고서 읽기 권한자가 시각적 개체를 맞춤 설정하도록 하는 방법](power-bi-personalize-visuals.md)에 대해 자세히 알아보세요.

## <a name="next-steps"></a>다음 단계

* [다른 사용자의 홈페이지 콘텐츠 추천](../collaborate-share/service-featured-content.md)
* [보고서 읽기 권한자가 보고서에서 시각적 개체를 맞춤 설정하도록 허용](power-bi-personalize-visuals.md)
* 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)
