---
title: Power BI Desktop에서 향상된 데이터 세트 메타데이터 사용
description: 이 문서에서는 Power BI에서 향상된 데이터 세트 메타데이터를 사용하는 방법을 설명합니다.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/08/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 661e50617094d396e8beb887ac0e4a27c28c2ca7
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906991"
---
# <a name="using-enhanced-dataset-metadata"></a>향상된 데이터 세트 메타데이터 사용

Power BI Desktop 보고서를 만들 때 해당 PBIX 및 PBIT 파일에서도 데이터 세트 메타데이터를 만듭니다. 이전에는 메타데이터가 Power BI Desktop에 한정된 형식으로 저장되었습니다. 메타데이터는 base-64로 인코딩된 M 식과 데이터 원본을 사용했고, Power BI는 메타데이터가 저장된 방법에 대해 가정했습니다.

**향상된 데이터 세트 메타데이터** 기능이 릴리스되어 해당 제한 사항이 대부분 제거되었습니다. PBIX 파일은 파일을 열 때 향상된 메타데이터로 자동 업그레이드됩니다. **향상된 데이터 세트 메타데이터** 를 사용하면 Power BI Desktop에서 만든 메타데이터는 [테이블 형식 개체 모델](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)을 기반으로 하는 Analysis Services 테이블 형식 모델에 사용되는 것과 비슷한 형식을 사용합니다.


**향상된 데이터 세트 메타데이터** 기능은 전략적이고 기본적입니다. 향후 Power BI 기능은 해당 메타데이터를 기반으로 빌드됩니다. 이러한 다른 기능은 향상된 데이터 세트 메타데이터의 이점을 제공합니다.

- [Power BI 데이터 세트 관리용 XMLA 읽기/쓰기](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)
- 차세대 기능을 활용하기 위해 Analysis Services 워크로드를 Power BI로 마이그레이션합니다.

## <a name="limitations"></a>제한 사항
SQL Server, Oracle, Teradata 및 레거시 HANA 연결을 위한 향상된 메타데이터 지원 이전에 Power BI Desktop은 데이터 모델에 네이티브 쿼리를 추가했습니다. 이 쿼리는 Power BI 서비스 데이터 모델에 사용됩니다. 향상된 메타데이터 지원 덕분에 Power BI 서비스 데이터 모델은 런타임에 네이티브 쿼리를 다시 생성합니다. Power BI Desktop에서 만든 쿼리는 사용되지 않습니다. 대부분의 경우 이 검색은 올바르게 자체를 확인하지만 기본 데이터를 읽지 않으면 일부 변환이 작동하지 않습니다. 이전에 작업한 보고서에 몇 가지 오류가 표시될 수도 있습니다. 예를 들어 다음과 같은 오류가 표시됩니다. 

“‘Dimension City’ 테이블의 M 쿼리를 네이티브 원본 쿼리로 변환할 수 없습니다. 나중에 다시 시도하거나 고객 지원팀에 문의하세요. 고객 지원팀에 문의한 경우 이러한 세부 정보를 제공해 주세요.” 

Power BI Desktop의 세 가지 위치에서 쿼리를 수정할 수 있습니다.

- 변경 내용을 적용하거나 새로 고치는 경우.
- Power Query 편집기의 경고 표시줄에서 식을 데이터 원본으로 접을 수 없음을 알려 줍니다.
    :::image type="content" source="media/desktop-enhanced-dataset-metadata/enhanced-metadata-apply-query-changes.png" alt-text="쿼리 변경 내용 적용 메시지의 스크린샷: 식을 데이터 원본으로 접을 수 없습니다.":::
- 보고서를 열 때 평가를 실행하여 지원되지 않는 쿼리가 있는지 확인하는 경우. 이러한 평가를 실행하면 성능에 영향을 미칠 수 있습니다.


## <a name="next-steps"></a>다음 단계

Power BI Desktop으로 모든 종류의 작업을 수행할 수 있습니다. 해당 기능에 대한 자세한 내용은 다음 리소스를 확인하세요.

* [Power BI Desktop이란?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop의 새로운 기능](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop을 사용한 쿼리 개요](../transform-model/desktop-query-overview.md)
* [Power BI Desktop의 데이터 형식](desktop-data-types.md)
* [Power BI Desktop에서 데이터 셰이핑 및 결합](desktop-shape-and-combine-data.md)
* [Power BI Desktop의 일반적인 쿼리 작업](../transform-model/desktop-common-query-tasks.md)
