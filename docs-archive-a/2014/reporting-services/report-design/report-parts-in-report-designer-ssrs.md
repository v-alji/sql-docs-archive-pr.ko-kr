---
title: 보고서 디자이너의 보고서 파트(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.components.f1
ms.assetid: 0c34311d-05d6-4bd2-b452-545fa95f8e7f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7535c5c2c514bc32a11a5fc0d97c6aee1cf5f2d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639297"
---
# <a name="report-parts-in-report-designer-ssrs"></a><span data-ttu-id="e1a05-102">보고서 디자이너의 보고서 파트(SSRS)</span><span class="sxs-lookup"><span data-stu-id="e1a05-102">Report Parts in Report Designer (SSRS)</span></span>
  <span data-ttu-id="e1a05-103">보고서 디자이너에서 프로젝트에 테이블, 차트 및 기타 보고서 항목을 만든 후에는 자신과 다른 사람이 다른 보고서에서 다시 사용할 수 있도록 이들 항목을 보고서 서버 또는 보고서 서버와 통합된 SharePoint 사이트에 *보고서 파트* 로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-103">In Report Designer, after you create tables, charts, and other report items in a project, you can publish them as *report parts* to a report server or SharePoint site integrated with a report server so that you and others can reuse them in other reports.</span></span>  
  
 <span data-ttu-id="e1a05-104">일반적으로 보고서 파트는 보고서 디자이너와 보고서 작성기에서 같은 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-104">In general, report parts function the same way in Report Designer and in Report Builder.</span></span> <span data-ttu-id="e1a05-105">기본 기능에 대해 알아보려면 msdn.microsoft.com의 [보고서 작성기 설명서](https://go.microsoft.com/fwlink/?LinkId=154494) 에서 [보고서 파트 &#40;보고서 작성기 및 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1a05-105">To read about basic functionality, see [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="e1a05-106">그러나 보고서 디자이너에서 보고서 파트가 작동하는 방식에는 기본적인 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-106">There are fundamental differences in the way report parts work in Report Designer.</span></span> <span data-ttu-id="e1a05-107">가장 큰 차이는 작업 흐름입니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-107">A main difference is the work flow.</span></span> <span data-ttu-id="e1a05-108">보고서 작성기에서는 공동 작성이 가능합니다. 보고서 파트를 만들고 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-108">Report Builder enables collaborative authoring: I create a report part and publish it.</span></span> <span data-ttu-id="e1a05-109">다시 사용, 수정 및 다시 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-109">You can reuse, modify, and republish it.</span></span> <span data-ttu-id="e1a05-110">보고서 디자이너에서 게시는 단방향으로 수행됩니다. 즉, 보고서 디자이너에서 보고서 파트를 게시하면 다른 사람이 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-110">In Report Designer, publishing is one-way: I can publish a report part from Report Designer, and you can reuse it.</span></span> <span data-ttu-id="e1a05-111">하지만 보고서 디자이너에서 보고서를 기존 보고서 파트를 다시 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-111">But I cannot reuse an existing report part in a report in Report Designer.</span></span> <span data-ttu-id="e1a05-112">이 항목에서는 보고서 파트에 대해 간략하게 설명한 후 이러한 차이점에 대해 중점적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-112">This topic elaborates on these differences, after a quick overview of report parts.</span></span>  
  
##  <a name="life-cycle-of-report-part-publishing"></a><a name="ComponentWorkflow"></a> <span data-ttu-id="e1a05-113">보고서 파트 게시 수명 주기</span><span class="sxs-lookup"><span data-stu-id="e1a05-113">Life Cycle of Report Part Publishing</span></span>  
 <span data-ttu-id="e1a05-114">![rs_ComponentCreation](../media/rs-componentcreation.gif "rs_ComponentCreation")</span><span class="sxs-lookup"><span data-stu-id="e1a05-114">![rs_ComponentCreation](../media/rs-componentcreation.gif "rs_ComponentCreation")</span></span>  
  
1.  <span data-ttu-id="e1a05-115">보고서 디자이너에서 A라는 사람이 보고서가 포함된 프로젝트를 만듭니다. 이 보고서에는 포함된 데이터 세트를 사용하는 차트가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-115">In Report Designer, Person A creates a project that contains a report with a chart that depends on an embedded dataset.</span></span>  
  
2.  <span data-ttu-id="e1a05-116">A가 포함된 데이터 세트가 들어 있는 차트에 게시를 위한 플래그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-116">Person A flags the chart with its embedded dataset for publishing.</span></span> <span data-ttu-id="e1a05-117">보고서 디자이너는 이 차트에 고유한 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-117">Report Designer assigns it a unique ID.</span></span> <span data-ttu-id="e1a05-118">그런 다음 A가 보고서를 보고서 서버로 배포하면</span><span class="sxs-lookup"><span data-stu-id="e1a05-118">Person A then deploys the report to the report server.</span></span> <span data-ttu-id="e1a05-119">보고서 디자이너가 차트를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-119">Report Designer publishes the chart.</span></span>  
  
3.  <span data-ttu-id="e1a05-120">B라는 사람이 보고서 작성기에서 빈 보고서를 만들어 이 차트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-120">Person B creates a blank report in Report Builder and adds the chart to it.</span></span> <span data-ttu-id="e1a05-121">그러면 이 차트는 포함된 데이터 세트와 함께 B가 만든 보고서의 파트가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-121">The chart is now part of Person B's report, along with the embedded dataset.</span></span> <span data-ttu-id="e1a05-122">B는 보고서에 있는 차트 및 데이터 세트의 인스턴스를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-122">Person B can modify the instances of the chart and dataset that are in the report.</span></span> <span data-ttu-id="e1a05-123">수정 작업을 수행해도 보고서 서버의 차트 및 데이터 세트 인스턴스에는 아무런 영향이 없으며, 보고서의 인스턴스와 보고서 서버의 인스턴스 간 관계도 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-123">This will have no effect on the instances of the chart and dataset on the report server, nor will it break the relationship between the instances in the report and on the report server.</span></span>  
  
     <span data-ttu-id="e1a05-124">![rs_BIDScomponentupdate](../media/rs-bidscomponentupdate.gif "rs_BIDScomponentupdate")</span><span class="sxs-lookup"><span data-stu-id="e1a05-124">![rs_BIDScomponentupdate](../media/rs-bidscomponentupdate.gif "rs_BIDScomponentupdate")</span></span>  
  
4.  <span data-ttu-id="e1a05-125">A가 보고서 디자이너에서 원본 보고서의 차트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-125">In Report Designer, Person A modifies the chart in the original report.</span></span>  
  
5.  <span data-ttu-id="e1a05-126">A가 보고서를 다시 배포합니다. 그러면 차트가 서버에 다시 게시되어 서버의 차트가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-126">Person A redeploys the report, which republishes the chart to the server, thus updating the chart on the server.</span></span>  
  
6.  <span data-ttu-id="e1a05-127">보고서 작성기에서 B가 서버에서 업데이트된 차트를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-127">In Report Builder, Person B accepts the updated chart from the server.</span></span> <span data-ttu-id="e1a05-128">그러면 B가 보고서에서 차트에 적용한 변경 내용을 이 업데이트 내용이 덮어쓰게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-128">This overwrites the changes that Person B had made to the chart in Person B's report.</span></span>  
  
##  <a name="publishing-report-parts"></a><a name="PublishingComponents"></a> <span data-ttu-id="e1a05-129">보고서 파트 게시</span><span class="sxs-lookup"><span data-stu-id="e1a05-129">Publishing Report Parts</span></span>  
 <span data-ttu-id="e1a05-130">보고서 파트를 게시하면 보고서 디자이너가 보고서 파트에 고유한 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-130">When you publish a report part, Report Designer assigns it a unique ID.</span></span> <span data-ttu-id="e1a05-131">이때부터 해당 보고서 파트에 대한 다른 내용이 변경되어도 이 ID는 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-131">From then on, it maintains that ID, no matter what else you change about it.</span></span> <span data-ttu-id="e1a05-132">ID는 보고서의 원본 보고서 항목을 보고서 파트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-132">The ID links the original report item in your report to the report part.</span></span> <span data-ttu-id="e1a05-133">다른 보고서 작성자가 보고서 작성기에서 이 보고서 파트를 다시 사용할 때도 이 ID는 다른 작성자의 보고서에 있는 보고서 파트를 이 보고서 파트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-133">When other report authors reuse the report part in Report Builder, the ID also links the report part in their report to the report part.</span></span>  
  
 <span data-ttu-id="e1a05-134">다음과 같은 보고서 항목을 보고서 파트로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-134">These are the report items you can publish as report parts:</span></span>  
  
-   <span data-ttu-id="e1a05-135">차트</span><span class="sxs-lookup"><span data-stu-id="e1a05-135">Charts</span></span>  
  
-   <span data-ttu-id="e1a05-136">계기</span><span class="sxs-lookup"><span data-stu-id="e1a05-136">Gauges</span></span>  
  
-   <span data-ttu-id="e1a05-137">이미지 및 포함 이미지</span><span class="sxs-lookup"><span data-stu-id="e1a05-137">Images and embedded images</span></span>  
  
-   <span data-ttu-id="e1a05-138">지도</span><span class="sxs-lookup"><span data-stu-id="e1a05-138">Maps</span></span>  
  
-   <span data-ttu-id="e1a05-139">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e1a05-139">Parameters</span></span>  
  
-   <span data-ttu-id="e1a05-140">사각형</span><span class="sxs-lookup"><span data-stu-id="e1a05-140">Rectangles</span></span>  
  
-   <span data-ttu-id="e1a05-141">테이블</span><span class="sxs-lookup"><span data-stu-id="e1a05-141">Tables</span></span>  
  
-   <span data-ttu-id="e1a05-142">행렬</span><span class="sxs-lookup"><span data-stu-id="e1a05-142">Matrices</span></span>  
  
-   <span data-ttu-id="e1a05-143">목록</span><span class="sxs-lookup"><span data-stu-id="e1a05-143">Lists</span></span>  
  
 <span data-ttu-id="e1a05-144">테이블, 행렬, 차트 등의 데이터를 표시하는 보고서 파트를 게시하는 경우에는 공유 데이터 세트를 기준으로 사용할 수 있습니다. 그렇지 않으면 보고서 파트를 게시할 때 이 파트가 사용하는 데이터 세트가 포함된 데이터 세트로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-144">If you are publishing a report part that displays data, such as a table, matrix, or chart, you can base it on a shared dataset; otherwise, when you publish the report part, the dataset that it depends on is saved as an embedded dataset.</span></span> <span data-ttu-id="e1a05-145">포함된 데이터 세트는 포함된 데이터 원본을 기반으로 할 수 있지만 자격 증명은 포함된 데이터 원본에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-145">Embedded datasets can be based on embedded data sources, but credentials are not stored in embedded data sources.</span></span> <span data-ttu-id="e1a05-146">따라서 보고서 파트에서 사용하는 포함된 데이터 세트가 포함된 데이터 원본을 사용하는 경우 이 보고서 파트를 다시 사용하는 사람은 모두 포함된 데이터 원본에 대한 자격 증명을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-146">Thus, if your report part depends on an embedded dataset that uses an embedded data source, anyone who reuses this report part will need to provide the credentials for the embedded data source.</span></span> <span data-ttu-id="e1a05-147">그렇게 하지 않으려면 자격 증명이 저장되어 있는 공유 데이터 원본을 포함된 데이터 세트와 공유 데이터 세트의 기준으로 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="e1a05-147">To avoid this, base your embedded and shared datasets on shared data sources with stored credentials.</span></span> <span data-ttu-id="e1a05-148">자세한 내용은 msdn.microsoft.com의 [보고서 작성기 설명서](https://go.microsoft.com/fwlink/?LinkId=154494) 에서 [보고서 작성기의 보고서 파트 및 데이터 집합](../report-data/report-parts-and-datasets-in-report-builder.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1a05-148">For more information, see [Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="e1a05-149">보고서 디자이너에서 보고서 파트를 게시할 때는 두 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-149">Publishing a report part in Report Designer is a two-step process:</span></span>  
  
1.  <span data-ttu-id="e1a05-150">**보고서 파트 게시** 대화 상자에서 게시할 보고서 항목에 플래그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-150">Flag the report items that you want to publish in the **Publish Report Parts** dialog box.</span></span>  
  
2.  <span data-ttu-id="e1a05-151">보고서를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-151">Deploy the report.</span></span>  
  
 <span data-ttu-id="e1a05-152">보고서를 배포하면 보고서 파트가 SharePoint 사이트 또는 보고서 서버에 게시되어 다른 사람이 보고서 파트를 다시 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-152">When you deploy the report, the report part is published to a SharePoint site or report server, and others can reuse it.</span></span> <span data-ttu-id="e1a05-153">보고서 파트를 게시하려면 보고서를 배포할 때 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 보고서 서버에 연결되어 있어야 하며 보고서 서버에 대한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-153">To publish a report part, you must have a connection to and sufficient permissions on a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server when you deploy the report.</span></span>  
  
  
##  <a name="reusing-report-parts"></a><a name="SearchReuseComponents"></a> <span data-ttu-id="e1a05-154">보고서 파트 다시 사용</span><span class="sxs-lookup"><span data-stu-id="e1a05-154">Reusing Report Parts</span></span>  
 <span data-ttu-id="e1a05-155">보고서 작성기에서와는 달리 보고서 파트를 만든 프로젝트 외의 다른 프로젝트에서는 보고서 파트를 검색하고 다시 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-155">Unlike in Report Builder, you cannot search for and reuse a report part in a project other than the one in which it was created.</span></span>  
  
 <span data-ttu-id="e1a05-156">보고서 작성기에서 작업하는 보고서 작성자는 자신이 만든 보고서에서 다른 사람이 게시한 보고서 파트를 검색하고 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-156">Report authors working in Report Builder can search for and reuse report parts that you publish in reports that they create.</span></span>  
  
##  <a name="republishing-report-parts"></a><a name="RepublishingComponents"></a> <span data-ttu-id="e1a05-157">보고서 파트 다시 게시</span><span class="sxs-lookup"><span data-stu-id="e1a05-157">Republishing Report Parts</span></span>  
 <span data-ttu-id="e1a05-158">보고서 디자이너에서는 기존 보고서 파트를 만든 보고서 내에서 보고서 파트를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-158">In Report Designer, you should update an existing report part from within the report in which you created it.</span></span> <span data-ttu-id="e1a05-159">보고서 작성기에서는 보고서 작성자가 보고서 파트를 다시 사용할 수 있으며 원래 작성자가 게시한 보고서 파트를 바꾸지 않고도 새 보고서 파트로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-159">In Report Builder, report authors can reuse the report part, and publish it as a new report part without replacing the report part that you published.</span></span> <span data-ttu-id="e1a05-160">또한 권한이 있으면 원래 작성자가 게시한 보고서 파트를 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-160">If they have sufficient permissions they can also update the report part that you published.</span></span> <span data-ttu-id="e1a05-161">사이트 또는 서버의 폴더에 대한 권한이 있으면 누구나 해당 사이트 또는 서버에 저장된 보고서 파트를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-161">Anyone with sufficient permissions for a folder on a site or server can update the report parts stored there.</span></span> <span data-ttu-id="e1a05-162">마지막 업데이트 내용이 이전 업데이트 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-162">The last update overwrites previous updates.</span></span>  
  
 <span data-ttu-id="e1a05-163">보고서 파트를 수정한 다음 사이트 또는 서버로 다시 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-163">You can modify and then republish the report part to the site or server.</span></span> <span data-ttu-id="e1a05-164">보고서 작성기를 사용하여 해당 보고서 파트를 보고서에 추가한 보고서 작성자가 다음 번에 해당 보고서를 열면 변경 내용 알림이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-164">Report Builder report authors who have added that report part to a report are informed of the change the next time they open that report.</span></span> <span data-ttu-id="e1a05-165">그러면 변경 내용 허용 여부를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-165">They can choose to accept your changes or not.</span></span>  
  
 <span data-ttu-id="e1a05-166">또한 이미 게시한 보고서를 새로 게시하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-166">You can also choose to publish as new a report that you have already published.</span></span> <span data-ttu-id="e1a05-167">보고서 파트 게시 대화 상자에서 "새 보고서 파트로 게시"를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-167">In the Publish Report Parts dialog box, click the Publish as a new report part.</span></span> <span data-ttu-id="e1a05-168">이 새 보고서 파트는 이전 보고서 파트와 관계가 없으며 새로운 고유 ID가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a05-168">This new report part has a new unique ID and no relationship to the old report part.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="e1a05-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1a05-169">See Also</span></span>  
 [<span data-ttu-id="e1a05-170">보고서 파트 관리</span><span class="sxs-lookup"><span data-stu-id="e1a05-170">Managing Report Parts</span></span>](managing-report-parts.md)  
  
  
