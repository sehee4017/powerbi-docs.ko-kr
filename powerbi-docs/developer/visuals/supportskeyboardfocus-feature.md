---
title: supportsKeyboardFocus 기능
description: 이 문서에서는 Power BI 시각적 개체 및 해당 요구 사항에서 supportsKeyboardFocus 기능을 사용하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 1e5a4cf8c80d8123d39fd2ab76898abc0c439ad9
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049387"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>supportsKeyboardFocus 기능 사용

이 문서에서는 Power BI 시각적 개체에서 `supportsKeyboardFocus` 기능을 사용하는 방법을 설명합니다.
`supportsKeyboardFocus` 기능을 사용하면 시각적 개체의 데이터 요소를 키보드만 사용하여 탐색할 수 있습니다.

시각적 개체 키보드 탐색에 대해 자세히 알아보려면 [키보드 탐색](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation)을 참조하세요.

## <a name="example"></a>예제

`supportsKeyboardFocus` 기능을 사용하는 시각적 개체를 엽니다. 시각적 개체에서 데이터 요소를 선택하고 탭 키를 선택합니다. 탭 키를 선택할 때마다 포커스가 다음 데이터 요소로 이동합니다. Enter 키를 눌러 강조 표시된 데이터 요소를 선택합니다.

![키보드 포커스 지원 예제](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>요구 사항

이 기능을 사용하려면 API v2.1.0 이상이 필요합니다.

이 기능은 이미지 시각적 개체를 제외한 모든 시각적 개체에 적용할 수 있습니다.

## <a name="usage"></a>사용량

`supportsKeyboardFocus` 기능을 사용하려면 시각적 개체의 *capabilities.json* 파일에 다음 코드를 추가합니다.
이 기능을 사용하면 시각적 개체가 키보드 탐색을 통해 포커스를 받을 수 있습니다.

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>다음 단계

접근성 기능에 대한 자세한 내용은 [접근성을 지원하는 Power BI 보고서 디자인](../../create-reports/desktop-accessibility-creating-reports.md)을 참조하세요.

Power BI 개발을 수행하려면 [Power BI 원 카드 시각적 개체 개발](develop-circle-card.md)을 참조하세요.
