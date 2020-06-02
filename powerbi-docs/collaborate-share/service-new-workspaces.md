---
title: Power BI의 새 작업 영역에서 작업 구성
description: 조직에 대한 주요 메트릭을 제공하도록 빌드된 대시보드 및 보고서의 컬렉션인 새 작업 영역에 대해 알아봅니다.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/26/2020
ms.author: maggies
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: 77de9608978379cee83236b0c362bd2d7d57d5c6
ms.sourcegitcommit: a7b142685738a2f26ae0a5fa08f894f9ff03557b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84120355"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Power BI의 새 작업 영역에서 작업 구성

*작업 영역*은 동료와 협업하여 대시보드, 보고서, 데이터 세트 및 페이지를 매긴 보고서의 컬렉션을 만드는 공간입니다. 새 작업 영역 환경을 사용하면 콘텐츠에 대한 액세스를 더 잘 관리할 수 있습니다. 이 문서에서는 새 작업 영역에 대해 설명하고 클래식 작업 영역과 어떻게 다른지 설명합니다.  클래식 작업 영역과 마찬가지로 새 작업 영역을 사용하여 앱을 만들고 배포합니다. 새 작업 영역을 만들 준비가 되셨나요? [새 작업 영역 환경 만들기](service-create-the-new-workspaces.md)를 읽으세요.

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Power BI 새 작업 영역 환경":::

업그레이드된 새 작업 영역을 기존의 클래식 작업 영역과 함께 사용할 수 있습니다. 새 작업 영역 환경은 기본 작업 영역 유형입니다. 필요한 경우 여전히 Microsoft 365 그룹을 기반으로 [클래식 작업 영역](service-create-workspaces.md)을 만들고 사용할 수 있습니다. 클래식 작업 영역을 마이그레이션할 준비가 되셨나요? 자세한 내용은 [Power BI에서 클래식 작업 영역을 새 작업 영역으로 업그레이드](service-upgrade-workspaces.md)를 참조하세요.

## <a name="new-and-classic-workspace-differences"></a>새 작업 영역과 클래식 작업 영역의 차이점

새 작업 영역에서는 몇 가지 기능이 다시 디자인되었습니다. 주요 차이점은 다음과 같습니다.

- 클래식 작업 영역과 달리 **새 작업 영역을 만들어도 Microsoft 365 그룹이 생성되지 않습니다**. 모든 새 작업 영역 관리는 Office 365가 아닌 Power BI에 위치합니다. 원하는 경우 Microsoft 365 그룹을 통해 콘텐츠에 대한 사용자 액세스를 계속 관리할 수 있습니다. 작업 영역 액세스 목록에서 Microsoft 365 그룹을 추가하기만 하면 됩니다.
- 새 작업 영역에서는 더 유연한 사용 권한 관리를 위해 **세분화된 작업 영역 역할을 사용합니다**.  클래식 작업 영역에 구성원 및 관리자 목록에는 개인만 추가할 수 있습니다. 
- **작업 영역 역할에 사용자 그룹 할당**: 새 작업 영역에서는 사용자 관리를 간소화하기 위해 이러한 역할에 여러 Active Directory 보안 그룹, 배포 목록 또는 Microsoft 365 그룹을 추가할 수 있습니다. 
- **연락처 목록**: 새 작업 영역에서는 작업 영역 활동에 대한 알림을 받을 사용자를 지정할 수 있습니다.
- **템플릿 앱 만들기**: 새 작업 영역에서만 템플릿 앱을 만들 수 있습니다. 템플릿 앱은 조직 외부 고객에게 배포할 수 있는 앱입니다. 이러한 고객은 템플릿 앱을 사용하여 자신의 데이터에 연결할 수 있습니다. [템플릿 앱](../connect-data/service-template-apps-overview.md)에 대해 자세히 알아보세요.
- **데이터 세트 공유**: 특정 작업 영역 외부의 데이터 세트를 공유하려면 데이터 세트가 포함된 보고서를 새 작업 영역 중 하나에 저장해야 합니다. 클래식 작업 영역의 데이터 세트는 공유할 수 없습니다. [공유 데이터 세트](../connect-data/service-datasets-across-workspaces.md)에 대해 자세히 알아보세요.
- **조직 콘텐츠 팩**: 클래식 작업 영역에서는 조직 콘텐츠 팩을 만들고 사용합니다. 새 작업 영역에서는 만들거나 사용할 수 없습니다. 앱 및 템플릿 앱이 새 작업 영역에서 조직 콘텐츠 팩을 대체합니다.

이 문서에서는 이러한 기능에 대해 자세히 설명합니다.

> [!NOTE]
> Power BI는 사용자가 구성원으로 속한 모든 Microsoft 365 그룹을 계속 나열합니다. 그러므로 기존 워크플로를 변경하지 않아도 됩니다.

### <a name="features-that-work-differently"></a>다르게 작동하는 기능

새 작업 영역에서는 일부 기능이 다르게 작동합니다. 이러한 차이점은 고객에게서 받은 피드백에 따라 의도적으로 적용한 것입니다. 이를 통해 작업 영역에서 보다 유연하게 공동 작업을 수행할 수 있습니다.

- **라이선스 적용**: 새 작업 영역 환경에 보고서를 게시하면 기존 라이선스 규칙이 적용됩니다. 사용자가 새 작업 영역에서 공동 작업을 수행하거나 Power BI 서비스의 다른 사용자에게 콘텐츠를 공유하려면 Power BI Pro 라이선스가 필요합니다. Pro 라이선스가 없는 사용자에게는 “Power BI Pro 라이선스를 가진 사용자만 이 작업 영역에 게시할 수 있습니다.”라는 오류가 표시됩니다.
- **'구성원이 다시 공유할 수 있음' 설정**: 새 작업 영역의 참가자 역할은 클래식 작업 영역의 '구성원이 다시 공유할 수 있음' 설정을 대체합니다.
- **읽기 전용 작업 영역**: 새 작업 영역의 뷰어 역할은 사용자에게 클래식 작업 영역에 대한 읽기 전용 액세스 권한을 부여하는 것을 대체합니다. 뷰어 역할은 새 작업 영역의 콘텐츠에 대해 비슷한 읽기 전용 액세스를 허용합니다.
- **Pro 라이선스가 없는 사용자**는 작업 영역이 Power BI Premium 용량에 있으면 뷰어 역할만 있어도 새 작업 영역에 액세스할 수 있습니다.
- **사용자가 데이터를 내보내도록 허용**: 새 작업 영역에서 뷰어 역할이 있는 사용자는 해당 작업 영역의 데이터 세트에 대한 빌드 권한이 있는 경우 데이터를 내보낼 수 있습니다. [데이터 세트 빌드 권한](../connect-data/service-datasets-build-permissions.md)에 대해 자세히 알아보세요.
- 새 작업 영역에는 **작업 영역 나가기** 단추가 없습니다.

### <a name="workspace-contact-list"></a>작업 영역 연락처 목록

새 **연락처 목록** 기능을 사용하면 새 작업 영역에서 발생하는 문제에 대한 알림을 받는 사용자를 지정할 수 있습니다. 기본적으로 새 작업 영역에서 작업 영역 관리자로 지정된 모든 사용자 또는 그룹에게 알림이 표시됩니다. 이 목록에 추가할 수 있습니다. 연락처 목록의 사용자 또는 그룹은 새 작업 영역의 UI(사용자 인터페이스)에도 나열되므로 작업 영역 최종 사용자가 누구에게 연락해야 할지 알 수 있습니다. 

[작업 영역 연락처 목록을 만드는 방법](service-create-the-new-workspaces.md#create-a-contact-list)을 자세히 알아보세요.

### <a name="workspace-onedrive"></a>작업 영역 OneDrive

앞서 설명한 것처럼 새 작업 영역을 만들 때 Power BI가 백그라운드에서 Microsoft 365 그룹을 만들지 않습니다. 그래도 OneDrive를 새 작업 영역에 연결하는 것이 유용할 수 있습니다. 새 작업 영역에서 작업 영역 OneDrive 기능을 사용하면 작업 영역 사용자가 SharePoint 문서 라이브러리 파일 스토리지를 사용할 수 있는 Microsoft 365 그룹을 구성할 수 있습니다. Power BI 외부에 그룹을 만듭니다.
 
Power BI는 Microsoft 365 그룹 멤버 자격과 새 작업 영역에 대한 액세스 권한이 있는 사용자 또는 그룹의 권한을 동기화하지 않습니다. 사용자가 직접 동기화할 수 있습니다. 이 설정에서 파일 스토리지를 구성하는 동일한 Microsoft 365 그룹을 통해 작업 영역 액세스를 관리합니다. 

[작업 영역 OneDrive를 설정하는 방법](service-create-the-new-workspaces.md#set-a-workspace-onedrive)을 자세히 알아보세요.  

## <a name="roles-in-the-new-workspaces"></a>새 작업 영역의 역할

역할을 통해 팀이 공동 작업할 수 있도록 새 작업 영역에서 수행할 수 있는 작업 및 사용자를 관리할 수 있습니다. 새 작업 영역을 사용하면 개인 및 사용자 그룹(보안 그룹, Microsoft 365 그룹 및 배포 목록)에 역할을 할당할 수 있습니다. 

새 작업 영역에 대한 액세스 권한을 부여하려면 해당 사용자 그룹 또는 개인을 작업 영역 역할 중 하나에 할당합니다. 관리자, 구성원, 참가자 또는 뷰어 역할을 할당합니다. 사용자 그룹의 모든 사용자는 할당된 역할을 얻습니다. 여러 사용자 그룹에 속한 경우 할당된 역할에서 제공하는 가장 높은 수준의 권한을 얻을 수 있습니다. 사용자 그룹을 중첩하는 경우 포함된 모든 사용자에게는 사용 권한이 있습니다. 보기와 상호 작용을 제외한 모든 기능에는 Power BI Pro 라이선스가 필요합니다. 이 문서에서 [라이선스](#licenses)에 대해 자세히 알아보세요.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - 역할을 사용할 수 없는 경우에도 사용자를 단독으로 또는 그룹으로 역할에 할당할 수 있습니다. 즉, Power BI Pro 라이선스가 없는 사용자를 라이선스가 필요한 역할에 할당할 수 있습니다. 자세한 내용은 이 문서의 [라이선스](#licenses)를 참조하세요.
> - 작업 영역에서 콘텐츠를 찾아보는 사용자에 대한 [RLS(행 수준 보안)](../admin/service-admin-rls.md)를 적용하려면 뷰어 역할을 사용합니다. 새 작업 영역에 대한 액세스 권한을 부여하지 않고 RLS를 적용할 수도 있습니다. [앱을 게시](service-create-distribute-apps.md)하고 해당 사용자에게 배포하거나 [공유를 사용하여 콘텐츠를 배포](service-share-dashboards.md)합니다.

## <a name="licensing-and-administering"></a>라이선스 및 관리

### <a name="licenses"></a>라이선스
새 작업 영역 중 하나가 공유 용량에 있는 경우 여기에 추가하는 모든 사용자에게 Power BI Pro 라이선스가 필요합니다. 이러한 사용자는 모두 새 작업 영역의 대시보드 및 보고서에서 공동 작업할 수 있습니다. 조직 내 다른 사용자에게 콘텐츠를 배포하려는 경우 해당 사용자에게 Power BI Pro 라이선스를 할당하거나 Power BI Premium 용량에 작업 영역을 배치할 수 있습니다.

새 작업 영역이 Power BI Premium 용량에 있으면 뷰어 역할을 가진 사용자는 Power BI Pro 라이선스가 없어도 작업 영역에 액세스할 수 있습니다. 그러나 이 사용자에게 관리자, 구성원 또는 참가자와 같은 상위 역할을 할당하면 사용자가 작업 영역에 액세스할 때 Pro 평가판을 시작하라는 메시지가 표시됩니다. Pro 라이선스가 없는 사용자가 뷰어 역할을 사용하도록 하려면 다른 작업 영역 역할이 개인 또는 사용자 그룹의 일부로 포함되지 않도록 해야 합니다.

> [!NOTE]
> 보고서를 새 작업 영역 환경에 게시하는 경우에는 기존 라이선스 규칙이 더 엄격하게 적용됩니다. Pro 라이선스 없이 Power BI Desktop 또는 다른 클라이언트 도구에서 게시하려고 하면 “Power BI Pro 라이선스를 가진 사용자만 이 작업 영역에 게시할 수 있습니다.”라는 오류가 표시됩니다.

### <a name="guest-users"></a>게스트 사용자

기본적으로 [Azure AD B2B 게스트 사용자](../admin/service-admin-azure-ad-b2b.md)는 작업 영역에 액세스할 수 없습니다. Power BI 관리자는 [외부 게스트 사용자가 조직의 콘텐츠를 편집하고 관리하도록 허용](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content)할 수 있습니다. 사용하도록 설정된 게스트 사용자는 사용 권한을 가진 작업 영역에 액세스할 수 있습니다.

### <a name="administering-new-workspace-experience-workspaces"></a>새 작업 영역 환경의 작업 영역 관리

새 작업 영역 환경 작업 영역에 대한 관리는 Power BI 관리 포털에서 수행합니다. Power BI 관리자는 조직에서 누가 작업 영역을 만들고 앱을 배포할 수 있는지 결정합니다. 관리자는 조직의 모든 작업 영역에 대한 상태를 볼 수 있습니다. 작업 영역을 관리 및 복구할 수도 있습니다. 관리 포털 문서에서 [새 작업 영역 관리](../admin/service-admin-portal.md#create-the-new-workspaces)에 대해 자세히 알아보세요.

### <a name="auditing"></a>감사

Power BI는 새 작업 영역 환경 작업 영역에 대한 다음 작업을 감사합니다.

| 식별 이름 | 작업 이름 |
|---|---|
| Power BI 폴더 만듦 | CreateFolder |
| Power BI 폴더 삭제됨 | DeleteFolder |
| Power BI 폴더 업데이트됨 | UpdateFolder |
| Power BI 폴더 액세스 권한 업데이트됨| UpdateFolderAccess |

[Power BI 감사](../admin/service-admin-auditing.md)에 대해 자세히 알아봅니다.

## <a name="limitations-and-considerations"></a>제한 사항 및 고려 사항

알아야 할 제한 사항:

- 작업 영역은 최대 1,000개 데이터 세트 또는 데이터 세트당 1,000개 보고서를 포함할 수 있습니다. 
- Power BI Pro 라이선스가 있는 사용자는 최대 1,000개 작업 영역의 구성원일 수 있습니다.
- Excel용 Power BI 게시자는 지원되지 않습니다.

## <a name="frequently-asked-questions"></a>질문과 대답

**새 작업 영역 환경이 기존 콘텐츠의 링크에 영향을 주나요?**

아니요. 새 작업 영역 환경은 클래식 작업 영역의 기존 항목 링크에 영향을 주지 않습니다. 새 작업 영역 환경의 GA(일반 공급)는 사용자가 만드는 기본 작업 영역을 변경하지만 기존 작업 영역을 변경하지는 않습니다. 

**GA를 통해 기존 작업 영역이 새 작업 영역 환경으로 업그레이드되나요?**

아니요. 새 작업 영역 환경 GA는 기본 작업 영역 유형만 새 작업 영역 환경으로 변경합니다. Microsoft 365 그룹을 기반으로 하는 기존 클래식 작업 영역은 변경되지 않습니다.

**Microsoft 365 그룹에 대한 작업 영역이 계속 자동으로 생성되나요?**

예. 두 유형의 작업 영역을 모두 나란히 지원하므로 작업 영역 목록에서 사용자가 액세스할 수 있는 모든 Microsoft 365 그룹을 계속 나열합니다.

## <a name="next-steps"></a>다음 단계

* [Power BI에서 새 작업 영역 만들기](service-create-the-new-workspaces.md)
* [클래식 작업 영역 만들기](service-create-workspaces.md)
* [Power BI에서 앱 설치 및 사용](service-create-distribute-apps.md)
* 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)

