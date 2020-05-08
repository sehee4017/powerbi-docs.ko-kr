---
title: Power BI를 통해 Snowflake에 연결
description: Power BI용 SSO를 사용한 Snowflake
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e5519e30be30d6367791d1b6822196b407a21b1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "77576861"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Power BI 서비스에서 Snowflake에 연결

## <a name="introduction"></a>소개

Power BI 서비스에서 Snowflake에 연결하는 것은 AAD에 대한 추가 기능이 제공(SSO 옵션 포함)된다는 점에서만 다른 커넥터와 다릅니다. 통합의 부분마다 Snowflake, Power BI 및 Azure에서 서로 다른 관리 역할이 필요합니다. SSO를 사용하지 않고 AAD 인증을 사용하도록 선택할 수도 있습니다. 기본 인증은 서비스의 다른 커넥터와 유사하게 작동합니다.

AAD 통합을 구성하고 필요에 따라 SSO를 사용하는 데 관심이 있는 경우:
* Snowflake 관리자인 경우 Snowflake 설명서의 [Power BI SSO to Snowflake - Getting Started](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html)(Snowflake에 Power BI SSO 사용 - 시작) 문서를 참조하세요.
* (SSO) Power BI 관리자인 경우 'Power BI 서비스 구성 - 관리자 포털' 섹션을 확인하세요.
* (SSO) Power BI 데이터 세트 작성자인 경우 'Power BI 서비스 구성 - 데이터 세트 사용' 섹션을 확인하세요.

## <a name="power-bi-service-configuration"></a>Power BI 서비스 구성

### <a name="admin-portal"></a>관리 포털

SSO를 사용하도록 설정하려면 테넌트 관리자가 관리 포털로 이동하고 Power BI AAD 자격 증명을 Snowflake로 전송하도록 승인해야 합니다.

![Snowflake SSO의 테넌트 관리자 설정](media/service-connect-snowflake/snowflakessotenant.png)

“관리 포털”로 이동하고, “테넌트 설정” 사이드바 항목을 선택하고, “통합 설정”까지 아래로 스크롤하면 “Snowflake SSO” 옵션이 표시됩니다.

앞서 언급한 대로, AAD 토큰을 Snowflake 서버로 전송하는 것에 동의하려면 이 기능을 수동으로 사용하도록 설정해야 합니다. 사용하도록 설정하려면 '사용 안 함' 토글을 클릭하고, [적용]을 누르고, 설정 변경이 적용될 때까지 기다립니다. 서비스가 구성을 전파하는 데 최대 한 시간이 걸릴 수 있습니다.

이 작업이 완료되면 SSO를 통해 보고서를 사용할 수 있습니다.

### <a name="configuring-a-dataset-with-aad"></a>AAD를 사용하여 데이터 세트 구성

Snowflake 커넥터를 기반으로 하는 보고서가 웹에 게시된 후에는 Power BI 웹 서비스에서 데이터 세트 작성자가 적절한 작업 영역으로 이동하고, ‘데이터 세트’를 선택하고, 관련 데이터 세트 옆에 있는 추가 작업의 ‘...’ 메뉴에서 ‘설정’을 선택합니다.

Power BI의 작동 방식으로 인해 SSO는 온-프레미스 데이터 게이트웨이를 통해 실행되는 데이터 원본이 없는 경우에만 작동합니다.

* 데이터 모델에서 Snowflake 원본만 사용하는 경우 온-프레미스 데이터 게이트웨이를 사용하지 않도록 선택하면 SSO를 사용할 수 있습니다.
* 다른 원본과 함께 Snowflake 원본을 사용하는 경우 온-프레미스 데이터 게이트웨이를 사용하는 원본이 없으면 SSO를 사용할 수 있습니다.
* 온-프레미스 데이터 게이트웨이를 통해 Snowflake 원본을 사용하는 경우 현재 AAD 자격 증명이 지원되지 않습니다. 이 기능은 전체 Power BI IP 범위가 아닌 게이트웨이가 설치되어 있는 단일 IP에서 VNet에 액세스하려는 경우에 사용될 수 있습니다.
* 게이트웨이가 필요한 다른 원본과 함께 Snowflake 원본을 사용하는 경우 온-프레미스 데이터 게이트웨이를 통해 Snowflake를 사용해야 하며 SSO를 사용할 수 없습니다.

온-프레미스 데이터 게이트웨이를 사용하는 방법에 대한 자세한 내용은 [온-프레미스 데이터 게이트웨이란?](https://docs.microsoft.com/power-bi/service-gateway-onprem) 문서를 참조하세요.

게이트웨이를 사용하지 않는 경우에는 모두 설정됩니다. 온-프레미스 데이터 게이트웨이에 Snowflake 자격 증명이 구성되어 있지만 모델에서 해당 데이터 원본만 사용하는 경우 데이터 세트 설정 페이지에서 토글을 클릭하여 해당 데이터 모델에 대해 게이트웨이를 끌 수 있습니다.

![게이트웨이를 해제하는 데이터 세트 설정](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

데이터 세트 작성자는 ‘데이터 원본 자격 증명’을 선택하고 로그인해야 합니다. 데이터 세트는 기본 자격 증명 또는 OAuth2(AAD) 자격 증명을 사용하여 Snowflake에 로그인 할 수 있습니다. AAD를 사용하도록 선택하면 데이터 세트가 SSO를 사용할 수 있습니다. 이 첫 번째 사용자가 데이터 세트를 위해 Snowflake에 로그인하려는 경우 해당 사용자는 데이터를 검색하는 데 사용된 Oauth2 자격 증명을 다른 사용자가 사용하도록 하는 옵션을 선택해야 합니다. 그러면 AAD SSO가 사용하도록 설정됩니다. 초기 사용자가 기본 인증 또는 OAuth2(AAD)를 사용하여 로그인하는지 여부와 관계없이 AAD 자격 증명은 SSO를 위해 전송됩니다. 

![Snowflake SSO의 데이터 세트 설정](media/service-connect-snowflake/snowflakessocredui.png)

이 작업이 완료되면 추가 사용자는 자동으로 AAD 인증을 사용하여 해당 Snowflake 데이터 세트의 데이터에 연결합니다.

SSO를 사용하도록 설정하지 않으면, 대부분의 다른 Power BI 보고서처럼 보고서를 새로 고치는 사용자는 로그인한 사용자의 자격 증명을 사용합니다.

### <a name="troubleshooting"></a>문제 해결

통합 관련 문제가 발생하는 경우에는 Snowflake [문제 해결 가이드](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting)를 참조하세요.

