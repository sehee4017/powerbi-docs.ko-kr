---
title: Power BI Report Server에 최적화된 Power BI Desktop 설치
description: Power BI Report Server에 최적화된 Power BI Desktop을 설치하는 방법에 대한 자세한 내용
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 02/13/2020
ms.openlocfilehash: 3f4538639765f62387fe6b4e493886f85ba22c3d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239363"
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Report Server에 최적화된 Power BI Desktop 설치

Power BI Report Server에 대한 Power BI 보고서를 만들려면 Power BI Report Server에 최적화된 Power BI Desktop 버전을 다운로드하여 설치해야 합니다. 이 릴리스는 Power BI 서비스와 함께 사용되는 Power BI Desktop과 다릅니다. 예를 들어 Power BI 서비스용 Power BI Desktop 버전은 일반에 공급된 후에만 Power BI Report Server 버전에서 사용할 수 있는 미리 보기 기능을 포함합니다. 이 릴리스를 사용하면 보고서 서버가 알려진 버전의 보고서 및 모델과 상호 작용할 수 있습니다. 

다행스럽게도 Power BI Desktop 및 Power BI Report Server에 최적화된 Power BI Desktop을 같은 컴퓨터에 모두 설치할 수 있습니다.

## <a name="download-and-install-power-bi-desktop"></a>Power BI Desktop 다운로드 및 설치

Power BI Report Server에 최적화된 최신 버전의 Power BI Desktop을 유지하는 가장 쉬운 방법은 보고서 서버의 웹 포털에서 시작하는 것입니다.

1. 보고서 서버 웹 포털에서 **다운로드** 화살표 > **Power BI Desktop**을 선택합니다.

    ![웹 포털에서 Power BI Desktop 다운로드](media/install-powerbi-desktop/report-server-download-web-portal.png)

    또는 [Power BI Report Server](https://powerbi.microsoft.com/report-server/) 홈페이지로 이동하고 **고급 다운로드 옵션**을 선택합니다.

2. 다운로드 센터 페이지에서 언어를 선택한 다음 **다운로드**를 선택합니다.

3. 컴퓨터에 따라 다음 중에서 선택합니다. 

    - **PBIDesktopRS.msi**(32비트 버전) 또는
    - **PBIDesktopRS_x64.msi**(64비트 버전).

1. 설치 프로그램을 다운로드한 후에는 Power BI Desktop(2019년 9월) 설치 마법사를 실행합니다.

2. 설치가 끝나면 **Power BI Desktop 시작**을 선택합니다.

    그러면 자동으로 시작되어 사용할 준비가 됩니다.

## <a name="verify-youre-using-the-correct-version"></a>올바른 버전을 사용하는지 확인
올바른 Power BI Desktop을 사용하는지 쉽게 확인할 수 있습니다. Power BI Desktop 내에서 시작 화면 또는 제목 표시줄을 확인하세요. 제목 표시줄에 **Power BI Desktop(2019년 9월)** 이라고 표시되면 올바른 버전이 준비된 것입니다. 또한 Power BI 로고 색은 역으로 노란색 바탕에 검은색이 아닌 검은색 바탕에 노란색입니다.

![Power BI Desktop 2019년 9월](media/install-powerbi-desktop/power-bi-report-server-desktop-sept-2019.png)

Power BI 서비스용 Power BI Desktop 버전은 제목 표시줄에 월 및 연도가 없습니다.

## <a name="file-extension-association"></a>파일 확장명 연결
동일한 머신에 Power BI Desktop 및 Power BI Report Server에 최적화된 Power BI Desktop을 모두 설치한 경우 가장 최근에 설치된 Power BI Desktop이 .pbix 파일과 연결됩니다. 따라서 .pbix 파일을 두 번 클릭하면 가장 최근에 설치된 Power BI Desktop을 시작합니다.

Power BI Desktop을 설치한 다음, Power BI Report Server에 최적화된 Power BI Desktop을 설치한 경우 기본적으로 Power BI Report Server에 최적화된 Power BI Desktop에 있는 모든 pbix 파일이 열립니다. pbix 파일을 열 때 Power BI Desktop을 시작하도록 기본값으로 설정하려는 경우 [Microsoft Store에서 Power BI Desktop](https://aka.ms/pbidesktopstore)을 다시 설치합니다.

먼저 사용하려는 버전의 Power BI Desktop을 열 수 있습니다. 그런 다음 Power BI Desktop 내에서 파일을 엽니다.

Power BI Report Server 내에서 Power BI 보고서를 편집하거나 웹 포털에서 새 Power BI 보고서를 만들면 항상 올바른 버전의 Power BI Desktop이 열립니다.

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항

Power BI Report Server, Power BI 서비스(`https://app.powerbi.com`) 및 Power BI 모바일 앱의 Power BI 보고서는 거의 동일한 역할을 담당하지만 몇 가지 다른 기능이 있습니다.

### <a name="selecting-a-language"></a>언어 선택

Power BI Report Server에 최적화된 Power BI Desktop의 경우 앱을 설치할 때 언어를 선택합니다. 이후에는 변경할 수 없지만 다른 언어로 된 버전을 설치할 수 있습니다.

### <a name="report-visuals-in-a-browser"></a>브라우저의 보고서 시각적 개체

Power BI Report Server 보고서는 Power BI 시각적 개체를 비롯한 대부분의 시각화를 지원합니다. Power BI Report Server 보고서는 다음 항목을 지원하지 않습니다.

* R 시각적 개체
* ArcGIS 맵
* 현재 위치
* Power BI Desktop 미리 보기 기능

### <a name="reports-in-the-power-bi-mobile-apps"></a>Power BI 모바일 앱의 보고서

Power BI Report Server 보고서는 [Power BI 모바일 앱](../consumer/mobile/mobile-apps-for-mobile-devices.md)에서 다음을 비롯한 모든 기본 기능을 지원합니다.

* [휴대폰 보고서 레이아웃](../create-reports/desktop-create-phone-report.md): Power BI 모바일 앱에 보고서를 최적화할 수 있습니다. 휴대폰에서 최적화된 보고서에는 특수 아이콘 ![휴대폰 보고서 레이아웃 아이콘](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png) 및 레이아웃이 포함됩니다.
  
    ![휴대폰에 최적화된 보고서](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

Power BI Report Server 보고서는 Power BI 모바일 앱에서 다음과 같은 기능을 지원하지 않습니다.

* R 시각적 개체
* ArcGIS 맵
* Power BI 시각적 개체
* 현재 위치
* 지역 필터링 또는 막대 코드

### <a name="custom-security"></a>사용자 지정 보안

Power BI Report Server에 최적화된 Power BI Desktop은 사용자 지정 보안을 지원하지 않습니다. Power BI Report Server가 사용자 지정 보안 확장 프로그램을 사용하여 구성된 경우에는 Power BI Desktop(Power BI Report Server에 최적화됨)에서 Power BI Report Server 인스턴스로 Power BI 보고서를 저장할 수 없습니다. Power BI Desktop에서 .pbix 보고서 파일을 저장하고 Power BI Report Server 포털 사이트에 업로드해야 합니다.

### <a name="saving-reports-to-a-power-bi-report-server-in-a-different-domain"></a>다른 도메인의 Power BI Report Server에 보고서 저장

Power BI 보고서를 Power BI Report Server에 저장하는 경우 Windows 자격 증명이 사용됩니다. Windows 자격 증명과 다른 도메인에 있는 보고서 서버에 직접 저장할 수는 없습니다. 웹 브라우저를 사용하여 보고서 서버를 확인한 다음, 사용자 머신에서 파일을 수동으로 업로드할 수도 있습니다.

## <a name="power-bi-desktop-for-earlier-versions-of-power-bi-report-server"></a>이전 버전의 Power BI Report Server에 대한 Power BI Desktop

보고서 서버가 이전 버전이면 해당 버전의 Power BI Desktop이 필요합니다. 다음은 이전 버전을 다운로드하기 위한 링크입니다.

- Microsoft Power BI Desktop([Power BI Report Server에 최적화됨 - 2019년 9월](https://go.microsoft.com/fwlink/?linkid=2103723))

## <a name="next-steps"></a>다음 단계

Power BI Desktop을 설치했으므로 Power BI 보고서를 작성하기 시작할 수 있습니다.

[Power BI Report Server용 Power BI 보고서 만들기](quickstart-create-powerbi-report.md)  
[Power BI Report Server란?](get-started.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)

