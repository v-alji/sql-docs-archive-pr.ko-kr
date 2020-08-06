---
title: 뷰를 통해 데이터 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- data modifications [SQL Server], views
- views [SQL Server], modifying data through
- modifying data [SQL Server], views
ms.assetid: 410e2812-4ebe-48b2-b95f-c7784f1c4336
author: stevestein
ms.author: sstein
ms.openlocfilehash: df1eb4a33d1d10e63363e52760dad805b20c0a8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646254"
---
# <a name="modify-data-through-a-view"></a><span data-ttu-id="fac68-102">뷰를 통해 데이터 수정</span><span class="sxs-lookup"><span data-stu-id="fac68-102">Modify Data Through a View</span></span>
  <span data-ttu-id="fac68-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 기본 테이블의 데이터를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-103">You can modify the data of an underlying base table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="fac68-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="fac68-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fac68-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="fac68-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fac68-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fac68-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fac68-107">보안</span><span class="sxs-lookup"><span data-stu-id="fac68-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fac68-108">**뷰를 통해 테이블 데이터를 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="fac68-108">**To modify table data through a view, using:**</span></span>  
  
     [<span data-ttu-id="fac68-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fac68-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fac68-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fac68-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fac68-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fac68-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fac68-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fac68-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fac68-113">[CREATE VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)의 '업데이트할 수 있는 뷰' 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fac68-113">See the section 'Updatable Views' in [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fac68-114">보안</span><span class="sxs-lookup"><span data-stu-id="fac68-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fac68-115">권한</span><span class="sxs-lookup"><span data-stu-id="fac68-115">Permissions</span></span>  
 <span data-ttu-id="fac68-116">수행하는 동작에 따라 대상 테이블에 대한 UPDATE, INSERT 또는 DELETE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-116">Requires UPDATE, INSERT, or DELETE permissions on the target table, depending on the action being performed.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fac68-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="fac68-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-table-data-through-a-view"></a><span data-ttu-id="fac68-118">뷰를 통해 테이블 데이터를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="fac68-118">To modify table data through a view</span></span>  
  
1.  <span data-ttu-id="fac68-119">**개체 탐색기**에서 뷰가 포함된 데이터베이스를 확장한 다음 **뷰**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-119">In **Object Explorer**, expand the database that contains the view and then expand **Views**.</span></span>  
  
2.  <span data-ttu-id="fac68-120">뷰를 마우스 오른쪽 단추로 클릭하고 **상위 200개의 행 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-120">Right-click the view and select **Edit Top 200 Rows**.</span></span>  
  
3.  <span data-ttu-id="fac68-121">수정될 행을 반환하기 위해 **SQL** 창에서 SELECT 문을 수정해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-121">You may need to modify the SELECT statement in the **SQL** pane to return the rows to be modified.</span></span>  
  
4.  <span data-ttu-id="fac68-122">**결과** 창에서 변경하거나 삭제할 행을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-122">In the **Results** pane, locate the row to be changed or deleted.</span></span> <span data-ttu-id="fac68-123">행을 삭제하려면 행을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-123">To delete the row, right-click the row and select **Delete**.</span></span> <span data-ttu-id="fac68-124">하나 이상의 열에서 데이터를 변경하려면 열에서 데이터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-124">To change data in one or more columns, modify the data in the column.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fac68-125">뷰가 여러 개의 기본 테이블을 참조하는 경우 행을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-125">You cannot delete a row if the view references more than one base table.</span></span> <span data-ttu-id="fac68-126">단일 기본 테이블에 속하는 열만 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-126">You can only update columns that belong to a single base table.</span></span>  
  
5.  <span data-ttu-id="fac68-127">행을 삽입하려면 행의 끝으로 스크롤하여 새 값을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-127">To insert a row, scroll down to the end of the rows and insert the new values.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fac68-128">뷰가 여러 개의 기본 테이블을 참조하는 경우 행을 삽입할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-128">You cannot insert a row if the view references more than one base table.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fac68-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="fac68-129">Using Transact-SQL</span></span>  
  
#### <a name="to-update-table-data-through-a-view"></a><span data-ttu-id="fac68-130">뷰를 통해 테이블 데이터를 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="fac68-130">To update table data through a view</span></span>  
  
1.  <span data-ttu-id="fac68-131">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fac68-132">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fac68-133">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-133">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="fac68-134">다음 예에서는 뷰 `StartDate` 의 열을 참조하여 특정 직원의 `EndDate` 및 `HumanResources.vEmployeeDepartmentHistory`열 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-134">This example changes the value in the `StartDate` and `EndDate` columns for a specific employee by referencing columns in the view `HumanResources.vEmployeeDepartmentHistory`.</span></span> <span data-ttu-id="fac68-135">이 뷰는 두 테이블에서 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-135">This view returns values from two tables.</span></span> <span data-ttu-id="fac68-136">수정할 열이 하나의 기본 테이블에만 속해 있기 때문에 다음 문은 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-136">This statement succeeds because the columns being modified are from only one of the base tables.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    UPDATE HumanResources.vEmployeeDepartmentHistory  
    SET StartDate = '20110203', EndDate = GETDATE()   
    WHERE LastName = N'Smith' AND FirstName = 'Samantha';   
    GO  
    ```  
  
 <span data-ttu-id="fac68-137">자세한 내용은 [UPDATE&#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fac68-137">For more information, see [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql).</span></span>  
  
#### <a name="to-insert-table-data-through-a-view"></a><span data-ttu-id="fac68-138">뷰를 통해 테이블 데이터를 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="fac68-138">To insert table data through a view</span></span>  
  
1.  <span data-ttu-id="fac68-139">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fac68-140">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fac68-141">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-141">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="fac68-142">다음 예에서는 뷰 `HumanResouces.Department` 의 관련 열을 지정하여 기본 테이블 `HumanResources.vEmployeeDepartmentHistory`에 새 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-142">The example inserts a new row into the base table `HumanResouces.Department` by specifying the relevant columns from the view `HumanResources.vEmployeeDepartmentHistory`.</span></span> <span data-ttu-id="fac68-143">단일 기본 테이블의 열만 지정되고 기본 테이블의 다른 열에 기본값이 들어 있으므로 이 문은 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="fac68-143">The statement succeeds because only columns from a single base table are specified and the other columns in the base table have default values.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    INSERT INTO HumanResources.vEmployeeDepartmentHistory (Department, GroupName)   
    VALUES ('MyDepartment', 'MyGroup');   
    GO  
    ```  
  
 <span data-ttu-id="fac68-144">자세한 내용은 [INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fac68-144">For more information, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).</span></span>  
  
  
