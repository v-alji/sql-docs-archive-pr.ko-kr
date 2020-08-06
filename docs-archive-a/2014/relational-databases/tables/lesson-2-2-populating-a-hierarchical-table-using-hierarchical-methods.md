---
title: 계층적 메서드를 사용하여 계층적 테이블 채우기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID
ms.assetid: 2c95fa60-5b8e-4a05-ac09-cffe2b05900a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef99d711a772a075f568a83f5d56fcecaaa598f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652695"
---
# <a name="populating-a-hierarchical-table-using-hierarchical-methods"></a><span data-ttu-id="6b835-102">계층 메서드를 사용하여 계층적 테이블 채우기</span><span class="sxs-lookup"><span data-stu-id="6b835-102">Populating a Hierarchical Table Using Hierarchical Methods</span></span>
  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="6b835-103">의 마케팅 부서에는 8명의 직원이 근무하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-103">has 8 employees working in the Marketing department.</span></span> <span data-ttu-id="6b835-104">직원 계층은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-104">The employee hierarchy looks like this:</span></span>  
  
 <span data-ttu-id="6b835-105">**EmployeeID**가 6인 **David** 는 Marketing Manager입니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-105">**David**, **EmployeeID** 6, is the Marketing Manager.</span></span> <span data-ttu-id="6b835-106">다음과 같은 3명의 Marketing Specialist가 **David**에게 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-106">Three Marketing Specialists report to **David**:</span></span>  
  
-   <span data-ttu-id="6b835-107">**Sariya**, **EmployeeID** 46</span><span class="sxs-lookup"><span data-stu-id="6b835-107">**Sariya**, **EmployeeID** 46</span></span>  
  
-   <span data-ttu-id="6b835-108">**John**, **EmployeeID** 271</span><span class="sxs-lookup"><span data-stu-id="6b835-108">**John**, **EmployeeID** 271</span></span>  
  
-   <span data-ttu-id="6b835-109">**Jill**, **EmployeeID** 119</span><span class="sxs-lookup"><span data-stu-id="6b835-109">**Jill**, **EmployeeID** 119</span></span>  
  
 <span data-ttu-id="6b835-110">Marketing Assistant인 **Wanida** (**EmployeeID** 269)는 **Sariya**에게 보고하고 다른 Marketing Assistant인 **Mary** (**EmployeeID** 272)는 **John**에게 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-110">Marketing Assistant **Wanida** (**EmployeeID** 269), reports to **Sariya**, and Marketing Assistant **Mary** (**EmployeeID** 272), reports to **John**.</span></span>  
  
### <a name="to-insert-the-root-of-the-hierarchy-tree"></a><span data-ttu-id="6b835-111">계층 트리의 루트를 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="6b835-111">To insert the root of the hierarchy tree</span></span>  
  
1.  <span data-ttu-id="6b835-112">다음 예에서는 Marketing Manager **David** 를 계층의 루트에 있는 테이블에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-112">The following example inserts **David** the Marketing Manager into the table at the root of the hierarchy.</span></span> <span data-ttu-id="6b835-113">**OrdLevel** 열은 계산 열입니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-113">The **OrdLevel** column is a computed column.</span></span> <span data-ttu-id="6b835-114">따라서 INSERT 문의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-114">Therefore, it is not part of the INSERT statement.</span></span> <span data-ttu-id="6b835-115">이 첫 번째 레코드는 [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) 메서드를 사용하여 이 첫 번째 레코드를 계층의 루트로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-115">This first record uses the [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) method to populate this first record as the root of the hierarchy.</span></span>  
  
    ```  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  <span data-ttu-id="6b835-116">다음 코드를 실행하여 테이블의 초기 행을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-116">Execute the following code to examine initial row in the table:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
 <span data-ttu-id="6b835-117">이전 단원에서와 같이 `ToString()` 메서드를 사용하여 `hierarchyid` 데이터 형식을 보다 이해하기 쉬운 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-117">As in the previous lesson, we use the `ToString()` method to convert the `hierarchyid` data type to a format that is more easily understood.</span></span>  
  
### <a name="to-insert-a-subordinate-employee"></a><span data-ttu-id="6b835-118">부하 직원을 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="6b835-118">To insert a subordinate employee</span></span>  
  
1.  <span data-ttu-id="6b835-119">**Sariya** 는 **David**에게 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-119">**Sariya** reports to **David**.</span></span> <span data-ttu-id="6b835-120">**Sariya의** 노드를 삽입 하려면 데이터 형식의 적절 한 **OrgNode** 값을 만들어야 합니다 `hierarchyid` .</span><span class="sxs-lookup"><span data-stu-id="6b835-120">To insert **Sariya's** node, you must create an appropriate **OrgNode** value of data type `hierarchyid`.</span></span> <span data-ttu-id="6b835-121">다음 코드에서는 `hierarchyid` 데이터 형식의 변수를 만들고 이를 테이블의 루트 OrgNode 값으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-121">The following code creates a variable of data type `hierarchyid` and populates it with the root OrgNode value of the table.</span></span> <span data-ttu-id="6b835-122">그런 다음 해당 변수를 [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) 메서드와 함께 사용하여 하위 노드인 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-122">Then uses that variable with the [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) method to insert row that is a subordinate node.</span></span> <span data-ttu-id="6b835-123">`GetDescendant` 는 두 개의 인수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-123">`GetDescendant` takes two arguments.</span></span> <span data-ttu-id="6b835-124">인수 값에 대해 다음 옵션을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-124">Review the following options for the argument values:</span></span>  
  
    -   <span data-ttu-id="6b835-125">부모가 NULL인 경우 `GetDescendant` 는 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-125">If parent is NULL, `GetDescendant` returns NULL.</span></span>  
  
    -   <span data-ttu-id="6b835-126">부모가 NULL이 아니고 자식1과 자식2가 모두 NULL인 경우 `GetDescendant` 는 부모의 자식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-126">If parent is not NULL, and both child1 and child2 are NULL, `GetDescendant` returns a child of parent.</span></span>  
  
    -   <span data-ttu-id="6b835-127">부모와 자식1이 NULL이 아니고 자식2가 NULL인 경우 `GetDescendant` 는 자식1보다 큰 부모의 자식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-127">If parent and child1 are not NULL, and child2 is NULL, `GetDescendant` returns a child of parent greater than child1.</span></span>  
  
    -   <span data-ttu-id="6b835-128">부모와 자식2가 NULL이 아니고 자식1이 NULL인 경우 `GetDescendant` 는 자식2보다 작은 부모의 자식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-128">If parent and child2 are not NULL and child1 is NULL, `GetDescendant` returns a child of parent less than child2.</span></span>  
  
    -   <span data-ttu-id="6b835-129">부모, 자식1 및 자식2가 모두 NULL이 아닌 경우 `GetDescendant` 는 자식1보다 크고 자식2보다 작은 부모의 자식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-129">If parent, child1, and child2 are all not NULL, `GetDescendant` returns a child of parent greater than child1 and less than child2.</span></span>  
  
     <span data-ttu-id="6b835-130">다음 코드에서는 테이블에 루트를 제외한 행이 아직 없기 때문에 루트 부모의 `(NULL, NULL)` 인수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-130">The following code uses the `(NULL, NULL)` arguments of the root parent because there are not yet any rows in the table except the root.</span></span> <span data-ttu-id="6b835-131">다음 코드를 실행하여 **Sariya**를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-131">Execute the following code to insert **Sariya**:</span></span>  
  
    ```  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  <span data-ttu-id="6b835-132">첫 번째 프로시저의 쿼리를 반복하여 테이블을 쿼리하고 항목이 나타나는 방식을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-132">Repeat the query from the first procedure to query the table and see how the entries appear:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    ```  
  
### <a name="to-create-a-procedure-for-entering-new-nodes"></a><span data-ttu-id="6b835-133">새 노드를 입력하는 프로시저를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6b835-133">To create a procedure for entering new nodes</span></span>  
  
1.  <span data-ttu-id="6b835-134">데이터 입력을 단순화하기 위해 다음 저장 프로시저를 만들어 직원을 **EmployeeOrg** 테이블에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-134">To simplify entering data, create the following stored procedure to add employees to the **EmployeeOrg** table.</span></span> <span data-ttu-id="6b835-135">이 프로시저는 추가하는 직원에 대한 입력 값을 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-135">The procedure accepts input values about the employee being added.</span></span> <span data-ttu-id="6b835-136">여기에는 새 직원의 관리자에게 지정된 **EmployeeID** , 새 직원의 **EmployeeID** 번호 및 해당 직원의 이름과 직책이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-136">This includes the **EmployeeID** of the new employee's manager, the new employee's **EmployeeID** number, and their first name and title.</span></span> <span data-ttu-id="6b835-137">이 프로시저는 `GetDescendant()` 및 [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-137">The procedure uses `GetDescendant()` and also the [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) method.</span></span> <span data-ttu-id="6b835-138">다음 코드를 실행하여 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-138">Execute the following code to create the procedure:</span></span>  
  
    ```  
    CREATE PROC AddEmp(@mgrid int, @empid int, @e_name varchar(20), @title varchar(20))   
    AS   
    BEGIN  
       DECLARE @mOrgNode hierarchyid, @lc hierarchyid  
       SELECT @mOrgNode = OrgNode   
       FROM HumanResources.EmployeeOrg   
       WHERE EmployeeID = @mgrid  
       SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
       BEGIN TRANSACTION  
          SELECT @lc = max(OrgNode)   
          FROM HumanResources.EmployeeOrg   
          WHERE OrgNode.GetAncestor(1) =@mOrgNode ;  
  
          INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
          VALUES(@mOrgNode.GetDescendant(@lc, NULL), @empid, @e_name, @title)  
       COMMIT  
    END ;  
    GO  
    ```  
  
2.  <span data-ttu-id="6b835-139">다음 예에서는 **David**에게 직접 또는 간접적으로 보고하는 나머지 직원 4명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-139">The following example adds the remaining 4 employees that report directly or indirectly to **David**.</span></span>  
  
    ```  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  <span data-ttu-id="6b835-140">다시 다음 쿼리를 실행하여 **EmployeeOrg** 테이블의 행을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-140">Again, execute the following query examine the rows in the **EmployeeOrg** table:</span></span>  
  
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
    /2/          0x68    1        271        John    Marketing Specialist  
    /2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
    /3/          0x78    1        119        Jill    Marketing Specialist  
    ```  
  
 <span data-ttu-id="6b835-141">이제 테이블이 마케팅 조직으로 모두 채워졌습니다.</span><span class="sxs-lookup"><span data-stu-id="6b835-141">The table is now fully populated with the Marketing organization.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6b835-142">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="6b835-142">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6b835-143">계층 메서드를 사용하여 계층적 테이블 쿼리</span><span class="sxs-lookup"><span data-stu-id="6b835-143">Querying a Hierarchical Table Using Hierarchy Methods</span></span>](lesson-2-3-querying-a-hierarchical-table-using-hierarchy-methods.md)  
  
  
