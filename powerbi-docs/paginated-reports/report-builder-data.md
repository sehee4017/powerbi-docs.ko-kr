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
ms.date: 06/06/2019
ms.openlocfilehash: fea4e4927b009e30bc040593f9237cc49ff73956
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921450"
---
# <a name="report-data-in-power-bi-report-builder"></a>Power BI 보고서 작성기의 보고서 데이터

보고서 데이터는 조직에서 데이터의 여러 원본에서 가져올 수 있습니다. Power BI 보고서 작성기 보고서 디자인의 첫 번째 단계는 기본 보고서 데이터를 나타내는 데이터 원본 및 데이터 세트를 만드는 것입니다. 각 데이터 원본은 데이터 연결 정보를 포함합니다. 각 데이터 세트는 데이터 원본에서 데이터로 사용할 필드 세트를 정의하는 쿼리 명령을 포함합니다. 각 데이터 세트의 데이터를 시각화하려면 테이블, 행렬, 차트 또는 지도와 같은 데이터 영역을 추가합니다. 보고서를 처리하면 데이터 원본에 대한 쿼리가 실행되고 각 데이터 영역이 필요에 따라 확장되어 데이터 세트에 대한 쿼리 결과를 표시합니다.  

[Power BI 보고서 작성기에서 페이지를 매긴 보고서의 포함된 데이터 원본을 만드는](paginated-reports-embedded-data-source.md) 방법을 알아봅니다.


##  <a name="terms"></a><a name="BkMk_ReportDataTerms"></a> 용어  
  
- **데이터 연결** *데이터 원본*이라고도 합니다. 데이터 연결은 연결 형식에 종속된 이름 및 연결 속성을 포함합니다. 기본적으로 데이터 연결은 자격 증명을 포함하지 않습니다. 데이터 연결은 외부 데이터 원본에서 검색할 데이터를 지정하지 않습니다. 이렇게 하려면 데이터 세트를 만들 때 쿼리를 지정합니다.  
  
- **연결 문자열.** 연결 문자열은 데이터 원본에 연결하는 데 필요한 연결 속성의 문자열 버전입니다. 연결 속성은 데이터 연결 형식에 따라 다릅니다.  
  
- **포함된 데이터 원본.** *보고서별 데이터 원본*이라고도 합니다. 보고서에서 정의되며 해당 보고서에서만 사용되는 데이터 원본입니다.  
  
- **자격 증명.** 자격 증명은 외부 데이터에 액세스할 수 있도록 제공해야 하는 인증 정보입니다.  
  
##  <a name="tips-for-specifying-report-data"></a><a name="BkMk_ReportDataTips"></a> 보고서 데이터 지정 시 유용한 정보

 다음 정보를 사용하여 보고서 데이터 전략을 설계하십시오.  
  
- **데이터 필터링** 쿼리 또는 보고서에서 보고서 데이터를 필터링할 수 있습니다. 데이터 세트 및 쿼리 변수를 사용하여 연계 매개 변수를 만들고, 사용자에게 수천 개의 선택 항목에서 보다 관리가 용이한 숫자로 선택 범위를 좁힐 수 있는 기능을 제공할 수 있습니다. 매개 변수 값 또는 지정하는 다른 값에 따라 테이블 또는 차트에서 데이터를 필터링할 수 있습니다.  
  
- **매개 변수** 쿼리 변수를 자동으로 포함하는 데이터 세트 쿼리 명령은 일치하는 보고서 매개 변수를 만듭니다. 매개 변수를 직접 만들 수도 있습니다. 보고서를 볼 때 보고서 도구 모음에 매개 변수가 표시됩니다. 사용자는 보고서 데이터 또는 보고서 형식을 제어하는 값을 선택할 수 있습니다. 특정 대상을 위한 보고서 데이터를 사용자 지정하기 위해 동일한 보고서 정의에 연결된 다양한 기본값을 사용하여 보고서 매개 변수의 세트를 만들거나 기본 제공 **UserID** 필드를 사용할 수 있습니다. 
  
- **데이터 그룹화 및 집계** 쿼리 또는 보고서에서 보고서 데이터를 그룹화하고 집계할 수 있습니다. 쿼리에서 값을 집계하는 경우 유의미한 제약 조건 내에서 보고서의 값을 계속해서 결합할 수 있습니다.  
  
- **데이터 정렬** 쿼리 또는 보고서에서 보고서 데이터를 정렬할 수 있습니다. 테이블에서 사용자가 정렬 순서를 제어할 수 있도록 대화형 정렬 단추를 추가할 수도 있습니다.  
  
- **식 기반 데이터** 대부분의 보고서 속성은 식 기반일 수 있으며, 식은 데이터 세트 필드 및 보고서 매개 변수에 대한 참조를 포함할 수 있으므로 보고서 데이터 및 모양을 제어하도록 강력한 식을 작성할 수 있습니다. 사용자에게 매개 변수를 정의하여 표시되는 데이터를 제어하는 기능을 제공할 수 있습니다.  
  
- **데이터 세트의 데이터 표시** 데이터 세트의 데이터는 일반적으로 테이블 및 차트와 같은 하나 이상의 데이터 영역에 표시됩니다.  
  
- **여러 데이터 세트의 데이터 표시** 다른 데이터 세트에서 값 또는 집계를 조회하는 하나의 데이터 세트를 기반으로 하는 데이터 영역에서 식을 작성할 수 있습니다. 다른 데이터 원본의 데이터를 표시하도록 하나의 데이터 세트에 따라 테이블에서 하위 보고서를 포함할 수 있습니다.  
  
 다음 목록을 사용하여 보고서에 대한 데이터 원본을 정의할 수 있습니다.  
  
- 조직에 대한 소프트웨어 데이터 계층 아키텍처 및 데이터 형식에서 발생할 수 있는 잠재적인 문제를 이해합니다. 데이터 확장 프로그램 및 데이터 처리 확장 프로그램이 쿼리 결과에 어떤 영향을 줄 수 있는지 이해합니다. 데이터 형식은 데이터의 원본, 데이터 공급 기업 및 보고서 정의(.rdl) 파일에 저장된 데이터 형식 간에 다릅니다.  
  
- 데이터 원본 및 데이터 세트는 보고서에 작성되며 Power BI 서비스에 게시됩니다. 게시된 후 Power BI 서비스에서 직접 또는 Enterprise Gateway에서 자격 증명을 구성할 수 있습니다. 

## <a name="next-steps"></a>다음 단계

- [Power BI Premium에서 페이지를 매긴 보고서란?](paginated-reports-report-builder-power-bi.md)  
- [페이지를 매긴 보고서의 데이터 검색 지침](../guidance/report-paginated-data-retrieval.md)