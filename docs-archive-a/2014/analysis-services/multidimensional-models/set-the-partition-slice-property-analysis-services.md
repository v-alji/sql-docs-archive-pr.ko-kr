---
title: 파티션 조각 속성 설정 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 08/05/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], data slices
- data slices [Analysis Services]
ms.assetid: 507b91e5-7f85-4c22-be97-4d7a676e6667
author: minewiskan
ms.author: owend
ms.openlocfilehash: f42c4536b99ba3fecf9b947942b881a3be72784f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653013"
---
# <a name="set-the-partition-slice-property-analysis-services"></a><span data-ttu-id="0d84e-102">파티션 조각 속성 설정(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="0d84e-102">Set the Partition Slice Property (Analysis Services)</span></span>
  <span data-ttu-id="0d84e-103">데이터 조각은 적절한 파티션의 데이터에 대한 직접적인 쿼리를 돕는 중요한 최적화 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-103">A data slice is an important optimization feature that helps direct queries to the data of the appropriate partitions.</span></span> <span data-ttu-id="0d84e-104">Slice 속성을 명시적으로 설정하면 MOLAP 및 HOLAP 파티션에 대해 생성된 기본 조각을 재정의하여 쿼리 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-104">Explicitly setting the Slice property can improve query performance by overriding default slices generated for MOLAP and HOLAP partitions.</span></span> <span data-ttu-id="0d84e-105">또한 Slice 속성은 파티션을 처리할 때 추가 유효성 검사를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-105">Additionally, the Slice property provides an extra validation check when processing the partition.</span></span>  
  
 <span data-ttu-id="0d84e-106">파티션을 만든 후 처리하기 전에 Slice 속성을 사용하여 데이터 조각을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-106">You can specify a data slice after you create a partition, but before processing it, using the Slice property.</span></span> <span data-ttu-id="0d84e-107">파티션 탭에서 측정값 그룹을 확장하고 파티션을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-107">On the Partitions tab, expand a measure group, right-click a partition, and select **Properties**.</span></span>  
  
## <a name="defining-a-slice"></a><span data-ttu-id="0d84e-108">조각 정의</span><span class="sxs-lookup"><span data-stu-id="0d84e-108">Defining a Slice</span></span>  
 <span data-ttu-id="0d84e-109">Slice 속성으로 유효한 값은 MDX 멤버, 집합 또는 튜플입니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-109">Valid values for a slice property are an MDX member, set, or tuple.</span></span> <span data-ttu-id="0d84e-110">다음 예에서는 유효한 조각 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-110">The following examples illustrate valid slice syntax:</span></span>  
  
|<span data-ttu-id="0d84e-111">조각</span><span class="sxs-lookup"><span data-stu-id="0d84e-111">Slice</span></span>|<span data-ttu-id="0d84e-112">멤버, 집합 또는 튜플</span><span class="sxs-lookup"><span data-stu-id="0d84e-112">Member, set or tuple</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="0d84e-113">[Date].[Calendar].[Calendar Year].&[2010]</span><span class="sxs-lookup"><span data-stu-id="0d84e-113">[Date].[Calendar].[Calendar Year].&[2010]</span></span>|<span data-ttu-id="0d84e-114">2010년의 팩트를 포함하는 파티션에 이 조각을 지정합니다. 이때 모델에 Calendar Year 계층이 있고 2010이 멤버인 Date 차원이 포함되어 있는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-114">Specify this slice on a partition containing facts from year 2010 (assuming the model includes a Date dimension with Calendar Year hierarchy, where 2010 is a member).</span></span> <span data-ttu-id="0d84e-115">파티션 원본 WHERE 절 또는 테이블이 이미 2010을 기준으로 필터링할 수 있지만 Slice를 지정하면 처리하는 중에 추가 검사뿐 아니라 쿼리 실행 중에 더 구체적으로 대상이 지정된 검색도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-115">Although the partition source WHERE clause or table might already filter by 2010, specifying the Slice provides an additional check during processing, as well as more targeted scans during query execution.</span></span>|  
|<span data-ttu-id="0d84e-116">{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }</span><span class="sxs-lookup"><span data-stu-id="0d84e-116">{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }</span></span>|<span data-ttu-id="0d84e-117">영업 지역 정보를 포함하는 팩트가 포함된 파티션에 이 조각을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-117">Specify this slice on a partition containing facts that include sales territory information.</span></span> <span data-ttu-id="0d84e-118">조각은 두 개 이상의 멤버로 구성된 MDX 집합일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-118">A slice can be an MDX set consisting of two or more members.</span></span>|  
|<span data-ttu-id="0d84e-119">[Measures].[Sales Amount Quota] > '5000'</span><span class="sxs-lookup"><span data-stu-id="0d84e-119">[Measures].[Sales Amount Quota] > '5000'</span></span>|<span data-ttu-id="0d84e-120">이 조각은 MDX 식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-120">This slice shows an MDX expression.</span></span>|  
  
 <span data-ttu-id="0d84e-121">파티션의 데이터 조각에는 파티션의 데이터가 아주 자세히 반영되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-121">A data slice of a partition should reflect, as closely as possible, the data in the partition.</span></span> <span data-ttu-id="0d84e-122">예를 들어 파티션이 2012년 데이터로 제한되는 경우에는 파티션의 데이터 조각이 시간 차원의 2012년 멤버를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-122">For example, if a partition is limited to 2012 data, the partition's data slice should specify the 2012 member of the Time dimension.</span></span> <span data-ttu-id="0d84e-123">파티션의 내용을 정확히 반영하는 데이터 조각을 지정하는 것이 항상 가능한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-123">It is not always possible to specify a data slice that reflects the exact contents of a partition.</span></span> <span data-ttu-id="0d84e-124">예를 들어 파티션에는 1월과 2월에 대한 데이터만 있지만 시간 차원의 수준은 Year, Quarter, Month인 경우에는 파티션 마법사로 1월과 2월 멤버를 모두 선택할 수 있는 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-124">For example, if a partition contains data for only January and February, but the levels of the Time dimension are Year, Quarter, and Month, the Partition Wizard cannot select both the January and February members.</span></span> <span data-ttu-id="0d84e-125">이러한 경우에는 파티션의 내용이 반영된 멤버의 부모를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-125">In such cases, select the parent of the members that reflect the partition's contents.</span></span> <span data-ttu-id="0d84e-126">이 예에서는 Quarter 1을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-126">In this example, select Quarter 1.</span></span>  
  
 <span data-ttu-id="0d84e-127">데이터 조각의 이점에 대한 설명은 [SSAS 큐브 파티션에 조각 설정](https://go.microsoft.com/fwlink/?LinkId=317783)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d84e-127">For an explanation of data slice benefits, see [Set the Slice on your SSAS Cube Partition](https://go.microsoft.com/fwlink/?LinkId=317783).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d84e-128">동적 MDX 함수(예: [Generate&#40;MDX&#41;](/sql/mdx/generate-mdx) 또는 [Except&#40;MDX&#41;](/sql/mdx/except-mdx-function))는 파티션에 대한 Slice 속성에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-128">Note that dynamic MDX functions (such as [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) or [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) are not supported in the Slice property for partitions.</span></span> <span data-ttu-id="0d84e-129">명시적 튜플 또는 멤버 참조를 사용하여 조각을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-129">You must define the slice by using explicit tuples or member references.</span></span>  
>   
>  <span data-ttu-id="0d84e-130">예를 들어 &#40;범위를 사용 하 여 범위를 정의 하는 [&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) 함수를 사용 하는 대신 특정 연도를 기준으로 각 멤버를 열거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-130">For example, rather than using the [: &#40;Range&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) function to define a range, you would need to enumerate each member by the specific years.</span></span>  
>   
>  <span data-ttu-id="0d84e-131">복잡한 조각을 정의해야 하는 경우 XMLA Alter 스크립트를 사용하여 조각에서 튜플을 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-131">If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script.</span></span> <span data-ttu-id="0d84e-132">그런 다음 ascmd 명령줄 도구 또는 SSIS [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) 를 사용하여 스크립트를 실행하고 지정된 멤버 집합을 만든 후 곧바로 파티션을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d84e-132">Then, you can use either the ascmd command-line tool or the SSIS [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) task to run the script and create the specified set of members immediately before you process the partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d84e-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d84e-133">See Also</span></span>  
 [<span data-ttu-id="0d84e-134">로컬 파티션 만들기 및 관리&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0d84e-134">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](create-and-manage-a-local-partition-analysis-services.md)  
  
  
