---
title: Power BI Desktop의 행 수준 보안(RLS) 지침
description: Power BI Desktop을 사용하여 데이터 모델에서 RLS(행 수준 보안)를 적용하기 위한 지침입니다.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: v-pemyer
ms.openlocfilehash: 308e34e5bf70a9999939c99667075b2e468b4df4
ms.sourcegitcommit: eff98b49e794c7c07670dcfb871f43cb06ed9d3a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85095638"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Power BI Desktop의 행 수준 보안(RLS) 지침

이 문서는 Power BI Desktop을 개발하는 데이터 모델러를 대상으로 합니다. 데이터 모델에서 RLS(행 수준 보안)를 적용하는 좋은 디자인 관행을 설명합니다.

RLS는 테이블 행을 필터링한다는 것을 이해하는 것이 중요합니다. 테이블, 열 또는 측정값을 포함한 모델 개체에 대한 액세스를 제한하도록 RLS를 구성할 수 없습니다.

> [!NOTE]
> RLS 또는 RLS 설정 방법은 이 문서에서 설명하지 않습니다. 자세한 내용은 [Power BI Desktop에 대해 RLS(행 수준 보안)를 사용하여 데이터 액세스 제한](../create-reports/desktop-rls.md)을 참조하세요.
>
> 또한 Azure Analysis Services 또는 SQL Server Analysis Services를 사용하여 외부에 호스트된 모델에 대한 라이브 연결에 RLS를 적용하는 것도 다루지 않습니다. 이러한 경우 Analysis Services가 RLS를 적용합니다. Power BI가 SSO(Single Sign-On)를 사용하여 연결하면 Analysis Services가 RLS를 적용 합니다(계정에 관리자 권한이 없는 경우).

## <a name="create-roles"></a>역할 만들기

여러 역할을 만들 수 있습니다. 단일 보고서 사용자의 권한 요구 사항을 고려할 때는 보고서 사용자가 여러 역할의 멤버인 디자인 대신 모든 권한을 부여하는 단일 역할을 만들려고 노력하세요. 보고서 사용자는 사용자 계정을 사용하여 직접적으로 또는 보안 그룹 멤버 자격을 통해 간접적으로 여러 역할에 매핑될 수 있기 때문입니다. 여러 역할 매핑으로 인해 예기치 않은 결과가 발생할 수 있습니다.

보고서 사용자가 여러 역할에 할당되면 RLS 필터는 가산적이 됩니다. 즉, 보고서 사용자는 이러한 필터의 합집합을 나타내는 테이블 행을 볼 수 있습니다. 또한 일부 시나리오에서는 보고서 사용자에게 테이블의 행이 표시되지 않는다고 보장할 수 없습니다. 따라서 SQL Server 데이터베이스 개체(및 기타 권한 모델)에 적용되는 권한과 달리 "한 번 거부되면 항상 거부됨" 원칙이 적용되지 않습니다.

두 역할이 있는 모델을 고려해 보세요. **작업자**라는 첫 번째 역할은 다음 규칙 식을 사용하여 모든 **Payroll** 테이블 행에 대한 액세스를 제한합니다.

```dax
FALSE()
```

> [!NOTE]
> 규칙은 식이 **false**로 계산되면 테이블 행을 반환하지 않습니다.

하지만 **관리자**라는 두 번째 역할은 다음 규칙 식을 사용하여 모든 **Payroll** 테이블 행에 대한 액세스를 허용합니다.

```dax
TRUE()
```

다음에 유의하세요. 보고서 사용자가 두 역할 모두에 매핑되는 경우 모든 **Salary** 테이블 행을 볼 수 있습니다.

## <a name="optimize-rls"></a>RLS 최적화

RLS는 모든 DAX 쿼리에 필터를 자동으로 적용하여 작동하며, 이러한 필터는 쿼리 성능에 부정적인 영향을 미칠 수 있습니다. 따라서 효율적인 RLS는 좋은 모델 디자인으로 귀결됩니다. 다음 문서에서 설명하는 것처럼 모델 디자인 지침을 따르는 것이 중요합니다.

- [별모양 스키마 및 Power BI에서의 중요성 이해](star-schema.md)
- [Power BI 지침 설명서](https://docs.microsoft.com/power-bi/guidance/)에서 찾을 수 있는 모든 관계 지침 문서

일반적으로 팩트 유형 테이블이 아닌 차원 유형 테이블에서 RLS 필터를 적용하는 것이 더 효율적입니다. 또한 잘 디자인된 관계를 사용하여 RLS 필터가 다른 모델 테이블로 전파되도록 합니다. 따라서 모델 관계가 동일한 결과를 얻을 수 있을 때는 [LOOKUPVALUE](https://docs.microsoft.com/dax/lookupvalue-function-dax) DAX 함수를 사용하지 않는 것이 좋습니다.

RLS 필터가 DirectQuery 테이블에서 적용되고 다른 DirectQuery 테이블과의 관계가 있는 경우에는 항상 원본 데이터베이스를 최적화해야 합니다. 그러려면 적절한 인덱스를 디자인하거나 지속형 계산 열을 사용해야 할 수 있습니다. 자세한 내용은 [Power BI Desktop의 DirectQuery 모델 지침](directquery-model-guidance.md)을 참조하세요.

### <a name="measure-rls-impact"></a>RLS 영향 측정

[성능 분석기](../create-reports/desktop-performance-analyzer.md)를 사용하여 Power BI Desktop에서 RLS 필터의 성능 영향을 측정할 수 있습니다. 먼저 RLS가 적용되지 않는 보고서 시각적 개체 쿼리 기간을 확인합니다. 그런 다음 **모델링** 리본 탭에서 **보기 형식** 명령을 사용하여 RLS를 적용하고 쿼리 기간을 확인 및 비교합니다.

## <a name="configure-role-mappings"></a>역할 매핑 구성

Power BI에 게시된 후 멤버를 데이터 세트 역할에 매핑해야 합니다. 데이터 세트 소유자 또는 작업 영역 관리자만 역할에 멤버를 추가할 수 있습니다. 자세한 내용은 [Power BI를 사용하는 행 수준 보안(RLS)(모델에서 보안 관리)](../admin/service-admin-rls.md#manage-security-on-your-model)을 참조하세요.

멤버는 사용자 계정 또는 보안 그룹일 수 있습니다. 가능하면 항상 보안 그룹을 데이터 세트 역할에 매핑하는 것이 좋습니다. 여기에는 Azure Active Directory의 보안 그룹 멤버 자격 관리가 포함됩니다. 네트워크 관리자에게 작업을 위임할 수 있습니다.

## <a name="validate-roles"></a>역할 유효성 검사

각 역할을 테스트하여 모델을 올바르게 필터링하는지 확인합니다. **모델링** 리본 탭에서 **보기 형식** 명령을 사용하면 쉽습니다.

모델에 [USERNAME](https://docs.microsoft.com/dax/username-function-dax) DAX 함수를 사용하는 동적 규칙이 있는 경우 예상된 값 _및 예상되지 않은_ 값을 테스트해야 합니다. 특히 [앱 소유 데이터](../developer/embedded/embedding.md#embedding-for-your-customers) 시나리오를 사용하여 Power BI 콘텐츠를 포함하는 경우 앱 논리는 어떤 값도 유효한 ID 사용자 이름으로 전달할 수 있습니다. 잘못된 값이나 악의적 값이 입력되면 가급적 필터가 행을 반환하지 않도록 합니다.

포함된 Power BI를 사용하여 앱이 사용자의 작업 역할을 유효 사용자 이름으로 전달하는 예를 살펴보겠습니다. 역할은 "관리자" 또는 "작업자" 중 하나입니다. 관리자는 모든 행을 볼 수 있지만 작업자는 **Type** 열 값이 "Internal"인 행만 볼 수 있습니다.

다음 규칙 식이 정의되어 있습니다.

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

이 규칙 식의 문제는 "Worker"를 제외한 모든 값이 모든 테이블 행을 반환한다는 것입니다. 따라서 "Wrker"와 같은 잘못된 값은 뜻하지 않게 모든 테이블 행을 반환합니다. 따라서 예상되는 각 값에 대해 테스트하는 식을 작성하는 것이 더 안전합니다. 다음과 같은 향상된 규칙 식에서는 예상되지 않은 값이 입력되면 테이블이 행을 반환하지 않습니다.

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>부분 RLS 디자인

경우에 따라 RLS 필터로 제한되지 않는 값이 계산에 필요합니다. 예를 들어 보고서가 전체 획득 수익 대비 보고서 사용자 영업 지역 획득 수익의 비율을 표시해야 할 수 있습니다.

DAX 식이 RLS를 재정의하는 것은 불가능하지만(사실 RLS가 적용되는지 확인할 수도 없습니다) 요약 모델 테이블을 사용할 수 있습니다. 요약 모델 테이블을 쿼리하여 "모든 지역"의 수익을 검색하며, 이 테이블은 RLS 필터의 제약을 받지 않습니다.

이 디자인 요구 사항을 구현하는 방법을 알아보겠습니다. 먼저 다음과 같은 모델 디자인을 고려합니다.

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="모델 다이어그램의 이미지가 표시됩니다. 이것은 다음 단락에서 설명합니다.":::

모델은 다음과 같은 4개의 테이블로 구성됩니다.

- **Salesperson** 테이블은 영업 사원당 행 하나를 저장합니다. 여기에는 각 영업 사원의 이메일 주소를 저장하는 **EmailAddress** 열이 포함됩니다. 이 테이블은 숨겨져 있습니다.
- **Sales** 테이블은 주문당 행 하나를 저장합니다. 여기에는 모든 지역의 획득 수익 대비 보고서 사용자 지역 획득 수익의 비율을 반환하도록 설계된 **Revenue % All Region** 측정값이 포함되어 있습니다.
- **Date** 테이블은 날짜당 행 하나를 저장하며, 연도 및 월 필터링과 그룹화를 허용합니다.
- **SalesRevenueSummary**는 계산된 테이블입니다. 이 테이블은 각 주문 날짜의 총 수익을 저장합니다. 이 테이블은 숨겨져 있습니다.

다음 식은 **SalesRevenueSummary** 계산된 테이블을 정의합니다.

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> [집계 테이블](../transform-model/desktop-aggregations.md)은 동일한 디자인 요구 사항을 달성할 수 있습니다.

다음 RLS 규칙은 **Salesperson** 테이블에 적용됩니다.

```dax
[EmailAddress] = USERNAME()
```

다음 테이블에는 세 가지 모델 관계 각각이 설명됩니다.

|관계|설명|
|---------|---------|
|![순서도 종결자 1.](media/common/icon-01-red-30x30.png)|**Salesperson** 테이블과 **Sales** 테이블 사이에는 다대다 관계가 있습니다. RLS 규칙은 [USERNAME](https://docs.microsoft.com/dax/username-function-dax) DAX 함수를 사용하여 숨겨진 **Salesperson** 테이블의 **EmailAddress** 열을 필터링합니다. 보고서 사용자의 **Region** 열 값은 **Sales** 테이블로 전파됩니다.|
|![순서도 종결자 2.](media/common/icon-02-red-30x30.png)|**Date** 테이블과 **Sales** 테이블 사이에는 일대다 관계가 있습니다.|
|![순서도 종결자 3.](media/common/icon-03-red-30x30.png)|**Date** 테이블과 **SalesRevenueSummary** 테이블 사이에는 일대다 관계가 있습니다.|

다음 식은 **Revenue % All Region** 측정값을 정의합니다.

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> 민감한 사실이 공개되지 않도록 주의하세요. 이 예에 두 개의 지역만 있다면 보고서 사용자는 다른 지역의 수익을 계산할 수 있습니다.

## <a name="avoid-using-rls"></a>RLS 사용 방지

RLS는 사용하지 않는 것이 합리적인 경우 가급적 사용하지 마세요. 정적 필터를 적용하는 소수의 간단한 RLS 규칙만 있는 경우 대신 여러 데이터 세트를 게시하는 것이 좋습니다. 각 데이터 세트에는 동일한 데이터 권한이 있는 특정 보고서 사용자 대상 그룹의 데이터가 포함되므로 역할을 정의하는 데이터 세트는 없습니다. 그런 다음 대상 그룹당 하나의 작업 영역을 만들고 작업 영역 또는 앱에 액세스 권한을 할당합니다.

예를 들어 영업 지역이 두 개뿐인 회사가 각 영업 지역의 데이터 세트를 다른 작업 영역에 게시하기로 결정합니다. 데이터 집합은 RLS를 적용하지 않습니다. 하지만 [쿼리 매개 변수](https://docs.microsoft.com/power-query/power-query-query-parameters)를 사용하여 원본 데이터를 필터링합니다. 이러한 방식으로 동일한 모델이 각 작업 영역에 게시되며, 데이터 집합 매개 변수 값만 서로 다릅니다. 영업 사원에게는 작업 영역(또는 게시된 앱) 중 하나에 대한 액세스 권한이 할당됩니다.

RLS를 사용하지 않으면 다음과 같은 몇 가지 장점이 있습니다.

- **쿼리 성능 향상:** 필터 수가 적기 때문에 성능이 향상될 수 있습니다.
- **더 작은 모델:** 모델은 많아지지만 크기는 작아집니다. 모델이 작아지면 특히 호스팅 용량에 리소스 압력이 있을 때 쿼리 및 데이터 새로 고침 응답성이 향상될 수 있습니다. 또한 용량이 설정한 한도 미만으로 모델 크기를 유지하는 것이 더 쉽습니다. 마지막으로 작업 영역을 만들거나 다른 용량으로 이동할 수 있으므로 워크로드를 서로 다른 용량에 분산하는 것이 더 쉽습니다.
- **추가 기능:** [웹에 게시](../collaborate-share/service-publish-to-web.md)와 같이 RLS와 연동되지 않는 Power BI 기능을 사용할 수 있습니다.

하지만 RLS를 사용하지 않으면 다음과 같은 몇 가지 단점이 있습니다.

- **여러 작업 영역:** 각 보고서 사용자 대상 그룹에는 하나의 작업 영역이 필요합니다. 앱이 게시되는 경우 보고서 사용자 대상 그룹마다 하나의 앱이 있다는 의미입니다.
- **콘텐츠 중복:** 각 작업 영역에 보고서 및 대시보드를 만들어야 합니다. 설정 및 유지 관리를 위한 추가 작업과 시간이 필요합니다.
- **높은 권한의 사용자:** 여러 보고서 사용자 대상 그룹에 속한 높은 권한의 사용자는 데이터의 통합 보기를 볼 수 없습니다. 이런 사용자는 (여러 작업 영역이나 앱에서) 여러 보고서를 열어야 합니다.

## <a name="troubleshoot-rls"></a>RLS 문제 해결

RLS가 예기치 않은 결과를 생성하는 경우 다음 문제를 확인합니다.

- 열 매핑 및 필터 방향과 관련하여 모델 테이블 사이에 잘못된 관계가 있습니다.
- **양방향으로 보안 필터 적용** 관계 속성이 올바르게 설정되지 않았습니다. 자세한 내용은 [양방향 관계 지침](relationships-bidirectional-filtering.md)을 참조하세요.
- 테이블에 데이터가 없습니다.
- 잘못된 값이 테이블에 로드됩니다.
- 사용자가 여러 역할에 매핑되어 있습니다.
- 모델에 집계 테이블이 포함되어 있고, RLS 규칙이 필터 집계와 세부 정보를 일관되게 필터링하지 않습니다. 자세한 내용은 [Power BI Desktop에서 집계 사용(집계에 대한 RLS)](../transform-model/desktop-aggregations.md#rls-for-aggregations)을 참조하세요.

특정 사용자가 데이터를 볼 수 없는 경우 사용자의 UPN이 저장되지 않았거나 잘못 입력되었기 때문일 수 있습니다. 이것은 이름 변경으로 인해 사용자 계정이 변경되었기 때문에 갑자기 발생할 수 있습니다.

> [!TIP]
> 테스트를 위해 [USERNAME](https://docs.microsoft.com/dax/username-function-dax) DAX 함수를 반환하는 측정값을 추가합니다. "Who Am I"와 비슷한 이름을 지정할 수 있습니다. 그런 다음 측정값을 보고서의 카드 시각적 개체에 추가하고 Power BI에 게시합니다.

특정 사용자가 모든 데이터를 볼 수 있다면 작업 영역에서 직접 보고서에 액세스하고 있고 데이터 세트 소유자일 가능성이 있습니다. RLS는 다음과 같은 경우에만 적용됩니다.

- 보고서가 앱에서 열린 경우.
- 보고서가 작업 영역에서 열리고 사용자가 [뷰어 역할](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)에 매핑된 경우.

## <a name="next-steps"></a>다음 단계

이 문서와 관련된 보다 자세한 내용을 알아보려면 다음 리소스를 참조하세요.

- [Power BI를 사용하는 RLS(행 수준 보안)](../admin/service-admin-rls.md)
- [Power BI Desktop에 대해 RLS(행 수준 보안)를 사용하여 데이터 액세스 제한](../create-reports/desktop-rls.md)
- [Power BI Desktop의 모델 관계](../transform-model/desktop-relationships-understand.md)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)
