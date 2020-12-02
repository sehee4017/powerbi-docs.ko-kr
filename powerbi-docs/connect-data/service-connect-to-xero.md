---
title: Power BI로 Xero에 연결
description: Power BI용 Xero
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 03/06/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: c942e399eb32fd7118d515f0d072972e3a820578
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410485"
---
# <a name="connect-to-xero-with-power-bi"></a>Power BI로 Xero에 연결
Xero는 중소기업을 위해 특별히 설계된 사용이 용이한 온라인 계정 소프트웨어입니다. 이 Power BI 템플릿 앱으로 Xero financials를 기반으로 한 매력적인 시각화를 만들어 보세요. 기본 대시보드에는 현금 보유 현황, 수익과 지출 비교, 손익 추세, 대금 결제 기간, 투자 수익률 등 다양한 중소기업 메트릭이 포함됩니다.

Power BI용 [Xero 템플릿 앱](https://app.powerbi.com/getdata/services/xero)에 연결하거나 [Xero 및 Power BI](https://help.xero.com/Power-BI) 통합에 대해 자세히 알아보세요.

## <a name="how-to-connect"></a>연결 방법

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. **Xero** \> **지금 받기** 를 선택합니다.
4. **이 Power BI 앱을 설치하겠습니까?** 에서 **설치** 를 선택합니다.

    ![Xero 설치](media/service-connect-to-xero/power-bi-install-xero.png)

4. **앱** 창에서 **Xero** 타일을 선택합니다.

   ![Xero 타일을 선택](media/service-connect-to-xero/power-bi-start-xero.png)

6. **새 앱 시작** 에서 **데이터** 를 선택합니다.

    ![새 앱 시작](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Xero 계정과 연결된 조직에 대한 별명을 입력합니다. 어떤 것이라도 좋으며 이렇게 하면 대부분 여러 Xero 조직의 사용자가 단순함을 유지하는 데 도움이 됩니다. 이 문서의 뒷부분에 나오는 [매개 변수 찾기](#FindingParams)에 대한 자세한 내용을 참조하세요.

    ![조직 별명](media/service-connect-to-xero/params.png)

5. **인증 방법** 에 대해 **OAuth** 를 선택합니다. Xero 계정에 로그인하라는 메시지가 표시되면 연결할 조직을 선택합니다. 로그인이 완료되면 **로그인** 을 선택하여 로딩 프로세스를 시작합니다.
   
    ![인증 방법](media/service-connect-to-xero/creds.png)
   
    ![Xero를 시작합니다.](media/service-connect-to-xero/creds2.png)
6. 승인되면 가져오기 프로세스가 자동으로 시작됩니다. 완료되면 새 대시보드, 보고서 및 모델이 탐색 창에 나타납니다. 대시보드를 선택하여 가져온 데이터를 표시합니다.
   
     ![Xero 대시보드](media/service-connect-to-xero/power-bi-xero-dashboard.png)

**다음 단계**

* 대시보드 맨 위에 있는 [질문 및 답변 상자에 질문](../consumer/end-user-q-and-a.md)합니다.
* 대시보드에서 [타일을 변경](../create-reports/service-dashboard-edit-tile.md)합니다.
* [타일을 선택](../consumer/end-user-tiles.md)하여 원본 보고서를 엽니다.
* 데이터 세트을 매일 새로 고치도록 예약하는 경우 새로 고침 일정을 변경하거나 **지금 새로 고침** 을 사용하여 필요할 때 새로 고칠 수 있습니다.

## <a name="whats-included"></a>포함된 내용
템플릿 앱 대시보드에는 다양한 영역을, 이에 대한 자세한 내용이 있는 해당 보고서와 함께 포괄하는 타일 및 메트릭이 포함됩니다.  

| 영역 | 대시보드 타일 | 보고서 |
| --- | --- | --- |
| 현금 |일일 현금 흐름 <br>들어온 현금 <br>나간 현금 <br>계정별 결산 잔액 <br>오늘 결산 잔액 |은행 계좌 |
| 고객 |송장 발부된 판매 <br>고객별 송장 발부된 판매 <br>송장 발부된 판매 급수 추세 <br>송장 기한 <br>미결 미수금 <br>기한이 지난 미수금 |고객 <br>재고 |
| 공급업체 |청구된 구매 <br>공급업체별 청구된 구매 <br>청구된 구매 급수 추세 <br> 만기 어음 <br>미결 매입금 <br>만기 매입금 |공급업체 <br>재고 |
| 재고 |제품별 월간 판매량 |재고 |
| 손익 |월간 손익 <br>순이익 당 회계 년도 <br>순이익 당월 <br>상위 비용 계정 |손익 |
| 대차대조표 |총 자산 <br>총 부채 <br>지분 |대차대조표 |
| 상태 |현재 비율 <br>매출 총이익 백분율 <br> 총 자산 이익률 <br>총 부채 대 자산 비율 |건강 <br>용어 및 기술 참고 사항 |

데이터 세트는 보고서 및 대시보드를 사용자 지정하는 다음 테이블을 포함합니다.  

* 주소  
* 경고  
* 은행 거래 내역서 일일 잔고  
* 은행 거래 내역서  
* 연락처  
* 비용 청구서  
* 송장 품목  
* 송장  
* 항목  
* 월말  
* 조직  
* 시산표  
* Xero 계정

## <a name="system-requirements"></a>시스템 요구 사항
Xero 템플릿 앱에 액세스하려면 다음 역할이 필요합니다. "Standard + Reports" 또는 "Advisor".

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>매개 변수 찾기
Power BI에서 추적할 조직 이름을 제공합니다. 특정 이름을 사용하여 여러 조직에 연결할 수 있습니다. 예약된 새로 고침에 영향을 주므로 동일한 조직에 여러 번 연결할 수 없습니다.   

## <a name="troubleshooting"></a>문제 해결
* Xero 사용자는 Power BI용 Xero 템플릿 앱에 액세스하려면 다음 역할을 보유해야 합니다. "Standard + Reports" 또는 "Advisor". 템플릿 앱은 Power BI를 통해 보고 데이터에 액세스하는 데 사용자 기반 권한을 사용합니다.
* 로드하는 동안 대시보드의 타일은 일반 로딩 상태입니다. 전체 로드가 완료될 때까지 이 상태를 유지합니다. 로드가 완료되었다는 알림을 받았는데 타일이 아직 로드 중이면, 대시보드 오른쪽 위에 있는 ...를 사용하여 대시보드 타일을 새로 고쳐 보세요.
* 템플릿 앱을 새로 고칠 수 없는 경우 Power BI에서 동일한 조직에 두 번 이상 연결했는지 확인하세요. Xero에서는 조직에 대한 단일 활성 연결만 허용하며 동일한 조직에 두 번 이상 연결하는 경우 자격 증명이 유효하지 않음을 나타내는 오류가 표시될 수 있습니다.  
* Power BI용 Xero 템플릿 앱을 연결하는 데 오류 메시지 또는 느린 로드 시간과 같은 문제가 있는 경우 먼저 캐시/쿠키를 지우고 브라우저를 다시 시작한 후 Power BI에 다시 연결합니다.  

다른 문제의 경우, 문제가 지속되면 https://support.powerbi.com 에 티켓을 제출하세요.

## <a name="next-steps"></a>다음 단계
[Power BI에서 시작](../fundamentals/service-get-started.md)

[Power BI에서 데이터 가져오기](service-get-data.md)
