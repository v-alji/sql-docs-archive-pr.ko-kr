---
title: scan for startup procs 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- scan for startup procs option
ms.assetid: 6bf9d252-e766-458d-9dcd-23d895f032a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fbf46fc7476e6e879991cfe3f649fd5617f3275e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649164"
---
# <a name="configure-the-scan-for-startup-procs-server-configuration-option"></a><span data-ttu-id="b3759-102">scan for startup procs 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="b3759-102">Configure the scan for startup procs Server Configuration Option</span></span>
  <span data-ttu-id="b3759-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 시작 프로시저 검색 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-103">This topic describes how to configure the **scan for startup procs** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b3759-104">**시작 프로시저 검색** 옵션을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시작 시 저장 프로시저의 자동 실행을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-104">Use the **scan for startup procs** option to scan for automatic execution of stored procedures at [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup time.</span></span> <span data-ttu-id="b3759-105">이 옵션을 1로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 서버에 정의된 자동 실행 저장 프로시저를 모두 검색하여 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-105">If this option is set to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] scans for and runs all automatically run stored procedures that are defined on the server.</span></span> <span data-ttu-id="b3759-106">**시작 프로시저 검색** 의 기본값은 0(검색 안 함)입니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-106">The default value for **scan for startup procs** is 0 (do not scan).</span></span>  
  
 <span data-ttu-id="b3759-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b3759-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b3759-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b3759-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b3759-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="b3759-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="b3759-110">보안</span><span class="sxs-lookup"><span data-stu-id="b3759-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b3759-111">**시작 프로시저 검색 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="b3759-111">**To configure the scan for startup procs option, using:**</span></span>  
  
     [<span data-ttu-id="b3759-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b3759-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b3759-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b3759-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="b3759-114">**후속 작업:**  [시작 프로시저 검색 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="b3759-114">**Follow Up:**  [After you configure the scan for startup procs option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b3759-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b3759-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b3759-116">권장 사항</span><span class="sxs-lookup"><span data-stu-id="b3759-116">Recommendations</span></span>  
  
-   <span data-ttu-id="b3759-117">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-117">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="b3759-118">이 옵션의 값은 **sp_configure**를 사용하여 설정할 수 있지만 자동 실행 저장 프로시저를 설정하거나 설정을 해제하는 데 사용되는 **sp_procoption**을 사용하면 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-118">The value for this option can be set by using **sp_configure**; however, it will be set automatically if you use **sp_procoption**, which is used to mark or unmark automatically run stored procedures.</span></span> <span data-ttu-id="b3759-119">**sp_procoption** 을 사용하여 첫 번째 저장 프로시저를 autoproc로 설정하면 이 옵션의 값이 자동으로 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-119">When **sp_procoption** is used to mark the first stored procedure as an autoproc, this option is set automatically to a value of 1.</span></span> <span data-ttu-id="b3759-120">**sp_procoption** 을 사용하여 마지막 저장 프로시저의 autoproc 설정을 해제하면 이 옵션의 값이 자동으로 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-120">When **sp_procoption** is used to unmark the last stored procedure as an autoproc, this option is automatically set to a value of 0.</span></span> <span data-ttu-id="b3759-121">**sp_procoption** 을 사용하여 autoprocs를 설정하거나 해제하고 autoprocs를 삭제하기 전에 항상 해제하면 이 옵션을 수동으로 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-121">If you use **sp_procoption** to mark and unmark autoprocs, and if you always unmark autoprocs before dropping them, there is no need to set this option manually.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b3759-122">보안</span><span class="sxs-lookup"><span data-stu-id="b3759-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b3759-123">권한</span><span class="sxs-lookup"><span data-stu-id="b3759-123">Permissions</span></span>  
 <span data-ttu-id="b3759-124">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="b3759-125">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="b3759-126">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b3759-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b3759-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a><span data-ttu-id="b3759-128">scan for startup procs 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="b3759-128">To configure the scan for startup procs option</span></span>  
  
1.  <span data-ttu-id="b3759-129">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="b3759-130">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-130">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="b3759-131">**기타**아래의 드롭다운 목록 상자에서 원하는 값을 선택하여 **시작 프로시저 검색** 옵션을 True 또는 False로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-131">Under **Miscellaneous**, change the **Scan for Startup Procs** option to True or False by selecting the value you want from the drop-down list box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b3759-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b3759-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a><span data-ttu-id="b3759-133">scan for startup procs 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="b3759-133">To configure the scan for startup procs option</span></span>  
  
1.  <span data-ttu-id="b3759-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b3759-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b3759-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b3759-137">다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `scan for startup procs` 옵션의 값을 `1`(으)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `scan for startup procs` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'scan for startup procs', 1 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-scan-for-startup-procs-option"></a><a name="FollowUp"></a> <span data-ttu-id="b3759-138">후속 작업: 시작 프로시저 검색 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="b3759-138">Follow Up: After you configure the scan for startup procs option</span></span>  
 <span data-ttu-id="b3759-139">설정을 적용하려면 서버를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3759-139">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3759-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3759-140">See Also</span></span>  
 <span data-ttu-id="b3759-141">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b3759-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="b3759-142">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b3759-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="b3759-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b3759-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="b3759-144">sp_procoption&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b3759-144">sp_procoption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)  
  
  
