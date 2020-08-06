---
title: Data Quality Client에서 Integration Services 프로젝트 열기| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd29bbba274535d6489eb8d188aa4f0150ed7c4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649186"
---
# <a name="open-integration-services-projects-in-data-quality-client"></a><span data-ttu-id="daea3-102">데이터 품질 클라이언트에서 Integration Services 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="daea3-102">Open Integration Services Projects in Data Quality Client</span></span>
  <span data-ttu-id="daea3-103">[!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)] 를 사용하여 정리 프로젝트를 일괄 처리 모드로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-103">The [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)] enables you to run a cleansing project in batch mode.</span></span> <span data-ttu-id="daea3-104">그러나 경우에 따라 DQS의 데이터 품질 프로젝트에서 정리 작업의 **결과 관리 및 보기** 탭에 있는 정리 결과를 검토하는 방법과 유사한 방식으로 Integration Services 패키지의 정리 결과를 검토할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-104">However, at times you might want to review the cleansing results in an Integration Services package similar to how you can review the cleansing results in the **Manage and View Results** tab of a cleansing activity in a data quality project in DQS.</span></span> <span data-ttu-id="daea3-105">DQS는 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 의 Integration Services 프로젝트를 다른 데이터 품질 프로젝트와 마찬가지로 **프로젝트 열기** 화면에서 열 수 있도록 지원하고 Integration Services 프로젝트의 정리 결과에 대한 대화식 정리 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-105">DQS enables you to open Integration Services projects in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] just like any other data quality project from the **Open project** screen, and have an interactive cleansing experience of the cleansing results in an Integration Services project.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="daea3-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="daea3-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="daea3-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="daea3-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="daea3-108">**의** 프로젝트 열기 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]화면에서는 완료된 Integration Services 프로젝트만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-108">Only completed Integration Services projects are available in the **Open project** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="daea3-109">실패한 프로젝트나 실행 중인 프로젝트는 **프로젝트 열기** 화면에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-109">Failed or running projects are not available in the **Open project** screen.</span></span>  
  
-   <span data-ttu-id="daea3-110">Integration Services 프로젝트는**의 대화식 정리 단계(** 결과 관리 및 보기 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]탭)에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-110">Integration Services projects open at the interactive cleansing stage (**Manage View and Results** tab) in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="daea3-111">**정리** 또는 **맵** 탭으로는 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-111">You cannot go to the **Cleanse** or **Map** tabs.</span></span> <span data-ttu-id="daea3-112">**다음** 을 클릭하여 **내보내기**탭으로만 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-112">You can only go to the **Export** tab by clicking **Next**.</span></span>  
  
-   <span data-ttu-id="daea3-113">잠긴 Integration Services 프로젝트는 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]에서 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-113">You cannot delete a locked Integration Services project from [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="daea3-114">삭제하려면 먼저 잠금을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-114">You must first unlock it to delete.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="daea3-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="daea3-115">Prerequisites</span></span>  
 <span data-ttu-id="daea3-116">DQS 정리 구성 요소 패키지가 포함된 Integration Services 프로젝트를 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]에서 보고 열려면 올바르게 실행이 완료된 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-116">You must have successfully completed running an Integration Services project containing a package with a DQS Cleansing component to see and open it in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="daea3-117">보안</span><span class="sxs-lookup"><span data-stu-id="daea3-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="daea3-118">권한</span><span class="sxs-lookup"><span data-stu-id="daea3-118">Permissions</span></span>  
 <span data-ttu-id="daea3-119">Integration Services 프로젝트를 열려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_kb_operator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-119">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to open an Integration Services project.</span></span>  
  
##  <a name="open-an-integration-services-project"></a><a name="Open"></a> <span data-ttu-id="daea3-120">Integration Services 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="daea3-120">Open an Integration Services Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="daea3-121">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="daea3-122">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]홈 화면에서 **데이터 품질 프로젝트 열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open Data Quality Project**.</span></span> <span data-ttu-id="daea3-123">**프로젝트 열기** 화면이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-123">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="daea3-124">**프로젝트 열기** 화면에서 다음 방법 중 하나로 Integration Services 프로젝트를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-124">In the **Open project** screen, you can identify an Integration Services project in either of the following ways:</span></span>  
  
    1.  <span data-ttu-id="daea3-125">**프로젝트 이름**: Integration Services 프로젝트는 다음과 같은 명명 용어를 사용 하 여 나열 됩니다. "package.productname Cleansing_ *\<DATE>\*\*\<TIME>* _ {GUID}"</span><span class="sxs-lookup"><span data-stu-id="daea3-125">**Project Name**: Integration Services projects are listed using the following naming terminology: "Package.DQS Cleansing_*\<DATE>\*\*\<TIME>*_{GUID}."</span></span> <span data-ttu-id="daea3-126">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 동일한 패키지를 올바르게 실행할 때마다 **프로젝트 열기** 화면에 새 프로젝트가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-126">Every time you successfully run the same package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], a new project is listed in the **Open project** screen.</span></span>  
  
    2.  <span data-ttu-id="daea3-127">**프로젝트 유형**: Integration Services 프로젝트는 **프로젝트 열기** 화면에서 **SSIS** 라는 프로젝트 형식을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-127">**Project Type**: Integration Services projects have **SSIS** as the project type in the **Open project** screen.</span></span>  
  
     <span data-ttu-id="daea3-128">프로젝트를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-128">Select a project, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="daea3-129">대화식 정리 단계(**결과 관리 및 보기** 탭)에서 Integration Services 프로젝트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-129">The Integration Services project opens at the interactive cleansing stage (**Manage View and Results** tab).</span></span> <span data-ttu-id="daea3-130">Integration Services 프로젝트의 데이터에 대해 대화식 정리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-130">You can perform an interactive cleansing on the data in the Integration Services project.</span></span> <span data-ttu-id="daea3-131">**결과 관리 및 보기** 탭에 대한 자세한 내용은 [DQS&#40;내부&#41; 기술 자료를 사용하여 데이터 정리](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)에서 [대화형 정리 단계](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="daea3-131">For detailed information about the **Manage and View Results** tab, see [Interactive Cleansing Stage](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).</span></span>  
  
5.  <span data-ttu-id="daea3-132">**다음** 을 클릭하여 **내보내기** 탭으로 이동합니다. 여기서 SQL Server 데이터베이스, .csv 파일 또는 Excel 파일의 새 테이블 중 하나에 처리된 데이터를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-132">Click **Next** to go to the **Export** tab where you can export the processed data to any of the following: a new table in the SQL Server database, a .csv file, or an Excel file.</span></span> <span data-ttu-id="daea3-133">**내보내기** 탭에 대한 자세한 내용은 [DQS&#40;내부&#41; 기술 자료를 사용하여 데이터 정리](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)에서 [내보내기 단계](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="daea3-133">For detailed information about the **Export** tab, see [Export Stage](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)</span></span>  
  
6.  <span data-ttu-id="daea3-134">데이터를 내보낸 후 **마침** 을 클릭하여 Integration Services 프로젝트를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="daea3-134">After exporting the data, click **Finish** to close the Integration Services project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daea3-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="daea3-135">See Also</span></span>  
 <span data-ttu-id="daea3-136">[DQS 정리 변환](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="daea3-136">[DQS Cleansing Transformation](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) </span></span>  
 [<span data-ttu-id="daea3-137">Integration Services&#40;SSIS&#41; 프로젝트</span><span class="sxs-lookup"><span data-stu-id="daea3-137">Integration Services &#40;SSIS&#41; Projects</span></span>](../integration-services/integration-services-ssis-projects-and-solutions.md)  
