---
title: '타사 서비스: Power BI Desktop용 Facebook 커넥터'
description: '타사 서비스: Power BI Desktop용 Facebook 커넥터'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 882cddf7728a27e78056a35c14fde20f00678e33
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527705"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Power BI Desktop용 Facebook 커넥터 사용
**Power BI Desktop**의 Facebook 커넥터는 Facebook Graph API를 사용합니다. 이와 같이 기능 및 가용성은 시간에 따라 달라질 수 있습니다.

[Power BI Desktop에 대한 Facebook 커넥터에 대한 자습서](desktop-tutorial-facebook-analytics.md)를 참조할 수 있습니다.

> [!IMPORTANT]
> **Facebook 데이터 커넥터 알림 사용 중단:** 2020년 4월부터, Excel에서 Facebook의 데이터를 가져오고 새로 고치는 기능은 더 이상 제대로 작동하지 않습니다. 그때까지 Facebook ‘가져오기 및 변환(파워 쿼리)’ 커넥터를 사용할 수 있습니다.  해당 날짜 이후에는 Facebook에 연결할 수 없으며 오류 메시지가 표시됩니다. 예기치 않은 결과를 방지하려면 최대한 빨리 Facebook 커넥터를 사용하는 기존의 ‘가져오기 및 변환(파워 쿼리)’ 쿼리를 수정하거나 제거하는 것이 좋습니다. 


2015년 4월 30일에 Facebook의 Graph API v1.0이 만료되었습니다. Power BI는 Facebook 커넥터에 대해 내부적으로 Graph API를 사용하여 데이터에 연결하고 분석할 수 있도록 합니다.

2015년 4월 30일 이전에 작성된 쿼리는 더 이상 작동하지 않거나 더 적은 양의 데이터를 반환합니다. 2015년 4월 30일 이후부터 Power BI는 Facebook API에 대한 모든 호출에 v2.8을 활용합니다. 2015년 4월 30일 이전에 쿼리가 작성되었으며 이후에 사용하지 않은 경우 요청되는 새로운 권한 집합을 승인하기 위해 다시 인증해야 할 수 있습니다.

변경 내용에 따라 업데이트 릴리스를 시도하기는 하지만 API로 인해 생성하는 쿼리 결과에 영향을 주는 방식이 변경될 수 있습니다. 특정 쿼리가 더 이상 지원되지 않는 경우도 있습니다. 이 종속성으로 인해 이 커넥터를 사용할 때 쿼리 결과를 보장할 수 없습니다.

Facebook API의 변경 사항에 대한 자세한 내용은 [여기](https://developers.facebook.com/docs/apps/changelog#v2_0)를 참조하세요.

