---
title: 데이터 흐름 제한 사항, 제한 사항, 지원되는 커넥터 및 기능
description: 데이터 흐름의 모든 기능 개요
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: b8811d9b869d4aa3592c9ed3531d067701b544a8
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91638366"
---
# <a name="dataflows-limitations-and-considerations"></a>데이터 흐름 제한 사항 및 고려 사항

다음 섹션에서 설명하는 것처럼 사용자가 유의해야 하는 작성, 새로 고침 및 용량 관리에 관련된 몇 가지 데이터 흐름 제한 사항이 있습니다.

## <a name="dataflow-authoring"></a>데이터 흐름 작성

데이터 흐름을 작성할 때 사용자는 다음 고려 사항에 유의해야 합니다.

* 데이터 흐름의 작성은 PQO(Power Query Online) 환경에서 수행됩니다. [파워 쿼리 제한](https://docs.microsoft.com/power-query/power-query-online-limits)에 설명된 제한 사항을 참조하세요.
데이터 흐름 작성은 PQO(Power Query Online) 환경에서 수행되기 때문에 데이터 흐름 워크로드 구성에서 수행되는 업데이트는 새로 고침에만 영향을 주며 작성 환경에는 영향을 주지 않습니다.

* 데이터 흐름은 소유자만 수정할 수 있습니다.

* 데이터 흐름은 ‘내 작업 영역’에서 사용할 수 없습니다.

* 게이트웨이 데이터 원본을 사용하는 데이터 흐름은 동일한 데이터 원본의 여러 자격 증명을 지원하지 않습니다.

* Web.Page 커넥터를 사용하려면 게이트웨이가 필요합니다.

## <a name="api-considerations"></a>API 고려 사항

지원되는 데이터 흐름 REST API에 관한 자세한 내용은 [REST API 참조](https://docs.microsoft.com/rest/api/power-bi/dataflows)에서 찾을 수 있습니다. 유의해야 하는 몇 가지 고려 사항은 다음과 같습니다.

* 데이터 흐름 내보내기 및 가져오기를 수행하면 해당 데이터 흐름에 새 ID가 제공됩니다.

* 연결된 엔터티를 포함하는 데이터 흐름을 가져와도 데이터 흐름 내에서 기존 참조는 수정되지 않습니다(해당 쿼리는 데이터 흐름을 가져오기 전에 수동으로 수정해야 함).

* 가져오기 API를 사용하여 처음으로 만든 데이터 흐름은 *CreateOrOverwrite* 매개 변수로 덮어쓸 수 있습니다.

## <a name="dataflows-in-shared"></a>공유의 데이터 흐름

공유 용량에는 데이터 흐름의 제한 사항이 있습니다.

* 데이터 흐름을 새로 고칠 때 공유의 시간 제한은 엔터티당 2시간이고 데이터 흐름당 3시간입니다.
* 쿼리의 ‘로드 사용’ 속성이 사용되지 않으면 연결된 엔터티는 데이터 흐름 내에 존재할 수 있지만 공유 데이터 흐름에서 만들 수는 없습니다.
* 계산된 엔터티는 공유 데이터 흐름에서 만들 수 없습니다.
* AutoML 및 Cognitive Services는 공유 데이터 흐름에서 사용할 수 없습니다.
* 증분 새로 고침은 공유 데이터 흐름에서 작동하지 않습니다.

## <a name="dataflows-in-premium"></a>프리미엄의 데이터 흐름

프리미엄에 있는 데이터 흐름에는 다음과 같은 제한 사항 및 고려 사항이 있습니다.

**새로 고침 및 데이터 고려 사항:**

* 데이터 흐름을 새로 고칠 때 시간 제한은 24시간입니다(엔터티 및/또는 데이터 흐름의 구분 없음).

* 증분 새로 고침 정책에서 일반 새로 고침으로 또는 그 반대로 데이터 흐름을 변경하면 모든 데이터가 삭제됩니다.

* 데이터 흐름의 스키마를 수정하면 모든 데이터가 삭제됩니다.

**연결된 엔터티 및 계산된 엔터티:**

* 연결된 엔터티는 32개 참조 수준까지 내려갈 수 있습니다.

* 연결된 엔터티의 순환 종속성은 허용되지 않습니다.

* 온-프레미스 데이터 원본에서 해당 데이터를 가져오는 일반 엔터티를 사용하여 연결된 엔터티를 조인할 수 없습니다.

* 데이터 흐름에서 하나의 쿼리(예: 쿼리 *A*)가 다른 쿼리(쿼리 *B*)의 계산에 사용되는 경우, 쿼리 *B*는 계산된 엔터티가 됩니다. 계산된 엔터티는 온-프레미스 원본을 참조할 수 없습니다.


**컴퓨팅 엔진:**

* 컴퓨팅 엔진을 사용하는 동안 데이터 수집을 위해 초기에 시간이 10%~20% 정도 증가합니다.

  1. 이는 컴퓨팅 엔진에 있는 첫 번째 데이터 흐름에만 적용되며 데이터 원본에서 데이터를 읽습니다.
  2. 원본 1을 사용하는 후속 데이터 흐름은 동일한 페널티를 발생시키지 않습니다.

* 컴퓨팅 엔진은 특정 작업에만 사용하며 연결된 엔터티를 통해 또는 계산된 엔터티로 사용되는 경우에만 사용합니다. [이 블로그 게시물](http://petcu40.blogspot.com/2019/06/m-folding-in-enhanced-engine-of-power.html)에서 전체 작업 목록을 사용할 수 있습니다.


**용량 관리:**

* 의도적으로 프리미엄 Power BI 용량에는 해당 용량이 낮은 메모리에서 실행되는 경우 다양한 방법으로 워크로드를 제한하는 내부 리소스 관리자가 있습니다.

  1. 데이터 흐름의 경우 이 제한 압력은 사용 가능한 M 컨테이너 수를 줄입니다.
  2. 데이터 크기에 맞게 적절히 크기가 조정된 컨테이너를 사용하여 데이터 흐름의 메모리를 100%로 설정할 수 있으며, 워크로드가 컨테이너 수를 적절하게 관리합니다.

* 워크로드에 할당된 총 메모리를 컨테이너에 할당된 메모리 양으로 나누면 대략적인 컨테이너 수를 알아볼 수 있습니다.

## <a name="dataflow-usage-in-datasets"></a>데이터 세트의 데이터 흐름 사용량

* Power BI Desktop에서 데이터 세트를 만든 다음, Power BI 서비스에 게시하는 경우 Power BI Desktop에서 데이터 흐름 데이터 원본에 사용되는 자격 증명이 데이터 세트가 서비스에 게시될 때 사용되는 것과 동일한 자격 증명인지 확인합니다.
  1. 해당 자격 증명이 동일한지 확인하지 못하면 데이터 세트를 새로 고칠 때 ‘키를 찾을 수 없음’ 오류가 발생합니다.

## <a name="next-steps"></a>다음 단계
다음 문서에서는 데이터 흐름 및 Power BI에 관한 자세한 정보를 제공합니다.

* [데이터 흐름 및 셀프 서비스 데이터 준비 소개](dataflows-introduction-self-service.md)
* [데이터 흐름 만들기](dataflows-create.md)
* [데이터 흐름 구성 및 사용](dataflows-configure-consume.md)
* [Azure Data Lake Gen 2를 사용하도록 데이터 흐름 스토리지 구성](dataflows-azure-data-lake-storage-integration.md)
* [데이터 흐름의 프리미엄 기능](dataflows-premium-features.md)
* [데이터 흐름에서 AI 사용](dataflows-machine-learning-integration.md)

