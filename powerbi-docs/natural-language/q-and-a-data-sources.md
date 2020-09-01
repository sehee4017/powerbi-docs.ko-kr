---
title: 가져오기, 라이브 연결 및 직접 쿼리에서 자연어 사용
description: 이 문서에서는 Power BI에서 사용할 수 있는 다양한 유형의 데이터 원본에서 Q&A 기능이 어떻게 작동하는지 살펴봅니다. 인덱싱 및 캐싱의 개념도 살펴봅니다.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: mohaali
ms.openlocfilehash: 85ecc5adc55daee86922c39e417db1cac5ba4a52
ms.sourcegitcommit: 0f807d3c74e5202b6e6a95fad49f2787928b9613
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706214"
---
# <a name="use-natural-language-with-import-live-connect-and-direct-query"></a>가져오기, 라이브 연결 및 직접 쿼리에서 자연어 사용

Power BI의 Q&A 기능을 사용하면 자연어를 통해 해당 데이터에 관해 질문을 하여 데이터에서 빠르게 답변을 얻을 수 있습니다. 이 문서에서는 인덱싱 및 캐싱을 사용하여 지원되는 각 구성의 성능을 개선하는 하는 방법을 설명합니다.

## <a name="what-data-sources-are-supported-in-qa"></a>Q&A에서 지원되는 데이터 원본은 무엇인가요?

Q&A는 다음 구성에서 지원됩니다.

- 가져오기 모드
- 라이브 연결 모드 – 온-프레미스 SQL Server Analysis Services, Azure Analysis Services 또는 Power BI 데이터 세트 사용
- 직접 쿼리 - Azure Synapse, Azure SQL 및 SQL Server 2019. 다른 원본이 직접 쿼리 모드에서 작동할 수도 있지만 공식적으로 해당 원본을 지원하지 않습니다.

Q&A 시각적 개체를 사용하는 경우 기본적으로 Q&A가 보고서 내부에서 사용됩니다. 직접 쿼리 또는 라이브 연결을 사용하는 경우 프롬프트가 표시됩니다. 옵션으로 이동하여 보고서의 자연어 기능을 명시적으로 켜고 끌 수 있습니다.

![Q&A 데스크톱 옵션](media/qna-desktop-options.png)

자세한 내용은 [Power BI Q&A 제한 사항](q-and-a-limitations.md)을 참조하세요.

## <a name="how-does-indexing-work-with-qa"></a>Q&A에서 인덱싱은 어떻게 작동하나요?

Q&A를 사용하는 경우 인덱스는 사용자에게 실시간 피드백을 빠르게 제공하고 사용자의 질문을 해석하는 데 도움이 되도록 빌드됩니다. 인덱스는 빌드하는 데 다소 시간이 걸릴 수 있으며 다음 요소 및 제한 사항을 포함합니다.

- Q&A 도구 내에서 명시적으로 꺼진 경우가 아니면 모든 열 이름 및 테이블이 인덱스에 삽입됩니다.
- 100자 미만의 모든 텍스트 값이 인덱싱됩니다. 100자를 초과하는 텍스트 값은 인덱싱되지 않습니다. 
- Q&A는 최대 5백만 개 고유 값을 해당 인덱스에 저장합니다. 해당 임계값을 초과하면 인덱스는 Q&A에서 받은 결과의 정확도를 줄일 수 있는 모든 잠재적인 값을 포함하지 않습니다.
- 인덱싱 중에 오류가 발생하면 다음 섹션에 설명된 대로 인덱스는 부분 상태로 유지되며 다음에 새로 고칠 때 다시 생성됩니다.

## <a name="how-often-is-the-index-refreshed-and-cached"></a>인덱스는 얼마나 자주 새로 고치고 캐시하나요?

Power BI Desktop에서 Q&A를 사용할 때 인덱스가 생성됩니다. 인덱스가 빌드되고 있음을 알리는 작은 아이콘이 표시됩니다. 이 시간 동안 제안을 포함한 Q&A 시각적 개체를 로드하는 데 시간이 걸릴 수 있습니다.

Power BI 서비스에서 인덱스는 게시/다시 게시하고 새로 고칠 때 다시 생성됩니다. Q&A 인덱스가 항상 자동으로 생성되는 것은 않으며 경우에 따라 데이터 세트 새로 고침을 최적화하기 위해 요청 시에만 생성됩니다. 직접 쿼리를 위해 데이터를 최대 하루에 한 번 인덱싱하여 직접 쿼리 원본에 대한 영향을 줄입니다.

## <a name="next-steps"></a>다음 단계

보고서에 자연어를 통합하는 방법에는 여러 가지가 있습니다. 자세한 내용은 다음 문서를 참조하세요.

* [질문 및 답변 시각적 개체](../visuals/power-bi-visualization-q-and-a.md)
* [질문 및 답변 모범 사례](q-and-a-best-practices.md)
