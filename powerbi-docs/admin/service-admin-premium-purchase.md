---
title: Power BI 프리미엄 구매 방법
description: Power BI Premium을 구매하고 전체 조직에 대한 콘텐츠에 대한 액세스를 활성화할 수 있는 방법을 알아봅니다.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 2250a93d5fc061ff1e9d67217d021686935a8db7
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512726"
---
# <a name="how-to-purchase-power-bi-premium"></a>Power BI 프리미엄 구매 방법

이 문서에서는 조직에 대한 Power BI 프리미엄 용량을 구입하는 방법을 설명합니다. 이 문서에서는 다음 시나리오를 다룹니다.

- 일반적인 프로덕션 시나리오에 P SKU 사용. P SKU는 월간 또는 연간 약정이 필요하며 매달 요금이 청구됩니다.

Power BI Premium에 대한 자세한 내용은 [Power BI Premium이란?](service-premium-what-is.md)을 참조하세요. 최신 가격 책정 및 계획 정보는 [Power BI 가격 책정 페이지](https://powerbi.microsoft.com/pricing/) 및 [Power BI Premium 계산기](https://powerbi.microsoft.com/calculator/)를 참조하세요. 조직에서 Power BI Premium을 사용하더라도 콘텐츠 작성자는 여전히 [Power BI Pro 라이선스](service-admin-purchasing-power-bi-pro.md)가 필요합니다. 조직을 위한 Power BI Pro 라이선스를 하나 이상 구입하세요. A SKU를 사용하는 경우 콘텐츠를 사용하는 ‘모든 사용자’도 Pro 라이선스가 필요합니다.

> [!NOTE]
> Premium 구독이 만료되면 30일 동안 용량에 대한 전체 액세스 권한을 가집니다. 그 후에는 콘텐츠가 공유 용량으로 전환됩니다. 1GB보다 큰 모델은 공유 용량에서 지원되지 않습니다.

> [!NOTE]
> Power BI Premium은 최근 **Premium Gen2** 라는 새 버전의 Premium을 출시했으며, 이 버전은 현재 미리 보기로 제공됩니다. Premium Gen2는 프리미엄 용량 관리를 간소화하고 관리 오버헤드를 줄입니다. 자세한 내용은 [Power BI Premium 2세대(미리 보기)](service-premium-what-is.md#power-bi-premium-generation-2-preview)를 참조하세요.

## <a name="purchase-p-skus-for-typical-production-scenarios"></a>일반적인 프로덕션 시나리오를 위해 P SKU 구매

Power BI Premium P1 SKU가 구성된 새 테넌트를 만들거나, 기존 조직을 위해 Power BI Premium 용량을 구매할 수 있습니다. 두 경우 모두, 필요에 따라 용량을 추가할 수 있습니다.

### <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Power BI 프리미엄 P1로 새 테넌트 만들기

기존 테넌트가 없어 새로 하나를 만들려면 Power BI 프리미엄도 동시에 구매할 수 있습니다. 다음 링크를 통해 새 테넌트를 만드는 과정을 안내받고 Power BI Premium([Power BI Premium P1 솔루션](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1))을 구입할 수 있습니다. 테넌트를 만들면 자동으로 해당 테넌트의 Microsoft 365 전역 관리자 역할에 할당됩니다.

용량을 구매한 후 [용량을 관리](service-admin-premium-manage.md#manage-capacity)하고 용량에 [작업 영역을 할당](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity)하는 방법을 알아봅니다.

### <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>기존 조직에 대한 Power BI 프리미엄 용량 구매

기존 조직(테넌트)이 있는 경우 Microsoft 365 전역 관리자 역할 또는 대금 청구 관리자 역할에 할당되어아야 구독 및 라이선스를 구매할 수 있습니다. 자세한 내용은 [Microsoft 365 관리자 역할 정보](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)를 참조하세요.

프리미엄 용량을 구매하려면 다음 단계를 따르세요.

1. Power BI 서비스 내에서 Microsoft 365 앱 선택기, **관리자** 를 차례로 선택합니다.

    ![Microsoft 365 앱 선택기](media/service-admin-premium-purchase/o365-app-picker.png)

    또는 Microsoft 365 관리 센터로 이동할 수 있습니다.

1. **청구** > **서비스 구입** 을 선택합니다.

1. **기타 계획** 아래에서 Power BI 프리미엄 제안을 찾습니다. P1~P3, EM3 및 P1(매월)로 나열됩니다.

1. 줄임표( **...** )를 마우스로 가리키고 **지금 구매** 를 선택합니다.

    ![지금 구입](media/service-admin-premium-purchase/premium-purchase.png)

1. 단계에 따라 구매를 완료합니다.

구매를 완료하면 **서비스 구입** 페이지에 항목을 구매했고 활성 상태인 것으로 표시됩니다.

![구매한 Power BI 프리미엄](media/service-admin-premium-purchase/premium-purchased.png)

용량을 구매한 후 [용량을 관리](service-admin-premium-manage.md#manage-capacity)하고 용량에 [작업 영역을 할당](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity)하는 방법을 알아봅니다.

### <a name="purchase-additional-capacities"></a>추가 용량 구매

이제 용량을 구매했으므로 요구 사항 증가에 따라 더 많은 용량을 추가할 수 있습니다. 또한 조직 내에서 프리미엄 용량 SKU(P1~P3)의 임의 조합을 사용할 수 있습니다. SKU마다 다양한 리소스 기능을 제공합니다.

1. Microsoft 365 관리 센터에서 **청구** > **서비스 구매** 를 선택합니다.

1. **기타 계획** 아래에서 추가로 구매할 Power BI 프리미엄 항목을 찾습니다.

1. **추가 옵션**(...)을 마우스로 가리키고 **라이선스 수량 변경** 을 선택합니다.

    ![라이선스 수량 변경](media/service-admin-premium-purchase/premium-purchase-more.png)

1. 이 항목에 대해 포함할 인스턴스 수를 변경합니다. 그런 다음 완료했으면 **제출** 을 선택합니다.

   > [!IMPORTANT]
   > **제출** 을 선택하면 등록된 신용 카드에 요금이 부과됩니다.

**서비스 구매** 페이지에 보유하고 있는 인스턴스 수가 표시됩니다. Power BI 관리 포털 내의 **용량 설정** 아래에서 사용 가능한 V 코어는 구매한 새 용량을 반영합니다.

![Power BI Premium 용량에 대한 사용 가능한 V 코어](media/service-admin-premium-purchase/premium-capacities.png)

### <a name="cancel-your-subscription"></a>구독 취소

Microsoft 365 관리 센터 내에서 구독을 취소할 수 있습니다. 프리미엄 구독을 취소하려면 다음을 수행합니다.

1. Microsoft 365 관리 센터로 이동합니다.

1. **청구** > **구독** 을 선택합니다.

1. 목록에서 Power BI 프리미엄 구독을 선택합니다.

1. **추가 작업** > **구독 취소** 를 선택합니다.

1. **구독 취소** 페이지는 [조기 종료 요금](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3)에 대한 책임 여부를 나타냅니다. 이 페이지는 구독에 대한 데이터가 삭제될 때도 이를 알려줍니다.

1. 정보를 자세히 읽고 계속하려면 **구독 취소** 를 선택합니다.

#### <a name="when-canceling-or-your-license-expires"></a>구독을 취소하거나 라이선스가 만료되는 경우

프리미엄 구독을 취소하거나 용량 라이선스가 만료되는 경우 구독 취소 또는 라이선스 만료 날짜로부터 30일 동안 프리미엄 용량에 계속 액세스할 수 있습니다. 30일 후에는 프리미엄 용량 또는 해당 작업 영역에 더 이상 액세스할 수 없습니다.

## <a name="purchase-a-skus-for-testing-and-other-scenarios"></a>테스트 및 기타 시나리오를 위해 A SKU 구매

테스트 및 기타 시나리오에 대해 A SKU를 구매할 수 있으며, 이 경우 시간 단위로 프리미엄 용량이 제공됩니다. 자세한 내용 및 단계는 [테스트용 Power BI Premium 구매](service-admin-premium-testing.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

[Power BI Premium에서 용량 구성 및 관리](service-admin-premium-manage.md)\
[Power BI 가격 책정 페이지](https://powerbi.microsoft.com/pricing/)\
[Power BI Premium 계산기](https://powerbi.microsoft.com/calculator/)\
[Power BI Premium FAQ](service-premium-faq.md)\
[Power BI 엔터프라이즈 배포 계획 백서](https://aka.ms/pbienterprisedeploy)

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)

Power BI는 Power BI Premium Gen2를 미리 보기 버전으로 소개했습니다. 이 버전은 다음과 같은 향상된 기능을 통해 Power BI Premium 환경을 개선합니다.
* 성능
* 사용자 단위 라이선싱
* 더 큰 규모
* 개선된 메트릭
* 자동 확장
* 관리 오버헤드 감소

Power BI Premium Gen2에 대한 자세한 내용은 [Power BI Premium 2세대(미리 보기)](service-premium-what-is.md#power-bi-premium-generation-2-preview)를 참조하세요.