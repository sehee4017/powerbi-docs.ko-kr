---
title: Power BI Premium의 페이지를 매긴 보고서란?
description: 이제 Power BI 서비스에서 페이지를 매긴 보고서를 사용할 수 있습니다. 이러한 보고서는 SQL Server Reporting Services에서 오랫동안 표준이었습니다. 이러한 보고서를 인쇄 또는 공유할 수 있습니다. 보고서 레이아웃을 정확하게 제어할 수 있습니다. 이러한 보고서에는 테이블이 여러 페이지에 걸쳐 있는 경우에도 테이블의 모든 데이터가 표시됩니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: jXTiYJKw1Rs
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 10/16/2020
ms.openlocfilehash: 2c136f4d81a9cb1c1904c3a06b58271391c76c23
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297760"
---
# <a name="what-are-paginated-reports-in-power-bi-premium"></a>Power BI Premium의 페이지를 매긴 보고서란?

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

페이지를 매긴 보고서는 인쇄 또는 공유하도록 디자인된 보고서입니다. 이러한 보고서가 페이지를 매긴 보고서로 불리는 이유는 페이지에 적합하게 형식 지정되어 있기 때문입니다. 이러한 보고서에는 테이블이 여러 페이지에 걸쳐 있는 경우에도 테이블의 모든 데이터가 표시됩니다. 보고서 페이지 레이아웃을 정확하게 제어할 수 있기 때문에 *pixel perfect* 라고도 합니다. Power BI Report Builder는 Power BI 서비스를 위해 페이지를 매긴 보고서를 작성하기 위한 독립 실행형 도구입니다. 

다음은 시작할 준비가 된 경우 유용한 몇 가지 빠른 링크입니다.

- [Microsoft 다운로드 센터에서 Power BI 보고서 작성기 설치](https://aka.ms/pbireportbuilder)
- [자습서: 페이지를 매긴 보고서 만들기](paginated-reports-quickstart-aw.md)
- [Power BI 페이지를 매긴 보고서 샘플](paginated-reports-samples.md)
- Power BI Report Server용 Report Builder 또는 SQL Server Reporting Services에 대한 정보를 찾고 있나요? [Report Builder 설치 - Power BI Report Server](../report-server/install-report-builder.md)를 참조하세요.

페이지를 매긴 보고서에는 흔히 여러 페이지가 있습니다. 예를 들어 이 보고서에는 563페이지가 있습니다. 각 페이지는 청구서당 한 페이지가 정확하게 배치되고 머리글과 바닥글이 반복됩니다.

![페이지를 매긴](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

Report Builder에서 보고서를 미리 본 후 Power BI 서비스, app.powerbi.com에 게시할 수 있습니다. 서비스에 보고서를 게시하려면 Power BI Pro 라이선스가 필요합니다. 작업 영역이 Power BI Premium 용량에 포함된 경우 내 작업 영역 또는 작업 영역에서 페이지를 매긴 보고서를 게시하고 공유할 수 있습니다. 또한 Power BI 관리자는 Power BI 관리 포털의 [프리미엄 용량 섹션](../admin/service-admin-premium-workloads.md#paginated-reports)에서 페이지를 매긴 보고서를 사용하도록 설정해야 합니다. 

## <a name="compare-power-bi-reports-and-paginated-reports"></a>Power BI 보고서와 페이지를 매긴 보고서 비교

페이지를 매긴 보고서의 주요 이점은 길이에 관계없이 테이블의 모든 데이터를 인쇄하는 기능입니다. Power BI 보고서에 테이블을 배치하는 그림. 페이지에 테이블의 일부 행이 표시되고 나머지 행을 볼 수 있도록 스크롤 막대가 표시됩니다. 해당 페이지를 인쇄하거나 PDF로 내보내는 경우 페이지에서 표시되는 행만 출력됩니다. 

이제 페이지를 매긴 보고서에 동일한 테이블을 추가한다고 가정합니다. 인쇄하거나 PDF로 내보내는 경우 페이지를 매긴 보고서에는 해당 테이블의 모든 행을 인쇄하는 데 필요한 만큼의 페이지가 있습니다. 

다음 비디오에서는 Peter Myers(Microsoft Most Valued Professional - 데이터 플랫폼)와 Chris Finlan(수석 프로그램 관리자)이 두 보고서 형식으로 비슷한 테이블을 인쇄하는 방법을 보여 줍니다. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/jXTiYJKw1Rs?list=PL1N57mwBHtN1icIhpjQOaRL8r9G-wytpT" frameborder="0" allowfullscreen></iframe>

이 비디오는 8개 모듈로 구성된 비디오 기반 과정 [하루에 배우는 Power BI 페이지를 매긴 보고서](../learning-catalog/paginated-reports-online-course.md)의 일부입니다. 이 과정은 Power BI 페이지를 매긴 보고서를 만들고 게시하고 배포하는 데 필요한 기술 지식을 가진 보고서 작성자로서 역량을 강화하도록 설계되었습니다.

## <a name="create-reports-in-power-bi-report-builder"></a>Power BI 보고서 작성기에서 보고서 만들기

페이지를 매긴 보고서에는 고유한 디자인 도구인 Power BI 보고서 작성기가 있습니다. Power BI Report Server 또는 SQL Server Reporting Services (SSRS)에 대한 페이지를 매긴 보고서를 만들기 위해 이전에 사용한 도구와 동일한 기반을 공유하는 새 도구입니다. 실제로 SSRS 2016 및 2017 또는 Power BI Report Server 온-프레미스용으로 만드는 페이지를 매긴 보고서는 Power BI 서비스와 호환됩니다. Power BI 서비스는 이전 버전과의 호환성을 유지 관리하므로 보고서를 향상시킬 수 있고 이전 버전의 페이지를 매긴 보고서를 업그레이드할 수 있습니다. 일부 보고서 기능은 시작 시 사용할 수 없습니다. 자세한 내용은 이 문서의 [제한 사항 및 고려 사항](#limitations-and-considerations)을 참조하세요.
     
## <a name="report-from-a-variety-of-data-sources"></a>다양한 데이터 원본의 보고서

하나의 페이지를 매긴 보고서에 다양하고 많은 데이터 원본이 포함될 수 있습니다. Power BI 보고서와 달리, 이 보고서에는 기본 데이터 모델이 없습니다. Power BI 서비스의 페이지를 매긴 보고서 초기 릴리스의 경우 보고서 자체에 포함된 데이터 원본 및 데이터 세트를 만듭니다. 지금은 공유 데이터 원본 또는 공유 데이터 세트를 사용할 수 없습니다. 로컬 컴퓨터의 보고서 작성기에서 보고서를 만듭니다. 보고서가 온-프레미스 데이터에 연결되면 보고서를 Power BI 서비스에 업로드한 후 게이트웨이를 만들고 데이터 연결을 리디렉션해야 합니다. 현재 연결할 수 있는 데이터 원본은 다음과 같습니다.

- Azure SQL Database와 데이터 웨어하우스(기본 및 oAuth를 통해)
- Azure Analysis Services(SSO를 통해)
- 게이트웨이를 통해 SQL Server
- 게이트웨이를 통해 SQL Server Analysis Services
- Power BI 데이터 세트
- Oracle
- Teradata

## <a name="design-your-report"></a>보고서 디자인  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>행렬, 차트 및 자유 형식 레이아웃을 사용하여 페이지를 매긴 보고서 만들기

테이블 보고서는 열 기반 데이터에 적합합니다. 크로스탭 또는 피벗 테이블 보고서와 같은 행렬 보고서는 요약된 데이터에 적합합니다. 차트 보고서는 그래픽 형식으로 데이터를 제공하고 자유 형식 ‘목록’ 보고서는 청구서와 같은 거의 모든 다른 것을 제공할 수 있습니다. 
  
보고서 작성기 마법사 중 하나로 시작할 수 있습니다. 테이블, 행렬 및 차트 마법사는 포함된 데이터 원본 연결 및 포함된 데이터 세트를 만드는 과정을 안내합니다. 그런 다음, 필드를 끌어서 놓아 데이터 세트 쿼리를 만들고, 레이아웃 및 스타일을 선택하고, 보고서를 사용자 지정합니다.  
  
지도 마법사를 사용하여 지리적 또는 기하학적 배경에 집계된 데이터를 표시하는 보고서를 만듭니다. 지도 데이터는 Transact-SQL 쿼리 또는 ESRI(Environmental Systems Research Institute, Inc.) 셰이프 파일의 공간 데이터일 수 있습니다. Microsoft Bing 지도 타일 배경을 추가할 수도 있습니다.  

### <a name="add-more-to-your-report"></a>보고서에 다른 항목 추가

데이터를 필터링, 그룹화 및 정렬하거나 공식 또는 식을 추가하여 데이터를 수정합니다. 차트, 계기, 스파크라인 및 표시기를 추가하여 데이터를 시각적 형식으로 요약합니다.  매개 변수 및 필터를 사용하여 사용자 지정된 보기에 대한 데이터를 필터링합니다. 외부 콘텐츠를 포함하여 이미지 및 기타 리소스를 포함하거나 참조합니다.  

보고서 자체부터 모든 텍스트 상자, 이미지, 테이블 및 차트까지, 페이지를 매긴 보고서의 모든 항목에는 보고서를 원하는 대로 정확하게 표시하기 위해 설정할 수 있는 속성 배열이 있습니다.

## <a name="creating-a-report-definition"></a>보고서 정의 만들기

페이지를 매긴 보고서를 디자인할 때 실제로는 ‘보고서 정의’를 만듭니다. 보고서 정의는 데이터를 포함하지 않습니다. 데이터를 가져올 위치, 가져올 데이터 및 데이터 표시 방법을 지정합니다. 보고서를 실행할 때 보고서 처리기는 지정한 보고서 정의를 사용하고, 데이터를 검색하고, 보고서 레이아웃과 결합하여 보고서를 생성합니다. 보고서 정의를 Power BI 서비스, `https://app.powerbi.com` 의 내 작업 영역 또는 동료와 공유된 작업 영역에 업로드합니다. 보고서 데이터 원본이 온-프레미스인 경우 보고서를 업로드한 후 데이터 원본 연결을 리디렉션하여 게이트웨이를 통과합니다. 

## <a name="view-your-paginated-report"></a>페이지를 매긴 보고서 보기
브라우저의 Power BI 서비스 및 Power BI 모바일 앱에서 페이지를 매긴 보고서를 볼 수 있습니다. Power BI 서비스에서 보고서를 HTML, MHTML, PDF, XML, CSV, TIFF, Word 및 Excel과 같은 여러 형식으로 내보낼 수 있습니다. 다른 사용자와 공유할 수도 있습니다.  

## <a name="create-a-subscription-to-your-report"></a>보고서에 대한 구독 만들기

이제 Power BI 서비스에서 페이지를 매긴 보고서에 대한 나 또는 다른 사용자의 전자 메일 구독을 설정할 수 있습니다. 일반적으로 프로세스는 Power BI 서비스에서의 보고서 및 대시보드 구독과 같습니다. 구독을 설정하면 전자 메일 수신 빈도를 선택할 수 있습니다: 매일, 매주 또는 매시간. 구독에는 전체 보고서 출력의 PDF 첨부 파일이 포함됩니다.

자세한 내용은 [자신 및 다른 사람이 Power BI 서비스에서 페이지를 매긴 보고서 구독하기](../consumer/paginated-reports-subscriptions.md) 문서를 참조합니다. 

## <a name="limitations-and-considerations"></a>제한 사항 및 고려 사항

초기 릴리스에서 지원되지 않는 몇 가지 다른 기능은 다음과 같습니다.

- 보고서 페이지 또는 시각적 개체를 Power BI 대시보드에 고정. 사용자는 여전히 Power BI Report Server 또는 Reporting Services 보고서 서버의 온-프레미스 페이지를 매긴 보고서에서 Power BI 대시보드로 시각화를 고정할 수 있습니다. 자세한 내용은 [Power BI 대시보드에 Reporting Services 항목 고정](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)을 참조하세요.
- 문서 구조.
- 드릴스루 보고서.  드릴스루 시나리오를 위해서는 URL 매개 변수를 페이지를 매긴 보고서와 함께 사용합니다.
- 공유 데이터 원본 및 공유 데이터 세트.

 
## <a name="next-steps"></a>다음 단계

- [Microsoft 다운로드 센터에서 Power BI 보고서 작성기 설치](https://aka.ms/pbireportbuilder)
- [자습서: 페이지를 매긴 보고서 만들기](paginated-reports-quickstart-aw.md)
- [온라인 과정: Power BI 페이지를 매긴 보고서 하루에 끝내기](../learning-catalog/paginated-reports-online-course.md)
- [Power BI 페이지를 매긴 보고서 샘플](paginated-reports-samples.md)
- [페이지를 매긴 보고서에 직접 데이터 입력](paginated-reports-enter-data.md)
- [자습서: 고객을 위해 애플리케이션에 페이지를 매긴 Power BI 보고서 포함](../developer/embedded/embed-paginated-reports-customers.md)