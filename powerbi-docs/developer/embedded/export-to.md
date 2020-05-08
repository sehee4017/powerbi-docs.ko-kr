---
title: Power BI 보고서 API 내보내기
description: 포함된 Power BI 보고서를 내보내는 방법을 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 03/24/2020
ms.openlocfilehash: db907897256ef4afc0bdb9a253a23880b6e79f53
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525471"
---
# <a name="export-power-bi-report-to-file-preview"></a>파일로 Power BI 보고서 내보내기(미리 보기)

`exportToFile` API를 사용하면 REST 호출을 통해 Power BI 보고서를 내보낼 수 있습니다. 지원되는 파일 형식은 다음과 같습니다.
* **.pptx**(PowerPoint)
* **.pdf**
* **.png**
    * .png로 내보내는 경우 여러 페이지가 포함된 보고서는 .zip 파일로 압축됩니다.
    * .zip에 포함된 각 파일은 보고서 페이지를 나타냅니다.
    * 페이지 이름은 [페이지 가져오기](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) 또는 [그룹의 페이지 가져오기](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup) API의 반환값과 동일합니다.

## <a name="usage-examples"></a>사용 예

내보내기 기능은 다양한 방법으로 사용할 수 있습니다. 다음은 몇 가지 예입니다.

* **인쇄로 보내기 단추** - 애플리케이션에서 클릭하면 내보내기 작업을 트리거하는 단추를 만듭니다. 작업은 표시된 보고서를 .pdf 또는 .pptx로 내보낼 수 있으며, 완료되면 사용자가 파일을 다운로드로 받을 수 있습니다. 책갈피를 사용하여 구성된 필터, 슬라이서 및 추가 설정을 포함하여 특정 상태에서 보고서를 내보낼 수 있습니다. 이 API는 비동기식이므로 파일을 사용하는 데 어느 정도 시간이 걸릴 수 있습니다.

* **메일 첨부 파일** - .pdf 보고서를 첨부하여 설정된 간격마다 자동화된 메일을 보냅니다. 이 시나리오는 주별 보고서를 임원에게 자동으로 전송하려는 경우에 유용할 수 있습니다.

## <a name="using-the-api"></a>API 사용

API를 사용하기 전에 다음 [관리자 테넌트 설정](../../service-admin-portal.md#tenant-settings)이 사용하도록 설정되었는지 확인합니다.
* **PowerPoint 프레젠테이션 또는 PDF 문서로 보고서 내보내기** - 기본적으로 사용하도록 설정됩니다.
* **이미지 파일로 보고서 내보내기** - *.png*에만 필요하며 기본적으로 사용되지 않습니다.

이 API는 비동기식입니다. [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) API를 호출하면 내보내기 작업을 트리거합니다. 내보내기 작업을 트리거한 후 [폴링](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus)을 사용하여 완료될 때까지 작업을 추적합니다.

폴링을 수행하는 동안 API는 완료된 작업량을 나타내는 숫자를 반환합니다. 각 내보내기 작업의 작업은 보고서에 포함된 페이지 수에 따라 계산됩니다. 모든 페이지는 가중치가 동일합니다. 예를 들어 10개 페이지를 포함하는 보고서를 내보내고 폴링을 통해 70이 반환되는 경우 API가 내보내기 작업에서 10개 페이지 중 7개를 처리했다는 의미입니다.

내보내기가 완료되면 폴링 API 호출이 파일을 가져오기 위한 [Power BI URL](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile)을 반환합니다. URL은 24시간 동안 제공됩니다.

## <a name="supported-features"></a>지원되는 기능

### <a name="selecting-which-pages-to-print"></a>인쇄할 페이지 선택

[페이지 가져오기](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) 또는 [그룹의 페이지 가져오기](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup) 반환 값에 따라 인쇄할 페이지를 지정합니다. 내보낼 페이지의 순서를 지정할 수도 있습니다.

### <a name="bookmarks"></a>책갈피

 `exportToFile` API를 사용하여 필터를 적용한 후 특정 상태에서 보고서를 프로그래밍 방식으로 내보낼 수 있습니다. 이 동작은 [책갈피](../../consumer/end-user-bookmarks.md) 기능을 사용하여 수행합니다. 책갈피를 사용하여 보고서를 내보내려면 [bookmarks JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks)를 사용합니다.

 예를 들어 책갈피의 `capturedBookmark.state` 메서드를 사용하여 특정 사용자가 보고서에 대해 만든 변경 내용을 캡처한 다음 현재 상태로 내보낼 수 있습니다.

[개인 책갈피](../../consumer/end-user-bookmarks.md#personal-bookmarks) 및 [영구 필터](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/)는 지원되지 않습니다.

### <a name="authentication"></a>인증

사용자(또는 마스터 사용자) 또는 [서비스 주체](embed-service-principal.md)를 사용하여 인증할 수 있습니다.

### <a name="row-level-security-rls"></a>행 수준 보안(RLS)

[RLS(행 수준 보안)](embedded-row-level-security.md)를 사용하여 특정 사용자 에게만 표시되는 데이터를 포함하는 보고서를 내보낼 수 있습니다. 예를 들어 지역 역할로 정의된 판매 보고서를 내보내는 경우 특정 지역만 표시되도록 보고서를 프로그래밍 방식으로 필터링할 수 있습니다.

RLS를 사용하여 내보내려면 다음과 같은 권한이 있어야 합니다.
* 보고서가 연결된 데이터 세트에 대한 쓰기 및 다시 공유 권한
* 보고서가 v1 작업 영역에 있는 경우 작업 영역 관리자여야 함
* 보고서가 v2 작업 영역에 있는 경우 작업 영역 구성원 또는 관리자여야 함

### <a name="data-protection"></a>데이터 보호

.pdf 및 .pptx 형식은 [민감도 레이블](../../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi)을 지원합니다. 민감도 레이블이 포함된 보고서를 .pdf 또는 .pptx로 내보내는 경우 내보낸 파일은 민감도 레이블이 포함된 보고서를 표시합니다.

민감도 레이블이 포함된 보고서는 [서비스 주체](embed-service-principal.md)를 사용하여 .pdf 또는 .pptx로 내보낼 수 없습니다.

### <a name="localization"></a>지역화

`exportToFile` API를 사용하는 경우 원하는 로컬을 전달할 수 있습니다. 지역화 설정은 보고서가 표시되는 방식에 영향을 줍니다(예: 선택한 로컬에 따라 서식 변경).

## <a name="concurrent-requests"></a>동시 요청

`exportToFile`은 동시 내보내기 작업 요청을 지원합니다. 아래 표에서는 보고서가 상주하는 SKU에 따라 동시에 실행할 수 있는 작업 수를 보여 줍니다. 동시 요청은 보고서 페이지 수를 나타냅니다. 예를 들어 A6 SKU에 대한 하나의 내보내기 요청에서 20개 페이지가 동시에 처리됩니다. 이는 한 페이지에서 각각 20개의 내보내기 요청을 전송하는 것과 거의 동일합니다.

동시 요청 수를 초과하는 작업은 종료되지 않습니다. 예를 들어 A1 SKU에서 3개 페이지를 내보내는 경우 첫 번째 작업이 실행되고, 나머지 두 작업은 다음 두 실행 주기 동안 대기합니다.

|Azure SKU  |Office SKU  |최대 동시 보고서 페이지 수  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>제한 사항

* 내보내는 보고서는 Premium 또는 Embedded 용량에 있어야 합니다.
* 내보내는 보고서의 데이터 세트는 Premium 또는 Embedded 용량에 있어야 합니다.
* 퍼블릭 미리 보기의 경우 시간당 내보내는 Power BI 보고서 페이지 수는 용량당 50개로 제한됩니다.
* 내보낸 보고서는 250MB의 파일 크기를 초과할 수 없습니다.
* .png로 내보내는 경우에는 민감도 레이블이 지원되지 않습니다.
* 민감도 레이블이 포함된 보고서는 [서비스 주체](embed-service-principal.md)를 사용하여 .pdf 또는 .pptx로 내보낼 수 없습니다.
* 내보낸 보고서에 포함할 수 있는 페이지 수는 30입니다. 보고서에 더 많은 페이지가 포함된 경우 API는 오류를 반환하고 내보내기 작업은 취소됩니다.
* [개인 책갈피](../../consumer/end-user-bookmarks.md#personal-bookmarks) 및 [영구 필터](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/)는 지원되지 않습니다.
* 소버린 클라우드는 지원되지 않습니다.
* 아래에 나열된 Power BI 시각적 개체는 지원되지 않습니다. 이러한 시각적 개체를 포함하는 보고서를 내보낼 경우 보고서에서 이러한 시각적 개체를 포함하는 부분은 렌더링되지 않으며 오류 기호가 표시됩니다.
    * 인증되지 않은 Power BI 시각적 개체
    * R 시각적 개체
    * PowerApps
    * Python 시각적 개체
    * Visio

## <a name="code-examples"></a>코드 예제

내보내기 작업을 만들 때 다음 세 단계를 수행해야 합니다.

1. 내보내기 요청 보내기
2. 폴링
3. 파일 가져오기

이 섹션에서는 각 단계에 대한 예제를 제공합니다.

### <a name="step-1---sending-an-export-request"></a>1단계 - 내보내기 요청 보내기

첫 번째 단계는 내보내기 요청을 보내는 것입니다. 이 예제에서는 특정 페이지에 대한 내보내기 요청을 보냅니다.

```csharp
/////// Export sample ///////
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names.
        // To get the page names use the GetPages API.
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
    };
    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
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
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }
        var httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;
        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
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
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}
public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="end-to-end-example"></a>엔드투엔드 예제

보고서를 내보내는 엔드투엔드 예제입니다. 이 예제는 다음과 같은 단계로 구성됩니다.
1. [내보내기 요청 보내기](#step-1---sending-an-export-request)
2. [폴링](#step-2---polling)
3. [파일 가져오기](#step-3---getting-the-file)

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
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
>[페이지를 매긴 보고서를 파일로 내보내기](export-paginated-report.md)

> [!div class="nextstepaction"]
>[고객에 대한 콘텐츠 포함](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[조직에 포함](embed-sample-for-your-organization.md)
