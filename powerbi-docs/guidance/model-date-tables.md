---
title: Power BI Desktop에서 날짜 테이블 만들기
description: Power BI Desktop에서 날짜 테이블을 만드는 방법 및 지침을 제공합니다.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/24/2020
ms.openlocfilehash: 9040fb54e51dfeecad853e5ba980f423ab48e908
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417845"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>Power BI Desktop에서 날짜 테이블 만들기

이 문서는 Power BI Desktop을 개발하는 데이터 모델러를 대상으로 합니다. 이 문서에서는 데이터 모델에서 날짜 테이블을 만들기 위한 디자인 모범 사례를 설명합니다.

DAX(Data Analysis Expressions) [시간 인텔리전스 함수](/dax/time-intelligence-functions-dax)를 사용하려면 모델 사전 요구 사항이 있습니다. 모델에 _날짜 테이블_ 이 하나 이상 있어야 합니다. 날짜 테이블은 다음 요구 사항을 충족하는 테이블입니다.

> [!div class="checklist"]
> - 이 테이블에 데이터 형식 **date**(또는 **date/time**)의 열이 있어야 합니다. 이 열은 _날짜 열_ 이라고 합니다.
> - 날짜 열에는 고유한 값이 있어야 합니다.
> - 날짜 열에는 공백이 포함되면 안됩니다.
> - 날짜 열에는 누락된 날짜가 없어야 합니다.
> - 날짜 열은 전체 연도에 걸쳐 있어야 합니다. 연도는 반드시 역년(1월~12월)일 필요가 없습니다.
> - 날짜 테이블은 [날짜 테이블로 표시](../transform-model/desktop-date-tables.md#setting-your-own-date-table)되어 있어야 합니다.

여러 가지 방법 중 하나를 사용하여 날짜 테이블을 모델에 추가할 수 있습니다.

- 자동 날짜/시간 옵션
- 날짜 차원 테이블에 연결하는 파워 쿼리
- 날짜 테이블을 생성 파워 쿼리
- 날짜 테이블을 생성하는 DAX
- 기존 날짜 테이블을 복제하는 DAX

> [!TIP]
> 날짜 테이블은 아마도 모델에 추가하는 가장 일관적인 기능일 것입니다. 또한 조직에서는 날짜 테이블을 일관되게 정의해야 합니다. 따라서 사용하려는 기술에 관계없이 완전히 구성된 날짜 테이블을 포함하는 [Power BI Desktop 템플릿](../create-reports/desktop-templates.md)을 만드는 것이 좋습니다. 조직의 모든 모델러와 템플릿을 공유합니다. 따라서 누군가가 새 모델을 개발하는 경우 지속적으로 정의된 날짜 테이블로 시작할 수 있습니다.

## <a name="use-auto-datetime"></a>자동 날짜/시간 사용

[자동 날짜/시간](../transform-model/desktop-auto-date-time.md) 옵션은 편리하고 빠르고 사용하기 쉬운 시간 인텔리전스를 제공합니다. 보고서 작성자는 달력 기간을 기준으로 필터링, 그룹화, 드릴 다운할 때 시간 인텔리전스를 사용할 수 있습니다.

달력 기간으로 작업할 때와 시간과 관련하여 간단한 모델 요구 사항이 있는 경우에만 자동 날짜/시간 옵션을 사용하도록 설정하는 것이 좋습니다. 임시 모델을 만들거나 데이터 탐색 또는 프로파일링을 수행하는 경우에도 이 옵션을 사용하는 것이 편리할 수 있습니다. 그러나 이 방법은 필터를 여러 테이블에 전파할 수 있는 단일 날짜 테이블 디자인을 지원하지 않습니다. 자세한 내용은 [Power BI Desktop의 자동 날짜/시간 지침](auto-date-time.md)을 참조하세요.

## <a name="connect-with-power-query"></a>파워 쿼리를 사용하여 연결

데이터 원본에 이미 날짜 테이블이 있는 경우 모델 날짜 테이블의 원본으로 사용하는 것이 좋습니다. 일반적으로 데이터 웨어하우스에 연결하는 경우에는 날짜 차원 테이블이 포함됩니다. 이러한 방식으로 모델은 조직의 시간에 대한 단일 소스를 활용합니다.

DirectQuery 모델을 개발하면서 데이터 원본에 날짜 테이블이 포함되어 있지 않은 경우 데이터 원본에 날짜 테이블을 추가하는 것이 좋습니다. 이 테이블은 날짜 테이블의 모든 모델링 요구 사항을 충족해야 합니다. 그런 다음 파워 쿼리를 사용하여 날짜 테이블에 연결할 수 있습니다. 그러면 모델 계산이 DAX 시간 인텔리전스 기능을 활용할 수 있습니다.

## <a name="generate-with-power-query"></a>파워 쿼리를 사용하여 생성

파워 쿼리를 사용하여 날짜 테이블을 생성할 수 있습니다. 다음은 그 방법을 보여 주는 두 개의 블로그 항목입니다.

- Matt Masson이 게시한 [파워 쿼리 스크립트를 사용하여 날짜 차원 만들기](https://www.mattmasson.com/2014/02/creating-a-date-dimension-with-a-power-query-script/)
- Chris Webb이 게시한 [파워 쿼리에서 날짜 차원 테이블 생성](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/)

> [!TIP]
> 조직에 시간에 대한 데이터 웨어하우스 또는 기타 일관된 정의가 없는 경우 파워 쿼리를 사용하여 [데이터 흐름](../transform-model/dataflows/dataflows-introduction-self-service.md)을 게시하는 것이 좋습니다. 그런 다음 모든 데이터 모델러를 데이터 흐름에 연결하여 모델에 날짜 테이블을 추가합니다. 이 데이터 흐름은 조직의 시간에 대한 단일 소스가 됩니다.

날짜 테이블을 생성해야 하는 경우 DAX를 사용하는 것이 좋습니다. 이 방법이 더 쉽게 느껴질 것입니다. 또한 DAX에는 날짜 테이블 만들기 및 관리를 간소화하는 몇 가지 기본 제공 인텔리전스가 포함되어 있기 때문에 더 편리할 수 있습니다.

## <a name="generate-with-dax"></a>DAX를 사용하여 생성

[CALENDAR](/dax/calendar-function-dax) 또는 [CALENDARAUTO](/dax/calendarauto-function-dax) DAX 함수를 사용하여 계산 테이블을 만들어 모델에서 날짜 테이블을 생성할 수 있습니다. 각 함수는 날짜의 단일 열 테이블을 반환합니다. 그런 다음 계산 열을 사용하여 계산 테이블을 확장해 날짜 간격 필터링 및 그룹화 요구 사항을 지원할 수 있습니다.

- 날짜 범위를 정의하려면 **CALENDAR** 함수를 사용합니다. 시작 날짜와 종료 날짜 두 값을 전달합니다. 이러한 값은 `MIN(Sales[OrderDate])` 또는 `MAX(Sales[OrderDate])` 같은 다른 DAX 함수로 정의될 수 있습니다.
- 날짜 범위가 모델에 저장된 모든 날짜를 자동으로 포함하게 하려면 **CALENDARAUTO** 함수를 사용합니다. 연도의 종료 월인 단일 선택적 매개 변수를 전달할 수 있습니다. 연도가 12월로 끝나는 역년인 경우 값을 전달할 필요가 없습니다. 표시된 날짜 테이블에 대한 요구 사항인 전체 연도가 반환되도록 하기 때문에 유용한 함수입니다. 또한 테이블을 향후 연도로 연장하기 위한 관리가 필요 없습니다. 데이터 새로 고침이 완료되면 테이블 다시 계산이 트리거됩니다. 새 연도의 날짜가 모델에 로드될 때 다시 계산하면 테이블의 날짜 범위가 자동으로 확장됩니다.

## <a name="clone-with-dax"></a>DAX를 사용하여 복제

모델에 이미 날짜 테이블이 있고 추가 날짜 테이블이 필요한 경우 기존 날짜 테이블을 쉽게 복제할 수 있습니다. 날짜가 [롤플레잉 차원](star-schema.md#role-playing-dimensions)인 경우가 그렇습니다. 계산 테이블을 만들어 테이블을 복제할 수 있습니다. 계산 테이블 식은 단순히 기존 날짜 테이블의 이름입니다.

## <a name="next-steps"></a>다음 단계

이 문서와 관련된 보다 자세한 내용을 알아보려면 다음 리소스를 참조하세요.

- [Power BI Desktop의 자동 날짜/시간](../transform-model/desktop-auto-date-time.md)
- [Power BI Desktop의 자동 날짜/시간 지침](auto-date-time.md)
- [Power BI Desktop에서 날짜 테이블 설정 및 사용](../transform-model/desktop-date-tables.md)
- [Power BI의 셀프 서비스 데이터 준비](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [CALENDAR 함수(DAX)](/dax/calendar-function-dax)
- [CALENDARAUTO 함수(DAX)](/dax/calendarauto-function-dax)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)