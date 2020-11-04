---
title: Power BI 페이지를 매긴 보고서의 하위 보고서 문제 해결
description: 페이지를 매긴 보고서 내부의 보고서 항목인 하위 보고서를 사용하는 경우 일반적인 문제의 해결 방법에 관해 알아봅니다.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: troubleshooting
ms.date: 04/29/2020
ms.openlocfilehash: 06d9b0fc60d9b44f98108cf46bc35c5de15316d6
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297995"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Power BI 페이지를 매긴 보고서의 하위 보고서 문제 해결

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

페이지를 매긴 보고서에서 하위 보고서를 사용하는 경우 예기치 않은 결과를 얻거나 기능이 예상대로 작동하지 않을 수 있습니다. 이 문서에서는 하위 보고서를 사용할 때 발생하는 일반적인 문제의 솔루션을 제공합니다. *하위 보고서* 는 페이지를 매긴 주 보고서의 본문 안에 다른 보고서를 표시하는 보고서 항목입니다. 자세한 배경 정보는 [Power BI 페이지를 매긴 보고서의 하위 보고서](subreports.md)를 참조하세요.

## <a name="subreport-couldnt-be-found"></a>하위 보고서를 찾을 수 없음

**설명:** 하위 보고서가 렌더링되지 않습니다. 대신 오류 메시지가 표시됩니다.

### <a name="message"></a>메시지

"지정된 'CustomerDetails' 위치에서 하위 보고서 'Subreport1'을 찾을 수 없습니다. 하위 보고서가 게시되었으며 이름이 올바른지 확인하세요."

### <a name="possible-reasons"></a>가능한 이유

- 지정된 이름의 하위 보고서가 주 보고서와 같은 작업 영역 또는 앱에 없습니다.
- 사용자가 하위 보고서에 액세스할 수 없습니다.
- 주 보고서의 하위 보고서 수가 하위 보고서 제한(하위 보고서 50개)에 도달했습니다.

### <a name="troubleshooting-steps"></a>문제 해결 단계

**작업 영역에서**

- 오류 메시지에 이름이 있는 보고서가 있는지 확인합니다. 이름은 대소문자를 구분하지 않습니다.

**앱에서**

- 오류 메시지에 이름이 있는 보고서가 앱에 있는지 확인합니다. 추가 지원은 앱 작성자에게 문의하세요.

**보고서가 공유되는 경우**

1. 오류 메시지에 이름이 있는 보고서가 공유되었는지 확인합니다.
2. 보고서가 있으면 주 보고서와 하위 보고서의 소유자 이름이 같은지 확인합니다. 그런 다음 해당 정보가 있는 주 보고서의 소유자에게 문의합니다.

## <a name="subreport-renders-with-unexpected-content"></a>예기치 않은 콘텐츠로 하위 보고서 렌더링

### <a name="possible-reason"></a>가능한 원인

Power BI를 사용하면 사용자가 같은 작업 영역에 이름이 같은 보고서를 여러 개 가질 수 있음

### <a name="troubleshooting-steps-for-report-authors"></a>문제 해결 단계(보고서 작성자용)

1. Power BI Report Builder에서 주 보고서를 열고 하위 보고서의 이름을 확인합니다.
2. 작업 영역에서 이름이 같은 보고서를 찾습니다.
3. 예상 보고서를 찾아 나머지의 이름을 바꿉니다.

**비작성자의 경우:** 작성자에게 문의하세요.

## <a name="data-retrieval-fails"></a>데이터 검색 실패

**설명:** 하위 보고서를 렌더링하는 동안 데이터 검색에 실패합니다. 하위 보고서가 렌더링되지 않습니다. 대신 오류 메시지가 표시됩니다.

### <a name="message"></a>메시지

"'다음 위치에 있는 하위 보고서 'Subreport1'의 데이터 검색에 실패했습니다. 'InvoiceDetails'. 자세한 내용은 로그 파일을 확인하세요."

### <a name="troubleshooting-steps"></a>문제 해결 단계

데이터 액세스 문제가 있는 보고서에 대한 일반적인 문제 해결 단계와 동일합니다.

## <a name="rendering-fails-unspecified-parameters"></a>렌더링 실패: 지정되지 않은 매개 변수

**설명:** 지정되지 않은 매개 변수로 인해 하위 보고서 렌더링에 실패합니다. 하위 보고서에는 필수 매개 변수가 있지만 주 보고서에서 모든 매개 변수를 설정하지는 않습니다.

### <a name="message"></a>메시지 
"다음 위치에 있는 하위 보고서 'Subreport1'에 대해 하나 이상의 매개 변수가 지정되지 않았습니다. 'SubreportAWithDS'."

### <a name="troubleshooting-steps-for-the-report-author"></a>문제 해결 단계(보고서 작성자용)

1. Power BI Report Builder에서 주 보고서 열기
2. Power BI Report Builder에서 하위 보고서 열기
3. 주 보고서의 하위 보고서 항목 내에 전달된 매개 변수 집합이 하위 보고서의 매개 변수 집합과 일치하는지 확인합니다.

**비작성자의 경우:** 작성자에게 문의하세요.

## <a name="rendering-fails-recursion-limit"></a>렌더링 실패: 재귀 제한

**설명:** 재귀 제한으로 인해 하위 보고서 렌더링에 실패합니다. 하위 보고서는 20개 수준보다 더 깊이 중첩될 수 없습니다.

### <a name="message"></a>메시지

"보고서 또는 하위 보고서에 재귀적 하위 보고서 'Subreport1'이 있습니다. 이 보고서는 최대 허용 재귀 제한을 초과했습니다."

### <a name="troubleshooting-steps-for-report-authors"></a>문제 해결 단계(보고서 작성자용)

- 중첩을 줄입니다.
- 보고서 구조를 다시 디자인합니다.

## <a name="other-errors"></a>다른 오류

**설명:** 이전 범주에 속하지 않는 오류입니다.

### <a name="message"></a>메시지

"오류: 하위 보고서를 표시할 수 없습니다."

### <a name="possible-reasons"></a>가능한 이유

- 하위 보고서가 렌더링되는 동안 매개 변수가 데이터 검색과 일치하지 않는 문제 등 여러 오류가 발생했습니다.
- 예기치 못한 오류.

### <a name="troubleshooting-steps-for-report-authors"></a>문제 해결 단계(보고서 작성자용)

1. 하위 보고서를 직접 렌더링할 수 있는지 확인합니다.
2. 하위 보고서를 렌더링할 수 있는 경우 하위 보고서와 주 보고서의 매개 변수를 확인합니다.
3. 주 보고서에 고유 하위 보고서가 50개를 넘지 않아야 하며, 하위 보고서가 20개 수준보다 더 깊이 중첩되어 있지 않은지 확인합니다.
4. 문제를 해결할 수 없는 경우 Power BI 고객 지원팀에 문의하세요.

**비작성자의 경우:** 작성자에게 문의하세요.

## <a name="next-steps"></a>다음 단계

[Power BI 페이지를 매긴 보고서의 하위 보고서](subreports.md)

[Power BI 서비스에서 페이지를 매긴 보고서 보기](../consumer/paginated-reports-view-power-bi-service.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)
