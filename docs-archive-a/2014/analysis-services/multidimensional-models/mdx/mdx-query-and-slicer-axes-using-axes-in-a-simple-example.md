---
title: 간단한 예에서 쿼리 및 Slicer 축 사용 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 324f082fd6659592e56af65680bd4aa623c625d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653024"
---
# <a name="using-query-and-slicer-axes-in-a-simple-example-mdx"></a><span data-ttu-id="21dc9-102">간단한 예에서 쿼리 및 Slicer 축 사용(MDX)</span><span class="sxs-lookup"><span data-stu-id="21dc9-102">Using Query and Slicer Axes in a Simple Example (MDX)</span></span>
  <span data-ttu-id="21dc9-103">이 항목에 제시된 예에서는 쿼리 및 slicer 축을 지정 및 사용하는 기본적인 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="21dc9-103">The simple example presented in this topic illustrates the basics of specifying and using query and slicer axes.</span></span>  
  
## <a name="the-cube"></a><span data-ttu-id="21dc9-104">큐브</span><span class="sxs-lookup"><span data-stu-id="21dc9-104">The Cube</span></span>  
 <span data-ttu-id="21dc9-105">Route 및 Time이라는 두 개의 간단한 차원을 가진 TestCube라는 이름의 큐브가 있는 경우</span><span class="sxs-lookup"><span data-stu-id="21dc9-105">A cube, named TestCube, has two simple dimensions named Route and Time.</span></span> <span data-ttu-id="21dc9-106">각 차원은 Route 및 Time으로 명명된 한 개의 사용자 계층만 가집니다.</span><span class="sxs-lookup"><span data-stu-id="21dc9-106">Each dimension has only one user hierarchy, named Route and Time respectively.</span></span> <span data-ttu-id="21dc9-107">큐브의 측정값은 Measures 차원의 일부이므로 이 큐브에는 모두 3개의 차원이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21dc9-107">Because the measures of the cube are part of the Measures dimension, this cube has three dimensions in all.</span></span>  
  
## <a name="the-query"></a><span data-ttu-id="21dc9-108">쿼리</span><span class="sxs-lookup"><span data-stu-id="21dc9-108">The Query</span></span>  
 <span data-ttu-id="21dc9-109">쿼리는 Packages 측정값을 경로와 횟수를 기준으로 비교할 수 있는 매트릭스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="21dc9-109">The query is to provide a matrix in which the Packages measure can be compared across routes and times.</span></span>  
  
 <span data-ttu-id="21dc9-110">다음 MDX 쿼리 예에서 Route와 Time 계층은 쿼리 축이며 Measures 차원은 slicer 축입니다.</span><span class="sxs-lookup"><span data-stu-id="21dc9-110">In the following MDX query example, the Route and Time hierarchies are the query axes, and the Measures dimension is the slicer axis.</span></span> <span data-ttu-id="21dc9-111">[Members](/sql/mdx/members-set-mdx) 함수는 MDX가 계층 또는 수준의 멤버를 사용하여 집합을 만들 것임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="21dc9-111">The [Members](/sql/mdx/members-set-mdx) function indicates that MDX will use the members of the hierarchy or level to construct a set.</span></span> <span data-ttu-id="21dc9-112">`Members` 함수를 사용하면 MDX 쿼리에서 특정 계층 또는 수준의 각 멤버를 명시적으로 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21dc9-112">The use of the `Members` function means that you do not have to explicitly state each member of a specific hierarchy or level in an MDX query.</span></span>  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a><span data-ttu-id="21dc9-113">결과</span><span class="sxs-lookup"><span data-stu-id="21dc9-113">The Results</span></span>  
 <span data-ttu-id="21dc9-114">결과는 COLUMNS와 ROWS 축 차원의 각 교차 위치에서 Packages 측정값을 보여 주는 표입니다.</span><span class="sxs-lookup"><span data-stu-id="21dc9-114">The result is a grid that identifies the value of the Packages measure at each intersection of the COLUMNS and ROWS axis dimensions.</span></span> <span data-ttu-id="21dc9-115">다음 표에서는 이 표의 모양을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="21dc9-115">The following table shows how this grid would look.</span></span>  
  
||<span data-ttu-id="21dc9-116">air</span><span class="sxs-lookup"><span data-stu-id="21dc9-116">air</span></span>|<span data-ttu-id="21dc9-117">sea</span><span class="sxs-lookup"><span data-stu-id="21dc9-117">sea</span></span>|  
|-|---------|---------|  
|<span data-ttu-id="21dc9-118">1st quarter</span><span class="sxs-lookup"><span data-stu-id="21dc9-118">1st quarter</span></span>|<span data-ttu-id="21dc9-119">60</span><span class="sxs-lookup"><span data-stu-id="21dc9-119">60</span></span>|<span data-ttu-id="21dc9-120">50</span><span class="sxs-lookup"><span data-stu-id="21dc9-120">50</span></span>|  
|<span data-ttu-id="21dc9-121">2nd quarter</span><span class="sxs-lookup"><span data-stu-id="21dc9-121">2nd quarter</span></span>|<span data-ttu-id="21dc9-122">45</span><span class="sxs-lookup"><span data-stu-id="21dc9-122">45</span></span>|<span data-ttu-id="21dc9-123">45</span><span class="sxs-lookup"><span data-stu-id="21dc9-123">45</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21dc9-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21dc9-124">See Also</span></span>  
 <span data-ttu-id="21dc9-125">[MDX&#41;&#40;쿼리 축의 내용 지정](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) </span><span class="sxs-lookup"><span data-stu-id="21dc9-125">[Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) </span></span>  
 [<span data-ttu-id="21dc9-126">Slicer 축의 내용 지정&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="21dc9-126">Specifying the Contents of a Slicer Axis &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
