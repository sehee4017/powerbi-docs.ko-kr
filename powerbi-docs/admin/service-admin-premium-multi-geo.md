---
title: Power BI Premium에 대한 다중 지역 지원
description: Power BI 테넌트의 홈 지역이 아닌 다른 지역에 있는 데이터 센터에 콘텐츠를 배포하는 방법을 알아봅니다.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: b0132996be1ed70f228ce96d413c4925dc1a3e48
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512772"
---
# <a name="configure-multi-geo-support-for-power-bi-premium"></a>Power BI Premium에 대한 다중 지역 지원 구성

다중 지역은 다국적 고객이 지역별, 산업별 또는 조직별 데이터 보존 요구 사항을 해결하는 데 도움이 되는 Power BI Premium 기능입니다. Power BI Premium 고객은 Power BI 테넌트의 홈 지역이 아닌 다른 지역에 있는 데이터 센터에 콘텐츠를 배포할 수 있습니다. 지역(지리)은 둘 이상의 지역을 포함할 수 있습니다. 예를 들어 미국은 지역이고 미국 중서부 및 미국 중남부는 미국에 있는 지역입니다. 다음 지역에 콘텐츠를 배포할 수 있습니다.

- 미국
- 캐나다
- 영국
- 브라질
- 유럽
- 일본
- 인도
- 아시아 태평양
- 오스트레일리아
- 아프리카

Power BI Germany, Power BI China(21Vianet에서 운영) 또는 Power BI(미국 정부용)에는 다중 지역을 사용할 수 없습니다.

이제 Power BI Embedded에서도 다중 지역을 사용할 수 있습니다. [Power BI Embedded의 다중 지역 지원](../developer/embedded/embedded-multi-geo.md)에서 자세히 알아보세요.

> [!NOTE]
> Power BI Premium은 최근 **Premium Gen2** 라는 새 버전의 Premium을 출시했으며, 이 버전은 현재 미리 보기로 제공됩니다. Premium Gen2는 프리미엄 용량 관리를 간소화하고 관리 오버헤드를 줄입니다. 자세한 내용은 [Power BI Premium 2세대(미리 보기)](service-premium-what-is.md#power-bi-premium-generation-2-preview)를 참조하세요.

## <a name="enable-and-configure"></a>사용 및 구성

새 용량의 경우 드롭다운에서 기본 지역이 아닌 다른 지역을 선택하여 다중 지역을 사용하도록 설정합니다.  각 사용 가능한 용량은 현재 위치한 지역을 표시합니다(예: **미국 중서부**).

![용량 크기: 지역을 선택합니다. Power BI 다중 지역](media/service-admin-premium-multi-geo/power-bi-multi-geo-capacity-size.png)

용량을 만든 후 용량은 해당 지역에 남아 있고 생성된 작업 영역에는 해당 지역에 저장된 콘텐츠가 포함됩니다. 작업 영역 설정 화면의 드롭다운을 통해 한 지역에서 다른 지역으로 작업 영역을 마이그레이션할 수 있습니다.

![작업 영역 편집: 사용 가능한 용량을 선택합니다. Power BI 다중 지역](media/service-admin-premium-multi-geo/power-bi-multi-geo-edit-workspace.png)

변경 내용을 확인하기 위해 이 메시지가 표시됩니다.

![할당된 작업 영역 변경 확인](media/service-admin-premium-multi-geo/power-bi-multi-geo-change-assigned-workspace-capacity.png)

지금은 마이그레이션하는 동안 게이트웨이 자격 증명을 다시 설정할 필요가 없습니다.  프리미엄 용량 지역에 저장된 후에는 마이그레이션 시 이를 다시 설정해야 합니다.

마이그레이션 중에 새 데이터 세트 게시 또는 예약된 데이터 새로 고침과 같은 특정 작업이 실패할 수 있습니다.  

다중 지역을 사용할 수 있는 경우 다음 항목은 프리미엄 지역에 저장됩니다.

- 가져오기 및 Direct Query 데이터 세트에 대한 모델(.ABF 파일)
- 쿼리 캐시
- R 이미지

다음 항목은 테넌트의 홈 지역에 남아 있습니다.

- 푸시 데이터 세트
- Excel 통합 문서
- 대시보드/보고서 메타데이터: 타일 이름, 타일 쿼리 등
- 게이트웨이 쿼리 또는 예약된 새로 고침 작업에 대한 서비스 버스
- 권한
- 데이터 세트 자격 증명



## <a name="view-capacity-regions"></a>용량 지역 보기

관리 포털에서 Power BI 테넌트의 모든 용량 및 현재 위치한 지역을 볼 수 있습니다.

![프리미엄 용량 보기](media/service-admin-premium-multi-geo/power-bi-multi-geo-premium-capacities.png) 

## <a name="change-the-region-for-existing-content"></a>기존 콘텐츠의 지역 변경

기존 콘텐츠의 지역을 변경해야 하는 경우에는 두 가지 옵션이 있습니다.

- 두 번째 용량을 만들고 작업 영역을 이동합니다. 테넌트에 예비 V 코어가 있으면 무료 사용자에게 가동 중단 시간이 발생하지 않습니다.
- 두 번째 용량도 만들어야 하는 경우에는 콘텐츠를 프리미엄에서 다시 공유 용량으로 임시로 이동할 수 있습니다. 추가 V 코어가 필요하지 않지만 무료 사용자에게 가동 중지 시간이 발생합니다.

## <a name="move-content-out-of-multi-geo"></a>다중 지역에서 콘텐츠 이동  

다음 두 가지 방법 중 하나로 다중 지역 용량에서 작업 영역을 제거할 수 있습니다.

- 작업 영역이 위치한 현재 용량을 삭제합니다.  이렇게 하면 작업 영역이 다시 홈 지역의 공유 용량으로 이동합니다.
- 개별 작업 영역을 다시 홈 테넌트에 있는 프리미엄 용량으로 마이그레이션합니다.

대규모 스토리지 형식 데이터 세트는 생성된 지역에서 이동할 수 없습니다. 대형 데이터 세트를 기반으로 하는 보고서는 데이터 세트를 로드할 수 없으며 ‘모델을 로드할 수 없습니다.’ 오류를 반환합니다. 대규모 스토리지 형식 데이터 세트를 원래 지역으로 다시 이동하여 다시 사용할 수 있도록 합니다.

## <a name="limitations-and-considerations"></a>제한 사항 및 고려 사항

- 지역 간에 시작한 모든 이동이 데이터 전송 전에 모든 회사 및 정부 준수 요구 사항을 따르는지 확인합니다.
- 원격 지역에 저장된 캐시된 쿼리는 해당 지역에 남아 있습니다. 그러나 전송 중인 다른 데이터는 여러 지역 간에 이동할 수 있습니다.
- 다중 지역 환경에서 데이터를 한 지역에서 다른 지역으로 이동하면 원본 데이터는 최대 30일 동안 데이터 이동이 시작된 지역에 남아 있을 수 있습니다. 해당 기간에 최종 사용자는 데이터에 액세스할 수 없습니다. 데이터가 이 지역에서 제거되고 30일 기간 동안 삭제됩니다.
- 가져온 데이터 모델에 대한 쿼리 텍스트 및 쿼리 결과 트래픽은 홈 지역을 통해 전송되지 않습니다. 보고서 메타데이터는 원격 지역에서 계속 제공되며 특정 DNS 라우팅 상태에서는 트래픽이 지역에서 제거될 수 있습니다. 
- 현재는 [데이터 흐름](../transform-model/dataflows/dataflows-introduction-self-service.md) 기능이 다중 지역에서 지원되지 않습니다.
- 대규모 스토리지 형식 데이터 세트를 생성된 지역에서 이동하면 보고서에서 데이터 세트를 로드하지 못하게 됩니다. 대규모 스토리지 데이터 세트를 원래 지역으로 다시 이동하여 사용할 수 있도록 합니다. 

## <a name="next-steps"></a>다음 단계

- [Power BI 프리미엄이란?](service-premium-what-is.md)
- [Power BI Embedded 용량에 대한 다중 지역](../developer/embedded/embedded-multi-geo.md)

궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)

Power BI는 Power BI Premium Gen2를 미리 보기 버전으로 소개했습니다. 이 버전은 다음과 같은 향상된 기능을 통해 Power BI Premium 환경을 개선합니다.
* 성능
* 사용자 단위 라이선싱
* 더 큰 규모
* 개선된 메트릭
* 자동 확장
* 관리 오버헤드 감소

Power BI Premium Gen2에 대한 자세한 내용은 [Power BI Premium 2세대(미리 보기)](service-premium-what-is.md#power-bi-premium-generation-2-preview)를 참조하세요.
