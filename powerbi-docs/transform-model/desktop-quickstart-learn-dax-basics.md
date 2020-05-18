---
title: Power BI Desktop의 DAX 기본 사항
description: Power BI Desktop의 DAX 기본 사항
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 9ff04510a786fa89e1e461e6eefee1af90e58a8e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83313388"
---
# <a name="apply-dax-basics-in-power-bi-desktop"></a>Power BI Desktop의 DAX 기본 사항 적용
이 문서는 Power BI Desktop을 처음 사용하는 사용자를 위한 것입니다. DAX(Data Analysis Expressions)를 사용하여 여러 가지 기본 계산 및 데이터 분석 문제를 해결하는 방법을 쉽고 빠르게 소개합니다. 또한 일부 개념 정보, 수행할 수 있는 일련의 작업, 배운 내용을 테스트하는 지식 점검을 살펴보겠습니다. 이 문서를 완료하면 DAX의 가장 중요한 기본 개념을 제대로 이해하고 있어야 합니다.

## <a name="what-is-dax"></a>DAX란 무엇인가요?
DAX란 수식 또는 식에서 하나 이상의 값을 계산하고 반환하는 데 사용할 수 있는 함수, 연산자 및 상수 컬렉션입니다. 간단히 말해서, DAX를 사용하면 이미 모델에 있는 데이터로 새로운 정보를 만들 수 있습니다.

## <a name="why-is-dax-so-important"></a>DAX는 왜 중요한가요?
새로운 Power BI Desktop 파일을 만들고 일부 데이터를 파일로 가져오는 작업은 간단합니다. DAX 수식을 사용하지 않고도 중요한 정보를 보여 주는 보고서를 만들 수 있습니다. 그러나 제품 범주 전체 및 다양한 날짜 범위에 대해 증가 비율을 분석해야 하는 경우는 어떻게 될까요? 또는 시장 추세와 비교하여 전년동기대비 성장을 계산해야 하는 경우는 어떻게 되나요? DAX 수식은 이러한 기능과 여러 가지 다른 중요한 기능도 제공합니다. 효과적인 DAX 수식을 만드는 방법을 학습하면 데이터를 최대한 활용하는 데 도움이 됩니다. 필요한 정보를 얻으면 총결산에 영향을 주는 실제 비즈니스 문제를 해결할 수 있습니다. 이는 Power BI의 강력한 기능이며, DAX는 이러한 기능에 도움이 됩니다.

## <a name="prerequisites"></a>필수 조건
Microsoft Excel에서 수식을 만드는 방법을 이미 잘 알고 있을 수 있습니다. 이 지식은 DAX를 이해하는 데 도움이 되지만 Excel 수식에 대해 잘 모르는 경우에도 여기에 설명된 개념을 사용하면 DAX 수식을 만들고 실제 BI 문제 해결을 바로 시작할 수 있습니다.

여기서는 계산, 특히 측정값 및 계산 열에서 사용된 DAX 수식을 이해하는 방법을 중심으로 설명합니다. Power BI Desktop을 사용하여 데이터를 가져오고 보고서에 필드를 추가하는 방법은 물론 [측정값](desktop-measures.md) 및 [계산 열](desktop-calculated-columns.md)의 기본 개념을 잘 알고 있어야 합니다.

### <a name="example-workbook"></a>예제 통합 문서

DAX를 학습하는 가장 좋은 방법은 몇 가지 기본 수식을 만들어 실제 데이터에 사용하고 그 결과를 직접 확인하는 것입니다. 이 문서의 예제 및 작업에서는 [Contoso Sales Sample for Power BI Desktop 파일](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip)을 사용합니다. 이 샘플 파일은 [자습서: Power BI Desktop에서 고유한 측정값 만들기](desktop-tutorial-create-measures.md) 문서에 사용된 것과 동일한 샘플 파일입니다. 

## <a name="lets-begin"></a>시작하기
여기서는 다음과 같은 세 가지 기본 개념을 중심으로 DAX를 살펴봅니다. ‘구문’, ‘함수’ 및 ‘컨텍스트’.    DAX에는 다른 중요한 개념도 있지만 이러한 세 가지 개념을 이해하면 DAX 기술을 구축할 최상의 토대가 제공됩니다.

### <a name="syntax"></a>구문
수식을 직접 만들기 전에 DAX 수식 구문에 대해 살펴보겠습니다. 구문에는 수식을 구성하는 요소, 보다 간단히 수식이 작성되는 방법이 포함됩니다. 예를 들어 다음은 측정값에 대한 간단한 DAX 수식입니다.

![DAX 수식 구문](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

이 수식에는 다음과 같은 구문 요소가 있습니다.

**A.** 측정값 이름, **Total Sales**

**B.** 등호 연산자( **=** ) - 수식의 시작을 나타냅니다. 계산되면 결과를 반환합니다.

**C.** DAX 함수 **SUM** - **Sales[SalesAmount]** 열에 있는 모든 숫자를 더합니다. 함수에 대해서는 나중에 자세히 살펴보겠습니다.

**D.** 괄호 **()** - 하나 이상의 인수를 포함하는 식을 둘러쌉니다. 모든 함수에는 하나 이상의 인수가 필요합니다. 인수는 함수에 값을 전달합니다.

**E.** 참조되는 테이블, **Sales**

**F.** Sales 테이블에서 참조되는 열, **[SalesAmount]** . 이 인수를 사용하여 SUM 함수는 SUM을 집계할 열을 파악합니다.

DAX 수식을 이해하려는 경우, 매일 생각하고 말하는 언어로 각 요소를 분석하면 도움이 되는 경우가 많습니다. 예를 들어 이 수식을 다음과 같이 읽을 수 있습니다.

> *Total Sales라는 측정값의 경우 Sales 테이블의 [SalesAmount] 열에 있는 값의 SUM을 계산(=)합니다.*
> 
> 

보고서에 추가되면 이 측정값은 포함된 각각의 다른 필드(예: 미국의 휴대폰)에 대한 판매 금액을 합계하여 값을 계산하고 반환합니다.

“이 측정값은 보고서에 SalesAmount 필드를 추가하는 것과 같은 동작을 수행하는 것이 아닐까?”라고 생각할 수 있습니다. 네, 그렇습니다. 그러나 SalesAmount 필드 값의 합계를 구하는 측정값을 직접 만드는 적절한 이유가 있습니다. 바로 다른 수식에서 인수로 사용할 수 있기 때문입니다. 지금은 약간 혼란스러울 수 있지만, DAX 수식에 대한 기술이 증가함에 따라 이 측정값을 알고 있으면 수식 및 모델을 보다 효율적으로 만들 수 있습니다. 실제로 나중에 다른 수식에서 인수로 표시되는 총 판매액 측정값을 확인할 수 있습니다.

이 수식에 대해 몇 가지 더 살펴보겠습니다. 특히 [SUM](https://msdn.microsoft.com/library/ee634387.aspx) 함수를 사용했습니다. 함수는 복잡한 계산 및 숫자, 날짜, 시간, 텍스트 등을 사용한 조작을 더 쉽게 수행할 수 있도록 미리 작성된 수식입니다. 함수에 대해서는 나중에 자세히 살펴보겠습니다.

또한 열 이름 [SalesAmount]가 해당 열이 속하는 Sales 테이블 뒤에 오는 것을 확인할 수 있습니다. 이 이름은 테이블 이름 뒤에 열 이름을 포함한다는 점에서 정규화된 열 이름이라고 합니다. 동일한 테이블에서 참조되는 열은 수식에 테이블 이름을 포함할 필요가 없으므로 많은 열을 참조하는 긴 수식을 더 짧고 읽기 쉽게 만들 수 있습니다. 그러나 동일한 테이블에 있더라도 측정값 수식에는 테이블 이름을 포함하는 것이 좋습니다.

> [!NOTE]
> 테이블 이름에 공백, 예약된 키워드 또는 허용되지 않는 문자가 포함된 경우 테이블 이름을 작은따옴표로 묶어야 합니다. 또한 테이블 이름에 ANSI 영숫자 문자 범위를 벗어나는 문자가 포함된 경우에는 로캘에서 해당 문자 집합을 지원하는지 여부와 관계없이 해당 이름을 따옴표로 묶어야 합니다.
> 
> 

수식은 올바른 구문을 사용해야 합니다. 대부분의 경우 구문이 올바르지 않으면 구문 오류가 반환됩니다. 구문은 올바르지만 반환된 값이 예상과 다른 경우도 있습니다. Power BI Desktop의 DAX 편집기에는 올바른 요소를 선택하여 구문상 올바른 수식을 만드는 데 사용되는 추천 기능이 포함됩니다.

간단한 수식을 만들어 보겠습니다. 이 작업을 통해 수식 구문 및 수식 입력줄에서 추천 기능이 어떻게 도움이 되는지를 더 잘 이해할 수 있습니다.

### <a name="task-create-a-measure-formula"></a>작업: 측정값 수식 만들기

1. Contoso Sales Sample Power BI Desktop 파일을 [다운로드](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip)하고 엽니다. 
    
2. 보고서 보기의 필드 목록에서 **Sales** 테이블을 마우스 오른쪽 단추로 클릭하고 **새 측정값**을 선택합니다.
    
3. 수식 입력줄에 새 측정값 이름 *Previous Quarter Sales*를 입력하여 **측정값**을 바꿉니다.
    
4. 등호 다음에 처음 몇 개의 문자 *CAL*을 입력한 다음, 사용할 함수를 두 번 클릭합니다. 이 수식에서는 **CALCULATE** 함수를 사용하려고 합니다.

   CALCULATE 함수를 사용하여 CALCULATE 함수에 전달되는 인수로 합계를 계산할 금액을 필터링합니다. 이런 함수를 중첩 함수라고 합니다. CALCULATE 함수에는 둘 이상의 인수가 있습니다. 첫 번째는 계산할 식이고 두 번째는 필터입니다.
   
5. **CALCULATE** 함수의 여는 괄호 *(* 다음에 *SUM*과 다른 여는 괄호 *(* 를 차례로 입력합니다. 

   이제 SUM 함수에 인수를 전달하겠습니다.

6. *Sal* 입력을 시작한 다음 **Sales[SalesAmount]** , 닫는 괄호 *)* 를 차례로 선택합니다. 

   CALCULATE 함수에 대한 첫 번째 식 인수입니다.
    
7. 쉼표( *,* ), 공백을 차례로 입력하여 첫 번째 필터를 지정하고 *PREVIOUSQUARTER*를 입력합니다. 
    
   PREVIOUSQUARTER 시간 인텔리전스 함수를 사용하여 이전 분기별로 SUM 결과를 필터링합니다.
    
8. PREVIOUSQUARTER 함수의 여는 괄호 *(* 다음에 *Calendar[DateKey]* 를 입력합니다.
    
   PREVIOUSQUARTER 함수에는 인접한 날짜 범위를 포함하는 열인 인수 하나가 있습니다. 예제에서는 Calendar 테이블의 DateKey 열입니다.
    
9. 두 개의 닫는 괄호 *))* 를 입력하여 PREVIOUSQUARTER 함수와 CALCULATE 함수에 전달되는 인수를 모두 닫습니다.
    
   이제 수식이 다음과 같이 표시됩니다.
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
10. 수식 입력줄에서 확인 표시 ![확인 표시 아이콘](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) 를 선택하거나 Enter 키를 눌러 수식의 유효성을 검사하고 모델에 추가합니다.

이제 완료되었습니다. DAX를 사용하여 복잡한 측정값을 만들었습니다. 이 수식은 보고서에서 적용된 필터에 따라 이전 분기에 대한 총 판매액을 계산합니다. 예를 들어 차트에 SalesAmount와 새로운 Previous Quarter Sales 측정값을 배치한 다음, Year 및 QuarterOfYear를 슬라이서로 추가하면 다음과 같이 표시됩니다.

![Previous Quarter Sales 및 SalesAmount 차트](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

방금 DAX 수식의 몇 가지 중요한 측면이 소개되었습니다. 

- 이 수식에는 두 개의 함수가 포함되어 있습니다. [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx) 시간 인텔리전스 함수가 [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx) 필터 함수에 전달되는 인수로 중첩되었습니다. 

   DAX 수식에는 중첩 함수가 최대 64개까지 포함될 수 있습니다. 그러나 수식에 이렇게 많은 중첩 함수가 포함될 가능성은 없습니다. 실제로 이러한 수식은 만들고 디버그하기가 어려우며 속도가 빠르지도 않을 것입니다.

- 이 수식에서는 필터도 사용했습니다. 필터는 계산될 범위를 좁힙니다. 이 경우 실제로 다른 함수의 결과인 필터 한 개를 인수로 선택했습니다. 필터에 대해서는 나중에 자세히 살펴보겠습니다.

- CALCULATE 함수를 사용했습니다. 이 함수는 DAX에서 가장 강력한 함수 중 하나입니다. 모델을 작성하고 더 복잡한 수식을 만들 때 이 함수를 여러 번 사용할 가능성이 큽니다. CALCULATE 함수에 대한 자세한 설명은 이 문서의 범위를 벗어나지만, DAX에 대한 지식이 많아지면 이 함수에 특별히 주의해야 합니다.

### <a name="syntax-quickquiz"></a>구문 QuickQuiz
1. 수식 입력줄에서 이 단추의 기능은 무엇인가요?
   
   > ![단추 선택](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. DAX 수식에서 항상 열 이름을 둘러싸는 것은 무엇인가요?

답변은 이 문서의 끝에서 제공됩니다.

### <a name="functions"></a>함수
함수는 특정 순서 또는 구조에서 인수라는 특정 값을 사용하여 계산을 수행하는 미리 정의된 수식입니다. 인수는 다른 함수, 다른 수식, 식, 열 참조, 숫자, 텍스트, TRUE/FALSE 같은 논리 값 또는 상수일 수 있습니다.

DAX에는 다음과 같은 범주의 함수가 포함됩니다. [날짜 및 시간](https://msdn.microsoft.com/library/ee634786.aspx), [시간 인텔리전스](https://msdn.microsoft.com/library/ee634763.aspx), [정보](https://msdn.microsoft.com/library/ee634552.aspx), [논리](https://msdn.microsoft.com/library/ee634365.aspx), [수학](https://msdn.microsoft.com/library/ee634241.aspx), [통계](https://msdn.microsoft.com/library/ee634822.aspx), [텍스트](https://msdn.microsoft.com/library/ee634938.aspx), [상위/하위](https://msdn.microsoft.com/library/mt150102.aspx) 및 [기타](https://msdn.microsoft.com/library/mt150101.aspx) 함수. Excel 수식의 함수에 익숙한 경우 DAX의 많은 함수가 유사하게 보이지만 DAX 함수는 다음과 같은 측면에서 고유합니다.

* DAX 함수는 항상 전체 열 또는 테이블을 참조합니다. 테이블 또는 열에서 특정 값만 사용하려는 경우 수식에 필터를 추가할 수 있습니다.
* 행 단위로 계산을 사용자 지정해야 하는 경우 DAX는 현재 행 값이나 관련 값을 일종의 인수로 사용할 수 있는 함수를 제공하여 컨텍스트에 따라 다른 계산을 수행합니다. 컨텍스트에 대해서는 나중에 자세히 살펴보겠습니다.
* DAX에는 값이 아닌 테이블을 반환하는 함수가 많이 포함되어 있습니다. 테이블은 표시되지 않고 다른 함수에 입력을 제공하는 데 사용됩니다. 예를 들어 테이블을 검색한 다음 테이블에 포함된 고유 값을 계산하거나 필터링된 테이블 또는 열 전체에서 동적 합계를 계산할 수 있습니다.
* DAX에는 다양한 시간 인텔리전스 함수가 포함되어 있습니다. 이러한 함수를 사용하여 날짜 범위를 정의하거나 선택하고 그에 따라 동적 계산을 수행할 수 있습니다. 예를 들어 병렬 기간 전체의 합계를 비교할 수 있습니다.
* Excel에는 많이 사용되는 VLOOKUP 함수가 있습니다. DAX 함수는 Excel의 VLOOKUP처럼 셀 또는 셀 범위를 참조로 사용하지 않습니다. DAX 함수는 열 또는 테이블을 참조로 사용합니다. Power BI Desktop에서는 관계형 데이터 모델을 사용한다는 점에 유의해야 합니다. 다른 테이블의 값을 쉽게 조회할 수 있으며, 대부분의 경우 수식을 만들 필요가 없습니다.
  
  보시는 것처럼 DAX의 함수를 사용하면 강력한 수식을 만들 수 있습니다. 실제로 여기서는 함수의 기본 사항만 다루었습니다. DAX에 대한 기술이 증가함에 따라 다양한 함수를 사용하여 수식을 만들 수 있습니다. 각 DAX 함수에 대한 자세한 내용은 [DAX 함수 참조](https://msdn.microsoft.com/query-bi/dax/data-analysis-expressions-dax-reference)를 참조하세요.

### <a name="functions-quickquiz"></a>함수 QuickQuiz
1. 함수는 항상 무엇을 참조하나요?
2. 수식에 둘 이상의 함수가 포함될 수 있나요?
3. 두 개의 텍스트 문자열을 하나의 문자열로 연결하려면 어떤 범주의 함수를 사용해야 할까요?

답변은 이 문서의 끝에서 제공됩니다.

### <a name="context"></a>컨텍스트
컨텍스트는 이해해야 할 가장 중요한 DAX 개념 중 하나입니다. DAX에는 행 컨텍스트와 필터 컨텍스트라는 두 가지 유형의 컨텍스트가 있습니다. 먼저 행 컨텍스트를 살펴보겠습니다.

**행 컨텍스트**

행 컨텍스트는 가장 쉽게 현재 행이라고 생각하면 됩니다. 이 컨텍스트는 테이블에서 단일 행을 식별하는 필터를 적용하는 함수가 수식에 있을 때마다 적용됩니다. 함수는 필터링하는 테이블의 각 행에 대해 기본적으로 행 컨텍스트를 적용합니다. 이 유형의 행 컨텍스트는 가장 자주 측정값에 적용됩니다.

**필터 컨텍스트**

필터 컨텍스트는 행 컨텍스트보다 이해하기가 약간 더 어렵습니다. 가장 쉽게 이해하려면 필터 컨텍스트는 결과 또는 값을 결정하는 계산에 적용된 하나 이상의 필터라고 생각하면 됩니다.

필터 컨텍스트는 행 컨텍스트를 대체하는 것이 아니라 행 컨텍스트에 추가로 적용됩니다. 예를 들어 계산에 포함할 값의 범위를 더욱 좁히기 위해 행 컨텍스트뿐만 아니라 행 컨텍스트의 특정 값(필터)도 지정하는 필터 컨텍스트를 적용할 수 있습니다.

필터 컨텍스트는 보고서에서 쉽게 볼 수 있습니다. 예를 들어 TotalCost를 시각화에 추가한 다음 Year 및 Region을 추가하면 지정된 연도 및 지역을 기반으로 하는 데이터의 하위 집합을 선택하는 필터 컨텍스트가 정의됩니다.

필터 컨텍스트가 DAX에서 매우 중요한 이유는 무엇인가요? 필터 컨텍스트는 시각화에 필드를 추가하여 가장 쉽게 적용할 수 있지만 DAX 수식에서 모든, 관련, 필터, 계산과 같은 함수를 사용하는 필터를 기타 측정값 및 열별로 정의하여 적용할 수도 있기 때문입니다. 예를 들어 Store Sales라는 측정값에서 다음 수식을 살펴보겠습니다.

![Store Sales 측정값](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

이 수식을 더 잘 이해하기 위해 다른 수식과 마찬가지로 자세히 분석할 수 있습니다.

이 수식에는 다음과 같은 구문 요소가 있습니다.

**A.** 측정값 이름, **Store Sales**

**B.** 등호 연산자( **=** ) - 수식의 시작을 나타냅니다.

**C.** **CALCULATE** 함수 - 지정한 필터로 수정된 컨텍스트에서 식을 인수로 계산합니다.

**D.** 괄호 **()** - 하나 이상의 인수를 포함하는 식을 둘러쌉니다.

**E.** 식과 동일한 테이블에 있는 측정값 **[Total Sales]** . Total Sales 측정값에는 =SUM(Sales[SalesAmount]) 수식이 있습니다.

**F.** 쉼표( **,** ) - 첫 번째 식 인수를 필터 인수와 구분합니다.

**G.** 정규화된 참조되는 열 **Channel[ChannelName]** . 바로 행 컨텍스트입니다. 이 열의 각 행은 Store, Online 등의 채널을 지정합니다.

**H.** 필터로 사용되는 특정 값, **Store**. 바로 필터 컨텍스트입니다.

이 수식은 *Store* 값을 필터로 사용하여, Channel[ChannelName] 열의 행에 대해서만 Total Sales 측정값에 정의된 매출 값을 계산합니다.

상상할 수 있듯이 수식 내에서 필터 컨텍스트를 정의할 수 있는 기능은 엄청나고 강력한 기능입니다. 관련 테이블에서 특정 값만 참조할 수 있는 기능은 이러한 예 중 하나일 뿐입니다. 컨텍스트에 대해 완벽하게 이해하지 못해도 됩니다. 수식을 직접 만들어 보면 컨텍스트와 DAX에서 컨텍스트가 매우 중요한 이유를 더 잘 이해할 수 있습니다.

### <a name="context-quickquiz"></a>컨텍스트 QuickQuiz
1. 컨텍스트의 두 가지 유형은 무엇인가요?
2. 필터 컨텍스트란 무엇인가요?
3. 행 컨텍스트란 무엇인가요?

답변은 이 문서의 끝에서 제공됩니다.

## <a name="summary"></a>요약
DAX에서 가장 중요한 개념에 대한 기본적인 내용을 이해했으므로 이제 측정값에 대한 DAX 수식을 직접 만들 수 있습니다. 실제로 DAX는 배우기가 약간 까다로울 수 있지만 사용 가능한 많은 리소스를 제공합니다. 이 문서 전체를 읽고 몇 가지 수식을 직접 시험해 보면 고유한 비즈니스 문제를 해결하는 데 도움이 되는 기타 DAX 개념 및 수식에 대해 더 자세히 이해할 수 있습니다. 많은 DAX 리소스를 사용할 수 있지만 [DAX(Data Analysis Expressions) 참조](https://msdn.microsoft.com/library/gg413422.aspx)가 가장 중요합니다.

DAX는 파워 피벗, Analysis Services 테이블 형식 모델 등의 다른 Microsoft BI 도구에서 여러 해 동안 사용되었으므로 유용한 정보가 많습니다. 자세한 내용은 Microsoft 및 업계 최고 BI 전문가들이 제공하는 설명서, 백서 및 블로그에서 확인할 수 있습니다. [TechNet의 DAX 리소스 센터 Wiki](https://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx)도 시작하는 데 많은 도움이 될 수 있습니다.

### <a name="quickquiz-answers"></a>빠른 퀴즈 답변
구문:

1. 유효성을 검사하고 모델에 측정값을 입력합니다.
2. 대괄호([])

함수:

1. 테이블 및 열
2. 예. 수식에는 중첩된 함수가 최대 64개까지 포함될 수 있습니다.
3. [텍스트 함수](https://msdn.microsoft.com/library/ee634938.aspx).

컨텍스트:

1. 행 컨텍스트 및 필터 컨텍스트
2. 단일 값을 결정하는 계산에서 사용되는 하나 이상의 필터
3. 현재 행
