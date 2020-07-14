---
title: Power BI에서 민감도 레이블 사용
description: Power BI에서 민감도 레이블을 사용하도록 설정하는 방법을 알아봅니다.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 07/06/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 0fe1b7b1b8175511838005b7b63ca7543bbf939a
ms.sourcegitcommit: 181679a50c9d7f7faebcca3a3fc55461f594d9e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86034339"
---
# <a name="enable-sensitivity-labels-in-power-bi"></a>Power BI에서 민감도 레이블 사용

[Microsoft Information Protection 민감도 레이블](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)을 Power BI에서 사용할 수 있도록 하려면 테넌트에서 사용하도록 설정해야 합니다. 이 문서에서는 이 작업을 수행하는 방법을 Power BI 테넌트 관리자에게 보여 줍니다. Power BI의 민감도 레이블에 대한 자세한 개요를 보려면 [Power BI의 민감도 레이블](service-security-sensitivity-label-overview.md)을 참조하세요. Power BI에서 민감도 레이블을 적용하는 방법에 대한 자세한 내용은 [민감도 레이블 적용](./service-security-apply-data-sensitivity-labels.md)을 참조하세요. 

민감도 레이블을 사용하도록 설정한 경우:

* 조직의 특정 사용자와 보안 그룹이 [민감도 레이블](./service-security-apply-data-sensitivity-labels.md)을 분류하고 Power BI 보고서, 대시보드, 데이터 세트 및 데이터 흐름에 적용할 수 있습니다.
* 조직의 모든 구성원이 해당 레이블을 볼 수 있습니다.

민감도 레이블을 사용하려면 Azure Information Protection 라이선스가 필요합니다. 자세한 내용은 [라이선스](service-security-sensitivity-label-overview.md#licensing)를 참조하세요.

## <a name="enable-sensitivity-labels"></a>민감도 레이블 사용

Power BI **관리 포털**로 이동하여 **테넌트 설정** 창을 열고 **정보 보호** 섹션을 찾습니다.

![Information Protection 섹션 찾기](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

**Information Protection** 섹션에서 다음 단계를 수행합니다.
1. **사용자가 Power BI 콘텐츠의 민감도 레이블을 적용할 수 있도록 허용**을 엽니다.
1. 설정/해제합니다.
1. Power BI 자산에서 민감도 레이블을 적용하고 변경할 수 있는 사람을 정의합니다. 기본적으로 조직의 모든 사용자가 민감도 레이블을 적용할 수 있습니다. 그러나 특정 사용자나 보안 그룹만 민감도 레이블을 설정할 수 있도록 선택할 수 있습니다. 전체 조직이나 특정 보안 그룹을 선택한 상태에서 사용자 또는 보안 그룹의 특정 하위 집합을 제외할 수 있습니다.
   
   * 전체 조직에 대해 민감도 레이블을 사용하도록 설정한 경우 예외는 일반적으로 보안 그룹입니다.
   * 특정 사용자나 보안 그룹에 대해서만 민감도 레이블을 사용하도록 설정한 경우 예외는 일반적으로 특정 사용자입니다.  
    이 방법을 사용하면 특정 사용자가 해당 권한이 있는 그룹에 속해 있더라도 Power BI에서 민감도 레이블을 적용하지 못하도록 방지할 수 있습니다.

1. **적용**을 누릅니다.

![민감도 레이블 사용](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> 자산에 대한 *‘만들기’* 및 *‘편집’* 권한이 있고, 이 섹션에서 설정된 관련 보안 그룹에 속해 있는 Power BI Pro 사용자만 민감도 레이블을 설정하고 편집할 수 있습니다. 이 그룹에 속하지 않는 사용자는 레이블을 설정하거나 편집할 수 없습니다.  

## <a name="troubleshooting"></a>문제 해결

Power BI는 Microsoft Information Protection 민감도 레이블을 사용합니다. 따라서 민감도 레이블을 사용하도록 설정할 때 오류 메시지가 발생하는 경우 다음 중 하나 때문일 수 있습니다.

* Azure Information Protection [라이선스](service-security-sensitivity-label-overview.md#licensing)가 없습니다.
* 민감도 레이블이 Power BI에서 지원하는 Microsoft Information Protection 버전으로 마이그레이션되지 않았습니다. [민감도 레이블을 마이그레이션](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)하는 방법을 자세히 알아보세요.
* 조직에 Microsoft Information Protection 민감도 레이블이 정의되어 있지 않습니다. 게시된 정책에 포함된 레이블만 사용할 수 있습니다. [민감도 레이블에 대해 자세히 알아보거나](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels), [Microsoft 보안 및 규정 준수 센터](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels)를 방문하여 조직의 레이블 및 게시 정책을 정의하는 방법을 알아보세요.

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항

Power BI의 민감도 레이블 제한 목록은 [Power BI의 민감도 레이블](service-security-sensitivity-label-overview.md#limitations)을 참조하세요.

## <a name="next-steps"></a>다음 단계

이 문서에서는 Power BI에서 민감도 레이블을 사용하도록 설정하는 방법을 설명했습니다. 다음 문서에서는 Power BI의 데이터 보호에 대해 자세히 설명합니다. 

* [Power BI의 민감도 레이블 개요](service-security-sensitivity-label-overview.md)
* [Power BI에서 민감도 레이블을 적용하는 방법](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Power BI에서 Microsoft Cloud App Security 제어 사용](service-security-using-microsoft-cloud-app-security-controls.md)
* [보호 메트릭 보고서](service-security-data-protection-metrics-report.md)