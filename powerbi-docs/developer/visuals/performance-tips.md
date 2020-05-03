---
title: 성능 팁
description: 고성능 Power BI 시각적 개체를 빌드하는 방법
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: 7ebc02b2c459517957425e78438e12e89dc2e1bb
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196563"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>고성능 Power BI 시각적 개체를 빌드하는 방법
이 문서에서는 시각적 개체를 렌더링할 때 개발자가 고성능을 달성할 수 있는 방법에 대한 기술을 설명합니다. 

시각적 개체의 렌더링에서 시간이 소모되는 것을 원하는 사람이 없으며, 렌더링할 때 코드에서 벗어날 수 있는 모든 성능 저하를 최소화하는 것이 중요합니다. 

> [!NOTE]
> 플랫폼이 지속적으로 개선되고 향상됨에 따라 새 버전의 API도 지속적으로 릴리스되고 있습니다. Power BI 시각적 개체의 플랫폼과 기능 세트를 최대한 활용하려면 최신 버전으로 최신 상태를 유지하는 것이 좋습니다.
>
> 최신의 **2.1 버전** 이후 Power BI 시각적 개체 로드 시간이 평균 20% 향상되었습니다.

## <a name="power-bi-visual-performance-tips"></a>Power BI 시각적 개체 성능 팁
최적의 시각적 개체 성능을 얻는 방법에 대한 몇 가지 추천 사항은 다음과 같습니다. 

### <a name="use-user-timing-api"></a>사용자 타이밍 API 사용
**사용자 타이밍 API**를 사용하여 앱의 JavaScript 성능을 측정하면 최적화가 필요한 스크립트 부분을 결정하는 데 도움이 될 수 있습니다.

자세한 내용은 [사용자 타이밍 API](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx)를 참조하세요.

### <a name="review-animation-loops"></a>애니메이션 루프 검토
애니메이션 루프에서 변경되지 않은 요소를 다시 그리나요? 

 - 문제: 프레임마다 변경되지 않는 요소를 그리는 데 시간이 낭비됩니다.

 - 해결 방법: 프레임을 선택적으로 업데이트 합니다. 
 
정적 시각화에 애니메이션을 적용하는 경우 그리기 코드를 하나의 업데이트 함수로 일괄로 묶고 애니메이션 루프의 각 반복에 대해 새 데이터를 사용하여 반복적으로 호출하는 것이 좋습니다.

대신 다음 업데이트 패턴을 고려하고, 시각적 개체 생성자 메서드를 사용하여 모든 정적 요소를 그린 다음, 업데이트 언어 함수에서 변경되는 시각화 요소만 그려야 합니다. 

   > [!TIP]
   > 비효율적인 애니메이션 루프는 일반적으로 축과 범례에서 발견됩니다.

### <a name="cache-dom-nodes"></a>DOM 노드 캐시 
DOM에서 노드 또는 노드 목록을 검색할 때 나중에 계산에서 다시 사용할 수 있는지 여부를 고려해야 합니다(경우에 따라 다음 루프 반복까지). 관련 영역에서 노드를 추가하거나 삭제할 필요가 없는 한 노드를 캐시하여 애플리케이션의 전체 효율성이 향상될 수 있습니다.

코드가 빠르고 브라우저 속도를 늦추지 않도록 DOM 액세스를 최소한으로 유지합니다. 

- 이전: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- 이후: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>DOM 조작 방지 
DOM 조작을 최대한 제한합니다.  `prepend()`, `append()` 및 `after()`와 같은 삽입 작업은 시간이 많이 걸리므로 필요한 경우에만 사용해야 합니다.

예를 들면 다음과 같습니다.

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

위의 예제에서는 `html()`을 사용하여 목록을 미리 작성하여 가속화할 수 있습니다. 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>JQuery 재검토

가능할 때마다 JS 프레임워크를 제한하고 네이티브 JS를 사용하면 사용 가능한 대역폭을 늘리고 처리 오버헤드를 낮출 수 있습니다. 이 경우 이전 브라우저와의 호환성 문제도 제한할 수 있습니다. 

JQuery의 `show`, `hide`, `addClass` 등과 같은 함수에 대한 대체 예제와 관련된 자세한 내용은 [youmightnotneedjquery.com](http://youmightnotneedjquery.com/)을 참조하세요.  

### <a name="use-canvas-or-webgl"></a>캔버스 또는 WebGL 사용 
애니메이션을 반복적으로 사용하려면 SVG 대신 **Canvas** 또는 **WebGL**을 사용하는 것이 좋습니다. SVG와 달리 이러한 옵션을 사용하면 성능이 콘텐츠가 아니라 크기에 따라 결정됩니다. 

[SVG 및 canvas: 선택 방법](https://msdn.microsoft.com/library/gg193983(v=vs.85).aspx)에서 차이점에 대해 자세히 알아볼 수 있습니다. 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>setTimeout 대신 requestAnimationFrame 사용 
[requestAnimationFrame](https://www.w3.org/TR/animation-timing/)을 사용하여 화상 애니메이션을 업데이트하는 경우 브라우저에서 다른 다시 그리기를 호출하기 **전에** 애니메이션 함수가 호출됩니다.

`requestAnimationFrame`을 사용하는 부드러운 애니메이션에 대한 자세한 내용은 이 [샘플](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html)을 참조하세요.

## <a name="next-steps"></a>다음 단계

[Power BI 최적화 가이드](/power-bi/guidance/power-bi-optimization)에서 최적화 기술에 대해 자세히 알아보세요.
