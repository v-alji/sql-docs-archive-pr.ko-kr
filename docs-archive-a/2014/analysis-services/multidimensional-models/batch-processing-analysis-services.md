---
title: 일괄 처리 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- batches [Analysis Services]
ms.assetid: ba4dcf72-0667-41d0-816b-ab8ff9a7d9cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: c777339f41f5f9029e4d03d47cc7f682e00032b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646698"
---
# <a name="batch-processing-analysis-services"></a><span data-ttu-id="59c2d-102">일괄 처리(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="59c2d-102">Batch Processing (Analysis Services)</span></span>
  <span data-ttu-id="59c2d-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 일괄 처리 명령을 사용하여 여러 처리 명령을 단일 요청으로 서버에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Batch command to send multiple processing commands to the server in a single request.</span></span> <span data-ttu-id="59c2d-104">일괄 처리를 사용하여 처리할 개체와 처리 순서를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-104">Batch processing gives you a way to control which objects are to be processed, and in what order.</span></span> <span data-ttu-id="59c2d-105">또한 일괄 처리는 일련의 독립 실행형 작업으로 실행되거나 한 프로세스가 실패하면 완료된 일괄 처리가 롤백되는 트랜잭션으로 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-105">Also, a batch can run as a series of stand-alone jobs, or as a transaction in which the failure of one process causes a rollback of the complete batch.</span></span>  
  
 <span data-ttu-id="59c2d-106">일괄 처리는 변경 내용을 커밋하는 데 걸리는 시간을 줄이고 통합함으로써 데이터 가용성을 최대화합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-106">Batch processing maximizes data availability by consolidating and reducing the amount of time taken to commit changes.</span></span> <span data-ttu-id="59c2d-107">차원을 전체 처리할 경우 해당 차원을 사용하는 파티션은 처리되지 않은 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-107">When you fully process a dimension, any partition using that dimension is marked as unprocessed.</span></span> <span data-ttu-id="59c2d-108">따라서 처리되지 않은 파티션이 포함된 큐브는 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-108">As a result, cubes that contain the unprocessed partitions are unavailable for browsing.</span></span> <span data-ttu-id="59c2d-109">영향을 받는 파티션과 함께 차원을 처리하는 일괄 처리 작업을 수행하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-109">You can address this with a batch processing job by processing the dimensions together with the affected partitions.</span></span> <span data-ttu-id="59c2d-110">일괄 처리 작업을 트랜잭션으로 실행하면 모든 처리가 완료될 때까지 트랜잭션에 포함된 모든 개체를 쿼리에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-110">Running the batch processing job as a transaction makes sure that all objects included in the transaction remain available for queries until all processing is completed.</span></span> <span data-ttu-id="59c2d-111">트랜잭션이 변경 내용을 커밋하면 개체를 일시적으로 사용할 수 없게 되지만 변경 내용을 커밋하는 데 걸리는 총 시간은 개체를 개별적으로 처리할 때보다 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-111">As the transaction commits the changes, locks are put on the affected objects, making the objects temporarily unavailable, but overall the amount of time used to commit the changes is less than if you processed objects individually.</span></span>  
  
 <span data-ttu-id="59c2d-112">이 항목의 절차에서는 차원과 파티션을 완전히 처리하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-112">The procedures in this topic show the steps for fully processing dimensions and partitions.</span></span> <span data-ttu-id="59c2d-113">일괄 처리에는 증분 처리 등과 같은 다른 처리 옵션도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-113">Batch processing can also include other processing options, such as incremental processing.</span></span> <span data-ttu-id="59c2d-114">이러한 절차를 올바르게 수행하려면 둘 이상의 차원과 하나 이상의 파티션이 들어 있는 기존 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-114">For these procedures to work correctly, you should use an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains at least two dimensions and one partition.</span></span>  
  
 <span data-ttu-id="59c2d-115">이 항목에는 다음 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-115">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="59c2d-116">SQL Server Data Tools에서 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="59c2d-116">Batch Processing in SQL Server Data Tools</span></span>](#bkmk_ssdt)  
  
 [<span data-ttu-id="59c2d-117">Management Studio에서 XMLA를 사용하여 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="59c2d-117">Batch Processing using XMLA in Management Studio</span></span>](#bkmk_xmla)  
  
##  <a name="batch-processing-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a> <span data-ttu-id="59c2d-118">SQL Server Data Tools에서 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="59c2d-118">Batch Processing in SQL Server Data Tools</span></span>  
 <span data-ttu-id="59c2d-119">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 개체를 처리하기 전에 개체가 포함된 프로젝트를 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-119">Before objects can be processed in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], the project that contains the objects must be deployed.</span></span> <span data-ttu-id="59c2d-120">자세한 내용은 [Analysis Services 프로젝트 배포&#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59c2d-120">For more information, see [Deploy Analysis Services Projects &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md).</span></span>  
  
1.  <span data-ttu-id="59c2d-121">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-121">Open [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="59c2d-122">배포된 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-122">Open a project that has been deployed.</span></span>  
  
3.  <span data-ttu-id="59c2d-123">솔루션 탐색기의 배포된 프로젝트에서 **차원** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-123">In Solution Explorer, under the deployed project, expand the **Dimensions** folder.</span></span>  
  
4.  <span data-ttu-id="59c2d-124">Ctrl 키를 누른 채로 **차원** 폴더에 나열된 각 차원을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-124">Holding the Ctrl key, click each dimension listed in the **Dimensions** folder.</span></span>  
  
5.  <span data-ttu-id="59c2d-125">선택한 차원을 마우스 오른쪽 단추로 클릭한 다음 **처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-125">Right-click the selected dimensions, and then click **Process**.</span></span>  
  
6.  <span data-ttu-id="59c2d-126">Ctrl 키를 누른 채로 **개체 목록**에 나열된 각 차원을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-126">Holding the Ctrl key, click each dimension listed in the **Object list**.</span></span>  
  
7.  <span data-ttu-id="59c2d-127">선택한 차원을 마우스 오른쪽 단추로 클릭한 다음 **전체 처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-127">Right-click the selected dimensions and select **Process Full**.</span></span>  
  
8.  <span data-ttu-id="59c2d-128">일괄 처리 작업을 사용자 지정하려면 **설정 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-128">To customize the batch process job, click **Change Settings.**</span></span>  
  
9. <span data-ttu-id="59c2d-129">**처리 옵션**에서 다음과 같이 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-129">Under **Processing options**, mark the following settings:</span></span>  
  
    -   <span data-ttu-id="59c2d-130">**처리 순서** 는 **순차**로, **트랜잭션 모드** 는 **단일 트랜잭션**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-130">**Processing Order** is set to **Sequential**, and **Transaction mode** is set to **One Transaction**.</span></span>  
  
    -   <span data-ttu-id="59c2d-131">**쓰기 저장(writeback) 테이블 옵션** 을 **기존 테이블 사용**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-131">**Writeback Table Option** is set to **Use existing**.</span></span>  
  
    -   <span data-ttu-id="59c2d-132">**영향을 받는 개체**에서 **영향을 받는 개체 처리** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-132">Under **Affected Objects**, select the **Process affected objects** check box.</span></span>  
  
10. <span data-ttu-id="59c2d-133">**차원 키 오류** 탭을 클릭 합니다. **기본 오류 구성 사용** 이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-133">Click the **Dimension key errors** tab. Verify that **Use default error configuration** is selected.</span></span>  
  
11. <span data-ttu-id="59c2d-134">**확인** 을 클릭하여 **설정 변경** 화면을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-134">Click **OK** to close the **Change Settings** screen.</span></span>  
  
12. <span data-ttu-id="59c2d-135">**개체 처리** 화면에서 **실행** 을 클릭하여 처리 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-135">Click **Run** in the **Process Objects** screen to start the processing job.</span></span>  
  
13. <span data-ttu-id="59c2d-136">**상태** 상자에 **처리에 성공했습니다**가 표시되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-136">When the **Status** box shows **Process succeeded**, click **Close**.</span></span>  
  
14. <span data-ttu-id="59c2d-137">**개체 처리** 화면에서 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-137">Click **Close** on the **Process Objects** screen.</span></span>  
  
##  <a name="batch-processing-using-xmla-in-management-studio"></a><a name="bkmk_xmla"></a><span data-ttu-id="59c2d-138">Management Studio XMLA를 사용 하 여 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="59c2d-138">Batch Processing using XMLA in Management Studio</span></span>  
 <span data-ttu-id="59c2d-139">일괄 처리를 수행하는 XMLA 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-139">You can create an XMLA script that performs batch processing.</span></span> <span data-ttu-id="59c2d-140">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 각 개체에 대한 XMLA 스크립트 생성을 시작한 다음 해당 스크립트를 예약된 태스크 내부에서 실행되거나 대화형으로 실행되는 단일 XMLA 쿼리에 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="59c2d-140">Start by generating an XMLA script in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] for each object, and then combine them into a single XMLA Query that you run interactively or inside a scheduled task.</span></span>  
  
 <span data-ttu-id="59c2d-141">단계별 지침에 대해서는 [SQL Server 에이전트를 사용 하 여 SSAS 관리 작업 예약](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) 의 **예 2** 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59c2d-141">For step by step instructions, see **Example 2** in [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c2d-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59c2d-142">See Also</span></span>  
 [<span data-ttu-id="59c2d-143">다차원 모델 개체 처리</span><span class="sxs-lookup"><span data-stu-id="59c2d-143">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
  
