---
title: 미국 주 및 지방 정부를 위한 COVID-19 추적 샘플
description: COVID-19 전염병에 대한 미국 주 및 지방 데이터를 사용하는 샘플 보고서를 다운로드하고 수정합니다.
author: LukaszPawlowski-MS
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/28/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: 8cdc4a9a78c20c7c4e6986b63a3af61a319df1b6
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82584936"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>미국 주 및 지방 정부를 위한 COVID-19 추적 샘플

Power BI 팀은 미국 주 및 지방 정부가 COVID-19에 대한 대화형 보고서를 게시하거나 사용자 지정할 수 있는 COVID-19 추적 샘플을 만들었습니다. Power BI Desktop을 사용하여 COVID-19 데이터를 분석하고 시각화하여 시, 카운티, 주 및 전국 수준에서 커뮤니티에 정보를 제공할 수 있습니다. 그런 다음 Power BI 웹에 게시 기능을 사용하여 시민에게 보고서를 공개할 수 있습니다. 이 문서에서는 자체 공용 스토리, 블로그 또는 웹 사이트에서 Power BI 대화형 시각화를 사용하기 위한 여러 옵션을 제공합니다.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="미국 데이터를 사용하는 COVID-19 샘플":::

이 문서에서는 다음 작업을 수행하는 방법을 설명합니다.

- Embed 태그를 복사하여 자체 사이트에 배치 
- 특정 주 서식 지정 등의 사용자 지정을 수행
- Power BI 서비스에 게시
- 웹에 게시 
- 이 데이터를 다른 원본의 데이터와 매시업 

## <a name="prerequisites"></a>필수 조건

Power BI를 사용하여 스토리를 알리기 전에 다음과 같은 사전 준비가 필요합니다.

- 무료 [Power BI Desktop](https://powerbi.microsoft.com/desktop/) 앱을 다운로드합니다.
- [Power BI 서비스](https://powerbi.microsoft.com/get-started/)에 등록합니다.

## <a name="option-1-pre-built-embed-code"></a>옵션 1: 미리 작성된 embed 태그

Microsoft는 샘플 보고서를 게시하고 웹에 게시 embed 태그를 만들었습니다. Embed 태그를 사용하여 전국 보기를 포함하는 전체 샘플을 포함하고 사용자의 웹 사이트에서 주 및 카운티 수준으로 드릴다운할 수 있습니다. 이 데이터를 게시하기 전에 이 문서의 [고지 사항](#disclaimers)을 검토하는 것이 좋습니다.

대화형 그래픽을 사이트에 포함시키려면 다음 embed 태그를 복사하여 웹 페이지에서 그래픽을 표시하려는 위치에 붙여넣습니다.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

Embed 태그는 HTML 페이지에 삽입할 수 있는 HTML iFrame 요소입니다. 제공된 iFrame의 너비와 높이를 사이트에 맞게 조정합니다. 샘플 보고서는 16:9 비율로 작성되었으므로 이 차원을 유지하는 크기를 선택합니다. 올바르게 구현되면 그래픽이 회색 테두리 없이 표시됩니다. 이러한 변경 작업을 수행할 때 [iFrame 크기 조정 팁과 요령을 검토](../service-publish-to-web.md#tips-for-iframe-height-and-width)하면 유용합니다.

## <a name="option-2-customize-the-sample-power-bi-file"></a>옵션 2: 샘플 Power BI 파일 사용자 지정

Power BI 파일에는 Power BI Desktop에서 편집할 수 있는 데이터 및 대화형 그래픽이 .pbix 파일 형식으로 포함되어 있습니다.  

일반적인 사용자 지정은 보고서를 특정 주로 필터링한 다음 사용자 지정된 보고서에 대한 자체 웹 게시 embed 태그를 만드는 것입니다.

USAFacts 데이터는 저작자 표시가 필요한 Creative Commons 라이선스로 제공됩니다. 이 데이터를 게시하기 전에 [고지 사항](#disclaimers)을 검토하세요.

시작하려면 [.pbix 파일(여기)을 다운로드](https://go.microsoft.com/fwlink/?linkid=2125058)합니다.

### <a name="update-your-report"></a>보고서 업데이트 

1. 아직 다운로드하지 않은 경우 무료 앱 [Power BI Desktop](https://powerbi.microsoft.com/desktop/)의 최신 버전을 다운로드합니다. 

2. 아직 다운로드하지 않은 경우 [.pbix 파일](https://go.microsoft.com/fwlink/?linkid=2125058)을 다운로드하고 Power BI Desktop에서 파일을 엽니다.

3. 보고서를 특정 주로 필터링하려면 화살표를 선택하여 필터 창을 확장합니다.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="필터 확장 창":::

4. 관심이 있는 주를 선택합니다. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="주 선택":::

5. 파일을 저장하려면 **파일** > **저장**을 선택합니다. 

### <a name="refresh-your-report"></a>보고서 새로 고침 

1. **새로 고침** 단추를 클릭합니다.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="새로 고침 단추":::

2. **익명** > **연결**을 선택합니다. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="익명 선택":::

 
3. 표시되는 경우 **개인 정보 수준 무시** > **저장**을 선택합니다. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="개인 정보 수준 선택":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Power BI 서비스에 보고서 게시

보고서를 원하는 대로 사용자 지정했으면 [여기에 설명된 단계에 따라 보고서를 Power BI 서비스에 게시](../desktop-upload-desktop-files.md)합니다.

### <a name="configure-scheduled-refresh"></a>예약된 새로 고침 구성

보고서 데이터를 최신 상태로 유지하려면 보고서를 게시한 후 [예약된 새로 고침을 구성](../refresh-scheduled-refresh.md)할 수 있습니다.

해당 단계를 수행할 때 다음 옵션을 선택합니다.

1. 데이터 원본 자격 증명 인증 방법: 익명
2. 이 데이터 원본에 대한 개인 정보 수준 설정: 공개

새로 고침 설정을 테스트하려면 데이터 세트 항목에서 사용할 수 있는 [지금 새로 고침](../refresh-data.md#data-refresh) 옵션을 선택합니다.

새로 고친 데이터는 일정이 실행될 때마다 로드됩니다. 기본 데이터는 USAFacts에서 제공되며 설정한 새로 고침 일정만큼 자주 업데이트되지 않을 수 있습니다. [USAFacts 웹 사이트](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/)를 확인하여 기본 데이터가 마지막으로 업데이트된 시기를 알 수 있습니다. 

사용자 지정된 보고서를 웹 사이트에 게시하려는 경우에는 적어도 USAFacts 데이터 업데이트 빈도만큼 예약된 새로 고침을 실행하도록 구성하는 것이 가장 좋습니다. USAFacts가 매일 다른 시간에 데이터를 새로 고칠 수 있으므로 매일 여러 번의 새로 고침을 구성하는 것이 좋습니다. 

### <a name="create-a-publish-to-web-embed-code"></a>웹에 게시 embed 태그 만들기 

사용자 지정 보고서를 자체 웹 사이트에 포함하려면 [자체 웹에 게시 embed 태그를 만드는 방법](../service-publish-to-web.md#create-embed-codes-with-publish-to-web)에 대한 지침을 따릅니다.

Embed 태그를 게시한 후에는 확인 대화 상자에서 iFrame을 사용하여 웹 사이트에 포함합니다.

Power BI Desktop에서 보고서를 변경한 경우 Power BI 서비스에서 게시하여 기존 보고서를 바꿀 수 있습니다. Embed 태그는 변경되지 않습니다. 보고서 변경 내용 또는 새로 고친 데이터를 웹 사이트에 표시하는 데 약 1시간이 걸립니다. 

## <a name="option-3-mash-up-data-from-another-source"></a>옵션 3: 다른 원본에서 데이터 매시업 

이 보고서의 데이터를 다른 원본의 데이터와 매시업할 수도 있습니다. 다음 예제는 [Johns Hopkins 대학교](https://github.com/CSSEGISandData/COVID-19)의 데이터를 기반으로 합니다. 이 데이터를 게시하기 전에 이 문서의 [고지 사항](#disclaimers)을 검토하는 것이 좋습니다.

1. **데이터 가져오기** > **웹**을 선택합니다.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="데이터 단추 가져오기":::

2. 다음 URL을 입력합니다.

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="웹에서 데이터 선택":::

3. **확인**을 선택합니다. 

    > [!NOTE]
    > Johns Hopkins 대학교에서 게시한 링크는 변경될 수 있습니다. 최신 정보는 [Johns Hopkins GitHub 페이지](https://github.com/CSSEGISandData/COVID-19)를 확인하세요.

4. **로드**를 선택하여 전 세계적 총 확진자 수에 대한 데이터 세트를 로드합니다.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="웹에서 데이터 로드":::

    이 문서 [Power BI Desktop에서 웹 페이지에 연결](../desktop-connect-to-web.md)에서는 웹에서 데이터를 로드하는 방법을 자세히 설명합니다.
    
그런 다음 Power BI Desktop을 사용하여 데이터를 시각화할 수 있습니다. 마지막으로 **옵션 2:** [Power BI 서비스에 보고서 게시](#publish-your-report-to-the-power-bi-service)의 단계를 사용하여 보고서를 게시하고 사용자 지정 embed 태그를 만듭니다. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>옵션 4: 코로나바이러스감염증-19 미국 추적 템플릿 앱 사용

한 가지 옵션이 더 있습니다. Power BI 팀은 사용자가 곧바로 시작할 수 있도록 코로나바이러스감염증-19 미국 추적 ‘템플릿 앱’을 만들었습니다.  템플릿 앱은 특정 데이터 원본에 대한 보고서, 대시보드, 데이터 세트의 번들입니다. 템플릿 앱은 AppSource에서 다운로드하여 필요에 맞게 사용하거나 수정할 수 있으며, 동료들에게 배포할 수 있습니다. 

코로나바이러스감염증-19 미국 추적 템플릿 앱에는 그대로 사용하거나 Power BI 서비스에서 곧바로 사용자 지정하거나 원하는 경우 다른 데이터 원본에 다운로드하여 추가할 수 있는 미리 작성된 코로나바이러스감염증-19 메트릭 보고서가 포함되어 있습니다. [코로나바이러스감염증-19 미국 추적 템플릿 앱](../connect-data/service-connect-to-covid-19-tracking.md)을 설치하는 방법을 알아보고 바로 시작하세요.

## <a name="about-the-data-source-for-this-report"></a>이 보고서용 데이터 원본 정보
이 대화형 보고서는 질병통제센터(CDC)와 주 및 지방 보건 기관에서 데이터를 집계합니다. 카운티 수준 데이터는 주 및 지방 보건 기관을 직접 참조(링크)하여 확인됩니다.

데이터는 USAFacts에서 제공합니다. 데이터 업데이트 빈도 때문에 정부 기관 또는 뉴스 미디어에서 보고한 정확한 수치가 반영되지 않을 수 있습니다. 자세한 내용을 보거나 데이터를 다운로드하려면 [USAFacts 웹 사이트](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/)를 참조하세요. 

## <a name="disclaimers"></a>고지 사항

이 보고서 및 데이터는 어떠한 종류의 보증도 없이 "모든 오류를 포함하여" "있는 그대로" 제공됩니다. Microsoft는 어떠한 명시적 보증 또는 보장도 하지 않으며 상품성, 특정 목적 적합성 및 비침해를 비롯한 모든 묵시적 보증을 명시적으로 부인합니다.

USAFacts 데이터는 Creative Commons 라이선스로 사용할 수 있습니다. 이 데이터를 사용하려면 USAFacts를 데이터 공급자로 인용하고 USAFacts로 다시 연결합니다. 정확한 저작자 표시 단계는 USAFacts 페이지 [미국의 코로나 바이러스: 주별 COVID-19 발생 매핑](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/)의 **#MadewithUSAFacts** 섹션을 참조하세요.

Johns Hopkins 대학교 데이터는 Copyright 2020 Johns Hopkins University에 따라 모든 권리가 보호됩니다. 이 데이터는 교육 및 학술 연구용으로만 일반에 제공됩니다. 다음은 매시업 예제에 표시된 데이터의 [사용 약관](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) 전문입니다. 자세한 내용은 [Johns Hopkins 대학교 웹 사이트](https://coronavirus.jhu.edu/map-faq.html)에서 확인할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[Power BI용 샘플 가져오기](../sample-datasets.md)