---
title: 계층적 메서드를 사용하여 계층적 테이블 쿼리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6c86c8e8678fc821dc3796a511349c1c3498bdb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652030"
---
# <a name="querying-a-hierarchical-table-using-hierarchy-methods"></a><span data-ttu-id="82491-102">계층 메서드를 사용하여 계층적 테이블 쿼리</span><span class="sxs-lookup"><span data-stu-id="82491-102">Querying a Hierarchical Table Using Hierarchy Methods</span></span>
  <span data-ttu-id="82491-103">이제 HumanResources.EmployeeOrg 테이블을 완전히 채웠으므로 이 태스크에서는 일부 계층 메서드를 사용하여 계층을 쿼리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="82491-103">Now that the HumanResources.EmployeeOrg table is fully populated, this task will show you how to query the hierarchy using some of the hierarchical methods.</span></span>  
  
### <a name="to-find-subordinate-nodes"></a><span data-ttu-id="82491-104">부하 직원 노드를 찾으려면</span><span class="sxs-lookup"><span data-stu-id="82491-104">To find subordinate nodes</span></span>  
  
1.  <span data-ttu-id="82491-105">Sariya에게는 부하 직원이 한 명 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82491-105">Sariya has one subordinate employee.</span></span> <span data-ttu-id="82491-106">Sariya의 부하 직원에 대해 쿼리하려면 [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) 메서드를 사용하는 다음 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="82491-106">To query for Sariya's subordinates, execute the following query that uses the [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) method:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
     <span data-ttu-id="82491-107">결과에 Sariya와 Wanida가 모두 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="82491-107">The result lists both Sariya and Wanida.</span></span> <span data-ttu-id="82491-108">Sariya는 0 수준에서 하위 항목이므로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="82491-108">Sariya is listed because she is the descendant at the 0 level.</span></span> <span data-ttu-id="82491-109">Wanida는 1 수준에서 하위 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="82491-109">Wanida is the descendant at the 1 level.</span></span>  
  
2.  <span data-ttu-id="82491-110">[GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) 메서드를 사용하여 이 정보에 대해 쿼리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82491-110">You can also query for this information by using the [GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) method.</span></span> <span data-ttu-id="82491-111">`GetAncestor` 는 반환하려는 수준에 대한 인수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="82491-111">`GetAncestor` takes an argument for the level that you are trying to return.</span></span> <span data-ttu-id="82491-112">Wanida는 Sariya보다 한 수준 아래이므로 다음 코드와 같이 `GetAncestor(1)` 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="82491-112">Since Wanida is one level underneath Sariya, use `GetAncestor(1)` as demonstrated in the following code:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
     <span data-ttu-id="82491-113">이번에는 결과에 Wanida만 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="82491-113">This time the result lists only Wanida.</span></span>  
  
3.  <span data-ttu-id="82491-114">이제 `@CurrentEmployee` 를 David(EmployeeID 6)로 변경하고 수준을 2로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="82491-114">Now change the `@CurrentEmployee` to David (EmployeeID 6) and the level to 2.</span></span> <span data-ttu-id="82491-115">다음을 실행하여 Wanida도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="82491-115">Execute the following to also return Wanida:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
     <span data-ttu-id="82491-116">이번에는 David에게 보고하는 두 수준 아래에 있는 Mary도 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="82491-116">This time, you also receive Mary who also reports to David, two levels down.</span></span>  
  
### <a name="to-use-getroot-and-getlevel"></a><span data-ttu-id="82491-117">GetRoot 및 GetLevel을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="82491-117">To use GetRoot, and GetLevel</span></span>  
  
1.  <span data-ttu-id="82491-118">계층이 커질수록 계층에서의 멤버 위치를 확인하기가 더 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="82491-118">As the hierarchy grows larger it is more difficult to determine where the members are in the hierarchy.</span></span> <span data-ttu-id="82491-119">[GetLevel](/sql/t-sql/data-types/getlevel-database-engine) 메서드를 사용하여 계층에서의 각 행 수준을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82491-119">Use the [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) method to find how many levels down each row is in the hierarchy.</span></span> <span data-ttu-id="82491-120">다음 코드를 실행하여 모든 행의 수준을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="82491-120">Execute the following code to view the levels of all the rows:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  <span data-ttu-id="82491-121">[GetRoot](/sql/t-sql/data-types/getroot-database-engine) 메서드를 사용하여 계층의 루트 노드를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82491-121">Use the [GetRoot](/sql/t-sql/data-types/getroot-database-engine) method to find the root node in the hierarchy.</span></span> <span data-ttu-id="82491-122">다음 코드에서는 루트인 단일 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="82491-122">The following code returns the single row which is the root:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
 <span data-ttu-id="82491-123">다음 태스크에서는 계층을 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82491-123">The next task will reorganize the hierarchy.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="82491-124">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="82491-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="82491-125">계층 메서드를 사용하여 계층적 테이블의 데이터 다시 정렬</span><span class="sxs-lookup"><span data-stu-id="82491-125">Reordering Data in a Hierarchical Table Using Hierarchical Methods</span></span>](lesson-2-4-reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
