---
title: Power BI 서비스 - 비즈니스 사용자를 위한 기본 개념
description: Power BI 서비스 앱, 작업 영역, 대시보드, 보고서, 데이터 세트 및 통합 문서입니다.
author: mihart
ms.reviewer: mihart
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.custom: seodec18
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/08/2020
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: 5c534436b93205d40251c26830be4d6acdfa034d
ms.sourcegitcommit: 6b436f6ed872cbc040ed6e2d3ac089c08fc78daf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928377"
---
# <a name="basic-concepts-for-the-power-bi-service-consumers"></a>Power BI 서비스 소비자를 위한 기본 개념

[!INCLUDE[consumer-appliesto-ynnm](../includes/consumer-appliesto-ynnm.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

이 문서에서는 [Power BI 개요](../fundamentals/power-bi-overview.md)를 이미 읽었고 자신을 [Power BI 비즈니스 사용자](end-user-consumer.md)로 인식하고 있다고 가정합니다. *비즈니스 사용자* 는 동료로부터 대시보드, 보고서 및 앱과 같은 Power BI 콘텐츠를 받습니다. *비즈니스 사용자* 는 Power BI의 웹 사이트 기반 버전인 Power BI 서비스(app.powerbi.com)를 사용합니다.

다른 사용자로부터 콘텐츠를 받으려면 다음 중 하나가 필요합니다.
- Power BI Pro 사용자 라이선스
- 조직에서 Power BI Premium에 대한 구독을 보유하고 Power BI Premium 용량에서 콘텐츠를 공유할 수 있습니다. [라이선스 및 구독 유형을 조회](end-user-license.md)합니다.

분명히 “Power BI Desktop” 또는 “Desktop”이라는 용어를 들어 보았을 것입니다. 이는 대시보드와 보고서를 빌드하고 소비자와 공유하는 ‘디자이너’가 사용하는 독립 실행형 도구입니다.  다른 Power BI 도구가 있다는 것을 알고 있어야 합니다. 비즈니스 사용자**인 한 Power BI 서비스만 사용하게 됩니다. 이 문서는 Power BI 서비스에만 적용됩니다.

## <a name="terminology-and-concepts"></a>용어 및 개념

이 문서는 Power BI의 시각적 둘러보기나 실습용 자습서가 아닙니다. 오히려 Power BI 용어 및 개념을 익힐 수 있는 개요 문서입니다. 용어와 전반적인 개념을 알려줄 것입니다. Power BI 서비스 및 해당 탐색을 둘러보려면 [빠른 시작 - Power BI 서비스 살펴보기](end-user-experience.md)를 방문하세요.

## <a name="open-the-power-bi-service-for-the-first-time"></a>Power BI 서비스를 처음으로 열기

대부분의 Power BI *비즈니스 사용자* 는 1) 자신의 회사에서 라이선스를 구입했고, 2) 관리자가 라이선스를 직원에게 할당했기 때문에 Power BI 서비스를 사용합니다.

시작하려면 브라우저를 열고 **app.powerbi.com** 을 입력합니다. Power BI 서비스를 처음 열면 다음과 같은 내용이 표시됩니다.

![Power BI 서비스 시작 화면의 스크린샷](media/end-user-basic-concepts/power-bi-home-open.png)

Power BI 서비스를 사용할 때는 웹 사이트를 열 때마다 표시되는 내용을 개인 설정할 수 있습니다. 예를 들어 Power BI가 **홈** 으로 열리는 것을 선호하는 사람도 있고, 즐겨찾기 대시보드에 먼저 표시되는 것을 선호하는 사람도 있습니다. 걱정하지 마세요. 환경을 개인 설정하는 방법은 이러한 두 문서에서 설명합니다.

- [Power BI 홈 및 전역 검색 소개](https://powerbi.microsoft.com/blog/introducing-power-bi-home-and-global-search)

- [Power BI 서비스의 주요 대시보드](end-user-featured.md)

![홈페이지 보기 및 대시보드 보기를 보여 주는 스크린샷](media/end-user-basic-concepts/power-bi-dash-home.png)

하지만 좀 더 자세히 살펴보기 전에 Power BI 서비스를 구성하는 요소에 대한 이야기로 돌아가 보겠습니다.

_______________________________________________________

## <a name="power-bi-content"></a>Power BI 콘텐츠

### <a name="introduction-to-building-blocks"></a>구성 요소 소개

Power BI *비즈니스 사용자* 를 위한 5가지 구성 요소는 **_시각화_** , **_대시보드_** , **_보고서_** , **_앱_** 및 **_데이터 세트_** 입니다. 이를 *Power BI* **_콘텐츠_** 라고 부르기도 합니다. *콘텐츠* 는 **_작업 영역_** 에 있습니다. 일반적인 워크플로에서는 이와 같은 구성 요소가 모두 사용됩니다. Power BI *디자이너* (아래 다이어그램에서 노란색으로 표시)는 *데이터 세트* 에서 데이터를 수집하고, 분석을 위해 Power BI로 가져오고, 유용한 사실과 인사이트를 보여 주는 다양한 *시각화* 로 구성된 *보고서* 를 만들고, 보고서의 시각화를 *대시보드* 에 고정하고, 보고서 및 대시보드를 *비즈니스 사용자* 와 공유합니다(아래 다이어그램에서 검은색으로 표시). *디자이너* 는 대시보드, 보고서 또는 앱의 형태로 공유합니다.

![기본 Power BI 워크플로 차트입니다.](media/end-user-basic-concepts/power-bi-workflow.png)

가장 기본적으로

- ![시각화 아이콘의 스크린샷](media/end-user-basic-concepts/visual.png) **_시각화_** (또는 *시각적 개체* )는 Power BI *디자이너* 가 빌드한 차트 유형입니다. 시각적 개체는 ‘보고서’ 및 ‘데이터 세트’의 데이터를 표시합니다.  일반적으로 *설계자* 는 Power BI Desktop의 시각적 개체를 빌드합니다.

    자세한 내용은 [보고서, 대시보드 및 앱에서 시각적 개체 조작](end-user-visualizations.md)을 참조하세요.

- ![데이터베이스 아이콘의 스크린샷](media/end-user-basic-concepts/power-bi-dataset-icon.png) ‘데이터 세트’는 데이터의 컨테이너입니다.  예를 들어 세계 보건 기구의 Excel 파일이 여기에 해당할 수 있습니다. 회사 소유의 고객 데이터베이스 또는 Salesforce 파일일 수도 있습니다. 데이터 세트는 *디자이너* 가 관리합니다.

- ![대시보드 아이콘의 스크린샷](media/end-user-basic-concepts/dashboard.png) ‘대시보드’는 대화형 시각적 개체, 텍스트 및 그래픽이 표시되는 단일 화면입니다.  대시보드는 가장 중요한 메트릭을 하나의 화면에 담아 스토리를 알려주거나 궁금증을 해결해 줍니다. 대시보드 콘텐츠는 하나 이상의 보고서와 하나 이상의 데이터 세트에서 가져옵니다.

    자세한 내용은 [Power BI 서비스 비즈니스 사용자에 대한 대시보드](end-user-dashboards.md)를 참조하세요.

- ![보고서 아이콘의 스크린샷](media/end-user-basic-concepts/report.png) ‘보고서’는 대화형 시각적 개체, 텍스트 및 그래픽으로 구성된 여러 페이지의 모음을 말합니다.  Power BI는 단일 데이터 세트를 기반으로 보고서를 만듭니다. 종종 *디자이너* 는 주 관심 분야를 다루거나 단일 질문에 답하도록 보고서 페이지를 구성합니다.

    자세한 내용은 [Power BI의 보고서](end-user-reports.md)를 참조하세요.

- ![앱 아이콘의 스크린샷](media/end-user-basic-concepts/app.png) ‘앱’은 ‘디자이너’가 관련 대시보드와 보고서를 번들로 묶고 공유하는 방법입니다.  *비즈니스 사용자* 는 일부 앱을 자동으로 받지만 동료나 커뮤니티에서 만든 다른 앱을 검색하러 갈 수도 있습니다. 예를 들어 Google Analytics 및 Microsoft Dynamics CRM과 같이 이미 사용할 수 있는 외부 서비스에 기본 앱을 사용할 수 있습니다.

명확하게 말하면, 신규 사용자가 Power BI 서비스에 처음 로그인한 경우 아직 대시보드, 앱 또는 보고서가 표시되지 않을 수 있습니다.

_______________________________________________________

## <a name="datasets"></a>데이터 세트

*데이터 세트* 는 *설계자* 가 가져오거나 연결한 다음, 보고서와 대시보드를 빌드하는 데 사용하는 데이터 컬렉션입니다. *비즈니스 사용자* 는 데이터 세트와 직접 상호 작용하지 않지만 더 큰 그림에 어떻게 부합하는지 알아보면 도움이 될 것입니다.  

각 데이터 세트는 단일 데이터 원본을 나타냅니다. 예를 들어 원본은 OneDrive, 온-프레미스 SQL Server Analysis Services 테이블 형식 데이터 세트 또는 Salesforce 데이터 세트에 해당할 수 있습니다. Power BI는 다양한 데이터 원본을 지원합니다.

디자이너가 사용자와 앱을 공유할 때 **관련 콘텐츠** 를 열어 사용 중인 데이터 세트를 조회할 수 있습니다.  데이터 세트에서 어떤 것도 추가하거나 변경할 수 없습니다. 그러나 디자이너가 사용자에게 권한을 부여하면 보고서를 다운로드하거나, [데이터에서 인사이트](end-user-insights.md)를 확인하거나, 데이터 세트를 기반으로 [고유한 보고서를 만들](../create-reports/service-report-create-new.md) 수도 있습니다.  

![캔버스에서 데이터 세트 섹션을 가리키는 화살표와 Power BI 사용자 인터페이스의 스크린샷.](media/end-user-basic-concepts/power-bi-datasets.png)

하나의 데이터 세트...

- 보고서 디자이너가 사용하여 대시보드와 보고서를 만드는 데 반복해서 사용할 수 있습니다.

- 다양한 보고서를 만드는 데 사용할 수 있습니다.

- 단일 데이터 세트의 시각적 개체가 다양한 대시보드에 표시될 수 있습니다.

  ![다 대 일 관계가 있는 데이터 세트를 보여 주는 그래픽](media/end-user-basic-concepts/drawing2.png)

다음 단원(시각화)에서 계속.

_______________________________________________________

## <a name="visualizations"></a>시각화

시각화(시각적 개체라고도 함)는 Power BI가 데이터에서 검색하는 인사이트를 표시합니다. 인간의 뇌는 숫자로 된 스프레드시트보다 그림을 더 빠르게 이해하므로 시각화를 사용하면 인사이트를 더 쉽게 파악할 수 있습니다.

Power BI에서 볼 수 있는 시각화 중 일부는 폭포, 리본, 트리맵, 원형, 깔때기, 카드, 분산형 및 계기입니다.

   ![8가지 샘플 시각적 개체의 스크린샷](media/end-user-basic-concepts/power-bi-visuals.png)

[Power BI에 포함된 시각화의 전체 목록](end-user-visual-type.md)을 참조하세요.

*사용자 지정 시각적 개체* 라는 특수 시각화는 커뮤니티에서 사용할 수 있습니다. 인식할 수 없는 시각적 개체가 포함된 보고서를 받은 경우 사용자 지정 시각적 개체일 가능성이 높습니다. 사용자 지정 시각적 개체를 해석하는 데 도움이 필요하면 보고서 또는 대시보드 ‘디자이너’의 이름을 조회하고 해당 디자이너에게 문의하세요.  연락처 정보는 상단 메뉴 모음에서 제목을 선택하여 사용할 수 있습니다.

한 보고서의 단일 시각화...

- 동일한 보고서에 여러 번 표시될 수 있습니다.

- 다양한 대시보드에 표시될 수 있습니다.

_______________________________________________________

## <a name="reports"></a>보고서

Power BI 보고서는 시각화, 그래픽 및 텍스트로 이루어진 하나 이상의 페이지입니다. 보고서의 모든 시각화는 단일 데이터 세트에서 제공합니다. *디자이너* 는 보고서를 빌드하고 개인적으로 또는 앱에 포함하는 방법으로 다른 사용자와 공유합니다.  일반적으로 *비즈니스 사용자* 는 [*읽기용 보기* 에서 보고서와 상호 작용](end-user-reading-view.md)합니다.

![탭이 있는 보고서의 스크린샷](media/end-user-basic-concepts/power-bi-report.png)

단일 보고서...

- 여러 대시보드에 연결할 수 있습니다(보고서에 고정된 타일이 여러 대시보드에 나타날 수 있습니다).

- 데이터 세트 하나의 데이터만 사용하여 만들 수 있습니다.  

- 여러 앱의 일부일 수 있습니다.

  ![보고서의 관계를 보여 주는 그래픽](media/end-user-basic-concepts/drawing5.png)

_______________________________________________________

## <a name="dashboards"></a>대시보드

대시보드는 기본 데이터 세트의 일부 하위 집합에 대한 사용자 지정된 그래픽 보기를 나타냅니다. *디자이너* 는 대시보드를 빌드하고 개인적으로 혹은 앱에 포함하는 방법으로 *비즈니스 사용자* 와 공유합니다. 대시보드는 ‘타일’, 그래픽 및 텍스트가 포함된 단일 캔버스입니다. 

  ![샘플 대시보드의 스크린샷](media/end-user-basic-concepts/power-bi-dashboard.png)

타일은 *디자이너가 보고서에서 대시보드 등으로* *고정* 하는 시각적 개체의 렌더링입니다. 고정된 각 타일에는 디자이너가 데이터 세트에서 만들고 대시보드에 고정한 [시각화](end-user-visualizations.md)가 표시됩니다. 또한 타일에는 전체 보고서 페이지가 포함될 수 있으며, 라이브 스트리밍 데이터 또는 동영상도 포함될 수 있습니다. *디자이너* 가 대시보드에 타일을 추가하는 여러 가지 방법이 있지만 이 개요 항목에서 다루기엔 너무 많습니다. 자세히 알아보려면 [Power BI의 대시보드 타일](end-user-tiles.md)을 참조하세요.

*비즈니스 사용자* 는 대시보드를 편집할 수 없습니다. 하지만 주석을 추가하고, 관련 데이터를 보고, 즐겨찾기로 설정하고, 구독하는 등의 작업은 가능합니다.

대시보드는 어떤 용도로 사용됩니까?  다음은 몇 가지 예입니다.

- 의사 결정을 내리는 데 필요한 모든 정보를 한 눈에 보기 위해서

- 비즈니스에 가장 중요한 정보를 모니터링하기 위해서

- 모든 동료가 동일한 페이지에서 동일한 정보를 보고 사용하도록 하기 위해서

- 비즈니스, 제품, 사업부, 마케팅 캠페인 등의 상태를 모니터링하기 위해서

- 더 큰 대시보드의 개인 설정된 보기를 만들어 자신에게 중요한 모든 메트릭을 표시하기 위해서

**하나의** 대시보드는...

- 여러 데이터 세트의 시각화를 표시할 수 있습니다.

- 여러 보고서의 시각화를 표시할 수 있습니다.

- 다른 도구(예: Excel)에서 고정된 시각화를 표시할 수 있습니다.

  ![대시보드 관계의 그래픽](media/end-user-basic-concepts/drawing1.png)

_______________________________________________________

## <a name="apps"></a>앱

이러한 대시보드 및 보고서 컬렉션은 관련 콘텐츠를 단일 패키지로 정리합니다. Power BI *디자이너* 는 작업 영역에서 이를 빌드하고 개인, 그룹, 전체 조직 또는 대중과 앱을 공유합니다. *비즈니스 사용자* 는 자신이 동료와 동일한 정보(단일 버전의 진실한 정보)로 작업하고 있음을 확신할 수 있습니다.

경우에 따라 앱의 작업 영역 자체가 공유되고 많은 사람이 작업 영역과 앱을 모두 공동 작업하고 업데이트할 수 있습니다. 앱에서 수행할 수 있는 작업의 범위는 지정된 권한 및 액세스에 따라 결정됩니다.

![앱 사용 권한 화면의 스크린샷.](media/end-user-basic-concepts/power-bi-app-permissions.png)

> [!NOTE]
> 앱을 사용하려면 Power BI Pro 라이선스가 필요하거나 앱 작업 영역을 프리미엄 용량에 저장해야 합니다. [라이선스에 대해 알아봅니다](end-user-license.md).



앱은 [Power BI 서비스](https://powerbi.com) 및 모바일 디바이스에서 쉽게 찾아 설치할 수 있습니다. 앱을 설치한 후에는 다양한 대시보드와 보고서의 이름을 기억할 필요가 없습니다. 여러 대시보드가 모두 앱, 브라우저 또는 모바일 디바이스에 함께 있습니다.

이 앱에는 단일 앱을 구성하는 두 개의 대시보드와 두 개의 보고서가 있습니다. 보고서 이름 오른쪽에 있는 화살표를 선택하면 해당 보고서를 구성하는 페이지의 목록이 표시됩니다.

![선택한 앱과 관련된 콘텐츠의 스크린샷](media/end-user-basic-concepts/power-bi-app-display.png)

앱이 업데이트될 때마다 변경 내용이 자동으로 표시됩니다. 또한 디자이너는 Power BI가 데이터를 새로 고치는 빈도에 대한 일정을 제어합니다. 데이터를 최신 상태로 유지하는 것에 대해서는 염려하지 않아도 됩니다.

몇 가지 방법으로 앱을 가져올 수 있습니다.

- 앱 디자이너는 Power BI 계정에 자동으로 앱을 설치할 수 있습니다.

- 앱 디자이너는 앱의 직접 링크를 소비자에게 보낼 수 있습니다.

- 조직 또는 커뮤니티에서 사용할 수 있는 앱을 Power BI 서비스 내에서 검색할 수 있습니다. 사용할 수 있는 모든 앱을 볼 수 있는 [Microsoft AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi)를 방문할 수도 있습니다.

모바일 디바이스의 Power BI에서는 AppSource가 아닌 직접 링크를 통해서만 설치할 수 있습니다. 앱 설계자가 앱을 자동 설치할 경우 앱 목록이 표시됩니다.

앱을 설치한 후 앱 목록에서 선택하고 어떤 대시보드나 보고서를 첫 번째로 열어서 살펴볼지 선택합니다.

![Power BI의 왼쪽 창에서 선택된 앱의 스크린샷](media/end-user-basic-concepts/power-bi-apps-card.png)

이 문서가 비즈니스 사용자용 Power BI 서비스를 이루는 구성 요소를 이해하는 데 도움이 되었기를 바랍니다.

## <a name="next-steps"></a>다음 단계

- [용어집](end-user-glossary.md) 검토 및 책갈피에 추가

- [Power BI 서비스 둘러보기](end-user-experience.md)

- [비즈니스 사용자를 위해 특별히 작성된 Power BI 개요](end-user-consumer.md) 읽기

- Will이 Power BI 서비스의 기본 개념을 검토하고 간략한 둘러보기를 제공하는 동영상을 보세요.

    <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
