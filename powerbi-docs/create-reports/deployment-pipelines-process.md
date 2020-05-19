---
title: 배포 파이프라인 프로세스
description: Power BI 배포 파이프라인 프로세스 이해
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: c4a823b0b41def6c10cd8f932bb97e91eb977ecb
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148612"
---
# <a name="understand-the-deployment-process-preview"></a>배포 프로세스 이해(미리 보기)

배포 프로세스를 사용하여 파이프라인의 한 단계에서 다른 단계로(일반적으로 개발에서 테스트로, 테스트에서 프로덕션으로) 콘텐츠를 복제할 수 있습니다.

배포하는 동안 Power BI는 현재 단계에서 대상 단계로 콘텐츠를 복사합니다. 복사 프로세스 동안 복사된 항목 간의 연결이 유지됩니다. 또한 Power BI는 구성된 데이터 세트 규칙을 대상 단계의 업데이트된 콘텐츠에 적용합니다. 배포되는 항목 수에 따라 콘텐츠를 배포하는 데 다소 시간이 걸릴 수 있습니다. 이 시간 동안 Power BI 포털의 다른 페이지로 이동할 수 있지만 대상 단계의 콘텐츠를 사용할 수는 없습니다.

## <a name="deploying-content-to-an-empty-stage"></a>빈 단계에 콘텐츠 배포

빈 단계에 콘텐츠를 배포하는 경우 원본 작업 영역의 보고서, 대시보드 및 데이터 세트에 대한 메타데이터가 대상 단계에 복사됩니다. 대상 단계에 대한 새 작업 영역이 프리미엄 용량에 생성됩니다.

한 단계에서 다음 단계로 콘텐츠를 배포하는 방법에는 두 가지가 있습니다. 모든 콘텐츠를 배포할 수도 있고, [배포할 콘텐츠 항목을 선택](deployment-pipelines-get-started.md#selective-deployment)할 수도 있습니다.

배포 파이프라인의 이후 단계에서 이전 단계로 콘텐츠를 배포할 수도 있습니다.

배포가 완료되면 새로 복사된 콘텐츠를 사용할 수 있도록 데이터 세트를 새로 고칩니다. 데이터 세트 새로 고침은 데이터가 한 단계에서 다른 단계로 복사되지 않기 때문에 필요합니다. 배포 프로세스 중에 복사되는 항목 속성과 복사되지 않는 항목 속성을 이해하려면 [배포하는 동안 복사되는 항목 속성](#item-properties-copied-during-deployment) 섹션을 검토하세요.

### <a name="creating-a-premium-capacity-workspace"></a>프리미엄 용량 작업 영역 만들기

처음 배포하는 동안 배포 파이프라인은 사용자에게 프리미엄 용량 권한이 있는지 확인합니다.  

용량 권한이 있는 경우에는 대상 단계에 작업 영역의 콘텐츠가 복사되고 해당 단계에 대한 새 작업 영역이 프리미엄 용량에 생성됩니다.

용량 권한이 없는 경우 작업 영역이 생성되지만 콘텐츠가 복사되지 않습니다. 용량 관리자에게 작업 영역을 용량에 추가하도록 요청하거나 해당 용량에 대한 할당 권한을 요청할 수 있습니다. 나중에 작업 영역이 용량에 할당되면 이 작업 영역에 콘텐츠를 배포할 수 있습니다.

### <a name="workspace-and-content-ownership"></a>작업 영역 및 콘텐츠 소유권

배포하는 사용자는 자동으로 복제된 데이터 세트의 데이터 세트 소유자와 새 작업 영역의 유일한 관리자가 됩니다.

## <a name="deploy-content-to-an-existing-workspace"></a>기존 작업 영역에 콘텐츠 배포

운영 중인 프로덕션 파이프라인의 콘텐츠를 기존 작업 영역이 있는 단계에 배포하는 작업에는 다음이 포함됩니다.

* 이미 콘텐츠가 포함된 단계에 새 콘텐츠를 추가합니다.

* 현재 작업 단계에서 새 콘텐츠를 배포하여 이전 콘텐츠를 대체합니다.

### <a name="deployment-process"></a>배포 프로세스

현재 단계의 콘텐츠가 대상 단계로 복사됩니다. Power BI가 대상 단계에서 기존 콘텐츠를 식별하여 덮어씁니다. 덮어쓸 콘텐츠 항목을 식별하기 위해 배포 파이프라인이 부모 항목과 해당 복제본 간의 연결을 사용합니다. 이 연결은 새 콘텐츠를 만들 때 유지됩니다. 덮어쓰기 작업은 항목의 콘텐츠만 덮어씁니다. 항목의 ID, URL 및 사용 권한은 변경되지 않고 그대로 유지됩니다.

대상 단계에서는 [복사되지 않는 항목 속성](deployment-pipelines-process.md#item-properties-that-are-not-copied)은 배포 이전 상태로 유지됩니다. 새 콘텐츠와 새 항목이 현재 단계에서 대상 단계로 복사됩니다.

### <a name="refreshing-the-dataset"></a>데이터 세트 새로 고침

가능한 경우 대상 데이터 세트의 데이터가 유지됩니다. 데이터 세트 변경 내용이 없는 경우 데이터는 배포 전 상태로 유지됩니다.

테이블 또는 계산된 측정값을 추가하는 것과 같이 약간만 변경된 경우에는 Power BI가 원래 데이터를 유지하며 필요한 항목만 새로 고치도록 새로 고침이 최적화됩니다. 중단이 발생하는 스키마 변경이나 데이터 원본 연결 변경의 경우에는 전체 새로 고침이 필요합니다.

### <a name="requirements-for-deploying-to-a-stage-with-an-existing-workspace"></a>기존 작업 영역이 포함된 단계에 배포하기 위한 요구 사항

배포된 콘텐츠가 [프리미엄 용량](../admin/service-premium-what-is.md)에 있는 한, 다음 조건을 충족하는 사용자는 기존 작업 영역이 포함된 스테이지에 배포할 수 있습니다.

* 원본 및 대상 배포 단계의 두 작업 영역 모두에 속하는 구성원인 [Pro 사용자](../admin/service-admin-purchasing-power-bi-pro.md).

* 배포하려는 대상 작업 영역에 있는 모든 데이터 세트의 소유자.

자세한 내용은 [사용 권한](#permissions) 섹션을 검토하세요.

## <a name="deployed-items"></a>배포된 항목

한 파이프라인 단계에서 다른 파이프라인 단계로 콘텐츠를 배포하는 경우 복사된 콘텐츠에는 다음과 같은 Power BI 항목이 포함됩니다.

* 데이터 세트

* 보고서

* 대시보드

### <a name="unsupported-items"></a>지원되지 않는 항목

배포 파이프라인은 다음 항목을 지원하지 않습니다.

* .pbix에서 시작하지 않은 데이터 세트

* 지원되지 않는 데이터 세트를 기반으로 한 보고서

* 작업 영역은 템플릿 앱을 사용할 수 없음

* 페이지를 매긴 보고서

* 데이터 흐름

* 푸시 데이터 세트

* 통합 문서

## <a name="item-properties-copied-during-deployment"></a>배포하는 동안 복사되는 항목 속성

다음 항목 속성은 배포하는 동안 복사되어 대상 단계의 항목 속성을 덮어씁니다.

* 데이터 원본([데이터 세트 규칙](deployment-pipelines-get-started.md#step-4---create-dataset-rules) 지원)

* 매개 변수([데이터 세트 규칙](deployment-pipelines-get-started.md#step-4---create-dataset-rules) 지원)

* 보고서 시각적 개체

* 보고서 페이지

* 대시보드 타일

* 모델 메타데이터

* 항목 관계

### <a name="item-properties-that-are-not-copied"></a>복사되지 않는 항목 속성

다음 항목 속성은 배포하는 동안 복사되지 않습니다.

* 데이터 - 데이터는 복사되지 않고 메타데이터만 복사됩니다.

* URL

* ID

* 권한 - 작업 영역 또는 특정 항목의 경우

* 작업 영역 설정 - 각 단계에는 자체 작업 영역이 있습니다.

* 앱 콘텐츠 및 설정 - 앱을 배포하려면 [Power BI 앱 배포](#deploying-power-bi-apps)를 참조하세요.

다음 데이터 세트 속성도 배포하는 동안 복사되지 않습니다.

* 역할 할당
    
* 새로 고침 일정
    
* 데이터 원본 자격 증명
    
* 쿼리 캐싱 설정(용량에서 상속 가능)
    
* 인증 설정

## <a name="deploying-power-bi-apps"></a>Power BI 앱 배포

[Power BI 앱](../consumer/end-user-apps.md)은 무료 Power BI 소비자에게 콘텐츠를 배포하는 권장 방법입니다. 배포 파이프라인을 사용하여 배포 파이프라인에서 Power BI 앱을 관리할 수 있습니다. 따라서 앱의 수명 주기에 대한 제어 및 유연성이 확대됩니다.

최종 사용자의 관점에서 각 앱 업데이트를 테스트할 수 있도록 각 배포 파이프라인 단계에 대한 앱을 만듭니다. 배포 파이프라인을 사용하면 이 프로세스를 쉽게 관리할 수 있습니다. 작업 영역 카드의 게시 또는 보기 단추를 사용하여 특정 파이프라인 단계에서 앱을 게시하거나 볼 수 있습니다.

[![](media/deployment-pipelines-process/publish.png "Publish app")](media/deployment-pipelines-process/publish.png#lightbox)

프로덕션 단계에서 왼쪽 아래 모서리에 있는 주 작업 단추를 클릭하면 Power BI의 앱 업데이트 페이지가 열려 앱 사용자가 콘텐츠 업데이트를 사용할 수 있습니다.

[![](media/deployment-pipelines-process/update-app.png "Update app")](media/deployment-pipelines-process/update-app.png#lightbox)

>[!IMPORTANT]
>배포 프로세스에는 앱 콘텐츠 또는 설정 업데이트가 포함되지 않습니다. 콘텐츠 또는 설정에 변경 내용을 적용하려면 필요한 파이프라인 단계에서 수동으로 앱을 업데이트해야 합니다.

## <a name="permissions"></a>권한

파이프라인 권한과 작업 영역 권한은 별도로 부여 및 관리됩니다. 예를 들어 파이프라인 액세스 권한이 있고 작업 영역 권한이 없는 사용자는 파이프라인을 보고 다른 사용자와 공유할 수 있습니다. 그러나 이 사용자는 파이프라인 또는 작업 영역 페이지에서 작업 영역의 콘텐츠를 볼 수 없으며 배포를 수행할 수 없습니다.

### <a name="user-with-pipeline-access"></a>파이프라인 액세스 권한이 있는 사용자

파이프라인 액세스 권한이 있는 사용자에게는 다음 권한이 있습니다.

* 파이프라인 보기
    
* 다른 사용자와 파이프라인 공유
    
* 파이프라인 편집 및 삭제

>[!NOTE]
>파이프라인 액세스 권한은 작업 영역 콘텐츠를 보거나 작업을 수행할 수 있는 권한을 부여하지 않습니다.

### <a name="workspace-viewer"></a>작업 영역 뷰어

‘파이프라인 액세스 권한’이 있는 작업 영역 뷰어는 다음 작업도 수행할 수 있습니다.

* 콘텐츠 사용

>[!NOTE]
>작업 영역 뷰어는 데이터 세트에 액세스하거나 작업 영역 콘텐츠를 편집할 수 없습니다.

### <a name="workspace-contributor"></a>작업 영역 참가자

‘파이프라인 액세스 권한’이 있는 작업 영역 참가자는 다음 작업도 수행할 수 있습니다.

* 콘텐츠 사용

* 단계 비교

* 데이터 세트 보기

### <a name="workspace-member"></a>작업 영역 구성원

‘파이프라인 액세스 권한’이 있는 작업 영역 구성원은 다음 작업도 수행할 수 있습니다.

* 작업 영역 콘텐츠 보기
    
* 단계 비교
    
* 보고서 및 대시보드 배포

* 작업 영역 제거

### <a name="workspace-admin"></a>작업 영역 관리자

‘파이프라인 액세스 권한’이 있는 작업 영역 관리자는 ‘작업 영역 구성원’ 작업 이외에 다음 작업도 수행할 수 있습니다.

* 작업 영역 할당

* 작업 영역 제거

### <a name="dataset-owner"></a>데이터 세트 소유자

작업 영역 구성원 또는 관리자인 데이터 세트 소유자는 다음 작업도 수행할 수 있습니다.

* 데이터 세트 업데이트
    
* 규칙 구성

>[!NOTE]
>이 섹션에서는 배포 파이프라인의 사용자 권한에 대해 설명합니다. 이 섹션에 나열된 사용 권한은 다른 Power BI 기능에서는 다르게 적용될 수 있습니다.

## <a name="limitations"></a>제한 사항

이 섹션에서는 배포 파이프라인의 제한 사항 대부분을 소개합니다.

* 작업 영역이  [프리미엄 용량](../admin/service-premium-what-is.md)에 있어야 합니다.

* Power BI [민감도 레이블](../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi)을 포함하는 보고서 및 대시보드와 같은 Power BI 항목은 배포할 수 없습니다.

* [증분 새로 고침](../admin/service-premium-incremental-refresh.md)을 사용하여 구성된 데이터 세트는 배포할 수 없습니다.

* 작업 영역 제한 사항의 목록은 [작업 영역 할당 제한 사항](deployment-pipelines-get-started.md#workspace-assignment-limitations)을 참조하세요.

* 데이터 세트 규칙 제한 사항의 목록은 [데이터 세트 규칙 제한 사항](deployment-pipelines-get-started.md#dataset-rule-limitations)을 참조하세요.

* 지원되지 않는 항목의 목록은 [지원되지 않는 항목](#unsupported-items)을 참조하세요.

## <a name="next-steps"></a>다음 단계

>[!div class="nextstepaction"]
>[배포 파이프라인 소개](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[배포 파이프라인 모범 사례](deployment-pipelines-best-practices.md)

>[!div class="nextstepaction"]
>[배포 파이프라인 시작](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[배포 파이프라인 문제 해결](deployment-pipelines-troubleshooting.md)