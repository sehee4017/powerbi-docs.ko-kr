---
title: 작업 영역에서 콘텐츠를 구성하는 방법
description: 작업 영역 및 작업 영역 역할에 대해 알아봅니다.
author: mihart
ms.author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 10/09/2020
ms.custom: licensing support
LocalizationGroup: Consumers
ms.openlocfilehash: 2341306672da4c1923dc5bc97f0d1537604a1a7c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96398709"
---
# <a name="collaborate-in-workspaces"></a>작업 영역에서 공동 작업

 *작업 영역* 은 특정 콘텐츠에서 동료와 공동으로 작업하는 위치입니다. 대시보드 및 보고서의 컬렉션을 저장하는 작업 영역은 Power BI *디자이너* 에서 만들어집니다. 그런 다음, 디자이너는 동료와 작업 영역을 공유할 수 있습니다. 디자이너는 대시보드 및 보고서의 컬렉션을 *앱* 에 묶어서 전체 커뮤니티, 조직 또는 특정 사용자나 그룹에 배포할 수도 있습니다. *템플릿 앱* 이라고 하는 특정 유형의 앱은 앱이 설치될 때 작업 영역을 만듭니다. [앱에 대해 자세히 알아봅니다](end-user-apps.md). 

 또한 Power BI 서비스를 사용하는 모든 사용자에게는 **내 작업 영역** 이 있습니다.  내 작업 영역은 콘텐츠를 직접 만들 수 있는 개인 샌드박스입니다.

 Power BI **홈** 에서 작업 영역을 보거나 왼쪽 탐색 창에서 **작업 영역** 을 선택하여 볼 수 있습니다.

 ![두 가지 유형의 작업 영역이 표시된 탐색 창을 보여 주는 스크린샷.](media/end-user-workspaces/power-bi-home-workspace.png)

## <a name="types-of-workspaces"></a>작업 영역 유형
**내 작업 영역** 에는 소유하고 만드는 모든 콘텐츠가 저장됩니다. 고유한 콘텐츠에 대한 개인 샌드박스 또는 작업 영역으로 생각하면 됩니다. 많은 Power BI *비즈니스 사용자* 는 새 콘텐츠를 만드는 일이 업무에 포함되어 있지 않으므로 **내 작업 영역** 이 비어 있는 상태로 유지됩니다. 정의상 *비즈니스 사용자* 는 다른 사용자가 만든 데이터를 사용하고 해당 데이터를 이용해 비즈니스 의사 결정을 내립니다. 콘텐츠를 만드는 경우 대신 [디자이너를 위한 Power BI 문서](../create-reports/index.yml)를 읽어 보시기 바랍니다.

**작업 영역** 에는 특정 앱의 모든 콘텐츠가 포함됩니다. ‘디자이너'는 앱을 만들 때 해당 앱을 활용하는 데 필요한 모든 콘텐츠를 함께 묶습니다. 콘텐츠에는 대시보드, 보고서 및 데이터 세트가 포함될 수 있습니다. 모든 앱에 이러한 세 가지 콘텐츠가 포함되어 있는 것은 아닙니다. 앱에 따라 대시보드가 하나만, 각 콘텐츠 유형이 3개씩 또는 보고서가 20개 포함되어 있을 수도 있습니다. ‘디자이너'가 앱에 무엇을 포함하는지에 따라 달라집니다.  일반적으로 *비즈니스 사용자* 와 공유되는 앱 작업 영역에는 데이터 세트가 포함되지 않습니다.

아래의 Fig sales 작업 영역에는 세 개의 보고서와 하나의 대시보드가 있습니다. 

![작업 영역 메뉴 아래 표시되는 작업 영역에 보고서와 대시보드가 포함된 것을 보여 주는 스크린샷.](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="permissions-in-the-workspaces"></a>작업 영역의 권한

액세스 권한은 팀이 공동 작업할 수 있도록 작업 영역에서 수행할 수 있는 작업을 결정합니다.  새 작업 영역에 대한 액세스 권한을 부여할 때 *디자이너* 는 작업 영역 역할 **보기 관리자**, **멤버**, **참가자** 또는 **관리자** 중 하나에 개인 또는 그룹을 추가합니다. 


Power BI *비즈니스 사용자* 는 일반적으로 **뷰어** 역할을 사용하여 작업 영역에서 상호 작용합니다. 그러나 *디자이너* 에서 **구성원** 또는 **기여자** 역할에 할당할 수도 있습니다. 보기 권한자 역할을 통해 다른 사용자가 만들고 공유한 콘텐츠(대시보드, 보고서, 앱)를 보고 상호 작용할 수 있습니다. 또한 보기 권한자 역할은 기본 데이터 세트에 액세스할 수 없으므로 콘텐츠와 상호 작용하는 안전한 방법이며 기본 데이터가 "손상"되지 않습니다.


뷰어 역할을 사용하여 *비즈니스 사용자* 로 수행할 수 있는 작업에 대한 자세한 목록은 [비즈니스 사용자를 위한 Power BI 기능](end-user-features.md)을 참조하세요.


### <a name="workspace-permissions-and-roles"></a>작업 영역 권한 및 역할

다음은 4가지 역할의 기능입니다. 관리자, 구성원, 참가자 및 뷰어. 보기와 상호 작용을 제외한 모든 기능에는 Power BI Pro 라이선스가 필요합니다.

[!INCLUDE[power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

## <a name="licensing-workspaces-and-capacity"></a>라이선스, 작업 영역 및 용량
또한 라이선스는 작업 영역에서 수행할 수 있는 작업과 수행할 수 없는 작업을 결정하는 역할을 합니다. 사용자가 Power BI *Pro* 라이선스를 가지거나 작업 영역을 프리미엄 용량에 저장하려면 많은 기능이 필요합니다. 

*비즈니스 사용자* 는 평가판 라이선스로 작업하는 경우가 많습니다. [라이선스에 대해 자세히 알아봅니다](end-user-license.md). 콘텐츠가 프리미엄 용량에 저장되지 않은 경우 비즈니스 사용자는 액세스할 수 없습니다.

작업 영역이 프리미엄 용량에 저장되는 경우 *비즈니스 사용자* 는 해당 작업 영역의 콘텐츠를 보고 상호 작용할 수 있습니다. 다이아몬드 아이콘은 프리미엄 용량에 저장된 작업 영역을 식별합니다.

![선택한 작업 영역](media/end-user-workspaces/power-bi-diamonds.png) 자세한 내용은 [사용 중인 라이선스 확인](end-user-license.md)을 참조하세요.



## <a name="next-steps"></a>다음 단계
* [Power BI의 앱](end-user-apps.md)    

* 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)

