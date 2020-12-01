---
title: Power BI용 Azure 보안 기준
description: Power BI 보안 기준은 Azure Security Benchmark에 지정된 보안 권장 사항을 구현하기 위한 절차 지침과 리소스를 제공합니다.
author: msmbaldwin
ms.service: security
ms.topic: conceptual
ms.date: 11/20/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: b0eb2906463efa95615fa76f3f7dda2a91ef126a
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95550447"
---
# <a name="azure-security-baseline-for-power-bi"></a>Power BI용 Azure 보안 기준

이 보안 기준은 [Azure Security Benchmark 버전 2.0](https://docs.microsoft.com/azure/security/benchmarks/overview)에서 Power BI에 대한 지침을 적용합니다. Azure Security Benchmark는 Azure에서 클라우드 솔루션을 보호하는 방법에 대한 권장 사항을 제공합니다. 콘텐츠는 Azure Security Benchmark 및 Power BI에 적용되는 관련 지침에서 정의된 **보안 컨트롤** 에 따라 그룹화됩니다. Power BI에 적용할 수 없는 **컨트롤** 은 제외되었습니다.

Power BI가 완전히 Azure Security Benchmark에 매핑되는 방법을 보려면 [전체 Power BI 보안 기준 매핑 파일](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines)을 참조하세요.

## <a name="network-security"></a>네트워크 보안

자세한 내용은 [Azure Security Benchmark: 네트워크 보안](/azure/security/benchmarks/security-controls-v2-network-security)을 참조하세요.

### <a name="ns-3-establish-private-network-access-to-azure-services"></a>NS-3: Azure 서비스에 대한 프라이빗 네트워크 액세스 설정

**지침**: Power BI는 Power BI 테넌트를 프라이빗 링크 엔드포인트에 연결하고 공용 인터넷 액세스를 비활성화하도록 지원합니다.

- [Power BI 액세스를 위한 프라이빗 링크](https://docs.microsoft.com/power-bi/admin/service-security-private-links)

**Azure Security Center 모니터링**: 해당 없음

**책임**: 공유됨

## <a name="identity-management"></a>ID 관리

자세한 내용은 [Azure Security Benchmark: ID 관리](/azure/security/benchmarks/security-controls-v2-identity-management)를 참조하세요.

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1: Azure Active Directory를 중앙 ID 및 인증 시스템으로 표준화

**지침**: Power BI는 Azure의 기본 ID 및 액세스 관리 서비스인 Azure AD(Azure Active Directory)와 통합됩니다. 조직의 ID 및 액세스 관리를 관리하도록 Azure AD에서 표준화해야 합니다.

Azure AD 보안은 조직의 클라우드 보안 관행에서 높은 우선 순위에 둬야 합니다. Azure AD는 Microsoft의 모범 사례 권장 사항을 기준으로 ID 보안 태세를 평가하는 데 도움이 되는 ID 보안 점수를 제공합니다. 점수를 사용하여 구성이 모범 사례 권장 사항에 얼마나 근접하게 일치하는지 측정하고 보안 태세를 개선할 수 있습니다.

참고: Azure AD는 Microsoft 계정이 없는 사용자가 애플리케이션 및 리소스에 로그인할 수 있게 하는 외부 ID를 지원합니다.

- [Azure Active Directory의 테넌시](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps)

- [Azure AD 인스턴스를 만들고 구성하는 방법](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [애플리케이션에 외부 ID 공급자 사용](https://docs.microsoft.com/azure/active-directory/b2b/identity-providers)

- [Azure Active Directory의 ID 보안 점수란?](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-secure-score)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2: 애플리케이션 ID를 안전하게 자동으로 관리

**지침**: Power BI 및 Power BI Embedded는 서비스 주체의 사용을 지원합니다. Power BI를 암호화하거나 액세스하는 데 사용되는 서비스 주체 자격 증명을 Key Vault에 저장하고, 자격 증명 모음에 적절한 액세스 정책을 할당하고, 액세스 권한을 정기적으로 검토합니다.

서비스 주체를 사용하여 Premium 작업 영역 및 데이터 세트 작업 자동화 https://docs.microsoft.com/power-bi/admin/service-premium-service-principal

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3: 애플리케이션 액세스에 Azure AD SSO(Single Sign-On) 사용

**지침**: Power BI는 Azure Active Directory를 사용하여 Azure 리소스, 클라우드 애플리케이션, 온-프레미스 애플리케이션에 ID 및 액세스 관리를 제공합니다. 여기에는 직원과 같은 엔터프라이즈 ID 및 파트너, 공급업체, 공급자와 같은 외부 ID도 포함됩니다. 이를 통해 SSO(Single Sign-On)가 온-프레미스 및 클라우드에서 조직의 데이터와 리소스에 대한 액세스를 관리하고 보호할 수 있습니다. 모든 사용자, 애플리케이션, 디바이스를 Azure AD에 연결하여 원활하고 안전하게 액세스하고 가시성과 제어를 강화할 수 있습니다.

- [Azure AD에서의 애플리케이션 SSO 이해](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4: 모든 Azure Active Directory 기반 액세스에 강력한 인증 제어 사용

**지침**: Power BI는 MFA(다단계 인증)를 통한 강력한 인증 제어와 강력한 암호 없는 방법을 지원하는 Azure AD와 통합됩니다.
- 다단계 인증 - Azure AD MFA를 지원하고 MFA 설정에서 Azure Security Center ID 및 액세스 관리 모범 사례 권장 사항을 따릅니다. MFA는 로그인 조건 및 위험 요소에 따라 모든 사용자나 일부 사용자에게 또는 사용자별 수준에서 적용할 수 있습니다.
- 암호 없는 인증 - 암호 없는 인증 옵션 3가지, 즉 비즈니스용 Windows Hello, Microsoft Authenticator 앱, 스마트 카드 등의 온-프레미스 인증 방법을 사용할 수 있습니다.

관리자 및 권한 있는 사용자의 경우 가장 높은 수준의 강력한 인증을 사용한 후에 적절한 강력한 인증 정책을 다른 사용자에게 롤아웃해야 합니다.

참고: MFA는 Azure AD에서 사용하도록 설정된 사용자 계정에만 적용할 수 있습니다. Power BI 서비스 주체는 MFA 사용을 지원하지 않습니다.

- [Azure에서 MFA를 사용하도록 설정하는 방법](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

- [Azure Active Directory에 대한 암호 없는 인증 옵션 소개](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5: 계정 변칙 모니터링 및 경고

**지침**: Microsoft Cloud App Security에서 포함할 사용자 및 그룹에만 적용되도록 개별적으로 범위를 지정할 수 있는 변칙 검색 정책을 정의합니다. 이러한 변칙 검색 정책을 사용하면 Power BI에 액세스하고 사용하는 사용자와 관련된 동작 변칙을 검색하고 모니터링할 수 있습니다.

- [Power BI에서 Microsoft Cloud App Security 컨트롤 사용](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6: 조건에 따라 Azure 리소스 액세스 제한

**지침**: Power BI는 사용자 정의 조건에 따라 보다 세분화된 액세스 제어를 위해 Azure AD 조건부 액세스를 지원합니다. 예를 들어 특정 IP 범위의 사용자 로그인은 로그인에 MFA를 사용해야 합니다. 다양한 사용 사례에 대해 세부적인 인증 세션 관리 정책을 사용할 수도 있습니다.

- [Azure 조건부 액세스 개요](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)

- [일반적인 조건부 액세스 정책](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

- [조건부 액세스를 사용하여 인증 세션 관리 구성](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

- [Power BI에서 Microsoft Cloud App Security 컨트롤 사용](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="im-7-eliminate-unintended-credential-exposure"></a>IM-7: 의도하지 않은 자격 증명 노출 제거

**지침**: Power BI Embedded 애플리케이션의 경우 코드 내에서 자격 증명을 식별하는 자격 증명 검사기를 구현하는 것이 좋습니다. 또한 자격 증명 스캐너는 검색된 자격 증명을 더 안전한 위치(예: Azure Key Vault)로 이동하도록 추천합니다.

Power BI를 암호화하거나 액세스하는 데 사용되는 암호화 키 또는 서비스 주체 자격 증명을 Key Vault에 저장하고, 자격 증명 모음에 적절한 액세스 정책을 할당하고, 액세스 권한을 정기적으로 검토합니다.
 
GitHub의 경우 네이티브 암호 검색 기능을 사용하여 코드 내에서 자격 증명 또는 다른 형태의 암호를 식별할 수 있습니다.

- [Power BI의 BYOK(Bring Your Own Encryption Key)](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

 
자격 증명을 설정하는 방법
- [스캐너](https://secdevtools.azurewebsites.net/helpcredscan.html) 

- [GitHub 암호 검색](https://docs.github.com/github/administering-a-repository/about-secret-scanning)

**Azure Security Center 모니터링**: 해당 없음

**책임**: 공유됨

## <a name="privileged-access"></a>권한 있는 액세스

자세한 내용은 [Azure Security Benchmark: 권한 있는 액세스](/azure/security/benchmarks/security-controls-v2-privileged-access)를 참조하세요.

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1: 권한이 높은 사용자 보호 및 제한

**지침**: 위험을 줄이고 최소 권한의 원칙을 따르기 위해 Power BI 관리자의 구성원을 소수의 사용자로 유지하는 것이 좋습니다. 해당 권한이 있는 사용자는 잠재적으로 조직의 모든 관리 기능에 액세스하고 수정할 수 있습니다. 전역 관리자는 Microsoft 365 또는 Azure Active Directory를 통해 Power BI 서비스에서도 관리자 권한을 암시적으로 보유합니다.

Power BI에 있는 권한이 높은 계정은 다음과 같습니다.
- 글로벌 관리자
- 청구 관리자
- 라이선스 관리자
- 사용자 관리자
- Power BI 관리자
- Power BI Premium 용량 관리자
- Power BI Embedded 용량 관리자

Power BI는 조건부 액세스 정책을 지원하고 Cloud App Security 서비스를 통해 Power BI에서 사용되는 세션을 라우팅할 수 있도록 Azure AD에서 세션 정책을 지원합니다.

M365 권한 있는 액세스 관리를 사용하여 Power BI 관리자 계정에 JIT(Just-In-Time) 권한 있는 액세스를 사용하도록 설정합니다.

- [Power BI와 관련된 관리자 역할](https://docs.microsoft.com/power-bi/admin/service-admin-administering-power-bi-in-your-organization#administrator-roles-related-to-power-bi)

- [M365 권한 있는 액세스 관리](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true)

- [Power BI의 Cloud App Security 컨트롤](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2: 중요 비즈니스용 시스템에 대한 관리 액세스 제한

**지침**: Power BI에 대한 권한이 높은 계정 또는 권한이 상승된 액세스를 가진 역할의 수를 제한합니다.

M365 권한 있는 액세스 관리 지침([여기](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true))을 참조하여 JIT(Just-In-Time) 권한 있는 액세스를 사용하도록 설정할 수 있습니다.

자세한 내용은 Power BI 엔터프라이즈 배포 문서([여기](https://aka.ms/PBIEnterpriseDeploymentWP))의 183페이지에서 확인할 수 있습니다.

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3: 정기적으로 사용자 액세스 권한 검토 및 조정

**지침**: Power BI 서비스 관리자는 Power BI 활동 로그를 기반으로 하는 사용자 지정 보고서를 사용하여 테넌트 수준에서 모든 Power BI 리소스의 사용량을 분석할 수 있습니다. REST API 또는 PowerShell cmdlet을 사용하여 활동을 다운로드할 수 있습니다. 날짜 범위, 사용자, 활동 유형을 기준으로 활동 데이터를 필터링할 수도 있습니다.

Power BI 활동 로그에 액세스하려면 다음과 같은 요구 사항을 충족해야 합니다.
- 전역 관리자 또는 Power BI 서비스 관리자여야 합니다.
- [Power BI 관리 cmdlet](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt)을 로컬에 설치했거나, Azure Cloud Shell에서 Power BI 관리 cmdlet을 사용해야 합니다.

위의 요구 사항이 충족되면 아래 지침에 따라 Power BI 내에서 사용자 활동을 추적할 수 있습니다.

- [Power BI에서 사용자 활동 추적](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4: Azure AD에서 응급 액세스 설정

**지침**: Power BI는 Azure Active Directory 및 M365와 통합되어 해당 리소스를 관리합니다. M365 테넌트 또는 Azure AD 조직에서 실수로 잠기는 것을 방지하려면 일반 관리 계정을 사용할 수 없는 경우 액세스를 위해 응급 액세스 계정을 설정합니다. 응급 액세스 계정은 일반적으로 권한이 높으며 특정 사용자에게 할당되면 안 됩니다. 응급 액세스 계정은 일반 관리 계정을 사용할 수 없는 '비상' 시나리오의 긴급한 상황으로 제한됩니다.

응급 액세스 계정의 자격 증명(예: 암호, 인증서 또는 스마트 카드)을 안전하게 유지하고 비상시에만 사용할 권한이 있는 사용자에게만 알립니다.

- [Azure AD에서 응급 액세스 계정 관리](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access)

- [M365 계정 보호](https://docs.microsoft.com/microsoft-365/campaigns/m365-campaigns-protect-admin-accounts)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6: 권한 있는 액세스 워크스테이션 사용

**지침**: 안전하고 격리된 워크스테이션은 관리자, 개발자 및 중요 서비스 운영자와 같은 중요한 역할의 보안에 매우 중요합니다. Power BI 관리와 관련된 관리 작업에는 안전성이 뛰어난 사용자 워크스테이션 및/또는 Azure Bastion을 사용합니다. Azure Active Directory, Microsoft Defender ATP(Advanced Threat Protection) 및/또는 Microsoft Intune을 사용하여 관리 작업을 위한 관리형 보안 사용자 워크스테이션을 배포할 수 있습니다. 보안 워크스테이션을 중앙에서 관리하여 강력한 인증, 소프트웨어 및 하드웨어 기준, 제한된 논리적 액세스 및 네트워크 액세스를 비롯한 보안 구성을 적용할 수 있습니다.

권한 있는 액세스 이해
- [워크스테이션](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-managed-workstation)

- [권한 있는 액세스 워크스테이션 배포](https://docs.microsoft.com/azure/active-directory/devices/howto-azure-managed-workstation)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

## <a name="data-protection"></a>데이터 보호

자세한 내용은 [Azure Security Benchmark: 데이터 보호](/azure/security/benchmarks/security-controls-v2-data-protection)를 참조하세요.

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1: 중요한 데이터 검색, 분류 및 레이블 지정

**지침**: 보고서, 대시보드, 데이터 세트 및 데이터 흐름에 대해 Microsoft Information Protection 민감도 레이블을 사용하여 무단 데이터 액세스 및 누출로부터 중요한 콘텐츠를 보호합니다.

Microsoft Information Protection 민감도 레이블을 사용하여 Power BI 서비스에서 보고서, 대시보드, 데이터 세트, 데이터 흐름을 분류하고 레이블을 지정할 뿐만 아니라 Power BI 서비스에서 Excel, PowerPoint, PDF 파일로 콘텐츠를 내보낼 때 무단 데이터 액세스와 누출로부터 중요한 콘텐츠를 보호합니다.

- [Power BI에서 민감도 레이블을 적용하는 방법](https://docs.microsoft.com/power-bi/admin/service-security-apply-data-sensitivity-labels)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="dp-2-protect-sensitive-data"></a>DP-2: 중요한 데이터 보호

**지침**: Power BI는 Microsoft Information Protection 민감도 레이블과 통합되어 중요한 데이터를 보호합니다. 자세한 내용은 [Power BI의 Microsoft Information Protection 민감도 레이블](https://docs.microsoft.com/power-bi/admin/service-security-sensitivity-label-overview)을 참조하세요.

Power BI를 통해 서비스 사용자는 미사용 데이터를 보호하기 위해 고유한 키를 가져올 수 있습니다. 자세한 내용은 [Power BI의 BYOK(Bring Your Own Encryption Key)](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)를 참조하세요.

고객은 데이터 원본을 온-프레미스에 유지하고 온-프레미스 데이터 게이트웨이에 Direct Query 또는 Live Connect를 활용하여 클라우드 서비스에 대한 데이터 노출을 최소화하는 옵션을 사용할 수 있습니다. 자세한 내용은 [온-프레미스 데이터 게이트웨이란?](https://docs.microsoft.com/data-integration/gateway/service-gateway-onprem)을 참조하세요.

Power BI는 행 수준 보안을 지원합니다. 자세한 내용은 [Power BI에서 RLS(행 수준 보안)](https://docs.microsoft.com/power-bi/admin/service-admin-rls)를 참조하세요. PBIX 파일이 보안 설정 프록시의 역할을 하는 경우 Direct Query 데이터 원본에도 RLS를 적용할 수 있습니다.

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3: 중요한 데이터 무단 전송 모니터링

**지침**: Power BI에 대한 Microsoft Cloud App Security 지원을 통해 부분적으로 제어할 수 있습니다.

Power BI에서 Cloud App Security를 사용하면 의도하지 않은 유출이나 위반으로부터 Power BI 보고서, 데이터 및 서비스를 보호할 수 있습니다. Cloud App Security에서 Azure AD(Azure Active Directory)의 실시간 세션 제어를 통해 조직의 데이터에 대한 조건부 액세스 정책을 만들어 Power BI 분석의 보안을 유지할 수 있습니다. 이러한 정책을 설정하면 관리자가 사용자 액세스 및 활동을 모니터링하고, 실시간 위험 분석을 수행하며, 레이블 관련 제어를 설정할 수 있습니다.

사용
- [Power BI의 Microsoft Cloud App Security 컨트롤](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4: 전송 중인 중요한 정보 암호화

**지침**: HTTP 트래픽에서 Power BI 리소스에 연결되는 모든 클라이언트 및 데이터 원본은 TLS v1.2 이상을 협상할 수 있는지 확인합니다.

- [TLS 버전 사용 적용](https://docs.microsoft.com/power-bi/admin/service-admin-power-bi-security#enforcing-tls-version-usage)

- [TLS 보안에 대한 정보](https://docs.microsoft.com/security/engineering/solving-tls1-problem)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="dp-5-encrypt-sensitive-data-at-rest"></a>DP-5: 중요한 미사용 데이터 암호화

**지침**: Power BI는 미사용 데이터 및 처리 중인 데이터를 암호화합니다. 기본적으로 Power BI는 Microsoft 관리형 키를 사용하여 데이터를 암호화합니다. 조직은 보고서 이미지에서 프리미엄 용량의 가져온 데이터 세트에 이르기까지 Power BI 전체에서 미사용 사용자 콘텐츠 암호화를 위해 자체 키를 사용하도록 선택할 수 있습니다.

- [Power BI에서 Bring Your Own Key 사용](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Azure Security Center 모니터링**: 해당 없음

**책임**: 공유됨

## <a name="asset-management"></a>자산 관리

자세한 내용은 [Azure Security Benchmark: 자산 관리](/azure/security/benchmarks/security-controls-v2-asset-management)를 참조하세요.

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1: 보안 팀이 자산의 위험에 대한 가시성 확보

**지침**: Power BI Office 감사 로그와 함께 Azure Sentinel을 사용하여 보안 팀이 Power BI 자산에 대한 위험을 확인할 수 있게 합니다.

- [Azure Sentinel에 Office 365 로그 연결](https://docs.microsoft.com/azure/sentinel/connect-office-365)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2: 보안 팀에 자산 인벤토리 및 메타데이터에 대한 액세스 권한이 있는지 확인

**지침**: 보안 팀이 지속적으로 업데이트되는 Power BI Embedded 리소스 인벤토리에 액세스할 수 있는지 확인합니다. 보안 팀은 새로운 위험에 대한 조직의 잠재적인 노출을 평가하기 위해, 그리고 지속적으로 보안을 향상하기 위한 입력 정보로서 이 인벤토리가 필요한 경우가 많습니다. 

Azure Resource Graph는 구독에서 모든 Power BI Embedded 리소스를 쿼리하고 검색할 수 있습니다.  

Azure에서 태그뿐만 아니라 다른 메타데이터(이름, 설명, 범주)도 사용하여 조직의 분류법에 따라 자산을 논리적으로 구성합니다.  

- [Azure Resource Graph Explorer를 사용하여 쿼리를 만드는 방법](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

- [리소스 명명 및 태그 지정 의사 결정 가이드](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=/azure/azure-resource-manager/management/toc.json)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="am-3-use-only-approved-azure-services"></a>AM-3: 승인된 Azure 서비스만 사용

**지침**: Power BI는 Power BI Embedded에 대한 Azure Resource Manager 기반 배포를 지원합니다. 사용자 지정 정책 정의를 사용하여 Azure Policy를 통해 해당 리소스의 배포를 제한할 수 있습니다.

Azure Policy를 사용하여 환경에서 사용자가 프로비저닝할 수 있는 서비스를 감사하고 제한합니다. Azure Resource Graph를 사용하여 구독 내에서 리소스를 쿼리하고 검색합니다. 또한 Azure Monitor를 사용하여 승인되지 않은 서비스가 검색되면 경고를 트리거하는 규칙을 만들 수 있습니다.

- [Azure Policy를 구성하고 관리하는 방법](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage)

다음을 사용하여 특정 리소스 종류를 거부하는 방법
- [Azure Policy](https://docs.microsoft.com/azure/governance/policy/samples/built-in-policies#general)

Azure를 사용하여 쿼리를 만드는 방법
- [Resource Graph Explorer](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

## <a name="logging-and-threat-detection"></a>로깅 및 위협 탐지

자세한 내용은 [Azure Security Benchmark: 로깅 및 위협 탐지](/azure/security/benchmarks/security-controls-v2-logging-threat-protection)를 참조하세요.

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2: Azure ID 및 액세스 관리를 위한 위협 탐지 사용

**지침**: Power BI의 모든 로그를 사용자 지정 위협 탐지를 설정하는 데 사용할 수 있는 SIEM으로 전달합니다. 또한 [여기](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls) 나온 가이드를 참조하여 Power BI에서 MCAS(Microsoft Cloud App Security) 컨트롤을 사용해 변칙 검색을 사용하도록 설정합니다.

- [Power BI에서 사용자 활동 추적](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3: Azure 네트워크 활동에 대한 로깅 사용

**지침**: Power BI는 완전 관리형 SaaS 제품이며 기본 네트워크 구성 및 로깅은 Microsoft의 책임입니다. Private Link를 활용하는 고객의 경우 일부 로깅 및 모니터링을 구성할 수 있습니다.

- [Private Link 로깅 및 모니터링](https://docs.microsoft.com/azure/private-link/private-link-overview#logging-and-monitoring)

**Azure Security Center 모니터링**: 해당 없음

**책임**: 공유됨

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4: Azure 리소스에 대한 로깅 사용

**지침**: Power BI에는 사용자 활동을 추적하는 두 가지 옵션인 Power BI 활동 로그 및 통합 감사 로그가 있습니다. 두 로그에는 모두 Power BI 감사 데이터의 전체 복사본이 포함되지만, 다음에 요약된 것처럼 몇 가지 주요 차이점이 있습니다.
 
통합 감사 로그:

 
- Power BI 감사 이벤트 외에도 SharePoint Online, Exchange Online, Dynamics 365 및 기타 서비스의 이벤트를 포함합니다.

 
- 전역 관리자 및 감사자와 같이 보기 전용 감사 로그 또는 감사 로그 사용 권한이 있는 사용자만 액세스할 수 있습니다.

 
- 전역 관리자 및 감사자는 Microsoft 365 보안 센터 및 Microsoft 365 규정 준수 센터를 사용하여 통합 감사 로그를 검색할 수 있습니다.

 
- 전역 관리자 및 감사자는 Microsoft 365 관리 API 및 cmdlet을 사용하여 감사 로그 항목을 다운로드할 수 있습니다.

 
- 90일간 감사 데이터를 유지합니다.

 
- 테넌트가 다른 Azure 지역으로 이동하더라도 감사 데이터를 유지합니다.
 
Power BI 활동 로그:

 
- Power BI 감사 이벤트만 포함합니다.

 
 
- 전역 관리자 및 Power BI 서비스 관리자가 액세스할 수 있습니다.

 
- 활동 로그를 검색하기 위한 사용자 인터페이스는 아직 없습니다.

 
- 전역 관리자 및 Power BI 서비스 관리자는 Power BI REST API 및 관리 cmdlet을 사용하여 활동 로그 항목을 다운로드할 수 있습니다.

 
- 30일간 활동 데이터를 유지합니다.

 
- 테넌트가 다른 Azure 지역으로 이동하면 활동 데이터를 보존하지 않습니다.

- [Power BI 감사 데이터](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Power BI 활동 로그](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Power BI 감사 로그](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Azure Security Center 모니터링**: 해당 없음

**책임**: 공유됨

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5: 보안 로그 관리 및 분석 중앙 집중화

**지침**: Power BI는 Power BI 활동 로그와 통합 감사 로그의 두 위치에 로그를 중앙 집중화합니다. 두 로그에는 모두 Power BI 감사 데이터의 전체 복사본이 포함되지만, 다음에 요약된 것처럼 몇 가지 주요 차이점이 있습니다.
 

통합 감사 로그:

- Power BI 감사 이벤트 외에도 SharePoint Online, Exchange Online, Dynamics 365 및 기타 서비스의 이벤트를 포함합니다.

- 전역 관리자 및 감사자와 같이 보기 전용 감사 로그 또는 감사 로그 사용 권한이 있는 사용자만 액세스할 수 있습니다.

- 전역 관리자 및 감사자는 Microsoft 365 Security Center 및 Microsoft 365 규정 준수 센터를 사용하여 통합 감사 로그를 검색할 수 있습니다.

- 전역 관리자 및 감사자는 Microsoft 365 관리 API 및 cmdlet을 사용하여 감사 로그 항목을 다운로드할 수 있습니다.

- 90일간 감사 데이터를 유지합니다.

- 테넌트가 다른 Azure 지역으로 이동하더라도 감사 데이터를 유지합니다.

 

Power BI 활동 로그:

- Power BI 감사 이벤트만 포함합니다.

- 전역 관리자 및 Power BI 서비스 관리자가 액세스할 수 있습니다.

- 활동 로그를 검색하기 위한 사용자 인터페이스는 아직 없습니다.

- 전역 관리자 및 Power BI 서비스 관리자는 Power BI REST API 및 관리 cmdlet을 사용하여 활동 로그 항목을 다운로드할 수 있습니다.

- 30일간 활동 데이터를 유지합니다.

- 테넌트가 다른 Azure 지역으로 이동하면 활동 데이터를 보존하지 않습니다.

- [Power BI 감사 데이터](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Power BI 활동 로그](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Power BI 감사 로그](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="lt-6-configure-log-storage-retention"></a>LT-6: 로그 스토리지 보존 구성

**지침**: 규정 준수, 규정 및 비즈니스 요구 사항에 따라 Office 감사 로그의 스토리지 보존 정책을 구성합니다.

- [Office 감사 로그 보존 정책](https://docs.microsoft.com/microsoft-365/compliance/audit-log-retention-policies)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

## <a name="incident-response"></a>사고 대응

자세한 내용은 [Azure Security Benchmark: 인시던트 응답](/azure/security/benchmarks/security-controls-v2-incident-response)을 참조하세요.

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: 준비 - Azure에 대한 인시던트 응답 프로세스 업데이트

**지침**: 조직이 보안 인시던트에 대응하는 프로세스를 보유하고, 해당 프로세스를 Azure에 대해 업데이트했으며, 준비 상태를 확인하기 위해 프로세스를 정기적으로 수행하는지 확인합니다.

- [엔터프라이즈 환경에서 보안 구현](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [인시던트 응답 참조 가이드](https://docs.microsoft.com/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: 준비 - 인시던트 알림 설정

**지침**: Azure Security Center에서 보안 인시던트 연락처 정보를 설정합니다. 이 연락처 정보는 MSRC(Microsoft 보안 대응 센터)가 불법적인 당사자나 권한 없는 당사자가 데이터에 액세스한 것을 발견한 경우 Microsoft가 연락하는 데 사용됩니다. 또한 인시던트 응답 요구 사항에 따라 다양한 Azure 서비스에서 인시던트 경고 및 알림을 사용자 지정하는 옵션도 있습니다. 

- [Azure Security Center 보안 연락처를 설정하는 방법](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: 탐지 및 분석 – 고품질 경고를 기반으로 인시던트 만들기

**지침**: 고품질 경고를 만들고 경고의 품질을 측정하는 프로세스가 있는지 확인합니다. 이렇게 하면 이전 인시던트에서 상황을 확인하고 분석가를 위한 경고의 우선 순위를 지정할 수 있으므로 가양성으로 인해 시간을 낭비하지 않습니다.

Microsoft Cloud App Security에서 Power BI와 관련된 경고를 모니터링합니다. 고품질 경고는 이전 인시던트, 유효성이 검사된 커뮤니티 소스, 다양한 신호 원본을 결합하고 상관 관계를 설정하여 경고를 생성하고 정리하도록 설계된 도구 등에서 얻은 경험을 기반으로 구축할 수 있습니다.

- [Cloud App Security의 경고 모니터링](https://docs.microsoft.com/cloud-app-security/monitor-alerts)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: 탐지 및 분석 – 인시던트 조사

**지침**: 조직에 대한 인시던트 대응 지침을 작성합니다. 정기적으로 시스템의 인시던트 응답 기능을 테스트하는 연습을 수행합니다. 약점과 결함을 식별하고 필요에 따라 계획을 수정합니다.

탐지에서 인시던트 사후 검토까지의 인시던트 처리/관리 단계뿐만 아니라 담당자의 모든 역할도 정의하는 인시던트 대응 계획이 작성되어 있는지 확인합니다.

- [Microsoft Threat Protection의 인시던트 개요](https://docs.microsoft.com/microsoft-365/security/mtp/incidents-overview)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: 탐지 및 분석 – 인시던트 우선 순위 지정

**지침**: 경고 심각도 및 자산 민감도에 따라 처음에 집중할 인시던트에 대해 분석가에게 컨텍스트를 제공합니다. 

 
Microsoft Threat Protection은 상관 관계 분석을 적용하고 다른 제품의 모든 관련 경고 및 조사를 하나의 인시던트에 집계합니다. Microsoft Threat Protection은 또한 Microsoft Threat Protection이 전체 환경 및 제품군에서 확보한 엔드투엔드 가시성을 고려하여 악의적인 것으로 식별할 수 있는 활동에 대해서만 고유한 경고를 트리거합니다. 따라서 Microsoft Threat Protection은 더 광범위한 공격 상황을 파악하여 보안 운영 분석가가 조직 전체의 복잡한 위협을 이해하고 처리할 수 있게 합니다.

- [Microsoft Threat Protection에서 인시던트 우선 순위 지정](https://docs.microsoft.com/microsoft-365/security/mtp/incident-queue?view=o365-worldwide&amp;preserve-view=true)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: 차단, 제거, 복구 - 인시던트 처리 자동화

**지침**: 수동 반복 작업을 자동화하여 응답 시간을 단축하고 분석가의 부담을 줄입니다. 수동 작업은 실행하는 데 더 오래 걸려 각 인시던트의 속도를 늦추고 분석가가 처리할 수 있는 인시던트 수를 줄입니다. 또한 수동 작업으로 인해 분석가의 피로 증가하여 지연을 유발하는 작업자 오류의 위험이 상승하고 분석가가 복잡한 작업에 효과적으로 집중할 수 있는 기능을 저하시킬 수 있습니다.  
 
Microsoft Threat Protection의 워크플로 자동화 기능을 사용하여 들어오는 보안 경고에 대한 응답으로 조사 및 수정을 자동으로 트리거합니다. 
 
- [Microsoft Threat Protection의 자동 조사 및 응답](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

## <a name="posture-and-vulnerability-management"></a>태세 및 취약성 관리

자세한 내용은 [Azure Security Benchmark: 태세 및 취약성 관리](/azure/security/benchmarks/security-controls-v2-vulnerability-management)를 참조하세요.

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1: Azure 서비스에 대한 보안 구성 설정 

**지침**: 조직과 보안 태세에 적절한 설정으로 Power BI 서비스를 구성합니다. 서비스, 콘텐츠에 대한 액세스와 작업 영역 및 앱 보안에 대한 설정은 신중하게 고려해야 합니다. Power BI 엔터프라이즈 배포 백서에서 Power BI 보안 및 데이터 보호를 참조하세요.

- [엔터프라이즈 배포 백서](https://aka.ms/PBIEnterpriseDeploymentWP)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="pv-2-sustain-secure-configurations-for-azure-services"></a>PV-2: Azure 서비스에 대한 보안 구성 유지

**지침**: Power BI Admin REST API를 사용하여 Power BI 인스턴스를 모니터링합니다.

- [Power BI Admin REST API](https://docs.microsoft.com/rest/api/power-bi/admin)

- [Power BI 엔터프라이즈 배포 백서](https://aka.ms/PBIEnterpriseDeploymentWP)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: 정기적인 공격 시뮬레이션 수행

**지침**: 필요에 따라 Azure 리소스에 대한 침투 테스트 또는 레드 팀 활동을 수행하고 모든 중요한 보안 결과를 수정해야 합니다.

Microsoft Cloud 침투 테스트 시행 규칙에 따라 침투 테스트가 Microsoft 정책을 위반하지 않는지 확인합니다. Microsoft의 전략과 Microsoft에서 관리하는 클라우드 인프라, 서비스, 애플리케이션에 대한 레드 팀 실행 및 실시간 사이트 침투 테스트를 사용합니다.

- [Azure의 침투 테스트](https://docs.microsoft.com/azure/security/fundamentals/pen-testing)

- [침투 테스트 시행 규칙](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [Microsoft Cloud 레드 팀](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Azure Security Center 모니터링**: 해당 없음

**책임**: 공유됨

## <a name="backup-and-recovery"></a>백업 및 복구

자세한 내용은 [Azure Security Benchmark: 백업 및 복구](/azure/security/benchmarks/security-controls-v2-backup-recovery)를 참조하세요.

### <a name="br-3-validate-all-backups-including-customer-managed-keys"></a>BR-3: 고객 관리형 키를 비롯한 모든 백업 유효성 검사

**지침**: Power BI에서 BYOK(Bring Your Own Key) 기능을 사용하는 경우 고객 관리형 키에 액세스하고 복원할 수 있는지 주기적으로 확인해야 합니다.

- [Power BI의 BYOK](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4: 분실한 키의 위험 완화

**지침**: Power BI에서 BYOK(Bring Your Own Key) 기능을 사용하는 경우 고객 관리형 키를 제어하는 Key Vault가 아래에 나온 Power BI의 BYOK 설명서 지침에 따라 구성되었는지 확인해야 합니다. Azure Key Vault에서 일시 삭제 및 제거 보호를 사용하도록 설정하여 실수로 또는 악의적으로 삭제되지 않도록 키를 보호합니다.

- [Power BI의 BYOK](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

- [Key Vault에서 일시 삭제 및 제거 보호를 사용하도록 설정하는 방법](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal)

게이트웨이 키 리소스의 경우 아래의 게이트웨이 복구 키 설명서에 나온 지침을 수행하고 있는지 확인합니다.

- [온-프레미스 데이터 게이트웨이 복구 키](https://docs.microsoft.com/data-integration/gateway/service-gateway-recovery-key)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

## <a name="governance-and-strategy"></a>거버넌스 및 전략

자세한 내용은 [Azure Security Benchmark: 거버넌스 및 전략](/azure/security/benchmarks/security-controls-v2-governance-strategy)을 참조하세요.

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: 자산 관리 및 데이터 보호 전략 정의 

**지침**: 시스템 및 데이터를 지속적으로 모니터링하고 보호하기 위한 명확한 전략을 문서화하고 전달해야 합니다. 중요 비즈니스용 데이터 및 시스템의 검색, 평가, 보호, 모니터링에 우선 순위를 지정합니다. 

이 전략에는 다음 요소에 대한 문서화된 지침, 정책, 표준이 포함되어야 합니다. 

-   비즈니스 위험에 따른 데이터 분류 표준

-   위험 및 자산 인벤토리에 대한 보안 조직의 가시성 

-   사용할 Azure 서비스에 대한 보안 조직의 승인 

-   수명 주기 전체에서 자산 보안

-   조직 데이터 분류에 따라 필요한 액세스 제어 전략

-   Azure 기본 및 타사 데이터 보호 기능 사용

-   전송 중 및 미사용 사용 사례에 대한 데이터 암호화 요구 사항

-   적절한 암호화 표준

자세한 내용은 다음 참조 문서를 참조하세요.
- [Azure 보안 아키텍처 권장 사항 - 스토리지, 데이터, 암호화](https://docs.microsoft.com/azure/architecture/framework/security/storage-data-encryption?toc=/security/compass/toc.json&amp;bc=/security/compass/breadcrumb/toc.json)

- [Azure 보안 기본 사항 - Azure 데이터 보안, 암호화, 스토리지](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview)

- [클라우드 채택 프레임워크 - Azure 데이터 보안 및 암호화 모범 사례](https://docs.microsoft.com/azure/security/fundamentals/data-encryption-best-practices?toc=/azure/cloud-adoption-framework/toc.json&amp;bc=/azure/cloud-adoption-framework/_bread/toc.json)

- [Azure Security Benchmark - 자산 관리](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-asset-management)

- [Azure Security Benchmark - 데이터 보호](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-data-protection)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: 엔터프라이즈 구분 전략 정의 

**지침**: ID, 네트워크, 애플리케이션, 구독, 관리 그룹 및 기타 컨트롤의 조합을 사용하여 자산에 대한 액세스를 구분하는 엔터프라이즈 전체 전략을 수립합니다.

서로 통신하고 데이터에 액세스해야 하는 시스템의 일상 작업을 사용하도록 설정해야 할 필요성과 보안 분리의 필요성을 신중하게 조정해야 합니다.

구분 전략이 네트워크 보안, ID 및 액세스 모델, 애플리케이션 권한/액세스 모델 및 사용자 프로세스 컨트롤을 비롯하여 컨트롤 형식 간에 일관되게 구현되는지 확인합니다.

- [Azure의 구분 전략에 대한 지침(동영상)](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Azure의 구분 전략에 대한 지침(문서)](https://docs.microsoft.com/security/compass/governance#enterprise-segmentation-strategy)

- [엔터프라이즈 구분 전략에 맞춰 네트워크 구분 조정](https://docs.microsoft.com/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: 보안 태세 관리 전략 정의

**지침**: 개별 자산과 해당 자산이 호스트되는 환경에 대한 위험을 지속적으로 측정하고 완화합니다. 게시된 애플리케이션, 네트워크 수신 및 송신 지점, 사용자 및 관리자 엔드포인트 등과 같은 고가치 자산과 노출이 많은 공격 노출 영역에 우선 순위를 지정합니다.

- [Azure Security Benchmark - 태세 및 취약성 관리](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-posture-vulnerability-management)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: 조직 역할, 책임, 의무 조정

**지침**: 보안 조직의 역할 및 책임에 대한 명확한 전략을 문서화하고 전달하는지 확인합니다. 보안 의사 결정에 대한 명확한 책임을 제시하고, 공유 책임 모델을 모두에게 교육하고, 클라우드를 보호하는 기술에 관해 기술 팀을 교육하는 일에 우선 순위를 지정합니다.

- [Azure 보안 모범 사례 1 – 사용자: 클라우드 보안 경험에 대한 팀 교육](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Azure 보안 모범 사례 2 – 사용자: 클라우드 보안 기술에 대한 팀 교육](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Azure 보안 모범 사례 3 – 프로세스: 클라우드 보안 결정에 대한 책임 할당](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="gs-5-define-network-security-strategy"></a>GS-5: 네트워크 보안 전략 정의

**지침**: 조직의 전반적인 보안 액세스 제어 전략의 일부로 Azure 네트워크 보안 방법을 설정합니다.  

이 전략에는 다음 요소에 대한 문서화된 지침, 정책, 표준이 포함되어야 합니다. 

-   중앙 집중식 네트워크 관리 및 보안 책임

-   엔터프라이즈 구분 전략에 맞춰 조정된 가상 네트워크 구분 모델

-   다양한 위협 및 공격 시나리오에서 수정 전략

-   인터넷 에지 및 수신/송신 전략

-   하이브리드 클라우드 및 온-프레미스 상호 연결 전략

-   최신 네트워크 보안 아티팩트(예: 네트워크 다이어그램, 참조 네트워크 아키텍처)

자세한 내용은 다음 참조 문서를 참조하세요.
- [Azure 보안 모범 사례 11 – 아키텍처 단일 통합 보안 전략](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure Security Benchmark - 네트워크 보안](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-network-security)

- [Azure 네트워크 보안 개요](https://docs.microsoft.com/azure/security/fundamentals/network-overview)

- [엔터프라이즈 네트워크 아키텍처 전략](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: ID 및 권한 있는 액세스 전략 정의

**지침**: 조직의 전반적인 보안 액세스 제어 전략의 일부로 Azure ID 및 권한 있는 액세스 방법을 설정합니다.  

이 전략에는 다음 요소에 대한 문서화된 지침, 정책, 표준이 포함되어야 합니다. 

-   중앙 집중식 ID 및 인증 시스템과 다른 내부 및 외부 ID 시스템 간의 상호 연결

-   다양한 사용 사례 및 조건에서 강력한 인증 방법

-   권한이 높은 사용자 보호

-   변칙 사용자 활동 모니터링 및 처리  

-   사용자 ID 및 액세스 검토와 조정 프로세스

자세한 내용은 다음 참조 문서를 참조하세요.

- [Azure Security Benchmark - ID 관리](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-identity-management)

- [Azure Security Benchmark - 권한 있는 액세스](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-privileged-access)

- [Azure 보안 모범 사례 11 – 아키텍처 단일 통합 보안 전략](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure ID 관리 보안 개요](https://docs.microsoft.com/azure/security/fundamentals/identity-management-overview)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: 로깅 및 위협 대응 전략 정의

**지침**: 규정 준수 요구 사항을 충족하면서 신속하게 위협을 탐지하고 수정할 수 있는 로깅 및 위협 대응 전략을 수립합니다. 통합 및 수동 단계가 아닌 위협에 집중할 수 있도록 분석가에게 고품질 경고 및 원활한 환경을 제공하는 것에 우선 순위를 지정합니다. 

이 전략에는 다음 요소에 대한 문서화된 지침, 정책, 표준이 포함되어야 합니다. 

-   보안 운영(SecOps) 조직의 역할 및 책임 

-   NIST 또는 다른 업계 프레임워크를 사용하여 잘 정의된 인시던트 응답 프로세스 

-   위협 탐지, 인시던트 응답 및 규정 준수 요구 사항을 지원하는 로그 캡처 및 보존

-   SIEM, 네이티브 Azure 기능, 기타 소스를 사용하여 위협에 대한 중앙 집중식 가시성 및 상관 관계 정보 

-   고객, 공급자 및 공공 당사자와의 통신 및 알림 계획

-   로깅 및 위협 탐지, 포렌식, 공격 수정, 제거와 같은 인시던트 처리를 위해 Azure 네이티브 및 타사 플랫폼 사용

-   확인한 상황 및 증거 보존을 포함하여 인시던트 및 인시던트 후 활동을 처리하는 프로세스

자세한 내용은 다음 참조 문서를 참조하세요.

- [Azure Security Benchmark - 로깅 및 위협 탐지](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-logging-threat-detection)

- [Azure Security Benchmark - 인시던트 응답](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-incident-response)

- [Azure 보안 모범 사례 4 - 프로세스 클라우드에 대한 인시던트 응답 프로세스 업데이트](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Azure 채택 프레임워크, 로깅, 보고 의사 결정 가이드](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Azure 엔터프라이즈 규모, 관리, 모니터링](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Azure Security Center 모니터링**: 해당 없음

**책임**: Customer

## <a name="next-steps"></a>다음 단계

- [Azure Security Benchmark V2 개요](/azure/security/benchmarks/overview)를 참조하세요.
- [Azure 보안 기준](/azure/security/benchmarks/security-baselines-overview)에 대해 자세히 알아보세요.
