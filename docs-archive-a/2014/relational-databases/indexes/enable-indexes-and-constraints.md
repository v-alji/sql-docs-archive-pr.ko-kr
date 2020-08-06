---
title: 인덱스 및 제약 조건 활성화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], enabling
- nonclustered indexes [SQL Server], enabling a disabled index
- index enabling [SQL Server]
- disabled indexes [SQL Server], how to enable
- constraints [SQL Server], enabling
- clustered indexes, enabling disabled indexes
ms.assetid: c55c8865-322e-4ab0-ba04-ea1f56735353
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d4e79689b80a40d00958fa557fe51df2adf9c14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660572"
---
# <a name="enable-indexes-and-constraints"></a><span data-ttu-id="b2b5a-102">인덱스 및 제약 조건 활성화</span><span class="sxs-lookup"><span data-stu-id="b2b5a-102">Enable Indexes and Constraints</span></span>
  <span data-ttu-id="b2b5a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 비활성화된 인덱스를 활성화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-103">This topic describes how to enable a disabled index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b2b5a-104">비활성화된 인덱스는 다시 작성되거나 삭제될 때까지 비활성화된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-104">After an index is disabled, it remains in a disabled state until it is rebuilt or dropped</span></span>  
  
 <span data-ttu-id="b2b5a-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b2b5a-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b2b5a-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b2b5a-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b2b5a-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b2b5a-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b2b5a-108">보안</span><span class="sxs-lookup"><span data-stu-id="b2b5a-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b2b5a-109">**비활성화된 인덱스를 활성화하려면:**</span><span class="sxs-lookup"><span data-stu-id="b2b5a-109">**To enable a disabled index, using:**</span></span>  
  
     [<span data-ttu-id="b2b5a-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b2b5a-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b2b5a-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b2b5a-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b2b5a-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b2b5a-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b2b5a-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b2b5a-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b2b5a-114">인덱스를 다시 작성한 후에 해당 인덱스를 비활성화하여 비활성화된 제약 조건은 수동으로 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-114">After rebuilding the index, any constraints that were disabled because of disabling the index must be manually enabled.</span></span> <span data-ttu-id="b2b5a-115">연관된 인덱스를 다시 작성하여 PRIMARY KEY 및 UNIQUE 제약 조건을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-115">PRIMARY KEY and UNIQUE constraints are enabled by rebuilding the associated index.</span></span> <span data-ttu-id="b2b5a-116">PRIMARY KEY 또는 UNIQUE 제약 조건을 참조하는 FOREIGN KEY 제약 조건을 활성화하기 전에 이 인덱스를 다시 작성(활성화)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-116">This index must be rebuilt (enabled) before you can enable FOREIGN KEY constraints that reference the PRIMARY KEY or UNIQUE constraint.</span></span> <span data-ttu-id="b2b5a-117">ALTER TABLE CHECK CONSTRAINT 문을 사용하여 FOREIGN KEY 제약 조건을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-117">FOREIGN KEY constraints are enabled by using the ALTER TABLE CHECK CONSTRAINT statement.</span></span>  
  
-   <span data-ttu-id="b2b5a-118">ONLINE 옵션이 ON으로 설정된 경우 비활성화된 클러스터형 인덱스를 다시 작성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-118">Rebuilding a disabled clustered index cannot be performed when the ONLINE option is set to ON.</span></span>  
  
-   <span data-ttu-id="b2b5a-119">클러스터형 인덱스를 비활성화하거나 활성화하고 비클러스터형 인덱스를 비활성화하면 클러스터형 인덱스 동작으로 인해 다음과 같은 결과가 비활성화된 비클러스터형 인덱스에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-119">When the clustered index is disabled or enabled and the nonclustered index is disabled, the clustered index action has the following results on the disabled nonclustered index.</span></span>  
  
    |<span data-ttu-id="b2b5a-120">클러스터형 인덱스 동작</span><span class="sxs-lookup"><span data-stu-id="b2b5a-120">Clustered Index Action</span></span>|<span data-ttu-id="b2b5a-121">비활성화된 비클러스터형 인덱스...</span><span class="sxs-lookup"><span data-stu-id="b2b5a-121">Disabled Nonclustered Index ...</span></span>|  
    |----------------------------|-----------------------------------|  
    |<span data-ttu-id="b2b5a-122">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="b2b5a-122">ALTER INDEX REBUILD.</span></span>|<span data-ttu-id="b2b5a-123">비활성화된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-123">Remains disabled.</span></span>|  
    |<span data-ttu-id="b2b5a-124">ALTER INDEX ALL REBUILD</span><span class="sxs-lookup"><span data-stu-id="b2b5a-124">ALTER INDEX ALL REBUILD.</span></span>|<span data-ttu-id="b2b5a-125">다시 작성되고 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-125">Is rebuilt and enabled.</span></span>|  
    |<span data-ttu-id="b2b5a-126">DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="b2b5a-126">DROP INDEX.</span></span>|<span data-ttu-id="b2b5a-127">비활성화된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-127">Remains disabled.</span></span>|  
    |<span data-ttu-id="b2b5a-128">CREATE INDEX WITH DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="b2b5a-128">CREATE INDEX WITH DROP_EXISTING.</span></span>|<span data-ttu-id="b2b5a-129">비활성화된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-129">Remains disabled.</span></span>|  
  
     <span data-ttu-id="b2b5a-130">클러스터형 인덱스를 새로 만들 때의 동작은 ALTER INDEX ALL REBUILD를 사용할 때와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-130">Creating a new clustered index, behaves the same as ALTER INDEX ALL REBUILD.</span></span>  
  
-   <span data-ttu-id="b2b5a-131">클러스터형 인덱스와 연관된 비클러스터형 인덱스에 허용된 동작은 두 인덱스 유형의 상태(비활성화되어 있거나 활성화되어 있는지)에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-131">Allowed actions on nonclustered indexes associated with a clustered index depend on the state, whether disabled or enabled, of both index types.</span></span> <span data-ttu-id="b2b5a-132">다음 표에는 비클러스터형 인덱스에 허용된 동작이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-132">The following table summarizes the allowed actions on nonclustered indexes.</span></span>  
  
    |<span data-ttu-id="b2b5a-133">비클러스터형 인덱스 동작</span><span class="sxs-lookup"><span data-stu-id="b2b5a-133">Nonclustered Index Action</span></span>|<span data-ttu-id="b2b5a-134">클러스터형 인덱스와 비클러스터형 인덱스가 모두 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-134">When both the clustered and nonclustered indexes are disabled.</span></span>|<span data-ttu-id="b2b5a-135">클러스터형 인덱스가 활성화되고 비클러스터형 인덱스는 비활성화되거나 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-135">When the clustered index is enabled and the nonclustered index is in either state.</span></span>|  
    |-------------------------------|--------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
    |<span data-ttu-id="b2b5a-136">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="b2b5a-136">ALTER INDEX REBUILD.</span></span>|<span data-ttu-id="b2b5a-137">동작이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-137">The action fails.</span></span>|<span data-ttu-id="b2b5a-138">동작이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-138">The action succeeds.</span></span>|  
    |<span data-ttu-id="b2b5a-139">DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="b2b5a-139">DROP INDEX.</span></span>|<span data-ttu-id="b2b5a-140">동작이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-140">The action succeeds.</span></span>|<span data-ttu-id="b2b5a-141">동작이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-141">The action succeeds.</span></span>|  
    |<span data-ttu-id="b2b5a-142">CREATE INDEX WITH DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="b2b5a-142">CREATE INDEX WITH DROP_EXISTING.</span></span>|<span data-ttu-id="b2b5a-143">동작이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-143">The action fails.</span></span>|<span data-ttu-id="b2b5a-144">동작이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-144">The action succeeds.</span></span>|  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b2b5a-145">보안</span><span class="sxs-lookup"><span data-stu-id="b2b5a-145">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b2b5a-146">권한</span><span class="sxs-lookup"><span data-stu-id="b2b5a-146">Permissions</span></span>  
 <span data-ttu-id="b2b5a-147">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-147">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="b2b5a-148">DBCC DBREINDEX를 사용하는 경우 사용자는 테이블의 소유자이거나 **sysadmin** 고정 서버 역할 또는 **db_ddladmin** 및 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-148">If using DBCC DBREINDEX, eser must either own the table or be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b2b5a-149">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b2b5a-149">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-a-disabled-index"></a><span data-ttu-id="b2b5a-150">비활성화된 인덱스를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="b2b5a-150">To enable a disabled index</span></span>  
  
1.  <span data-ttu-id="b2b5a-151">개체 탐색기에서 더하기 기호를 클릭하여 인덱스를 활성화할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-151">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to enable an index.</span></span>  
  
2.  <span data-ttu-id="b2b5a-152">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-152">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="b2b5a-153">더하기 기호를 클릭하여 인덱스를 활성화할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-153">Click the plus sign to expand the table on which you want to enable an index.</span></span>  
  
4.  <span data-ttu-id="b2b5a-154">더하기 기호를 클릭하여 **인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-154">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="b2b5a-155">활성화할 인덱스를 마우스 오른쪽 단추로 클릭하고 **다시 작성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-155">Right-click the index you want to enable and select **Rebuild**.</span></span>  
  
6.  <span data-ttu-id="b2b5a-156">**인덱스 다시 작성** 대화 상자에서 **다시 작성할 인덱스** 표에 올바른 인덱스가 있는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-156">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to rebuild** grid and click **OK**.</span></span>  
  
#### <a name="to-enable-all-indexes-on-a-table"></a><span data-ttu-id="b2b5a-157">테이블의 모든 인덱스를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="b2b5a-157">To enable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="b2b5a-158">개체 탐색기에서 더하기 기호를 클릭하여 인덱스를 활성화할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-158">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to enable the indexes.</span></span>  
  
2.  <span data-ttu-id="b2b5a-159">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-159">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="b2b5a-160">더하기 기호를 클릭하여 인덱스를 활성화할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-160">Click the plus sign to expand the table on which you want to enable the indexes.</span></span>  
  
4.  <span data-ttu-id="b2b5a-161">**인덱스** 폴더를 마우스 오른쪽 단추로 클릭하고 **모두 다시 작성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-161">Right-click the **Indexes** folder and select **Rebuild All**.</span></span>  
  
5.  <span data-ttu-id="b2b5a-162">**인덱스 다시 작성** 대화 상자에서 **다시 작성할 인덱스** 표에 올바른 인덱스가 있는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-162">In the **Rebuild Indexes** dialog box, verify that the correct indexes are in the **Indexes to rebuild** grid and click **OK**.</span></span> <span data-ttu-id="b2b5a-163">**다시 작성할 인덱스** 표에서 인덱스를 제거하려면 인덱스를 선택한 다음 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-163">To remove an index from the **Indexes to rebuild** grid, select the index and then press the Delete key.</span></span>  
  
 <span data-ttu-id="b2b5a-164">**인덱스 다시 작성** 대화 상자에는 다음 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-164">The following information is available in the **Rebuild Indexes** dialog box:</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b2b5a-165">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b2b5a-165">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-a-disabled-index-using-alter-index"></a><span data-ttu-id="b2b5a-166">ALTER INDEX를 사용하여 비활성화된 인덱스를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="b2b5a-166">To enable a disabled index using ALTER INDEX</span></span>  
  
1.  <span data-ttu-id="b2b5a-167">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b2b5a-168">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b2b5a-169">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table.  
  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    REBUILD;   
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-create-index"></a><span data-ttu-id="b2b5a-170">CREATE INDEX를 사용하여 비활성화된 인덱스를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="b2b5a-170">To enable a disabled index using CREATE INDEX</span></span>  
  
1.  <span data-ttu-id="b2b5a-171">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-171">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b2b5a-172">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-172">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b2b5a-173">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-173">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- re-creates the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    -- using the OrganizationLevel and OrganizationNode columns  
    -- and then deletes the existing IX_Employee_OrganizationLevel_OrganizationNode index  
    CREATE INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
       (OrganizationLevel, OrganizationNode)  
    WITH (DROP_EXISTING = ON);  
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-dbcc-dbreindex"></a><span data-ttu-id="b2b5a-174">DBCC DBREINDEX를 사용하여 비활성화된 인덱스를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="b2b5a-174">To enable a disabled index using DBCC DBREINDEX</span></span>  
  
1.  <span data-ttu-id="b2b5a-175">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-175">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b2b5a-176">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-176">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b2b5a-177">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-177">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", IX_Employee_OrganizationLevel_OrganizationNode);  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-alter-index"></a><span data-ttu-id="b2b5a-178">ALTER INDEX를 사용하여 테이블의 모든 인덱스를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="b2b5a-178">To enable all indexes on a table using ALTER INDEX</span></span>  
  
1.  <span data-ttu-id="b2b5a-179">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-179">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b2b5a-180">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-180">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b2b5a-181">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-181">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    ALTER INDEX ALL ON HumanResources.Employee  
    REBUILD;  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-dbcc-dbreindex"></a><span data-ttu-id="b2b5a-182">DBCC DBREINDEX를 사용하여 테이블의 모든 인덱스를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="b2b5a-182">To enable all indexes on a table using DBCC DBREINDEX</span></span>  
  
1.  <span data-ttu-id="b2b5a-183">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-183">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b2b5a-184">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-184">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b2b5a-185">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-185">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", " ");  
    GO  
    ```  
  
 <span data-ttu-id="b2b5a-186">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql), [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) 및 [DBCC DBREINDEX&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2b5a-186">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql), [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql), and [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql).</span></span>  
  
  
