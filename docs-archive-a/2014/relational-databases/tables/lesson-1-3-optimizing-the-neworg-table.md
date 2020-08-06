---
title: NewOrg 테이블 최적화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
author: stevestein
ms.author: sstein
ms.openlocfilehash: 39c09a3a73051e7a61f3a62a125232d83d1570c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638605"
---
# <a name="optimizing-the-neworg-table"></a><span data-ttu-id="a138b-102">NewOrg 테이블 최적화</span><span class="sxs-lookup"><span data-stu-id="a138b-102">Optimizing the NewOrg Table</span></span>
  <span data-ttu-id="a138b-103">[기존 계층적 데이터로 테이블 채우기](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) 태스크에서 만든 **neword** 테이블은 모든 직원 정보를 포함 하며 데이터 형식을 사용 하 여 계층 구조를 나타냅니다 `hierarchyid` .</span><span class="sxs-lookup"><span data-stu-id="a138b-103">The **NewOrd** table that you created in the [Populating a Table with Existing Hierarchical Data](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) task contains all the employee information, and represents the hierarchical structure by using a `hierarchyid` data type.</span></span> <span data-ttu-id="a138b-104">이 태스크에서는 새 인덱스를 추가하여 `hierarchyid` 열에서의 검색을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-104">This task adds new indexes to support searches on the `hierarchyid` column.</span></span>  
  
## <a name="clustered-index"></a><span data-ttu-id="a138b-105">클러스터형 인덱스</span><span class="sxs-lookup"><span data-stu-id="a138b-105">Clustered Index</span></span>  
 <span data-ttu-id="a138b-106">`hierarchyid`열 (**OrgNode**)은 **neworg** 테이블의 기본 키입니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-106">The `hierarchyid` column (**OrgNode**) is the primary key for the **NewOrg** table.</span></span> <span data-ttu-id="a138b-107">테이블을 만들 때 **OrgNode** 열의 고유성을 적용하기 위해 이 열에 **PK_NewOrg_OrgNode** 라는 클러스터형 인덱스가 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-107">When the table was created, it contained a clustered index named **PK_NewOrg_OrgNode** to enforce the uniqueness of the **OrgNode** column.</span></span> <span data-ttu-id="a138b-108">이 클러스터형 인덱스는 테이블의 깊이 우선 검색도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-108">This clustered index also supports a depth-first search of the table.</span></span>  
  
## <a name="nonclustered-index"></a><span data-ttu-id="a138b-109">비클러스터형 인덱스</span><span class="sxs-lookup"><span data-stu-id="a138b-109">Nonclustered Index</span></span>  
 <span data-ttu-id="a138b-110">이 단계에서는 일반적인 검색을 지원하는 두 개의 비클러스터형 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-110">This step creates two nonclustered indexes to support typical searches.</span></span>  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a><span data-ttu-id="a138b-111">효율적인 검색을 위해 NewOrg 테이블을 인덱싱하려면</span><span class="sxs-lookup"><span data-stu-id="a138b-111">To index the NewOrg table for efficient searches</span></span>  
  
1.  <span data-ttu-id="a138b-112">계층의 같은 수준에서의 쿼리를 돕기 위해 [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) 메서드를 사용하여 계층의 수준을 포함하는 계산 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-112">To help queries at the same level in the hierarchy, use the [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) method to create a computed column that contains the level in the hierarchy.</span></span> <span data-ttu-id="a138b-113">그런 다음 수준 및 `Hierarchyid`에 대한 복합 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-113">Then, create a composite index on the level and the `Hierarchyid`.</span></span> <span data-ttu-id="a138b-114">다음 코드를 실행하여 계산 열과 너비 우선 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-114">Run the following code to create the computed column and the breadth-first index:</span></span>  
  
    ```  
    ALTER TABLE NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  <span data-ttu-id="a138b-115">**EmployeeID** 열에 대한 고유 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-115">Create a unique index on the **EmployeeID** column.</span></span> <span data-ttu-id="a138b-116">이는 **EmployeeID** 번호를 기준으로 단일 직원을 단일 조회하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-116">This is the traditional singleton lookup of a single employee by **EmployeeID** number.</span></span> <span data-ttu-id="a138b-117">다음 코드를 실행하여 **EmployeeID**에 대한 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-117">Run the following code to create an index on **EmployeeID**:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON NewOrg(EmployeeID) ;  
    GO  
    ```  
  
3.  <span data-ttu-id="a138b-118">다음 코드를 실행하여 3가지 인덱스 각각의 순서대로 테이블에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-118">Run the following code to retrieve data from the table in the order of each of the three indexes:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM NewOrg   
    ORDER BY OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY H_Level, OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  <span data-ttu-id="a138b-119">결과 집합을 비교하여 각 인덱스 유형에서 순서가 저장되는 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-119">Compare the result sets to see how the order is stored in each type of index.</span></span> <span data-ttu-id="a138b-120">각 출력의 처음 4개 행만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-120">Only the first four rows of each output follow.</span></span>  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     <span data-ttu-id="a138b-121">깊이 우선 인덱스: 직원 레코드가 해당 관리자에 인접하게 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-121">Depth-first index: Employee records are stored adjacent to their manager.</span></span>  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     <span data-ttu-id="a138b-122">**EmployeeID**우선 인덱스: 행이 **EmployeeID** 시퀀스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-122">**EmployeeID**-first index: Rows are stored in **EmployeeID** sequence.</span></span>  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
> [!NOTE]  
>  <span data-ttu-id="a138b-123">깊이 우선 인덱스와 너비 우선 인덱스의 차이를 보여 주는 다이어그램은 [계층적 데이터&#40;SQL Server&#41;](../hierarchical-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a138b-123">For diagrams that show the difference between a depth-first index and a breadth-first index, see [Hierarchical Data &#40;SQL Server&#41;](../hierarchical-data-sql-server.md).</span></span>  
  
#### <a name="to-drop-the-unnecessary-columns"></a><span data-ttu-id="a138b-124">불필요한 열을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a138b-124">To drop the unnecessary columns</span></span>  
  
1.  <span data-ttu-id="a138b-125">**ManagerID** 열은 직원/관리자 관계를 나타냅니다(이제 **OrgNode** 열이 나타냄).</span><span class="sxs-lookup"><span data-stu-id="a138b-125">The **ManagerID** column represents the employee/manager relationship, which is now represented by the **OrgNode** column.</span></span> <span data-ttu-id="a138b-126">다른 애플리케이션에 **ManagerID** 열이 필요하지 않은 경우 다음 문을 사용하여 해당 열을 삭제하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-126">If other applications do not need the **ManagerID** column, consider dropping it by using the following statement:</span></span>  
  
    ```  
    ALTER TABLE NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  <span data-ttu-id="a138b-127">**EmployeeID** 열도 중복됩니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-127">The **EmployeeID** column is also redundant.</span></span> <span data-ttu-id="a138b-128">**OrgNode** 열은 각 직원을 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-128">The **OrgNode** column uniquely identifies each employee.</span></span> <span data-ttu-id="a138b-129">다른 애플리케이션에 **EmployeeID** 열이 필요하지 않은 경우 다음 코드를 사용하여 인덱스와 열을 차례로 삭제하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-129">If other applications do not need the **EmployeeID** column, consider dropping the index and then the column by using the following code:</span></span>  
  
    ```  
    DROP INDEX EmpIDs_unq ON NewOrg ;  
    ALTER TABLE NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a><span data-ttu-id="a138b-130">원래 테이블을 새 테이블로 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="a138b-130">To replace the original table with the new table</span></span>  
  
1.  <span data-ttu-id="a138b-131">원래 테이블에 추가 인덱스 또는 제약 조건이 포함된 경우 이를 **NewOrg** 테이블에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-131">If your original table contained any additional indexes or constraints, add them to the **NewOrg** table.</span></span>  
  
2.  <span data-ttu-id="a138b-132">이전 **EmployeeDemo** 테이블을 새 테이블로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-132">Replace the old **EmployeeDemo** table with the new table.</span></span> <span data-ttu-id="a138b-133">다음 코드를 실행하여 이전 테이블을 삭제한 다음 새 테이블의 이름을 이전 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-133">Run the following code to drop the old table, and then rename the new table with the old name:</span></span>  
  
    ```  
    DROP TABLE EmployeeDemo ;  
    GO  
    sp_rename 'NewOrg', EmployeeDemo ;  
    GO  
    ```  
  
3.  <span data-ttu-id="a138b-134">다음 코드를 실행하여 최종 테이블을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="a138b-134">Run the following code to examine the final table:</span></span>  
  
    ```  
    SELECT * FROM EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a138b-135">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="a138b-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a138b-136">요약: 테이블을 계층 구조로 변환</span><span class="sxs-lookup"><span data-stu-id="a138b-136">Summary: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
