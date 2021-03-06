---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "71409373"
---
## <a name="faq"></a>FAQ
**질문:** 이전에 Power BI 서비스에서 데이터 세트에 대한 역할과 규칙을 만든 경우 어떻게 되나요? 아무 작업도 수행하지 않아도 계속 작동합니까?  
**답변:** 아니요, 시각적 개체가 제대로 렌더링되지 않습니다. Power BI Desktop 내 역할 및 규칙을 다시 만든 다음, Power BI 서비스에 게시해야 합니다.

**질문:** Analysis Services 데이터 원본에 대해 이러한 역할을 만들 수 있나요?  
**답변:** 데이터를 Power BI Desktop으로 가져온 경우 사용할 수 있습니다. 라이브 연결을 사용하는 경우 Power BI 서비스 내에서 RLS를 구성할 수 없습니다. 이것은 Analysis Services 모델 온-프레미스 내에서 정의됩니다.

**질문:** RLS를 사용하여 내 사용자가 액세스할 수 있는 열이나 측정값을 제한할 수 있나요?  
**답변:** 아니요, 사용자가 특정 데이터 행에 대한 액세스 권한이 있는 경우 해당 행의 모든 데이터 열을 볼 수 있습니다.

**질문:** RLS를 사용하면 자세한 데이터를 숨기고 시각적 개체에서 요약된 데이터에 대한 액세스 권한을 부여할 수 있나요?  
**답변:** 아니요, 데이터 개별 행의 보안을 유지할 수 있지만 사용자는 요약된 데이터 또는 세부 정보를 확인할 수 있습니다.

**질문:** 내 데이터 원본에 이미 보안 역할이 정의되어 있습니다(예: SQL Server 역할 또는 SAP BW 역할). 이러한 역할과 RLS 사이에는 어떤 관계가 있나요?  
**답변:** 데이터를 가져오는지 아니면 DirectQuery를 사용하는지에 따라 달라집니다. Power BI 데이터 세트로 데이터를 가져오는 경우에는 데이터 원본의 보안 역할이 사용되지 않습니다. 이 경우 RLS를 정의하여 Power BI에서 연결하는 사용자를 위한 보안 규칙을 적용해야 합니다. DirectQuery를 사용하는 경우에는 데이터 원본의 보안 역할이 사용됩니다. 사용자가 보고서를 열면 Power BI가 기본 데이터 원본으로 쿼리를 전송하고, 해당 데이터 원본은 사용자의 자격 증명에 따라 데이터에 보안 규칙을 적용합니다.
