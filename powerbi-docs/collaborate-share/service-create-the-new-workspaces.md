---
title: 새 작업 영역 만들기 - Power BI
description: 새 작업 영역과 조직에 대한 주요 메트릭을 제공하도록 빌드된 대시보드, 보고서 및 페이지를 매긴 보고서 컬렉션을 만드는 방법을 알아봅니다.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/26/2020
ms.author: maggies
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: c3a625dcdd58f881c9314e821753f66098e073f5
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85354435"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>Power BI에서 새 작업 영역 만들기

이 문서에서는 클래식 작업 영역 대신 새 작업 영역 작업 영역을 만드는 방법을 설명합니다.  두 유형의 작업 영역 모두 동료와 공동 작업을 할 수 있습니다. 여기에서 대시보드, 보고서 및 페이지를 매긴 보고서의 컬렉션을 만듭니다. 원하는 경우 해당 컬렉션을 앱으로 묶어 더 광범위한 대상 그룹에 배포할 수도 있습니다.

다음은 새 작업 영역과 이전 버전 간의 차이점입니다. 새 작업 영역을 사용하면 다음을 수행할 수 있습니다.

- 사용자 그룹 및 개인에게 작업 영역 역할을 할당합니다.
- Microsoft 365 그룹을 만들지 않고 Power BI에서 작업 영역을 만듭니다.
- 더 유연한 사용 권한 관리를 위해 세분화된 작업 영역 역할을 사용합니다.

:::image type="content" source="media/service-create-the-new-workspaces/power-bi-workspace-sales-marketing.png" alt-text="영업 및 마케팅 샘플 작업 영역":::

자세한 배경 정보는 [새 작업 영역](service-new-workspaces.md) 문서를 참조하세요.

클래식 작업 영역을 마이그레이션할 준비가 되셨나요? 자세한 내용은 [Power BI에서 클래식 작업 영역을 새 작업 영역으로 업그레이드](service-upgrade-workspaces.md)를 참조하세요.

> [!NOTE]
> 작업 영역에서 콘텐츠를 검색하는 Power BI Pro 사용자를 위해 RLS(행 수준 보안)를 적용하려면 사용자에게 뷰어 역할을 할당합니다.

## <a name="create-one-of-the-new-workspaces"></a>새로운 작업 영역 중 하나 만들기

1. 먼저 작업 영역을 만듭니다. **작업 영역** > **작업 영역 만들기**를 선택합니다.
   
     ![작업 영역 만들기](media/service-create-the-new-workspaces/power-bi-workspace-create.png)

2. **클래식으로 되돌리기**를 선택하지 않으면 업그레이드된 작업 영역이 자동으로 생성됩니다.
   
     ![새 작업 영역 환경](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     **클래식으로 되돌리기**를 선택하는 경우 Microsoft 365 그룹을 기준으로 [클래식 작업 영역이 만들어집니다](service-create-workspaces.md).

2. 작업 영역에 고유한 이름을 지정합니다. 이름을 사용할 수 없는 경우 편집하여 고유한 이름을 입력합니다.
   
     작업 영역에서 만드는 앱은 작업 영역과 동일한 이름 및 아이콘을 갖게 됩니다.
   
1. 작업 영역에 대해 설정할 수 있는 몇 가지 선택적 항목은 다음과 같습니다.

    **작업 영역 이미지**를 업로드합니다. 파일은 .png 또는 .jpg 형식일 수 있습니다. 파일 크기는 45KB보다 작아야 합니다.
    
    [**연락처 목록**을 추가합니다](#create-a-contact-list). 기본적으로 작업 영역 관리자는 연락처입니다. 
    
    Microsoft 365 그룹 파일 스토리지 위치를 사용할 [**작업 영역 OneDrive**를 지정](#set-a-workspace-onedrive)합니다. 

    작업 영역을 **전용 용량**에 할당하려면 **프리미엄** 탭에서 **전용 용량**을 선택합니다.
     
    ![전용 용량](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. **저장**을 선택합니다.

    Power BI는 작업 영역을 만들고 엽니다. 구성원으로 속해 있는 작업 영역 목록에서 볼 수 있습니다. 

## <a name="create-a-contact-list"></a>연락처 목록 만들기

작업 영역에서 발생하는 문제에 대한 알림을 받을 사용자를 지정할 수 있습니다. 기본적으로 작업 영역 관리자로 지정된 모든 사용자 또는 그룹에게 알림이 표시되지만 연락처 목록에 다른 사용자를 추가할 수 있습니다. 연락처 목록에 포함된 사용자 또는 그룹은 UI(사용자 인터페이스)에 나열되어 사용자가 작업 영역에 관련된 도움말을 확인할 수 있습니다.

1. 다음 두 가지 방법 중 하나로 **연락처 목록** 설정에 액세스합니다.

    처음 만드는 경우 **작업 영역 만들기** 창에서

    탐색 창에서 **작업 영역** 옆에 있는 화살표를 선택하고 작업 영역 이름 옆에 있는 **추가 옵션**(…) > **작업 영역 설정**을 선택합니다. **설정** 창이 열립니다.

    ![작업 영역 설정](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. **고급** >  **연락처 목록**에서 기본값인 **작업 영역 관리자**를 그대로 적용하거나 고유한 **특정 사용자 또는 그룹** 목록을 추가합니다. 

    ![작업 영역 연락처](media/service-create-the-new-workspaces/power-bi-workspace-contacts.png)

3. **저장**을 선택합니다.

## <a name="set-a-workspace-onedrive"></a>작업 영역 OneDrive 설정

작업 영역 OneDrive 기능을 사용하면 작업 영역 사용자가 SharePoint 문서 라이브러리 파일 스토리지를 사용할 수 있는 Microsoft 365 그룹을 구성할 수 있습니다. 먼저 Power BI 외부에 그룹을 만듭니다. 

Power BI는 작업 영역 액세스 권한을 가지도록 구성된 사용자 또는 그룹의 권한을 Microsoft 365 그룹 멤버 자격과 동기화하지 않습니다. 이 Microsoft 365 그룹 설정에서 파일 스토리지를 구성하는 동일한 Microsoft 365 그룹에 [작업 영역에 대한 액세스 권한](#give-access-to-your-workspace)을 제공하는 것이 좋습니다. 그런 다음, Microsoft 365 그룹의 멤버 자격을 관리하여 작업 영역 액세스를 관리합니다. 

1. 다음 두 가지 방법 중 하나로 새 **작업 영역 OneDrive** 설정에 액세스합니다.

    처음 만드는 경우 **작업 영역 만들기** 창에서

    탐색 창에서 **작업 영역** 옆에 있는 화살표를 선택하고 작업 영역 이름 옆에 있는 **추가 옵션**(…) > **작업 영역 설정**을 선택합니다. **설정** 창이 열립니다.

    ![작업 영역 설정](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. **고급** > **작업 영역 OneDrive**에서 이전에 만든 Microsoft 365 그룹의 이름을 입력합니다. URL이 아닌 이름만 입력합니다. Power BI는 그룹의 OneDrive를 자동으로 선택합니다.

    ![OneDrive 위치 지정](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. **저장**을 선택합니다.

### <a name="access-the-workspace-onedrive-location"></a>작업 영역 OneDrive 위치에 액세스

OneDrive 위치를 구성한 후에는 Power BI 서비스에서 다른 데이터 원본으로 이동하는 것과 동일한 방법으로 가져올 수 있습니다.

1. 탐색 창에서 **데이터 가져오기**를 선택한 다음, **파일** 상자에서 **가져오기**를 선택합니다.

    ![데이터 가져오기, 파일 가져오기](media/service-create-the-new-workspaces/power-bi-get-data-files.png)

1.  **Onedrive – 비즈니스** 항목은 사용자의 고유한 비즈니스용 OneDrive입니다. 두 번째 OneDrive는 추가한 OneDrive입니다.

    ![작업 영역 파일 위치 - 데이터 가져오기](media/service-create-the-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

### <a name="connect-to-apps-in-new-workspaces"></a>새 작업 영역에서 앱에 연결

새 작업 영역 환경에서는 콘텐츠 팩 대신 앱을 만들고 사용합니다. 앱은 타사 서비스 및 조직 데이터에 연결하는 대시보드, 보고서 및 데이터 세트의 컬렉션입니다. 앱을 사용하면 Microsoft Dynamics CRM, Salesforce, Google Analytics 등의 서비스에서 데이터를 쉽게 가져올 수 있습니다.

새 작업 영역 환경에서 조직 콘텐츠 팩을 만들거나 사용할 수 없습니다. 현재 사용 중인 콘텐츠 팩에 대한 앱을 제공하도록 내부 팀에 요청합니다. 

## <a name="give-access-to-your-workspace"></a>작업 영역에 대한 액세스 권한 부여

특정 작업 영역에서 관리자 역할이 있는 사용자는 다른 사용자에게 해당 작업 영역에 대한 액세스 권한을 부여할 수 있습니다.

1. 관리자이므로 작업 영역 콘텐츠 목록 페이지에 **액세스 권한**이 표시됩니다.

    ![작업 영역 콘텐츠 목록](media/service-create-the-new-workspaces/power-bi-workspace-access-icon.png)

1. 보안 그룹, 배포 목록, Microsoft 365 그룹 또는 개인을 이러한 작업 영역에 관리자, 멤버, 참가자 또는 뷰어로 추가합니다. 다양한 역할에 대한 설명은 [새 작업 영역의 역할](service-new-workspaces.md#roles-in-the-new-workspaces)을 참조하세요.

    ![작업 영역 추가 멤버, 관리자, 기여자](media/service-create-the-new-workspaces/power-bi-workspace-add-members.png)

9. **추가** > **닫기**를 선택합니다.


## <a name="distribute-an-app"></a>앱 배포

조직 내의 많은 대상 그룹에 공식 콘텐츠를 배포하려는 경우 작업 영역에서 앱을 게시할 수 있습니다.  콘텐츠가 준비되면 게시할 대시보드 및 보고서를 선택한 다음, 앱으로 게시합니다. 각 작업 영역에서 하나의 앱을 만들 수 있습니다.

[새 작업 영역에서 앱을 게시](service-create-distribute-apps.md)하는 방법을 자세히 알아보세요.

## <a name="security-settings"></a>보안 설정

**참가자가 이 작업 영역에 대한 앱을 업데이트하도록 허용** 설정을 통해 작업 영역 관리자는 작업 영역에 대한 앱을 업데이트하는 기능을 참가자 역할의 사용자에게 위임할 수 있습니다. 기본적으로 작업 영역 관리자 및 구성원만 작업 영역에 대한 앱을 게시하고 업데이트할 수 있습니다. 

사용하도록 설정하면 참가자는 다음을 수행할 수 있습니다.
* 이름, 아이콘, 설명, 지원 사이트, 색과 같은 앱 메타데이터를 업데이트
* 보고서 또는 데이터 세트 추가와 같이 앱에 포함된 항목을 추가 또는 제거
* 앱이 열리는 앱 탐색 또는 기본 항목을 변경

그러나 참가자는 다음과 같은 작업을 수행할 수 없습니다.
* 처음으로 앱을 게시
* 앱에 대한 사용 권한이 있는 사용자를 변경


## <a name="next-steps"></a>다음 단계
* [Power BI의 새 작업 영역에서 작업 구성](service-new-workspaces.md)에 대해 알아보기
* [클래식 작업 영역 만들기](service-create-workspaces.md)
* [Power BI의 새 작업 영역에서 앱 게시](service-create-distribute-apps.md)
* 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
