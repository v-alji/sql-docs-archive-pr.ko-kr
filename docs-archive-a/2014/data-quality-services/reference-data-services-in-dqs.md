---
title: DQS의 참조 데이터 서비스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ef217717-6d05-443e-af26-44dc745a349d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4ed286b5834d81f775ee097672bfbc861c0b369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651285"
---
# <a name="reference-data-services-in-dqs"></a><span data-ttu-id="dceab-102">DQS의 참조 데이터 서비스</span><span class="sxs-lookup"><span data-stu-id="dceab-102">Reference Data Services in DQS</span></span>
  <span data-ttu-id="dceab-103">참조 데이터는 신뢰할 수 있는 공용 도메인에서 또는 고급 상용 콘텐츠 공급자를 통해 사용할 수 있는 관련 또는 분류된 전역 데이터(엔터프라이즈의 경계를 벗어남)의 정확하고 완전한 집합을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-103">Reference data refers to an accurate and complete set of related or categorized global data (beyond the boundaries of an enterprise) that is available at trusted public domains or from premium commercial content providers.</span></span>  
  
 <span data-ttu-id="dceab-104">DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )의 참조 데이터 서비스 기능을 사용하여 타사 참조 데이터 공급자를 구독하고 고품질 데이터를 기준으로 비즈니스 데이터의 유효성을 검사하여 비즈니스 데이터를 쉽게 정리하고 보강할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-104">The Reference Data Service feature in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) enables you to subscribe to third-party reference data providers, and to easily cleanse and enrich your business data by validating it against their high-quality data.</span></span> <span data-ttu-id="dceab-105">정리 프로세스가 진행되는 동안 Data Quality Services 내에서 업계 선두 데이터 품질 서비스 공급업체의 서비스를 사용하여 데이터 표준화, 수정 또는 보강을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-105">You can use services from leading data quality service providers from within DQS to standardize, correct, or enrich your data during the cleansing process.</span></span> <span data-ttu-id="dceab-106">예를 들어 지역 번호 또는 우편 번호 목록을 사용하여 참조 데이터를 기준으로 고객 주소의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-106">For example, you can use a list of area codes or zip codes against the reference data to validate addresses of your customers.</span></span>  
  
 <span data-ttu-id="dceab-107">참조 데이터 서비스 기능에는 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-107">The Reference Data Service feature has the following benefits:</span></span>  
  
-   <span data-ttu-id="dceab-108">참조 데이터를 사용하면 타사 회사에서 보증하는 데이터에 비교하여 자신의 데이터 품질을 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-108">Reference data enables you to ensure the quality of your data by comparing it to data guaranteed by a third-party company.</span></span>  
  
-   <span data-ttu-id="dceab-109">DQS 기술 자료 구축 및 데이터 품질 프로젝트에 참조 데이터 프로세스가 통합되어 있으므로 포괄적인 데이터 품질 프로세스를 도입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-109">The reference data process is incorporated into DQS knowledge base building and a data quality project, enabling you to institute a comprehensive data quality process.</span></span>  
  
-   <span data-ttu-id="dceab-110">에서는 Azure Marketplace 및 타사 참조 데이터 공급자에서 직접 참조 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-110">Supports using reference data from Azure Marketplace as well as directly from third party reference data providers.</span></span>  
  
##  <a name="using-reference-data-from-azure-marketplace"></a><a name="Marketplace"></a><span data-ttu-id="dceab-111">Azure Marketplace의 참조 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="dceab-111">Using Reference Data from Azure Marketplace</span></span>  
 <span data-ttu-id="dceab-112">DQS는 Azure Marketplace의 참조 데이터를 사용 하 여 콘텐츠 공급자가 Marketplace를 통해 참조 데이터 서비스를 제공할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-112">DQS supports using reference data from Azure Marketplace to enable content providers to provide reference data services through Marketplace.</span></span> <span data-ttu-id="dceab-113">Marketplace는 단일 마켓플레이스와 고품질 데이터 및 애플리케이션 배달 채널을 클라우드 서비스로 제공하는 Microsoft의 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-113">Marketplace is a service from Microsoft that provides a single marketplace and delivery channel for high-quality data and applications as cloud services.</span></span> <span data-ttu-id="dceab-114">Marketplace에 대 한 자세한 내용은 [Azure Marketplace에 대해 알아보기](https://azuremarketplace.microsoft.com/marketplace/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dceab-114">For more information about Marketplace, see [Learn About Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/).</span></span>  
  
 <span data-ttu-id="dceab-115">Marketplace와 DQS 간의 원활한 통합은 DQS 내 데이터 품질 프로젝트에 대한 정보 검색, 탐색 및 가져오기와 관련된 단계를 간소화합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-115">The seamless integration between Marketplace and DQS simplifies the steps associated with discovering, exploring, and acquiring information for data quality projects from within DQS.</span></span> <span data-ttu-id="dceab-116">DQS에서 데이터를 가져올 수 있으므로 DQS 사용자는 DQS, Marketplace 및 참조 데이터 서비스 공급자를 혁신적인 방식으로 결합하여 고품질 데이터를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-116">The data is consumed from DQS, and helps DQS users achieve high data quality by bringing together DQS, Marketplace, and reference data service providers in an innovative way.</span></span>  
  
 <span data-ttu-id="dceab-117">DQS에서 Marketplace의 참조 데이터를 정리 작업에 사용하려면 유효한 Marketplace 계정 키가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-117">To use reference data from Marketplace in DQS for the cleansing activity, you must have a Marketplace account key.</span></span> <span data-ttu-id="dceab-118">Marketplace 계정 키를 만드는 것은 무료이며 유료 데이터 세트를 구독하는 경우에만 요금이 청구됩니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-118">Creating a Marketplace account key is free, and you pay only if you subscribe to paid datasets.</span></span> <span data-ttu-id="dceab-119">무료 데이터 세트를 구독하고 사용하는 경우에는 요금이 청구되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-119">There is no charge for subscribing to, and using free datasets.</span></span> <span data-ttu-id="dceab-120">Marketplace 계정 키를 만드는 방법에 대 한 자세한 내용은 [계정 만들기](https://go.microsoft.com/fwlink/?LinkId=212936) ()를 참조 하세요 https://go.microsoft.com/fwlink/?LinkId=212936) .</span><span class="sxs-lookup"><span data-stu-id="dceab-120">For detailed information about creating a Marketplace account key, see [Create Your Account](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936).</span></span>  
  
 <span data-ttu-id="dceab-121">또한 DQS 내에서 다음과 같은 Marketplace 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-121">Additionally, you can perform the following Marketplace activities from within DQS:</span></span>  
  
-   <span data-ttu-id="dceab-122">Marketplace에서 데이터 집합을 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-122">Browse data sets in Marketplace.</span></span>  
  
-   <span data-ttu-id="dceab-123">Marketplace 계정 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-123">Create a Marketplace account key.</span></span>  
  
-   <span data-ttu-id="dceab-124">계정 키 및 데이터 공급자 구독과 같은 Marketplace 계정 세부 사항을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-124">Manage your Marketplace account details such as account keys and subscriptions to data providers.</span></span>  
  
 <span data-ttu-id="dceab-125">**에 있는** 구성 **화면의** 참조 데이터 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]탭에서 이러한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-125">You can perform these activities in the **Reference Data** tab of the **Configuration** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
##  <a name="using-reference-data-directly-from-the-third-party-reference-data-providers"></a><a name="Direct"></a> <span data-ttu-id="dceab-126">타사 참조 데이터 공급자를 통해 직접 참조 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="dceab-126">Using Reference Data Directly from the Third Party Reference Data Providers</span></span>  
 <span data-ttu-id="dceab-127">인터넷에 연결되어 있지 않아서 Marketplace를 사용할 수 없는 경우 DQS는 조직의 네트워크 내에 있는 데이터 공급자에 직접 연결할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-127">If you are not connected to the Internet and therefore cannot use Marketplace, DQS also supports direct connection to data providers that are available within your organization's network.</span></span> <span data-ttu-id="dceab-128">다이렉트 온라인 타사 참조 데이터 공급자의 참조 데이터를 사용하려면 DQS에서 해당 데이터 공급자에 대한 레코드를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-128">To use reference data from direct online third-party reference data providers, you have to create a record for the data provider in DQS.</span></span>  
  
##  <a name="how-to-cleanse-data-by-using-the-reference-data"></a><a name="HowToCleanse"></a> <span data-ttu-id="dceab-129">참조 데이터를 사용하여 데이터를 정리하는 방법</span><span class="sxs-lookup"><span data-stu-id="dceab-129">How to Cleanse Data by Using the Reference Data</span></span>  
 <span data-ttu-id="dceab-130">참조 데이터를 사용하여 DQS의 데이터를 정리하기 위한 3단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-130">Cleansing your data in DQS using reference data includes the following three steps:</span></span>  
  
1.  <span data-ttu-id="dceab-131">**DQS에서 참조 데이터 공급자 세부 정보 구성**: DQS에서 참조 데이터를 사용하려면 DQS에서 참조 데이터 서비스 세부 정보를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-131">**Configuring the reference data provider details in DQS**: Before you can use reference data in DQS, you must configure reference data service details in DQS.</span></span>  
  
    1.  <span data-ttu-id="dceab-132">Marketplace를 사용하는 경우 유효한 Marketplace 계정 키를 제공하고 Marketplace의 [Data Quality Services](../data-quality-services/data-quality-services.md) 데이터 범주로 이동한 후 필요한 공급자를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-132">If you are using Marketplace, provide a valid Marketplace account key, browse to the [Data Quality Services](../data-quality-services/data-quality-services.md) data category in Marketplace, and subscribe to the required providers.</span></span>  
  
    2.  <span data-ttu-id="dceab-133">다이렉트 온라인 참조 데이터 공급자를 사용하는 경우 DQS에서 다이렉트 참조 데이터 공급자 세부 정보를 추가해야 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-133">If you are using a direct online reference data provider, you must add direct reference data provider details in DQS before you can use it.</span></span>  
  
     <span data-ttu-id="dceab-134">DQS에서 참조 데이터 공급자 세부 정보를 구성하는 작업은 특정 데이터 공급자에 대해 한 번만 수행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-134">Configuring the reference data provider details in DQS is one time activity for a particular data provider.</span></span> <span data-ttu-id="dceab-135">DQS 관리자만 DQS에서 참조 데이터 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-135">Only DQS administrators can configure reference data settings in DQS.</span></span>  
  
2.  <span data-ttu-id="dceab-136">**기술 자료의 도메인/복합 도메인을 참조 데이터 서비스에 매핑**: 1단계에서 구독/추가한 적절한 데이터 서비스에 도메인/복합 도메인을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-136">**Map a domain/composite domain in a knowledge base to the reference data service**: Map a domain/composite domain to the appropriate reference data service subscribed/added in step 1.</span></span>  
  
3.  <span data-ttu-id="dceab-137">**데이터 품질 프로젝트의 정리 작업에 매핑된 도메인 사용**: **정리** 작업에 대한 데이터 품질 프로젝트를 만들 때 2단계서 참조 데이터 서비스와 매핑된 도메인/복합 도메인이 포함된 기술 자료를 선택하고 정리 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-137">**Use the Mapped Domains for the Cleansing activity in a data quality project**: While creating a data quality project for the **Cleansing** activity, select the knowledge base that contains domains/composite domains mapped with reference data services in step 2, and perform the cleansing activity.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="dceab-138">관련 작업</span><span class="sxs-lookup"><span data-stu-id="dceab-138">Related Tasks</span></span>  
  
|<span data-ttu-id="dceab-139">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="dceab-139">Task Description</span></span>|<span data-ttu-id="dceab-140">항목</span><span class="sxs-lookup"><span data-stu-id="dceab-140">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="dceab-141">Marketplace 또는 다이렉트 온라인 타사 데이터 공급자의 참조 데이터 서비스를 사용하도록 DQS를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-141">Describes how to configure DQS to use reference data services from Marketplace or direct third-party online data providers.</span></span>|[<span data-ttu-id="dceab-142">참조 데이터를 사용하도록 DQS 구성</span><span class="sxs-lookup"><span data-stu-id="dceab-142">Configure DQS to Use Reference Data</span></span>](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)|  
|<span data-ttu-id="dceab-143">기술 자료의 도메인/복합 도메인을 참조 데이터 서비스에 매핑하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-143">Describes how to map a domain/composite domain in a knowledge base to a reference data service.</span></span>|[<span data-ttu-id="dceab-144">참조 데이터에 도메인 또는 복합 도메인 연결</span><span class="sxs-lookup"><span data-stu-id="dceab-144">Attach a Domain or Composite Domain to Reference Data</span></span>](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|<span data-ttu-id="dceab-145">참조 데이터 서비스를 사용하여 데이터를 정리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dceab-145">Describes how to cleanse data using reference data service.</span></span>|[<span data-ttu-id="dceab-146">참조 데이터&#40;외부&#41; 기술 자료를 사용하여 데이터 정리</span><span class="sxs-lookup"><span data-stu-id="dceab-146">Cleanse Data Using Reference Data &#40;External&#41; Knowledge</span></span>](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)|  
  
  
