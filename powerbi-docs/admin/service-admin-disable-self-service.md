---
title: 셀프 서비스 등록 및 구매 사용 또는 사용 안 함
description: 관리자가 Power BI 서비스에 등록하고 라이선스를 업그레이드할 수 있는 기능을 해제하는 방법에 대한 정보입니다.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 966699f20e83a7ea34140486f97f4491c4ba35e2
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90857453"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>셀프 서비스 등록 및 구매 사용 또는 사용 안 함

대부분의 조직에서 셀프 서비스 등록은 기본적으로 사용하도록 설정되어 있습니다. 조직의 개별 사용자는 회사 또는 학교 계정을 사용하여 Power BI에 등록할 수 있습니다. 사용자가 Pro를 요구하는 기능을 사용하려고 하는 경우 Power BI Pro 라이선스를 직접 구매하는 옵션이 제공될 수도 있습니다. 관리자는 셀프 서비스 등록을 사용하거나 사용하지 않도록 설정할지 여부를 결정합니다. 조직의 사용자가 본인의 라이선스를 얻기 위해 셀프 서비스 구매를 수행할 수 있는지 여부를 제어할 수도 있습니다.

> [!NOTE]
>Microsoft CSP(클라우드 솔루션 공급자)를 통해 Power BI를 확보한 경우 사용자가 개별적으로 등록하는 것을 차단하기 위해 설정을 사용하지 못할 수 있습니다. 또한 CSP는 조직의 전역 관리자 역할을 하므로 이 설정을 변경하는 데 도움을 요청해야 할 수도 있습니다.
>
>

PowerShell 명령을 사용하여 셀프 서비스 등록 및 구매를 제어하는 설정을 변경합니다. 조직의 사용자가 셀프 서비스 등록을 수행하거나 셀프 서비스를 구매할 수 있는지 여부를 제어하는 두 가지 설정이 있습니다.

- 모든 셀프 서비스 등록을 사용하지 않도록 설정하려면 Azure AD PowerShell 명령을 사용하여 **AllowAdHocSubscriptions**라는 Azure Active Directory의 설정을 변경합니다. 이 문서의 단계를 수행하여 [셀프 서비스 등록을 사용하거나 사용하지 않도록 합니다](#enable-or-disable-self-service-signup). 이 옵션은 *모든* Microsoft 클라우드 기반 앱 및 서비스에 대한 셀프 서비스 등록 기능을 해제합니다.

- 사용자가 자신의 Pro 라이선스를 구매하지 못하게 하려면 MSCommerce PowerShell 명령을 사용하여 **AllowSelfServicePurchase** 설정을 변경합니다. 이 설정을 사용하면 특정 제품에 대한 셀프 서비스 구매를 해제할 수 있습니다. 이 문서의 단계에 따라 [Power BI Pro 라이선스의 셀프 서비스 구매를 사용 하거나 사용하지 않도록 설정합니다](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>셀프 서비스 등록 사용 또는 사용 안 함

셀프 서비스 등록을 사용하도록 설정하면 **AllowAdHocSubscriptions**의 값이  *true*가 됩니다. 이 설정을 *false*로 변경하면 어떻게 되는지 살펴보겠습니다.

- 설정을 true에서 false로 변경하면 조직의 새 사용자 개별 등록이 차단됩니다. 설정 변경 이전에 Power BI를 등록한 사용자의 경우 등록한 라이선스가 유지됩니다.

- false로 설정을 변경해도 이미 Power BI(무료) 라이선스가 있는 사용자는 개인 Power BI Pro 평가판에 계속 등록할 수 있습니다.

- 관리자는 새 사용자에게 필요한 모든 Power BI 라이선스를 할당해야 합니다.

### <a name="before-you-begin"></a>시작하기 전에

이러한 단계에서는 Azure Active Directory PowerShell 명령을 사용하여 **AllowAdHocSubscriptions** 설정의 값을 변경합니다. 이러한 명령을 사용하려면 Azure AD PowerShell 모듈을 설치해야 합니다. PowerShell에 대한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7)을 참조하세요.

Azure AD 모듈을 설치하려면 관리자 권한으로 Windows PowerShell을 시작합니다. 로컬 실행 정책에서 스크립트를 실행할 수 있는지 확인합니다. 문제가 발생하는 경우 [PowerShell 실행 정책](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies)을 참조하여 로컬 정책을 변경하는 방법에 대해 알아보세요.

다음 명령을 실행하여 Azure AD 모듈을 설치합니다.

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>셀프 서비스 등록 정책 변경

PowerShell에서 다음 명령을 실행하여 Azure AD에 연결합니다.

```powershell
Connect-MsolService
```

로그인 대화 상자에서 관리자 자격 증명을 입력하여 필요할 수 있는 2단계 인증을 완료합니다. 확인 후 PowerShell 창으로 돌아갑니다.

현재 설정을 보려면 다음 명령을 실행합니다. 출력은 "fl" 스위치를 사용하여 서식이 지정된 목록으로 파이프됩니다.

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

현재 설정을 변경하려면 다음 명령을 실행합니다.

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

이 명령을 실행한 후에는 모든 사용자에 대해 셀프 서비스 등록을 사용할 수 없습니다. 다시 설정하려면 이 명령을 다시 실행하고 값을 $true로 설정합니다.

## <a name="enable-or-disable-self-service-purchase"></a>셀프 서비스 구매 사용 또는 사용 안 함

셀프 서비스 구매를 사용하는 경우 **AllowSelfServicePurchase**의 값이 *true*가 됩니다. 이 설정을 *false*로 변경하면 어떻게 되는지 살펴보겠습니다.

- 설정을 true에서 false로 변경하는 경우 조직의 사용자는 자신의 Power BI Pro 라이선스를 구입하지 못하도록 차단됩니다. 설정 변경 이전에 라이선스를 구매한 사용자의 경우 구매한 라이선스가 유지됩니다.

- 설정을 false로 변경하면 Power BI(무료) 라이선스가 있는 사용자는 개별 Power BI Pro 라이선스를 받을 수 없습니다. 

- 관리자는 Pro 라이선스를 필요로 하는 모든 사용자에게 할당해야 합니다.

### <a name="before-you-begin"></a>시작하기 전에

이러한 단계에서는 MSCommerce PowerShell 명령을 사용하여 **AllowSelfServicePurchase** 설정 값을 변경합니다. 이러한 명령을 사용하려면 MSCommerce PowerShell 모듈을 설치해야 합니다. PowerShell에 대한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7)을 참조하세요.

MSCommerce 모듈을 설치하려면 관리자 권한으로 Windows PowerShell을 시작합니다. 로컬 실행 정책에서 스크립트를 실행할 수 있는지 확인합니다. 문제가 발생하는 경우 [PowerShell 실행 정책](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies)을 참조하여 로컬 정책을 변경하는 방법에 대해 알아보세요.

다음 명령을 실행하여 MSCommerce 모듈을 설치합니다.

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>셀프 서비스 등록 정책 변경

PowerShell에서 다음 명령을 실행하여 연결합니다.

```powershell
Connect-MSCommerce
```

로그인 대화 상자에서 관리자 자격 증명을 입력하여 필요할 수 있는 2단계 인증을 완료합니다. 확인 후 PowerShell 창에 연결 성공이 표시됩니다.

현재 설정을 보려면 다음 명령을 실행합니다. 텍스트가 잘리는 것을 방지하기 위해 출력은 "fl" 스위치를 사용하여 서식이 지정된 목록으로 파이프됩니다.

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

**ProductId**를 제공하여 개별 제품에 대한 셀프 서비스 구매를 허용하는 설정을 사용하지 않도록 설정할 수 있습니다. Power BI 서비스에 대한 현재 설정을 변경하려면 다음 명령을 실행합니다.

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

이 명령을 실행한 후에는 모든 사용자에 대해 Power BI의 셀프 서비스 구매를 사용할 수 없습니다. 다시 설정하려면 이 명령을 다시 실행하고 값을 $true로 설정합니다.

## <a name="next-steps"></a>다음 단계

Power BI의 셀프 서비스 구매 및 나머지 Power Platform에 대한 자세한 내용은 다음 문서를 참조하세요.

- [셀프 서비스 구매 FAQ](/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [MSCommerce PowerShell 모듈에 AllowSelfServicePurchase 사용](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)