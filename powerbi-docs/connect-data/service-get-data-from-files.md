---
title: Power BI 파일에서 데이터 가져오기
description: Excel, Power BI Desktop 및 CSV 파일에서 Power BI로 데이터를 가져오는 방법 알아보기
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: b7b886b5e0c21c77e0a5a6aca83fa0ae0751f435
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2020
ms.locfileid: "86264121"
---
# <a name="get-data-from-files-for-power-bi"></a>Power BI 파일에서 데이터 가져오기
![Excel, Power BI Desktop 및 CSV 아이콘](media/service-get-data-from-files/file_icons.png)

Power BI에서는 세 가지 형식의 파일에서 데이터 및 보고서를 연결하거나 가져올 수 있습니다.

* Microsoft Excel(.xlsx 또는 .xlsm)
* Power BI Desktop(.pbix)
* 쉼표로 구분된 값(.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>파일에서 데이터를 가져온다는 것은 정확히 무슨 의미일까요?
Power BI에서 사용자가 탐색하는 데이터는 데이터 세트의 것입니다. 하지만 데이터 세트를 가지려면 먼저 일부 데이터를 가져와야 합니다. 이 문서의 경우 파일에서 데이터를 가져오는 것에 초점을 맞추려고 합니다.

데이터 세트의 중요성과 이 데이터 세트에 대한 데이터를 가져오는 방법에 대해 더 잘 이해하기 위해 자동차를 생각해 보겠습니다. 자동차에 앉아 대시보드를 보세요. 이것은 마치 컴퓨터 앞에서 Power BI에서 대시보드를 바라보고 있는 것과 같습니다. 대시보드는 엔진 회전 속도, 온도, 변속 기어, 속도 등 자동차가 어떻게 작동하고 있는지 모든 것을 보여줍니다.

Power BI에서 데이터 세트는 자동차의 엔진과 비슷합니다. 데이터 세트는 Power BI 대시보드에 표시되는 데이터, 메트릭 및 정보를 제공합니다. 물론 엔진, 또는 데이터 세트는 연료가 필요하며 Power BI에서는 이 연료가 데이터입니다. 자동차에는 엔진에 휘발유를 제공하는 연료 탱크가 있습니다. Power BI도 상당히 유사하게 데이터 세트에 공급할 수 있는 데이터가 있는 연료 탱크가 필요합니다. 이 경우에서 연료 탱크는 Power BI Desktop 파일, Excel 통합 문서 파일 또는 .CSV 파일입니다.

한 단계 더 나아가 살펴볼 수 있습니다. 자동차의 연료 탱크는 휘발유로 채워야 합니다. Power BI, Excel 또는 .CSV 파일의 휘발유는 다른 데이터 원본의 데이터입니다. 우리는 다른 데이터 원본에서 데이터를 가져온 후 Excel, Power BI Desktop 또는 .CSV 파일에 넣습니다. Excel 통합 문서 또는 .CSV 파일인 경우 직접 데이터 행을 입력할 수 있습니다. 또는 외부 데이터 원본에 연결하여 데이터를 쿼리하여 파일에 로드할 수 있습니다. 일부 데이터가 포함된 파일이 있다면 Power BI에 데이터 세트로 가져올 수 있습니다.

> [!NOTE]
> Excel 통합 문서의 데이터는 Power BI에서 가져올 테이블 또는 데이터 모델에 있어야 합니다.
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>파일 저장 위치는 중요합니다.
**로컬** - 파일을 사용자 컴퓨터의 로컬 드라이브 또는 조직의 다른 위치에 저장하는 경우 Power BI에서 파일을 Power BI로 *가져올* 수 있습니다. 파일은 사실 로컬 드라이브에 그대로 남아 있으므로, 전체 파일을 실제로 Power BI로 가져온 것은 아닙니다. 실제로는, 새 데이터 세트가 Power BI에서 만들어지고 데이터, 그리고 일부 경우에는 데이터 모델이 데이터 세트로 로드됩니다. 파일에 보고서가 있을 경우 Power BI의 보고서에 나타납니다.

**OneDrive - 비즈니스** – 비즈니스용 OneDrive가 있고 Power BI에 로그인하는 같은 계정으로 로그인할 경우 Excel Power BI Desktop의 작업, 또는 Power BI에서 .CSV 파일 및 데이터 세트, 보고서 그리고 대시보드의 동기화를 유지하는 가장 효과적인 방법입니다. Power BI와 OneDrive가 모두 클라우드에 있으므로 Power BI는 매시간 OneDrive의 파일에 연결합니다. 변경 내용이 발견되면 데이터 세트, 보고서 및 대시보드가 Power BI에서 자동으로 업데이트됩니다.

**OneDrive - 개인** – 본인의 OneDrive 계정으로 파일을 저장할 경우 비즈니스용 OneDrive에 제공하는 것과 동일한 많은 혜택을 누릴 수 있습니다. 가장 큰 차이점은 파일에 처음 연결할 때(‘데이터 가져오기’ > ‘파일’ > ‘OneDrive - 개인’ 사용) Microsoft 계정으로 OneDrive에 로그인해야 한다는 점이 가장 큰 차이점이며, 일반적으로 Power BI에 로그인하기 위해 사용하는 것과는 다릅니다. Microsoft 계정으로 OneDrive에 로그인할 경우 로그인 유지 옵션을 선택해야 합니다. 이러한 방식으로 Power BI는 매시간 파일에 연결할 수 있으며 Power BI의 데이터 세트는 동기화를 유지하게 됩니다.

**SharePoint 팀 사이트** – Power BI Desktop 파일을 SharePoint 팀 사이트에 저장하는 것은 비즈니스용 OneDrive에 저장하는 것과 상당히 같습니다. 가장 큰 차이점은 Power BI에서 파일에 연결하는 방법입니다. URL을 지정하거나 루트 폴더에 연결할 수 있습니다.

## <a name="ready-to-get-started"></a>시작할 준비가 되셨나요?
Power BI로 파일을 가져오는 방법에 대해 자세히 알아보려면 다음 문서를 참조하세요.

* [Excel 통합 문서 파일에서 데이터 가져오기](service-excel-workbook-files.md)
* [Power BI Desktop 파일에서 데이터 가져오기](service-desktop-files.md)
* [쉼표로 구분된 값 파일에서 데이터 가져오기](service-comma-separated-value-files.md)

