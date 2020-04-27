---
title: Power BI Desktop의 모델에서 보고서 분리
description: Power BI Desktop의 모델에서 보고서를 분리하는 방법에 대한 지침입니다.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: dad451da460abed65a69990394522f268d7f21cd
ms.sourcegitcommit: 5ece366fceee9832724dae40eacf8755e1d85b04
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81525268"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Power BI Desktop의 모델에서 보고서 분리

새 Power BI Desktop 솔루션을 만들 때 수행해야 하는 첫 번째 작업 중 하나는 "데이터 가져오기"입니다. 데이터를 가져오면 명백하게 다른 두 가지 결과를 발생시킬 수 있습니다. 결과는 다음과 같을 수 있습니다.

- 이미 게시된 모델에 대한 [Live Connection](../desktop-report-lifecycle-datasets.md)을 만듭니다. 이 모델은 Power BI 데이터 세트 또는 원격 호스팅 Analysis Services 모델일 수 있습니다.
- 가져오기, DirectQuery 또는 복합 모델일 수 있는 새 모델 개발을 시작합니다.

이 문서는 두 번째 시나리오와 관련이 있습니다. 보고서와 모델을 단일 Power BI Desktop 파일로 결합해야 하는지 여부에 대한 지침을 제공합니다.

## <a name="single-file-solution"></a>단일 파일 솔루션

_단일 파일 솔루션_은 모델을 기반으로 하는 단일 보고서만 있는 경우 제대로 작동합니다. 이 경우 모델과 보고서가 모두 동일한 사람의 것일 가능성이 높습니다. 보고서를 다른 사용자와 공유할 수는 있지만 _개인 BI_ 솔루션으로 정의합니다. 이러한 솔루션은 일반적으로 _임시_ 보고서로 설명되는 비즈니스 챌린지의 역할 범위 보고서 또는 일회성 평가를 나타낼 수 있습니다.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="단일 파일에는 동일한 사람이 개발한 모델 및 보고서가 포함되어 있습니다." border="true":::

## <a name="separate-report-files"></a>보고서 파일 분리

다음과 같은 경우 모델 및 보고서 개발을 별도의 Power BI Desktop 파일로 분리하는 것이 좋습니다.

- 데이터 모델러와 보고서 작성자가 서로 다른 사람인 경우.
- 모델은 현재 또는 나중에 여러 보고서에 대한 원본이 되는 것으로 이해되는 경우.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="다음과 같은 세 가지 PBIX 파일이 있습니다. 첫 번째 파일에는 모델만 포함됩니다. 다른 두 파일은 보고서만 포함하고 Power BI 서비스에 호스트된 모델에 라이브 연결합니다. 보고서는 다른 사람이 개발합니다." border="true":::

데이터 모델러는 여전히 Power BI Desktop 보고서 제작 환경을 사용하여 모델 디자인을 테스트하고 유효성을 검사할 수 있습니다. 그러나 Power BI 서비스에 파일을 게시한 직후에는 작업 영역에서 보고서를 제거해야 합니다. 그리고 데이터 세트를 다시 게시하여 덮어쓸 때마다 보고서를 제거해야 한다는 점에 주의해야 합니다.

### <a name="preserve-the-model-interface"></a>모델 인터페이스 유지

때로는 모델 변경이 불가피한 경우도 있습니다. 데이터 모델러는 모델 인터페이스가 손상되지 않도록 주의해야 합니다. 이러한 작업을 수행하는 경우 관련 보고서 시각적 개체 또는 대시보드 타일이 손상될 수 있습니다. 손상된 시각적 개체는 오류로 나타나며 보고서 작성자와 소비자에게 불편을 일으킬 수 있습니다. 심지어 데이터의 신뢰를 줄일 수 있습니다.

따라서 모델 변경 내용을 신중하게 관리해야 합니다. 가능하면 다음과 같이 변경하지 마십시오.

- 테이블, 열, 계층 구조, 계층 수준 또는 측정값의 이름을 재지정
- 열 데이터 형식 수정
- 다른 데이터 형식을 반환하도록 측정값 식 수정
- 측정값을 다른 홈 테이블로 이동. 측정값을 이동하면 해당 홈 테이블 이름을 사용하여 측정값을 정규화하는 보고서 범위 측정값이 손상될 수 있기 때문입니다. 정규화된 측정값 이름을 사용하여 DAX 식을 작성하지 않는 것이 좋습니다. 자세한 내용은 [DAX: 열 및 측정값 참조](dax-column-measure-references.md)를 참조하세요.

새 테이블, 열, 계층, 계층 수준 또는 측정값을 추가하는 것은 안전하지만 한 가지 예외는 있습니다. 새 측정값 이름이 보고서 범위 측정값 이름과 충돌할 수 있습니다. 충돌을 방지하려면 보고서 작성자가 보고서에서 측정값을 정의할 때 명명 규칙을 채택하는 것이 좋습니다. 보고서 범위 측정값 이름에 밑줄 또는 다른 문자를 접두사로 사용할 수 있습니다.

모델에 대한 주요 변경 내용을 적용해야 하는 경우 다음 중 하나를 수행하는 것이 좋습니다.

- Power BI 서비스에서 [데이터 세트에 대한 관련 콘텐츠를 봅니다](../consumer/end-user-related.md#view-related-content-for-a-dataset).
- Power BI 서비스에서 [데이터 계보](../collaborate-share/service-data-lineage.md) 보기를 탐색합니다.

두 옵션 모두 관련 보고서 및 대시보드를 신속하게 식별할 수 있습니다. 관련된 각 아티팩트에 대한 연락처를 쉽게 볼 수 있으므로 데이터 계보 보기를 선택하는 것이 더 나을 수 있습니다. 실제로 이는 연락처에 주소가 지정된 전자 메일 메시지를 여는 하이퍼링크입니다.

계획된 주요 변경 내용에 대해 알리려면 각 관련 아티팩트의 소유자에게 문의하는 것이 좋습니다. 이러한 방식으로 보고서를 준비하고 다시 게시할 준비가 되어 가동 중지 시간 및 불만을 최소화할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 문서와 관련된 보다 자세한 내용을 알아보려면 다음 리소스를 참조하세요.

- [Power BI Desktop에서 Power BI 서비스의 데이터 세트에 연결](../desktop-report-lifecycle-datasets.md)
- [Power BI 서비스에서 관련 콘텐츠 보기](../consumer/end-user-related.md)
- [데이터 계보](../collaborate-share/service-data-lineage.md)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)
