---
title: 페이지를 매긴 보고서의 URL 매개 변수 - Power BI 보고서 작성기
description: 이메일이나 웹 페이지에 포함할 수 있는 URL에 매개 변수를 추가하여 Power BI에서 페이지를 매긴 보고서에 명령을 보내는 방법에 대해 알아봅니다.
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 09/09/2020
ms.openlocfilehash: 4284ba559bff0ba0a3bde7dd34c6f26034ecf12e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415568"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Power BI에서 페이지를 매긴 보고서의 URL 매개 변수

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

URL에 매개 변수를 추가하여 Power BI에서 페이지를 매긴 보고서에 명령을 보낼 수 있습니다. 예를 들어, 특정 보고서 매개 변수 값을 사용하여 보고서를 보았을 수 있습니다. 미리 정의된 URL 액세스 매개 변수를 사용하여 이 정보를 URL에 캡슐화합니다. 형식을 렌더링하거나 보고서 도구 모음의 모양과 느낌을 바꾸기 위한 매개 변수를 포함하여 Power BI에서 보고서를 처리하는 방법을 추가로 사용자 지정할 수 있습니다. 그런 다음, 이 URL을 메일이나 웹 페이지에 직접 붙여넣어 다른 사용자의 브라우저에서도 같은 방식으로 보고서를 표시할 수 있습니다. 

URL 액세스 매개 변수를 통해 수행할 수 있는 작업은 다음과 같습니다. 

- 보고서에 보고서 매개 변수를 보냅니다. 
- 지원되는 파일 형식으로 보고서 내용을 내보내기 시작합니다. 
- 매개 변수 창을 숨기거나 표시합니다. 
- DeviceInfo 설정을 지정합니다. 

URL 액세스를 통해 사용할 수 있는 명령 및 설정의 전체 목록은 이 문서 뒷부분에 나오는  [URL 액세스 매개 변수 참조](#url-access-parameter-reference)를 참조하세요. 

## <a name="url-access-concepts"></a>URL 액세스 개념 

Power BI에 대한 URL 요청은 서비스에서 처리하는 매개 변수를 포함합니다. 서비스에서 URL 요청을 처리하는 방법은 매개 변수, 매개 변수 접두사, URL에 포함된 항목의 형식에 따라 달라집니다. 페이지를 매긴 보고서 URL 기능은 표준 URL 주소 지정을 지원하는 대부분의 브라우저 및 애플리케이션과 호환됩니다. 

## <a name="url-access-syntax"></a>URL 액세스 구문 

URL 요청에는 임의의 순서로 나열된 여러 매개 변수가 포함될 수 있습니다. 매개 변수는 앰퍼샌드(&)로 구분됩니다. 이름 및 값 쌍은 등호(=)로 구분됩니다. 예:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>구문 설명 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

Power BI 테넌트의 웹 서비스 URL입니다. 예: 

**&** URL 액세스 매개 변수의 이름 및 값 쌍을 구분하는 데 사용됩니다.

**prefix** Power BI 서비스의 동작을 지정하는 URL 매개 변수의 접두사(예:  rp: or rdl:)입니다. 

> [!NOTE]
> 보고서 매개 변수는 매개 변수 접두사가 필요하며 대/소문자를 구분합니다. 

**parameter** 매개 변수 이름입니다. 

### <a name="value"></a>value 

사용 중인 매개 변수의 값에 해당하는 URL 텍스트입니다. 

URL에 보고서 매개 변수를 전달하는 예는  [URL에 보고서 매개 변수 전달](report-builder-url-pass-parameters.md)을 참조하세요.

## <a name="url-access-parameter-reference"></a>URL 액세스 매개 변수 참조

다음 매개 변수를 URL의 일부로 사용하여 Power BI에서 페이지를 매긴 보고서의 모양과 느낌을 구성할 수 있습니다. 가장 일반적인 매개 변수는 이 섹션에 나와 있습니다. 매개 변수는 대/소문자를 구분하지 않고 출력 형식과 연관된 매개 변수 prefix `rdl:` if로 시작됩니다.  

### <a name="report-commands-rdl"></a>보고서 명령(`rdl:`) 

**내보내기 형식** 보고서를 렌더링하고 내보낼 형식을 지정합니다.

예: rdl:format=PDF

사용 가능한 값은 다음과 같습니다.
 
- PPTX(PowerPoint)
- MHTML 
- 이미지 
- EXCELOPENXML(EXCEL) 
- WORDOPENXML(WORD) 
- CSV 
- PDF 
- ACCESSIBLEPDF(PDF)
- XML 

**보고서 보기** 보고서를 표시하는 데 사용되는 보기 유형을 지정합니다.

-   rdl:reportView

    - 'interactive'(기본값): 보고서를 대화형 모드로 로드합니다.
    - 'pageView': 보고서를 페이지 보기 모드로 로드합니다.

**매개 변수 패널** 보고서가 로드될 때 매개 변수 패널이 열려 있는지 닫혀 있는지 아니면 모두 숨겨져 있는지를 지정합니다.

-   rdl:parameterPanel

    - ‘collapsed’: 매개 변수 패널이 닫힌 상태로 보고서를 로드합니다. 사용자가 단추를 클릭하여 확장할 수 있도록 매개 변수 단추가 사용 설정됩니다.
    - ‘hidden’: 매개 변수 패널이 닫혀 있고 매개 변수 단추가 비활성화된 상태로 보고서를 로드합니다.
    - ‘expanded’(기본값): 매개 변수 패널이 열려 있고 매개 변수 단추를 사용할 수 있는 상태로 보고서를 로드합니다.

**장치 정보** 다음 내보내기 형식에 대한 추가 출력 매개 변수를 지정할 수 있습니다. 

PDF / ACCESSIBLEPDF:

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
    - rdl:StartPage=integer
    
CSV:

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - rdl:UseFormattedValues=true/false
    
WORDOPENXML (WORD):

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL):

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint):
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML:

- rdl:XSLT=string
- rdl:MIMEType=string
- rdl:UseFormattedValues=true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:Schema=true/false

**동일한 브라우저 창에서 하이퍼링크 열기** 보고서의 하이퍼링크 URL에 ‘rdl:targetSameWindow=true’를 추가하여 Power BI가 동일한 브라우저 창에서 이 하이퍼링크를 열도록 할 수 있습니다. 보고서에 하이퍼링크를 추가하는 방법에 대한 자세한 내용은 SQL Server Reporting Services 설명서에서 [URL에 하이퍼링크 추가](/sql/reporting-services/report-design/add-a-hyperlink-to-a-url-report-builder-and-ssrs)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [Power BI에서 페이지를 매긴 보고서에 대한 URL에 보고서 매개 변수 전달](report-builder-url-pass-parameters.md)
- [Power BI Premium에서 페이지를 매긴 보고서란?](paginated-reports-report-builder-power-bi.md)