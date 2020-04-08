---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621593"
---
서비스 주체는 Azure AD 애플리케이션이 콘텐츠 및 API Power BI 서비스에 액세스하도록 하는 데 사용할 수 있는 인증 방법입니다.

Azure AD(Azure Active Directory) 앱을 만들 때 [서비스 주체 개체](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)가 만들어집니다. 서비스 주체 개체(*서비스 주체*라고도 함)는 Azure AD가 앱을 인증하도록 합니다. 인증된 앱은 Azure AD 테넌트 리소스에 액세스할 수 있습니다.

인증을 위해 서비스 주체는 Azure AD 앱의 *애플리케이션 ID*와 다음 중 하나를 사용합니다.
* 애플리케이션 암호
* 인증서