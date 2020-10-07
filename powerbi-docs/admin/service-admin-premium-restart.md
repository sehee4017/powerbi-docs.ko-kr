---
title: Power BI Premium 용량 다시 시작
description: 성능 문제를 해결하는 Power BI Premium 용량을 다시 시작하는 방법에 대해 알아봅니다.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 03/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 0f237efece8403730ea7790d45bca6f5169e53fd
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91599530"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Power BI Premium 용량 다시 시작

Power BI 관리자는 프리미엄 용량을 다시 시작해야 할 수도 있습니다. 이 문서에서는 용량을 다시 시작하는 방법을 설명하고 다시 시작 및 성능에 대한 몇 가지 질문을 다룹니다.

## <a name="why-does-power-bi-provide-this-option"></a>Power BI가 이 옵션을 제공하는 이유는?

Power BI는 사용자에게 막대한 양의 데이터에 대한 복잡한 분석을 수행할 수 있는 기능을 제공합니다. 안타깝게도 사용자는 작업으로 Power BI 서비스에 오버로드되거나 지나치게 복잡한 쿼리를 작성하거나 순환 참조를 만드는 등의 성능 문제가 발생할 수 있습니다.

Power BI 공유 용량은 파일 크기, 새로 고침 일정 및 기타 서비스 측면에 제한을 함으로써 이러한 경우로부터 어느 정도 보호 기능을 제공합니다. 반면 Power BI Premium 용량에서는 이러한 제한의 대부분이 발생합니다. 결과적으로 잘못된 DAX 식 또는 매우 복잡한 모델을 가진 단일 보고서는 심각한 성능 문제가 발생할 수 있습니다. 처리될 때 보고서는 용량에서 사용 가능한 모든 리소스를 소비할 수 있습니다. 

Power BI는 프리미엄 용량 사용자를 이러한 문제로부터 보호하는 방법을 지속적으로 개선하고 있습니다. 또한 용량이 초과될 때와 그 이유를 분석할 수 있는 도구를 통해 관리자에게 권한을 부여하고 있습니다. 자세한 내용은 [단기 교육 세션](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be) 및 [긴 교육 세션](https://powerbi.tips/2018/07/)을 참조하세요. 동시에, 중요한 문제가 발생하는 경우 이를 완화하는 기능이 필요합니다. 이러한 문제를 완화하는 가장 빠른 방법은 용량을 다시 시작하는 것입니다.

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>다시 시작 프로세스는 안전한가요? 데이터가 손실되나요?

용량에 저장된 모든 데이터, 정의, 보고서 및 대시보드는 다시 시작한 후에도 완전히 그대로 유지됩니다. 용량을 다시 시작하는 경우 새로 고침 엔진에서 진행 중인 예약 및 임시 새로 고침이 일시적으로 중지되었다가 대부분의 경우 Power BI에서 기본 제공되는 새로 고침 재시도 논리로 인해 다시 시작됩니다. 용량을 사용할 수 있게 되면 서비스가 영향을 받는 새로 고침을 다시 시도합니다. 다시 시작 프로세스 중에 사용자 인터페이스에서 새로 고침 상태가 변경되지 않을 수 있습니다. 

용량과 상호 작용하는 사용자는 다시 시작 프로세스 중에 저장되지 않은 작업을 잃게 됩니다. 사용자는 다시 시작이 완료된 후에 브라우저를 새로 고쳐야 합니다.

## <a name="how-do-i-restart-a-capacity"></a>용량을 다시 시작하는 방법은?

다음 단계에 따라 용량을 다시 시작합니다.

1. Power BI 관리 포털의 **용량 설정** 탭에서 용량으로 이동합니다. 

1. **CapacityRestart** *기능 플래그*를 용량 URL에 추가합니다. `https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true`.

1. **고급 설정** > **용량 다시 시작**에서 **용량 다시 시작**을 선택합니다.

    ![용량 다시 시작](media/service-admin-premium-restart/restart-capacity.png)

1. **용량 다시 시작** 대화 상자에서 **예, 용량 다시 시작**을 선택합니다.

    ![다시 시작 확인](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>앞으로 문제가 발생하지 않도록 하는 방법은?

문제를 방지하는 가장 좋은 방법은 사용자에게 효율적인 데이터 모델링에 대해 교육하는 것입니다. 자세한 내용은 [교육 세션](https://powerbi.tips/2018/07/)을 참조하세요.

또한 정기적으로 [용량을 모니터링](service-admin-premium-monitor-capacity.md)하여 근본적인 문제를 나타내는 추세를 찾아보는 것이 좋습니다. 용량을 보다 효율적으로 관리할 수 있도록 모니터링 앱과 기타 도구의 정기적인 릴리스를 계획하고 있습니다.

## <a name="next-steps"></a>다음 단계

[Power BI Premium이란?](service-premium-what-is.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
