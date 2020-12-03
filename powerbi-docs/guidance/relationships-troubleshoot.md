---
title: 관계 문제 해결 지침
description: 모델 관계 문제 해결에 대한 지침입니다.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: e8f76bf1e1947815176a1b24be2b758489093071
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418535"
---
# <a name="relationship-troubleshooting-guidance"></a>관계 문제 해결 지침

이 문서는 Power BI Desktop을 개발하는 데이터 모델러를 대상으로 합니다. 모델 및 보고서를 개발할 때 발생할 수 있는 특정 문제를 해결하는 방법에 대한 지침을 제공합니다.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>문제 해결 검사 목록

보고서 시각적 개체가 두 개 이상의 테이블에 있는 필드를 사용하도록 구성되어 있는데 올바른 결과를 제공하지 않는 경우 문제가 모델 관계와 관련된 것일 수 있습니다.

이 경우 다음 문제 해결 검사 목록을 따라 일반적인 문제를 해결할 수 있습니다. 문제를 식별할 때까지 검사 목록을 하나씩 처리할 수 있습니다.

1. 시각적 개체를 테이블 또는 행렬로 전환하거나 "데이터 보기" 창을 엽니다. 쿼리 결과를 볼 수 있는 경우 문제를 더 쉽게 해결할 수 있습니다.
1. 쿼리 결과가 비어 있는 경우 데이터 뷰로 전환합니다. 테이블이 데이터 행과 함께 로드되었는지 확인합니다.
1. 모델 뷰로 전환합니다. 쉽게 관계를 확인하고 해당 속성을 빠르게 확인할 수 있습니다.
1. 테이블 간에 관계가 존재하는지 확인합니다.
1. 카디널리티 속성이 올바르게 구성되었는지 확인합니다. 현재 "다" 쪽 열에 고유 값이 포함되어 있고 "일" 쪽으로 잘못 구성된 경우 속성이 잘못된 것일 수 있습니다.
1. 관계가 활성화되어 있는지 확인합니다(실선).
1. 필터 방향이 전파를 지원하는지 확인합니다(화살촉 해석).
1. 올바른 열이 연결되어 있는지 확인합니다. 관계를 선택하거나 커서를 가리켜 연결된 열을 표시합니다.
1. 관련 열 데이터 형식이 동일하거나 최소한 호환되는지 확인합니다. 텍스트 열을 정수 열에 연결할 수 있지만 필터가 전파할 일치 항목을 찾지 못할 수 있습니다.
1. 데이터 뷰로 전환하고 연결된 열에서 일치하는 값을 찾을 수 있는지 확인합니다.

## <a name="troubleshooting-guide"></a>문제 해결 가이드

다음은 발생하는 문제와 가능한 솔루션의 목록입니다.

|문제|가능한 이유|
|---------|---------|
|시각적 개체에 결과가 표시되지 않음|- 모델에 아직 데이터가 로드되지 않았습니다.<br />- 필터 컨텍스트에 데이터가 없습니다.<br />- 행 수준 보안이 적용됩니다.<br />- 관계가 테이블 간에 전파되지 않습니다. 위의 _검사 목록_ 을 참조하세요.<br />- 행 수준 보안이 적용되지만 양방향 관계가 전파되지 않습니다. [Power BI Desktop을 사용하는 행 수준 보안(RLS)](../create-reports/desktop-rls.md)을 참조하세요.|
|시각적 개체가 각 그룹화에 대해 동일한 값을 표시 |- 관계가 존재하지 않습니다.<br />- 관계가 테이블 간에 전파되지 않습니다. 위의 _검사 목록_ 을 참조하세요.|
|시각적 개체에 결과가 표시되지만 올바르지 않음|- 시각적 개체가 잘못 구성되었습니다.<br />- 측정 논리가 잘못되었습니다.<br />- 모델 데이터를 새로 고쳐야 합니다.<br />- 원본 데이터가 올바르지 않습니다.<br />- 관계 열이 잘못 연결되어 있습니다(예: **ProductID** 열이 **CustomerID** 열에 매핑됨).<br />- 두 DirectQuery 테이블 간의 관계이며 관계의 "일" 쪽 열에 중복 값이 포함되어 있습니다.|
|BLANK 그룹화 또는 슬라이서/필터 항목이 나타나고 원본 열에 BLANK가 포함되지 않음|- 일반 관계이며 "다" 쪽 열에 "일" 쪽 열에 저장되지 않은 값이 포함되어 있습니다. [Power BI Desktop의 모델 관계(일반 관계)](../transform-model/desktop-relationships-understand.md#regular-relationships)를 참조하세요.<br />- 일반 일 대 일 관계이며 연결된 열에 BLANK가 포함되어 있습니다. [Power BI Desktop의 모델 관계(일반 관계)](../transform-model/desktop-relationships-understand.md#regular-relationships)를 참조하세요.<br />- 비활성 관계 "다" 쪽 열에 BLANK가 저장되었거나 "일" 쪽에 저장된 값이 없습니다.|
|시각적 개체에 누락된 데이터가 있음|- 잘못된/예기치 않은 필터가 적용되었습니다.<br />- 행 수준 보안이 적용됩니다.<br />- 제한된 관계이며 연결된 열에 BLANK가 있거나 데이터 무결성 문제가 있습니다. [Power BI Desktop의 모델 관계(제한된 관계)](../transform-model/desktop-relationships-understand.md#limited-relationships)를 참조하세요.<br />- 두 DirectQuery 테이블 간의 관계이며 관계가 [참조 무결성을 가정](../transform-model/desktop-relationships-understand.md#assume-referential-integrity)하도록 구성되었지만 데이터 무결성 문제(연결된 열에 일치하지 않는 값)가 있습니다.|
|행 수준 보안이 올바르게 적용되지 않음|- 관계가 테이블 간에 전파되지 않습니다. 위의 _검사 목록_ 을 참조하세요.<br />- 행 수준 보안이 적용되지만 양방향 관계가 전파되지 않습니다. [Power BI Desktop을 사용하는 행 수준 보안(RLS)](../create-reports/desktop-rls.md)을 참조하세요.|
|||

## <a name="next-steps"></a>다음 단계

이 문서와 관련된 보다 자세한 내용을 알아보려면 다음 리소스를 참조하세요.

- [Power BI Desktop의 모델 관계](../transform-model/desktop-relationships-understand.md)
- 질문이 있으신가요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)
