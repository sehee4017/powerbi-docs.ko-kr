---
title: 데이터 세트 및 데이터 흐름 인증 설정(미리 보기)
description: 조직에서 데이터 세트 및 데이터 흐름 인증 프로세스를 설정하는 방법을 알아봅니다.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/22/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 1fc33b48613335f4fba97921e3d528175eb2a47f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81267848"
---
# <a name="set-up-dataset-and-dataflow-certification-preview"></a>데이터 세트 및 데이터 흐름 인증 설정(미리 보기)

조직은 중요한 정보의 신뢰할 수 있는 소스인 데이터 세트와 데이터 흐름을 인증할 수 있습니다.

Power BI 테넌트 관리자가 조직의 인증 프로세스를 설정해야 합니다. 이것은 다음을 의미합니다.
* 테넌트에서 인증 사용
* 데이터 세트와 데이터 흐름을 인증할 수 있는 권한이 있는 그룹 및 사용자 목록 정의
* 데이터 세트의 경우 조직의 데이터 세트 인증 정책 URL 제공(있는 경우)

데이터 세트 및 데이터 흐름 인증은 데이터 세트 및 데이터 흐름 ‘보증’의 일부입니다.  자세한 내용은 [데이터 세트 보증](../service-datasets-promote.md) 및 [데이터 흐름 보증](../transform-model/service-dataflows-promote-certify.md)을 참조하세요.


## <a name="set-up-certification"></a>인증 설정

1. 관리 포털에서 테넌트 설정으로 이동합니다.
1. 설정 내보내기 및 공유 섹션에서 인증 섹션을 펼칩니다.

   ![데이터 세트 및 데이터 흐름 인증 설정](media/service-admin-setup-certification/service-admin-certification-setup-dialog.png)

1. 토글을 **사용**으로 설정합니다.
1. 데이터 세트 인증의 경우 조직에 게시된 인증 정책이 있으면 해당 URL을 여기에 입력할 수 있습니다. 그러면 **데이터 흐름 보증 설정 대화 상자**의 인증 섹션에 있는 [자세한 정보](../service-datasets-promote.md#request-dataset-certification) 링크가 됩니다. 
1. 데이터 세트와 데이터 흐름을 인증할 수 있는 권한이 있는 사용자 또는 그룹을 지정합니다. 권한 있는 인증자는 [데이터 세트](../service-datasets-promote.md#request-dataset-certification) 또는 [데이터 흐름](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow) 보증 설정 대화 상자의 인증 섹션에서 인증 단추를 사용할 수 있습니다.
1. **적용**을 클릭합니다.

## <a name="next-steps"></a>다음 단계
* [데이터 세트 승격](../service-datasets-promote.md)
* [데이터 세트 인증](../service-datasets-certify.md)
* [데이터 흐름 승격](../transform-model/service-dataflows-promote-certify.md#promote-a-dataflow)
* [데이터 흐름 인증](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow)
* 질문이 있으신가요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
