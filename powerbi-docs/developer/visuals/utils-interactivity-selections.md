---
title: Power BI 시각적 개체 InteractivityUtils
description: 이 문서에서는 InteractivityUtils를 사용하여 Power BI 시각적 개체에 선택 항목을 추가하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 02/24/2020
ms.openlocfilehash: 3614505cec185779bce3f63c6e7a565a5ef39443
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920892"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Power BI 시각적 개체 InteractivityUtils

`InteractivityUtils`는 교차 선택 및 교차 필터링 구현을 간소화하는 데 사용할 수 있는 함수와 클래스의 세트입니다.

> [!NOTE]
> 새로 업데이트된 InteractivityUtils는 최신 버전(3.x.x 이상)의 도구만 지원합니다.

## <a name="installation"></a>설치

1. 패키지를 설치하려면 현재 Power BI 시각적 개체 프로젝트가 있는 디렉터리에서 다음 명령을 실행합니다.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. 버전 3.0 이상 또는 도구를 사용하는 경우 `powerbi-models`를 설치하여 종속성을 해결합니다.

    ```bash
    npm install powerbi-models --save
    ```

3. InteractivityUtils를 사용하려면 Power BI 시각적 개체의 소스 코드에 필요한 구성 요소를 가져옵니다.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>CSS 파일 포함

Power BI 시각적 개체에서 패키지를 사용하려면 다음 CSS 파일을 `.less` 파일로 가져옵니다.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Power BI 시각적 개체 도구는 외부 CSS 규칙을 래핑하여 CSS 파일을 `.less` 파일로 가져옵니다.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>SelectableDataPoint 속성

일반적으로 데이터 요소는 선택 항목과 값을 포함합니다. 이 인터페이스는 `SelectableDataPoint` 인터페이스를 확장합니다.

`SelectableDataPoint`에는 아래에 설명된 속성이 이미 있습니다.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>데이터 요소에 대한 인터페이스 정의

1. InteractivityUtils의 인스턴스를 만들고 개체를 시각적 개체의 속성으로 저장합니다.

    ```typescript
    export class Visual implements IVisual {
      // ...
      private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
      // ...
      constructor(options: VisualConstructorOptions) {
          // ...
          this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
          // ...
      }
    }
    ```

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }
    ```

2. 기본 동작 클래스를 확장합니다.

    > [!NOTE]
    > `BaseBehavior`는 [5.6.x 버전의 InteractivityUtils](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0)에서 도입되었습니다. 이전 버전을 사용하는 경우 아래 샘플에서 동작 클래스를 만듭니다.

3. 동작 클래스의 옵션에 대한 인터페이스를 정의합니다.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. `visual behavior`의 클래스를 정의합니다. 또는 `BaseBehavior` 클래스를 확장합니다.

    **`visual behavior`에 대한 클래스 정의**

    이 클래스는 `click`, `contextmenu` 마우스 이벤트를 처리합니다.

    데이터 요소를 클릭하는 경우 시각적 개체가 선택 처리기를 호출하여 데이터 요소를 선택합니다. 시각적 개체의 백그라운드 요소를 클릭하면 선택 항목 지우기 처리기가 호출됩니다.

    이 클래스에는 다음과 같은 상응하는 메서드가 있습니다.
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
        protected options: BaseBehaviorOptions<SelectableDataPointType>;
        protected selectionHandler: ISelectionHandler;
    
        protected bindClick() {
          // ...
        }
    
        protected bindClearCatcher() {
          // ...
        }
    
        protected bindContextMenu() {
          // ...
        }
    
        public bindEvents(
            options: BaseBehaviorOptions<SelectableDataPointType>,
            selectionHandler: ISelectionHandler): void {
          // ...
        }
    
        public renderSelection(hasSelection: boolean): void {
          // ...
        }
    }
    ```

    **`BaseBehavior` 클래스 확장**

    ```typescript
    import powerbi from "powerbi-visuals-api";
    import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }

    export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
      // ...
    }
    ```

5. 요소에 대한 클릭을 처리하려면 *d3* 선택 개체 `on` 메서드를 호출합니다. 이것은 `elementsSelection` 및 `clearCatcherSelection`에도 적용됩니다.

    ```typescript
    protected bindClick() {
      const {
          elementsSelection
      } = this.options;
    
      elementsSelection.on("click", (datum) => {
          const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
          mouseEvent && this.selectionHandler.handleSelection(
              datum,
              mouseEvent.ctrlKey);
      });
    }
    ```

6. `contextmenu` 이벤트에 대한 유사한 처리기를 추가하여 선택 관리자의 `showContextMenu` 메서드를 호출합니다.

    ```typescript
    protected bindContextMenu() {
        const {
            elementsSelection
        } = this.options;
    
        elementsSelection.on("contextmenu", (datum) => {
            const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
            if (event) {
                this.selectionHandler.handleContextMenu(
                    datum,
                    {
                        x: event.clientX,
                        y: event.clientY
                    });
                event.preventDefault();
            }
        });
    }
    ```

7. 처리기에 함수를 할당하기 위해 InteractivityUtils는 `bindEvents` 메서드를 호출합니다. `bindEvents` 메서드에 다음 호출을 추가합니다.
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

    ```typescript
      public bindEvents(
          options: BaseBehaviorOptions<SelectableDataPointType>,
          selectionHandler: ISelectionHandler): void {

          this.options = options;
          this.selectionHandler = selectionHandler;

          this.bindClick();
          this.bindClearCatcher();
          this.bindContextMenu();
      }
    ```

8. `renderSelection` 메서드는 차트에 있는 요소의 시각적 상태를 업데이트해야 합니다. 다음은 `renderSelection`의 샘플 구현입니다.

    ```typescript
    public renderSelection(hasSelection: boolean): void {
        this.options.elementsSelection.style("opacity", (category: any) => {
            if (category.selected) {
                return 0.5;
            } else {
                return 1;
            }
        });
    }
    ```

9. 마지막 단계는 `visual behavior`의 인스턴스를 만들고 InteractivityUtils 인스턴스의 `bind` 메서드를 호출하는 것입니다.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge`는 *d3* 선택 개체로서, 시각적 개체에서 선택할 수 있는 모든 요소를 나타냅니다.
    * `select(this.target)`은 *d3* 선택 개체로서, 시각적 개체의 기본 DOM 요소를 나타냅니다.
    * `this.categories`는 요소가 포함된 데이터 요소로서, 인터페이스는 `VisualDataPoint` 또는 `categories: VisualDataPoint[];`입니다.
    * `this.behavior`는 다음과 같이 시각적 개체의 생성자에 생성된 `visual behavior`의 새 인스턴스입니다.

      ```typescript
      export class Visual implements IVisual {
        // ...
        constructor(options: VisualConstructorOptions) {
            // ...
            this.behavior = new Behavior();
        }
        // ...
      }
      ```
## <a name="next-steps"></a>다음 단계

* [책갈피 전환에서 선택 항목을 처리하는 방법 읽기](bookmarks-support.md#visuals-with-selection)

* [시각적 개체 데이터 요소에 대한 상황에 맞는 메뉴를 추가하는 방법 읽기](context-menu.md)

* [선택 관리자를 사용하여 Power BI 시각적 개체에 선택 항목을 추가하는 방법 읽기](selection-api.md)
