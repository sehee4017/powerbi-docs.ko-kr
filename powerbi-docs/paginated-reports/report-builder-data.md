---
title: Power BI 보고서 작성기의 보고서 데이터
description: Power BI 보고서 작성기에서 보고서를 디자인하는 첫 번째 단계는 기본 보고서 데이터를 나타내는 데이터 원본 및 데이터 세트를 만드는 것입니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 08/04/2020
ms.openlocfilehash: 97b93f23c8070af1b514032cea122b257097d664
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96120661"
---
# <a name="report-data-in-power-bi-report-builder"></a>Power BI 보고서 작성기의 보고서 데이터

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

보고서 데이터는 조직에서 데이터의 여러 원본에서 가져올 수 있습니다. Power BI 보고서 작성기 보고서 디자인의 첫 번째 단계는 기본 보고서 데이터를 나타내는 데이터 원본 및 데이터 세트를 만드는 것입니다. 각 데이터 원본은 데이터 연결 정보를 포함합니다. 각 데이터 세트는 데이터 원본에서 데이터로 사용할 필드 세트를 정의하는 쿼리 명령을 포함합니다. 각 데이터 세트의 데이터를 시각화하려면 테이블, 행렬, 차트 또는 지도와 같은 데이터 영역을 추가합니다. 보고서를 처리하면 데이터 원본에 대한 쿼리가 실행되고 각 데이터 영역이 필요에 따라 확장되어 데이터 세트에 대한 쿼리 결과를 표시합니다.  

[Power BI 보고서 작성기에서 페이지를 매긴 보고서의 포함된 데이터 원본을 만드는](paginated-reports-embedded-data-source.md) 방법을 알아봅니다.


##  <a name="terms"></a><a name="BkMk_ReportDataTerms"></a> 용어  
  
- **데이터 연결** *데이터 원본* 이라고도 합니다. 데이터 연결은 연결 형식에 종속된 이름 및 연결 속성을 포함합니다. 기본적으로 데이터 연결은 자격 증명을 포함하지 않습니다. 데이터 연결은 외부 데이터 원본에서 검색할 데이터를 지정하지 않습니다. 이렇게 하려면 데이터 세트를 만들 때 쿼리를 지정합니다.  
  
- **연결 문자열.** 연결 문자열은 데이터 원본에 연결하는 데 필요한 연결 속성의 문자열 버전입니다. 연결 속성은 데이터 연결 형식에 따라 다릅니다. 

    > [!NOTE]
    > 데이터 원본 연결 문자열은 식 기반일 수 없습니다.
  
- **포함된 데이터 원본.** *보고서별 데이터 원본* 이라고도 합니다. 보고서에서 정의되어 해당 보고서에서만 사용되는 데이터 원본입니다.  
  
- **자격 증명.** 자격 증명은 외부 데이터 액세스를 위해 제공해야 하는 인증 정보입니다.  
  
##  <a name="tips-for-specifying-report-data"></a><a name="BkMk_ReportDataTips"></a> 보고서 데이터 지정 시 유용한 정보

 다음 정보를 사용하여 보고서 데이터 전략을 설계하십시오.  
  
- **데이터 필터링** 쿼리 또는 보고서의 보고서 데이터를 필터링할 수 있습니다. 데이터 세트 및 쿼리 변수를 사용하여 연계 매개 변수를 만들고, 사용자에게 수천 가지의 선택권을 좀 더 관리 가능한 수치로 좁히는 기능을 제공할 수 있습니다. 매개 변수 값이나 지정하는 기타 값을 기반으로 테이블 또는 차트의 데이터를 필터링할 수 있습니다.  
  
- **매개 변수** 쿼리 변수를 포함하는 데이터 세트 쿼리 명령은 일치하는 보고서 매개 변수를 자동으로 만듭니다. 매개 변수를 직접 만들 수도 있습니다. 보고서를 볼 때 보고서 도구 모음에 매개 변수가 표시됩니다. 사용자는 보고서 데이터 또는 보고서 모양을 제어하는 값을 선택할 수 있습니다. 특정 대상을 위해 보고서 데이터를 사용자 지정하려면 동일한 보고서 정의에 다양한 기본값이 연결된 보고서 매개 변수 집합을 만들거나 기본 제공 **UserID** 필드를 사용할 수 있습니다. 
  
- **데이터 그룹화 및 집계** 쿼리 또는 보고서의 보고서 데이터를 그룹화하고 집계할 수 있습니다. 쿼리의 값을 집계하는 경우 계속해서 유의미한 값 제약 조건 내에서 보고서에 값을 결합할 수 있습니다.  
  
- **데이터 정렬** 쿼리 또는 보고서의 보고서 데이터를 정렬할 수 있습니다. 테이블에는 사용자가 정렬 순서를 제어할 수 있도록 대화형 정렬 단추를 추가할 수도 있습니다.  
  
- **식 기반 데이터** 대부분의 보고서 속성은 식 기반일 수 있고 식에는 데이터 세트 필드 및 보고서 매개 변수에 대한 참조를 포함할 수 있기 때문에 보고서 데이터 및 모양을 제어하는 강력한 식을 작성할 수 있습니다. 매개 변수 정의를 통해 표시할 데이터를 제어하는 기능을 사용자에게 제공할 수 있습니다.  
  
- **데이터 세트의 데이터 표시** 데이터 세트의 데이터는 일반적으로 테이블 및 차트와 같은 하나 이상의 데이터 영역에 표시됩니다.  
  
- **여러 데이터 세트의 데이터 표시**  데이터 영역에서 단일 데이터 세트를 기반으로 값을 조회하거나 다른 데이터 세트로 집계하는 식을 작성할 수 있습니다. 테이블에 단일 데이터 세트를 기반으로 하며 다양한 데이터 원본의 데이터를 표시하는 하위 보고서를 포함할 수 있습니다.  
  
 다음 목록을 사용하여 보고서의 데이터 원본을 정의할 수 있습니다.  
  
- 소프트웨어 데이터 계층 아키텍처 및 데이터 형식에서 발생할 수 있는 문제에 대해 이해합니다. 데이터 확장 프로그램 및 데이터 처리 확장 프로그램이 쿼리 결과에 어떤 영향을 미치는지 이해합니다. 데이터 형식은 데이터 원본, 데이터 제공자, 보고서 정의 파일(.rdl)에 저장된 데이터 형식 사이에 서로 다릅니다.  
  
- 데이터 원본 및 데이터 세트는 보고서에 작성되며 Power BI 서비스에 게시됩니다. 게시된 후 Power BI 서비스에서 직접 또는 Enterprise Gateway에서 자격 증명을 구성할 수 있습니다. 

## <a name="next-steps"></a>다음 단계

- [Power BI Premium에서 페이지를 매긴 보고서란?](paginated-reports-report-builder-power-bi.md)  
- [페이지를 매긴 보고서의 데이터 검색 지침](../guidance/report-paginated-data-retrieval.md)
