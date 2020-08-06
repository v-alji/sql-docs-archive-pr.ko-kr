---
title: 기존 계층적 데이터로 테이블 채우기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: fd943d84-dbe6-4a05-912b-c88164998d80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 966548b11ad4697abc06de5c5c239a511f80b7af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729344"
---
# <a name="populating-a-table-with-existing-hierarchical-data"></a><span data-ttu-id="7804f-102">기존 계층적 데이터로 테이블 채우기</span><span class="sxs-lookup"><span data-stu-id="7804f-102">Populating a Table with Existing Hierarchical Data</span></span>
  <span data-ttu-id="7804f-103"> 이 태스크에서는 새 테이블을 만들고 이를 **EmployeeDemo** 테이블의 데이터로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-103">This task creates a new table and populates it with the data in the **EmployeeDemo** table.</span></span> <span data-ttu-id="7804f-104">이 태스크의 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-104">This task has the following steps:</span></span>  
  
-   <span data-ttu-id="7804f-105">`hierarchyid` 열이 포함된 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-105">Create a new table that contains a `hierarchyid` column.</span></span> <span data-ttu-id="7804f-106">이 열로 기존 **EmployeeID** 및 **ManagerID** 열을 대체할 수도 있지만</span><span class="sxs-lookup"><span data-stu-id="7804f-106">This column could replace the existing **EmployeeID** and **ManagerID** columns.</span></span> <span data-ttu-id="7804f-107">여기서는 해당 열을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-107">However, you will retain those columns.</span></span> <span data-ttu-id="7804f-108">이는 기존 애플리케이션에서 해당 열을 참조할 수 있으며 해당 열을 유지하는 것이 전송 후에 데이터를 이해하는 데 도움이 되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-108">This is because existing applications might refer to those columns, and also to help you understand the data after the transfer.</span></span> <span data-ttu-id="7804f-109">테이블 정의에서 **OrgNode** 를 기본 키로 지정하므로 해당 열에 고유 값을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-109">The table definition specifies that **OrgNode** is the primary key, which requires the column to contain unique values.</span></span> <span data-ttu-id="7804f-110">**OrgNode** 열의 클러스터형 인덱스는 **OrgNode** 시퀀스의 날짜를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-110">The clustered index on the **OrgNode** column will store the date in **OrgNode** sequence.</span></span>  
  
-   <span data-ttu-id="7804f-111">각 관리자에게 직접 보고하는 직원 수를 추적하는 데 사용되는 임시 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-111">Create a temporary table that is used to track how many employees report directly to each manager.</span></span>  
  
-   <span data-ttu-id="7804f-112">**EmployeeDemo** 테이블의 데이터를 사용하여 새 테이블을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-112">Populate the new table by using data from the **EmployeeDemo** table.</span></span>  
  
### <a name="to-create-a-new-table-named-neworg"></a><span data-ttu-id="7804f-113">NewOrg라는 새 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="7804f-113">To create a new table named NewOrg</span></span>  
  
-   <span data-ttu-id="7804f-114">쿼리 편집기 창에서 다음 코드를 실행하여 **HumanResources.NewOrg**라는 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-114">In a Query Editor window, run the following code to create a new table named **HumanResources.NewOrg**:</span></span>  
  
    ```  
    CREATE TABLE NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="to-create-a-temporary-table-named-children"></a><span data-ttu-id="7804f-115">#Children이라는 임시 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="7804f-115">To create a temporary table named #Children</span></span>  
  
1.  <span data-ttu-id="7804f-116">각 노드의 자식 수를 포함할 **Num** 열이 포함된 **#Children** 이라는 임시 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-116">Create a temporary table named **#Children** with a column named **Num** that will contain the number of children for each node:</span></span>  
  
    ```  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  <span data-ttu-id="7804f-117">**NewOrg** 테이블을 채우는 쿼리의 속도를 상당히 높일 인덱스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-117">Add an index that will significantly speed up the query that populates the **NewOrg** table:</span></span>  
  
    ```  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="to-populate-the-neworg-table"></a><span data-ttu-id="7804f-118">NewOrg 테이블을 채우려면</span><span class="sxs-lookup"><span data-stu-id="7804f-118">To populate the NewOrg table</span></span>  
  
1.  <span data-ttu-id="7804f-119">재귀 쿼리는 집계가 있는 하위 쿼리를 금지합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-119">Recursive queries forbid subqueries with aggregates.</span></span> <span data-ttu-id="7804f-120">대신 **ROW_NUMBER()** 메서드를 통해 [Num](/sql/t-sql/functions/row-number-transact-sql) 열을 채우는 다음 코드를 사용하여 **#Children** 테이블을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-120">Instead, populate the **#Children** table with the following code, which uses the [ROW_NUMBER()](/sql/t-sql/functions/row-number-transact-sql) method to populate the **Num** column:</span></span>  
  
    ```  
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM EmployeeDemo  
    GO  
  
    ```  
  
2.  <span data-ttu-id="7804f-121">**#Children** 테이블을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-121">Review the **#Children** table.</span></span> <span data-ttu-id="7804f-122">**Num** 열에 각 관리자에 대한 일련 번호가 포함되는 방식을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-122">Note how the **Num** column contains sequential numbers for each manager.</span></span>  
  
    ```  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     `EmployeeID ManagerID Num`  
  
     `---------- --------- ---`  
  
     `1        NULL       1`  
  
     `2         1         1`  
  
     `3         1         2`  
  
     `4         2         1`  
  
     `5         2         2`  
  
     `6         2         3`  
  
     `7         3         1`  
  
     `8         3         2`  
  
     `9         4         1`  
  
     `10        4         2`  
  
3.  <span data-ttu-id="7804f-123">**Neworg** 테이블을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-123">Populate the **NewOrg** table.</span></span> <span data-ttu-id="7804f-124">GetRoot 및 ToString 메서드를 사용 하 여 **Num** 값을 형식에 `hierarchyid` 연결한 다음 **OrgNode** 열을 결과 계층 값으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-124">Use the GetRoot and ToString methods to concatenate the **Num** values into the `hierarchyid` format, and then update the **OrgNode** column with the resultant hierarchical values:</span></span>  
  
    ```  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   
  
    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO  
  
    ```  
  
4.  <span data-ttu-id="7804f-125">`hierarchyid` 열을 문자 형식으로 변환하면 이해하기가 더 쉬워집니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-125">A `hierarchyid` column is more understandable when you convert it to character format.</span></span> <span data-ttu-id="7804f-126">**OrgNode** 열의 두 가지 표현이 포함된 다음 코드를 실행하여 **NewOrg** 테이블의 데이터를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-126">Review the data in the **NewOrg** table by executing the following code, which contains two representations of the **OrgNode** column:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM NewOrg   
    ORDER BY LogicalNode;  
    GO  
  
    ```  
  
     <span data-ttu-id="7804f-127">**Logicalnode** 열은 `hierarchyid` 계층을 나타내는 보다 읽기 쉬운 텍스트 형식으로 열을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-127">The **LogicalNode** column converts the `hierarchyid` column into a more readable text form that represents the hierarchy.</span></span> <span data-ttu-id="7804f-128">나머지 태스크에서는 `ToString()` 메서드를 사용하여 `hierarchyid` 열의 논리 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-128">In the remaining tasks, you will use the `ToString()` method to show the logical format of the `hierarchyid` columns.</span></span>  
  
5.  <span data-ttu-id="7804f-129">더 이상 필요하지 않은 임시 테이블을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-129">Drop the temporary table, which is no longer needed:</span></span>  
  
    ```  
    DROP TABLE #Children  
    GO  
    ```  
  
 <span data-ttu-id="7804f-130">다음 태스크에서는 계층 구조를 지원하는 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7804f-130">The next task will create indexes to support the hierarchical structure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7804f-131">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="7804f-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7804f-132">NewOrg 테이블 최적화</span><span class="sxs-lookup"><span data-stu-id="7804f-132">Optimizing the NewOrg Table</span></span>](lesson-1-3-optimizing-the-neworg-table.md)  
  
  
