---
title: Power BI Embedded의 질문 및 답변
description: Power BI Embedded는 질문 및 답변을 애플리케이션에 통합하고 사용자가 자연어를 사용하여 질문할 수 있는 방법을 제공합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 11/20/2017
ms.openlocfilehash: 0106cc9ddb0e82a7b40e362342fce5196ef655c5
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91749279"
---
# <a name="qa-in-power-bi-embedded"></a>Power BI Embedded의 질문 및 답변

Power BI Embedded는 질문 및 답변을 애플리케이션에 통합하고 사용자가 자연어를 사용하여 질문하고 차트나 그래프와 같은 시각적 개체 형식으로 즉각적인 답변을 받을 수 있는 방법을 제공합니다.

![포함된 프레임의 질문 및 답변 대화형 질문](media/qanda/embedded-qanda.gif)

애플리케이션 내에 질문 및 답변을 포함하는 방법은 **대화형** 및 **결과 전용** 두 가지입니다. **대화형** 모드에서는 질문을 입력하고 시각적 개체 내에 표시할 수 있습니다. 저장된 질문이 있거나 표시하려는 질문이 있으면 embed config에 질문을 채워서 **결과 전용** 모드를 사용할 수 있습니다.

다음은 JavaScript 코드의 모습입니다.

```javascript
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnaMode.Interactive | models.QnaMode.ResultOnly,
    question:    optional parameter for Explore mode (QnaMode.Interactive) and mandatory for Render Result mode (QnaMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>설정 질문

설정 질문과 함께 **결과 전용 모드**를 사용하면 추가 질문을 프레임에 삽입하고 이전 결과를 대체하여 즉시 답변을 받도록 할 수 있습니다. 새 질문과 일치하는 새 시각적 개체가 렌더링됩니다.

이런 사용의 한 가지 예는 질문과 답변 목록입니다. 사용자가 질문을 검토하고 포함된 동일한 부분 내에 답변을 할 수 있습니다.

**JS SDK 사용을 위한 코드 조각:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>시각적 개체가 렌더링된 이벤트

**대화형** 모드의 경우 렌더링된 시각적 개체가 변경될 때마다 업데이트된 입력 쿼리를 대상으로 데이터가 변경된 이벤트를 사용하여 애플리케이션에 통지할 수 있습니다.

*visualRendered* 이벤트를 수신 대기하면 나중에 사용할 수 있도록 질문을 저장할 수 있습니다. 

**JS SDK 사용을 위한 코드 조각:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>embed 토큰

질문 및 답변 부분을 시작하려면 데이터 세트에서 embed 토큰 끄기를 만듭니다. 자세한 내용은 [토큰 생성](/rest/api/power-bi/embedtoken)을 참조하세요.

## <a name="next-steps"></a>다음 단계

질문 및 답변 포함을 시도해 보려면 [JavaScript embed 샘플](https://microsoft.github.io/PowerBI-JavaScript/demo/)을 참조하세요.

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)