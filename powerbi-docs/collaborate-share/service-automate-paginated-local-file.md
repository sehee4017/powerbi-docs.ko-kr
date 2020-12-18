---
title: Power Automate를 사용하여 페이지를 매긴 보고서를 로컬 폴더에 저장
description: 이 문서에서는 템플릿을 사용하여 파일 시스템으로 페이지를 매긴 보고서의 되풀이 내보내기를 원하는 형식으로 설정합니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: a30f0df972c375af4fb284ce3bba5372870d6efb
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098808"
---
# <a name="save-a-power-bi-paginated-report-to-a-local-folder--with-power-automate"></a>Power Automate를 사용하여 Power BI 페이지를 매긴 보고서를 로컬 폴더에 저장

[Power Automate](/power-automate/getting-started)를 사용하면 Power BI 페이지를 매긴 보고서를 지원되는 다양한 형식과 시나리오로 내보내고 배포하는 작업을 자동화할 수 있습니다. 이 문서에서는 템플릿을 사용하여 파일 시스템으로 페이지를 매긴 보고서의 되풀이 내보내기를 원하는 형식으로 설정합니다. Power Automate 흐름에서 페이지를 매긴 보고서에 대한 파일로 내보내기 작업을 처음으로 사용하는 경우 필수 조건을 참조하세요.

:::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-overview.png" alt-text="페이지를 매긴 보고서의 되풀이 내보내기 작업을 설정합니다.":::

Power BI 페이지를 매긴 보고서용으로 사용할 다른 Power Automate 템플릿을 찾고 있다면 [Power Automate를 사용하여 Power BI 페이지를 매긴 보고서 내보내기](service-automate-paginated-integration.md)를 참조하세요.

## <a name="prerequisites"></a>필수 조건  

수행하려면 다음이 필요합니다.

- 예약된 용량으로 지원되는 Power BI 테넌트의 작업 영역 하나 이상 이 용량은 A4/P1 ~ A6/P3 SKU 중 하나일 수 있습니다. [Power BI Premium의 페이지를 매긴 보고서에 예약된 용량](../admin/service-premium-what-is.md#paginated-reports)에 대해 자세히 알아보세요.
- Office 365 구독에서 제공되는 Power Automate의 표준 커넥터 액세스 권한

## <a name="save-a-power-bi-paginated-report-to-a-local-folder"></a>Power BI 페이지를 매긴 보고서를 로컬 폴더에 저장

1. **Power BI 페이지를 매긴 보고서를 로컬 파일 시스템에 저장** 템플릿을 선택합니다. Power BI에 로그인하고 로컬 파일 시스템에 연결되어 있는지 확인합니다. **계속** 을 선택합니다. 

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-save-report-local-file-1.png" alt-text="Power BI 페이지를 매긴 보고서를 로컬 파일 시스템에 저장합니다.":::

2. 파일 시스템에 연결하려면 **새 연결 추가** 를 선택해야 할 수 있습니다. 
1. **연결 이름**, 원하는 **루트 폴더** 에 대한 경로를 입력하고 **사용자 이름** 및 **암호** 를 입력하여 인증합니다. 온-프레미스 데이터 게이트웨이를 사용하는 경우 드롭다운에서 **게이트웨이** 를 선택합니다.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-set-file-system-2.png" alt-text="연결 이름 및 루트 폴더를 입력합니다.":::
 
3. 흐름에 대한 **되풀이** 빈도를 설정하려면 **빈도** 드롭다운에서 옵션을 선택하고 원하는 **간격** 값을 입력합니다.  

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-frequency-3.png" alt-text="흐름의 되풀이 빈도를 설정합니다.":::

4. 필요에 따라 **고급 옵션 표시** 를 선택합니다. **표준 시간대**, **시작 시간**, **요일 선택**, **다음 시간**, **다음 시간(분)** 과 같은 추가 **되풀이** 매개 변수를 설정합니다. 
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-advanced-4.png" alt-text="되풀이의 고급 옵션을 설정합니다.":::

5. **작업 영역** 상자에서 보고서가 있는 예약된 용량의 작업 영역을 선택합니다. **보고서** 상자에서 작업 영역에서 내보낼 페이지를 매긴 보고서를 선택합니다. **내보내기 형식** 상자에서 원하는 내보내기 형식을 선택합니다. 필요에 따라 페이지를 매긴 보고서에 대한 매개 변수를 지정할 수 있습니다. [Power BI REST API용 커넥터 참조](/connectors/powerbi/#export-to-file-for-paginated-reports)에서 매개 변수에 대한 자세한 설명을 확인하세요.  
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-select-workspace-report-5.png" alt-text="작업 영역 및 보고서를 선택합니다.":::

6. **파일 만들기** 대화 상자에서, **폴더 경로** 에서 페이지를 매긴 보고서를 내보낼 폴더를 선택합니다.
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-create-file-6.png" alt-text="페이지를 매긴 보고서를 내보낼 폴더를 선택합니다.":::

7. Power Automate에서 **파일 이름** 및 **파일 콘텐츠** 를 자동으로 생성합니다. **파일 이름** 을 수정할 수 있지만 동적으로 생성된 **파일 콘텐츠** 값은 유지하세요.
8. 완료되면 **다음 단계** 또는 **저장** 을 선택합니다. Power Automate가 흐름을 만들고 평가합니다.
9. Power Automate에서 오류를 발견한 경우 **흐름 편집** 을 선택하여 수정합니다. 그렇지 않으면 뒤로 화살표를 선택하여 흐름 세부 정보를 확인하고 새 흐름을 실행합니다.
10. 흐름을 실행하면 Power Automate가 페이지를 매긴 보고서를 지정된 형식으로 파일 시스템의 선택한 폴더에 내보냅니다.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-exported-10.png" alt-text="Power Automate는 페이지를 매긴 보고서를 지정된 형식으로 내보냅니다.":::

## <a name="next-steps"></a>다음 단계

- [Power Automate를 사용하여 Power BI 페이지를 매긴 보고서 내보내기](service-automate-paginated-integration.md)
- [Power Automate 시작하기](/power-automate/getting-started/)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)

