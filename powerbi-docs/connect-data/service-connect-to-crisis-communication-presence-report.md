---
title: 재난 안내 상태 보고서에 연결
description: 코로나바이러스감염증-19 재난 안내 상태 보고서 템플릿 앱을 가져와서 설치하고 데이터에 연결하는 방법
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: f637bb10ed7ec27dcb3da07fc04cae39328ffebe
ms.sourcegitcommit: 34cca70ba84f37b48407d5d8a45c3f51fb95eb3c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80752260"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>재난 안내 상태 보고서에 연결

이 Power BI 앱은 재난 안내용 Microsoft Power Platform 솔루션의 보고서/대시보드 아티팩트입니다. 이 앱은 재난 안내 앱 사용자를 위해 작업자 위치를 추적합니다. 솔루션은 Power Apps, Power Automate, Teams, SharePoint 및 Power BI의 기능을 통합하여 구현되며, 웹과 모바일, Teams에서 사용할 수 있습니다.

![재난 안내 상태 보고서 앱 보고서](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

이 대시보드는 응급 관리자들이 적시에 올바른 의사 결정을 내릴 수 있도록 의료 시스템 전반의 집계 데이터를 보여 줍니다.

이 문서에서는 앱을 설치하고 데이터 원본에 연결하는 방법을 설명합니다. 재난 안내 앱에 대한 자세한 내용은 [Power Apps에서 재난 안내 샘플 템플릿 설정 및 알아보기](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)를 참조하세요.

템플릿 앱을 설치하고 데이터 원본에 연결할 후에는 필요에 맞게 보고서를 사용자 지정할 수 있습니다. 그런 다음, 조직의 동료들에게 이 보고서를 앱으로 배포할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

이 템플릿 앱을 설치하기 전에 먼저 [재난 안내 샘플](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)을 설치하고 설정해야 합니다. 이 솔루션을 설치하면 앱에 데이터를 채우는 데 필요한 데이터 원본 참조가 만들어집니다.

재난 안내 샘플을 설치할 때는 [“CI_Employee Status”의 SharePoint 목록 폴더 경로와 목록 ID](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi)를 기록해 두세요.

## <a name="install-the-app"></a>앱 설치

1. 다음 링크를 클릭하여 앱을 가져옵니다. [재난 안내 상태 보고서 템플릿 앱](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. 앱의 AppSource 페이지에서 [**지금 가져오기**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)를 선택합니다.

    [![AppSource의 재난 안내 상태 보고서 앱](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. **한 가지 더**의 정보를 읽고 **계속**을 선택합니다.

    ![재난 안내 상태 보고서 앱, 한 가지 더](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. **설치**를 선택합니다. 

    ![재난 안내 상태 보고서 앱 설치](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    앱이 설치되면 앱 페이지에 설치된 앱이 표시됩니다.

   ![앱 페이지의 재난 안내 상태 보고서 앱](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>데이터 원본 연결

1. 앱 페이지에서 아이콘을 선택하여 앱을 엽니다.

1. 시작 화면에서 **탐색**을 선택합니다.

   ![템플릿 앱 시작 화면](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   앱이 열리고 샘플 데이터가 표시됩니다.

1. 페이지 맨 위에 있는 배너에서 **데이터 연결** 링크를 선택합니다.

   ![재난 안내 상태 보고서 앱의 데이터 연결 링크](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. 대화 상자에서
   1. SharePoint_Folder 필드에 [“CI_Employee Status” SharePoint 목록 경로](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi)를 입력합니다.
   1. List_ID 필드에 목록 설정에서 가져온 목록 ID를 입력합니다. 완료하면 **다음**을 클릭합니다.

   ![재난 안내 상태 보고서 앱의 URL 대화 상자](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. 표시되는 다음 대화 상자에서 인증 방법을 **OAuth2**로 설정합니다. 개인 정보 수준 설정은 변경하지 않아도 됩니다.

   **로그인**을 선택합니다.

   ![재난 안내 상태 보고서 앱의 인증 대화 상자](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. Microsoft 로그인 화면에서 Power BI에 로그인합니다.

   ![Microsoft 로그인 화면](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   로그인하면 보고서가 데이터 원본에 연결되고 최신 데이터로 채워집니다. 데이터가 채워지는 동안 활동 모니터가 회전합니다.

   ![재난 안내 상태 보고서 앱의 새로 고침 진행 중](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>보고서 새로 고침 예약

데이터 새로 고침이 완료되면 [새로 고침 일정을 설정](../refresh-scheduled-refresh.md)하여 보고서 데이터를 최신 상태로 유지합니다.

1. 위쪽 헤더 표시줄에서 **Power BI**를 선택합니다.

   ![Power BI 이동 경로](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. 왼쪽 탐색 창의 **작업 영역** 아래에서 병원 응급 대응 의사 결정 지원 대시보드 작업 영역을 찾은 다음, [예약된 새로 고침 구성](../refresh-scheduled-refresh.md) 문서의 지침을 따릅니다.

## <a name="customize-and-share"></a>사용자 지정 및 공유

자세한 내용은 [앱 사용자 지정 및 공유](../service-template-apps-install-distribute.md#customize-and-share-the-app)를 참조하세요. 앱을 게시하거나 배포하기 전에 반드시 [보고서 고지 사항](../create-reports/sample-covid-19-us.md#disclaimers)을 검토하세요.

## <a name="next-steps"></a>다음 단계
* [Power Apps에서 재난 안내 샘플 템플릿 설정 및 알아보기](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
* [Power BI 템플릿 앱이란?](../service-template-apps-overview.md)
* [조직에 템플릿 앱 설치 및 배포](../service-template-apps-install-distribute.md)
