---
title: Power BI 마이그레이션 개요
description: 또 다른 타사 BI 도구에서 Power BI로 마이그레이션을 계획하고 수행하는 방법을 알아봅니다.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 8f8e58f61d2baa66cd0baf351857656588cfbe9f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419248"
---
# <a name="power-bi-migration-overview"></a>Power BI 마이그레이션 개요

고객들은 Power BI를 기반으로 점점 더 표준화하여 관리형 SSBI(셀프 서비스 비즈니스 인텔리전스)를 지원하고, 엔터프라이즈 BI 제공을 합리화하며, 경제적 압력을 해결하는 데이터 문화를 추진하고 있습니다. 이 Power BI 마이그레이션 문서 시리즈의 목표는 타사 BI 도구에서 Power BI로 마이그레이션을 계획하고 수행하는 방법에 관한 지침을 제공하는 것입니다.

Power BI 마이그레이션 시리즈의 문서는 다음과 같습니다.

1. Power BI 마이그레이션 개요(이 문서)
1. [Power BI로 마이그레이션 준비](powerbi-migration-pre-migration-steps.md)
1. [Power BI로 마이그레이션하기 위한 요구 사항 수집(1단계)](powerbi-migration-requirements.md)
1. [Power BI로 마이그레이션하기 위해 배포 계획(2단계)](powerbi-migration-planning.md)
1. [Power BI로 마이그레이션하기 위해 개념 증명 수행(3단계)](powerbi-migration-proof-of-concept.md)
1. [Power BI로 마이그레이션할 콘텐츠 만들기(4단계)](powerbi-migration-create-validate-content.md)
1. [Power BI에 배포(5단계)](powerbi-migration-deploy-support-monitor.md)
1. [고객 Power BI 마이그레이션을 통해 배우기](powerbi-migration-learn-from-customers.md)

다음과 같은 두 가지 가정이 적용됩니다. 조직에 현재 레거시 BI 플랫폼이 있으며 공식적으로 콘텐츠 및 사용자를 마이그레이션하도록 결정했습니다. 시리즈에서는 Power BI 서비스로 마이그레이션하는 작업을 중점적으로 다룹니다. 문서 시리즈에서 설명한 내용 이외에 국가별 클라우드 고객을 위해 추가적인 고려 사항이 적용될 수 있습니다.

다음 다이어그램은 조직에서 Power BI를 배포하기 위한 개략적인 4개 단계를 보여 줍니다.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-high-level-overview.png" alt-text="다음 표에서 설명하는 개략적인 4개 단계를 보여 주는 이미지.":::

|단계|설명|
|--------|-----------|
|![1단계.](media/common/icon-01-red-30x30.png)|**Power BI를 설정 및 평가합니다.** 첫 단계에는 초기 Power BI 아키텍처 설정이 포함됩니다. 이때 예비 배포 및 거버넌스 계획이 처리되며 투자 수익률 및/또는 비용 혜택 분석을 포함한 Power BI 평가도 처리됩니다.|
|![단계 2:](media/common/icon-02-red-30x30.png)|**Power BI에서 빠르게 새 솔루션을 만듭니다.** 두 번째 단계에서 셀프 서비스 BI 작성자는 요구 사항을 위해 Power BI 사용 및 평가를 시작할 수 있으며 Power BI에서 빠르게 가치를 얻을 수 있습니다. 2단계의 활동은 Power BI와 같은 새로운 BI 도구를 선택하기 위해 승인을 얻는 데 중요한 민첩성 및 신속한 비즈니스 가치에 역점을 둡니다. 따라서 다이어그램에서는 2단계의 활동을 3단계의 마이그레이션 활동과 나란히 보여 줍니다.|
|![3단계.](media/common/icon-03-red-30x30.png)|**레거시 플랫폼에서 Power BI로 BI 자산을 마이그레이션합니다.** 세 번째 단계에서는 Power BI로 마이그레이션을 처리합니다. 이 단계는 Power BI 마이그레이션 문서 시리즈의 중점적인 내용입니다. 다음 섹션에서는 5개 특정 마이그레이션 단계를 설명합니다.|
|![4단계.](media/common/icon-04-red-30x30.png)|**Power BI를 채택, 관리, 모니터링합니다.** 마지막 단계는 데이터 문화 조성, 통신, 교육과 같은 지속적인 활동으로 구성됩니다. 해당 활동은 효과적인 Power BI 구현에 크게 영향을 줍니다. 조직에 적합한 거버넌스 및 보안 정책과 프로세스뿐만 아니라 스케일링, 확장 및 지속적인 개선을 위한 감사 및 모니터링이 있어야 합니다.|

> [!IMPORTANT]
> 공식적인 Power BI로 마이그레이션은 거의 항상 새로운 Power BI 솔루션 개발과 병렬로 수행됩니다. _Power BI 솔루션_ 은 데이터 및 보고서 사용을 둘 다 포함하는 일반적인 용어입니다. 단일 Power BI Desktop(.pbix) 파일에는 데이터 모델 또는 보고서가 포함되거나 둘 다 포함될 수 있습니다. 데이터를 다시 사용할 수 있도록 [보고서에서 데이터 모델을 분리](../guidance/report-separate-from-model.md)하는 것이 좋지만 필수는 아닙니다.
>
> 공식적인 마이그레이션을 계획하고 수행하는 동안 새 요구 사항을 작성하는 데 Power BI를 사용하면 승인을 받는 데 도움이 됩니다. 동시 단계는 콘텐츠 작성자에게 Power BI를 통한 실용적인 실제 환경을 제공합니다.

## <a name="five-stages-of-a-power-bi-migration"></a>Power BI 마이그레이션의 5개 단계

다이어그램의 3단계에서는 Power BI로 마이그레이션을 처리합니다. 이 단계에는 5개 일반적인 단계가 있습니다.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-five-stages.png" alt-text="다음에 설명되는 Power BI 마이그레이션의 단계를 보여 주는 이미지.":::

이전 다이어그램에 표시된 후속 단계는 다음과 같습니다.

- [마이그레이션 전 단계](#pre-migration-steps)
- [1단계: 요구 사항 수집 및 우선 순위 지정](#stage-1-gather-requirements-and-prioritize)
- [2단계: 배포 계획](#stage-2-plan-for-deployment)
- [3단계: 개념 증명 수행](#stage-3-conduct-proof-of-concept)
- [4단계: 콘텐츠 만들기 및 유효성 검사](#stage-4-create-and-validate-content)
- [5단계: 배포, 지원 및 모니터링](#stage-5-deploy-support-and-monitor)

### <a name="pre-migration-steps"></a>마이그레이션 전 단계

마이그레이션 전 단계에는 레거시 BI 플랫폼에서 Power BI로 콘텐츠를 마이그레이션하는 프로젝트를 시작하기 전에 고려할 수 있는 작업이 포함됩니다. 일반적으로 초기 테넌트 수준 배포 계획이 포함됩니다. 해당 활동에 관한 자세한 내용은 [Power BI로 마이그레이션 준비](powerbi-migration-pre-migration-steps.md)를 참조하세요.

### <a name="stage-1-gather-requirements-and-prioritize"></a>1단계: 요구 사항 수집 및 우선 순위 지정

1단계는 정보를 수집하고 단일 솔루션의 마이그레이션을 계획하는 데 초점을 맞춥니다. 이 프로세스는 반복적이며 적절한 규모의 활동으로 범위가 지정되어야 합니다. 1단계의 산출물에는 마이그레이션할 보고서 및 데이터의 우선 순위가 지정된 인벤토리가 포함됩니다. 활동 수준을 완벽하게 예측하려면 2단계 및 3단계의 추가 활동이 필요합니다. 1단계의 활동에 관한 자세한 내용은 [Power BI로 마이그레이션하기 위한 요구 사항 수집](powerbi-migration-requirements.md)을 참조하세요.

### <a name="stage-2-plan-for-deployment"></a>2단계: 배포 계획

2단계는 각 특정 솔루션을 위해 1단계에서 정의된 요구 사항을 충족하는 방법에 초점을 맞춥니다. 2단계의 산출물에는 반복적인 비선형 프로세스이지만 프로세스를 안내하기 위해 최대한 많은 세부 정보가 포함됩니다. 개념 증명 만들기(3단계)는 이 단계와 병렬로 수행될 수 있습니다. 솔루션을 만드는 동안(4단계)에도 배포 계획 결정에 영향을 주는 추가 정보가 알려질 수 있습니다. 2단계의 해당 배포 계획 유형에서는 솔루션 수준에 초점을 맞추지만 이미 조직 수준에서 내린 결정을 준수합니다. 2단계의 활동에 관한 자세한 내용은 [Power BI로 마이그레이션하기 위해 배포 계획](powerbi-migration-planning.md)을 참조하세요.

### <a name="stage-3-conduct-proof-of-concept"></a>3단계: 개념 증명 수행

3단계는 최대한 빨리 미지의 상태를 해결하고 위험을 완화하는 데 초점을 맞춥니다. 기술적인 POC(개념 증명)는 가정의 유효성을 검사하는 데 유용하며 배포 계획(2단계)과 함께 반복해서 수행될 수 있습니다. 이 단계의 산출물은 범위가 좁은 Power BI 솔루션입니다. POC를 삭제 가능한 작업으로 의도하는 것은 아닙니다. 그러나 프로덕션 환경에서 사용할 수 있게 하려면 4단계에서 추가 작업이 필요할 수 있습니다. 이 점에 있어서, 조직에서 해당 활동을 프로토타입, 파일럿, 모형, 빠른 시작 또는 MVP(Minimally Viable Product)로 참조할 수 있습니다. POC 수행이 항상 필요한 것은 아니며 비공식적으로 수행될 수 있습니다. 3단계의 활동에 관한 자세한 내용은 [Power BI로 마이그레이션하기 위해 개념 증명 수행](powerbi-migration-proof-of-concept.md)을 참조하세요.

### <a name="stage-4-create-and-validate-content"></a>4단계: 콘텐츠 만들기 및 유효성 검사

4단계는 POC를 프로덕션에서 사용할 수 있는 솔루션으로 변환하는 실제 작업이 수행되는 경우입니다. 이 단계의 산출물은 개발 환경에서 유효성이 검사된 완료된 Power BI 솔루션입니다. 5단계에서 배포할 준비가 된 것입니다. 4단계의 활동에 관한 자세한 내용은 [Power BI로 마이그레이션할 콘텐츠 만들기](powerbi-migration-create-validate-content.md)를 참조하세요.

### <a name="stage-5-deploy-support-and-monitor"></a>5단계: 배포, 지원 및 모니터링

5단계에서는 주로 새 Power BI 솔루션을 프로덕션 환경에 배포하는 작업에 초점을 맞춥니다. 이 단계의 산출물은 비즈니스 사용자가 활발히 사용하는 프로덕션 솔루션입니다. Agile 방법론을 사용하는 경우 향후 반복에서 제공될 몇 가지 계획된 개선 사항이 포함될 수 있습니다. 위험 및 사용자 중단 최소화와 같이 Power BI를 편하게 사용하는 수준에 따라 단계별 배포를 수행할 수 있습니다. 또는 처음에 더 작은 파일럿 사용자 그룹에 배포할 수 있습니다. 이 단계와 이후 단계에서는 지원 및 모니터링도 중요합니다. 5단계의 활동에 관한 자세한 내용은 [Power BI로 마이그레이션](powerbi-migration-deploy-support-monitor.md)을 참조하세요.

> [!TIP]
> Power BI 마이그레이션 문서 시리즈에서 설명하는 대부분 개념은 표준 Power BI 구현 프로젝트에도 적용됩니다.

## <a name="consider-migration-reasons"></a>마이그레이션 이유 고려

생산성이 높고 정상적인 데이터 문화를 사용하는 것은 대부분 조직의 주요 목표입니다. Power BI는 해당 목표를 용이하게 하는 뛰어난 도구입니다. Power BI로 마이그레이션을 고려할 수 있는 세 가지 일반적인 이유는 다음과 같이 정리할 수 있습니다.

- 셀프 서비스 BI 사용자 커뮤니티의 역량을 강화하는 새로운 기능을 도입하여 **관리형 셀프 서비스 BI를 사용** 할 수 있습니다. Power BI를 사용하면 더 광범위하게 사용 가능한 정보 및 의사 결정에 액세스할 수 있는 반면, 찾기가 어려울 수 있는 전문가 기술에 덜 의존할 수 있습니다.
- 기존 BI 도구로 처리되지 않는 요구 사항을 충족하도록 **엔터프라이즈 BI 제공을 합리화** 하는 반면, 복잡성 수준이 감소하고, 소유 비용이 감소하며, 현재 사용 중인 여러 BI 도구에서 표준화됩니다.
- 더 적은 리소스, 시간 및 인력을 사용하여 생산성을 높이기 위해 **경제적 압력을 해결** 합니다.

## <a name="achieve-power-bi-migration-success"></a>Power BI 마이그레이션 달성

마이그레이션마다 약간의 차이가 있습니다. 조직 구조, 데이터 전략, 데이터 관리 완성도 및 조직 목표에 따라 달라질 수 있습니다. 그러나 Power BI 마이그레이션을 달성하는 고객에게서 일관되게 확인되는 몇 가지 사례가 있습니다.

- **경영진의 지원:** 프로세스 초기에 경영진 스폰서를 식별합니다. 해당 스폰서는 조직에서 BI를 적극적으로 지원하고 마이그레이션의 긍정적인 결과를 달성하기 위해 개인적으로 투자하는 사람이어야 합니다. 경영진 스폰서는 Power BI에 관련된 결과를 위한 궁극적인 권한 및 책임을 보유합니다.
- **교육, 지원 및 통신:** 기술 이니셔티브를 넘어서는 것임을 인식합니다. 모든 BI 또는 분석 프로젝트도 사람 이니셔티브이므로 사용자 교육 및 지원 초기에 투자하는 것이 좋습니다. 또한 모든 관련자에게 발생하는 상황, 이유를 투명하게 설명하고 현실적인 기대치를 설정하는 통신 계획을 만듭니다. 관련자의 입력을 캡처하려면 통신 계획에 피드백 루프를 포함해야 합니다.
- **빠른 성과:** 처음에는 실질적인 비즈니스 가치가 있고 긴급한 중요 항목을 우선적으로 처리합니다. 항상 레거시 BI 플랫폼에 표시되는 대로 정확하게 보고서를 마이그레이션하는 것보다는, 다시 디자인된 보고서를 처리할 때 수행할 작업을 포함하여 보고서에서 답변하려는 비즈니스 질문에 초점을 맞춥니다.
- **현대화 및 개선 사항:** 항상 작업을 수행했던 방법을 다시 생각해 봅니다. 마이그레이션은 상황을 개선할 기회를 제공할 수 있습니다. 예를 들어 마이그레이션이 수동 데이터 준비를 제거하거나 단일 보고서로 한정된 비즈니스 규칙을 재배치할 수 있습니다. 활동이 정당화될 수 있는 경우 기존 솔루션을 리팩터링, 현대화 및 통합하는 것이 좋습니다. 여러 보고서를 하나로 통합하거나 한동안 사용되지 않은 레거시 아티팩트를 제거하는 작업이 포함될 수 있습니다.
- **지속적인 학습:** 지속적으로 학습하고 적응하면서 단계적 접근 방식을 사용할 준비를 합니다. 짧고 반복적인 주기로 작업해서 신속하게 가치를 이끌어냅니다. 알 수 없는 위험을 최소화하고, 가정의 유효성을 검사하고, 새로운 기능을 알아보기 위해 작은 POC를 완료하는 사례를 자주 수행합니다. Power BI는 매월 업데이트되는 클라우드 서비스이므로 최신 개발 정보를 계속 파악하고 해당하는 경우 과정을 조정하는 것이 중요합니다.
- **변경에 대한 저항:** 변경에 대한 저항 수준이 다양할 수 있으며 일부 사용자가 새로운 도구 학습에 저항한다는 것을 이해합니다. 또한 다른 BI 도구에 관한 전문 지식을 얻기 위해 상당한 시간과 노력을 바친 일부 전문가는 대체되는 것에 위협을 느낄 수 있습니다. 특히 고도로 분권화된 조직에서는 내부 정치 싸움이 발생할 수 있으므로 대비하세요.
- **제약 조건:** 자금 조달, 시간 예측뿐 아니라 관련된 모든 사람의 역할 및 책임을 포함하여 마이그레이션 계획을 현실적으로 고려합니다.

## <a name="acknowledgments"></a>승인

이 문서 시리즈는 Data Platform MVP 및 [Coates Data Strategies](https://www.coatesdatastrategies.com/)의 소유주인 Melissa Coates가 작성했습니다. 기고자 및 검토자에는 Marc Reguera, Venkatesh Titte, Patrick Baumgartner, Tamer Farag, Richard Tkachuk, Matthew Roche, Adam Saxton, Chris Webb, Mark Vaillancourt, Daniel Rubiolo, David Iseminger 및 Peter Myers가 포함됩니다.

## <a name="next-steps"></a>다음 단계

[Power BI 마이그레이션 시리즈의 다음 문서](powerbi-migration-pre-migration-steps.md)에서는 Power BI로 마이그레이션하는 경우 마이그레이션 전 단계를 알아봅니다.

기타 유용한 리소스는 다음과 같습니다.

- [Microsoft의 BI 변환](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI 엔터프라이즈 배포 계획 백서](https://aka.ms/PBIEnterpriseDeploymentWP)
- [SSRS 보고서를 Power BI로 마이그레이션](migrate-ssrs-reports-to-power-bi.md)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)

조직에서 마이그레이션 프로세스를 성공적으로 완료하는 데 도움을 줄 숙련된 Power BI 파트너와 협력할 수 있습니다. Power BI 파트너와 협력하려면 [Power BI 파트너 포털](https://powerbi.microsoft.com/partners/)을 방문하세요.
