---
title: Power BI로 마이그레이션하기 위해 개념 증명 수행
description: Power BI로 마이그레이션할 때 개념 증명을 수행하는 방법에 관한 지침입니다.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 77174da7fd47470974a292ba98f6b50c268b04fd
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419133"
---
# <a name="conduct-proof-of-concept-to-migrate-to-power-bi"></a>Power BI로 마이그레이션하기 위해 개념 증명 수행

이 문서에서는 Power BI로 마이그레이션할 때 최대한 빨리 위험을 완화하고 미지의 상태를 해결하기 위한 POC(개념 증명) 수행과 관련된 **3단계** 를 설명합니다.

:::image type="content" source="media/powerbi-migration-proof-of-concept/migrate-to-powerbi-stage-3.png" alt-text="Power BI 마이그레이션의 단계를 보여 주는 이미지. 이 문서에서는 3단계가 강조됩니다.":::

> [!NOTE]
> 위의 그래픽에 관한 전체 설명은 [Power BI 마이그레이션 개요](powerbi-migration-overview.md)를 참조하세요.

3단계는 최대한 빨리 미지의 상태를 해결하고 위험을 완화하는 데 초점을 맞춥니다. 기술 POC는 가정의 유효성을 검사하는 데 유용합니다. 솔루션 배포 계획과 함께 반복해서 수행할 수 있습니다([2단계](powerbi-migration-planning.md)에서 설명됨).

이 단계의 산출물은 범위가 좁은 Power BI 솔루션으로, 해결되지 않은 초기 질문을 해결하고 [4단계](powerbi-migration-create-validate-content.md)에서 추가 작업을 프로덕션 환경에서 사용할 수 있도록 준비합니다.

> [!IMPORTANT]
> POC를 삭제 가능한 작업으로 의도하는 것은 아닙니다. 대신, 프로덕션 환경에서 사용할 수 있는 솔루션의 초기 반복일 것으로 예상합니다. 조직에서 해당 활동을 프로토타입, 파일럿, 모형, 빠른 시작 또는 MVP(Minimally Viable Product)로 참조할 수 있습니다. POC 수행이 항상 필요한 것은 아니며 비공식적으로 발생할 수도 있습니다.

> [!TIP]
> 문서에서 설명하는 대부분의 항목은 표준 Power BI 구현 프로젝트에도 적용됩니다. 조직에서 Power BI를 더 능숙하게 사용할 수 있게 되면 POC를 수행할 필요성이 사라집니다. 그러나 Power BI의 빠른 릴리스 주기와 끊임없는 새로운 기능 소개로 인해 학습 목적으로 기술 POC를 정기적으로 수행할 수 있습니다.

## <a name="set-poc-goals-and-scope"></a>POC 목표 및 범위 설정

POC를 수행하는 경우 다음 목표에 초점을 맞춥니다.

- 기능 작동 방식에 관한 가정을 확인합니다.
- 레거시 BI 플랫폼과 비교되는 Power BI 작동 방식의 차이점을 직접 알아봅니다.
- 실무 전문가의 특정 요구 사항에 관해 처음 이해한 내용의 유효성을 검사합니다.
- 데이터 구조, 관계, 데이터 형식 또는 데이터 값과 관련된 문제를 파악하고 검색하기 위해 실제 데이터로 작은 데이터 세트를 만듭니다.
- 모델 계산에 사용되는 [DAX 구문](/dax/) 식을 실험하고 유효성을 검사합니다.
- 게이트웨이를 사용하여 데이터 원본 연결을 테스트합니다(게이트웨이 원본이 될 경우).
- 게이트웨이를 사용하여 데이터 새로 고침을 테스트합니다(게이트웨이 원본이 될 경우).
- 해당하는 경우 행 수준 보안을 포함하여 보안 구성을 확인합니다.
- 레이아웃 및 모양 결정을 실험합니다.
- Power BI 서비스의 모든 기능이 예상대로 작동하는지 확인합니다.

POC 범위는 미지의 상태가 무엇인지 또는 동료와 유효성을 검사해야 하는 목표가 무엇인지에 따라 달라집니다. 복잡성을 줄이려면 범위 측면에서 POC를 최대한 좁게 유지합니다.

대부분의 경우 마이그레이션을 사용할 때 시작하는 기존 솔루션이 있으므로 요구 사항이 잘 알려집니다. 그러나 적용되는 향상된 기능의 범위 또는 기존 Power BI 기술에 따라 POC는 여전히 상당한 가치를 제공합니다. 또한 특히 개선이 이루어진 경우 요구 사항을 빠르게 설명하려면 소비자 피드백을 빠르게 프로토타입으로 생성하는 것이 적절합니다.

> [!IMPORTANT]
> POC에 데이터의 하위 집합만 포함되거나 제한된 시각적 개체만 포함되는 경우에도 처음부터 끝까지 해당 항목을 사용하는 것이 중요합니다. 즉, Power BI Desktop의 개발부터 Power BI 서비스의 개발 작업 영역에 대한 배포까지 해당 항목을 사용해야 합니다. POC 목표를 완전히 달성하는 유일한 방법입니다. Power BI 서비스가 Single Sign-On을 사용하는 DirectQuery 데이터 세트 같이 이전에 사용하지 않은 중요한 기능을 제공해야 하는 경우 특히 그렇습니다. POC 중에는 불확실하거나 다른 사용자에게 확인해야 하는 측면에 초점을 맞춥니다.

## <a name="handle-differences-in-power-bi"></a>Power BI의 차이점 처리

Power BI는 ‘모델 기반 도구’ 또는 ‘보고서 기반 도구’로 사용할 수 있습니다.  모델 기반 솔루션은 데이터 모델을 개발하지만 보고서 기반 솔루션은 이미 배포된 데이터 모델에 연결됩니다.

최고의 유연성으로 인해 마이그레이션하는 원본 레거시 BI 플랫폼과 근본적으로 다를 수 있는 Power BI의 몇 가지 측면이 있습니다.

### <a name="consider-redesigning-the-data-architecture"></a>데이터 아키텍처 다시 디자인 고려

고유한 의미 체계 계층이 있는 레거시 BI 플랫폼에서 마이그레이션하는 경우 가져오기 데이터 세트를 만드는 것이 좋은 옵션이 될 수 있습니다. Power BI 함수는 [별모양 스키마(star schema)](star-schema.md) 테이블 디자인에 가장 적합합니다. 따라서 레거시 의미 체계 계층이 별모양 스키마가 아닌 경우 Power BI를 최대한 활용하기 위해 일부 다시 디자인해야 할 수 있습니다. 별모양 스키마 디자인 원칙(관계, 일반적으로 사용되는 측정값 및 친숙한 조직 용어 포함)에 따라 의미 체계 계층을 디자인하는 작업은 셀프 서비스 보고서 작성자를 위한 훌륭한 시작점이 될 수 있습니다.

보고서가 SQL 쿼리 또는 저장 프로시저를 사용하여 관계형 데이터 원본을 참조하는 레거시 BI 플랫폼에서 마이그레이션하는 경우 및 [DirectQuery 모드](../connect-data/desktop-use-directquery.md)에서 Power BI를 사용하려는 경우 데이터 모델의 일 대 일 마이그레이션을 수행할 수 있습니다.

> [!CAUTION]
> 가져온 단일 테이블로 구성된 많은 Power BI Desktop 파일을 만드는 작업을 살펴보면 이것은 일반적으로 디자인이 최적이 아님을 나타냅니다. 해당 상황을 인식하는 경우 [별모양 스키마](star-schema.md) 디자인을 사용하여 만든 [공유 데이터 세트](../connect-data/service-datasets-across-workspaces.md)를 사용하면 더 나은 결과를 얻을 수 있는지 조사합니다.

### <a name="decide-how-to-handle-dashboard-conversions"></a>대시보드 변환 처리 방법 결정

BI 업계에서 대시보드는 단일 페이지에 주요 메트릭을 표시하는 시각적 개체의 컬렉션입니다. 그러나 Power BI에서 대시보드는 Power BI 서비스에서만 만들 수 있는 특정 시각화 기능을 나타냅니다. 레거시 BI 플랫폼에서 대시보드를 마이그레이션하는 경우 다음과 같은 두 가지 선택 옵션이 있습니다.

1. 레거시 대시보드는 Power BI ‘보고서’로 다시 만들 수 있습니다. 대부분의 보고서는 Power BI Desktop으로 만듭니다. 페이지를 매긴 보고서와 Excel 보고서는 대체 옵션이기도 합니다.
2. 레거시 대시보드는 Power BI ‘대시보드’로 다시 만들 수 있습니다. [대시보드](../fundamentals/service-basic-concepts.md#dashboards)는 Power BI 서비스의 시각화 기능입니다. 일반적으로 대시보드 시각적 개체는 하나 이상의 보고서, Q&A 또는 빠른 인사이트에서 시각적 개체를 고정하여 만듭니다.

> [!TIP]
> 대시보드는 Power BI 콘텐츠 형식이므로 보고서 또는 대시보드 이름에 ‘대시보드’라는 단어를 사용하지 않는 것이 좋습니다.

### <a name="focus-on-the-big-picture-when-recreating-visuals"></a>시각적 개체를 다시 만드는 경우 넓은 시각에 집중

모든 BI 도구에는 장점 및 주요 영역이 있습니다. 따라서 레거시 BI 플랫폼에서 사용하는 정확한 보고서 시각적 개체는 Power BI에 비슷한 해당 항목이 없을 수 있습니다.

보고서 시각적 개체를 다시 만드는 경우 보고서에서 처리 중인 넓은 시각의 비즈니스 질문에 더 집중합니다. 이렇게 하면 모든 시각적 개체의 디자인을 정확히 동일한 방식으로 복제해야 하는 압력이 제거됩니다. 마이그레이션된 보고서를 사용하는 경우 콘텐츠 소비자는 일관성을 인정하지만 사소한 세부 정보에 관한 시간이 걸리는 논쟁에 휘말리지 않는 것이 중요합니다.

## <a name="next-steps"></a>다음 단계

[Power BI 마이그레이션 시리즈의 다음 문서](powerbi-migration-create-validate-content.md)에서는 Power BI로 마이그레이션할 때 콘텐츠 만들기 및 유효성 검사에 관련된 4단계를 알아봅니다.

기타 유용한 리소스는 다음과 같습니다.

- [Microsoft의 BI 변환](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI 엔터프라이즈 배포 계획 백서](https://aka.ms/PBIEnterpriseDeploymentWP)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)

조직에서 마이그레이션 프로세스를 성공적으로 완료하는 데 도움을 줄 숙련된 Power BI 파트너와 협력할 수 있습니다. Power BI 파트너와 협력하려면 [Power BI 파트너 포털](https://powerbi.microsoft.com/partners/)을 방문하세요.
