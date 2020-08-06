---
title: 데이터 조작 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 4865192e-f46b-4ce5-b51c-9e08dbad5b85
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1a1de8b9a3431d79573cd916fa7273b6d8fa7f0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651357"
---
# <a name="manipulating-data-mdx"></a><span data-ttu-id="193be-102">데이터 조작(MDX)</span><span class="sxs-lookup"><span data-stu-id="193be-102">Manipulating Data (MDX)</span></span>

<span data-ttu-id="193be-103">MDX를 사용하여 다양한 방법으로 데이터를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="193be-103">Multidimensional Expressions (MDX) can be used to manipulate the data in a variety of ways.</span></span> <span data-ttu-id="193be-104">이 문서에 나열 된 문서는 MDX 언어에서 데이터 조작의 고급 개념 중 일부를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="193be-104">The article listed in this article cover some of the more advanced concepts of data manipulation in the MDX language.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="193be-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="193be-105">In This Section</span></span>

|<span data-ttu-id="193be-106">항목</span><span class="sxs-lookup"><span data-stu-id="193be-106">Topic</span></span>|<span data-ttu-id="193be-107">Description</span><span class="sxs-lookup"><span data-stu-id="193be-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="193be-108">DRILLTHROUGH를 사용하여 원본 데이터 검색&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="193be-108">Using DRILLTHROUGH to Retrieve Source Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-retrieve-source-data-using-drillthrough.md)|<span data-ttu-id="193be-109">다차원 데이터 원본의 셀에 적용될 수 있는 원본 데이터의 행 집합 검색을 위한 MDX [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) 문 사용에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="193be-109">Discusses the use of the MDX [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) statement to retrieve the rowsets of source data applicable to a cell in a multidimensional data source</span></span>|  
|[<span data-ttu-id="193be-110">RollupChildren 함수 작업&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="193be-110">Working with the RollupChildren Function &#40;MDX&#41;</span></span>](mdx-data-manipulation-rollupchildren-function.md)|<span data-ttu-id="193be-111">MDX [RollupChildren](/sql/mdx/rollupchildren-mdx) 의 영향을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="193be-111">Discusses the impact of the MDX [RollupChildren](/sql/mdx/rollupchildren-mdx)</span></span>
|[<span data-ttu-id="193be-112">패스 순서 및 계산 순서 이해&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="193be-112">Understanding Pass Order and Solve Order &#40;MDX&#41;</span></span>](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|<span data-ttu-id="193be-113">계산 순서의 개념과 이 기능이 MDX 식, 문 및 스크립트에 어떤 영향을 주는지 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="193be-113">Details the concepts of solve order, and how this feature affects MDX expressions, statements, and scripts.</span></span>|  

<!-- ??

|[Script for Search and Replace] function on the analysis of multidimensional data.|

GeneMi is removing this commented row because it is unclear what article its link meant to link to.
Also, I had to add its leading '|' character, for consistency to aid bulk automated updated to our markdown source code.

GeneMi , 2019/01/19
-->

## <a name="see-also"></a><span data-ttu-id="193be-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="193be-114">See Also</span></span>

[<span data-ttu-id="193be-115">MDX 쿼리 기본 사항(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="193be-115">MDX Query Fundamentals (Analysis Services)</span></span>](mdx-query-fundamentals-analysis-services.md)
