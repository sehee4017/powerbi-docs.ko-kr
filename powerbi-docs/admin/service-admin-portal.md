---
title: Power BI 관리 포털
description: 관리 포털을 통해 조직에서 Power BI의 테넌트 관리를 사용할 수 있습니다. 사용 메트릭, Microsoft 365 관리 센터에 대한 액세스 및 설정과 같은 항목을 포함하고 있습니다.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/12/2020
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 460ab380798975065eb90bf904b2b5bacd1edd2c
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315974"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>관리 포털에서 Power BI 관리

관리 포털을 통해 조직의 Power BI ‘테넌트’를 관리할 수 있습니다. 포털에는 사용 메트릭, Microsoft 365 관리 센터에 대한 액세스 및 설정과 같은 항목이 포함되어 있습니다.

전체 관리 포털은 전역 관리자이거나 Power BI 서비스 관리자 역할에 할당된 모든 사용자가 액세스할 수 있습니다. 이러한 역할 중 하나를 할당받지 않은 경우에는 포털에 **용량 설정**만 표시됩니다. Power BI 서비스 관리자 역할에 대한 자세한 내용은 [Power BI 관리자 역할 이해](service-admin-role.md)를 참조하세요.

## <a name="how-to-get-to-the-admin-portal"></a>관리 포털에 도달하는 방법

Power BI 관리 포털에 대한 액세스 권한을 얻으려면 계정이 Microsoft 365 또는 Azure AD(Azure Active Directory) 내에서 **전역 관리자**로 표시되거나 Power BI 서비스 관리자 역할이 할당되어야 합니다. Power BI 서비스 관리자 역할에 대한 자세한 내용은 [Power BI 관리자 역할 이해](service-admin-role.md)를 참조하세요. Power BI 관리 포털에 도달하려면 다음을 수행합니다.

1. Power BI 서비스의 오른쪽 위에서 설정 아이콘을 선택합니다.

1. **관리 포털**을 선택합니다.

    ![관리 포털에 대한 설정](media/service-admin-portal/powerbi-admin-settings.png)

포털에는 9개의 탭이 있습니다. 이 문서의 나머지 부분에서는 이러한 각 탭에 대한 정보를 제공합니다.

![관리 포털 탐색](media/service-admin-portal/powerbi-admin-landing-page.png)

* [사용량 메트릭](#usage-metrics)
* [사용자](#users)
* [감사 로그](#audit-logs)
* [테넌트 설정](#tenant-settings)
* [용량 설정](#capacity-settings)
* [embed 태그](#embed-codes)
* [조직의 시각적 개체](#organizational-visuals)
* [데이터 흐름 스토리지(미리 보기)](#dataflowStorage)
* [작업 영역](#workspaces)
* [사용자 지정 브랜딩](#custom-branding)

## <a name="usage-metrics"></a>사용량 메트릭

**사용량 메트릭**을 통해 조직의 Power BI 사용을 모니터링할 수 있습니다. 또한 조직을 위한 Power BI 내에서 가장 활발한 사용자 및 그룹이 누구인지 확인하는 기능을 제공합니다. 

> [!NOTE]
> 대시보드에 처음 액세스할 때 또는 대시보드를 오랫동안 보지 않았다가 다시 방문한 후 대시보드를 로드하는 동안 로드 중 화면이 표시될 수 있습니다.

대시보드가 로드된 후 타일 섹션 두 개가 표시됩니다. 첫 번째 섹션은 개별 사용자에 대한 사용량 데이터를 포함하고 있으며 두 번째 섹션은 조직의 그룹에 대해 유사한 정보를 포함하고 있습니다.

다음은 각 타일에 표시되는 내용에 대한 요약입니다.

* 사용자 작업 영역의 모든 대시보드, 보고서 및 데이터 세트에 대한 고유한 개수입니다.
  
    ![대시보드, 보고서, 데이터 세트에 대한 고유한 개수](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* 액세스할 수 있는 사용자 수별로 가장 많이 사용한 대시보드입니다. 예를 들어 사용자 3명과 공유하는 대시보드가 있는데 서로 다른 두 사용자가 연결한 콘텐츠 팩에 이를 추가하면 개수는 6(1+3+2)개가 됩니다.
  
    ![가장 많이 사용한 대시보드](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* 사용자가 연결한 가장 인기 있는 콘텐츠입니다. 사용자가 데이터 가져오기 프로세스를 통해 도달할 수 있는 모든 것, 다시 말해서 SaaS 콘텐츠 팩, 조직 콘텐츠 팩, 파일 또는 데이터베이스가 이에 해당합니다.
  
    ![가장 많이 사용한 패키지](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* 직접 만든 대시보드 및 공유하는 대시보드를 모두 포함하여 가지고 있는 대시보드 수를 기반으로 하는 최상위 사용자의 뷰입니다.
  
    ![최상위 사용자 - 대시보드](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* 가지고 있는 보고서 수를 기반으로 하는 최상위 사용자의 뷰입니다.
  
    ![최상위 사용자 - 보고서](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

두 번째 섹션은 동일한 유형의 정보를 보여 주지만 그룹을 기반으로 합니다. 여기에서는 조직에서 가장 활발한 그룹 및 해당 그룹이 사용 중인 콘텐츠의 종류를 확인할 수 있습니다.

이 정보를 사용하여 조직의 사용자가 Power BI를 사용하는 방법을 실제로 파악할 수 있으며 조직에서 매우 활발한 사용자 및 그룹을 인식할 수 있습니다.

## <a name="control-usage-metrics"></a>사용량 메트릭 제어

사용량 메트릭 보고서는 Power BI 또는 전역 관리자가 켜거나 끌 수 있는 기능입니다. 관리자는 사용량 메트릭에 액세스할 수 있는 사용자를 세부적으로 제어할 수 있습니다. 기본적으로 조직의 모든 사용자에 대해 **켬**으로 설정되어 있습니다.

관리자는 콘텐츠 작성자가 사용량 메트릭에서 사용자별 데이터를 볼 수 있는지 여부도 설정할 수 있습니다. 

보고서에 대한 자세한 내용은 [Power BI 대시보드 및 보고서의 사용량 메트릭 모니터링](../collaborate-share/service-usage-metrics.md)을 참조하세요.

### <a name="usage-metrics-for-content-creators"></a>콘텐츠 작성자용 사용량 메트릭

1. 관리 포털에서 **테넌트 설정** > **콘텐츠 작성자용 사용량 메트릭**을 선택합니다.

    ![관리 포털 테넌트 설정 사용 메트릭](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. 사용량 메트릭을 활성화(또는 비활성화)하고 **적용**을 클릭합니다.

    ![설정된 사용 메트릭](../collaborate-share/media/service-usage-metrics/power-bi-tenant-settings-updated.png)


### <a name="per-user-data-in-usage-metrics"></a>사용량 메트릭의 사용자별 데이터

기본적으로 사용자별 데이터는 사용량 메트릭에서 활성화되어 있고 메트릭 보고서에는 콘텐츠 소비자 계정 정보가 포함됩니다. 일부 또는 모든 사용자에게 이 정보를 포함하지 않으려는 경우 지정된 보안 그룹 또는 전체 조직에 기능을 사용하지 않도록 설정합니다. 그러면 계정 정보는 *이름 없음*으로 보고서에 표시됩니다.

![사용자별 사용량 현황 데이터](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>모든 기존 사용량 메트릭 콘텐츠 삭제

조직 전체의 사용량 메트릭을 비활성화할 때, 관리자는 다음 옵션 중 하나 또는 둘 모두를 선택할 수 있습니다.

- **기존 사용량 메트릭 콘텐츠 모두 삭제** 옵션을 사용하여 사용량 메트릭 보고서 및 데이터 세트를 사용하여 빌드한 기존 보고서 및 대시보드 타일을 모두 삭제합니다. 이 옵션은 이미 사용량 메트릭을 사용 중일 수도 있는 조직의 모든 사용자에게서 사용량 메트릭 데이터에 대한 모든 액세스를 제거합니다. 
- **현재 사용량 메트릭 콘텐츠의 모든 기존 사용자별 데이터 삭제** 이 옵션은 이미 사용량 메트릭을 사용 중인 사용자를 포함하여 조직의 모든 사용자에게서 사용자별 데이터에 대한 액세스를 모두 제거합니다. 

기존 사용량 메트릭과 사용자별 메트릭 콘텐츠의 삭제는 되돌릴 수 없으므로 조심해야 합니다.

## <a name="users"></a>사용자

Microsoft 365 관리 센터에서 Power BI 사용자, 그룹 및 관리자를 관리합니다. **사용자** 탭은 테넌트의 관리 센터에 대한 링크를 제공합니다.

![Microsoft 365 관리 센터로 이동](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>감사 로그

Office 365 보안 및 준수 센터에서 Power BI 감사 로그를 관리합니다. **감사 로그** 탭은 테넌트의 보안 및 준수 센터에 대한 링크를 제공합니다. [자세히 알아보기](service-admin-auditing.md)

감사 로그를 사용하려면 [**내부 활동 감사 및 규정 준수를 위해 감사 로그 만들기**](#create-audit-logs-for-internal-activity-auditing-and-compliance) 설정이 사용하도록 설정되어 있는지 확인합니다.

## <a name="tenant-settings"></a>테넌트 설정

**테넌트 설정** 탭에서는 조직에서 사용할 수 있는 기능에 대한 세분화된 제어를 제공합니다. 중요한 데이터에 대한 우려가 있는 경우 일부 기능은 사용자의 조직에 적합하지 않을 수 있거나 특정 기능을 특정 그룹만 사용할 수 있도록 할 수 있습니다.

> [!NOTE]
> Power BI 사용자 인터페이스에서 기능의 가용성을 제어하는 테넌트 설정은 거버넌스 정책을 수립하는 데 도움이 될 수 있지만 보안 조치는 아닙니다. 예를 들어 **데이터 내보내기** 설정은 데이터 세트에 대한 Power BI 사용자의 권한을 제한하지 않습니다. 데이터 세트에 대한 읽기 권한이 있는 Power BI 사용자에게는 이 데이터 세트를 쿼리할 수 있는 권한이 있으며, Power BI 사용자 인터페이스에서 **데이터 내보내기** 기능을 사용하지 않고 결과를 유지할 수도 있습니다.

다음 이미지에서는 **테넌트 설정** 탭의 여러 설정을 보여 줍니다.

![테넌트 설정](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> 설정 변경 내용이 테넌트의 모든 사용자에게 적용되려면 최대 10분까지 걸릴 수 있습니다.

설정에는 다음과 같은 세 가지 상태가 포함될 수 있습니다.

* **전체 조직에서 사용하지 않도록 설정됨**: 조직의 누구도 이 기능을 사용할 수 없습니다.

    ![모두 사용 안 함 설정](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **전체 조직에서 사용하도록 설정됨**: 조직의 모든 사용자가 이 기능을 사용할 수 있습니다.

    ![모두 사용 설정](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **조직 일부에서 사용하도록 설정됨**: 조직에서 사용자 또는 그룹의 특정 하위 세트만 이 기능을 사용할 수 있습니다.

    특정 사용자 그룹을 제외하고 전체 조직에서 기능을 사용하도록 설정할 수 있습니다.

    ![하위 집합 사용 설정](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    또한 특정 사용자 그룹에만 기능을 사용하도록 설정하고 사용자 그룹에 대해 사용하지 않도록 설정할 수도 있습니다. 이 경우 특정 사용자가 허용되는 그룹에 있더라도 해당 기능에 액세스할 수 없게 됩니다.

    ![제외 사용 설정](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

다음 몇몇 섹션에서는 다양한 형식의 테넌트 설정 개요를 제공합니다.

## <a name="help-and-support-settings"></a>도움말 및 지원 설정

### <a name="publish-get-help-information"></a>"도움말 보기" 정보 게시

조직의 사용자는 Power BI 도움말 메뉴에서 내부 도움말 및 지원 리소스로 이동할 수 있습니다. 특히 이러한 매개 변수는 학습, 커뮤니티 및 도움말 보기 메뉴 항목을 변경합니다.

또한 라이선스 요청에 URL을 지정하여 **계정 업그레이드** 단추의 대상 URL을 사용자 지정합니다. Power BI Pro 라이선스가 없는 사용자는 **Power BI Pro 업데이트** 대화 상자와 **개인 스토리지 관리** 페이지에 이 단추가 표시됩니다. 또한 Power BI는 이 대화 상자나 스토리지 페이지에서 **무료로 Pro 사용해 보기** 단추를 더 이상 제공하지 않습니다. 이렇게 하면 Power BI에서 라이선스 관리 솔루션을 통해 조직에 정의된 프로세스를 사용자에게 안정적으로 안내할 수 있습니다.

![제외 사용 설정](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>서비스 중단 또는 인시던트에 대한 이메일 알림 받기

이 테넌트가 서비스 중단 또는 인시던트의 영향을 받는 경우 메일 사용이 가능한 보안 그룹이 메일 알림을 받습니다. [서비스 중단 알림](service-interruption-notifications.md)에 대해 자세히 알아보세요.

## <a name="workspace-settings"></a>작업 영역 설정

**테넌트 설정**에서 관리 포털에는 작업 영역을 제어하는 두 개의 섹션이 있습니다.

- 새 작업 영역 환경을 만듭니다.
- 작업 영역에서 데이터 세트를 사용합니다.

### <a name="create-the-new-workspaces"></a>새 작업 영역 만들기

작업 영역은 사용자가 대시보드, 보고서 및 기타 콘텐츠에 대해 공동 작업할 수 있는 장소입니다. 관리자는 **작업 영역(새 작업 영역 환경) 만들기** 설정을 사용하여 조직에서 작업 영역을 만들 수 있는 사용자를 표시합니다. 관리자는 조직의 모든 사용자가 새 작업 영역 환경 작업 영역을 만들도록 허용 또는 금지할 수 있습니다. 특정 보안 그룹의 구성원으로만 만들기를 제한할 수도 있습니다. [작업 영역](../collaborate-share/service-new-workspaces.md)에 대해 자세히 알아보세요.

:::image type="content" source="media/service-admin-portal/power-bi-admin-workspace-settings.png" alt-text="새 작업 영역 환경 만들기":::

Microsoft 365 그룹을 기반으로 하는 클래식 작업 영역의 경우 관리 포털 및 Azure Active Directory에서 관리가 계속 수행됩니다.

> [!NOTE]
> **작업 영역 만들기(새 작업 영역 환경)**  설정은 기본적으로 Microsoft 365 그룹을 만들 수 있는 사용자만 새 Power BI 작업 영역을 만들도록 허용합니다. 해당하는 사용자가 새 작업 영역을 만들 수 있도록 Power BI 관리 포털에서 값을 설정해야 합니다.

**작업 영역 목록**

관리 포털에는 테넌트의 작업 영역에 대한 다른 설정 섹션이 있습니다. 이 섹션에서 작업 영역 목록을 정렬 및 필터링하고 각 작업 영역에 대한 세부 정보를 표시할 수 있습니다. 자세한 내용은 이 문서의 [작업 영역](#workspaces)을 참조하세요.

**콘텐츠 팩 및 앱 게시**

관리 포털에서는 조직에 앱을 배포할 권한이 있는 사용자를 제어할 수도 있습니다. 자세한 내용은 이 문서의 [콘텐츠 팩과 앱을 전체 조직에 게시](#publish-content-packs-and-apps-to-the-entire-organization)를 참조하세요.

### <a name="use-datasets-across-workspaces"></a>작업 영역에서 데이터 세트 사용

관리자는 조직에서 작업 영역의 데이터 세트를 사용할 수 있는 사용자를 제어할 수 있습니다. 이 설정을 활성화하면 사용자는 특정 데이터 세트에 대해 필수 빌드 권한이 계속 필요합니다.

:::image type="content" source="media/service-admin-portal/power-bi-admin-datasets-workspaces.png" alt-text="작업 영역에서 데이터 세트 사용":::

자세한 내용은 [작업 영역 데이터 세트 소개](../connect-data/service-datasets-across-workspaces.md)를 참조하세요.


## <a name="export-and-sharing-settings"></a>내보내기 및 공유 설정

### <a name="share-content-with-external-users"></a>외부 사용자와 콘텐츠 공유

조직의 사용자는 조직 외부의 사용자와 대시보드, 보고서 및 앱을 공유할 수 있습니다. [외부 공유](../collaborate-share/service-share-dashboards.md#share-a-dashboard-or-report-outside-your-organization)에 관해 자세히 알아보세요.

![외부 사용자 설정](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

다음 이미지는 외부 사용자와 공유할 때 표시되는 메시지를 보여 줍니다.

![외부 사용자와 공유](media/service-admin-portal/powerbi-admin-sharing-external.png)  

> [!IMPORTANT]
> 이 옵션은 Power BI 사용자가 조직에서 Power BI를 통해 외부 사용자를 Azure AD B2B(Azure Active Directory B2B) 게스트 사용자로 초대할 수 있는지 여부를 제어합니다. 사용하도록 설정된 경우, Azure AD에서 게스트 초대자 역할을 갖는 사용자는 보고서, 대시보드 및 Power BI 앱을 공유할 때 외부 메일 주소를 추가할 수 있습니다. 외부 수신자는 Azure AD B2B 게스트 사용자로 조직에 가입하라는 초대를 받게 됩니다. 이 설정을 비활성화할 경우 이 조직에서 기존에 Azure AD B2B 게스트 사용자가 된 외부 사용자는 계속해서 Power BI의 사용자 선택 UI에 표시되고 항목, 작업 영역 및 앱에 대한 액세스 권한을 부여받을 수 있습니다.

### <a name="publish-to-web"></a>웹에 게시

**웹에 게시** 설정은 Power BI 테넌트 관리자에게 사용자가 embed 태그를 만들어 보고서를 웹에 게시할 수 있는 옵션을 제공합니다. 이 기능을 통해 웹상의 모든 사용자가 보고서 및 해당 데이터를 사용할 수 있습니다. [웹에 게시하는 방법](../collaborate-share/service-publish-to-web.md)에 대해 자세히 알아보세요.

> [!NOTE]
> Power BI 관리자만 새 웹에 게시 embed 태그를 만들 수 있습니다. 조직에 기존 embed 태그가 있을 수 있습니다. 현재 게시된 보고서를 검토하려면 관리 포털의 [embed 태그](service-admin-portal.md#embed-codes) 섹션을 참조하세요.

다음 이미지에서는 **웹에 게시** 설정을 사용하도록 설정된 경우 보고서에 대한 **기타 옵션(...)** 메뉴를 보여 줍니다.

![기타 옵션 메뉴의 웹에 게시](media/service-admin-portal/power-bi-more-options-publish-web.png)

관리 포털의 **웹에 게시** 설정은 사용자가 embed 태그를 만들 수 있는 옵션을 제공합니다.

![웹에 게시 설정](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

관리자는 **웹에 게시**를 **사용**으로 설정하고, **embed 태그 작동 방식 선택**을 **기존 embed 태그만 허용**으로 설정할 수 있습니다. 이 경우 사용자는 embed 태그를 만들 수 있지만, 이렇게 하려면 Power BI 관리자에게 문의해야 합니다.

![웹에 게시 프롬프트](../collaborate-share/media/service-publish-to-web/publish_to_web_admin_prompt.png)

**웹에 게시** 설정에 따라 UI에 다른 옵션이 표시됩니다.

|기능 |전체 조직에 대해 사용 |전체 조직에 대해 사용 안 함 |특정 보안 그룹   |
|---------|---------|---------|---------|
|보고서 **기타 옵션(...)** 메뉴 아래의 **웹에 게시**|모든 사용자에 대해 사용|모든 사용자에게 표시 안 함|권한 있는 사용자 또는 그룹에만 표시.|
|**설정** 아래의 **embed 태그 관리**|모든 사용자에 대해 사용|모든 사용자에 대해 사용|모든 사용자에 대해 사용<br><br>권한 있는 사용자 또는 그룹에만 * **삭제** 옵션 제공.<br>*  모든 사용자에 대해 **코드 가져오기** 사용.|
|관리자 포털 내의 **embed 태그**|상태는 다음 중 하나를 반영합니다.<br>* 활성<br>* 지원되지 않음<br>* 차단됨|상태에 **사용 안 함**이 표시됨|상태는 다음 중 하나를 반영합니다.<br>* 활성<br>* 지원되지 않음<br>* 차단됨<br><br>테넌트 설정에 따라 사용자에게 권한이 부여되지 않으면 **침해됨**이라는 상태가 표시됩니다.|
|게시된 기존 보고서|모두 사용|모두 사용 안 함|보고서가 모든 사용자에 대해 계속 렌더링합니다.|

### <a name="export-data"></a>데이터 내보내기

조직의 사용자는 타일 또는 시각화에서 데이터를 내보낼 수 있습니다. 이 컨트롤은 Excel에서 분석, .csv로 내보내기, 데이터 세트 다운로드(.pbix) 및 Power BI 서비스 라이브 연결 기능을 제어합니다. [타일 또는 시각적 기체에서 데이터를 내보내는](../visuals/power-bi-visualization-export-data.md) 방법에 대해 자세히 알아보세요.

>[!NOTE]
> Excel로 내보내기 설정이 도입되기 전에 이 설정은 Excel 파일로 데이터 내보내기도 제어했습니다. 자세한 내용은 [Excel로 내보내기 아래의 참고](#export-to-excel)를 참조하세요.

![데이터 내보내기 설정](media/service-admin-portal/powerbi-admin-portal-export-data-setting.png)

다음 이미지는 타일에서 데이터를 내보내는 옵션을 보여 줍니다.

![타일에서 데이터 내보내기](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> **데이터 내보내기**를 사용하지 않도록 설정하면 사용자는 Power BI 서비스 라이브 연결과 함께 [Excel에서 분석](../collaborate-share/service-analyze-in-excel.md) 기능을 사용할 수 없습니다.

### <a name="export-to-excel"></a>Excel로 내보내기

조직의 사용자가 시각화에서 Excel 파일로 데이터를 내보낼 수 있습니다.

![Excel로 내보내기 설정](media/service-admin-portal/powerbi-admin-portal-export-to-excel-setting.png)

>[!IMPORTANT]
> Excel로 내보내기 설정이 도입되기 전에 Excel 파일로 내보내기는 데이터 내보내기 설정에 의해 제어되었습니다. 따라서 Excel로 내보내기 설정이 도입되기 전에 존재한 테넌트에서는 테넌트 관리자가 Excel로 내보내기 설정을 처음 볼 때 ‘적용되지 않은 변경 내용’이 있음을 알게 됩니다. 새 설정을 적용하려면 이러한 변경 내용을 적용해야 합니다. 그렇지 않으면 Excel 파일로 내보내기는 데이터 내보내기 설정에 의해 계속 제어됩니다.

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>PowerPoint 프레젠테이션 또는 PDF 문서로 보고서 내보내기

조직의 사용자가 Power BI 보고서를 PowerPoint 파일 또는 PDF 문서로 내보낼 수 있습니다. [자세히 알아보기](../consumer/end-user-powerpoint.md)

다음 이미지는 **보고서를 PowerPoint 프레젠테이션 또는 PDF 문서로 내보내기** 설정을 사용하도록 설정한 경우 보고서의 **파일** 메뉴를 보여줍니다.

![보고서를 PowerPoint 프레젠테이션으로 내보내기](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>대시보드 및 보고서 인쇄

조직의 사용자는 대시보드 및 보고서를 인쇄할 수 있습니다. [자세히 알아보기](../consumer/end-user-print.md)

다음 이미지는 대시보드를 인쇄하는 옵션을 보여 줍니다.

![대시보드 인쇄](media/service-admin-portal/powerbi-admin-print-dashboard.png)

다음 이미지는 **대시보드 및 보고서 인쇄** 설정을 사용할 수 있을 때 보고서의 **파일** 메뉴를 보여 줍니다.

![보고서 인쇄](media/service-admin-portal/powerbi-admin-print-report.png)

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>외부 게스트 사용자가 조직의 콘텐츠를 편집 및 관리하도록 허용

Azure AD B2B 게스트 사용자는 조직의 콘텐츠를 편집하고 관리할 수 있습니다. [자세히 알아보기](service-admin-azure-ad-b2b.md)

다음 이미지는 외부 게스트 사용자가 조직의 콘텐츠를 편집 및 관리하도록 허용하는 옵션을 보여줍니다.

![외부 게스트 사용자가 조직의 콘텐츠를 편집 및 관리하도록 허용](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

관리 포털에서 조직으로 외부 사용자를 초대할 권한을 갖는 사용자를 제어할 수 있습니다. 자세한 내용은 이 문서의 [외부 사용자와 콘텐츠 공유](#export-and-sharing-settings)를 참조하세요.

### <a name="email-subscriptions"></a>메일 구독
조직의 사용자가 메일 구독을 만들 수 있습니다. [구독](../collaborate-share/service-publish-to-web.md)에 대해 자세히 알아보세요.

![메일 구독 사용](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

### <a name="featured-content"></a>주요 콘텐츠

조직의 일부 또는 모든 보고서 작성자가 Power BI 홈의 추천 섹션에서 콘텐츠를 추천하도록 허용합니다. 새 사용자는 Power BI 홈페이지의 맨 위에서 추천 콘텐츠를 볼 수 있습니다. 사용자가 **즐겨찾기**, **자주 사용하는 항목** 및 **최근 항목**을 추가하면 추천 콘텐츠가 홈페이지 아래쪽으로 이동합니다. 

먼저 작은 프로모터 세트로 시작하는 것이 좋습니다. 전체 조직이 홈에서 콘텐츠를 추천하도록 허용하면 모든 승격된 콘텐츠를 추적하기가 어려울 수 있습니다. 

추천 콘텐츠를 사용하도록 설정한 후 관리 포털에서 관리할 수도 있습니다. 도메인에서 추천 콘텐츠를 제어하는 방법에 대한 자세한 내용은 이 문서의 [추천 콘텐츠 관리](#manage-featured-content)를 참조하세요.

## <a name="content-pack-and-app-settings"></a>콘텐츠 팩 및 앱 설정

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>콘텐츠 팩과 앱을 전체 조직에 게시

관리자는 이 설정을 사용하여, 콘텐츠 팩과 앱을 특정 그룹이 아닌 전체 조직에 게시할 수 있는 사용자를 결정합니다. [앱 게시](../collaborate-share/service-create-distribute-apps.md)에 대해 자세히 알아보세요.

다음 이미지는 콘텐츠 팩을 만들 때 **내 전체 조직** 옵션을 보여 줍니다.

![조직에 콘텐츠 팩 게시](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>템플릿 앱 및 조직 콘텐츠 팩 만들기

조직의 사용자는 Power BI Desktop에서 하나의 데이터 원본을 기반으로 하는 데이터 세트를 사용하는 템플릿 앱 및 조직 콘텐츠 팩을 만들 수 있습니다. [템플릿 앱](../connect-data/service-template-apps-create.md)에 대해 자세히 알아보세요.

### <a name="push-apps-to-end-users"></a>최종 사용자에게 앱 푸시

보고서 작성자는 [AppSource](https://appsource.microsoft.com)에서 설치하지 않고 최종 사용자와 직접 앱을 공유할 수 있습니다. [최종 사용자를 위해 앱을 자동으로 설치](../collaborate-share/service-create-distribute-apps.md#automatically-install-apps-for-end-users)에 대해 자세히 알아보세요.

## <a name="integration-settings"></a>통합 설정

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>온-프레미스 데이터 세트를 통해 Excel에서 분석 사용

조직의 사용자는 Excel을 사용하여 온-프레미스 Power BI 데이터 세트를 보고 상호 작용할 수 있습니다. [자세히 알아보기](../collaborate-share/service-analyze-in-excel.md)

> [!NOTE]
> **데이터 내보내기**를 사용하지 않도록 설정하면 사용자는 **Excel에서 분석** 기능을 사용할 수 없습니다.

### <a name="use-arcgis-maps-for-power-bi"></a>ArcGIS Maps for Power BI 사용

조직의 사용자는 Esri에서 제공하는 ArcGIS Maps for Power BI 시각화를 사용할 수 있습니다. [자세히 알아보기](../visuals/power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Power BI(미리 보기)용 전역 검색 사용

조직의 사용자는 Azure Search에 의존하는 외부 검색 기능을 사용할 수 있습니다.

## <a name="featured-tables-settings"></a>주요 테이블 설정

**테넌트 설정** 아래의 **주요 테이블에 대한 연결 허용** 테넌트 설정을 사용하면 Power BI 관리자가 조직에서 Excel 데이터 형식 갤러리의 주요 테이블을 사용할 수 있는 사용자를 제어할 수 있습니다. 

:::image type="content" source="media/service-admin-portal/admin-allow-connections-featured-tables.png" alt-text="주요 테이블에 대한 모든 연결":::

**데이터 내보내기** 테넌트 설정이 **사용 안 함**으로 설정되면 주요 테이블에 대한 연결도 사용할 수 없습니다.

[Excel의 Power BI 주요 테이블](../collaborate-share/service-excel-featured-tables.md)에 대해 자세히 알아보세요.

## <a name="power-bi-visuals-settings"></a>Power BI 시각적 개체 설정

### <a name="add-and-use-power-bi-visuals"></a>Power BI 시각적 개체 추가 및 사용

조직의 사용자는 Power BI 시각적 개체를 조작하고 공유할 수 있습니다. [자세히 알아보기](../developer/visuals/power-bi-custom-visuals.md)

> [!NOTE]
> 이 설정은 전체 조직에 적용하거나 특정 그룹으로 제한할 수 있습니다.

Power BI Desktop(3월 19일 릴리스부터 시작)은 **그룹 정책**을 사용하여 조직의 배포된 컴퓨터에서 Power BI 시각화 개체를 사용하지 않도록 설정할 수 있습니다.

<table>
<tr><th>특성</th><th>값</th>
</tr>
<td>key</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableCustomVisuals</td>
</tr>
</table>

1의 값(십진수)을 사용하면 Power BI에서 Power BI 시각적 개체를 사용할 수 있습니다(기본값).

0의 값(십진수)을 사용하면 Power BI에서 Power BI 시각적 개체를 사용할 수 없습니다.

### <a name="allow-only-certified-visuals"></a>인증된 시각적 개체만 허용

“Power BI 시각적 개체 추가 및 사용” 설정으로 표시된 Power BI 시각적 개체를 추가하고 사용할 수 있는 권한이 부여된 조직의 사용자는 [인증된 Power BI 시각적 개체](https://go.microsoft.com/fwlink/?linkid=2002010)만 사용할 수 있습니다(인증되지 않은 시각적 개체는 차단되고 사용 시 오류 메시지가 표시됨). 


Power BI Desktop(3월 19일 릴리스부터 시작)은 **그룹 정책**을 사용하여 조직의 배포된 컴퓨터에서 인증되지 않은 Power BI 시각화 개체를 사용하지 않도록 설정할 수 있습니다.

<table>
<tr><th>특성</th><th>값</th>
</tr>
<td>key</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableUncertifiedVisuals</td>
</tr>
</table>

1의 값(십진수)을 사용하면 Power BI에서 인증되지 않은 Power BI 시각적 개체를 사용할 수 있습니다(기본값).

0의 값(십진수)은 Power BI에서 인증되지 않은 Power BI 시각적 개체를 비활성화합니다(이 옵션은 [인증된 Power BI 시각적 개체](https://go.microsoft.com/fwlink/?linkid=2002010)만 사용할 수 있음).

## <a name="r-visuals-settings"></a>R 시각적 개체 설정

### <a name="interact-with-and-share-r-visuals"></a>R 시각적 개체와 상호 작용 및 공유

조직의 사용자는 R 스크립트를 사용하여 만든 시각적 개체와 상호 작용하고 공유할 수 있습니다. [자세히 알아보기](../visuals/service-r-visuals.md)

> [!NOTE]
> 이 설정은 전체 조직에 적용되며 특정 그룹에 제한될 수 없습니다.

## <a name="audit-and-usage-settings"></a>감사 및 사용 설정

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>내부 활동 감사 및 규정 준수를 위해 감사 로그 만들기

조직의 사용자는 감사를 사용하여 조직의 다른 사용자가 Power BI에서 수행한 작업을 모니터링할 수 있습니다. [자세히 알아보기](service-admin-auditing.md)

감사 로그 항목을 기록하려면 이 설정이 사용하도록 설정되어야 합니다. 감사를 설정하고 나서 감사 데이터를 확인할 때까지 최대 48시간이 지연될 수 있습니다. 데이터가 즉시 표시되지 않으면 나중에 감사 로그를 확인합니다. 감사 로그를 볼 수 있는 권한을 부여받고 나서 로그에 액세스할 때까지 유사하게 지연될 수 있습니다.

> [!NOTE]
> 이 설정은 전체 조직에 적용되며 특정 그룹에 제한될 수 없습니다.

### <a name="usage-metrics-for-content-creators"></a>콘텐츠 작성자용 사용량 메트릭

조직의 사용자가 자신이 만든 보고서 및 대시보드에 대한 사용량 메트릭을 확인할 수 있습니다. [자세히 알아보기](../collaborate-share/service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>콘텐츠 작성자에 대한 사용량 메트릭의 사용자별 데이터

콘텐츠 사용자에 대한 사용량 메트릭에는 콘텐츠에 액세스하는 사용자의 표시 이름 및 메일 주소가 노출됩니다. [자세히 알아보기](../collaborate-share/service-usage-metrics.md)

사용자별 데이터는 기본적으로 사용량 메트릭에 사용되도록 설정되고, 콘텐츠 생성자 계정 정보는 메트릭 보고서에 포함됩니다. 모든 사용자에 대해 이 정보를 수집하지 않으려는 경우 지정된 보안 그룹 또는 전체 조직에 기능을 사용하지 않도록 설정할 수 있습니다. 그러면 제외된 사용자에 대한 계정 정보는 *이름 없음*으로 보고서에 표시됩니다.

## <a name="dashboard-settings"></a>대시보드 설정

### <a name="data-classification-for-dashboards"></a>대시보드에 대한 데이터 분류

조직의 사용자는 대시보드 보안 수준을 나타내는 분류로 대시보드를 태그할 수 있습니다. [자세히 알아보기](../create-reports/service-data-classification.md)

> [!NOTE]
> 이 설정은 전체 조직에 적용되며 특정 그룹에 제한될 수 없습니다.

## <a name="developer-settings"></a>개발자 설정

### <a name="embed-content-in-apps"></a>앱에 콘텐츠 포함

조직 내 사용자는 Power BI 대시보드 및 보고서를 SaaS(Software as a Service) 애플리케이션에 포함할 수 있습니다. 이 설정을 사용하지 않도록 설정하면 사용자는 REST API를 사용하여 Power BI 콘텐츠를 해당 애플리케이션에 포함할 수 없게 됩니다. [자세히 알아보기](../developer/embedded/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>서비스 주체가 Power BI API를 사용하도록 허용

Azure AD(Azure Active Directory)에 등록된 웹앱은 할당된 서비스 주체를 사용하여 로그인한 사용자 없이 Power BI API에 액세스합니다. 앱이 서비스 주체 인증을 사용하도록 하려면 해당 서비스 주체가 허용된 보안 그룹에 포함되어 있어야 합니다. [자세히 알아보기](../developer/embedded/embed-service-principal.md)

> [!NOTE]
> 서비스 주체는 해당 보안 그룹의 모든 Power BI 테넌트 설정에 대한 사용 권한을 상속받습니다. 사용 권한을 제한하려면 서비스 주체에 대한 전용 보안 그룹을 만들고, 사용하도록 설정된 해당 Power BI 설정에 대한 '특정 보안 그룹 제외' 목록에 이를 추가합니다.

## <a name="dataflow-settings"></a>데이터 흐름 설정

### <a name="create-and-use-dataflows"></a>데이터 흐름 만들기 및 사용

조직의 사용자가 데이터 흐름을 만들고 사용할 수 있습니다. 데이터 흐름 개요는 [Power BI의 셀프 서비스 데이터 준비](../transform-model/service-dataflows-overview.md)를 참조하세요. 프리미엄 용량에 대한 데이터 흐름을 사용하려면 [워크로드 구성](service-admin-premium-workloads.md)을 참조하세요.

> [!NOTE]
> 이 설정은 전체 조직에 적용되며 특정 그룹에 제한될 수 없습니다.

## <a name="template-apps-settings"></a>템플릿 앱 설정

세 가지 설정은 템플릿 앱을 게시하거나 설치하는 데 사용되는 템플릿 앱 기능을 제어합니다.

![Power BI 관리 포털 템플릿 앱 설정](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>템플릿 앱 게시

조직의 사용자가 템플릿 앱 작업 영역을 만들 수 있습니다. [AppSource](https://appsource.microsoft.com) 또는 다른 배포 메서드를 통해 템플릿 앱을 게시하거나 조직 외부의 클라이언트에 배포할 수 있는 사용자를 제어합니다.

![Power BI 관리 포털, 템플릿 앱 설정 만들기](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>AppSource에 나열된 템플릿 앱 설치

조직의 사용자는 [AppSource](https://appsource.microsoft.com)의 템플릿 앱**만** 다운로드하고 설치할 수 있습니다. AppSource에서 템플릿 앱을 설치할 수 있는 특정 사용자 또는 보안 그룹을 제어합니다.

![Power BI 관리 포털, 템플릿 앱 설정 설치](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>AppSource에 나열되지 않은 템플릿 앱 설치

조직에서 **[AppSource](https://appsource.microsoft.com)에 나열되지 않은** 템플릿 앱을 다운로드하고 설치할 수 있는 사용자를 제어합니다.

![Power BI 관리 포털, 템플릿 앱 설정 설치](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>용량 설정

### <a name="power-bi-premium"></a>Power BI Premium

**Power BI Premium** 탭에서는 조직용으로 구매한 Power BI Premium 용량(EM 또는 P SKU)을 관리할 수 있습니다. 조직 내 모든 사용자가 **Power BI Premium** 탭을 볼 수 있으나, ‘용량 관리자’ 또는 할당 권한이 있는 사용자로 할당된 경우에만 탭 내 콘텐츠를 볼 수 있습니다. 사용자에게 권한이 없으면 다음과 같은 메시지가 나타납니다.

![Premium 설정 액세스 권한 없음](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

**Power BI Embedded** 탭에서는 고객용으로 구매한 Power BI Embedded(A SKU) 용량을 확인할 수 있습니다. Azure에서만 A SKU를 구매할 수 있으므로 **Azure Portal**에서 [Azure의 포함된 용량을 관리](../developer/embedded/azure-pbie-create-capacity.md)할 수 있습니다.

Power BI Embedded(A SKU) 설정을 관리하는 방법은 [Azure의 Power BI Embedded란?](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)을 참조하세요.

## <a name="embed-codes"></a>embed 태그

관리자는 보고서를 공개적으로 공유할 테넌트에 대해 생성된 embed 태그를 볼 수 있습니다. 코드를 취소하거나 삭제할 수도 있습니다. [자세히 알아보기](../collaborate-share/service-publish-to-web.md)

![Power BI 관리 포털 내의 embed 태그](media/service-admin-portal/embed-codes.png)

 ## <a name=""></a><a name="organizational-visuals">조직의 시각적 개체</a> 

**조직 시각적 개체** 탭에서는 조직 내부에서 Power BI 시각적 개체를 배포 및 관리할 수 있습니다. 조직 시각적 개체를 사용하면 조직에서 소유 시각적 개체를 쉽게 배포할 수 있으므로 이후 보고서 작성자가 Power BI Desktop에서 이를 검색하고 보고서로 가져올 수 있습니다. [자세히 알아보기](../developer/visuals/power-bi-custom-visuals-organization.md)

> [!WARNING]
> 사용자 지정 시각적 개체에는 보안 또는 개인 정보 관련 위험이 있는 코드가 포함될 수 있습니다. 조직의 리포지토리로 배포하기 전에 사용자 지정 시각적 개체의 작성자와 원본을 신뢰할 수 있는지 확인해야 합니다.

다음 이미지는 조직의 리포지토리에 현재 배포된 모든 Power BI 시각적 개체를 보여 줍니다.

![조직 관리의 시각적 개체](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>새 사용자 지정 시각적 개체 추가

목록에 새 사용자 지정 시각적 개체를 추가하려면 다음 단계를 수행합니다. 

1. 오른쪽 창에서 **사용자 지정 시각적 개체 추가**를 선택합니다.

    ![Power BI 시각적 개체 양식](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

1. **사용자 지정 시각적 개체 추가** 양식을 채웁니다.

    * **.pbiviz 파일 선택**(필수): 업로드할 사용자 지정 시각적 개체 파일을 선택합니다. 버전이 지정된 API Power BI 시각적 개체만 지원됩니다(여기 참조).

    사용자 지정 시각적 개체를 업로드하기 전에 보안 및 개인 정보에 대해 사용자 지정 시각적 개체를 검토하여 조직의 표준에 적합한지 확인해야 합니다.

    * **사용자 지정 시각적 개체 이름 지정**(필수): Power BI Desktop 사용자가 쉽게 이해할 수 있도록 시각적 개체에 간단한 제목을 지정합니다.

    * **아이콘**: Power BI Desktop UI에 표시되는 아이콘 파일입니다.

    * **설명**: 사용자에게 더 많은 컨텍스트와 교육을 제공하기 위한 시각적 개체에 대한 간단한 설명입니다.

1. **적용**을 선택하여 업로드 요청을 시작합니다. 성공하면 목록에 새 항목이 표시됩니다. 실패하면 해당 오류 메시지가 표시됩니다.

### <a name="delete-a-custom-visual-from-the-list"></a>목록에서 사용자 지정 시각적 개체 삭제

시각적 개체를 영구적으로 삭제하려면 리포지토리에서 시각적 개체의 휴지통 아이콘을 선택합니다.

> [!IMPORTANT]
> 삭제는 되돌릴 수 없습니다. 삭제되면 시각적 개체는 기존 보고서에서 렌더링을 즉시 중지합니다. 동일한 시각적 개체를 다시 업로드하더라도 삭제된 이전 시각적 개체를 대체하지 않습니다. 그러나 사용자는 새 시각적 개체를 다시 가져오고 해당 보고서에 있는 인스턴스를 대체할 수 있습니다.

### <a name="disable-a-custom-visual-in-the-list"></a>목록에서 사용자 지정 시각적 개체 사용 안 함

조직의 저장소에서 시각적 개체를 사용하지 않으려면 기어 아이콘을 선택합니다. **액세스** 섹션에서 사용자 지정 시각적 개체를 사용 안 함으로 설정합니다.

시각적 개체를 사용하지 않도록 설정하면 시각적 개체가 기존 보고서에 렌더링되지 않고 아래와 같은 오류 메시지가 표시됩니다.

*이 사용자 지정 시각적 개체는 더 이상 사용할 수 없습니다. 자세한 내용은 관리자에게 문의하세요.*

그러나 책갈피로 지정된 시각적 개체는 여전히 작동합니다.

업데이트 후 또는 관리자가 변경한 후 Power BI Desktop 사용자는 애플리케이션을 다시 시작하거나 Power BI 서비스에서 브라우저를 새로 고쳐 업데이트를 확인해야 합니다.

### <a name="update-a-visual"></a>시각적 개체 업데이트

조직 저장소에서 시각적 개체를 업데이트하려면 기어 아이콘을 선택합니다. 시각적 개체의 새 버전을 찾아보고 업로드합니다.

시각적 개체 ID가 변경되지 않았는지 확인합니다. 새 파일은 조직 전체의 모든 보고서에 대해 이전 파일을 대체합니다. 그러나 시각적 개체의 새 버전이 시각적 개체의 이전 버전에 대한 사용이나 데이터 구조를 중단하는 경우에는 이전 버전을 바꾸지 마세요. 대신에 시각적 개체의 새 버전에 대한 새 목록을 만들어야 합니다. 예를 들어 새 버전 번호(버전 X.X)를 새 나열된 시각적 개체의 제목에 추가합니다. 이렇게 하면 업데이트된 버전 번호를 가진 동일한 시각적 개체가 되므로 기존 보고서가 해당 기능을 중단하지 않습니다. 다시 한번 시각적 개체 ID가 변경되지 않았는지 확인합니다. 그러면 다음에 사용자가 Power BI Desktop에서 조직의 리포지토리에 들어갈 때 새 버전을 가져올 수 있으며, 보고서에 있는 현재 버전을 바꾸라는 메시지가 표시됩니다.

자세한 내용은 [조직의 Power BI 시각적 개체에 대한 자주 묻는 질문](../developer/visuals/power-bi-custom-visuals-faq.md#organizational-power-bi-visuals)을 참조하세요.

## <a name=""></a><a name="dataflowStorage">데이터 흐름 스토리지(미리 보기)</a>

기본적으로 Power BI에 사용되는 데이터는 Power BI에서 제공하는 내부 스토리지에 저장됩니다. 데이터 흐름 및 ADLS Gen2(Azure Data Lake Storage Gen2)를 통합하면 조직의 Azure Data Lake Storage Gen2 계정에 데이터 흐름을 저장할 수 있습니다. 자세한 내용은 [데이터 흐름 및 Azure Data Lake 통합(미리 보기)](../transform-model/service-dataflows-azure-data-lake-integration.md)을 참조하세요.

## <a name="workspaces"></a>작업 영역

관리자는 테넌트에 있는 작업 영역을 볼 수 있습니다. 작업 영역 목록을 정렬 및 필터링하고 각 작업 영역에 대한 세부 정보를 표시할 수 있습니다. 테이블 열은 작업 영역에 대해 [Power BI 관리자 Rest API](/rest/api/power-bi/admin)에서 반환된 속성에 해당합니다. 개인 작업 영역은 **개인 그룹** 형식, 클래식 작업 영역은 **그룹** 형식, 새 작업 영역 환경은 **작업 영역** 형식입니다. 자세한 내용은 [새 작업 영역에서 작업 구성](../collaborate-share/service-new-workspaces.md)을 참조하세요.

관리자는 관리 포털 또는 PowerShell Cmdlet을 사용하여 작업 영역을 관리하고 복구할 수도 있습니다. 

![작업 영역 목록](media/service-admin-portal/workspaces-list.png)

**작업 영역** 탭에 각 작업 영역의 *상태*가 표시됩니다. 다음 표에서 각 상태의 자세한 의미를 확인할 수 있습니다.

|주  |설명  |
|---------|---------|
| 활성 | 일반 작업 영역입니다. 사용량이나 콘텐츠에 대한 정보는 알 수 없으며, 작업 영역 자체가 ‘일반’ 작업 영역이라는 사실만 알 수 있습니다. |
| 분리됨 | 관리 사용자가 없는 작업 영역입니다. |
| 삭제됨 | 삭제된 작업 영역입니다. 최대 90일 동안, 필요한 경우 작업 영역을 복원하기에 충분한 메타데이터가 유지됩니다. |
| 제거 중 | 현재 삭제가 진행 중이지만 아직 완전히 삭제되지 않은 작업 영역입니다. 사용자는 ‘제거 중’으로 항목을 이동하고 궁극적으로 ‘삭제됨’으로 이동하여 작업 영역을 삭제할 수 있습니다. |

## <a name="custom-branding"></a>사용자 지정 브랜딩

관리자는 전체 조직에 대한 Power BI의 모양을 사용자 지정할 수 있습니다. 현재 세 가지 기본 옵션이 있습니다.

![사용자 지정 브랜딩 옵션](media/service-admin-portal/power-bi-custom-branding.png)

* **로고 업로드**: 최상의 결과를 위해 200 x 30 픽셀 이상의 .png(10KB 이하)로 저장된 로고를 업로드합니다.

* **커버 이미지 업로드**: 최상의 결과를 위해 1920 x 160 픽셀 이상의 .jpg 또는 .png(1MB 이하)로 저장된 커버 이미지를 업로드합니다.

* **색 테마 선택**: 16진수 #, RGB, 값 또는 제공된 팔레트를 기준으로 테마를 선택할 수 있습니다.


자세한 내용은 [조직에 대한 사용자 지정 브랜딩](https://aka.ms/orgBranding)을 참조하세요.

![작업 영역 목록](media/service-admin-portal/workspaces-list.png)

## <a name="manage-featured-content"></a>추천 콘텐츠 관리

테넌트 관리자는 조직 전체에서 Power BI 홈의 추천 섹션으로 승격된 모든 보고서, 대시보드 및 앱을 관리할 수 있습니다.

- 관리 포털에서 **추천 콘텐츠**를 선택합니다.

여기에서 콘텐츠를 추천하는 사용자, 추천된 시간 및 모든 관련 메타데이터의 개요를 볼 수 있습니다. 의심스러운 항목이 있거나 추천 섹션을 정리하려는 경우 필요에 따라 승격된 콘텐츠를 삭제할 수 있습니다.

추천 콘텐츠 사용에 대한 내용은 이 문서에서 [추천 콘텐츠](#featured-content)를 참조하세요.

## <a name="next-steps"></a>다음 단계

[조직에서 Power BI 관리](service-admin-administering-power-bi-in-your-organization.md)  
[Power BI 관리자 역할 이해](service-admin-role.md)  
[조직에서 Power BI 감사](service-admin-auditing.md)  

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
