---
title: Power BI에 대한 자격 증명을 프로그래밍 방식으로 구성
description: Power BI를 자동화할 때 자격 증명을 프로그래밍 방식으로 구성하는 방법
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 02/23/2020
ms.openlocfilehash: 1c8741736f0639cba7f8df3f9891a6fe20397d8e
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079511"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Power BI에 대한 자격 증명을 프로그래밍 방식으로 구성

Power BI에 대한 자격 증명을 프로그래밍 방식으로 구성하려면 다음 단계를 따릅니다.

## <a name="update-credentials-flow-for-data-sources"></a>데이터 원본에 대한 자격 증명 흐름 업데이트

1. [데이터 원본 가져오기](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup)를 호출하여 데이터 세트의 데이터 원본을 검색합니다. 각 데이터 원본의 응답 본문에는 형식, 연결 세부 정보, 게이트웨이 및 데이터 원본 ID가 있습니다.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. 자격 증명 형식과 [데이터 원본 업데이트 예제](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)에 따라 자격 증명 문자열을 빌드합니다.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. [게이트웨이 가져오기](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways)를 호출하여 게이트웨이 공용 키를 검색합니다.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. 자격 증명을 암호화합니다.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    2단계의 게이트웨이 공개 키로 자격 증명 문자열을 암호화합니다. 게이트웨이 버전에 따라 공개 키 크기가 서로 다를 수 있습니다. [PowerBI-CSharp GitHub 리포지토리](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions)에서 사용할 수 있는 다음 예제(SDK 코드)를 참조하세요.
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. 암호화된 자격 증명을 사용하여 자격 증명 세부 정보를 빌드합니다.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    **3단계**에서 검색된 공개 키를 사용하여 AssymetricKeyEncriptor 클래스를 사용합니다.

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. [데이터 원본 업데이트](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)를 호출하여 자격 증명을 설정합니다.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>데이터 게이트웨이에 대한 새 데이터 원본 구성

1. 머신에 [온-프레미스 데이터 게이트웨이](https://powerbi.microsoft.com/gateway/)를 설치합니다.

2. [게이트웨이 가져오기](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways)를 호출하여 게이트웨이 ID 및 공용 키를 검색합니다.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. **2단계**에서 검색된 게이트웨이 공개 키를 사용하여 [데이터 원본에 대한 자격 증명 흐름 업데이트](#update-credentials-flow-for-data-sources)에 설명된 것과 동일한 방법으로 자격 증명 정보를 빌드합니다.

4. 요청 본문을 빌드합니다.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. [데이터 원본 만들기](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) API를 호출합니다.

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>자격 증명 유형

[Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/)를 사용하여 **엔터프라이즈 온-프레미스 게이트웨이**에서 [데이터 원본 만들기](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) 또는 [데이터 원본 업데이트](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)를 호출할 때, 자격 증명 값이 게이트웨이의 공개 키를 사용하여 암호화해야 합니다.

>[!NOTE]
>.NET SDK v3 역시 아래에 나열된 .NET SDK v2 예제를 실행할 수 있습니다.

### <a name="windows-and-basic-credentials"></a>Windows 및 기본 자격 증명

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>키 자격 증명

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**OAuth2 자격 증명**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**익명 자격 증명**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>문제 해결

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>데이터 원본 가져오기를 호출할 때 게이트웨이 및 데이터 원본 ID를 찾을 수 없음

이 문제는 데이터 세트가 게이트웨이에 바인딩되지 않았음을 의미합니다. 새 데이터 세트를 만들 때 각 클라우드 연결에 대해 자격 증명이 없는 데이터 원본이 사용자의 클라우드 게이트웨이에 자동으로 생성됩니다. 이 게이트웨이는 클라우드 연결에 대한 자격 증명을 저장하는 데 사용됩니다.

데이터 세트를 만든 후에는 데이터 세트와 적절한 게이트웨이 간에 자동 바인딩이 만들어집니다. 이 게이트웨이에는 모든 연결에 대해 일치하는 데이터 원본이 포함되어 있습니다. 이러한 게이트웨이나 여러 개의 적합한 게이트웨이가 없으면 자동 바인딩이 실패합니다.

온-프레미스 데이터 세트를 사용하는 경우 누락된 온-프레미스 데이터 원본을 만들고 [게이트웨이에 바인딩](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway)을 사용하여 수동으로 데이터 세트를 게이트웨이에 바인딩합니다.

바인딩될 수 있는 게이트웨이를 검색하려면 [게이트웨이 검색](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways)을 사용합니다.