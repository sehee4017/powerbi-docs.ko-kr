---
title: Power BI 및 Azure 송신
description: Azure 송신 요금과 테넌트 위치 기반 Power BI 및 Power BI Premium 이해
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: c93299a2066dd2f15843048742e857495db7242a
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85230603"
---
# <a name="power-bi-and-azure-egress"></a>Power BI 및 Azure 송신

Azure 데이터 원본과 Power BI를 함께 사용하면 Power BI 테넌트가 Azure 데이터 원본과 동일한 지역에 있도록 하여 Azure 요금을 방지할 수 있습니다.

데이터 원본을 배포할 때 Power BI 테넌트가 동일한 Azure 지역에 배포되면 예약된 새로 고침 및 DirectQuery 상호 작용에 대한 송신 요금이 발생하지 않습니다. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Power BI 테넌트의 위치 확인

Power BI 테넌트의 위치를 확인하려면 [내 Power BI 테넌트는 어디에 있습니까?](../admin/service-admin-where-is-my-tenant-located.md) 문서를 참조하세요.

Power BI Premium Multi-Geo 고객의 경우 Power BI 테넌트가 일부 Azure 기반 데이터 원본에 최적의 위치에 있지 않은 경우, 원하는 Azure 지역에서 Power BI Premium Multi-Geo를 배포하여 Power BI 테넌트와 데이터 원본이 동일한 Azure 지역 내에 있을 경우의 이점을 활용하세요.

## <a name="next-steps"></a>다음 단계

Power BI Premium 또는 Multi-Geo에 대한 자세한 내용을 보려면 다음 리소스를 살펴보세요.

* [Microsoft Power BI Premium이란?](../admin/service-premium-what-is.md)
* [Power BI 프리미엄 구매 방법](../admin/service-admin-premium-purchase.md)
* [Power BI Premium에 대한 Multi-Geo 지원(미리](../admin/service-admin-premium-multi-geo.md) 보기)
* [내 Power BI 테넌트는 어디에 있나요?](../admin/service-admin-where-is-my-tenant-located.md)
* [Power BI 프리미엄 FAQ](../admin/service-premium-faq.md)
