---
title: Azure AD B2B에서 외부 게스트 사용자에게 콘텐츠 배포
description: Power BI에서는 Azure AD B2B(Azure Active Directory Business-to-Business)를 통해 외부 게스트 사용자와 콘텐츠를 공유할 수 있습니다.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 2bb54bf7340e89b86bfbfd56390b79a7051dd709
ms.sourcegitcommit: 2cb249fc855e369eed1518924fbf026d5ee07eb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83812281"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Azure AD B2B에서 외부 게스트 사용자에게 Power BI 콘텐츠 배포

Power BI에서는 Azure AD B2B(Azure Active Directory Business-to-Business)를 통해 외부 게스트 사용자와 콘텐츠를 공유할 수 있습니다.
Azure AD B2B 사용을 통해 조직은 특정 위치에서 외부 사용자와 공유를 사용하도록 설정하고 관리합니다. 기본적으로 외부 게스트는 소비 전용 환경을 사용합니다. 또한 조직의 외부 게스트 사용자가 조직의 콘텐츠를 편집하고 관리할 수 있도록 허용할 수 있습니다.

이 문서에서는 Power BI의 Azure AD B2B 기본 사항을 소개합니다. 자세한 내용은 [Azure Active Directory B2B를 사용하여 외부 게스트 사용자에게 Power BI 콘텐츠 배포](../guidance/whitepaper-azure-b2b-power-bi.md)를 참조하세요.

## <a name="enable-access"></a>액세스 사용

게스트 사용자를 초대하기 전에 Power BI 관리 포털에서 [외부 사용자와 콘텐츠 공유](service-admin-portal.md#export-and-sharing-settings) 기능을 사용하도록 설정합니다. 이 옵션을 사용하는 경우에도 사용자는 게스트 사용자를 초대하기 위해 Azure Active Directory에 권한이 있어야 하며, 이 권한은 게스트 초대자 역할을 통해 부여됩니다. 

[외부 게스트 사용자가 조직의 콘텐츠를 편집 및 관리하도록 허용](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) 옵션을 사용하면 조직의 Power BI 탐색을 포함하여 작업 영역에 있는 콘텐츠를 보고 만드는 기능을 게스트 사용자에게 제공할 수 있습니다.

> [!NOTE]
> [외부 사용자와 콘텐츠 공유](service-admin-portal.md#export-and-sharing-settings) 설정은 Power BI를 통해 외부 사용자를 조직에 초대할 수 있는지를 제어합니다. 외부 사용자가 초대를 수락하면 조직에서 Azure AD B2B 게스트 사용자가 됩니다. 이러한 사용자는 Power BI 환경 전반에서 사용자 선택기에 표시됩니다. 이 설정을 해제할 경우 조직의 기존 게스트 사용자는 액세스 권한이 있는 모든 항목에 계속 액세스할 수 있으며, 계속해서 사용자 선택기에 나열됩니다. 또한 [계획 초대](#planned-invites) 방법을 통해 게스트를 추가하는 경우 해당 게스트가 사용자 선택기에도 표시됩니다. 게스트 사용자가 Power BI에 액세스하지 못하게 하려면 Azure AD 조건부 액세스 정책을 사용합니다.

## <a name="who-can-you-invite"></a>누구를 초대할 수 있나요?

개인 계정(예: gmail.com, outlook.com 및 hotmail.com)을 포함한 대부분의 메일 주소를 가진 게스트 사용자를 조직에 초대할 수 있습니다. Azure AD B2B에서는 이러한 주소를 *소셜 ID*라고 합니다.

[미국 정부용 Power BI](service-govus-overview.md)와 같이 정부 클라우드와 관련된 사용자를 초대할 수 없습니다.

## <a name="invite-guest-users"></a>게스트 사용자 초대

게스트 사용자를 조직에 최초로 초대할 때만 초대가 필요합니다. 사용자를 초대하려면 계획 또는 임시 초대를 사용합니다.

임시 초대를 사용하려면 다음 기능을 사용합니다.
* 보고서 및 대시보드 공유
* 앱 액세스 목록

임시 초대는 작업 영역 액세스 목록에서 지원되지 않습니다. [계획 초대 방법](#planned-invites)을 사용하여 해당 사용자를 조직에 추가합니다. 외부 사용자가 조직의 게스트가 된 후 해당 사용자를 작업 영역 액세스 목록에 추가합니다.

### <a name="planned-invites"></a>계획 초대

초대할 사용자를 알고 있는 경우 계획 초대를 사용합니다. Azure Portal 또는 PowerShell을 사용하여 초대를 보낼 수 있습니다. 사람을 초대하려면 테넌트 관리자여야 합니다.

Azure Portal에서 초대를 보내려면 다음 단계를 수행합니다.

1. [Azure Portal](https://portal.azure.com)에서 **Azure Active Directory**를 선택합니다.

1. **관리** 아래에서 **사용자** > **모든 사용자** > **새 게스트 사용자**를 선택합니다.

    ![새 게스트 사용자 옵션이 표시된 Azure Portal의 스크린샷.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. **메일 주소** 및 **개인 메시지**를 입력합니다.

    ![Azure AD Portal 새 게스트 사용자 대화 상자의 스크린샷.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. **초대**를 선택합니다.

여러 명의 게스트 사용자를 초대하려면 PowerShell을 사용합니다. 자세한 내용은 [Azure AD B2B 협업 코드 및 PowerShell 샘플](/azure/active-directory/b2b/code-samples/)을 참조하세요.

게스트 사용자는 받은 이메일 초대에서 **시작**을 선택해야 합니다. 그러면 게스트 사용자가 테넌트에 추가됩니다.

![게스트 사용자 메일 초대 스크린샷.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>임시 초대

언제든지 외부 사용자를 초대하려면 외부 사용자를 대시보드에 추가하거나 공유 UI를 통해 보고하거나 액세스 페이지를 통해 앱을 보고합니다. 다음은 앱을 사용할 외부 사용자를 초대할 때 수행할 작업의 예입니다.

![Power BI의 앱 액세스 목록에 추가된 외부 사용자 스크린샷.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

게스트 사용자는 앱이 자신과 공유되었음을 안내하는 메일을 받게 됩니다.

![게스트 사용자와 공유된 앱을 안내하는 메일 스크린샷](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

게스트 사용자가 해당 조직 이메일 주소로 로그인해야 합니다. 로그인 후 초대를 수락하라는 메시지가 표시됩니다. 로그인한 후 게스트 사용자를 위해 앱이 열립니다. 앱으로 돌아가려면 링크를 책갈피로 표시하거나, 메일을 저장해야 합니다.


## <a name="licensing"></a>라이선싱

게스트 사용자가 공유된 콘텐츠를 보려면 적합한 라이선싱이 있어야 합니다. 사용자에게 적합한 라이선싱이 있도록 하는 방법에는 Power BI Premium 사용, Power BI Pro 라이선스 할당, 게스트의 Power BI Pro 라이선스 사용 등 세 가지가 있습니다.

[조직에서 콘텐츠를 편집하고 관리할 수 있는 게스트 사용자](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)는 작업 영역에 콘텐츠를 제공하거나 다른 사람들과 콘텐츠를 공유하려면 Power BI Pro 라이선스가 필요합니다.

### <a name="use-power-bi-premium"></a>Power BI Premium 사용

작업 영역을 [Power BI Premium 용량](service-premium-what-is.md)에 할당하면 게스트 사용자가 Power BI Pro 라이선스 없이도 앱을 사용할 수 있습니다. Power BI Premium에서는 앱이 새로 고침 비율 증대, 전용 용량, 대규모 모델 크기 등과 같은 다른 기능도 활용할 수 있습니다.

![Power BI Premium을 사용한 경우 게스트 사용자 환경 다이어그램.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>게스트 사용자에게 Power BI Pro 라이선스 할당

테넌트 내의 게스트 사용자에게 Power BI Pro 라이선스를 할당하면 게스트 사용자가 테넌트의 콘텐츠를 볼 수 있습니다. 라이선스 할당 방법에 대한 자세한 내용은 [라이선스 페이지에서 사용자에게 라이선스 할당](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page)을 참조하세요. 게스트 사용자에게 Pro 라이선스를 할당하기 전에 Microsoft 계정 담당자에게 문의하여 Microsoft 계약 조건을 준수하고 있는지 확인합니다.

![테넌트에서 Pro 라이선스를 할당한 경우 게스트 사용자 환경 다이어그램.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>게스트 사용자가 자신의 Power BI Pro 라이선스 사용

게스트 사용자에게 이미 테넌트 안에 할당된 Power BI Pro 라이선스가 있습니다.

![게스트 사용자 라이선스를 사용한 경우 게스트 사용자 환경 다이어그램.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>콘텐츠를 편집하고 관리할 수 있는 게스트 사용자

[외부 게스트 사용자가 조직의 콘텐츠를 편집 및 관리하도록 허용](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) 기능을 사용하는 경우, 지정된 게스트 사용자는 조직의 Power BI에 대한 추가 액세스 권한을 얻습니다. 허용된 게스트는 권한이 있는 콘텐츠를 보고, 홈에 액세스하고, 작업 영역을 찾아보며, 앱을 설치하고, 액세스 목록에서 앱이 어디에 있는지 살펴보거나 작업 영역에 콘텐츠를 제공할 수 있습니다. 또 새로운 작업 영역 환경을 사용하는 작업 영역의 관리자를 만들거나 관리자가 될 수 있습니다. 몇 가지 제한 사항이 적용됩니다. 고려 사항 및 제한 사항 섹션 목록에는 이러한 제한 사항을 확인할 수 있습니다.
 
허용된 게스트가 Power BI에 로그인할 수 있도록 지원하려면 테넌트 URL을 제공하세요. 테넌트 URL을 찾으려면 이 단계를 수행합니다.

1. Power BI 서비스의 맨 위 메뉴에서 도움말( **?** )을 선택한 후 **Power BI 정보**를 선택합니다.

2. **테넌트 URL** 옆에 있는 값을 찾습니다. 허용된 게스트 사용자와 테넌트 URL을 공유합니다.

    ![게스트 사용자 테넌트 URL이 표시된 Power BI 정보 대화 상자 스크린샷.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항

* 기본적으로 외부 Azure AD B2B에서는 게스트 권한이 콘텐츠 소비로만 제한됩니다. 외부 Azure AD B2B 게스트는 앱, 대시보드, 보고서를 보고, 데이터를 내보내며, 대시보드 및 보고서에 대한 전자 메일 구독을 만들 수 있습니다. 작업 영역에 액세스하거나 자신의 콘텐츠를 게시할 수는 없습니다. 제한 사항을 제거하려면 [외부 게스트 사용자가 조직의 콘텐츠를 편집 및 관리하도록 허용](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) 기능을 사용할 수 있습니다.

* 게스트 사용자를 초대하려면 Power BI Pro 라이선스가 필요합니다. Pro 평가판 사용자는 Power BI에서 게스트 사용자를 초대할 수 없습니다.

* 일부 환경은 [조직에서 콘텐츠를 편집하고 관리할 수 있는 게스트 사용자](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)에게 제공되지 않습니다. 보고서를 업데이트하거나 게시하려면 데이터 가져오기 등의 Power BI 서비스 웹 UI를 사용하여 Power BI Desktop 파일을 업로드해야 합니다.  다음 환경은 지원되지 않습니다.
    * Power BI Desktop에서 Power BI 서비스에 직접 게시
    * 게스트 사용자는 Power BI Desktop을 사용하여 Power BI 서비스의 서비스 데이터 세트에 연결할 수 없습니다.
    * Microsoft 365 그룹에 연결된 클래식 작업 영역:
        * 게스트 사용자는 이러한 작업 영역의 관리자를 만들거나 관리자가 될 수 없습니다.
        * 게스트 사용자는 멤버가 될 수 있습니다.
    * 작업 영역 액세스 목록 임시 초대 전송이 지원되지 않습니다.
    * 게스트 사용자에게는 Power BI Publisher for Excel이 지원되지 않습니다.
    * 게스트 사용자는 Power BI Gateway를 설치하여 조직에 연결할 수 없습니다.
    * 게스트 사용자는 전체 조직에 게시된 앱을 설치할 수 없습니다.
    * 게스트 사용자는 조직 콘텐츠 팩을 사용, 생성, 업데이트 또는 설치할 수 없습니다.
    * 게스트 사용자는 Excel의 분석을 사용할 수 없습니다.
    * 게스트 사용자는 댓글에서 @mentioned 대상이 될 수 없습니다.
    * 게스트 사용자는 구독을 사용할 수 없습니다.
    * 이 기능을 사용하는 게스트 사용자는 회사 또는 학교 계정이 있어야 합니다. 
    
* 개인 계정을 사용하는 게스트 사용자는 로그인 제한 사항으로 인해 더 많은 제한을 받습니다.
    * 웹 브라우저를 통해 Power BI 서비스의 사용 환경을 이용할 수 있습니다.
    * Power BI Mobile 앱은 사용할 수 없습니다.
    * 회사 또는 학교 계정이 필요한 경우 자격 증명을 제공하기 위해 로그인할 수 없습니다.

* 이 기능은 현재 Power BI SharePoint Online 보고서 웹 파트에서 사용할 수 없습니다.

* 외부 게스트 사용자가 전체 조직 내에서 수행할 수 있는 작업을 제한하는 Active Directory 설정이 있습니다. 이 설정은 Power BI 환경에도 적용됩니다. 다음 설명서에는 설정에 대해 설명되어 있습니다.
    * [외부 협업 설정 관리](/azure/active-directory/b2b/delegate-invitations#configure-b2b-external-collaboration-settings)
    * [특정 조직의 B2B 사용자 초대 허용 또는 차단](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)
    * [조건부 액세스를 사용하여 액세스 허용 또는 차단](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps)
    
* 조직 외부 공유는 국가별 클라우드에서 지원되지 않습니다. 대신, 외부 사용자가 콘텐츠에 액세스하는 데 사용할 수 있는 조직 내 사용자 계정을 만듭니다. 

* 게스트 사용자에게 직접 공유하는 경우 Power BI는 링크가 포함된 메일을 사용자에게 보냅니다. 메일을 보내지 않으려면 게스트 사용자를 보안 그룹에 추가하고 보안 그룹에 공유합니다.  

## <a name="next-steps"></a>다음 단계

행 수준 보안 작동 방식을 포함한 자세한 내용은 다음 백서를 참조하세요. [Azure AD B2B를 사용하여 외부 게스트 사용자에게 Power BI 콘텐츠 배포](https://aka.ms/powerbi-b2b-whitepaper).

Azure AD B2B에 대한 자세한 내용은 [Azure AD B2B 협업이란?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/)을 참조하세요.
