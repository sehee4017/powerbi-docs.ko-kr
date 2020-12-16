---
title: 새로 고침 시나리오 문제 해결
description: 새로 고침 시나리오 문제 해결
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 12/14/2020
LocalizationGroup: Data refresh
ms.openlocfilehash: eba044de4918ad3cc62ce8b47144eab25c34702a
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491808"
---
# <a name="troubleshooting-refresh-scenarios"></a>새로 고침 시나리오 문제 해결

다음에서 Power BI 서비스에서 데이터를 새로 고침할 때 직면할 수 있는 다양한 시나리오에 대한 정보를 찾을 수 있습니다.

> [!NOTE]
> 아래 나열되어 있지 않은 시나리오가 발생하고 문제를 발생시킨 경우 [커뮤니티 사이트](https://community.powerbi.com/)에 추가 지원을 요청하거나 [지원 티켓](https://powerbi.microsoft.com/support/)을 만들 수 있습니다.
>

새로 고침에 대한 기본 요구 사항이 충족되고 확인되는지를 항상 확인해야 합니다. 이러한 기본 요구 사항은 다음과 같습니다.

* 게이트웨이가 최신 버전인지 확인
* 보고서에 게이트웨이가 선택되어 있는지 확인합니다. 선택되어 있지 않은 경우 데이터 원본이 변경되었거나 없을 수 있습니다.

이러한 요구 사항이 충족된 것을 확인했다면 다음 섹션에서 더 많은 문제 해결 방법을 살펴봅니다. 


## <a name="email-notifications"></a>메일 알림

메일 알림에서 이 문서에 액세스하는 경우, 새로 고침 문제에 대한 메일을 더 이상 받지 않으려면 Power BI 관리자에게 문의하세요. Power BI의 해당 데이터 세트에서 구독한 메일 또는 메일 목록을 제거하도록 요청합니다. 관리자는 Power BI 관리 포털의 다음 영역에서 이 작업을 수행할 수 있습니다.

![새로 고침 알림 메일](media/refresh-troubleshooting-refresh-scenarios/refresh-email.png)

## <a name="refresh-using-web-connector-doesnt-work-properly"></a>웹 커넥터를 사용하여 새로 고침이 제대로 작동하지 않는 경우

[**Web.Page**](/powerquery-m/web-page) 함수를 사용하는 웹 커넥터 스크립트가 있고 2016년 11월 18일 이후에 데이터 세트 또는 보고서를 업데이트한 경우 새로 고침이 제대로 작동하도록 하려면 게이트웨이를 사용해야 합니다.

## <a name="unsupported-data-source-for-refresh"></a>새로 고침을 지원하지 않는 데이터 소스

데이터 세트를 구성할 때 새로 고치기 위해 지원되지 않는 데이터 원본을 사용하는 데이터 세트를 비롯한 오류가 발생할 수 있습니다. 자세한 내용은 [새로 고침을 지원하지 않는 데이터 원본 문제 해결](service-admin-troubleshoot-unsupported-data-source-for-refresh.md)을 참조하세요.

## <a name="dashboard-doesnt-reflect-changes-after-refresh"></a>대시보드는 새로 고침 후의 변경을 반영하지 않습니다.

새로 고침이 대시보드 타일에 반영되도록 하려면 약 10~15분 정도 기다려 주세요. 여전히 표시되지 않으면 대시 보드에 시각화를 다시 고정합니다.

## <a name="gatewaynotreachable-when-setting-credentials"></a>자격 증명 설정 시의 GatewayNotReachable

데이터 원본에 대한 자격 증명을 설정하려고 할 때 `GatewayNotReachable`이 발생할 수 있습니다. 이는 만료된 게이트웨이로 인한 결과일 수 있습니다. 최신 게이트웨이를 설치하고 다시 시도하십시오.

## <a name="processing-error-the-following-system-error-occurred-type-mismatch"></a>처리 오류: 다음 시스템 오류가 발생했습니다. 형식 불일치

이는 Power BI Desktop 파일 또는 Excel 통합 문서에서의 M 스크립트에 관한 문제일 수 있습니다. Power BI Desktop 버전이 만료되어서 발생할 수도 있습니다.

## <a name="tile-refresh-errors"></a>타일 새로 고침 오류

대시보드 타일 및 설명에 발생할 수 있는 오류 목록은 [타일 오류 문제 해결](refresh-troubleshooting-tile-errors.md)을 참조하세요.

## <a name="refresh-fails-when-updating-data-from-sources-that-use-aad-oauth"></a>AAD OAuth를 사용하는 원본의 데이터가 업데이트될 때 새로 고침 실패함

여러 다양한 데이터 원본에서 사용하는 Azure Active Directory(**AAD**) OAuth 토큰은 약 1시간 후 만료됩니다. Power BI 서비스는 데이터를 로드할 때 최대 2시간까지 대기하므로 데이터 로드가 토큰 만료보다 오래 걸리는(1시간 이상) 상황이 발생할 수 있습니다. 이 경우 데이터 로드 프로세스가 실패하고 자격 증명 오류가 발생할 수 있습니다.

AAD OAuth를 사용하는 데이터 원본에는 **Microsoft Dynamics CRM Online**, **SharePoint Online**(SPO) 등이 포함됩니다. 이러한 데이터 원본에 연결하며 1시간 이상 데이터를 로드할 때 자격 증명 오류가 발생한다면 이것이 원인일 수 있습니다.

Microsoft는 데이터 로드 프로세스에서 토큰을 새로 고치고 계속할 수 있게 하는 솔루션을 연구 중입니다. 그러나 Dynamics CRM Online 또는 SharePoint Online 인스턴스(또는 다른 AAD OAuth 데이터 원본)가 너무 커 2시간 데이터 로드 임계값에 걸릴 경우, Power BI 서비스에서 데이터 로드 제한 시간 만료도 함께 발생할 수 있습니다.

또한 제대로 작동하려면 AAD OAuth를 사용하여 **SharePoint Online** 데이터 원본에 연결할 때 **Power BI 서비스** 에 로그인하는 데 사용하는 동일한 계정을 사용해야 합니다.

## <a name="uncompressed-data-limits-for-refresh"></a>새로 고침에 대한 압축되지 않은 데이터 한도

**Power BI 서비스** 로 가져올 데이터 세트에 대한 최대 크기는 1GB입니다. 이러한 데이터 세트는 높은 성능을 보장하기 위해 압축률이 높습니다. 또한 공유 용량에서 서비스는 새로 고치는 동안 처리되는 비압축 데이터의 양을 10GB로 한정합니다. 이 한도는 압축의 부분을 차지하므로 1GB보다 훨씬 더 높습니다. Power BI 프리미엄의 데이터 세트는 이 한도에 해당하지 않습니다. 이 이유로 인해 Power BI 서비스에서 새로 고침이 실패한 경우 Power BI로 가져오는 데이터의 양을 줄이고 다시 시도하십시오.

## <a name="scheduled-refresh-timeout"></a>예약된 새로 고침 제한 시간

가져온 데이터 세트에 대한 예약된 새로 고침 제한 시간은 2시간입니다. 이 제한 시간은 **프리미엄** 작업 영역에서 데이터 세트에 대해 5시간으로 증가됩니다. 이 제한이 발생하는 경우 데이터 세트의 크기 또는 복잡성을 줄이거나 데이터 세트를 더 작은 조각으로 나누는 것이 좋습니다.

## <a name="scheduled-refresh-failures"></a>예약된 새로 고침 실패

예약된 새로 고침이 네 번 연속 실패하면 Power BI가 새로 고침을 비활성화합니다. 기본 문제를 해결한 다음, 예약된 새로 고침을 다시 활성화합니다.

## <a name="access-to-the-resource-is-forbidden"></a>리소스에 대한 액세스가 금지되었습니다.  

이 오류는 캐시된 자격 증명이 만료되는 경우에 발생할 수 있습니다. Power BI에 로그인하고 `https://app.powerbi.com?alwaysPromptForContentProviderCreds=true`으로 이동하여 인터넷 브라우저 캐시를 지웁니다. 이렇게 하면 자격 증명의 업데이트를 적용합니다.

## <a name="data-refresh-failure-because-of-password-change-or-expired-credentials"></a>암호 변경 또는 만료된 자격 증명으로 인한 데이터 새로 고침 오류

데이터 새로 고침은 캐시된 자격 증명이 만료되어 실패할 수도 있습니다. Power BI에 로그인하고 `https://app.powerbi.com?alwaysPromptForContentProviderCreds=true`으로 이동하여 인터넷 브라우저 캐시를 지웁니다. 이렇게 하면 자격 증명의 업데이트를 적용합니다.

## <a name="next-steps"></a>다음 단계

- [Power BI에서 데이터 새로 고침](refresh-data.md)  
- [온-프레미스 데이터 게이트웨이 문제 해결](service-gateway-onprem-tshoot.md)  
- [Power BI 게이트웨이 - 개인 문제 해결](service-admin-troubleshooting-power-bi-personal-gateway.md)  

궁금한 점이 더 있나요? [Microsoft Power BI 커뮤니티에 질문하세요.](https://community.powerbi.com/)
