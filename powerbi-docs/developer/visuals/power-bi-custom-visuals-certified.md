---
title: 인증된 Power BI 시각적 개체
description: 인증을 위해 사용자 지정 시각적 개체를 제출하기 위한 요구 사항 및 프로세스와 인증된 Power BI 시각적 개체 목록.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: how-to
ms.subservice: powerbi-custom-visuals
ms.date: 03/08/2020
ms.openlocfilehash: ee79a2f74714322e6ff7b4ec965060b7c9291060
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237435"
---
# <a name="get-a-power-bi-visual-certified"></a>Power BI 시각적 개체 인증받기

인증된 Power BI 시각적 개체란 Microsoft Power BI 팀 [코드 요구 사항](#certification-requirements)을 충족하는 [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals)의 Power BI 시각적 개체입니다. 이러한 시각적 개체는 외부 서비스 또는 리소스에 액세스 하지 않고 보안 코딩 패턴 및 지침을 따르는지 확인하는 테스트를 거쳤습니다.

인증된 Power BI 시각적 개체는 더 많은 기능을 제공합니다. 예를 들어 [PowerPoint로 내보내기](../../consumer/end-user-powerpoint.md)가 가능하고 사용자가 [보고서 페이지를 구독](../../consumer/end-user-subscribe.md)할 때 받은 이메일에 시각적 개체를 표시할 수 있습니다.

인증 프로세스는 선택 사항입니다. 인증되지 않은 Power BI 시각적 개체라고 해서 반드시 안전하지 않은 Power BI 시각적 개체인 것은 아닙니다. 일부 Power BI 시각적 개체는 [인증 요구 사항](power-bi-custom-visuals-certified.md#certification-requirements) 중 하나 이상을 준수하지 않았기 때문에 인증되지 않았습니다. 예를 들어 외부 서비스에 연결하는 맵 Power BI 시각적 개체 또는 상용 라이브러리를 사용하는 Power BI 시각적 개체가 그렇습니다.

> [!NOTE]
> Microsoft는 타사 Power BI 시각적 개체의 작성자가 아닙니다. 타사 시각적 개체의 기능을 확인하려면 시각적 개체의 작성자에게 직접 문의하세요.

## <a name="certification-requirements"></a>인증 요구 사항

Power BI 시각적 개체를 [인증](#get-a-power-bi-visual-certified)받으려면 Power BI 시각적 개체가 이 섹션에 나열된 요구 사항을 준수해야 합니다. 

### <a name="general-requirements"></a>일반 요구 사항

Power BI 시각적 개체는 파트너 센터에서 승인되어야 합니다. Power BI 시각적 개체가 이미 [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)에 있는 것이 좋습니다. Power BI 시각적 개체를 AppSource에 게시하는 방법을 알아보려면 [파트너 센터에 Power BI 시각적 개체 게시](office-store.md)를 참조하세요.

인증을 받기 위해 Power BI 시각적 개체를 제출하기 전에 [Power BI 시각적 개체에 대한 지침](guidelines-powerbi-visuals.md)을 준수하는지 확인합니다.

Power BI 시각적 개체를 제출할 때 컴파일된 패키지가 제출된 패키지와 정확히 일치하는지 확인합니다.

### <a name="code-repository-requirements"></a>코드 리포지토리 요구 사항

GitHub에서 공개적으로 코드를 공유할 필요는 없지만 Power BI 팀이 코드 리포지토리를 검토할 수 있어야 합니다. 이렇게 하는 가장 좋은 방법은 GitHub에서 소스 코드(JavaScript 또는 TypeScript)를 제공하는 것입니다.

리포지토리에는 다음이 포함되어야 합니다.
* Power BI 시각적 개체 단 하나의 코드. 여러 Power BI 시각적 개체의 코드나 관계가 없는 코드는 포함할 수 없습니다.
* **certification**(소문자 필수)이라는 분기. 이 분기의 소스 코드는 제출된 패키지와 일치해야 합니다. 이 코드는 Power BI 시각적 개체를 다시 제출하는 경우, 다음 제출 프로세스 중에만 업데이트할 수 있습니다.

Power BI 시각적 개체가 비공개 npm 패키지 또는 git 하위 모듈을 사용하는 경우, 이 코드가 포함된 추가 리포지토리에 대한 액세스 권한을 제공해야 합니다.

Power BI 시각적 리포지토리가 어떻게 보이는지 이해하려면 [Power BI 시각적 개체 샘플 가로 막대형 차트](https://github.com/microsoft/PowerBI-visuals-sampleBarChart)에 대한 GitHub 리포지토리를 검토합니다.

### <a name="file-requirements"></a>파일 요구 사항

최신 버전의 API를 사용하여 Power BI 시각적 개체를 작성합니다.

리포지토리에는 다음 파일이 포함되어야 합니다.
* **.gitignore** - 이 파일에 `node_modules`, `.tmp` 및 `dist`를 추가합니다. 코드에는 *node_modules*, *.tmp* 또는 *dist* 폴더가 포함될 수 없습니다.
* **capabilities.json** - 이 파일의 속성이 변경된 새 버전의 Power BI 시각적 개체를 제출하는 경우, 기존 사용자의 보고서를 중단하지 않는지 확인합니다.
* **pbiviz.json** 
* **package.json**. 시각적 개체에는 다음 패키지가 설치되어 있어야 합니다.
   * ["tslint"](https://www.npmjs.com/package/tslint) - 버전 5.18.0 이상
   * ["typescript"](https://www.npmjs.com/package/typescript) - 버전 3.0.0 이상
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib) - 버전 6.2.0 이상
   * 이 파일은 linter를 실행하기 위한 명령을 포함해야 합니다. `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>명령 요구 사항

다음 명령이 오류를 반환하지 않는지 확인합니다.

* `npm install`
* `pbiviz package`
* `npm audit` - 높음 또는 보통 수준의 경고를 반환하지 않아야 합니다.
* [필요한 구성](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json)을 포함하는 [Microsoft의 TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib). 이 명령이 lint 오류를 반환하지 않아야 합니다.

### <a name="compiling-requirements"></a>컴파일 요구 사항

최신 버전의 [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)를 사용하여 Power BI 시각적 개체를 작성합니다.

`pbiviz package`를 사용하여 Power BI 시각적 개체를 컴파일해야 합니다. 자체 빌드 스크립트를 사용하는 경우, `npm run package` 사용자 지정 빌드 명령을 제공합니다.

### <a name="source-code-requirements"></a>소스 코드 요구 사항

[Power BI 시각적 개체 추가 인증](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification) 정책 목록을 따르는지 확인합니다. 제출이 이러한 지침을 따르지 않는 경우, 파트너 센터의 거부 전자 메일에는 이 링크에 나열된 정책 번호가 포함됩니다.

코드가 Power BI 인증 정책에 맞도록 하려면 아래 나열된 코드 요구 사항에 따르세요.  

**필수**
* 공용 Javascript 또는 TypeScript 라이브러리와 같은 공개적으로 검토 가능한 OSS 구성 요소만 사용하세요.
* 코드는 [렌더링 이벤트 API](event-service.md)를 지원해야 합니다.
* DOM을 안전하게 조작해야 합니다. DOM에 추가하기 전에 사용자 입력 또는 사용자 데이터에 대한 삭제를 사용합니다.
* [샘플 보고서](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix)를 테스트 데이터 세트로 사용합니다.

**허용되지 않음**
* 외부 서비스 또는 리소스에 액세스. 예를 들어 Power BI가 어떤 서비스에도 HTTP/S 또는 WebSocket 요청을 보낼 수 없어야 합니다.
* `innerHTML` 또는 `D3.html(user data or user input)` 사용.
* 브라우저 콘솔에서 입력 데이터에 대한 JavaScript 오류 또는 예외.
* `eval()`과 같은 임의 또는 동적 코드, `settimeout()`, `requestAnimationFrame()`, `setinterval(user input function)`, 사용자 입력 또는 사용자 데이터의 안전하지 않은 사용.
* 축소된 JavaScript 파일 또는 프로젝트.

## <a name="submitting-a-power-bi-visual-for-certification"></a>인증을 위한 Power BI 시각적 개체 제출

파트너 센터를 통해 Power BI 팀에 Power BI 시각적 개체를 인증하도록 요청할 수 있습니다.

>[!TIP]
>Power BI 인증 프로세스는 시간이 걸릴 수 있습니다. 새 Power BI 시각적 개체를 만드는 경우 Power BI 인증을 요청하기 전에 파트너 센터를 통해 Power BI 시각적 개체를 게시하는 것이 좋습니다. 이렇게 하면 시각적 개체의 게시가 지연되지 않습니다.

Power BI 인증을 요청하려면

1. 파트너 센터에 로그인합니다.
2. **개요 페이지**에서 Power BI 시각적 개체를 선택하고 **제품 설정** 페이지로 이동합니다.
3. **Power BI 인증 요청** 확인란을 선택합니다.
4. **검토 및 게시** 페이지의 **인증에 대한 참고 사항** 텍스트 상자에 소스 코드 및 액세스 자격 증명에 대한 링크를 제공합니다.

### <a name="private-repository-submission-process"></a>프라이빗 리포지토리 제출 프로세스

GitHub와 같은 프라이빗 리포지토리를 사용하여 인증을 위한 Power BI 시각적 개체를 제출하는 경우 이 섹션의 지침을 따르세요.
1. 유효성 검사 팀을 위한 새 계정을 만듭니다.
2. 계정의 [2단계 인증](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa)을 구성합니다.
3. [새 복구 코드 집합을 생성합니다](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. Power BI 시각적 개체를 제출할 때 다음을 제공합니다.
    * 리포지토리에 대한 링크
    * 로그인 자격 증명(암호 포함)
    * 복구 코드
    * 우리 계정([pbicvsupport](https://github.com/pbicvsupport))에 대한 읽기 전용 권한

## <a name="certified-power-bi-visual-badges"></a>인증된 Power BI 시각적 개체 배지

Power BI 시각적 개체가 인증되면 인증되었음을 나타내는 지정된 배지를 가져옵니다.

### <a name="certified-power-bi-visuals-in-appsource"></a>AppSource의 인증된 Power BI 시각적 개체

* 온라인에서 [AppSource의 Power BI 시각적 개체](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)를 검색하면 시각적 카드에 있는 작은 노란색 배지에 인증된 Power BI 시각적 개체라고 표시됩니다.

    ![AppSource 인증 Power BI 시각적 개체](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* AppSource에서 Power BI 시각적 카드를 클릭하면 *PBI 인증*이라는 노란색 배지에 이 Power BI 시각적 개체가 인증되었다고 표시됩니다.

    ![앱 페이지 인증된 Power BI 시각적 개체](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Power BI 인터페이스의 인증된 Power BI 시각적 개체

* Power BI(데스크톱 또는 서비스) 내에서 Power BI 시각적 개체를 가져오는 경우 파란색 배지는 Power BI 시각적 개체가 인증되었음을 표시합니다.

    ![Power BI 인터페이스의 인증된 Power BI 시각적 개체](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* *Power BI 인증* 필터 옵션을 선택하여 인증된 Power BI 시각적 개체만 표시할 수 있습니다.

## <a name="publication-timeline"></a>게시 타임라인

AppSource에 배포하는 프로세스는 다소 시간이 걸릴 수 있습니다. 이 프로세스가 완료되면 Power BI 시각적 개체를 AppSource에서 다운로드할 수 있습니다.

### <a name="when-will-users-be-able-to-download-my-visual"></a>사용자가 내 시각적 개체를 다운로드할 수 있나요?

* Power BI 시각적 개체를 처음 제출한 경우 사용자는 AppSource에서 전자 메일을 받은 후 몇 시간 후에 다운로드할 수 있습니다.

* 기존 Power BI 시각적 개체에 업데이트를 제출하는 경우 사용자가 제출한 후 한 달 이내에 업데이트를 다운로드할 수 있습니다.

    >[!NOTE]
    > AppSource의 *버전* 필드는 시각적 개체를 제출한 후 약 1주일 후에 AppSource에서 Power BI를 승인한 날짜로 업데이트됩니다. 사용자는 업데이트된 시각적 개체를 다운로드할 수 있지만 업데이트된 기능은 적용되지 않습니다. 시각적 개체의 새 기능은 한 달 후에 사용자의 보고서에 영향을 줍니다. 

### <a name="when-will-my-power-bi-visual-display-a-certification-badge"></a>언제 내 Power BI 시각적 개체에서 인증 배지를 표시하나요?

* Power BI 시각적 개체를 처음 제출한 경우 AppSource에서 승인 전자 메일을 받은 날에 인증 배지가 나타납니다.

* 기존 Power BI 시각적 개체에 대한 인증을 요청하는 경우 제출 후 한 달 이내에 인증 배지가 표시됩니다.

## <a name="next-steps"></a>다음 단계

* 자체 Power BI 시각적 개체를 만들어  [Microsoft AppSource](https://appsource.microsoft.com)에 추가하는 데 관심이 있는 웹 개발자라면  [Power BI 시각적 개체 개발](custom-visual-develop-tutorial.md) 자습서로 시작할 수 있습니다.

* 시각적 개체에 대한 자세한 내용은 [인증된 시각적 개체에 관한 자주 묻는 질문](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)을 참조하세요.

* [Power BI 시각적 개체 개발](custom-visual-develop-tutorial.md)

* [Microsoft의 Power BI 시각적 개체 YouTube 재생 목록](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Power BI의 시각적 개체](power-bi-custom-visuals.md)

* [Microsoft AppSource에 Power BI 시각적 개체 게시하기](office-store.md)

* 궁금한 점이 더 있나요? [Power BI 커뮤니티를 이용하세요.](https://community.powerbi.com/)