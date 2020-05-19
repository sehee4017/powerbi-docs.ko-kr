---
title: 시각적 개체 API
description: 이 문서에서는 Power BI 시각적 개체에 대해 IVisual API를 사용하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302969"
---
# <a name="visual-api"></a>시각적 개체 API
모든 시각적 개체는 `IVisual` 인터페이스를 구현하는 클래스로 시작합니다. `IVisual` 인터페이스를 구현하는 클래스가 정확히 하나만 있다면 클래스 이름은 무엇이든 지정할 수 있습니다.

> [!NOTE]
> 시각적 개체 클래스 이름은 *pbiviz.json* 파일에 정의된 이름과 일치해야 합니다.

구현해야 하는 다음 메서드를 포함하는 샘플 시각적 클래스를 참조하세요.

* `constructor` - 시각적 개체의 상태를 초기화 하는 표준 생성자입니다.
* `update` - 시각적 개체의 데이터를 업데이트합니다.
* `enumerateObjectInstances` - 필요할 때 수정할 수 있는 속성 창(서식 옵션)을 채우기 위해 개체를 반환합니다.
* `destroy` - 정리를 위한 표준 소멸자입니다.

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>constructor

시각적 개체 클래스의 생성자는 시각적 개체를 인스턴스화할 때 호출됩니다. 시각적 개체에 필요한 모든 설정 작업에 사용할 수 있습니다.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement` - 시각적 개체를 포함할 DOM 요소에 대한 참조입니다.
* `host: IVisualHost` - 시각적 개체 호스트(Power BI)와 상호 작용하는 데 사용할 수 있는 속성 및 서비스 컬렉션입니다.

   `IVisualHost` - 다음 서비스를 포함합니다.

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder` - 시각적 개체에서 선택 가능한 항목에 대한 메타데이터를 생성하고 저장합니다.
   * `createSelectionManager` - 시각적 개체의 호스트에 는 선택 상태 변경 내용을 알리는 데 사용되는 통신 브리지를 만듭니다. [선택 API](./selection-api.md)를 참조하세요.
   * `createLocalizationManager` - [지역화](./localization.md)에 도움이 되는 관리자를 생성합니다.
   * `allowInteractions: boolean` - 시각적 개체를 대화형으로 표시할지 여부에 대한 힌트를 제공하는 부울 플래그입니다.
   * `applyJsonFilter` - 특정 필터 형식을 적용합니다. [필터 API](./filter-api.md)를 참조하세요.
   * `persistProperties` - 사용자가 속성을 유지하고 시각적 개체 정의와 함께 저장하여 다음 번 다시 로드에 사용하도록 허용합니다.
   * `eventService` - [이벤트 서비스](./event-service.md)를 반환하여 **렌더링** 이벤트를 지원합니다.
   * `storageService` - 시각적 개체에서 [로컬 스토리지](./local-storage.md)를 사용하는 데 도움이 되는 서비스를 반환합니다.
   * `authenticationService` - 사용자 인증에 도움이 되는 서비스를 생성합니다.
   * `tooltipService` - 시각적 개체에서 도구 설명을 사용하는 데 도움이 되는 [도구 설명 서비스](./add-tooltips.md)를 반환합니다.
   * `launchUrl` - 다음 탭에서 [URL을 시작](./launch-url.md)하는 데 도움이 됩니다.
   * `locale` - 로캘 문자열을 반환합니다. [지역화](./localization.md)를 참조하세요.
   * `instanceId` - 현재 시각적 개체 인스턴스를 식별하는 문자열을 반환합니다.
   * `colorPalette` - 데이터에 색을 적용하는 데 필요한 colorPalette를 반환합니다.
   * `fetchMoreData` - 표준 제한(1,000행)보다 많은 데이터 사용을 지원합니다.
   * `switchFocusModeState` - 포커스 모드 상태를 변경하는 데 도움이 됩니다.

## <a name="update"></a>update

모든 시각적 개체는 데이터 또는 호스트 환경이 변경될 때마다 호출되는 공용 업데이트 메서드를 구현해야 합니다.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport` - 시각적 개체를 렌더링해야 하는 뷰포트의 차원입니다.
* `dataViews: DataView[]` - 시각적 개체를 렌더링하는 데 필요한 모든 데이터를 포함하는 dataview 개체입니다(시각적 개체는 일반적으로 DataView 아래의 범주 속성을 사용).
* `type: VisualUpdateType` - 이 업데이트의 유형을 나타내는 플래그입니다(**Data** | **Resize** | **ViewMode** | **Style** | **ResizeEnd**).
* `viewMode: ViewMode` - 시각적 개체의 보기 모드를 나타내는 플래그입니다(**View** | **Edit** | **InFocusEdit**).
* `editMode: EditMode` - 시각적 개체의 편집 모드를 나타내는 플래그입니다(**Default** | **Advanced**). (시각적 개체가 **AdvancedEditMode**를 지원하는 경우, **editMode**가 **Advanced**로 설정된 경우에만 고급 UI 컨트롤을 렌더링해야 합니다. [AdvancedEditMode](./advanced-edit-mode.md)를 참조하세요.)
* `operationKind?: VisualDataChangeOperationKind` - 데이터 변경 유형을 나타내는 플래그입니다(**Create** | **Append**).
* `jsonFilters?: IFilter[]` - 적용된 json 필터의 컬렉션입니다.
* `isInFocus?: boolean` - 시각적 개체가 포커스 모드인지 여부를 나타내는 플래그입니다.
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

이 메서드는 기능에 나열된 모든 개체에 대해 호출됩니다. 옵션(현재는 이름만)을 사용하여 이 속성을 표시하는 방법에 대한 정보를 포함하는 `VisualObjectInstanceEnumeration`을 반환합니다.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string` - 개체의 이름입니다.

## <a name="destroy-optional"></a>destroy `optional`

소멸 함수는 시각적 개체를 언로드할 때 호출되며 이벤트 수신기 제거와 같은 정리 작업에 사용될 수 있습니다.

``` typescript
public destroy(): void
```

> [!Note]
> Power BI는 일반적으로 `destroy`를 호출하지 않습니다. 시각적 개체를 포함하는 전체 IFrame을 제거하는 것이 더 빠르기 때문입니다.
