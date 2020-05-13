---
title: 모바일 개발
description: 모바일 친화적인 Power BI 시각적 개체를 만드는 방법
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196632"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>모바일 친화적인 Power BI 시각적 개체를 만드는 방법
모바일 사용은 Power BI에서 중요한 역할을 합니다. 그 장점 중 하나는 언제 어디서나 데이터에 연결되어 있다는 것입니다.

Power BI 시각적 개체를 만드는 개발자는 가능한 한 많은 사용자에게 도달하고 최상의 모바일 환경을 제공하기 위해 각 모바일 디바이스의 고유한 제약 조건을 처리해야 합니다.

[Windows, iOS 및 Android용 Power BI 앱](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices)을 사용하여 비즈니스 사용자가 손가락 끝 터치를 통해 이동 중인 데이터를 포괄적으로 볼 수 있습니다.

## <a name="requirements"></a>요구 사항

모바일 친화적인 시각적 개체를 개발하는 데 요구 사항은 다음과 같습니다.

- 렌더링

  Power BI 시각적 개체는 보고서, 대시보드 또는 **포커스** 모드에서 실행되는 경우에서 오류 없이 지원되는 모든 모바일 디바이스(지원되는 브라우저 및 애플리케이션 포함)에서 렌더링해야 합니다. 

- 대화형

  대화형 기능은 데스크톱 디바이스에 제공되는 것과 동일한 방식으로 제공되어야 합니다. 데스크톱 브라우저에서 처리되는 모든 이벤트를 지원하거나 모바일 디바이스와 비슷한 이벤트 처리기가 있어야 합니다.
  
  예를 들어 기본 탐색 및 데이터 요소 선택은 데스크톱 브라우저의 기능과 동일해야 합니다. 시각적 개체에서 **Ctrl**을 사용하여 다중 선택을 지원하는 경우 개발자는 비슷한 이벤트 처리기를 모바일 디바이스에 추가하는 것을 고려해야 합니다.

  다음 표에는 모바일 디바이스에 해당하는 이벤트 목록이 나와 있습니다.

  | 마우스 이벤트 이름 | 터치 이벤트 이름 |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | 외부 라이브러리 사용 |
  | `contextmenu` | 외부 라이브러리 사용 |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove`(또는 외부 라이브러리) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > 일부 모바일 또는 터치 스크린 디바이스는 마우스(또는 *mouse* 접두사 사용) 이벤트를 지원하지 않습니다. 이러한 경우 *마우스* 및 *터치* 이벤트 모두를 동시에 처리합니다.

## <a name="optional"></a>선택 사항
다음은 선택 사항으로 간주되며 더 나은 최종 사용자 환경을 만드는 데 사용됩니다.

- 렌더링

  더 작은 시각적 개체 크기를 지원하려면 사용자가 변경할 수 있는 서식 옵션을 추가하여 각 요소의 크기를 조정합니다. 예를 들어 보고서 및 대시보드에서 사용할 수 있도록 서식 옵션을 레이블에 추가합니다. 이를 통해 사용자는 모바일 디바이스에 맞게 시각적 개체를 구체적으로 사용자 지정할 수 있습니다.
  
  데스크톱 브라우저의 시각적 개체에도 동일한 설정을 적용할 수 있으며, 필요한 경우 시각적 개체를 더 작은 화면으로 조정하도록 재정의할 수 있습니다.

  > [!NOTE]
  > **포커스** 모드에서 시각적 개체를 최적화하려면 세로 및 가로 화면 크기 방향을 모두 고려해야 합니다. [포커스 모드에서 콘텐츠 표시](/power-bi/consumer/end-user-focus)를 참조하세요.

- 대화형

  끌기 및 스크롤과 같은 모바일 특정 이벤트 처리기를 추가하는 것이 좋습니다.

- 장애 조치 

  모바일 디바이스에서 렌더링할 수 없는 경우 시각적 개체에 설명이 포함된 오류가 표시됩니다.

## <a name="supported-browsers-and-devices"></a>지원되는 브라우저 및 디바이스
Power BI 시각적 개체는 Power BI 앱을 지원하는 모든 디바이스에서 렌더링해야 합니다. 자세한 내용은 [Power BI에 지원되는 브라우저](/power-bi/power-bi-browsers) 및 [Power BI 모바일 앱](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices)을 참조하세요.

최신 Windows, iOS 및 Android 디바이스 모델을 테스트할 때 개발자는 이러한 품질 측면의 대부분을 고려해야 합니다.

## <a name="next-steps"></a>다음 단계
시작하려면 [자습서: Power BI 시각적 개체 개발](/power-bi/developer/visuals/custom-visual-develop-tutorial)을 참조하세요.
