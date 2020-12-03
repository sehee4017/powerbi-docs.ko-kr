---
title: 배포 파이프라인 문제 해결
description: Power BI에서 배포 파이프라인 문제 해결
author: KesemSharabi
ms.author: kesharab
ms.topic: troubleshooting
ms.service: powerbi
ms.subservice: pbi-deployment
ms.date: 11/11/2020
ms.openlocfilehash: 3787f1cb61262f9f1fa64e04487c7d6395b4e549
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417638"
---
# <a name="deployment-pipelines-troubleshooting"></a>배포 파이프라인 문제 해결

이 문서를 사용하여 배포 파이프라인의 문제를 해결할 수 있습니다.

## <a name="general"></a>일반

### <a name="whats-deployment-pipelines-in-power-bi"></a>Power BI의 배포 파이프라인이란 무엇인가요?

Power BI의 배포 파이프라인을 이해하려면 [배포 파이프라인 개요](deployment-pipelines-overview.md)를 참조하세요.

### <a name="how-do-i-get-started-with-deployment-pipelines"></a>배포 파이프라인을 시작하려면 어떻게 해야 하나요?

[시작 지침](deployment-pipelines-get-started.md)을 사용하여 배포 파이프라인 시작합니다.

### <a name="why-cant-i-see-the-deployment-pipelines-button"></a>배포 파이프라인 단추가 표시되지 않는 이유는 무엇인가요?

다음 조건이 충족되지 않으면 배포 파이프라인 단추를 볼 수 없습니다.

* 다음의 Premium 라이선스 중 하나를 사용하고 있습니다.

    * Power BI [Pro 사용자](../admin/service-admin-purchasing-power-bi-pro.md)이며 프리미엄 용량이 있는 조직에 속해 있습니다.

    * [PPU(사용자 단위 Premium)](../admin/service-premium-per-user-faq.md).

* [새 작업 영역 환경](../collaborate-share/service-create-the-new-workspaces.md)의 관리자입니다.

### <a name="why-cant-i-see-the-pipeline-stage-tag-in-my-workspace"></a>내 작업 영역에서 파이프라인 단계 태그를 볼 수 없는 이유는 무엇인가요?

배포 파이프라인은 파이프라인에 할당된 작업 영역에 파이프라인 단계 태그를 표시합니다. 개발 및 테스트 단계의 태그는 항상 표시됩니다. 하지만 [파이프라인에 대한 액세스 권한](deployment-pipelines-process.md#user-with-pipeline-access)이 있거나 [작업 영역 관리자](deployment-pipelines-process.md#workspace-admin)인 경우에는 프로덕션 태그만 표시됩니다.

> [!div class="mx-imgBorder"]
> ![프로덕션 파이프라인 작업 영역에 있는 프로덕션 태그의 스크린샷](media/deployment-pipelines-troubleshooting/production-tag.png)

## <a name="licensing"></a>라이선싱

### <a name="what-licenses-are-needed-to-work-with-deployment-pipelines"></a>배포 파이프라인을 사용하는 데 필요한 라이선스는 무엇입니까?

배포 파이프라인을 사용하려면 다음 라이선스 중 하나가 있어야 합니다.

* [Pro 사용자](../admin/service-admin-purchasing-power-bi-pro.md) 라이선스([프리미엄 용량](../admin/service-premium-what-is.md)에 상주하는 작업 영역 포함).

* [PPU(사용자 단위 Premium)](../admin/service-premium-per-user-faq.md).

자세한 내용은 [배포 파이프라인 액세스](deployment-pipelines-get-started.md#accessing-deployment-pipelines)를 참조하세요.

### <a name="what-type-of-capacity-can-i-assign-to-a-workspace-in-a-pipeline"></a>파이프라인의 작업 영역에 할당할 수 있는 용량 유형은 무엇인가요?

파이프라인이 작동하려면 배포 파이프라인의 모든 작업 영역이 용량에 있어야 합니다. 그러나 파이프라인의 작업 영역마다 다른 용량을 사용할 수 있습니다. 동일한 파이프라인에서 작업 영역마다 다른 용량 유형을 사용할 수도 있습니다.

개발 및 테스트를 위해 각 사용자에 대해 Pro Power BI 계정과 함께 A 또는 EM 용량을 사용할 수 있습니다. 개발 및 테스트 단계에서 각 사용자에 대해 PPU를 사용할 수도 있습니다.

프로덕션 작업 영역에는 P 용량이 필요합니다. 포함된 애플리케이션을 통해 콘텐츠를 배포하는 ISV의 경우 프로덕션에 A 또는 EM 용량을 사용할 수도 있습니다. PPU는 프로덕션 작업 영역에도 사용할 수 있습니다.

>[!NOTE]
>한 사용자가 PPU를 사용하여 작업 영역을 만들면, 다른 PPU 사용자들만 작업 영역에 액세스하여 해당 콘텐츠를 사용할 수 있습니다.

## <a name="technical"></a>기술

### <a name="why-cant-i-see-all-my-workspaces-when-i-try-to-assign-a-workspace-to-a-pipeline"></a>파이프라인에 작업 영역을 할당하려고 할 때 내 작업 영역이 모두 표시되지 않는 이유는 무엇인가요?

파이프라인에 작업 영역을 할당하려면 다음 조건을 충족해야 합니다.

* 작업 영역이 [새 작업 영역 환경](../collaborate-share/service-create-the-new-workspaces.md)입니다.

* 작업 영역의 관리자입니다.

* 작업 영역이 다른 파이프라인에 할당되지 않았습니다.

* 작업 영역이 [프리미엄 용량](../admin/service-premium-what-is.md)에 있습니다.

이러한 조건을 충족하지 않는 작업 영역은 선택할 수 있는 작업 영역 목록에 표시되지 않습니다.

### <a name="how-can-i-assign-workspaces-to-all-the-stages-in-a-pipeline"></a>파이프라인의 모든 단계에 작업 영역을 할당하려면 어떻게 해야 하나요?

파이프라인당 하나의 작업 영역을 할당할 수 있습니다. 작업 영역이 파이프라인에 할당되면 다음 파이프라인 단계에 해당 작업 영역을 배포할 수 있습니다. 처음 배포하는 동안 원본 단계 항목의 복사본을 사용하여 새 작업 영역이 생성됩니다. 복사된 항목의 관계는 유지됩니다. 자세한 내용은 방법: [배포 파이프라인에 작업 영역 할당](deployment-pipelines-get-started.md#step-2---assign-a-workspace-to-a-deployment-pipeline)을 참조하세요.

### <a name="why-did-my-first-deployment-fail"></a>첫 번째 배포가 실패하는 이유는 무엇인가요?

몇 가지 이유로 첫 번째 배포가 실패할 수 있습니다. 아래 표에 이러한 이유 중 일부가 나와 있습니다.

|Error  |작업  |
|---------|---------|
|[프리미엄 용량 권한](deployment-pipelines-process.md#creating-a-premium-capacity-workspace)이 없습니다.     |프리미엄 용량이 있는 조직에서 작업하는 경우, 용량 관리자에게 작업 영역을 용량에 추가하도록 요청하거나 해당 용량에 대한 할당 권한을 요청하세요. 작업 영역이 용량에 할당된 후 다시 배포하세요.</br></br>프리미엄 용량을 사용하는 조직에서 작업하지 않는 경우 [PPU(사용자 단위 Premium)](../admin/service-premium-per-user-faq.md)를 구매하는 것이 좋습니다.        |
|작업 영역 권한이 없습니다.     |배포하려면 작업 영역 구성원이어야 합니다. 작업 영역 관리자에게 적절한 권한을 부여하도록 요청하세요.         |
|Power BI 관리자가 작업 영역 만들기를 사용하지 않도록 설정했습니다.     |Power BI 관리자에게 지원을 요청하세요.         |
|작업 영역이 [새 작업 영역 환경](../collaborate-share/service-create-the-new-workspaces.md)이 아닙니다.     |새 작업 영역 환경에서 콘텐츠를 만드세요. 클래식 작업 영역에 콘텐츠가 있는 경우 새 작업 영역 환경으로 [업그레이드](../collaborate-share/service-upgrade-workspaces.md)할 수 있습니다.         |
|[선택적 배포](deployment-pipelines-get-started.md#selective-deployment)를 사용 중이고 콘텐츠의 데이터 세트가 선택되지 않았습니다.     |다음 중 하나를 수행합니다. </br></br>데이터 세트에 연결된 콘텐츠를 선택 취소합니다. 선택 취소된 콘텐츠(예: 보고서 또는 대시보드)는 다음 단계에 복사되지 않습니다. </br></br>선택한 콘텐츠에 연결된 데이터 세트를 선택합니다. 데이터 세트가 다음 단계로 복사됩니다.         |

### <a name="im-getting-a-warning-that-i-have-unsupported-artifacts-in-my-workspace-when-im-trying-to-deploy-how-can-i-know-which-artifacts-are-not-supported"></a>배포하려고 할 때 내 작업 영역에 '지원되지 않는 아티팩트'가 있다는 경고가 발생합니다. 지원되지 않는 아티팩트는 어떻게 알 수 있나요?

배포 파이프라인에서 지원되지 않는 항목 및 아티팩트의 전체 목록은 다음 섹션을 참조하세요.

* [지원되지 않는 항목](deployment-pipelines-process.md#unsupported-items)

* [복사되지 않는 항목 속성](deployment-pipelines-process.md#item-properties-that-are-not-copied)

### <a name="why-did-my-deployment-fail-due-to-broken-rules"></a>손상된 규칙 때문에 배포가 실패하는 이유는 무엇인가요?

데이터 세트 규칙을 구성하는 데 문제가 있는 경우 [데이터 세트 규칙](deployment-pipelines-get-started.md#step-4---create-dataset-rules)을 방문하여 [데이터 세트 규칙 제한](deployment-pipelines-get-started.md#dataset-rule-limitations)을 준수하는지 확인해야 합니다.

배포가 이전에 성공했지만 갑자기 손상된 규칙 때문에 실패하는 경우 데이터 세트를 다시 게시하기 때문일 수 있습니다. 다음과 같은 원본 데이터 세트 변경으로 인해 배포가 실패합니다.

**매개 변수 규칙**

* 매개 변수가 제거되었습니다.

* 매개 변수 이름이 변경되었습니다.

**데이터 원본 규칙**

데이터 세트 규칙에 누락된 값이 있습니다. 데이터 세트가 변경된 경우 이 문제가 발생할 수 있습니다.

![끊어진 링크로 인해 배포가 실패하는 경우에 표시되는 잘못된 규칙 오류의 스크린샷](media/deployment-pipelines-troubleshooting/broken-rule.png)

이전에 성공한 배포가 끊어진 링크로 인해 실패할 경우 경고가 표시됩니다. **규칙 구성** 을 선택하여 실패한 데이터 세트가 표시된 배포 설정 창으로 이동할 수 있습니다. 데이터 세트를 선택하면 손상된 규칙이 표시됩니다.

성공적으로 배포하려면 손상된 규칙을 수정하거나 제거한 후 다시 배포합니다.

### <a name="how-can-i-change-the-data-source-in-the-pipeline-stages"></a>파이프라인 단계에서 데이터 원본을 변경하려면 어떻게 해야 하나요?

Power BI 서비스에서는 데이터 원본 연결을 변경할 수 없습니다.

테스트 또는 프로덕션 단계의 데이터 원본을 변경하려는 경우 [데이터 세트 규칙](deployment-pipelines-get-started.md#step-4---create-dataset-rules) 또는 [API](/rest/api/power-bi/datasets/updateparametersingroup)를 사용할 수 있습니다. 데이터 세트 규칙은 다음 배포 이후에만 적용됩니다.

### <a name="i-fixed-a-bug-in-production-but-now-i-cant-select-the-deploy-to-previous-stage-button-why-is-it-greyed-out"></a>프로덕션에서 버그를 수정했지만 이제 '이전 단계에 배포' 단추를 선택할 수 없습니다. 이 단추가 회색으로 표시되는 이유는 무엇인가요?

빈 단계에 대해서만 이전 단계 배포가 가능합니다. 테스트 단계에 콘텐츠가 있는 경우 프로덕션에서 이전 단계 배포를 할 수 없습니다.

파이프라인을 만든 후 개발 단계를 사용하여 콘텐츠를 개발하고 테스트 단계를 사용하여 검토 및 테스트합니다. 이러한 단계에서 버그를 수정한 다음 프로덕션 단계에 고정된 환경을 배포할 수 있습니다.

>[!NOTE]
>이전 단계 배포에서는 [전체 배포](deployment-pipelines-get-started.md#deploying-all-content)만 지원합니다. [선택적 배포](deployment-pipelines-get-started.md#selective-deployment)는 지원하지 않습니다.

### <a name="does-deployment-pipelines-support-multi-geo"></a>배포 파이프라인이 다중 지역을 지원하나요?

다중 지역이 지원됩니다. 다른 지역에서 단계 간에 콘텐츠를 배포하는 데 시간이 더 오래 걸릴 수 있습니다.

## <a name="permissions"></a>권한

### <a name="what-is-the-deployment-pipelines-permissions-model"></a>배포 파이프라인 권한 모델이란 무엇인가요?

배포 파이프라인 권한 모델은 [사용 권한](deployment-pipelines-process.md#permissions) 섹션에 설명되어 있습니다.

### <a name="who-can-deploy-content-between-stages"></a>단계 간에 콘텐츠를 배포할 수 있는 사람은 누구인가요?

콘텐츠는 빈 단계 또는 콘텐츠가 포함된 단계에 배포할 수 있습니다. 콘텐츠는 [프리미엄 용량](../admin/service-premium-what-is.md)에 있어야 합니다.

* **빈 단계에 배포** - 원본 작업 영역에서 구성원 또는 관리자인 모든 [Pro](../admin/service-admin-purchasing-power-bi-pro.md) 또는 [PPU](../admin/service-premium-per-user-faq.md) 사용자.

* **콘텐츠가 포함된 단계에 배포** - 원본 및 대상 배포 단계에서 두 작업 영역의 구성원 또는 관리자인 모든 [Pro](../admin/service-admin-purchasing-power-bi-pro.md) 또는 [PPU](../admin/service-premium-per-user-faq.md) 사용자.

* **데이터 세트 재정의** - 데이터 세트가 변경되지 않은 경우에도 배포가 대상 단계에 포함된 각 데이터 세트를 재정의합니다. 사용자는 배포에 지정된 모든 대상 단계 데이터 세트의 소유자여야 합니다.

### <a name="which-permissions-do-i-need-to-configure-dataset-rules"></a>데이터 세트 규칙을 구성하는 데 필요한 권한은 무엇인가요?

배포 파이프라인에서 데이터 세트 규칙을 구성하려면 데이터 세트 소유자여야 합니다.

### <a name="why-cant-i-see-workspaces-in-the-pipeline"></a>파이프라인에서 작업 영역을 볼 수 없는 이유는 무엇인가요?

파이프라인 권한과 작업 영역 권한은 별도로 관리됩니다. 파이프라인 권한이 있지만 작업 영역 권한이 없을 수 있습니다. 자세한 내용은 [사용 권한](deployment-pipelines-process.md#permissions) 섹션을 검토하세요.

## <a name="next-steps"></a>다음 단계

>[!div class="nextstepaction"]
>[배포 파이프라인 소개](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[배포 파이프라인 시작](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[배포 파이프라인 프로세스 이해](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[배포 파이프라인 모범 사례](deployment-pipelines-best-practices.md)