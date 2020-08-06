---
title: 기본 MDX 스크립트 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default MDX scripts
- statements [MDX]
- expressions [MDX], scripts
- scripts [MDX], about scripts
ms.assetid: 83d9afda-7d34-42b5-8f28-20172a905f23
author: minewiskan
ms.author: owend
ms.openlocfilehash: de0d2fea002beda0eca480bd27140bdd202fcb83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737005"
---
# <a name="the-basic-mdx-script-mdx"></a><span data-ttu-id="a44ca-102">기본 MDX 스크립트(MDX)</span><span class="sxs-lookup"><span data-stu-id="a44ca-102">The Basic MDX Script (MDX)</span></span>
  <span data-ttu-id="a44ca-103">MDX (Multidimensional Expressions) 스크립트는의 큐브에 대 한 계산 프로세스를 정의 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-103">A Multidimensional Expressions (MDX) script defines the calculation process for a cube in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a44ca-104">다음과 같은 두 가지 유형의 MDX 스크립트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-104">There are two types of MDX scripts:</span></span>  
  
 <span data-ttu-id="a44ca-105">**기본 MDX 스크립트**</span><span class="sxs-lookup"><span data-stu-id="a44ca-105">**The default MDX script**</span></span>  
 <span data-ttu-id="a44ca-106">큐브를 만드는 시점에 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 는 해당 큐브에 대해 기본 MDX 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-106">At the time that you create a cube, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] creates a default MDX script for that cube.</span></span> <span data-ttu-id="a44ca-107">이 스크립트는 전체 큐브에 대한 계산 패스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-107">This script defines a calculation pass for the whole cube.</span></span>  
  
 <span data-ttu-id="a44ca-108">**사용자 정의 MDX 스크립트**</span><span class="sxs-lookup"><span data-stu-id="a44ca-108">**User-defined MDX script**</span></span>  
 <span data-ttu-id="a44ca-109">큐브를 만든 후 큐브의 계산 기능을 확장하는 사용자 정의 MDX 스크립트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-109">After you have created a cube, you can add user-defined MDX scripts that extend the calculation capabilities of the cube.</span></span>  
  
## <a name="the-default-mdx-script"></a><span data-ttu-id="a44ca-110">기본 MDX 스크립트</span><span class="sxs-lookup"><span data-stu-id="a44ca-110">The Default MDX Script</span></span>  
 <span data-ttu-id="a44ca-111">큐브를 정의할 때 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 가 만드는 기본 MDX 스크립트는 단 하나의 CALCULATE 문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-111">The default MDX script that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] creates when you define a cube contains a single CALCULATE statement.</span></span> <span data-ttu-id="a44ca-112">이 단일 CALCULATE 문은 기본 MDX 스크립트 시작 부분에 있고 첫 번째 계산 패스 중에 전체 큐브를 계산해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-112">This single CALCULATE statement is at the beginning of the default MDX script, and indicates that the entire cube should be calculated during the first calculation pass.</span></span>  
  
 <span data-ttu-id="a44ca-113">또한 기본 MDX 스크립트에는 큐브 디자이너에서 만든 명명된 집합, 대입 식 및 계산 멤버를 만드는 스크립트 명령도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-113">The default MDX script also contains the script commands that create named sets, assignments, and calculated members created in Cube Designer:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="a44ca-114">는 기본 MDX 스크립트에 스크립트 명령을 직접 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-114">directly adds script commands to the default MDX script.</span></span>  
  
-   <span data-ttu-id="a44ca-115">큐브에 있는 각각의 명명된 집합의 경우 해당 CREATE SET 문이 기본 MDX 스크립트에 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-115">For each named set in the cube, a corresponding CREATE SET statement exists in the default MDX script.</span></span>  
  
-   <span data-ttu-id="a44ca-116">큐브에서 정의한 각각의 계산 멤버의 경우 해당 CREATE MEMBER 문이 기본 MDX 스크립트에 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-116">For each calculated member defined in the cube, a corresponding CREATE MEMBER statement exists in the default MDX script.</span></span>  
  
 <span data-ttu-id="a44ca-117">큐브 디자이너의 **계산** 탭을 사용하여 기본 MDX 스크립트에 있는 스크립트 명령, 명명된 집합 및 계산 멤버의 순서를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-117">You can control the order of script commands, named sets, and calculated members in the default MDX script by using the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="a44ca-118">기본 MDX 스크립트에 저장된 계산 정의에 대한 자세한 내용은 [다차원 모델의 계산](../calculations-in-multidimensional-models.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a44ca-118">For more information on defining calculations stored in the default MDX script, see [Calculations in Multidimensional Models](../calculations-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="a44ca-119">큐브와 연결된 MDX 스크립트가 없는 경우 큐브는 기본 MDX 스크립트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-119">If there is no MDX script associated with a cube, the cube assumes the default MDX script.</span></span> <span data-ttu-id="a44ca-120">큐브는 MDX 스크립트에 따라 계산 동작을 결정하므로 큐브는 최소한 하나 이상의 MDX 스크립트와 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-120">A cube needs to be associated with at least one MDX script because a cube relies on the MDX script to determine calculation behavior.</span></span> <span data-ttu-id="a44ca-121">즉, MDX 스크립트와 연결되지 않았거나 빈 MDX 스크립트와 연결된 큐브는 어떤 셀도 계산하지 못할뿐더러 계산하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-121">In other words, a cube that was not associated with an MDX script or was associated with an empty MDX script could not and would not be able to calculate any cells.</span></span> <span data-ttu-id="a44ca-122">ASSL(Analysis Services Scripting Language) 명령 또는 AMO(Analysis Management Objects)를 사용하여 프로그래밍 방식으로 큐브를 만드는 경우에는 해당 큐브에 대해 단일 CALCULATE 문을 포함한 기본 MDX 스크립트를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-122">If you programmatically create cubes, either by using Analysis Services Scripting Language (ASSL) commands or by using Analysis Management Objects (AMO), it is recommended that you create a default MDX script containing a single CALCULATE statement for the cube.</span></span>  
  
## <a name="mdx-script-content"></a><span data-ttu-id="a44ca-123">MDX 스크립트 내용</span><span class="sxs-lookup"><span data-stu-id="a44ca-123">MDX Script Content</span></span>  
 <span data-ttu-id="a44ca-124">MDX 스크립트는 다음 문과 식을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-124">An MDX script can contain the following statements and expressions:</span></span>  
  
 <span data-ttu-id="a44ca-125">모든 MDX 스크립팅 문</span><span class="sxs-lookup"><span data-stu-id="a44ca-125">All MDX scripting statements</span></span>  
 <span data-ttu-id="a44ca-126">MDX 스크립트에서 MDX 스크립팅 문은 계산의 컨텍스트 및 범위를 제어하고 MDX 스크립트에 있는 다른 문의 동작을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-126">In MDX scripts, MDX scripting statements control the context and scope of calculations, and manage the behavior of other statements in the MDX script.</span></span> <span data-ttu-id="a44ca-127">이 범주에는 다음 문이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-127">This category includes the following statements:</span></span>  
  
-   [<span data-ttu-id="a44ca-128">승수로</span><span class="sxs-lookup"><span data-stu-id="a44ca-128">CALCULATE</span></span>](/sql/mdx/mdx-scripting-calculate)  
  
-   [<span data-ttu-id="a44ca-129">고정</span><span class="sxs-lookup"><span data-stu-id="a44ca-129">FREEZE</span></span>](/sql/mdx/mdx-scripting-freeze)  
  
-   [<span data-ttu-id="a44ca-130">범위</span><span class="sxs-lookup"><span data-stu-id="a44ca-130">SCOPE</span></span>](/sql/mdx/mdx-scripting-scope)  
  
 <span data-ttu-id="a44ca-131">MDX 스크립팅 문에 대한 자세한 내용은 [MDX 스크립팅 문&#40;MDX&#41;](/sql/mdx/mdx-scripting-statements-mdx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a44ca-131">For more information on MDX scripting statements, see [MDX Scripting Statements &#40;MDX&#41;](/sql/mdx/mdx-scripting-statements-mdx).</span></span>  
  
 [<span data-ttu-id="a44ca-132">CREATE MEMBER</span><span class="sxs-lookup"><span data-stu-id="a44ca-132">CREATE MEMBER</span></span>](/sql/mdx/mdx-data-definition-create-member)  
 <span data-ttu-id="a44ca-133">CREATE MEMBER 문은 계산 멤버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-133">The CREATE MEMBER statement creates calculated members.</span></span> <span data-ttu-id="a44ca-134">계산 멤버 작성 방법에 대한 자세한 내용은 [계산 멤버를 MDX로 작성&#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a44ca-134">For more information about how to create calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
 [<span data-ttu-id="a44ca-135">CREATE SET</span><span class="sxs-lookup"><span data-stu-id="a44ca-135">CREATE SET</span></span>](/sql/mdx/mdx-data-definition-create-set)  
 <span data-ttu-id="a44ca-136">CREATE SET 문은 명명된 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-136">The CREATE SET statement creates named sets.</span></span> <span data-ttu-id="a44ca-137">명명된 집합을 만드는 방법에 대한 자세한 내용은 [명명된 집합을 MDX로 작성&#40;MDX&#41;](mdx-named-sets-building-named-sets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a44ca-137">For more information about how to create names sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
 <span data-ttu-id="a44ca-138">조건문</span><span class="sxs-lookup"><span data-stu-id="a44ca-138">Conditional statements</span></span>  
 <span data-ttu-id="a44ca-139">조건문은 MDX 스크립트에 조건부 논리를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-139">Conditional statements add conditional logic to MDX scripts.</span></span> <span data-ttu-id="a44ca-140">이 범주로는 [CASE](/sql/mdx/case-statement-mdx) 및 [IF](/sql/mdx/mdx-scripting-if) 문이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-140">This category includes the [CASE](/sql/mdx/case-statement-mdx) and [IF](/sql/mdx/mdx-scripting-if) statements.</span></span>  
  
 <span data-ttu-id="a44ca-141">대입 식</span><span class="sxs-lookup"><span data-stu-id="a44ca-141">Assignment expressions</span></span>  
 <span data-ttu-id="a44ca-142">대입 식은 제약이 있는 하위 큐브에 값과 같이 식을 대입합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-142">An assignment expression assigns an expression, such as a value, to a constrained subcube.</span></span> <span data-ttu-id="a44ca-143">제약이 있는 하위 큐브 식은 MDX 스크립트 내에 있는 하위 큐브의 "가장자리"를 정의하는 제약이 있는 집합 식의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-143">A constrained subcube expression is a collection of constrained set expressions that define the "edges" of a subcube within an MDX script.</span></span> <span data-ttu-id="a44ca-144">다음 코드에서는 제약이 있는 하위 큐브 식에 대한 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a44ca-144">The following codes shows the syntax for a constrained subcube expression:</span></span>  
  
```  
<Constrained subcube> ::= (   
    ( <Constrained set> [<Crossjoin operator> <Constrained set>...] |  
    <ROOT function> |  
    <TREE function> |  
    LEAVES() |  
    * ) [, <Constrained subcube>...]  
<Constrained set> ::=   
    <Natural hierarchy>.MEMBERS |   
    <Natural hierarchy>.LEVEL(<numeric expression>).MEMBERS |   
    { <Natural hierarchy member> } |   
    DESCENDANTS( <Natural hierarchy member>, <Level expression>, ( SELF | AFTER | SELF_AND_AFTER ) ) |   
    DESCENDANTS( <Natural hierarchy member>, , LEAVES )  
<Natural hierarchy> ::= <Hierarchy identifier>  
<Natural hierarchy member> ::= <Natural hierarchy>.<identifier>[.<identifier>...]  
```  
  
## <a name="see-also"></a><span data-ttu-id="a44ca-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a44ca-145">See Also</span></span>  
 <span data-ttu-id="a44ca-146">[Mdx 언어 참조 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="a44ca-146">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="a44ca-147">MDX 스크립팅 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a44ca-147">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)  
  
  
