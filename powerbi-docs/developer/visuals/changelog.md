---
title: Power BI 시각적 개체 API 변경 로그
description: 이 문서에서는 여러 버전의 Power BI 시각적 개체 API의 주요 변경 내용에 대해 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: c43542bc6c2bb0699403062f68024f9718bbbb60
ms.sourcegitcommit: 54e571a10b0fdde5cd6036017eac9ef228de5116
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501952"
---
# <a name="power-bi-visuals-api-changelog"></a>Power BI 시각적 개체 API 변경 로그
이 페이지에는 API 버전에 대한 빠른 요약이 포함되어 있습니다. 여기에 나열된 버전은 안정적인 것으로 간주되며 변경되지 않습니다.


## <a name="api-v340"></a>API v3.4.0
  * `fetchMoreData`: 새로운 `aggregateSegments` 매개 변수(기본값: true), 집계 없음 fetchMoreData 지원

## <a name="api-v320"></a>API v3.2.0
  * **[supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)** 지원

## <a name="api-v260"></a>API v2.6.0
  * 업데이트 옵션에 **isInFocus** 를 추가하고 시각적 개체에 **switchFocusModeState** 메서드를 추가
  * **부분합** 사용자 지정을 지원

## <a name="api-v250"></a>API v2.5.0
  * **[분석 창](./analytics-pane.md)** 을 지원
  * `SelectionIdBuilder` **withMatrixNode** 및 **withTable** 메서드를 지원
  * `DataRepetitionSelector` 인터페이스를 더 이상 지원하지 않고 `data.CustomVisualOpaqueIdentity` 인터페이스로 대체

## <a name="api-v230"></a>API v2.3.0
  * **[방문 페이지 API](./landing-page.md)**
  * **[로컬 스토리지 API](./local-storage.md)**
  * **[튜플 필터 API(다중 열 필터)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[이벤트 렌더링 API](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v220"></a>API v2.2.0
  * **[DataView에서 JSON 필터 복원](./filter-api.md#restore-the-json-filter-from-the-data-view)** 을 지원
  * **[ContextMenu API](./context-menu.md)**

## <a name="api-v210"></a>API v2.1.0
  * 성능 향상:
    * 로드 시간 단축
    * 메모리 사용 공간 축소
    * 데이터 및 이벤트 트랜잭션 최적화  

**릴리스 정보**
* 리팩터링된 필터링 API는 API 2.2에서 사용할 수 있으며 API 2.1에서는 지원되지 않습니다.
* 시각적 개체는 해당 기능에 선언된 dataView 형식만 받습니다. 여러 dataView 형식을 사용하는 시각적 개체는 이 업데이트의 결과로 중단됩니다.
* `DataViewScopeIdentity` 인터페이스는 더 이상 지원하지 않고 `data.DataRepetitionSelector` 인터페이스로 대체했습니다. `DataViewScopeIdentity` 인터페이스의 키 속성을 사용한 경우 `JSON.stringify(identity)`로 바꿀 수 있습니다.
* `undefined`는 dataView 내에서 `null`로 바뀝니다. `var item in myArray`를 사용하여 배열을 반복하는 경우 `undefined`에서 건너뛰지만 `null`에서는 건너뛰지 않습니다. 이 패턴을 사용하는 시각적 개체는 이 업데이트로 인해 중단될 수 있습니다. 배열에서 `null` 여부를 확인해야 합니다.
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* `proto` 속성이 dataView 내부에서 숨겨진 metadata\data를 더 이상 저장하지 않습니다. `proto`를 통해 속성에 액세스하는 시각적 개체는 이 업데이트로 인해 중단될 수 있습니다.

## <a name="api-v1130"></a>API v1.13.0
* **[슬라이서 동기화](./enable-sync-slicers.md)** 를 지원. 이 기능은 PBI 현재 코드 상태로 인한 단일 필드 슬라이서에 대해서만 유효합니다. [자세히 알아보기](../../visuals/power-bi-visualization-slicers.md)
* 접근성: [고대비 지원](./high-contrast-support.md) 
* 접근성: 키보드 포커스 플래그 허용

## <a name="api-v1120"></a>API v1.12.0
* 테마를 지원
* **[fetchMoreData](./fetch-more-data.md)** 를 지원. **더 많은 데이터 가져오기 API** 는 하드 한도인 30,000개 데이터 요소에 구애되지 않습니다.
* **[캔버스 도구 설명 API](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **[FilterManager API](./filter-api.md)**
* **[책갈피](./bookmarks-support.md)** 를 지원 

## <a name="api-v1100"></a>API v1.10.0
* `ILocalizationManager`를 추가
* **인증 API**

## <a name="api-v190"></a>API v1.9.0
* **[launchUrl API](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* 기능 스키마에서 새 형식 **fillRule** (그라데이션)을 지원
* 개체 속성용 기능 스키마에서 **규칙** 속성을 지원

## <a name="api-v170"></a>API v1.7.0
* **[RESJSON](./localization.md#resource-file)** 을 지원

## <a name="api-v162"></a>API v1.6.2
* 시각적 개체 내 편집 모드로 전환하는 시각적 개체용 **[편집 모드](./advanced-edit-mode.md)** 를 지원
* Html을 기반으로 하는 **[대화형(html) R Power BI 시각적 개체](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** 를 지원

## <a name="api-v150"></a>API v1.5.0
* 시각적 상호 작용을 위해 **[상호 작용 허용](./visuals-interactions.md)** 을 지원

## <a name="api-v140"></a>API v1.4.0
* **[지역화](./localization.md)** 를 지원

## <a name="api-v130"></a>API v1.3.0
* **[도구 설명](./add-tooltips.md)** 을 지원

## <a name="api-v120"></a>API v1.2.0
* 시각적 개체에 사용되는 색을 관리하기 위해 **colorPalette** 를 추가합니다.
* **다중 선택** 을 지원 - selectionManager는 `SelectionId`의 배열을 허용할 수 있습니다.
* R 스크립트를 사용하여 **[R 시각적 개체](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** 를 지원합니다.

## <a name="api-v110"></a>API v1.1.0
* iFrame에서 시각적 개체 디버그를 지원
* 더 빠른 iFrame 초기화를 사용하는 경량 샌드박스를 추가
* [Capabilities.objects가 "text" 형식을 지원하지 않음](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12) 문제를 수정
* 시각적 API 형식 정의 및 스키마를 업데이트하는 `pbiviz update`를 지원
* 특정 API 버전으로 시각적 개체를 만들기 위해 `pbiviz new`에서 `--api-version` 플래그를 지원
* API v1.2.0의 알파 릴리스를 지원

**시각적 개체 호스트**
* 데이터 선택에 사용되는 고유 식별자를 만드는 **createSelectionIdBuilder** 를 추가
* 시각적 개체의 선택 상태를 관리하고 변경 내용을 시각적 개체 호스트에 전달하는 **createSelectionManager** 를 추가
* 시각적 개체에서 사용할 기본 **색** 배열을 추가

## <a name="api-v100"></a>API v1.0.0
* 초기 API 릴리스
