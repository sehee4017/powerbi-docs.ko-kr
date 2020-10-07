---
title: Power BI 데이터 세트 속성
description: Power BI 데이터 세트 API의 속성에 대한 자세한 내용
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: e0092003cbf019bcf720eeb7aa32e8a9e800f143
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747301"
---
# <a name="dataset-properties"></a>데이터 세트 속성

데이터 세트 API의 현재 v1은 이름과 테이블의 컬렉션을 사용하여 데이터 세트를 만듭니다. 각 테이블에는 이름과 행의 컬렉션이 있습니다. 각 열에는 이름 및 datatype이 있습니다. 테이블 간의 측정값 및 관계를 지원함으로써 특히 이러한 속성을 확장했습니다. 이 릴리스에 대해 지원되는 속성의 전체 목록은 아래와 같습니다.

> [!IMPORTANT]
> [데이터 세트 작업 그룹](/rest/api/power-bi/datasets) 페이지에서 액세스할 수 있습니다.

## <a name="dataset"></a>데이터 세트

이름  |Type  |설명  |읽기 전용  |필수
---------|---------|---------|---------|---------
id     |  Guid       | 데이터 세트용 시스템 전체 범위 고유 식별자입니다.        | True        | False        
name     | String        | 데이터 세트의 사용자 정의 이름입니다.        | False        | True        
tables     | Table[]        | 테이블의 컬렉션입니다.        |  False       | False        
relationships     | Relationship[]        | 테이블 간 관계의 컬렉션입니다.        | False        |  False  
defaultMode     | String        | 데이터 세트가 "Push" 및 "Streaming"의 값으로 푸시되거나, 스트림되거나 둘 다 되는지 여부를 결정합니다.         | False        |  False

## <a name="table"></a>Table

이름  |Type  |설명  |읽기 전용  |필수
---------|---------|---------|---------|---------
name     | String        |  테이블의 사용자 정의 이름입니다. 테이블의 식별자로 사용되기도 합니다.       | False        |  True       
columns     |  column[]       |  열의 컬렉션입니다.       | False        |  True       
measures     | measure[]        |  측정값의 컬렉션입니다.       | False        |  False       
isHidden     | Boolean        | True인 경우, 테이블은 클라이언트 도구에서 숨겨집니다.        | False        | False        

## <a name="column"></a>열

이름  |Type  |설명  |읽기 전용  |필수
---------|---------|---------|---------|---------
name     |  String        | 열의 사용자 정의 이름입니다.        |  False       | True       
dataType     |  String       |  지원되는 [EDM 데이터 형식](/dotnet/framework/data/adonet/entity-data-model-primitive-data-types) 및 제한 사항입니다. [데이터 형식 제한](#data-type-restrictions)을 참조하세요.      |  False       | True        
formatString     | String        | 값이 표시될 때 그 서식을 어떻게 지정하는지 설명하는 문자열입니다. 문자열 서식을 지정하는 방법에 대 한 자세한 내용은 [FORMAT_STRING 콘텐츠](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents)를 참조하세요.      | False        | False        
sortByColumn    | String        |   현재 열을 정렬하는 데 사용하기 위해 동일 테이블에 있는 열의 문자열 이름입니다.     | False        | False       
dataCategory     | String        |  이 열에 있는 데이터를 설명하는 데이터 범주에 사용할 문자열 값입니다. 몇 가지 일반적인 값으로는 Address, City, Continent, Country, Image, ImageUrl, Latitude, Longitude, Organization, Place, PostalCode, StateOrProvince, WebUrl 등이 있습니다.       |  False       | False        
isHidden    |  Boolean       |  열을 보기에서 숨겨져 있는지를 나타내는 속성입니다. 기본값은 false입니다.       | False        | False        
summarizeBy     | String        |  열에 대한 기본 집계 메서드입니다. 값으로는 default, none, sum, min, max, count, average, distinctCount 등이 있습니다.     |  False       | False

## <a name="measure"></a>측정값

이름  |Type  |설명  |읽기 전용  |필수
---------|---------|---------|---------|---------
name     | String        |  측정값의 사용자 정의 이름입니다.       |  False       | True        
expression     | String        | 유효한 DAX 식입니다.        | False        |  True       
formatString     | String        |  값이 표시될 때 그 서식을 어떻게 지정하는지 설명하는 문자열입니다. 문자열 서식을 지정하는 방법에 대 한 자세한 내용은 [FORMAT_STRING 콘텐츠](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents)를 참조하세요.       | False        | False        
isHidden     | String        |  True인 경우, 테이블은 클라이언트 도구에서 숨겨집니다.       |  False       | False       

## <a name="relationship"></a>관계

이름  |Type  |설명  |읽기 전용  |필수 
---------|---------|---------|---------|---------
name     | String        | 관계의 사용자 정의 이름입니다. 관계의 식별자로 사용되기도 합니다.        | False       | True        
crossFilteringBehavior     | String        |    관계의 필터 방향으로는 OneDirection(기본값), BothDirections, Automatic 등이 있습니다.       | False        | False        
fromTable     | String        | 외래 키 테이블의 이름입니다.        | False        | True         
fromColumn    | String        | 외래 키 열의 이름입니다.        | False        | True         
toTable    | String        | 기본 키 테이블의 이름입니다.        | False        | True         
toColumn     | String        | 기본 키 열의 이름입니다.        | False        | True        

## <a name="data-type-restrictions"></a>데이터 형식 제한

이러한 제한은 dataType 속성에 적용됩니다.

데이터 형식  |제한 사항  
---------|---------
Int64     |   Int64.MaxValue 및 Int64.MinValue는 허용되지 않습니다.      
Double     |  Double.MaxValue 및 Double.MinValue 값은 허용되지 않습니다. NaN은 지원되지 않습니다.+Infinity 및 -Infinity는 일부 함수(예: Min, Max)에서 지원되지 않습니다.       
Boolean     |   True 또는 False입니다.
Datetime    |   데이터 로드 동안 일 분수가 포함된 값을 1/300초(3.33ms)의 배수로 양자화합니다.      
String     |  현재 문자열 값당 최대 4000자를 허용합니다.
10진수|전체 자릿수=28, 확장=4

## <a name="example"></a>예제
다음 코드 샘플에는 이러한 유형의 많은 속성이 있습니다.

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```