---
title: embed 토큰을 생성하기 위한 고려 사항
description: embed 토큰을 생성하기 위한 고려 사항, 제한 사항 및 필요한 권한에 대해 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: 24442f20a0c713deb489cd2461839f2b5da39a30
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197705"
---
# <a name="considerations-when-generating-an-embed-token"></a>embed 토큰 생성 시 고려 사항

[토큰 생성](/rest/api/power-bi/embedtoken)은 웹앱 또는 포털에 Power BI 항목을 포함하기 위한 토큰을 생성할 수 있는 REST API입니다. 토큰은 Power BI 서비스에 대한 요청에 권한을 부여하는 데 사용됩니다.

토큰 생성 API는 앱에서 해당 사용자의 자격 증명(유효한 ID)에 따라 단일 ID(마스터 사용자 또는 서비스 주체)를 사용하여 개별 사용자에 대한 토큰을 생성합니다.

인증에 성공하면 관련 데이터에 대한 액세스 권한이 부여됩니다.

>[!NOTE]
>토큰 생성은 [*고객에 대한 콘텐츠가 포함*](embed-sample-for-customers.md)되는 경우에만 적용됩니다( *앱 소유 데이터* 시나리오라고도 함).

다음 API를 사용하여 토큰을 생성할 수 있습니다.

* [대시보드](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)

* [데이터 세트](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)

* [여러 보고서에 대한 토큰 생성](/rest/api/power-bi/embedtoken/generatetoken)


* [보고서 작성](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)

* [보고서](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)

* [Tile](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

## <a name="workspace-versions"></a>작업 영역 버전

Power BI에는 *클래식* 작업 영역과 *새* 작업 영역의 두 가지 작업 영역 버전이 있습니다. [새 작업 영역 및 클래식 작업 영역 차이점](../../collaborate-share/service-new-workspaces.md#new-and-classic-workspace-differences)에서 이러한 작업 영역 간의 차이점에 대해 자세히 알아볼 수 있습니다.

embed 토큰을 만들 때 다른 작업 영역은 고려 사항이 다르며 다른 사용 권한이 필요합니다.

|                  |*클래식* 작업 영역 |*새* 작업 영역|
|------------------|---------|--------|
|**고려 사항**|<li>데이터 세트와 항목은 같은 작업 영역에 있어야 합니다.</li><li>서비스 주체를 사용할 수 없습니다.</li>  |데이터 세트와 항목은 두 개의 서로 다른 *새* 작업 영역에 있을 수 있습니다. |
|**작업 영역 권한**|마스터 사용자는 작업 영역의 관리자여야 합니다.  |서비스 주체 또는 마스터 사용자는 둘 이상의 작업 영역의 구성원이어야 합니다. |

>[!NOTE]
>* [내 작업 영역](../../consumer/end-user-workspaces.md#types-of-workspaces)에 대한 embed 토큰을 만들 수 없습니다.
>* *항목* 이라는 단어는 대시보드, 타일, 질문 및 답변 또는 보고서와 같은 Power BI 항목을 나타냅니다.

## <a name="securing-your-data"></a>데이터 보안

솔루션을 만들 때 데이터 보안을 위해 다음 두 가지 접근 방식을 고려합니다.

* [작업 영역 기반 격리](embed-multi-tenancy.md#power-bi-workspace-based-isolation)

* [행 수준 보안 기반 격리](embed-multi-tenancy.md#row-level-security-based-isolation)

RLS 접근 방식을 사용하려는 경우 이 문서의 끝에 있는 [RLS 고려 사항 및 제한 사항](generate-embed-token.md#row-level-security)을 검토하세요.

## <a name="token-permissions"></a>토큰 사용 권한

토큰 API 생성에서 *GenerateTokenRequest* 섹션은 토큰 권한을 설명합니다.

>[!NOTE]
>이 섹션에 나열된 토큰 권한은 [여러 보고서에 대한 토큰 생성](/rest/api/power-bi/embedtoken/generatetoken) API에 적용되지 않습니다.

### <a name="access-level"></a>액세스 수준

*accessLevel* 매개 변수를 사용하여 사용자의 액세스 수준을 결정합니다.

* **보기** - 사용자에게 보기 권한을 부여합니다.

* **편집** - 사용자에게 보기 및 편집 권한을 부여합니다(보고서에 대한 embed 토큰을 생성할 때만 적용됨).

    [여러 보고서에 대한 토큰 생성](/rest/api/power-bi/embedtoken/generatetoken) API를 사용하는 경우 *allowEdit* 매개 변수를 사용하여 사용자에게 보기 및 편집 권한을 부여합니다.

* **만들기** - 사용자에게 보고서를 만들 수 있는 권한을 부여합니다(보고서 생성을 위한 embed 토큰을 생성하는 경우에만 적용됨).

    보고서 생성을 위해 *datasetId* 매개 변수도 제공해야 합니다.

### <a name="saving-a-copy-of-the-report"></a>보고서 복사본 저장

*allowSaveAs* 부울을 사용하여 사용자가 보고서를 새 보고서로 저장할 수 있습니다. 기본적으로 이 설정은 *false* 로 설정됩니다.

이 매개 변수는 보고서에 대한 embed 토큰을 생성할 때만 적용됩니다.

### <a name="row-level-security"></a>행 수준 보안

[RLS(행 수준 보안)](embedded-row-level-security.md)를 사용하면 토큰을 생성하는 데 사용하는 서비스 주체 또는 마스터 사용자의 ID와 다른 ID를 사용하도록 선택할 수 있습니다. 이 옵션을 사용하면 대상으로 지정된 사용자에 따라 포함된 정보를 표시할 수 있습니다. 예를 들어 애플리케이션에서 사용자에게 로그인을 요청한 다음, 로그인한 사용자가 영업 직원인 경우 판매 정보만 포함된 보고서를 표시할 수 있습니다.

RLS를 사용하는 경우, 경우에 따라 사용자 ID( *EffectiveIdentity* 매개 변수)를 생략할 수 있습니다. 이를 통해 토큰은 전체 데이터베이스에 액세스할 수 있습니다. 이 메서드는 전체 데이터 세트를 볼 수 있는 권한이 있는 관리자 및 관리자와 같은 사용자에게 액세스 권한을 부여하는 데 사용할 수 있습니다. 그러나 모든 시나리오에서 이 메서드를 사용할 수는 없습니다. 아래 표에는 여러 RLS 유형이 나열되어 있으며 사용자의 ID를 지정하지 않고 사용할 수 있는 인증 방법이 나와 있습니다.

이 표에는 각 RLS 유형에 적용되는 고려 사항 및 제한 사항도 나와 있습니다.

|RLS 형식  |유효 사용자 ID를 지정하지 않고 embed 토큰을 생성할 수 있나요?  |고려 사항 및 제한 사항  |
|---------|---------|---------|
|클라우드 RLS(클라우드 행 수준 보안)      |✔ 마스터 사용자<br/>✖ 서비스 주체          |         |
|RDL(페이지를 매긴 보고서)     |✖ 마스터 사용자<br/>✔ 서비스 주체        |마스터 사용자를 사용하여 RDL용 embed 토큰을 생성할 수 없습니다.         |
|온-프레미스 라이브 연결의 AS(Analysis Services)    |✔ 마스터 사용자<br/>✖ 서비스 주체         |embed 토큰을 생성하는 사용자에게는 다음 사용 권한 중 하나가 필요합니다.<li>게이트웨이 관리자 권한</li><li>Datasource impersonate 권한( *ReadOverrideEffectiveIdentity* )</li>         |
|AS(Analysis Services) Azure 라이브 연결    |✔ 마스터 사용자<br/>✖ 서비스 주체         |embed 토큰을 생성하는 사용자의 ID는 재정의할 수 없습니다. 사용자 지정 데이터를 사용하여 동적 RLS 또는 보안 필터링을 구현할 수 있습니다.<br/><br/>**참고:** 서비스 주체는 개체 ID를 유효한 ID(RLS 사용자 이름)로 제공해야 합니다.         |
|SSO(Single Sign-On)     |✔ 마스터 사용자<br/>✖ 서비스 주체         |유효한 ID 개체에서 ID Blob 속성을 사용하여 명시적 (SSO) ID를 제공할 수 있습니다.         |
|SSO 및 클라우드 RLS     |✔ 마스터 사용자<br/>✖ 서비스 주체         |다음을 제공해야 합니다.<li>유효한 ID 개체의 ID Blob 속성이 있는 명시적 (SSO) ID</li><li>유효한 (RLS) ID(사용자 이름)</li>         |

>[!NOTE]
>서비스 주체는 항상 다음을 제공해야 합니다.
>* RLS 데이터 세트가 있는 모든 항목의 ID입니다.
>* SSO 데이터 세트의 경우 사용자 이름 속성이 정의된 유효한 RLS ID입니다.

## <a name="next-steps"></a>다음 단계

>[!div class="nextstepaction"]
>[앱 등록](register-app.md)

> [!div class="nextstepaction"]
>[고객을 위한 Power BI Embedded](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Azure Active Directory의 애플리케이션 및 서비스 주체 개체](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[서비스 주체가 있는 온-프레미스 데이터 게이트웨이를 사용하는 행 수준 보안](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[서비스 주체 및 인증서를 사용하여 Power BI 콘텐츠 포함](embed-service-principal-certificate.md)