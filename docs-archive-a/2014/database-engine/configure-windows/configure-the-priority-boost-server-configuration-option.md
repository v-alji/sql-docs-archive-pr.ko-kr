---
title: priority boost 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- priority boost option
ms.assetid: 765f1e83-dd52-44fb-b0c8-1078f213607b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f42d7d2022e07dcac3039557295dc70e4500583d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649168"
---
# <a name="configure-the-priority-boost-server-configuration-option"></a><span data-ttu-id="32481-102">priority boost 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="32481-102">Configure the priority boost Server Configuration Option</span></span>
  <span data-ttu-id="32481-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 우선 순위 높임 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-103">This topic describes how to configure the **priority boost** configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="32481-104">**우선순위 높임** 옵션을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 같은 컴퓨터에 있는 다른 프로세스보다 더 높은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2008 또는 Windows 2008 R2 일정 우선순위에서 실행될 것인지 아닌지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32481-104">Use the **priority boost** option to specify whether [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should run at a higher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2008 or Windows 2008 R2 scheduling priority than other processes on the same computer.</span></span> <span data-ttu-id="32481-105">이 옵션을 1로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 Windows 2008 또는 Windows Server 2008 R2 스케줄러에서 우선 순위 13으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="32481-105">If you set this option to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs at a priority base of 13 in the Windows 2008 or Windows Server 2008 R2 scheduler.</span></span> <span data-ttu-id="32481-106">기본값인 0으로 설정하면 우선 순위 7이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="32481-106">The default is 0, which is a priority base of 7.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="32481-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="32481-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="32481-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="32481-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="32481-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="32481-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="32481-110">보안</span><span class="sxs-lookup"><span data-stu-id="32481-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="32481-111">**우선 순위 높임 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="32481-111">**To configure the priority boost option, using:**</span></span>  
  
     [<span data-ttu-id="32481-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="32481-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="32481-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="32481-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="32481-114">**후속 작업:**  [우선 순위 높임 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="32481-114">**Follow Up:**  [After you configure the priority boost option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="32481-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="32481-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="32481-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="32481-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="32481-117">우선 순위를 너무 높게 설정하면 운영 체제 및 네트워크 기능에 필요한 리소스를 모두 사용하게 되어 SQL Server 종료 또는 서버의 다른 운영 체제 태스크 사용 시에 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-117">Raising the priority too high may drain resources from essential operating system and network functions, resulting in problems shutting down SQL Server or using other operating system tasks on the server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="32481-118">보안</span><span class="sxs-lookup"><span data-stu-id="32481-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="32481-119">권한</span><span class="sxs-lookup"><span data-stu-id="32481-119">Permissions</span></span>  
 <span data-ttu-id="32481-120">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="32481-120">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="32481-121">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-121">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="32481-122">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32481-122">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="32481-123">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="32481-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-priority-boost-option"></a><span data-ttu-id="32481-124">우선 순위 높임 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="32481-124">To configure the priority boost option</span></span>  
  
1.  <span data-ttu-id="32481-125">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-125">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="32481-126">**프로세서** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-126">Click the **Processors** node.</span></span>  
  
3.  <span data-ttu-id="32481-127">**스레드**에서 **SQL Server 우선 순위 높임** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-127">Under **Threads**, select the **Boost SQL Server priority** check box.</span></span>  
  
4.  <span data-ttu-id="32481-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 중지하고 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-128">Stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="32481-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="32481-129">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-priority-boost-option"></a><span data-ttu-id="32481-130">우선 순위 높임 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="32481-130">To configure the priority boost option</span></span>  
  
1.  <span data-ttu-id="32481-131">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-131">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="32481-132">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-132">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="32481-133">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-133">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="32481-134">다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `priority boost` 옵션의 값을 `1`(으)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="32481-134">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `priority boost` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'priority boost', 1 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="32481-135">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-135">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-priority-boost-option"></a><a name="FollowUp"></a> <span data-ttu-id="32481-136">후속 작업: 우선 순위 높임 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="32481-136">Follow Up: After you configure the priority boost option</span></span>  
 <span data-ttu-id="32481-137">설정을 적용하려면 서버를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32481-137">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32481-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32481-138">See Also</span></span>  
 <span data-ttu-id="32481-139">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="32481-139">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="32481-140">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="32481-140">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="32481-141">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="32481-141">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
