---
title: Power BI로 마이그레이션할 콘텐츠 만들기
description: Power BI로 마이그레이션하는 경우 콘텐츠를 만들고 유효성을 검사하는 방법에 관한 지침입니다.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: a12a320b061967e9201e3513e504277a9df586b4
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803504"
---
# <a name="createcontenttomigratetopowerbi"></a>Power BI로 마이그레이션할 콘텐츠 만들기

이 문서에서는 Power BI로 마이그레이션할 때 콘텐츠를 만들고 유효성을 검사하는 작업과 관련된 **4단계**를 설명합니다.

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="Power BI 마이그레이션의 단계를 보여 주는 이미지. 이 문서에서는 4단계가 강조됩니다.":::

> [!NOTE]
> 위의 그래픽에 관한 전체 설명은 [Power BI 마이그레이션 개요](powerbi-migration-overview.md)를 참조하세요.

4단계는 POC(개념 증명)를 프로덕션 환경에서 사용할 수 있는 솔루션으로 변환하는 실제 작업을 수행하는 데 초점을 맞춥니다.

이 단계의 산출물은 개발 작업 영역에서 유효성이 검사되었고 프로덕션 환경에 배포할 준비가 된 Power BI 솔루션입니다.

> [!TIP]
> 문서에서 설명하는 대부분의 항목은 표준 Power BI 구현 프로젝트에도 적용됩니다.

## <a name="create-the-production-solution"></a>프로덕션 솔루션 만들기

이때 POC를 수행한 동일한 사람이 계속해서 프로덕션 환경에서 사용할 수 있는 Power BI 솔루션을 생성할 수 있습니다. 또는 다른 사람이 참여할 수 있습니다. 타임라인이 위험해지지 않는다면 향후 Power BI 개발을 담당할 사용자가 참여하는 것이 좋습니다. 이렇게 하면 해당 사용자가 적극적으로 학습할 수 있습니다.

> [!IMPORTANT]
> POC에서 최대한 많은 작업을 다시 사용합니다.

### <a name="develop-new-import-dataset"></a>새 가져오기 데이터 세트 개발

요구 사항을 충족하는 기존 Power BI 데이터 세트가 아직 없거나 요구 사항을 충족하도록 개선할 수 없는 경우 새 가져오기 데이터 세트를 만들 수 있습니다.

처음부터 데이터 및 보고서의 개발 작업을 분리하는 것이 가장 좋습니다. 여러 사용자가 데이터 모델링 및 보고서를 담당하는 경우 [데이터와 보고서를 분리](report-separate-from-model.md)하면 작업 및 권한을 쉽게 분리할 수 있습니다. 이를 통해 확장성이 더 높은 접근 방식이 되며 데이터 재사용 가능성이 향상됩니다.

가져오기 데이터 세트 개발과 관련된 필수 활동은 다음과 같습니다.

- 하나 이상의 데이터 원본(Power BI 데이터 흐름일 수 있음)에서 [데이터를 취득](../connect-data/desktop-quickstart-connect-to-data.md)합니다.
- 데이터를 [셰이핑, 결합 및 준비](../connect-data/desktop-shape-and-combine-data.md)합니다.
- [날짜 테이블](../transform-model/desktop-date-tables.md)을 포함하여 [데이터 세트 모델](../transform-model/desktop-modeling-view.md)을 만듭니다.
- [모델 관계](../transform-model/desktop-create-and-manage-relationships.md)를 만들고 확인합니다.
- [측정값](../transform-model/desktop-measures.md)을 정의합니다.
- 필요한 경우 [행 수준 보안](../admin/service-admin-rls.md)을 설정합니다.
- 동의어를 구성하고 [Q&A를 최적화](../natural-language/q-and-a-best-practices.md)합니다.
- [복합 모델](../transform-model/desktop-composite-models.md) 또는 [집계](../transform-model/desktop-aggregations.md) 사용과 같은 데이터 스토리지 모드에 관한 결정에 영향을 줄 수 있는 확장성, 성능 및 동시성을 계획합니다.

> [!TIP]
> 다양한 개발/테스트/프로덕션 환경이 있는 경우 데이터 원본을 [매개 변수화](/power-query/power-query-query-parameters)하는 것이 좋습니다. 이를 통해 [5단계](powerbi-migration-deploy-support-monitor.md)에 설명된 배포를 훨씬 더 쉽게 수행할 수 있습니다.

### <a name="develop-new-reports-and-dashboards"></a>새 보고서 및 대시보드 개발

Power BI 보고서 또는 대시보드의 개발과 관련된 필수 작업은 다음과 같습니다.

- 기존 데이터 모델에 대한 라이브 연결을 사용하거나 새 데이터 모델을 만드는 작업 결정
- 새 데이터 모델을 만드는 경우 모델 테이블(가져오기, DirectQuery 또는 복합)을 위한 [데이터 스토리지 모드](../transform-model/desktop-storage-mode.md)를 결정합니다.
- 요구 사항을 충족하는 가장 적합한 데이터 시각화 도구를 Power BI Desktop, Paginated Report Builder 또는 Excel 중에서 결정합니다.
- 보고서에서 알려야 하는 스토리를 알리고 보고서에서 대답해야 하는 질문을 해결하는 [가장 적합한 시각적 개체](../consumer/end-user-visual-type.md)를 결정합니다.
- 모든 시각적 개체가 분명하고, 간결하며, 비즈니스 친화적인 용어를 제공하는지 확인합니다.
- 상호 작용 요구 사항을 해결합니다.
- 라이브 연결을 사용하는 경우 [보고서 수준 측정값](../transform-model/desktop-tutorial-create-measures.md)을 추가합니다.
- 특히 소비자가 주요 메트릭을 모니터링하는 간편한 방법을 원하는 경우 Power BI 서비스에서 [대시보드](../create-reports/service-dashboards.md)를 만듭니다.

> [!NOTE]
> 대부분의 해당 결정은 계획 초기 단계 또는 기술 POC에서 수행되었습니다.

## <a name="validate-the-solution"></a>솔루션 유효성 검사

Power BI 솔루션 유효성 검사의 네 가지 주요 측면은 다음과 같습니다.

1. 데이터 정확도
2. 보안
3. 기능
4. 성능

### <a name="validate-data-accuracy"></a>데이터 정확도 유효성 검사

마이그레이션하는 동안 일회성 활동으로 새 보고서의 데이터가 레거시 보고서에 표시된 데이터와 일치하는지 확인해야 합니다. 또는 차이가 있는 경우 이유를 설명할 수 있습니다. 새 솔루션에서 해결되는 레거시 솔루션의 오류를 찾는 경우는 생각보다 더 일반적입니다.

지속적인 데이터 유효성 검사 활동의 일부로 새 보고서를 원래 원본 시스템과 교차 확인해야 합니다. 해당 유효성 검사는 보고서 변경을 게시할 때마다 반복 가능한 방법으로 수행하는 것이 가장 좋습니다.

### <a name="validate-security"></a>보안 유효성 검사

보안의 유효성을 검사하는 경우 다음과 같은 두 가지 주요 측면을 고려해야 합니다.

- 데이터 권한
- 데이터 세트, 보고서 및 대시보드에 액세스

가져오기 데이터 세트에서 RLS([행 수준 보안](../admin/service-admin-rls.md))를 정의하여 데이터 권한을 적용합니다. DirectQuery 스토리지 모드를 사용하는 경우([Single Sign-On](../connect-data/service-gateway-sso-overview.md)과 함께 사용 가능) 원본 시스템에서 데이터 권한을 적용할 수도 있습니다.

Power BI 콘텐츠에 대한 액세스 권한을 부여하는 기본 방법은 다음과 같습니다.

- [작업 영역 역할](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)(콘텐츠 편집기 및 뷰어용).
- 패키지된 작업 영역 콘텐츠 세트에 적용되는 [앱 권한](../collaborate-share/service-create-distribute-apps.md#publish-your-app)(뷰어용).
- 개별 보고서 또는 대시보드 [공유](../collaborate-share/service-share-dashboards.md)(뷰어용).

> [!TIP]
> 콘텐츠 작성자에게 보안을 효과적으로 관리하는 방법을 교육하는 것이 좋습니다. 강력한 테스트, 감사 및 모니터링을 준비하는 것도 중요합니다.

### <a name="validate-functionality"></a>기능 유효성 검사

이제 필드 이름, 형식 지정, 정렬 및 기본 요약 동작과 같이 데이터 세트 세부 정보를 다시 확인합니다. [슬라이서](../visuals/power-bi-visualization-slicers.md), [드릴다운](../consumer/end-user-drill.md), [드릴스루](../create-reports/desktop-drillthrough.md), [식](../create-reports/desktop-conditional-format-visual-titles.md), [단추](../create-reports/desktop-buttons.md) 또는 [책갈피](../create-reports/desktop-bookmarks.md)와 같은 대화형 보고서 기능도 모두 확인됩니다.

개발 프로세스 중에 정기적으로 Power BI 서비스의 개발 작업 영역에 Power BI 솔루션을 게시해야 합니다. 서비스에서 모든 기능이 예상대로 작동하는지 확인합니다(예: 사용자 지정 시각적 개체의 렌더링). 또한 추가 테스트를 수행해도 좋습니다. [예약된 새로 고침](../connect-data/refresh-scheduled-refresh.md), [Q&A](../consumer/end-user-q-and-a.md) 및 [모바일 디바이스](../consumer/mobile/mobile-apps-for-mobile-devices.md)에서 보고서 및 대시보드가 표시되는 방식을 테스트합니다.

### <a name="validate-performance"></a>성능 유효성 검사

소비자 환경에서 Power BI 솔루션의 성능은 중요합니다. 대부분 보고서는 10초 내에 시각적 개체를 제공해야 합니다. 로드하는 데 더 오래 걸리는 보고서가 있는 경우 지연의 원인이 될 수 것을 재검토해야 합니다. 보고서 성능은 Power BI Desktop 외에도 Power BI 서비스에서 정기적으로 평가되어야 합니다.

표준이 아닌 [DAX(Data Analysis eXpressions)](../transform-model/desktop-quickstart-learn-dax-basics.md), 좋지 않은 데이터 세트 디자인 또는 최적이 아닌 보고서 디자인(예: 단일 페이지에서 너무 많은 시각적 개체를 렌더링하려는 경우)에서 많은 성능 문제가 발생합니다. 네트워크, 오버로드된 데이터 게이트웨이 또는 프리미엄 용량을 구성하는 방법과 같은 기술적 환경 문제는 성능 문제에도 영향을 줄 수 있습니다. 자세한 내용은 [Power BI 최적화 가이드](power-bi-optimization.md) 및 [Power BI의 보고서 성능 문제 해결](report-performance-troubleshoot.md)을 참조하세요.

## <a name="document-the-solution"></a>솔루션 문서화

Power BI 솔루션에 유용한 두 가지 기본 유형의 설명서는 다음과 같습니다.

- 데이터 세트 설명서
- 보고서 설명서

대상 그룹이 가장 쉽게 액세스할 수 있는 어디에나 문서를 저장할 수 있습니다. 일반 옵션은 다음과 같습니다.

- **SharePoint 사이트 내:** SharePoint 사이트는 COE(Center of Excellence) 또는 내부 Power BI 커뮤니티 사이트에 사용할 수 있습니다.
- **앱 내:** Power BI 앱을 게시할 때 소비자에게 추가 정보를 전달하도록 URL을 구성할 수 있습니다.
- **개별 Power BI Desktop 파일 내:** 테이블 및 열과 같은 모델 요소가 설명을 정의할 수 있습니다. 해당 설명은 보고서를 작성할 때 **필드** 창에 도구 설명으로 나타납니다.

> [!TIP]
> Power BI 관련 설명서의 허브로 사용되는 사이트를 만드는 경우 해당 URL 위치를 사용하여 [도움말 보기 메뉴를 사용자 지정](../admin/service-admin-portal.md#publish-get-help-information)하는 것이 좋습니다.

### <a name="create-dataset-documentation"></a>데이터 세트 설명서 만들기

데이터 세트 설명서는 나중에 데이터 세트를 관리할 사용자를 대상으로 합니다. 다음을 포함하는 것이 좋습니다.

- 디자인 결정 및 이유
- 데이터 세트를 소유, 유지 관리 및 인증하는 사용자
- 데이터 새로 고침 요구 사항
- 데이터 세트에 정의된 사용자 지정 비즈니스 규칙
- 특정 데이터 세트 보안 또는 데이터 프라이버시 요구 사항
- 향후 유지 관리 요구 사항
- 알려진 미해결 문제 또는 지연된 백로그 항목

시간이 지남에 따라 데이터 세트에 발생한 가장 중요한 변경 내용을 요약하는 변경 로그를 만들도록 선택할 수도 있습니다.

### <a name="create-report-documentation"></a>보고서 설명서 만들기

일반적으로 보고서 소비자를 대상으로 하는 연습으로 구성된 보고서 설명서는 소비자가 보고서 및 대시보드에서 더 많은 가치를 창출하는 데 도움이 될 수 있습니다. 종종 짧은 비디오 자습서도 유용합니다.

보고서의 숨겨진 페이지에 추가 보고서 설명서를 포함하도록 선택할 수도 있습니다. 디자인 결정 및 변경 로그를 포함할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[Power BI 마이그레이션 시리즈의 다음 문서](powerbi-migration-deploy-support-monitor.md)에서는 Power BI로 마이그레이션할 때 콘텐츠 배포, 지원 및 모니터링과 관련된 5단계를 알아봅니다.

기타 유용한 리소스는 다음과 같습니다.

- [Microsoft의 BI 변환](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI 엔터프라이즈 배포 계획 백서](https://aka.ms/PBIEnterpriseDeploymentWP)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)

조직에서 마이그레이션 프로세스를 성공적으로 완료하는 데 도움을 줄 숙련된 Power BI 파트너와 협력할 수 있습니다. Power BI 파트너와 협력하려면 [Power BI 파트너 포털](https://powerbi.microsoft.com/partners/)을 방문하세요.
