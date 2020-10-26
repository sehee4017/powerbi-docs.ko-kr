---
title: 서비스 주체 앱 만들기
description: 서비스 주체 앱 만들기
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 10/15/2020
ms.custom: include file
ms.openlocfilehash: 0f6c74ddc5a7decc8c1a6444568de44d3adbbc68
ms.sourcegitcommit: 8561902ef0ad63b0881187a22f25d1aa1ec3bcbc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92210789"
---
## <a name="step-2---create-an-azure-ad-security-group"></a>2단계 - Azure AD 보안 그룹 만들기

현재 서비스 주체에는 Power BI 콘텐츠 및 API에 대한 액세스 권한이 없습니다. 서비스 주체에 액세스 권한을 부여하려면 Azure AD에서 보안 그룹을 만들고 사용자가 만든 서비스 주체를 해당 보안 그룹에 추가합니다.

Azure AD 보안 그룹을 만드는 방법에는 두 가지가 있습니다.
* 수동으로(Azure에서)
* PowerShell 사용

### <a name="create-a-security-group-manually"></a>수동으로 보안 그룹 만들기

수동으로 Azure 보안 그룹을 만들려면 [Azure Active Directory를 사용하여 기본 그룹 만들기 및 멤버 추가](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) 문서에 있는 지침을 따르세요. 

### <a name="create-a-security-group-using-powershell"></a>PowerShell을 사용하여 보안 그룹 만들기

다음은 새 보안 그룹을 만들고 이 보안 그룹에 앱을 추가하는 샘플 스크립트입니다.

>[!NOTE]
>전체 조직에 대해 서비스 주체 액세스를 사용하도록 설정하려면 이 단계를 건너뜁니다.

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>3단계 - Power BI 서비스 관리자 설정 사용

Azure AD 앱이 Power BI 콘텐츠 및 API에 액세스할 수 있도록 Power BI 관리자는 Power BI 관리 포털에서 서비스 사용자 액세스를 사용하도록 설정해야 합니다.

Azure AD에서 만든 보안 그룹을 **개발자 설정** 의 특정 보안 그룹 섹션에 추가합니다.

>[!IMPORTANT]
>서비스 주체는 사용하도록 설정된 모든 테넌트 설정에 액세스할 수 있습니다. 관리자 설정에 따라 여기에는 특정 보안 그룹 또는 전체 구성이 포함됩니다.
>
>특정 테넌트 설정에 대한 서비스 주체 액세스를 제한하려면 특정 보안 그룹에만 액세스를 허용합니다. 또는 서비스 주체에 대한 전용 보안 그룹을 만들고 원하는 테넌트 설정에서 제외할 수 있습니다.

>[!div class="mx-imgBorder"]
>:::image type="content" source="../developer/embedded/media/embed-service-principal/admin-portal.png" alt-text="Power BI 포털의 관리 옵션에서 개발자 설정을 보여주는 스크린샷.":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>4단계 - 작업 영역에 서비스 주체 추가

Azure AD 앱이 Power BI 서비스의 보고서, 대시보드, 데이터 세트와 같은 아티팩트에 액세스할 수 있도록 하려면 서비스 주체 엔터티를 작업 영역에 멤버 또는 관리자로 추가합니다.

>[!NOTE]
>이 섹션에서는 UI 지침을 제공합니다. [그룹 - 그룹 사용자 추가 API](/rest/api/power-bi/groups/addgroupuser)를 사용하여 작업 영역에 서비스 주체를 추가할 수도 있습니다.

1. 액세스를 사용하도록 설정할 작업 영역으로 스크롤한 다음 **자세히** 메뉴에서 **작업 영역 액세스** 를 선택합니다.

    :::image type="content" source="../developer/embedded/media/embed-service-principal/workspace-access.png" alt-text="Power BI 포털의 관리 옵션에서 개발자 설정을 보여주는 스크린샷.":::

2. 서비스 주체를 **관리자** 또는 **멤버** 로 작업 영역에 추가합니다.

    :::image type="content" source="../developer/embedded/media/embed-service-principal/add-service-principal-in-the-UI.png" alt-text="Power BI 포털의 관리 옵션에서 개발자 설정을 보여주는 스크린샷.":::