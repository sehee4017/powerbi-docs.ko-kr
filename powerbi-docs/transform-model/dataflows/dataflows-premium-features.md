---
title: 데이터 흐름의 프리미엄 기능
description: Power BI 데이터 흐름에서 사용할 수 있는 프리미엄 기능 개요
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: ffd11a57267ef69aab7b999a29949c33163e52e8
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91638408"
---
# <a name="premium-features-of-dataflows"></a>데이터 흐름의 프리미엄 기능

Power BI Pro 및 Power BI Premium 사용자에 대해 데이터 흐름이 지원됩니다. 일부 기능은 Power BI Premium 구독에서만 사용할 수 있습니다. 이 문서에서는 프리미엄 전용 기능과 용도에 대해 자세히 설명합니다. 

다음 기능은 Power BI Premium에서만 사용할 수 있습니다.

* 향상된 컴퓨팅 엔진
* DirectQuery
* 계산된 엔터티
* 연결된 엔터티
* 증분 새로 고침

다음 섹션에서는 이러한 각 기능에 대해 자세히 설명합니다.

## <a name="the-enhanced-compute-engine"></a>향상된 컴퓨팅 엔진

Power BI의 향상된 컴퓨팅 엔진을 사용하면 Power BI Premium 구독자가 할당된 용량을 사용하여 데이터 흐름의 사용을 최적화할 수 있습니다. 향상된 컴퓨팅 엔진을 사용하면 다음과 같은 이점이 제공됩니다.

* *join* , *distinct* , *filter,* *group by* 를 수행하는 작업과 같이 계산된 엔터티에 대해 실행이 오래 걸리는 ETL 단계에 필요한 새로 고침 시간을 대폭 줄여 줍니다.
* 엔터티에 대해 DirectQuery 쿼리 수행

향상된 컴퓨팅 엔진을 사용하도록 설정하는 방법은 일반적인 질문에 대한 답변과 함께 다음에 설명됩니다.

### <a name="using-the-enhanced-compute-engine"></a>향상된 컴퓨팅 엔진 사용

향상된 컴퓨팅 엔진은 Power BI 서비스의 **용량 설정** 페이지에 있는 **데이터 흐름** 섹션에서 사용하도록 설정할 수 있습니다. 기본적으로 향상된 컴퓨팅 엔진은 **꺼짐** 으로 설정되어 있습니다. 향상된 컴퓨팅 엔진을 활성화하려면 다음 이미지와 같이 토글을 **켜기** 로 바꾸고 설정을 저장합니다. 

![향상된 컴퓨팅 엔진 켜기](media/dataflows-premium-features/compute-engine-settings.png)

> [!IMPORTANT]
> 향상된 컴퓨팅 엔진은 A3 이상의 Power BI 용량에 대해서만 작동합니다.

향상된 컴퓨팅 엔진이 켜지면 **데이터 흐름** 으로 돌아가서 동일한 용량에 있는 기존의 연결된 엔터티에서 만들어진 *join* 또는 *group by* 작업과 같은 복잡한 작업을 수행하는 계산된 엔터티의 성능이 향상된 것을 볼 수 있습니다. 

컴퓨팅 엔진을 최대한 활용하려면 다음과 같은 방법으로 ETL 단계를 두 개의 개별적인 데이터 흐름으로 분할합니다.

* **데이터 흐름 1** - 이 데이터 흐름은 데이터 원본에서 필요한 것만 수집하고 이를 데이터 흐름 2에 넣어야 합니다.
* **데이터 흐름 2** - 모든 ETL 작업은 이 두 번째 데이터 흐름에서 수행하되, 동일한 용량에 있는 데이터 흐름 1을 참조해야 합니다. 컴퓨팅 엔진이 반드시 사용되도록 하려면 다른 작업을 수행하기 전에 먼저 접기(filter, group by, distinct, join)가 가능한 작업을 수행해야 합니다.

### <a name="common-questions-and-answers"></a>일반적인 질문과 답변

**질문:** 향상된 컴퓨팅 엔진을 사용하도록 설정했는데 새로 고침이 더 느립니다. 이유가 무엇일까요?

**답변:** 향상된 컴퓨팅 엔진을 사용하도록 설정했는데 새로 고침 시간이 느려졌다면 두 가지 원인이 있을 수 있습니다.

 * 향상된 컴퓨팅 엔진을 사용하도록 설정한 경우 엔진이 제대로 작동하려면 어느 정도의 메모리가 필요합니다. 이에 따라 새로 고침을 수행하는 데 사용할 수 있는 메모리가 줄어들고 새로 고침이 지연될 가능성이 커지며, 결과적으로 동시에 새로 고칠 수 있는 데이터 흐름의 개수가 줄어듭니다. 이 문제를 해결하려면 향상된 컴퓨팅을 사용하도록 설정할 때 동시 데이터 흐름 새로 고침에 사용 가능한 메모리가 전과 동일하게 유지되도록 데이터 흐름에 할당되는 메모리를 늘리시기 바랍니다.

 * 새로 고침 속도가 더 느려질 수 있는 또 다른 이유는 컴퓨팅 엔진이 기존 엔터티 위에서만 작동하기 때문입니다. 데이터 흐름에서 데이터 흐름이 아닌 데이터 원본을 참조하는 경우에는 개선 사항이 표시되지 않습니다. 일부 빅 데이터 시나리오의 경우 데이터 원본에서의 초기 읽기 시에 데이터가 향상된 컴퓨팅 엔진으로 전달되어야 하기 때문에 더 느려지므로 성능이 향상되지 않습니다.  

**질문:** 향상된 컴퓨팅 엔진 토글이 표시되지 않습니다. 이유가 무엇일까요?

**답변:** 향상된 컴퓨팅 엔진은 세계 각 지역에 단계적으로 출시되고 있습니다. 2020년 말에는 모든 지역에서 지원될 것으로 예상됩니다.

**질문:** 컴퓨팅 엔진에서 지원하는 데이터 형식은 무엇인가요?

**답변:** 향상된 컴퓨팅 엔진 및 데이터 흐름은 현재 다음과 같은 데이터 형식을 지원합니다. 데이터 흐름이 이러한 데이터 형식을 사용하지 않을 경우 새로 고침 중에 오류가 발생합니다.

* 날짜/시간
* 10진수
* 텍스트
* 정수
* 표준 시간대
* True/False
* 날짜
* 시간

## <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Power BI (미리 보기)에서 데이터 흐름와 함께 DirectQuery 사용

DirectQuery를 사용하여 데이터 흐름에 직접 연결할 수 있으므로 관련 데이터를 가져오지 않고도 데이터 흐름에 직접 연결할 수 있습니다. 

데이터 흐름과 함께 DirectQuery를 사용하면 Power BI 및 데이터 흐름 프로세스를 다음과 같이 향상할 수 있습니다.

* **별도의 새로 고침 일정 필요 없음** - DirectQuery는 데이터 흐름에 직접 연결하므로 가져온 데이터 세트를 만들 필요가 없어집니다. 따라서 데이터 흐름과 함께 DirectQuery를 사용하면 데이터를 동기화하기 위한 데이터 흐름 및 데이터 세트의 새로 고침 일정을 별도로 만들 필요가 없습니다.

* **데이터 필터링** - DirectQuery는 데이터 흐름 내에 있는 데이터의 필터링된 보기를 작업하는 데 유용합니다. 데이터를 필터링하여 데이터 흐름 내 데이터의 작은 하위 집합으로 작업하려면 DirectQuery(및 컴퓨팅 엔진)를 사용하여 데이터 흐름 데이터를 필터링하고 필요한 필터링된 하위 집합으로 작업할 수 있습니다.


### <a name="using-directquery-for-dataflows"></a>데이터 흐름에 DirectQuery 사용

데이터 흐름과 함께 DirectQuery 사용은 2020년 5월 버전의 Power BI Desktop부터 제공되는 미리 보기 기능입니다. 

데이터 흐름과 함께 DirectQuery를 사용하기 위한 필수 조건도 있습니다.

* 데이터 흐름이 Power BI Premium 지원 작업 영역 내에 있어야 합니다.
* **컴퓨팅 엔진** 이 켜져 있어야 합니다.

### <a name="enable-directquery-for-dataflows"></a>데이터 흐름에 DirectQuery 사용

데이터 흐름을 DirectQuery 액세스에 사용할 수 있도록 하려면 향상된 컴퓨팅 엔진이 최적화된 상태여야 합니다. 데이터 흐름에 DirectQuery를 사용하도록 설정하려면 새로운 **향상된 컴퓨팅 엔진 설정** 옵션을 **켜짐** 으로 설정합니다. 다음 이미지는 올바로 선택한 설정을 보여 줍니다.

![직접 쿼리를 위한 세분화된 제어](media/dataflows-premium-features/compute-engine-granular-control.png)

해당 설정을 적용한 후 데이터 흐름을 새로 고쳐 최적화를 적용합니다.

### <a name="considerations-and-limitations-for-directquery"></a>DirectQuery에 대한 고려 사항 및 제한 사항

DirectQuery 및 데이터 흐름에는 몇 가지 알려진 제한 사항이 있습니다.

* 이 기능의 미리 보기 기간 중 데이터 흐름과 함께 DirectQuery를 사용하는 경우 일부 고객에게 시간 초과나 성능 문제가 발생할 수 있습니다. 이러한 문제는 미리 보기 기간 동안 적극적으로 해결됩니다.

* 가져오기 및 DirectQuery 데이터 원본이 있는 복합/혼합 모델은 현재 지원되지 않습니다.

* 대용량 데이터 흐름은 시각화를 볼 때 시간 제한 문제로 인한 어려움이 있을 수 있습니다. 시간 제한 문제가 발생하는 대용량 데이터 흐름은 가져오기 모드를 사용해야 합니다.

* DirectQuery를 사용하는 경우 데이터 원본 설정에서 데이터 흐름 커넥터가 잘못된 자격 증명을 표시합니다. 이는 동작에 영향을 주지 않으며 데이터 세트는 제대로 작동합니다. 

## <a name="computed-entities"></a>계산된 엔터티

Power BI Premium 구독과 함께 **데이터 흐름** 을 사용하는 경우 **스토리지 내 계산** 을 수행할 수 있습니다. 이렇게 하면 기존 데이터 흐름에서 계산을 수행하고 결과를 반환하여 보고서 만들기와 분석에 초점을 맞출 수 있습니다.

![계산된 엔터티](media/dataflows-premium-features/computed-entity.png)

스토리지 내 계산을 수행하려면 먼저 데이터 흐름을 만들고 해당 Power BI 데이터 흐름 스토리지로 데이터를 가져와야 합니다. 데이터가 포함된 데이터 흐름이 있으면 스토리지 내 계산을 수행하는 엔터티인 계산된 엔터티를 만들 수 있습니다.

### <a name="considerations-and-limitations-of-computed-entities"></a>계산된 엔터티의 고려 사항 및 제한 사항

* 조직의 Azure Data Lake Storage Gen2 계정에서 만든 데이터 흐름을 사용할 때 연결된 엔터티와 계산된 엔터티는 해당 엔터티가 동일한 스토리지 계정에 있을 경우에만 제대로 작동합니다. 

온-프레미스 및 클라우드 데이터로 조인된 데이터에 대한 계산을 수행하는 경우 각 원본(온-프레미스용 및 클라우드용)에 대해 새 데이터 흐름을 만든 다음, 이러한 두 데이터 원본에 대해 병합/계산할 세 번째 데이터 흐름을 만듭니다.

## <a name="linked-entities"></a>연결된 엔터티

Power BI Premium 구독과 함께 사용할 때 기존 데이터 흐름을 참조할 수 있습니다. 이를 통해 계산된 엔터티를 사용하여 이러한 엔터티에 대해 계산을 수행하거나 여러 데이터 흐름 내에서 재사용할 수 있는 "단일 원본" 테이블을 만들 수 있습니다.

## <a name="incremental-refresh"></a>증분 새로 고침

새로 고칠 때마다 모든 데이터를 끌어올 필요가 없도록 데이터 흐름을 증분 방식으로 새로 고치도록 설정할 수 있습니다. 이렇게 하려면 데이터 흐름을 선택한 다음, 증분 새로 고침 아이콘을 선택합니다.

![증분 새로 고침](media/dataflows-premium-features/incremental-refresh.png)

증분 새로 고침을 설정하면 날짜 범위를 지정하는 매개 변수가 데이터 흐름에 추가됩니다. 증분 새로 고침을 설정하는 방법에 대한 자세한 내용은 [증분 새로 고침](https://docs.microsoft.com/power-query/dataflows/incremental-refresh) 문서를 참조하세요.

### <a name="considerations-for-when-not-to-set-incremental-refresh"></a>증분 새로 고침을 설정하지 않을 때의 고려 사항

다음과 같은 상황에서는 데이터 흐름을 증분 새로 고침으로 설정하지 마세요.

* 데이터 흐름을 참조하는 연결된 엔터티는 증분 새로 고침을 사용하면 안 됩니다. 데이터 흐름은 쿼리 폴딩을 지원하지 않습니다(엔터티가 DirectQuery를 사용하는 경우에도). 
* 데이터 흐름을 참조하는 데이터 세트는 증분 새로 고침을 사용하지 않아야 합니다. 데이터 흐름에 대한 새로 고침은 일반적으로 잘 수행됩니다. 새로 고침이 예상보다 오래 걸리면 컴퓨팅 엔진 및/또는 DirectQuery 모드를 사용하는 것이 좋습니다.

## <a name="next-steps"></a>다음 단계
다음 문서에서는 데이터 흐름 및 Power BI에 관한 자세한 정보를 제공합니다.

* [데이터 흐름 및 셀프 서비스 데이터 준비 소개](dataflows-introduction-self-service.md)
* [데이터 흐름 만들기](dataflows-create.md)
* [데이터 흐름 구성 및 사용](dataflows-configure-consume.md)
* [Azure Data Lake Gen 2를 사용하도록 데이터 흐름 스토리지 구성](dataflows-azure-data-lake-storage-integration.md)
* [데이터 흐름에서 AI 사용](dataflows-machine-learning-integration.md)
* [데이터 흐름 제한 사항 및 고려 사항](dataflows-features-limitations.md)