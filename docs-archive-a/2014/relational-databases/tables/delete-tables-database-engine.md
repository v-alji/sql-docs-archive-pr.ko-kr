---
title: 테이블 삭제(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table deletions [SQL Server]
- deleting tables
- removing tables
- dropping tables
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e361456534f565f854d348bbef5751c7d66c0f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738158"
---
# <a name="delete-tables-database-engine"></a><span data-ttu-id="25c9b-102">테이블 삭제(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="25c9b-102">Delete Tables (Database Engine)</span></span>
  <span data-ttu-id="25c9b-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 데이터베이스에서 테이블을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-103">You can delete (drop) a table from your database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="25c9b-104">테이블을 삭제할 때는 신중한 검토가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-104">Think carefully before you delete a table.</span></span> <span data-ttu-id="25c9b-105">기존의 쿼리, 뷰, 사용자 정의 함수, 저장 프로시저 또는 프로그램에서 해당 테이블을 참조하는 경우 테이블을 삭제하면 이 개체들은 유효하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-105">If existing queries, views, user-defined functions, stored procedures, or programs refer to that table, the deletion will make these objects invalid.</span></span>  
  
 <span data-ttu-id="25c9b-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="25c9b-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="25c9b-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="25c9b-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="25c9b-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="25c9b-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="25c9b-109">보안</span><span class="sxs-lookup"><span data-stu-id="25c9b-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="25c9b-110">**테이블을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="25c9b-110">**To Delete a Table, using:**</span></span>  
  
     [<span data-ttu-id="25c9b-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="25c9b-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="25c9b-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="25c9b-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="25c9b-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="25c9b-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="25c9b-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="25c9b-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="25c9b-115">FOREIGN KEY 제약 조건에 의해 참조되는 테이블은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-115">You cannot drop a table that is referenced by a FOREIGN KEY constraint.</span></span> <span data-ttu-id="25c9b-116">참조하는 FOREIGN KEY 제약 조건 또는 참조하는 테이블을 먼저 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-116">The referencing FOREIGN KEY constraint or the referencing table must first be dropped.</span></span> <span data-ttu-id="25c9b-117">참조하는 테이블과 기본 키를 포함하는 테이블이 하나의 DROP TABLE 문에서 삭제되는 경우 참조하는 테이블이 먼저 나열되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-117">If both the referencing table and the table that holds the primary key are being dropped in the same DROP TABLE statement, the referencing table must be listed first.</span></span>  
  
-   <span data-ttu-id="25c9b-118">테이블을 삭제하면 해당 테이블에 있는 규칙이나 기본값의 바인딩이 해제되고 해당 테이블과 연결된 제약 조건이나 트리거가 자동으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-118">When a table is dropped, rules or defaults on the table lose their binding, and any constraints or triggers associated with the table are automatically dropped.</span></span> <span data-ttu-id="25c9b-119">테이블을 다시 만들려면 해당 규칙과 기본값을 다시 바인딩하고 트리거를 다시 만들어야 하며 필요한 제약 조건을 모두 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-119">If you re-create a table, you must rebind the appropriate rules and defaults, re-create any triggers, and add all required constraints.</span></span>  
  
-   <span data-ttu-id="25c9b-120">FILESTREAM 특성이 있는 `varbinary (max)` 열이 포함된 테이블을 삭제해도 파일 시스템에 저장된 데이터는 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-120">If you drop a table that contains a `varbinary (max)` column with the FILESTREAM attribute, any data stored in the file system will not be removed.</span></span>  
  
-   <span data-ttu-id="25c9b-121">동일한 일괄 처리에서 동일한 테이블에 대해 DROP TABLE과 CREATE TABLE을 실행할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-121">DROP TABLE and CREATE TABLE should not be executed on the same table in the same batch.</span></span> <span data-ttu-id="25c9b-122">이를 실행하면 예기치 않은 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-122">Otherwise an unexpected error may occur.</span></span>  
  
-   <span data-ttu-id="25c9b-123">삭제된 테이블을 참조하는 뷰나 저장 프로시저는 명시적으로 삭제하거나 테이블에 대한 참조를 제거하도록 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-123">Any view or stored procedure that references the dropped table must be explicitly deleted or modified to remove the reference to the table.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="25c9b-124">보안</span><span class="sxs-lookup"><span data-stu-id="25c9b-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="25c9b-125">권한</span><span class="sxs-lookup"><span data-stu-id="25c9b-125">Permissions</span></span>  
 <span data-ttu-id="25c9b-126">테이블이 속한 스키마에 대한 ALTER 권한, 테이블에 대한 CONTROL 권한 또는 **db_ddladmin** 고정 데이터베이스 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-126">Requires ALTER permission on the schema to which the table belongs, CONTROL permission on the table, or membership in the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="25c9b-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="25c9b-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-table-from-the-database"></a><span data-ttu-id="25c9b-128">데이터베이스에서 테이블을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="25c9b-128">To delete a table from the database</span></span>  
  
1.  <span data-ttu-id="25c9b-129">개체 탐색기에서 삭제하려는 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-129">In Object Explorer, select the table you want to delete.</span></span>  
  
2.  <span data-ttu-id="25c9b-130">테이블을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **삭제** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-130">Right-click the table and choose **Delete** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="25c9b-131">삭제를 확인하는 메시지 상자가 나타나면</span><span class="sxs-lookup"><span data-stu-id="25c9b-131">A message box prompts you to confirm the deletion.</span></span> <span data-ttu-id="25c9b-132">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-132">Click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="25c9b-133">테이블을 삭제하면 테이블에 대한 모든 관계도 자동으로 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-133">Deleting a table automatically removes any relationships to it.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="25c9b-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="25c9b-134">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-table-in-query-editor"></a><span data-ttu-id="25c9b-135">쿼리 편집기에서 테이블을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="25c9b-135">To delete a table in Query Editor</span></span>  
  
1.  <span data-ttu-id="25c9b-136">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="25c9b-137">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="25c9b-138">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25c9b-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 <span data-ttu-id="25c9b-139">자세한 내용은 [DROP TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25c9b-139">For more information, see [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)</span></span>  
  
  
