---
title: Power BI에서 웹에 게시
description: Power BI 웹에 게시를 사용하면 대화형 Power BI 콘텐츠를 블로그 게시, 웹 사이트, 이메일 또는 소셜 미디어에 쉽게 포함할 수 있습니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 09/18/2020
LocalizationGroup: Share your work
ms.openlocfilehash: cea4af4a8c265e5195a8239bd592c8734e332255
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2020
ms.locfileid: "91375169"
---
# <a name="publish-to-web-from-power-bi"></a>Power BI에서 웹에 게시

Power BI **웹에 게시** 옵션을 사용하면 대화형 Power BI 콘텐츠를 블로그 게시, 웹 사이트, 이메일 또는 소셜 미디어에 쉽게 포함할 수 있습니다. 또한 게시된 시각적 개체를 편집, 업데이트, 새로 고침 또는 공유 중지할 수 있습니다.

> [!WARNING]
> **웹에 게시**를 사용하는 경우 인터넷에 있는 모든 사용자가 게시된 보고서나 시각적 개체를 볼 수 있습니다. 보기에는 인증이 필요하지 않습니다. 여기에는 보고서에서 집계하는 세부 정보 수준 데이터 보기가 포함됩니다. 보고서를 게시하기 전에 데이터와 시각화를 공개적으로 공유할 수 있는지 확인합니다. 기밀 또는 소유 정보는 게시하지 마세요. 확실하지 않은 경우 게시하기 전에 조직의 정책을 확인합니다.

>[!Note]
>콘텐츠를 내부 포털 또는 웹 사이트에 안전하게 포함할 수 있습니다. [포함](service-embed-secure.md) 또는 [SharePoint Online에 포함](service-embed-report-spo.md) 옵션을 사용합니다. 이러한 옵션을 사용하면 사용자가 내부 데이터를 볼 때 모든 권한과 데이터 보안이 적용됩니다.

## <a name="create-embed-codes-with-publish-to-web"></a>웹에 게시를 사용하여 embed 태그 만들기

**웹에 게시**는 개인 또는 그룹 작업 영역에서 편집할 수 있는 보고서에 사용할 수 있습니다.  사용자와 공유되는 보고서 또는 행 수준 보안을 사용하여 데이터를 보호하는 보고서에는 사용할 수 없습니다. **웹에 게시**가 지원되지 않는 경우의 전체 목록은 아래 [**제한**](#limitations) 섹션을 참조하세요. **웹에 게시**를 사용하기 전에 이 문서의 앞부분에 있는 **경고**를 확인해 보세요.

다음 단계는 **웹에 게시**를 사용하는 방법을 설명합니다.

1. 편집할 수 있는 작업 영역에서 보고서를 열고, **기타 옵션(...)**   > **포함** > **웹에 게시(퍼블릭)** 를 차례로 선택합니다.

   ![기타 옵션의 웹에 게시](media/service-publish-to-web/power-bi-more-options-publish-web.png)
   
2. Power BI 관리자가 embed 태그를 만들 수 있도록 허용하지 않은 경우 해당 관리자에게 문의해야 할 수 있습니다.

   ![Power BI 관리자에게 문의](media/service-publish-to-web/publish_to_web_admin_prompt.png)
   
   조직에서 웹에 게시를 사용하도록 설정할 수 있는 사용자를 찾는 데 도움이 필요하면 이 문서의 뒷부분에 나오는 [Power BI 관리자를 찾는 방법](#find-your-power-bi-administrator)을 참조하세요.

3. 대화 상자 콘텐츠를 검토하고 **embed 태그 만들기**를 선택합니다.

   ![퍼블릭 웹 사이트에 포함 검토](media/service-publish-to-web/publish_to_web2_ga.png)

4. 여기에 표시된 대로 경고를 검토하고 공용 웹 사이트에 데이터를 포함해도 괜찮은지 확인합니다. 이 경우 **게시**를 선택합니다.

   ![경고를 검토합니다.](media/service-publish-to-web/publish_to_web3_ga.png)

5. 링크가 있는 대화 상자가 나타납니다. 이메일로 보낼 링크를 선택하거나 HTML을 복사합니다. iFrame과 같은 코드에 포함하거나 웹 페이지 또는 블로그에 직접 붙여넣을 수 있습니다.

   ![성공: 링크 및 HTML](media/service-publish-to-web/publish_to_web4.png)

6. 이전에 보고서의 embed 태그를 만들고 **웹에 게시**를 선택한 경우 2-4 단계에서 대화 상자가 표시되지 않습니다. 대신 **Embed 태그** 대화 상자가 나타납니다.

   ![embed 태그 대화 상자](media/service-publish-to-web/publish_to_web5.png)

   각 보고서에 대한 embed 태그는 하나만 만들 수 있습니다.


### <a name="tips-for-view-modes"></a>보기 모드에 대한 팁

블로그 게시물에 콘텐츠를 포함하는 경우 일반적으로 특정 화면 크기에 맞추어야 합니다.  필요에 따라 iFrame 태그의 높이와 너비를 조정할 수 있습니다. 그러나 보고서가 지정된 iFrame 영역 내에 맞는지 확인해야 하므로 보고서를 편집할 때 적절한 보기 모드도 설정해야 합니다.

다음 표는 보기 모드에 대한 지침과 포함했을 때 표시되는 모양을 제공합니다.

| 보기 모드 | 포함되었을 때 구현되는 모양 |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**페이지에 맞추기**는 보고서의 페이지 높이 및 너비를 고려합니다. 16:9 또는 4:3과 같은 *동적* 비율로 페이지를 설정하는 경우 콘텐츠가 iFrame 내에 맞게 확장됩니다. iFrame에 포함된 경우 **페이지에 맞추기**를 사용하면 *letterboxing*이 발생할 수 있으며 여기에서 콘텐츠가 iFrame 내에 맞게 확장된 후 iFrame 영역에 회색 배경이 표시됩니다. letterboxing을 최소화하려면 iFrame의 높이와 너비를 적절하게 설정합니다. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**실제 크기**는 보고서 페이지에 설정된 대로 보고서의 크기를 유지합니다. 따라서 iFrame에 스크롤 막대가 표시될 수 있습니다. 스크롤 막대를 피하도록 iFrame 높이 및 너비를 설정합니다. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**너비에 맞추기**는 iFrame의 가로 영역에 콘텐츠가 채워지도록 합니다. 테두리는 계속 표시되지만, 콘텐츠는 사용 가능한 가로 공간을 모두 사용하도록 확장됩니다. |

### <a name="tips-for-iframe-height-and-width"></a>iFrame 높이 및 너비에 대한 팁

**웹에 게시** embed 태그는 다음 예제와 같습니다.

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
너비와 높이를 수동으로 편집하여 보고서를 포함하는 페이지에 원하는 대로 정확하게 맞출 수 있습니다.

더 완벽하게 맞추기 위해 아래쪽 표시줄의 현재 크기에 맞추어 iFrame의 높이에 56픽셀을 추가할 수 있습니다. 보고서 페이지가 동적 크기를 사용하고 아래 표에서 몇 가지 크기를 제공하는 경우 letterboxing 없이 맞추도록 사용할 수 있습니다.

| 비율 | 크기 | 치수(너비 x 높이) |
| --- | --- | --- |
| 16:9 |소형 |640 x 416px |
| 16:9 |중간 |800 x 506px |
| 16:9 |대형 |960 x 596px |
| 4:3 |소형 |640 x 536px |
| 4:3 |중간 |800 x 656px |
| 4:3 |대형 |960 x 776px |

## <a name="manage-embed-codes"></a>embed 태그 관리

**웹에 게시** embed 태그를 만들면 Power BI의 **설정** 메뉴에서 코드를 관리할 수 있습니다. embed 태그 관리에는 대상 시각적 개체 또는 코드에 대한 보고서(사용할 수 없는 embed 코드 렌더링)를 제거하거나 embed 태그를 가져오는 기능이 포함되어 있습니다.

1. **웹에 게시** embed 태그를 관리하려면 톱니바퀴 모양의 **설정** 아이콘을 클릭하고 **embed 태그 관리**를 선택합니다.

   ![embed 태그 관리](media/service-publish-to-web/publish_to_web8.png)

2. embed 태그가 나타납니다.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. embed 태그를 검색하거나 삭제할 수 있습니다. 삭제하면 보고서 또는 시각적 개체에 대한 링크가 비활성화됩니다.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. **삭제**를 선택하면 확인을 요청하는 메시지가 나타납니다.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>보고서 업데이트 및 데이터 새로 고침

**웹에 게시** embed 태그를 만들고 공유하면 보고서가 변경된 내용으로 업데이트되고 embed 태그 링크가 즉시 활성화됩니다. 링크를 열면 누구나 볼 수 있습니다. 처음 만든 후 보고서 또는 시각적 개체 업데이트가 사용자에게 표시될 때까지 최대 2시간이 걸릴 수 있습니다. 데이터는 검색된 때부터 1시간 동안 캐시됩니다. 자주 새로 고쳐야 하는 데이터에는 웹에 게시를 사용하지 않는 것이 좋습니다. 자세한 내용은 이 문서의 뒷부분에 나오는 [**작동 방법**](#howitworks) 섹션을 참조하세요. 

### <a name="data-refresh"></a>데이터 새로 고침

데이터 새로 고침은 포함된 보고서 또는 시각적 개체에 자동으로 반영됩니다. embed 태그에서 새로 고친 데이터가 표시되려면 최대 2시간 정도 걸릴 수 있습니다. 자동 새로 고침을 비활성화하려면 보고서에서 사용하는 데이터 세트에 대한 일정에서 **새로 고치지 않음**을 선택합니다.  

## <a name="power-bi-visuals"></a>Power BI 시각적 개체

Power BI 시각적 개체는 **웹에 게시**에서 지원됩니다. **웹에 게시**를 사용하면 게시된 시각적 개체를 공유하는 대상 사용자는 Power BI 시각적 개체를 사용하도록 설정하여 보고서를 볼 필요가 없습니다.

## <a name="understanding-the-embed-code-status-column"></a>embed 태그 상태 열 이해

>[!Note]
>자주 게시한 embed 태그를 검토합니다. 더 이상 공개적으로 사용할 필요가 없는 항목을 제거합니다.

**embed 태그 관리** 페이지에 상태 열이 포함됩니다. 기본적으로 embed 태그는 **활성**이지만 아래에 나열된 상태 중 하나일 수도 있습니다.

| 상태 | 설명 |
| --- | --- |
| **활성** |보고서를 인터넷 사용자가 보고 상호 작용할 수 있습니다. |
| **차단** |보고서 콘텐츠가 [Power BI 서비스 약관](https://powerbi.microsoft.com/terms-of-service)을 위반합니다. Microsoft가 차단했습니다. 콘텐츠가 오류로 차단되었다고 판단되면 고객 지원으로 문의하세요. |
| **지원되지 않음** |보고서의 데이터 세트에서 행 수준 보안 또는 지원되지 않는 다른 구성을 사용하고 있습니다. 전체 목록은 [**제한**](#limitations) 섹션을 참조하세요. |
| **침해됨** |embed 태그가 정의된 테넌트 정책을 벗어납니다. 이 상태는 일반적으로 embed 태그를 만든 후에 해당 embed 태그를 소유한 사용자를 제외하도록 **웹에 게시** 테넌트 설정이 변경되면 발생합니다. 테넌트 설정이 비활성화되거나 사용자가 더 이상 embed 태그를 만들 수 없는 경우 기존 embed 태그는 **침해됨** 상태를 표시합니다. 자세한 내용은 이 문서의 [Power BI 관리자 찾기](#find-your-power-bi-administrator) 섹션을 참조하세요. |

## <a name="report-a-concern-with-publish-to-web-content"></a>웹에 게시 콘텐츠와 관련된 문제 보고

웹 사이트 또는 블로그에 포함된 **웹에 게시** 콘텐츠와 관련된 문제를 보고하려면 **웹에 게시** 보고서의 아래쪽 표시줄에서 **플래그** 아이콘을 선택합니다.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

해당 문제를 설명하는 이메일을 Microsoft에 보내도록 요청하는 메시지가 표시됩니다. Microsoft는 [Power BI 서비스 약관](https://powerbi.microsoft.com/terms-of-service)에 따라 콘텐츠를 평가하여 적절한 조치를 취합니다.

## <a name="licensing"></a>라이선싱

**웹에 게시**를 사용하려면 Microsoft Power BI 사용자여야 합니다. 보고서 열람자는 Power BI 사용자일 필요가 없습니다.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>작동 방법(기술 세부 사항)

**웹에 게시**를 사용하여 embed 태그를 만들면 보고서는 인터넷 사용자에게 표시됩니다. 공개적으로 사용할 수 있으므로 보기 권한자는 나중에 소셜 미디어를 통해 보고서를 쉽게 공유할 수 있습니다. 사용자가 직접 공용 URL을 열어 보고서를 보거나 웹 페이지 또는 블로그에 포함된 보고서를 보면 Power BI는 보고서 정의 및 보고서를 보는 데 필요한 쿼리 결과를 캐시합니다. 이렇게 캐시하면 수천 명의 동시 사용자가 성능에 영향을 주지 않고 보고서를 볼 수 있습니다.

데이터는 검색된 때부터 1시간 동안 캐시됩니다. 보고서 정의를 업데이트하거나(예: 보기 모드를 변경하는 경우) 보고서 데이터를 새로 고치는 경우 사용자가 보는 보고서 버전에 변경 내용이 반영되는 데 최대 2시간이 걸릴 수 있습니다. 각 요소 및 데이터 값은 독립적으로 캐시되므로 데이터 업데이트가 발생하면 사용자에게 현재 값과 이전 값의 조합이 표시될 수 있습니다. 따라서 작업을 미리 준비하고 설정에 만족하는 경우에만 **웹에 게시** embed 태그를 만드는 것이 좋습니다. 데이터를 새로 고치는 경우 새로 고침 횟수를 최소화하고 업무 외 시간에 새로 고침을 수행합니다. 자주 새로 고쳐야 하는 데이터에는 웹에 게시를 사용하지 않는 것이 좋습니다.

## <a name="find-your-power-bi-administrator"></a>Power BI 관리자 찾기

Power BI 관리 포털에는 웹에 게시할 수 있는 사용자를 제어할 수 있는 설정이 있습니다. 조직의 [Power BI 관리자](../admin/service-admin-role.md)와 협력하여 관리 포털에서 [웹에 게시 테넌트 설정](../admin/service-admin-portal.md#publish-to-web)을 변경합니다.

Power BI에 등록한 소규모 조직이나 개인의 경우 아직 Power BI 관리자가 없을 수 있습니다. [관리자 인수 프로세스](/azure/active-directory/users-groups-roles/domains-admin-takeover)를 따릅니다. Power BI 관리자가 생기면 embed 태그를 만들 수 있습니다.

일반적으로 기존 조직에는 이미 Power BI 관리자가 있습니다. 다음 역할의 사람들이 Power BI 관리자 역할을 할 수 있습니다.

- 전역 관리자
- Azure Active Directory에서 Power BI 서비스 관리자 역할이 있는 사용자

조직에서 [이러한 사용자 중 하나를 찾아서](/office365/admin/admin-overview/admin-overview#who-has-admin-permissions-in-my-business) 관리 포털에서 [웹에 게시 테넌트 설정](../admin/service-admin-portal.md#publish-to-web)을 업데이트하도록 요청해야 합니다.

## <a name="limitations"></a>제한 사항

**웹에 게시**는 Power BI 서비스의 데이터 원본 및 보고서 대부분에 지원됩니다. 그러나 다음 유형의 보고서는 현재 **웹에 게시**에서 지원되지 않거나 사용할 수 없습니다.

- 행 수준 보안을 사용하는 보고서
- 온-프레미스에 호스트된 Analysis Services 테이블 형식, Analysis Service 다차원 및 Azure Analysis Services를 비롯한 모든 라이브 연결 데이터 원본을 사용하는 보고서
- 보고서와 다른 작업 영역에 저장된 [공유 데이터 세트](../connect-data/service-datasets-across-workspaces.md)를 사용하는 보고서
- [공유 및 인증된 데이터 세트](../connect-data/service-datasets-share.md).
- 사용자에게 직접적으로 또는 조직 콘텐츠 팩을 통해 공유되는 보고서
- 편집 멤버가 아닌 작업 영역의 보고서
- “R” 및 Python 시각적 개체는 현재 **웹에 게시** 보고서에서 지원되지 않습니다.
- 웹에 게시된 보고서의 시각적 개체에서 데이터 내보내기
- ArcGIS Maps for Power BI 시각적 개체.
- Power BI 시각적 개체 Q&A.
- 보고서 수준 DAX 측정값을 포함하는 보고서.
- Single Sign-On 데이터 쿼리 모델.
- 보안 기밀 또는 소유 정보.
- **포함** 옵션에 제공되는 자동 인증 기능은 Power BI JavaScript API에서 작동하지 않습니다. Power BI JavaScript API의 경우 포함에 대해 [사용자 소유 데이터](../developer/embedded/embed-sample-for-your-organization.md) 접근 방식을 사용합니다.

## <a name="next-steps"></a>다음 단계

- [SharePoint Online 보고서 웹 파트](service-embed-report-spo.md) 

- [보안 포털 또는 웹 사이트에 보고서 포함](service-embed-secure.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)