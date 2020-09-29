---
title: 허용 목록에 Power BI URL 추가
description: 이 문서에는 Power BI에 대한 연결 허용 목록에 추가할 URL 엔드포인트 및 포트가 나열됩니다.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2020
ms.custom: seodec18
ms.openlocfilehash: e4aec179b298c5a8ca52cf73ac5fdceed7e8602a
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90857683"
---
# <a name="add-power-bi-urls-to-your-allow-list"></a>허용 목록에 Power BI URL 추가
[//]: # "suparnap, miwehnia, natham은 이 목록을 유지 관리하기 위한 연락처입니다."

Power BI 서비스는 인터넷에 연결해야 합니다. 이 문서의 표에 나열된 엔드포인트는 Power BI 서비스를 사용하는 고객에게 연결할 수 있어야 합니다.

Power BI 서비스를 사용하려면 아래 테이블에 **필수**라고 표시된 엔드포인트 및 연결된 사이트에서 **필수**라고 표시된 엔드포인트에 연결할 수 있어야 합니다. 외부 사이트에 대한 링크가 특정 섹션을 가리키는 경우 해당 섹션에서 엔드포인트를 검토해야 합니다.

**선택적**으로 표시된 엔드포인트는 특정 기능을 사용할 수 있도록 허용 목록에 추가될 수도 있습니다.

Power BI 서비스에서는 TCP 포트 443이 나열된 엔드포인트에 대해 열려야 합니다.

와일드 카드(*)는 루트 도메인 아래에 있는 모든 수준을 나타내고 정보를 사용할 수 없는 경우 해당 없음을 사용합니다. **대상** 열에는 도메인 이름 및 외부 사이트 링크가 나열됩니다. 이들 사이트에 추가 엔드포인트 정보가 있습니다.

>[!Important]
>아래 표의 정보는 Power BI 독일, 21Vianet에서 운영하는 중국 Power BI 또는 미국 정부용 Power BI에는 적용되지 않습니다. 클라우드 서비스 간 통신에 대해 자세히 알아보려면 [정부 및 글로벌 Azure 클라우드 서비스](service-govus-overview.md#connect-government-and-global-azure-cloud-services)를 참조하세요.

## <a name="authentication"></a>인증

Power BI는 Microsoft 365 인증 및 ID 섹션에 있는 필수 엔드포인트에 따라 달라집니다. Power BI를 사용하려면 아래 연결된 사이트에 있는 엔드포인트에 연결해야 합니다.

| 행 | 용도 | 대상 | 포트 |
| --- | --- | --- | --- |
| 1 | **필수:** 인증 및 ID | [Microsoft 365 Common 및 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)에 대한 설명서를 참조하세요.  | 해당 없음 |

## <a name="general-site-usage"></a>일반 사이트 사용

Power BI의 일반적인 사용의 경우 아래 테이블 및 연결된 사이트에 있는 엔드포인트에 연결해야 합니다.

| 행 | 용도 | 대상 | 포트 |
| --- | --- | --- | --- |
| 1 | **필수:** 백 엔드 API | api.powerbi.com | TCP 443 |
| 2 | **필수:** 백 엔드 API | *.analysis.windows.net | TCP 443 |
| 3 | **필수:** 백 엔드 API | *.pbidedicated.windows.net | TCP 443 |
| 4 | **필수:** CDN(Content Delivery Network) | content.powerapps.com | TCP 443 |
| 5 | **필수:** Microsoft 365 통합 | [Microsoft 365 Common 및 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)에 대한 설명서를 참조하세요. | 해당 없음 |
| 6 | **필수:** 포털 | *.powerbi.com | TCP 443 |
| 7 | **필수:** 서비스 원격 분석 | dc.services.visualstudio.com | TCP 443 |
| 8 | **선택 사항:** 정보 메시지 | dynmsg.modpim.com | TCP 443 |
| 9 | **선택 사항:** NPS 설문 조사 | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>관리

Power BI에서 관리 기능을 수행하려면 아래 연결된 사이트의 엔드포인트에 연결해야 합니다.

| 행 | 용도 | 대상 | 포트 |
| --- | --- | --- | --- |
| 1 | **필수:** 사용자 관리 및 감사 로그 보기의 경우 | [Microsoft 365 Common 및 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)에 대한 설명서를 참조하세요. | 해당 없음 |
| | | |

## <a name="getting-data"></a>데이터 가져오기

OneDrive와 같은 특정 데이터 원본에서 데이터를 가져오려면 아래 테이블의 엔드포인트에 연결해야 합니다. 조직에서 사용되는 특정 데이터 원본의 경우 추가 인터넷 도메인 및 URL에 대한 액세스 권한이 필요할 수 있습니다.

| 행 | 용도 | 대상 | 포트 |
| --- | --- | --- | --- |
| 1 | **필수:** AppSource(Power BI의 내부 또는 외부 앱) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **선택 사항:** 로그인하고 콘텐츠 팩의 데이터 가져오기 | 사용되는 콘텐츠 팩에 따라 다름 | 사용되는 콘텐츠 팩에 따라 다름 |
| 3 | **선택 사항:** 개인 OneDrive에서 파일 가져오기 | [OneDrive 사이트에 대한 필수 URL 및 포트](/onedrive/required-urls-and-ports)를 참조하세요. | 해당 없음 |
| 4 | **선택 사항:** Power BI(60초 후) 자습서 비디오 | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **선택 사항:** PubNub 스트리밍 데이터 원본 | [PubNub 설명서](https://support.pubnub.com/support/solutions/articles/14000043522)를 참조하세요. | 해당 없음 |
| | | |

## <a name="dashboard-and-report-integration"></a>대시보드 및 보고서 통합

Power BI는 특정 엔드포인트에 따라 대시보드 및 보고서를 지원합니다. 아래 테이블 및 연결된 사이트에 있는 엔드포인트에 연결해야 합니다.

| 행 | 용도 | 대상 | 포트 |
| --- | --- | --- | --- |
| 1 | **필수:** Excel 통합 | [Microsoft 365 Common 및 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)에 대한 설명서를 참조하세요. | 해당 없음 |
| | | |

## <a name="power-bi-visuals"></a>Power BI 시각적 개체

Power BI는 특정 엔드포인트에 따라 Power BI 시각적 개체를 보고 액세스합니다. 아래 테이블 및 연결된 사이트에 있는 엔드포인트에 연결해야 합니다.

| 행 | 용도 | 대상 | 포트 |
| --- | --- | --- | --- |
| 1 | **필수:** Marketplace 인터페이스 또는 파일에서 사용자 지정 시각적 개체 가져오기 | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **선택 사항:** Bing Maps | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **선택 사항:** PowerApps | PowerApps 시스템 요구 사항 사이트에서 [필수 서비스 섹션](/powerapps/maker/canvas-apps/limits-and-config#required-services)을 참조하세요. | 해당 없음 |
| 4 | **선택 사항:** Visio | [Microsoft 365 Common 및 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)과 [SharePoint Online 및 비즈니스용 OneDrive](/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business)에 대한 설명서를 참조하세요. | 해당 없음 |
| | | |

## <a name="related-external-sites"></a>관련 외부 사이트

Power BI는 다른 관련 사이트에 연결됩니다. 이러한 사이트는 설명서, 지원, 새로운 기능 요청 등을 호스트합니다. 이러한 사이트에 대한 액세스는 Power BI 기능에 영향을 주지 않으므로 허용 목록에 추가하는 것은 선택 사항입니다.

| 행 | 용도 | 대상 | 포트 |
| --- | --- | --- | --- |
| 1 | **선택 사항:** 커뮤니티 사이트 | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **선택 사항:** 설명서 사이트 | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **선택 사항:** 다운로드 사이트(Power BI Desktop 관련 사이트 등) | download.microsoft.com | TCP 443 |
| 4 | **선택 사항:** 외부 리디렉션 | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **선택 사항:** 아이디어 피드백 사이트| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **선택 사항:** Power BI 사이트 - 방문 페이지, 자세한 내용 링크, 지원 사이트, 다운로드 링크, 파트너 쇼케이스 등 | powerbi.microsoft.com | TCP 443 |
| 7 | **선택 사항:** Power BI 개발자 센터 | dev.powerbi.com | TCP 443 |
| 8 | **선택 사항:** 지원 사이트 | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |