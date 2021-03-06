---
title: 조직의 사용자에 대한 Power BI 라이선스 부여
description: Power BI에서 사용 가능한 다양한 사용자 라이선스 유형과 관리자가 조직의 사용자에 대한 라이선스를 구매하고 관리하는 방법을 간략하게 설명합니다.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/11/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 00c375267ceaede23b317fb71d76e31e4ae66a83
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408645"
---
# <a name="licensing-the-power-bi-service-for-users-in-your-organization"></a>조직의 사용자에 대한 Power BI 서비스 라이선스 부여

사용자가 Power BI 서비스에서 수행할 수 있는 작업은 보유한 사용자별 라이선스 유형에 따라 달라집니다. 라이선스에서 제공하는 액세스 수준은 작업 영역에서 Premium 작업 영역에 액세스하는지 여부에 따라 달라집니다. Power BI 서비스의 모든 사용자에게 라이선스가 있어야 합니다.

사용자는 두 가지 방법으로 라이선스를 받을 수 있습니다. 사용자는 셀프 서비스 등록 기능 및 회사 또는 학교 계정을 사용하여 무료 라이선스나 Pro 또는 사용자 단위 Premium 라이선스를 받을 수 있습니다. 또는 관리자가 Power BI 라이선스를 가져오고 사용자에게 라이선스를 할당할 수 있습니다.

이 문서에서는 관리자 관점에서 구매 서비스 및 사용자별 라이선싱에 대해 집중적으로 살펴봅니다. 사용자가 자신의 라이선스를 얻을 수 있는 방법에 대한 자세한 내용은 [Power BI에 개별 등록](../fundamentals/service-self-service-signup-for-power-bi.md)을 참조하세요.

## <a name="who-can-purchase-and-assign-licenses"></a>라이선스는 누가 구매하고 할당할 수 있나요?

조직의 라이선스를 구매하거나 할당하려면 관리자 역할이 할당되어야 합니다. 관리자 역할은 Azure Active Directory 관리 센터 또는 Microsoft 365 관리 센터를 사용하여 할당됩니다. 다음 표에서는 구매 및 라이선싱과 관련된 작업을 수행하는 데 필요한 역할을 보여 줍니다. Azure Active Directory의 관리자 역할 할당에 대한 자세한 내용은 [Azure Active Directory에서 관리자 역할 보기 및 할당](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)을 참조하세요. 모범 사례를 포함하여 Microsoft 365의 관리자 역할에 대한 자세한 내용은 [관리자 역할 정보](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide)를 참조하세요.

| 서비스 및 라이선스는 누가 구매할 수 있나요? | 사용자 라이선스는 누가 관리할 수 있나요? |
| --------------- | --------------- |
| 청구 관리자 | 라이선스 관리자 |
| 글로벌 관리자 | 사용자 관리자 |
|  | 글로벌 관리자 |

이러한 역할은 조직을 관리합니다. Power BI 서비스 관리자 역할에 대한 자세한 내용은 [Power BI 서비스 관리자 역할 이해](service-admin-role.md)를 참조하세요.

## <a name="get-power-bi-for-your-organization"></a>조직용 Power BI를 사용해 보세요.

가격 책정에 대한 자세한 내용은 [가격 책정 및 제품 비교](https://powerbi.microsoft.com/pricing/)를 참조하세요.

전역 관리자 또는 청구 관리자는 조직의 사용자에 대한 Power BI 서비스를 등록하고 라이선스를 구입할 수 있습니다. 구매할 준비가 되지 않은 경우 Power BI Pro 평가판을 선택합니다. 한 달에 사용할 25개의 라이선스를 받게 됩니다. 등록하는 방법에 대한 단계별 지침은 [조직의 Power BI 구독 가져오기](service-admin-org-subscription.md)를 참조하세요.

## <a name="about-self-service-sign-up"></a>셀프 서비스 등록 정보

개별 사용자는 회사 또는 학교 계정으로 등록하여 자신의 Power BI 라이선스를 받을 수 있습니다. 사용자는 체험용 라이선스를 사용하여 내 작업 영역을 사용하는 개인 데이터 분석 및 시각화에 대한 Power BI를 탐색할 수 있지만 다른 사용자와 공유할 수 없습니다. 콘텐츠를 공유하려면 Power BI Pro 라이선스가 필요합니다. Power BI Premium 라이선스는 Premium을 통해서만 사용할 수 있는 다양한 기능 및 콘텐츠 유형에 대한 액세스를 잠금 해제합니다. 사용자 단위 Premium 라이선스는 이러한 기능에 대한 액세스를 사용자 단위 Premium 라이선스가 있는 다른 사용자로만 제한합니다. 용량 기반 Premium 라이선스는 무료 라이선스가 있는 사용자가 콘텐츠에 액세스하도록 허용하는 반면, Pro 라이선스가 있는 사용자만 콘텐츠를 만들 수 있습니다. 조직에서 상용 클라우드를 사용하는 경우 사용자는 라이선스 유형을 Pro로 업그레이드하거나 Pro에 직접 등록할 수 있습니다. Azure Government, Azure 독일 또는 Azure 중국 21Vianet 클라우드 인스턴스에 배포된 교육 조직이나 조직에서는 Pro를 직접 구매하거나 Pro로 업그레이드할 수 없습니다.

조직의 사용자가 셀프 서비스 등록을 사용하지 못하게 하려면 [셀프 서비스 등록 사용 또는 사용 안 함](service-admin-disable-self-service.md)을 참조하여 사용하지 않도록 설정하는 방법을 알아보세요.

셀프 서비스 등록 기능을 해제하면 사용자는 데이터 시각화 및 분석을 위해 Power BI를 탐색할 수 없습니다. 개별 등록을 차단하는 경우 조직의 Power BI (무료) 라이선스를 얻어 모든 사용자에게 할당하는 것이 좋습니다. 모든 기존 사용자에게 Power BI (무료) 라이선스를 자동으로 할당하려면 다음 단계를 따르세요.

1. 전역 관리자 또는 청구 관리자 자격 증명을 사용하여 [Microsoft 365 관리 센터](https://admin.microsoft.com)에 로그인합니다.
1. 왼쪽 사이드바 메뉴에서 **청구** > **서비스 구입** 을 선택합니다.
1. 검색하거나 스크롤하여 Power BI (무료) 제품을 찾습니다. 제품을 선택한 다음 **지금 가져오기** 를 선택합니다.
1. 모든 사용자를 포함하는 데 필요한 라이선스 수를 입력합니다.
1. **라이선스가 없는 모든 사용자에게 자동으로 할당** 을 선택하고 체크 아웃합니다.

  ![셀프 서비스 가입을 보여 주는 Power BI 무료 자동 할당 구독의 스크린샷.](media/service-admin-licensing-organization/m365-auto-assign.png)

조직에서 이미 라이선스가 있는 사용자를 확인하려면 [사용자 라이선스 보기 및 관리](service-admin-manage-licenses.md)를 참조하여 방법을 알아보세요.

## <a name="license-types-and-capabilities"></a>라이선스 유형 및 기능

Power BI 사용자 단위 라이선스에는 무료 Pro 및 Premium의 두 가지 종류가 있습니다. 사용자에게 필요한 라이선스 유형은 콘텐츠가 저장되는 위치, 해당 콘텐츠와 상호 작용하는 방법, 그리고 해당 콘텐츠가 Premium 기능을 사용하는지 여부에 따라 결정됩니다. 콘텐츠를 저장할 수 있는 위치는 조직의 [라이선스 유형](#license-types)에 따라 결정됩니다.

라이선스의 한 유형인 [Power BI Premium](service-admin-premium-purchase.md) 용량 기반 라이선스를 통해 무료 라이선스 사용자는 프리미엄 용량에 할당된 작업 영역의 콘텐츠에 대해 작업을 수행할 수 있습니다. 체험용 라이선스를 가진 사용자는 프리미엄 용량 외에 Power BI 서비스를 사용하여 데이터에 연결하고 **내 작업 영역** 에서 보고서 및 대시보드를 만들기만 할 수 있습니다. 다른 사용자와 콘텐츠를 공유하거나 다른 작업 영역에 콘텐츠를 게시할 수 없습니다. 작업 영역 유형에 대한 자세한 내용은 [작업 영역 유형](../consumer/end-user-workspaces.md#types-of-workspaces)을 참조하세요.

무료 및 Pro 사용자 단위 라이선스의 Power BI 라이선스는 제한된 공유 용량만을 사용하여 콘텐츠를 처리합니다. 콘텐츠가 공유 용량에 저장되는 경우 Power BI Pro 라이선스를 할당받은 사용자는 다른 Power BI Pro 사용자와만 협업할 수 있습니다. 다른 사용자가 공유한 콘텐츠를 사용하고, 앱 작업 영역에 콘텐츠를 게시하고, 대시보드를 공유하며, 대시보드 및 보고서를 구독할 수 있습니다.  작업 영역이 프리미엄 용량에 있는 경우 Pro 사용자는 Power BI Pro 라이선스가 없는 사용자에게 콘텐츠를 배포할 수 있습니다.

사용자 단위 Premium 라이선스를 사용하는 경우 사용자 단위 Premium 라이선스 사용자가 만든 콘텐츠는 프리미엄 용량에서 호스트되는 작업 영역에 특별히 배치되지 않는 한 다른 Premium 라이선스 사용자와만 공유할 수 있습니다. 아래 표에는 각 라이선스 유형의 기본 기능이 요약되어 있습니다. 라이선스 유형별 기능 가용성에 대한 자세한 내용은 [라이선스 유형별 기능](../fundamentals/service-features-license-type.md)을 참조하세요.

| 라이선스 유형 | 작업 영역이 공유 용량에 있는 경우의 기능 | 작업 영역이 프리미엄 용량에 있는 경우의 추가 기능 |
| --------- | ----------- | ----------- |
| Power BI(무료) | 내 작업 영역의 콘텐츠에 액세스 | 공유한 콘텐츠 사용 |
| Power BI Pro | 다른 작업 영역에 콘텐츠를 게시하고, 대시보드를 공유하며, 대시보드 및 보고서를 구독하고, Pro 라이선스가 있는 사용자와 공유합니다. | 무료 라이선스를 보유한 사용자에게 콘텐츠 배포 |

## <a name="license-types"></a>라이선스 유형

Microsoft의 모든 사용자 기반 상용 라이선스는 Azure Active Directory ID를 기반으로 합니다. Power BI 서비스를 사용하려면 Azure Active Directory에서 상용 라이선스를 지원하는 ID로 로그인해야 합니다. ID 서비스로 Azure Active Directory를 사용하는 모든 Microsoft 라이선스에 Power BI를 추가할 수 있습니다. Office 365 E5와 같은 일부 라이선스는 Power BI Pro 라이선스를 포함하므로 Power BI의 별도 등록이 필요하지 않습니다.

조직에서는 표준 및 프리미엄의 두 가지 Power BI 라이선스를 사용할 수 있습니다.

관리자는 표준 셀프 서비스 Power BI Pro 라이선스를 사용하여 사용자 단위 라이선스를 할당합니다. Power BI Pro 라이선스에는 사용자당 월 요금이 부과됩니다. 이 라이선스 유형을 사용하면 협업, 게시, 공유 및 임시 분석을 수행할 수 있습니다. 콘텐츠는 Microsoft 완전 관리형 공유 스토리지 용량에 저장됩니다.

Power BI Premium 라이선스는 조직에 용량을 할당합니다. 엔터프라이즈 BI, 빅 데이터 분석, 클라우드 및 온-프레미스 보고에 적합한 Premium은 고급 관리 및 배포 제어를 제공합니다. 전용 컴퓨팅 및 스토리지 리소스는 조직의 용량 관리자가 관리합니다. 이 전용 환경에 대해 월별 비용이 발생합니다. 프리미엄 용량에 저장된 콘텐츠는 기타 Premium 장점 외에도 Power BI Pro 라이선스가 없는 사용자가 액세스할 수 있으며 Power BI Pro 라이선스가 없는 사용자에게 배포할 수 있습니다. Premium을 사용하려면 하나 이상의 사용자에게 Power BI Pro 라이선스가 할당되어야 하며, 콘텐츠 작성자 및 개발자에게는 여전히 Power BI Pro 라이선스가 필요합니다.

표준 라이선스와 프리미엄 라이선스는 함께 사용할 수 있습니다. Power BI Premium과 Power BI Pro를 모두 사용할 수 있습니다. 이 구성에서는 프리미엄 용량에 저장된 콘텐츠를 모든 사용자와 공유할 수 있으며 공유 용량도 사용할 수 있습니다. 용량 한도에 대한 자세한 내용은 [Power BI 작업 영역에서 데이터 스토리지 관리](service-admin-manage-your-data-storage-in-power-bi.md)를 참조하세요.

제품 기능 및 가격 책정을 비교하려면 [Power BI 가격 책정](https://powerbi.microsoft.com/pricing)을 참조하세요.

## <a name="guest-user-access"></a>게스트 사용자 액세스

조직 외부에 있는 사용자에게 콘텐츠를 배포하려고 할 수 있습니다. 콘텐츠를 게스트로 보도록 초대하여 외부 사용자와 콘텐츠를 공유할 수 있습니다. Azure AD B2B(Azure Active Directory Business-to-Business)를 통해 외부 게스트 사용자와 공유할 수 있습니다. 외부 사용자와 공유하려면 다음 필수 구성 요소를 충족해야 합니다.

- 외부 사용자와 콘텐츠를 공유하는 기능을 사용하도록 설정해야 합니다.

- 게스트 사용자가 공유된 콘텐츠를 보려면 적합한 라이선싱이 있어야 합니다.

게스트 사용자 액세스에 대한 자세한 내용은 [Azure AD B2B에서 외부 게스트 사용자에게 Power BI 콘텐츠 배포](service-admin-azure-ad-b2b.md)를 참조하세요.

## <a name="purchase-power-bi-pro-licenses"></a>Power BI Pro 라이선스 구매

관리자는 Microsoft 365 또는 Microsoft 파트너를 통해 Power BI Pro 라이선스를 구매합니다. 라이선스를 구입한 후에는 개별 사용자에게 할당합니다. 자세한 내용은 [Power BI Pro 라이선스 구매 및 할당](service-admin-purchasing-power-bi-pro.md)을 참조하세요.

### <a name="power-bi-pro-license-expiration"></a>Power BI Pro 라이선스 만료

Power BI Pro 라이선스가 만료된 후 유예 기간이 있습니다. 볼륨 라이선스 구입에 포함된 라이선스의 경우 유예 기간은 90일입니다. 라이선스를 직접 구입한 경우 유예 기간은 30일입니다.

Power BI Pro는 Microsoft 365와 라이선스 수명 주기가 동일합니다. 자세한 내용은 [비즈니스용 Microsoft 365 구독이 종료되면 내 데이터 및 액세스 권한은 어떻게 되나요?](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires)를 참조하세요.


## <a name="next-steps"></a>다음 단계

- [Power BI Pro 라이선스 구매 및 할당](service-admin-purchasing-power-bi-pro.md)
- [비즈니스 구독 및 청구 설명서](/microsoft-365/commerce/?view=o365-worldwide)
- [로그인한 Power BI 사용자 찾기](service-admin-access-usage.md)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)


Power BI는 Power BI Premium Gen2를 미리 보기 버전으로 소개했습니다. 이 버전은 다음과 같은 향상된 기능을 통해 Power BI Premium 환경을 개선합니다.
* 성능
* 사용자 단위 라이선싱
* 더 큰 규모
* 개선된 메트릭
* 자동 확장
* 관리 오버헤드 감소

Power BI Premium Gen2에 대한 자세한 내용은 [Power BI Premium 2세대(미리 보기)](service-premium-what-is.md#power-bi-premium-generation-2-preview)를 참조하세요.