---
title: Power BI Windows 앱에서 온-프레미스 보고서 및 KPI 보기
description: Windows 10용 Power BI 모바일 앱은 중요한 온-프레미스 비즈니스 정보에 대한 터치 기반의 라이브 모바일 액세스를 제공합니다.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/19/2020
ms.author: painbar
ms.openlocfilehash: 28353ec6d0b2f8a1f83544d63526748c621cb858
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694104"
---
# <a name="view-on-premises-reports-and-kpis-in-the-power-bi-windows-app"></a>Power BI Windows 앱에서 온-프레미스 보고서 및 KPI 보기
SQL Server 2016 Reporting Services에서 Windows 10용 Power BI 앱은 중요한 온-프레미스 비즈니스 정보에 대한 터치 기반의 라이브 모바일 액세스를 제공합니다. 

![Reporting Services 모바일 보고서](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>먼저 수행할 중요한 작업
SQL Server 2016 Enterprise Edition 모바일 보고서 게시자를 사용하여 [Reporting Services 모바일 보고서를 만들고](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher)[Reporting Services 웹 포털](/sql/reporting-services/web-portal-ssrs-native-mode)에 게시합니다. 웹 포털에 KPI를 만듭니다. 폴더에 정리하고 쉽게 찾을 수 있도록 즐겨찾기를 표시합니다. 

그런 다음, Windows 10용 Power BI 앱에서 폴더에 정리되어 있거나 즐겨찾기에 모아놓은 KPS, 모바일 보고서 및 Power BI 고보서를 봅니다. 

> [!NOTE]
> 디바이스에서 Windows 10이 실행되고 있어야 합니다. RAM 1GB, 내부 스토리지 8GB 이상인 디바이스에서 앱이 최적으로 작동합니다.

>[!NOTE]
>**Windows 10 Mobile을 사용하는 휴대폰**용 Power BI 모바일 앱 지원은 2021년 3월 16일 중단될 예정입니다. [자세히 알아보기](https://go.microsoft.com/fwlink/?linkid=2121400)

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>SQL Server 2016 Reporting Services 서버 없이 샘플을 탐색합니다.
Reporting Services 웹 포털에 대한 액세스가 없더라도, Reporting Services 모바일 보고서의 기능을 탐색할 수 있습니다.

1. Windows 10 디바이스에서 Power BI 앱을 엽니다.
2. 왼쪽 위 모퉁이에서 전역 탐색 단추 ![전역 탐색 단추](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) 를 탭합니다.
3. **설정** 아이콘 ![설정 아이콘](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)을 탭하고 **서버에 연결**을 마우스 오른쪽 단추로 클릭하거나 탭한 채로 유지한 다음 **샘플 보기**를 탭합니다.
   
   ![SSRS 샘플 보기](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. 소매 보고서 또는 판매 보고서 폴더를 열어 KPI 및 모바일 보고서를 탐색합니다.
   
   ![샘플 KPI 및 모바일 보고서](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

KPI 및 모바일 보고서와 상호 작용할 샘플을 찾아봅니다.

## <a name="connect-to-a-reporting-services-report-server"></a>Reporting Services 보고서 서버에 연결
1. 탐색 창의 아래쪽에서 **설정** ![설정 아이콘](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)을 탭합니다.
2. **서버에 연결**을 탭합니다.
3. 서버 주소, 사용자 이름, 암호를 입력합니다. 서버 주소에 대해 다음 형식을 사용합니다.
   
     `https://<servername>/reports` 또는   `https://<servername>/reports`
   
   > [!NOTE]
   > 연결 문자열의 시작 부분에 **http** 또는 **https**를 포함합니다.
   > 
   > 
   
    원하는 경우, **고급 옵션**을 눌러서 서버에 이름을 지정합니다.
4. 확인 표시를 탭하여 연결합니다. 
   
   이제 탐색 창에 서버가 표시됩니다.
   
   ![탐색 창의 서버](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >언제든지 전역 탐색 단추 ![전역 탐색 단추](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png)를 탭하면 Power BI 서비스에서 Reporting Services 모바일 보고서와 대시보드 간에 이동할 수 있습니다. 
   > 

   >[!NOTE]
   >사용자 지정 포트가 구성된 보고서 서버는 지원되지 않으며 Power BI Windows 앱에서 액세스할 수 없습니다. 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Power BI 앱에서 Reporting Services KPI와 모바일 보고서 보기
Reporting Services KPI, 모바일 보고서 및 Power BI 보고서(미리 보기)는 Reporting Services 웹 포털에서와 동일한 폴더에 표시됩니다.

![보고서 폴더](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* 포커스 모드로 보려면 KPI를 누릅니다.
  
    ![포커스 모드의 KPI](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* 모바일 보고서를 눌러서 열고 Power BI 앱에서 상호 작용합니다.
  
    ![Reporting Services 모바일 보고서](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>즐겨찾는 KPI 및 보고서 보기
Reporting Services 웹 포털에 KPI, 모바일 보고서 및 Power BI 보고서를 즐겨찾기로 표시해 놓으면 Windows 10 디바이스에서 Power BI 즐겨찾기 대시보드와 보고서를 통해 한 폴더에서 편리하게 볼 수 있습니다.

* **즐겨찾기**를 누릅니다.
  
   ![즐겨찾기 아이콘](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   웹 포털의 즐겨찾기가 이 페이지에 모두 있습니다.
  
자세한 내용은 [Power BI 모바일 앱의 즐겨찾기](mobile-apps-favorites.md)를 읽어보세요.

## <a name="remove-a-connection-to-a-report-server"></a>보고서 서버에 대한 연결을 제거합니다.
Power BI 모바일 앱에서 한 번에 하나의 보고서 서버에 연결될 수 있습니다. 다른 서버에 연결하려는 경우 현재 서버에서 분리해야 합니다.

1. 탐색 창의 아래쪽에서 **설정** ![설정 아이콘](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)을 탭합니다.
2. 연결하지 않을 서버 이름을 탭한 채로 있습니다.
3. **서버 제거**를 탭합니다.
   
    ![서버 제거](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Reporting Services 모바일 보고서 및 KPI 만들기
Power BI 모바일 앱에서 Reporting Services KPI와 모바일 보고서를 만들지 않습니다. SQL Server 모바일 보고서 게시자 및 SQL Server 2016 Reporting Services 웹 포털에서 만듭니다.

* [Reporting Services 모바일 보고서를 만들](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher)어서, Reporting Services 웹 포털에 게시합니다.
* [Reporting Services 웹 포털에서 KPI](/sql/reporting-services/working-with-kpis-in-reporting-services)를 만듭니다.

## <a name="next-steps"></a>다음 단계
* [Windows 10용 Power BI 모바일 앱 시작](mobile-windows-10-phone-app-get-started.md)  
* [Power BI란?](../../fundamentals/power-bi-overview.md)  
* 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
