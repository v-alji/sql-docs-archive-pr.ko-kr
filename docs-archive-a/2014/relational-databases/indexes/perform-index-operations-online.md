---
title: 온라인으로 인덱스 작업 수행 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d09bd99a0eaec5fdb433bd8c33351d7622957a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660556"
---
# <a name="perform-index-operations-online"></a><span data-ttu-id="be5ff-102">온라인으로 인덱스 작업 수행</span><span class="sxs-lookup"><span data-stu-id="be5ff-102">Perform Index Operations Online</span></span>
  <span data-ttu-id="be5ff-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 온라인으로 인덱스를 만들거나, 다시 작성하거나, 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-103">This topic describes how to create, rebuild, or drop indexes online in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="be5ff-104">ONLINE 옵션을 사용하면 여러 사용자가 인덱스 작업 동안 기본 테이블이나 클러스터형 인덱스 데이터 및 모든 관련 비클러스터형 인덱스에 동시에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-104">The ONLINE option allows concurrent user access to the underlying table or clustered index data and any associated nonclustered indexes during these index operations.</span></span> <span data-ttu-id="be5ff-105">예를 들어 특정 사용자가 클러스터형 인덱스를 다시 작성하는 동안 해당 사용자와 다른 사용자가 계속해서 기본 데이터를 업데이트하고 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-105">For example, while a clustered index is being rebuilt by one user, that user and others can continue to update and query the underlying data.</span></span> <span data-ttu-id="be5ff-106">클러스터형 인덱스 작성 또는 다시 작성 등의 DDL(데이터 정의 언어) 작업을 오프라인으로 수행할 때 이러한 작업은 기본 데이터와 관련 인덱스에 대해 배타적 잠금을 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-106">When you perform data definition language (DDL) operations offline, such as building or rebuilding a clustered index; these operations hold exclusive locks on the underlying data and associated indexes.</span></span> <span data-ttu-id="be5ff-107">이로 인해 해당 인덱스 작업이 완료될 때까지 기본 데이터를 수정하거나 쿼리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-107">This prevents modifications and queries to the underlying data until the index operation is complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be5ff-108">온라인 인덱스 작업은 일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-108">Online index operations are not available in every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition.</span></span> <span data-ttu-id="be5ff-109">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be5ff-109">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="be5ff-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="be5ff-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="be5ff-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="be5ff-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="be5ff-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="be5ff-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="be5ff-113">보안</span><span class="sxs-lookup"><span data-stu-id="be5ff-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="be5ff-114">**온라인으로 인덱스를 다시 작성하려면:**</span><span class="sxs-lookup"><span data-stu-id="be5ff-114">**To rebuild an index online, using:**</span></span>  
  
     [<span data-ttu-id="be5ff-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="be5ff-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="be5ff-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="be5ff-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="be5ff-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="be5ff-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="be5ff-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="be5ff-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="be5ff-119">온라인 인덱스 작업은 인덱스 작업 동안 동시 사용자 작업이 필수적인 1년 365일, 하루 24시간 운영되는 비즈니스 환경에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-119">We recommend performing online index operations for business environments that operate 24 hours a day, seven days a week, in which the need for concurrent user activity during index operations is vital.</span></span>  
  
-   <span data-ttu-id="be5ff-120">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 ONLINE 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-120">The ONLINE option is available in the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
    -   [<span data-ttu-id="be5ff-121">CREATE  INDEX</span><span class="sxs-lookup"><span data-stu-id="be5ff-121">CREATE INDEX</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
    -   [<span data-ttu-id="be5ff-122">ALTER INDEX</span><span class="sxs-lookup"><span data-stu-id="be5ff-122">ALTER INDEX</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
    -   [<span data-ttu-id="be5ff-123">DROP  INDEX</span><span class="sxs-lookup"><span data-stu-id="be5ff-123">DROP INDEX</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
    -   <span data-ttu-id="be5ff-124">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (CLUSTERED 인덱스 옵션을 사용하는 UNIQUE 또는 PRIMARY KEY 제약 조건을 추가하거나 삭제하려는 경우)</span><span class="sxs-lookup"><span data-stu-id="be5ff-124">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (To add or drop UNIQUE or PRIMARY KEY constraints with CLUSTERED index option)</span></span>  
  
-   <span data-ttu-id="be5ff-125">온라인으로 인덱스를 만들거나, 다시 작성하거나, 삭제하는 작업과 관련된 제한 사항은 [온라인 인덱스 작업에 대한 지침](guidelines-for-online-index-operations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be5ff-125">For more limitations and restrictions concerning creating, rebuilding, or dropping indexes online, see [Guidelines for Online Index Operations](guidelines-for-online-index-operations.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="be5ff-126">보안</span><span class="sxs-lookup"><span data-stu-id="be5ff-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="be5ff-127">권한</span><span class="sxs-lookup"><span data-stu-id="be5ff-127">Permissions</span></span>  
 <span data-ttu-id="be5ff-128">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-128">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="be5ff-129">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="be5ff-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rebuild-an-index-online"></a><span data-ttu-id="be5ff-130">온라인으로 인덱스를 다시 작성하려면</span><span class="sxs-lookup"><span data-stu-id="be5ff-130">To rebuild an index online</span></span>  
  
1.  <span data-ttu-id="be5ff-131">개체 탐색기에서 더하기 기호를 클릭하여 온라인으로 인덱스를 다시 작성할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-131">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rebuild an index online.</span></span>  
  
2.  <span data-ttu-id="be5ff-132">**테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-132">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="be5ff-133">더하기 기호를 클릭하여 온라인으로 인덱스를 다시 작성할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-133">Click the plus sign to expand the table on which you want to rebuild an index online.</span></span>  
  
4.  <span data-ttu-id="be5ff-134">**인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-134">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="be5ff-135">온라인으로 다시 작성할 인덱스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-135">Right-click the index that you want to rebuild online and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="be5ff-136">**페이지 선택**아래에서 **옵션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-136">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="be5ff-137">**온라인 DML 처리 허용**을 선택한 다음 목록에서 **True** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-137">Select **Allow online DML processing**, and then select **True** from the list.</span></span>  
  
8.  <span data-ttu-id="be5ff-138">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-138">Click **OK**.</span></span>  
  
9. <span data-ttu-id="be5ff-139">온라인으로 다시 작성할 인덱스를 마우스 오른쪽 단추로 클릭하고 **다시 작성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-139">Right-click the index that you want to rebuild online and select **Rebuild**.</span></span>  
  
10. <span data-ttu-id="be5ff-140">**인덱스 다시 작성** 대화 상자에서 **다시 작성할 인덱스** 표에 올바른 인덱스가 있는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-140">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to rebuild** grid and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="be5ff-141">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="be5ff-141">Using Transact-SQL</span></span>  
  
#### <a name="to-create-rebuild-or-drop-an-index-online"></a><span data-ttu-id="be5ff-142">온라인으로 인덱스를 만들거나, 다시 작성하거나, 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="be5ff-142">To create, rebuild, or drop an index online</span></span>  
  
1.  <span data-ttu-id="be5ff-143">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-143">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="be5ff-144">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-144">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="be5ff-145">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="be5ff-146">이 예에서는 기존 인덱스를 온라인으로 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-146">The example rebuilds an existing online</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     <span data-ttu-id="be5ff-147">다음 예에서는 `NewGroup` 절을 사용하여 온라인으로 클러스터형 인덱스를 삭제하고 결과 테이블을 `MOVE TO` 파일 그룹으로 옮깁니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-147">The following example deletes a clustered index online and moves the resulting table (heap) to the filegroup `NewGroup` by using the `MOVE TO` clause.</span></span> <span data-ttu-id="be5ff-148">테이블을 이동하기 전과 이동한 후에 파일 그룹에서의 인덱스 및 테이블 배치를 확인하기 위해 `sys.indexes`, `sys.tables`및 `sys.filegroups` 카탈로그 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="be5ff-148">The `sys.indexes`, `sys.tables`, and `sys.filegroups` catalog views are queried to verify the index and table placement in the filegroups before and after the move.</span></span>  
  
     [!code-sql[IndexDDL#DropIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/dropindex.sql#dropindex4)]  
  
 <span data-ttu-id="be5ff-149">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be5ff-149">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
