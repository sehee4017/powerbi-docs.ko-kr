---
title: 'Power BI의 페이지를 매긴 보고서: FAQ'
description: 이 문서에서는 페이지를 매긴 보고서에 대한 질문과 대답을 제공합니다. 이러한 보고서는 인쇄 또는 PDF 생성에 최적화되어 있고 정교하게 형식 지정된 완벽한 픽셀 출력입니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 10/19/2020
ms.openlocfilehash: 7cba43ff6339ce890ca2f4f1744282648eaf877b
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297903"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Power BI의 페이지를 매긴 보고서: FAQ 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

이 문서에서는 페이지를 매긴 보고서에 대한 질문과 대답을 제공합니다. 이러한 보고서는 인쇄 또는 PDF 생성에 최적화되어 있고 정교하게 형식 지정된 완벽한 픽셀 출력입니다. 이러한 보고서가 “페이지를 매긴” 보고서로 불리는 이유는 여러 페이지에 적합하게 형식 지정되어 있기 때문입니다. 페이지를 매긴 보고서는 SQL Server Reporting Services의 RDL 보고서 기술을 기반으로 합니다. 

이 문서에서는 Power BI Premium의 페이지를 매긴 보고서와 페이지를 매긴 보고서를 제작하는 데 사용되는 독립 실행형 도구인 보고서 작성기에 대해 가지고 있는 여러 가지 일반적인 질문에 대한 답변을 제공합니다. 서비스에 보고서를 게시하려면 Power BI Pro 라이선스가 필요합니다. 작업 영역이 Power BI Premium 용량에 포함된 경우 내 작업 영역 또는 작업 영역에서 페이지를 매긴 보고서를 게시하고 공유할 수 있습니다. 

## <a name="administration"></a>관리

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>페이지를 매긴 보고서에 필요한 크기의 프리미엄 용량은 무엇인가요?

페이지를 매긴 보고서 워크로드는 P1 - P3 SKU에서 사용할 수 있습니다.  임베디드 또는 테스트/개발 시나리오를 위해 A4 – A6 SKU와 함께 사용할 수도 있습니다.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>내 용량의 페이지를 매긴 보고서에 지정할 수 있는 최대 메모리 임계값은 얼마인가요?

이 워크로드에 최대 100%의 메모리를 사용할 수 있습니다.

### <a name="how-does-user-access-work-for-paginated-reports"></a>페이지를 매긴 보고서에 대한 사용자 액세스는 어떻게 이루어지나요?

페이지를 매긴 보고서에 대한 사용자 액세스는 Power BI 서비스의 다른 모든 콘텐츠에 대한 사용자 액세스와 동일합니다. 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>페이지를 매긴 보고서 워크로드를 켜는/끄는 방법은 무엇인가요?

용량 관리자는 용량 관리자 포털 페이지에서 페이지를 매긴 보고서 워크로드를 사용하거나 사용하지 않도록 설정할 수 있습니다.  기본적으로 워크로드는 사용자가 만드는 모든 새 용량에 대해 설정되지만 첫 페이지가 매겨진 보고서를 업로드할 때까지 메모리를 사용하지 않습니다.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>내 테넌트에서 페이지를 매긴 보고서의 사용량을 모니터링할 수 있는 방법은 무엇인가요?

감사 로그의 다음 이벤트 아래에 이 보고서 종류의 사용량이 자세히 나와 있습니다.

- Power BI 보고서 보기
- Power BI 보고서 삭제
- Power BI 보고서 만들기
- 다운로드한 Power BI 보고서

ReportType 필드에는 Power BI 보고서가 아닌 페이지를 매긴 보고서를 식별하는 “PaginatedReport” 값이 있습니다.

감사 로그는 페이지를 매긴 보고서에 대한 다음 이벤트도 제공합니다.

- 게이트웨이에 바인딩된 Power BI 데이터 세트
- Power BI 데이터 원본 검색
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>프리미엄 용량 모니터링 앱을 통해 이 워크로드를 모니터링할 수 있나요?

예, 모니터링은 Power BI 데이터 세트에 대한 동일한 관련 세부 정보가 포함된 새 탭으로 사용할 수 있습니다.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>페이지를 매긴 보고서를 만들고 게시하려면 Pro 라이선스가 필요한가요?

작업 영역이 프리미엄 용량에 포함된 경우 Pro 라이선스 없이 내 작업 영역에 페이지를 매긴 보고서를 업로드할 수 있습니다.  다른 작업 영역의 경우 콘텐츠를 작성하고 게시하려면 Pro 라이선스가 있어야 합니다. Pro 라이선스가 없어도 Power BI 보고서 작성기를 다운로드하여 사용할 것을 권장하지만 Pro 라이선스가 없으면 생성한 페이지를 매긴 보고서를 게시할 수 없습니다. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>작업 영역에 페이지를 매긴 보고서가 있는데 페이지를 매긴 보고서 워크로드가 꺼져 있는 경우 어떻게 하나요?

오류 메시지가 수신되지만 워크로드가 다시 켜질 때까지 보고서를 볼 수 없습니다. 작업 영역에서 보고서를 삭제할 수는 있습니다.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-that-support-paginated-reports"></a>페이지를 매긴 보고서를 지원하는 각 Premium SKU의 기본 메모리는 얼마인가요?

페이지를 매긴 보고서에 대한 각 Premium SKU의 기본 메모리는 다음과 같습니다.

- **P1/A4** : 기본값 20%, 최솟값 10%
- **P2/A5** : 기본값 20%, 최솟값 5%
- **P3/A6** : 기본값 20%, 최솟값 2.5%

Power BI 관리자는 관리 포털에서 기본 최대 메모리 비율을 수정할 수 있습니다. **용량 설정** 탭의 **Power BI Premium** 에서 **페이지를 매긴 보고서** 워크로드 섹션을 참조하세요.

:::image type="content" source="media/paginated-reports-faq/paginated-reports-capacity-settings.png" alt-text="페이지를 매긴 보고서 용량 설정 탭":::

## <a name="general"></a>일반

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>페이지를 매긴 보고서와 Power BI 보고서를 사용해야 하는 경우를 비교하면 각각 언제인가요?

페이지를 매긴 보고서는 인쇄 또는 PDF 생성에 최적화된 정교한 서식의 완벽한 픽셀 출력이 요구되는 시나리오에 가장 적합합니다.  손익 계산서가 페이지를 매긴 보고서로 만들 보고서 종류의 좋은 예입니다.  

Power BI 보고서는 탐색 및 대화형 작업에 최적화되어 있습니다.  여러 영업 사원이 특정 지역/산업/고객에 대해 동일한 보고서의 데이터를 분할하여 수치가 어떻게 변경되는지 확인하려는 영업 보고서로는 Power BI 보고서가 가장 적합합니다.

자세한 내용은 [Power BI의 페이지를 매긴 보고서가 필요한 경우](../guidance/report-paginated-or-power-bi.md)를 참조하세요.

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>설명서는 Power BI 보고서 작성기가 기본 작성 도구라고 표시됩니다. Power BI용 SQL Server Data Tools에서 페이지를 매긴 보고서를 만들 수 있나요?

예. 하지만 Power BI 서비스에서는 한 번에 하나의 항목만 업로드할 수 있으므로 작성자가 SSDT(SQL Server Data Tools)와 함께 사용하는 시나리오 중 다수는 아직 지원되지 않습니다. 이 FAQ 뒷부분에 제공된 [지원되지 않는 기능의 전체 목록](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)을 참조하세요.  

### <a name="what-versions-of-report-builder-do-you-support"></a>지원되는 보고서 작성기 버전은 무엇인가요?

페이지를 매긴 보고서를 위한 Power BI 서비스의 기본 제작 도구로 Power BI 보고서 작성기를 출시했습니다. [Power BI 보고서 작성기는 Microsoft 다운로드 센터에서](https://aka.ms/pbireportbuilder) 설치할 수 있습니다.

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>SQL Server Reporting Services에 저장한 기존 보고서를 Power BI로 이동하려면 어떻게 해야 하나요?

이제 GitHub 프로젝트에서 SQL Server Reporting Services의 콘텐츠를 Power BI로 마이그레이션할 수 있도록 지원합니다.  [https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)에서 세부 정보를 확인하고 도구를 다운로드하세요.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>보고서를 열어서 서비스에 직접 게시할 수 있나요?

예. 보고서를 열어서 Power BI 보고서 작성기에서 서비스에 직접 게시할 수 있도록 지원을 추가했습니다.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Power BI에서 아직 지원되지 않는 SSRS의 페이지를 매긴 보고서 기능은 무엇인가요?

현재 페이지를 매긴 보고서에서는 다음 항목을 지원하지 않습니다.

- 공유 데이터 원본
- 공유 데이터 세트
- 다른 보고서로 드릴스루 및 클릭스루
- 연결된 보고서
- 사용자 지정 글꼴

토글/정렬을 제외하고 Power BI 서비스에서 지원되지 않는 기능이 있는 파일을 업로드하려고 하면 오류 메시지를 받게 됩니다.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>페이지를 매긴 보고서에 대해 현재 지원되는 데이터 원본은 무엇인가요?

데이터 원본 목록을 보려면 [Power BI 페이지를 매긴 보고서의 지원되는 데이터 원본](paginated-reports-data-sources.md) 문서를 참조하세요. 

### <a name="what-authentication-methods-do-you-support"></a>지원되는 인증 방법은 무엇인가요?

Azure Analysis Services, Azure SQL Database 및 Power BI 데이터 원본에 대해 SSO를 지원합니다.  Azure SQL Database 및 Azure Analysis Services에 대해 OAuth도 지원합니다.  기타 데이터 원본의 경우 현재는 포털 또는 게이트웨이에 사용자 이름 및 암호를 데이터 원본과 함께 저장해야 합니다.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>내 페이지를 매긴 보고서의 데이터 원본으로 Power BI 데이터 세트를 사용할 수 있나요?

예. 페이지를 매긴 보고서의 데이터 원본으로 Power BI 데이터 세트를 지원합니다.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>게이트웨이를 통해 저장 프로시저를 사용할 수 있나요?

예, 게이트웨이를 통한 저장 프로시저는 SQL Server 데이터 원본에 대해 지원되며 매개 변수를 사용하는 경우도 포함됩니다.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Power BI 서비스에서 내 보고서에 사용할 수 있는 내보내기 형식은 무엇인가요?

Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, .CSV, XML 및 MHTML로 내보낼 수 있습니다.

### <a name="can-i-print-paginated-reports"></a>페이지를 매긴 보고서를 인쇄할 수 있나요?

예. 인쇄는 새롭고 향상된 인쇄 미리 보기 환경을 포함하여 페이지를 매긴 보고서에 사용할 수 있습니다. 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>페이지를 매긴 보고서를 메일 구독을 통해 받아볼 수 있나요?

예. 메일 구독은 페이지를 매긴 보고서에서 완전 지원되며 6가지 파일 형식 및 매개 변수 값을 지원합니다.

### <a name="can-i-run-custom-code-in-my-report"></a>내 보고서에서 사용자 지정 코드를 실행할 수 있나요?

예, SSRS에서처럼 보고서에서 코드를 실행하는 기능을 지원합니다.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Power BI Embedded를 사용하여 호스트하는 앱에 페이지를 매긴 보고서를 포함할 수 있나요?

보안 포함 지원을 비롯한 SaaS 포함은 이미 사용할 수 있습니다. PaaS를 포함하는 경우 [고객을 위해 애플리케이션에 페이지를 매긴 Power BI 보고서 포함](../developer/embedded/embed-paginated-reports-customers.md) 자습서를 참조하세요.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Power BI 보고서에서 페이지를 매긴 보고서로 드릴스루할 수 있나요?

예, 페이지를 매긴 보고서와 URL 매개 변수를 함께 사용하여 수행할 수 있습니다.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Power BI 앱을 통해 내 페이지를 매긴 보고서 콘텐츠를 공유할 수 있나요?

예, v1과 v2 모두 작업 영역에서 페이지를 매긴 보고서를 앱으로 배포하는 것을 지원됩니다. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-report-tiles-to-dashboards-work-with-paginated-reports"></a>보고서 타일을 대시보드에 고정하는 기능과 같이, Power BI의 다른 보고서 관련 기능이 페이지를 매긴 보고서에서도 작동합니까?

가능한 한 보고서가 서비스의 동일한 주요 시나리오를 지원하도록 할 계획입니다.  보고서를 작성하는 도구가 달라도 소비자 관점에서는 포털의 목록에 있는 또 다른 보고서인 경우가 이상적입니다. 필요한 작업을 달성할 수 있으면 어떻게 만들어졌는지는 중요시하지 않습니다.  이 기능 패리티의 좋은 예가 계획된 주석 지원입니다. 기능 자체는 보고서 종류마다 약간 다르게 작동할 수 있으나 보고서 종류 둘 다에 대해 주석을 사용할 수 있습니다.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Power BI 서비스의 페이지를 매긴 보고서에 대한 보고서 뷰어 컨트롤이 있나요?

아니요. 현재 보고서 뷰어 컨트롤은 제공되지 않습니다.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Power BI 서비스의 새 홈 환경에서 페이지를 매긴 보고서를 검색할 수 있나요?

예. 이제 홈에서 페이지를 매긴 보고서를 검색할 수 있습니다.  또한 새 홈 환경의 다른 부분에 보고서가 표시됩니다.

## <a name="considerations-and-troubleshooting"></a>고려 사항 및 문제 해결
페이지를 매긴 보고서에서 DateTime 필드를 사용할 때 주의해야 하는 사항은 다음과 같습니다.

- 현재 DateTime 매개 변수와 관련된 몇 가지 세계화 제한 사항이 있습니다. Power BI 서비스의 모든 DateTime 매개 변수는 Power BI Report Builder에서 DataTime을 설계하는 방법에 관계없이 미국 형식(MM/DD/YYYY)으로 가져옵니다.

Power BI 서비스에서 페이지가 매겨진 보고서를 볼 때 세션 시간이 초과되어 사용자에게 다음 알림이 표시될 수 있습니다.

:::image type="content" source="media/paginated-reports-faq/expired-session-notification.png" alt-text="페이지를 매긴 보고서 세션 만료 알림":::

- 세션은 60분 동안 비활성된 후 또는 디바이스가 잠겨 있거나, 비활성화 상태이거나, 보고서가 브라우저의 활성 탭에 보고서가 표시되지 않을 때 시간이 초과됩니다.

## <a name="next-steps"></a>다음 단계

- [Microsoft 다운로드 센터에서 Power BI 보고서 작성기 설치](https://aka.ms/pbireportbuilder)
- [자습서: 페이지를 매긴 보고서 만들기](paginated-reports-quickstart-aw.md)
