---
title: Power BI Desktop의 Analysis Services 다차원 데이터
description: Power BI Desktop의 SSAS(SQL Server Analysis Services) 다차원 데이터
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7b96e9707e9c91c6403047091bed00afbff3789d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222527"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Power BI Desktop의 SSAS 다차원 모델에 연결

Power BI Desktop을 통해 일반적으로 *SSAS MD*라고 하는 *SSAS 다차원 모델*에 액세스할 수 있습니다.

SSAS MD 데이터베이스에 연결하려면 **데이터 가져오기**를 선택하고 **데이터베이스** > **SQL Server Analysis Services**를 선택한 다음 **연결**을 선택합니다.

![SSAS(SQL Server Analysis Services) 데이터베이스, 데이터 가져오기 대화 상자, Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

Power BI 서비스 및 Power BI Desktop은 모두 라이브 연결 모드에서 SSAS 다차원 모델을 지원합니다. 라이브 모드에서 **SSAS 다차원 모델**을 사용하는 보고서를 Power BI 서비스에 게시 및 업로드할 수 있습니다.

## <a name="capabilities-and-features-of-ssas-md"></a>SSAS MD의 기능 및 특징

다음 섹션에서는 Power BI 및 SSAS MD 연결의 특징과 기능을 설명합니다.

### <a name="tabular-metadata-of-multidimensional-models"></a>다차원 모델의 테이블 형식 메타데이터

다음 테이블은 다차원 개체와 Power BI Desktop에 반환되는 테이블 형식 메타데이터 간의 관계를 보여줍니다. Power BI가 테이블 형식 메타데이터에 대한 모델을 쿼리합니다. 반환된 메타데이터를 기반으로 하는 Power BI Desktop은 시각화(예: 테이블, 행렬, 차트 또는 슬라이서)를 만들 때 SSAS에 대해 적절한 DAX 쿼리를 실행합니다.

| BISM-Multidimentional 개체 | 테이블 형식 메타데이터 |
| --- | --- |
| 큐브 |모델 |
| 큐브 차원 |테이블 |
| 차원 특성(키), 이름 |열 |
| 측정값 그룹 |테이블 |
| 측정값 |측정값 |
| 연결된 측정값 그룹이 없는 측정값 |측정값이라고 하는 테이블 내에서  |
| 측정값 그룹 -> 큐브 차원 관계 |관계 |
| 큐브 뷰 |큐브 뷰 |
| KPI |KPI |
| 사용자/부모-자식 계층 구조 |계층 구조 |

### <a name="measures-measure-groups-and-kpis"></a>측정값, 측정값 그룹 및 KPI

다차원 큐브의 측정값 그룹은 **필드** 창에서 옆에 시그마(∑)가 포함된 테이블로 표시됩니다. 연결된 측정값 그룹이 없는 계산 측정값은 테이블 형식 메타데이터의 *측정값*이라고 하는 특수 테이블 아래에 그룹화됩니다.

다차원 모델에서 복잡한 모델을 간소화하기 위해 ‘표시 폴더’ 내에 위치할 큐브에서 측정값 집합 또는 KPI 집합을 정의할 수 있습니다.  Power BI는 테이블 형식 메타데이터의 표시 폴더를 인식하고 표시 폴더 내 측정값 및 KPI를 보여줍니다. 다차원 데이터베이스의 KPI는 *값*, *목표*, *상태 그래픽* 및 *추세 그래픽*을 지원합니다.

### <a name="dimension-attribute-type"></a>차원 특성 형식

다차원 모델은 또한 차원 특성과 특정 차원 특성 형식에 연결하는 것도 지원합니다. 예를 들어, *도시*, *시/도*, *국가* 및 *우편 번호* 차원 특성이 적절한 지리 형식을 가지고 있고 이들과 연결된 **지리** 차원은 테이블 형식 메타데이터에 노출됩니다. Power BI는 메타 데이터를 인식하여 맵을 시각화할 수 있도록 해줍니다. Power BI의 *필드* 창 요소 옆에 있는 **맵** 아이콘으로 이러한 연결을 알아볼 수 있습니다.

또한 Power BI는 이미지의 URL(Uniform Resource Locator)을 포함하는 필드를 제공하면 이미지를 렌더링할 수도 있습니다. 이러한 필드를 SQL Server Data Tools에서(또는 Power BI에서) *ImageURL* 형식으로 지정할 수 있습니다. 그런 다음 해당 형식 정보가 테이블 형식 메타데이터에 포함된 Power BI에 제공됩니다. 그런 다음 Power BI는 URL에서 이러한 이미지를 검색하고 시각적 개체에 표시할 수 있습니다.

### <a name="parent-child-hierarchies"></a>부모-자식 계층 구조

다차원 모델은 테이블 형식 메타데이터의 *계층*으로 제공되는 부모-자식 계층 구조를 지원합니다. 부모-자식 계층 구조의 각 수준은 테이블 형식 메타데이터에 숨겨진 열로 노출됩니다. 부모-자식 차원의 키 특성은 테이블 형식 메타데이터에 노출되지 않습니다.

### <a name="dimension-calculated-members"></a>차원 계산 멤버

다차원 모델은 다양한 형식의 계산 멤버생성을 지원합니다.  가장 일반적인 두 가지 형식의 계산 멤버는 다음과 같습니다.

* *모두*의 형제가 아닌 특성 계층의 계산 멤버
* 사용자 계층 구조의 계산 멤버

다차원 모델은 *특성 계층의 계산 멤버*를 열의 값으로 노출합니다. 이러한 형식의 계산 멤버를 노출하려면 몇 가지 추가 옵션 및 제약 조건이 있습니다.

* 선택 사양인 *UnknownMember*를 가질 수 있는 차원 특성

* 계산 멤버를 포함하는 특성이 차원의 유일한 특성이 아닐 경우 해당 특성은 차원의 키 특성이 될 수 없습니다.

* 계산 멤버를 포함하는 특성은 부모-자식 특성일 수 없습니다.

사용자 계층 구조의 계산 멤버는 Power BI에 노출되지 않습니다. 대신 사용자 계층의 계산 멤버를 포함하는 큐브에 연결할 수 있습니다. 그러나 이전 글머리 기호 목록에서 언급한 제약 조건을 충족하지 않는 경우 계산 멤버를 볼 수 없습니다.

### <a name="security"></a>보안

다차원 모델은 *역할*을 통해 차원 및 셀 수준 보안을 지원합니다. Power BI를 사용하여 큐브에 연결하는 경우 적절한 사용 권한에 대해 인증되고 평가됩니다. 사용자가 ‘차원 보안’을 적용하면, 해당 차원 멤버는 Power BI에서 사용자가 볼 수 없습니다.  그러나 사용자가 ‘셀 보안’ 사용 권한을 정의하여 특정 셀을 제한하는 경우, 해당 사용자는 Power BI를 사용하여 큐브에 연결할 수 없습니다. 

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항

SSAS MD를 사용하는 데에는 특정 제한 사항이 있습니다.

* Enterprise 및 BI 버전의 SQL Server 2014만 라이브 연결을 지원합니다. Standard 버전의 SQL Server에서는 라이브 연결을 위해 SQL Server 2016 이상이 필요합니다.

* *작업* 및 *명명된 집합*은 Power BI에 노출되지 않습니다. 시각적 개체 및 보고서를 만들기 위해 작업 또는 명명된 세트를 포함하는 큐브에 계속 연결할 수 있습니다.

* Power BI가 SSAS 모델에 대한 메타데이터를 표시하는 경우 때때로 모델에서 데이터를 검색할 수 없습니다. 이 시나리오는 32비트 버전의 MSOLAP 공급자를 설치했지만 64비트 버전을 설치하지 않은 경우에 발생할 수 있습니다. 64비트 버전을 설치하면 문제가 해결될 수 있습니다.

* SSAS 다차원 모델에 연결된 보고서를 작성할 때 ‘보고서 수준’ 측정값을 만들 수 없습니다.  사용할 수 있는 유일한 측정값은 MD 모델에 정의된 측정값입니다.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Power BI Desktop에서 지원되는 SSAS MD의 기능

이 SSAS MD 릴리스에서는 다음 요소의 소비가 지원됩니다. 이러한 기능에 대한 자세한 내용은 [다차원 모델에 대한 파워 뷰 이해](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014)를 참조하세요.

* 기본 멤버
* 차원 특성
* 차원 특성 형식
* 다음과 같은 차원 계산 멤버:
  * 차원에 둘 이상의 특성이 있는 경우 단일 실제 멤버여야 합니다.
  * 유일한 특성이 아니면 차원의 키 특성일 수 없습니다. 그리고
  * 부모-자식 특성이 될 수 없습니다.
* 차원 보안
* 표시 폴더
* 계층 구조
* ImageUrls
* KPI
* KPI 추세
* 측정값(측정값 그룹 유무)
* 변형으로서 측정값

## <a name="troubleshooting"></a>문제 해결

다음 목록에서는 SSAS(SQL Server Analysis Services)에 연결하는 경우에 발생하는 알려진 모든 문제를 설명합니다.

* **오류: 모델 스키마를 로드할 수 없습니다.** - Analysis Services에 연결 중인 사용자가 데이터베이스/큐브에 액세스할 수 없는 경우에 일반적으로 이 오류가 발생합니다.
