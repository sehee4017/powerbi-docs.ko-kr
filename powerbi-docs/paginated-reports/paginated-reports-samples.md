---
title: Power BI 페이지를 매긴 보고서 샘플
description: 이 문서에서는 Power BI 페이지를 매긴 보고서 샘플을 다운로드하고 사용하는 방법에 대해 알아봅니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/10/2020
ms.openlocfilehash: cfa4b46e521079802ec87b63d6323e01213625c3
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483868"
---
# <a name="sample-power-bi-paginated-reports"></a>Power BI 페이지를 매긴 보고서 샘플


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

이 문서에서는 다운로드하여 살펴볼 수 있는 여러 가지 Power BI 페이지를 매긴 보고서 샘플에 대한 정보 및 링크를 제공합니다. 페이지를 매긴 보고서를 사용하는 일반적인 방법을 보여 줍니다.

## <a name="prerequisites"></a>필수 조건

- 이러한 보고서는 편집하지 않고 온라인으로 공유할 수 있습니다. 이렇게 하려면 Power BI Pro 라이선스가 필요합니다. [Power BI Pro 라이선스 평가판](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro)에 가입합니다.
- [프리미엄 용량](../admin/service-premium-what-is.md)의 Power BI 작업 영역에 대한 액세스 권한도 필요합니다.
- 이러한 보고서를 편집하려면 Microsoft 다운로드 센터에서 [Power BI Report Builder를 설치](https://aka.ms/pbireportbuilder)해야 합니다.
- 이제 GitHub에서 페이지를 매긴 보고서 샘플을 다운로드할 수 있습니다. GitHub 계정이 필요하지는 않습니다. 

## <a name="download-the-reports"></a>보고서 다운로드

보고서를 성공적으로 다운로드하려면 리포지토리를 zip 파일로 다운로드한 다음 압축을 풀어야 합니다. 페이지를 매긴 보고서는 .rdl 파일입니다.

1. [Reporting Services GitHub 리포지토리](https://github.com/microsoft/Reporting-Services)를 엽니다.
1. 녹색 **Code** 단추 > **ZIP 다운로드** 를 선택합니다.

    :::image type="content" source="media/paginated-reports-samples/paginated-report-download-zip.png" alt-text="Power BI 페이지 매긴 보고서 샘플이 포함된 GitHub 리포지토리의 스크린샷":::
    
1. 파일을 열고 **모두 추출** 을 선택하고 파일의 위치를 선택합니다. 기본적으로 폴더 이름은 **Reporting-Services-master** 가 됩니다.
1. **Reporting-Services-master** 폴더를 연 다음 **PaginatedReportSamples** 폴더를 엽니다.

    >[!NOTE]
    >**Reporting-Services-master** 폴더에 있는 다른 폴더를 모두 삭제할 수 있습니다. 필요하지 않은 다른 샘플이 포함되어 있습니다.

1. .rdl 파일 중 하나를 선택하여 Power BI Report Builder에서 엽니다.
1. 이제 [페이지를 매긴 보고서를 Power BI 서비스에 게시](paginated-reports-save-to-power-bi-service.md)할 수 있습니다.

## <a name="invoice"></a>송장

:::image type="content" source="media/paginated-reports-samples/paginated-report-invoice.png" alt-text="Power BI 페이지를 매긴 보고서 샘플 청구서 스크린샷":::


이 페이지를 매긴 보고서는 자체 포함 청구서입니다. 이 보고서 시나리오에서는 픽셀을 완벽하게 인쇄할 수 있는 청구서를 만들려고 합니다. 송장에는 품목 설명, 수량, 할인 및 비용을 나열하는 세부 정보를 포함하여 총 판매액이 표시되어야 합니다.

이 샘플에는 다음과 같이 실제 청구서를 만들기 위한 고유한 특징이 강조 표시되어 있습니다.  

- 테이블릭스(테이블 및 행렬 기반의 데이터 영역). 동적으로 생성된 사용자별 콘텐츠 및 테마를 표시합니다.
- 보고서 본문 테이블릭스의 각 행에 배치되는 사각형 데이터 영역.
- 텍스트 상자 및 줄과 같은 보고서 항목.
- 콘텐츠를 동적으로 선택할 수 있는 보고서 매개 변수. 표시되는 콘텐츠는 식 자리 표시자를 사용하여 특정 주제에 적용됩니다. 

데이터 원본: .rdl 파일에 포함됨

## <a name="labels"></a>레이블

:::image type="content" source="media/paginated-reports-samples/paginated-report-labels.png" alt-text="페이지를 매긴 보고서 레이블 스크린샷":::

자체 포함된 페이지를 매긴 보고서 샘플입니다. 이 보고서는 우편물 레이블 템플릿의 인쇄 레이아웃에 맞게 완벽하게 크기가 조정되는 여러 열 보고서입니다. 

레이블 보고서는 간단하지만 페이지를 매긴 레이블을 만들 때는 다음과 같은 몇 가지 고유한 특징이 있습니다.

- 열 간격이 정의된 고정 열 개수가 세 개인 테이블릭스.
- 인쇄된 페이지의 행과 열에서 반복되는 사각형 데이터 영역.
- 각 사각형 데이터 영역에 표시할 콘텐츠를 선택할 수 있는 보고서 매개 변수.

데이터 원본: .rdl에 포함됨

## <a name="mailing-letter"></a>편지

:::image type="content" source="media/paginated-reports-samples/paginated-report-letter.png" alt-text="Power BI 페이지를 매긴 보고서 샘플 편지 스크린샷":::

이 자체 포함된 페이지를 매긴 보고서 샘플은 실제 편지를 작성하기 위해 설계되었습니다. 이 보고서 시나리오에서는 픽셀을 완벽하게 인쇄할 수 있고 동적 콘텐츠가 포함된 편지를 만들려고 합니다.

이 샘플에는 다음과 같은 고유한 특징이 있습니다. 

- 사각형 데이터 영역은 보고서 본문의 여러 섹션에 배치됩니다. 
- 편지를 개인 설정하는 이미지. 
- 테이블릭스 데이터 영역(테이블 및 행렬 기반의 데이터 영역). 테이블릭스에는 동적으로 생성된 사용자별 콘텐츠가 표시됩니다.
- 텍스트 상자 및 줄과 같은 보고서 항목.
- 콘텐츠를 동적으로 선택할 수 있는 보고서 매개 변수. 표시되는 콘텐츠는 식 자리 표시자를 사용하여 특정 주제에 적용됩니다. 

데이터 원본: .rdl에 포함됨

## <a name="transcript"></a>대본

:::image type="content" source="media/paginated-reports-samples/paginated-report-transcript.png" alt-text="Power BI 페이지를 매긴 보고서 샘플 대본 스크린샷":::

이 보고서 시나리오에서는 픽셀을 완벽하게 인쇄할 수 있는 대본을 만들려고 합니다. 각 학생에 대해 프로그램 설명 세부 정보 및 날짜를 나열하는 동적 콘텐츠를 포함해야 합니다.

이 자체 포함된 페이지를 매긴 보고서 샘플에는 다음과 같은 고유한 특징이 있습니다. 

- 테이블릭스 데이터 영역(테이블 및 행렬 기반의 데이터 영역). 테이블릭스에는 중첩된 행 그룹을 사용하여 동적으로 생성된 사용자별 콘텐츠가 표시됩니다.
- 사각형 데이터 영역은 보고서 본문의 여러 섹션에 배치됩니다.
- 텍스트 상자 및 줄과 같은 보고서 항목.

데이터 원본: .rdl에 포함됨

## <a name="sales-performance"></a>영업 성과

:::image type="content" source="media/paginated-reports-samples/paginated-report-sales-performance.png" alt-text="영업 성과에 대한 Power BI 페이지를 매긴 보고서 샘플 스크린샷":::

Country Sales Performance는 자체 포함된 페이지를 매긴 보고서 샘플입니다. 이 보고서 시나리오에서는 픽셀을 완벽하게 인쇄할 수 있는 청구서를 만들어 총 판매액과 세부 정보를 표시하려고 합니다. 이 샘플에서는 다음과 같은 기능을 보여 줍니다.

- 매개 변수를 사용하여 테이블의 세부 정보 확장.
- 머리글 및 바닥글.
- 식 자리 표시자를 사용하는 텍스트 상자, 줄, 사각형과 같은 보고서 항목.
- 데이터 막대.
- 추세선.
- 계기 패널.

데이터 원본: .rdl에 포함됨
  
## <a name="next-steps"></a>다음 단계

[Power BI 서비스에서 페이지를 매긴 보고서 보기](../consumer/paginated-reports-view-power-bi-service.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)
