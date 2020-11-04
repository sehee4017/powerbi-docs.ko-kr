---
title: Power BI 보고서 작성기에서 보고서 계획
description: Power BI 보고서 작성기로 다양한 종류의 페이지를 매긴 보고서를 만들 수 있습니다. 유용하고 이해하기 쉬운 보고서를 만들려면 먼저 계획을 세우는 것이 좋습니다.
ms.date: 07/25/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3f075372436723cd8952decd68ecc764bd6e92a0
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297747"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>Power BI 보고서 작성기에서 보고서 계획

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Power BI 보고서 작성기로 다양한 종류의 페이지를 매긴 보고서를 만들 수 있습니다. 예를 들어 판매 데이터, 마케팅 및 판매 추세를 요약하거나 자세히 보여 주는 보고서를 만들거나 운영 보고서 또는 대시보드를 만들 수 있습니다. 판매 주문, 제품 카탈로그 또는 양식 편지와 같은 서식 있는 텍스트를 사용한 보고서를 만들 수도 있습니다. 이러한 보고서는 모두 보고서 작성기에 있는 동일한 기본 빌딩 블록을 다르게 조합하여 만듭니다. 보고서를 만들기 전에 먼저 계획을 세우면 보다 유용하고 이해하기 쉬운 보고서를 만들 수 있습니다. 보고서 생성 작업을 시작하기 전에 고려해야 할 사항은 다음과 같습니다.  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>보고서를 어떤 형식으로 표시하나요?
  
Power BI 포털과 같은 브라우저에서 온라인으로 보고서를 렌더링하거나 Excel, Word 또는 PDF와 같은 다른 형식으로 내보낼 수 있습니다. 내보내는 모든 형식에서 모든 기능을 사용할 수 있는 것은 아니므로 보고서의 최종 형식을 결정할 때는 신중을 기해야 합니다. 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>데이터를 어떤 구조로 표시하나요?
  
테이블 형식, 행렬(크로스탭 또는 피벗 테이블 보고서와 유사), 차트 또는 자유 형식 구조 중에서 선택하거나 이들을 조합하여 데이터를 나타낼 수 있습니다. 자세한 내용은 [Power BI 보고서 작성기의 테이블, 행렬 및 목록](report-builder-tables-matrices-lists.md)을 참조하세요.  
  
## <a name="how-do-you-want-your-report-to-look"></a>보고서를 어떻게 확인하시겠습니까?
  
보고서 작성기는 보고서의 가독성을 높이고, 핵심 정보를 강조하고, 보고서를 읽는 사람이 보고서를 보다 쉽게 탐색할 수 있도록 하기 위해 보고서에 추가할 수 있는 다양한 보고서 항목을 제공합니다. 원하는 보고서 형태를 알면 입력란, 사각형, 이미지, 선 등의 보고서 항목이 필요한지 여부를 결정할 수 있습니다. 항목을 표시하거나 숨기고, 문서 구조를 추가하고, 드릴스루 보고서나 하위 보고서를 포함하고, 보고서에서 다른 보고서에 연결할 수도 있습니다.   
  
## <a name="should-the-data-be-filtered"></a>데이터를 필터링해야 하나요?
  
특정 사용자나 위치, 또는 특정 시간대로 보고서 범위를 좁힐 수 있습니다. 보고서 데이터를 필터링하려면 매개 변수를 사용하여 원하는 데이터만 검색하고 표시합니다. 자세한 내용은 [Power BI 보고서 작성기의 보고서 매개 변수](paginated-reports-parameters.md)를 참조하세요.  
  
## <a name="do-you-need-to-create-calculations"></a>계산을 해야 하나요? 
  
보고서에 꼭 맞는 필드가 데이터 원본과 데이터 세트에 없을 수도 있습니다. 이 경우 고유의 계산 필드를 만들어야 할 수도 있습니다. 예를 들어 단가에 수량을 곱해서 품목의 판매액을 구할 수 있습니다. 조건부 서식 및 기타 고급 기능을 제공하려는 경우에도 식을 사용합니다. 자세한 내용은 [Power BI 보고서 작성기의 식](report-builder-expressions.md)을 참조하세요.  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>보고서 항목을 처음에 숨길지 여부
  
보고서를 처음 실행할 때 데이터 영역, 그룹 및 열과 같은 보고서 항목을 숨길지 여부를 검토합니다. 예를 들어 처음에는 요약 테이블만 제공하고 그 후에 세부 데이터로 드릴다운할 수 있습니다. 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>보고서 배달 방법  
  
사용자 본인에게만 필요한 정보가 포함된 보고서의 경우 보고서를 로컬 컴퓨터에 저장하고 보고서에 대한 작업을 계속하거나 보고서를 로컬에서 실행할 수 있습니다. 그러나 보고서를 다른 사용자와 공유하려면 보고서를 Power BI에 저장해야 합니다. Power BI에 저장하면 다른 사용자가 필요할 때마다 실행할 수 있습니다. 또는 다른 사용자에게 보고서의 구독 및 메일 전송을 설정할 수 있습니다. 원하는 경우 특정 내보내기 형식으로 보고서가 배달되도록 할 수도 있습니다. 
  
## <a name="next-steps"></a>다음 단계

- [Power BI Premium에서 페이지를 매긴 보고서란?](paginated-reports-report-builder-power-bi.md)
