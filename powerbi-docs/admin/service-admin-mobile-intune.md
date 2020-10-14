---
title: Microsoft Intune으로 모바일 앱 구성
description: Microsoft Intune으로 Power BI 모바일 앱을 구성하는 방법 여기에는 애플리케이션을 추가 및 배포하는 방법도 포함됩니다. 또한 보안을 제어하기 위한 모바일 애플리케이션 정책을 만드는 방법도 포함됩니다.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a7a3e0382b80d46ddb41b3f5677763a1a08bf26d
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91981553"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Microsoft Intune으로 모바일 앱 구성

Microsoft Intune을 사용하여 조직에서는 디바이스 및 애플리케이션을 관리할 수 있습니다. iOS 및 Android용 Power BI 모바일 애플리케이션은 Intune과 통합됩니다. 이 통합을 통해 디바이스에서 애플리케이션을 관리하고 보안을 제어할 수 있습니다. 구성 정책을 통해 액세스 핀 요구, 애플리케이션에서 데이터가 처리되는 방식, 앱이 사용되고 있지 않을 때 애플리케이션 데이터를 암호화하는 것과 같은 항목을 제어할 수 있습니다.

Microsoft Power BI 모바일 앱을 사용하면 중요한 비즈니스 정보에 액세스할 수 있습니다. 조직의 모든 관리 디바이스 및 앱 비즈니스 데이터에 대한 대시보드 및 보고서를 보고 상호 작용할 수 있습니다. 지원되는 Intune 앱에 대한 자세한 내용은 [Microsoft Intune 보호 앱](/intune/apps/apps-supported-intune-apps)을 참조하세요.

## <a name="general-mobile-device-management-configuration"></a>일반 모바일 디바이스 관리 구성

이 문서에서는 Intune이 제대로 구성되어 있고 디바이스가 intune에 등록되었다고 가정합니다. 이 문서는 Microsoft Intune에 대한 전체 구성 가이드로 제공되지는 않았습니다. Intune에 대한 자세한 내용은 [Intune이란?](/intune/introduction-intune/)을 참조하세요.

Microsoft Intune은 Microsoft 365 내에서 MDM(모바일 디바이스 관리)과 공존할 수 있습니다. MDM을 사용하는 경우 디바이스는 MDM에 등록된 것으로 표시되지만 Intune에서 관리할 수 있습니다.

최종 사용자가 디바이스에서 Power BI 앱을 사용하려면 먼저 Intune 관리자가 앱을 Intune에 추가하고 최종 사용자에게 앱을 할당해야 합니다.

> [!NOTE]
> Intune을 구성한 후에는 iOS 또는 Android 디바이스에서 Power BI 모바일 앱의 백그라운드 데이터 새로 고침이 꺼집니다. 앱을 시작하면 Power BI에서 웹의 Power BI 서비스로부터 데이터를 새로 고칩니다.

## <a name="step-1-add-the-power-bi-app-to-intune"></a>1단계: Intune에 Power BI 앱 추가

Intune에 Power BI 앱을 추가하려면 다음 항목에서 제공하는 단계를 사용합니다.
- [Microsoft Intune에 iOS 스토어 앱 추가](/intune/apps/store-apps-ios)
- [Microsoft Intune에 Android 스토어 앱 추가](/intune/apps/store-apps-android)

## <a name="step-2-assign-the-app-to-your-end-users"></a>2단계: 최종 사용자에게 앱 할당

Microsoft Intune에 Power BI 앱을 추가한 후 사용자 및 디바이스에 앱을 할당할 수 있습니다. 디바이스가 Intune에서 관리되는지 여부에 상관없이 디바이스에 앱을 할당할 수 있습니다.

Power BI 앱을 사용자 및 디바이스에 할당하려면 [Microsoft Intune을 사용하여 그룹에 앱 할당](/intune/apps/apps-deploy)에 제공된 단계를 사용하세요.

## <a name="step-3-create-and-assign-app-protection-policies"></a>3단계: 앱 보호 정책 만들기 및 할당

앱 보호 정책(APP)은 관리되는 앱에서 조직의 데이터를 안전하게 보호하거나 유지되도록 하는 규칙입니다. 정책은 사용자가 "회사" 데이터를 액세스하거나 이동하려고 할 때 적용되는 규칙이거나, 사용자가 앱 내에 있을 때 금지되거나 모니터링되는 일련의 작업일 수 있습니다. 관리되는 앱은 앱 보호 정책이 적용되어 있으며 Intune을 통해 관리할 수 있는 앱입니다.

MAM(모바일 애플리케이션 관리) 앱 보호 정책을 사용하면 애플리케이션 내에서 조직의 데이터를 관리하고 보호할 수 있습니다. 중요한 데이터를 포함하는 회사 또는 학교 관련 앱인 MAM-WE(등록 없는 MAM)는 BYOD(Bring-your-own-device) 시나리오의 개인 디바이스를 비롯한 거의 모든 디바이스에서 관리할 수 있습니다. 자세한 내용은 [앱 보호 정책 개요](/intune/apps/app-protection-policy)를 참조하세요.

Power BI 앱에 대한 앱 보호 정책을 만들고 할당하려면 [앱 보호 정책을 만들고 할당하는 방법](/intune/apps/app-protection-policies)에서 제공하는 단계를 사용합니다.

## <a name="step-4-use-the-application-on-a-device"></a>4단계: 디바이스에서 애플리케이션 사용

관리되는 앱은 해당 앱에서 액세스할 수 있는 회사 데이터를 보호하기 위해 회사 지원팀이 설정할 수 있는 앱입니다. 디바이스에서 관리되는 앱에서 회사 데이터에 액세스하는 경우 앱이 예상과 약간 다르게 작동하는 것을 알 수 있습니다. 예를 들어 보호된 회사 데이터를 복사하고 붙여넣을 수 없거나, 해당 데이터를 특정 위치에 저장할 수 없습니다.

최종 사용자가 디바이스에서 Power BI 앱을 사용하는 방법을 이해하려면 다음 문서에서 제공하는 단계를 검토하세요.
- [iOS 디바이스에서 관리되는 앱 사용](/intune-user-help/use-managed-apps-on-your-device-ios#how-do-i-get-managed-apps)
- [Android 디바이스에서 관리되는 앱 사용](/intune-user-help/use-managed-apps-on-your-device-android)

## <a name="next-steps"></a>다음 단계

[앱 보호 정책을 만들고 할당하는 방법](/intune/app-protection-policies) 

[모바일 디바이스용 Power BI 앱](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)