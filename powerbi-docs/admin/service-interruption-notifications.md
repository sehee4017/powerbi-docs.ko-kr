---
title: 서비스 중단 알림
description: Power BI 서비스 중단 또는 성능 저하가 발생하는 경우 메일 알림을 받는 방법을 알아봅니다.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/11/2020
ms.author: kfollis
ms.openlocfilehash: 344ce3b83bbb9922e0359e04e65c01a1a088bcb3
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83135398"
---
# <a name="service-interruption-notifications"></a>서비스 중단 알림

업무상 중요한 비즈니스 애플리케이션에 대한 가용성 인사이트가 있어야 합니다. Power BI는 서비스 중단 또는 성능 저하가 있을 경우 필요에 따라 메일을 받을 수 있도록 인시던트 알림을 제공합니다. Power BI의 99.9% SLA(서비스 수준 약정)에 따라 이와 같은 상황은 거의 발생하지 않지만, Microsoft는 고객에게 최신 정보를 제공하려고 합니다. 다음 스크린샷은 알림을 사용하도록 설정하는 경우 받게 될 메일 유형을 보여 줍니다.

![알림 메일 새로 고침](media/service-interruption-notifications/refresh-notification-email.png)

현재 Microsoft는 다음 _안정성 시나리오_에 대한 메일을 보냅니다.

- 보고서 열기 안정성
- 모델 새로 고침 안정성
- 쿼리 새로 고침 안정성

보고서 열기, 데이터 세트 새로 고침, 쿼리 실행 등의 작업에 ‘확장 지연’이 있는 경우 알림이 전송됩니다.  인시던트가 해결되면 후속 메일을 받게 됩니다.

> [!NOTE]
> 이 기능은 현재 Power BI Premium의 전용 용량에만 사용할 수 있습니다. 공유 용량이나 포함된 용량에는 사용할 수 없습니다.

## <a name="capacity-and-reliability-notifications"></a>용량 및 안정성 알림

Power BI Premium 용량의 리소스 사용률이 높은 상태가 지속되어 안정성에 영향을 줄 수 있다고 판단될 경우 알림 메일이 발송됩니다. 이러한 경우에는 보고서 열기, 데이터 세트 새로 고침, 쿼리 실행과 같은 작업이 오래 지연되는 경우가 포함됩니다. 

알림 메일에서는 다음을 포함하여 높은 리소스 사용률이 발생한 이유에 대한 정보를 안내합니다.

* 해당 데이터 세트의 데이터 세트 ID
* 작업 유형
* 높은 리소스 사용률과 관련된 CPU 시간

Power BI는 Power BI Premium 용량의 오버로드가 감지되는 경우에도 메일 알림을 발송합니다. 메일에서는 오버로드의 가능한 원인, 직전 10분 동안 로드를 생성한 작업, 각 작업이 생성한 로드의 양을 안내합니다. 


Premium 용량이 둘 이상 있는 경우에는 사용자가 리소스 집약적인 항목을 포함하는 작업 영역을 로드가 가장 적은 용량으로 이전하는 방안을 고려할 수 있도록 메일에서 오버로드된 기간의 해당 용량에 대한 정보도 안내합니다.

오버로드 메일 알림은 오버로드 임계값이 트리거된 경우에만 발송됩니다. 해당 Premium 용량의 로드가 임계값 미만으로 떨어져도 이를 안내하는 메일은 발송되지 않습니다.

다음 이미지는 샘플 알림 메일을 보여 줍니다.

![오버로드 용량 알림 메일](media/service-interruption-notifications/refresh-notification-email-2.png)


## <a name="enable-notifications"></a>알림 사용

Power BI 테넌트 관리자는 관리 포털에서 알림을 사용하도록 설정합니다.

1. 알림을 받아야 하는 메일 사용 보안 그룹을 식별하거나 만듭니다.

1. 관리 포털에서 **테넌트 설정**을 선택합니다. **도움말 및 지원 설정**에서 **서비스 중단 또는 인시던트에 대한 메일 알림 받기**를 확장합니다.

1. 알림을 사용하도록 설정하고, 보안 그룹을 입력한 다음, **적용**을 선택합니다.

    ![서비스 알림 사용](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> Power BI는 계정 no-reply-powerbi@microsoft.com에서 알림을 보냅니다. 알림이 스팸 또는 정크 폴더로 분류되지 않도록 이 계정이 허용 목록에 포함되어 있는지 확인합니다.

## <a name="next-steps"></a>다음 단계

[Power BI Pro 및 Power BI Premium 지원 옵션](service-support-options.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)
