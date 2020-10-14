---
title: 서비스 주체 개요
description: 서비스 주체 개요
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 6086185fb671b9f418ef2ec070b762020fbe8f75
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91989698"
---
서비스 주체는 Azure AD 애플리케이션이 콘텐츠 및 API Power BI 서비스에 액세스하도록 하는 데 사용할 수 있는 인증 방법입니다.

Azure AD(Azure Active Directory) 앱을 만들 때 [서비스 주체 개체](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)가 만들어집니다. 서비스 주체 개체(*서비스 주체*라고도 함)는 Azure AD가 앱을 인증하도록 합니다. 인증된 앱은 Azure AD 테넌트 리소스에 액세스할 수 있습니다.

인증을 위해 서비스 주체는 Azure AD 앱의 *애플리케이션 ID*와 다음 중 하나를 사용합니다.

* 애플리케이션 암호
* 인증서