---
title: 미국 정부 기관 고객용 Power BI - 개요
description: 미국 정부 고객은 Microsoft 365 정부 플랜에 Power BI Pro 구독을 추가할 수 있습니다. 이 서비스 설명에서 기능 가용성을 등록, 연결, 검토하는 방법을 알아봅니다.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/30/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: fe4f9c54b45035cc22f2e582a75ba98d648c549d
ms.sourcegitcommit: 8861dac6724202a5b3be456a6aff8f3584e0cccf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132370"
---
# <a name="power-bi-for-us-government-customers"></a>미국 정부 기관 고객용 Power BI

이 문서는 Microsoft 365 정부 플랜의 일부로 Power BI를 배포하는 정부 기관 고객을 위한 것입니다. 정부 플랜은 미국 규정 준수 및 보안 표준을 충족해야 하는 조직의 고유한 요구 사항을 위해 설계되었습니다. 미국 정부 기관 고객을 위해 고안된 Power BI 서비스는 상용 Power BI 서비스 버전과 다릅니다. 이러한 기능 차이는 다음 섹션에 설명되어 있습니다.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Microsoft 365 정부 플랜에 Power BI 추가

Power BI 미국 정부 기관 구독을 획득하고 사용자에게 라이선스를 할당하려면 먼저 Microsoft 365 정부 플랜에 등록해야 합니다. 조직에 이미 Microsoft 365 정부 플랜이 있는 경우 [정부 고객용 Power BI Pro 구독](#buy-a-power-bi-pro-subscription-for-government-customers)으로 건너뜁니다.

### <a name="enroll-in-a-microsoft-365-government-plan"></a>Microsoft 365 정부 플랜에 등록

신규 고객은 Microsoft 365 정부 플랜에 등록하기 전에 조직의 자격 유효성을 검사해야 합니다.  먼저 [정부 기관용 Microsoft 365 자격 유효성 검사 양식](https://www.microsoft.com/microsoft-365/government/eligibility-validation)을 작성합니다. 조직에 적합한 플랜을 선택하려면 [Microsoft 365 미국 정부 서비스 설명](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government)을 참조하세요.

> [!NOTE]
> 이미 상용 환경에 Power BI를 배포했고 미국 정부 클라우드로 마이그레이션하려는 경우 Microsoft 365 정부 플랜에 새로운 Power BI Pro 구독을 추가해야 합니다. 다음으로 상용 데이터를 미국 정부 기관용 Power BI 서비스에 복제하고 사용자 계정에서 상용 라이선스 할당을 제거한 다음 사용자 계정에 Power BI Pro 정부 기관 라이선스를 할당합니다.
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>정부 고객용 Power BI Pro 구독 구입

Microsoft 365를 배포한 후 Power BI Pro 구독을 추가할 수 있습니다. [미국 정부 기관 등록](service-govus-signup.md)의 단계별 지침에 따라 Power BI Pro 정부 서비스를 구매합니다. Power BI를 사용해야 하는 모든 사용자에게 충분한 라이선스를 구입한 다음 개별 사용자 계정에 할당합니다.

> [!IMPORTANT]
> Power BI 미국 정부는 ‘무료’ 라이선스로 제공되지 않습니다. 정부 커뮤니티 클라우드에 액세스하려면 각 사용자에게 ‘Pro’ 라이선스가 할당되어야 합니다. 무료 라이선스가 할당된 사용자 계정은 상용 클라우드에만 액세스할 권한이 있으며, 인증 및 액세스 문제가 발생합니다. Power BI Premium을 구매한 경우 사용자 액세스를 사용하기 위해 Pro 라이선스를 할당할 필요가 없습니다.  보고서가 프리미엄 용량에 게시되는 경우 조직의 사용자가 공유되는 보고서에 액세스할 수 있습니다. 라이선스 유형 간의 차이점을 검토하려면 [라이선스 유형별 Power BI 서비스 기능](../fundamentals/service-features-license-type.md)을 참조하세요.
>

## <a name="government-cloud-instances"></a>정부 클라우드 인스턴스

Microsoft 365는 다양한 규정 준수 요구 사항을 충족하기 위해 다양한 정부 기관용 환경을 제공합니다. 각 등록에 대한 자세한 내용은 다음을 참조하세요.

* [Microsoft 365 GCC(정부 커뮤니티 클라우드)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc)는 연방, 주, 지방 정부를 위해 설계되었습니다.

* [Microsoft 365 GCC High(정부 커뮤니티 클라우드 높음)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod)는 연방 기관, 방위 산업, 항공 우주 산업 및 제어되는 미분류 정보를 보유하는 기타 조직을 위해 설계되었습니다. 이 환경은 국가 안보 조직 및 ITAR(국제 무기 거래 규정) 데이터 또는 DFARS(국방 연방 획득 규칙 부록) 요구 사항이 있는 회사에 적합합니다.

* [Microsoft 365 DoD 환경](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod)은 미국 국방부 전용으로 설계되었습니다.


## <a name="sign-in-to-power-bi-for-us-government"></a>미국 정부 기관용 Power BI에 로그인

Power BI에 연결하기 위한 URL은 정부 사용자와 상용 사용자 간에 다릅니다. Power BI에 로그인하려면 다음 URL을 사용하세요.

| 상용 버전  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

계정이 둘 이상의 클라우드에 설정되어 있을 수 있습니다. 계정이 이런 방식으로 설정된 경우 Power BI Desktop에 로그인할 때 연결할 클라우드를 선택할 수 있습니다.

## <a name="allow-connections-to-power-bi"></a>Power BI에 대한 연결 허용

Power BI 서비스를 사용하려면 인터넷에서 필요한 엔드포인트에 대한 연결을 허용해야 합니다. 자체 네트워크, Power BI 및 기타 종속 서비스 간에 통신을 가능하게 하려면 해당 대상에 연결할 수 있어야 합니다.

아래 표에서는 일반 사이트 사용을 위해 Power BI 서비스에 대한 연결을 가능하게 하는 허용 목록에 추가할 필요한 엔드포인트를 나열합니다. 해당 엔드포인트는 미국 정부 클라우드에 고유합니다. Power BI 서비스에서는 TCP 포트 443이 나열된 엔드포인트에 대해 열려야 합니다. 데이터, 대시보드 및 보고서 통합, Power BI 시각적 개체 및 기타 선택적 서비스를 가져오기 위한 엔드포인트는 미국 정부 클라우드에 고유하지 않습니다. 관련 URL을 허용 목록에 추가하려면 [허용 목록에 Power BI URL 추가](power-bi-whitelist-urls.md)를 참조하세요.

Power BI의 인증, ID 및 관리는 Microsoft 365 서비스에 대한 연결에 따라 달라집니다. 또한 감사 로그를 보려면 Microsoft 365에 연결해야 합니다. 해당 서비스의 엔드포인트를 식별하려면 아래 표에서 Microsoft 365 통합을 참조하세요.

### <a name="power-bi-urls-for-general-site-usage"></a>일반 사이트 사용을 위한 Power BI URL

|  목적 | 대상 |
| ---- | ----- |
| 백 엔드 API | **GCC** : api.powerbigov.us |
| | **GCC-High** : api.high.powerbigov.us |
| | **DoD** : api.mil.powerbi.gov.us |
| 백 엔드 API | **GCC** : *analysis.usgovcloudapi.net |
| | **GCC High** : *.high.analysis.usgovcloudapi.net |
| | **DoD** : *.mil.analysis.usgovcloudapi.net |
| 백 엔드 API | **All** : *.pbidedicated.usgovcloudapi.net |
| CDN(콘텐츠 전송 네트워크) | **GCC** : gov.content.powerapps.us |
| | **GCC High** : high.content.powerapps.us |
| | **DoD** : mil.content.powerapps.us |
| Microsoft 365 통합 | **GCC** : [전 세계 엔드포인트](/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| | **GCC High** : [미국 정부 GCC High 엔드포인트](/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints) |
| | **DoD** : [미국 정부 DOD 엔드포인트](/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints) |
| 포털 |**GCC** : *.powerbigov.us |
| | **GCC-High** : *.high.powerbigov.us |
| | **DoD** : *.mil.powerbigov.us |
| 서비스 원격 분석 | **All** : dc.services.visualstudio.us |
| 정보 메시지(선택) | **All** : dynmsg.modpim.com |
| NPS 설문 조사(선택 사항) | **All** : nps.onyx.azure.net |

## <a name="connect-government-and-global-azure-cloud-services"></a>정부 및 글로벌 Azure 클라우드 서비스 연결

Azure는 여러 클라우드에 분산되어 있습니다. 기본적으로 클라우드별 인스턴스와의 연결을 열도록 방화벽 규칙을 사용할 수 있지만 클라우드 간 네트워킹은 다릅니다.  퍼블릭 클라우드의 서비스와 정부 커뮤니티 클라우드의 서비스가 통신하려면 특정 방화벽 규칙을 구성해야 합니다. 예를 들어 Power BI의 정부 클라우드 배포에서 SQL 데이터베이스의 퍼블릭 클라우드 인스턴스에 액세스하려면 SQL 데이터베이스에 방화벽 규칙이 필요합니다. 다음 데이터 센터의 Azure Government 클라우드와의 연결을 허용하도록 SQL 데이터베이스에서 특정 방화벽 규칙을 구성합니다.

* USGov 아이오와
* USGov 버지니아
* USGov 텍사스
* USGov 애리조나
* US DoD 동부
* US DoD 중부

미국 정부 클라우드 IP 범위를 얻으려면 [Azure IP 범위 및 서비스 태그 - 미국 정부 클라우드](https://www.microsoft.com/download/details.aspx?id=57063) 파일을 다운로드합니다. Power BI 및 파워 쿼리의 범위가 둘 다 나열됩니다.

Microsoft Azure Government 클라우드 서비스에 관한 자세한 내용은 [Azure Government 설명서](/azure/azure-government/)를 참조하세요.

SQL 데이터베이스에 대한 방화벽을 설정하려면 [IP 방화벽 규칙 만들기 및 관리](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules)를 참조하세요.

## <a name="power-bi-feature-availability"></a>Power BI 기능 가용성

정부 클라우드 고객의 요구 사항을 수용하기 위해 정부 플랜과 상용 플랜에는 몇 가지 차이점이 있습니다. Microsoft의 목표는 일반 공급 30일 이내에 정부 클라우드에서 모든 기능을 사용할 수 있도록 하는 것입니다. 경우에 따라 기본 종속성으로 인해 기능을 사용하지 못할 수 있습니다.

다음 표에는 특정 정부 환경에서 사용할 수 없는 기능이 나와 있습니다. 릴리스가 계획된 경우 예상 가용성이 포함됩니다.

|기능 |GCC |GCC High |DoD|
|------|------|------|------|
|[정부와 상업용 클라우드 간 Azure B2B Collaboration](service-admin-azure-ad-b2b.md)<sup>1</sup>|![사용 가능](../media/yes.png)|![사용할 수 없음](../media/no.png)|![사용할 수 없음](../media/no.png)|
|[Power BI 웹 파트를 사용하여 SharePoint Online에 포함](/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![사용 가능](../media/yes.png)|![사용 가능](../media/yes.png)|![사용할 수 없음](../media/no.png)|
|[데이터 기반 경고를 위한 Power Automate 연결](../connect-data/power-bi-data-sources.md)|![사용 가능](../media/yes.png)|![사용 가능](../media/yes.png)|![사용할 수 없음](../media/no.png)|
|[Teams의 Power BI 탭](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>2</sup>|![사용 가능](../media/yes.png)|![사용할 수 없음](../media/no.png)|![사용할 수 없음](../media/no.png)|
|[대형 모델](service-premium-large-models.md) | 2020 Q4 |2020 Q4| ![사용할 수 없음](../media/no.png) |
|[데이터 흐름 - SQL 컴퓨팅 엔진 최적화](../transform-model/service-dataflows-enhanced-compute-engine.md) | 2020 Q4 |2020 Q4| ![사용할 수 없음](../media/no.png) |
|[데이터 흐름 - 직접 쿼리](../transform-model/service-dataflows-directquery.md) | 2020 Q4 |2020 Q4|![사용할 수 없음](../media/no.png)|
|[데이터 보호(MIP 레이블)](service-security-sensitivity-label-overview.md)|2020 Q4|2020 Q4 |2020 Q4|
|[템플릿 앱](../connect-data/service-template-apps-overview.md)<sup>3</sup>|2020 Q4 |2020 Q4| 2020 Q4|
|[사용자 지정 시각적 개체](../developer/visuals/power-bi-custom-visuals.md)<sup>3</sup>|2020 Q4 |2020 Q4| 2020 Q4|
|[통화 품질 데이터 커넥터](/microsoftteams/cqd-power-bi-connector)|![사용할 수 없음](../media/no.png)|![사용할 수 없음](../media/no.png)|![사용할 수 없음](../media/no.png)|
|[Bring Your Own Storage(Azure Data Lake Gen 2)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md)|![사용할 수 없음](../media/no.png)|![사용할 수 없음](../media/no.png)|![사용할 수 없음](../media/no.png)|
|[QR 코드 생성](../create-reports/service-create-qr-code-for-tile.md)|![사용할 수 없음](../media/no.png)|![사용할 수 없음](../media/no.png)|![사용할 수 없음](../media/no.png)|

<sup>1</sup> B2B Collaboration을 GCC에 사용할 수 있지만 외부 사용자는 해당 환경에서 라이선스를 발급받아야 합니다. 상업용 클라우드 라이선스는 GCC에서 유효하지 않습니다. 미국 정부용 B2B Collaboration의 알려진 제한 사항에 관한 자세한 내용은 [Azure Government 및 글로벌 Azure 비교](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2)를 참조하세요.

<sup>2</sup> Teams for GCC의 Power BI 환경은 제한적이고, 클래식 작업 영역에서만 작동하며, [Microsoft Teams에 Power BI 콘텐츠 포함](../collaborate-share/service-embed-report-microsoft-teams.md)에 설명된 향상된 기능을 포함하지 않습니다.

<sup>3</sup> 릴리스의 템플릿 앱 및 사용자 지정 시각적 개체에 대한 기능은 정부 클라우드에서 제한됩니다. 특정 제한 사항에 대한 자세한 내용은 릴리스에 게시될 예정입니다.

## <a name="next-steps"></a>다음 단계

* [미국 정부 기관용 Power BI 등록](service-govus-signup.md)
* [Microsoft Power Apps US Government](/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](/power-automate/us-govt)
* [Power BI 미국 정부 데모](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)
