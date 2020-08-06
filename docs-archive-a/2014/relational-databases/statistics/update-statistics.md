---
title: 통계 업데이트 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- updating statistics
- statistics [SQL Server], updating
ms.assetid: 4b97c0b4-03ff-4cfb-9c3f-3b33290b7a2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 28491dda23c2ba9402e91dc051249f5bdcdf28d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659873"
---
# <a name="update-statistics"></a><span data-ttu-id="13aaa-102">통계 업데이트</span><span class="sxs-lookup"><span data-stu-id="13aaa-102">Update Statistics</span></span>
  <span data-ttu-id="13aaa-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 테이블 또는 인덱싱된 뷰에 대한 쿼리 최적화 통계를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-103">You can update query optimization statistics on a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="13aaa-104">기본적으로 쿼리 최적화 프로그램은 필요할 때 통계를 업데이트하여 쿼리 계획을 향상시킵니다. 하지만 경우에 따라 사용자가 UPDATE STATISTICS 또는 `sp_updatestats` 저장 프로시저를 사용하여 기본 업데이트 주기보다 자주 통계를 업데이트하여 쿼리 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-104">By default, the query optimizer already updates statistics as necessary to improve the query plan; in some cases you can improve query performance by using UPDATE STATISTICS or the stored procedure `sp_updatestats` to update statistics more frequently than the default updates.</span></span>  
  
 <span data-ttu-id="13aaa-105">통계를 업데이트하면 쿼리가 최신 통계로 컴파일되지만</span><span class="sxs-lookup"><span data-stu-id="13aaa-105">Updating statistics ensures that queries compile with up-to-date statistics.</span></span> <span data-ttu-id="13aaa-106">쿼리도 다시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-106">However, updating statistics causes queries to recompile.</span></span> <span data-ttu-id="13aaa-107">쿼리 계획 향상과 쿼리 재컴파일 소요 시간 간의 성능 균형을 유지해야 하므로 통계를 너무 자주 업데이트하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-107">We recommend not updating statistics too frequently because there is a performance tradeoff between improving query plans and the time it takes to recompile queries.</span></span> <span data-ttu-id="13aaa-108">구체적인 성능 균형 유지의 정도는 애플리케이션에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-108">The specific tradeoffs depend on your application.</span></span> <span data-ttu-id="13aaa-109">UPDATE STATISTIC은 통계를 작성하기 위해 tempdb를 사용하여 행 샘플을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-109">UPDATE STATISTICS can use tempdb to sort the sample of rows for building statistics.</span></span>  
  
 <span data-ttu-id="13aaa-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="13aaa-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="13aaa-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="13aaa-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="13aaa-112">보안</span><span class="sxs-lookup"><span data-stu-id="13aaa-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="13aaa-113">**다음을 사용하여 통계 개체를 업데이트하려면**</span><span class="sxs-lookup"><span data-stu-id="13aaa-113">**To update a statistics object, using:**</span></span>  
  
     [<span data-ttu-id="13aaa-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="13aaa-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="13aaa-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="13aaa-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="13aaa-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="13aaa-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="13aaa-117">보안</span><span class="sxs-lookup"><span data-stu-id="13aaa-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="13aaa-118">권한</span><span class="sxs-lookup"><span data-stu-id="13aaa-118">Permissions</span></span>  
 <span data-ttu-id="13aaa-119">UPDATE STATISTICS를 사용하거나 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 통해 변경 작업을 하려면 테이블 또는 뷰에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-119">If using UPDATE STATISTICS or making changes through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], requires ALTER permission on the table or view.</span></span> <span data-ttu-id="13aaa-120">`sp_updatestats`를 사용할 경우 **sysadmin** 고정 서버 역할에 멤버 자격이 있거나 데이터베이스(**dbo**)의 소유권이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-120">If using `sp_updatestats`, requires membership in the **sysadmin** fixed server role, or ownership of the database (**dbo**).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="13aaa-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="13aaa-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-update-a-statistics-object"></a><span data-ttu-id="13aaa-122">통계 개체를 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="13aaa-122">To update a statistics object</span></span>  
  
1.  <span data-ttu-id="13aaa-123">**개체 탐색기**에서 더하기 기호를 클릭하여 통계를 업데이트할 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-123">In **Object Explorer**, click the plus sign to expand the database in which you want to update the statistic.</span></span>  
  
2.  <span data-ttu-id="13aaa-124">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-124">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="13aaa-125">더하기 기호를 클릭하여 통계를 업데이트할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-125">Click the plus sign to expand the table in which you want to update the statistic.</span></span>  
  
4.  <span data-ttu-id="13aaa-126">더하기 기호를 클릭하여 **통계** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-126">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="13aaa-127">업데이트하려는 통계 개체를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-127">Right-click the statistics object you wish to update and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="13aaa-128">**통계 속성-**_statistics_name_ 대화 상자에서 **이 열에 대 한 통계 업데이트** 확인란을 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-128">In the **Statistics Properties -**_statistics_name_ dialog box, select the **Update statistics for these columns** check box and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="13aaa-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="13aaa-129">Using Transact-SQL</span></span>  
  
#### <a name="to-update-a-specific-statistics-object"></a><span data-ttu-id="13aaa-130">특정 통계 개체를 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="13aaa-130">To update a specific statistics object</span></span>  
  
1.  <span data-ttu-id="13aaa-131">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="13aaa-132">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="13aaa-133">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example updates the statistics for the AK_SalesOrderDetail_rowguid index of the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;   
    GO  
    ```  
  
#### <a name="to-update-all-statistics-in-a-table"></a><span data-ttu-id="13aaa-134">테이블의 모든 통계를 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="13aaa-134">To update all statistics in a table</span></span>  
  
1.  <span data-ttu-id="13aaa-135">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="13aaa-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="13aaa-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all indexes on the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail;   
    GO  
    ```  
  
 <span data-ttu-id="13aaa-138">자세한 내용은 [UPDATE STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)로 만든 데이터베이스 유지 관리 계획을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-138">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
#### <a name="to-update-all-statistics-in-a-database"></a><span data-ttu-id="13aaa-139">데이터베이스의 모든 통계를 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="13aaa-139">To update all statistics in a database</span></span>  
  
1.  <span data-ttu-id="13aaa-140">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="13aaa-141">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="13aaa-142">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13aaa-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all tables in the database.   
    EXEC sp_updatestats;  
    ```  
  
 <span data-ttu-id="13aaa-143">자세한 내용은 [sp_updatestats&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13aaa-143">For more information, see [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span>  
  
  
