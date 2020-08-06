---
title: MDX 쿼리 기본 사항 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- statements [MDX]
- Multidimensional Expressions [Analysis Services], statements
- Multidimensional Expressions [Analysis Services], queries
- MDX [Analysis Services], statements
- MDX queries [Analysis Services]
- MDX [Analysis Services], queries
- queries [MDX]
ms.assetid: a560383b-bb58-472e-95f5-65d03d8ea08b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1a2a9a4f564bc33cc7a1b41a1a4c766c7a76a2cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653611"
---
# <a name="mdx-query-fundamentals-analysis-services"></a><span data-ttu-id="5e3e3-102">MDX 쿼리 기본 사항(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="5e3e3-102">MDX Query Fundamentals (Analysis Services)</span></span>
  <span data-ttu-id="5e3e3-103">MDX를 사용하면 큐브와 같은 다차원 개체를 쿼리하여 큐브의 데이터를 포함하는 다차원 셀 집합을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-103">Multidimensional Expressions (MDX) lets you query multidimensional objects, such as cubes, and return multidimensional cellsets that contain the cube's data.</span></span> <span data-ttu-id="5e3e3-104">이 항목 및 하위 항목에서는 MDX 쿼리에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-104">This topic and its subtopics provide an overview of MDX queries.</span></span>  
  
 <span data-ttu-id="5e3e3-105">다음 항목에서는 MDX 쿼리 및 쿼리가 만드는 셀 집합에 대해 설명하고 기본적인 MDX 구문에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-105">The following topics describe MDX queries and the cellsets they produce, and provide more detailed information about basic MDX syntax.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e3e3-106">MDX 쿼리 및 계산과 관련 된 성능 문제에 대 한 자세한 내용은 [SQL Server 2005 Analysis Services 성능 가이드](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)의 "효율적인 MDX 작성" 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-106">For more information about performance issues related to MDX queries and calculations, see the section "Writing Efficient MDX" in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5e3e3-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5e3e3-107">In This Section</span></span>  
  
|<span data-ttu-id="5e3e3-108">항목</span><span class="sxs-lookup"><span data-stu-id="5e3e3-108">Topic</span></span>|<span data-ttu-id="5e3e3-109">Description</span><span class="sxs-lookup"><span data-stu-id="5e3e3-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5e3e3-110">기본 MDX 쿼리&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-110">The Basic MDX Query &#40;MDX&#41;</span></span>](mdx-query-the-basic-query.md)|<span data-ttu-id="5e3e3-111">MDX SELECT 문의 기본 구문에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-111">Provides basic syntax information for the MDX SELECT statement.</span></span>|  
|[<span data-ttu-id="5e3e3-112">쿼리 및 Slicer 축으로 쿼리 제한&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-112">Restricting the Query with Query and Slicer Axes &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-restricting-the-query.md)|<span data-ttu-id="5e3e3-113">쿼리 및 slicer 축의 의미 및 지정 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-113">Describes what query and slicer axes are and how to specify them.</span></span>|  
|[<span data-ttu-id="5e3e3-114">쿼리에 큐브 컨텍스트 설정&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-114">Establishing Cube Context in a Query &#40;MDX&#41;</span></span>](establishing-cube-context-in-a-query-mdx.md)|<span data-ttu-id="5e3e3-115">MDX SELECT 문에서 FROM 절을 사용하는 목적을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-115">Provides a description of the purpose of the FROM clause in an MDX SELECT statement.</span></span>|  
|[<span data-ttu-id="5e3e3-116">명명된 집합을 MDX로 작성&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-116">Building Named Sets in MDX &#40;MDX&#41;</span></span>](mdx-named-sets-building-named-sets.md)|<span data-ttu-id="5e3e3-117">MDX에서 명명된 집합을 사용하는 목적과 MDX 쿼리에서 명명된 집합을 만들고 사용하는 데 필요한 기술을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-117">Describes the purpose of named sets in MDX, and the techniques needed to create and use them in MDX queries.</span></span>|  
|[<span data-ttu-id="5e3e3-118">계산 멤버를 MDX로 작성&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-118">Building Calculated Members in MDX &#40;MDX&#41;</span></span>](mdx-calculated-members-building-calculated-members.md)|<span data-ttu-id="5e3e3-119">MDX의 계산 멤버에 대해 설명하고 MDX 식에서 계산 멤버를 만들고 사용하는 데 필요한 기술을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-119">Provides information about calculated members in MDX, including the techniques needed to create and use them in MDX expressions.</span></span>|  
|[<span data-ttu-id="5e3e3-120">MDX로 셀 계산 작성&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-120">Building Cell Calculations in MDX &#40;MDX&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/calculations.md)|<span data-ttu-id="5e3e3-121">계산 셀을 만들고 사용하는 과정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-121">Details the process of creating and using calculated cells.</span></span>|  
|[<span data-ttu-id="5e3e3-122">속성 값 만들기 및 사용&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-122">Creating and Using Property Values &#40;MDX&#41;</span></span>](../../creating-and-using-property-values-mdx.md)|<span data-ttu-id="5e3e3-123">차원, 수준, 멤버 및 셀 속성을 만들고 사용하는 과정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-123">Details the process of creating and using dimension, level, member, and cell properties.</span></span>|  
|[<span data-ttu-id="5e3e3-124">데이터 조작&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-124">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)|<span data-ttu-id="5e3e3-125">드릴스루 및 롤업을 사용하는 데이터 조작법에 대한 기본 지식 및 MDX의 패스 순서 및 계산 순서를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-125">Describes the basics behind manipulating data using drillthrough and rollup, and also describes pass order and solve order in MDX.</span></span>|  
|[<span data-ttu-id="5e3e3-126">데이터 수정&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-126">Modifying Data &#40;MDX&#41;</span></span>](mdx-data-modification-modifying-data.md)|<span data-ttu-id="5e3e3-127">쓰기 저장(writeback)을 사용하여 다차원 데이터를 일시적 또는 영구적으로 변경하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-127">Describes how to use writebacks to temporarily or permanently change multidimensional data.</span></span>|  
|[<span data-ttu-id="5e3e3-128">변수 및 매개 변수 사용&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5e3e3-128">Using Variables and Parameters &#40;MDX&#41;</span></span>](using-variables-and-parameters-mdx.md)|<span data-ttu-id="5e3e3-129">MDX 쿼리에서 변수와 매개 변수를 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e3e3-129">Describes how to use variables and parameters within MDX queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e3e3-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e3e3-130">See Also</span></span>  
 [<span data-ttu-id="5e3e3-131">MDX&#40;Multidimensional Expression&#41; 참조</span><span class="sxs-lookup"><span data-stu-id="5e3e3-131">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
