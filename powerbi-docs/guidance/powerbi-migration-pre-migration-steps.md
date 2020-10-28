---
title: Power BI로 마이그레이션 준비
description: Power BI로 마이그레이션하는 경우 마이그레이션 전 단계에 관한 지침입니다.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 01d1e48537b2d373be3897259f8ac6e97886f268
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92680967"
---
# <a name="prepare-to-migrate-to-power-bi"></a>Power BI로 마이그레이션 준비

이 문서에서는 Power BI로 마이그레이션하기 전에 고려할 수 있는 작업을 설명합니다.

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="Power BI 마이그레이션의 단계를 보여 주는 이미지. 이 문서에서는 마이그레이션 전 단계가 강조됩니다.":::

> [!NOTE]
> 위의 그래픽에 관한 전체 설명은 [Power BI 마이그레이션 개요](powerbi-migration-overview.md)를 참조하세요.

마이그레이션 전 단계는 5개 마이그레이션 단계를 진행하기 전에 중요한 준비를 나타내는 사전 계획을 강조합니다. 더 큰 조직의 경우 각 사업부 또는 부서 영역에서 일부 부분이 반복될 수 있지만 대부분의 마이그레이션 전 단계는 한 번 수행됩니다.

마이그레이션 전 단계의 산출물에는 초기 거버넌스 모델, 초기 개략적인 배포 계획 및 마이그레이션할 보고서 및 데이터의 인벤토리가 포함됩니다. 개별 솔루션을 마이그레이션하기 위한 활동 수준을 완전히 예측하려면 1, 2 및 3단계 활동의 추가 정보가 필요합니다.

> [!TIP]
> 문서에서 설명하는 대부분의 항목은 표준 Power BI 구현 프로젝트에도 적용됩니다.

## <a name="create-costbenefit-analysis-and-evaluation"></a>비용/혜택 분석 및 평가 만들기

초기 평가 중에 몇 가지 주요 고려 사항은 다음과 같습니다.

- 원하는 특정 미래 상태에 도달하기 위해 비즈니스 사례 및 BI 전략에 관한 명확성
- 성공의 의미 및 마이그레이션 이니셔티브의 진행률 및 성공 여부를 측정하는 방법에 관한 명확성
- 비용 예측 및 ROI(투자 수익률) 계산 결과
- 범위 및 복잡성 수준이 더 작은 몇 가지 생산성이 높은 Power BI 이니셔티브의 성공적인 결과

## <a name="identify-stakeholders-and-executive-support"></a>관련자 및 경영진 지원 식별

관련자를 식별하기 위한 몇 가지 고려 사항은 다음과 같습니다.

- 비즈니스 사례 및 BI 전략에서 관련자와 협력을 보장합니다.
- 해당 콘텐츠의 마이그레이션이 이후 일정에 따라 착수되는 경우에도 동기화 우려 사항을 파악하기 위해 사업부 전체의 담당자를 포함합니다.
- 초기에 Power BI 챔피언을 참여시킵니다.
- 관련자와 함께 통신 계획을 만들고 따릅니다.

> [!TIP]
> 과도한 통신을 시작하는 것을 두려워하는 경우 이 방법이 적합할 수 있습니다.

## <a name="generate-initial-governance-model"></a>초기 거버넌스 모델 생성

Power BI 구현 초기에 해결할 몇 가지 주요 항목은 다음과 같습니다.

- Power BI를 채택하는 경우 및 Power BI가 조직의 전체 BI 전략에 맞는 경우의 특정 목표
- 특히 분권화된 조직에서 Power BI 관리자 역할을 처리하는 방법
- 신뢰할 수 있는 데이터 취득과 관련된 정책: 신뢰할 수 있는 데이터 원본 사용, 데이터 품질 문제 해결 및 일관된 용어 및 공통 정의 사용
- 내부 및 외부 사용자에게 데이터 원본, 데이터 모델, 보고서 및 콘텐츠를 전송하기 위한 보안 및 데이터 프라이버시 전략
- 내부 및 외부 규정 준수, 규정 및 감사 요구 사항을 충족하는 방법

> [!IMPORTANT]
> 가장 효과적인 거버넌스 모델은 필요한 제어 수준과 사용자 역량의 규형을 맞추는 것입니다. 자세한 내용을 확인하고 [코어의 관리](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) 및 [에지의 유연성](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)을 참조하세요.

## <a name="conduct-initial-deployment-planning"></a>초기 배포 계획 수행

초기 배포 계획에는 조직의 Power BI 구현을 위한 표준, 정책 및 기본 설정 정의가 포함됩니다.

[2단계](powerbi-migration-planning.md)는 솔루션 수준 배포 계획을 참조합니다. 2단계 활동은 가능하면 항상 조직 수준 결정을 따라야 합니다.

Power BI 구현 초기에 처리할 일부 중요한 항목은 다음과 같습니다.

- 문서화해야 하는 [Power BI 테넌트 설정](admin-tenant-settings.md) 결정 사항.
- 문서화해야 하는 [작업 영역 관리](../collaborate-share/service-new-workspaces.md) 결정
- 앱, 작업 영역, 공유, 구독 및 콘텐츠 포함과 같은 데이터 및 [콘텐츠 배포 방법](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md)과 관련된 고려 사항 및 기본 설정
- 가져오기 모드 또는 DirectQuery 모드를 사용하거나 [복합 모델](composite-model-guidance.md)에서 두 모드를 결합하는 것과 같이 [데이터 세트 모드](../connect-data/service-dataset-modes-understand.md)와 관련된 기본 설정
- [데이터 및 액세스 보호](../admin/service-admin-power-bi-security.md)
- 재사용 가능성을 위해 [공유 데이터 세트](../connect-data/service-datasets-share.md) 사용
- 신뢰할 수 있는 데이터 사용을 촉진하기 위해 [데이터 인증](../collaborate-share/service-endorsement-overview.md) 적용
- 다양한 사용 사례 또는 사업부의 Power BI 보고서, Excel 보고서 또는 페이지를 매긴 보고서를 포함한 다양한 [보고서 유형](../create-reports/index.yml) 사용
- 중앙 집중화된 BI 아티팩트 및 비즈니스 관리형 BI 아티팩트를 관리하기 위한 변경 관리 접근 방식
- 소비자, 데이터 모델러, 보고서 작성자 및 관리자를 위한 학습 계획
- [Power BI Desktop 템플릿](../create-reports/desktop-templates.md), [사용자 지정 시각적 개체](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/) 및 문서화된 보고서 디자인 표준을 사용하여 콘텐츠 작성자 지원
- 새 라이선스 요청, 새 게이트웨이 데이터 원본 추가, 게이트웨이 데이터 원본에 대한 권한 얻기, 새 작업 영역 요청, 작업 영역 권한 변경 및 정기적으로 발생할 수 있는 기타 일반적인 요구 사항과 같은 사용자 요구 사항을 관리하기 위한 절차 및 프로세스

> [!IMPORTANT]
> 배포 계획은 반복적인 프로세스입니다. 배포 결정은 Power BI를 사용하는 조직 환경이 성장하고 Power BI가 진화함에 따라 여러 번 구체화 및 보강됩니다. 이 프로세스 중에 결정된 사항은 마이그레이션 프로세스의 [2단계](powerbi-migration-planning.md)에서 설명하는 솔루션 수준 배포 계획 중에 사용됩니다.

## <a name="establish-initial-architecture"></a>초기 아키텍처 설정

[BI 솔루션 아키텍처](center-of-excellence-business-intelligence-solution-architecture.md)는 시간이 지남에 따라 발전하고 숙성됩니다. 즉시 처리할 Power BI 설정 작업은 다음과 같습니다.

- Power BI 테넌트 설정 Azure Active Directory와 통합
- [Power BI 관리자](../admin/service-admin-role.md) 정의
- 초기 [사용자 라이선스](../admin/service-admin-licensing-organization.md) 구매 및 할당
- [Power BI 테넌트 설정](admin-tenant-settings.md)을 구성하고 검토합니다.
- [작업 영역 역할](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) 설정 및 Azure Active Directory 보안 그룹과 사용자에게 액세스 권한 할당
- 정기적인 업데이트 계획을 통해 초기 [데이터 게이트웨이](../connect-data/service-gateway-deployment-guidance.md) 클러스터 구성
- 초기 [프리미엄 용량 라이선스](../admin/service-admin-premium-purchase.md) 구매(해당하는 경우)
- 지속적인 관리 계획을 통해 [프리미엄 용량 워크로드](../admin/service-admin-premium-workloads.md) 구성

## <a name="define-success-criteria-for-migration"></a>마이그레이션의 성공 조건 정의

첫 번째 작업은 개별 솔루션 마이그레이션의 성공이 무엇인지 이해하는 것입니다. 질문할 수 있는 내용은 다음과 같습니다.

- **마이그레이션의 특정 동기 및 목표는 무엇인가요?** 자세한 내용은 [Power BI 마이그레이션 개요(마이그레이션 이유 고려)](powerbi-migration-overview.md#consider-migration-reasons)를 참조하세요. 이 문서에서는 Power BI로 마이그레이션하는 가장 일반적인 이유를 설명합니다. 물론, 목표는 조직 수준에서 지정해야 합니다. 그 외에도 하나의 레거시 BI 솔루션 마이그레이션은 비용 절감 면에서 큰 이점이 있을 수 있지만, 다른 레거시 BI 솔루션 마이그레이션은 워크플로 최적화 혜택을 얻는 데 집중할 수 있습니다.
- **마이그레이션의 예상 비용/혜택 또는 ROI는 무엇인가요?** 비용, 기능 증가, 복잡성 감소 또는 민첩성 향상에 관련된 기대치를 분명히 파악하면 성공 여부를 측정하는 데 도움이 됩니다. 마이그레이션 프로세스 중에 결정을 내리는 데 도움이 되는 기본 원칙을 제공할 수 있습니다.
- **성공 여부를 측정하는 데 사용되는 KPI(핵심 성과 지표)는 무엇인가요?** 다음 목록은 몇 가지 예제 KPI를 제공합니다.
    - 전월 대비 감소하는 레거시 BI 플랫폼에서 렌더링된 보고서 수
    - 전월 대비 증가하는 Power BI에서 렌더링된 보고서 수
    - 전분기 대비 증가하는 Power BI 보고서 소비자 수
    - 목표 날짜까지 프로덕션 환경으로 마이그레이션된 보고서 백분율
    - 전년 대비 라이선스 비용의 비용 절감

> [!TIP]
> [Power BI 활동 로그](../admin/service-admin-auditing.md)를 KPI 진행률 측정을 위한 원본으로 사용할 수 있습니다.

## <a name="prepare-inventory-of-existing-reports"></a>기존 보고서의 인벤토리 준비

레거시 BI 플랫폼에서 기존 보고서의 인벤토리를 준비하는 것은 이미 존재하는 항목을 이해하기 위한 중요한 단계입니다. 이 단계의 결과는 마이그레이션 활동 수준 평가에 대한 입력입니다. 인벤토리 준비와 관련된 활동은 다음과 같습니다.

1. **보고서 인벤토리:** 마이그레이션 후보인 보고서 및 대시보드 목록을 컴파일합니다.
2. **데이터 원본 인벤토리:** 기존 보고서에서 액세스하는 모든 데이터 원본 목록을 컴파일합니다. 엔터프라이즈 데이터 원본뿐 아니라 부서별 및 개인 데이터 원본도 둘 다 포함해야 합니다. 이 프로세스를 통해 이전에 IT 부서에 알려지지 않은 데이터 원본을 찾아낼 수 있으며, 이를 ‘섀도 IT’라고 합니다.
3. **감사 로그:** 사용 패턴을 이해하고 우선 순위 지정을 지원하기 위해 레거시 BI 플랫폼 감사 로그의 데이터를 가져옵니다. 감사 로그에서 얻을 수 있는 중요한 정보는 다음과 같습니다.
    - 주별/월별/분기별 각 보고서가 실행된 평균 횟수
    - 주별/월별/분기별 보고서당 평균 소비자 수
    - 각 보고서, 특히 경영진이 사용하는 보고서의 소비자
    - 각 보고서가 실행된 가장 최근 날짜

> [!NOTE]
> 대부분의 경우 콘텐츠는 있는 그대로 Power BI로 마이그레이션되지 않습니다. 마이그레이션은 데이터 아키텍처를 다시 디자인하고/하거나 보고서 전송을 개선할 기회를 나타냅니다. 어떤 리팩터링을 수행해야 하는지 평가를 시작할 수 있도록 현재 존재하는 항목을 이해하려면 보고서 인벤토리를 컴파일하는 것이 중요합니다. 이 시리즈의 나머지 문서에서는 개선 사항을 더 자세히 설명합니다.

## <a name="explore-automation-options"></a>자동화 옵션 살펴보기

엔드투엔드 Power BI 변환 프로세스를 완전히 자동화할 수는 없습니다.

자동으로 작업을 수행할 수 있는 기존 도구가 있는 경우 데이터 및 보고서의 기존 인벤토리를 컴파일하는 작업을 자동화할 수 있습니다. 기존 인벤토리 컴파일과 같이 마이그레이션 프로세스의 일부에 사용할 수 있는 자동화의 범위는 보유한 도구에 따라 달라집니다.

## <a name="next-steps"></a>다음 단계

[Power BI 마이그레이션 시리즈의 다음 문서](powerbi-migration-requirements.md)에서는 Power BI로 마이그레이션할 때 요구 사항 수집 및 우선 순위 지정에 관련된 1단계를 알아봅니다.

기타 유용한 리소스는 다음과 같습니다.

- [Microsoft의 BI 변환](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI 엔터프라이즈 배포 계획 백서](https://aka.ms/PBIEnterpriseDeploymentWP)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)

조직에서 마이그레이션 프로세스를 성공적으로 완료하는 데 도움을 줄 숙련된 Power BI 파트너와 협력할 수 있습니다. Power BI 파트너와 협력하려면 [Power BI 파트너 포털](https://powerbi.microsoft.com/partners/)을 방문하세요.
