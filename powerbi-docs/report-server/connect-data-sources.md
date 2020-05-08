---
title: Power BI Report Server의 페이지를 매긴 보고서 데이터 원본
description: Power BI Report Server에서 페이지를 매긴 보고서(.rdl)가 연결할 수 있는 데이터 원본에 대해 알아봅니다.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 7cb5772e6ccdc1e4036d70f65a3a28210a4f6df1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78260718"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Power BI Report Server의 페이지를 매긴 보고서 데이터 원본
Power BI Report Server의 Reporting Services 페이지를 매긴 보고서는 SQL Server Reporting Services에서 지원되는 동일한 데이터 원본을 지원합니다. [Reporting Services에서 지원하는 데이터 원본](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs) 목록을 참조하세요.

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>UseInstalledUICulture를 사용하여 Oracle 데이터 원본에 연결

Oracle 데이터 원본에 연결하기 위해 Power BI Report Server는 NLS 독립적인 .NET용 Oracle Data Provider(ODP.NET)를 사용합니다.

기본적으로 보고서 서버는 첫 번째 클라이언트의 UI 문화권을 사용하여 ODP.NET를 로드합니다.  따라서 보고서 서버에서 Oracle로의 모든 후속 연결은 서비스를 다시 시작할 때까지 해당 초기 UI 문화권에 있습니다.  이 방법을 사용하면 UI 문화권 서식의 불일치 때문에 보고서를 렌더링하는 데 문제가 발생할 수 있습니다.

Power BI Report Server에서 더 나은 환경을 제공하기 위해 UseInstalledUICulture라는 구성 설정을 도입했습니다. UseInstalledUICulture를 true로 설정하면 보고서 서버는 항상 첫 번째 클라이언트의 문화권 대신 서버 UI 문화권에서 ODP.NET을 로드합니다.
이 설정은 2월 서비스 릴리스부터 Power BI Report Server에서 사용할 수 있습니다.

기능을 사용하도록 설정하려면 아래와 같이 ORACLE 확장 항목 rsreportserver.config 파일을 수정합니다.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>다음 단계
이제 데이터 원본에 연결했으므로 [페이지를 매긴 보고서를 만듭니다](quickstart-create-paginated-report.md).  


궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
