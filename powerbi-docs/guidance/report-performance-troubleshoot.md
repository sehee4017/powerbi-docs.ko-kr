---
title: Power BI의 보고서 성능 문제 해결
description: Power BI에서 보고서 성능 저하를 진단하기 위한 문제 해결 가이드입니다.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: troubleshooting
ms.date: 04/15/2020
ms.openlocfilehash: 97af45ea90db1f0ccd2fdab7eba67ec91e580983
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417868"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Power BI의 보고서 성능 문제 해결

이 문서에서는 개발자와 관리자가 보고서 성능 저하 문제를 해결할 수 있는 지침을 제공합니다. 지침은 Power BI 보고서와 Power BI 페이지를 매긴 보고서에도 적용됩니다.

로드 속도가 느리거나 슬라이서 또는 다른 기능과 상호 작용할 때 업데이트 속도가 느려지는 보고서 사용자는 보고서 성능 저하를 식별할 수 있습니다. 보고서가 프리미엄 용량에 호스트되는 경우 [Power BI Premium 메트릭 앱](../admin/service-admin-premium-monitor-capacity.md)을 모니터링하여 보고서 성능 저하를 식별할 수도 있습니다. 이 앱은 Power BI Premium 구독의 상태 및 용량을 모니터링하는 데 도움이 됩니다.

## <a name="follow-flowchart-steps"></a>순서도 단계 따르기

다음 순서도를 사용하여 성능 저하의 원인을 이해하고 수행할 작업을 결정합니다.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="순서도 이미지가 표시되고 문서 텍스트에 자세히 설명됩니다." border="true":::

수행할 작업을 설명하는 6개의 순서도 종결자가 있습니다.

|종결자|작업|
|---------|---------|
|![순서도 종결자 1.](media/common/icon-01-red-30x30.png)|용량 관리<br />용량 크기 조정 |
|![순서도 종결자 2.](media/common/icon-02-red-30x30.png)|일반적인 보고서 사용 중 용량 작업 조사|
|![순서도 종결자 3.](media/common/icon-03-red-30x30.png)|아키텍처 변경<br />Azure Analysis Services 고려<br />온-프레미스 게이트웨이 확인|
|![순서도 종결자 4.](media/common/icon-04-red-30x30.png)|Azure Analysis Services 고려<br />Power BI Premium 고려|
|![순서도 종결자 5.](media/common/icon-05-red-30x30.png)|Power BI Desktop 성능 분석기 사용<br />보고서, 모델 또는 DAX 최적화|
|![순서도 종결자 6.](media/common/icon-06-red-30x30.png)|지원 티켓 모으기|

## <a name="take-action"></a>작업 수행

첫 번째 고려 사항은 성능 저하 보고서가 프리미엄 용량에 호스트되는지 여부를 이해하는 것입니다.

### <a name="premium-capacity"></a>프리미엄 용량

보고서가 프리미엄 용량에서 호스트되는 경우 **Power BI Premium 메트릭 앱** 을 사용하여 보고서 호스팅 용량이 용량 리소스를 수시로 초과하는지 여부를 확인합니다. CPU가 80%를 수시로 초과하는 경우에 발생합니다. 메모리의 경우 [활성 메모리 메트릭](../admin/service-premium-metrics-app.md#the-active-memory-metric)이 50을 초과하는 때입니다. 리소스에 대한 압박이 있을 때 [용량을 관리하거나 크기를 조정](../admin/service-admin-premium-manage.md)해야 할 수 있습니다(순서도 종결자 1). 적절한 리소스가 있는 경우 일반적인 보고서 사용 중에 용량 작업을 조사합니다(순서도 종결자 2).

### <a name="shared-capacity"></a>공유 용량

공유 용량에서 보고서를 호스트하는 경우에는 용량 상태를 모니터링할 수 없습니다. 다른 조사 접근 방식을 사용해야 합니다.

먼저 하루 또는 월의 특정 시간에 성능 저하가 발생하는지 확인합니다. 이러한 경우는 많은 사용자가 보고서를 열고 있는 것입니다. 다음과 같은 두 가지 옵션을 고려해야 합니다.

- 데이터 세트를 [Azure Analysis Services](/azure/analysis-services/analysis-services-overview)또는 프리미엄 용량으로 마이그레이션하여 쿼리 처리량을 늘립니다(순서도 종결자 4).
- Power BI Desktop [성능 분석기](../create-reports/desktop-performance-analyzer.md)를 사용하여 시각적 개체 및 DAX 수식과 같은 각 보고서 요소의 상태를 확인할 수 있습니다. 이 방법은 성능 문제의 원인이 쿼리인지 시각적 개체 렌더링인지 확인하는 데 특히 유용합니다(순서도 종결자 5).

시간 패턴이 없는 것을 확인하는 경우 다음으로 성능 저하가 특정 지리 또는 지역으로 격리되는지 여부를 고려합니다. 이러한 경우는 데이터 원본이 원격이고 네트워크 통신이 느릴 수 있습니다. 이 경우 다음을 고려하세요.

- [Azure Analysis Services](/azure/analysis-services/analysis-services-overview)를 사용하여 아키텍처 변경(순서도 종결자 3).
- [온-프레미스 데이터 게이트웨이 성능](/data-integration/gateway/service-gateway-performance) 최적화(순서도 종결자 3).

마지막으로, 시간 패턴이 없고 _또한_ 모든 지역에서 성능이 저하되는 것을 확인하는 경우 특정 디바이스, 클라이언트 또는 웹 브라우저에서 성능 저하가 발생하는지 여부를 조사합니다. 그렇지 않으면 앞에서 설명한 대로 Power BI Desktop [Performance Analyzer](../create-reports/desktop-performance-analyzer.md)를 사용하여 보고서나 모델을 최적화합니다(순서도 종결자 5).

특정 디바이스, 클라이언트 또는 웹 브라우저에서 성능이 저하되는 것을 확인하면 [Power BI 지원 페이지](https://powerbi.microsoft.com/support/)를 통해 지원 티켓을 만드는 것이 좋습니다(순서도 종결자 6).

## <a name="next-steps"></a>다음 단계

이 문서에 대한 자세한 내용은 다음 리소스를 참조하세요.

- [Power BI 지침](index.yml)
- [보고서 성능 모니터링](monitor-report-performance.md)
- [성능 분석기](../create-reports/desktop-performance-analyzer.md)
- 백서: [Power BI Enterprise 배포 계획](https://go.microsoft.com/fwlink/?linkid=2057861)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)
