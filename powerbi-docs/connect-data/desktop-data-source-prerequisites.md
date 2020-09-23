---
title: Power BI 데이터 원본 필수 조건
description: Power BI 데이터 원본 필수 조건
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 373249061f39c40ec3a78ba9541575721bd60022
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859638"
---
# <a name="power-bi-data-source-prerequisites"></a>Power BI 데이터 원본 필수 조건
각 데이터 공급자의 경우 Power BI는 개체에 특정 공급자 버전을 지원합니다. Power BI에 사용 가능한 데이터 원본에 대한 자세한 내용은 [데이터 원본](desktop-data-sources.md)을 참조하세요. 다음 표는 이러한 요구 사항을 설명합니다.

| 데이터 소스 | 공급자 | 최소 공급자 버전 | 최소 데이터 원본 버전 | 지원되는 데이터 원본 개체 | 다운로드 링크 |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net(.NET Framework로 작성) |.NET Framework 3.5(전용) |SQL Server 2005+ |테이블/뷰, 스칼라 함수, 테이블 함수 |.NET Framework 3.5 이상에 포함됨 |
| 액세스 권한 |Microsoft Access 데이터베이스 엔진(ACE) |ACE 2010 SP1 |제한 없음 |테이블/뷰 |[다운로드 링크](./desktop-access-database-errors.md) |
| Excel(.xls 파일만) (참고 1 참조) |Microsoft Access 데이터베이스 엔진(ACE) |ACE 2010 SP1 |제한 없음 |테이블, 시트 |[다운로드 링크](./desktop-access-database-errors.md) |
| Oracle(참고 2 참조) |ODP.NET |ODAC 11.2 릴리스 5(11.2.0.3.20) |9.x+ |테이블/뷰 |[다운로드 링크](./desktop-connect-oracle-database.md) |
| | System.Data.OracleClient(.NET Framework에서 작성됨) |.NET Framework 3.5 |9.x+ |테이블/뷰 |.NET Framework 3.5 이상에 포함됨 |
| IBM DB2 |IBM에서 ADO.Net 클라이언트(IBM 데이터 서버 드라이버 패키지의 일부) |10.1 |9.1+ |테이블/뷰 |[다운로드 링크](https://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |커넥터/Net |6.6.5 |5.1 |테이블/뷰, 스칼라 함수 |[다운로드 링크](https://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |NPGSQL ADO.NET 공급자(Power BI Desktop과 함께 제공) |4.0.10 |9.4 |테이블/뷰 |[다운로드 링크](https://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |.NET Data Provider for Teradata |14+ |12+ |테이블/뷰 |[다운로드 링크](https://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |.NET 3.5용 iAnywhere.Data.SQLAnywhere |16+ |16+ |테이블/뷰 |[다운로드 링크](https://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>.xlsx 확장명을 가진 Excel 파일은 별도 공급자 설치가 필요하지 않습니다.

>[!NOTE]
>Oracle 공급자는 Oracle 클라이언트 소프트웨어(버전 8.1.7+)가 필요합니다.
> 
>