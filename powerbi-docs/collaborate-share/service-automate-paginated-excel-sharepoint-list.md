---
title: Excel Online 테이블 또는 SharePoint 목록의 각 행에 대해 페이지를 매긴 보고서 내보내기
description: 이 문서에서는 Power Automate를 사용하여 Excel Online 테이블 또는 SharePoint Online 목록의 각 행에 대해 페이지를 매긴 보고서 내보내기를 자동화합니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: 7a48a9a594364de4261aa66de48c1a4262392364
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097849"
---
# <a name="export-a-paginated-report-for-each-row-in-an-excel-online-table-or-sharepoint-list"></a>Excel Online 테이블 또는 SharePoint 목록의 각 행에 대해 페이지를 매긴 보고서 내보내기

[Power Automate](/power-automate/getting-started)를 사용하면 Power BI 페이지를 매긴 보고서를 지원되는 다양한 형식과 시나리오로 내보내고 배포하는 작업을 자동화할 수 있습니다. 이 문서에서는 Power Automate 템플릿을 사용하여 단일 또는 여러 페이지를 매긴 보고서의 되풀이 내보내기 설정을 자동화합니다. Excel Online 테이블 또는 SharePoint Online 목록의 각 행에 대해 원하는 형식으로 내보낼 수 있습니다. 내보낸 페이지를 매긴 보고서를 비즈니스용 OneDrive 또는 SharePoint Online 사이트에 배포하거나 Office 365 Outlook을 통해 메일로 보낼 수 있습니다.

:::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-overview.png" alt-text="Excel Online 테이블을 사용하여 페이지를 매긴 보고서 내보내기":::

Excel Online 테이블 또는 SharePoint Online 목록의 각 행은 페이지를 매긴 보고서를 받는 구독 기반의 단일 사용자를 나타낼 수 있습니다. 또는 각 행은 배포할 페이지를 매긴 고유 보고서를 나타낼 수 있습니다. 테이블 또는 목록에는 OneDrive, SharePoint Online 또는 Outlook 등 보고서를 배포하는 방법을 지정하는 열이 필요합니다. Power Automate 흐름은 이 열을 Switch 문에 사용합니다.

Power BI 페이지를 매긴 보고서용으로 사용할 다른 Power Automate 템플릿을 찾고 있다면 [Power Automate를 사용하여 Power BI 페이지를 매긴 보고서 내보내기](service-automate-paginated-integration.md)를 참조하세요.

## <a name="prerequisites"></a>필수 조건  

수행하려면 다음이 필요합니다.

- 예약된 용량으로 지원되는 Power BI 테넌트의 작업 영역 하나 이상 이 용량은 A4/P1 ~ A6/P3 SKU 중 하나일 수 있습니다. [Power BI Premium의 페이지를 매긴 보고서에 예약된 용량](../admin/service-premium-what-is.md#paginated-reports)에 대해 자세히 알아보세요.
- Office 365 구독에서 제공되는 Power Automate의 표준 커넥터 액세스 권한
- Excel Online 테이블을 사용하는 경우 Excel에서 테이블 형식으로 지정해야 합니다. 방법을 알아보려면 [테이블 만들기](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f)를 참조하세요.

## <a name="export-a-paginated-report-for-each-row-in-a-table-or-list"></a>테이블이나 목록의 각 행에 대해 페이지를 매긴 보고서 내보내기

> [!NOTE]
> 다음 단계와 이미지는 **Excel Online 테이블의 각 행에 대해 Power BI 페이지를 매긴 보고서 내보내기** 템플릿을 사용하여 흐름을 설정하는 방법을 보여 줍니다. 동일한 단계를 수행하여 **SharePoint Online 목록의 항목에 대해 Power BI 페이지를 매긴 보고서 내보내기** 템플릿을 사용하여 흐름을 만듭니다. Excel Online 테이블 대신 SharePoint Online 목록에는 페이지를 매긴 보고서를 내보내는 방법에 대한 정보가 포함됩니다.  

1. Power Automate [flow.microsoft.com](https://flow.microsoft.com/)에 로그인합니다. 
1. **템플릿** 을 선택하고  **paginated reports**(페이지를 매긴 보고서)를 검색합니다. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Power BI 페이지를 매긴 보고서용에 대한 Power Automate 템플릿 스크린샷":::

1. **Export a Power BI paginated report for each row in an Excel Online table**(Excel Online 테이블의 각 행에 대해 Power BI 페이지를 매긴 보고서 내보내기) 또는 **Export a Power BI paginated report for items in a SharePoint Online list**(SharePoint Online 목록의 항목에 대해 Power BI 페이지를 매긴 보고서 내보내기) 템플릿을 선택합니다. Excel Online, Power BI, 비즈니스용 OneDrive, SharePoint Online 및 Office 365 Outlook에 로그인했는지 확인하세요. **계속** 을 선택합니다.  

   :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-excel-online-1.png" alt-text="Excel Online 테이블의 각 행에 대해 Power BI 페이지를 매긴 보고서 내보내기":::

1. 흐름에 대해 **되풀이** 설정하려면 **빈도** 에서 옵션을 선택하고 원하는 **간격** 값을 입력합니다.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-recurrence-2.png" alt-text="흐름에 대해 되풀이 선택":::

1. (선택 사항) **고급 옵션 표시** 를 선택하여 **표준 시간대**, **시작 시간**, **요일 선택**, **다음 시간**, **다음 시간(분)** 을 비롯한 추가 **되풀이** 매개 변수를 설정합니다.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-advanced-recurrence-3.png" alt-text="선택 사항으로 고급 되풀이 옵션 선택":::

1. **위치** 상자에서 Excel Online 테이블 또는 SharePoint Online 목록이 저장된 SharePoint Online 사이트 또는 비즈니스용 OneDrive를 선택합니다. 그런 다음 드롭다운에서 **문서 라이브러리** 를 선택합니다.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-location-4.png" alt-text="Excel Online 테이블의 위치 선택":::

1. **파일** 상자에서 Excel Online 파일 또는 SharePoint Online 목록을 선택합니다. **테이블** 상자의 드롭다운에서 테이블 또는 목록의 이름을 선택합니다. 
 
    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-file-table-5.png" alt-text="Excel Online 파일 및 테이블의 이름 선택":::

    > [!TIP]
    > Excel에서 데이터를 테이블 형식으로 지정하는 방법을 알아보려면 [테이블 만들기](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f)를 참조하세요. 

1. 파일 이름에 사용할 변수를 초기화합니다. **이름** 및 **값** 의 기본값을 유지하거나 수정할 수 있지만 **형식** 은 **문자열** 과 같게 그대로 둡니다.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-name-type-6.png" alt-text="이름 및 값을 입력하고 형식을 문자열과 같게 유지":::

1. **각각에 적용** 에서 **이전 단계에서 출력 선택** 상자가 기본적으로 **값** 으로 설정되어 있습니다. 이 설정은 Excel Online 테이블 또는 SharePoint Online 목록의 각 행에 대한 **각각에 적용** 에 포함된 작업을 반복합니다.  

1. **작업 영역** 상자에서 예약된 용량의 작업 영역을 선택합니다. **보고서** 상자에서 선택한 작업 영역에서 내보낼 페이지를 매긴 보고서를 선택합니다. 드롭다운 목록에서 **사용자 지정 값 입력** 을 설정하는 경우 Excel Online 테이블 또는 SharePoint Online 목록의 열과 같도록 **작업 영역** 및 **보고서** 를 설정할 수 있습니다. 이러한 열은 각각 작업 영역 ID와 보고서 ID를 포함해야 합니다.  

1. 드롭다운 목록에서 **내보내기 형식** 을 선택하거나 원하는 내보내기 형식이 포함된 Excel Online 테이블의 열과 같도록 설정합니다. 예를 들어 PDF, DOCX 또는 PPTX입니다. 필요에 따라 페이지를 매긴 보고서에 대한 매개 변수를 지정할 수 있습니다. [Power BI REST API용 커넥터 참조](/connectors/powerbi/#export-to-file-for-paginated-reports)에서 매개 변수에 대한 자세한 설명을 확인하세요.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-export-format-9.png" alt-text="페이지를 매긴 보고서의 파일로 내보내기 작성":::

1. **값** 상자에서 페이지를 매긴 보고서를 내보낸 후 보고서 이름을 입력합니다. 파일 확장명을 입력해야 합니다. .pdf, .docx 또는 .pptx로 정적으로 설정할 수 있습니다. 또는 Excel 테이블에서 원하는 내보내기 형식에 해당하는 열을 선택하여 동적으로 설정합니다. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-output-value-10.png" alt-text="보고서 이름 및 파일 확장명 선택":::

1. **전환** 작업에서 원하는 전달 방법에 해당하는 Excel Online 테이블의 열을 **On**(설정) 상자에 입력합니다. 예를 들어 **OneDrive**, **SharePoint** 또는 **메일** 입니다. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-switch-11.png" alt-text="전환에서 On(설정) 상자에 Excel Online 테이블의 열 입력":::

1. **사례**, **사례 2**, **사례 3** 에 이전 단계에서 선택한 Excel Online 테이블 열에 있는 값을 입력합니다.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-1-2-3-12.png" alt-text="사례, 사례 2 및 사례 3의 값 입력":::

1. 페이지를 매긴 보고서를 OneDrive에 저장하는 경우에는 저장해야 하는 **폴더 경로** 를 선택합니다.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-onedrive-13.png" alt-text="OneDrive에 저장하는 경우":::

1. 페이지를 매긴 보고서를 SharePoint Online에 저장하는 경우에는 저장해야 하는 **사이트 주소** 및 **폴더 경로** 를 입력합니다. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-sharepoint-14.png" alt-text="페이지를 매긴 보고서를 SharePoint Online에 저장하는 경우":::

1. 페이지를 매긴 보고서를 Outlook을 통해 메일로 보내는 경우에는 **받는 사람**, **제목** 및 **본문** 상자에 입력합니다. 이러한 상자에는 Excel Online 테이블 또는 SharePoint Online 목록의 정적 콘텐츠 또는 동적 콘텐츠가 포함될 수 있습니다. Power Automate는 페이지를 매긴 보고서를 이 메일에 자동으로 첨부합니다.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-email-15.png" alt-text="페이지를 매긴 보고서를 Outlook을 통해 메일로 보내는 경우":::

1. 완료되면  **다음 단계** 또는 **저장** 을 선택합니다. Power Automate가 흐름을 생성하고 평가하고 오류를 찾은 경우 알려 줍니다. 

1. 오류가 있는 경우  **흐름 편집** 을 선택하여 수정합니다. 그렇지 않으면 **뒤로** 화살표를 선택하여 흐름 정보를 확인하고 새 흐름을 실행합니다. 


## <a name="next-steps"></a>다음 단계

- [Power Automate를 사용하여 Power BI 페이지를 매긴 보고서 내보내기](service-automate-paginated-integration.md)
- [Power Automate 시작하기](/power-automate/getting-started/)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)

