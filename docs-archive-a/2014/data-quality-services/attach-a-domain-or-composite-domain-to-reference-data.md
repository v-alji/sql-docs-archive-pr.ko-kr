---
title: 참조 데이터에 도메인 또는 복합 도메인 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.refdata.f1
- sql12.dqs.dm.refcatalog.f1
ms.assetid: 36af981c-d0d0-4dc6-afe5-bbb3c97845dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d54dcb01823253eeda92cc3a576d73a45de4ef7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647271"
---
# <a name="attach-a-domain-or-composite-domain-to-reference-data"></a><span data-ttu-id="08d9f-102">참조 데이터에 도메인 또는 복합 도메인 연결</span><span class="sxs-lookup"><span data-stu-id="08d9f-102">Attach a Domain or Composite Domain to Reference Data</span></span>
  <span data-ttu-id="08d9f-103">이 항목에서는 데이터 품질 기술 자료의 도메인/복합 도메인을 Azure Marketplace의 참조 데이터 서비스에 연결 하 여 고품질 참조 데이터에 대 한 정보를 작성 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-103">This topic describes how to attach domains/composite domains in a data quality knowledge base to a reference data service in Azure Marketplace to build knowledge against the high-quality reference data.</span></span> <span data-ttu-id="08d9f-104">각 참조 데이터 서비스에는 스키마(데이터 열)가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-104">Each reference data service contains a schema (data columns).</span></span> <span data-ttu-id="08d9f-105">도메인 또는 복합 도메인을 참조 데이터 서비스에 연결한 후 연결된 도메인 또는 연결된 복합 도메인 내의 개별 도메인을 참조 데이터 서비스 스키마의 적절한 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-105">After attaching a domain or a composite domain to a reference data service, you must map the attached domain or the individual domains within the attached composite domain to the appropriate columns in a reference data service schema.</span></span> <span data-ttu-id="08d9f-106">복합 도메인을 참조 데이터 서비스에 연결하면 한 도메인만 참조 데이터 서비스에 연결한 다음 복합 도메인 내 개별 도메인을 참조 데이터 서비스 스키마의 적절한 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-106">Attaching a composite domain to a reference data service enables you to attach just one domain to a reference data service, and then map the individual domains within the composite domain to appropriate columns in the reference data service schema.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="08d9f-107">도메인을 참조 데이터 서비스 스키마의 열에 매핑하는 동안 참조 데이터 서비스에 연결된 복합 도메인을 도메인 드롭다운 목록에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-107">The composite domain attached to a reference data service is available in the domains drop-down list while mapping domains to the columns in the reference data service schema.</span></span> <span data-ttu-id="08d9f-108">복합 도메인을 참조 데이터 서비스 스키마의 열에 매핑하지 마세요. 복합 도메인 내의 개별 도메인만 참조 데이터 서비스 스키마의 적절한 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-108">Do not map the composite domain to a column in the reference data service schema; you must only map individual domains within a composite domain to the appropriate columns in the reference data service schema.</span></span> <span data-ttu-id="08d9f-109">그렇지 않으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-109">Otherwise, it will result in an error.</span></span>  
  
 <span data-ttu-id="08d9f-110">참조 데이터 서비스를 사용하도록 선택한 경우 참조 데이터 서비스 스키마에 적절한 도메인과 함께 매핑되어야 하는 필수 열이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-110">A reference data service schema can have a mandatory column that must be mapped with appropriate domain should you choose to use the reference data service.</span></span> <span data-ttu-id="08d9f-111">참조 데이터 스키마의 필수 열은 열 이름에서 "(M)"으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-111">The mandatory column in a reference data schema is identified with "(M)" against the column name.</span></span> <span data-ttu-id="08d9f-112">예를 들어 **AddressLine**은 **Melissa Data – Address Data**의 필수 스키마 열이고 **CompanyName**은 **Digital Trowel Inc. – Us companies and professional data for SQL users**의 필수 스키마 열입니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-112">For example, **AddressLine** is the mandatory schema column in **Melissa Data - Address Data** and **CompanyName** is the mandatory schema column in **Digital Trowel Inc. - Us companies and professional data for SQL users**.</span></span>  
  
 <span data-ttu-id="08d9f-113">이 토픽에서는 복합 도메인 **Address Verification** 아래에 **Address Line**, **City**, **State** 및 **Zip**의 4개 도메인을 만들고, 도메인을 **Melissa Data – Address Check** 참조 데이터 서비스에 연결한 다음, 복합 도메인 내의 개별 도메인을 참조 데이터 서비스 스키마의 적절한 열에 매핑할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-113">In this topic, we will create four domains: **Address Line**, **City**, **State**, and **Zip**, under a composite domain, **Address Verification**, attach the composite domain to the **Melissa Data - Address Check** reference data service, and then map the individual domains within the composite domain to appropriate columns in the reference data service schema.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="08d9f-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="08d9f-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="08d9f-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="08d9f-115">Prerequisites</span></span>  
 <span data-ttu-id="08d9f-116">참조 데이터 서비스를 사용하도록 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )를 구성한 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-116">You must have configured [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) to use reference data services.</span></span> <span data-ttu-id="08d9f-117">[참조 데이터를 사용하도록 DQS 구성](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08d9f-117">See [Configure DQS to Use Reference Data](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="08d9f-118">보안</span><span class="sxs-lookup"><span data-stu-id="08d9f-118">Security</span></span>  
  
#### <a name="permissions"></a><span data-ttu-id="08d9f-119">권한</span><span class="sxs-lookup"><span data-stu-id="08d9f-119">Permissions</span></span>  
 <span data-ttu-id="08d9f-120">참조 데이터에 도메인을 매핑하려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-120">You must have the dqs_kb_editor role on the DQS_MAIN database to map domains to reference data.</span></span>  
  
##  <a name="map-domains-to-reference-data-from-melissa-data"></a><a name="Map"></a><span data-ttu-id="08d9f-121">Melissa 데이터에서 참조 데이터에 도메인 매핑</span><span class="sxs-lookup"><span data-stu-id="08d9f-121">Map domains to reference data from Melissa Data</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="08d9f-122">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-122">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="08d9f-123">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 **기술 자료 관리**에서 **새 기술 자료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-123">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Knowledge Base Management**, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="08d9f-124">**새 기술 자료** 화면에서 새 기술 자료의 이름을 입력하고 **도메인 관리** 작업을 클릭한 후 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-124">In the **New knowledge base** screen, type a name for the new knowledge base, click the **Domain Management** activity, and click **Create**.</span></span>  
  
4.  <span data-ttu-id="08d9f-125">**도메인 관리** 화면에서 **도메인 만들기** 아이콘을 클릭하여 도메인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-125">In the **Domain Management** screen, click the **Create a domain** icon to create a domain.</span></span> <span data-ttu-id="08d9f-126">4개의 도메인 **Address Line**, **City**, **State**및 **Zip**을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-126">Create the following four domains: **Address Line**, **City**, **State**, and **Zip**.</span></span>  
  
5.  <span data-ttu-id="08d9f-127">**복합 도메인 만들기** 아이콘을 클릭하여 복합 도메인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-127">Click the **Create a composite domain** icon to create a composite domain.</span></span> <span data-ttu-id="08d9f-128">**복합 도메인 만들기** 대화 상자에서 **복합 도메인 이름** 입력란에 **Address Verification** 을 입력하고 3단계에서 만든 모든 도메인을 복합 도메인에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-128">In the **Create a composite domain** dialog box, type **Address Verification** in the **Composite Domain Name** box, and include all the domains created in step 3 in the composite domain.</span></span> <span data-ttu-id="08d9f-129">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-129">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="08d9f-130">왼쪽에 있는 **도메인** 창에서 **Address Verification**을 클릭하여 복합 도메인을 선택한 다음 오른쪽에서 **참조 데이터** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-130">In the **Domain** pane on the left side, select the composite domain by clicking **Address Verification**, and then click the **Reference Data** tab on the right side.</span></span>  
  
7.  <span data-ttu-id="08d9f-131">**찾아보기** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-131">Click the **Browse** icon.</span></span>  
  
8.  <span data-ttu-id="08d9f-132">**온라인 참조 데이터 공급자 카탈로그** 대화 상자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-132">In the **Online Reference Data Providers Catalog** dialog box:</span></span>  
  
    1.  <span data-ttu-id="08d9f-133">**DataMarket Data Quality Services**에서 **Melissa Data – Address Check** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-133">Under **DataMarket Data Quality Services**, select the **Melissa Data - Address Check** box.</span></span>  
  
    2.  <span data-ttu-id="08d9f-134">Melissa Data – Address Check 참조 데이터 서비스의 열을 적절한 도메인(Address Line, City, State 및 Zip)과 함께 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-134">Map the columns of the Melissa Data - Address Check reference data service with the appropriate domains (Address Line, City, State, and Zip).</span></span> <span data-ttu-id="08d9f-135">**RDS 스키마** 열에서 참조 데이터 서비스 열을 선택한 다음 **도메인** 열에서 적절한 도메인을 선택하여 열을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-135">You map the columns by selecting a reference data service column in the **RDS Schema** column, and then selecting the appropriate domain in the **Domain** column.</span></span> <span data-ttu-id="08d9f-136">테이블에 더 많은 행을 추가하려면 **스키마 항목 추가** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-136">To add more rows in the table, click the **Add Schema Entry** icon.</span></span>  
  
    3.  <span data-ttu-id="08d9f-137">**확인** 을 클릭하여 변경 내용을 저장하고 **온라인 참조 데이터 공급자 카탈로그** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-137">Click **OK** to save the changes, and close the **Online Reference Data Providers Catalog** dialog box.</span></span>  
  
         <span data-ttu-id="08d9f-138">![온라인 참조 데이터 공급자 카탈로그 대화 상자](../../2014/data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "온라인 참조 데이터 공급자 카탈로그 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="08d9f-138">![Online Reference Data Providers Catalog dialog box](../../2014/data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "Online Reference Data Providers Catalog dialog box")</span></span>  
  
        > [!NOTE]  
        >  -   <span data-ttu-id="08d9f-139">**온라인 참조 데이터 공급자 카탈로그** 대화 상자에서 **DataMarket data Quality Services** 노드는 Azure Marketplace에서 구독 한 모든 참조 데이터 서비스 공급자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-139">In the **Online Reference Data Providers Catalog** dialog box, the **DataMarket Data Quality Services** node displays all the reference data service providers that you have subscribed to in Azure Marketplace.</span></span> <span data-ttu-id="08d9f-140">DQS에서 다이렉트 온라인 타사 참조 데이터 서비스 공급자를 구성한 경우 **타사 Direct Online 공급자** 라는 노드 아래에 해당 공급자가 표시됩니다(지금은 DQS에 다이렉트 온라인 타사 참조 데이터 서비스 공급자가 구성되어 있지 않으므로 사용할 수 없음).</span><span class="sxs-lookup"><span data-stu-id="08d9f-140">If you have configured direct online third-party reference data service providers in DQS, they will appear under another node called **3rd Party Direct Online Providers** (not available now as no direct online third-party reference data service providers are configured in DQS).</span></span>  
  
9. <span data-ttu-id="08d9f-141">**참조 데이터** 탭으로 돌아갑니다. 필요한 경우 **공급자 설정** 영역에서 다음 상자의 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-141">You will return to the **Reference Data** tab. In the **Provider Settings** area, change values in the following boxes, if required:</span></span>  
  
    -   <span data-ttu-id="08d9f-142">**자동 수정 임계값**: 신뢰도 수준이 이 임계값보다 높은 참조 데이터 서비스의 수정 사항이 자동으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-142">**Auto Correction Threshold**: Corrections from reference data service with confidence level above this threshold values will be automatically done.</span></span> <span data-ttu-id="08d9f-143">해당 백분율 값의 10진수 표기법으로 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-143">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="08d9f-144">예를 들어 90%의 경우 0.9를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-144">For example, enter 0.9 for 90%.</span></span>  
  
    -   <span data-ttu-id="08d9f-145">**제안된 후보**: 참조 데이터 서비스에서 표시할 제안된 후보의 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-145">**Suggested Candidates**: Number of suggested candidates to display from the reference data service.</span></span>  
  
    -   <span data-ttu-id="08d9f-146">**최소 신뢰도**: 신뢰도 수준이 이 값보다 낮은 참조 데이터 서비스의 제안은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-146">**Min Confidence**: Suggestions from reference data service with confidence level lower than this value will be ignored.</span></span> <span data-ttu-id="08d9f-147">해당 백분율 값의 10진수 표기법으로 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-147">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="08d9f-148">예를 들어 60%의 경우 0.6을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-148">For example, enter 0.6 for 60%.</span></span>  
  
10. <span data-ttu-id="08d9f-149">**마침** 을 클릭하여 기술 자료를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-149">Click **Finish** to publish the knowledge base.</span></span> <span data-ttu-id="08d9f-150">기술 자료가 올바르게 게시되면 확인 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-150">A confirmation message appears after the knowledge base is published successfully.</span></span>  
  
 <span data-ttu-id="08d9f-151">이제 데이터 품질 프로젝트의 정리 작업에이 기술 자료를 사용 하 여 Azure Marketplace 통해 Melissa Data에서 제공 하는 기술 자료를 기반으로 원본 데이터의 미국 주소를 표준화 하 고 정리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-151">You can now use this knowledge base for cleansing activity in a data quality project to standardize and cleanse US addresses in your source data based on the knowledge provided by Melissa Data through Azure Marketplace.</span></span>  
  
##  <a name="follow-up-after-mapping-a-domain-to-reference-data"></a><a name="FollowUp"></a> <span data-ttu-id="08d9f-152">후속 작업: 참조 데이터에 도메인을 매핑한 후</span><span class="sxs-lookup"><span data-stu-id="08d9f-152">Follow Up: After Mapping a Domain to Reference Data</span></span>  
 <span data-ttu-id="08d9f-153">데이터 품질 프로젝트를 만들고 미국 주소가 포함된 원본 데이터를 이 항목에서 만든 기술 자료와 비교하여 정리 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9f-153">Create a data quality project, and run the cleansing activity on your source data containing US addresses by comparing it against the knowledge base created in this topic.</span></span> <span data-ttu-id="08d9f-154">[참조 데이터&#40;외부&#41; 기술 자료를 사용하여 데이터 정리](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08d9f-154">See [Cleanse Data Using Reference Data &#40;External&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d9f-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08d9f-155">See Also</span></span>  
 <span data-ttu-id="08d9f-156">[DQS의 참조 Data Services](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span><span class="sxs-lookup"><span data-stu-id="08d9f-156">[Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span></span>  
 [<span data-ttu-id="08d9f-157">데이터 정리</span><span class="sxs-lookup"><span data-stu-id="08d9f-157">Data Cleansing</span></span>](../../2014/data-quality-services/data-cleansing.md)  
  
  
