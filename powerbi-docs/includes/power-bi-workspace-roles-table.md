---
title: Power BI 작업 영역 역할
description: Power BI 작업 영역 역할 표
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 5ed3a65f1ef65640c76ada765931a85714aad3af
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781356"
---
다음은 관리자, 구성원, 참가자, 뷰어 등 네 가지 역할의 기능입니다. 보기와 상호 작용을 제외한 모든 기능에는 Power BI Pro 라이선스가 필요합니다.

|기능   | 관리자  | 멤버  | 참가자  | 뷰어 |
|---|---|---|---|---|
| 작업 영역 업데이트 및 삭제  | X  |   |   |   | 
| 다른 관리자를 비롯한 사람 추가/제거  | X  |   |   |   |
| 낮은 권한을 가진 구성원 또는 다른 사용자 추가  |  X | X  |   |   |
| 앱 게시 및 업데이트 |  X | X  |   |   |
| 항목 공유 또는 앱 공유.<sup>1</sup> |  X | X  |   |   |
| 다른 사용자가 항목을 다시 공유하도록 허용.<sup>1</sup> |  X | X  |   |   |
| 동료의 홈에서 앱 추천 |  X | X  |   |   |
| 동료의 홈에서 대시보드 및 보고서 추천 |  X | X  | X |   |
| 작업 영역에서 콘텐츠 만들기, 편집 및 삭제  |  X | X  | X  |   |
| 작업 영역에 보고서 게시, 콘텐츠 삭제  |  X | X  | X  |   |
| 이 작업 영역의 데이터 세트를 기반으로 하여 다른 작업 영역에 보고서 만들기.<sup>1</sup> |  X | X  | X  |   |
| 보고서 복사.<sup>2</sup> | X | X | X |  |
| 온-프레미스 게이트웨이를 통해 데이터 새로 고침을 예약합니다.<sup>3</sup> | X | X | X |  |
| 게이트웨이 연결 설정을 수정합니다.<sup>3</sup> | X | X | X |  |
| 항목을 보고 상호 작용합니다.<sup>4</sup> |  X | X  | X  | X  |
| 작업 영역 데이터 흐름에 저장된 데이터 읽기 | X | X | X | X |

1. 참가자와 시청자는 다시 공유 권한이 있는 경우 작업 영역에서 항목을 공유할 수 있습니다.
2. 보고서를 복사하고 다른 작업 영역에서 이 작업 영역의 데이터 세트를 기반으로 하는 보고서를 만들려면 데이터 세트에 대한 빌드 권한이 있어야 합니다. 이 작업 영역의 데이터 세트에 대해 관리자, 구성원 및 기여자 역할이 있는 사용자는 해당 작업 영역 역할을 통해 빌드 권한을 갖습니다.
3. 게이트웨이에 대한 권한도 필요하다는 사실에 유의하세요. 이러한 권한은 작업 영역 역할 및 권한에 관계없이 다른 곳에서 관리됩니다. 자세한 내용은 [온-프레미스 게이트웨이 관리](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage)를 참조하세요.
4. Power BI Pro 라이선스가 없더라도, 항목이 프리미엄 용량의 작업 영역에 있는 경우 Power BI 서비스에서 항목을 보고 상호 작용할 수 있습니다.

