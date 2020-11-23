---
title: 데이터 흐름 모범 사례
description: 데이터 흐름에 대한 모범 사례 링크 및 지침 모음
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/13/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 5adfcc3d4ff7d78335f250b92b856bcd14d64c0a
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94674746"
---
# <a name="dataflows-best-practices"></a>데이터 흐름 모범 사례

Power BI **데이터 흐름** 은 엔터프라이즈 중심의 데이터 준비 솔루션이며 사용, 재사용 및 통합을 위해 준비된 데이터 에코시스템을 사용하도록 설정합니다. 이 문서에서는 데이터 흐름을 최대한 이해하고 사용하는 데 도움이 되는 문서 및 기타 정보에 대한 링크와 함께 모범 사례 목록을 제공합니다.


## <a name="dataflows-best-practices-table-and-links"></a>데이터 흐름 모범 사례 표 및 링크

다음 표에서는 데이터 흐름을 만들거나 사용할 때의 모범 사례를 설명하는 문서에 대한 링크 모음을 제공합니다. 각 링크는 비즈니스 논리 개발, 복잡한 데이터 흐름 개발, 데이터 흐름 재사용 및 데이터 흐름으로 엔터프라이즈 규모를 달성하는 방법에 대한 정보를 포함합니다.


|**항목**  |**지침 영역**  |**문서 또는 콘텐츠에 대한 링크**  |
|---------|---------|---------|
|파워 쿼리     | 데이터 랭글링 환경을 최대한 활용하기 위한 팁과 요령        |[파워 쿼리 모범 사례](https://docs.microsoft.com/power-query/best-practices)        |
|계산 엔터티 활용     |데이터 흐름에서 계산된 엔터티를 사용하면 성능상의 이점이 있습니다.         |[컴퓨팅 엔터티 시나리오](https://docs.microsoft.com/power-query/dataflows/computed-entities-scenarios)         |
|복잡한 데이터 흐름 개발     |대규모의 고성능 데이터 흐름을 개발하기 위한 패턴         |[복합 데이터 흐름](https://docs.microsoft.com/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|데이터 흐름 다시 사용     |패턴, 지침 및 사용 사례         |[데이터 흐름 다시 사용](https://docs.microsoft.com/power-query/dataflows/best-practices-reusing-dataflows)         |
|대규모 구현     |엔터프라이즈 아키텍처를 보완하기 위한 대규모 사용 및 지침         |[데이터 흐름을 사용하는 데이터 웨어하우징](https://docs.microsoft.com/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|향상된 컴퓨팅 활용     |잠재적으로 데이터 흐름 성능을 25배까지 향상         |[향상된 컴퓨팅 엔진](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|워크로드 설정 최적화     |성능을 최대화할 수 있는 레버를 이해하여 데이터 흐름 인프라를 최대한 활용         |[데이터 흐름 워크로드 구성](dataflows-premium-workload-configuration.md)         |
|테이블 조인 및 확장     |성능이 향상된 조인 만들기         |[테이블 확장 작업 최적화](https://docs.microsoft.com/power-query/optimize-expanding-table-columns)         |
|쿼리 폴딩 지침     |원본 시스템을 사용하여 변환 속도 향상         |[쿼리 폴딩](https://docs.microsoft.com/power-query/power-query-folding)         |
|데이터 프로파일링 사용     |열 품질, 배포 및 프로필 이해         |[데이터 프로파일링 도구](https://docs.microsoft.com/power-query/data-profiling-tools)         |
|오류 처리 구현     |제안을 통해 탄력적으로 오류를 새로 고치는 강력한 데이터 흐름 개발         |[일반 오류의 패턴](https://docs.microsoft.com/power-query/dealing-with-errors)  </br> [복잡한 오류 처리](https://docs.microsoft.com/power-query/error-handling)      |
|스키마 뷰 사용      |넓은 테이블로 작업하고 스키마 수준 작업을 수행할 때 제작 환경 개선         |[스키마 뷰](https://docs.microsoft.com/power-query/schema-view)         |
|||


        
## <a name="next-steps"></a>다음 단계

다음 문서에서는 데이터 흐름 및 Power BI에 관한 자세한 정보를 제공합니다.

* [데이터 흐름 및 셀프 서비스 데이터 준비 소개](dataflows-introduction-self-service.md)
* [데이터 흐름 만들기](dataflows-create.md)
* [데이터 흐름 구성 및 사용](dataflows-configure-consume.md)
* [데이터 흐름의 프리미엄 기능](dataflows-premium-features.md)
* [Azure Data Lake Gen 2를 사용하도록 데이터 흐름 스토리지 구성](dataflows-azure-data-lake-storage-integration.md)
* [데이터 흐름에서 AI 사용](dataflows-machine-learning-integration.md)
* [데이터 흐름 제한 사항 및 고려 사항](dataflows-features-limitations.md)