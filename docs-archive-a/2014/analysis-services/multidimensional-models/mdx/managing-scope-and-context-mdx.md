---
title: 범위 및 컨텍스트 관리 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], context
- scope [MDX]
- CALCULATE statement
- This function [MDX]
- SCOPE statement
- scripts [MDX], scope
ms.assetid: 631e7c20-8be9-4c35-8609-76516aef19d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: f7cf1e6cea8df00b632e114a5a8756373738ca6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649738"
---
# <a name="managing-scope-and-context-mdx"></a><span data-ttu-id="512ed-102">범위 및 컨텍스트 관리(MDX)</span><span class="sxs-lookup"><span data-stu-id="512ed-102">Managing Scope and Context (MDX)</span></span>
  <span data-ttu-id="512ed-103">에서 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] MDX (Multidimensional Expressions) 스크립트는 스크립트 실행 내의 특정 지점에서 전체 큐브나 큐브의 특정 부분에 적용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a Multidimensional Expressions (MDX) script can apply to the entire cube, or to specific portions of the cube, at specific points within the execution of the script.</span></span> <span data-ttu-id="512ed-104">MDX 스크립트는 계산 패스를 사용하여 큐브 내에서의 계산에 계층화된 방법을 취할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-104">The MDX script can take a layered approach to calculations within a cube through the use of calculation passes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="512ed-105">계산 패스가 계산에 미치는 영향에 대한 자세한 내용은 [패스 순서 및 계산 순서 이해&#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="512ed-105">For more information on how calculation passes can affect calculations, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
 <span data-ttu-id="512ed-106">MDX 스크립트 내에서 계산 패스, 범위 및 컨텍스트를 제어하려면 특히 CALCULATE 문, `This` 함수 및 SCOPE 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-106">To control the calculation pass, scope, and context within an MDX script, you specifically use the CACULATE statement, the `This` function, and the SCOPE statement.</span></span>  
  
## <a name="using-the-calculate-statement"></a><span data-ttu-id="512ed-107">CALCULATE 문 사용</span><span class="sxs-lookup"><span data-stu-id="512ed-107">Using the CALCULATE Statement</span></span>  
 <span data-ttu-id="512ed-108">CALCULATE 문은 큐브의 각 셀을 집계된 데이터로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-108">The CALCULATE statement populates each cell in the cube with aggregated data.</span></span> <span data-ttu-id="512ed-109">예를 들어 기본 MDX 스크립트는 스크립트 시작 부분에 CALCULATE 문이 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-109">For example, the default MDX script has a single CALCULATE statement at the beginning of the script.</span></span>  
  
 <span data-ttu-id="512ed-110">CALCULATE 문의 구문에 대한 자세한 내용은 [CALCULATE 문&#40;MDX&#41;](/sql/mdx/mdx-scripting-calculate)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="512ed-110">For more information on the syntax of the CALCULATE statement, see [CALCULATE Statement &#40;MDX&#41;](/sql/mdx/mdx-scripting-calculate).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="512ed-111">스크립트에 CALCULATE 문을 포함한 SCOPE 문이 들어 있는 경우 MDX는 전체 큐브에 대해서가 아니라 SCOPE 문으로 정의되는 하위 큐브의 컨텍스트 내에서 CALCULATE 문을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-111">If the script contains a SCOPE statement that contains a CALCULATE statement, MDX evaluates the CALCULATE statement within the context of the subcube defined by the SCOPE statement, not against the whole cube.</span></span>  
  
## <a name="using-the-this-function"></a><span data-ttu-id="512ed-112">This 함수 사용</span><span class="sxs-lookup"><span data-stu-id="512ed-112">Using the This Function</span></span>  
 <span data-ttu-id="512ed-113">`This` 함수를 사용하면 MDX 스크립트 내의 현재 하위 큐브를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-113">The `This` function lets you retrieve the current subcube within an MDX script.</span></span> <span data-ttu-id="512ed-114">`This` 함수를 사용하여 현재 하위 큐브 내에 있는 셀의 값을 MDX 식으로 빠르게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-114">You can use the `This` function to quickly set the value of cells within the current subcube to an MDX expression.</span></span> <span data-ttu-id="512ed-115">SCOPE 문과 함께 `This` 함수를 사용하여 특정 계산 패스 중에 특정 하위 큐브의 내용을 변경하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-115">You often use the `This` function in conjunction with the SCOPE statement to change the contents of a specific subcube during a specific calculation pass.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="512ed-116">스크립트에 `This` 함수를 포함한 SCOPE 문이 들어 있는 경우 MDX는 전체 큐브에 대해서가 아니라 SCOPE 문으로 정의되는 하위 큐브의 컨텍스트 내에서 `This` 함수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-116">If the script contains a SCOPE statement that contains a `This` function, MDX evaluates the `This` function within the context of the subcube defined by the SCOPE statement, not against the whole cube.</span></span>  
  
### <a name="this-function-example"></a><span data-ttu-id="512ed-117">This 함수 예</span><span class="sxs-lookup"><span data-stu-id="512ed-117">This Function Example</span></span>  
 <span data-ttu-id="512ed-118">다음 MDX 스크립트 명령 예에서는 `This` 함수를 사용하여 [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] 샘플 큐브의 Finance 측정값 그룹에 있는 Amount 측정값을 Customer 차원에 있는 Redmond 멤버의 자식에 대해 10% 증가시키는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-118">The following MDX script command example uses the `This` function to increase the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension:</span></span>  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 <span data-ttu-id="512ed-119">함수 구문에 대 한 자세한 내용은 `This` [이 &#40;MDX&#41;](/sql/mdx/this-mdx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="512ed-119">For more information on the syntax of the `This` function, see [This &#40;MDX&#41;](/sql/mdx/this-mdx).</span></span>  
  
## <a name="using-the-scope-statement"></a><span data-ttu-id="512ed-120">SCOPE 문 사용</span><span class="sxs-lookup"><span data-stu-id="512ed-120">Using the SCOPE Statement</span></span>  
 <span data-ttu-id="512ed-121">SCOPE 문은 MDX 스크립트 내의 다른 MDX 식과 문을 포함하고 해당 범위를 지정하는 현재 하위 큐브를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-121">The SCOPE statement defines the current subcube that contains, and specifies the scope of, other MDX expressions and statements within an MDX script.</span></span> <span data-ttu-id="512ed-122">MDX는 하위 큐브의 컨텍스트 내에서 `This` 함수와 CALCULATE 문을 포함하여 이런 다른 MDX 식과 문을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-122">MDX evaluates this other MDX expressions and statements, including the `This` function and the CALCULATE statement, within the context of the subcube.</span></span>  
  
 <span data-ttu-id="512ed-123">SCOPE 문은 동적이지만 특성상 반복적이지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-123">A SCOPE statement is dynamic, but not iterative in nature.</span></span> <span data-ttu-id="512ed-124">SCOPE 문 내에 포함된 문은 한 번 실행되지만 하위 큐브 자체는 동적으로 결정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-124">The statements contained within a SCOPE statement run once, but the subcube itself can be dynamically determined.</span></span> <span data-ttu-id="512ed-125">예를 들어 SampleCube라는 큐브가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-125">For example, you have a cube named SampleCube.</span></span> <span data-ttu-id="512ed-126">SampleCube 큐브에 대해 다음 SCOPE 문을 적용하여 컨텍스트를 측정값 차원 내의 ALLMEMBERS로 정의하는 하위 큐브를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-126">Against the SampleCube cube, you apply the following SCOPE statement to define a subcube the defines the context as the ALLMEMBERS within the Measures dimension:</span></span>  
  
 `SCOPE([Measures].ALLMEMBERS);`  
  
 `THIS = [Measures].ALLMEMBERS.COUNT;`  
  
 `END SCOPE;`  
  
 <span data-ttu-id="512ed-127">이 SCOPE 문 내부의 문과 식은 한 번 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-127">The statements and expressions within this SCOPE statement run once.</span></span>  
  
 <span data-ttu-id="512ed-128">이제 어떤 업무용 사용자가 SampleCube 큐브에 대해 ExistingMeasure라는 측정값을 하나 포함한 다음 MDX 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-128">Now, a business user runs the following MDX query that contains one measure, named ExistingMeasure, against the SampleCube cube:</span></span>  
  
 `WITH MEMBER [Measures].[NewMeasure] AS '1'`  
  
 `SELECT`  
  
 `[Measures].ALLMEMBERS ON COLUMNS,`  
  
 `[Customer].DEFAULTMEMBER ON ROWS`  
  
 `FROM`  
  
 `[SampleCube]`  
  
 <span data-ttu-id="512ed-129">쿼리에서 반환하는 셀 집합은 다음 테이블에 표시된 출력과 비슷한 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-129">The cellset returned from the query resembles the output shown in the following table.</span></span>  
  
||<span data-ttu-id="512ed-130">[ExistingMeasure]</span><span class="sxs-lookup"><span data-stu-id="512ed-130">[ExistingMeasure]</span></span>|<span data-ttu-id="512ed-131">[NewMeasure]</span><span class="sxs-lookup"><span data-stu-id="512ed-131">[NewMeasure]</span></span>|  
|-|-------------------------|--------------------|  
|<span data-ttu-id="512ed-132">[Customer].[All]</span><span class="sxs-lookup"><span data-stu-id="512ed-132">[Customer].[All]</span></span>|<span data-ttu-id="512ed-133">2</span><span class="sxs-lookup"><span data-stu-id="512ed-133">2</span></span>|<span data-ttu-id="512ed-134">2</span><span class="sxs-lookup"><span data-stu-id="512ed-134">2</span></span>|  
  
 <span data-ttu-id="512ed-135">반환된 셀 집합을 보고서 NewMeasure 측정값을 정의한 후 MDX 스크립트 내의 SCOPE 문에 포함된 ExistingMeasure 값이 동적으로 업데이트되는 방법을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-135">Looking at the returned cellset, notice how the ExistingMeasure value, included in the SCOPE statement within the MDX script, is dynamically updated after the measure NewMeasure was defined.</span></span>  
  
 <span data-ttu-id="512ed-136">SCOPE 문은 다른 SCOPE 문 내에 중첩될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-136">A SCOPE statement can be nested within another SCOPE statement.</span></span> <span data-ttu-id="512ed-137">하지만 SCOPE 문은 반복적이지 않으므로 SCOPE 문을 중첩하는 주 목적은 특수 처리를 위해 하위 큐브를 보다 세분화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-137">However, as the SCOPE statement is not iterative, the primary purpose for nesting SCOPE statements is to further subdivide a subcube for special treatment.</span></span>  
  
### <a name="scope-statement-example"></a><span data-ttu-id="512ed-138">SCOPE 문의 예</span><span class="sxs-lookup"><span data-stu-id="512ed-138">SCOPE Statement Example</span></span>  
 <span data-ttu-id="512ed-139">다음 MDX 스크립트 예에서는 SCOPE 문을 사용하여 [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] 샘플 큐브의 Finance 측정값 그룹에 있는 Amount 측정값을 Customer 차원에 있는 Redmond 멤버의 자식에 대해 10% 높게 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-139">The following MDX script example uses a SCOPE statement to sets the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension.</span></span> <span data-ttu-id="512ed-140">하지만 또 다른 SCOPE 문은 하위 큐브를 변경하여 역년 기준 2002년도의 자식에 대한 Amount 측정값을 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-140">However, another SCOPE statement changes the subcube to include the Amount measure for the children of the 2002 calendar year.</span></span> <span data-ttu-id="512ed-141">마지막으로 Amount 측정값을 해당 하위 큐브에 대해서만 집계하고 다른 역년의 Amount 측정값에 대해 집계된 값은 바꾸지 않고 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="512ed-141">Finally, the Amount measure is then aggregated only for that subcube, leaving the aggregated values for the Amount measure in other calendar years unchanged.</span></span>  
  
```  
/* Calculate the entire cube first. */  
CALCULATE;  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 <span data-ttu-id="512ed-142">SCOPE 문의 구문에 대한 자세한 내용은 [SCOPE 문&#40;MDX&#41;](/sql/mdx/mdx-scripting-scope)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="512ed-142">For more information on the syntax of the SCOPE statement, see [SCOPE Statement &#40;MDX&#41;](/sql/mdx/mdx-scripting-scope).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512ed-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="512ed-143">See Also</span></span>  
 <span data-ttu-id="512ed-144">[Mdx 언어 참조 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="512ed-144">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 <span data-ttu-id="512ed-145">[MDX &#40;기본 MDX 스크립트&#41;](the-basic-mdx-script-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="512ed-145">[The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md) </span></span>  
 [<span data-ttu-id="512ed-146">MDX 쿼리 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="512ed-146">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
