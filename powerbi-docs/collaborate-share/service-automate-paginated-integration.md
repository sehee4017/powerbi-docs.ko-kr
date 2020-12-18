---
title: Power Automate를 사용하여 페이지가 매겨진 보고서 내보내기
description: Power BI 페이지를 매긴 보고서를 내보내는 Power Automate 흐름을 만드는 방법을 알아봅니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/14/2020
LocalizationGroup: Get started
ms.openlocfilehash: 5c69abe925751e8b065f262e151bfee65c487238
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97492061"
---
# <a name="export-power-bi-paginated-reports-with-power-automate"></a>Power Automate를 사용하여 Power BI 페이지를 매긴 보고서 내보내기

[Power Automate](/power-automate/getting-started)를 사용하면 Power BI 페이지를 매긴 보고서를 지원되는 다양한 형식과 시나리오로 내보내고 배포하는 작업을 자동화할 수 있습니다. 이 문서에서는 페이지를 매긴 보고서를 내보내는 데 사용할 고유한 흐름을 만드는 데 사용할 템플릿을 알아봅니다.  

## <a name="prerequisites"></a>필수 조건  

수행하려면 다음이 필요합니다.

- 예약된 용량으로 지원되는 Power BI 테넌트의 작업 영역 하나 이상 이 용량은 A4/P1 ~ A6/P3 SKU 중 하나일 수 있습니다. [Power BI Premium의 예약된 용량](../admin/service-premium-what-is.md)에 대해 자세히 알아보세요.
- Office 365 구독에서 제공되는 Power Automate의 표준 커넥터 액세스 권한

## <a name="create-a-flow-from-a-template"></a>템플릿에서 흐름 만들기 

1. Power Automate [flow.microsoft.com](https://flow.microsoft.com/)에 로그인합니다. 
1. **템플릿** 을 선택하고  **paginated reports**(페이지를 매긴 보고서)를 검색합니다. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Power BI 페이지를 매긴 보고서용에 대한 Power Automate 템플릿 스크린샷":::

## <a name="select-a-template"></a>템플릿 선택 

목록에서 템플릿을 선택하여 단계별 연습을 시작합니다.  

- [비즈니스용 OneDrive 또는 SharePoint Online 폴더에 Power BI 페이지를 매긴 보고서를 저장](service-automate-paginated-onedrive-sharepoint.md)합니다.  
- [SharePoint Online 목록의 항목 또는 Excel Online 테이블의 각 행에 대해 Power BI 페이지를 매긴 보고서를 내보냅니다](service-automate-paginated-excel-sharepoint-list.md).
- [Power BI 페이지를 매긴 보고서를 로컬 시스템 폴더에 저장](service-automate-paginated-local-file.md)합니다.

## <a name="next-steps"></a>다음 단계

- [페이지를 매긴 보고서에 대한 Power BI 내보내기 API](../developer/embedded/export-paginated-report.md)
- [Power Automate 시작하기](/power-automate/getting-started/)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)
