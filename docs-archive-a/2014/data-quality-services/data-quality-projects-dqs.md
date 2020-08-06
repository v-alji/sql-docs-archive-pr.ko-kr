---
title: 데이터 품질 프로젝트(DQS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a43fc9c0-19b6-414a-8661-4c7c55e0c03e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 471d528144b6687ffa3aeedb82cf479817c4edc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647863"
---
# <a name="data-quality-projects-dqs"></a><span data-ttu-id="2a077-102">데이터 품질 프로젝트(DQS)</span><span class="sxs-lookup"><span data-stu-id="2a077-102">Data Quality Projects (DQS)</span></span>
  <span data-ttu-id="2a077-103">DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )의 데이터 품질 프로젝트는 기술 자료를 사용하여 *데이터 정리* 및 *데이터 일치* 작업을 수행한 다음 결과 데이터를 SQL Server 데이터베이스 또는 .csv 파일로 내보내 원본 데이터의 품질을 향상시킬 수 있는 수단입니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-103">A data quality project in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) is a means of using a knowledge base to improve the quality of your source data by performing *data cleansing* and *data matching* activities, and then exporting the resultant data to a SQL Server database or a .csv file.</span></span> <span data-ttu-id="2a077-104">데이터 품질 프로젝트를 정리 프로젝트 또는 일치 프로젝트로 만들어 각 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-104">You can create a data quality project as a cleansing project or a matching project to perform respective activities.</span></span> <span data-ttu-id="2a077-105">데이터 정리 및 일치에 대한 정보는 같은 기술 자료에 기본 제공될 수 있으므로 같은 기술 자료를 사용하여 정리 및 일치 프로젝트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-105">Cleansing and matching projects can be run using the same knowledge base, because knowledge for data cleansing and matching can be built into the same knowledge base.</span></span>  
  
 <span data-ttu-id="2a077-106">데이터 품질 프로젝트에는 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-106">A data quality project has the following benefits:</span></span>  
  
-   <span data-ttu-id="2a077-107">DQS 기술 자료의 정보를 사용하여 원본 데이터에 대해 데이터 정리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-107">Enables you to perform data cleansing on your source data by using the knowledge in a DQS knowledge base.</span></span>  
  
-   <span data-ttu-id="2a077-108">기술 자료의 일치 정책을 사용하여 원본 데이터에 대해 데이터 일치를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-108">Enables you to perform data matching on your source data by using the matching policy in a knowledge base.</span></span>  
  
-   <span data-ttu-id="2a077-109">정리 및 일치 작업을 안내하고 선택 항목에 따라 SQL Server 데이터베이스 또는 .csv 파일로 데이터를 내보내는 마법사를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-109">Provides a wizard to guide you through the cleansing and matching activities, and export the data as per your selection to a SQL Server database or to a .csv file.</span></span> <span data-ttu-id="2a077-110">데이터 관리자는 데이터 품질 프로젝트를 사용하여 컴퓨터 기반/대화형 정리 및 데이터 일치 단계를 실행하고 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-110">The data steward can use the data quality project to run and control the computer-assisted/interactive cleansing and data matching steps.</span></span>  
  
##  <a name="data-quality-project-cleansing-activity"></a><a name="Cleansing"></a> <span data-ttu-id="2a077-111">데이터 품질 프로젝트: 정리 작업</span><span class="sxs-lookup"><span data-stu-id="2a077-111">Data Quality Project: Cleansing Activity</span></span>  
 <span data-ttu-id="2a077-112">정리 데이터 품질 프로젝트를 사용하여 기술 자료에 따라 원본 데이터를 정리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-112">A cleansing data quality project enables you to cleanse your source data based on a knowledge base.</span></span> <span data-ttu-id="2a077-113">DQS의 데이터 정리 작업은 2단계 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-113">The data cleansing activity in DQS is a two-step process:</span></span>  
  
1.  <span data-ttu-id="2a077-114">*컴퓨터 기반* 데이터 정리 프로세스는 기술 자료의 정보에 대해 원본 데이터를 분석하고 변경 내용을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-114">A *computer-assisted* data cleansing process that analyzes source data against the knowledge in the knowledge base, and proposes changes.</span></span> <span data-ttu-id="2a077-115">처리된 데이터는 DQS에 의해 분류(제안, 새로 만들기, 잘못됨, 수정됨 및 올바름)되어 추가로 처리할 수 있도록 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-115">The processed data is categorized (suggested, new, invalid, corrected, and correct) by DQS, and displayed to the user for further processing.</span></span>  
  
2.  <span data-ttu-id="2a077-116">*대화형* 정리 프로세스에서는 데이터 관리자가 컴퓨터 기반 데이터 정리 프로세스에서 제안된 데이터를 승인, 거부 또는 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-116">An *interactive* cleansing process that enables the data steward to approve, reject, or modify the data proposed by the computer-assisted data cleansing process.</span></span>  
  
 <span data-ttu-id="2a077-117">데이터 품질 프로젝트의 정리 작업에 대한 자세한 내용은 [Data Cleansing](../../2014/data-quality-services/data-cleansing.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a077-117">For detailed information about the cleansing activity in a data quality project, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
##  <a name="data-quality-project-matching-activity"></a><a name="Matching"></a> <span data-ttu-id="2a077-118">데이터 품질 프로젝트: 일치 작업</span><span class="sxs-lookup"><span data-stu-id="2a077-118">Data Quality Project: Matching Activity</span></span>  
 <span data-ttu-id="2a077-119">일치 데이터 품질 프로젝트를 사용하면 정확한 수치 및 근사치 일치를 확인하고 이를 통해 중복 데이터를 제거하는 방식으로 기술 자료의 일치 정책에 따라 일치 작업을 수행하여 데이터 중복을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-119">A matching data quality project enables you to perform matching activity based on matching policy in a knowledge base to prevent data duplication by identifying exact and approximate matches, and thereby enabling you to remove duplicate data.</span></span> <span data-ttu-id="2a077-120">따라서 일치를 실행하기 전에 데이터를 정리하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-120">It is recommended that you cleanse your data before running matching on it.</span></span> <span data-ttu-id="2a077-121">이렇게 하려면</span><span class="sxs-lookup"><span data-stu-id="2a077-121">To do so:</span></span>  
  
1.  <span data-ttu-id="2a077-122">데이터 품질 프로젝트를 만들고 **정리** 작업을 선택한 다음 원본 데이터에 대해 데이터 정리 작업을 완료하고 SQL Server 데이터베이스의 테이블로 데이터를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-122">Create a data quality project, select the **Cleansing** activity, complete the data cleansing activity on your source data, and then export it to a table in a SQL Server database.</span></span>  
  
2.  <span data-ttu-id="2a077-123">일치 정책이 포함된 기술 자료를 사용하여 다른 데이터 품질 프로젝트를 만들고 **일치** 작업을 선택한 다음 **맵** 페이지에서 1단계 중에 정리한 데이터를 내보낸 데이터베이스 및 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-123">Create another data quality project by using a knowledge base that contains a matching policy, select the **Matching** activity, and then in the **Map** page, select the database and the table where you exported the cleansed data in step 1.</span></span>  
  
3.  <span data-ttu-id="2a077-124">정리한 데이터에 대해 일치 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-124">Complete the matching activity on the cleansed data.</span></span>  
  
 <span data-ttu-id="2a077-125">데이터 품질 프로젝트의 일치 작업에 대한 자세한 내용은 [Data Matching](../../2014/data-quality-services/data-matching.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a077-125">For detailed information about the matching activity in a data quality project, see [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
##  <a name="data-profiling-and-notifications"></a><a name="ProfilingNotification"></a> <span data-ttu-id="2a077-126">데이터 프로파일링 및 알림</span><span class="sxs-lookup"><span data-stu-id="2a077-126">Data Profiling and Notifications</span></span>  
 <span data-ttu-id="2a077-127">데이터 품질 프로젝트에서 정리 및 일치 작업을 실행하는 동안 DQS에 의해 처리되는 데이터의 실시간 통계 및 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-127">While running the cleansing and matching activities in a data quality project, you can see real-time statistics and information about the data that is being processed by DQS.</span></span> <span data-ttu-id="2a077-128">데이터 프로파일링을 통해 정리 및 일치 프로세스의 효과를 평가하고 잠재적으로 데이터 정리 또는 일치로 데이터 품질이 개선된 정도를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-128">Data profiling helps you assess the effectiveness of the cleansing and matching processes, and you can potentially determine the extent to which data cleansing or matching helped improve the data quality.</span></span> <span data-ttu-id="2a077-129">DQS 프로파일링에서는 *완결성* (데이터가 존재하는 정도)과 *정확도* (데이터를 의도된 용도에 맞게 사용할 수 있는 정도)의 두 가지 데이터 품질 차원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-129">DQS profiling provides two data-quality dimensions: *completeness* (the extent to which data is present) and *accuracy* (the extent to which data can be used for its intended use).</span></span> <span data-ttu-id="2a077-130">또한 데이터 프로파일링 정보를 기반으로 데이터 정리 및 데이터 일치 작업을 향상시키기 위해 수행할 수 있는 작업에 대한 알림이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-130">Further, based on the data profiling information, notifications are displayed to the user on the actions that can be taken to enhance the data cleansing and data matching operations.</span></span> <span data-ttu-id="2a077-131">데이터 프로파일링 및 알림에 대한 자세한 내용은 [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a077-131">For detailed information about data profiling and notifications, see [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2a077-132">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2a077-132">Related Tasks</span></span>  
  
|<span data-ttu-id="2a077-133">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="2a077-133">Task Description</span></span>|<span data-ttu-id="2a077-134">항목</span><span class="sxs-lookup"><span data-stu-id="2a077-134">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="2a077-135">데이터 품질 프로젝트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-135">Describes how to create a data quality project.</span></span>|[<span data-ttu-id="2a077-136">데이터 품질 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="2a077-136">Create a Data Quality Project</span></span>](../../2014/data-quality-services/create-a-data-quality-project.md)|  
|<span data-ttu-id="2a077-137">데이터 품질 프로젝트를 관리하는 방법(열기, 잠금 해제, 이름 바꾸기 및 삭제)에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-137">Describes how to manage (open, unlock, rename, and delete) a data quality project.</span></span>|[<span data-ttu-id="2a077-138">데이터 품질 프로젝트&#41; 열기, 잠금 해제, 이름 바꾸기 및 삭제 &#40;관리</span><span class="sxs-lookup"><span data-stu-id="2a077-138">Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project</span></span>](../../2014/data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)|  
|<span data-ttu-id="2a077-139">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]에서 Integration Services 프로젝트를 여는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2a077-139">Describes how to open an Integration Services project in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>|[<span data-ttu-id="2a077-140">데이터 품질 클라이언트에서 Integration Services 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="2a077-140">Open Integration Services Projects in Data Quality Client</span></span>](../../2014/data-quality-services/open-integration-services-projects-in-data-quality-client.md)|  
  
## <a name="see-also"></a><span data-ttu-id="2a077-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a077-141">See Also</span></span>  
 [<span data-ttu-id="2a077-142">DQS 기술 자료 및 도메인</span><span class="sxs-lookup"><span data-stu-id="2a077-142">DQS Knowledge Bases and Domains</span></span>](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
