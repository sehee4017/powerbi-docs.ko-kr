---
title: Power BI 보고서 작성기의 식 예제
description: 식은 Power BI 보고서 작성기의 페이지를 매긴 보고서에 자주 사용되어 보고서의 내용과 모양을 제어합니다.
author: maggiesMSFT
ms.author: maggies
ms.date: 11/08/2020
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
ms.openlocfilehash: a919efad0b9656327a766986456c533242d40c2e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416327"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Power BI 보고서 작성기의 식 예제

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

식은 Power BI 보고서 작성기의 페이지를 매긴 보고서에 자주 사용되어 보고서의 내용과 모양을 제어합니다. 식은 Microsoft Visual Basic으로 작성되며, 기본 제공 함수, 사용자 지정 코드, 보고서와 그룹 변수 및 사용자 정의 변수를 사용할 수 있습니다. 식은 등호(=)로 시작됩니다.   

이 항목에서는 보고서의 일반적인 태스크에 사용할 수 있는 식 예를 제공합니다.  
  
-   [Visual Basic 함수](#VisualBasicFunctions) 날짜, 문자열, 변환 및 조건부 Visual Basic 함수의 예제입니다.  
  
-   [보고서 함수](#ReportFunctions) 집계 및 기타 기본 제공 보고서 함수 예  
  
-   [보고서 데이터 모양](#AppearanceofReportData) 보고서 모양 변경 예  
  
-   [속성](#Properties) 형식 또는 표시 유형을 제어하는 보고서 항목 속성 설정 예  
  
-   [매개 변수](#Parameters) 식에서의 매개 변수 사용 예  
  
-   [사용자 지정 코드](#CustomCode) 포함된 사용자 지정 코드 예  
  
식을 사용할 수 있는 단순 및 복합 식의 기본 사항 식을 사용할 수 있는 위치 및 식에 포함할 수 있는 참조 형식에 대한 자세한 내용은 [Power BI 보고서 작성기의 식](report-builder-expressions.md) 아래의 항목을 참조하세요. 
  
## <a name="functions"></a>Functions  
 보고서의 여러 식에는 함수가 포함됩니다. 이러한 함수를 사용하여 데이터의 형식을 지정하고, 논리를 적용하고, 보고서 메타데이터에 액세스할 수 있습니다. Microsoft Visual Basic 런타임 라이브러리, `xref:System.Convert` 및 `xref:System.Math` 네임스페이스에서 함수를 사용하는 식을 작성할 수 있습니다. 사용자 지정 코드에서 함수에 대한 참조를 추가할 수 있습니다. `xref:System.Text.RegularExpressions`를 포함하여 Microsoft .NET Framework의 클래스를 사용할 수도 있습니다.  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Visual Basic 함수  
 Visual Basic 함수를 사용하여 텍스트 상자에 표시되거나 보고서의 매개 변수, 속성 또는 다른 영역에 사용되는 데이터를 조작할 수 있습니다. 이 섹션에서는 이러한 함수 중 몇 가지를 보여 주는 예를 제공합니다. 자세한 내용은 MSDN의 [Visual Basic 런타임 라이브러리 멤버](/dotnet/visual-basic/language-reference/runtime-library-members) 를 참조하세요.  
  
 .NET Framework는 특정 날짜 형식과 같은 다양한 사용자 지정 형식 옵션을 제공합니다. 자세한 내용은 [서식 지정 형식](/dotnet/standard/base-types/formatting-types)을 참조하세요.  
  
### <a name="math-functions"></a>수치 연산 함수  
  
-   **Round** 함수는 숫자를 가장 가까운 정수로 반올림하거나 내림하려는 경우 유용합니다. 다음 식에서는 1.3을 1로 반내림합니다.  
  
    ```  
    = Round(1.3)  
    ```  
  
     Excel의 **MRound** 함수와 같이 지정한 배수로 값을 반올림하거나 내림하는 식을 작성할 수도 있습니다. 정수를 만드는 계수로 값을 곱해 숫자를 반올림하거나 내림한 다음 동일한 계수로 나눕니다. 예를 들어 1.3을 .2의 배수 중 가장 가까운 배수인 1.4로 반올림하려면 다음 식을 사용합니다.  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> 날짜 함수  
  
-   **Today** 함수는 현재 날짜를 제공합니다. 이 식은 보고서에 날짜를 표시할 경우 입력란에 사용하거나 현재 날짜를 기반으로 데이터를 필터링할 경우 매개 변수에 사용할 수 있습니다.  
  
    ```  
    =Today()  
    ```  
  
-   **DateInterval** 함수를 사용하여 날짜의 특정 부분을 추출합니다. 몇 가지 유효한 **DateInterval** 매개 변수는 다음과 같습니다.

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    예를 들어 이 식은 현재 날짜에 대한 현재 연도의 주 수를 표시합니다.
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   **DateAdd** 함수는 단일 매개 변수를 기반으로 날짜 범위를 제공하는 데 유용합니다. 다음 식에서는 *StartDate* 라는 매개 변수로부터 6개월 후의 날짜를 제공합니다.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   **Year** 함수는 특정 날짜의 연도를 표시합니다. 이 함수를 사용하여 날짜를 그룹화하거나 연도를 일련의 날짜 레이블로 표시할 수 있습니다. 이 식은 지정된 판매 주문 날짜 그룹에 대한 연도를 제공합니다. 날짜 처리에 **Month** 함수 및 다른 함수를 사용할 수 있습니다. 자세한 내용은 Visual Basic 설명서를 참조하세요.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   식에서 함수를 결합하여 형식을 사용자 지정할 수 있습니다. 다음 식에서는 월-일-연도 형식의 날짜를 월-주-주 번호 형식의 날짜로 변경합니다. 예를 들어 12/23/2009를 12월 주 3으로 변경합니다.  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     이 식을 데이터 세트에서 계산 필드로 사용할 경우 차트에서 이 식을 사용하면 각 달의 주를 기준으로 값을 집계할 수 있습니다.  
  
-   다음 식은 SellStartDate 값을 MMM-YY 형식으로 지정합니다. SellStartDate 필드는 datetime 데이터 형식입니다.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   다음 식은 SellStartDate 값을 dd/MM/yyyy 형식으로 지정합니다. SellStartDate 필드는 datetime 데이터 형식입니다.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   **CDate** 함수는 값을 날짜로 변환합니다. **Now** 함수는 현재 날짜와 시스템에 따른 시간을 포함하는 날짜 값을 반환합니다. **DateDiff** 는 두 날짜 값 사이의 시간 간격을 지정하는 Long 값을 반환합니다.  
  
     다음 예제는 현재 연도의 시작 날짜를 표시합니다.  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   다음 예제는 현재 달을 기준으로 이전 달의 시작 날짜를 표시합니다.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   다음 식은 SellStartDate와 LastReceiptDate 사이의 간격 연도를 생성합니다. 이러한 필드는 두 가지 다른 데이터 세트 즉, DataSet1 및 DataSet2에 있습니다.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   **DatePart** 함수는 주어진 날짜 값의 지정된 구성 요소를 포함하는 정수 값을 반환합니다. 다음 식은 DataSet1에 있는 SellStartDate의 첫 번째 값에 대한 연도를 반환합니다. 보고서에 여러 개의 데이터 세트가 있으므로 데이터 세트 범위가 지정됩니다.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   **DateSerial** 함수는 자정으로 설정된 시간 정보와 함께 지정된 년, 월, 일을 나타내는 날짜 값을 반환합니다. 다음 예제는 현재 달을 기준으로 이전 달의 마지막 날짜를 표시합니다.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   다음 식은 사용자가 선택한 날짜 매개 변수 값을 기준으로 여러 날짜를 표시합니다.  
  
|예제 설명|예제|  
|-------------------------|-------------|  
|어제|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|2일 전|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|1개월 전|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|2개월 전|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|1년 전|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|2년 전|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> 문자열 함수  
  
-   연결 연산자와 Visual Basic 상수를 사용하여 둘 이상의 필드를 결합합니다. 다음 식에서는 두 필드를 같은 입력란에서 별도의 줄에 반환합니다.  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   **Format** 함수를 사용하여 문자열의 날짜와 숫자 형식을 지정합니다. 다음 식에서는 *StartDate* 와 *EndDate* 매개 변수의 값을 자세한 날짜 형식으로 표시합니다.  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     입력란에 날짜 또는 숫자만 있는 경우 입력란 내에서 **Format** 함수 대신 서식을 적용하려면 입력란의 Format 속성을 사용해야 합니다.  
  
-   **Right**, **Len** 및 **InStr** 함수는 하위 문자열을 반환하는 데 유용합니다. 예를 들어 *DOMAIN*\\*username* 에서 사용자 이름만 잘라서 반환할 수 있습니다. 다음 식에서는\\User *라는 매개 변수에서 백슬래시(* ) 문자의 오른쪽에 있는 문자열 부분을 반환합니다.  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     다음 식은 Visual Basic 함수 대신 `xref:System.String` .NET Framework 클래스의 멤버를 사용하여 이전 식과 동일한 값을 생성합니다.  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   다중값 매개 변수에서 선택한 값을 표시합니다. 다음 예에서는 **Join** 함수를 사용하여 *MySelection* 매개 변수의 선택한 값을 보고서 항목에 있는 입력란의 값에 대해 식으로 설정할 수 있는 단일 문자열에 연결합니다.  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     다음 예에서는 선택한 값 목록 이전의 텍스트 문자열을 표시할 뿐 아니라 위의 예와 동일한 작업을 수행합니다.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   .NET Framework `xref:System.Text.RegularExpressions`의 **Regex** 함수는 기존 문자열의 형식(예: 전화 번호 형식 지정)을 변경하는 데 유용합니다. 다음 식에서는 **Replace** 함수를 사용하여 필드의 10자리 전화 번호 서식을 "*nnn*-*nnn*-*nnnn*"에서 "(*nnn*) *nnn*-*nnnn*"으로 변경합니다.  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Fields!Phone.Value의 값에 추가 공백이 없고 `xref:System.String`를 참조하세요.  
  
### <a name="lookup"></a>조회  
  
-   키 필드를 지정하면 **Lookup** 함수를 사용하여 키-값 쌍과 같이 일 대 일 관계가 있는 데이터 세트에서 값을 검색할 수 있습니다. 일치시킬 제품 식별자가 제공된 경우 다음 식은 데이터 세트에서 제품 이름("Product")을 표시합니다.  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   키 필드를 지정하면 **LookupSet** 함수를 사용하여 일 대 다 관계가 있는 데이터 세트에서 값 집합을 검색할 수 있습니다. 예를 들어 한 사람이 전화 번호를 여러 개 가질 수 있습니다. 다음 예에서는 PhoneList 데이터 세트의 각 행에 개인 식별자와 전화 번호가 포함되어 있다고 가정합니다. **LookupSet** 은 값 배열을 반환합니다. 다음 식은 반환 값을 단일 문자열로 결합하고 ContactID로 지정된 사람의 전화 번호 목록을 표시합니다.  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> 변환 함수  
 Visual Basic 함수를 사용하여 필드를 한 데이터 형식에서 다른 데이터 형식으로 변환할 수 있습니다. 필드의 기본 데이터 형식을 계산이나 텍스트 결합에 필요한 다른 데이터 형식으로 변환하는 데에 변환 함수를 사용할 수 있습니다.  
  
-   다음 식은 500의 상수를 10진수 형식으로 변환하여 필터 식의 Value 필드에 있는 Transact-SQL money 데이터 형식과 비교합니다.  
  
    ```  
    =CDec(500)  
    ```  
  
-   다음 식에서는 다중값 매개 변수 *MySelection* 에 대해 선택된 값의 수를 표시합니다.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> 의사 결정 함수  
  
-   **Iif** 함수는 식이 True인지 여부에 따라 두 값 중 하나를 반환합니다. 다음 식에서는 **Iif** 함수를 사용하여 **의 값이 100을 초과하면 부울 값** True `LineTotal` 를 반환하고, 그렇지 않으면 **False** 를 반환합니다.  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   여러 **IIF** 함수(“중첩 IIF”라고도 함)를 사용하여 `PctComplete`의 값에 따라 3개의 값 중 하나를 반환할 수 있습니다. 다음 식을 입력란의 채우기 색에 배치하면 입력란의 값에 따라 배경색을 변경할 수 있습니다.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     값이 10 이상이면 녹색 배경을 표시하고 1에서 9 사이면 파란색 배경을, 1 미만이면 빨간색 배경을 표시합니다.  
  
-   같은 기능을 구현하는 다른 방법으로 **Switch** 함수를 사용하는 방법이 있습니다. **Switch** 함수는 테스트할 조건이 3개 이상인 경우에 유용합니다. **Switch** 함수는 계열에서 True로 계산되는 첫 번째 식과 연결된 값을 반환합니다.  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     값이 10 이상이면 녹색 배경을 표시하고 1에서 9 사이면 파란색 배경을 표시하고 1이면 노란색 배경을 표시하고 0 이하면 빨간색 배경을 표시합니다.  
  
-   `ImportantDate` 필드의 값을 테스트하여 1주일 이상 지난 경우 "빨간색"을 반환하고, 그렇지 않으면 "파란색"을 반환합니다. 이 식은 보고서 항목에 있는 입력란의 Color 속성을 제어하는 데 사용할 수 있습니다.  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   `PhoneNumber` 필드의 값을 테스트하고, **null**(Visual Basic의 **Nothing**)이면 "No Value(값 없음)"를 반환하고, 그렇지 않으면 전화 번호 값을 반환합니다. 이 식은 보고서 항목에 있는 입력란의 값을 제어하는 데 사용할 수 있습니다.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   `Department` 필드의 값을 테스트하고, 하위 보고서 이름 또는 **null**(Visual Basic의 **Nothing**)을 반환합니다. 이 식은 포함된 조건부 드릴스루 하위 보고서에 사용할 수 있습니다.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   필드 값이 Null인지 여부를 테스트합니다. 이 식은 이미지 보고서 항목의 **Hidden** 속성을 제어하는 데 사용할 수 있습니다. 다음 예에서 [LargePhoto] 필드로 지정된 이미지는 필드의 값이 Null이 아닌 경우에만 표시됩니다.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   **MonthName** 함수는 지정한 월의 이름을 포함하는 문자열 값을 반환합니다. 다음 예제는 필드에 0 값이 포함된 경우 NA를 표시합니다.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> 보고서 함수  
 식에서 보고서의 데이터를 조작하는 데 사용할 수 있는 추가 보고서 함수에 대한 참조를 추가할 수 있습니다. 이 섹션에서는 이러한 함수 중 두 가지 예를 제공합니다. 
  
###  <a name="sum"></a><a name="Sum"></a> 합계  
  
-   **Sum** 함수는 그룹 또는 데이터 영역에서 값의 합계를 구합니다. 이 함수는 그룹의 머리글 또는 바닥글에서 유용하게 사용됩니다. 다음 식에서는 Order 그룹 또는 데이터 영역에 데이터의 합계를 표시합니다.  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   조건부 집계 계산에도 **Sum** 함수를 사용할 수 있습니다. 예를 들어 가능한 값이 Not Started, Started, Finished인 State라는 필드가 데이터 세트에 있는 경우 다음 식을 그룹 머리글에 배치하면 Finished 값에 대해서만 집계 합을 계산합니다.  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   **RowNumber** 함수는 데이터 영역의 입력란에 사용될 경우 식이 나타나는 입력란의 각 인스턴스에 대한 행 번호를 표시합니다. 이 함수는 테이블에서 행 번호를 지정하는 데 유용합니다. 또한 행 수에 따라 페이지를 나누는 등 더욱 복잡한 태스크에 유용합니다. 자세한 내용은 이 항목에서 [페이지 나누기](#PageBreaks) 를 참조하십시오.  
  
     **RowNumber** 에 지정한 범위는 번호 다시 매기기를 시작하는 시점을 제어합니다. **Nothing** 키워드는 함수가 가장 바깥쪽 데이터 영역의 첫 번째 행부터 계산을 시작하는 것을 나타냅니다. 중첩 데이터 영역에서 계산을 시작하려면 데이터 영역 이름을 사용하고, 그룹 내에서 계산을 시작하려면 그룹 이름을 사용합니다.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> 보고서 데이터 모양  
 식을 사용하여 데이터가 보고서에 나타나는 모양을 조작할 수 있습니다. 예를 들어 단일 입력란에서 두 필드의 값을 표시하거나, 보고서에 대한 정보를 표시하거나, 페이지 나누기가 보고서에 삽입되는 모양에 영향을 줄 수 있습니다.  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> 페이지 머리글 및 바닥글  
 보고서를 디자인할 때 보고서 이름 및 보고서 바닥글에 페이지 번호를 표시할 수 있습니다. 이렇게 하려면 다음 식을 사용합니다.  
  
-   다음 식에서는 보고서 이름과 보고서가 실행된 시간을 제공합니다. 식은 보고서 바닥글이나 보고서 본문의 입력란에 배치할 수 있습니다. 시간은 간단한 날짜에 대한 .NET Framework 서식 문자열의 형식으로 지정됩니다.  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   다음 식을 보고서 바닥글에 사용하면 보고서의 페이지 번호와 총 페이지 수를 제공합니다.  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 다음 예에서는 디렉터리 목록에서 찾을 수 있는 페이지와 유사한 페이지의 첫 번째와 마지막 값을 페이지 머리글에 표시하는 방법을 설명합니다. 이 예에서는 데이터 영역에 `LastName`라는 입력란이 있다고 가정합니다.  
  
-   다음 식을 페이지 머리글 왼쪽의 입력란에 사용하면 페이지에서 `LastName` 입력란의 첫 번째 값을 제공합니다.  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   다음 식을 페이지 머리글 오른쪽의 입력란에 사용하면 페이지에서 `LastName` 입력란의 마지막 값이 제공됩니다.  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 다음 예에서는 총 페이지 수를 표시하는 방법을 설명합니다. 이 예에서는 데이터 영역에 `Cost`라는 입력란이 있다고 가정합니다.  
  
-   다음 식을 페이지 머리글 또는 바닥글에 사용하면 페이지의 `Cost` 입력란에 값의 합계를 제공합니다.  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  페이지 머리글 또는 바닥글에서 식마다 보고서 항목을 하나만 참조할 수 있습니다. 또한 페이지 머리글과 바닥글 식에서 입력란 이름을 참조할 수 있지만 입력란 내의 실제 데이터 식은 참조할 수 없습니다.  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> 페이지 나누기  
 일부 보고서에서는 페이지 나누기를 그룹 또는 보고서 항목 외에도 지정된 행 수의 끝에 배치할 수 있습니다. 이렇게 하려면 그룹이나 원하는 세부 레코드를 포함하는 그룹을 만들고, 페이지 나누기를 그룹에 추가한 다음 그룹 식을 지정된 행 수에 따라 그룹에 추가합니다.  
  
-   다음 식을 그룹 식에 사용하면 25행마다 번호를 할당합니다. 그룹에 페이지 나누기가 정의되어 있는 경우 이 식을 사용하면 25행마다 페이지가 나눠집니다.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     사용자가 페이지당 행 수에 대한 값을 설정하도록 허용하려면 `RowsPerPage` 라는 매개 변수를 만들고 다음 식에서 볼 수 있듯이 그룹 식이 매개 변수에 기반을 두도록 합니다.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> 속성  
 식은 입력란에서 데이터를 표시하는 데 사용될 뿐만 아니라 속성이 보고서 항목에 적용되는 방식을 변경하는 데에도 사용됩니다. 보고서 항목에 대한 스타일 정보를 변경하거나 보고서 항목의 표시 유형을 변경할 수 있습니다.  
  
###  <a name="formatting"></a><a name="Formatting"></a> 서식  
  
-   다음 식을 입력란의 Color 속성에 사용하면 `Profit` 필드의 값에 따라 텍스트 색이 달라집니다.  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     또한 `Me` Visual Basic 개체 변수도 사용할 수 있습니다. 이 변수는 입력란의 값을 참조할 수 있는 다른 방법입니다.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   다음 식을 데이터 영역에 있는 보고서 항목의 BackgroundColor 속성에 사용하면 각 행의 배경색을 흐린 녹색과 흰색으로 번갈아 표시합니다.  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     특정 범위에 식을 사용할 경우 집계 함수의 데이터 세트를 나타내야 할 수도 있습니다.  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  사용 가능한 색은 .NET Framework KnownColor 열거형에서 제공합니다.  
  
### <a name="chart-colors"></a>차트 색  
 셰이프 차트의 색을 지정하려면 사용자 지정 코드를 사용하여 색이 데이터 요소 값에 매핑되는 순서를 제어할 수 있습니다. 이렇게 하면 범주 그룹이 동일한 여러 차트에 일관된 색을 사용할 수 있습니다. 
  
###  <a name="visibility"></a><a name="Visibility"></a> 표시 유형  
 보고서 항목에 대해 표시 유형 속성을 사용하여 보고서에서 항목을 표시하거나 숨길 수 있습니다. 테이블과 같은 데이터 영역에서 처음에 식의 값을 기반으로 정보 행을 숨길 수 있습니다.  
  
-   다음 식을 그룹에서 정보 행의 초기 표시 유형에 사용하면 `PctQuota` 필드에서 90%를 초과하는 모든 판매액에 대해 정보 행을 표시합니다.  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   다음 식을 테이블의 Hidden 속성에 설정하면 테이블에 13개 이상의 행이 있는 경우에만 테이블이 표시됩니다.  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   다음 식을 열의 **Hidden** 속성에 설정하면 데이터 원본에서 데이터를 검색한 후에 보고서 데이터 세트에 필드가 있는 경우에만 열이 표시됩니다.  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URL  
 보고서 데이터를 사용하여 URL을 사용자 지정할 수 있으며 입력란에 대한 동작으로 URL을 추가할지 여부를 조건부로 제어할 수도 있습니다.  
  
-   다음 식을 입력란에서 동작으로 사용하면 데이터 세트 필드 `EmployeeID`를 URL 매개 변수로 지정하는 사용자 지정 URL이 생성됩니다.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   다음 식은 입력란에 URL을 추가할지 여부를 조건부로 제어합니다. 이 식은 보고서에 활성 URL을 포함할지 여부를 사용자가 결정하도록 허용하는 `IncludeURLs` 라는 매개 변수를 사용합니다. 이 식은 입력란의 동작으로 설정됩니다. 이 매개 변수를 False로 설정하고 보고서를 보면 하이퍼링크 없이 Microsoft Excel로 보고서를 내보낼 수 있습니다.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
> [!NOTE]
>  Power BI 페이지를 매긴 보고서는 **Go To URL** 식에서 JavaScript를 사용하는 것을 지원하지 않습니다.  
  
##  <a name="report-data"></a><a name="ReportData"></a> 보고서 데이터  
 식을 사용하여 보고서에 사용되는 데이터를 조작할 수 있습니다. 매개 변수 및 다른 보고서 정보를 참조할 수 있습니다. 보고서 데이터 검색에 사용하는 쿼리를 변경할 수도 있습니다.  
  
###  <a name="parameters"></a><a name="Parameters"></a> 매개 변수  
 매개 변수의 식을 사용하여 매개 변수에 대한 기본값을 다양화할 수 있습니다. 예를 들어 매개 변수를 사용하여 보고서 실행에 사용하는 사용자 ID에 따라 특정 사용자에 대한 데이터를 필터링할 수 있습니다.  
  
-   다음 식을 매개 변수에 대한 기본값으로 사용하면 보고서를 실행하는 사람의 사용자 ID를 수집합니다.  
  
    ```  
    =User!UserID  
    ```  
  
-   쿼리 매개 변수, 필터 식, 입력란 또는 보고서의 다른 영역에서 매개 변수를 참조하려면 **Parameters** 전역 컬렉션을 사용합니다. 이 예에서는 매개 변수 이름을 *Department* 라고 가정합니다.  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   매개 변수는 보고서에서 만들 수 있지만 숨김으로 설정됩니다. 보고서가 보고서 서버에서 실행되면 매개 변수가 도구 모음에 표시되지 않으며 보고서 판독기에서 기본값을 변경할 수 없습니다. 기본값으로 설정된 숨겨진 매개 변수를 사용자 지정 상수로 사용할 수 있습니다. 이 값을 필드 식을 포함한 모든 식에 사용할 수 있습니다. 다음 식은 *ParameterField* 라는 매개 변수에 대한 기본 매개 변수 값으로 지정된 필드를 식별합니다.  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> 사용자 지정 코드  
 보고서에 포함된 사용자 지정 코드를 사용할 수 있습니다. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>사용자 지정 집계에 그룹 변수 사용  
 특정 그룹 범위에 대해 로컬인 그룹 변수의 값을 초기화한 다음 해당 변수에 대한 참조를 식에 포함할 수 있습니다. 사용자 지정 코드가 있는 그룹 변수를 사용하려면 사용자 지정 집계를 구현합니다. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>런타임에 null 또는 0 값 표시 안 함  
 식의 일부 값은 보고서를 처리할 때 Null이나 정의되지 않은 값으로 계산될 수 있습니다. 이 경우 런타임 오류가 발생하여 입력란에 계산된 식이 아닌 **#Error** 가 표시될 수 있습니다. **IIF** 함수는 이러한 동작에 특히 민감합니다. If-Then-Else 문과 달리 **IIF** 문의 각 부분(함수 호출 포함)이 **true** 또는 **false** 를 테스트하는 루틴에 전달되기 전에 계산되기 때문입니다. `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` 문은 **가 NOTHING인 경우 렌더링된 보고서에서** #Error `Fields!Sales.Value` 를 생성합니다.  
  
 이러한 상황을 방지하려면 다음 전략 중 하나를 사용합니다.  
  
-   필드 B의 값이 0이거나 정의되지 않은 경우 분자를 0으로, 분모를 1로 설정합니다. 그렇지 않은 경우 분자를 필드 A의 값으로, 분모를 필드 B의 값으로 설정합니다.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   사용자 지정 코드 함수를 사용하여 식의 값을 반환합니다. 다음 예에서는 현재 값과 이전 값의 차이를 백분율로 반환합니다. 이는 두 개의 연속 값 사이의 차이를 계산하는 데 사용할 수 있으며, 첫 번째 비교의 경계 사례(이전 값이 없는 경우)와 이전 값 또는 현재 값 중 하나가 **null**(Visual Basic의 **Nothing**)인지 여부를 처리합니다.  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     다음 식은 "ColumnGroupByYear" 컨테이너(그룹 또는 데이터 영역)에 대해 입력란에서 이 사용자 지정 코드를 호출하는 방법을 보여줍니다.  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     이 방법으로 런타임 예외를 방지할 수 있습니다. 이제 입력란의 `=IIF(Me.Value < 0, "red", "black")` Color **속성에서** 같은 식을 사용하여 값이 0보다 큰지 작은지에 따라 조건부로 텍스트를 표시할 수 있습니다.  
  
## <a name="next-steps"></a>다음 단계

- [Power BI Premium에서 페이지를 매긴 보고서란?](paginated-reports-report-builder-power-bi.md)
