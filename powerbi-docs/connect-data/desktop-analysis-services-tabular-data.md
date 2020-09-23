---
title: Power BI Desktop의 Analysis Services 표 형식 데이터에 연결
description: Power BI Desktop에서는 라이브 연결을 사용하거나, 항목을 선택하여 Power BI Desktop으로 가져오는 방식으로 SQL Server Analysis Services 테이블 형식 모델에 연결하고 데이터를 가져올 수 있습니다.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/28/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: bb55342974bcd64e7d5871b7b84977105b7467fa
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90858695"
---
# <a name="connect-to-analysis-services-tabular-data-in-power-bi-desktop"></a>Power BI Desktop의 Analysis Services 표 형식 데이터에 연결
Power BI Desktop에서 SQL Server Analysis Services 테이블 형식 모델의 데이터에 연결하여 데이터를 가져올 수 있는 방법은 다음 두 가지입니다. 라이브 연결을 사용하여 탐색하거나, 항목을 선택하고 Power BI Desktop으로 가져옵니다.

측정값에 대해 좀 더 자세히 살펴보겠습니다.

**라이브 연결을 사용하여 탐색**: 라이브 연결을 사용하면 테이블 형식 모델이나 큐브 뷰의 테이블, 열 및 측정값 같은 항목이 Power BI Desktop **필드** 창 목록에 표시됩니다. Power BI Desktop의 고급 시각화 및 보고 도구를 사용하여 새롭고 매우 뛰어난 대화형 방식으로 테이블 형식 모델을 탐색할 수 있습니다.

라이브 연결에서는 테이블 형식 모델의 데이터를 Power BI Desktop으로 가져오지 않습니다. 시각화 도구를 조작할 때마다 Power BI Desktop이 테이블 형식 모델을 쿼리하여 사용자에게 표시되는 결과를 계산합니다. 항상 테이블 형식 모델에서 사용할 수 있는 DirectQuery 테이블이나 마지막 처리 시간의 최신 데이터가 표시됩니다. 

테이블 형식 모델은 매우 안전합니다. Power BI Desktop에 표시되는 항목은 연결한 테이블 형식 모델에 대한 사용자의 권한에 따라 달라집니다.

Power BI Desktop에 동적 보고서를 만들 경우 Power BI 사이트에 게시하여 공유할 수 있습니다. 테이블 형식 모델에 대한 라이브 연결을 사용하는 Power BI Desktop 파일을 Power BI 사이트에 게시하는 경우 관리자가 온-프레미스 데이터 게이트웨이를 설치하여 구성해야 합니다. 자세한 내용은 [온-프레미스 데이터 게이트웨이](service-gateway-onprem.md)를 참조하세요.

**항목을 선택하고 Power BI Desktop으로 가져오기**: 이 옵션을 사용하여 연결하면 테이블 형식 모델이나 큐브 뷰의 테이블, 열 및 측정값 같은 항목을 선택하여 Power BI Desktop 모델에 로드할 수 있습니다. Power BI Desktop의 Power Query 편집기를 통해 원하는 항목 및 관련 모델링 기능을 추가로 셰이핑하여 데이터를 추가로 모델링합니다. Power BI Desktop과 테이블 형식 모델 간 라이브 연결은 유지되지 않기 때문에 Power BI Desktop 모델을 오프라인으로 탐색하거나 Power BI 사이트에 게시할 수 있습니다.

## <a name="to-connect-to-a-tabular-model"></a>테이블 형식 모델에 연결하려면
1. Power BI Desktop의 **홈** 탭에서 **데이터 가져오기** > **자세히** > **데이터베이스**를 선택합니다.
   
1. **SQL Server Analysis Services 데이터베이스**를 선택한 다음, **연결**을 선택합니다.
   
   ![SQL Server Analysis Services 데이터베이스 선택](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. **SQL Server Analysis Services 데이터베이스** 창에서 **서버** 이름을 입력하고, 연결 모드를 선택한 다음, **확인**을 선택합니다.
   
   ![SQL Server Analysis Services 데이터베이스 창](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. **탐색기** 창의 이 단계는 선택한 연결 모드에 따라 달라집니다.

   - 라이브로 연결하는 경우 테이블 형식 모델 또는 큐브 뷰를 선택합니다.
  
      ![탐색기 테이블 형식 모델 또는 큐브 뷰 선택](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
   - 항목을 선택하고 데이터를 가져오도록 선택한 경우 테이블 형식 모델 또는 큐브 뷰를 선택한 다음, 로드할 특정 테이블 또는 열을 선택합니다. 로드하기 전에 데이터를 셰이핑하려면 **쿼리 편집**을 선택하여 Power Query 편집기를 엽니다. 준비가 되면 **로드**를 선택하여 Power BI Desktop에 데이터를 가져옵니다.

      ![로드할 탐색기 테이블 또는 열 선택](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>질문과 대답
**질문:** 온-프레미스 데이터 게이트웨이가 필요한가요?

**답변:** 경우에 따라 다릅니다. Power BI Desktop을 사용하여 테이블 형식 모델에 라이브로 연결하되 Power BI 사이트에 게시하지 않으려는 경우 게이트웨이가 필요하지 않습니다. 반면에 Power BI 사이트에 게시하려는 경우, Power BI 서비스와 온-프레미스 Analysis Services 서버 간의 안전한 통신을 위해 데이터 게이트웨이가 필요합니다. 데이터 게이트웨이를 설치하기 전에 Analysis Services 서버 관리자에게 문의해야 합니다.

항목을 선택하고 데이터를 가져오도록 선택하는 경우 테이블 형식 모델 데이터를 Power BI Desktop 파일에 직접 가져오므로 게이트웨이가 필요하지 않습니다.

**질문:** Power BI 서비스에서 테이블 형식 모델에 라이브로 연결하는 것과 Power BI Desktop에서 테이블 형식 모델에 라이브로 연결하는 것에는 어떤 차이가 있나요?

**답변:** 조직의 온-프레미스에서 실행되는 Analysis Services 데이터베이스의 Power BI 서비스 사이트에서 테이블 형식 모델에 라이브로 연결하는 경우 둘 사이의 안전한 통신을 위해 온-프레미스 데이터 게이트웨이가 필요합니다. Power BI Desktop에서 테이블 형식 모델에 라이브로 연결하는 경우 연결하는 Power BI Desktop 및 Analysis Services 서버는 둘 다 조직의 온-프레미스에서 실행되고 있으므로 게이트웨이가 필요하지 않습니다. 그러나 Power BI Desktop 파일을 Power BI 사이트에 게시할 경우 게이트웨이가 필요합니다.

**질문:** 라이브 연결을 만든 경우 동일한 Power BI Desktop 파일에서 다른 데이터 원본에 연결할 수 있나요?

**답변:** 아니요. 같은 파일에서 라이브 데이터를 탐색하고 다른 형식의 데이터 원본에 연결할 수 없습니다. 이미 데이터를 가져왔거나 Power BI Desktop 파일의 다른 데이터 원본에 연결한 경우 라이브 탐색을 위해 새 파일을 만들어야 합니다.

**질문:** 라이브 연결을 만든 경우 Power BI Desktop에서 모델 또는 쿼리를 편집할 수 있나요?

**답변:** Power BI Desktop에서 보고서 수준 측정값을 만들 수 있지만, 다른 모든 쿼리 및 모델링 기능은 라이브 데이터를 탐색할 때 사용할 수 없습니다.

**질문:** 만든 라이브 연결은 안전한가요?

**답변:** 예. 현재 Windows 자격 증명을 사용하여 Analysis Services 서버에 연결합니다. 라이브 탐색 중에는 Power BI 서비스 또는 Power BI Desktop에서 기본 또는 저장된 자격 증명을 사용할 수 없습니다.

**질문:** 탐색기에서 모델 및 큐브 뷰가 보입니다. 차이점은 무엇인가요?

**답변:** 큐브 뷰는 테이블 형식 모델의 특정 뷰입니다. 여기에는 고유의 데이터 분석 필요에 따라 특정 테이블, 열 또는 측정치만 포함될 수 있습니다. 테이블 형식 모델에는 항상 하나 이상의 큐브 뷰가 포함되어 있어 모델의 모든 항목을 포함할 수 있습니다. 어떤 큐브 뷰를 선택할지 확실하지 않은 경우에는 관리자에게 문의하세요.

**질문:** Power BI 작동 방식을 변경하는 Analysis Services 기능이 있나요?

**답변:** 예. 테이블 형식 모델에서 사용하는 기능에 따라 Power BI Desktop의 환경이 변경될 수 있습니다. 일부 사례:
* 모델의 측정값이 열과 함께 테이블이 아니라 **필드** 창 목록 맨 위에 그룹화될 수도 있습니다. 걱정하지 마세요. 정상적으로 계속 사용할 수 있으며, 이 방식으로 측정값을 찾는 것이 더 간편합니다.

* 테이블 형식 모델에 계산 그룹이 정의되어 있을 경우 모델 측정값과 함께 사용해야 하며 시각적 개체에 숫자 필드를 추가하여 만든 암시적 측정값과 함께 사용할 수 없습니다. 모델에 동일한 효과를 가진 **DiscourageImplicitMeasures** 플래그가 수동으로 설정되어 있을 수도 있습니다. 자세한 내용은 [Analysis Services의 계산 그룹](/analysis-services/tabular-models/calculation-groups#benefits)을 참조하세요.

## <a name="to-change-the-server-name-after-initial-connection"></a>최초 연결 후 서버 이름을 변경하려면
탐색 라이브 연결이 있는 Power BI Desktop 파일을 만든 후 다른 서버로 연결 전환이 필요한 상황이 발생할 수 있습니다. 예를 들어, 개발 서버에 연결할 때 Power BI Desktop 파일을 만들었으며 Power BI 서비스에 게시하기 전에 프러덕션 서버로 연결을 전환하려는 경우가 있습니다.

서버 이름을 변경하려면 다음을 수행합니다.

1. **홈** 탭에서 **쿼리 편집**을 선택합니다.

2. **SQL Server Analysis Services 데이터베이스** 창에서 **서버** 이름을 입력한 다음, **확인**을 선택합니다.

   
## <a name="troubleshooting"></a>문제 해결 
다음 목록에서는 SSAS(SQL Server Analysis Services) 또는 Azure Analysis Services에 연결하는 경우에 발생하는 알려진 모든 문제를 설명합니다. 

* **오류: 모델 스키마를 로드할 수 없습니다.** Analysis Services에 연결 중인 사용자가 데이터베이스/모델에 액세스할 수 없는 경우에 일반적으로 이 오류가 발생합니다.