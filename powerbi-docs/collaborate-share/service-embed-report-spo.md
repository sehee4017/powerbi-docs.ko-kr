---
title: SharePoint Online에 보고서 웹 파트 포함
description: SharePoint Online용 Power BI의 새로운 보고서 웹 파트를 사용하면 SharePoint Online 페이지에서 대화형 Power BI 보고서를 쉽게 포함시킬 수 있습니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 06/28/2020
ms.openlocfilehash: 94419bb25aa00645b22a1dad1f97fcc792c3d63d
ms.sourcegitcommit: 561f6de3e4621d9d439dd54fab458ddca78ace2c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939556"
---
# <a name="embed-a-report-web-part-in-sharepoint-online"></a>SharePoint Online에 보고서 웹 파트 포함

SharePoint Online용 Power BI의 새로운 보고서 웹 파트를 사용하면 SharePoint Online 페이지에서 대화형 Power BI 보고서를 쉽게 포함시킬 수 있습니다.

새로운 **SharePoint Online에 포함** 옵션을 사용하면 포함된 보고서가 [RLS(행 수준 보안)](../admin/service-admin-rls.md)를 통해 모든 항목 사용 권한과 데이터 보안을 준수하므로 안전한 내부 포털을 쉽게 만들 수 있습니다.

## <a name="requirements"></a>요구 사항

**SharePoint Online에 포함** 보고서가 작동하려면 다음이 필요합니다.

* Power BI Pro 라이선스 또는 Power BI 라이선스를 포함한 [Power BI Premium 용량(EM 또는 P SKU)](../admin/service-premium-what-is.md).
* SharePoint Online용 Power BI 웹 파트는 [최신 페이지](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)가 필요합니다.
* 포함된 보고서를 사용하려면 사용자가 Power BI 서비스에 로그인하여 Power BI 라이선스를 활성화해야 합니다.

## <a name="embed-your-report"></a>보고서 포함
보고서를 SharePoint Online에 포함하려면 보고서 URL을 가져와 SharePoint Online의 Power BI 웹 파트와 함께 사용해야 합니다.

### <a name="get-a-report-url"></a>보고서 URL 가져오기

1. Power BI 내에서 보고서를 봅니다.

2. **기타 옵션(...)** 드롭다운 메뉴에서 **포함** > **SharePoint Online**을 차례로 선택합니다.

    ![기타 옵션 메뉴, SharePoint Online](media/service-embed-report-spo/power-bi-more-options-sharepoint-online.png)

3. 대화 상자에서 보고서 URL을 복사합니다.

    ![Embed 링크](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>SharePoint Online 페이지에 Power BI 보고서 추가

1. SharePoint Online에서 대상 페이지를 열고 **편집**을 선택합니다.

    ![SP 편집 페이지](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    또는 Sharepoint Online에서 **+ 새로 만들기**를 선택하여 새 최신 사이트 페이지를 만듭니다.

    ![SP 새 페이지](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. **+** 드롭다운을 선택한 다음, **Power BI** 웹 파트를 선택합니다.

    ![SP 새 웹 파트](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. **보고서 추가**를 선택합니다.

    ![SP 새 보고서](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. 이전에 복사한 보고서 URL을 **Power BI 보고서 링크** 창에 붙여넣습니다. 보고서를 자동으로 로드합니다.

    ![SP 새 웹 파트 속성](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. **게시**를 선택하여 변경 사항을 SharePoint Online 사용자가 볼 수 있도록 합니다.

    ![SP 보고서 로드됨](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>보고서에 액세스 권한 부여

SharePoint Online에 보고서를 포함해도 사용자에게 보고서를 볼 수 있는 권한이 자동으로 부여되지 않으므로 Power BI에서 보기 권한을 설정해야 합니다.

> [!IMPORTANT]
> Power BI 서비스 내에서 보고서를 볼 수 있는 사람이 누구인지 확인하고 목록에 없는 사람에게 액세스 권한을 부여합니다.

Power BI에서 보고서 액세스를 제공하는 두 가지 방법이 있습니다. 첫 번째 방법은 Microsoft 365 그룹을 사용하여 SharePoint Online 팀 사이트를 구축하는 경우 사용자를 **Power BI 서비스 내 작업 영역** 및 **SharePoint 페이지**의 멤버로 나열하는 것입니다. 자세한 내용은 [작업 영역 관리](service-manage-app-workspace-in-power-bi-and-office-365.md) 방법을 참조하세요.

두 번째 방법은 앱 내에 보고서를 포함하여 사용자와 직접 공유하는 것입니다.  

1. Pro 사용자여야 하는 작성자는 작업 영역에 보고서를 만듭니다. ‘Power BI 무료 사용자’와 공유하려면 작업 영역을 ‘프리미엄 작업 영역’으로 설정해야 합니다. 

2. 작성자가 앱을 게시하고 설치합니다. 작성자는 SharePoint Online에 포함하는 데 사용되는 보고서 URL에 액세스할 수 있도록 앱을 설치해야 합니다.

3. 이제 모든 최종 사용자도 앱을 설치해야 합니다. [Power BI 관리 포털](../admin/service-admin-portal.md)에서 사용하도록 설정할 수 있는 **앱을 자동으로 설치** 기능을 사용하여 최종 사용자를 위해 앱을 미리 설치되도록 할 수도 있습니다.

   ![앱을 자동으로 설치](media/service-embed-report-spo/install-app-automatically.png)

4. 작성자가 앱을 열고 보고서로 이동합니다.

5. 작성자는 앱이 설치한 보고서에서 포함 보고서 URL을 복사합니다. 작업 영역의 원래 보고서 URL을 사용하면 안 됩니다.

6. SharePoint Online에서 새 팀 사이트를 만듭니다.

7. 이전에 복사한 보고서 URL을 Power BI 웹 파트에 추가합니다.

8. SharePoint Online 페이지 및 직접 만든 Power BI 앱에서 데이터를 사용할 모든 최종 사용자 및/또는 그룹을 추가합니다.

    > [!NOTE]
    > **사용자 또는 그룹은 SharePoint 페이지에서 보고서를 보려면 SharePoint Online 페이지 및 Power BI 앱의 보고서에 대한 액세스 권한이 둘 다 필요합니다.**

이제 최종 사용자가 SharePoint Online의 팀 사이트로 이동하여 해당 페이지에서 보고서를 볼 수 있습니다.

## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

Power BI 환경에서 다단계 인증을 사용하여 로그인해야 하는 경우 ID를 확인하기 위해 보안 디바이스에 로그인하라는 메시지가 나타날 수 있습니다. 이는 다단계 인증을 사용하여 SharePoint Online에 로그인하지 않았지만 Power BI 환경에서 계정의 유효성을 검사하기 위해 보안 디바이스가 필요한 경우에 발생합니다.

> [!NOTE]
> Power BI는 아직 Azure Active Directory 2.0을 통한 다단계 인증을 지원하지 않습니다. 사용자에게 오류 메시지가 표시됩니다. 사용자가 해당 보안 디바이스를 사용하여 SharePoint Online에 다시 로그인하면 보고서를 볼 수 있습니다.

## <a name="web-part-settings"></a>웹 파트 설정

다음은 SharePoint Online용 Power BI 웹 파트를 조정할 수 있는 설정입니다.

![SP 웹 파트 속성](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| 속성 | 설명 |
| --- | --- |
| 페이지 이름 |웹 파트의 기본 페이지를 설정합니다. 드롭다운에서 값을 선택합니다. 페이지가 표시되지 않는 경우는 보고서가 한 페이지이거나 붙여 넣은 URL에 페이지 이름이 포함된 경우입니다. URL에서 보고서 섹션을 제거하여 특정 페이지를 선택합니다. |
| 표시 |보고서가 SharePoint Online 페이지 내에서 어떻게 표시되는지 조정합니다. |
| 탐색 창 표시 |페이지 탐색 창을 표시하거나 숨깁니다. |
| 필터 창 표시 |필터 창을 표시하거나 숨깁니다. |

## <a name="reports-that-do-not-load"></a>로드되지 않는 보고서

보고서가 Power BI 웹 파트 내에서 로드되지 않으면 다음과 같은 메시지가 표시될 수 있습니다.

![이 콘텐츠는 사용할 수 있는 메시지가 아닙니다.](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

이 메시지가 표시되는 데는 일반적으로 두 가지 이유가 있습니다.

1. 보고서 액세스 권한이 없습니다.
2. 보고서가 삭제되었습니다.

이 문제를 해결하려면 SharePoint Online 페이지 소유자에게 문의하세요.

## <a name="licensing"></a>라이선싱

SharePoint에서 보고서를 보는 사용자에게 **Power BI Pro 라이선스**가 필요하거나, **[Power BI Premium 용량(EM 또는 P SKU)](../admin/service-admin-premium-purchase.md)** 에 있는 작업 영역에 있어야 합니다.

## <a name="known-issues-and-limitations"></a>알려진 문제 및 제한 사항

* 오류: "An error occurred, please try logging out and back in and then revisiting this page.(오류가 발생했습니다. 로그아웃했다가 다시 로그인한 후 이 페이지를 다시 방문하세요.) Correlation ID: undefined, http response status:(상관관계 ID: 정의되지 않음, http 응답 상태:) 400, server error code 10001, message:(400, 서버 코드 오류 10001, 메시지:) Missing refresh token(새로 고침 태그 없음)"
  
  이 오류가 발생하면 아래 문제 해결 단계 중 하나를 시도하세요.
  
  1. SharePoint에서 로그아웃했다가 다시 로그인합니다. 다시 로그인하기 전에 모든 브라우저 창을 닫아야 합니다.

  2. 사용자 계정에 MFA(다단계 인증)가 필요한 경우 MFA 다단계 인증 디바이스(휴대폰 앱, 스마트 카드 등)를 사용하여 SharePoint에 로그인합니다.
  
  3. Azure B2B 게스트 사용자 계정은 지원되지 않습니다. 파트가 로드 중임을 나타내는 Power BI 로고가 사용자에게 표시되지만 보고서는 표시되지 않습니다.

* Power BI는 SharePoint Online에서 지원하는 것과 동일한 지역화된 언어를 지원하지 않습니다. 결과적으로 포함된 보고서 내에 적절한 지역화가 표시되지 않을 수 있습니다.

* Internet Explorer 10을 사용하는 경우 문제가 발생할 수 있습니다. <!--You can look at the [browsers support for Power BI](../consumer/end-user-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->

* [내셔널 클라우드](https://powerbi.microsoft.com/clouds/)에서는 Power BI 웹 파트를 사용할 수 없습니다.

* 클래식 SharePoint Server는 이 웹 파트에서 지원되지 않습니다.

* [URL 필터](service-url-filters.md)는 SPO 웹 파트에서 지원되지 않습니다.

## <a name="next-steps"></a>다음 단계

* [최종 사용자의 최신 사이트 페이지 작성 허용 또는 금지](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Power BI에서 앱 만들기 및 배포](service-create-distribute-apps.md)  
* [동료 및 다른 사용자와 대시보드 공유](service-share-dashboards.md)  
* [Power BI 프리미엄이란?](../admin/service-premium-what-is.md)
* [보안 포털 또는 웹 사이트에 보고서 포함](service-embed-secure.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
