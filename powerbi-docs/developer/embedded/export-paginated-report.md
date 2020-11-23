---
title: Power BI 페이지를 매긴 보고서 API 내보내기
description: 포함된 Power BI 페이지를 매긴 보고서를 내보내는 방법을 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: 908aa715c31396485bcebfaa7227f3241cb02fb8
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94668560"
---
# <a name="export-paginated-report-to-file-preview"></a>페이지를 매긴 보고서를 파일로 내보내기(미리 보기)

`exportToFile` API를 사용하면 REST 호출을 통해 Power BI 페이지를 매긴 보고서를 내보낼 수 있습니다. 지원되는 파일 형식은 다음과 같습니다.
* **.pptx**(PowerPoint)
* **.pdf**
* **.xlsx**(Excel)
* **.dox**(Word)
* **.csv**
* **.xml**
* **.mhtml**
* **이미지**
    * 이미지로 내보내는 경우 `OutputFormat` 형식 설정을 통해 이미지 형식을 설정합니다.
    * 지원되는 OutputFormat 값은 .bmp, emf, .gif, .jpeg, .png 또는 .tiff(기본값)입니다.

## <a name="usage-examples"></a>사용 예

내보내기 기능은 다양한 방법으로 사용할 수 있습니다. 다음은 몇 가지 예입니다.

* **인쇄로 보내기 단추** - 애플리케이션에서 클릭하면 내보내기 작업을 트리거하는 단추를 만듭니다. 작업은 표시된 보고서를 .pdf 또는 .pptx로 내보낼 수 있으며, 완료되면 사용자가 파일을 다운로드로 받을 수 있습니다. 보고서 매개 변수와 형식 설정을 사용하면 필터링된 데이터, 사용자 지정 페이지 크기 및 기타 형식 관련 설정을 포함하여 보고서를 특정 상태로 내보낼 수 있습니다. 이 API는 비동기식이므로 파일을 사용하는 데 어느 정도 시간이 걸릴 수 있습니다.

* **메일 첨부 파일** - .pdf 보고서를 첨부하여 설정된 간격마다 자동화된 메일을 보냅니다. 이 시나리오는 주별 보고서를 임원에게 자동으로 전송하려는 경우에 유용할 수 있습니다.

## <a name="using-the-api"></a>API 사용

이 API는 비동기식입니다. [exportToFile](/rest/api/power-bi/reports/exporttofile) API를 호출하면 내보내기 작업을 트리거합니다. 내보내기 작업을 트리거한 후 [폴링](/rest/api/power-bi/reports/getexporttofilestatus)을 사용하여 완료될 때까지 작업을 추적합니다.

내보내기가 완료되면 폴링 API 호출이 파일을 가져오기 위한 [Power BI URL](/rest/api/power-bi/reports/getfileofexporttofile)을 반환합니다. URL은 24시간 동안 제공됩니다.

## <a name="supported-features"></a>지원되는 기능

### <a name="format-settings"></a>형식 설정

각 파일 형식에 대해 다양한 형식 설정을 지정합니다. 지원되는 속성과 값은 페이지를 매긴 보고서 URL 매개 변수의 [디바이스 정보 매개 변수](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl)와 같습니다.

다음은 보고서 페이지 크기를 사용하여 보고서의 처음 4개 페이지를 .pptx 파일로 내보내는 예제와 보고서의 세 번째 페이지를 .jpeg 파일로 내보내는 예제입니다.

**처음 4개 페이지를 .pptx로 내보내기**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**세 번째 페이지를 .jpeg로 내보내기**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>보고서 매개 변수

`exportToFile` API를 사용하면 보고서 매개 변수 세트를 통해 프로그래밍 방식으로 보고서를 내보낼 수 있습니다. 이 작업은 [보고서 매개 변수](../../paginated-reports/paginated-reports-parameters.md) 기능을 사용하여 수행합니다.

다음은 보고서 매개 변수 값을 설정하는 예제입니다.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>인증

사용자(또는 마스터 사용자) 또는 [서비스 주체](embed-service-principal.md)를 사용하여 인증할 수 있습니다.

### <a name="row-level-security-rls"></a>행 수준 보안(RLS)

RLS(행 수준 보안)가 정의된 Power BI 데이터 세트를 데이터 원본으로 사용하는 경우 특정 사용자에게만 표시되는 데이터를 포함하는 보고서를 내보낼 수 있습니다. 예를 들어 지역 역할로 정의된 판매 보고서를 내보내는 경우 특정 지역만 표시되도록 보고서를 프로그래밍 방식으로 필터링할 수 있습니다.

RLS를 사용하여 내보내려면, 보고서에서 데이터 원본으로 사용하는 Power BI 데이터 세트에 대한 읽기 권한이 있어야 합니다.

다음은 RLS에 유효한 사용자 이름을 제공하는 예제입니다.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}
            ]
      }
}
```
## <a name="ppu-concurrent-requests"></a>PPU 동시 요청
`exportToFile` API는 PPU([사용자 단위 Premium)](../../admin/service-premium-per-user-faq.md) 사용 시 5분에 요청 하나를 허용합니다. 5분 내에 여러 요청(둘 이상)이 제공되면 *요청이 너무 많음*(429) 오류가 발생합니다.

## <a name="code-examples"></a>코드 예제

코드 예제에 사용된 Power BI API SDK는 [여기](https://www.nuget.org/packages/Microsoft.PowerBI.Api)에서 다운로드할 수 있습니다.

내보내기 작업을 만들 때 다음 세 단계를 수행해야 합니다.

1. 내보내기 요청 보내기
2. 폴링
3. 파일 가져오기

이 섹션에서는 각 단계에 대한 예제를 제공합니다.

### <a name="step-1---sending-an-export-request"></a>1단계 - 내보내기 요청 보내기

첫 번째 단계는 내보내기 요청을 보내는 것입니다. 이 예제에서는 특정 페이지 범위, 크기 및 보고서 매개 변수 값의 내보내기 요청을 보냅니다.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"},
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} },
        },
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>2단계 - 폴링

내보내기 요청을 보낸 후 폴링을 사용하여 대기 중인 내보내기 파일이 준비될 때를 식별할 수 있습니다.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>3단계 - 파일 가져오기

폴링이 URL을 반환하면 이 예제를 사용하여 받은 파일을 가져옵니다.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>엔드투엔드 예제

보고서를 내보내는 엔드투엔드 예제입니다. 이 예제는 다음과 같은 단계로 구성됩니다.
1. [내보내기 요청 보내기](#step-1---sending-an-export-request)
2. [폴링](#step-2---polling)
3. [파일 가져오기](#step-3---getting-the-file)

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
           // Error, failure in exporting the report
            return null;
        }

        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>다음 단계

고객 및 조직용 콘텐츠를 포함하는 방법을 검토합니다.

> [!div class="nextstepaction"]
>[파일로 보고서 내보내기](export-to.md)

> [!div class="nextstepaction"]
>[고객에 대한 콘텐츠 포함](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[조직에 포함](embed-sample-for-your-organization.md)
