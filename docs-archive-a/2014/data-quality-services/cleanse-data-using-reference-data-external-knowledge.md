---
title: 참조 데이터(외부) 기술 자료를 사용하여 데이터 정리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 158009e9-8069-4741-8085-c14a5518d3fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 107fd3bbf3c6f14e50cb6527400697aab7c7d6a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728740"
---
# <a name="cleanse-data-using-reference-data-external-knowledge"></a><span data-ttu-id="291e4-102">참조 데이터(외부) 기술 자료를 사용하여 데이터 정리</span><span class="sxs-lookup"><span data-stu-id="291e4-102">Cleanse Data Using Reference Data (External) Knowledge</span></span>
  <span data-ttu-id="291e4-103">이 항목에서는 참조 데이터 공급자의 기술 자료를 사용하여 데이터를 정리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-103">This topic describes how to cleanse data using knowledge from the reference data providers.</span></span> <span data-ttu-id="291e4-104">[DQS &#40;내부&#41; 기술 자료를 사용하여 데이터 정리](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)에서 설명한 대로 정리 작업을 실행하는 모든 단계는 참조 데이터 공급자의 기술 자료를 사용하여 데이터를 정리하는 경우와 같지만 이 항목에서는 DQS([!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)])에서 참조 데이터 서비스를 사용하여 데이터를 정리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-104">While all the steps of running a cleansing activity remains the same for cleansing your data using knowledge from the reference data providers as explained in the [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md), this topic provides information specific to data cleansing using reference data service in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>

 <span data-ttu-id="291e4-105">DQS의 참조 데이터 서비스 기능을 사용하여 데이터를 정리하는 경우 DQS 정리 프로세스에서는 매핑된 도메인 값을 참조 데이터 서비스 공급자에게 일괄 처리 요청으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-105">When you use the reference data service feature in DQS to cleanse your data, the DQS cleansing process sends the mapped domain values to the reference data service provider as a batch request.</span></span> <span data-ttu-id="291e4-106">참조 데이터 서비스는 다음과 같은 정보로 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-106">The reference data service responds with the following information:</span></span>

-   <span data-ttu-id="291e4-107">제안된 수정</span><span class="sxs-lookup"><span data-stu-id="291e4-107">Suggested correction</span></span>

-   <span data-ttu-id="291e4-108">신뢰도</span><span class="sxs-lookup"><span data-stu-id="291e4-108">Confidence</span></span>

-   <span data-ttu-id="291e4-109">매핑된 도메인에 대한 추가 정보</span><span class="sxs-lookup"><span data-stu-id="291e4-109">Additional information about the mapped domain.</span></span> <span data-ttu-id="291e4-110">참조 데이터는 추가 데이터로 원본을 표준화, 구문 분석 또는 보강할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-110">Reference data can also standardize, parse, or enrich the source with additional data.</span></span> <span data-ttu-id="291e4-111">이 정보는 응답의 추가 필드에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-111">This information is provided in additional fields in the response.</span></span>

 <span data-ttu-id="291e4-112">참조 데이터 서비스에서 응답을 받은 후 정리 작업 도중 DQS에서는 다음과 같은 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-112">After getting the response from reference data service, the following happens in DQS during the cleansing activity:</span></span>

-   <span data-ttu-id="291e4-113">도메인을 참조 데이터 서비스와 매핑하는 동안 지정한 **자동 수정 임계값** 및 **최소 신뢰도** 값을 기반으로 신뢰도 수준에 따라 도메인 값이 자동으로 수정되거나 제안됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-113">Based on the **Auto Correction Threshold** and **Min Confidence** values specified during mapping of the domains with reference data service, domain values are automatically corrected or suggested based on the confidence level.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="291e4-114">참조 데이터 서비스에서 기술 자료를 사용하여 데이터를 정리하는 동안 도메인을 참조 데이터 서비스에 매핑하는 도중 지정한 임계값이 적용되며 **구성** 섹션의 **일반 설정** 탭에서 지정한 임계값은 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-114">The threshold values that you specify during mapping a domain to a reference data service are applied while cleansing data using the knowledge in reference data service, and not the ones that are specified in the **General Settings** tab in the **Configuration** section.</span></span> <span data-ttu-id="291e4-115">참조 데이터 정리에 대 한 임계값을 지정 하는 방법에 대 한 자세한 내용은 [참조 데이터에 도메인 또는 복합 도메인 연결](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)의 9 단계를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="291e4-115">For information about specifying threshold values for reference data cleansing, see step 9 in [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>

-   <span data-ttu-id="291e4-116">도메인 값은 **제안**, **새로 만들기**, **잘못 됨**, **수정됨**및 **수정**으로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-116">Domain values are categorized into the following: **Suggested**, **New**, **Invalid**, **Corrected**, and **Correct**.</span></span>

-   <span data-ttu-id="291e4-117">추가 데이터가 원본에 연결되고 정보를 정리된 데이터와 함께 내보내기에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-117">Additional data is appended to the source, and the information is available along with the cleansed data for exporting.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="291e4-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="291e4-118">Before You Begin</span></span>

###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="291e4-119">필수 조건</span><span class="sxs-lookup"><span data-stu-id="291e4-119">Prerequisites</span></span>
 <span data-ttu-id="291e4-120">DQS 기술 자료의 필수 도메인이 알맞은 참조 데이터 서비스에 매핑되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-120">You must have mapped required domains in a DQS knowledge base to the appropriate reference data service.</span></span> <span data-ttu-id="291e4-121">또한 정리할 데이터 유형에 대한 정보가 기술 자료에 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-121">Additionally, the knowledge base must contain knowledge about the type of data that you want to cleanse.</span></span> <span data-ttu-id="291e4-122">예를 들어 미국 주소가 포함된 원본 데이터를 정리하려면 미국 주소의 "고품질" 데이터를 제공하는 참조 데이터 서비스 공급자로 도메인을 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-122">For example, if you want to cleanse your source data that contains US addresses, you must map your domains to a reference data service provider that provides high-quality" data for US addresses.</span></span> <span data-ttu-id="291e4-123">자세한 내용은 [참조 데이터에 도메인 또는 복합 도메인 연결](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="291e4-123">For more information, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>

###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="291e4-124">보안</span><span class="sxs-lookup"><span data-stu-id="291e4-124">Security</span></span>

####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="291e4-125">권한</span><span class="sxs-lookup"><span data-stu-id="291e4-125">Permissions</span></span>
 <span data-ttu-id="291e4-126">데이터 정리를 수행하려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_kb_operator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-126">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to perform data cleansing.</span></span>

##  <a name="cleanse-your-data-using-reference-data-knowledge"></a><a name="Cleanse"></a> <span data-ttu-id="291e4-127">참조 데이터 기술 자료를 사용하여 데이터 정리</span><span class="sxs-lookup"><span data-stu-id="291e4-127">Cleanse Your Data Using Reference Data Knowledge</span></span>
 <span data-ttu-id="291e4-128">이전 항목에서 매핑한 도메인을 사용 하는 것과 동일한 예제를 사용 하 여 [참조 데이터에 도메인 또는 복합 도메인을 연결](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)하 고 Melissa 데이터 서비스를 사용 하 여 Azure Marketplace 합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-128">We will continue with the same example of using the domains that we mapped in the previous topic, [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md), with the Melissa Data service in Azure Marketplace.</span></span> <span data-ttu-id="291e4-129">이제 같은 도메인을 사용하여 샘플 US 주소 몇 개를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-129">Now, we will use the same domains to cleanse some sample US addresses.</span></span> <span data-ttu-id="291e4-130">데이터를 정리하는 단계는 [DQS&#40;내부&#41; 기술 자료를 사용하여 데이터 정리](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)에 설명된 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-130">The steps to cleanse data are the same as described in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).</span></span> <span data-ttu-id="291e4-131">그러나 프로세스를 진행하는 동안 필요할 때마다 다시 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-131">However, we will draw you attention wherever necessary during the process.</span></span>

1.  <span data-ttu-id="291e4-132">데이터 품질 프로젝트를 만들고 **정리** 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-132">Create a data quality project, and select the **Cleansing** activity.</span></span> <span data-ttu-id="291e4-133">[Create a Data Quality Project](../../2014/data-quality-services/create-a-data-quality-project.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="291e4-133">See [Create a Data Quality Project](../../2014/data-quality-services/create-a-data-quality-project.md).</span></span>

2.  <span data-ttu-id="291e4-134">**맵** 페이지에서 **Address Line**, **City**, **State**및 **Zip**도메인을 원본 데이터의 알맞은 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-134">On the **Map** page, map the following 4 domains with appropriate columns in your source data: **Address Line**, **City**, **State**, and **Zip**.</span></span> <span data-ttu-id="291e4-135">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-135">Click **Next**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="291e4-136">**Address Verification** 복합 도메인에 있는 도메인 4개를 모두 매핑하면 이제 개별 도메인 수준이 아닌 복합 도메인 수준에서 데이터 정리가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-136">As you have mapped all the 4 domains within the **Address Verification** composite domain, the data cleansing will now be done at the composite domain level, and not at the individual domain level.</span></span>

3.  <span data-ttu-id="291e4-137">**정리** 페이지에서 **시작**을 클릭하여 컴퓨터 기반 정리 프로세스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-137">On the **Cleanse** page, run the computer-assisted cleansing process by clicking **Start**.</span></span> <span data-ttu-id="291e4-138">정리 프로세스가 끝난 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-138">After the cleansing process is over, click **Next**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="291e4-139">**정리** 페이지에 다음 두 가지 방법으로 참조 데이터 서비스에 연결된 도메인에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-139">On the **Cleanse** page, DQS displays information about the domains that are attached to reference data service in the following two ways:</span></span>
    > 
    >  -   <span data-ttu-id="291e4-140">**시작** 단추 아래에 메시지가 표시 됩니다. "도메인 \<Domain1> , \<Domain2> ,... \<DomainN> 참조 데이터 서비스 공급자를 사용 하 여 정리 됩니다. "</span><span class="sxs-lookup"><span data-stu-id="291e4-140">A message is displayed below the **Start** button: "Domains \<Domain1>, \<Domain2>,... \<DomainN> are cleansed using reference data service provider."</span></span> <span data-ttu-id="291e4-141">이 예에서는 다음 메시지가 표시됩니다. “Address Verification 도메인이 참조 데이터 서비스 공급자를 사용하여 정리됩니다.”</span><span class="sxs-lookup"><span data-stu-id="291e4-141">In this example, the following message will be displayed: "Domain Address Verification is cleansed using reference data service provider."</span></span>
    > -   <span data-ttu-id="291e4-142">![도메인이 RDS에 연결 됨](../../2014/data-quality-services/media/dqs-rdsindicator.JPG "도메인이 RDS에 연결됨")아이콘이 **프로파일러** 영역에 참조 데이터 서비스 공급자에 연결 된 도메인에 대해 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-142">An icon, ![Domain is attached to RDS](../../2014/data-quality-services/media/dqs-rdsindicator.JPG "Domain is attached to RDS"), is displayed in the **Profiler** area against the domains attached to reference data service provider.</span></span> <span data-ttu-id="291e4-143">이 예에서는 **Address Verification** 복합 도메인에 대해 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-143">In this example, the icon will be displayed against the **Address Verification** composite domain.</span></span>

4.  <span data-ttu-id="291e4-144">**결과 관리 및 보기** 페이지에서 도메인 값을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-144">On the **Manage and view results** page, review your domain values.</span></span> <span data-ttu-id="291e4-145">참조 데이터 서비스는 도메인이 참조 데이터 서비스에 매핑되는 동안 **제안된 후보** 상자에 지정된 최대 제안 수에 따라 둘 이상의 제안을 값에 대해 표시할 수 있습니다(사용 가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="291e4-145">The reference data service can display more than one suggestion, if available, for a value depending upon the maximum number of suggestions specified in the **Suggested Candidates** box during the mapping of the domain to the reference data service.</span></span> <span data-ttu-id="291e4-146">예를 들어, 다음 미국 주소에는 두 가지 제안이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-146">For example, two suggestions are displayed for the following US address:</span></span>

     <span data-ttu-id="291e4-147">**원래 값:**</span><span class="sxs-lookup"><span data-stu-id="291e4-147">**Original value:**</span></span>

    |<span data-ttu-id="291e4-148">Address Line</span><span class="sxs-lookup"><span data-stu-id="291e4-148">Address Line</span></span>|<span data-ttu-id="291e4-149">도시</span><span class="sxs-lookup"><span data-stu-id="291e4-149">City</span></span>|<span data-ttu-id="291e4-150">주</span><span class="sxs-lookup"><span data-stu-id="291e4-150">State</span></span>|<span data-ttu-id="291e4-151">Zip</span><span class="sxs-lookup"><span data-stu-id="291e4-151">Zip</span></span>|
    |------------------|----------|-----------|---------|
    |<span data-ttu-id="291e4-152">1 msft way</span><span class="sxs-lookup"><span data-stu-id="291e4-152">1 msft way</span></span>|<span data-ttu-id="291e4-153">Redmond</span><span class="sxs-lookup"><span data-stu-id="291e4-153">Redmond</span></span>||<span data-ttu-id="291e4-154">98052</span><span class="sxs-lookup"><span data-stu-id="291e4-154">98052</span></span>|

     <span data-ttu-id="291e4-155">**제안 된 값:**</span><span class="sxs-lookup"><span data-stu-id="291e4-155">**Suggested values:**</span></span>

    |<span data-ttu-id="291e4-156">Address Line</span><span class="sxs-lookup"><span data-stu-id="291e4-156">Address Line</span></span>|<span data-ttu-id="291e4-157">도시</span><span class="sxs-lookup"><span data-stu-id="291e4-157">City</span></span>|<span data-ttu-id="291e4-158">주</span><span class="sxs-lookup"><span data-stu-id="291e4-158">State</span></span>|<span data-ttu-id="291e4-159">Zip</span><span class="sxs-lookup"><span data-stu-id="291e4-159">Zip</span></span>|
    |------------------|----------|-----------|---------|
    |<span data-ttu-id="291e4-160">1 Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="291e4-160">1 Microsoft Way</span></span>|<span data-ttu-id="291e4-161">Redmond</span><span class="sxs-lookup"><span data-stu-id="291e4-161">Redmond</span></span>|<span data-ttu-id="291e4-162">WA</span><span class="sxs-lookup"><span data-stu-id="291e4-162">WA</span></span>|<span data-ttu-id="291e4-163">98052</span><span class="sxs-lookup"><span data-stu-id="291e4-163">98052</span></span>|
    |<span data-ttu-id="291e4-164">PO Box 1</span><span class="sxs-lookup"><span data-stu-id="291e4-164">PO Box 1</span></span>|<span data-ttu-id="291e4-165">Redmond</span><span class="sxs-lookup"><span data-stu-id="291e4-165">Redmond</span></span>|<span data-ttu-id="291e4-166">WA</span><span class="sxs-lookup"><span data-stu-id="291e4-166">WA</span></span>|<span data-ttu-id="291e4-167">98073</span><span class="sxs-lookup"><span data-stu-id="291e4-167">98073</span></span>|

     <span data-ttu-id="291e4-168">![참조 데이터 서비스를 사용하여 정리](../../2014/data-quality-services/media/dqs-rdscleansing.JPG "참조 데이터 서비스를 사용하여 정리")</span><span class="sxs-lookup"><span data-stu-id="291e4-168">![Cleansing using reference data service](../../2014/data-quality-services/media/dqs-rdscleansing.JPG "Cleansing using reference data service")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="291e4-169">복합 도메인의 경우 컴퓨터 기반 정리 프로세스 도중 수정한 개별 도메인이 다른 색으로 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-169">For composite domains, DQS also highlights the individual domains in a different color that were corrected during the computer-assisted cleansing process.</span></span> <span data-ttu-id="291e4-170">예를 들어 이 경우에는 **Address Line** 및 **State** 도메인이 수정되었으므로 녹청으로 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-170">For example, in this case, the **Address Line** and **State** domains were corrected, and therefore highlighted in cyan.</span></span>

5.  <span data-ttu-id="291e4-171">모든 도메인 값을 검토한 후 **다음** 을 클릭하여 데이터를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-171">After you are done with reviewing all the domain values, click **Next** to export the data.</span></span>

6.  <span data-ttu-id="291e4-172">**내보내기** 페이지에는 각 도메인의 정리 작업에 대한 원본, 이유, 신뢰도 및 상태의 일반 정보 외에, Melissa Data 참조 데이터 서비스가 주소 데이터에 대해 제공하는 주소, 위도와 경도, 지방 이름, 주소 유형(건물, 거리 등) 등의 추가 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-172">On the **Export** page, you will notice that apart from the regular information about the cleansing activity for each domain (Source, Reason, Confidence, and Status), there is additional information provided by the Melissa Data reference data service about your address data, such as latitude and longitude of your address, county name, address type (highrise, street, etc.), and so on.</span></span>

7.  <span data-ttu-id="291e4-173">데이터를 필요한 대상(SQL Server, CSV 또는 Excel)으로 내보내고 **마침** 을 클릭하여 프로젝트를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-173">Export your data to the required destination (SQL Server, CSV, or Excel), and click **Finish** to close the project.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="291e4-174">64비트 버전의 Excel을 사용 중인 경우 정리한 데이터를 Excel 파일로 내보낼 수 없습니다. SQL Server 데이터베이스 또는 .csv 파일로만 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291e4-174">If you are using 64-bit version of Excel, you cannot export the cleansed data to an Excel file; you can export only to a SQL Server database or to a .csv file.</span></span>


