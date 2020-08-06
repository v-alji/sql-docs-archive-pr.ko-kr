---
title: 계층적 메서드를 사용하여 계층적 테이블의 데이터 다시 정렬 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 7b8064c7-62c6-488d-84d2-57a5828fb907
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac6c93f359a81a80af81182120f213564680de0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646268"
---
# <a name="reordering-data-in-a-hierarchical-table-using-hierarchical-methods"></a><span data-ttu-id="2e397-102">계층 메서드를 사용하여 계층적 테이블의 데이터 다시 정렬</span><span class="sxs-lookup"><span data-stu-id="2e397-102">Reordering Data in a Hierarchical Table Using Hierarchical Methods</span></span>
  <span data-ttu-id="2e397-103">계층을 다시 구성하는 것은 일반적인 유지 관리 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-103">Reorganizing a hierarchy is a common maintenance task.</span></span> <span data-ttu-id="2e397-104">이 태스크에서는 UPDATE 문을 [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) 메서드와 함께 사용하여 먼저 단일 행을 계층의 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-104">In this task, we will use an UPDATE statement with the [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) method to first move a single row to a new location in the hierarchy.</span></span> <span data-ttu-id="2e397-105">그런 다음 전체 하위 트리를 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-105">Then we will move an entire sub-tree to a new location.</span></span>  
  
 <span data-ttu-id="2e397-106">`GetReparentedValue` 메서드는 두 개의 인수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-106">The `GetReparentedValue` method takes two arguments.</span></span> <span data-ttu-id="2e397-107">첫 번째 인수는 수정할 계층 부분을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-107">The first argument describes the part of the hierarchy to be modified.</span></span> <span data-ttu-id="2e397-108">예를 들어 계층이 **/1/4/2/3/** 인 경우 **/1/4/** 섹션을 변경하여 계층을 **/2/1/2/3/** 으로 만들고 마지막 두 노드(**2/3/**)는 변경하지 않으려면 변경되는 노드(**/1/4/**)를 첫 번째 인수로 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-108">For example, if a hierarchy is **/1/4/2/3/** and you want to change the **/1/4/** section, the hierarchy becomes **/2/1/2/3/**, leaving the last two nodes (**2/3/**) unchanged, you must provide the changing nodes (**/1/4/**) as the first argument.</span></span> <span data-ttu-id="2e397-109">두 번째 인수는 새 계층 구조 수준(이 예제의 경우 **/2/1/**)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-109">The second argument provides the new hierarchy level, in our example **/2/1/**.</span></span> <span data-ttu-id="2e397-110">두 인수의 수준 수가 같을 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-110">The two arguments do not have to contain the same number of levels.</span></span>  
  
### <a name="to-move-a-single-row-to-a-new-location-in-the-hierarchy"></a><span data-ttu-id="2e397-111">단일 행을 계층의 새 위치로 이동하려면</span><span class="sxs-lookup"><span data-stu-id="2e397-111">To move a single row to a new location in the hierarchy</span></span>  
  
1.  <span data-ttu-id="2e397-112">현재 Wanida는 Sariya에게 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-112">Currently Wanida reports to Sariya.</span></span> <span data-ttu-id="2e397-113">이 절차에서는 Wanida가 Jill에게 보고하도록 현재 노드 **/1/1/** 에서 Wanida를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-113">In this procedure, you move Wanida from her current node **/1/1/,** so that she reports to Jill.</span></span> <span data-ttu-id="2e397-114">Wanida의 새 노드는 **/3/1/** 이 되므로 **/1/** 이 첫 번째 인수이고 **/3/** 이 두 번째 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-114">Her new node will become **/3/1/** so **/1/** is the first argument and **/3/** is the second.</span></span> <span data-ttu-id="2e397-115">이러한 인수는 Sariya와 Jill의 **OrgNode** 값에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-115">These correspond to the **OrgNode** values of Sariya and Jill.</span></span> <span data-ttu-id="2e397-116">다음 코드를 실행하여 Wanida를 Sariya의 조직에서 Jill의 조직으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-116">Execute the following code to move Wanida from Sariya's organization to Jill's:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  <span data-ttu-id="2e397-117">다음 코드를 실행하여 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-117">Execute the following code to see the result:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     <span data-ttu-id="2e397-118">이제 Wanida는 **/3/1/** 노드에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-118">Wanida is now at node **/3/1/**.</span></span>  
  
### <a name="to-reorganize-a-section-of-a-hierarchy"></a><span data-ttu-id="2e397-119">계층의 섹션을 다시 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2e397-119">To reorganize a section of a hierarchy</span></span>  
  
1.  <span data-ttu-id="2e397-120">동시에 많은 사람을 이동하는 방법을 보여 주기 위해 먼저 다음 코드를 실행하여 Wanida에게 보고하는 인턴을 한 명 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-120">To demonstrate how to move a larger number of people at the same time, first execute the following code to add an intern reporting to Wanida:</span></span>  
  
    ```  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  <span data-ttu-id="2e397-121">이제 Kevin은 Wanida에게 보고하고 Wanida는 Jill에게 보고하며 Jill은 David에게 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-121">Now Kevin reports to Wanida, who reports to Jill, who reports to David.</span></span> <span data-ttu-id="2e397-122">즉, Kevin은 **/3/1/1/** 수준에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-122">That means that Kevin is at level **/3/1/1/**.</span></span> <span data-ttu-id="2e397-123">Jill의 부하 직원을 모두 새 관리자에게로 이동하기 위해 **OrgNode** 가 **/3/** 인 모든 노드를 새 값으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-123">To move all of Jill's subordinates to a new manager, we will update all nodes that have **/3/** as their **OrgNode** to a new value.</span></span> <span data-ttu-id="2e397-124">다음 코드를 실행하여 Wanida가 Sariya에게 보고하도록 업데이트하고 Kevin은 계속 Wanida에게 보고하도록 둡니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-124">Execute the following code to update Wanida to report to Sariya, but keep  Kevin reporting to Wanida:</span></span>  
  
    ```  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  <span data-ttu-id="2e397-125">다음 코드를 실행하여 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-125">Execute the following code to see the result:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
------------ ------- -------- ---------- ------- -----------------  
/            Ox      0        6          David   Marketing Manager  
/1/          0x58    1        46         Sariya  Marketing Specialist  
/1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
/1/1//2      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
 <span data-ttu-id="2e397-126">Jill에게 보고했던 전체 조직 트리(Wanida와 Kevin)가 이제 Sariya에게 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2e397-126">The entire organizational tree that had reported to Jill (both Wanida and Kevin) now reports to Sariya.</span></span>  
  
 <span data-ttu-id="2e397-127">계층의 섹션을 다시 구성하는 저장 프로시저는 [Moving Subtrees](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees)의 "하위 트리 이동" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e397-127">For a stored procedure to reorganize a section of a hierarchy, see the "Moving Subtrees" section of [Moving Subtrees](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2e397-128">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="2e397-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2e397-129">요약: 계층적 테이블의 데이터 관리</span><span class="sxs-lookup"><span data-stu-id="2e397-129">Summary: Managing Data in a Hierarchical Table</span></span>](lesson-2-5-summary-managing-data-in-a-hierarchical-table.md)  
  
  
