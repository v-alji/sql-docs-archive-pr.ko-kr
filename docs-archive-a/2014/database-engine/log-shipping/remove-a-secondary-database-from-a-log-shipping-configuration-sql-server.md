---
title: 로그 전달 구성에서 보조 데이터베이스 제거(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- deleting secondary databases
- secondary databases [SQL Server], in log shipping
- removing secondary databases
- secondary data files [SQL Server], removing
- log shipping [SQL Server], secondary databases
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 119f2762d41d0787b6b3279507e9671e89fddfca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652313"
---
# <a name="remove-a-secondary-database-from-a-log-shipping-configuration-sql-server"></a><span data-ttu-id="af358-102">로그 전달 구성에서 보조 데이터베이스 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="af358-102">Remove a Secondary Database from a Log Shipping Configuration (SQL Server)</span></span>
  <span data-ttu-id="af358-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 로그 전달 보조 데이터베이스를 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-103">This topic describes how to remove a log shipping secondary database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="af358-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="af358-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="af358-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="af358-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="af358-106">보안</span><span class="sxs-lookup"><span data-stu-id="af358-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="af358-107">**로그 전달 보조 데이터베이스를 제거하려면:**</span><span class="sxs-lookup"><span data-stu-id="af358-107">**To remove a log shipping secondary database, using:**</span></span>  
  
     [<span data-ttu-id="af358-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af358-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="af358-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af358-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="af358-110">관련 작업</span><span class="sxs-lookup"><span data-stu-id="af358-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="af358-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="af358-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="af358-112">보안</span><span class="sxs-lookup"><span data-stu-id="af358-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="af358-113">권한</span><span class="sxs-lookup"><span data-stu-id="af358-113">Permissions</span></span>  
 <span data-ttu-id="af358-114">로그 전달 저장 프로시저를 사용하려면 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="af358-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="af358-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-a-log-shipping-secondary-database"></a><span data-ttu-id="af358-116">로그 전달 보조 데이터베이스를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="af358-116">To remove a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="af358-117">현재 로그 전달 주 서버인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스에 연결하고 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-117">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is currently the log shipping primary server and expand that instance.</span></span>  
  
2.  <span data-ttu-id="af358-118">**데이터베이스**를 확장하고 로그 전달 주 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-118">Expand **Databases**, right-click the log shipping primary database, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="af358-119">**페이지 선택**에서 **트랜잭션 로그 전달**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-119">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
4.  <span data-ttu-id="af358-120">**보조 서버 인스턴스 및 데이터베이스**에서 제거할 데이터베이스를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-120">Under **Secondary server instances and databases**, click the database you want to remove.</span></span>  
  
5.  <span data-ttu-id="af358-121">**제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-121">Click **Remove**.</span></span>  
  
6.  <span data-ttu-id="af358-122">**확인** 을 클릭하여 구성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-122">Click **OK** to update the configuration.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="af358-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="af358-123">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-a-secondary-database"></a><span data-ttu-id="af358-124">보조 데이터베이스를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="af358-124">To Remove a Secondary Database</span></span>  
  
1.  <span data-ttu-id="af358-125">주 서버에서 [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) 를 실행하여 주 서버에서 보조 데이터베이스에 대한 정보를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-125">On the primary server, execute [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) to delete the information about the secondary database from the primary server.</span></span>  
  
2.  <span data-ttu-id="af358-126">보조 서버에서 [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) 를 실행하여 보조 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-126">On the secondary server, execute [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) to delete the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="af358-127">보조 ID가 같은 보조 데이터베이스가 없는 경우 **sp_delete_log_shipping_secondary_database** 에서 **sp_delete_log_shipping_secondary_primary** 가 호출되어 보조 ID에 대한 항목과 복사 및 복원 작업이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="af358-127">If there are no other secondary databases with the same secondary ID, **sp_delete_log_shipping_secondary_primary** is invoked from **sp_delete_log_shipping_secondary_database** and deletes the entry for the secondary ID and the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="af358-128">보조 서버에서 복사 및 복원 작업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="af358-128">On the secondary server, disable the copy and restore jobs.</span></span> <span data-ttu-id="af358-129">자세한 내용은 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af358-129">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="af358-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="af358-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="af358-131">SQL Server 2014 &#40;Transact-sql&#41;로그 전달 업그레이드</span><span class="sxs-lookup"><span data-stu-id="af358-131">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="af358-132">로그 전달 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af358-132">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="af358-133">로그 전달 구성에 보조 데이터베이스 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af358-133">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="af358-134">로그 전달 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af358-134">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="af358-135">로그 전달 보고서 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="af358-135">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="af358-136">로그 전달 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af358-136">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="af358-137">로그 전달 보조 데이터베이스로 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af358-137">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="af358-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af358-138">See Also</span></span>  
 <span data-ttu-id="af358-139">[로그 전달 정보&#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af358-139">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="af358-140">로그 전달 테이블 및 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="af358-140">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
