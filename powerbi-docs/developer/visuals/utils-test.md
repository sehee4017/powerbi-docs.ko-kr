---
title: Power BI 시각적 개체의 테스트 유틸리티 사용 소개
description: 이 문서에서는 테스트 유틸리티를 사용하여 Power BI 시각적 개체에 대한 단위 테스트에서 모의 및 특정 메서드 사용을 단순화하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196609"
---
# <a name="power-bi-visuals-test-utils"></a>Power BI 시각적 개체 테스트 유틸리티

이 문서에서는 Power BI 시각적 개체 테스트 유틸리티를 설치하고, 가져오고, 사용하는 방법에 대해 설명합니다. 이러한 테스트 유틸리티는 단위 테스트에 사용할 수 있으며 데이터 보기, 선택 및 색 스키마와 같은 요소에 대한 모의 및 메서드를 포함합니다.

## <a name="requirements"></a>요구 사항

이 패키지를 사용하려면 다음을 설치해야 합니다.

* [node.js](https://nodejs.org)(LTS 버전을 사용하는 것이 좋음)
* [npm](https://www.npmjs.com/) 버전 3.0.0 이상
* [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools) 패키지

## <a name="installation"></a>설치

테스트 유틸리티를 설치하고 해당 종속성을 *package.json*에 추가하려면 Power BI 시각적 개체 디렉터리에서 다음 명령을 실행합니다.

```bash
npm install powerbi-visuals-utils-testutils --save
```

다음은 테스트 유틸리티 퍼블릭 API에 대한 설명과 예제를 제공합니다.

## <a name="visualbuilderbase"></a>VisualBuilderBase

가장 자주 사용되는 `build`, `update` 및 `updateRenderTimeout` 메서드를 사용하는 단위 테스트에서 **VisualBuilder**를 통해 사용됩니다. 

`build` 메서드는 만든 시각적 개체의 인스턴스를 반환합니다.

`enumerateObjectInstances` 및 `updateEnumerateObjectInstancesRenderTimeout` 메서드는 버킷 및 서식 옵션에 대한 변경 내용을 확인하는 데 필요합니다.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> 자세한 예제는 [VisualBuilderBase 단위 테스트 작성](./unit-tests-introduction.md#create-a-visual-instance-builder) 및 [VisualBuilderBase 실제 사용 시나리오](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts)를 참조하세요.

## <a name="dataviewbuilder"></a>DataViewBuilder

이 모듈은 **TestDataViewBuilder**에서 사용되며, `createCategoricalDataViewBuilder` 메서드에 사용되는 **CategoricalDataViewBuilder** 클래스를 제공합니다. 또한 단위 테스트에서 모의 **DataView**를 사용하는 데 필요한 인터페이스와 메서드를 지정합니다.

* `withValues`는 정적 계열 열을 추가하고, `withGroupedValues`는 동적 계열 열을 추가합니다.

  **DataViewCategorical** 시각적 개체에는 동적 계열 및 정적 계열을 모두 적용하지 않습니다. **DataViewCategorical** 쿼리에서만 이 두 열을 모두 사용할 수 있습니다. 여기서 **DataViewTransform**은 별도의 **DataViewCategorical** 시각적 개체로 분할되어야 합니다.

* `build`는 메타데이터 및 DataViewCategorical이 포함된 DataView를 반환합니다.

  **DataView** 시각적 개체를 빌드할 때 동적 계열 및 정적 계열을 모두 포함하는 것과 같이 매개 변수 조합이 잘못된 경우 `build`에서 **Undefined**를 반환합니다.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

단위 테스트에서 **VisualData**를 만드는 데 사용됩니다. 데이터가 데이터 필드 버킷에 배치되면 Power BI에서 해당 데이터에 기반한 범주별 **DataView** 개체를 생성합니다. **TestDataViewBuilder**는 범주별 **DataView** 만들기를 시뮬레이션하는 데 도움이 됩니다.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  다음은 `testDataView`를 만들 때 가장 자주 사용되는 인터페이스를 나열합니다.

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> 자세한 예제는 [TestDataViewBuilder 단위 테스트 작성](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) 및 [TestDataViewBuilder 실제 사용 시나리오](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts)를 참조하세요.

## <a name="mocks"></a>Mock(모의)

### <a name="mockivisualhost"></a>MockIVisualHost

**IVisualHost**를 구현하여 Power BI 프레임워크와 같은 외부 종속성이 없는 Power BI 시각적 개체를 테스트합니다.

유용한 메서드에는 `createSelectionIdBuilder`, `createSelectionManager`, `createLocalizationManager` 및 getter 속성이 있습니다.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost`는 실제로 **MockIVisualHost**인 **IVisualHost**의 인스턴스를 만들고 반환합니다.
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    예제
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost**는 **IVisualHost**의 가짜 구현이며 단위 테스트에만 사용해야 합니다.

### <a name="mockicolorpalette"></a>MockIColorPalette

**IColorPalette**를 구현하여 Power BI 프레임워크와 같은 외부 종속성이 없는 Power BI 시각적 개체를 테스트합니다.

**MockIColorPalette**는 단위 테스트에서 색 스키마 또는 고대비 모드를 확인하는 데 유용한 속성을 제공합니다.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette`는 실제로 **MockIColorPalette**인 **IColorPalette**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    예제
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette**는 **IColorPalette**의 가짜 구현이며 단위 테스트에만 사용해야 합니다.

### <a name="mockiselectionid"></a>MockISelectionId

**ISelectionId**를 구현하여 Power BI 프레임워크와 같은 외부 종속성이 없는 Power BI 시각적 개체를 테스트합니다.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId`는 실제로 **MockISelectionId**인 **ISelectionId**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    예제
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId**는 **ISelectionId**의 가짜 구현이며 단위 테스트에만 사용해야 합니다.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

**ISelectionIdBuilder**를 구현하여 Power BI 프레임워크와 같은 외부 종속성이 없는 Power BI 시각적 개체를 테스트합니다. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder`는 실제로 **MockISelectionIdBuilder**인 **ISelectionIdBuilder**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    예제
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder**는 **ISelectionIdBuilder**의 가짜 구현이며 단위 테스트에만 사용해야 합니다.

### <a name="mockiselectionmanager"></a>MockISelectionManager

**ISelectionManager**를 구현하여 Power BI 프레임워크와 같은 외부 종속성이 없는 Power BI 시각적 개체를 테스트합니다. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager`는 실제로 **MockISelectionManager**인 **ISelectionManager**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    예제
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager**는 **ISelectionManager**의 가짜 구현이며 단위 테스트에만 사용해야 합니다.

### <a name="mockilocale"></a>MockILocale

  단위 테스트 프로세스 중에 필요에 따라 로캘을 설정하고 변경합니다.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale`은 **MockILocale**의 인스턴스를 만들고 반환합니다.
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
단위 테스트 프로세스 중에 필요에 따라 `TooltipService`를 시뮬레이션하고 호출합니다.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService`는 **MockITooltipService**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions`는 **MockIAllowInteractions**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
단위 테스트에 필요한 **LocalizationManager**의 기본 기능을 제공합니다.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager`는 실제로 **MockILocalizationManager**인 **ILocalizationManager**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    예제
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
**TelemetryService** 사용을 시뮬레이션합니다.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  `MockITelemetryService`를 만듭니다.
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
모의 AAD 토큰을 제공하여 **AuthenticationService** 작업을 시뮬레이션합니다.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService`는 실제로 **MockIAuthenticationService**인 **IAuthenticationService**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
**LocalStorage**와 동일한 동작으로 **ILocalVisualStorageService**를 사용할 수 있습니다.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService`는 실제로 **MockIStorageService**인 **ILocalVisualStorageService**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService`는 실제로 **MockIEventService**인 **IVisualEventService**의 인스턴스를 만들고 반환합니다.
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>utils(유틸리티)

utils에는 색, 숫자 및 이벤트와 관련된 도우미를 포함하여 Power BI 시각적 개체의 단위 테스트를 위한 도우미 메서드가 포함됩니다.

- `renderTimeout`은 시간 제한을 반환합니다.
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom`은 단위 테스트에서 픽스쳐를 설정하는 데 도움이 됩니다.
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  예제
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>색 관련 도우미 메서드

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  다음 구조체를 반환합니다.

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch`는 입력 문자열에서 구문 분석된 **RgbColor** 개체를 비교합니다.
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString`은 입력 문자열에서 색을 구문 분석하여 지정된 **RgbColor** 인터페이스에 반환합니다.
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>숫자 관련 도우미 메서드

- `getRandomNumbers`는 min 및 max 값을 사용하여 난수를 생성합니다. `exceptionList`를 지정하고 결과 변경에 대한 함수를 제공할 수 있습니다.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers`는 지정된 min 및 max 값을 사용하여 `getRandomNumber` 메서드에서 생성된 난수의 배열을 제공합니다.
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>이벤트 관련 도우미 메서드
단위 테스트에서 웹 페이지 이벤트 시뮬레이션을 위해 작성되는 메서드는 다음과 같습니다.

- `clickElement`는 지정된 요소의 클릭을 시뮬레이션합니다.
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch`는 터치 이벤트를 시뮬레이션하는 데 도움이 되는 **Touch** 개체를 반환합니다.
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList`는 시뮬레이션된 **Touch** 이벤트의 목록을 반환합니다.
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent`는 **MouseEvent**를 반환합니다.
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent`는 **MouseEvent**를 만들고 반환합니다.
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>D3 이벤트 관련 도우미 메서드

단위 테스트에서 D3 이벤트를 시뮬레이션하는 데 사용되는 메서드는 다음과 같습니다.

- `flushAllD3Transitions`는 모든 D3 전환을 완료하도록 강제로 적용합니다.

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > 일반적으로 0이 아닌 지연 전환은 순간 지연(10밀리초 미만) 후에 실행되지만, 브라우저에서 페이지를 두 번 렌더링하면 잠시 깜박일 수 있습니다. 첫 번째 이벤트 루프가 종료되면 첫 번째 타이머 콜백에서 즉시 다시 실행됩니다.
  >
  > 이러한 깜박임은 IE와 많은 수의 웹 보기에서 더 눈에 띄며 iOS에는 추천되지 않습니다.
  > 
  > 첫 번째 이벤트 루프의 끝에서 타이머 큐를 플러시하면 0이 아닌 지연 전환을 즉시 실행하고 깜박임을 방지할 수 있습니다.

다음 메서드도 포함됩니다.
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>도우미 인터페이스
도우미 함수에 사용되는 인터페이스 및 열거형은 다음과 같습니다.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>다음 단계

webpack 기반 Power BI 시각적 개체에 대한 단위 테스트와 `karma` 및 `jasmine`을 사용하는 단위 테스트를 작성하려면 [자습서: Power BI 시각적 개체 프로젝트에 대한 단위 테스트 추가](./unit-tests-introduction.md) 예제를 참조하세요.
