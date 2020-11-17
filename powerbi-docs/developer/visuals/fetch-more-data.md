---
title: Power BI에서 더 많은 데이터 가져오기
description: 이 문서에서는 Power BI 시각적 개체에 대해 큰 데이터 세트의 분할된 가져오기를 사용하도록 설정하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: b8be5b68603f818e26e7f731e4f163bc626b5053
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483699"
---
# <a name="fetch-more-data-from-power-bi"></a>Power BI에서 더 많은 데이터 가져오기

이 문서에서는 `fetchMoreData` 메서드를 사용하여 30KB 데이터 요소의 하드 한도를 무시하기 위해 더 많은 데이터를 로드하는 방법을 설명합니다. 이 방법은 데이터를 청크로 제공합니다. 성능을 향상하기 위해 사용 사례에 맞게 청크 크기를 구성할 수 있습니다.

## <a name="limitations-of-fetchmoredata"></a>fetchMoreData의 제한 사항

* 창 크기는 2~30,000의 범위로 제한됩니다.
* Dataview의 총 행 개수는 1,048,576행입니다.
* 세그먼트 집계 모드에서 dataview 메모리 크기는 100MB로 제한됩니다.

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>큰 데이터 세트의 분할된 가져오기 사용

`dataview` 세그먼트 모드의 경우, 필요한 `dataViewMapping`에 대한 시각적 개체의 *capabilities.json* 파일에서 `dataReductionAlgorithm`의 창 크기를 정의합니다. `count`는 창 크기를 결정하고, 이 크기에 따라 각 업데이트에서 `dataview`에 추가될 수 있는 새 데이터 행 수가 제한됩니다.

다음 코드를 *capabilities.json* 파일에 추가합니다.

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

새 세그먼트가 기존 `dataview`에 추가되고, 시각적 개체에 `update` 호출로 제공됩니다.

## <a name="usage-in-the-power-bi-visual"></a>Power BI 시각적 개체에서 사용

Power BI 기본 세그먼트 집계 모드 또는 증분 업데이트 모드에서 `fetchMoreData`를 사용할 수 있습니다. 

### <a name="using-segments-aggregation-mode-default"></a>세그먼트 집계 모드 사용(기본값)

이 모드를 사용하는 경우 시각적 개체에 제공된 dataview에는 이전의 모든 `fetchMoreData requests`에 대한 누적 데이터가 들어 있습니다. 따라서 각 업데이트를 통해 dataview 크기가 증가할 것으로 예상됩니다. 예를 들어 총 100,000개의 행이 필요하고 창 크기가 10,000으로 설정된 경우 첫 번째 업데이트 dataview는 10,000개의 행을 포함하고 두 번째 업데이트 dataview는 20,000개의 행을 포함해야 합니다.

`aggregateSegments = true`를 사용하고 `fetchMoreData`를 호출하여 이 모드를 선택합니다.

`dataView.metadata.segment`가 있는지 검사하여 데이터가 있는지를 확인할 수 있습니다.

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

`options.operationKind`를 검사하여 첫 번째 업데이트인지, 후속 업데이트인지 확인할 수도 있습니다. 다음 코드에서 `VisualDataChangeOperationKind.Create`는 첫 번째 세그먼트를 나타내고, `VisualDataChangeOperationKind.Append`는 후속 세그먼트를 나타냅니다.

샘플 구현은 다음 코드 조각을 참조하세요.

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

다음과 같이 UI 이벤트 처리기에서 `fetchMoreData` 메서드를 호출할 수도 있습니다.

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(true);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

`this.host.fetchMoreData` 메서드 호출에 대한 응답으로, Power BI는 새 데이터 세그먼트를 사용하여 시각적 개체의 `update` 메서드를 호출합니다.

> [!NOTE]
> 클라이언트 메모리 제약 조건을 방지하기 위해, Power BI는 현재 가져온 데이터 합계를 100MB로 제한합니다. `fetchMoreData()`가 `false`를 반환하면 한도에 도달한 것을 알 수 있습니다.

### <a name="using-incremental-updates-mode"></a>증분 업데이트 모드 사용

이 모드를 사용하는 경우 시각적 개체에 제공된 dataview에는 증분 데이터만 포함됩니다. 따라서 dataview 크기는 정의된 창 크기를 전달하지 않습니다. 예를 들어 총 101,000개의 행이 필요하고 창 크기가 10,000으로 설정된 경우 시각적 개체는 dataview 크기 10,000의 10개의 업데이트와 크기 1,000의 dataview를 사용하는 업데이트 하나를 가져옵니다.

`aggregateSegments = false`를 사용하고 `fetchMoreData`를 호출하여 이 모드를 선택합니다.

`dataView.metadata.segment`가 있는지 검사하여 데이터가 있는지를 확인할 수 있습니다.

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

`options.operationKind`를 검사하여 첫 번째 업데이트인지, 후속 업데이트인지 확인할 수도 있습니다. 다음 코드에서 `VisualDataChangeOperationKind.Create`는 첫 번째 세그먼트를 나타내고, `VisualDataChangeOperationKind.Segment`는 후속 세그먼트를 나타냅니다.

샘플 구현은 다음 코드 조각을 참조하세요.

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Segment) {
        
    }

    // skip overlapping rows 
    const rowOffset = (dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1;

    // Process incoming data
    for (var i = rowOffset; i < dataView.table.rows.length; i++) {
        var val = <number>(dataView.table.rows[i][0]); // Pick first column               
            
     }
     
    // complete update implementation
}
```

다음과 같이 UI 이벤트 처리기에서 `fetchMoreData` 메서드를 호출할 수도 있습니다.

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(false);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

`this.host.fetchMoreData` 메서드 호출에 대한 응답으로, Power BI는 새 데이터 세그먼트를 사용하여 시각적 개체의 `update` 메서드를 호출합니다.

> [!NOTE]
> dataview 데이터는 서로 다른 업데이트 간에 대부분 배타적이지만 이후의 dataview 간에는 약간의 겹치는 부분이 있습니다.
> 테이블 및 범주 데이터 매핑의 경우 처음 N개의 dataview 행에 이전 dataview에서 복사된 데이터가 포함되어야 합니다.
> N은 다음을 통해 확인할 수 있습니다. `(dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1`