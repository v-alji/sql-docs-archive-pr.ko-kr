---
title: 원격 서버 연결 옵션 보기 또는 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], connection options
- servers [SQL Server], remote
- connections [SQL Server], remote servers
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 73fe5e484d62cde025d1a560937e8cbcf5ec361d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729787"
---
# <a name="view-or-configure-remote-server-connection-options-sql-server"></a><span data-ttu-id="c946e-102">원격 서버 연결 옵션 보기 또는 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c946e-102">View or Configure Remote Server Connection Options (SQL Server)</span></span>
  <span data-ttu-id="c946e-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 서버 수준에서 원격 서버 연결 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-103">This topic describes how to view or configure remote server connection options at the server level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c946e-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c946e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c946e-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c946e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c946e-106">보안</span><span class="sxs-lookup"><span data-stu-id="c946e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c946e-107">**원격 서버 연결 옵션을 보거나 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="c946e-107">**To view or configure remote server connection options, using:**</span></span>  
  
     [<span data-ttu-id="c946e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c946e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c946e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c946e-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="c946e-110">**후속 작업:**  [원격 서버 연결 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="c946e-110">**Follow Up:**  [After you configure remote server connection options](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c946e-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c946e-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c946e-112">보안</span><span class="sxs-lookup"><span data-stu-id="c946e-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c946e-113">권한</span><span class="sxs-lookup"><span data-stu-id="c946e-113">Permissions</span></span>  
 <span data-ttu-id="c946e-114">**sp_serveroption** 을 실행하려면 서버에 대한 ALTER ANY LINKED SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-114">Executing **sp_serveroption** requires ALTER ANY LINKED SERVER permission on the server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c946e-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c946e-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-configure-remote-server-connection-options"></a><span data-ttu-id="c946e-116">원격 서버 연결 옵션을 보거나 구성하려면</span><span class="sxs-lookup"><span data-stu-id="c946e-116">To view or configure remote server connection options</span></span>  
  
1.  <span data-ttu-id="c946e-117">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-117">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c946e-118">**SQL Server 속성 - \<***server_name***>** 대화 상자에서 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-118">In the **SQL Server Properties - \<***server_name***>** dialog box, click **Connections**.</span></span>  
  
3.  <span data-ttu-id="c946e-119">**연결** 페이지에서 **원격 서버 연결** 설정을 확인한 다음 필요한 경우 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-119">On the **Connections** page, review the **Remote server connections** settings, and modify them if necessary.</span></span>  
  
4.  <span data-ttu-id="c946e-120">원격 서버 쌍의 다른 서버에 대해 1단계에서 3단계까지 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-120">Repeat steps 1 through 3 on the other server of the remote server pair.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c946e-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c946e-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-remote-server-connection-options"></a><span data-ttu-id="c946e-122">원격 서버 연결 옵션을 보려면</span><span class="sxs-lookup"><span data-stu-id="c946e-122">To view remote server connection options</span></span>  
  
1.  <span data-ttu-id="c946e-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c946e-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c946e-125">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-125">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c946e-126">이 예제에서는 [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) 를 사용하여 모든 원격 서버에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-126">This example uses [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) to return information about all remote servers.</span></span>  
  
```sql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### <a name="to-configure-remote-server-connection-options"></a><span data-ttu-id="c946e-127">원격 서버 연결 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="c946e-127">To configure remote server connection options</span></span>  
  
1.  <span data-ttu-id="c946e-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c946e-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c946e-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c946e-131">이 예제에서는 [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) 을 사용하여 원격 서버를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-131">This example shows how to use [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) to configure a remote server.</span></span> <span data-ttu-id="c946e-132">다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 다른 인스턴스인 `SEATTLE3`에 해당하는 원격 서버를 구성하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 로컬 인스턴스와 데이터 정렬이 호환되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-132">The example configures a remote server corresponding to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, to be collation compatible with the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="follow-up-after-you-configure-remote-server-connection-options"></a><a name="FollowUp"></a> <span data-ttu-id="c946e-133">후속 작업: 원격 서버 연결 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="c946e-133">Follow Up: After you configure remote server connection options</span></span>  
 <span data-ttu-id="c946e-134">설정을 적용하려면 원격 서버를 중지한 후 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c946e-134">The remote server must be stopped and restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c946e-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c946e-135">See Also</span></span>  
 <span data-ttu-id="c946e-136">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c946e-136">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="c946e-137">[원격 서버](remote-servers.md) </span><span class="sxs-lookup"><span data-stu-id="c946e-137">[Remote Servers](remote-servers.md) </span></span>  
 <span data-ttu-id="c946e-138">[연결된 서버&#40;데이터베이스 엔진&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="c946e-138">[Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="c946e-139">[sp_linkedservers&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c946e-139">[sp_linkedservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql) </span></span>  
 <span data-ttu-id="c946e-140">[sp_helpserver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c946e-140">[sp_helpserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) </span></span>  
 [<span data-ttu-id="c946e-141">sp_serveroption&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c946e-141">sp_serveroption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
