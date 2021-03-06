---
title: 관리자가 Power BI Desktop 로그인 양식을 관리하는 방법
description: Power BI Desktop을 열 때 초기 로그인 양식을 관리하는 방법을 알아봅니다.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 12/14/2020
ms.openlocfilehash: 44cb8d3f646b0bd8e673c8ef3c1743b58bcbcaba
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491187"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>관리자: Power BI Desktop 로그인 양식 관리
Power BI Desktop이 처음 시작되면 로그인 양식이 표시됩니다. 계속하려면 정보를 입력하거나 Power BI에 로그인합니다. 관리자는 레지스트리 키를 사용하여 이 양식을 관리합니다. 

![Power BI Desktop용 초기 로그인 양식의 스크린샷.](media/desktop-admin-sign-in-form/sign-in-form.png)

관리자는 다음 레지스트리 키를 사용하여 로그인 양식을 사용하지 않도록 설정합니다. 글로벌 정책을 사용하여 전체 조직에 푸시할 수도 있습니다.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
구성에 따라 일부 고객에게 성공한 다음 키를 사용해 볼 수도 있습니다.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

값 0은 대화 상자를 사용하지 않도록 설정합니다.




궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)

