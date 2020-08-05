---
title: Power BI 계획된 유지 관리
description: Power BI에 대한 계획된 유지 관리가 조직에 어떤 영향을 미치는지, 조직이 수행해야 할 수 있는 다음 단계가 무엇인지 관리자에게 보여 주는 정보입니다.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/19/2020
ms.author: kfollis
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: 13bbf23c075fb1f58c2af71ae0a082d4e539d023
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537691"
---
# <a name="power-bi-planned-maintenance"></a>Power BI 계획된 유지 관리

Power BI 서비스에 대한 계획된 유지 관리는 고객에게 신뢰할 수 있는 제품을 제공한다는 Microsoft의 약속을 지키기 위한 것입니다. 계획된 유지 관리를 수행하는 경우 조직에서 일정 시간 동안 Power BI 서비스를 사용할 수 없게 됩니다. 사용자가 Power BI 서비스에 액세스할 수 없으며 백그라운드 작업이 실패할 수 있습니다. 유지 관리 기간 후에는 서비스가 정상적으로 작동하고 대화형 및 백그라운드 작업이 모두 성공하게 됩니다.  

유지 관리는 조직에 미치는 영향을 최소화하기 위해 정규 업무 시간 외에 이루어집니다. 전 세계적으로 사용자를 보유하는 조직의 경우 "정규 업무 시간 외"가 다른 사용자에게 영향을 줄 수 있다는 것을 당사는 인식하고 있습니다. 사용자에게 영향을 끼쳐 죄송합니다. Power BI를 개선하고 이러한 유지 관리 기간을 최소화하기 위해 노력하고 있습니다.

조직이 영향을 받는 경우에는 사전 통지를 제공합니다. Microsoft 365 관리자는 Microsoft 365 메시지 센터에서 사전 통지를 확인할 수 있고 전자 메일도 받습니다. 또한 프리미어 지원 계약을 체결한 고객은 Microsoft 계정 팀을 통해 알림을 받습니다.

## <a name="actions-to-take-now"></a>지금 수행할 작업

* Microsoft 365 관리자는 Power BI 계획된 유지 관리에 대한 메시지를 [메시지 센터에서 확인](https://admin.microsoft.com/Adminportal/Home#/MessageCenter)해야 합니다. 메시지에 대해 알고 있어야 하지만 메시지 센터 액세스할 수 없는 사용자와 메시지를 공유합니다.
* Microsoft 365 관리자가 아닌 경우에는 IT 부서 또는 내부 지원 팀과 협력하여 향후 유지 관리에 대해 문의하세요.

## <a name="actions-to-take-when-maintenance-is-complete"></a>유지 관리가 완료될 때 수행할 작업

* 사용자는 열려 있는 모든 브라우저 창을 새로 고쳐야 합니다.
* Power BI Mobile 앱 사용자는 최신 버전을 사용 중인지 확인하고 앱에서 로그아웃한 다음 다시 로그인해야 합니다. 휴대폰의 앱 스토어를 확인하거나 [Power BI Mobile](https://powerbi.microsoft.com/mobile/) 페이지를 확인하세요.
* 로컬에서 또는 OneDrive 및 SharePoint 위치에서 조직의 시각적 개체를 사용하는 보고서를 편집하거나 게시한 고객은 조직 시각적 개체 저장소를 통해 시각적 개체를 다시 가져오거나 업데이트된 PBIX를 다운로드한 후 다시 게시해야 합니다. 조직 시각적 개체에 대한 자세한 내용은 [조직 시각적 개체](organizational-visuals.md)를 참조하세요.
* Excel에서 분석 기능을 사용하는 Excel 통합 문서가 새로 고쳐지지 않는 경우 연결 문자열을 업데이트하거나 해당 데이터 세트에 대한 ODC 연결을 다시 다운로드해야 할 수 있습니다. 자세한 내용은 [Excel에서 분석](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data)을 참조하세요.
* 유지 관리가 완료되면 콘텐츠에 포함된 Power BI에 대한 링크가 연결되지 않을 수 있습니다. 예를 들어 SharePoint 또는 Teams의 포함된 링크를 사용하면 사용자 오류가 발생할 수 있습니다. 이 문제를 해결하려면 Power BI에서 포함된 링크를 다시 생성한 다음 해당 링크를 사용하는 위치를 업데이트해야 합니다. 포함된 링크에 대한 자세한 내용은 [SharePoint Online에 보고서 웹 파트 포함](../collaborate-share/service-embed-report-spo.md) 및 [Power BI를 사용하여 Microsoft Teams에서 협업](../collaborate-share/service-collaborate-microsoft-teams.md)을 참조하십시오.

## <a name="next-steps"></a>다음 단계

* [서비스 중단 알림 사용](service-interruption-notifications.md)
* [메시지 센터에서 예정된 변경 내용 추적](https://docs.microsoft.com/microsoft-365/admin/manage/message-center?view=o365-worldwide)
