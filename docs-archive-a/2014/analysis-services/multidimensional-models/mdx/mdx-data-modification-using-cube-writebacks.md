---
title: 큐브 쓰기 저장 (MDX) 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- writeback [Analysis Services], cubes
- cubes [Analysis Services], modifying
- modifying cubes
- UPDATE CUBE statement
- cubes [Analysis Services], writeback
ms.assetid: ae2385fc-7fa0-4f8e-98d7-dcb0a5f0eeea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3ac43e9206619117c1fc090a594ca32ccbeeeb31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649732"
---
# <a name="using-cube-writebacks-mdx"></a><span data-ttu-id="0ef93-102">큐브 쓰기 저장(Writeback) 사용(MDX)</span><span class="sxs-lookup"><span data-stu-id="0ef93-102">Using Cube Writebacks (MDX)</span></span>
  <span data-ttu-id="0ef93-103">큐브를 업데이트하는 데는 [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-103">You update a cube by using the [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) statement.</span></span> <span data-ttu-id="0ef93-104">이 문은 특정 값을 가진 튜플을 업데이트할 수 있도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-104">This statement lets you update a tuple with a specific value.</span></span> <span data-ttu-id="0ef93-105">큐브 업데이트에 UPDATE CUBE 문을 효과적으로 사용하기 위해서는 문의 구문, 발생할 수 있는 오류 조건 및 업데이트로 인한 큐브의 영향을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-105">To effectively use the UPDATE CUBE statement to update a cube, you have to understand the syntax for the statement, the error conditions that can occur, and the affect that updates can have on a cube.</span></span>  
  
## <a name="update-cube-statement-syntax"></a><span data-ttu-id="0ef93-106">UPDATE CUBE 문 구문</span><span class="sxs-lookup"><span data-stu-id="0ef93-106">UPDATE CUBE Statement Syntax</span></span>  
 <span data-ttu-id="0ef93-107">다음은 UPDATE CUBE 문의 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-107">The following syntax describes the UPDATE CUBE statement:</span></span>  
  
```  
UPDATE [CUBE] <Cube_Name> SET <tuple>.VALUE = <value> [,<tuple>.VALUE = <value>...]  
 [ USE_EQUAL_ALLOCATION | USE_EQUAL_INCREMENT |  
  USE_WEIGHTED_ALLOCATION [BY <weight value_expression>] |  
  USE_WEIGHTED_INCREMENT [BY <weight value_expression>] ]   
```  
  
 <span data-ttu-id="0ef93-108">튜플의 전체 좌표 집합을 지정하지 않으면 지정되지 않은 좌표에 계층의 기본 멤버가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-108">If a full set of coordinates is not specified for the tuple, the unspecified coordinates will use the default member of the hierarchy.</span></span> <span data-ttu-id="0ef93-109">확인된 튜플은 [Sum](/sql/mdx/sum-mdx) 함수를 사용하여 집계한 셀을 참조해야 하며 셀 좌표 중 하나로 계산 멤버를 사용해선 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-109">The tuple identified must reference a cell that is aggregated with the [Sum](/sql/mdx/sum-mdx) function, and must not use a calculated member as one of the cell's coordinates.</span></span>  
  
 <span data-ttu-id="0ef93-110">UPDATE CUBE 문은 원자 셀에 일련의 개별 쓰기 저장 작업을 생성하는 서브루틴으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-110">You can think of the UPDATE CUBE statement as a subroutine that generates a series of individual writeback operations to atomic cells.</span></span> <span data-ttu-id="0ef93-111">이 쓰기 저장 작업은 모두 지정된 합계로 롤업됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-111">All these individual writeback operations then roll up into the specified sum.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ef93-112">업데이트된 셀이 겹치지 않을 경우 `Update Isolation Level` 연결 문자열 속성을 사용하여 UPDATE CUBE의 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-112">When updated cells do not overlap, the `Update Isolation Level` connection string property can be used to enhance performance for UPDATE CUBE.</span></span> <span data-ttu-id="0ef93-113">자세한 내용은 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ef93-113">For more information, see <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ef93-114">예제</span><span class="sxs-lookup"><span data-stu-id="0ef93-114">Example</span></span>  
 <span data-ttu-id="0ef93-115">Adventure Works 큐브에서 Sales Targets 측정값 그룹을 사용하여 UPDATE CUBE를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-115">You can test UPDATE CUBE using the Sales Targets measure group in the Adventure Works cube.</span></span> <span data-ttu-id="0ef93-116">이 측정값 그룹은 SUM으로 집계된 측정값으로 구성되며 UPDATE CUBE의 필수 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-116">This measure group consists of measures aggregated by SUM, which is a requirement for UPDATE CUBE.</span></span>  
  
1.  <span data-ttu-id="0ef93-117">Adventure Works 데이터베이스에서 Sales Targets 측정값 그룹에 쓰기 저장을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-117">Enable writeback for the Sales Targets measure group in the Adventure Works database.</span></span> <span data-ttu-id="0ef93-118">Management Studio에서 측정값 그룹을 마우스 오른쪽 단추로 클릭하고 **쓰기 저장 옵션**을 가리킨 후 **쓰기 저장 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-118">In Management Studio, right-click a measure group, point to **Write Back Options**, choose **Enable Writeback**.</span></span>  
  
     <span data-ttu-id="0ef93-119">Writeback 폴더에 새로운 쓰기 저장 테이블이 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-119">You should see a new writeback table in the Writeback folder.</span></span> <span data-ttu-id="0ef93-120">테이블 이름은 WriteTable_Fact Sales Quota입니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-120">The table name is WriteTable_Fact Sales Quota.</span></span>  
  
2.  <span data-ttu-id="0ef93-121">MDX 쿼리 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-121">Open an MDX query window.</span></span> <span data-ttu-id="0ef93-122">원래 값을 보려면 다음 select 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-122">Run the following select statement to view the original value:</span></span>  
  
    ```  
    SELECT [Measures].[Sales Amount Quota] on 0 ,  
    [Employee].[Employee Department].[Title].&[Sales Representative].children on 1  
    FROM [Adventure Works]  
  
    ```  
  
     <span data-ttu-id="0ef93-123">각 담당자의 판매 할당액이 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-123">You should see sales amount quotas for each representative.</span></span>  
  
3.  <span data-ttu-id="0ef93-124">새 값을 쓰기 저장하려면 update cube 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-124">Run the update cube statement to write back a new value.</span></span> <span data-ttu-id="0ef93-125">이 예에서는 판매 할당액을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-125">In this example, we are setting the sales amount quota to 0.</span></span> <span data-ttu-id="0ef93-126">새 값이 0이므로 할당 방법을 지정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="0ef93-126">Because the new value is 0, do not specify an allocation method.</span></span>  
  
    ```  
    UPDATE CUBE [Adventure Works]   
    SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 0  
  
    ```  
  
4.  <span data-ttu-id="0ef93-127">SELECT 문을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-127">Re-run the SELECT statement.</span></span> <span data-ttu-id="0ef93-128">이제 할당액에 0이 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-128">You should now see zero for the quotas.</span></span>  
  
 <span data-ttu-id="0ef93-129">쓰기 저장 값이 현재 세션으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-129">The writeback value is constrained to the current session.</span></span> <span data-ttu-id="0ef93-130">사용자와 세션 간에 값을 유지하려면 쓰기 저장 테이블을 처리하십시오.</span><span class="sxs-lookup"><span data-stu-id="0ef93-130">To persist the value across users and sessions, process the writeback table.</span></span> <span data-ttu-id="0ef93-131">Management Studio에서 WriteTable_Fact Sales Quota를 마우스 오른쪽 단추로 클릭하고 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-131">In Management Studio, right-click WriteTable_Fact Sales Quota and choose **Process**.</span></span>  
  
 <span data-ttu-id="0ef93-132">할당 방법을 지정하려면 새 값이 0보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-132">To specify an allocation method, the new value must be greater than zero.</span></span> <span data-ttu-id="0ef93-133">이 예에서 Sales Amount Quota의 새 값은 200만이고 할당 방법을 통해 모든 판매 담당자 간에 할당량이 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-133">In this example, the new value for Sales Amount Quota is two million and the allocation method distributes the amount across all sales representatives.</span></span>  
  
```  
UPDATE CUBE [Adventure Works]   
SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 2000000   
USE_EQUAL_ALLOCATION  
```  
  
## <a name="error-conditions"></a><span data-ttu-id="0ef93-134">오류 조건</span><span class="sxs-lookup"><span data-stu-id="0ef93-134">Error Conditions</span></span>  
 <span data-ttu-id="0ef93-135">다음 표에서는 쓰기 저장 실패를 유발하는 원인과 해당 오류의 결과를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-135">The following table describes both what can cause writebacks to fail and the result of those errors.</span></span>  
  
|<span data-ttu-id="0ef93-136">오류 조건</span><span class="sxs-lookup"><span data-stu-id="0ef93-136">Error Condition</span></span>|<span data-ttu-id="0ef93-137">결과</span><span class="sxs-lookup"><span data-stu-id="0ef93-137">Result</span></span>|  
|---------------------|------------|  
|<span data-ttu-id="0ef93-138">업데이트가 함께 존재할 수 없는 동일한 차원의 멤버를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-138">Update includes members from the same dimension that do not exist with one another.</span></span>|<span data-ttu-id="0ef93-139">업데이트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-139">Update will fail.</span></span> <span data-ttu-id="0ef93-140">참조된 셀이 큐브 공간에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-140">The cube space will not contain the referenced cell.</span></span>|  
|<span data-ttu-id="0ef93-141">업데이트가 부호 없는 형식의 측정값을 원본으로 하는 측정값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-141">Update includes a measure sourced to a measure of an unsigned type.</span></span>|<span data-ttu-id="0ef93-142">업데이트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-142">Update will fail.</span></span> <span data-ttu-id="0ef93-143">증가분은 음수 값을 사용할 수 있는 측정값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-143">Increments require that the measure be able to take a negative value.</span></span>|  
|<span data-ttu-id="0ef93-144">업데이트가 sum 이외의 집계를 수행하는 측정값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-144">Update includes a measure that aggregates other than sum.</span></span>|<span data-ttu-id="0ef93-145">오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-145">An error is raised.</span></span>|  
|<span data-ttu-id="0ef93-146">하위 큐브에서 업데이트를 시도했습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-146">Update was tried on a subcube.</span></span>|<span data-ttu-id="0ef93-147">오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-147">An error is raised.</span></span>|  
  
## <a name="affect-of-cube-changes"></a><span data-ttu-id="0ef93-148">큐브 변경의 영향</span><span class="sxs-lookup"><span data-stu-id="0ef93-148">Affect of Cube Changes</span></span>  
 <span data-ttu-id="0ef93-149">다음 변경 사항은 쓰기 저장(writeback)에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-149">The following changes will not have an effect on a writeback:</span></span>  
  
-   <span data-ttu-id="0ef93-150">큐브, 큐브의 측정값 그룹 또는 큐브의 차원에 대한 처리</span><span class="sxs-lookup"><span data-stu-id="0ef93-150">Processing of a cube, the cube's measure groups, or the cube's dimensions.</span></span>  
  
-   <span data-ttu-id="0ef93-151">임의의 차원에 속성 추가</span><span class="sxs-lookup"><span data-stu-id="0ef93-151">Adding attributes to any dimension.</span></span>  
  
-   <span data-ttu-id="0ef93-152">새 차원 추가</span><span class="sxs-lookup"><span data-stu-id="0ef93-152">Adding a new dimension.</span></span>  
  
-   <span data-ttu-id="0ef93-153">쓰기 저장(writeback)을 포함하지 않는 차원 삭제</span><span class="sxs-lookup"><span data-stu-id="0ef93-153">Deleting a dimension that does not include the writeback.</span></span>  
  
-   <span data-ttu-id="0ef93-154">계층 추가, 수정 또는 제거</span><span class="sxs-lookup"><span data-stu-id="0ef93-154">Adding, modifying, or removing a hierarchy.</span></span>  
  
-   <span data-ttu-id="0ef93-155">새 측정값 추가</span><span class="sxs-lookup"><span data-stu-id="0ef93-155">Adding a new measure.</span></span>  
  
 <span data-ttu-id="0ef93-156">다음 변경은 쓰기 저장(writeback) 데이터를 제거하기 전에는 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-156">The following changes cannot be made without removing the writeback data:</span></span>  
  
-   <span data-ttu-id="0ef93-157">쓰기 저장(writeback)가 속성을 포함할 때 속성 또는 속성 계층 삭제.</span><span class="sxs-lookup"><span data-stu-id="0ef93-157">Deleting an attribute, or its attribute hierarchy, if the attribute is included in the writeback.</span></span> <span data-ttu-id="0ef93-158">여기에는 속성 또는 속성 계층의 명시적 제거 또는 속성의 부모 차원 제거도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ef93-158">This includes explicitly removing the attribute, or its attribute hierarchy, or removing the attribute's parent dimension.</span></span>  
  
-   <span data-ttu-id="0ef93-159">쓰기 저장(writeback)에 포함된 측정값 삭제</span><span class="sxs-lookup"><span data-stu-id="0ef93-159">Deleting a measure included in the writeback.</span></span>  
  
-   <span data-ttu-id="0ef93-160">쓰기 저장(writeback)에 포함된 차원에 `(All)` 수준 없이 속성 추가</span><span class="sxs-lookup"><span data-stu-id="0ef93-160">Adding an attribute without an `(All)` level to a dimension included in the writeback.</span></span>  
  
-   <span data-ttu-id="0ef93-161">쓰기 저장(writeback)에 포함된 차원의 차원 세분성 변경</span><span class="sxs-lookup"><span data-stu-id="0ef93-161">Changing the dimension granularity for a dimension included in the writeback.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef93-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ef93-162">See Also</span></span>  
 [<span data-ttu-id="0ef93-163">데이터 수정&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="0ef93-163">Modifying Data &#40;MDX&#41;</span></span>](mdx-data-modification-modifying-data.md)  
  
  
