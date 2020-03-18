---
title: Power BI 시각적 개체에서 도구 설명 유틸리티를 사용하는 방법 소개
description: 이 문서에서는 Power BI 시각적 개체에 대한 도구 설명 사용자 지정을 간소화하는 도구 설명 유틸리티 사용 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 67470ec405806f44fdb483e857d222ad4ff05a45
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379171"
---
# <a name="tooltip-utils"></a>도구 설명 유틸리티
이 문서는 도구 설명 유틸리티를 설치하고, 가져오고, 사용하는 데 도움이 됩니다. 이 유틸리티는 Power BI 시각적 개체의 도구 설명 사용자 지정에 유용합니다.

## <a name="requirements"></a>요구 사항
이 패키지를 사용하려면 다음과 같은 항목이 있어야 합니다.
* [node.js](https://nodejs.org)(최신 LTS 버전 권장)
* [npm](https://www.npmjs.com/)(지원되는 최소 버전은 3.0.0)
* [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)로 만들어진 사용자 지정 시각적 개체

## <a name="installation"></a>설치

패키지를 설치하려면 현재 시각적 개체가 있는 디렉터리에서 다음 명령을 실행해야 합니다.

```bash
npm install powerbi-visuals-utils-colorutils --save
```
이 명령은 패키지를 설치하고 ```package.json```에 대한 종속성으로 패키지를 추가합니다.

## <a name="usage"></a>사용량

> 사용 가이드에서는 패키지의 공용 API를 설명합니다. 패키지의 각 공용 인터페이스에 대한 설명과 몇 가지 예제를 찾을 수 있습니다.

이 패키지에서는 도구 설명 작업을 처리하는 데 도움이 되는 `TooltipServiceWrapper` 및 메서드를 만드는 방법을 제공합니다. 다음 도구 설명 인터페이스가 사용됩니다. `ITooltipServiceWrapper`, `TooltipEventArgs`, `TooltipEnabledDataPoint`. 

또한 모바일 개발과 관련된 특정 메서드(터치 이벤트 처리기)도 있습니다. `touchEndEventName`, `touchStartEventName`, `usePointerEvents`.

`TooltipServiceWrapper`는 도구 설명을 조작하기 위한 가장 간단한 방법을 제공합니다.

이 모듈에서는 다음 인터페이스 및 함수를 제공합니다.
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [인터페이스](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Touch events](#touch-events)

### `createTooltipServiceWrapper`
이 함수는 ITooltipServiceWrapper의 인스턴스를 만듭니다.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

```ITooltipService```는 [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335)에서 사용할 수 있습니다.

**예제**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

[여기](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391)에서 사용자 지정 시각적 개체의 예제 코드를 살펴보세요.

### `ITooltipServiceWrapper`
이 인터페이스는 Tooltipservice의 공용 메서드를 설명합니다.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

이 메서드는 현재 선택 항목에 도구 설명을 추가합니다.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**예제**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

[여기](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931)에서 사용자 지정 시각적 개체의 예제 코드를 살펴보세요.

또한 [여기](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)에서 Gantt 사용자 지정 시각적 개체의 도구 설명 사용자 지정에 대한 다음 예제도 참조하세요.

### `ITooltipServiceWrapper.hide`

이 메서드는 도구 설명을 숨깁니다.

```typescript
hide(): void;
```

**예제**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
이들 인터페이스는 TooltipServiceWrapper를 만들고 사용하는 동안 사용됩니다. 또한 이들은 이전 항목의 예제에서도 언급되었습니다([여기](#itooltipservicewrapperaddtooltip)).

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

이제 도구 설명 유틸리티는 모바일 개발에 유용한 여러 터치 이벤트를 처리할 수 있습니다.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
이 메서드는 터치 시작 이벤트 이름을 반환합니다.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
이 메서드는 터치 시작 이벤트 이름을 반환합니다.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
이 메서드는 현재 touchStart 이벤트가 포인터와 관련되는지 여부를 반환합니다.
