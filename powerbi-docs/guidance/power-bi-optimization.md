---
title: Power BI 최적화 가이드
description: Power BI 최적화 가이드입니다.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: d718c9c7f627d735c083a46c1483815e3744faca
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378872"
---
# <a name="optimization-guide-for-power-bi"></a>Power BI 최적화 가이드

이 문서에서는 개발자와 관리자가 최적화된 Power BI 솔루션을 생성하고 유지 관리할 수 있는 지침을 제공합니다. 여러 아키텍처 계층에서 솔루션을 최적화할 수 있습니다. 계층은 다음과 같습니다.

- 데이터 원본
- 데이터 모델
- 대시보드, Power BI 보고서, Power BI 페이지를 매긴 보고서를 포함한 시각화
- 용량, 데이터 게이트웨이, 네트워크를 포함한 환경

## <a name="optimizing-the-data-model"></a>데이터 모델 최적화

데이터 모델은 전체 시각화 환경을 지원합니다. 데이터 모델은 외부 또는 내부에서 호스트되며 Power BI에서는 _데이터 세트_라고 부릅니다. 옵션을 이해하고 솔루션에 적합한 데이터 세트 유형을 선택하는 것이 중요합니다. 세 가지 데이터 세트 모드는 가져오기, DirectQuery 및 복합입니다. 자세한 내용은 [Power BI 서비스의 데이터 세트](../service-datasets-understand.md)와 [Power BI 서비스의 데이터 세트 모드](../service-dataset-modes-understand.md)를 참조하세요.

구체적인 데이터 세트 모드 지침은 다음을 참조하세요.

- [가져오기 모델링을 위한 데이터 축소 방법](import-modeling-data-reduction.md)
- [Power BI Desktop의 DirectQuery 모델 지침](directquery-model-guidance.md)
- [Power BI Desktop의 복합 모델 지침](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>시각화 최적화

Power BI 시각화는 대시보드, Power BI 보고서 또는 Power BI 페이지를 매긴 보고서일 수 있습니다. 각각 아키텍처가 다르므로 각각 고유한 지침이 있습니다. 

### <a name="dashboards"></a>대시보드

Power BI는 라이브 보고서 타일과 스트리밍 타일을 제외한 대시보드 타일을 위한 캐시를 유지 관리한다는 것을 이해하는 것이 중요합니다. 자세한 내용은 [Power BI에서 데이터 새로 고침(타일 새로 고침)](../refresh-data.md#tile-refresh)을 참조하세요. 데이터 세트가 동적 [RLS(행 수준 보안)](../service-admin-rls.md)를 적용하는 경우 타일이 사용자별로 캐시되므로 성능 영향을 이해해야 합니다.

라이브 보고서 타일을 대시보드에 고정하면 쿼리 캐시에서 보고서 타일이 제공되지 않습니다. 대신 보고서처럼 동작하고 백 엔드 코어에 대한 쿼리를 즉시 수행합니다.

이름에서 알 수 있듯이 캐시에서 데이터를 검색하면 데이터 원본을 사용할 때보다 더 일관되며 더 나은 성능이 제공됩니다. 이 기능을 활용하는 한 가지 방법은 사용자의 첫 번째 방문 페이지가 대시보드가 되도록 하는 것입니다. 종종 사용되고 많이 요청되는 시각적 개체를 대시보드에 고정합니다. 이러한 방식으로 대시보드는 적은 용량 부하로 일관된 성능을 제공하는 중요한 "첫 번째 방어선"이 됩니다. 사용자는 보고서를 계속 클릭하여 세부 정보를 분석할 수 있습니다.

DirectQuery 및 라이브 연결 데이터 세트의 경우, 데이터 원본을 쿼리하여 캐시가 주기적으로 업데이트됩니다. 기본적으로 1시간마다 업데이트되지만 데이터 세트 설정에서 다른 빈도를 구성할 수 있습니다. 캐시가 업데이트될 때마다 기본 데이터 원본에 쿼리를 전송하여 캐시를 업데이트합니다. 생성된 쿼리의 수는 해당 데이터 원본에 의존하는 대시보드에 고정된 시각적 개체의 수에 따라 달라집니다. 행 수준 보안을 사용하는 경우 각기 다른 보안 컨텍스트에 대해 쿼리가 생성됩니다. 예를 들어 사용자를 분류하는 두 가지 역할이 있고 해당 사용자에게 두 가지 데이터 보기가 있다고 생각해 보세요. Power BI는 쿼리 캐시 새로 고침 도중 두 가지 쿼리 집합을 생성합니다.

### <a name="power-bi-reports"></a>Power BI 보고서

Power BI 보고서 디자인을 최적화하기 위한 몇 가지 권장 사항이 있습니다.

> [!NOTE]
> 보고서가 DirectQuery 데이터 세트에 기반하는 경우, 추가 보고서 디자인 최적화에 대해서는 [Power BI Desktop의 DirectQuery 모델 지침(보고서 디자인 최적화)](directquery-model-guidance.md#optimize-report-designs)을 참조하세요.

#### <a name="apply-the-most-restrictive-filters"></a>가장 제한적인 필터 적용

시각적 개체는 표시해야 할 데이터가 많을수록 더 느리게 로드됩니다. 이 원칙은 명확해 보이지만 잊기 쉽습니다. 예를 들어 큰 데이터 세트가 있다고 가정합니다. 데이터 세트 위에 테이블이 있는 보고서를 빌드합니다. 최종 사용자는 페이지에서 슬라이서를 사용하여 원하는 행으로 이동하며, 일반적으로 몇십 개 행에만 관심이 있습니다.

흔히 저지르는 실수는 테이블의 기본 보기, 즉 1억 개 이상의 모든 행을 필터링하지 않은 상태로 두는 것입니다. 모든 행의 데이터가 메모리로 로드되고 새로 고칠 때마다 압축 해제됩니다. 이 처리를 하려면 메모리가 매우 많이 필요합니다. 이 문제를 해결하려면 "Top N" 필터를 사용하여 테이블에 표시되는 항목의 최대 수를 줄여야 합니다. 사용자에게 필요한 항목 수보다 큰 최대 수(예: 10,000개)를 설정하면 됩니다. 이에 따라 최종 사용자 환경은 그대로 유지되고 메모리 사용률이 크게 떨어집니다. 가장 중요한 점은 성능이 개선되는 것입니다.

보고서의 모든 시각적 개체에 위와 비슷한 디자인 방법이 제안됩니다. 스스로에게 물어보세요. 이 시각적 개체의 모든 데이터가 정말로 필요한가? 최종 사용자 환경에 미치는 영향을 최소화하면서 시각적 개체에 표시되는 데이터 양을 줄이도록 필터링하는 방법이 있는가? 특히 테이블에는 비용이 많이 들 수 있습니다.

#### <a name="limit-visuals-on-report-pages"></a>보고서 페이지에서 시각적 개체 제한

위의 원칙은 보고서 페이지에 추가되는 시각적 개체의 수에 동일하게 적용됩니다. 특정 보고서 페이지의 시각적 개체 수를 필요한 정도로만 제한하는 것이 좋습니다. [드릴스루 페이지](report-drillthrough.md)와 [보고서 페이지 도구 설명](report-page-tooltips.md)은 보고서에 시각적 개체를 더 넣지 않고 추가 세부 정보를 제공하는 유용한 방법입니다.

#### <a name="evaluate-custom-visual-performance"></a>사용자 지정 시각적 개체 성능 평가

높은 성능을 보장하기 위해 각 사용자 지정 시각적 개체의 역량에 대해 알아보아야 합니다. 제대로 최적화되지 않은 Power BI 시각적 개체는 전체 보고서의 성능에 부정적인 영향을 미칠 수 있습니다.

### <a name="power-bi-paginated-reports"></a>Power BI 페이지를 매긴 보고서

보고서의 데이터 검색에 모범 사례 디자인을 적용하면 Power BI 페이지를 매긴 보고서 디자인을 최적화할 수 있습니다. 자세한 내용은 [페이지를 매긴 보고서 데이터 검색 지침](report-paginated-data-retrieval.md)을 참조하세요.

또한 [페이지를 매긴 보고서 작업](../service-admin-premium-workloads.md#paginated-reports)에 할당된 메모리가 용량에 충분한지 확인합니다.

## <a name="optimizing-the-environment"></a>환경 최적화

용량 설정 구성, 데이터 게이트웨이 크기 조정, 네트워크 대기 시간 단축을 통해 Power BI 환경을 최적화할 수 있습니다.

### <a name="capacity-settings"></a>용량 설정

전용 용량(Power BI Premium(P SKU) 또는 Power BI Embedded(A SKU, A4-A6)에서 사용 가능)을 사용하는 경우, 용량 설정을 관리할 수 있습니다. 자세한 내용은 [프리미엄 용량 관리](../service-premium-capacity-manage.md)를 참조하세요. 용량을 최적화하는 방법에 대한 지침은 [프리미엄 용량 최적화](../service-premium-capacity-optimize.md)를 참조하세요.

### <a name="gateway-sizing"></a>게이트웨이 크기 조정

게이트웨이는 Power BI가 인터넷을 통해 직접 액세스할 수 없는 데이터에 액세스해야 하는 경우에 필요합니다. 온-프레미스 서버 또는 VM에서 호스트되는 IaaS(Infrastructure as a Service)에 [온-프레미스 데이터 게이트웨이](../service-gateway-onprem.md)를 설치할 수 있습니다.

게이트웨이 워크로드 및 크기 조정 권장 사항을 이해하려면 [온-프레미스 데이터 게이트웨이 크기 조정](gateway-onprem-sizing.md)을 참조하세요.

### <a name="network-latency"></a>네트워크 대기 시간

네트워크 대기 시간은 Power BI 서비스 연결에 대한 요청 및 전달할 응답에 필요한 시간이 늘어나면 보고서 성능에 영향을 줄 수 있습니다. Power BI의 테넌트는 특정 지역에 할당됩니다.

> [!TIP]
> 테넌트의 위치를 확인하려면 [내 Power BI 테넌트는 어디에 있나요?](../service-admin-where-is-my-tenant-located.md)를 참조하세요.

테넌트의 사용자가 Power BI 서비스에 액세스하는 경우 해당 요청은 항상 이 영역에 라우팅됩니다. 요청이 Power BI 서비스에 도달하면 서비스는 추가 요청을 기본 데이터 원본 또는 게이트웨이 등으로 보낼 수 있습니다. 이 또한 네트워크 대기 시간의 영향을 받습니다.

[Azure 속도 테스트](https://azurespeedtest.azurewebsites.net/)와 같은 도구는 클라이언트와 Azure 지역 간의 네트워크 대기 시간을 표시합니다. 일반적으로 네트워크 대기 시간의 영향을 최소화하려면 데이터 원본, 게이트웨이 및 Power BI 클러스터를 최대한 가깝게 유지해야 합니다. 가급적 동일한 지역 내에 있는 것이 좋습니다. 네트워크 대기 시간이 문제가 되는 경우 클라우드에서 호스트되는 가상 머신 안에 게이트웨이 및 데이터 원본을 배치하여 Power BI 클러스터와의 거리를 줄이세요.

## <a name="monitoring-performance"></a>성능 모니터링

성능을 모니터링하여 병목 상태를 식별할 수 있습니다. 느린 쿼리 또는 보고서 시각적 개체가 지속적인 최적화의 중심이 되어야 합니다. 모니터링은 Power BI Desktop의 디자인 타임이나 Power BI Premium 용량의 프로덕션 워크로드에서 수행할 수 있습니다. 자세한 내용은 [Power BI에서 보고서 성능 모니터링](monitor-report-performance.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

이 문서에 대한 자세한 내용은 다음 리소스를 참조하세요.

- [Power BI 지침](index.yml)
- [보고서 성능 모니터링](monitor-report-performance.md)
- 백서: [Power BI Enterprise 배포 계획](https://go.microsoft.com/fwlink/?linkid=2057861)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)
