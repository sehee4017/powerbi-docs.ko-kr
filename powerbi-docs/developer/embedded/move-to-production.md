---
title: Power BI Embedded 애플리케이션을 프로덕션 환경으로 이동
description: Power BI 애플리케이션을 프로덕션 환경으로 이동하는 데 필요한 단계를 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 6132066f9b724cf5658d3e66ccb835bb23b93d39
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96907757"
---
# <a name="move-your-embedded-app-to-production"></a>포함된 앱을 프로덕션 환경으로 이동

애플리케이션 개발을 완료한 후에 프로덕션 환경으로 이동하려면 용량으로 작업 영역을 백업해야 합니다.

> [!Important]
> 모든 작업 영역(보고서 또는 대시보드가 포함된 작업 영역과 데이터 세트가 포함된 작업 영역)을 용량에 할당해야 합니다.

## <a name="create-a-capacity"></a>용량 만들기

용량을 만들면 고객을 위한 리소스의 혜택을 활용할 수 있습니다. 다음과 같은 두 가지 유형의 용량 중에서 선택할 수 있습니다.

* **Power BI Premium** - *EM* 및 *P* 의 두 SKU 제품군에서 사용할 수 있는 테넌트 수준 Microsoft 356 구독입니다. Power BI 콘텐츠를 포함하는 경우 이 솔루션을 *‘Power BI 포함’* 이라고 합니다. 이 구독과 관련된 자세한 내용은 [Power BI Premium이란?](../../admin/service-premium-what-is.md)을 참조하세요.

* **Azure Power BI Embedded** - [Microsoft Azure Portal](https://portal.azure.com)에서 용량을 구입할 수 있습니다. 이 구독은 *A* SKU를 사용합니다. Power BI Embedded 용량을 만드는 방법에 대한 자세한 내용은 [Azure Portal에서 Power BI Embedded 용량 만들기](azure-pbie-create-capacity.md)를 참조하세요.

    > [!NOTE]
    > A SKU에서는 무료 Power BI 라이선스를 사용하여 Power BI 콘텐츠에 액세스할 수 없습니다.

### <a name="capacity-specifications"></a>용량 사양

아래 표에서는 각 SKU의 리소스 및 한도를 설명합니다. 요구 사항에 가장 적합한 용량을 확인하려면 [내 시나리오를 위해 구입해야 하는 SKU](./embedded-faq.md#which-solution-should-i-choose) 표를 참조하세요.

| 용량 노드 | 총 V 코어 | 백 엔드 V 코어 | RAM(GB) | 프런트 엔드 V 코어 | DirectQuery/Live Connection(초당) | 모델 새로 고침 병렬 처리 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

## <a name="development-testing"></a>개발 테스트

개발 테스트를 위해 Pro 라이선스에 평가판 포함 토큰을 사용할 수 있습니다. 프로덕션 환경에 포함하려면 용량을 사용합니다.

Power BI ‘서비스 주체’ 계정 또는 ‘마스터 사용자’(마스터 계정)가 생성할 수 있는 평가판 포함 토큰의 수는 제한됩니다.  [사용 가능한 기능](/rest/api/power-bi/availablefeatures/getavailablefeatures) API를 사용하여 현재 포함된 사용의 비율을 확인합니다. 사용량은 서비스 주체 계정 또는 마스터 계정별로 표시됩니다.

테스트하는 중에 포함 토큰이 부족해지는 경우 Power BI Embedded 또는 Premium [용량](embedded-capacity.md)을 구매해야 합니다. 용량으로 생성할 수 있는 포함 토큰 수에는 제한이 없습니다.

## <a name="assign-a-workspace-to-a-capacity"></a>용량에 작업 영역 할당

용량을 만들면 해당 용량에 작업 영역을 할당할 수 있습니다.

포함된 콘텐츠(데이터 세트, 보고서, 대시보드 포함)와 관련된 Power BI 리소스를 포함하는 모든 작업 영역을 용량에 할당해야 합니다. 예를 들어 포함된 보고서 및 보고서에 바인딩된 데이터 세트가 서로 다른 작업 영역에 있을 경우 두 작업 영역을 모두 용량에 할당해야 합니다.

### <a name="assign-a-workspace-to-a-capacity-using-a-service-principal"></a>서비스 주체를 사용하여 용량에 작업 영역 할당

[서비스 주체](embed-service-principal.md)를 사용하여 작업 영역에 용량을 할당하려면 [Power BI REST API](/rest/api/power-bi/capacities/groups_assigntocapacity)를 사용합니다. Power BI REST API를 사용할 때는 [서비스 주체 개체 ID](embed-service-principal.md)를 사용해야 합니다.

### <a name="assign-a-workspace-to-a-capacity-using-a-master-user"></a>마스터 사용자를 사용하여 용량에 작업 영역 할당

아래 단계에 따라 **마스터 사용자** 를 사용하여 작업 영역에 용량을 할당합니다.

1. **Power BI 서비스** 에서 작업 영역을 열고 

1. **Power BI 서비스** 내에서 작업 영역을 확장하고 콘텐츠를 포함하는 데 사용하는 작업 영역에 대한 줄임표를 선택합니다. 그런 다음, **작업 영역 편집** 을 선택합니다.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/workspace-settings.png" alt-text="Power BI 서비스 포털의 작업 영역 설정 메뉴를 보여 주는 스크린샷":::

2. **Premium** 탭을 선택하고 다음을 수행합니다.

    * **용량** 을 사용하도록 설정합니다.

    * 만든 용량을 선택합니다.

    * **저장** 을 선택합니다.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-tab.png" alt-text="Power BI 서비스 포털의 작업 영역 프리미엄 설정 메뉴를 보여 주는 스크린샷":::

    용량에 작업 영역을 할당하면 해당 작업 영역 옆에 다이아몬드가 표시됩니다. 

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-workspace.png" alt-text="Power BI 서비스 포털에서 프리미엄 용량이 있는 작업 영역 옆에 있는 다이아몬드를 보여 주는 스크린샷":::

## <a name="next-steps"></a>다음 단계

>[!div class="nextstepaction"]
>[Power BI Embedded 분석의 용량 및 SKU](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Power BI Embedded 분석의 용량 계획](embedded-capacity-planning.md)

>[!div class="nextstepaction"]
>[embed 토큰 생성 시 고려 사항](generate-embed-token.md)