---
title: Power BI 시각적 개체용 SSL 인증서 만들기
description: Windows, Mac 또는 Linux에서 Power BI 시각적 도구를 사용하여 또는 수동으로 SSL 인증서를 생성하는 방법을 알아봅니다.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: f6f458d2fe82668074d7cfb046cb5a72afa35c38
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92048789"
---
# <a name="create-an-ssl-certificate"></a>SSL 인증서 만들기

이 문서에서는 Power BI 시각적 개체용 SSL(Secure Sockets Layer) 인증서를 생성하고 설치하는 방법을 설명합니다.

Windows, macOS X 및 Linux 절차의 경우 Power BI 시각적 도구 **.pbiviz** 패키지가 설치되어 있어야 합니다. 자세한 내용은 [Power BI 시각적 개체 개발을 위한 환경 설정](./environment-setup.md)을 참조하세요. 

## <a name="create-a-certificate-on-windows"></a>Windows에서 인증서 만들기

Windows 8 이상에서 PowerShell `New-SelfSignedCertificate` cmdlet을 사용하여 인증서를 생성하려면 다음 명령을 실행합니다.

```powershell
pbiviz --install-cert
```

Windows 7의 경우 `pbiviz` 도구를 사용하려면 명령줄에서 OpenSSL 유틸리티를 사용해야 합니다. OpenSSL을 설치하려면 [OpenSSL](https://www.openssl.org) 또는 [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries)로 이동합니다.

인증서에 대한 자세한 내용 및 설치 지침은 [Windows용 인증서 만들기 및 설치](./environment-setup.md#create-and-install-a-certificate)를 참조하세요.

## <a name="create-a-certificate-on-macos-x"></a>macOS X에서 인증서 만들기

OpenSSL 유틸리티는 일반적으로 macOS X 운영 체제에서 사용할 수 있습니다.

다음 명령 중 하나를 실행하여 OpenSSL 유틸리티를 설치할 수도 있습니다.

- *Brew* 패키지 관리자를 사용하는 경우:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- *MacPorts* 를 사용하는 경우:
  
  ```cmd
  sudo port install openssl
  ```

OpenSSL 유틸리티를 설치한 후 다음 명령을 실행하여 새 인증서를 생성합니다.

```cmd
pbiviz --install-cert
```

자세한 내용 및 지침은 [인증서 만들기 및 설치](./environment-setup.md#create-and-install-a-certificate)의 OSX 탭을 참조하세요.

## <a name="create-a-certificate-on-linux"></a>Linux에서 인증서 만들기

OpenSSL 유틸리티는 일반적으로 Linux 운영 체제에서 사용할 수 있습니다.

시작하기 전에 다음 명령을 실행하여 `openssl` 및 `certutil`이 설치되어 있는지 확인합니다.

```sh
which openssl
which certutil
```

`openssl` 및 `certutil`이 설치되지 않은 경우 `openssl` 및 `libnss3` 유틸리티를 설치합니다.

### <a name="create-the-ssl-configuration-file"></a>SSL 구성 파일 만들기

다음 텍스트를 포함하는 */tmp/openssl.cnf* 라는 파일을 만듭니다.

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>루트 인증 기관 생성

로컬 인증서에 서명하기 위한 루트 CA(인증 기관)를 생성하려면 다음 명령을 실행합니다.

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>localhost용 인증서 생성 

생성된 CA 및 *openssl.cnf* 를 사용하여 `localhost`용 인증서를 생성하려면 다음 명령을 실행합니다.

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>루트 인증서 추가

Chrome 브라우저의 데이터베이스에 루트 인증서를 추가하려면 다음을 실행합니다.

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Mozilla Firefox 브라우저의 데이터베이스에 루트 인증서를 추가하려면 다음을 실행합니다.

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

시스템 수준 루트 인증서를 추가하려면 다음을 실행합니다.

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>루트 인증서 제거

루트 인증서를 제거하려면 다음을 실행합니다.

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>수동으로 인증서 생성

OpenSSL을 사용하여 수동으로 SSL 인증서를 생성할 수도 있습니다. 인증서를 생성하는 도구는 임의로 지정할 수 있습니다.

OpenSSL 유틸리티를 이미 설치한 경우 다음을 실행하여 새 인증서를 생성합니다.

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

일반적으로 다음 명령 중 하나를 실행하여 `PowerBI-visuals-tools` 웹 서버 인증서를 찾을 수 있습니다.

- 전역 도구 인스턴스의 경우:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- 로컬 도구 인스턴스의 경우:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>PEM 형식

PEM(Privacy Enhanced Mail) 인증서 형식을 사용하는 경우 인증서 파일을 *PowerBIVisualTest_public.crt* 로 저장하고 프라이빗 키를 *PowerBIVisualTest_private.key* 로 저장합니다.

### <a name="pfx-format"></a>PFX 형식

PFX(Personal Information Exchange) 인증서 형식을 사용하는 경우 인증서 파일을 *PowerBIVisualTest_public.pfx* 에 저장합니다.

PFX 인증서 파일에 암호가 필요한 경우

1. 구성 파일에서 다음을 지정합니다.
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. `server` 섹션에서 \<YOUR PASSPHRASE> 자리 표시자를 바꿔 암호를 지정합니다.

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>다음 단계
- [Power 원 카드 BI 시각적 개체 개발](develop-circle-card.md)
- [Power BI 시각적 개체 샘플](samples.md)
- [AppSource에 Power BI 시각적 개체 게시](office-store.md)