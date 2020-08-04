---
title: Power BI를 사용하여 Microsoft Teams에서 협업
description: Microsoft Teams 채널 및 채팅에서 대화형 Power BI 콘텐츠를 쉽게 공유하고 협업할 수 있습니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 07/22/2020
ms.openlocfilehash: 17a0879dac416a98d214ed11861947cb2c311487
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254211"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Power BI를 사용하여 Microsoft Teams에서 협업

Microsoft Teams 채널 및 채팅의 대화형 Power BI 콘텐츠를 공유하고 협업하기 위한 다양한 옵션이 있습니다. 

- Microsoft Teams의 **Power BI** 탭을 사용하여 [Microsoft Teams 채널 및 채팅에 대화형 보고서를 포함](service-embed-report-microsoft-teams.md)할 수 있습니다. **Power BI** 탭에서는 동료가 팀의 데이터를 찾고 팀 채널 내에서 데이터에 대해 논의할 수 있습니다. 
- 보고서, 대시보드 및 앱의 링크를 Microsoft Teams 메시지 상자에 붙여넣으면 [링크 미리 보기](service-teams-link-preview.md)를 만들 수 있습니다. 링크 미리 보기는 링크에 관한 정보를 표시합니다. 
- Power BI 서비스에서 보고서 및 대시보드를 볼 때 [Teams에 공유](service-share-report-teams.md)를 사용하여 Teams에서 빠르게 대화를 시작합니다.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Teams 채널에 포함된 Power BI 보고서의 스크린샷.":::

## <a name="requirements"></a>요구 사항

일반적으로 Power BI가 Microsoft Teams에서 작동하려면 다음 요소를 확인합니다.

- 사용자에게 Power BI Pro 라이선스가 있거나, 보고서가 Power BI 라이선스가 있는 [Power BI 프리미엄 용량(EM 또는 P SKU)](../admin/service-premium-what-is.md)에 포함되어 있습니다.
- 사용자가 Power BI 서비스에 로그인하여 Power BI 라이선스를 활성화했습니다.
- 사용자가 Microsoft Teams의 **Power BI** 탭을 사용하기 위한 요구 사항을 충족합니다.

Microsoft Teams에서 **Power BI** 탭을 사용하려면 다음 요소를 확인합니다.

- Microsoft Teams에 **Power BI** 탭이 있습니다.
- **Power BI** 탭을 사용하여 Microsoft Teams에서 보고서를 추가하려면 보고서를 호스트하는 작업 영역에서 보기 권한자 이상의 역할이 있어야 합니다. 다른 역할에 대한 자세한 내용은 [새 작업 영역의 역할](service-new-workspaces.md#roles-in-the-new-workspaces)을 참조하세요.
- Microsoft Teams의 **Power BI** 탭에서 보고서를 보려면 사용자에게 보고서를 볼 수 있는 권한이 있어야 합니다.
- 사용자는 채널 및 채팅에 대한 액세스 권한이 있는 Microsoft Teams 사용자여야 합니다.

Power BI에서 **Teams에 공유** 기능을 사용하려면 다음 설정을 확인합니다.

- Power BI 관리자가 Power BI 관리 포털에서 **Teams에 공유** 테넌트 설정을 사용하지 않도록 설정하지 않았습니다. 해당 설정을 사용하면 조직이 **Teams에 공유** 단추를 숨길 수 있습니다. 자세한 내용은 [Power BI 관리 포털](../admin/service-admin-portal.md#share-to-teams-tenant-setting) 문서를 참조하세요.

## <a name="grant-access-to-reports"></a>보고서에 액세스 권한 부여

Microsoft Teams에 보고서를 포함하거나 항목에 대한 링크를 보내는 경우 사용자에게 보고서를 볼 수 있는 권한이 자동으로 부여되지 않습니다. [사용자가 Power BI에서 보고서를 보도록 허용](service-share-dashboards.md)해야 합니다. 해당 팀의 Microsoft 365 그룹을 사용하면 더 쉽습니다.

> [!IMPORTANT]
> Power BI 서비스 내에서 보고서를 볼 수 있는 사람이 누구인지 확인하고 목록에 없는 사람에게 액세스 권한을 부여합니다.

팀의 모든 사용자가 보고서에 액세스할 수 있도록 하는 한 가지 방법은 보고서를 단일 작업 영역에 저장하고 팀의 Microsoft 365 그룹에 액세스 권한을 부여하는 것입니다.

## <a name="known-issues-and-limitations"></a>알려진 문제 및 제한 사항

- Power BI는 Microsoft Teams에서 지원하는 것과 동일한 지역화된 언어를 지원하지 않습니다. 결과적으로 포함된 보고서 내에 적절한 지역화가 표시되지 않을 수 있습니다.
- Power BI 대시보드는 Microsoft Teams의 **Power BI** 탭에 포함될 수 없습니다.
- Power BI 라이선스 또는 보고서에 액세스할 권한이 없는 사용자에게는 "콘텐츠를 사용할 수 없습니다"라는 메시지가 표시됩니다.
- Internet Explorer 10을 사용하는 경우 문제가 발생할 수 있습니다. <!--You can look at the [browsers support for Power BI](../consumer/end-user-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL 필터](service-url-filters.md)는 Microsoft Teams의 **Power BI** 탭에서 지원되지 않습니다.
- 국가 클라우드에서는 새 **Power BI** 탭을 사용할 수 없습니다. 새 작업 영역 환경 또는 보고서를 지원하지 않는 이전 버전을 Power BI 앱에서 사용할 수 있습니다.
- 탭이 저장되면 탭 설정을 통해 탭 이름을 변경할 수 없습니다. **이름 바꾸기** 옵션을 사용하여 변경합니다.
- 링크 미리 보기 서비스에서 Single Sign-On이 지원되지 않습니다.
- 링크 미리 보기는 모임 채팅 또는 프라이빗 채널에서 작동하지 않습니다.

## <a name="next-steps"></a>다음 단계

- [Microsoft Teams에 Power BI 콘텐츠 포함](service-embed-report-microsoft-teams.md)
- [Microsoft Teams에서 Power BI 링크 미리 보기 가져오기](service-teams-link-preview.md)
- [Power BI 서비스에서 Teams에 직접 공유](service-share-report-teams.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다](https://community.powerbi.com/).
