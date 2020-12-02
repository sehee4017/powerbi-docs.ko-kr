---
title: Power BI Desktop에서 R 스크립트 실행
description: Power BI Desktop에서 R 스크립트 실행
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/14/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 604e90cf2f2c1010559c70df67a6cd54ac08fa36
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404551"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Power BI Desktop에서 R 스크립트 실행

Power BI Desktop에서 직접 R 스크립트를 실행하고 결과 데이터 세트를 Power BI Desktop 데이터 모델로 가져올 수 있습니다.

## <a name="install-r"></a>R 설치

Power BI Desktop에서 R 스크립트를 실행하려면 로컬 컴퓨터에 R을 설치해야 합니다. [Microsoft R 애플리케이션 네트워크 ](https://mran.revolutionanalytics.com/download/) 및 [CRAN 리포지토리](https://cran.r-project.org/bin/windows/base/)를 포함한 여러 위치에서 무료로 R을 다운로드하여 설치할 수 있습니다. 현재 릴리스는 설치 경로에서 유니코드 문자와 공백(빈 문자)을 지원합니다.

## <a name="run-r-scripts"></a>R 스크립트 실행

Power BI Desktop에서 몇 단계만 수행하면 R 스크립트를 실행하고 데이터 모델을 만들 수 있습니다. 데이터 모델을 사용하면 보고서를 만들어 Power BI 서비스에서 공유할 수 있습니다. 이제 Power BI Desktop의 R 스크립팅은 10진수(.) 및 쉼표(,)를 포함하는 숫자 형식을 지원합니다.

### <a name="prepare-an-r-script"></a>R 스크립트 준비

Power BI Desktop에서 R 스크립트를 실행하려면 로컬 R 개발 환경에서 스크립트를 만들고 성공적으로 실행되도록 합니다.

Power BI Desktop에서 스크립트를 실행하려면 새로 수정되지 않은 작업 영역에서 스크립트를 성공적으로 실행해야 합니다. 이 필수 구성 요소는 패키지 및 종속성이 명시적으로 로드되고 실행되어야 함을 뜻합니다. `source()`를 사용하여 종속 스크립트를 실행할 수 있습니다.

Power BI Desktop에서 R 스크립트를 준비하고 실행하는 경우 몇 가지 제한 사항이 있습니다.

* 데이터 프레임만 가져오기 때문에 Power BI로 가져오려는 데이터가 데이터 프레임에 표시되어야 합니다.
* 복합 및 벡터로 유형이 지정된 열은 가져오지 않으며, 만든 테이블에서 오류 값으로 대체됩니다.
* `N/A`인 값은 Power BI Desktop에서 `NULL` 값으로 변환됩니다.
* 30분 이상 실행되는 R 스크립트는 시간 초과됩니다.
* 사용자 입력 대기와 같은 R 스크립트의 대화형 호출은 스크립트의 실행을 중지합니다.
* R 스크립트 내에서 작업 디렉터리를 설정할 때 작업 디렉터리의 상대 경로가 아닌 전체 경로를 정의 *해야* 합니다.

### <a name="run-your-r-script-and-import-data"></a>R 스크립트 실행 및 데이터 가져오기

이제 R 스크립트를 실행하여 데이터를 Power BI Desktop으로 가져올 수 있습니다.

1. Power BI Desktop에서 **데이터 가져오기** 를 선택하고, **기타** > **R 스크립트** 를 선택한 다음 **연결** 을 선택합니다.

    ![R 스크립트에 연결, 기타 범주, 데이터 가져오기 대화 상자, Power BI Desktop](media/desktop-r-scripts/r-scripts-1.png)

2. 로컬 컴퓨터에 R이 설치되어 있다면 스크립트를 스크립트 창에 복사하고 **확인** 을 선택하면 됩니다. 설치된 최신 버전이 R 엔진으로 표시됩니다.

    ![R 스크립트 대화 상자, Power BI Desktop](media/desktop-r-scripts/r-scripts-2.png)

3. **확인** 을 선택하여 R 스크립트를 실행합니다. 이 스크립트를 성공적으로 실행하는 경우 결과 데이터 프레임을 선택하여 Power BI 모델에 추가할 수 있습니다.

스크립트를 실행하는 데 사용할 R 설치를 제어할 수 있습니다. R 설치 설정을 지정하려면 **파일** > **옵션 및 설정** > **옵션** 을 선택한 다음 **R 스크립팅** 을 선택합니다. **R 스크립트 옵션** 에서 **검색된 R 홈 디렉터리** 드롭다운 목록은 현재 R 설치 옵션을 보여 줍니다. 원하는 R 설치가 없으면 **기타** 를 선택한 다음 원하는 R 설치 폴더로 이동하거나 **R 홈 디렉터리 설정** 에 원하는 R 설치 폴더를 입력합니다.

![R 스크립트 옵션, 옵션 대화 상자, Power BI Desktop](media/desktop-r-scripts/r-scripts-4.png)

### <a name="refresh"></a>새로 고침

Power BI Desktop에서 R 스크립트를 새로 고칠 수 있습니다. R 스크립트를 새로 고칠 때 Power BI Desktop은 Power BI Desktop 환경에서 R 스크립트를 다시 실행합니다.

## <a name="next-steps"></a>다음 단계

Power BI의 R에 대한 자세한 내용은 다음을 참조하세요.

* [R을 사용하여 Power BI 시각적 개체 만들기](../create-reports/desktop-r-visuals.md)
* [Power BI로 외부 R IDE 사용](desktop-r-ide.md)
