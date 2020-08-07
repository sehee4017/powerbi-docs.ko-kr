---
title: DAX 샘플 모델
description: 참조 문서를 지원하는 DAX 샘플 모델입니다.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/25/2020
ms.author: v-pemyer
ms.openlocfilehash: 6e2fe331fa274305447266321893204dddcc3148
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537461"
---
# <a name="dax-sample-model"></a>DAX 샘플 모델

**Adventure Works DW 2020** Power BI Desktop 샘플 모델은 DAX 학습을 지원하도록 설계되었습니다. 이 모델은 AdventureWorksDW2017용 [Adventure Works 데이터 웨어하우스 샘플](/sql/samples/adventureworks-install-configure#data-warehouse-downloads)을 기반으로 하지만 샘플 모델의 목표에 맞게 데이터가 수정되었습니다.

## <a name="scenario"></a>시나리오

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="Adventure Works 회사 로고 이미지가 표시됩니다.":::

Adventure Works 회사는 자전거와 액세서리를 글로벌 시장에 판매하는 자전거 제조업체를 대표합니다. 이 회사의 데이터 웨어하우스 데이터는 Azure SQL Database에 저장됩니다.

## <a name="model-structure"></a>모델 구조

모델에는 7개의 테이블이 있습니다.

|테이블|Description|
|-----|-------|
|**고객**|고객과 고객의 지리적 위치를 설명합니다. 고객은 온라인으로 제품을 구입합니다(인터넷 판매).|
|**Date**|**Date** 테이블과 **Sales** 테이블 간에는 주문 날짜, 배송 날짜, 기한 등 세 가지 관계가 있습니다. 주문 날짜 관계는 활성 상태입니다. 회사의 보고서는 매년 7월 1일에 시작되는 회계 연도를 사용하여 매출을 보고합니다. 테이블은 **Date** 열을 사용하여 날짜 테이블로 표시됩니다.|
|**Product**|완성된 제품만 저장합니다.|
|**Reseller**|재판매인과 재판매인의 지리적 위치를 설명합니다. 재판매인은 고객에게 제품을 판매합니다.|
|**Sales**|판매 주문 라인 그레인에 행을 저장합니다. 재정적 값은 모두 미국 달러(USD) 기준입니다. 가장 이른 주문 날짜는 2017년 7월 1일이고, 가장 최근 주문 날짜는 2020년 6월 15일입니다.|
|**Sales Order**|판매 주문 및 주문 라인 번호와 **재판매인** 또는 **인터넷**인 판매 채널을 설명합니다. 이 테이블은 **Sales** 테이블과 일대일 관계를 갖습니다.|
|**Sales Territory**|영업권역은 그룹(북아메리카, 유럽, 태평양), 국가, 지역으로 구성됩니다. 미국만 지역 수준에서 제품을 판매합니다.|

모델에는 DAX 계산이 포함되어 있지 않습니다.

## <a name="download-sample"></a>샘플 다운로드

Power BI Desktop 샘플 모델 파일은 [여기](https://aka.ms/dax-docs-sample-file)서 다운로드할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 문서에 대한 자세한 내용은 다음 리소스를 참조하세요.

- [DAX(Data Analysis Expressions) 참조](/dax/)
- 학습 경로: [Power BI Desktop에서 DAX 사용](https://docs.microsoft.com/learn/paths/dax-power-bi/)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com)
