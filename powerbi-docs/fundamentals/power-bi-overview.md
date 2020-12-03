---
title: Power BI란?
description: Power BI 개요 및 다양한 부분의 연동 방식 - Power BI Desktop, Power BI 서비스, Power BI Mobile, Report Server 및 Power BI Embedded.
author: mihart
ms.author: mihart
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: overview
ms.date: 09/23/2020
LocalizationGroup: Get started
ms.openlocfilehash: acbd0761b481ec4884ab94d50de219a2d753b574
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416534"
---
# <a name="what-is-power-bi"></a>Power BI란?
**Power BI** 는 관련 없는 데이터 소스를 시각적으로 몰입도가 뛰어나고 일관된 대화형 정보로 변환하는 소프트웨어 서비스, 앱 및 커넥터의 컬렉션입니다. 데이터는 Excel 스프레드시트이거나 클라우드 기반 및 온-프레미스 하이브리드 데이터 웨어하우스의 컬렉션일 수 있습니다. Power BI를 사용하면 쉽게 데이터 원본에 연결하고, 중요한 항목을 시각화 및 검색하고, 원하는 모든 사람과 공유할 수 있습니다.

## <a name="the-parts-of-power-bi"></a>Power BI의 요소
Power BI는 다음 세 가지 기본 사항부터 시작하여 모두 함께 작동하는 여러 요소로 구성됩니다. 
- **Power BI Desktop** 이라는 Windows 데스크톱 애플리케이션.
- **Power BI 서비스** 라는 온라인 SaaS(*Software as a Service*) 서비스. 
- Windows, iOS 및 Android 디바이스용 Power BI **모바일 앱**.

![Power BI Desktop, 서비스 및 Mobile의 통합을 보여주는 다이어그램 스크린샷.](media/power-bi-overview/power-bi-overview-blocks.png)

이 세 가지 요소(&mdash;Power BI Desktop, 서비스 및 모바일 앱&mdash;)는 직원들이 자신 또는 자신의 역할에 가장 효과적으로 비즈니스 인사이트를 생성, 공유, 사용하도록 설계되었습니다.

이 세 가지 외에도 Power BI에는 두 가지 다른 요소가 있습니다.

- **Power BI 보고서 작성기**: Power BI 서비스에서 공유할 페이지가 매겨진 보고서를 만듭니다. 이 문서의 뒷부분에 나오는 [페이지가 매겨진 보고서](#paginated-reports-in-the-power-bi-service)에 대해 자세히 알아보세요.
- **Power BI Report Server**: Power BI Desktop에서 만든 후 Power BI 보고서를 게시할 수 있는 온-프레미스 보고서 서버입니다. 이 문서 뒤부분에 나오는 [Power BI Report Server](#on-premises-reporting-with-power-bi-report-server)에 대해 자세히 알아보세요.

## <a name="how-power-bi-matches-your-role"></a>Power BI와 사용자 역할을 일치시키는 방법
Power BI 사용 방법은 프로젝트 또는 팀에서 사용자의 역할에 따라 달라질 수 있습니다. 다른 역할을 맡은 사람은 Power BI를 다른 방식으로 사용할 수도 있습니다.

예를 들어 여러분은 주로 **Power BI 서비스** 를 사용하여 보고서 및 대시보드를 볼 수 있습니다. 숫자를 다루는 비즈니스 보고서를 작성하는 동료는 **Power BI Desktop** 또는 **Power BI 보고서 작성기** 를 광범위하게 사용하여 보고서를 만든 다음, 여러분이 보는 Power BI 서비스에 해당 보고서를 게시할 수 있습니다. 영업을 담당하는 또 다른 동료는 주로 **Power BI 전화 앱** 을 사용하여 영업 할당량 관련 진행 상황을 모니터링하고 새로운 잠재 고객의 세부 정보를 확인할 수 있습니다.

개발자인 경우 Power BI API를 사용하여 데이터를 데이터 세트로 푸시하거나 대시보드와 보고서를 사용자 지정 애플리케이션에 포함할 수 있습니다. 새로운 시각적 개체에 대한 아이디어가 있나요? 직접 빌드하고 다른 사람과 공유합니다.  

달성하려는 목표 또는 지정된 프로젝트에서 맡은 역할에 따라 Power BI의 각 요소를 서로 다른 시점에 사용할 수도 있습니다.

Power BI 사용 방법은 상황에 가장 적합한 Power BI 도구나 서비스가 무엇이냐에 따라 다를 수 있습니다. 예를 들어 Power BI Desktop을 사용하여 팀을 위해 고객 참여 통계에 대한 보고서를 만들고 Power BI 서비스의 실시간 대시보드에서 재고 및 제조 진행 상황을 볼 수 있습니다. Power BI 데이터 세트를 기반으로 페이지가 매겨진 우편 송장의 보고서를 만들 수 있습니다. 상황에 맞게 Power BI의 각 부분을 사용할 수 있어서 매우 유연하고 매력적입니다.

역할과 관련된 문서를 살펴보세요.
- [*비즈니스 사용자*](../consumer/end-user-consumer.md)를 위한 Power BI
- [*보고서 작성자*](desktop-what-is-desktop.md)를 위한 Power BI Desktop
- [*엔터프라이즈 보고서 작성자*](../paginated-reports/paginated-reports-report-builder-power-bi.md)를 위한 Power BI 보고서 작성기
- [ *‘관리자용’*](../admin/service-admin-administering-power-bi-in-your-organization.md) Power BI
- *개발자* 용 Power BI
    * [Power BI를 사용한 임베디드 분석](../developer/embedded/embedding.md)
    * [Azure의 Power BI Embedded란?](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)
    * [Power BI의 시각적 개체](../developer/visuals/power-bi-custom-visuals.md)
    * [개발자는 Power BI API로 무엇을 할 수 있나요?](../developer/automation/overview-of-power-bi-rest-api.md)

## <a name="the-flow-of-work-in-power-bi"></a>Power BI의 작업 흐름
Power BI의 일반적인 워크플로 중 하나는 Power BI Desktop에서 데이터 원본에 연결하고 보고서를 빌드하는 것으로 시작합니다. 그런 다음, Power BI Desktop에서 Power BI 서비스로 해당 보고서를 게시하고 Power BI 서비스 및 모바일 디바이스의 비즈니스 사용자가 보고서를 보고 상호 작용할 수 있도록 공유합니다.

이 워크플로가 일반적이며 세 가지 주요 Power BI 요소가 서로를 어떻게 보완하는지를 보여줍니다.

다음은 [Power BI Desktop과 Power BI 서비스의 자세한 비교](../fundamentals/service-service-vs-desktop.md)입니다.

## <a name="paginated-reports-in-the-power-bi-service"></a>Power BI 서비스의 페이지를 매긴 보고서

다른 워크플로에는 Power BI 서비스의 페이지가 매겨진 보고서가 포함됩니다. 엔터프라이즈 보고서 작성자는 인쇄 또는 공유할 페이지가 매겨진 보고서를 디자인합니다. 이러한 보고서를 Power BI 서비스에서 공유할 수도 있습니다. 이러한 보고서가 페이지를 매긴 보고서로 불리는 이유는 페이지에 적합하게 형식 지정되어 있기 때문입니다. 작업 보고서 또는 청구서나 기록과 같은 양식을 인쇄하는 경우에 자주 사용됩니다. 이러한 보고서에는 테이블이 여러 페이지에 걸쳐 있는 경우에도 테이블의 모든 데이터가 표시됩니다. Power BI Report Builder는 페이지를 매긴 보고서를 작성하기 위한 독립 실행형 도구입니다.

:::image type="content" source="media/power-bi-overview/paginated-report-invoice-power-bi-service.png" alt-text="Power BI 서비스의 페이지를 매긴 보고서의 스크린샷.":::

Power BI 서비스의 [페이지를 매긴 보고서](../paginated-reports/paginated-reports-report-builder-power-bi.md)에 대해 자세히 알아보세요.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Power BI Report Server를 사용하는 온-프레미스 보고

방화벽 뒤에서 보고서를 온-프레미스에 유지해야 하는 경우 어떻게 해야 하나요?  계속 읽어보세요.

Power BI Report Server에서 제공하는 바로 사용 가능한 도구와 서비스를 사용하여 Power BI Desktop 및 Power BI의 페이지를 매긴 보고서를 만들고, 배포하고, 관리할 수 있습니다.

![Power BI Report Server, 서비스 및 모바일의 통합을 보여주는 다이어그램 스크린샷.](media/power-bi-overview/power-bi-report-server2.png)

Power BI Report Server는 방화벽 뒤에 배포한 다음, 웹 브라우저, 모바일 디바이스 또는 메일로 보는지에 관계없이 다양한 방법으로 적합한 사용자에게 보고서를 배달하는 솔루션입니다. 그리고 Power BI Report Server는 클라우드의 Power BI와 호환되므로 준비가 되면 클라우드로 이동할 수 있습니다. 

[Power BI Report Server](../report-server/get-started.md)에 대해 자세히 알아보세요.

## <a name="next-steps"></a>다음 단계
- [빠른 시작: Power BI 서비스 사용 방법 알아보기](../consumer/end-user-experience.md)   
- [자습서: Power BI 서비스 시작](service-get-started.md)
- [빠른 시작: Power BI Desktop에서 데이터에 연결](../connect-data/desktop-quickstart-connect-to-data.md)
