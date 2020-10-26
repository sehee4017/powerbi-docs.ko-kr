---
title: 서비스 주체 앱 만들기
description: 서비스 주체 앱 만들기
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 80886eab6de6c125d0361b326f5d31d2b3bb35e5
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91524528"
---
1. [Microsoft Azure](https://ms.portal.azure.com/#allservices)에 로그인합니다.

2. **앱 등록** 을 검색하고 **앱 등록** 링크를 클릭합니다.

    ![azure 앱 등록](media/embedded-service-principal/azure-app-registration.png)

3. **새 등록** 을 클릭합니다.

    ![앱 등록](media/embedded-service-principal/new-registration.png)

4. 필수 정보를 입력합니다.
    * **이름** - 애플리케이션의 이름을 입력합니다.
    * **지원되는 계정 유형** - 지원되는 계정 유형을 선택합니다.
    * (선택 사항) **리디렉션 URI** - 필요한 경우 URI를 입력합니다.

5. **등록** 을 클릭합니다.

6. 등록한 후에는 **개요** 탭에서 *애플리케이션 ID* 를 확인할 수 있습니다. 나중에 사용할 수 있도록 *애플리케이션 ID* 를 복사하여 저장합니다.

    ![스크린샷은 개요 탭에서 애플리케이션 ID를 가져올 수 있는 위치를 보여줍니다.](media/embedded-service-principal/application-id.png)