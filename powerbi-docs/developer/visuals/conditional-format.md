---
title: 조건부 서식 지정
description: Power BI 시각적 개체 프로젝트에 조건부 서식을 적용하는 방법 알아보기
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: how-to
ms.subservice: powerbi-custom-visuals
ms.date: 10/27/2020
ms.openlocfilehash: 5243d1eda3fef2c7b82350fb0ca2669eb43c7623
ms.sourcegitcommit: b5365df7fc32b7c49f8a2bf2cf75b5edd6bda9b6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513850"
---
# <a name="add-conditional-formatting"></a>조건부 서식 추가

[조건부 서식](../../visuals/service-tips-and-tricks-for-color-formatting.md#conditional-formatting-for-visualizations)을 통해 보고서 작성자는 숫자 값에 따라 보고서에 색상이 표시되는 방법을 지정할 수 있습니다.

이 문서에서는 Power BI 시각적 개체에 조건부 서식 기능을 추가하는 방법을 설명합니다.

조건부 서식은 다음 속성 형식에만 적용할 수 있습니다.
* 색
* 텍스트
* 아이콘
* 웹 URL

## <a name="add-conditional-formatting-to-your-project"></a>프로젝트에 조건부 서식 추가

이 섹션에서는 기존 Power BI 시각적 개체에 조건부 서식을 추가하는 방법을 보여줍니다. 이 문서의 예제 코드는 [SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart) 시각적 개체를 기반으로 합니다. [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts)에서 소스 코드를 검사할 수 있습니다.

### <a name="add-a-conditional-color-formatting-entry-in-the-format-pane"></a>서식 창에 조건부 색 서식 지정 항목 추가

이 섹션에서는 서식 창의 데이터 요소에 조건부 색 서식 지정 항목을 추가하는 방법을 알아봅니다.

1. `powerbi-visuals-api`에서 노출하는 `VisualObjectInstance`의 `propertyInstanceKind` 배열을 사용합니다. 첫 번째 단계는 파일에 다음 가져오기가 포함되는지 확인하는 것입니다.

    ```typescript
    import powerbiVisualsApi from "powerbi-visuals-api";
    ```

2. 적절한 서식 유형(*상수*, *ConstantOrRule* 또는 *규칙*)을 지정하려면 `VisualEnumerationInstanceKinds` 열거를 사용합니다. 파일에 다음 가져오기를 추가합니다.

    ```typescript
    import VisualEnumerationInstanceKinds = powerbiVisualsApi.VisualEnumerationInstanceKinds;
    ```

3. `propertyInstanceKind` 배열에서 조건부 서식을 지원하려는 모든 속성을 나열합니다. `enumerateObjectInstances` 메서드에서 이러한 속성을 정의합니다.

    ```typescript
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
            …
            case 'colorSelector':
                …
                    objectEnumeration.push({
                        objectName: objectName,
                        displayName: barDataPoint.category,
                        properties: {
                            fill: {
                                solid: {
                                    color: barDataPoint.color
                                }
                            }
                        },
                        selector: dataViewWildcard.createDataViewWildcardSelector(dataViewWildcard.DataViewWildcardMatchingOption.InstancesAndTotals),
                        altConstantValueSelector: barDataPoint.selectionId.getSelector(),

                        // List your conditional formatting properties
                        propertyInstanceKind: {
                            fill: VisualEnumerationInstanceKinds.ConstantOrRule
                        }
                    });
                }
            …
    }

    ```

    `VisualEnumerationInstanceKinds.ConstantOrRule`은(는) 상수 서식 지정 UI 요소와 함께 조건부 서식 UI 항목을 만듭니다.

    >[!div class="mx-imgBorder"]
    >![일반 색 버튼 옆에 있는, Power BI에 표시되는 조건부 서식 버튼의 스크린샷.](media/conditional-formatting/conditional-formatting-ui.png)

### <a name="define-how-conditional-formatting-behaves"></a>조건부 서식 지정 동작 방법 정의

서식 지정을 데이터 요소에 적용하는 방법을 정의합니다.

`powerbi-visuals-utils-dataviewutils`에서 선언된 `createDataViewWildcardSelector`을(를) 사용하여 조건부 서식을 인스턴스, 합계 또는 둘 다에 적용할지 여부를 지정합니다. 자세한 내용은 [DataViewWildcard](utils-dataview.md#)를 참조하세요.

`enumerateObjectInstances`에서 조건부 서식을 적용하려는 개체를 다음과 같이 변경합니다.

 * `selector` 값을 `dataViewWildcard.createDataViewWildcardSelector(dataViewWildcardMatchingOption)` 호출로 바꿉니다. `DataViewWildcardMatchingOption`은(는) 조건부 서식이 인스턴스, 합계 또는 둘 다에 적용되는지 여부를 정의합니다.

* `selector` 속성에 대해 이전에 정의된 값을 가진 `altConstantValueSelector` 속성을 추가합니다.

```typescript
case 'colorSelector':
         …
            objectEnumeration.push({
                objectName: objectName,
                displayName: barDataPoint.category,
                properties: {
                    fill: {
                        solid: {
                            color: barDataPoint.color
                        }
                    }
                },

                // Define whether the conditional formatting will apply to instances, totals, or both
                selector: dataViewWildcard.createDataViewWildcardSelector(dataViewWildcard.DataViewWildcardMatchingOption.InstancesAndTotals),

                // Add this property with the value previously defined for the selector property
                altConstantValueSelector: barDataPoint.selectionId.getSelector(),

                propertyInstanceKind: { 
                    fill: VisualEnumerationInstanceKinds.ConstantOrRule
                }
            });
        }

```

## <a name="next-steps"></a>다음 단계

[DataViewUtils](utils-dataview.md) 문서를 검토합니다.