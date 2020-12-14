---
title: 고객의 애플리케이션에 콘텐츠 포함
description: Power BI 임베디드 분석 샘플에 보고서, 대시보드 또는 타일을 포함하는 방법을 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/02/2020
ms.openlocfilehash: 7bc825992f5c7382e1c0a24783f732957913c588
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96907201"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-customers-application"></a>자습서:  샘플 ‘고객에 대한 콘텐츠 포함’ 애플리케이션을 사용하여 Power BI 콘텐츠 포함

**임베디드 분석** 및 **Power BI Embedded**(Azure 제품)를 사용하여 보고서, 대시보드, 타일과 같은 Power BI 콘텐츠를 애플리케이션에 포함할 수 있습니다.

이 자습서에서는 다음과 같은 작업을 수행하는 방법을 알아봅니다.
>[!div class="checklist"]
>* 포함된 환경을 설정합니다.
>* ‘고객에 대한 콘텐츠 포함’(‘앱 소유 데이터’라고도 함) 애플리케이션 예제를 구성합니다. 

애플리케이션을 사용하기 위해 사용자는 Power BI에 로그인하거나 Power BI 라이선스를 가질 필요가 없습니다.

타사용 애플리케이션을 만들려는 ISV(독립 소프트웨어 공급업체) 또는 개발자인 경우에는 ‘고객에 대한 콘텐츠 포함’ 방법을 사용하여 Power BI 콘텐츠를 포함하는 것이 좋습니다.

## <a name="code-sample-specifications"></a>코드 샘플 사양

이 자습서에는 다음 언어 중 하나로 ‘고객에 대한 콘텐츠 포함’ 애플리케이션 예제를 구성하기 위한 지침이 포함되어 있습니다.

* .NET Framework
* .NET Core
* Java
* Node JS
* Python

코드 샘플은 다음 브라우저를 지원합니다.

* Google Chrome

* Microsoft Edge

* Mozilla Firefox

## <a name="prerequisites"></a>필수 구성 요소

이 자습서를 시작하기 전에 아래에 나온 Power BI 및 코드 종속성이 모두 있는지 확인합니다.

* **Power BI 종속성**

    * 고유한 [Azure Active Directory 테넌트](create-an-azure-active-directory-tenant.md)

    * Power BI에 대해 앱을 인증하려면 다음 중 하나가 필요합니다.

        * [서비스 주체](embed-service-principal.md) - Azure AD가 앱을 인증할 수 있게 하는 Azure AD(Azure Active Directory) [서비스 주체 개체](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) 라이선스 - **마스터 사용자** 이며 앱이 이 라이선스를 사용하여 Power BI에 대해 인증합니다.

        * Power BI [PPU(사용자 단위 Premium)](../../admin/service-premium-per-user-faq.md) 라이선스 - **마스터 사용자** 이며 앱이 이 라이선스를 사용하여 Power BI에 대해 인증합니다.

    >[!NOTE]
    >[프로덕션으로 이동](move-to-production.md)하려면 [용량](embedded-capacity.md)이 필요합니다.

* **코드 종속성**

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)
    
    
    # <a name="net-core"></a>[.NET Core](#tab/net-core)
    
    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core)(이상)
    
    * IDE(통합 개발 환경). 다음 중 하나를 사용하는 것이 좋습니다.
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="java"></a>[Java](#tab/java)
    
    * [JDK(또는 JRE)](https://www.oracle.com/java/technologies/)
    
    * [Eclipse IDE](https://www.eclipse.org/downloads/packages/) - *Java EE용 Eclipse 개발자*(Enterprise Edition)가 있는지 확인합니다.
    
    * [Apache Tomcat 이진 배포](https://tomcat.apache.org/)
    
    # <a name="node-js"></a>[Node JS](#tab/node-js)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * IDE(통합 개발 환경). 다음 중 하나를 사용하는 것이 좋습니다.
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    # <a name="python"></a>[Python](#tab/python)
    
    * [Python 3](https://www.python.org/downloads/)(이상)
    
        >[!NOTE]
        >* *Python* 을 처음 설치하는 경우 **PATH에 Python 추가** 옵션을 선택하여 설치를 `PATH` 변수에 추가합니다.
        >* *Python* 이 이미 설치된 경우 해당 설치 경로가 `PATH` 변수에 포함되어 있는지 확인합니다. 자세한 내용은 [Excursus: 환경 변수 설정](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables) Python 설명서를 참조하세요(이 링크는 Python 3 참조).
    
    * IDE(통합 개발 환경). 다음 중 하나를 사용하는 것이 좋습니다.
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    ---

## <a name="method"></a>메서드

‘고객에 대한 콘텐츠 포함’ 샘플 앱을 만들려면 다음 단계를 수행합니다.

1. [인증 방법을 선택](#step-1---select-your-authentication-method)합니다.

2. [Azure AD 애플리케이션을 등록](#step-2---register-an-azure-ad-application)합니다.

3. [Power BI 작업 영역을 만듭니다](#step-3---create-a-power-bi-workspace).

4. [Power BI 보고서를 만들고 게시](#step-4---create-and-publish-a-power-bi-report)합니다.

5. [포함하는 매개 변수 값을 가져옵니다](#step-5---get-the-embedding-parameter-values).

6. [서비스 주체 API 액세스](#step-6---service-principal-api-access)
 
7. [작업 영역 액세스를 사용하도록 설정](#step-7---enable-workspace-access)합니다.

8. [콘텐츠를 포함](#step-8---embed-your-content)합니다.

## <a name="step-1---select-your-authentication-method"></a>1단계 - 인증 방법 선택

포함된 솔루션은 선택한 인증 방법에 따라 달라집니다. 따라서 인증 방법 간의 차이점을 이해하고 솔루션에 가장 적합한 방법을 결정하는 것이 중요합니다.

다음 표에서는 [서비스 주체](embed-service-principal.md) 인증 방법과 **마스터 사용자** 인증 방법 간의 몇 가지 주요 차이점을 설명합니다.

|고려 사항  |서비스 사용자  |마스터 사용자  |
|---------|---------|---------|
|메커니즘     |Azure AD 앱의 [서비스 주체 개체](/azure/active-directory/develop/app-objects-and-service-principals.md#service-principal-object)를 통해 Azure AD가 Power BI에 대해 포함된 솔루션 앱을 인증할 수 있습니다.        |Azure AD 앱은 Power BI 사용자의 자격 증명(사용자 이름 및 암호)을 사용하여 Power BI에 대해 인증합니다.         |
|보안     |‘서비스 주체’는 Azure AD 권장 권한 부여 방법입니다. 서비스 주체*를 사용하는 경우 ‘애플리케이션 암호’ 또는 ‘인증서’를 사용하여 인증할 수 있습니다. </br></br>이 자습서에서는 ‘애플리케이션 암호’로 ‘서비스 주체’를 사용하는 방법을 설명합니다.  ‘서비스 주체’ 및 ‘인증서’를 사용하여 포함하려면 [서비스 주체 및 인증서](embed-service-principal-certificate.md) 문서를 참조하세요.          |이 인증 방법은 ‘서비스 주체’를 사용하는 것만큼 안전하지 않습니다. 왜냐하면 ‘마스터 사용자’ 자격 증명(사용자 이름 및 암호)을 사용할 때는 주의해야 하기 때문입니다. 예를 들어 포함하는 애플리케이션에 자격 증명을 노출해서는 안 되며 암호를 자주 변경해야 합니다.         |
|Azure AD 위임된 권한 |필수 아님. |‘마스터 사용자’ 또는 관리자는 앱이 Power BI REST API [권한](/azure/active-directory/develop/v2-permissions-and-consent)(범위라고도 함)에 액세스할 수 있게 동의해야 합니다. 예를 들어 *Report.ReadWrite.All* 입니다. |
|Power BI 서비스 액세스 |‘서비스 주체’를 사용하여 Power BI 서비스에 액세스할 수 없습니다.|‘마스터 사용자’ 자격 증명을 사용하여 Power BI 서비스에 액세스할 수 있습니다.|
|라이선스     |Pro 라이선스가 필요하지 않습니다. 멤버 또는 관리자로 속해 있는 모든 작업 영역의 콘텐츠를 사용할 수 있습니다.         |[Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) 라이선스가 필요합니다.         |

## <a name="step-2---register-an-azure-ad-application"></a>2단계 - Azure AD 애플리케이션 등록

Azure AD를 사용하여 애플리케이션을 등록하면 다음을 수행할 수 있습니다.
> [!div class="checklist"]
>* 앱에 대한 ID 설정
>* 앱이 [Power BI REST API](/rest/api/power-bi/)에 액세스하도록 허용
>* ‘마스터 사용자’를 사용하는 경우 - 앱의 [Power BI REST 권한](/azure/active-directory/develop/v2-permissions-and-consent) 지정

애플리케이션을 Azure AD에 등록하려면 [애플리케이션 등록](register-app.md)의 지침을 따르세요.

>[!NOTE]
>애플리케이션을 등록하기 전에 사용할 인증 방법, ‘서비스 주체’ 또는 ‘마스터 사용자’를 결정해야 합니다. 

## <a name="step-3---create-a-power-bi-workspace"></a>3단계 - Power BI 작업 영역 만들기

Power BI는 보고서, 대시보드, 타일을 작업 영역에 보관합니다. 이러한 항목을 포함하려면 항목을 만들고 작업 영역에 업로드해야 합니다.

>[!TIP]
>작업 영역이 이미 있는 경우 이 단계를 건너뛸 수 있습니다.

작업 영역을 만들려면 다음을 수행합니다.

1. Power BI에 로그인합니다.

2. **작업 영역** 을 선택합니다.

3. **작업 영역 만들기** 를 선택합니다.

4. 작업 영역 이름을 지정하고 **저장** 을 선택합니다.

## <a name="step-4---create-and-publish-a-power-bi-report"></a>4단계 - Power BI 보고서 만들기 및 게시

다음 단계는 보고서를 만들어 작업 영역에 업로드하는 것입니다. Power BI Desktop을 사용하여 [고유한 보고서를 만든](/powerbi-docs/fundamentals/desktop-getting-started#build-reports) 후 작업 영역에 [게시](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work)할 수 있습니다. 또는 작업 영역에 샘플 보고서를 업로드할 수 있습니다.

>[!Tip]
>보고서가 포함된 작업 영역이 이미 있는 경우 이 단계를 건너뛸 수 있습니다.

샘플 보고서를 다운로드하고 작업 영역에 게시하려면 다음 단계를 수행합니다.

1. GitHub [Power BI Desktop 샘플](https://github.com/microsoft/PowerBI-Developer-Samples) 폴더를 엽니다.

2. **Code**(코드)를 선택하고 **Download zip**(ZIP 다운로드)을 선택합니다.

    :::image type="content" source="media/embed-sample-for-customers/download-sample-report.png" alt-text="Power BI Desktop 샘플 GitHub의 ZIP 다운로드 옵션을 보여 주는 스크린샷":::

3. 다운로드한 ZIP의 압축을 풀고 **Samples Reports** 폴더로 이동합니다.

4. 포함할 보고서를 선택하고 작업 영역에 [게시](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work)합니다.

## <a name="step-5---get-the-embedding-parameter-values"></a>5단계 - 포함하는 매개 변수 값 가져오기

콘텐츠를 포함하려면 특정 매개 변수 값을 가져와야 합니다. 다음 표에서는 필요한 값을 보여 주고 ‘서비스 주체’ 인증 방법, ‘마스터 사용자’ 인증 방법 또는 두 가지 모두에 적용할 수 있는지를 나타냅니다. 

콘텐츠를 포함하기 전에 아래에 나열된 모든 값이 있는지 확인합니다. 일부 값은 사용하는 인증 방법에 따라 다릅니다.

|매개 변수   |서비스 사용자   |마스터 사용자  |
|-------------------|---|---|
|[클라이언트 ID](#client-id) |![적용 대상](../../media/yes.png) |![적용 대상](../../media/yes.png) |
|[작업 영역 ID](#workspace-id)     |![적용 대상](../../media/yes.png) |![적용 대상](../../media/yes.png) |
|[보고서 ID](#report-id)           |![적용 대상](../../media/yes.png) |![적용 대상](../../media/yes.png) |
|[클라이언트 암호](#client-secret) |![적용 대상](../../media/yes.png) |![미적용 대상](../../media/no.png) |
|[테넌트 ID](#tenant-id)                 |![적용 대상](../../media/yes.png) |![미적용 대상](../../media/no.png) |
|[Power BI 사용자 이름](#power-bi-username-and-password)   |![미적용 대상](../../media/no.png) |![적용 대상](../../media/yes.png) |
|[Power BI 암호](#power-bi-username-and-password)   |![미적용 대상](../../media/no.png) |![적용 대상](../../media/yes.png) |

### <a name="client-id"></a>클라이언트 ID

>[!TIP]
>**적용 대상:** ![적용 대상: ](../../media/yes.png)서비스 주체 ![적용 대상:](../../media/yes.png)마스터 사용자

클라이언트 ID GUID(‘애플리케이션 ID’라고도 함)를 가져오려면 다음 단계를 수행합니다.

1. [Microsoft Azure](https://ms.portal.azure.com/#allservices)에 로그인합니다.

2. **앱 등록** 을 검색하고 **앱 등록** 링크를 선택합니다.

3. Power BI 콘텐츠를 포함하는 데 사용하는 Azure AD 앱을 선택합니다.

4. **개요** 섹션에서 **애플리케이션(클라이언트) ID** GUID를 복사합니다.

### <a name="workspace-id"></a>작업 영역 ID

>[!TIP]
>**적용 대상:** ![적용 대상: ](../../media/yes.png)서비스 주체 ![적용 대상: ](../../media/yes.png)마스터 사용자

작업 영역 ID GUID를 가져오려면 다음 단계를 수행합니다.

1. Power BI 서비스에 로그인합니다.

2. 포함하려는 보고서를 엽니다.

3. URL에서 GUID를 복사합니다. GUID는 **/groups/** 와 **/reports/** 사이의 숫자입니다.

    :::image type="content" source="media/embed-sample-for-customers/workspace-id.png" alt-text="Power BI 서비스 URL의 작업 영역 ID GUID를 보여 주는 스크린샷":::

### <a name="report-id"></a>보고서 ID

>[!TIP]
>**적용 대상:** ![적용 대상: ](../../media/yes.png)서비스 주체 ![적용 대상: ](../../media/yes.png)마스터 사용자

1. Power BI 서비스에 로그인합니다.

2. 포함하려는 보고서를 엽니다.

3. URL에서 GUID를 복사합니다. GUID는 **/reports/** 와 **/ReportSection** 사이의 숫자입니다.

    :::image type="content" source="media/embed-sample-for-customers/report-id.png" alt-text="Power BI 서비스 URL의 보고서 ID GUID를 보여 주는 스크린샷":::

### <a name="client-secret"></a>클라이언트 암호

>[!TIP]
>**적용 대상:** ![적용 대상: ](../../media/yes.png)서비스 주체 ![미적용 대상: ](../../media/no.png)마스터 사용자

클라이언트 암호를 가져오려면 다음 단계를 수행합니다.

1. [Microsoft Azure](https://ms.portal.azure.com/#allservices)에 로그인합니다.

2. **앱 등록** 을 검색하고 **앱 등록** 링크를 선택합니다.

3. Power BI 콘텐츠를 포함하는 데 사용하는 Azure AD 앱을 선택합니다.

4. **관리** 에서 **인증서 및 암호** 를 선택합니다.

5. **클라이언트 암호** 아래에서 **새 클라이언트 암호** 를 선택합니다.

6. **클라이언트 암호 추가** 팝업 창에서 애플리케이션 암호에 대한 설명을 제공하고 애플리케이션 암호가 만료되는 경우를 선택하고 **추가** 를 선택합니다.

7. **클라이언트 암호** 섹션에서 새로 만든 애플리케이션 암호의 **값** 열에 문자열을 복사합니다. 클라이언트 암호 값은 ‘클라이언트 ID’입니다.

### <a name="tenant-id"></a>테넌트 ID

>[!TIP]
>**적용 대상:** ![적용 대상: ](../../media/yes.png)서비스 주체 ![미적용 대상: ](../../media/no.png)마스터 사용자

테넌트 ID GUID를 가져오려면 다음 단계를 수행합니다.

1. [Microsoft Azure](https://ms.portal.azure.com/#allservices)에 로그인합니다.

2. **앱 등록** 을 검색하고 **앱 등록** 링크를 선택합니다.

3. Power BI 콘텐츠를 포함하는 데 사용하는 Azure AD 앱을 선택합니다.

4. **개요** 섹션에서 **디렉터리(테넌트) ID** GUID를 복사합니다.

### <a name="power-bi-username-and-password"></a>Power BI 사용자 이름 및 암호

>[!TIP]
>**적용 대상:** ![미적용 대상: ](../../media/no.png)서비스 주체 ![적용 대상: ](../../media/yes.png)마스터 사용자

**마스터 사용자** 로 사용 중인 Power BI 사용자의 ‘사용자 이름’ 및 ‘암호’를 가져옵니다.  Power BI 서비스에서 작업 영역을 만들고 해당 작업 영역에 보고서를 업로드하는 데 사용한 것과 동일한 사용자입니다.

## <a name="step-6---service-principal-api-access"></a>6단계 - 서비스 주체 API 액세스

>[!TIP]
>**적용 대상:** ![적용 대상: ](../../media/yes.png)서비스 주체 ![미적용 대상: ](../../media/no.png)마스터 사용자
>
>이 단계는 ‘서비스 주체’ 인증 방법을 사용하는 경우에만 해당됩니다. ‘마스터 사용자’를 사용하는 경우에는 이 단계를 건너뛰고 [7단계 - 작업 영역 액세스 사용](#step-7---enable-workspace-access)으로 진행하세요.

Azure AD 앱이 Power BI 콘텐츠 및 API에 액세스할 수 있도록 Power BI 관리자는 Power BI 관리 포털에서 서비스 사용자 액세스를 사용하도록 설정해야 합니다. 테넌트 관리자가 아닌 경우 테넌트 관리자에게 ‘테넌트 설정’을 사용하도록 설정해 달라고 요청하세요.
        
1. ‘Power BI 서비스’에서 **설정** > **설정** > **관리 포털** 을 선택합니다.
        
    :::image type="content" source="media/embed-sample-for-customers/admin-settings.png" alt-text="Power BI 서비스 설정 메뉴의 관리 설정 메뉴 옵션을 보여 주는 스크린샷":::
        
2. **테넌트 설정** 을 선택한 다음 **개발자 설정** 섹션으로 스크롤합니다.
        
3. **서비스 주체가 Power BI API를 사용하도록 허용** 을 확장하고 이 옵션을 사용하도록 설정합니다.
        
    :::image type="content" source="media/embed-sample-for-customers/developer-settings.png" alt-text="Power BI 서비스에서 테넌트 설정 메뉴 옵션의 개발자 설정 옵션을 사용하도록 설정하는 방법을 보여 주는 스크린샷":::
        
>[!NOTE]
>‘서비스 주체’를 사용하는 경우 ‘보안 그룹’을 사용하여 테넌트 설정에 대한 액세스를 제한하는 것이 좋습니다.  이 기능에 대한 자세한 내용은 [서비스 주체](embed-service-principal.md) 문서에서 다음 섹션을 참조하세요.
> * [Azure AD 보안 그룹 만들기](embed-service-principal.md#step-2---create-an-azure-ad-security-group)
>* [Power BI 서비스 관리자 설정 사용](embed-service-principal.md#step-3---enable-the-power-bi-service-admin-settings)

## <a name="step-7---enable-workspace-access"></a>7단계 - 작업 영역 액세스 사용

Azure AD 앱이 Power BI 서비스의 보고서, 대시보드, 데이터 세트와 같은 아티팩트에 액세스할 수 있도록 하려면 ‘서비스 주체’ 또는 ‘마스터 사용자’를 작업 영역에 ‘멤버’ 또는 ‘관리자’로 추가합니다.   

1. Power BI 서비스에 로그인합니다.

2. 액세스를 사용하도록 설정할 작업 영역으로 스크롤한 다음 **자세히** 메뉴에서 **작업 영역 액세스** 를 선택합니다.

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Power BI 작업 영역의 추가 메뉴에 있는 작업 영역 액세스 단추를 보여주는 스크린샷.":::

3. **액세스** 창에서 사용하는 인증 방법에 따라 ‘서비스 주체’ 또는 ‘마스터 사용자’를 **메일 주소 입력** 텍스트 상자에 복사합니다. 

    >[!NOTE]
    >‘서비스 주체’를 사용하는 경우 해당 이름은 Azure AD 앱에 제공한 이름입니다.

5. **추가** 를 선택합니다.

## <a name="step-8---embed-your-content"></a>8단계 - 콘텐츠 포함

Power BI Embedded 애플리케이션 예제를 사용하여 ‘고객에 대한 콘텐츠 포함’ Power BI 앱을 만들 수 있습니다.

Power BI 보고서를 포함하도록 ‘고객에 대한 콘텐츠 포함’ 애플리케이션 예제를 수정하려면 다음 단계를 따르세요.  

1. [Power BI 개발자 샘플](https://github.com/microsoft/PowerBI-Developer-Samples) 폴더를 엽니다.

2. **Code**(코드)를 선택하고 **Download zip**(ZIP 다운로드)을 선택합니다.

    :::image type="content" source="media/embed-sample-for-customers/developer-samples.png" alt-text="Power BI 개발자 샘플 GitHub의 ZIP 다운로드 옵션을 보여 주는 스크린샷":::

3. 다운로드한 ZIP의 압축을 풀고 **PowerBI-Developer-Samples-master** 폴더로 이동합니다.

4. 애플리케이션에서 사용할 언어에 따라 다음 폴더 중 하나를 엽니다.

* .NET Core
* .NET Framework
* Java
* Node JS
* Python
    >[!NOTE]
    >‘고객에 대한 콘텐츠 포함’ 애플리케이션 예제는 위에 나열된 언어만 지원합니다. *React TS* 애플리케이션 예제는 ‘[조직에 대한 콘텐츠 포함](embed-sample-for-your-organization.md)’ 솔루션만 지원합니다.

5. **고객에 대한 콘텐츠 포함** 폴더를 엽니다.

# <a name="net-core"></a>[.NET Core](#tab/net-core)

6. 다음 방법 중 하나를 사용하여 ‘고객에 대한 콘텐츠 포함 샘플 앱’을 엽니다.

    * [Visual Studio](https://visualstudio.microsoft.com/)를 사용하는 경우 **AppOwnsData.sln** 파일을 엽니다.

    * [Visual Studio Code](https://code.visualstudio.com/)를 사용하는 경우 **App Owns Data** 폴더를 엽니다.

7. **appsettings.json** 을 엽니다.

8. 인증 방법에 따라 다음 매개 변수 값을 입력합니다.

    |매개 변수            |서비스 사용자  |마스터 사용자  |
    |---------------------|---------|---------|
    |`AuthenticationMode` |ServicePrincipal         |MasterUser         |
    |`ClientId`           |Azure AD 앱 [클라이언트 ID](#client-id)         |Azure AD 앱 [클라이언트 ID](#client-id)         |
    |`TenantId`           |Azure AD [테넌트 ID](#tenant-id)         |해당 없음         |
    |`PbiUsername`        |해당 없음         |‘마스터 사용자’ 이름([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |
    |`PbiPassword`        |해당 없음         |‘마스터 사용자’ 암호([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |
    |`ClientSecret`       |Azure AD [클라이언트 암호](#client-secret)         |해당 없음         |
    |`WorkspaceId`        |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)          |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)         |
    |`ReportId`           |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)            |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)         |

9. 적절한 옵션을 선택하여 프로젝트를 실행합니다.

    * **Visual Studio** 를 사용하는 경우 **IIS Express**(재생)를 선택합니다.

    * **Visual Studio Code** 를 사용하는 경우 **실행 > 디버깅 시작** 을 선택합니다.

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

6. [Visual Studio](https://visualstudio.microsoft.com/)를 사용하여 **AppOwnsData.sln** 파일을 엽니다.

7. **Web.config** 를 엽니다.

8. 인증 방법에 따라 다음 매개 변수 값을 입력합니다.

    |매개 변수            |서비스 사용자  |마스터 사용자  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`applicationId`           |Azure AD 앱 [클라이언트 ID](#client-id)         |Azure AD 앱 [클라이언트 ID](#client-id)         |
    |`workspaceId`        |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)          |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)         |
    |`reportId`           |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)            |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)         |
    |`pbiUsername`        |해당 없음         |‘마스터 사용자’ 이름([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |
    |`pbiPassword`        |해당 없음         |‘마스터 사용자’ 암호([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |
    |`applicationSecret`       |Azure AD [클라이언트 암호](#client-secret)         |해당 없음         |
    |`tenant`           |Azure AD [테넌트 ID](#tenant-id)         |해당 없음         |

9. **IIS Express**(재생)를 선택하여 프로젝트를 실행합니다.

>[!NOTE]
>샘플 앱을 실행할 때 포함된 보고서가 표시되지 않으면 다음 단계를 수행하여 Power BI 패키지를 새로 고칩니다.
>1. 프로젝트 이름(AppOwnesData)을 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리** 를 선택합니다.
>2. **Power BI JavaScript** 를 검색한 후 패키지를 다시 설치합니다.
>
>자세한 내용은 [How to reinstall and update packages](/nuget/consume-packages/reinstalling-and-updating-packages)(패키지 다시 설치 및 업데이트 방법)를 참조하세요.

# <a name="java"></a>[Java](#tab/java)

6. **Eclipse** 를 열고 아래에 설명된 지침을 따릅니다.

    >[!NOTE]
    >‘고객에 대한 콘텐츠 포함 샘플 앱’에 대한 지침은 [Java EE용 Eclipse 개발자](https://www.eclipse.org/downloads/packages/)(Enterprise Edition)를 참조하세요. 다른 애플리케이션을 사용하는 경우에는 직접 설정해야 합니다.

7. Eclipse에 Tomcat 서버를 추가합니다.

    a. **창** > **보기 표시** > **서버** 를 선택합니다.

    b. 서버 탭에서 **No servers are available. Click this link to create new server**(사용할 수 있는 서버가 없습니다. 새 서버를 만들려면 이 링크를 클릭합니다.)를 선택합니다.

    다. **Define a New Server**(새 서버 정의) 창에서 **Apache** 를 확장하고 머신에서 실행 중인 Tomcat 서버를 선택합니다. 예를 들어 *Tomcat v9.0 Server* 입니다.

    d. **다음** 을 선택합니다.

    e. **Tomcat 서버** 창에서 **찾아보기** 를 선택하고 Tomcat 서버가 포함된 폴더로 이동합니다.

    f. **Tomcat 서버** 창에서 **설치된 JRE** 를 선택합니다.

    g. **설치된 JRE** 창에서 사용 가능한 *jre* 를 선택하고 **적용 및 닫기** 를 선택합니다.

    h. **Tomcat 서버** 창에서 **마침** 을 선택합니다. *서버* 탭에서 Tomcat 서버를 볼 수 있습니다.

8. Eclipse에서 프로젝트를 엽니다.

    >[!IMPORTANT]
    >경로 이름이 너무 길면 Eclipse에서 문제가 발생할 수도 있습니다. 이 문제를 방지하려면 샘플 앱의 폴더가 컴퓨터의 폴더 구조에 너무 깊이 중첩되지 않았는지 확인합니다.

    a. **파일** 을 선택한 다음 **Open Projects from File System**(파일 시스템에서 프로젝트 열기)을 선택합니다.

    b. **Import Projects from File System or Archive**(파일 시스템 또는 보관에서 프로젝트 가져오기) 창에서 **디렉터리** 를 선택하고 **AppOwnsData** 폴더를 엽니다.

    다. **마침** 을 선택합니다.

9. Tomcat 서버를 프로젝트에 추가합니다.

    a. **패키지 탐색기** 창에서 **AppOwnsData** 를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다.

    b. **AppOwnesData의 속성** 창에서 **대상 런타임** 을 선택한 다음 **Apache Tomcat** 을 선택합니다. 이 선택 항목에는 사용하는 *Apache Tomcat* 버전(예: *Apache Tomact v9.0*)이 포함됩니다.

    다. **적용 및 닫기** 를 선택합니다.

10. 필수 매개 변수를 입력합니다.

    a. **패키지 탐색기** 에서 **AppOwnsData** 프로젝트를 확장합니다.

    b. **Java 리소스** 를 확장합니다.

    다. **src** 를 확장합니다.

    d. **com.embedsample.appoensdata.config** 를 확장합니다.

    e. **Config.java** 를 엽니다.

    f. 인증 방법에 따라 다음 매개 변수 값을 입력합니다.

    |매개 변수            |서비스 사용자  |마스터 사용자  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`workspaceId`        |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)          |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)         |
    |`reportId`           |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)            |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)         | 
    |`clientId`           |Azure AD 앱 [클라이언트 ID](#client-id)         |Azure AD 앱 [클라이언트 ID](#client-id)         |
    |`pbiUsername`        |해당 없음         |‘마스터 사용자’ 이름([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |
    |`pbiPassword`        |해당 없음         |‘마스터 사용자’ 암호([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |
    |`tenantId`           |Azure AD [테넌트 ID](#tenant-id)         |해당 없음         |
    |`appSecret`       |Azure AD [클라이언트 암호](#client-secret)         |해당 없음         |

11. 프로젝트 실행

    a. **패키지 탐색기** 에서 **AppOwnesData** 를 마우스 오른쪽 단추로 클릭합니다.

    b. **다음 계정으로 실행**  > **서버에서 실행** 을 선택합니다.

    다. **서버에서 실행** 창에서 **기존 서버 선택** 및 *Tomcat* 서버를 선택합니다.

    d. **마침** 을 선택합니다.

# <a name="node-js"></a>[Node JS](#tab/node-js)

6. 선호하는 IDE를 사용하여 **App Owns Data** 폴더를 엽니다. 다음 중 하나를 사용하는 것이 좋습니다.

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

7. 터미널을 열고 `npm install`을 실행하여 필요한 종속성을 설치합니다.

8. **Config** 폴더를 확장하고 **config.json** 을 엽니다.

9. 인증 방법에 따라 다음 매개 변수 값을 입력합니다.

    |매개 변수            |서비스 사용자  |마스터 사용자  |
    |---------------------|---------|---------|
    |`authenticationMode` |ServicePrincipal         |MasterUser         |
    |`clientId`           |Azure AD 앱 [클라이언트 ID](#client-id)         |Azure AD 앱 [클라이언트 ID](#client-id)         |
    |`workspaceId`        |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)          |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)         |
    |`reportId`           |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)            |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)         |
    |`pbiUsername`        |해당 없음         |‘마스터 사용자’ 이름([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |
    |`pbiPassword`        |해당 없음         |‘마스터 사용자’ 암호([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |
    |`clientSecret`       |Azure AD [클라이언트 암호](#client-secret)         |해당 없음         |
    |`tenantId`           |Azure AD [테넌트 ID](#tenant-id)         |해당 없음         |

10. 다음을 수행하여 프로젝트를 실행합니다.

    a. IDE 터미널에서 `npm start`를 실행합니다.

    b. 브라우저에서 새 탭을 열고 [http://localhost:5300](http://localhost:5300)으로 이동합니다.

# <a name="python"></a>[Python](#tab/python)

6. **PowerShell** 또는 **명령 프롬프트** 를 엽니다.

7. **Python** > **고객에 대한 콘텐츠 포함** 폴더인지 그리고 폴더에 **requirements.txt** 파일이 있는지 확인하고 `pip3 install -r requirements.txt`를 실행합니다.

8. 선호하는 IDE를 사용하여 **App Owns Data** 폴더를 엽니다. 다음 중 하나를 사용하는 것이 좋습니다.

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

9. **config.py** 를 엽니다.

10. 인증 방법에 따라 다음 매개 변수 값을 입력합니다.

    |매개 변수            |서비스 사용자  |마스터 사용자  |
    |---------------------|---------|---------|
    |`AUTHENTICATION_MODE` |ServicePrincipal         |MasterUser         |
    |`WORKSPACE_ID`        |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)          |포함된 보고서가 있는 작업 영역의 ID([작업 영역 ID](#workspace-id) 참조)         |
    |`REPORT_ID`           |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)            |포함하는 보고서의 ID([보고서 ID](#report-id) 참조)         |
    |`TENANT_ID`           |Azure AD [테넌트 ID](#tenant-id)         |해당 없음         |
    |`CLIENT_ID`           |Azure AD 앱 [클라이언트 ID](#client-id)         |Azure AD 앱 [클라이언트 ID](#client-id)         |
    |`CLIENT_SECRET`       |Azure AD [클라이언트 암호](#client-secret)         |해당 없음         |
    |`POWER_BI_USER`        |해당 없음         |‘마스터 사용자’ 이름([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |
    |`POWER_BI_PASS`        |해당 없음         |‘마스터 사용자’ 암호([Power BI 사용자 이름 및 암호 참조)](#power-bi-username-and-password)         |

11. 파일을 저장합니다.

12. 다음을 수행하여 프로젝트를 실행합니다.

    a. **PowerShell** 또는 **명령 프롬프트** 에서 **Python** > **고객에 대한 콘텐츠 포함** > **AppOwnesData** 폴더로 이동하고 `flask run`을 실행합니다.

    b. 브라우저에서 새 탭을 열고 [http://localhost:5300](http://localhost:5300)으로 이동합니다.

---

## <a name="developing-your-application"></a>애플리케이션 배포

‘고객에 대한 콘텐츠 포함’ 애플리케이션 예제 구성하고 실행한 후에 애플리케이션 개발을 시작할 수 있습니다.

준비가 되면 [프로덕션으로 이동](move-to-production.md) 요구 사항을 검토하세요. [용량](embedded-capacity.md)도 필요하며, [용량 계획](embedded-capacity-planning.md) 문서를 검토하여 요구 사항에 가장 잘 맞는 SKU를 설정해야 합니다.


## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
>[프로덕션으로 이동](move-to-production.md)

>[!div class="nextstepaction"]
>[조직에 포함](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[고객을 위해 페이지를 매긴 보고서 포함](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[조직에 대해 페이지가 매겨진 보고서 포함](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Power BI 커뮤니티에 문의](https://community.powerbi.com/)