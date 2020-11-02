---
title: 코로나바이러스감염증-19 미국 추적 보고서에 연결
description: 코로나바이러스감염증-19 미국 케이스 템플릿 앱을 가져와서 설치하고 데이터에 연결하는 방법
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/05/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 01dab6cad6142b455a0d61a0011e43cea6da23e1
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349527"
---
# <a name="connect-to-the-covid-19-us-tracking-report"></a>코로나바이러스감염증-19 미국 추적 보고서에 연결
이 문서에서는 코로나바이러스감염증-19 추적 보고서의 템플릿 앱을 설치하고 데이터 원본에 연결하는 방법을 설명합니다.

![COVID-19 미국 추적 보고서](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-title-screen.png)

데이터에 대한 정보와 부인이 포함된 보고서 자체에 대한 자세한 내용은 [미국 주 및 지방 정부를 위한 코로나바이러스감염증-19 추적 샘플](../create-reports/sample-covid-19-us.md)을 참조하세요.

템플릿 앱을 설치하고 데이터 원본에 연결할 후에는 필요에 맞게 보고서를 사용자 지정할 수 있습니다. 그런 다음, 조직의 동료들에게 이 보고서를 앱으로 배포할 수 있습니다.

## <a name="install-the-app"></a>앱 설치

1. 다음 링크를 클릭하여 앱을 가져옵니다. [코로나바이러스감염증-19 미국 추적 보고서 템플릿 앱](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. 앱의 AppSource 페이지에서 [**지금 가져오기**](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)를 클릭합니다.

    [![Appsource의 코로나바이러스감염증-19 미국 추적 보고서](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-appsource-icon.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. 메시지가 표시되면 **설치** 를 클릭합니다. 앱이 설치되면 앱 페이지에 설치된 앱이 표시됩니다.

   ![앱 페이지의 코로나바이러스감염증-19 미국 추적 보고서](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>데이터 원본 연결 

1. 앱 페이지에서 아이콘을 클릭하여 앱을 엽니다.

1. 표시되는 시작 화면에서 **연결** 을 선택합니다.

   ![템플릿 앱 시작 화면](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-splash-screen.png)

1. 매개 변수 대화 상자가 나타납니다. 필수 매개 변수는 없습니다. **다음** 을 클릭합니다.

   ![코로나19 미국 추적 보고서 매개 변수 대화 상자의 스크린샷](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-parameters-dialog.png)

1. 인증 방법 대화 상자가 나타납니다. 권장 값은 미리 채워져 있습니다. 다른 값에 대한 특정 지식이 없는 경우 변경하지 마세요.

    **다음** 을 클릭합니다.

   ![코로나19 미국 추적 보고서 인증 대화 상자의 스크린샷](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-authentication-dialog.png)

1. **로그인** 을 클릭합니다.

   ![코로나19 미국 추적 보고서 로그인 대화 상자의 스크린샷](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-signin-dialog.png)
 
   보고서가 데이터 원본에 연결되고 최신 데이터로 채워집니다. 이 시간 동안 샘플 데이터가 표시되고 새로 고침이 진행 중입니다.

   ![코로나바이러스감염증-19 미국 추적 보고서 새로 고침 진행 중](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>보고서 새로 고침 예약

데이터 새로 고침이 완료되면 앱의 작업 영역이 표시됩니다. [새로 고침 일정을 설정](../connect-data/refresh-scheduled-refresh.md)하여 보고서 데이터를 최신 상태로 유지합니다.

## <a name="customize-and-share"></a>사용자 지정 및 공유

자세한 내용은 [앱 사용자 지정 및 공유](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app)를 참조하세요. 앱을 게시하거나 배포하기 전에 반드시 [보고서 고지 사항](../create-reports/sample-covid-19-us.md#disclaimers)을 검토하세요.

## <a name="next-steps"></a>다음 단계
* [미국 주 및 지방 정부를 위한 COVID-19 추적 샘플](../create-reports/sample-covid-19-us.md)
* 질문이 있으신가요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
* [Power BI 템플릿 앱이란?](../connect-data/service-template-apps-overview.md)
* [조직에 템플릿 앱 설치 및 배포](../connect-data/service-template-apps-install-distribute.md)
