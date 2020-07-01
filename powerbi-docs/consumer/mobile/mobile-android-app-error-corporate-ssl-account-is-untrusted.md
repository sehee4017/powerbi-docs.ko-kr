---
title: “회사 SSL 인증서를 신뢰할 수 없습니다” 수정
description: Power BI용 Android 앱에 로그인할 때 "회사 SSL 인증서를 신뢰할 수 없기 때문에 인증할 수 없습니다."라는 메시지가 표시될 수 있습니다.
.": ''
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 85e295b2320f8aecca2176149ce37c0a25ad2bd2
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237459"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>“회사 SSL 인증서를 신뢰할 수 없습니다.” 수정 - Power BI
Microsoft Power BI용 Android 모바일 앱에 로그인할 때 "이 디바이스에서 회사 SSL 인증서를 신뢰할 수 없기 때문에 인증할 수 없습니다."라는 메시지가 표시될 수 있습니다. 회사 IT 관리자에게 문의하세요." 

일반적으로 필요한 작업은 Android 디바이스의 운영 체제에 따라 다르지만 이 오류가 발생할 수 있는 몇 가지 다른 문제가 있습니다.

## <a name="on-android-7-or-later"></a>Android 7 이상
**Chrome** 앱의 업데이트를 찾아 설치합니다.

## <a name="on-android-6-and-earlier"></a>Android 6 이하
디바이스에 업데이트된 버전의 System Webview가 필요할 수 있습니다. 디바이스에 설치되어 있을 수 있으므로 **업데이트**를 클릭만 하면 됩니다.

디바이스에 System Webview가 설치되어 있지 않은 경우

1. Android 디바이스에서 Power BI를 닫습니다.
2. Google Play 스토어를 열고 Google Inc.의 **System Webview**를 검색합니다.
3. 설치합니다.
4. Power BI 앱을 다시 시작하고 로그인합니다.

## <a name="time-zone-settings"></a>표준 시간대 설정
디바이스의 시간대 설정이 잘못되었을 수 있습니다. 

**설정** > **시스템** > **날짜 및 시간**으로 이동하여 확인합니다.

## <a name="custom-authentication-server"></a>사용자 지정 인증 서버
사용자 지정 인증 서버를 사용하는 경우 회사 인증 서버의 SSL 인증서가 유효하지 않을 수 있습니다. [이 문서](https://support.microsoft.com/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce)의 지침에 따라 조직의 IT와 함께 회사 인증 서버 구성을 테스트하세요.

## <a name="next-steps"></a>다음 단계
* Android 앱 스토어에서 [Android 앱 다운로드](https://go.microsoft.com/fwlink/?LinkID=544867)
* 질문이 있으신가요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/) 

