---
title: 배포 파이프라인 개요
description: Power BI에서 배포 파이프라인이란 무엇인지 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: 5522d84cab235270a2eb368be02cfa0fb4e5eaa9
ms.sourcegitcommit: 10c5b6cd5e7070f96de8a9f1d9b95f3d242ac7f2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86557144"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>배포 파이프라인 소개(미리 보기)

오늘날의 세계에서 분석은 거의 모든 조직에서 의사 결정을 수립하는 데 중요한 부분입니다. 분석 도구로서의 사용이 증가함에 따라 Power BI는 더 많은 데이터를 사용하고 더 매력적으로 보이며 사용자에게 더 친숙해져야 합니다. 그러나 무엇보다 Power BI는 항상 사용 가능하고 신뢰할 수 있어야 합니다. 이러한 요구 사항을 충족하기 위해 BI 작성자는 효과적으로 공동 작업을 수행해야 합니다.

배포 파이프라인은 엔터프라이즈의 BI 작성자가 프리미엄 용량을 사용하여 조직 콘텐츠의 수명 주기를 관리할 수 있도록 하는 효율적이고 재사용 가능한 도구입니다. 이를 통해 최종 사용자가 사용하기 전에 보고서, 대시보드 및 데이터 세트와 같은 Power BI 콘텐츠를 개발 및 테스트할 수 있습니다.

이 도구는 다음 세 단계로 구성된 파이프라인으로 디자인되었습니다.

* **<a name="development"></a>개발**
    
    이 단계는 동료 작성자와 함께 새 콘텐츠를 디자인, 빌드 및 업로드하는 데 사용됩니다. 이는 배포 파이프라인의 첫 번째 단계입니다.

* **<a name="test"></a>테스트**

    콘텐츠를 업로드하고 개발 단계에서 모든 변경 내용을 적용한 후에는 테스트를 위해 콘텐츠를 이 단계로 이동할 수 있습니다. 다음은 테스트 환경에서 수행할 수 있는 작업의 세 가지 예입니다.

    * 테스터 및 검토자와 콘텐츠 공유

    * 보다 대용량의 데이터를 사용하여 로드 및 테스트 실행

    * 앱을 테스트하여 최종 사용자에게 표시되는 방식을 확인

* **<a name="production"></a>프로덕션**

    콘텐츠를 테스트한 후 프로덕션 단계를 사용하여 콘텐츠의 최종 버전을 조직 전체의 비즈니스 사용자와 공유할 수 있습니다.

![개발, 테스트, 프로덕션이라는 세 단계를 모두 채운 작업 배포 파이프라인의 스크린샷](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>다음 단계

>[!div class="nextstepaction"]
>[배포 파이프라인 시작](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[배포 파이프라인 프로세스 이해](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[배포 파이프라인 문제 해결](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[배포 파이프라인 모범 사례](deployment-pipelines-best-practices.md)