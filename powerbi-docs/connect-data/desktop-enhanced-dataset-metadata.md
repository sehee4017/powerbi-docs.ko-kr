---
title: Power BI Desktop에서 향상된 데이터 세트 메타데이터 사용
description: 이 문서에서는 Power BI에서 향상된 데이터 세트 메타데이터를 사용하는 방법을 설명합니다.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 09/22/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 2c5e465026f1ba7564bda18ad3b005b024a663a7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404988"
---
# <a name="using-enhanced-dataset-metadata"></a>향상된 데이터 세트 메타데이터 사용

Power BI Desktop 보고서를 만들 때 해당 PBIX 및 PBIT 파일에서도 데이터 세트 메타데이터를 만듭니다. 이전에는 메타데이터가 Power BI Desktop에 한정된 형식으로 저장되었습니다. Base-64로 인코딩된 M 식과 데이터 원본을 사용했고 메타데이터가 저장된 방법에 대한 가정이 생성되었습니다.

**향상된 데이터 세트 메타데이터** 기능이 릴리스되어 해당 제한 사항이 대부분 제거되었습니다. PBIX 파일은 파일을 열 때 향상된 메타데이터로 자동 업그레이드됩니다. **향상된 데이터 세트 메타데이터** 를 사용하면 Power BI Desktop에서 만든 메타데이터는 [테이블 형식 개체 모델](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)을 기반으로 하는 Analysis Services 테이블 형식 모델에 사용되는 것과 비슷한 형식을 사용합니다.


향후 Power BI 기능은 메타데이터를 기반으로 할 것이므로 **향상된 데이터 세트 메타데이터** 기능은 전략적이며 기초적인 기능입니다. 향상된 데이터 세트 메타데이터를 활용하기 위해 제공하는 몇 가지 추가 기능에는 Power BI 데이터 세트를 관리하는 작업과 차세대 기능을 활용하기 위해 Analysis Services 워크로드를 Power BI로 마이그레이션하는 작업을 위한 [XMLA 읽기/쓰기](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)가 포함됩니다.


## <a name="next-steps"></a>다음 단계

Power BI Desktop으로 모든 종류의 작업을 수행할 수 있습니다. 해당 기능에 대한 자세한 내용은 다음 리소스를 확인하세요.

* [Power BI Desktop이란?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop의 새로운 기능](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop을 사용한 쿼리 개요](../transform-model/desktop-query-overview.md)
* [Power BI Desktop의 데이터 형식](desktop-data-types.md)
* [Power BI Desktop에서 데이터 셰이핑 및 결합](desktop-shape-and-combine-data.md)
* [Power BI Desktop의 일반적인 쿼리 작업](../transform-model/desktop-common-query-tasks.md)