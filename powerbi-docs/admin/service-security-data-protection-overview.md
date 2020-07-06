---
title: Power BI의 데이터 보호
description: Power BI에서 데이터 보호 기능이 작동하는 방식을 알아봅니다.
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 4575c80106329a00c959db73c2851c99959f41ec
ms.sourcegitcommit: 46a340937d9f01c6daba86a4ab178743858722ec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85393660"
---
# <a name="data-protection-in-power-bi"></a>Power BI의 데이터 보호

현대적인 기업은 중요한 데이터를 처리하고 보호하는 방법에 대한 엄격한 비즈니스 규정 및 요구 사항을 준수해야 합니다. 이러한 데이터에 대한 제어 및 가시성을 제공하기 위해 Power BI가 Microsoft Information Protection 및 Microsoft Cloud App Security와 통합됩니다. 다음을 수행할 수 있습니다.
* Microsoft Information Protection [민감도 레이블](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide)을 사용하여 Office 365에서 파일을 분류하고 보호하는 데 사용되는 것과 동일한 분류법으로 Power BI 서비스(대시보드, 보고서, 데이터 세트 및 데이터 흐름)의 콘텐츠를 분류하고 레이블을 추가합니다.
* Excel, PowerPoint 또는 PDF 파일로 내보낼 때 Microsoft Information Protection 민감도 레이블 및 보호를 데이터에 적용합니다.
* Microsoft Cloud App Security를 사용하여 Power BI의 활동을 모니터링하고, 보안 문제를 조사하며, Microsoft Cloud App Security 조건부 액세스 앱 제어를 통해 Power BI의 콘텐츠를 보호합니다.

**중요**
* 민감도 레이블 지정은 Power BI 내의 콘텐츠에 대한 액세스에는 영향을 주지 **않습니다**. Power BI 내의 콘텐츠에 대한 액세스는 Power BI 사용 권한으로만 관리됩니다. 레이블이 표시되는 동안 연결된 모든 암호화 설정([Microsoft 365 보안 센터](https://security.microsoft.com/) 또는 [Microsoft 365 준수 센터](https://compliance.microsoft.com/)에서 구성)이 적용되지 않습니다. 이러한 설정은 Excel, PowerPoint 및 PDF 파일로 내보낸 데이터에만 적용됩니다.
* 민감도 레이블 및 파일 암호화는 Excel, PowerPoint 및 PDF로 내보내기 이외의 내보내기 경로에는 적용되지 **않습니다**. Power BI 테넌트 관리자는 민감도 레이블 및 관련 파일 암호화 설정의 적용을 지원하지 않는 모든 내보내기 경로를 사용하지 않도록 설정할 수 있습니다.

## <a name="sensitivity-labels-in-power-bi"></a>Power BI의 민감도 레이블

민감도 레이블은 [Microsoft 365 보안 센터](https://security.microsoft.com/) 또는 [Microsoft 365 규정 준수 센터](https://compliance.microsoft.com/)에서 만들고 관리합니다.

두 센터 중 하나에서 민감도 레이블에 액세스하려면 **분류 > 민감도 레이블**로 이동합니다. 이러한 민감도 레이블은 Azure Information Protection, Office 앱, Office 365 서비스 등의 여러 Microsoft 서비스에서 사용할 수 있습니다.

> [!Important]
> 조직에서 Azure Information Protection 민감도 레이블을 사용하는 경우 Power BI에서 레이블을 사용하려면 이전에 나열된 서비스 중 하나로 [마이그레이션](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)해야 합니다.

> [!NOTE]
> 민감도 레이블은 퍼블릭 클라우드에만 지원되고, 국가 클라우드와 같은 클라우드의 테넌트에서는 지원되지 않습니다.

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Power BI에서 민감도 레이블 작동 방식

Power BI 대시보드, 보고서, 데이터 세트 또는 데이터 흐름에 민감도 레이블을 적용하는 경우 다음과 같은 이점을 제공하는 태그를 해당 리소스에 적용하는 것과 비슷합니다.
* **사용자 지정 가능** - 조직에 있는 다양한 수준의 중요한 콘텐츠를 위해 개인, 공용, 일반, 기밀, 매우 기밀 등의 범주를 만들 수 있습니다.
* **일반 텍스트** - 레이블은 일반 텍스트로 작성되므로 사용자가 민감도 레이블 지침에 따라 콘텐츠 처리 방법을 쉽게 이해할 수 있습니다.
* **영구적** - 민감도 레이블이 콘텐츠에 적용된 후에는 Excel, PowerPoint 및 PDF 파일로 내보낼 때 해당 콘텐츠를 포함하며 정책을 적용하기 위한 기초가 됩니다.

즉, 민감도 레이블은 Excel, PowerPoint 및 PDF 파일로 내보낼 때 콘텐츠를 따라 이동하고 정책을 적용하기 위한 기초가 됩니다.

Power BI 테넌트 관리자는 [Power BI 관리 포털](service-admin-portal.md)에서 [Excel로 내보내기](service-admin-portal.md#export-to-excel) 및 [PowerPoint 및 PDF로 내보내기](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents)를 제어할 수 있습니다.

## <a name="sensitivity-label-example"></a>민감도 레이블 예제

Power BI의 민감도 레이블이 작동하는 방식의 빠른 예제는 다음과 같습니다.
1. Power BI 서비스에서 **매우 기밀** 민감도 레이블을 보고서에 적용합니다.

   ![목록 보기의 민감도 레이블](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. 이 보고서의 데이터를 Excel 파일로 내보내면 민감도 레이블과 보호가 내보낸 Excel 파일에 적용됩니다.

   ![민감도 레이블이 콘텐츠를 따라 이동함](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

Microsoft Office 애플리케이션에서 민감도 레이블은 위의 이미지에 표시된 바와 같이 메일 또는 문서의 태그로 표시됩니다. Power BI 전체에서 콘텐츠를 사용 및 공유할 때 콘텐츠와 함께 이동하고 지속되는 분류를 스티커처럼 콘텐츠에 할당할 수도 있습니다. 이 분류를 사용하여 사용 현황 보고서를 생성하고 중요한 콘텐츠의 활동 데이터를 볼 수 있습니다. 이 정보에 따라 나중에 언제든지 보호 설정을 적용하도록 선택할 수 있습니다.

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>Power BI에서 민감도 레이블을 사용하기 위한 요구 사항

Power BI에서 민감도 레이블을 사용하도록 설정하고 사용하려면 먼저 다음 필수 조건을 충족해야 합니다.
* [Microsoft 365 보안 센터](https://security.microsoft.com/) 또는 [Microsoft 365 규정 준수 센터](https://compliance.microsoft.com/)에서 민감도 레이블을 정의했는지 확인합니다.
* Power BI에서 [민감도 레이블을 사용](service-security-enable-data-sensitivity-labels.md)합니다.
* 사용자에게 [적절한 라이선스](#licensing)가 있는지 확인합니다.
* Power BI에서 Microsoft Cloud App Security를 사용하는 경우 [적절한 라이선스](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing)가 있는지 확인합니다.

## <a name="protect-content-using-microsoft-cloud-app-security"></a>Microsoft Cloud App Security를 사용하여 콘텐츠 보호

Microsoft Cloud App Security를 사용하여 의도하지 않은 유출이나 위반으로부터 Power BI 콘텐츠를 보호할 수 있습니다. Microsoft Cloud App Security를 설정하고 구성하면 보안 관리자가 사용자 액세스 및 활동을 모니터링하고, 실시간 위험 분석을 수행하며, 레이블 관련 제어를 설정할 수 있습니다.

예를 들어 조직에서 Microsoft Cloud App Security를 사용하여 사용자가 중요한 데이터를 Power BI에서 비관리형 디바이스로 다운로드할 수 없도록 하는 정책을 구성할 수 있습니다. 이러한 구성을 사용하면 사용자가 생산성을 유지하고 어디서나 Power BI에 연결하도록 허용하는 동시에 Microsoft Cloud App Security를 통해 위반하는 사용자 작업을 실시간으로 차단할 수 있습니다.

**요구 사항**

민감도 레이블이 Microsoft Cloud App Security를 사용하려면 먼저 다음 필수 조건을 충족해야 합니다.
* Cloud App Security 및 Azure Information Protection을 [테넌트에 사용](https://docs.microsoft.com/cloud-app-security/azip-integration)하도록 설정해야 합니다.
* 앱을 [Microsoft Cloud App Security에 연결](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps)해야 합니다.

## <a name="licensing"></a>라이선싱

* Power BI에서 Microsoft Information Protection 민감도 레이블을 적용하고 보려면 Azure Information Protection Premium P1 또는 Premium P2 라이선스가 필요합니다. Microsoft Azure Information Protection은 독립 실행형으로 구입하거나 Microsoft 라이선스 제품군 중 하나를 통해 구입할 수 있습니다. 자세한 내용은 [Azure Information Protection 가격 책정](https://azure.microsoft.com/pricing/details/information-protection/)을 참조하세요.
* Office 앱에서 레이블을 보고 적용하려면 [라이선스 요구 사항](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels)을 충족해야 합니다.
* Power BI 콘텐츠에 레이블을 적용하려면 사용자에게 위에서 언급한 Azure Information Protection 라이선스 외에도 Power BI Pro 라이선스가 있어야 합니다.
* 원치 않는 누출 및 위반으로부터 Power BI 콘텐츠를 보호하는 데 사용하려면 [Microsoft Cloud App Security에 필요한 라이선스](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing)가 있어야 합니다.

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항

다음 목록은 Power BI에서 민감도 레이블의 몇 가지 제한 사항입니다.

**일반**
* 민감도 레이블은 대시보드, 보고서, 데이터 세트 및 데이터 흐름에만 적용할 수 있습니다. 현재, [페이지를 매긴 보고서](../paginated-reports/report-builder-power-bi.md) 및 통합 문서에서는 민감도 레이블을 사용할 수 없습니다.
* Power BI 자산의 민감도 레이블은 작업 영역 목록, 계보, 즐겨찾기, 최근 항목 및 앱에 표시됩니다. 현재 “공유한 항목” 보기에는 레이블이 표시되지 않습니다. 그러나 Power BI 자산에 적용된 레이블은 표시되지 않는 경우에도 Excel, PowerPoint 및 PDF 파일로 내보낸 데이터에 항상 유지됩니다.
* 민감도 레이블은 글로벌(퍼블릭) 클라우드의 테넌트에만 지원됩니다. 다른 클라우드의 테넌트에서는 민감도 레이블이 지원되지 않습니다.
* 템플릿 앱에 대해서는 데이터 민감도 레이블이 지원되지 않습니다. 앱이 추출되고 설치될 때 템플릿 앱 작성자가 설정한 민감도 레이블은 제거되고 앱 소비자가 설치된 템플릿 앱의 아티팩트에 추가한 민감도 레이블은 앱이 업데이트될 때 손실됩니다(nothing으로 다시 설정됨).
* Power BI는 [전달 금지](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions), [사용자 정의](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) 및 [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions) 보호 유형의 민감도 레이블을 지원하지 않습니다. 전달 금지 및 사용자 정의 보호 유형은 [Microsoft 365 보안 센터](https://security.microsoft.com/) 또는 [Microsoft 365 준수 센터](https://compliance.microsoft.com/)에 정의된 레이블을 참조합니다.
* 사용자가 Power BI 내에서 부모 레이블을 적용하는 것을 허용하지 않는 것이 좋습니다. 부모 레이블이 콘텐츠에 적용되는 경우 해당 콘텐츠에서 파일(Excel, PowerPoint 및 PDF)로 데이터 내보내기가 실패합니다. [하위 레이블(그룹화 레이블)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels)을 참조하세요.

**내보내기**
* 레이블 및 보호 컨트롤은 데이터를 Excel, PowerPoint 및 PDF 파일로 내보낼 때만 적용됩니다. 데이터를 .csv 또는 .pbix 파일, Excel의 분석 또는 다른 내보내기 경로로 내보낼 때는 레이블 및 보호가 적용되지 않습니다.
* 내보낸 파일에 민감도 레이블 및 보호를 적용해도 콘텐츠 표시가 파일에 추가되지 않습니다. 그러나 레이블이 콘텐츠 표시를 적용하도록 구성된 경우에는 Office 데스크톱 앱에서 해당 파일을 열 때 Azure Information Protection 통합 레이블 지정 클라이언트에 의해 자동으로 적용됩니다. 데스크톱, 모바일 또는 웹앱에 대해 기본 제공 레이블을 사용하는 경우 콘텐츠 표시가 자동으로 적용되지 않습니다. 자세한 내용은 [Office 앱에서 콘텐츠 표시 및 암호화를 적용할 때](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption)를 참조하세요.
* Power BI에서 파일을 내보내는 사용자는 민감도 레이블 설정에 따라 해당 파일에 대한 액세스 및 편집 권한을 갖습니다. 데이터를 내보내는 사용자는 파일의 소유자 권한을 얻지 못합니다.
* 데이터를 파일로 내보낼 때 레이블을 적용할 수 없는 경우 내보내기가 실패합니다. 레이블을 적용할 수 없어 내보내기가 실패했는지 확인하려면 제목 표시줄의 가운데에 있는 보고서 또는 대시보드 이름을 클릭하면 열리는 정보 드롭다운에 “민감도 레이블을 로드할 수 없습니다”라는 메시지가 표시되는지 확인합니다. 이는 보안 관리자가 적용된 레이블을 게시 취소 또는 삭제하거나 임시 시스템 문제로 인해 발생할 수 있습니다.


## <a name="next-steps"></a>다음 단계

이 문서에서는 Power BI의 데이터 보호에 대해 간략하게 설명했습니다. 다음 문서에서는 Power BI의 데이터 보호에 대해 자세히 설명합니다. 

* [Power BI에서 데이터 민감도 레이블 사용](service-security-enable-data-sensitivity-labels.md)
* [Power BI에서 데이터 민감도 레이블 적용](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Power BI에서 Microsoft Cloud App Security 제어 사용](service-security-using-microsoft-cloud-app-security-controls.md)
* [데이터 보호 메트릭 보고서](service-security-data-protection-metrics-report.md)