---
title: 포함 파일
description: 포함 파일
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: ed87101fe7f5fadd24594d53bbd0ffb6f029faa4
ms.sourcegitcommit: 92b033ee7a6e36808371b247b7b41536cee6c2f6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "90012905"
---
## <a name="single-sign-on"></a>Single Sign-On

Azure SQL DirectQuery 데이터 세트가 서비스에 게시되면 Azure AD(Azure Active Directory) OAuth2를 사용하여 최종 사용자에 대한 SSO(Single Sign-On)를 사용하도록 설정할 수 있습니다.

SSO를 활성화하려면 데이터 세트에 대한 설정으로 이동하여 **데이터 원본** 탭을 열고 SSO 확인란을 선택합니다.

![Azure SQL DQ 대화 상자 구성](media/direct-query-sso/sso-dialog.png)

SSO 옵션이 활성화되어 있고 사용자가 데이터 원본을 기반으로 빌드된 보고서에 액세스하면 Power BI가 Azure SQL 데이터베이스 또는 데이터 웨어하우스 쿼리에 인증된 Azure AD 자격 증명을 보냅니다. 이 옵션을 사용하면 Power BI가 데이터 원본 수준에서 구성된 보안 설정을 적용할 수 있습니다.

SSO 옵션은 이 데이터 원본을 사용하는 모든 데이터 세트에 적용됩니다. 가져오기 시나리오에 사용되는 인증 방법에는 영향을 주지 않습니다.

> [!Note]
> Azure MFA(Multi-Factor Authentication)는 지원되지 않습니다. DirectQuery와 함께 SSO를 사용하려는 사용자는 MFA에서 제외해야 합니다.
