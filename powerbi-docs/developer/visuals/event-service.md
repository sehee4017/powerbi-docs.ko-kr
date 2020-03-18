---
title: Power BI 시각적 개체의 렌더링 이벤트
description: Power BI 시각적 개체는 PowerPoint 또는 PDF로 내보낼 준비가 되었음을 Power BI에 알릴 수 있습니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: c54aaa92f3463ce1102866c8d3b69532c8b25cf7
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380252"
---
# <a name="render-events-in-power-bi-visuals"></a>Power BI 시각적 개체의 렌더링 이벤트

새 API는 렌더링 중에 호출되어야 하는 세 가지 메서드(`started`, `finished` 또는 `failed`)로 구성됩니다.

렌더링이 시작되면 Power BI 시각적 개체 코드에서 `renderingStarted` 메서드를 호출하여 렌더링 프로세스가 시작되었음을 알립니다.

렌더링이 성공적으로 완료되면 Power BI 시각적 개체 코드에서 즉시 `renderingFinished` 메서드를 호출하여 시각적 개체 이미지를 내보낼 준비가 되었음을 수신기(주로 ‘PDF로 내보내기’ 및 ‘PowerPoint로 내보내기’)에 알립니다.  

프로세스 중에 문제가 발생하면 Power BI 시각적 개체가 렌더링되지 않습니다. 렌더링 프로세스가 완료되지 않았음을 수신기에 알리려면, Power BI 시각적 개체 코드에서 `renderingFailed` 메서드를 호출해야 합니다. 이 메서드는 실패 이유를 나타내는 선택적 문자열도 제공합니다.

## <a name="usage"></a>사용량

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>샘플: 시각적 개체가 애니메이션을 표시하지 않음

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>샘플: 시각적 개체가 애니메이션을 표시함

시각적 개체에 렌더링할 애니메이션이나 비동기 함수가 있는 경우, 애니메이션 이후 또는 비동기 함수 내에서 `renderingFinished` 메서드를 호출해야 합니다.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>시각적 개체 인증을 위한 렌더링 이벤트

시각적 개체의 렌더링 이벤트 지원은 시각적 개체 인증 요구 사항 중 하나입니다. 자세한 내용은 [인증 요구 사항](power-bi-custom-visuals-certified.md#certification-requirements)을 참조하세요.