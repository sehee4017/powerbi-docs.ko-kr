---
title: 최고 전문가 조직 설정
description: 최고 전문가 조직을 통해 Microsoft가 표준화된 분석 및 데이터 플랫폼을 만들어 올바른 운영 모델, 관련자 참여, 공유 및 전용 투자를 통해 인사이트를 활용하는 방법을 알아보세요.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: v-pemyer
ms.openlocfilehash: 477b6a1e29fc05da3004a2dcf8466ef969df4531
ms.sourcegitcommit: f73ea4b9116ad186817ec5cc5d5f487d49cc0cb0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88638615"
---
# <a name="establish-a-center-of-excellence"></a>최고 전문가 조직 설정

이 문서는 IT 전문가와 IT 관리자를 대상으로 합니다. 조직에서 BI 및 분석 COE(최고 전문가 조직)를 설정하는 방법과 Microsoft가 자체 BI 및 분석 COE(최고 전문가 조직)를 설정한 방법을 알아봅니다.

일각에서는 COE가 단순한 지원 센터라는 오해가 있는데, 이런 사고는 현실과 한참 동떨어진 것입니다.

일반적으로 BI 및 분석 COE는 BI 플랫폼의 설정과 유지 관리를 책임지는 전문가 팀입니다. 이 팀은 단일 데이터 소스를 만들고 인사이트를 활용하고 가속화할 일관된 회사 전체 메트릭 집합을 정의할 책임도 있습니다. 그러나 COE는 광범위한 용어입니다. 따라서 다양한 방법으로 구현 및 관리할 수 있으며, 그 구조와 범위는 조직마다 다를 수 있습니다. 그 핵심은 항상 적합한 사용자에게 적합한 데이터와 인사이트 기능을 제공하는 강력한 플랫폼에 대한 것입니다. 이상적으로는 전파, 교육, 지원도 촉진합니다 이를 Microsoft에서는 [코어의 관리](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)라고 하며 BI 플랫폼 및 단일 데이터 소스로 제공합니다.

대규모 조직에서는 핵심 COE가 위성 COE(종종 부서 수준)에 의해 ‘확장된’ 여러 COE를 찾을 수 있습니다. 이런 방식에서 위성 COE는 분류 및 정의에 익숙한 전문가 그룹으로서 핵심 데이터를 ‘해당 부서에 맞춰’ 의미 있는 데이터로 변환하는 방법을 알고 있습니다. 부서별 분석가는 핵심 데이터에 대한 사용 권한을 부여받고 자신의 보고서에 사용할 수 있도록 핵심 데이터를 신뢰합니다. 신중하게 준비된 핵심 차원, 팩트 및 비즈니스 논리에 의존하는 솔루션을 빌드합니다. 때로는 더 작은 규모의 부서별 데이터 세트 및 비즈니스 논리를 사용하여 확장할 수도 있습니다. 중요한 점은 위성 COE의 연결이 끊어지지 않으며 위성 COE가 개별적으로 작업하지 않는다는 것입니다. Microsoft에서 위성 COE는 [에지의 유연성](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)을 증진합니다.

이 확장된 시나리오가 성공하려면 부서는 ‘역할 참여를 위한 비용을 부담’해야 합니다. 다시 말해서, 부서는 핵심 COE에 재정적으로 투자해야 합니다. 이렇게 하면 부서들은 “공평한 몫을 받지 못하거나” 부서 요구 사항의 우선 순위가 낮게 지정되는 우려를 하지 않아도 됩니다.

이 시나리오를 지원하기 위해 핵심 COE는 자금이 지원되는 부서 요구 사항을 충족하도록 확장해야 합니다. 여러 데이터 세트를 온보딩한 후에는 규모의 경제가 개입됩니다. Microsoft에서는 중앙에서 작업하는 것이 보다 경제적이며 더 빠른 결과를 제공한다는 사실이 금세 명백해졌습니다. 각각의 새 주제 영역이 온보딩되자 Microsoft는 전체 플랫폼에서 활용과 기여를 가능하게 함으로써 기본 데이터 문화를 보강한 훨씬 더 큰 규모의 경제를 경험했습니다.

예제를 살펴보겠습니다. BI 플랫폼은 재무, 판매 및 마케팅을 위한 핵심 차원, 팩트 및 비즈니스 논리를 제공합니다. 또한 수백 개의 KPI(핵심 성과 지표)를 정의합니다. 이제 Power Platform 비즈니스의 분석가가 리더십 대시보드를 준비해야 합니다. 수익 및 파이프라인과 같은 일부 KPI는 BI 플랫폼에서 직접 제공지만 다른 KPI는 보다 세부적인 비즈니스 요구를 기반으로 합니다. 이러한 요구 사항 중 하나는 Power BI 관련 기능, 즉 데이터 흐름을 사용자가 채택하기 위한 KPI의 요구 사항입니다. 분석가는 핵심 BI 플랫폼 데이터를 부서 데이터와 통합할 Power BI [복합 모델](composite-model-guidance.md)을 생성합니다. 그런 다음 비즈니스 논리를 추가하여 부서별 KPI를 정의합니다. 마지막으로, 분석가는 로컬 지식과 데이터로 증폭된 회사 전체 COE 리소스를 활용하는 새로운 모델을 기반으로 리더십 대시보드를 작성합니다.

중요한 점은 핵심 COE와 위성 COE 사이의 책임 구분을 통해 부서별 분석가가 데이터 플랫폼 관리가 아니라 새로운 영역을 개척하는 데 집중할 수 있다는 점입니다. 경우에 따라 위성 COE와 핵심 COE 사이에 상호 이익이 되는 관계가 있을 수도 있습니다. 예를 들어 위성 COE는 부서에 도움이 되는 것으로 입증되었으며 결과적으로 전체 회사에 이익이 되는 핵심 메트릭으로서 핵심 COE에서 제공되고 지원되는 새 메트릭을 정의할 수도 있습니다.

## <a name="bi-platform"></a>BI 플랫폼

조직에서 COE는 BI 팀 또는 BI 그룹과 같이 다른 이름으로 인식될 수도 있습니다. 이름보다는 COE가 실제로 수행하는 일이 더 중요합니다. 형식화된 팀이 없는 경우 BI 플랫폼을 설정하도록 핵심 BI 전문가를 함께 모은 팀을 육성하는 것이 좋습니다.

Microsoft에서는 COE를 BI 플랫폼이라고 합니다. 여기에는 회사 내에서 재무, 판매, 마케팅 같은 다양한 부서를 나타내는 많은 관련자 그룹이 있습니다. [공유 기능](#shared-capabilities) 및 [전용 배달](#dedicated-deliveries)을 실행하도록 구성되어 있습니다.

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="다이어그램은 다음 섹션에서 설명하는 공유 기능 및 전용 배달을 보여 줍니다.":::

### <a name="shared-capabilities"></a>공유 기능

BI 플랫폼을 설정하고 운영하려면 공유 기능이 필요합니다. 공유 기능은 플랫폼 자금을 조달하는 모든 관련자 그룹을 지원합니다. 이러한 그룹은 다음 팀으로 구성됩니다.

- **핵심 플랫폼 엔지니어링:** 엔지니어링 마인드를 가지고 BI 플랫폼을 설계했습니다. BI 플랫폼은 데이터 수집, 데이터 보강 처리, 해당 데이터를 분석가가 사용하도록 BI 의미 체계 모델로 제공하도록 지원하는 프레임워크 세트입니다. 엔지니어는 핵심 BI 플랫폼 기능의 기술적 설계와 구현을 담당합니다. 예를 들어 데이터 파이프라인을 설계하고 구현합니다.
- **인프라 및 호스팅:** IT 엔지니어는 모든 Azure 서비스를 프로비전하고 관리하는 일을 담당합니다.
- **지원 및 운영:** 이 팀은 플랫폼을 계속 실행합니다. 지원 팀은 데이터 권한과 같은 사용자 요구 사항을 처리합니다. 운영 팀은 플랫폼을 계속 실행하며 실행 상태로 유지하고 Service Level Agreement(SLA, 서비스 수준 약정)를 충족하며 지연 또는 실패를 전달합니다.
- **릴리스 관리:** 기술 PM(프로그램 관리자) 릴리스 변경입니다. 변경은 플랫폼 프레임워크 업데이트부터 BI 의미 체계 모델에 대한 변경 요청까지 다양할 수 있습니다. 이러한 항목은 변경으로 인해 아무것도 손상되지 않도록 하는 마지막 방어선입니다.

### <a name="dedicated-deliveries"></a>전용 배달

각 관련자 그룹에 대한 전용 배달 팀이 있습니다. 이 팀은 일반적으로 데이터 엔지니어, 분석 엔지니어 및 기술 PM으로 구성되며 해당 자금은 모두 관련자 그룹이 조달합니다.

## <a name="bi-team-roles"></a>BI 팀 역할

Microsoft에서 BI 플랫폼은 확장성 있는 전문가 팀에 의해 운영됩니다. 팀은 전용 및 공유 리소스에 따라 배정됩니다. 현재 다음과 같은 역할이 있습니다.

- **프로그램 관리자:** PM은 전용 리소스입니다. BI 팀과 관련자 간의 기본 연락처 역할을 합니다. 관련자 비즈니스 요구 사항을 기술 사양으로 변환하는 일을 합니다. 또한 관련자 결과물의 우선 순위를 관리합니다.
- **데이터베이스 리드:** 중앙 집중식 데이터 웨어하우스에 새 데이터 세트를 온보딩하는 일을 담당하는 전용 리소스입니다. 데이터 세트를 온보딩하려면 일치하는 차원을 설정하고 비즈니스 논리와 사용자 지정 특성을 추가하고 표준 이름과 서식을 지정해야 할 수 있습니다.
- **분석 리드:** BI 의미 체계 모델 설계 및 디자인을 담당하는 전용 리소스입니다. 표준 명명 및 서식 지정을 사용하여 일관된 아키텍처를 적용하기 위해 노력합니다. 성능 최적화는 역할의 중요한 부분입니다.
- **작업 및 인프라:** 작업 및 데이터 파이프라인 관리를 담당하는 공유 리소스입니다. 또한 Azure 구독, Power BI 용량, 가상 머신 및 데이터 게이트웨이를 관리하는 일도 담당합니다.
- **지원:** 문서 작성, 교육 구성, BI 의미 체계 모델 변경 내용 전달, 사용자 질문에 대한 답변을 담당하는 공유 리소스입니다.

## <a name="governance-and-compliance"></a>거버넌스 및 규정 준수

각 관련자 그룹에 대해 PM 리드는 프로그램 간 거버넌스 및 감독을 제공합니다. 최우선의 목표는 IT 투자가 비즈니스 가치를 창출하고 위험을 완화하는 것입니다. 운영 위원회 모임을 정기적으로 열어 프로세스를 검토하고 주요 이니셔티브를 승인합니다.

## <a name="grow-your-own-community"></a>고유한 커뮤니티 확장

다음을 수행하여 조직 내에서 커뮤니티를 설정하고 확장합니다.

- 사용자가 질문하고, 제안하며, 아이디어를 공유하고, 항의할 수 있도록 BI 팀과 시간을 정하는 정기적인 “업무 시간” 이벤트를 포함합니다.
- Teams 채널을 만들어 지원을 제공하고 누구나 질문하고 게시된 질문에 응답하도록 권장합니다.
- 비공식적인 사용자 그룹을 실행하고 홍보하며 직원이 프레젠테이션 또는 참석하도록 권장합니다.
- 특정 제품 및 BI 플랫폼 자체에서 더 공식적인 학습 이벤트를 실행합니다. 무료 과정 키트로 제공되고 직원에게 처음으로 Power BI를 소개하는 좋은 방법인 [Power BI 대시보드 1일 실습](https://powerbi.microsoft.com/diad/)을 제공하는 것이 좋습니다.

## <a name="next-steps"></a>다음 단계

이 문서에 대한 자세한 내용은 다음 리소스를 참조하세요.

- [COE의 BI 솔루션 아키텍처](center-of-excellence-business-intelligence-solution-architecture.md)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)

[시리즈의 다음 문서](center-of-excellence-business-intelligence-solution-architecture.md)에서는 COE의 BI 솔루션 아키텍처 및 사용되는 다양한 기술에 대해 알아봅니다.

### <a name="professional-services"></a>전문 서비스

인증된 Power BI 파트너는 조직이 COE를 설정할 때 성공하도록 도와줄 수 있습니다. 비용 효율적인 학습 또는 데이터 감사를 제공할 수 있습니다. Power BI 파트너와 협력하려면 [Power BI 파트너 포털](https://powerbi.microsoft.com/partners/)을 방문하세요.

숙련된 컨설팅 파트너와 협업할 수도 있습니다. 해당 파트너는 Power BI를 [평가](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [고려](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) 또는 [구현](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1)하도록 도와줄 수 있습니다.
