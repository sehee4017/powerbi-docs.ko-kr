---
title: Power BI로 마이그레이션하기 위해 배포 계획
description: Power BI로 마이그레이션하는 경우 배포 계획에 관한 지침입니다.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: f161819b6e26c197bacc5534b5abfb426d612624
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419225"
---
# <a name="plan-deployment-to-migrate-to-power-bi"></a>Power BI로 마이그레이션하기 위해 배포 계획

이 문서에서는 단일 Power BI 솔루션의 마이그레이션 계획과 관련된 **2단계** 를 설명합니다.

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="Power BI 마이그레이션의 단계를 보여 주는 이미지. 이 문서에서는 2단계가 강조됩니다.":::

> [!NOTE]
> 위의 그래픽에 관한 전체 설명은 [Power BI 마이그레이션 개요](powerbi-migration-overview.md)를 참조하세요.

2단계는 1단계에서 정의된 요구 사항을 사용하여 솔루션을 Power BI으로 마이그레이션하는 방법에 초점을 맞춥니다.

2단계의 산출물에는 배포 프로세스를 안내하는 데 필요한 최대한 많은 특정 결정이 포함됩니다.

이러한 특성의 의사 결정은 반복적인 비선형 프로세스입니다. [마이그레이션 전 단계](powerbi-migration-pre-migration-steps.md)에서 몇 가지 계획이 이미 수행됩니다. [3단계](powerbi-migration-proof-of-concept.md)에 설명된 개념 증명을 통해 배우는 것은 배포 계획과 병행될 수 있습니다. 솔루션을 만드는 동안([4단계](powerbi-migration-create-validate-content.md)에서 설명됨)에도 배포 결정에 영향을 주는 추가 정보가 발생할 수 있습니다.

> [!IMPORTANT]
> 1~5단계는 하나의 특정 솔루션과 관련된 활동을 나타냅니다. 솔루션 수준에서 프로세스에 영향을 주는 결정 및 활동이 조직/테넌트 수준에 있습니다. 일부 해당하는 상위 수준 계획 활동은 [Power BI 마이그레이션 개요](powerbi-migration-overview.md) 문서에서 설명됩니다. 해당하는 경우 효율성 및 일관성을 위한 조직 수준 결정을 따릅니다.

> [!TIP]
> 문서에서 설명하는 항목은 표준 Power BI 구현 프로젝트에도 적용됩니다.

## <a name="choose-power-bi-product"></a>Power BI 제품 선택

첫 번째 결정 중 하나는 Power BI 제품을 선택하는 것입니다. [Power BI 서비스](../fundamentals/power-bi-service-overview.md) 또는 [Power BI Report Server](../report-server/get-started.md) 중에 결정하는 것입니다. 콘텐츠가 게시된 후 포함, 모바일 전송 및 메일 구독과 같은 다양한 추가 옵션을 사용할 수 있습니다.

아키텍처 고려 사항에 관한 자세한 내용은 **Power BI 엔터프라이즈 배포 백서** 의 [섹션 3](https://aka.ms/PBIEnterpriseDeploymentWP)을 참조하세요.

> [!CAUTION]
> 파일 시스템에 저장된 Power BI Desktop 파일을 사용할 생각이 있다면 이것은 최적의 접근 방식이 아니라는 것을 알아야 합니다. Power BI 서비스(또는 Power BI Report Server) 사용하면 보안, 콘텐츠 배포 및 협업에 상당한 이점이 있습니다. 활동을 감사 및 모니터링하는 기능은 Power BI 서비스에서 사용하도록 설정할 수도 있습니다.

## <a name="decide-on-workspace-management-approach"></a>작업 영역 관리 접근 방식 결정

[작업 영역](../collaborate-share/service-new-workspaces.md)은 Power BI 서비스의 핵심 개념으로, 작업 영역 관리를 계획의 중요한 측면으로 만듭니다. 질문할 내용은 다음과 같습니다.

- 새 솔루션에 새 작업 영역이 필요한가요?
- 개발, 테스트 및 프로덕션을 수용하는 데 필요한 별도의 작업 영역이 필요한가요?
- 데이터 및 보고서에 별도의 작업 영역이 사용되나요, 아니면 단일 작업 영역으로 충분한가요? 특히 데이터 세트 보안의 경우 별도 작업 영역에는 수많은 이점이 있습니다. 필요한 경우 보고서를 게시하는 사용자와 별도로 관리할 수 있습니다.
- 작업 영역의 보안 요구 사항은 무엇인가요? [작업 영역 역할](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)의 계획에 영향을 줍니다. 콘텐츠 소비자가 앱을 사용하는 경우 [앱에 대한 권한](../collaborate-share/service-create-distribute-apps.md#publish-your-app)은 작업 영역과 별도로 관리됩니다. 앱 뷰어의 고유 권한을 통해 보고서 또는 대시보드의 읽기 전용 소비자를 위한 보안 요구 사항 충족에 추가적인 유연성이 허용됩니다.
- 새 콘텐츠를 보호하는 데 기존 그룹을 사용할 수 있나요? Azure Active Directory 및 Microsoft 365 그룹이 둘 다 지원됩니다. 기존 프로세스에 맞게 조정된 경우 그룹을 사용하면 개별 사용자에게 할당하는 것보다 더 쉽게 권한을 관리할 수 있습니다.
- 외부 게스트 사용자와 관련된 보안 고려 사항이 있나요? Azure Active Directory 관리자 및 Power BI 관리자와 협력하여 [게스트 사용자 액세스](../admin/service-admin-azure-ad-b2b.md)를 구성해야 할 수 있습니다.

> [!TIP]
> 특정 비즈니스 활동 또는 프로젝트를 위한 작업 영역을 만드는 것이 좋습니다. 부서별로 작업 영역과 같이 조직 구조를 기반으로 작업 영역 구성을 시작하려고 생각할 수 있지만 일반적으로 해당 접근 방식은 결국 너무 광범위해집니다.

## <a name="determine-how-content-will-be-consumed"></a>콘텐츠 소비 방법 결정

솔루션 소비자가 보고서 및 대시보드를 볼 때 선호하는 방법을 이해하면 도움이 됩니다. 질문할 내용은 다음과 같습니다.

- [Power BI 앱](../consumer/end-user-apps.md)(단일 작업 영역의 보고서 및 대시보드로 구성됨)이 소비자에게 콘텐츠를 제공하는 가장 좋은 방법인가요, 아니면 콘텐츠 뷰어가 작업 영역에 직접 액세스하는 것으로 충분한가요?
- [Teams](../collaborate-share/service-embed-report-microsoft-teams.md), [SharePoint Online](../collaborate-share/service-embed-report-spo.md) 또는 [보안 포털이나 웹 사이트](../collaborate-share/service-embed-secure.md)와 같은 다른 곳에 특정 보고서 및 대시보드가 포함되나요?
- 소비자는 [모바일 디바이스](../consumer/mobile/mobile-apps-for-mobile-devices.md)를 사용하여 콘텐츠에 액세스하나요? 보고서를 작은 폼 팩터 디바이스에 제공하기 위한 요구 사항은 일부 [보고서 디자인 결정](../create-reports/desktop-create-phone-report.md)에 영향을 줍니다.

## <a name="decide-if-other-content-may-be-created"></a>다른 콘텐츠를 만들 수 있는지 결정

소비자가 다음과 같은 새 콘텐츠를 만들도록 허용할지에 관련된 여러 가지 주요 결정을 내립니다.

- 소비자가 게시된 데이터 세트에서 새 보고서를 만들 수 있나요? 사용자에게 데이터 세트 [빌드 권한](../connect-data/service-datasets-build-permissions.md)을 할당하여 해당 기능을 사용하도록 설정할 수 있습니다.
- 소비자가 보고서를 사용자 지정하려는 경우 해당 보고서의 [복사본을 저장](../connect-data/service-datasets-copy-reports.md)하고 필요에 맞게 개인 설정할 수 있나요?

> [!CAUTION]
> _복사본 저장_ 기능은 멋진 기능이지만 보고서에 특정 그래픽 또는 머리글/바닥글 메시지가 포함되는 경우 주의해서 사용해야 합니다. 로고, 아이콘 및 텍스트 메시지는 종종 브랜딩 요구 사항 또는 규정 준수와 관련이 있으므로 해당 항목을 제공하고 배포하는 방법을 신중하게 제어해야 합니다. _복사본 저장_ 이 사용되지만 새 작성자가 원래 그래픽 또는 머리글/바닥글 메시지를 변경하지 않는 경우에는 실제로 누가 보고서를 생성했는지 혼동될 수 있습니다. 브랜딩의 중요함이 감소할 수도 있습니다.

## <a name="evaluate-needs-for-premium-capacity"></a>프리미엄 용량의 요구 사항 평가

작업 영역이 [프리미엄 용량](../admin/service-premium-what-is.md)에 저장된 경우 추가 용량을 사용할 수 있습니다. 프리미엄 용량의 작업 영역이 유용할 수 있는 몇 가지 이유는 다음과 같습니다.

- Power BI Pro 라이선스가 없는 소비자가 콘텐츠에 액세스할 수 있습니다.
- 대규모 데이터 세트를 지원합니다.
- 더 빈번한 데이터 새로 고침을 지원합니다.
- 데이터 흐름의 전체 기능 세트 사용을 지원합니다.
- 배포 파이프라인 및 XMLA 엔드포인트를 비롯한 엔터프라이즈 기능이 제공됩니다.
- 페이지를 매긴 보고서를 지원합니다(워크로드가 사용되는 경우).

## <a name="determine-data-acquisition-method"></a>데이터 취득 방법 결정

보고서에 필요한 데이터는 여러 가지 결정에 영향을 줄 수 있습니다. 질문할 내용은 다음과 같습니다.

- 기존 Power BI [공유 데이터 세트](../connect-data/service-datasets-share.md)를 사용할 수 있나요, 아니면 이 솔루션에 적합한 새 Power BI 데이터 세트를 만드나요?
- 추가 요구 사항을 충족하기 위해 새 데이터 또는 측정값으로 기존 공유 데이터 세트를 보강해야 하나요?
- 가장 적합한 [데이터 스토리지 모드](../transform-model/desktop-storage-mode.md)는 무엇인가요? 옵션에는 가져오기, DirectQuery, 복합 또는 라이브 연결이 포함됩니다.
- 쿼리 성능을 개선하기 위해 [집계](../transform-model/desktop-aggregations.md)를 사용해야 하나요?
- [데이터 흐름](../transform-model/dataflows/dataflows-introduction-self-service.md)을 만드는 것이 유용하고 데이터 흐름을 수많은 데이터 세트의 원본으로 사용할 수 있나요?
- 새 [게이트웨이 데이터 원본](../connect-data/service-gateway-data-sources.md)을 등록해야 하나요?

## <a name="decide-where-original-content-will-be-stored"></a>원래 콘텐츠를 저장할 위치 결정

목표 배포 대상을 계획하는 것 외에도 다음과 같이 원래 또는 원본 콘텐츠가 저장될 위치를 계획해야 합니다.

- 원래 Power BI Desktop(.pbix) 파일을 저장할 승인된 위치를 지정합니다. 해당 위치는 콘텐츠를 편집하는 사용자에게만 제공하는 것이 가장 좋습니다. Power BI 서비스에서 보안을 설정하는 방법에 맞게 조정되어야 합니다.
- 버전 관리 기록 또는 원본 제어를 포함하는 원래 Power BI Desktop 파일의 위치를 사용합니다. 버전 관리를 사용하면 필요한 경우 콘텐츠 작성자가 이전 파일 버전으로 되돌릴 수 있습니다. 해당 용도에는 비즈니스용 OneDrive 또는 SharePoint가 적합합니다.
- 플랫 파일 또는 Excel 파일과 같은 중앙 집중화되지 않은 원본 데이터를 저장할 승인된 위치를 지정합니다. 데이터 세트 작성자가 오류 없이 도달할 수 있고 정기적으로 백업되는 경로여야 합니다.
- Power BI 서비스에서 내보낸 콘텐츠를 위한 승인된 위치를 지정합니다. 목표는 Power BI 서비스에 정의된 보안이 의도치 않게 우회되지 않게 하는 것입니다.

> [!IMPORTANT]
> 원래 Power BI Desktop 파일에 가져온 데이터가 포함된 경우 해당 파일을 위한 보호된 위치를 지정하는 것이 특히 중요합니다.

## <a name="assess-the-level-of-effort"></a>활동 수준 평가

요구 사항([1단계](powerbi-migration-requirements.md)에서 설명됨) 및 솔루션 배포 계획에서 충분한 정보를 사용할 수 있으면 이제 활동 수준을 평가할 수 있습니다. 그런 다음, 작업, 타임라인 및 책임을 사용하여 프로젝트 계획을 공식화할 수 있습니다.

> [!TIP]
> 인건비(급여 및 임금)은 일반적으로 대부분 조직에서 가장 높은 지출에 속합니다. 정확하게 예측하는 것은 어려울 수 있지만 생산성 향상으로 뛰어난 ROI(투자 수익률)를 확보할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[Power BI 마이그레이션 시리즈의 다음 문서](powerbi-migration-proof-of-concept.md)에서는 Power BI로 마이그레이션할 때 최대한 빨리 위험을 완화하고 미지의 상태를 해결하기 위한 개념 증명 수행과 관련된 3단계를 알아봅니다.

기타 유용한 리소스는 다음과 같습니다.

- [Microsoft의 BI 변환](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI 엔터프라이즈 배포 계획 백서](https://aka.ms/PBIEnterpriseDeploymentWP)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)

조직에서 마이그레이션 프로세스를 성공적으로 완료하는 데 도움을 줄 숙련된 Power BI 파트너와 협력할 수 있습니다. Power BI 파트너와 협력하려면 [Power BI 파트너 포털](https://powerbi.microsoft.com/partners/)을 방문하세요.