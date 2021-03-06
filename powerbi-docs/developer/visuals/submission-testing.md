---
title: Power BI 시각적 개체 제출 테스트
description: 이 문서에서는 AppSource에 게시하기 전에 시각적 개체가 통과해야 하는 테스트 사례에 대해 설명합니다. 또한 옵션 테스트 사례도 있습니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: 515813aeb98010f838cfff75febbb1ef206bc2cf
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94397487"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>Power BI 시각적 개체 제출 테스트

시각적 개체를 [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)에 게시하기 전에 시각적 개체가 이 도움말에 나온 테스트를 통과해야 합니다. 시각적 개체를 제출 전에 테스트하세요. 필요한 테스트 사례를 통과하지 않은 시각적 개체는 거부됩니다.

게시 프로세스에 대한 자세한 내용은 [파트너 센터에 Power BI 시각적 개체 게시](./office-store.md)를 참조하세요.

## <a name="testing-a-new-version-of-a-published-visual"></a>게시된 시각적 개체의 새 버전 테스트

이미 게시된 시각적 개체의 새 버전을 테스트하거나 디버그하는 경우 Power BI Desktop에서 개발자 모드를 사용하도록 설정하면 AppSource 버전을 로컬 파일 버전으로 재정의할 수 있습니다.

개발자 모드를 사용하도록 설정하려면 다음 단계를 수행합니다.

1. Power BI Desktop을 엽니다.

2.  **파일** > **옵션 및 설정** 을 선택합니다.

3.  **옵션** 을 선택합니다.

4. 옵션 창의 현재 파일 목록에서 **보고서 설정** 을 선택합니다.

5. 개발자 모드에서 **Turn on developer mode for this session**(이 세션에 개발자 모드 설정) 옵션을 선택합니다.

>[!NOTE]
>Power BI Desktop에서 개발자 모드는 한 세션에 대해서만 유효합니다. 테스트를 위해 새 Power BI Desktop 인스턴스를 여는 경우 개발자 모드를 다시 사용하도록 설정해야 합니다.

## <a name="general-test-cases"></a>일반 테스트 사례

시각적 개체가 일반 테스트 사례를 통과하는지 확인합니다.

| 테스트 사례 | 예상 결과
| --------- | ----------------
| **범주** 및 **값** 을 사용하여 **누적 세로 막대형 차트** 를 만듭니다. 이 항목을 시각적 개체로 변환했다가 다시 세로 막대형 차트로 변환합니다. | 이러한 변환 후 오류가 표시되지 않습니다. |
| 세 개의 측정값이 있는 **계기** 를 만듭니다. 이 항목을 시각적 개체로 변환했다가 다시 **계기** 로 변환합니다. | 이러한 변환 후 오류가 표시되지 않습니다. |
| 시각적 개체에서 항목을 선택합니다. | 다른 시각적 개체가 선택 항목을 반영합니다. |
| 다른 시각적 개체의 요소를 선택합니다. | 시각적 개체가 다른 시각적 개체의 선택 항목에 따라 필터링된 데이터를 표시합니다. |
| 최소/최대 **dataViewMapping** 조건을 확인합니다. | 필드 버킷은 여러 필드 또는 단일 필드를 사용할 수도 있고 다른 버킷에 의해 결정될 수도 있습니다. 최소/최대 **dataViewMapping** 조건이 시각적 개체의 기능에 올바르게 설정되어 있어야 합니다. |
| 모든 필드를 다양한 순서로 제거합니다. | 필드가 임의의 순서로 제거될 때 시각적 개체가 올바르게 표시됩니다. 콘솔 또는 브라우저에 오류가 없습니다. |
| 가능한 각 버킷 구성으로 **형식** 창을 엽니다. | 이 테스트는 null 참조 예외를 트리거하지 않습니다. |
| **필터** 창을 사용하여 시각적 개체, 페이지 및 보고서 수준에서 데이터를 필터링합니다. | 필터를 적용한 후 도구 설명이 올바릅니다. 도구 설명이 필터링된 값을 표시합니다. |
| **슬라이서** 를 사용하여 데이터를 필터링합니다. | 필터를 적용한 후 도구 설명이 올바릅니다. 도구 설명이 필터링된 값을 표시합니다. |
| 게시된 시각적 개체를 사용하여 데이터를 필터링합니다. 예를 들어 원형 조각 또는 열을 선택합니다. | 필터를 적용한 후 도구 설명이 올바릅니다. 도구 설명이 필터링된 값을 표시합니다. |
| 교차 필터링이 지원되는 경우 필터가 제대로 작동하는지 확인합니다. | 적용된 선택이 보고서의 이 페이지에 있는 다른 시각적 개체를 필터링합니다. |
| Ctrl, Alt 및 Shift 키를 사용하여 선택합니다. | 예기치 않은 동작이 표시되지 않습니다. |
| **보기 모드** 를 **실제 크기**, **페이지에 맞추기** 및 **너비에 맞추기** 로 변경합니다. | 마우스 좌표가 정확합니다. |
| 시각적 개체의 크기를 조정합니다. | 시각적 개체가 크기 조정에 올바르게 반응합니다. |
| 보고서 크기를 최소로 설정합니다. | 표시 오류가 없습니다. |
| 스크롤 막대가 제대로 작동하는지 확인합니다. | 필요한 경우 스크롤 막대가 존재해야 합니다. 스크롤 막대 크기를 확인합니다. 스크롤 막대가 너무 넓거나 길지 않아야 합니다. 스크롤 막대의 위치 및 크기가 시각적 개체의 다른 요소와 조화를 이루어야 합니다. 시각적 개체의 여러 크기에 스크롤 막대가 필요한지 확인합니다. |
| 시각적 개체를 **대시보드** 에 고정합니다. | 시각적 개체가 올바르게 표시되어야 합니다. |
| 단일 보고서 페이지에 여러 버전의 시각적 개체를 추가합니다. | 모든 버전의 시각적 개체가 올바르게 표시되고 작동합니다. |
| 여러 버전의 시각적 개체를 여러 보고서 페이지에 추가합니다. | 모든 버전의 시각적 개체가 올바르게 표시되고 작동합니다. |
| 보고서 페이지 사이를 전환합니다. | 시각적 개체가 올바르게 표시됩니다. |
| 시각적 개체의 읽기용 보기 및 편집용 보기를 테스트합니다. | 모든 함수가 제대로 작동합니다. |
| 시각적 개체가 애니메이션을 사용하는 경우 시각적 개체의 요소를 추가, 변경 및 삭제합니다. | 시각적 요소의 애니메이션이 제대로 작동합니다. |
| **속성** 창을 엽니다. 속성을 설정 및 해제하고 사용자 지정 텍스트를 입력하며 사용 가능한 옵션을 강조하고 잘못된 데이터를 입력합니다. | 시각적 개체가 올바르게 응답합니다. |
| 보고서를 저장했다가 다시 엽니다. | 모든 속성 설정이 유지됩니다. |
| 보고서에서 페이지를 바꿨다가 다시 돌아갑니다. | 모든 속성 설정이 유지됩니다. |
| 시각적 개체가 제공하는 다양한 옵션을 포함하여 시각적 개체의 모든 기능을 테스트합니다. | 모든 표시 및 기능이 제대로 작동합니다. |
| 다음 테스트와 같이 모든 숫자, 날짜 및 문자 데이터 형식을 테스트합니다. | 모든 데이터의 서식이 올바릅니다. |
| 서식이 지정된 도구 설명 값, 축 레이블, 데이터 레이블 및 기타 시각적 요소의 서식을 검토합니다. | 모든 요소의 서식이 올바릅니다. |
| 데이터 레이블이 서식 문자열을 사용하는지 확인합니다. | 모든 데이터 레이블의 서식이 올바릅니다. |
| 도구 설명의 숫자 값에 대해 자동 서식을 설정하고 해제합니다. | 도구 설명이 값을 올바르게 표시합니다. |
| 숫자, 텍스트, 날짜-시간, 모델의 다양한 서식 문자열을 포함하여 다양한 데이터 형식을 갖는 데이터 항목을 테스트합니다. 수천 개의 행, 한 행, 두 행과 같은 다양한 데이터 볼륨을 테스트합니다. | 모든 표시 및 기능이 제대로 작동합니다. |
| Null, 무한대, 음수 값, 잘못된 값 형식과 같은 잘못된 데이터를 시각적 개체에 제공합니다. | 모든 표시 및 기능이 제대로 작동합니다. |

## <a name="optional-browser-testing"></a>선택적 브라우저 테스트

AppSource 팀은 최신 Windows 버전의 Google Chrome, Microsoft Edge 및 Mozilla Firefox 브라우저에서 시각적 개체의 유효성을 검사합니다.
필요에 따라 다음 브라우저에서 시각적 개체를 테스트합니다.

| 테스트 사례 | 예상 결과
| --------- | ----------------
| **Windows** |
| Google Chrome(이전 버전) | 모든 표시 및 기능이 제대로 작동합니다. |
| Mozilla Firefox(이전 버전) | 모든 표시 및 기능이 제대로 작동합니다. |
| Microsoft Edge(이전 버전) | 모든 표시 및 기능이 제대로 작동합니다. |
| Microsoft Internet Explorer 11(선택 사항) | 모든 표시 및 기능이 제대로 작동합니다. |
| **macOS** |
| Chrome(이전 버전) | 모든 표시 및 기능이 제대로 작동합니다. |
| Firefox(이전 버전) | 모든 표시 및 기능이 제대로 작동합니다. |
| Safari(이전 버전) | 모든 표시 및 기능이 제대로 작동합니다. |
| **Linux** |
| Firefox(최신 버전 및 이전 버전) | 모든 표시 및 기능이 제대로 작동합니다. |
| **Mobile iOS** |
| Apple Safari iPad(이전 Safari 버전) | 모든 표시 및 기능이 제대로 작동합니다. |
| Chrome iPad(최신 Safari 버전) | 모든 표시 및 기능이 제대로 작동합니다. |
| **Mobile Android** |
| Chrome(최신 버전 및 이전 버전) | 모든 표시 및 기능이 제대로 작동합니다. |

## <a name="desktop-testing"></a>Desktop 테스트

현재 버전의 [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/)에서 시각적 개체를 테스트합니다.

| 테스트 사례 | 예상 결과
| --------- | ----------------
| 시각적 개체의 모든 기능을 테스트합니다. | 모든 표시 및 기능이 제대로 작동합니다. |
| Power BI Desktop의 **게시** 단추를 사용하여 파일을 가져오고, 저장하고, 열고, Power BI 웹 서비스에 게시합니다. | 모든 표시 및 기능이 제대로 작동합니다. |
| 전체 자릿수를 늘리거나 줄여 소수 자릿수를 0~3자리로 지정하면서 숫자 형식 문자열을 변경합니다. | 시각적 개체가 올바르게 표시됩니다. |

## <a name="performance-testing"></a>성능 테스트

시각적 개체가 적절한 수준의 성능을 제공해야 합니다. 개발자 도구를 사용하여 성능을 확인합니다. 시각적 신호와 콘솔 시간 로그에 의존하지 마세요.

| 테스트 사례 | 예상 결과
| --------- | ----------------
| 많은 시각적 요소를 포함하는 시각적 개체를 만듭니다. | 시각적 개체가 정상적으로 작동하며 애플리케이션이 중지하지 않아야 합니다. 애니메이션 속도, 크기 조정, 필터링, 선택과 같은 요소에 성능 문제가 없어야 합니다.

## <a name="next-steps"></a>다음 단계

게시 프로세스에 대한 자세한 내용은 [파트너 센터에 Power BI 시각적 개체 게시](./office-store.md)를 참조하세요.

궁금한 점이 더 있나요? [Power BI 커뮤니티에 문의하세요](https://community.powerbi.com/).
