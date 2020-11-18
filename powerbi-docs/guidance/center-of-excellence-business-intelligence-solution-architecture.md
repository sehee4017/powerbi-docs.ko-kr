---
title: 최고 전문가 조직(Center of Excellence, COE)의 BI 솔루션 아키텍처
description: 강력한 BI 플랫폼을 디자인하고 개발할 때 고려할 사항에 대해 알아봅니다.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/11/2020
ms.author: v-pemyer
ms.openlocfilehash: d84f6a4fcf7ff531b76b6e731f165aa6e0df764f
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512128"
---
# <a name="bi-solution-architecture-in-the-center-of-excellence"></a>최고 전문가 조직(Center of Excellence, COE)의 BI 솔루션 아키텍처

이 문서는 IT 전문가와 IT 관리자를 대상으로 합니다. COE의 BI 솔루션 아키텍처 및 사용되는 다양한 기술에 대해 알아봅니다. Azure, Power BI, Excel을 비롯한 이러한 기술을 함께 활용하여 확장성 있는 데이터 기반 클라우드 BI 플랫폼을 제공할 수 있습니다.

강력한 BI 플랫폼을 설계하는 것은 교량을 건축하는 것과 비슷합니다. 변환되고 보강된 원본 데이터를 데이터 소비자에게 연결하는 교량과 같습니다. 이러한 복잡한 구조의 디자인은 엔지니어링 마인드를 요구하지만 가장 창의적이고 보람 있는 IT 아키텍처 중 하나일 수 있습니다. 대규모 조직에서 BI 솔루션 아키텍처는 다음과 같이 구성될 수 있습니다.

- 데이터 원본
- 데이터 수집
- 빅 데이터/데이터 준비
- 데이터 웨어하우스
- BI 의미 체계 모델
- 보고서

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-business-intelligence-platform.png" alt-text="데이터 원본에서 데이터 수집, 빅 데이터, 저장소, 데이터 웨어하우스, BI 의미 체계 모델링, 보고, 기계 학습까지 BI 플랫폼 아키텍처 다이어그램을 보여 주는 다이어그램.":::

플랫폼은 특정 요구를 지원해야 합니다. 특히 비즈니스 서비스 및 데이터 소비자의 기대를 충족하기 위해 확장하고 수행해야 합니다. 이와 동시에, 처음부터 보안을 보장하도록 디자인해야 합니다. 또한 새로운 데이터와 주제 영역을 시간 내에 온라인으로 전환해야 하므로 변경에 맞게 조정되도록 충분한 복원력이 있어야 합니다.

## <a name="frameworks"></a>프레임워크

Microsoft는 처음부터 프레임워크 개발에 투자하여 시스템과 유사한 접근 방식을 채택했습니다. 기술 및 비즈니스 프로세스 프레임워크는 디자인 및 논리의 재사용을 높이고 일관된 결과를 제공합니다. 또한 다양한 기술을 활용하는 아키텍처 유연성을 제공하며 반복 가능한 프로세스를 통해 엔지니어링 오버헤드를 간소화하고 감소시킵니다.

잘 설계된 프레임워크는 데이터 계보, 영향 분석, 비즈니스 논리 유지 관리, 분류 관리, 거버넌스 간소화에 대한 가시성을 증대합니다. 또한 개발이 더 빨라지고 대규모 팀 전반의 협업은 응답성과 효과가 향상됩니다.

이 문서에서는 몇 가지 프레임워크에 관해 설명합니다.

## <a name="data-models"></a>데이터 모델

데이터 모델을 사용하면 데이터를 구조화하고 액세스하는 방법을 제어할 수 있습니다. 비즈니스 서비스 및 데이터 소비자에게 데이터 모델은 BI 플랫폼과 상호 작용하는 인터페이스입니다.

BI 플랫폼은 다음과 같은 세 가지 유형의 모델을 제공할 수 있습니다.

- 엔터프라이즈 모델
- BI 의미 체계 모델
- ML(기계 학습) 모델

### <a name="enterprise-models"></a>엔터프라이즈 모델

**엔터프라이즈 모델** 은 IT 설계자가 빌드하고 유지 관리합니다. 차원 모델 또는 데이터 마트라고도 합니다. 일반적으로 데이터는 차원 테이블 및 팩트 테이블로 관계형 형식으로 저장됩니다. 이러한 테이블은 많은 시스템에서 통합된 데이터를 정리 및 보강하여 저장하고 보고 및 분석을 위한 신뢰할 수 있는 원본을 나타냅니다.

엔터프라이즈 모델은 보고 및 BI를 위한 일관된 단일 데이터 원본을 제공합니다. 한 번 빌드되고 회사 표준으로 공유됩니다. 거버넌스 정책은 고객 정보나 재무 같은 중요한 데이터 세트에 대한 액세스가 요구에 따라 제한되도록 하여 데이터를 안전하게 보호합니다. 일관성을 보장하는 명명 규칙을 채택하여 데이터 신뢰도와 품질을 더욱 확고히 합니다.

클라우드 BI 플랫폼에서는 [Azure Synapse의 Synapse SQL 풀](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is#synapse-sql-pool-in-azure-synapse)에 엔터프라이즈 모델을 배포할 수 있습니다. 그러면 Synapse SQL 풀은 빠르고 강력한 인사이트를 위해 의존할 수 있는 조직의 단일 소스 버전이 됩니다.

### <a name="bi-semantic-models"></a>BI 의미 체계 모델

**BI 의미 체계 모델** 은 엔터프라이즈 모델을 통해 의미 체계 계층을 나타냅니다. BI 개발자 및 비즈니스 사용자가 빌드하고 유지 관리합니다. BI 개발자는 엔터프라이즈 모델의 데이터를 원본으로 하는 핵심 BI 의미 체계 모델을 만듭니다. 비즈니스 사용자는 비교적 작은 규모의 독립적인 모델을 만들 수도 있고 부서별 원본이나 외부 원본으로 핵심 BI 의미 체계 모델을 확장할 수도 있습니다. BI 의미 체계 모델은 일반적으로 단일 주제 영역에 집중하며 널리 공유되는 경우가 많습니다.

비즈니스 기능은 데이터만으로 사용할 수 없으며 개념, 관계, 규칙 및 표준을 설명하는 BI 의미 체계 모델에 의해 사용할 수 있게 됩니다. 이런 방식으로 데이터 관계를 정의하고 비즈니스 규칙을 계산으로 캡슐화하는 직관적이고 이해하기 쉬운 구조를 나타냅니다. 또한 적절한 사용자가 올바른 데이터에 액세스할 수 있도록 세분화된 데이터 권한을 적용할 수 있습니다. 중요한 점은 쿼리 성능을 가속화함으로써 테라바이트 수준의 데이터에 대해서도 응답성이 뛰어난 대화형 분석을 제공한다는 점입니다. BI 의미 체계 모델은 엔터프라이즈 모델과 마찬가지로 일관성을 보장하는 명명 규칙을 채택합니다.

클라우드 BI 플랫폼에서 BI 개발자는 [Azure Analysis Services](/azure/analysis-services/) 또는 [Power BI Premium 용량](../admin/service-premium-what-is.md#reserved-capacities)에 BI 의미 체계 모델을 배포할 수 있습니다. 보고 및 분석 계층으로 사용되는 경우 Power BI에 배포하는 것이 좋습니다. 이러한 제품은 서로 다른 스토리지 모드를 지원하므로, 데이터 모델 테이블이 데이터를 캐시하거나 기본 데이터 원본에 쿼리를 전달하는 기술인 [DirectQuery](directquery-model-guidance.md)를 사용할 수 있습니다. DirectQuery는 모델 테이블이 대규모 데이터 볼륨을 나타내는 경우나 거의 실시간으로 결과를 제공해야 하는 경우 이상적인 스토리지 모드입니다. 두 스토리지 모드를 결합할 수 있습니다. [복합 모델](composite-model-guidance.md)은 서로 다른 스토리지 모드를 사용하는 테이블을 단일 모델에 결합합니다.

과도하게 쿼리되는 모델의 경우 [Azure Load Balancer](/azure/load-balancer/load-balancer-overview)를 사용하여 모델 복제본 간에 쿼리 로드를 균등하게 분산할 수 있습니다. 또한 애플리케이션 크기를 조정하고 가용성이 높은 BI 의미 체계 모델을 만들 수 있습니다.

### <a name="machine-learning-models"></a>기계 학습 모델

[**ML(기계 학습) 모델**](/windows/ai/windows-ml/what-is-a-machine-learning-model)은 데이터 과학자가 빌드하고 유지 관리합니다. 주로 데이터 레이크의 원시 원본에서 개발합니다.

학습된 ML 모델은 데이터 내의 패턴을 표시할 수 있습니다. 대부분의 경우 이러한 패턴을 사용하여 데이터를 보강하는 데 사용할 수 있는 예측을 만들 수 있습니다. 예를 들어 구매 동작은 고객 이탈을 예측하고 고객 세그먼트를 구분하는 데 사용할 수 있습니다. 예측 결과를 엔터프라이즈 모델에 추가하여 고객 세그먼트별로 분석할 수 있습니다.

클라우드 BI 플랫폼에서는 [Azure Machine Learning](/azure/machine-learning/overview-what-is-azure-ml)을 사용하여 ML 모델을 학습, 배포, 자동화, 관리 및 추적할 수 있습니다.

## <a name="data-warehouse"></a>데이터 웨어하우스

BI 플랫폼의 핵심에는 엔터프라이즈 모델을 호스트하는 데이터 웨어하우스가 있습니다. 데이터 웨어하우스는 레코드 시스템 또는 허브로서 권한 승인된 데이터의 소스입니다. 보고, BI 및 데이터 과학을 위한 엔터프라이즈 모델을 지원합니다.

LOB(기간 업무) 애플리케이션을 비롯한 많은 비즈니스 서비스는 데이터 웨어하우스를 기업의 지식을 위한 관리되는 신뢰 원본으로 사용할 수 있습니다.

Microsoft에서 데이터 웨어하우스는 ADLS Gen2([Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction)) 및 Azure Synapse Analytics에서 호스트됩니다.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse.png" alt-text="이미지는 Azure Data Lake Storage Gen2에 연결하는 Azure Synapse Analytics를 보여 줍니다.":::

- **ADLS Gen2** 는 Azure에서 Azure Storage를 엔터프라이즈 데이터 레이크를 구축하기 위한 기반으로 만듭니다. 수백 기가비트의 처리량을 유지하는 동시에 여러 페타바이트의 정보를 처리하도록 설계되었습니다. 또한 낮은 비용의 스토리지 용량 및 트랜잭션을 제공합니다. 추가로, Hadoop 호환 액세스를 지원하여 HDFS(Hadoop 분산 파일 시스템)를 사용하는 것처럼 데이터를 관리하고 액세스할 수 있게 합니다. 실제로 [Azure HDInsight](/azure/hdinsight/), [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) 및 Azure Synapse Analytics는 모두 ADLS Gen2에 저장된 데이터에 액세스할 수 있습니다. 따라서 BI 플랫폼에서는 원시 원본 데이터, 부분적으로 처리되었거나 스테이징된 데이터, 프로덕션 준비가 된 데이터를 저장하는 것이 좋습니다. Microsoft는 이 플랫폼을 사용하여 모든 비즈니스 데이터를 저장합니다.
- **Azure Synapse Analytics** 는 엔터프라이즈 데이터 웨어하우징과 빅 데이터 분석을 결합한 분석 서비스입니다. 또한 서버리스 주문형 리소스 또는 프로비저닝된 리소스를 규모에 맞게 사용하여 사용자의 용어로 데이터를 자유롭게 쿼리할 수 있습니다. Azure Synapse Analytics의 구성 요소인 Synapse SQL은 완벽한 T-SQL 기반 분석을 지원하므로 차원 테이블 및 팩트 테이블을 구성하는 엔터프라이즈 모델을 호스트하는 것이 적합합니다. 간단한 [Polybase T-SQL](/sql/relational-databases/polybase/polybase-guide) 쿼리를 사용하여 ADLS Gen2에서 테이블을 효율적으로 로드할 수 있습니다. 그런 다음 [MPP](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture#synapse-sql-mpp-architecture-components)의 기능을 통해 고성능 분석을 실행합니다.

### <a name="business-rules-engine-framework"></a>비즈니스 규칙 엔진 프레임워크

데이터 웨어하우스 계층에서 구현할 수 있는 비즈니스 논리를 카탈로그하는 BRE(**비즈니스 규칙 엔진**) 프레임워크를 개발했습니다. BRE은 많은 의미가 있지만 데이터 웨어하우스의 컨텍스트에서 관계형 테이블에서 계산 열을 만드는 데 유용합니다. 이러한 계산 열은 일반적으로 조건문을 사용하여 수학적 계산 또는 식으로 표현됩니다.

핵심 BI 코드에서 비즈니스 논리를 분할하려고 합니다. 일반적으로 비즈니스 규칙은 SQL 저장 프로시저에 하드 코드되므로 비즈니스 요구 사항이 변경될 때 비즈니스 규칙을 유지 관리하는 데 많은 노력을 기울여야 하는 경우가 많습니다. BRE에서 비즈니스 규칙은 한 번 정의되고 서로 다른 데이터 웨어하우스 엔터티에 적용될 때 여러 번 사용됩니다. 계산 논리를 변경해야 하는 경우에는 여러 저장 프로시저가 아닌 하나의 위치에서 업데이트하기만 하면 됩니다. 부수적인 이점도 있습니다. BRE 프레임워크는 구현된 비즈니스 논리에 대한 투명성과 가시성을 제공하며, 이는 자체 업데이트 설명서를 만드는 일련의 보고서를 통해 노출될 수 있습니다.

## <a name="data-sources"></a>데이터 원본

데이터 웨어하우스는 실제로 모든 데이터 원본의 데이터를 통합할 수 있습니다. 주로 판매, 마케팅, 재무 등에 대한 주제별 데이터를 저장하는 관계형 데이터베이스인 LOB 데이터 원본을 통해 빌드됩니다. 이러한 데이터베이스는 클라우드에서 호스트되거나 온-프레미스에 상주할 수 있습니다. 다른 데이터 원본은 파일 기반일 수 있습니다. 특히 웹 로그 또는 디바이스에서 제공된 IOT 데이터입니다. 무엇보다, SaaS(Software-as-a-Service) 공급업체로부터 데이터를 제공받을 수 있습니다.

Microsoft에서 내부 시스템의 일부는 원시 파일 형식을 사용하여 ADLS Gen2에 운영 데이터를 출력합니다. 데이터 레이크 이외에 다른 원본 시스템은 관계형 LOB 애플리케이션, Excel 통합 문서, 기타 파일 기반 원본, MDM(마스터 데이터 관리) 및 사용자 지정 데이터 리포지토리를 구성합니다. MDM 리포지토리를 사용하면 마스터 데이터를 관리함으로써 신뢰할 수 있고 유효성이 검사된 표준 데이터 버전을 보장할 수 있습니다.

## <a name="data-ingestion"></a>데이터 수집

정기적으로 그리고 비즈니스의 변화에 따라 데이터는 원본 시스템에서 수집되어 데이터 웨어하우스에 로드됩니다. 주기는 하루 한 번 또는 더 짧은 간격일 수 있습니다. 데이터 수집은 데이터의 추출, 변환 후 로드와 관련되거나 반대로 데이터 추출, 로드 후 변환과 관련됩니다. 이 차이는 변환이 발생하는 위치에 놓여 있습니다. 변환은 데이터 정리, 준수, 통합 및 표준화에 적용됩니다. 자세한 내용은 [ETL(추출, 변환 및 로드)](/azure/architecture/data-guide/relational-data/etl)을 참조하세요.

궁극적으로, 가능한 한 빠르고 효율적으로 올바른 데이터를 엔터프라이즈 모델에 로드하는 것이 목표입니다.

Microsoft에서는 ADF([Azure Data Factory](/azure/data-factory/introduction))를 사용합니다. 서비스는 데이터 유효성 검사, 변환, 외부 원본 시스템에서 데이터 레이크로 대량 로드를 예약하고 오케스트레이션하는 데 사용됩니다. 병렬 및 대규모로 데이터를 처리하기 위해 사용자 지정 프레임워크에서 관리됩니다. 또한 문제 해결, 성능 모니터링을 지원하고 특정 조건 충족 시 경고 알림을 트리거하도록 포괄적인 로깅이 수행됩니다.

[Azure Databricks](/azure/azure-databricks/what-is-azure-databricks)(Azure Cloud Services 플랫폼에 최적화된 Apache Spark 기반 분석 플랫폼)는 특히 데이터 과학을 위해 변환을 수행합니다. 또한 Python Notebook을 사용하여 ML 모델을 빌드하고 실행합니다. 이러한 ML 모델의 점수는 데이터 웨어하우스에 로드되어 예측을 엔터프라이즈 애플리케이션 및 보고서와 통합합니다. Azure Databricks는 데이터 레이크 파일에 직접 액세스하기 때문에 데이터를 복사하거나 가져올 필요가 없어지거나 최소화됩니다.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-ingestion.png" alt-text="이미지는 Azure Data Factory에서 데이터를 제공하고 Azure Data Lake Storage Gen2를 통해 Azure Databricks로 데이터 파이프라인을 오케스트레이션하는 방법을 보여 줍니다.":::

### <a name="ingestion-framework"></a>데이터 수집 프레임워크

**데이터 수집 프레임워크** 를 구성 테이블 및 절차 집합으로 개발했습니다. 최소한의 코드를 사용하고 빠른 속도로 대량의 데이터를 얻는 데이터 기반 접근 방식을 지원합니다. 간단히 말해서 이 프레임워크는 데이터 웨어하우스를 로드하는 데이터 취득 프로세스를 간소화합니다.

이 프레임워크는 데이터 원본 및 데이터 대상 관련 정보(예: 원본 유형, 서버, 데이터베이스, 스키마 및 테이블 관련 세부 정보)를 저장하는 구성 테이블에 의존합니다. 이 디자인 접근 방식을 사용하면 특정 ADF 파이프라인 또는 [SSIS(SQL Server Integration Services)](/sql/integration-services/sql-server-integration-services) 패키지를 개발할 필요가 없습니다. 대신, 선택한 언어로 프로시저가 작성되고 런타임에 동적으로 생성되고 실행되는 ADF 파이프라인을 만듭니다. 따라서 데이터 취득은 쉽게 조작 가능한 구성 연습이 됩니다. 일반적으로 하드 코드된 ADF 또는 SSIS 패키지를 만들려면 광범위한 개발 리소스가 필요합니다.

데이터 수집 프레임워크는 업스트림 원본 스키마 변경을 처리하는 프로세스도 간소화하도록 설계되었습니다. 스키마 변경 사항 검색을 통해 원본 시스템에서 새로 추가된 특성을 획득하는 경우 구성 데이터를 수동이나 자동으로 업데이트하기 쉽습니다.

### <a name="orchestration-framework"></a>오케스트레이션 프레임워크

데이터 파이프라인을 운영하고 오케스트레이션하는 **오케스트레이션 프레임워크** 를 개발했습니다. 이 프레임워크는 구성 테이블 집합에 의존하는 데이터 기반 디자인을 사용합니다. 이러한 테이블은 파이프라인 종속성 및 원본 데이터를 대상 데이터 구조에 매핑하는 방법을 설명하는 메타데이터를 저장합니다. 이 적응형 프레임워크의 개발에 대한 투자는 그 이상의 이점을 가져왔습니다. 각 데이터 이동을 하드 코드해야 하는 요구 사항이 더 이상 적용되지 않습니다.

## <a name="data-storage"></a>데이터 스토리지

데이터 레이크는 나중에 준비 데이터 변환과 함께 사용할 수 있도록 대량의 원시 데이터를 저장할 수 있습니다.

Microsoft에서는 단일 데이터 소스로 ADLS Gen2를 사용합니다. 또한 스테이징된 데이터 및 프로덕션 준비가 된 데이터와 함께 원시 데이터를 저장합니다. 빅 데이터 분석을 위한 확장성이 높고 비용 효과적인 데이터 레이크 솔루션을 제공합니다. 고성능 파일 시스템의 강력한 기능을 대규모로 결합함으로써 데이터 분석 워크로드에 최적화하여 인사이트 시간을 단축할 수 있습니다.

ADLS Gen2는 세분화된 액세스 권한으로 구성되는 Blob Storage 및 고성능 파일 시스템 네임스페이스의 두 가지 이점을 모두 제공합니다.

구체화된 데이터는 관계형 데이터베이스에 저장되어 보안, 거버넌스 및 관리 효율성을 갖추고 엔터프라이즈 모델에 대한 고성능의 확장성이 뛰어난 데이터 저장소를 제공합니다. 주체 관련 데이터 마트는 Azure Synapse Analytics에 저장되며 Azure Databricks 또는 Polybase T-SQL 쿼리에 의해 로드됩니다.

## <a name="data-consumption"></a>데이터 사용

보고 계층에서 비즈니스 서비스는 데이터 웨어하우스에서 제공된 엔터프라이즈 데이터를 사용하며 임시 분석 또는 데이터 과학 작업을 위해 데이터 레이크의 데이터에 직접 액세스합니다.

세분화된 사용 권한은 데이터 레이크, 엔터프라이즈 모델 및 BI 의미 체계 모델의 모든 계층에서 적용됩니다. 사용 권한은 데이터 소비자가 액세스할 권한이 있는 데이터만 볼 수 있게 합니다.

Microsoft에서는 Power BI 보고서 및 대시보드 그리고 [Power BI 페이지를 매긴 보고서](../paginated-reports/paginated-reports-report-builder-power-bi.md)를 사용합니다. 특히 재무 보고를 위한 일부 보고 및 임시 분석은 Excel에서 처리됩니다.

Microsoft는 데이터 모델에 대한 참조 정보를 제공하는 데이터 사전을 게시합니다. 사용자가 BI 플랫폼에 대한 정보를 검색할 수 있도록 이 사전을 사용자에게 제공합니다. 사전은 모델 디자인을 문서화하고 엔터티, 형식, 구조, 데이터 계보, 관계 및 계산에 대한 설명을 제공합니다. [Azure Data Catalog](/azure/data-catalog/overview)를 사용하여 데이터 원본을 쉽게 검색하고 이해할 수 있도록 만듭니다.

일반적으로 데이터 사용 패턴은 역할에 따라 다릅니다.

- **데이터 분석가** 는 핵심 BI 의미 체계 모델에 직접 연결됩니다. 핵심 BI 의미 체계 모델에 필요한 모든 데이터와 논리가 포함되어 있으면 데이터 분석가는 라이브 연결을 사용하여 Power BI 보고서 및 대시보드를 만듭니다. 부서 데이터를 사용하여 모델을 확장해야 하는 경우에는 Power BI [복합 모델](composite-model-guidance.md)을 만듭니다. 스프레드시트 스타일의 보고서가 필요한 경우에는 Excel을 사용하여 핵심 BI 의미 체계 모델 또는 부서 BI 의미 체계 모델을 기반으로 보고서를 생성합니다.
- **BI 개발자** 및 운영 보고서 작성자는 엔터프라이즈 모델에 직접 연결됩니다. Power BI Desktop을 사용하여 라이브 연결 분석 보고서를 만듭니다. 또한 Azure Synapse Analytics 엔터프라이즈 모델에서(T-SQL 사용) 또는 Power BI 의미 체계 모델에서(DAX 또는 MDX 사용) 데이터에 액세스하는 기본 SQL 쿼리를 작성함으로써 운영 형식 BI 보고서를 Power BI 페이지를 매긴 보고서로 작성할 수도 있습니다.
- **데이터 과학자** 는 데이터 레이크의 데이터에 직접 연결됩니다. Azure Databricks 및 Python Notebook을 사용하여 ML 모델을 개발합니다. 이 방법은 종종 실험적이며 프로덕션 사용을 위해서는 전문 기술이 필요합니다.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse-consumption.png" alt-text="Power BI, Excel 및 Azure Machine Learning과 함께 Azure Synapse Analytics 사용을 보여 주는 이미지.":::

## <a name="next-steps"></a>다음 단계

이 문서에 대한 자세한 내용은 다음 리소스를 참조하세요.

- [Azure Synapse Analytics를 사용하는 Azure의 엔터프라이즈 BI](/azure/architecture/reference-architectures/data/enterprise-bi-synapse)
- 궁금한 점이 더 있나요? [Power BI 커뮤니티에 질문합니다.](https://community.powerbi.com/)
- 제안? [Power BI 개선을 위한 아이디어 제공](https://ideas.powerbi.com/)

### <a name="professional-services"></a>전문 서비스

인증된 Power BI 파트너는 조직이 COE를 설정할 때 성공하도록 도와줄 수 있습니다. 비용 효율적인 학습 또는 데이터 감사를 제공할 수 있습니다. Power BI 파트너와 협력하려면 [Power BI 파트너 포털](https://powerbi.microsoft.com/partners/)을 방문하세요.

숙련된 컨설팅 파트너와 협업할 수도 있습니다. 해당 파트너는 Power BI를 [평가](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [고려](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) 또는 [구현](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1)하도록 도와줄 수 있습니다.
