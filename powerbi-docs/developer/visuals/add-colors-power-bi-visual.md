---
title: Power BI 시각적 개체에 색 추가
description: 이 문서에서는 Power BI 시각적 개체에 색을 추가하는 방법과 색이 있는 시각적 개체의 데이터 요소를 처리하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: 3f3574545d82ac11c762b7011afdc49cbe855224
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141160"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Power BI 시각적 개체에 색 추가

이 문서에서는 시각적 개체에 색을 추가하는 방법과 색이 있는 시각적 개체의 데이터 요소를 처리하는 방법을 설명합니다.

`IVisualHost`는 해당 서비스 중 하나로 색을 노출합니다.
이 문서의 예제 코드는 [SampleBarChart 시각적 개체](https://github.com/microsoft/PowerBI-visuals-sampleBarChart)를 수정합니다.
소스 코드는 [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts)를 참조하세요.

시각적 개체 만들기를 시작하려면 [Power BI 시각적 개체 개발](custom-visual-develop-tutorial.md)을 참조하세요.

## <a name="add-color-to-data-points"></a>데이터 요소에 색 추가

각 색은 각 데이터 요소를 나타냅니다.
다음 예제와 같이 `BarChartDataPoint` 인터페이스에 색을 추가합니다.

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>색상표 서비스 사용

`colorPalette` 서비스는 시각적 개체에 사용되는 색을 관리합니다.
이 서비스의 인스턴스는 `IVisualHost`에서 사용할 수 있습니다.

`update` 메서드에서 정의됩니다.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>데이터 요소에 색 할당

다음으로 `dataPoints`를 지정합니다.
이 예제에서 각 `dataPoints`에는 값, 범주 및 색이 포함됩니다.
`dataPoints`에는 다른 속성도 포함될 수 있습니다.

`SampleBarChart`에서 `visualTransform` 메서드는 `dataPoints` 계산을 캡슐화합니다.
해당 메서드는 가로 막대형 차트 Viewmodel의 일부입니다.
이 메서드는 `visualTransform`에서 `dataPoints` 계산을 반복하기 때문에 다음 코드와 같이 색을 할당하는 데 적합한 위치입니다.

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

그런 다음 `update` 메서드 내의 [d3](https://d3js.org/)-selection `barSelection`에 `dataPoints`의 데이터를 적용합니다.

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>다음 단계

Power BI 시각적 개체에 대한 자세한 내용은 [Power BI 시각적 개체의 기능 및 속성](capabilities.md)을 참조하세요.

Power BI 시각적 개체를 개발하는 방법에 대한 자세한 내용은 [Power BI 시각적 개체를 디버그하는 방법](visuals-how-to-debug.md) 및 [Power BI 시각적 개체 문제 해결](power-bi-custom-visuals-troubleshoot.md)을 참조하세요.
