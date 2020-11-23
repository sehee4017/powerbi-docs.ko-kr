---
title: 관리 포털을 사용하여 Power BI Premium 용량 모니터링
description: Power BI 관리 포털을 사용하여 프리미엄 용량을 모니터링합니다.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: b6f6b819b5c31f655d0c0dc43d8852cb34b5a7a2
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512059"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>관리 포털에서 용량 모니터링

관리 포털의 **용량 설정** 영역에 있는 **상태** 탭에서는 용량과 사용 가능한 워크로드에 대한 메트릭 요약을 제공합니다.  

![포털의 용량 상태 탭](media/service-admin-premium-monitor-portal/admin-portal-health.png)

보다 포괄적인 메트릭이 필요한 경우 [Power BI Premium 용량 메트릭](service-admin-premium-monitor-capacity.md) 앱을 사용 합니다. 앱은 드릴다운과 필터링은 물론, 용량 성능에 영향을 주는 거의 모든 측면에 대한 가장 세부적인 메트릭을 제공합니다. 자세히 알아보려면 [앱을 사용하여 프리미엄 용량 모니터링](service-admin-premium-monitor-capacity.md)을 참조하세요.

> [!IMPORTANT]
> Power BI Premium 용량의 리소스 사용률이 높아서 성능 또는 안정성 문제가 발생할 경우 문제를 식별하고 해결할 수 있도록 알림 메일을 받을 수 있습니다. 이는 오버로드된 용량 문제를 해결하는 간소화된 방법이 될 수 있습니다. 자세한 내용은 [용량 및 안정성 알림](service-interruption-notifications.md#capacity-and-reliability-notifications)을 참조하세요.

> [!NOTE]
> Power BI Premium은 최근 **Premium Gen2** 라는 새 버전의 Premium을 출시했으며, 이 버전은 현재 미리 보기로 제공됩니다. Premium Gen2는 프리미엄 용량 관리를 간소화하고 관리 오버헤드를 줄입니다. 자세한 내용은 [Power BI Premium 2세대(미리 보기)](service-premium-what-is.md#power-bi-premium-generation-2-preview)를 참조하세요.

## <a name="system-metrics"></a>시스템 메트릭

**상태** 탭 맨 위의 CPU 사용률과 메모리 사용량은 용량에 대한 가장 중요한 메트릭의 빨리 보기를 제공합니다. 이러한 메트릭은 용량에 사용 가능한 모든 워크로드를 포함하여 누적됩니다.

| **메트릭** | **설명** |
| --- | --- |
| CPU 사용률 | 사용 가능한 총 CPU의 백분율로 나타낸 평균 CPU 사용률입니다. |
| 메모리 사용량 | GB(기가바이트) 단위의 평균 메모리 사용량입니다.|

## <a name="workload-metrics"></a>워크로드 메트릭

용량에 사용할 수 있는 각 워크워드에 대한 메트릭입니다. CPU 사용률과 메모리 사용량이 표시됩니다.

| **메트릭** | **설명** |
| --- | --- |
| CPU 사용률 | 사용 가능한 총 CPU의 백분율로 나타낸 평균 CPU 사용률입니다. |
| 메모리 사용량 | GB(기가바이트) 단위의 평균 메모리 사용량입니다.|

### <a name="detailed-workload-metrics"></a>자세한 워크로드 메트릭

각 워크로드에 추가 메트릭이 있습니다. 표시되는 메트릭 유형은 워크로드에 따라 달라집니다. 워크로드에 대한 자세한 메트릭을 보려면 확장(아래쪽) 화살표를 클릭합니다.

![워크로드 상태 확장](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>데이터 흐름

##### <a name="dataflow-operations"></a>데이터 흐름 작업

| **메트릭** | **설명** |
| --- | --- |
| 총 개수 | 각 데이터 흐름에 대한 총 새로 고침 수입니다. |
| 성공한 수 | 각 데이터 흐름에 대해 성공한 총 새로 고침 수입니다.|
| 평균 기간(분) | 데이터 흐름에 대한 평균 새로 고침 기간(분) |
| 최대 기간(분) | 데이터 흐름에 대해 가장 오래 실행된 새로 고침 기간(분)입니다. |
| 평균 대기 시간(분) | 데이터 흐름 새로 고침의 예약 시간과 시작 시간 사이의 평균 지연 시간(분)입니다. |
| 최대 대기 시간(분) | 데이터 흐름에 대한 최대 대기 시간(분)입니다.  |

#### <a name="datasets"></a>데이터 세트

##### <a name="refresh"></a>새로 고침

| **메트릭** | **설명** |
| --- | --- |
| 총 개수 | 각 데이터 세트의 총 새로 고침 횟수입니다. |
| 성공한 수 | 각 데이터 세트에 대해 성공한 총 새로 고침 수입니다. |
| 실패한 수 | 각 데이터 세트에 대해 실패한 총 새로 고침 수입니다. |
| 성공률  | 성공한 새로 고침 수를 총 새로 고침 수로 나눈 값입니다. 안정성. |
| 평균 기간(분) | 데이터 세트의 평균 새로 고침 기간(분)입니다.  |
| 최대 기간(분) | 데이터 세트에 대해 가장 오래 실행된 새로 고침 기간(분)입니다. |
| 평균 대기 시간(분) | 데이터 세트 새로 고침의 예약 시간과 시작 시간 사이의 평균 지연 시간(분)입니다. |
| 최대 대기 시간(분) | 데이터 세트에 대한 최대 대기 시간(분)입니다. |

##### <a name="query"></a>쿼리

| **메트릭** | **설명** |
| --- | --- |
| 총 개수 | 데이터 세트에 대해 실행된 총 쿼리 수입니다. |
| 평균 기간(밀리초) |데이터 세트에 대한 평균 쿼리 기간(밀리초)|
| 최대 기간(ms) |데이터 세트에서 가장 오래 실행된 쿼리 기간(밀리초)입니다. |
| 평균 대기 시간(밀리초) |데이터 세트의 평균 쿼리 대기 시간(밀리초)입니다. |
| 최대 대기 시간(밀리초) |데이터 세트에서 가장 오래 대기한 쿼리 기간(밀리초)입니다. |

##### <a name="eviction"></a>제거

| **메트릭** | **설명** |
| --- | --- |
| 모델 수 | 이 용량에 대한 총 데이터 세트 제거 수입니다. 용량에서 메모리 부족 문제가 발생하면 노드가 메모리에서 하나 이상의 데이터 세트를 제거합니다. 현재 실행 중인 쿼리/새로 고침 작업이 없는 비활성 상태의 데이터 세트가 먼저 제거됩니다. 그런 다음, '최근에 사용되지 않은 것'(LRU)을 기준으로 제거됩니다. |

#### <a name="paginated-reports"></a>페이지를 매긴 보고서

##### <a name="report-execution"></a>보고서 실행

| **메트릭** | **설명** |
| --- | --- |
| 실행 수  | 사용자가 보고서를 실행하고 본 횟수입니다.|

##### <a name="report-usage"></a>보고서 사용량

| **메트릭** | **설명** |
| --- | --- |
| 성공한 수 | 사용자가 보고서를 본 횟수입니다. |
| 실패한 수 |사용자가 보고서를 본 횟수입니다.|
| 행 개수 |보고서의 데이터 행 수입니다. |
| 데이터 검색 기간(밀리초) |보고서의 데이터를 검색하는 데 걸리는 평균 시간(밀리초). 이 기간이 길면 쿼리 속도가 느리거나 다른 데이터 원본 문제가 있음을 나타낼 수 있습니다.  |
| 처리 기간(밀리초) |보고서의 데이터를 처리하는 데 걸리는 평균 시간(밀리초)입니다. |
| 렌더링 기간(밀리초) |브라우저에서 보고서를 렌더링하는 데 걸리는 평균 시간(밀리초)입니다. |

> [!NOTE]
> **AI** 워크로드에 대한 자세한 메트릭은 아직 사용할 수 없습니다.

## <a name="next-steps"></a>다음 단계

이제 Power BI Premium 용량을 모니터링하는 방법을 이해했으므로 용량 최적화에 대해 자세히 알아보세요.

> [!div class="nextstepaction"]
> [Power BI Premium 용량 최적화](service-premium-capacity-optimize.md)


Power BI는 Power BI Premium Gen2를 미리 보기 버전으로 소개했습니다. 이 버전은 다음과 같은 향상된 기능을 통해 Power BI Premium 환경을 개선합니다.
* 성능
* 사용자 단위 라이선싱
* 더 큰 규모
* 개선된 메트릭
* 자동 확장
* 관리 오버헤드 감소

Power BI Premium Gen2에 대한 자세한 내용은 [Power BI Premium 2세대(미리 보기)](service-premium-what-is.md#power-bi-premium-generation-2-preview)를 참조하세요.