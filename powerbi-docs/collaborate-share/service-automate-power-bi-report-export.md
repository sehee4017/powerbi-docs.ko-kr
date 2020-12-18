---
title: Power Automate를 사용하여 보고서 내보내기 및 이메일로 보내기
description: 이 문서에서는 Power Automate를 사용하여 지원되는 다양한 형식 및 시나리오로 Power BI 보고서의 내보내기 및 배포를 자동화합니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Get started
ms.openlocfilehash: 45bccbefc6e499375d33aa049ead8a6c6e47bc8c
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098828"
---
# <a name="export-and-email-a-power-bi-report-with-power-automate"></a>Power Automate를 사용하여 Power BI 보고서 내보내기 및 이메일로 보내기

[Power Automate](/power-automate/getting-started)를 사용하면 Power BI 보고서를 다양한 형식과 시나리오로 내보내고 배포하는 작업을 자동화할 수 있습니다. 이 문서에서는 처음부터 자체 흐름을 만듭니다. Power BI 보고서용 파일로 내보내기 작업을 사용하여 이메일을 통해 Power BI 보고서를 자동으로 배포합니다.

:::image type="content" source="media/service-automate-power-bi-report-export/automate-power-bi-report-overview.png" alt-text="보고서를 내보내고 이메일로 보내는 Power Automate 단계.":::

## <a name="prerequisites"></a>필수 조건  

수행하려면 다음이 필요합니다.

- 예약된 용량으로 지원되는 Power BI 테넌트의 작업 영역 하나 이상 이 용량은 A1/EM1~A6/P3 SKU 중 하나일 수 있습니다. [Power BI Premium의 예약된 용량](../admin/service-premium-what-is.md)에 대해 자세히 알아보세요.
- Office 365 구독에서 제공되는 Power Automate의 표준 커넥터 액세스 권한

## <a name="create-a-flow-from-scratch"></a>처음부터 흐름 만들기 

이 작업에서는 처음부터 간단한 흐름을 만듭니다. 흐름은 Power BI 보고서를 PDF로 내보내고 이메일에 첨부하여 일주일 간격으로 보냅니다.  

1. Power Automate(flow.microsoft.com)에 로그인합니다.
2. **만들기** > **예약된 흐름** 을 선택합니다. 

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-scheduled-flow-2.png" alt-text="Power Automate에서 예약된 흐름을 만듭니다.":::

3. **예약된 흐름 빌드** 에서 흐름 이름을 지정합니다. 
4. **이 흐름 실행** 에서 흐름의 시작 날짜 및 시간과 되풀이 빈도를 선택합니다.
5. **요일 선택** 에서 흐름을 실행할 요일을 선택하고 **만들기** 를 선택합니다.

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-build-flow-5.png" alt-text="Power Automate에서 흐름을 예약합니다.":::

6. **되풀이** 에서 **고급 옵션 표시** 를 선택하고 **다음 시간** 및 **다음 시간(분)** 에 값을 입력하여 흐름이 실행될 특정 시간을 설정합니다.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-recurrence-6.png" alt-text="Power Automate에서 되풀이를 설정합니다.":::

7. **새 단계** 를 선택합니다.
8. **작업 선택** 에서 **Power BI** 를 검색하고 **Power BI 보고서용 파일로 내보내기** 를 선택합니다.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-choose-action-8.png" alt-text="Power Automate에서 작업을 선택합니다.":::

9. **Power BI 보고서용 파일로 내보내기** 에서 드롭다운에 있는 **작업 영역** 및 **보고서** 를 선택합니다.
10. Power BI 보고서에 대해 원하는 **내보내기 형식** 을 선택합니다.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-export-file-10.png" alt-text="Power Automate에서 내보내기 형식을 선택합니다.":::

11. 필요에 따라 **페이지 pageName -1** 필드에서 내보낼 특정 페이지를 표시합니다. 페이지 이름 매개 변수는 표시 페이지 이름과 다릅니다. Power BI 서비스의 페이지로 이동하고 URL의 마지막 부분을 복사하여 페이지 이름을 찾습니다.
 
     :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-copy-url-11.png" alt-text="URL에서 창 이름을 선택합니다.":::

12. 필요에 따라 **페이지 책갈피 이름** 필드에 표시할 특정 책갈피를 나타냅니다. 페이지 이름 매개 변수와 마찬가지로 보고서 URL에서 책갈피 이름 매개 변수를 찾습니다. Power BI 보고서에 대한 추가 매개 변수를 지정할 수 있습니다. [Power BI REST API용 커넥터 참조](/connectors/powerbi/#export-to-file-for-power-bi-reports)에서 이러한 매개 변수에 대한 자세한 설명을 확인하세요.

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-bookmark-url-12.png" alt-text="URL에서 책갈피 이름을 선택합니다.":::

13. **새 단계** 를 선택합니다.
14. **작업 선택** 에서 **Outlook** 을 검색하고 **이메일 보내기(V2)** 를 선택합니다.
15. **이메일 보내기(V2)** 에서 이메일의 **받는 사람**, **제목** 및 **본문** 필드를 작성합니다.
16. **고급 옵션 표시** 를 선택합니다. **첨부 파일 이름 – 1** 에 첨부 파일의 이름을 입력합니다. 파일 이름에 원하는 **내보내기 형식** 과 일치하는 파일 확장명(예: .PDF)을 추가합니다.
17. **첨부 파일 콘텐츠** 에서 **파일 콘텐츠** 를 선택하여 내보낸 Power BI 보고서를 첨부합니다.  
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-send-email-17.png" alt-text="이메일로 내보낸 보고서를 선택합니다.":::

18. 완료되면 **다음 단계** 또는 **저장** 을 선택합니다. Power Automate가 흐름을 생성하고 평가하고 오류를 찾은 경우 알려 줍니다.
1. 오류가 있는 경우  **흐름 편집** 을 선택하여 수정합니다. 그렇지 않으면 **뒤로** 화살표를 선택하여 흐름 세부 정보를 확인하고 새 흐름을 실행합니다.
    흐름을 실행하면 Power Automate는 지정된 형식으로 Power BI 보고서를 내보내고 예약된 대로 이메일 첨부 파일로 보냅니다.  

## <a name="next-steps"></a>다음 단계

- [Power Automate와 Power BI 데이터 경고 통합](service-flow-integration.md)
- [Power Automate 시작하기](/power-automate/getting-started/)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)
