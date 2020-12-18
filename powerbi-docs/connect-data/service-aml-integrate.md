---
title: '자습서:  Power BI에서 Azure Machine Learning 모델 사용'
titleSuffix: Azure Machine Learning
description: Power BI에서 Azure Machine Learning 모델을 사용하는 방법을 알아봅니다.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: tutorial
ms.author: samkemp
author: samuel100
ms.reviewer: sdgilley, maggies
ms.date: 12/10/2020
ms.openlocfilehash: 6c68fff575e4da0c9126904df2de5292747c209c
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491785"
---
# <a name="tutorial-consume-azure-machine-learning-models-in-power-bi"></a>자습서:  Power BI에서 Azure Machine Learning 모델 사용

이 자습서에서는 기계 학습 모델을 기반으로 Power BI 보고서를 만드는 과정을 안내합니다. 이 자습서를 마치면 다음을 수행할 수 있습니다.

> [!div class="checklist"]
> * Power BI의 기계 학습 모델(Azure Machine Learning을 사용하여 배포됨)의 점수를 매깁니다.
> * Power Query 편집기에서 Azure Machine Learning 모델에 연결합니다.
> * 해당 모델을 기반으로 시각화를 사용하여 보고서를 만듭니다.
> * Power BI 서비스에 해당 보고서를 게시합니다.
> * 보고서에 예약된 새로 고침을 설정합니다.

## <a name="prerequisites"></a>필수 구성 요소

이 자습서를 시작하기 전에 다음을 수행해야 합니다.

- Azure Machine Learning에서 기계 학습 모델을 학습하고 배포합니다. 다음 세 가지 Azure Machine Learning 자습서 중 하나를 사용합니다. 

    - [옵션 A: 코드](/azure/machine-learning/tutorial-power-bi-custom-model)
    - [옵션 B: 디자이너](/azure/machine-learning/tutorial-power-bi-designer-model)
    - [옵션 C: 자동화된 ML](/azure/machine-learning/tutorial-power-bi-automated-model)

- [무료 Power BI 평가판](https://app.powerbi.com/signupredirect?pbi_source=web)에 등록합니다.
- 로컬 컴퓨터에 [Power BI Desktop을 설치](https://powerbi.microsoft.com/desktop/)합니다.

## <a name="create-the-data-model"></a>데이터 모델 만들기

Power BI Desktop을 열고 **Get Data** 를 선택합니다. **데이터 가져오기** 대화 상자에서 **웹** 을 검색합니다. **웹** 원본 >**연결** 을 선택합니다.

:::image type="content" source="media/service-aml-integrate/pbi-get-data.png" alt-text="웹 데이터를 보여주는 스크린샷.":::

**웹에서** 대화 상자에서 상자에 다음 URL을 복사한 후 붙여넣습니다.

```txt 
https://www4.stat.ncsu.edu/~boos/var.select/diabetes.tab.txt
```

:::image type="content" source="media/service-aml-integrate/pbi-data.png" alt-text="웹 url을 보여주는 스크린샷.":::

**확인** 을 선택합니다.

**데이터 변환** 을 선택하여 **Power Query 편집기** 창을 엽니다.

Power Query 편집기의 홈 리본에서 **Azure Machine Learning** 버튼을 선택합니다.

:::image type="content" source="media/service-aml-integrate/aml-button.png" alt-text="Power Query 편집기를 보여주는 스크린샷.":::

Single Sign-On을 사용하여 Azure 계정에 로그인하면 사용 가능한 서비스 목록이 표시됩니다. 기계 학습 모델 학습 및 배포 자습서에서 만든 **my-sklearn-service** 를 선택합니다. 

Power Query에서 열이 자동으로 채워집니다. 서비스에 대한 스키마에 입력을 지정한 Python 데코레이터가 있었습니다. **확인** 을 선택합니다.

:::image type="content" source="media/service-aml-integrate/aml-pbi-run.png" alt-text="Azure Machine Learning 모델을 보여주는 스크린샷.":::

**확인** 을 선택하면 Azure Machine Learning 서비스가 호출됩니다. 데이터와 엔드포인트 모두의 데이터 개인 정보에 대한 경고를 트리거합니다.

:::image type="content" source="media/service-aml-integrate/data_privacy_warning.png" alt-text="개인 정보 경고를 보여주는 스크린샷.":::

**계속** 을 선택합니다. 다음 화면에서 **이 파일에 대한 개인 정보 수준 검사 무시** > **저장** 을 선택합니다.

데이터에 점수가 매겨지면 Power Query에서 **AzureML.my-diabetes-model** 이라는 추가 열을 만듭니다.

:::image type="content" source="media/service-aml-integrate/scored-data.png" alt-text="점수가 매겨진 추가된 열을 보여주는 스크린샷.":::

서비스에서 반환하는 데이터는 **목록** 입니다. 

> [!NOTE]
> 디자이너 모델을 배포한 경우 **레코드** 가 표시됩니다.

예측을 가져오려면 **변환** 리본에서 **열 확장** 버튼 > **새 행으로 확장** 을 선택합니다.

확장 후에는 AzureML.my-diabetes-model 열에 예측이 표시됩니다.

:::image type="content" source="media/service-aml-integrate/after-expand.png" alt-text="확장을 보여주는 스크린샷.":::

데이터 모델 정리를 완료하려면 다음 단계를 수행합니다.

1. **AzureML.my-diabetes-model** 열의 이름을 **예측** 으로 바꿉니다.
1. **Y** 열의 이름을 **실제** 로 바꿉니다.
1. 다음과 같이 **실제** 열의 유형을 변경합니다. 열을 선택한 다음 **변환** 리본에서 **데이터 형식** > **10진수** 를 선택합니다.
1. 다음과 같이 **예측** 열의 유형을 변경합니다. 해당 열을 선택한 다음 **변환** 리본에서 **데이터 형식** > **10진수** 를 선택합니다.
1. **홈** 리본에서 **닫기 및 적용** 을 선택합니다.

## <a name="create-a-report-with-visualizations"></a>시각화를 사용하여 보고서 만들기

이제 데이터를 표시하는 몇 가지 시각화를 만들 수 있습니다.

1. **시각화** 창에서 **꺾은선형 차트** 를 선택합니다. 
1. 꺾은선형 차트 시각적 개체를 선택한 상태에서 다음을 수행합니다.
1. **보존 기간** 필드를 **축** 으로 끌어 옵니다.
1. **실제** 필드를 **값** 으로 끌어옵니다.
1. **예측** 필드를 **값** 으로 끌어옵니다.

페이지가 채워지도록 꺾은선형 차트의 크기를 조정합니다. 이제 보고서에 두 줄이 있는 단일 꺾은선형 차트가 있습니다. 하나는 예측에 대한 줄이고 하나는 실제 값에 대한 줄로 보존 기간별로 분포되어 있습니다.

:::image type="content" source="media/service-aml-integrate/report-viz.png" alt-text="보고서 시각화를 보여주는 스크린샷.":::

## <a name="publish-the-report"></a>보고서 게시

원하는 경우 시각화를 더 추가할 수 있습니다. 간결성을 위해 이 자습서에 보고서를 게시하겠습니다.

1. 보고서를 저장합니다.
1. **파일** > **게시** > **Power BI에 게시** 를 선택합니다.
1. Power BI 서비스에 로그인합니다.
1. **내 작업 영역** 을 선택합니다.
1. 보고서가 성공적으로 게시되면 **Power BI에서 <MY_PBIX_FILE.pbix> 열기** 링크를 선택합니다. 보고서가 브라우저에서 Power BI에 보고서를 엽니다.

     :::image type="content" source="media/service-aml-integrate/publish-success.png" alt-text="성공적인 게시를 보여주는 스크린샷.":::

## <a name="enable-datasets-to-refresh"></a>데이터 세트가 새로 고쳐지도록 설정

점수를 매길 새 데이터로 데이터 원본이 새로 고쳐지는 시나리오에서는 데이터 점수를 매길 수 있도록 자격 증명을 업데이트해야 합니다. 

Power BI 서비스의 내 작업 영역에 있는 검은색 머리글 표시줄에서 **추가 옵션(...)**  > **설정** > **설정** 을 선택합니다.

:::image type="content" source="media/service-aml-integrate/settings-pbi.png" alt-text="설정을 보여주는 스크린샷.":::

**데이터 세트** 를 선택하고 **데이터 원본 자격 증명** 을 확장한 다음 **자격 증명 편집** 을 선택합니다.

:::image type="content" source="media/service-aml-integrate/data-refresh.png" alt-text="자격 증명 새로 고침을 보여주는 스크린샷.":::

**azureMLFunctions** 및 **웹** 모두에 대한 지침을 따르세요. 개인 정보 수준을 선택했는지 확인합니다. 이제 데이터의 **예약된 새로 고침** 을 설정할 수 있습니다. **새로 고침 빈도** 및 **표준 시간대** 를 선택합니다. Power BI에서 새로 고침 실패 알림을 보낼 수 있는 이메일 주소를 선택할 수도 있습니다.

:::image type="content" source="media/service-aml-integrate/schedule-refresh.png" alt-text="데이터 세트 및 점수 매기기 새로 고침을 보여주는 스크린샷.":::

**적용** 을 선택합니다.

>[!NOTE]
> 데이터를 새로 고치면 점수 매기기를 위해 Azure Machine Learning 엔드포인트에도 데이터가 전송됩니다.

## <a name="clean-up-resources"></a>리소스 정리

>[!IMPORTANT]
>직접 만든 리소스는 다른 Azure Machine Learning 자습서 및 방법 문서에 대한 필수 조건으로 사용할 수 있습니다.

만든 리소스를 사용하지 않으려는 경우에는 요금이 부과되지 않도록 해당 리소스를 삭제합니다.

1. Azure Portal의 맨 왼쪽에서 **리소스 그룹** 을 선택합니다.
 
1. 목록에서 만든 리소스 그룹을 선택합니다.

1. **리소스 그룹 삭제** 를 선택합니다.

   ![Azure Portal에서 리소스 그룹을 삭제하기 위해 선택한 항목의 스크린샷](./media/service-aml-integrate/delete-resources.png)

1. 리소스 그룹 이름을 입력합니다. 그런 다음, **삭제** 를 선택합니다.
1. Power BI 서비스의 내 작업 영역에서 보고서 및 관련 데이터 세트를 삭제합니다. 컴퓨터에서 Power BI Desktop 또는 보고서를 삭제할 필요가 없습니다. Power BI Desktop은 무료입니다.

## <a name="next-steps"></a>다음 단계

이 자습서 시리즈에서는 Azure Machine Learning의 점수 매기기 엔드포인트로 새 데이터의 점수를 매길 수 있도록 Power BI에서 일정을 설정하는 방법을 학습했습니다.
