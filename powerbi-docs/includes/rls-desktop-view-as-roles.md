---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464409"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Power BI Desktop 내에서 역할 유효성 검사
역할을 만든 후에 Power BI Desktop 내에서 역할의 결과를 테스트합니다.

1. **모델링** 탭에서 **역할로 보기**를 선택합니다. 

    ![역할로 보기 선택](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    **역할로 보기** 창이 표시되고, 여기서 직접 만든 역할을 볼 수 있습니다.

    ![역할로 보기 창](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. 만든 역할을 선택한 다음, **확인**을 선택하여 해당 역할을 적용합니다. 

   보고서는 해당 역할과 관련된 데이터를 렌더링합니다.

4. 또한 **다른 사용자**를 선택하고 지정된 사용자를 제공할 수 있습니다. 

    ![다른 사용자 선택](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   Power BI 서비스 및 Power BI Report Server가 사용하는 UPN(사용자 계정 이름)을 제공하는 것이 가장 좋습니다.

   Power BI Desktop 내에서 **다른 사용자**는 DAX 식을 기반으로 하는 동적 보안을 사용하는 경우에만 다른 결과가 표시됩니다. 

5. **확인**을 선택합니다. 

   해당 사용자가 볼 수 있는 내용에 따라 보고서가 렌더링됩니다.



