---
title: 쿼리 및 Slicer 축 (MDX)을 사용 하 여 쿼리 제한 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed4d50aa40d2915c60f887e64cdc3ef8a6d52c5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734487"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a><span data-ttu-id="5d564-102">쿼리 및 Slicer 축으로 쿼리 제한(MDX)</span><span class="sxs-lookup"><span data-stu-id="5d564-102">Restricting the Query with Query and Slicer Axes (MDX)</span></span>
  <span data-ttu-id="5d564-103">MDX(Multidimensional Expressions) SELECT 쿼리를 구성할 때 애플리케이션에서는 일반적으로 큐브를 검토하고 계층 집합을 다음과 같이 두 개의 하위 집합으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="5d564-103">When formulating a Multidimensional Expressions (MDX) SELECT statement, an application typically examines a cube and divides the set of hierarchies into two subsets:</span></span>  
  
-   <span data-ttu-id="5d564-104">**쿼리 축**-여러 멤버에 대해 데이터가 검색 되는 계층 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="5d564-104">**Query axes**-the set of hierarchies from which data is retrieved for multiple members.</span></span> <span data-ttu-id="5d564-105">쿼리 축에 대한 자세한 내용은 [쿼리 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d564-105">For more information about query axes, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
-   <span data-ttu-id="5d564-106">**Slicer 축**-단일 멤버에 대해 데이터가 검색 되는 계층 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="5d564-106">**Slicer axis**-the set of hierarchies from which data is retrieved for a single member.</span></span> <span data-ttu-id="5d564-107">Slicer 축에 대한 자세한 내용은 [Slicer 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d564-107">For more information about the slicer axis, see [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
 <span data-ttu-id="5d564-108">쿼리 및 slicer 축은 쿼리할 큐브의 여러 계층으로부터 구성될 수 있으므로, 이러한 용어는 MDX 쿼리로 반환된 큐브에서 생성되는 계층으로부터 쿼리할 큐브가 사용하는 계층을 구분하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d564-108">Because query and slicer axes can be constructed from multiple hierarchies of the cube to be queried, these terms are used to differentiate the hierarchies used by the cube that is to be queried from the hierarchies created in the cube returned by an MDX query.</span></span>  
  
 <span data-ttu-id="5d564-109">쿼리 및 slicer 축을 사용하는 간단한 예제를 보려면 [간단한 예제에서 쿼리 및 Slicer 축 사용&#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d564-109">To see a simple example using query and slicer axes, see [Using Query and Slicer Axes in a Simple Example &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d564-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d564-110">See Also</span></span>  
 <span data-ttu-id="5d564-111">[MDX &#40;멤버, 튜플 및 집합을 사용 하 여 작업&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="5d564-111">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 [<span data-ttu-id="5d564-112">MDX 쿼리 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5d564-112">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
