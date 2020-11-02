---
title: Power BI에서 고객 관리형 키 사용
description: Power BI에서 고객 관리형 키를 사용하는 방법을 알아봅니다.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 10/21/2020
LocalizationGroup: Premium
ms.openlocfilehash: fc93ae0f54bfe4f72ec18687829e9eb78dfaedd7
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349371"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Power BI에서 고객 관리형 키 사용

Power BI는 미사용 데이터 및 처리 중인 데이터를 암호화합니다. 기본적으로 Power BI는 Microsoft 관리형 키를 사용하여 데이터를 암호화합니다. 조직은 보고서 이미지에서 프리미엄 용량의 가져온 데이터 세트에 이르기까지 Power BI 전체에서 미사용 사용자 콘텐츠 암호화를 위해 자체 키를 사용하도록 선택할 수 있습니다. 

## <a name="why-use-customer-managed-keys"></a>고객 관리형 키를 사용하는 이유

조직은 Power BI CMK(고객 관리형 키)를 사용하여 클라우드 서비스 공급자(이 경우 Microsoft)와 함께 미사용 데이터 암호화를 위한 규정 준수 요구 사항을 충족할 수 있습니다. CMK는 새로운 Power BI Premium 고객에게만 제공되며 조직이 제공되고 관리되는 키를 사용하여 Power BI 사용자 콘텐츠를 암호화할 수 있도록 합니다. 고객 관리형 키를 해지하면 Microsoft를 포함하여 모두가 한 시간 이내에 Power BI 내에서 사용자 콘텐츠를 읽을 수 없게 됩니다. BYOK 제품에 비해 CMK는 프리미엄 용량에서 호스트되는 보고서 및 데이터 세트로 가져오는 고객 데이터뿐만 아니라 서비스에서 생성되는 사용자 콘텐츠를 포함하며, 더욱 엄격한 캐싱 정책을 적용하고, 단일 키만 적용하여 모든 데이터를 암호화할 수 있습니다.


## <a name="how-to-use-customer-managed-keys"></a>고객 관리형 키를 사용하는 방법
Power BI 고객 관리형 키를 옵트인하려면 조직은 조직의 Microsoft 계정 관리자에게 문의하여 조직이 CMK 사용에 필요한 특정 크기 요구 사항을 충족하는지 확인해야 합니다.  


## <a name="next-steps"></a>다음 단계

다음 링크는 고객 관리형 키에 유용할 수 있는 정보를 제공합니다.

* [Power BI의 BYOK(Bring Your Own Encryption Key)](service-encryption-byok.md)
* [Power BI Premium에 대한 다중 지역 지원 구성](service-admin-premium-multi-geo.md)
* [용량 함수 작동 방법](service-premium-what-is.md#how-capacities-function)
* [증분 새로 고침](service-premium-incremental-refresh.md).
