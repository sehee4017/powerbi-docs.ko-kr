---
title: 비즈니스용 OneDrive 또는 SharePoint Online에 페이지를 매긴 보고서 저장
description: 이 문서에서는 Power Automate를 사용하여 Power BI 페이지를 매긴 보고서를 비즈니스용 OneDrive 또는 SharePoint Online 폴더에 자동으로 저장합니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 11/17/2020
LocalizationGroup: Get started
ms.openlocfilehash: 4a0a504db15d78bec112aaafd2a972f066e88193
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96407679"
---
# <a name="save-a-paginated-report-to-onedrive-for-business-or-sharepoint-online"></a>비즈니스용 OneDrive 또는 SharePoint Online에 페이지를 매긴 보고서 저장

[Power Automate](/power-automate/getting-started)를 사용하면 Power BI 페이지를 매긴 보고서를 지원되는 다양한 형식과 시나리오로 내보내고 배포하는 작업을 자동화할 수 있습니다. 이 문서에서는 Power Automate를 사용하여 Power BI 페이지를 매긴 보고서를 비즈니스용 OneDrive 또는 SharePoint Online 폴더에 자동으로 저장합니다.

:::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/paginated-onedrive-flow.png" alt-text="페이지를 매긴 보고서를 OneDrive 또는 SharePoint Online에 저장하기 위한 Power Automate 흐름의 스크린샷":::

Power BI 페이지를 매긴 보고서용으로 사용할 다른 Power Automate 템플릿을 찾고 있다면 [Power Automate를 사용하여 Power BI 페이지를 매긴 보고서 내보내기](service-automate-paginated-integration.md)를 참조하세요. 

## <a name="prerequisites"></a>필수 조건  

수행하려면 다음이 필요합니다.

- 예약된 용량으로 지원되는 Power BI 테넌트의 작업 영역 하나 이상 이 용량은 A4/P1 ~ A6/P3 SKU 중 하나일 수 있습니다. [Power BI Premium의 예약된 용량](../admin/service-premium-what-is.md)에 대해 자세히 알아보세요.
- Office 365 구독에서 제공되는 Power Automate의 표준 커넥터 액세스 권한

## <a name="save-a-paginated-report-to-onedrive-for-business-or-a-sharepoint-online-folder"></a>비즈니스용 OneDrive 또는 SharePoint Online 폴더에 페이지를 매긴 보고서 저장 

이러한 템플릿 중 하나를 사용하여 비즈니스용 OneDrive 또는 SharePoint Online 폴더에 대해 원하는 형식의 페이지를 매긴 보고서의 반복 내보내기를 설정합니다. Power Automate 흐름에서 페이지를 매긴 보고서에 대한 파일로 내보내기 작업을 처음으로 사용하는 경우 필수 조건을 참조하세요. 

> [!NOTE]
> 다음 단계와 이미지는 **비즈니스용 OneDrive에 Power BI 페이지를 매긴 보고서 저장** 템플릿을 사용하여 흐름을 설정하는 방법을 보여 줍니다. 동일한 단계를 수행하여 **SharePoint Online 폴더에 Power BI 페이지를 매긴 보고서 저장** 템플릿을 사용하여 흐름을 만듭니다. 페이지를 매긴 보고서를 내보낼 위치를 선택할 때 비즈니스용 OneDrive 폴더 대신 SharePoint Online 폴더를 선택합니다. 

1. Power Automate [flow.microsoft.com](https://flow.microsoft.com/)에 로그인합니다. 
1. **템플릿** 을 선택하고  **paginated reports**(페이지를 매긴 보고서)를 검색합니다. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Power BI 페이지를 매긴 보고서용에 대한 Power Automate 템플릿 스크린샷":::

1. **Save a Power BI paginated report to OneDrive for Business**(비즈니스용 OneDrive에 Power BI 페이지를 매긴 보고서 저장) 또는 **Save a Power BI paginated report to a SharePoint Online folder**(SharePoint Online 폴더에 Power BI 페이지를 매긴 보고서 저장)를 선택합니다. Power BI 및 비즈니스용 OneDrive나 SharePoint Online에 로그인했는지 확인합니다.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-step1.png" alt-text="Power BI 및 비즈니스용 OneDrive 템플릿을 선택하는 스크린샷":::
1. **계속** 을 선택합니다.  


1. 흐름에 대해 **되풀이** 설정하려면 **빈도** 에서 옵션을 선택하고 원하는 **간격** 값을 입력합니다.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-2-recurrence.png" alt-text="흐름의 되풀이 선택":::

1. (선택 사항) **고급 옵션 표시** 를 선택하여 **표준 시간대**, **시작 시간**, **요일 선택**, **다음 시간**, **다음 시간(분)** 을 비롯한 추가 **되풀이** 매개 변수를 설정합니다.  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-3-advanced-recurrence.png" alt-text="되풀이의 고급 옵션 표시":::

1. **작업 영역** 상자에서 예약된 용량의 작업 영역을 선택합니다. **보고서** 상자에서 선택한 작업 영역에서 내보낼 페이지를 매긴 보고서를 선택합니다. **내보내기 형식** 상자에서 원하는 내보내기 형식을 선택합니다. 필요에 따라 페이지를 매긴 보고서에 대한 매개 변수를 지정할 수 있습니다. [Power BI Rest API용 커넥터 참조](/connectors/powerbi/#export-to-file-for-paginated-reports)에서 매개 변수에 대한 자세한 설명을 확인하세요.  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-4-export-format.png" alt-text="페이지를 매긴 보고서, 작업 영역, 내보내기 형식 선택":::

1. **폴더 경로** 에서 페이지를 매긴 보고서를 내보낼 비즈니스용 OneDrive 또는 SharePoint Online 폴더를 선택합니다.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-5-create-file.png" alt-text="대상을 선택하고 파일 만들기":::

1. Power Automate에서 **파일 이름** 및 **파일 콘텐츠** 를 자동으로 생성합니다. 파일 이름을 변경할 수 있지만 동적으로 생성된 **파일 콘텐츠** 값은 유지하세요. 

1. 완료되면  **다음 단계** 또는 **저장** 을 선택합니다. Power Automate가 흐름을 생성하고 평가하고 오류를 찾은 경우 알려 줍니다. 

1. 오류가 있는 경우  **흐름 편집** 을 선택하여 수정합니다. 그렇지 않으면 **뒤로** 화살표를 선택하여 흐름 정보를 확인하고 새 흐름을 실행합니다. 

    흐름을 실행하면 Power Automate가 페이지를 매긴 보고서를 지정된 형식으로 비즈니스용 OneDrive 또는 SharePoint Online에 내보냅니다.  

## <a name="next-steps"></a>다음 단계

- [Power Automate를 사용하여 Power BI 페이지를 매긴 보고서 내보내기](service-automate-paginated-integration.md)
- [Power Automate 시작하기](/power-automate/getting-started/)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)
