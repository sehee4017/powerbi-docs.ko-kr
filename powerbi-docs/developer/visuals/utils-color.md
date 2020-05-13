---
title: Power BI 시각적 개체에서 ColorUtils를 사용하는 방법 소개
description: 이 문서에서는 ColorUtils를 사용하여 Power BI 시각적 개체의 시각적 개체 데이터 요소에 테마 및 팔레트를 간단하게 적용하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 8de530871739a18c1afc72cee3e0da5fc70ebb16
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379355"
---
# <a name="color-utils"></a>색 유틸리티
이 문서는 ColorUtils를 설치하고, 가져오고, 사용하는 데 도움이 됩니다. 이 문서에서는 ColorUtils를 사용하여 Power BI 시각적 개체의 시각적 개체 데이터 요소에 테마 및 팔레트를 간단하게 적용하는 방법을 설명합니다.

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

## <a name="usage"></a>사용

InteractivityUtils를 사용하려면 시각적 개체의 소스 코드에 필요한 구성 요소를 가져와야 합니다.
```typescript
import { ColorHelper } from "powerbi-visuals-utils-colorutils";
```

Power BI 시각적 개체에서 ColorUtils를 설치하고 사용하는 방법을 알아봅니다.

* [사용 가이드] 사용 가이드에서는 패키지의 퍼블릭 API에 대해 설명합니다. 패키지의 각 공용 인터페이스에 대한 설명과 몇 가지 예제를 찾을 수 있습니다.

이 패키지에는 다음과 같은 클래스와 모듈이 포함되어 있습니다.
* [ColorHelper](#colorhelper) - 차트 값에 대해 서로 다른 색을 생성하는 데 유용합니다.
* [colorUtils](#colorutils) - 색 형식을 변환하는 데 유용합니다.

## `ColorHelper`
`ColorHelper` 클래스는 다음과 같은 함수 및 메서드를 제공합니다.

### `getColorForSeriesValue` 
이 메서드는 지정된 계열 값의 색을 가져옵니다. 명시적 색 또는 기본 색이 설정되지 않은 경우 이 계열에 대한 색 눈금에서 색이 할당됩니다.
```typescript
getColorForSeriesValue(objects: IDataViewObjects, value: PrimitiveValue, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>예제
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;

import DataViewValueColumns = powerbi.DataViewValueColumns;
import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;

import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const valueColumns: DataViewValueColumns = visualUpdateOptions.dataViews[0].categorical.values,
            grouped: DataViewValueColumnGroup[] = valueColumns.grouped(),
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        for (let i = 0; i < grouped.length; i++) {
            let grouping: DataViewValueColumnGroup = grouped[i];

            let color = colorHelper.getColorForSeriesValue(grouping.objects, grouping.name); // returns a color of the series
        }
    }
}
```

### `getColorForMeasure`
이 메서드는 지정된 측정값의 색을 가져옵니다.
```typescript
 getColorForMeasure(objects: IDataViewObjects, measureKey: any, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>예제
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;
import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const objects: DataViewObjects = visualUpdateOptions.dataViews[0].categorical.categories[0].objects[0],
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        let color = colorHelper.getColorForMeasure(objects, ""); // returns a color
    }
}
```

### <a name="static-normalizeselector"></a>정적 `normalizeSelector`
이 메서드는 정규화된 선택기를 반환합니다.
```typescript
static normalizeSelector(selector: Selector, isSingleSeries?: boolean): Selector;
```
#### <a name="example"></a>예제
```typescript
import ISelectionId = powerbi.visuals.ISelectionId;
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

let selectionId: ISelectionId = ...;
let selector = ColorHelper.normalizeSelector(selectionId.getSelector(), false);
```

`getThemeColor` 및 `getHighContrastColor` 메서드는 둘 다 색 테마 색과 관련이 있습니다.
또한 `ColorHelper`에는 확인에 유용한 `isHighContrast` 속성이 있습니다.

### `getThemeColor`
이 메서드는 테마 색을 반환합니다.
```typescript
 getThemeColor(themeColorName?: ThemeColorName): string;
```
### `getHighContrastColor`
 이 메서드는 고대비 모드에 대한 색을 반환합니다.
```typescript
getHighContrastColor(themeColorName?: ThemeColorName, defaultColor?: string): string;
```
#### <a name="example-related-to-high-contrast-mode-usage"></a>고대비 모드 사용과 관련된 예제:
```typescript

import { ColorHelper } from "powerbi-visuals-utils-colorutils";

export class MyVisual implements IVisual {
        private colorHelper: ColorHelper;

        private init(options: VisualConstructorOptions): void {
            this.colors = options.host.colorPalette;
            this.colorHelper = new ColorHelper(this.colors);
        } 

            private createViewport(element: HTMLElement): void {
                const fontColor: string = "#131aea";
                const axisBackgroundColor: string = this.colorHelper.getThemeColor();
                
                // some d3 code before
                d3ElementName.attr("fill", colorHelper.getHighContrastColor("foreground", fontColor);
            }
                
            public static parseSettings(dataView: DataView, colorHelper: ColorHelper): VisualSettings {
                // some code that should be applied on formatting settings
                if (colorHelper.isHighContrast) {
                        this.settings.fontColor = colorHelper.getHighContrastColor("foreground", this.settings.fontColor);
                    }
            }
}
```


## `ColorUtils`
 이 모듈은 다음과 같은 함수를 제공합니다.

* [hexToRGBString](#hextorgbstring)
* [rotate](#rotate)
* [parseColorString](#parsecolorstring)
* [calculateHighlightColor](#calculatehighlightcolor)
* [createLinearColorScale](#createlinearcolorscale)
* [shadeColor](#shadecolor)
* [rgbBlend](#rgbblend)
* [channelBlend](#channelblend)
* [hexBlend](#hexblend)

### <a name="hextorgbstring"></a>hexToRGBString
16진수 색을 RGB 문자열로 변환합니다.

```typescript
function hexToRGBString(hex: string, transparency?: number): string
```

#### <a name="example"></a>예제

```typescript
import  { hexToRGBString } from "powerbi-visuals-utils-colorutils";

hexToRGBString('#112233');

// returns: "rgb(17,34,51)"
```

### <a name="rotate"></a>rotate
RGB 색을 회전합니다.

```typescript
function rotate(rgbString: string, rotateFactor: number): string
```

#### <a name="example"></a>예제

```typescript
import { rotate } from "powerbi-visuals-utils-colorutils";

rotate("#CC0000", 0.25); // returns: #66CC00
```

### <a name="parsecolorstring"></a>parseColorString
RGB 형식에 대한 모든 색 문자열을 구문 분석합니다.

```typescript
function parseColorString(color: string): RgbColor
```

#### <a name="example"></a>예제

```typescript
import { parseColorString } from "powerbi-visuals-utils-colorutils";

parseColorString('#09f');
// returns: {R: 0, G: 153, B: 255 }

parseColorString('rgba(1, 2, 3, 1.0)');
// returns: {R: 1, G: 2, B: 3, A: 1.0 }
```

### <a name="calculatehighlightcolor"></a>calculateHighlightColor
lumianceThreshold 및 델타를 기준으로 rgbColor에서 강조 표시 색을 계산합니다.

```typescript
function calculateHighlightColor(rgbColor: RgbColor, lumianceThreshold: number, delta: number): string
```

#### <a name="example"></a>예제

```typescript
import { calculateHighlightColor } from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    yellowRGB = parseColorString(yellow);

calculateHighlightColor(yellowRGB, 0.8, 0.2);

// returns: '#CCCC00'
```

### <a name="createlinearcolorscale"></a>createLinearColorScale
지정된 숫자 도메인에 대한 선형 색 눈금을 반환합니다.

```typescript
function createLinearColorScale(domain: number[], range: string[], clamp: boolean): LinearColorScale
```

#### <a name="example"></a>예제

```typescript
import { createLinearColorScale } from "powerbi-visuals-utils-colorutils";

let scale = ColorUtility.createLinearColorScale(
    [0, 1, 2, 3, 4],
    ["red", "green", "blue", "black", "yellow"],
    true);

scale(1); // returns: green
scale(10); // returns: yellow
```

### <a name="shadecolor"></a>shadeColor
문자열 16진 식을 숫자로 변환하고 백분율 및 R, G, B 채널을 계산합니다.
각 채널에 대한 백분율을 적용하고 16진수 값을 파운드 기호가 있는 문자열로 다시 반환합니다.

```typescript
function shadeColor(color: string, percent: number): string
```

#### <a name="example"></a>예제

```typescript
import { shadeColor } from "powerbi-visuals-utils-colorutils";

shadeColor('#000000', 0.1); // returns '#1a1a1a'
shadeColor('#FFFFFF', -0.5); // returns '#808080'
shadeColor('#00B8AA', -0.25); // returns '#008a80'
shadeColor('#00B8AA', 0); // returns '#00b8aa'
```

### <a name="rgbblend"></a>rgbBlend
배경색 위에 불투명도가 적용된 색을 오버레이합니다. 모든 알파 채널은 무시됩니다.

```typescript
function rgbBlend(foreColor: RgbColor, opacity: number, backColor: RgbColor): RgbColor
```

#### <a name="example"></a>예제

```typescript
import { rgbBlend} from "powerbi-visuals-utils-colorutils";

rgbBlend({R: 100, G: 100, B: 100}, 0.5, {R: 200, G: 200, B: 200});

// returns: {R: 150, G: 150, B: 150}
```

### <a name="channelblend"></a>channelBlend
두 색의 단일 채널을 혼합합니다.

```typescript
function channelBlend(foreChannel: number, opacity: number, backChannel: number): number
```

#### <a name="example"></a>예제

```typescript
import { channelBlend} from "powerbi-visuals-utils-colorutils";

channelBlend(0, 1, 255); // returns: 0
channelBlend(128, 1, 255); // returns: 128
channelBlend(255, 0, 0); // returns: 0
channelBlend(88, 0, 88); // returns: 88
```

### <a name="hexblend"></a>hexBlend
배경색 위에 불투명도가 적용된 색을 오버레이합니다.

```typescript
function hexBlend(foreColor: string, opacity: number, backColor: string): string
```

#### <a name="example"></a>예제

```typescript
import { hexBlend} from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    black = "#000000",
    white = "#FFFFFF";

hexBlend(yellow, 0.5, white); // returns: "#FFFF80"
hexBlend(white, 0.5, yellow); // returns: "#FFFF80"

hexBlend(yellow, 0.5, black); // returns: "#808000"
hexBlend(black, 0.5, yellow); // returns: "#808000"
```