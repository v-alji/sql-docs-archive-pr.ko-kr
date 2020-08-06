---
title: 쿼리에 큐브 컨텍스트 설정 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72ae6e19f879651feb47841d70b444e9f845c74e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727395"
---
# <a name="establishing-cube-context-in-a-query-mdx"></a><span data-ttu-id="d5276-102">쿼리에 큐브 컨텍스트 설정(MDX)</span><span class="sxs-lookup"><span data-stu-id="d5276-102">Establishing Cube Context in a Query (MDX)</span></span>
  <span data-ttu-id="d5276-103">모든 MDX 쿼리는 지정된 큐브 컨텍스트 내에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-103">Every MDX query runs within a specified cube context.</span></span> <span data-ttu-id="d5276-104">이 컨텍스트는 쿼리 내의 식에 의해 계산되는 멤버를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-104">This context defines the members that are evaluated by the expressions within the query.</span></span>  
  
 <span data-ttu-id="d5276-105">SELECT 문에서 FROM 절은 큐브 컨텍스트를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-105">In the SELECT statement, the FROM clause determines the cube context.</span></span> <span data-ttu-id="d5276-106">이 컨텍스트는 전체 큐브이거나 해당 큐브의 하위 큐브일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-106">This context can be the whole cube or just a subcube from that cube.</span></span> <span data-ttu-id="d5276-107">FROM 절을 통해 큐브 컨텍스트를 지정한 경우 추가 함수를 사용하여 해당 큐브를 확장하거나 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-107">Having specified cube context through the FROM clause, you can use additional functions to expand or restrict that context.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5276-108">SCOPE 및 CALCULATE 문을 사용하면 MDX 스크립트 내에서 큐브 컨텍스트를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-108">The SCOPE and CALCULATE statements also let you manage cube context from within an MDX script.</span></span> <span data-ttu-id="d5276-109">자세한 내용은 [MDX 스크립팅 기본 사항&#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5276-109">For more information, see [MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md).</span></span>  
  
## <a name="from-clause-syntax"></a><span data-ttu-id="d5276-110">FROM 절 구문</span><span class="sxs-lookup"><span data-stu-id="d5276-110">FROM Clause Syntax</span></span>  
 <span data-ttu-id="d5276-111">다음 구문은 FROM 절에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-111">The following syntax describes the FROM clause:</span></span>  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 <span data-ttu-id="d5276-112">이 구문에서 `<SELECT subcube clause>` 절은 SELECT 문이 실행되는 큐브 또는 하위 큐브를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-112">In this syntax, notice that it is the `<SELECT subcube clause>` clause that describes the cube or subcube on which the SELECT statement is executed.</span></span>  
  
 <span data-ttu-id="d5276-113">FROM 절의 간단한 예로는 전체 Adventure Works 예제 큐브에 대해 실행되는 절을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-113">A simple example of a FROM clause would be one that runs against the entire Adventure Works sample cube.</span></span> <span data-ttu-id="d5276-114">이러한 FROM 절의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-114">Such a FROM clause would have the following format:</span></span>  
  
```  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="d5276-115">MDX SELECT 문의 FROM 절에 대한 자세한 내용은 [SELECT 문&#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5276-115">For more information about the FROM clause in the MDX SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
## <a name="refining-the-context"></a><span data-ttu-id="d5276-116">컨텍스트 구체화</span><span class="sxs-lookup"><span data-stu-id="d5276-116">Refining the Context</span></span>  
 <span data-ttu-id="d5276-117">FROM 절은 단일 큐브 내의 큐브 컨텍스트를 지정하지만 한 번에 하나 이상의 데이터를 사용하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-117">Although the FROM clause specifies the cube context as within a single cube, this does not have to limit you from working with data from more than one cube at a time.</span></span>  
  
 <span data-ttu-id="d5276-118">MDX [LookupCube](/sql/mdx/lookupcube-mdx) 함수를 사용하면 큐브 컨텍스트 외부의 다른 큐브에서 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-118">You can use the MDX [LookupCube](/sql/mdx/lookupcube-mdx) function to retrieve data from cubes outside the cube context.</span></span> <span data-ttu-id="d5276-119">또한 [Filter](/sql/mdx/filter-mdx) 함수 등을 사용하여 쿼리를 계산할 때 컨텍스트를 임시적으로 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5276-119">Additionally, functions such as the [Filter](/sql/mdx/filter-mdx) function, are available that allow temporary restriction of the context while evaluating the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5276-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5276-120">See Also</span></span>  
 [<span data-ttu-id="d5276-121">MDX 쿼리 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d5276-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
