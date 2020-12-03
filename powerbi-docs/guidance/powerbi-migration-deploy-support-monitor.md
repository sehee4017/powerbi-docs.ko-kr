---
title: Power BI에 배포
description: Power BI로 마이그레이션할 때 콘텐츠를 배포, 지원 및 모니터링하는 방법에 관한 지침입니다.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: bfa3ffad111c7ab819ed1269586a7b32ccf43bba
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419271"
---
# <a name="deploy-to-power-bi"></a>Power BI에 배포

이 문서에서는 Power BI로 마이그레이션할 때 콘텐츠를 배포, 지원 및 모니터링하는 작업과 관련된 **5단계** 를 설명합니다.

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="Power BI 마이그레이션의 단계를 보여 주는 이미지. 이 문서에서는 5단계가 강조됩니다.":::

> [!NOTE]
> 위의 그래픽에 관한 전체 설명은 [Power BI 마이그레이션 개요](powerbi-migration-overview.md)를 참조하세요.

5단계에서는 주로 새 Power BI 솔루션을 프로덕션 환경에 배포하는 작업에 초점을 맞춥니다.

이 단계의 산출물은 비즈니스에서 사용할 준비가 된 프로덕션 솔루션입니다. Agile 방법을 사용하는 경우 향후 반복에서 제공될 몇 가지 계획된 개선 사항이 포함될 수 있습니다. 이 단계와 이후 단계에서는 지원 및 모니터링도 중요합니다.

> [!TIP]
> 아래 설명된 병렬로 실행 및 레거시 보고서 해제를 제외하고, 문서에 설명된 항목은 표준 Power BI 구현 프로젝트에도 적용됩니다.

## <a name="deploy-to-test-environment"></a>테스트 환경에 배포

IT 관리형 솔루션 또는 비즈니스 생산성에 중요한 솔루션의 경우 일반적으로 테스트 환경이 있습니다. 테스트 환경은 개발과 프로덕션 사이에 있으며 모든 Power BI 솔루션에 필요한 것은 아닙니다. 테스트 작업 영역은 프로덕션 환경으로 릴리스되기 전에 UAT(사용자 승인 테스트)가 수행되도록 개발에서 분리된 안정적인 위치로 사용할 수 있습니다.

콘텐츠가 프리미엄 용량의 작업 영역에 게시된 경우 [배포 파이프라인](../create-reports/deployment-pipelines-overview.md)은 개발, 테스트 및 프로덕션 작업 영역에 대한 배포 프로세스를 간소화할 수 있습니다. 또는 수동으로 게시하거나 [PowerShell 스크립트](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/)로 게시할 수 있습니다.

### <a name="deploy-to-test-workspace"></a>테스트 작업 영역에 배포

일반적으로 테스트 작업 영역에 배포하는 동안 주요 활동은 다음과 같습니다.

- **연결 문자열 및 매개 변수:** 개발 및 테스트 간에 데이터 원본이 다른 경우 데이터 세트 연결 문자열을 조정합니다. [매개 변수화](../connect-data/service-parameters.md)를 사용하여 연결 문자열을 효과적으로 관리할 수 있습니다.
- **작업 영역 콘텐츠**: 테스트 작업 영역에 데이터 세트 및 보고서를 게시하고 대시보드를 만듭니다.
- **앱:** UAT 프로세스의 일부를 구성하는 경우 테스트 작업 영역의 콘텐츠를 사용하여 [앱](../consumer/end-user-apps.md)을 게시합니다. 일반적으로 앱 권한은 UAT와 관련된 소수의 사용자로 제한됩니다.
- **데이터 새로 고침:** UAT가 활발히 발생하는 기간 동안 데이터 세트 가져오기를 위해 [데이터 세트 새로 고침을 예약](../connect-data/refresh-scheduled-refresh.md)합니다.
- **보안:** [작업 영역 역할](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)을 업데이트하거나 확인합니다. 테스트 작업 영역 액세스에는 UAT와 관련된 소수의 사용자가 포함됩니다.

> [!NOTE]
> 개발, 테스트 및 프로덕션에 대한 배포 옵션에 관한 자세한 내용은 [Power BI 엔터프라이즈 배포 계획 백서](https://aka.ms/PBIEnterpriseDeploymentWP)의 섹션 9를 참조하세요.

### <a name="conduct-user-acceptance-testing"></a>사용자 승인 테스트 수행

일반적으로 UAT에는 실무 전문가인 비즈니스 사용자가 관련됩니다. 확인된 후 해당 사용자는 새 콘텐츠가 정확하고, 요구 사항을 충족하며, 다른 사용자가 더 널리 사용하도록 배포될 수 있다는 것을 승인합니다.

서면 승인을 포함하여 UAT 프로세스가 공식적인 범위는 변경 관리 사례에 따라 달라집니다.

## <a name="deploy-to-production-environment"></a>프로덕션 환경에 배포

프로덕션 환경에 배포하기 위해 고려해야 할 몇 가지 사항이 있습니다.

### <a name="conduct-a-staged-deployment"></a>단계적 배포 수행

위험 및 사용자 중단을 최소화하려는 경우 또는 다른 문제가 있는 경우 단계적 배포를 수행할 수 있습니다. 프로덕션에 대한 첫 번째 배포에는 더 작은 파일럿 사용자 그룹이 포함될 수 있습니다. 파일럿을 사용하면 파일럿 사용자의 피드백을 적극적으로 요청할 수 있습니다.

모든 대상 사용자가 새 Power BI 솔루션에 대한 권한을 가질 때까지 점진적으로 프로덕션 작업 영역 또는 앱에서 권한을 확장합니다.

> [!TIP]
> [Power BI 활동 로그](../admin/service-admin-auditing.md)를 사용하여 소비자가 새 Power BI 솔루션을 채택하고 사용하는 방법을 이해할 수 있습니다.

### <a name="handle-additional-components"></a>추가 구성 요소 처리

배포 프로세스 중에 Power BI 관리자와 협력하여 다음과 같이 전체 솔루션을 지원하는 데 필요한 다른 요구 사항을 해결해야 할 수 있습니다.

- **게이트웨이 유지 관리:** 데이터 게이트웨이의 [새 데이터 원본](../connect-data/service-gateway-data-sources.md) 등록이 필요할 수 있습니다.
- **게이트웨이 드라이버 및 커넥터:** 새로운 전용 데이터 원본을 사용하려면 게이트웨이 클러스터의 각 서버에 새 드라이버 또는 사용자 지정 커넥터를 설치해야 할 수 있습니다.
- **새 프리미엄 용량 만들기:** 기존 [프리미엄 용량](../admin/service-premium-capacity-manage.md)을 사용할 수 있습니다. 또는 새 프리미엄 용량이 보장되는 상황이 있을 수 있습니다. 예를 들어 부서별 워크로드를 분리하려는 경우일 수 있습니다.
- **Power BI 데이터 흐름 설정:** 데이터 준비 활동은 파워 쿼리 온라인을 사용하여 [Power BI 데이터 흐름](../transform-model/dataflows/dataflows-introduction-self-service.md)에서 한 번 설정될 수 있습니다. 이렇게 하면 많은 다양한 Power BI Desktop 파일에서 데이터 준비 작업을 복제하지 않을 수 있습니다.
- **새 조직 시각적 개체 등록:** [조직 시각적 개체](../developer/visuals/power-bi-custom-visuals-organization.md) 등록은 AppSource에서 시작되지 않은 사용자 지정 시각적 개체를 위해 관리 포털에서 수행될 수 있습니다.
- **추천 콘텐츠 설정:** Power BI 서비스 홈페이지에서 [콘텐츠를 추천](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)할 수 있는 사용자를 제어하는 테넌트 설정이 있습니다.
- **민감도 레이블 설정:** 모든 [민감도 레이블](../admin/service-security-data-protection-overview.md)은 Microsoft Information Protection과 통합됩니다.

### <a name="deploy-to-production-workspace"></a>프로덕션 작업 영역에 배포

일반적으로 프로덕션 작업 영역에 배포하는 동안 주요 활동은 다음과 같습니다.

- **변경 관리:** 필요한 경우 배포하기 위한 승인을 구하고 표준 변경 관리 방법을 사용하여 사용자 집단에 배포를 전달합니다. 프로덕션 배포가 허용되는 동안 승인된 변경 관리 창이 표시될 수 있습니다. 일반적으로 IT 관리형 콘텐츠에 적용되며 셀프 서비스 콘텐츠에 적용되는 빈도는 훨씬 적습니다.
- **롤백 계획:** 마이그레이션을 통해 처음으로 새 솔루션을 마이그레이션하는 것으로 예상됩니다. 콘텐츠가 이미 있으면 필요한 경우 이전 버전으로 되돌릴 계획을 세우는 것이 좋습니다. 이를 위해 이전 버전의 Power BI Desktop 파일을 포함할 수 있습니다(SharePoint 또는 OneDrive 버전 관리 사용).
- **연결 문자열 및 매개 변수:** 테스트와 프로덕션 간에 데이터 원본이 다른 경우 데이터 세트 연결 문자열을 조정합니다. 이를 위해 [매개 변수화](../connect-data/service-parameters.md)를 효과적으로 사용할 수 있습니다.
- **데이터 새로 고침:** 가져온 데이터 세트를 위한 [데이터 세트 새로 고침을 예약](../connect-data/refresh-scheduled-refresh.md)합니다.
- **작업 영역 콘텐츠**: 프로덕션 작업 영역에 데이터 세트 및 보고서를 게시하고 대시보드를 만듭니다. 콘텐츠가 프리미엄 용량의 작업 영역에 게시된 경우 [배포 파이프라인](../create-reports/deployment-pipelines-overview.md)은 개발, 테스트 및 프로덕션 작업 영역에 배포하는 프로세스를 간소화할 수 있습니다.
- **앱:** 앱이 콘텐츠 배포 전략의 일부인 경우 프로덕션 작업 영역의 콘텐츠를 사용하여 [앱](../consumer/end-user-apps.md)을 게시합니다.
- **보안:** 콘텐츠 배포 및 협업 전략에 따라 [작업 영역 역할](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)을 업데이트하고 확인합니다.
- **데이터 세트 설정:** 다음을 포함하여 각 데이터 세트의 설정을 업데이트하고 확인합니다.
  - [보증](../collaborate-share/service-endorse-content.md)(예: 인증됨 또는 승격됨)
  - 게이트웨이 연결 또는 데이터 원본 자격 증명
  - 예약된 새로 고침
  - [질문 및 답변 추천 질문:](../create-reports/service-q-and-a-create-featured-questions.md)
- **보고서 및 대시보드 설정:** 각 보고서 및 대시보드의 설정을 업데이트하고 확인합니다. 가장 중요한 설정은 다음과 같습니다.
  - 설명
  - 담당자 또는 그룹
  - [민감도 레이블](../admin/service-security-apply-data-sensitivity-labels.md)
  - [추천 콘텐츠](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **구독:** 필요한 경우 보고서 구독을 설정합니다.

> [!IMPORTANT]
> 이때 중요 시점에 도달했습니다. 마이그레이션 완료 시 완수를 축하합니다.

### <a name="communicate-with-users"></a>사용자와 통신

소비자에게 새 솔루션을 알립니다. 콘텐츠를 찾을 수 있는 위치 및 관련 설명서, FAQ 및 자습서를 알려 줍니다. 새 콘텐츠를 소개하려면 Lunch-and-Learn 유형의 세션을 개최하거나 주문형 비디오를 준비하는 것이 좋습니다.

도움을 요청하는 방법 및 피드백을 제공하는 방법에 관한 지침을 포함해야 합니다.

### <a name="conduct-a-retrospective"></a>회고 수행

회고를 수행하여 마이그레이션에서 제대로 진행된 항목과 다음 마이그레이션에서 개선할 항목을 검토하는 것이 더 좋습니다.

## <a name="run-in-parallel"></a>병렬로 실행

대부분의 경우 새 솔루션은 미리 결정된 시간 동안 레거시 솔루션과 병렬로 실행됩니다. 병렬로 실행의 장점은 다음과 같습니다.

- 특히 보고서가 중요 업무용으로 간주하는 경우 위험이 감소합니다.
- 사용자가 새 Power BI 솔루션에 익숙해질 시간을 허용합니다.
- Power BI에서 제공된 정보를 레거시 보고서와 상호 참조할 수 있습니다.

## <a name="decommission-the-legacy-report"></a>레거시 보고서 해제

특정 시점에 Power BI로 마이그레이션된 보고서를 레거시 BI 플랫폼에서 사용할 수 없습니다. 다음과 같은 경우 레거시 보고서 해제가 발생할 수 있습니다.

- 사용자 집단에 알렸어야 하는 병렬로 실행을 위한 미리 결정된 시간이 만료되었습니다. 해당 시간은 일반적으로 30~90일입니다.
- 레거시 시스템의 모든 사용자는 새 Power BI 솔루션에 액세스할 수 있습니다.
- 레거시 보고서에서는 더 이상 중요한 활동이 발생하지 않습니다.
- 새 Power BI 솔루션에서 사용자 생산성에 영향을 줄 수 있는 문제가 발생하지 않습니다.

## <a name="monitor-the-solution"></a>솔루션 모니터링

[Power BI 활동 로그](../admin/service-admin-auditing.md)의 이벤트를 사용하여 새 솔루션의 사용 패턴을 이해할 수 있습니다(또는 Power BI Report Server에 배포된 콘텐츠의 [실행 로그 ](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view)). 활동 로그를 분석하면 실제 사용이 예상과 다른지 여부를 확인할 수 있습니다. 솔루션이 적절히 지원되는지 유효성 검사할 수도 있습니다.

활동 로그를 검토하여 해결할 수 있는 몇 가지 질문은 다음과 같습니다.

- 콘텐츠를 얼마나 자주 보고 있나요?
- 누가 콘텐츠를 보고 있나요?
- 일반적으로 콘텐츠를 앱 또는 작업 영역을 통해 보나요?
- 대부분 사용자가 브라우저 또는 모바일 애플리케이션을 사용하고 있나요?
- 구독이 사용되고 있나요?
- 해당 솔루션을 기반으로 새 보고서를 만들고 있나요?
- 콘텐츠가 자주 업데이트되고 있나요?
- 보안이 어떻게 정의되나요?
- 데이터 새로 고침 실패와 같은 문제가 주기적으로 발생하고 있나요?
- 추가 교육이 필요함을 의미할 수 있는 걱정스러운 활동이 발생하고 있나요(예: 상당한 내보내기 활동 또는 많은 개별 보고서 공유)?

> [!IMPORTANT]
> 누군가가 활동 로그를 정기적으로 검토해야 합니다. 감사 또는 규정 준수를 위해서는 활동 로그를 캡처하고 기록을 저장하는 것만으로도 가치가 있습니다. 그러나 실제 가치는 사전 조치를 수행할 수 있는 경우입니다.

## <a name="support-the-solution"></a>솔루션 지원

마이그레이션이 완료되더라도 문제를 해결하고 성능 문제를 처리하는 데는 마이그레이션 후 기간이 중요합니다. 시간이 지남에 따라 비즈니스 요구 사항이 진화하면서 마이그레이션된 솔루션이 변경될 수 있습니다.

조직 전체에서 셀프 서비스 BI 관리 방법에 따라 지원이 약간 다르게 수행되는 경향이 있습니다. 사업부 전체에서 Power BI 챔피언은 종종 비공식적으로 일선 지원의 역할을 합니다. 비공식적인 역할이지만 권장되어야 하는 중요한 역할입니다.

일상적인 시스템 지향 요청 처리 및 에스컬레이션을 위해 지원 티켓을 사용하여 IT 직원이 배정되는 공식 지원 프로세스를 갖추는 것도 중요합니다.

조직에서 Power BI를 지원, 교육 및 제어하는 내부 컨설턴트와 같은 역할을 하는 [COE(Center of Excellence)](center-of-excellence-establish.md)가 있을 수도 있습니다. COE는 내부 포털에서 유용한 Power BI 콘텐츠를 큐레이팅하는 작업을 담당할 수 있습니다.

마지막으로, 콘텐츠 소비자는 콘텐츠에 관한 질문이 있을 경우 문의할 담당자를 알 수 있고 문제나 개선 사항에 관한 피드백을 제공하기 위한 메커니즘을 사용할 수 있어야 합니다.

## <a name="next-steps"></a>다음 단계

[시리즈의 마지막 문서](powerbi-migration-learn-from-customers.md)에서는 Power BI로 마이그레이션할 때 고객을 통해 배웁니다.

기타 유용한 리소스는 다음과 같습니다.

- [Microsoft의 BI 변환](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI 엔터프라이즈 배포 계획 백서](https://aka.ms/PBIEnterpriseDeploymentWP)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)

조직에서 마이그레이션 프로세스를 성공적으로 완료하는 데 도움을 줄 숙련된 Power BI 파트너와 협력할 수 있습니다. Power BI 파트너와 협력하려면 [Power BI 파트너 포털](https://powerbi.microsoft.com/partners/)을 방문하세요.