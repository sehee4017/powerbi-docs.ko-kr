---
title: 'Project Online: Power BI Desktop을 통해서 데이터에 연결'
description: 'Project Online: Power BI Desktop을 통해서 데이터에 연결'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 04/01/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 807ba59066508d063dba2e2f921eff19cf018bc5
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214610"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>Power BI Desktop을 통해 Project Online 데이터에 연결
Power BI Desktop을 통해 Project Online의 데이터에 연결할 수 있습니다.

## <a name="step-1-download-power-bi-desktop"></a>1단계: Power BI Desktop 다운로드
1. [Power BI Desktop을 다운로드](https://go.microsoft.com/fwlink/?LinkID=521662)하고 설치 관리자를 실행하여 컴퓨터에 **Power BI Desktop**을 설치합니다.

## <a name="step-2-connect-to-project-online-with-odata"></a>2단계: OData를 사용하여 Project Online에 연결
1. **Power BI Desktop**을 엽니다.
2. *시작 화면*에서 **데이터 가져오기**를 선택합니다.
3. **OData 피드**를 선택하고 **연결**을 선택합니다.
4. URL 상자의 OData 피드에 대한 주소를 입력하고 확인을 클릭합니다.
   
   프로젝트 웹앱 주소가*https://\<tenantname\>.sharepoint.com/sites/pwa*와 비슷한 경우 OData 피드에 대해 입력할 주소는 *https://\<tenantname\>.sharepoint.com/sites/pwa/\_api/Projectdata*입니다.
   
   이 예에서는 다음을 사용합니다.

    `https://contoso.sharepoint.com/sites/pwa/default.aspx`

5. Power BI Desktop에서 회사 또는 학교 계정을 사용하여 인증하라는 메시지가 나타납니다. 조직 계정을 선택하고 자격 증명을 입력합니다.
   
   ![연결하기 위한 자격 증명 프롬프트를 보여 주는 Power BI Desktop의 스크린샷.](media/desktop-project-online-connect-to-data/image.png)

OData 피드에 연결하는 데 사용하는 계정에는 프로젝트 웹앱 사이트에 대한 포트폴리오 뷰어 이상의 액세스 권한이 있어야 합니다. 

여기에서는 연결하고자 하는 테이블을 선택하고 쿼리를 작성할 수 있습니다.  시작하는 방법이 궁금하십니까?  다음 블로그 게시물에서는 사용자의 Project Online 데이터에서 번다운 차트를 작성하는 방법을 보여줍니다.  이 블로그 게시물은 Project Online에 연결하는 데 Power Query를 사용하는 것을 참조하지만, Power BI Desktop도 사용 가능합니다.

[파워 피벗 및 파워 쿼리를 사용하여 프로젝트에 대한 번다운 차트 만들기](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

