---
title: Power BI 관리 포털
description: 관리 포털에서 Power BI에 대한 조직 차원의 설정을 구성할 수 있습니다. 사용 메트릭을 확인하고, 테넌트 설정을 구성하고, 용량을 사용하고, 작업 영역, 조직 시각적 개체 및 주요 콘텐츠를 볼 수 있습니다.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 10/22/2020
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 9cbb6bb03d9add4324c3fc57a6426435850a001c
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96578179"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>관리 포털에서 Power BI 관리

관리 포털을 통해 조직의 Power BI 설정을 관리할 수 있습니다. 포털에는 사용 현황 메트릭, Microsoft 365 관리 센터에 대한 액세스 및 테넌트 설정과 같은 항목이 포함되어 있습니다.

전역 관리자 및 Power BI 서비스 관리자 역할이 있는 사용자가 전체 관리 포털에 액세스할 수 있습니다. 이러한 역할 중 하나를 할당받지 않은 경우에는 포털에 **용량 설정** 만 표시됩니다. Power BI 서비스 관리자 역할에 대한 자세한 내용은 [Power BI 관리자 역할 이해](service-admin-role.md)를 참조하세요.

## <a name="how-to-get-to-the-admin-portal"></a>관리 포털에 도달하는 방법

Power BI 관리 포털에 액세스하려면 전역 관리자 또는 Power BI 서비스 관리자여야 합니다. Power BI 서비스 관리자 역할에 대한 자세한 내용은 [Power BI 관리자 역할 이해](service-admin-role.md)를 참조하세요. Power BI 관리 포털로 이동하려면 다음 단계를 수행합니다.

1. 관리자 계정 자격 증명을 사용하여 [Power BI](https://app.powerbi.com)에 로그인합니다.

1. 페이지 헤더에서 **설정** > **관리 포털** 을 선택합니다.

    ![관리 포털에 대한 설정](media/service-admin-portal/powerbi-admin-settings.png)

관리 포털에는 여러 섹션이 있습니다. 이 문서의 나머지 부분에서는 이러한 각 섹션에 대한 정보를 제공합니다.

![관리 포털 탐색](media/service-admin-portal/powerbi-admin-landing-page.png)

* [사용량 메트릭](#usage-metrics)
* [사용자](#users)
* [감사 로그](#audit-logs)
* [테넌트 설정](#tenant-settings)
* [용량 설정](#capacity-settings)
* [embed 태그](#embed-codes)
* [조직의 시각적 개체](organizational-visuals.md#organizational-visuals)
* [Azure 연결(미리 보기)](#azure-connections-preview)
* [작업 영역](#workspaces)
* [사용자 지정 브랜딩](#custom-branding)
* [보호 메트릭](#protection-metrics)
* [추천 콘텐츠](#featured-content)

## <a name="usage-metrics"></a>사용량 메트릭

**사용 현황 메트릭** 을 통해 조직의 Power BI 사용 현황을 모니터링할 수 있습니다. 또한 Power BI에서 조직 내 가장 활동적인 사용자 및 그룹을 보여 줍니다.

> [!NOTE]
> 대시보드에 처음 액세스할 때 또는 대시보드를 오랫동안 보지 않았다가 다시 방문한 후 대시보드를 로드하는 동안 로드 중 화면이 표시될 수 있습니다.

대시보드가 로드된 후 타일 섹션 두 개가 표시됩니다. 첫 번째 섹션은 개별 사용자에 대한 사용 현황 데이터를 포함하고 있으며 두 번째 섹션은 그룹에 대해 유사한 정보를 포함하고 있습니다.

다음은 각 타일에 표시되는 내용에 대한 요약입니다.

* 사용자 작업 영역의 모든 대시보드, 보고서 및 데이터 세트에 대한 고유한 개수입니다.
  
    ![대시보드, 보고서, 데이터 세트에 대한 고유한 개수](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)


* 액세스할 수 있는 사용자 수별로 가장 많이 사용한 대시보드입니다. 예: 세 명의 사용자와 공유하는 대시보드가 있습니다. 또한 두 명의 다른 사용자가 연결된 콘텐츠 팩에 대시보드를 추가했습니다. 대시보드의 수는 6(1+3+2)입니다.
  
    ![가장 많이 사용한 대시보드](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* 사용자가 연결한 가장 인기 있는 콘텐츠입니다. 콘텐츠는 SaaS 콘텐츠 팩, 조직 콘텐츠 팩, 파일 또는 데이터베이스와 같은 데이터 가져오기 프로세스를 통해 사용자가 연결할 수 있는 모든 항목입니다.

  
    ![가장 많이 사용한 패키지](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* 직접 만든 대시보드 및 공유하는 대시보드를 모두 포함하여 가지고 있는 대시보드 수를 기반으로 하는 최상위 사용자의 뷰입니다.
  
    ![최상위 사용자 - 대시보드](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* 가지고 있는 보고서 수를 기반으로 하는 최상위 사용자의 뷰입니다.
  
    ![최상위 사용자 - 보고서](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

두 번째 섹션은 동일한 유형의 정보를 보여 주지만 그룹을 기반으로 합니다. 이 섹션에서는 조직에서 가장 활동적인 그룹 및 해당 그룹이 사용 중인 콘텐츠의 종류를 확인할 수 있습니다.

이 정보를 사용하여 조직 전체에서 Power BI를 사용하는 방법에 대한 실질적인 정보를 얻을 수 있습니다.

## <a name="control-usage-metrics"></a>사용량 메트릭 제어

사용량 메트릭 보고서는 Power BI 또는 전역 관리자가 켜거나 끌 수 있는 기능입니다. 관리자는 사용량 메트릭에 액세스할 수 있는 사용자를 세부적으로 제어할 수 있습니다. 기본적으로 조직의 모든 사용자에 대해 **켬** 으로 설정되어 있습니다.

관리자는 콘텐츠 작성자가 사용량 메트릭에서 사용자별 데이터를 볼 수 있는지 여부도 설정할 수 있습니다. 

보고서에 대한 자세한 내용은 [Power BI 대시보드 및 보고서의 사용량 메트릭 모니터링](../collaborate-share/service-usage-metrics.md)을 참조하세요.

### <a name="usage-metrics-for-content-creators"></a>콘텐츠 작성자용 사용량 메트릭

1. 관리 포털에서 **테넌트 설정** > **감사 및 사용 현황 설정** > **콘텐츠 작성자의 사용 현황 메트릭** 을 선택합니다.

    ![관리 포털 테넌트 설정 사용 메트릭](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. 사용량 메트릭을 활성화(또는 비활성화)하고 **적용** 을 클릭합니다.

    ![설정된 사용 메트릭](../collaborate-share/media/service-usage-metrics/power-bi-tenant-settings-updated.png)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>콘텐츠 작성자에 대한 사용량 메트릭의 사용자별 데이터

기본적으로 사용자별 데이터는 사용 현황 메트릭에 사용되도록 설정되고, 계정 정보는 메트릭 보고서에 포함됩니다. 일부 또는 모든 사용자에게 계정 정보를 포함하지 않으려는 경우 지정된 보안 그룹 또는 전체 조직에 기능을 사용하지 않도록 설정합니다. 그러면 계정 정보는 *이름 없음* 으로 보고서에 표시됩니다.

![사용자별 사용량 현황 데이터](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>모든 기존 사용량 메트릭 콘텐츠 삭제

조직 전체의 사용량 메트릭을 비활성화할 때, 관리자는 다음 옵션 중 하나 또는 둘 모두를 선택할 수 있습니다.

- **기존 사용량 메트릭 콘텐츠 모두 삭제** 옵션을 사용하여 사용량 메트릭 보고서 및 데이터 세트를 사용하여 빌드한 기존 보고서 및 대시보드 타일을 모두 삭제합니다. 이 옵션은 이미 사용량 메트릭을 사용 중일 수도 있는 조직의 모든 사용자에게서 사용량 메트릭 데이터에 대한 모든 액세스를 제거합니다.
- **현재 사용량 메트릭 콘텐츠의 모든 기존 사용자별 데이터 삭제** 는 이미 사용량 메트릭을 사용 중인 사용자를 포함하여 조직의 모든 사용자에게서 사용자별 데이터에 대한 액세스 권한을 모두 제거합니다.

기존 사용량 메트릭과 사용자별 메트릭 콘텐츠의 삭제는 되돌릴 수 없으므로 조심해야 합니다.

## <a name="users"></a>사용자

Microsoft 365 관리 센터에서 Power BI 사용자, 그룹 및 관리자를 관리합니다. **사용자** 탭은 관리 센터에 대한 링크를 제공합니다.

![Microsoft 365 관리 센터로 이동](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>감사 로그

Office 365 보안 및 준수 센터에서 Power BI 감사 로그를 관리합니다. **감사 로그** 탭은 보안 및 준수 센터에 대한 링크를 제공합니다. 자세한 내용은 [Power BI에서 사용자 활동 추적](service-admin-auditing.md)을 참조하세요.

감사 로그를 사용하려면 [**내부 활동 감사 및 규정 준수를 위해 감사 로그 만들기**](#create-audit-logs-for-internal-activity-auditing-and-compliance) 설정이 사용하도록 설정되어 있는지 확인합니다.

## <a name="tenant-settings"></a>테넌트 설정

**테넌트 설정** 에서는 조직에서 사용할 수 있는 기능에 대한 세분화된 제어를 제공합니다. 중요한 데이터에 대한 우려가 있는 경우 일부 기능은 사용자의 조직에 적합하지 않을 수 있거나 특정 기능을 특정 그룹만 사용할 수 있도록 할 수 있습니다.

> [!NOTE]
> Power BI 사용자 인터페이스에서 기능의 가용성을 제어하는 테넌트 설정은 거버넌스 정책을 수립하는 데 도움이 될 수 있지만 보안 조치는 아닙니다. 예를 들어 **데이터 내보내기** 설정은 데이터 세트에 대한 Power BI 사용자의 권한을 제한하지 않습니다. 데이터 세트에 대한 읽기 권한이 있는 Power BI 사용자에게는 이 데이터 세트를 쿼리할 수 있는 권한이 있으며, Power BI 사용자 인터페이스에서 **데이터 내보내기** 기능을 사용하지 않고 결과를 유지할 수도 있습니다.

다음 섹션에서는 **테넌트 설정** 탭의 설정을 자세히 설명합니다.

> [!NOTE]
> 설정 변경 내용이 조직의 모든 사용자에게 적용되려면 최대 15분이 걸릴 수 있습니다.

많은 설정의 상태는 다음 세 가지 중 하나입니다.

* **전체 조직에서 사용하지 않도록 설정됨**: 조직의 누구도 이 기능을 사용할 수 없습니다.

    ![모두 사용 안 함 설정](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **전체 조직에서 사용하도록 설정됨**: 조직의 모든 사용자가 이 기능을 사용할 수 있습니다.

    ![모두 사용 설정](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **조직 일부에서 사용하도록 설정됨**: 이 기능은 조직의 특정 보안 그룹이 사용할 수 있습니다.

    또한 **특정 사용자 그룹을 제외하고** 전체 조직에 대해 기능을 사용하도록 설정할 수 있습니다.

    ![하위 집합 사용 설정](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    또한 설정을 조합하여 특정 사용자 그룹에만 기능을 사용하도록 설정하고 사용자 그룹에 대해 사용하지 않도록 설정할 수도 있습니다. 이 경우 특정 사용자가 허용되는 그룹에 있더라도 해당 기능에 액세스할 수 없게 됩니다. 사용자에 대한 가장 제한적인 설정이 적용됩니다.

    ![제외 사용 설정](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

다음 몇몇 섹션에서는 다양한 형식의 테넌트 설정 개요를 제공합니다.

## <a name="tenant-wide-new-look-settings"></a>테넌트 차원의 새 디자인 설정

**새 디자인** 옵션을 사용하지 않도록 설정하면 이 조직의 사용자가 Power BI의 새 디자인을 설정하거나 해제할 수 있습니다. **새 디자인** 옵션을 사용하도록 설정하면 이 조직의 *모든* 사용자에게 Power BI 새 디자인의 현대적인 컨트롤이 항상 표시됩니다. 새 디자인을 더 이상 해제할 수 없습니다. 새 디자인 옵션은 기본적으로 사용하도록 설정되어 있습니다.

:::image type="content" source="media/service-admin-portal/admin-portal-new-look-disable.png" alt-text="관리 포털의 새 디자인 사용 안 함 옵션 스크린샷":::

## <a name="help-and-support-settings"></a>도움말 및 지원 설정

### <a name="publish-get-help-information"></a>"도움말 보기" 정보 게시

![도움말 보기 정보 게시](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

관리자는 내부 URL을 지정하여 Power BI 도움말 메뉴 및 라이선스 업그레이드에 대한 링크 대상을 재정의할 수 있습니다. 사용자 지정 URL이 설정된 경우 조직의 사용자는 기본 대상 대신 내부 도움말 및 지원 리소스로 이동합니다. 다음 대상 리소스를 사용자 지정할 수 있습니다.

* **알아보기**. 기본적으로 이 도움말 메뉴 링크는 [모든 Power BI 학습 경로 및 모듈의 목록](/learn/browse/?products=power-bi)을 대상으로 합니다. 대신 이 링크를 내부 학습 리소스에 전달하려면 **학습 설명서** 에 대하여 사용자 지정 URL을 설정하세요.

* **커뮤니티**. 도움말 메뉴에서 사용자를 내부 포럼으로 이동하려면 [Power BI 커뮤니티](https://community.powerbi.com/) 대신 **토론 포럼** 에 대한 사용자 지정 URL을 설정합니다.

* **라이선싱 업그레이드**. Power BI (무료) 라이선스를 사용하는 사용자에게는 서비스를 사용하는 동안 Power BI Pro로 계정을 업그레이드할 기회가 부여될 수 있습니다. **라이선싱 요청** 에 대한 내부 URL을 지정하는 경우 내부 요청 및 구매 흐름으로 사용자를 리디렉션하고 셀프 서비스 구매를 방지합니다. 사용자가 라이선스를 구입하는 것을 방지하고 사용자가 Power BI Pro 평가판을 시작할 수 있도록 허용하는 경우 구입 및 체험 환경을 분리하려면 [사용자가 Power BI Pro를 사용해 볼 수 있도록 허용](#allow-users-to-try-power-bi-pro)을 참조하세요.

* **도움말 보기**. 도움말 메뉴에서 사용자를 내부 지원 센터로 이동하려면 [Power BI 지원](https://powerbi.microsoft.com/support/) 대신 **지원 센터** 에 대한 사용자 지정 URL을 설정합니다.

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>서비스 중단 또는 인시던트에 대한 이메일 알림 받기

이 테넌트가 서비스 중단 또는 인시던트의 영향을 받는 경우 메일 사용이 가능한 보안 그룹이 메일 알림을 받습니다. [서비스 중단 알림](service-interruption-notifications.md)에 대해 자세히 알아보세요.

### <a name="allow-users-to-try-power-bi-pro"></a>사용자가 Power BI Pro를 사용해 볼 수 있도록 허용

![사용자가 Power BI Pro 설정 UI를 사용해 볼 수 있도록 허용](media/service-admin-portal/allow-pro-trial.png)

**사용자가 Power BI Pro를 사용해 볼 수 있도록 허용** 설정은 기본적으로 사용하도록 설정되어 있습니다. 이 설정은 사용자가 Power BI Pro 라이선스를 얻는 방법에 대한 제어를 향상시킵니다. 셀프 서비스 구매를 차단한 시나리오에서는 이 설정을 통해 사용자가 Power BI Pro 평가판을 시작할 수 있습니다. 최종 사용자 환경은 라이선스 설정을 결합하는 방법에 따라 달라집니다. 다음 테이블에서는 Power BI(무료)에서 Power BI Pro로의 업그레이드 환경이 어떻게 다양한 설정 조합의 영향을 받는지 보여 줍니다.

| 셀프 서비스 구매 설정 | 사용자가 Power BI Pro 설정을 사용해 볼 수 있도록 허용 | 최종 사용자 환경 |
| ------ | ------ | ----- |
| 사용 | 사용 안 함 | 사용자가 Pro 라이선스를 구입할 수 있지만 평가판을 시작할 수 없음 |
| 사용 | 사용 | 사용자가 Pro 무료 평가판을 시작하고 유료 라이선스로 업그레이드할 수 있음 |
| 사용 안 함 | 사용 안 함 | IT 관리자에게 라이선스를 요청하라는 메시지가 사용자에게 표시됨 |
| 사용 안 함 | 사용 | 사용자가 Pro 평가판을 시작할 수 있지만 유료 라이선스를 얻으려면 IT 관리자에게 문의해야 함 |

> [!NOTE]
> [도움말 및 지원 설정](#help-and-support-settings)에서 라이선싱 요청에 대한 내부 URL을 추가할 수 있습니다. URL을 설정하면 기본 셀프 서비스 환경이 재정의됩니다. Power BI Pro 라이선스 평가판 등록은 리디렉션되지 않습니다. 위의 테이블에 설명된 시나리오에서 라이선스를 구입할 수 있는 사용자는 내부 URL로 리디렉션됩니다.

자세한 내용은 [셀프 서비스 등록 및 구매 사용 또는 사용 안 함](service-admin-disable-self-service.md)을 참조하세요.

## <a name="workspace-settings"></a>작업 영역 설정

**테넌트 설정** 에서 관리 포털에는 작업 영역을 제어하는 세 개의 섹션이 있습니다.

- [새 작업 영역 환경 만들기](#create-the-new-workspaces)
- [작업 영역에서 데이터 세트 사용](#use-datasets-across-workspaces)
- [클래식 작업 영역 만들기 차단](#block-classic-workspace-creation).

### <a name="create-the-new-workspaces"></a>새 작업 영역 만들기

작업 영역은 사용자가 대시보드, 보고서 및 기타 콘텐츠에 대해 협업할 수 있는 장소입니다. 관리자는 **작업 영역(새 작업 영역 환경) 만들기** 설정을 사용하여 조직에서 작업 영역을 만들 수 있는 사용자를 표시합니다. 관리자는 조직의 모든 사용자가 새 작업 영역 환경 작업 영역을 만들도록 허용 또는 금지할 수 있습니다. 특정 보안 그룹의 구성원으로만 만들기를 제한할 수도 있습니다. [작업 영역](../collaborate-share/service-new-workspaces.md)에 대해 자세히 알아보세요.

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

### <a name="block-classic-workspace-creation"></a>클래식 작업 영역 만들기 차단

관리자는 조직에서 클래식 작업 영역을 만들 수 있는지를 제어할 수 있습니다. 이 설정을 사용하면 작업 영역을 만드는 사용자가 새 작업 영역 환경의 작업 영역만 만들 수 있습니다. 

![클래식 작업 영역 만들기 차단](media/service-admin-portal/power-bi-admin-block-classic-workspaces.png)

이 설정을 사용하면 새로 만든 Office 365 그룹이 Power BI 작업 영역 목록에 표시되지 않습니다. 기존 클래식 작업 영역은 목록에 계속 표시됩니다. 이 설정을 사용하지 않으면 사용자가 속한 모든 Office 365 그룹이 작업 영역 목록에 표시됩니다. [새 작업 영역 환경 작업 영역](../collaborate-share/service-new-workspaces.md)에 관해 자세히 알아보세요.

## <a name="export-and-sharing-settings"></a>내보내기 및 공유 설정

### <a name="allow-azure-active-directory-guest-users-to-access-power-bi"></a>Azure Active Directory 게스트 사용자가 Power BI에 액세스할 수 있도록 허용

이 설정이 사용되면 Azure AD B2B(Azure Active Directory Business-to-Business) 게스트 사용자가 Power BI에 액세스할 수 있습니다. 이 설정이 사용되지 않으면 게스트 사용자가 Power BI에 액세스하려고 할 때 오류가 발생합니다. 전체 조직에서 이 설정이 사용되지 않으면 사용자가 조직에 게스트를 초대할 수 없습니다. Power BI 액세스할 수 있는 게스트 사용자를 제어하려면 특정 보안 그룹 옵션을 사용하세요.

![Azure Active Directory 게스트 사용자가 Power BI에 액세스할 수 있도록 허용](media/service-admin-portal/powerbi-admin-allow-aad-b2b-guests.png)

### <a name="invite-external-users-to-your-organization"></a>조직에 외부 사용자 초대 

조직에서 **조직에 외부 사용자 초대** 설정을 사용하면, Power BI 공유 및 사용 권한 환경을 통해 새 외부 사용자를 조직에 초대할 수 있는지를 선택할 수 있습니다. 이 설정이 사용되지 않으면 아직 조직의 게스트 사용자가 아닌 외부 사용자를 Power BI를 통해 조직에 추가할 수 없습니다.

![조직에 외부 사용자 초대](media/service-admin-portal/powerbi-admin-allow-invite-aad-b2b-guests.png)

> [!IMPORTANT]
> 이 설정의 이전 이름은 “외부 사용자와 콘텐츠 공유”였습니다. 수정된 이름은 설정이 수행하는 작업을 좀 더 정확하게 반영합니다.

외부 사용자를 조직에 초대하려는 사용자에게는 Azure Active Directory 게스트 초대자 역할도 필요합니다. 이 설정은 Power BI를 통해 초대하는 기능만 제어합니다. 

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>외부 게스트 사용자가 조직의 콘텐츠를 편집 및 관리하도록 허용

Azure AD B2B 게스트 사용자는 조직의 콘텐츠를 편집하고 관리할 수 있습니다. [자세히 알아보기](service-admin-azure-ad-b2b.md)

다음 이미지는 외부 게스트 사용자가 조직의 콘텐츠를 편집 및 관리하도록 허용하는 옵션을 보여줍니다.

![외부 게스트 사용자가 조직의 콘텐츠를 편집 및 관리하도록 허용](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

관리 포털에서 조직으로 외부 사용자를 초대할 권한을 갖는 사용자를 제어할 수 있습니다. 자세한 내용은 이 문서의 [외부 사용자와 콘텐츠 공유](#export-and-sharing-settings)를 참조하세요.

### <a name="publish-to-web"></a>웹에 게시

Power BI 관리자로서, **웹에 게시** 설정을 사용하면 사용자가 embed 태그를 만들어 보고서를 웹에 게시할 수 있는 옵션을 제공합니다. 이 기능을 통해 웹상의 모든 사용자가 보고서 및 해당 데이터를 사용할 수 있습니다. [웹에 게시하는 방법](../collaborate-share/service-publish-to-web.md)에 대해 자세히 알아보세요.

> [!NOTE]
> Power BI 관리자만 새 웹에 게시 embed 태그를 만들 수 있습니다. 조직에 기존 embed 태그가 있을 수 있습니다. 현재 게시된 보고서를 검토하려면 관리 포털의 [embed 태그](service-admin-portal.md#embed-codes) 섹션을 참조하세요.

다음 이미지에서는 **웹에 게시** 설정을 사용하도록 설정된 경우 보고서에 대한 **기타 옵션(...)** 메뉴를 보여 줍니다.

![기타 옵션 메뉴의 웹에 게시](media/service-admin-portal/power-bi-more-options-publish-web.png)

관리 포털의 **웹에 게시** 설정은 사용자가 embed 태그를 만들 수 있는 옵션을 제공합니다.

![웹에 게시 설정](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

관리자는 **웹에 게시** 를 **사용** 으로 설정하고, **embed 태그 작동 방식 선택** 을 **기존 embed 태그만 허용** 으로 설정할 수 있습니다. 이 경우 사용자는 embed 태그를 만들 수 있지만, 이렇게 하려면 Power BI 관리자에게 문의해야 합니다.

![웹에 게시 프롬프트](../collaborate-share/media/service-publish-to-web/publish_to_web_admin_prompt.png)

**웹에 게시** 설정에 따라 UI에 다른 옵션이 표시됩니다.

|기능 |전체 조직에 대해 사용 |전체 조직에 대해 사용 안 함 |특정 보안 그룹   |
|---------|---------|---------|---------|
|보고서 **기타 옵션(...)** 메뉴 아래의 **웹에 게시**|모든 사용자에 대해 사용|모든 사용자에게 표시 안 함|권한 있는 사용자 또는 그룹에만 표시.|
|**설정** 아래의 **embed 태그 관리**|모든 사용자에 대해 사용|모든 사용자에 대해 사용|모든 사용자에 대해 사용<br><br>권한 있는 사용자 또는 그룹에만 * **삭제** 옵션 제공.<br>*  모든 사용자에 대해 **코드 가져오기** 사용.|
|관리자 포털 내의 **embed 태그**|상태에는 다음 값 중 하나가 있습니다.<br>* 활성<br>* 지원되지 않음<br>* 차단됨|상태에 **사용 안 함** 이 표시됨|상태에는 다음 값 중 하나가 있습니다.<br>* 활성<br>* 지원되지 않음<br>* 차단됨<br><br>테넌트 설정에 따라 사용자에게 권한이 부여되지 않으면 **침해됨** 이라는 상태가 표시됩니다.|
|게시된 기존 보고서|모두 사용|모두 사용 안 함|보고서가 모든 사용자에 대해 계속 렌더링합니다.|

### <a name="copy-and-paste-visuals"></a>시각적 개체 복사 및 붙여넣기

조직의 사용자는 타일 또는 보고서 시각적 개체에서 시각적 개체를 복사하여 외부 애플리케이션에 정적 이미지로 붙여넣을 수 있습니다.

![시각적 개체 복사 및 붙여넣기 사용 설정 스위치의 스크린샷](media/service-admin-portal/powerbi-admin-portal-copy-paste-visuals-setting.png)

### <a name="export-to-excel"></a>Excel로 내보내기

조직의 사용자가 시각화에서 Excel 파일로 데이터를 내보낼 수 있습니다.

![Excel로 내보내기 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-export-to-excel-setting.png)

### <a name="export-to-csv"></a>.csv로 내보내기

조직의 사용자는 타일, 시각화 또는 페이지를 매긴 보고서에서 .csv 파일로 데이터를 내보낼 수 있습니다.

![.csv로 내보내기 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-export-to-csv-setting.png)

### <a name="download-reports"></a>보고서 다운로드

조직의 사용자는 .pbix 파일과 페이지를 매긴 보고서를 다운로드할 수 있습니다.

![보고서 다운로드 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-download-reports-setting.png)

### <a name="allow-live-connections"></a>라이브 연결 허용

조직의 사용자는 Power BI 서비스 Live Connect를 사용할 수 있습니다. 또한 라이브 연결을 허용하면 사용자가 Excel에서 분석할 수 있습니다.

![라이브 연결 허용 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-allow-live-connections-setting.png)

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>PowerPoint 프레젠테이션 또는 PDF 문서로 보고서 내보내기

조직의 사용자는 보고서를 PowerPoint 파일 또는 PDF 문서로 내보낼 수 있습니다.

![PowerPoint 또는 PDF 문서로 보고서 내보내기의 스크린샷](media/service-admin-portal/powerbi-admin-portal-export-pptx-pdf-setting.png)

### <a name="export-reports-as-mhtml-documents"></a>보고서를 MHTML 문서로 내보내기

조직의 사용자는 페이지를 매긴 보고서를 MHTML 문서로 내보낼 수 있습니다.

![MHTML로 내보내기 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-export-mhtml-setting.png)

### <a name="export-reports-as-word-documents"></a>보고서를 Word 문서로 내보내기

조직의 사용자는 페이지를 매긴 보고서를 Word 문서로 내보낼 수 있습니다.

![Word로 내보내기 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-export-word-setting.png)

### <a name="export-reports-as-xml-documents"></a>보고서를 XML 문서로 내보내기

조직의 사용자는 페이지를 매긴 보고서를 XML 문서로 내보낼 수 있습니다.

![XML로 내보내기 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-export-xml-setting.png)

### <a name="export-reports-as-image-files-preview"></a>보고서를 이미지 파일로 내보내기(미리 보기)

조직의 사용자는 파일로 보고서 내보내기 API를 사용하여 보고서를 이미지 파일로 내보낼 수 있습니다.

![이미지로 내보내기 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-export-as-image-setting.png)

### <a name="print-dashboards-and-reports"></a>대시보드 및 보고서 인쇄


![인쇄 대시보드 및 보고서 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-print-dashboards-reports-setting.png)

### <a name="certification"></a>인증
이 조직의 사용자가 데이터 세트, 데이터 흐름, 보고서 및 앱을 인증할 수 있도록 허용합니다. 자세한 내용은 [콘텐츠 인증 사용](service-admin-setup-certification.md)을 참조하세요.

### <a name="email-subscriptions"></a>메일 구독
조직의 사용자가 메일 구독을 만들 수 있습니다. [구독](../collaborate-share/service-publish-to-web.md)에 대해 자세히 알아보세요.

![메일 구독 사용](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

### <a name="featured-content"></a>주요 콘텐츠

조직의 일부 또는 모든 보고서 작성자가 Power BI 홈의 추천 섹션에서 콘텐츠를 추천하도록 허용합니다. 새 사용자는 Power BI 홈페이지의 맨 위에서 추천 콘텐츠를 볼 수 있습니다. 사용자가 **즐겨찾기**, **자주 사용하는 항목** 및 **최근 항목** 을 추가하면 추천 콘텐츠가 홈페이지 아래쪽으로 이동합니다. 

먼저 작은 프로모터 세트로 시작하는 것이 좋습니다. 전체 조직이 홈에서 콘텐츠를 추천하도록 허용하면 모든 승격된 콘텐츠를 추적하기가 어려울 수 있습니다. 

추천 콘텐츠를 사용하도록 설정한 후 관리 포털에서 관리할 수도 있습니다. 도메인에서 추천 콘텐츠를 제어하는 방법에 대한 자세한 내용은 이 문서의 [추천 콘텐츠 관리](#manage-featured-content)를 참조하세요.

### <a name="allow-connections-to-featured-tables"></a>주요 테이블에 대한 연결 허용

이 설정을 통해 Power BI 관리자는 조직에서 Excel 데이터 형식 갤러리의 주요 테이블을 사용할 수 있는 사용자를 제어할 수 있습니다. 

![주요 테이블에 대한 연결 허용 설정의 스크린샷](media/service-admin-portal/powerbi-admin-portal-allow-connections-featured-tables-setting.png)

>[!NOTE]
>[라이브 연결 허용](#allow-live-connections) 설정이 사용 안 함으로 설정된 경우에는 주요 테이블에 대한 연결도 사용하지 않도록 설정됩니다.

[Excel의 Power BI 주요 테이블](../collaborate-share/service-excel-featured-tables.md)에 대해 자세히 알아보세요.

### <a name="share-to-teams"></a>Teams에 공유

이 설정을 사용하면 조직이 Power BI 서비스에서 **Teams에 공유** 단추를 숨길 수 있습니다. 사용 안 함으로 설정하면 사용자가 Power BI 서비스에서 보고서와 대시보드를 볼 때 작업 모음 또는 상황에 맞는 메뉴에서 **Teams에 공유** 단추가 표시되지 않습니다.

![Power BI 관리 포털에 있는 Teams에 공유 테넌트 설정의 스크린샷.](media/service-admin-portal/service-teams-share-to-teams-tenant-setting.png)

[Teams에 Power BI 콘텐츠 공유](../collaborate-share/service-share-report-teams.md)에 관해 자세히 알아보세요.

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

### <a name="allow-xmla-endpoints-and-analyze-in-excel-with-on-premises-datasets"></a>온-프레미스 데이터 세트를 사용하여 XMLA 엔드포인트 및 Excel의 분석 허용

조직의 사용자는 Excel을 사용하여 온-프레미스 Power BI 데이터 세트를 보고 상호 작용할 수 있습니다. 또한 XMLA 엔드포인트에 대한 연결을 허용합니다. [자세한 정보](../collaborate-share/service-analyze-in-excel.md)

### <a name="use-arcgis-maps-for-power-bi"></a>ArcGIS Maps for Power BI 사용

조직의 사용자는 Esri에서 제공하는 ArcGIS Maps for Power BI 시각화를 사용할 수 있습니다. [자세히 알아보기](../visuals/power-bi-visualizations-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Power BI(미리 보기)용 전역 검색 사용

조직의 사용자는 Azure Search에 의존하는 외부 검색 기능을 사용할 수 있습니다.

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

사용자별 데이터는 기본적으로 사용량 메트릭에 사용되도록 설정되고, 콘텐츠 생성자 계정 정보는 메트릭 보고서에 포함됩니다. 모든 사용자에 대해 이 정보를 수집하지 않으려는 경우 지정된 보안 그룹 또는 전체 조직에 기능을 사용하지 않도록 설정할 수 있습니다. 그러면 제외된 사용자에 대한 계정 정보는 *이름 없음* 으로 보고서에 표시됩니다.

## <a name="dashboard-settings"></a>대시보드 설정

### <a name="data-classification-for-dashboards"></a>대시보드에 대한 데이터 분류

조직의 사용자는 대시보드 보안 수준을 나타내는 분류로 대시보드를 태그할 수 있습니다. [자세히 알아보기](../create-reports/service-data-classification.md)

> [!NOTE]
> 이 설정은 전체 조직에 적용되며 특정 그룹에 제한될 수 없습니다.

### <a name="web-content-on-dashboard-tiles"></a>대시보드 타일의 웹 콘텐츠

조직의 사용자는 Power BI 대시보드에서 웹 콘텐츠 타일을 추가하고 볼 수 있습니다. [자세한 정보](../create-reports/service-dashboard-add-widget.md)

> [!NOTE]
> 이 경우 악의적인 웹 콘텐츠를 통해 조직이 보안 위험에 노출될 수 있습니다.

## <a name="developer-settings"></a>개발자 설정

### <a name="embed-content-in-apps"></a>앱에 콘텐츠 포함

조직 내 사용자는 Power BI 대시보드 및 보고서를 SaaS(Software as a Service) 애플리케이션에 포함할 수 있습니다. 이 설정을 사용하지 않도록 설정하면 사용자는 REST API를 사용하여 Power BI 콘텐츠를 해당 애플리케이션에 포함할 수 없게 됩니다. [자세히 알아보기](../developer/embedded/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>서비스 주체가 Power BI API를 사용하도록 허용

Azure AD(Azure Active Directory)에 등록된 웹앱은 할당된 서비스 주체를 사용하여 로그인한 사용자 없이 Power BI API에 액세스합니다. 앱이 서비스 주체 인증을 사용하도록 하려면 해당 서비스 주체가 허용된 보안 그룹에 포함되어 있어야 합니다. [자세히 알아보기](../developer/embedded/embed-service-principal.md)

> [!NOTE]
> 서비스 주체는 해당 보안 그룹의 모든 Power BI 테넌트 설정에 대한 사용 권한을 상속받습니다. 사용 권한을 제한하려면 서비스 주체에 대한 전용 보안 그룹을 만들고, 사용하도록 설정된 해당 Power BI 설정에 대한 '특정 보안 그룹 제외' 목록에 이를 추가합니다.

## <a name="dataflow-settings"></a>데이터 흐름 설정

### <a name="create-and-use-dataflows"></a>데이터 흐름 만들기 및 사용

조직의 사용자가 데이터 흐름을 만들고 사용할 수 있습니다. 데이터 흐름 개요는 [Power BI의 셀프 서비스 데이터 준비](../transform-model/dataflows/dataflows-introduction-self-service.md)를 참조하세요. 프리미엄 용량에 대한 데이터 흐름을 사용하려면 [워크로드 구성](service-admin-premium-workloads.md)을 참조하세요.

> [!NOTE]
> 이 설정은 전체 조직에 적용되며 특정 그룹에 제한될 수 없습니다.

## <a name="template-apps-settings"></a>템플릿 앱 설정

세 가지 설정은 템플릿 앱을 게시하거나 설치하는 데 사용되는 템플릿 앱 기능을 제어합니다.

![Power BI 관리 포털 템플릿 앱 설정](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>템플릿 앱 게시

조직의 사용자가 템플릿 앱 작업 영역을 만들 수 있습니다. [AppSource](https://appsource.microsoft.com) 또는 다른 배포 메서드를 통해 템플릿 앱을 게시하거나 조직 외부의 클라이언트에 배포할 수 있는 사용자를 제어합니다.

![전체 조직에 사용하도록 설정된 템플릿 앱 설정 게시](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>AppSource에 나열된 템플릿 앱 설치

조직의 사용자는 [AppSource](https://appsource.microsoft.com)의 템플릿 앱 **만** 다운로드하고 설치할 수 있습니다. AppSource에서 템플릿 앱을 설치할 수 있는 특정 사용자 또는 보안 그룹을 제어합니다.

![템플릿 앱 설치 설정](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>AppSource에 나열되지 않은 템플릿 앱 설치

조직에서 **[AppSource](https://appsource.microsoft.com)에 나열되지 않은** 템플릿 앱을 다운로드하고 설치할 수 있는 사용자를 제어합니다.

![AppSource에 나열되지 않은 템플릿 앱 설치 설정](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>용량 설정

### <a name="power-bi-premium"></a>Power BI Premium

**Power BI Premium** 탭에서는 조직용으로 구매한 Power BI Premium 용량(EM 또는 P SKU)을 관리할 수 있습니다. 조직 내 모든 사용자가 **Power BI Premium** 탭을 볼 수 있으나, ‘용량 관리자’ 또는 할당 권한이 있는 사용자로 할당된 경우에만 탭 내 콘텐츠를 볼 수 있습니다. 사용자에게 권한이 없으면 다음과 같은 메시지가 나타납니다.

![Premium 설정 액세스 권한 없음](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

**Power BI Embedded** 탭에서는 고객용으로 구매한 Power BI Embedded(A SKU) 용량을 확인할 수 있습니다. Azure에서만 A SKU를 구매할 수 있으므로 **Azure Portal** 에서 [Azure의 포함된 용량을 관리](../developer/embedded/azure-pbie-create-capacity.md)할 수 있습니다.

Power BI Embedded(A SKU) 설정을 관리하는 방법은 [Azure의 Power BI Embedded란?](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)을 참조하세요.

## <a name="embed-codes"></a>embed 태그

관리자는 보고서를 공개적으로 공유할 테넌트에 대해 생성된 embed 태그를 볼 수 있습니다. 코드를 취소하거나 삭제할 수도 있습니다. [자세히 알아보기](../collaborate-share/service-publish-to-web.md)

![Power BI 관리 포털 내의 embed 태그](media/service-admin-portal/embed-codes.png)

## <a name="organizational-visuals"></a>조직의 시각적 개체

Power BI 시각적 개체 테넌트 설정을 비롯한 모든 Power BI 시각적 개체 관리 설정은 [Power BI 시각적 개체 관리 설정 관리](organizational-visuals.md)에 설명되어 있습니다.

## <a name="azure-connections-preview"></a>Azure 연결(미리 보기)

### <a name="tenant-level-storage-preview"></a>테넌트 수준 스토리지(미리 보기)

기본적으로 Power BI에 사용되는 데이터는 Power BI에서 제공하는 내부 스토리지에 저장됩니다. 데이터 흐름 및 ADLS Gen2(Azure Data Lake Storage Gen2)를 통합하면 조직의 Azure Data Lake Storage Gen2 계정에 데이터 흐름을 저장할 수 있습니다. 자세한 내용은 [데이터 흐름 및 Azure Data Lake 통합(미리 보기)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md)을 참조하세요.

### <a name="workspace-level-storage-permissions-preview"></a>작업 영역 수준 스토리지 권한(미리 보기)

기본적으로 작업 영역 관리자가 자체 스토리지 계정을 연결할 수 없습니다. 이 미리 보기 기능을 통해 작업 영역 관리자가 자신의 스토리지 계정을 연결하는 데 사용할 수 있는 설정을 켤 수 있습니다.

## <a name="workspaces"></a>작업 영역

관리자는 **작업 영역** 탭에서 테넌트에 있는 작업 영역을 볼 수 있습니다. 이 탭에서 다음 작업을 수행할 수 있습니다.

- 작업 영역 목록과 세부 정보를 새로 고칩니다.
- 작업 영역에 대한 데이터를 .csv 파일로 내보냅니다. 
- 해당 ID, 사용자 및 해당 역할, 대시보드, 보고서 및 데이터 세트를 포함하여 작업 영역에 대한 세부 정보를 확인합니다.
- 액세스 권한이 있는 사용자 목록을 편집합니다. 즉, 작업 영역을 삭제할 수 있습니다. 작업 영역에 자신을 관리자 권한으로 추가한 다음 작업 영역을 열고 삭제할 수 있습니다.
- 이름 및 설명 필드를 편집합니다.
- 클래식 작업 영역을 새 작업 영역 환경으로 업그레이드

![작업 영역 목록](media/service-admin-portal/workspaces-list.png)

또한 관리자는 사용자가 새 작업 영역 환경 작업 영역 및 클래식 작업 영역을 만드는 기능을 제어할 수 있습니다. 자세한 내용은 이 문서의 [작업 영역 설정](#workspace-settings)을 참조하세요.

**작업 영역** 탭의 테이블 열은 작업 영역에 대해 [Power BI 관리자 Rest API](/rest/api/power-bi/admin)에서 반환된 속성에 해당합니다. 개인 작업 영역은 **개인 그룹** 형식, 클래식 작업 영역은 **그룹** 형식, 새 작업 영역 환경은 **작업 영역** 형식입니다. 자세한 내용은 [새 작업 영역에서 작업 구성](../collaborate-share/service-new-workspaces.md)을 참조하세요.

**작업 영역** 탭에 각 작업 영역의 *상태* 가 표시됩니다. 다음 표에서 각 상태의 자세한 의미를 확인할 수 있습니다.

|주  |Description  |
|---------|---------|
| **활성** | 일반 작업 영역입니다. 사용량이나 콘텐츠에 대한 정보는 알 수 없으며, 작업 영역 자체가 ‘일반’ 작업 영역이라는 사실만 알 수 있습니다. |
| **분리됨** | 관리 사용자가 없는 작업 영역입니다. |
| **삭제됨** | 삭제된 작업 영역입니다. 최대 90일 동안, 필요한 경우 작업 영역을 복원하기에 충분한 메타데이터가 유지됩니다. |
| **제거 중** | 현재 삭제가 진행 중이지만 아직 완전히 삭제되지 않은 작업 영역입니다. 사용자는 ‘제거 중’으로 항목을 이동하고 궁극적으로 ‘삭제됨’으로 이동하여 작업 영역을 삭제할 수 있습니다. |

관리자는 관리 포털 또는 PowerShell cmdlet을 사용하여 작업 영역을 관리하고 복구할 수도 있습니다. 

![작업 영역 목록](media/service-admin-portal/workspaces-list.png)

관리자는 클래식 작업 영역을 새 작업 영역 환경으로 업그레이드할 수 있습니다. 관리자는 **그룹** 형식의 작업 영역을 하나 이상 선택하여 업그레이드할 수 있습니다. 업그레이드는 큐에 대기되고 비동기적으로 실행됩니다. 관리자가 시작한 업그레이드의 전체 속도가 서비스를 원활하게 실행할 수 있게 제한되기 때문에 **보류 중** 업그레이드를 모두 완료하는 데 몇 분에서 며칠 정도 걸릴 수 있습니다. 관리자는 **작업 영역 업그레이드 상태** 열을 통해 관리자가 시작한 업그레이드의 진행률을 추적할 수 있습니다. 관리자는 관리자가 시작한 업그레이드가 **보류 중** 인 경우 해당 업그레이드를 취소할 수 있습니다. 작업 영역을 즉시 업그레이드하려면 작업 영역 관리자에게 문의하여 작업 영역 설정 창에서 업그레이드를 시작하도록 요청합니다. [Power BI 관리자가 시작한 작업 영역 업그레이드를 시작하기 전에 작업 영역 업그레이드에 대해 자세히 알아보기](../collaborate-share/service-upgrade-workspaces.md)

다음 표에서 업그레이드 상태의 자세한 의미를 확인할 수 있습니다.

|상태  |Description  |
|---------|---------|
| **(비어 있음)** | Power BI 관리자가 작업 영역을 업그레이드하지 않습니다. |
| **보류 중** | 작업 영역이 업그레이드될 때까지 큐에 대기 중입니다. 업그레이드를 취소할 수 있습니다. |
| **진행 중** | 작업 영역이 현재 업그레이드되는 중입니다. 업그레이드를 취소할 수 없습니다. |
| **완료됨** | 지난 30일 내에 Power BI 관리자가 작업 영역을 업그레이드했습니다. 작업 영역 관리자는 작업 영역이 업그레이드된 후 30일 기간 중에 원하는 경우 클래식 옵션으로 돌아갈 수 있습니다. |


## <a name="custom-branding"></a>사용자 지정 브랜딩

관리자는 전체 조직에 대한 Power BI의 모양을 사용자 지정할 수 있습니다. 현재 세 가지 기본 옵션이 있습니다.

![사용자 지정 브랜딩 옵션](media/service-admin-portal/power-bi-custom-branding.png)

* **로고 업로드**: 최상의 결과를 위해 200 x 30 픽셀 이상의 .png(10KB 이하)로 저장된 로고를 업로드합니다.

* **커버 이미지 업로드**: 최상의 결과를 위해 1920 x 160 픽셀 이상의 .jpg 또는 .png(1MB 이하)로 저장된 커버 이미지를 업로드합니다.

* **색 테마 선택**: 16진수 #, RGB, 값 또는 제공된 팔레트를 기준으로 테마를 선택할 수 있습니다.


자세한 내용은 [조직에 대한 사용자 지정 브랜딩](https://aka.ms/orgBranding)을 참조하세요.

## <a name="protection-metrics"></a>보호 메트릭

Power BI에 대한 정보 보호를 사용하도록 설정하면 관리 포털에 데이터 보호 메트릭이 표시됩니다. 보고서는 민감도 레이블이 콘텐츠를 보호하는 방법을 보여 줍니다.

## <a name="manage-featured-content"></a>추천 콘텐츠 관리

Power BI 관리자로서, 조직 전체에서 Power BI 홈의 추천 섹션으로 승격된 모든 보고서, 대시보드 및 앱을 관리할 수 있습니다.

- 관리 포털에서 **추천 콘텐츠** 를 선택합니다.

여기에서 콘텐츠를 추천하는 사용자, 추천된 시간 및 모든 관련 메타데이터의 개요를 볼 수 있습니다. 의심스러운 항목이 있거나 추천 섹션을 정리하려는 경우 필요에 따라 승격된 콘텐츠를 삭제할 수 있습니다.

추천 콘텐츠 사용에 대한 내용은 이 문서에서 [추천 콘텐츠](#featured-content)를 참조하세요.

## <a name="next-steps"></a>다음 단계

[조직에서 Power BI 관리](service-admin-administering-power-bi-in-your-organization.md)  
[Power BI 관리자 역할 이해](service-admin-role.md)  
[조직에서 Power BI 감사](service-admin-auditing.md)  

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
