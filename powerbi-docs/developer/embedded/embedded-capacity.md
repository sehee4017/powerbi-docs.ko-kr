---
title: Power BI 임베디드 분석의 용량 및 SKU
description: Power BI 임베디드 분석의 용량과 SKU를 살펴봅니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/17/2020
ms.openlocfilehash: 4102ed7307c9b7be40fb682befc4056094cbe6ad
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916938"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Power BI 임베디드 분석의 용량 및 SKU

프로덕션으로 전환 시 Power BI 임베디드 분석에는 임베디드 Power BI 콘텐츠 게시를 위해 용량( *A* , *EM* 또는 *P* SKU)이 필요합니다.

용량은 독점적 사용을 위해 예약된 전용 리소스 집합입니다. 이 용량을 보유하면 사용자별 라이선스를 구매할 필요 없이 사용자에게 대시보드, 보고서 및 데이터 세트를 게시할 수 있습니다. 또한 콘텐츠에 대해 신뢰할 수 있는 일관된 성능을 제공합니다.

>[!NOTE]
>게시하려면 Power BI Pro 계정이 하나 필요합니다.

## <a name="what-is-embedded-analytics"></a>임베디드 분석이란?

Power BI 임베디드 분석에는 두 솔루션이 포함됩니다.
* *Power BI Embedded*  - Azure 제품
* Power BI를 *Power BI Premium* 에 포함  - Office 제품

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded는 애플리케이션에 시각적 개체를 포함하려는 ISV와 개발자를 위한 제품입니다.

Power BI Embedded를 사용하는 애플리케이션에서는 사용자가 Power BI Embedded 용량에 저장된 콘텐츠를 사용할 수 있습니다.

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../../admin/service-premium-what-is.md)은 조직, 파트너, 고객 및 공급업체에 대한 단일 보기를 제공하는 완전한 BI 솔루션을 원하는 기업 고객을 위해 설계되었습니다.

Power BI Premium은 사용자가 모바일 앱, 내부 개발 앱 또는 Power BI 포털(Power BI 서비스)을 통해 콘텐츠를 사용할 수 있는 SaaS 제품입니다. Power BI Premium은 이를 통해 내부 및 외부 고객 모두를 대상으로 솔루션을 제공할 수 있습니다.

## <a name="capacity-and-skus"></a>용량 및 SKU

각 용량은 특정 SKU를 제공하고, 각 SKU는 메모리 및 컴퓨팅 성능에 대해 서로 다른 리소스 계층을 제공합니다. 필요한 SKU 유형은 배포하려는 솔루션의 유형에 따라 달라집니다.

각 계층에 대해 어떤 워크로드가 지원되는지 알아보려면 [Premium 용량에서 워크로드 구성](../../admin/service-admin-premium-workloads.md) 문서를 참조하세요.

용량을 계획하고 테스트하려면 다음 링크를 사용합니다.
* [용량 계획](embedded-capacity-planning.md)
* [테스트 방법](../../admin/service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>Power BI Embedded SKU

Power BI Embedded는 [*a* SKU](../../admin/service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios)와 함께 제공됩니다.

### <a name="power-bi-premium-skus"></a>Power BI Premium SKU

Power BI Premium은 두 가지 SKU, 즉 *P* 와 *EM* 을 제공합니다.
* [*P* 및 *EM* SKU](../../admin/service-premium-what-is.md#subscriptions-and-licensing)의 차이점 이해
* [Premium SKU 구매](../../admin/service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>어떤 SKU를 사용해야 하나요?

아래 표에는 기능, 해당 기능에 필요한 용량, 각각 필요한 특정 SKU가 요약되어 있습니다.

이 표에서 사용자 지정 앱은 포함된 분석을 사용하여 만든 웹앱을 말합니다. (JavaScript 또는 .NET SDK나 REST API를 사용하여) 사용자 지정 웹앱에 개발자로 포함하는 경우 UX를 제어하고 사용자 지정할 수 있습니다. Power BI 서비스, Power BI Mobile 등의 다른 포함 옵션을 사용하는 경우에는 이 기능을 사용할 수 없습니다.

| 시나리오 | Azure   | Office          |
|----------|---------|-----------------|
|          | (SKU) | (P 및 EM SKU) |
|[고객에 대한 콘텐츠 포함](embed-sample-for-customers.md)</br>(앱이 데이터 소유)     |✔        |✔        |
|[조직에 포함](embed-sample-for-your-organization.md)</br>(사용자가 데이터 소유)     |✖        |✔         |
|Microsoft 365 앱</br>(이전에는 Office 365 앱이라고 함)<ul><li>[에 포함](../../collaborate-share/service-embed-report-microsoft-teams.md)</li><li>[SharePoint에 포함](../../collaborate-share/service-embed-report-spo.md)</li></ul>     |✖        |✔        |
|[보안 URL 포함](../../collaborate-share/service-embed-secure.md)</br>(Power BI 서비스로부터 포함)     |✖        |✔        |

>[!NOTE]
>* Power BI 앱 작업 영역에 콘텐츠를 게시하려면 [Power BI Pro 라이선스](../../admin/service-admin-purchasing-power-bi-pro.md)가 필요합니다.
>* **P SKU** 를 사용해야만 Power BI 사용자가 Power BI 서비스에서 Power BI 앱 및 공유 콘텐츠를 사용할 수 있습니다.

### <a name="capacity-considerations"></a>용량 고려 사항

아래 표에는 결제 및 사용 고려 사항이 용량별로 나열되어 있습니다.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI 프리미엄</strong></p></td>
</tr>
<tr>
<td><p><strong>제안</strong></p></td>
<td style="text-align: center"><p>Azure</p></td>
<td style="text-align: center" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center"><p>A</p></td>
<td style="text-align: center"><p>EM</p></td>
<td style="text-align: center"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Billing</strong></td>
<td style="text-align: center">시간별</td>
<td style="text-align: center">매월</td>
<td style="text-align: center">매월</td>
</tr>
<tr>
<td><p><strong>약정</strong></td>
<td style="text-align: center">없음</td>
<td style="text-align: center">매년</td>
<td style="text-align: center">매월 또는 매년</td>
</tr>
<tr>
<td valign="top"><p><strong>사용 현황</strong></td>
<td style="text-align: center">Azure 리소스는 다음 작업이 가능합니다.<li><a href="azure-pbie-scale-capacity.md">확장 또는 축소</a></li><li><a href="azure-pbie-pause-start.md">일시 중지 및 재시작</a>
</td></li>
<td style="text-align: center">앱 및 Microsoft 애플리케이션에</br> 포함</td>
<td style="text-align: center">앱 및 Power BI 서비스에</br> 포함</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>SKU 메모리 및 컴퓨팅 성능

아래 표에서는 각 SKU의 리소스 및 한도를 설명합니다.

| 용량 노드 | 총 V 코어 | 백 엔드 V 코어 | RAM(GB) | 프런트 엔드 V 코어 | DirectQuery/Live Connection(초당) | 모델 새로 고침 병렬 처리 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
>[고객에 대한 콘텐츠 포함](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[조직에 포함](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [앱에서 포함](embed-from-apps.md)