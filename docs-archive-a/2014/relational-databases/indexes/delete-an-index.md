---
title: 인덱스 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- dropping indexes
- indexes [SQL Server], dropping
- index deletions [SQL Server]
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4552ba701782e5790f95f54c0c1c66f82573f1e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740932"
---
# <a name="delete-an-index"></a><span data-ttu-id="c3872-102">인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="c3872-102">Delete an Index</span></span>
  <span data-ttu-id="c3872-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 인덱스를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-103">This topic describes how to delete (drop) an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c3872-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c3872-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c3872-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c3872-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c3872-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c3872-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c3872-107">보안</span><span class="sxs-lookup"><span data-stu-id="c3872-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c3872-108">**인덱스를 삭제하려면:**</span><span class="sxs-lookup"><span data-stu-id="c3872-108">**To delete an index, using:**</span></span>  
  
     [<span data-ttu-id="c3872-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c3872-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c3872-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c3872-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c3872-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c3872-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c3872-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c3872-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c3872-113">PRIMARY KEY 또는 UNIQUE 제약 조건으로 생성된 인덱스는 이 방법으로 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-113">Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be deleted by using this method.</span></span> <span data-ttu-id="c3872-114">대신 제약 조건을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-114">Instead, the constraint must be deleted.</span></span> <span data-ttu-id="c3872-115">제약 조건과 해당 인덱스를 제거하려면 [에서](/sql/t-sql/statements/alter-table-transact-sql) ALTER TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)]에 DROP CONSTRAINT 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-115">To remove the constraint and corresponding index, use [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) with the DROP CONSTRAINT clause in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c3872-116">자세한 내용은 [Delete Primary Keys](../tables/delete-primary-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3872-116">For more information, see [Delete Primary Keys](../tables/delete-primary-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c3872-117">보안</span><span class="sxs-lookup"><span data-stu-id="c3872-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c3872-118">권한</span><span class="sxs-lookup"><span data-stu-id="c3872-118">Permissions</span></span>  
 <span data-ttu-id="c3872-119">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-119">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="c3872-120">이 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_ddladmin** 및 **db_owner** 고정 데이터베이스 역할에 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-120">This permission is granted by default to the **sysadmin** fixed server role and the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c3872-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c3872-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-index-by-using-object-explorer"></a><span data-ttu-id="c3872-122">개체 탐색기를 사용하여 인덱스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="c3872-122">To delete an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="c3872-123">개체 탐색기에서 인덱스를 삭제할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-123">In Object Explorer, expand the database that contains the table on which you want to delete an index.</span></span>  
  
2.  <span data-ttu-id="c3872-124">**테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-124">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="c3872-125">삭제할 인덱스가 포함된 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-125">Expand the table that contains the index you want to delete.</span></span>  
  
4.  <span data-ttu-id="c3872-126">**인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-126">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="c3872-127">삭제할 인덱스를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-127">Right-click the index you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="c3872-128">**개체 삭제** 대화 상자에서 올바른 인덱스가 **삭제할 개체** 에 있는지 확인하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-128">In the **Delete Object** dialog box, verify that the correct index is in the **Object to be deleted** grid and click **OK**.</span></span>  
  
#### <a name="to-delete-an-index-using-table-designer"></a><span data-ttu-id="c3872-129">테이블 디자이너를 사용하여 인덱스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="c3872-129">To delete an index using Table Designer</span></span>  
  
1.  <span data-ttu-id="c3872-130">개체 탐색기에서 인덱스를 삭제할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-130">In Object Explorer, expand the database that contains the table on which you want to delete an index.</span></span>  
  
2.  <span data-ttu-id="c3872-131">**테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-131">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="c3872-132">삭제할 인덱스가 포함된 테이블을 마우스 오른쪽 단추로 클릭하고 디자인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-132">Right-click the table that contains the index you want to delete and click Design.</span></span>  
  
4.  <span data-ttu-id="c3872-133">**테이블 디자이너** 메뉴에서 **인덱스/키**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-133">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="c3872-134">**인덱스/키** 대화 상자에서 삭제하려는 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-134">In the **Indexes/Keys** dialog box, select the index you want to delete.</span></span>  
  
6.  <span data-ttu-id="c3872-135">**삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-135">Click **Delete**.</span></span>  
  
7.  <span data-ttu-id="c3872-136">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-136">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="c3872-137">**파일** 메뉴에서 _table_name_**저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-137">On the **File** menu, select **Save**_table_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c3872-138">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c3872-138">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-index"></a><span data-ttu-id="c3872-139">인덱스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="c3872-139">To delete an index</span></span>  
  
1.  <span data-ttu-id="c3872-140">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3872-141">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c3872-142">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3872-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 <span data-ttu-id="c3872-143">자세한 내용은 [DROP INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3872-143">For more information, see [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql).</span></span>  
  
  
