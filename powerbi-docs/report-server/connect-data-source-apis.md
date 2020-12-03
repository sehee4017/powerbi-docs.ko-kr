---
title: PowerShell을 사용하여 데이터 원본 연결 문자열 변경
description: PowerShell의 API를 사용하여 데이터 원본 연결 문자열 변경 - Power BI Report Server
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.openlocfilehash: 4e1947abe0fa0f17e1db92619f0aa7fba5df5575
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415476"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>PowerShell을 사용하여 Power BI 보고서에서 데이터 원본 연결 문자열 변경 - Power BI Report Server


Power BI Report Server 2020년 10월 릴리스부터 DirectQuery 및 새로 고침을 위해 Power BI 보고서에 대한 연결을 업데이트하는 기능을 사용할 수 있습니다.

> [!IMPORTANT]
> 이 기능은 이전 릴리스에서 설정하는 방법에 관한 호환성이 손상되는 변경이기도 합니다. Power BI Report Server의 2020년 10월 이전 버전을 사용하고 있는 경우 [PowerShell을 사용하여 Power BI 보고서에서 데이터 원본 연결 문자열 변경 - Power BI Report Server 2020년 10월 이전 버전](connect-data-source-apis-pre-oct-2020.md)을 참조하세요.

## <a name="prerequisites"></a>필수 조건:
- [Power BI Report Server 및 Power BI Report Server에 대해 최적화된 Power BI Desktop](https://powerbi.microsoft.com/report-server/)의 2020년 10월 릴리스를 다운로드합니다.
- **향상된 데이터 세트 메타데이터** 를 사용하며, Report Server에 대해 최적화된 Power BI Desktop의 2020년 10월 릴리스에 저장된 보고서.
- 매개 변수가 있는 연결을 사용하는 보고서. 매개 변수가 있는 연결과 데이터베이스가 있는 보고서만 게시 후에 업데이트할 수 있습니다.
- 이 예제에서는 Reporting Services PowerShell 도구를 사용합니다. 새로운 REST API를 사용하여 동일한 결과를 얻을 수 있습니다.

## <a name="create-a-report-with-parameterized-connections"></a>매개 변수가 있는 연결을 사용하여 보고서 만들기
    
1. 서버에 대한 SQL Server 연결을 만듭니다. 아래 예제에서는 localhost를 ReportServer라는 데이터베이스에 연결하고 ExecutionLog에서 데이터를 끌어옵니다.

    :::image type="content" source="media/connect-data-source-apis/sql-server-connect-database.png" alt-text="SQL Server 데이터베이스에 연결":::

    현재 M 쿼리는 다음과 같이 표시됩니다.

    ```
    let
        Source = Sql.Database("localhost", "ReportServer"),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```

2. Power Query 편집기 리본에서 **매개 변수 관리** 를 선택합니다.

    :::image type="content" source="media/connect-data-source-apis/power-query-manage-parameters.png" alt-text="매개 변수 관리 선택":::

1.  servername 및 databasename에 대한 매개 변수를 만듭니다.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-parameters.png" alt-text="매개 변수 관리, servername 및 databasename 설정":::


3. 첫 번째 연결에 대한 쿼리를 편집하고 데이터베이스와 servername을 매핑합니다.

    :::image type="content" source="media/connect-data-source-apis/report-server-map-database-server.png" alt-text="서버와 데이터베이스 이름 매핑":::

    이제 쿼리는 다음과 같이 표시됩니다.

    ```
    let
        Source = Sql.Database(ServerName, Databasename),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```
    
    4. 해당 보고서를 서버에 게시합니다. 이 예제에서 보고서 이름은 executionlogparameter입니다. 다음 이미지는 데이터 원본 관리 페이지의 예입니다.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-data-source-credentials.png" alt-text="데이터 원본 관리 페이지":::

## <a name="update-parameters-using-the-powershell-tools"></a>PowerShell 도구를 사용하여 매개 변수 업데이트

1. PowerShell을 열고 [https://github.com/microsoft/ReportingServicesTools](https://github.com/microsoft/ReportingServicesTools)에 있는 지침에 따라 최신 Reporting Services 도구를 설치합니다.
    
2.  보고서에 대한 매개 변수를 가져오려면 다음 PowerShell 호출을 사용하여 새 REST DataModelParameters API를 사용합니다.

    ```powershell
    Get-RsRestItemDataModelParameters '/executionlogparameter'

        Name         Value
        ----         -----
        ServerName   localhost
        Databasename ReportServer
    ```

3. 이 호출의 결과를 변수에 저장합니다.

    ```powershell
    $parameters = Get-RsRestItemDataModelParameters '/executionlogparameter'
    ```

4. 이 변수는 변경해야 하는 값으로 업데이트됩니다.
5. 이 호출의 결과를 변수에 저장합니다.

    ```powershell
    $parameters[0].Value = 'myproductionserver'
    $parameters[1].Value = 'myproductiondatabase'
    ```

6. 업데이트된 값을 사용하면 `Set-RsRestItemDataModelParameters` commandlet을 사용하여 서버에서 값을 업데이트할 수 있습니다.

    ```powershell
    Set-RsRestItemDataModelParameters -RsItem '/executionlogparameter' -DataModelParameters $parameters
    ```

7. 매개 변수가 업데이트되면 서버는 매개 변수에 바인딩된 모든 데이터 원본을 업데이트합니다. **데이터 원본 편집** 대화 상자로 돌아가면 업데이트된 서버와 데이터베이스에 대한 자격 증명을 설정할 수 있어야 합니다.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-executionlogparameter-dialog.png" alt-text="업데이트된 서버와 데이터베이스에 대한 자격 증명 설정":::

## <a name="next-steps"></a>다음 단계

[Power BI Report Server의 페이지를 매긴 보고서 데이터 원본](connect-data-sources.md) 

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
