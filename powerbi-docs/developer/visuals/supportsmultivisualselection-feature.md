---
title: supportsMultiVisualSelection 기능
description: 이 문서에서는 Power BI 시각적 개체 및 해당 요구 사항에서 supportsMultiVisualSelection 기능을 사용하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272698"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>supportsMultiVisualSelection 기능 사용

`supportsMultiVisualSelection` 기능을 사용하면 보고서의 여러 시각적 개체에서 선택 항목을 사용할 수 있습니다.

## <a name="example"></a>예제

둘 이상의 시각적 개체를 포함하는 보고서에서 두 값을 선택하여 다른 시각적 개체에 해당 값이 적용되도록 합니다. 예를 들어 [소매점 분석 샘플](../../create-reports/sample-retail-analysis.md)에서 한 시각적 개체에서 **패션 직판**을 선택합니다. Ctrl 키를 선택하고 다른 시각적 개체에서 **1월**을 선택합니다. 보고서에서 선택 항목이 이 기능 사용을 지원하는 다른 시각적 개체에 적용됩니다. 다른 시각적 개체는 이제 **패션 직판** 및 **1월**로 범위가 지정됩니다.

## <a name="requirements"></a>요구 사항

이 기능을 사용하려면 API v3.2.0 이상이 필요합니다.

이미지 시각적 개체에는 이 기능을 적용할 수 없습니다. 주요 동인, 분해 트리, 질문 및 대답 시각적 개체, 텍스트 상자 및 계기 차트와 같은 고급 시각적 개체에는 적용할 수 없습니다.

## <a name="usage"></a>사용량

`supportsMultiVisualSelection` 기능을 사용하려면 시각적 개체의 `capabilities.json` 파일에 다음 코드를 추가합니다.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>다음 단계

Power BI 개념에 대한 자세한 내용은 [Power BI의 시각적 개체](power-bi-visuals-concept.md)를 참조하세요.

Power BI 개발을 시도하려면 [Power BI 시각적 개체 개발](custom-visual-develop-tutorial.md)을 참조하세요.
