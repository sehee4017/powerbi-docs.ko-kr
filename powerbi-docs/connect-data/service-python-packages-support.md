---
title: 지원되는 Python 패키지에 대해 알아보기
description: Power BI에서 지원되는 Python 패키지와 지원되지 않는 Python 패키지
author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/26/2020
ms.author: otarb
LocalizationGroup: Connect to data
ms.openlocfilehash: b1dc77d2ebf0803430ceeace7e14bfa62a6d2a60
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785236"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>Power BI 서비스에서 Python 패키지를 사용하여 시각적 개체 만들기
강력한 [Python 프로그래밍 언어](https://www.python.org/)를 사용하여 Power BI 서비스에서 시각적 개체를 만들 수 있습니다. 많은 Python 패키지가 Power BI 서비스에서 지원되며 항상 지원되는 패키지는 더 많습니다.

다음 섹션에서는 Power BI에서 지원되는 Python 패키지의 사전순 테이블을 제공합니다. 

## <a name="request-support-for-a-new-python-package"></a>새 Python 패키지에 대한 지원 요청
**Power BI 서비스**에서 지원되는 Python 패키지는 **지원 패키지**라는 제목의 다음 섹션에서 찾을 수 있습니다. 이 목록에 없는 Python 패키지에 대한 지원을 요청하려면 [Power BI Ideas](https://ideas.powerbi.com)에 요청을 제출하세요.

## <a name="requirements-and-limitations-of-python-packages"></a>Python 패키지의 요구 사항 및 제한 사항
Python 패키지에는 몇 가지 요구 사항과 제한 사항이 있습니다.

* 현재 Python 런타임: Python 3.7.7.
* 대부분의 경우 Power BI 서비스는 GPL-2, GPL-3, MIT+ 등과 같은 무료 오픈 소스 소프트웨어 라이선스를 포함한 Python 패키지를 지원합니다.
* Power BI 서비스는 PyPI에 게시된 패키지를 지원합니다. Power BI 서비스는 프라이빗 또는 사용자 지정 Python 패키지를 지원하지 않습니다. 사용자는 Power BI 서비스에서 패키지 제공을 요청하기 전에 PyPI에서 자신의 프라이빗 패키지를 제공하는 것이 좋습니다.
* **Power BI Desktop**의 Python 시각적 개체의 경우 사용자 지정 Python 패키지를 비롯한 모든 패키지를 설치할 수 있습니다.
* 보안 및 개인 정보 보호를 위해 현재 서비스에서는 World-Wide Web을 통해 클라이언트 서버 쿼리를 제공하는 Python 패키지는 지원되지 않습니다. 이러한 시도에 대한 네트워킹이 차단됩니다.
* 새 Python 패키지를 포함하는 승인 프로세스에는 종속성 트리가 있습니다. 따라서 서비스에 설치되어야 하는 일부 종속성을 지원할 수 없습니다.

## <a name="python-packages-that-are-supported-in-power-bi"></a>Power BI에서 지원되는 Python 패키지
다음 테이블은 Power BI 서비스에서 **지원되는** 패키지를 보여 줍니다.


|        패키지        |   버전   |                                   링크                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|s  eaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>다음 단계
Power BI의 Python에 대한 자세한 내용은 다음 문서를 참조하세요.

* [Python을 사용하여 Power BI 시각적 개체 만들기](desktop-python-visuals.md)
* [Power BI Desktop에서 Python 스크립트 실행](desktop-python-scripts.md)
* [쿼리 편집기에서 Python 사용](desktop-python-in-query-editor.md)
