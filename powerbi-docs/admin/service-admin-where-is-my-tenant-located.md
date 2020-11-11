---
title: 내 Power BI 테넌트는 어디에 있습니까?
description: Power BI 테넌트의 위치와 해당 위치를 선택하는 방법에 대해 알아보세요. 서비스에 대한 상호 작용에 영향을 줄 수 있으므로 이를 알아두는 것이 중요합니다.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 268594b54186ca319eca6a7577dcfaa17c066fd4
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916110"
---
# <a name="where-is-my-power-bi-tenant-located"></a>내 Power BI 테넌트는 어디에 있습니까?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Power BI 테넌트의 위치와 해당 위치를 선택하는 방법에 대해 알아보세요. 서비스에 대한 상호 작용에 영향을 줄 수 있으므로 위치를 알아두는 것이 중요합니다.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Power BI 테넌트 위치를 확인하는 방법

테넌트가 있는 지역을 찾으려면 다음 단계를 수행합니다.

1. Power BI 서비스의 맨 위 메뉴에서 도움말( **?** )을 선택한 후 **Power BI 정보** 를 선택합니다.

1. **데이터 저장 위치** 옆에 있는 값을 확인합니다. 테넌트가 위치한 지역입니다. 작업 영역의 다른 영역에서 용량을 사용하지 않는 한, 이 값은 데이터가 저장되는 영역이기도 합니다.

    ![데이터 영역](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>데이터 영역을 선택하는 방법

데이터 영역은 테넌트를 만들 때 선택한 국가/지역에 따라 다릅니다. 이 정보를 공유하기 때문에 Microsoft 365 및 Power BI 모두에 등록하는 데 선택 사항이 적용됩니다. 새 테넌트인 경우 가입할 때 목록에서 해당 국가/지역을 선택합니다.

![국가 선택](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI는 테넌트에 대한 데이터가 저장되는 위치를 결정하는 이 선택 항목에 가장 가까운 데이터 영역을 선택합니다.

> [!IMPORTANT]
> 테넌트를 만든 후에는 이 선택 사항을 변경할 수 없습니다.

궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)
