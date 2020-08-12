---
title: R 스크립트에서 R 시각적 개체로 깔대기형 그림 빌드
description: 이 문서에서는 R 스크립트에서 R Power BI 시각적 개체에 대한 깔때기형 그림을 빌드하는 방법을 설명합니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: 2cc37d1296d7f170bf8c6280465e7a3f1aa52e33
ms.sourcegitcommit: 0d0ab427bb71b37c9e5170c515a8f274e1f20c17
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87878686"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>자습서:  R 스크립트에서 R 시각적 개체로 깔대기형 그림 빌드
이 문서에서는 R 시각적 개체에서 R 스크립트를 사용하여 깔때기형 그림을 빌드하는 방법을 단계별로 설명합니다.

이 문서에서는 다음을 만드는 방법을 설명합니다.

> [!div class="checklist"]
>
> * RStudio 용 R 스크립트
> * Power BI의 R 시각적 개체
> * Power BI의 ‘PNG 기반’ R 지원 시각적 개체
> * Power BI의 ‘HTML 기반’ R 지원 시각적 개체

깔때기형 그림은 예상되는 변형의 크기를 쉽게 이용하고 해석하고 표시하는 방법을 제공합니다. **깔때기**는 신뢰도 제한을 사용하여 구성되며 이상값은 깔때기 외부에 점으로 표시됩니다.

이 예제에서 깔때기형 그림은 다양한 집합 데이터를 비교하고 분석하는 데 사용됩니다.  

> [!NOTE]
> 원본 파일은 각 단계 세트에서 다운로드할 수 있습니다.

## <a name="build-an-r-script-with-dataset"></a>데이터 세트를 사용하여 R 스크립트 빌드

1. [최소 R 스크립트](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r) 및 해당 데이터 테이블 [dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv)를 다운로드합니다.

1. 그런 다음 [이 스크립트](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r)를 미러링하도록 스크립트를 편집합니다. 이렇게 하면 입력 오류 처리 및 사용자 매개 변수가 추가되어 그림의 모양을 제어할 수 있습니다.

## <a name="build-a-report"></a>보고서 작성

그런 다음 [이 스크립트](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r)를 미러링하도록 스크립트를 편집합니다. 이렇게 하면 Power BI Desktop 작업 영역으로 *read.csv* 대신 *dataset.csv*가 로드되고 **암 사망률** 표가 생성됩니다. 다음 [PBIX 파일](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix)의 결과를 확인합니다.

> [!NOTE]
> `dataset`는 R 시각적 개체의 입력 `data.frame`에 대한 하드 코드된 이름입니다. 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>R 코드에서 R 지원 시각적 개체 및 패키지 만들기

1. 시작하기 전에 [PBIVIZ 도구를 설치](./custom-visual-develop-tutorial.md#installing-packages)해야 합니다.

1. 다음 명령을 실행하여 새로운 R 지원 시각적 개체를 만듭니다.

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   이 명령은 초기 템플릿 시각적 개체(**template**`-t`)를 사용하여 *funnel-visual* 폴더를 만듭니다. PBIVIZ는 *dist* 폴더에 있으며, R 코드는 *script.r* 파일에 있습니다. Power BI로 가져와서 어떻게 되는지 확인하세요.

1. *script.r* 파일을 편집하고 콘텐츠를 이전 스크립트로 바꿉니다.

1. *capabilities.json*을 편집하고 `Values` 문자열을 `dataset`로 바꿉니다. 이렇게 하면 템플릿의 “역할”의 이름이 R 코드에서와같이 바뀝니다.

   ![이전 및 이후](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. (선택 사항) *dependencies.json*을 편집하고 R 스크립트에 필요한 각 R 패키지의 섹션을 추가합니다. 이렇게 하면 시각적 개체를 처음 로드할 때 이러한 패키지를 자동으로 가져오도록 Power BI에 지시합니다.

   ![이전 및 이후](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. `pbiviz package` 명령을 사용하여 시각적 개체를 다시 패키지한 후 Power BI로 가져옵니다.

> [!NOTE]
> [PBIX](https://github.com/microsoft/PowerBI-visuals/blob/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) 및 다운로드할 [소스 코드](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/)를 확인합니다.

## <a name="make-r-based-visual-improvements"></a>R 기반 시각적 기능 향상

사용자가 입력 테이블의 열 순서를 알아야 하므로 시각적 개체는 아직 사용자에게 친숙하지 않습니다.

1. 입력 필드 `dataset`를 `Population`, `Number`, `Tooltips` 등 3개의 필드(역할)로 나눕니다.

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. *capabilities.json*을 편집하고 `dataset` 역할을 세 가지 새로운 역할로 바꾸거나 [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json)을 다운로드합니다.

   각 입력 필드에 대한 이름, 형식, 도구 설명 및 최대 열 수를 정의하는 `dataRoles` 및 `dataViewMappings` 섹션을 업데이트해야 합니다.

   ![이전 및 이후](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   자세한 내용은 [기능](./capabilities.md)을 참조하세요.

1. `dataset` 대신 `Population`, `Number` 및 `Tooltips`를 입력 데이터 프레임으로 지원하기 위해 *script.r*을 편집하거나, [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r)을 다운로드합니다.

   ![스크립트](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > R 스크립트의 변경을 따르려면 주석 블록을 검색합니다. 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. `pbiviz package` 명령을 사용하여 시각적 개체를 다시 패키지한 후 Power BI로 가져옵니다.

> [!NOTE]
> [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) 및 다운로드할 [소스 코드](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02)를 확인합니다.

## <a name="add-user-parameters"></a>사용자 매개 변수 추가

1. 사용자가 UI의 내부 매개 변수를 포함하여 시각적 요소의 색과 크기를 제어할 수 있는 기능을 추가합니다.

   ![CV02to03](./media/funnel-plot/diagram-two.PNG)

1. *capabilities.json*을 편집하고 `objects` 섹션을 업데이트합니다. 여기서는 각 매개 변수의 이름, 도구 설명 및 유형을 정의하고 매개 변수 파티션을 그룹으로 결정합니다(이 경우 세 개의 그룹).

   [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json)을 다운로드하고, 자세한 내용은 [개체 속성](./objects-properties.md)을 참조하세요.

   ![capabilities](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. *src/settings.ts*가 [이 settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts)를 미러링하도록 편집합니다. 이 파일은 TypeScript로 작성됩니다.  

   여기에서 다음에 추가된 코드의 두 블록을 찾을 수 있습니다.
   - 속성 값을 보유할 새 인터페이스 선언
   - 멤버 속성 및 기본값 정의

   ![설정](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. *script.r*이 [이 script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r)을 미러링하도록 편집합니다. 그러면 사용자 매개 변수마다 `if.exists` 호출을 추가하여 UI의 매개 변수에 대한 지원이 추가됩니다.

   > [!TIP]
   > R 스크립트의 변경을 따르려면 주석을 검색합니다.
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![앞뒤의 스크립트](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   앞서 설명한 것처럼 UI에 매개 변수를 노출하지 않도록 결정할 수 있습니다.  

1. `pbiviz package` 명령을 사용하여 시각적 개체를 다시 패키지한 후 Power BI로 가져옵니다.

> [!NOTE]
> [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) 및 다운로드할 [소스 코드](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/)를 확인합니다.

> [!TIP]
> 여기서는 여러 매개 변수 형식(부울, 숫자, 문자열 및 색)을 한 번에 추가했습니다. 간단한 사례는 단일 매개 변수를 추가하는 방법에 대한 [이 예제](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md)를 참조하세요. 

## <a name="convert-visual-to-rhtml-based-visual"></a>시각적 개체를 RHTML 기반 시각적 개체로 변환

결과 시각적 개체는 PNG 기반이므로 마우스를 갖다 놓아도 반응하지 않고 확대할 수도 없으므로 HTML 기반 시각적 개체로 변환해야 합니다. 빈 R 지원 HTML 기반 시각적 개체 템플릿을 만든 다음 PNG 기반 프로젝트에서 일부 스크립트를 복사해 보겠습니다.

1. 명령 실행:

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. *capabilities.json*을 열고 `"scriptOutputType":"html"` 줄을 기록해 둡니다.

1. *dependencies.json*을 열고 나열된 R 패키지의 이름을 기록해 둡니다.

1. *script.r*을 열고 구조를 기록해 둡니다. 외부 입력을 사용하지 않으므로 RStudio에서 열고 실행할 수 있습니다. 

   이렇게 하면 *out.html*이 생성되고 저장됩니다. 이 파일은 외부 종속성 없이 자체 포함되어 있으며 HTML 위젯 내부에 그래픽을 정의합니다. 

   > [!IMPORTANT]
   > `htmlWidgets` 사용자의 경우, `plotly` 또는 `widget` 개체를 자체 콘텐츠 HTML로 변환하는 데 도움이 되는 R 유틸리티가 [r_files 폴더](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files)에 제공됩니다. 
   > 
   > 이 버전의 R 지원 시각적 개체는 코드를 더 읽기 쉽게 만들기 위해 `source` 명령(이전 형식의 시각적 개체와 달리)도 지원합니다.   
 
1. *capabilities.json*을 이전 단계의 *capabilities.json*으로 바꾸거나, [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json)을 다운로드합니다.

   다음을 유지해야 합니다.

   `"scriptOutputType": "html"`

1. 최신 버전의 *script.r*을 템플릿의 *script.r*과 병합하거나, [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r)을 다운로드합니다.

   새 스크립트는 `plotly` 패키지를 사용하여 **ggplot** 개체를 **plotly** 개체로 변환한 다음 `htmlWidgets` 패키지를 사용하여 HTML 파일에 저장합니다. 

   대부분의 유틸리티 함수는 [_r_files/utils.r_](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r)로 이동하고, **plotly** 개체의 모양에 대한 `generateNiceTooltips` 함수가 추가됩니다.

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > R 스크립트의 변경을 따르려면 주석을 검색합니다.
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. 최신 버전의 *dependencies.json*을 템플릿의 *dependencies.json*과 병합하여 새 R 패키지 종속성을 포함시키거나, [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json)을 다운로드합니다.

1. 이전 단계에서와 동일한 방식으로 *src/settings.ts*를 편집합니다.

1. `pbiviz package` 명령을 사용하여 시각적 개체를 다시 패키지한 후 Power BI로 가져옵니다.

> [!NOTE]
> [PBIX 및 다운로드할 소스 코드](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01)를 확인합니다.

## <a name="build-additional-examples"></a>추가 예제 빌드

1. 다음 명령을 실행하여 빈 프로젝트를 만듭니다. 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. 이 [쇼케이스](http://www.htmlwidgets.org/showcase_networkD3.html)에서 코드를 가져와 강조 표시된 대로 변경합니다.

   ![강조 표시된 변경 내용](./media/funnel-plot/diagram-three.PNG)

1. 템플릿의 *script.r*을 바꾸고 `pbiviz package`를 다시 실행합니다. 이제 시각적 개체가 Power BI 보고서에 포함됩니다!

## <a name="tips-and-tricks"></a>팁과 요령

* 개발자는 **버전**, **메일**, **이름**, **라이선스 형식** 등의 올바른 메타데이터를 저장하도록 *pbiviz.json*을 편집하는 것이 좋습니다.

   > [!IMPORTANT]
   > **guid** 필드는 시각적 개체에 대한 고유 식별자입니다. 각 시각적 개체에 대해 새 프로젝트를 만들면 GUID도 달라집니다. 새 시각적 개체로 복사된 이전 프로젝트를 사용하는 경우도 동일하므로 복사할 필요가 없습니다.

* [*assets/icon.png*](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png)를 편집하여 시각적 개체에 대한 고유 아이콘을 만듭니다. 

* Power BI 보고서에서와 동일한 데이터를 사용하여 RStudio에서 R 코드를 디버그하려면 R 스크립트의 시작 부분에 다음을 추가합니다(`fileRda` 변수 편집).

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   그러면 Power BI 보고서의 환경이 저장되고 RStudio에 로드됩니다. 

* [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R)에서 제공되는 코드를 사용하여 R 지원 시각적 개체를 처음부터 개발할 필요가 없습니다. 템플릿으로 사용할 시각적 개체를 선택하고 코드를 새 프로젝트에 복사할 수 있습니다.

   예를 들어 [스플라인 사용자 지정 시각적 개체](https://github.com/Microsoft/PowerBI-visuals-spline)를 사용해 보세요.

* 각 R 시각적 개체는 해당 입력 테이블에 `unique` 연산자를 적용합니다. 동일한 행이 제거되지 않도록 하려면 고유 ID를 사용하여 추가 입력 필드를 추가하고 R 코드에서는 무시하는 것이 좋습니다.   

* Power BI 계정이 있는 경우 `pbiviz package` 명령으로 다시 패키지하는 대신 Power BI 서비스를 사용하여 [즉석에서](/power-bi/developer/visuals/custom-visual-develop-tutorial/) 시각적 개체를 개발합니다.

### <a name="html-widgets-gallery"></a>HTML 위젯 갤러리
[HTML 위젯 갤러리](http://gallery.htmlwidgets.org/)에서 다음 시각적 개체에 사용할 시각적 개체를 찾아봅니다. 쉽게 작업할 수 있도록 선택 가능한 대화형 HTML 시각적 개체를 20개 이상 사용하여 [시각적 개체 프로젝트 리포지토리](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML)를 만들었습니다.

> [!TIP]
> HTML 위젯 간의 전환에는 **서식** > **설정** > **형식**을 사용합니다. [이 PBIX 파일](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix)을 사용해 보세요. 

#### <a name="to-use-a-sample-for-your-visual"></a>시각적 개체에 샘플을 사용하려면

1. 전체 폴더를 다운로드합니다.
1. 하나의 위젯만 유지하도록 *script.r* 및 *dependencies.json*을 편집합니다.
1. *capabilities.json* 및 *settings.ts*를 편집하여 `Type` 선택기를 제거합니다.
1. *visual.ts*에서 `const updateHTMLHead: boolean = true;`를 `false`로 변경합니다. (성능 향상을 위해)
1. *pbiviz.json*에서 메타데이터를 변경합니다(`guid` 필드가 가장 중요).
1. 필요에 따라 시각적 개체를 다시 패키지하고 계속 사용자 지정합니다. 

![CV02to03](./media/funnel-plot/diagram-four.PNG)

![CV02to03](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> 이 프로젝트의 모든 위젯이 서비스에서 지원되지는 않습니다.

## <a name="next-steps"></a>다음 단계

자세한 내용은 [Power BI 시각적 개체](./custom-visual-develop-tutorial.md) 및 [R 시각적 개체](/power-bi/visuals/service-r-visuals)에 대한 추가 자습서를 확인하세요.

[시각적 개체를 개발하여](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/) [Office Store(갤러리)](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI)에 제출하는 방법을 알아보고, 추가 예제는 [R 스크립트 쇼케이스](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals)를 참조하세요.
