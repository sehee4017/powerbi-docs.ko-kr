---
title: 지역별 응급 대응 대시보드에 연결
description: 지역별 응급 대응 템플릿 앱의 COVID-19 의사 결정 지원 대시보드를 가져오고 설치하는 방법 및 데이터에 연결하는 방법입니다.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6af8568dc39544ce064643c8dfb80fa2932cf13a
ms.sourcegitcommit: 834cad24901f7fd966c4010e36a7904bc120e57f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82149673"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>지역별 응급 대응 대시보드에 연결
지역별 응급 대응 대시보드는 [Microsoft Power Platform 지역별 응급 대응 솔루션](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview)의 보고 구성 요소입니다. 지역별 조직 관리자는 Power BI 테넌트에서 대시보드를 볼 수 있으므로 효율적인 의사 결정에 도움이 되는 중요한 데이터 및 메트릭을 빠르게 볼 수 있습니다.

![지역별 응급 대응 대시보드 앱 보고서](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

이 문서에서는 지역별 응급 대응 대시보드 템플릿 앱을 사용하여 지역별 응급 대응 앱을 설치하는 방법과 데이터 원본에 연결하는 방법에 대해 설명합니다.

대시보드에 표시되는 항목에 대한 자세한 내용은 [인사이트 가져오기](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)를 참조하세요.

템플릿 앱을 설치하고 데이터 원본에 연결할 후에는 필요에 맞게 보고서를 사용자 지정할 수 있습니다. 그런 다음, 조직의 동료들에게 이 보고서를 앱으로 배포할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

이 템플릿 앱을 설치하기 전에 먼저 [지역별 응급 대응 솔루션](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy)을 설치하고 설정해야 합니다. 이 솔루션을 설치하면 앱에 데이터를 채우는 데 필요한 데이터 원본 참조가 만들어집니다.

지역별 응급 대응 솔루션을 설치하는 경우 [Common Data Service 환경 인스턴스에 대한 URL](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard)을 적어 두세요. 데이터에 템플릿 앱을 연결할 때 이 URL이 필요합니다.

## <a name="install-the-app"></a>앱 설치

1. 다음 링크를 클릭하여 앱을 가져옵니다. [지역별 응급 대응 대시보드 템플릿 앱](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. 앱의 AppSource 페이지에서 [**지금 가져오기**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)를 선택합니다.

    [![AppSource의 지역별 응급 대응 대시보드 앱](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. **설치**를 선택합니다. 

    ![지역별 응급 대응 대시보드 앱 설치](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    앱이 설치되면 앱 페이지에 설치된 앱이 표시됩니다.

   ![앱 페이지의 지역별 응급 대응 대시보드 앱](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>데이터 원본 연결 

1. 앱 페이지에서 아이콘을 선택하여 앱을 엽니다.

1. 시작 화면에서 **탐색**을 선택합니다.

   ![템플릿 앱 시작 화면](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   앱이 열리고 샘플 데이터가 표시됩니다.

1. 페이지 맨 위에 있는 배너에서 **데이터 연결** 링크를 선택합니다.

   ![지역별 응급 대응 대시보드 앱의 데이터 연결 링크](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. 표시되는 대화 상자에서[Common Data Service 환경 인스턴스 URL](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard)을 입력합니다. 예: https://[myenv].crm.dynamics.com. 완료하면 **다음**을 클릭합니다.

   ![지역별 응급 대응 대시보드 앱의 URL 대화 상자](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. 표시되는 다음 대화 상자에서 인증 방법을 **OAuth2**로 설정합니다. 개인 정보 수준 설정은 변경하지 않아도 됩니다.

   **로그인**을 선택합니다.

   ![지역별 응급 대응 대시보드 앱의 인증 대화 상자](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. Microsoft 로그인 화면에서 Power BI에 로그인합니다.

   ![Microsoft 로그인 화면](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   로그인하면 보고서가 데이터 원본에 연결되고 최신 데이터로 채워집니다. 데이터가 채워지는 동안 활동 모니터가 회전합니다.

   ![지역별 응급 대응 대시보드 앱의 새로 고침 진행 중](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>보고서 새로 고침 예약

데이터 새로 고침이 완료되면 [새로 고침 일정을 설정](../refresh-scheduled-refresh.md)하여 보고서 데이터를 최신 상태로 유지합니다.

1. 위쪽 헤더 표시줄에서 **Power BI**를 선택합니다.

   ![Power BI 이동 경로](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. 왼쪽 탐색 창의 **작업 영역** 아래에서 지역별 응급 대응 대시보드 작업 영역을 찾아서 [예약된 새로 고침 구성](../refresh-scheduled-refresh.md) 문서의 지침을 따릅니다.

## <a name="customize-and-share"></a>사용자 지정 및 공유

자세한 내용은 [앱 사용자 지정 및 공유](../service-template-apps-install-distribute.md#customize-and-share-the-app)를 참조하세요. 앱을 게시하거나 배포하기 전에 반드시 [보고서 고지 사항](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview#disclaimer)을 검토하세요.

## <a name="next-steps"></a>다음 단계
* [지역별 응급 대응 대시보드 이해](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Power Apps에서 재난 안내 샘플 템플릿 설정 및 알아보기](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
* [Power BI 템플릿 앱이란?](../service-template-apps-overview.md)
* [조직에 템플릿 앱 설치 및 배포](../service-template-apps-install-distribute.md)
