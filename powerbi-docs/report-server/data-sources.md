---
title: Power BI Report Server에서 Power BI 보고서 데이터 원본
description: Power BI 보고서는 여러 데이터 원본에 연결할 수 있습니다. 데이터 사용 방법에 따라 다른 데이터 원본을 사용할 수 있습니다.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 08/04/2020
ms.author: maggies
ms.openlocfilehash: 9dface817b9ec5421ba9ea93abb8037e3e70029d
ms.sourcegitcommit: 4130e5e6947b809df628370cc80c00194243468d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88857790"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Power BI Report Server에서 Power BI 보고서 데이터 원본
Power BI 보고서는 여러 데이터 원본에 연결할 수 있습니다. 데이터 사용 방법에 따라 다른 데이터 원본을 사용할 수 있습니다. DirectQuery 또는 SQL Server Analysis Services에 대한 라이브 연결을 사용하여 데이터를 가져오거나 데이터를 직접 쿼리할 수 있습니다. 일부 데이터 원본은 Power BI Report Server에 최적화된 Power BI Desktop에서 지원되지만 Power BI Report Server에 게시된 Power BI 보고서에 대해서는 최적화되지 않습니다. 두 위치에서 지원되는 데이터 원본에 대해서는 다음 목록을 참조하세요.

이러한 데이터 원본은 Power BI Report Server 내에서 사용되는 Power BI 보고서에 적용됩니다. 페이지가 매겨진 보고서(.rdl)로 지원되는 데이터 원본에 대한 자세한 내용은 [Reporting Services에서 지원되는 데이터 원본](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs)을 참조하세요.

> [!IMPORTANT]
> Power BI Desktop 보고서의 모든 데이터 원본은 예약된 새로 고침 구성을 지원해야 합니다.
>  

## <a name="list-of-supported-data-sources"></a>지원되는 데이터 원본 목록

| **데이터 원본** | **캐시된 데이터** | **예약된 새로 고침** | **라이브/DirectQuery** |
| --- | --- | --- | --- |
| SQL Server 데이터베이스 |예 |예 |예 |
| SQL Server Analysis Services |예 |예 |예 |
| Azure SQL Database |예 |예 |예 |
| Azure SQL Data Warehouse |예 |예 |예 |
| Excel |예 |예 |예 |
| Access 데이터베이스 |예 |예 |예 |
| Active Directory |예 |예 |아니요 |
| Amazon Redshift |예 |아니요 |아니요 |
| Azure Blob Storage |예 |예 |예 |
| Azure Data Lake Store |예 |아니요 |예 |
| Azure HDInsight(HDFS) |예 |아니요 |예 |
| Azure HDInsight(Spark) |예 |아니요 |아니요 |
| Azure Table Storage |예 |예 |예 |
| Dynamics 365(온라인) |예 |아니요 |예 |
| Facebook |예 |아니요 |예 |
| 폴더 |예 |예 |아니요 |
| Google 웹로그 분석 |예 |아니요 |아니요 |
| HDFS(Hadoop 파일) |예 |아니요 |예 |
| IBM DB2 데이터베이스 |예 |예 |예 |
| Impala |예 |아니요 |예 |
| JSON |예 |예 |아니요 |
| Microsoft Exchange |예 |아니요 |아니요 |
| Microsoft Exchange Online |예 |아니요 |예 |
| MySQL 데이터베이스 |예 |예 |예 |
| OData 피드 |예 |예 |아니요 |
| ODBC |예 |예 |예 |
| OLE DB |예 |예 |예 |
| Oracle 데이터베이스 |예 |예 |예 |
| PostgreSQL 데이터베이스 |예 |예 |예 |
| Power BI 서비스 |예 |아니요 |예 |
| R 스크립트 |예 |아니요 |아니요 |
| Salesforce 개체 |예 |아니요 |아니요 |
| Salesforce 보고서 |예 |아니요 |예 |
| SAP Business Warehouse 서버 |예 |예 |예 |
| SAP HANA 데이터베이스 |예 |예 |예 |
| SharePoint 폴더(온-프레미스) |예 |예 |예 |
| SharePoint 목록(온-프레미스) |예 |예 |예 |
| SharePoint Online 목록 |예 |아니요 |아니요 |
| Snowflake |예 |아니요 |예 |
| Sybase 데이터베이스 |예 |예 |아니요 |
| Teradata |예 |예 |예 |
| 텍스트/CSV |예 |예 |예 |
| 웹 |예 |예 |아니요 |
| XML |예 |예 |예 |
| appFigures(베타) |예 |아니요 |예 |
| Azure Analysis Services 데이터베이스 |예 |아니요 |예 |
| Azure Cosmos DB(베타) |예 |아니요 |예 |
| Azure HDInsight Spark(베타) |예 |아니요 |예 |
| Common Data Service(베타) |예 |아니요 |예 |
| comScore Digital Analytix(베타) |예 |아니요 |예 |
| Dynamics 365 for Customer Insights(베타) |예 |아니요 |예 |
| Dynamics 365 Financial(베타) |예 |아니요 |예 |
| GitHub(베타) |예 |아니요 |예 |
| Google BigQuery(베타) |예 |아니요 |예 |
| IBM Informix 데이터베이스(베타) |예 |아니요 |예 |
| IBM Netezza(베타) |예 |아니요 |예 |
| Kusto(베타) |예 |아니요 |예 |
| MailChimp(베타) |예 |아니요 |예 |
| Microsoft Azure Consumption Insights(베타) |예 |아니요 |예 |
| Mixpanel(베타) |예 |아니요 |예 |
| Planview Enterprise(베타) |예 |아니요 |예 |
| Projectplace(베타) |예 |아니요 |예 |
| QuickBooks Online(베타) |예 |아니요 |아니요 |
| Smartsheet |예 |아니요 |예 |
| Spark(베타) |예 |아니요 |예 |
| SparkPost(베타) |예 |아니요 |예 |
| SQL Sentry(베타) |예 |아니요 |예 |
| Stripe(베타) |예 |아니요 |예 |
| SweetIQ(베타) |예 |아니요 |예 |
| Troux(베타) |예 |아니요 |예 |
| Twilio(베타) |예 |아니요 |예 |
| tyGraph(베타) |예 |아니요 |예 |
| Vertica(베타) |예 |아니요 |예 |
| Visual Studio Team Services(베타) |예 |아니요 |예 |
| Webtrends(베타) |예 |아니요 |예 |
| Zendesk(베타) |예 |아니요 |예 |

> [!IMPORTANT]
> 데이터 원본에서 구성된 행 수준 보안은 특정 DirectQuery(SQL Server, Azure SQL Database, Oracle 및 Teradata)에 대해 작동되어야 하며 Kerberos를 가정하는 라이브 연결은 환경에서 적절히 구성됩니다.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>모델 새로 고침을 위해 지원되는 인증 방법 목록

Power BI Report Server는 모델 새로 고침을 위한 OAuth 기반 인증을 지원하지 않습니다. Excel 또는 Access 데이터베이스와 같은 일부 데이터 원본은 파일 또는 웹과 같은 별도의 단계를 거쳐 데이터에 연결합니다.

| **데이터 원본** | **익명 인증** | **키 인증** | **사용자 이름 및 암호** | **Windows 인증** |
| --- | --- | --- | --- | --- |
| SQL Server 데이터베이스 |예 |아니요 |예 |예 |
| SQL Server Analysis Services |예 |아니요 |예 |예 |
| 웹 |예 |아니요 |예 |예 |
| Azure SQL Database |예 |아니요 |예 |아니요 |
| Azure SQL Data Warehouse |예 |아니요 |예 |예 |
| Active Directory |예 |아니요 |예 |예 |
| Amazon Redshift |예 |아니요 |아니요 |아니요 |
| Azure Blob Storage |예 |예 |아니요 |예 |
| Azure Data Lake Store |예 |아니요 |아니요 |예 |
| Azure HDInsight(HDFS) |예 |아니요 |아니요 |예 |
| Azure HDInsight(Spark) |예 |아니요 |아니요 |아니요 |
| Azure Table Storage |예 |예 |아니요 |예 |
| Dynamics 365(온라인) |예 |아니요 |아니요 |예 |
| Facebook |예 |아니요 |아니요 |예 |
| 폴더 |예 |아니요 |아니요 |예 |
| Google 웹로그 분석 |예 |아니요 |아니요 |아니요 |
| HDFS(Hadoop 파일) |예 |아니요 |아니요 |예 |
| IBM DB2 데이터베이스 |예 |아니요 |예 |예 |
| Impala |예 |아니요 |아니요 |아니요 |
| Microsoft Exchange |예 |아니요 |아니요 |아니요 |
| Microsoft Exchange Online |예 |아니요 |아니요 |예 |
| MySQL 데이터베이스 |예 |아니요 |예 |예 |
| OData 피드 |예 |예 |예 |예 |
| ODBC |예 |아니요 |예 |예 |
| OLE DB |예 |아니요 |예 |예 |
| Oracle 데이터베이스 |예 |아니요 |예 |예 |
| PostgreSQL 데이터베이스 |예 |아니요 |예 |예 |
| Power BI 서비스 |예 |아니요 |아니요 |예 |
| R 스크립트 |예 |아니요 |아니요 |아니요 |
| Salesforce 개체 |예 |아니요 |아니요 |아니요 |
| Salesforce 보고서 |예 |아니요 |아니요 |예 |
| SAP Business Warehouse 서버 |예 |아니요 |예 |예 |
| SAP HANA 데이터베이스 |예 |아니요 |예 |예 |
| SharePoint 폴더(온-프레미스) |예 |아니요 |아니요 |예 |
| SharePoint 목록(온-프레미스) |예 |아니요 |아니요 |예 |
| SharePoint Online 목록 |예 |아니요 |아니요 |아니요 |
| Snowflake |예 |아니요 |아니요 |예 |
| Sybase 데이터베이스 |예 |아니요 |예 |예 |
| Teradata |예 |아니요 |예 |예** |
| appFigures(베타) |예 |아니요 |아니요 |예 |
| Azure Analysis Services 데이터베이스(베타) |예 |아니요 |아니요 |예 |
| Azure Cosmos DB(베타) |예 |아니요 |아니요 |예 |
| Azure HDInsight Spark(베타) |예 |아니요 |아니요 |예 |
| Common Data Service(베타) |예 |아니요 |아니요 |예 |
| comScore Digital Analytix(베타) |예 |아니요 |아니요 |예 |
| Dynamics 365 for Customer Insights(베타) |예 |아니요 |아니요 |예 |
| Dynamics 365 Financial(베타) |예 |아니요 |아니요 |예 |
| GitHub(베타) |예 |아니요 |아니요 |예 |
| Google BigQuery(베타) |예 |아니요 |아니요 |예 |
| IBM Informix 데이터베이스(베타) |예 |아니요 |아니요 |예 |
| IBM Netezza(베타) |예 |아니요 |아니요 |예 |
| Kusto(베타) |예 |아니요 |아니요 |예 |
| MailChimp(베타) |예 |아니요 |아니요 |예 |
| Microsoft Azure Consumption Insights(베타) |예 |아니요 |아니요 |예 |
| Mixpanel(베타) |예 |아니요 |아니요 |예 |
| Planview Enterprise(베타) |예 |아니요 |아니요 |예 |
| Projectplace(베타) |예 |아니요 |아니요 |예 |
| QuickBooks Online(베타) |예 |아니요 |아니요 |아니요 |
| Smartsheet |예 |아니요 |아니요 |예 |
| Spark(베타) |예 |아니요 |아니요 |예 |
| SparkPost(베타) |예 |아니요 |아니요 |예 |
| SQL Sentry(베타) |예 |아니요 |아니요 |예 |
| Stripe(베타) |예 |아니요 |아니요 |예 |
| SweetIQ(베타) |예 |아니요 |아니요 |예 |
| Troux(베타) |예 |아니요 |아니요 |예 |
| Twilio(베타) |예 |아니요 |아니요 |예 |
| tyGraph(베타) |예 |아니요 |아니요 |예 |
| Vertica(베타) |예 |아니요 |아니요 |예 |
| Visual Studio Team Services(베타) |예 |아니요 |아니요 |예 |
| Webtrends(베타) |예 |아니요 |아니요 |예 |
| Zendesk(베타) |예 |아니요 |아니요 |예 |

**Teradata에서 LDAP 인증을 사용하는 것(Power BI Desktop에서 명령 프롬프트 명령 ‘setx PBI_EnableTeradataLdap true’를 사용하여 설정)은 모델 새로 고침에서 지원되지 않습니다.

## <a name="list-of-supported-authentication-methods-for-directquery"></a>DirectQuery를 위해 지원되는 인증 방법 목록

Power BI Report Server는 DirectQuery를 위한 OAuth 기반 인증을 지원하지 않습니다.

| **데이터 원본** | **익명 인증** | **키 인증** | **사용자 이름 및 암호** | **Windows 인증** | **Windows 통합 인증** |
| --- | --- | --- | --- | --- | --- |
| SQL Server 데이터베이스 |예 |아니요 |예 |예 |예 |
| SQL Server Analysis Services |예 |아니요 |예 |예 |예 |
| Azure SQL Database |예 |아니요 |예 |아니요 |아니요 |
| Azure SQL Data Warehouse |예 |아니요 |예 |아니요 |예 |
| Oracle 데이터베이스 |예 |아니요 |예 |예 |예 |
| SAP Business Warehouse 서버 |예 |아니요 |예 |아니요 |예 |
| SAP HANA 데이터베이스 |예 |아니요 |예 |예 |예** |
| Teradata |예 |아니요 |예 |예 |예 |

**SAP HANA는 게시된 Power BI Desktop 파일(.pbix)에서 관계형 데이터베이스로 사용하는 경우에만 Windows 통합 인증을 사용하여 DirectQuery를 지원합니다.

## <a name="next-steps"></a>다음 단계

Power BI 서비스의 [Power BI용 데이터 원본](../connect-data/power-bi-data-sources.md)

데이터 원본에 연결했으므로 데이터 원본의 데이터를 사용하여 [Power BI 보고서를 만듭니다](quickstart-create-powerbi-report.md).

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
