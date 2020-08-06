---
title: 하위 보고서(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab5bea3a-109e-4c25-92d9-494df7c52dd8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ce30cf575148af11d6485125089beace07fd5429
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639269"
---
# <a name="subreports-report-builder-and-ssrs"></a><span data-ttu-id="13cda-102">하위 보고서(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="13cda-102">Subreports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="13cda-103">하위 보고서는 주 보고서의 본문 안에 다른 보고서를 표시하는 보고서 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-103">A subreport is a report item that displays another report inside the body of a main report.</span></span> <span data-ttu-id="13cda-104">보고서의 하위 보고서는 개념적 측면에서 웹 페이지의 프레임과 유사하며</span><span class="sxs-lookup"><span data-stu-id="13cda-104">Conceptually, a subreport in a report is similar to a frame in a Web page.</span></span> <span data-ttu-id="13cda-105">보고서 내에 다른 보고서를 포함하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-105">It is used to embed a report within a report.</span></span> <span data-ttu-id="13cda-106">모든 보고서를 하위 보고서로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-106">Any report can be used as a subreport.</span></span> <span data-ttu-id="13cda-107">하위 보고서로 표시되는 보고서는 보고서 서버에서 주로 부모 보고서와 같은 폴더에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-107">The report that is displayed as the subreport is stored on a report server, usually in the same folder as the parent report.</span></span> <span data-ttu-id="13cda-108">하위 보고서에 부모 보고서가 매개 변수를 전달하도록 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-108">You can design the parent report to pass parameters to the subreport.</span></span> <span data-ttu-id="13cda-109">하위 보고서의 각 인스턴스에 데이터 필터링 매개 변수를 사용하여 하위 보고서를 데이터 영역 내에서 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-109">A subreport can be repeated within data regions, using a parameter to filter data in each instance of the subreport.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13cda-110">하위 보고서를 테이블릭스 데이터 영역에서 사용하는 경우 하위 보고서 및 해당 매개 변수는 모든 행에 대해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-110">If you use a subreport in a tablix data region, the subreport and its parameters will be processed for every row.</span></span> <span data-ttu-id="13cda-111">행이 많을 경우 드릴스루 보고서가 더 적합한지 여부를 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="13cda-111">If there are many rows, consider whether a drillthrough report is more appropriate.</span></span>  
  
 <span data-ttu-id="13cda-112">![rs_Subreport](../media/rs-subreport.gif "rs_Subreport")</span><span class="sxs-lookup"><span data-stu-id="13cda-112">![rs_Subreport](../media/rs-subreport.gif "rs_Subreport")</span></span>  
  
 <span data-ttu-id="13cda-113">위의 그림에서 주 Sales Order 보고서에 표시된 연락처 정보는 실제로 Contacts 하위 보고서에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-113">In this illustration, the contact information displayed in the main Sales Order report actually comes from a Contacts subreport.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="comparing-subreports-and-nested-data-regions"></a><span data-ttu-id="13cda-114">하위 보고서와 중첩된 데이터 영역 비교</span><span class="sxs-lookup"><span data-stu-id="13cda-114">Comparing Subreports and Nested Data Regions</span></span>  
 <span data-ttu-id="13cda-115">하위 보고서를 사용하여 별도의 데이터 그룹을 표시하려는 경우 테이블, 행렬 또는 차트 같은 데이터 영역을 대신 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-115">If you're thinking of using subreports to display separate groups of data, consider using data regions, such as tables, matrices, and charts, instead.</span></span> <span data-ttu-id="13cda-116">데이터 영역만 있는 보고서는 하위 보고서가 있는 보고서보다 성능이 나을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-116">Reports with data regions only may perform better than reports that include subreports.</span></span>  
  
 <span data-ttu-id="13cda-117">동일한 데이터 원본의 데이터 그룹을 단일 데이터 영역에 중첩하려면 데이터 영역을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-117">Use data regions to nest groups of data from the same data source within a single data region.</span></span> <span data-ttu-id="13cda-118">다른 데이터 원본의 데이터 그룹을 단일 데이터 영역에 중첩하거나, 여러 부모 보고서에서 하위 보고서를 다시 사용하거나, 다른 보고서 내부에 독립 실행형 보고서를 표시하려면 하위 보고서를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-118">Use subreports to nest groups of data from different data sources within a single data region, reuse a subreport in multiple parent reports, or display a standalone report inside of another report.</span></span> <span data-ttu-id="13cda-119">예를 들어 다른 보고서의 본문 안에 하위 보고서를 여러 개 넣어 "요약 책"을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-119">For example, you can create a "briefing book" by placing multiple subreports inside the body of another report.</span></span>  
  
 <span data-ttu-id="13cda-120">데이터 영역은 하위 보고서와 같은 기능과 유연성을 제공하면서도 성능은 보다 우수합니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-120">Data regions provide much of the same functionality and flexibility as subreports, but with better performance.</span></span> <span data-ttu-id="13cda-121">보고서 서버에서는 하위 보고서의 각 인스턴스를 개별 보고서로 처리하기 때문에 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-121">Because the report server processes each instance of a subreport as a separate report, performance can be impacted.</span></span> <span data-ttu-id="13cda-122">자세한 내용은 [중첩된 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13cda-122">For more information, see [Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-parameters-in-subreports"></a><span data-ttu-id="13cda-123">하위 보고서에서 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="13cda-123">Using Parameters in Subreports</span></span>  
 <span data-ttu-id="13cda-124">부모 보고서에서 하위 보고서로 매개 변수를 전달하려면 하위 보고서로 사용하는 보고서에 보고서 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-124">To pass parameters from the parent report to the subreport, define a report parameter in the report that you use as the subreport.</span></span> <span data-ttu-id="13cda-125">하위 보고서를 부모 보고서에 배치하면 부모 보고서에서 하위 보고서의 보고서 매개 변수에 전달할 값 및 보고서 매개 변수를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-125">When you place the subreport in the parent report, you can select the report parameter and a value to pass from the parent report to the report parameter in the subreport.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13cda-126">하위 보고서에서 선택하는 매개 변수는 쿼리 매개 변수가 아닌 보고서 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-126">The parameter that you select from the subreport is a report parameter, not a query parameter.</span></span>  
  
 <span data-ttu-id="13cda-127">하위 보고서를 보고서의 본문이나 데이터 영역에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-127">You can place a subreport in the main body of the report, or in a data region.</span></span> <span data-ttu-id="13cda-128">하위 보고서를 데이터 영역에 배치하면 하위 보고서는 데이터 영역에 있는 그룹 또는 행의 인스턴스마다 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-128">If you place a subreport in a data region, the subreport will repeat with each instance of the group or row in the data region.</span></span> <span data-ttu-id="13cda-129">그룹 또는 행의 값을 하위 보고서에 전달하려면 하위 보고서 값 속성에서 하위 보고서 매개 변수에 전달하려는 값을 포함하는 필드의 식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-129">To pass a value from the group or row to the subreport, in the subreport value property, use a field expression for the field containing the value you want to pass to the subreport parameter.</span></span>  
  
 <span data-ttu-id="13cda-130">하위 보고서 작업에 대한 자세한 내용은 [하위 보고서 및 매개 변수 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13cda-130">For more information about working with subreports, see [Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md).</span></span>  
  
## <a name="specifying-subreport-names-and-locations"></a><span data-ttu-id="13cda-131">하위 보고서 이름 및 위치 지정</span><span class="sxs-lookup"><span data-stu-id="13cda-131">Specifying Subreport Names and Locations</span></span>  
 <span data-ttu-id="13cda-132">주 보고서가 같은 보고서 서버의 다른 폴더에 있는 하위 보고서를 지정하도록 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-132">You can design a main report to specify a subreport in a different folder on the same report server.</span></span>  
  
 <span data-ttu-id="13cda-133">하위 보고서를 지정하는 데 사용하는 구문은 보고서 서버가 기본 모드에 있는지, 아니면 SharePoint 통합 모드에 있는지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-133">The syntax you use to specify the subreport depends on whether the report server is in native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="13cda-134">자세한 내용은 [외부 항목에 대한 경로 지정&#40;보고서 작성기 및 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13cda-134">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="13cda-135">보고서 작성기에서 주 보고서의 하위 보고서를 미리 보려면 두 보고서가 같은 보고서 서버에 있어야 합니다. 그렇지 않은 경우 하위 보고서의 전체 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13cda-135">In Report Builder, to preview a subreport in a main report, both reports must be located in the same report server, or you must specify a full path to the subreport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13cda-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13cda-136">See Also</span></span>  
 [<span data-ttu-id="13cda-137">드릴스루, 드릴다운, 하위 보고서 및 중첩 데이터 영역&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="13cda-137">Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;</span></span>](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
