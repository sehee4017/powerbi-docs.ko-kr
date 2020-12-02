---
title: Power BI Desktop의 자동 날짜/시간 지침
description: Power BI Desktop의 자동 날짜/시간 기능을 사용하는 방법에 대한 지침입니다.
author: peter-myers
ms.author: v-pemyer
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 10/23/2019
ms.openlocfilehash: ed99c48aaef116f58ebff0d8026b37938a39de3b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394592"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Power BI Desktop의 자동 날짜/시간 지침

이 문서에서는 Power BI Desktop에서 가져오기 또는 복합 모델을 개발하는 데이터 모델러를 대상으로 합니다. 특정 상황에서 Power BI Desktop _자동 날짜/시간_ 을 사용하는 경우 지침, 권장 사항 및 고려 사항을 제공합니다. _자동 날짜/시간_ 에 대한 개요 및 일반적인 소개는 [Power BI Desktop의 자동 날짜/시간](../transform-model/desktop-auto-date-time.md)을 참조하세요.

_자동 날짜/시간_ 옵션은 편리하고 빠르고 사용하기 쉬운 시간 인텔리전스를 제공합니다. 보고서 작성자는 달력 기간을 기준으로 필터링, 그룹화, 드릴 다운할 때 시간 인텔리전스를 사용할 수 있습니다.

## <a name="considerations"></a>고려 사항

다음 글머리 기호 목록에서는 _자동 날짜/시간_ 옵션과 관련된 고려 사항 및 가능한 제한 사항을 설명합니다.

- **모두 적용되거나 모두 적용되지 않음:** _자동 날짜/시간_ 옵션을 사용하도록 설정하는 경우 가져오기 테이블에서 관계의 &quot;다&quot; 측면이 아닌 모든 날짜 열에 적용됩니다. 열에 따라 선택적으로 사용 또는 사용 안 함을 지정할 수 없습니다.
- **달력 기간만 해당:** 연도 및 분기 열은 달력 기간과 관련이 있습니다. 즉, 연도는 1월 1일에 시작하여 12월 31일에 끝납니다. 연도 시작(또는 종료) 날짜를 사용자 지정할 수는 없습니다.
- **사용자 지정:** 기간을 설명하는 데 사용되는 값은 사용자 지정할 수 없습니다. 또한 다른 기간(예: 주)을 설명하는 열을 더 추가할 수도 없습니다.
- **연도 필터링:** **분기**, **월** 및 **일** 열 값에는 연도 값이 포함되지 않습니다. 예를 들어 **월** 열에는 월 이름(1월, 2월 등)만 포함됩니다. 값은 완전히 자체 설명되지 않으며, 일부 보고서 디자인에서는 연도 필터 컨텍스트를 전달하지 못할 수 있습니다.

    이 때문에 **연도** 열에서 필터 또는 그룹화를 수행하는 것이 중요합니다. **연도** 수준을 의도적으로 제거하지 않는 한 계층 연도를 사용하여 드릴 다운할 때 필터링됩니다. 연도별 필터 또는 그룹이 없는 경우, 예를 들어 월별 그룹화는 모든 연도에서 해당 월의 값을 요약합니다.
- **단일 테이블 날짜 필터링:** 각 날짜 열에 (숨겨진) 자체 자동 날짜/시간 테이블이 생성되기 때문에 한 테이블에 시간 필터를 적용하여 여러 모델 테이블로 전파하는 것은 불가능합니다. 이러한 방식으로 필터링하는 것은 매출 및 매출 예산과 같은 여러 주제(팩트 유형 테이블)에 대해 보고할 때 일반적인 모델링 요구 사항입니다. 자동 날짜/시간을 사용하는 경우 보고서 작성자는 각 날짜 열에 필터를 적용해야 합니다.
- **모델 크기:** 숨겨진 자동 날짜/시간 테이블을 생성하는 각 날짜 열에 대해 모델 크기가 증가하고 데이터 새로 고침 시간도 늘어납니다.
- **기타 보고 도구:** 다음 경우에는 자동 날짜/시간 테이블로 작업할 수 없습니다.
  - [Excel에서 분석](../collaborate-share/service-analyze-in-excel.md) 사용
  - Power BI 페이지를 매긴 보고서 Analysis Services 쿼리 디자이너 사용
  - 비 Power BI 보고서 디자이너를 사용하여 모델에 연결

## <a name="recommendations"></a>권장 사항

달력 기간으로 작업할 때와 시간과 관련하여 간단한 모델 요구 사항이 있는 경우에만 _자동 날짜/시간_ 옵션을 사용하도록 설정하는 것이 좋습니다. 임시 모델을 만들거나 데이터 탐색 또는 프로파일링을 수행하는 경우에도 이 옵션을 사용하는 것이 편리할 수 있습니다.

데이터 원본이 이미 날짜 차원 테이블을 정의하는 경우 이 테이블을 사용하여 조직 내에서 시간을 일관되게 정의해야 합니다. 예를 들어 데이터 원본이 데이터 웨어하우스인 경우입니다. 그렇지 않으면 DAX [CALENDAR](/dax/calendar-function-dax) 또는 [CALENDARAUTO](/dax/calendarauto-function-dax) 함수를 사용하여 모델에서 날짜 테이블을 생성할 수 있습니다. 그런 다음 계산된 열을 추가하여 알려진 시간 필터링 및 그룹화 요구 사항을 지원할 수 있습니다. 이 디자인 방법을 사용하면 모든 팩트 유형 테이블로 전파되는 단일 날짜 테이블을 만들어 시간 필터를 적용하는 단일 테이블을 만들 수 있습니다. 날짜 테이블을 만드는 방법에 대한 자세한 내용은 [Power BI Desktop에서 날짜 테이블 설정 및 사용](../transform-model/desktop-date-tables.md) 문서를 참조하세요.

_자동 날짜/시간_ 옵션이 프로젝트와 관련이 없는 경우 전역 _자동 날짜/시간_ 옵션을 사용하지 않도록 설정하는 것이 좋습니다. 그러면 새로 만드는 Power BI Desktop 파일은 모두 _자동 날짜/시간_ 옵션을 사용하지 않도록 설정됩니다.

## <a name="next-steps"></a>다음 단계

이 문서와 관련된 보다 자세한 내용을 알아보려면 다음 리소스를 참조하세요.

- [Power BI Desktop에서 날짜 테이블 만들기](model-date-tables.md)
- [Power BI Desktop의 자동 날짜/시간](../transform-model/desktop-auto-date-time.md)
- [Power BI Desktop에서 날짜 테이블 설정 및 사용](../transform-model/desktop-date-tables.md)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)
