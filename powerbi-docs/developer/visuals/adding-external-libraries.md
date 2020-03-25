---
title: Power BI 시각적 개체에 외부 라이브러리 추가
description: 이 문서에서는 Power BI 시각적 개체에서 외부 라이브러리를 사용하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: 9df111e7545c43fe9b75784b1a95df4f37fd01e7
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114132"
---
# <a name="adding-external-libraries"></a>외부 라이브러리 추가

이 문서에서는 Power BI 시각적 개체에서 외부 라이브러리를 사용하는 방법을 설명합니다. 여기에는 Power BI 시각적 개체의 코드에서 외부 라이브러리를 설치하고, 가져오고, 호출하는 방법에 대한 정보가 포함되어 있습니다.

## <a name="javascript-libraries"></a>JavaScript 라이브러리

1. *npm* 또는 *yarn*과 같은 패키지 관리자를 사용하여 외부 JavaScript 라이브러리를 설치합니다.
2. 외부 라이브러리를 사용하여 필요한 모듈을 원본 파일로 가져옵니다.

>[!NOTE]
>입력한 내용을 JavaScript 라이브러리에 추가하고 intellisense 및 컴파일 타임 안전을 얻으려면 적절한 패키지를 설치해야 합니다.

### <a name="installing-the-d3-library"></a>D3 라이브러리 설치

다음은 [npm](https://www.npmjs.com/)을 사용하여 [d3 라이브러리](https://www.npmjs.com/package/d3) 및 [@types/d3](https://www.npmjs.com/package/@types/d3) 패키지를 설치하는 예입니다.

전체 예제는 [Power BI 시각화](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29) 코드를 참조하세요.

1. *d3* 패키지와 *d3 형식* 패키지를 설치합니다.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. *d3* 라이브러리가 사용되는 파일(예: `visual.ts`)로 이 라이브러리를 가져옵니다.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS 프레임워크

1. *npm* 또는 *yarn*과 같은 패키지 관리자를 사용하여 외부 CSS 프레임워크를 설치합니다.
2. 시각적 개체의 `.less` 파일에 `import` 문을 포함합니다.

### <a name="installing-bootstrap"></a>부트스트랩 설치

[npm](https://www.npmjs.com/)을 사용하여 [부트스트랩](https://www.npmjs.com/package/bootstrap)을 설치하는 예입니다.

전체 예제는 [Power BI 시각화](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32) 코드를 참조하세요.

1. *부트스트랩* 패키지를 설치합니다.

    ```powershell
    npm install bootstrap --save
    ```

2. `visual.less`에 `import` 문을 포함합니다.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
