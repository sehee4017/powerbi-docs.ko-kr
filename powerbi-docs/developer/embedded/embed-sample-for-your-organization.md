---
title: 조직용 Power BI 임베디드 분석 애플리케이션에 콘텐츠 포함
description: 조직의 임베디드 분석에 Power BI API를 사용하여 애플리케이션에 보고서(Power BI 또는 페이지 매김), 대시보드 또는 타일을 통합하거나 포함하는 방법을 알아봅니다. 임베디드 분석 소프트웨어, 임베디드 분석 도구 또는 임베디드 비즈니스 인텔리전스 도구를 사용하여 애플리케이션에 Power BI를 통합하는 방법을 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: seodec18
ms.date: 02/04/2020
ms.openlocfilehash: 223495b68f160b637f5bcf40b37f1f1a1365fffd
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098171"
---
# <a name="tutorial-embed-power-bi-content-into-an-application-for-your-organization"></a>자습서:  조직의 애플리케이션에 Power BI 콘텐츠 포함

**Power BI** 에서 사용자 소유 데이터를 사용하여 애플리케이션에 보고서(Power BI 또는 페이지 매김), 대시보드 또는 타일을 포함할 수 있습니다. **사용자 소유 데이터** 를 사용하면 애플리케이션에서 Power BI 서비스를 확장할 수 있으므로 임베디드 분석을 사용할 수 있습니다. 이 자습서는 보고서(Power BI 또는 페이지 매김)를 애플리케이션에 통합하는 방법을 보여 줍니다. Power BI .NET SDK를 Power BI JavaScript API와 함께 사용하여 Power BI를 조직의 애플리케이션에 포함합니다.

![Power BI 포함 보고서](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

이 자습서에서는 다음 작업에 대해 학습합니다.
> [!div class="checklist"]
> * Azure에서 애플리케이션을 등록합니다.
> * Power BI 테넌트를 사용하여 애플리케이션에 Power BI 또는 페이지를 매긴 보고서를 포함합니다.

## <a name="prerequisites"></a>필수 조건

시작하려면 다음이 필요합니다.

* [Power BI Pro 계정](../../fundamentals/service-self-service-signup-for-power-bi.md).
* [Microsoft Azure](https://azure.microsoft.com/) 구독.
* 고유한 [Azure Active Directory 테넌트 ](create-an-azure-active-directory-tenant.md) 설정이 필요합니다.
* 페이지를 매긴 보고서를 포함하려면 최소 P1 용량이 필요합니다. [페이지를 매긴 보고서에 필요한 크기의 프리미엄 용량은 무엇인가요? 참조](../../paginated-reports/paginated-reports-faq.md#what-size-premium-capacity-do-i-need-for-paginated-reports)

아직 **Power BI Pro** 에 등록하지 않은 경우 시작하기 전에 [평가판에 등록](https://powerbi.microsoft.com/pricing/)합니다.

Azure 구독이 없는 경우 시작하기 전에 [체험 계정](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)을 만듭니다.

>[!NOTE]
>[PPU(사용자 단위 Premium)](../../admin/service-premium-per-user-faq.md)가 지원됩니다. 그러나 PPU를 사용 중인 경우 조직의 PPU 사용자만 솔루션에 액세스할 수 있습니다.

## <a name="set-up-your-embedded-analytics-development-environment"></a>임베디드 분석 개발 환경 설정

애플리케이션에 보고서, 대시보드 또는 타일 포함을 시작하기 전에 사용자 환경이 Power BI에 포함을 허용하도록 설정해야 합니다.

[포함 설정 도구](https://app.powerbi.com/embedsetup)를 통해 환경을 만들고 보고서를 포함하는 방법을 설명할 수 있는 샘플 애플리케이션을 신속하게 시작하고 다운로드할 수 있습니다. 페이지를 매긴 보고서를 포함하는 경우, 만든 작업 영역에 P1 이상의 용량을 할당해야 합니다.

환경을 수동으로 설정하도록 선택하면 아래를 계속할 수 있습니다.

### <a name="register-an-application-in-azure-active-directory"></a>Azure Active Directory에서 애플리케이션 등록

Azure Active Directory로 [애플리케이션을 등록](register-app.md)하여 애플리케이션에서 [Power BI REST API](/rest/api/power-bi/)에 액세스할 수 있도록 합니다. 애플리케이션을 등록하면 애플리케이션의 ID를 설정하고 Power BI REST 리소스에 대한 권한을 지정할 수 있습니다.

>[!NOTE]
>고유의 애플리케이션에서 *인증* 으로 이동하여 *리디렉션 URI* 필드에 리디렉션 주소를 삽입합니다.
리디렉션에 대해 자세히 알아보려면 [Redirect URI (reply URL) restrictions and limitations](https://docs.microsoft.com/azure/active-directory/develop/reply-url)(리디렉션 URI(회신 URL) 제한 사항)를 참조하세요.

## <a name="set-up-your-power-bi-environment"></a>Power BI 환경 설정

### <a name="create-a-workspace"></a>작업 영역 만들기

고객을 위해 보고서, 대시보드 또는 타일을 포함하는 경우 콘텐츠를 작업 영역 내에 배치해야 합니다. 설정할 수 있는 작업 영역에는 [기존 작업 영역](../../collaborate-share/service-create-workspaces.md) 또는 [새 작업 영역](../../collaborate-share/service-create-the-new-workspaces.md)이 있습니다.

### <a name="create-and-publish-your-power-bi-reports"></a>Power BI 보고서 만들기 및 게시

Power BI Desktop을 사용하여 보고서와 데이터 세트를 만들 수 있습니다. 그런 다음, 해당 보고서를 작업 영역에 게시할 수 있습니다. 보고서를 게시하는 최종 사용자가 작업 영역에 게시하려면 Power BI Pro 라이선스가 필요합니다.

1. GitHub에서 샘플 [데모](https://github.com/Microsoft/powerbi-desktop-samples)를 다운로드합니다.

    ![데모 다운로드](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026-1.png)

2. Power BI Desktop에서 샘플 .pbix 보고서 열기

   ![샘플 Power BI Desktop 보고서](media/embed-sample-for-your-organization/embed-sample-for-your-organization-027.png)

3. 작업 영역에 게시합니다.

   ![Power BI Desktop 보고서 게시](media/embed-sample-for-your-organization/embed-sample-for-your-organization-028.png)

    이제 Power BI 서비스에서 온라인으로 보고서를 볼 수 있습니다.

   ![Power BI Desktop 보고서 보기](media/embed-sample-for-your-organization/embed-sample-for-your-organization-029.png)
   
### <a name="create-and-publish-your-paginated-reports"></a>페이지를 매긴 보고서 만들기 및 게시

[Power BI 보고서 작성기](../../paginated-reports/paginated-reports-report-builder-power-bi.md#create-reports-in-power-bi-report-builder)를 사용하여 페이지를 매긴 보고서를 만들 수 있습니다. 그런 다음, P1 이상의 용량에 할당된 작업 영역에 [보고서를 업로드](../../paginated-reports/paginated-reports-quickstart-aw.md#upload-the-report-to-the-service)할 수 있습니다. 보고서를 업로드하는 최종 사용자가 작업 영역에 게시하려면 Power BI Pro 라이선스가 필요합니다.
   
## <a name="embed-your-content-by-using-the-sample-application"></a>샘플 애플리케이션을 사용하여 콘텐츠 포함

이 샘플은 간단한 데모용으로 의도적으로 유지됩니다.

샘플 애플리케이션을 사용하여 콘텐츠 포함을 시작하려면 다음 단계를 수행합니다.

1. [Visual Studio](https://www.visualstudio.com/)(버전 2013 이상)를 다운로드합니다. 최신 [NuGet 패키지](https://www.nuget.org/profiles/powerbi)를 다운로드해야 합니다.

2. GitHub에서 [사용자 소유 데이터 샘플](https://github.com/Microsoft/PowerBI-Developer-Samples)을 다운로드하여 시작하세요.

    ![사용자 소유 데이터 애플리케이션 샘플](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026.png)

3. 샘플 애플리케이션에서 **Cloud.config** 파일을 엽니다.

    애플리케이션을 실행하려면 필드를 입력해야 합니다.

    | 필드 |
    |--------------------|
    | **[애플리케이션 ID](#application-id)** |
    | **[작업 영역 ID](#workspace-id)** |
    | **[보고서 ID](#report-id)** |
    | **[AADAuthorityUrl](#aadauthorityurl)** |

    ![Cloud.config 파일](media/embed-sample-for-your-organization/embed-sample-for-your-organization-030.png)

### <a name="application-id"></a>애플리케이션 ID

**Azure** 의 **애플리케이션 ID** 를 사용하여 **applicationId** 정보를 입력합니다. **applicationId** 는 응용 프로그램에서 권한을 요청 중인 사용자에게 응용 프로그램을 인식시키는 데 사용됩니다.

**applicationId** 를 가져오려면 다음 단계를 수행합니다.

1. [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. 왼쪽 탐색 창에서 **모든 서비스** 를 선택하고 **앱 등록** 을 선택합니다.

3. **applicationId** 가 필요한 응용 프로그램을 선택합니다.

    ![앱 선택](media/embed-sample-for-your-organization/embed-sample-for-your-organization-042.png)

4. GUID로 나열된 **애플리케이션 ID** 가 있습니다. 이 **응용 프로그램 ID** 를 애플리케이션의 **applicationId** 로 사용합니다.

    ![applicationId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-043.png)

### <a name="workspace-id"></a>작업 영역 ID

Power BI의 작업 영역(그룹) GUID를 사용하여 **workspaceId** 정보를 입력합니다. Power BI 서비스에 로그인하거나 PowerShell을 사용할 때 URL에서 이 정보를 가져올 수 있습니다.

URL <br>

![workspaceId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-040.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "User Owns Embed Test"
```

   ![PowerShell의 workspaceId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-040-ps.png)

### <a name="report-id"></a>보고서 ID

Power BI의 보고서 GUID를 사용하여 **reportId** 정보를 입력합니다. Power BI 서비스에 로그인하거나 PowerShell을 사용할 때 URL에서 이 정보를 가져올 수 있습니다.

Power BI 보고서 URL <br>

![PBI reportId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-041.png)


페이지를 매긴 보고서 URL<br>

![페이지를 매긴 reportId](media/embed-sample-for-your-organization/paginated-reports-url.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "User Owns Embed Test" | Get-PowerBIReport
```

![PowerShell의 reportId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-041-ps.png)

### <a name="aadauthorityurl"></a>AADAuthorityUrl

조직 테넌트 내에 포함하거나 게스트 사용자와 함께 포함할 수 있는 URL을 사용하여 **AADAuthorityUrl** 정보를 입력합니다.

조직 테넌트에 포함된 경우 URL( *https://login.microsoftonline.com/common/oauth2/authorize* )을 사용하세요.

게스트에 포함된 경우 *report-owner-tenant-id* 를 대체하여 보고서 소유자의 테넌트 ID를 추가하는 URL(`https://login.microsoftonline.com/report-owner-tenant-id`)을 사용하세요.

### <a name="run-the-application"></a>애플리케이션 실행

1. **Visual Studio** 에서 **실행** 을 선택합니다.

    ![애플리케이션 실행](media/embed-sample-for-your-organization/embed-sample-for-your-organization-033.png)

2. 그런 다음, **보고서 포함** 을 선택합니다. 테스트하기 위해 선택한 콘텐츠(보고서, 대시보드 또는 타일)에 따라 애플리케이션에서 해당 옵션을 선택합니다.

    ![콘텐츠 선택](media/embed-sample-for-your-organization/embed-sample-for-your-organization-034.png)

3. 이제 애플리케이션 예제에서 보고서를 볼 수 있습니다.

    ![애플리케이션에서 보고서 보기](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

## <a name="embed-your-content-within-your-application"></a>애플리케이션 내에서 콘텐츠 포함

콘텐츠를 포함하는 단계가 [Power BI REST API](/rest/api/power-bi/)를 사용하여 수행할 수 있더라도 이 아티클에 설명된 예제 코드는 .NET SDK를 사용하여 만듭니다.

보고서를 웹앱에 통합하려면 Power BI REST API 또는 Power BI C# SDK를 사용합니다. Azure Active Directory 권한 부여 액세스 토큰을 사용하여 보고서를 가져올 수도 있습니다. 그런 다음, 동일한 액세스 토큰을 사용하여 보고서를 로드합니다. Power BI Rest API는 특정 Power BI 리소스에 대한 프로그래밍 방식 액세스를 제공합니다. 자세한 내용은 [Power BI REST API](/rest/api/power-bi/) 및 [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)를 참조하세요.

### <a name="get-an-access-token-from-azure-ad"></a>Azure AD에서 액세스 토큰 가져오기

애플리케이션 내에서 Azure AD에서 액세스 토큰을 가져와야 Power BI REST API로 호출할 수 있습니다. 자세한 내용은 [사용자를 인증하고 Power BI 앱에 대한 Azure AD 액세스 토큰 가져오기](get-azuread-access-token.md)를 참조하세요.

### <a name="get-a-report"></a>보고서 가져오기

Power BI 또는 페이지를 매긴 보고서를 가져오려면, Power BI 및 페이지를 매긴 보고서 목록을 가져오는 [보고서 가져오기](/rest/api/power-bi/reports/getreports) 작업을 사용합니다. 보고서 목록에서 보고서 ID를 가져올 수 있습니다.

### <a name="get-reports-by-using-an-access-token"></a>액세스 토큰을 사용하여 보고서 가져오기

[보고서 가져오기](/rest/api/power-bi/reports/getreports) 작업은 보고서 목록을 반환합니다. 보고서 목록에서 단일 보고서를 가져올 수 있습니다.

REST API를 호출하려면 *권한 부여* 헤더를 *Bearer {access token}* 형식으로 포함해야 합니다.

#### <a name="get-reports-with-the-rest-api"></a>REST API를 사용하여 보고서 가져오기

다음 코드 샘플은 REST API로 보고서를 검색하는 방법을 보여줍니다.

> [!Note]
> 포함하려는 콘텐츠 항목을 가져오는 샘플은 [샘플 애플리케이션](https://github.com/Microsoft/PowerBI-Developer-Samples)의 Default.aspx.cs 파일 내에서 사용 가능합니다. 예로는 보고서, 대시보드 또는 타일이 있습니다.

```csharp
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string reportType { get; set }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-by-using-the-net-sdk"></a>.NET SDK를 사용하여 보고서 가져오기

.NET SDK를 사용하여 REST API를 직접 호출하는 대신 보고서 목록을 검색할 수 있습니다. 다음 코드 샘플은 보고서를 나열하는 방법을 보여 줍니다.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It is used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

### <a name="load-a-report-by-using-javascript"></a>JavaScript를 사용하여 보고서 로드

JavaScript를 사용하여 웹 페이지의 div 요소로 보고서를 로드합니다. 다음 코드 샘플은 제공된 작업 영역에서 보고서를 검색하는 방법을 보여 줍니다.

> [!NOTE]  
> 포함하려는 콘텐츠 항목을 로드하는 샘플은 [샘플 애플리케이션](https://github.com/Microsoft/PowerBI-Developer-Samples)의 **Default.aspx** 파일에 제공됩니다.

```javascript
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

#### <a name="sitemaster"></a>Site.master

```javascript
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReport, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    }
  );
}
```

## <a name="using-a-power-bi-premium-capacity"></a>Power BI Premium 용량 사용

이제 애플리케이션 개발을 완료했으므로 용량으로 작업 영역을 백업해야 합니다.

### <a name="create-a-capacity"></a>용량 만들기

용량을 만들면 작업 영역의 콘텐츠에 대한 리소스의 혜택을 활용할 수 있습니다. 페이지를 매긴 보고서의 경우 최소 P1 용량을 사용하여 작업 영역을 백업해야 합니다. [Power BI Premium](../../admin/service-premium-what-is.md)을 사용하여 용량을 만들 수 있습니다.

다음 표에는 [Microsoft 365](../../admin/service-admin-premium-purchase.md) 내에서 사용할 수 있는 Power BI Premium SKU가 나와 있습니다.

| 용량 노드 | 총 vCore<br/>(백 엔드 + 프런트 엔드) | 백 엔드 vCore | 프런트 엔드 vCore | DirectQuery/라이브 연결 제한 |
| --- | --- | --- | --- | --- | --- |
| EM1 |vCore 1개 |vCore 0.5개, 3GB RAM |vCore 0.5개 |초당 3.75 |
| EM2 |vCore 2개 |vCore 1개, 5GB RAM |vCore 1개 |초당 7.5 |
| EM3 |vCore 4개 |vCore 2개, 10GB RAM |vCore 2개 |초당 15 |
| P1 |vCore 8개 |vCore 4개, 25GB RAM |vCore 4개 |초당 30 |
| P2 |vCore 16개 |vCore 8개, 50GB의 RAM |vCore 8개 |초당 60 |
| P3 |vCore 32개 |vCore 16개, 100GB의 RAM |vCore 16개 |초당 120 |
| P4 |vCore 64개 |vCore 32개, 200GB RAM |vCore 32개 |초당 240 |
| P5 |vCore 128개 |vCore 64개, 400GB RAM |vCore 64개 |초당 480 |

> [!NOTE]
> - Microsoft Office 앱에 포함하려는 경우 EM SKU를 사용하여 무료 Power BI 라이선스로 콘텐츠에 액세스할 수 있습니다. 하지만 Powerbi.com 또는 Power BI Mobile을 사용하는 경우 무료 Power BI 라이선스를 사용하여 콘텐츠에 액세스할 수 없습니다.
> - Powerbi.com 또는 Power BI Mobile을 사용하여 Microsoft Office 앱에 포함하려는 경우 무료 Power BI 라이선스로 콘텐츠에 액세스할 수 있습니다.

### <a name="assign-a-workspace-to-a-capacity"></a>용량에 작업 영역 할당

용량을 만든 후 해당 용량에 작업 영역을 할당할 수 있습니다. 이 프로세스를 완료하려면 다음 단계를 수행합니다.

1. Power BI 서비스 내에서 작업 영역을 확장하고 콘텐츠를 포함하는 데 사용하는 작업 영역에 대한 줄임표를 선택합니다. 그런 다음, **작업 영역 편집** 을 선택합니다.

    ![작업 영역 편집](media/embed-sample-for-your-organization/embed-sample-for-your-organization-036.png)

2. **고급** 을 확장하고 **용량** 을 사용하도록 설정합니다. 만든 용량을 선택합니다. 그런 다음, **저장** 을 선택합니다.

    ![용량 할당](media/embed-sample-for-your-organization/embed-sample-for-your-organization-024.png)

3. **저장** 을 선택하면 작업 영역 이름 옆에 다이아몬드가 표시됩니다.

    ![용량에 연결된 작업 영역](media/embed-sample-for-your-organization/embed-sample-for-your-organization-037.png)

## <a name="admin-settings"></a>관리 설정

전역 관리자 또는 Power BI 서비스 관리자는 테넌트에 REST API를 사용하도록 설정하거나 해제할 수 있습니다. Power BI 관리자는 전체 조직 또는 개별 보안 그룹에 대해 이 설정을 지정할 수 있습니다. 기본적으로 전체 조직에서 사용하도록 설정됩니다. [Power BI 관리 포털](../../admin/service-admin-portal.md)에서 이러한 변경 내용을 적용할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 Power BI 조직 계정을 사용하여 애플리케이션에 Power BI 콘텐츠를 포함하는 방법을 배웠습니다. 이제 앱을 사용하여 Power BI 콘텐츠를 애플리케이션에 포함할 수 있습니다. 고객의 Power BI 콘텐츠를 포함할 수도 있습니다(페이지를 매긴 보고서를 포함하는 용도로는 아직 지원되지 않음).

> [!div class="nextstepaction"]
> [앱에서 포함](embed-from-apps.md)

> [!div class="nextstepaction"]
>[고객에 대한 콘텐츠 포함](embed-sample-for-customers.md)

추가 질문이 있는 경우 [Power BI 커뮤니티에 질문합니다](https://community.powerbi.com/).