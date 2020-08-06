---
title: locks 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- locks option [SQL Server]
ms.assetid: b0cf0f86-7652-4574-a9fb-908e10d03973
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e45f4cc539be585966eb0beb30d4938b504c3419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741248"
---
# <a name="configure-the-locks-server-configuration-option"></a><span data-ttu-id="90b21-102">locks 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="90b21-102">Configure the locks Server Configuration Option</span></span>
  <span data-ttu-id="90b21-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] locks [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-103">This topic describes how to configure the **locks** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="90b21-104">**locks** 옵션은 사용 가능한 최대 잠금 수를 설정하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 에서 잠금에 사용하는 메모리 용량을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-104">The **locks** option sets the maximum number of available locks, thereby limiting the amount of memory the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses for them.</span></span> <span data-ttu-id="90b21-105">기본 설정은 0이며 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 시스템 요구 사항의 변화를 기준으로 동적으로 잠금 구조를 할당하거나 할당 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-105">The default setting is 0, which allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to allocate and deallocate lock structures dynamically, based on changing system requirements.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="90b21-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="90b21-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="90b21-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="90b21-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="90b21-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="90b21-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="90b21-109">보안</span><span class="sxs-lookup"><span data-stu-id="90b21-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="90b21-110">**잠금 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="90b21-110">**To configure the locks option, using:**</span></span>  
  
     [<span data-ttu-id="90b21-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="90b21-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="90b21-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="90b21-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="90b21-113">**후속 작업:**  [잠금 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="90b21-113">**Follow Up:**  [After you configure the locks option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="90b21-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="90b21-114">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="90b21-115">권장 사항</span><span class="sxs-lookup"><span data-stu-id="90b21-115">Recommendations</span></span>  
  
-   <span data-ttu-id="90b21-116">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-116">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="90b21-117">**locks** 를 0으로 설정한 상태로 서버를 시작하면 잠금 관리자가 초기 2,500개의 잠금 구조 풀에 사용할 충분한 메모리를 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 으로부터 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-117">When the server is started with **locks** set to 0, the lock manager acquires sufficient memory from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for an initial pool of 2,500 lock structures.</span></span> <span data-ttu-id="90b21-118">잠금 풀을 모두 사용하면 풀에 사용할 추가 메모리를 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-118">As the lock pool is exhausted, additional memory is acquired for the pool.</span></span>  
  
     <span data-ttu-id="90b21-119">일반적으로 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 메모리 풀에서 사용 가능한 잠금 풀에 메모리가 더 많이 필요하고 컴퓨터 메모리를 더 사용할 수 있는 경우 **최대 서버 메모리** 임계값에 도달하지 않았으면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 잠금 요청을 만족시킬 수 있도록 동적으로 메모리가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-119">Generally, if more memory is required for the lock pool than is available in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] memory pool, and more computer memory is available (the **max server memory** threshold has not been reached), the [!INCLUDE[ssDE](../../includes/ssde-md.md)] allocates memory dynamically to satisfy the request for locks.</span></span> <span data-ttu-id="90b21-120">그러나 이 메모리 할당으로 인해 운영 체제 수준에서 페이징이 발생하는 경우, 예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 같은 컴퓨터에서 실행되는 다른 애플리케이션이 이 메모리를 사용하면 잠금 공간이 추가로 할당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-120">However, if allocating that memory would cause paging at the operating system level (for example, if another application is running on the same computer as an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and using that memory), more lock space is not allocated.</span></span> <span data-ttu-id="90b21-121">동적 잠금 풀은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 할당된 메모리의 60% 이상은 확보하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-121">The dynamic lock pool does not acquire more than 60 percent of the memory allocated to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="90b21-122">잠금 풀이 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 의해 확보된 메모리의 60%에 도달하거나 컴퓨터에 더 이상 사용 가능한 메모리가 없는 경우 잠금에 대한 요청을 추가하면 오류가 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-122">After the lock pool has reached 60 percent of the memory acquired by an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or no more memory is available on the computer, further requests for locks generate an error.</span></span>  
  
     <span data-ttu-id="90b21-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 잠금을 동적으로 사용하는 것이 권장 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-123">Allowing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use locks dynamically is the recommended configuration.</span></span> <span data-ttu-id="90b21-124">그러나 **locks** 를 설정하여 잠금 리소스를 동적으로 할당하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기능을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-124">However, you can set **locks** and override the ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to allocate lock resources dynamically.</span></span> <span data-ttu-id="90b21-125">**locks** 가 0 이외의 값으로 설정되면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 **locks**에 지정된 값보다 많은 잠금을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-125">When **locks** is set to a value other than 0, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] cannot allocate more locks than the value specified in **locks**.</span></span> <span data-ttu-id="90b21-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 사용할 수 있는 잠금 수가 초과되었다는 메시지가 표시되면 이 값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-126">Increase this value if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] displays a message that you have exceeded the number of available locks.</span></span> <span data-ttu-id="90b21-127">각 잠금은 잠금 하나당 96바이트의 메모리를 사용하므로 이 값을 늘리면 서버에서 전용으로 사용하는 메모리 양을 늘려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-127">Because each lock consumes memory (96 bytes per lock), increasing this value can require increasing the amount of memory dedicated to the server.</span></span>  
  
-   <span data-ttu-id="90b21-128">또한 **locks** 옵션은 잠금 에스컬레이션이 수행될 때 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-128">The **locks** option also affects when lock escalation occurs.</span></span> <span data-ttu-id="90b21-129">**locks** 가 0으로 설정된 경우 현재 잠금 구조에서 사용되는 메모리가 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 메모리 풀의 40%에 도달하면 잠금 에스컬레이션이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-129">When **locks** is set to 0, lock escalation occurs when the memory used by the current lock structures reaches 40 percent of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] memory pool.</span></span> <span data-ttu-id="90b21-130">**locks** 가 0으로 설정되지 않은 경우 잠금 수가 **locks**에 지정된 값의 40%에 도달하면 잠금 에스컬레이션이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-130">When **locks** is not set to 0, lock escalation occurs when the number of locks reaches 40 percent of the value specified for **locks**.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="90b21-131">보안</span><span class="sxs-lookup"><span data-stu-id="90b21-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="90b21-132">권한</span><span class="sxs-lookup"><span data-stu-id="90b21-132">Permissions</span></span>  
 <span data-ttu-id="90b21-133">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="90b21-134">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="90b21-135">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="90b21-136">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="90b21-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-locks-option"></a><span data-ttu-id="90b21-137">잠금 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="90b21-137">To configure the locks option</span></span>  
  
1.  <span data-ttu-id="90b21-138">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="90b21-139">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-139">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="90b21-140">**병렬 처리**아래에 원하는 **잠금** 옵션 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-140">Under **Parallelism**, type the desired value for the **locks** option.</span></span>  
  
     <span data-ttu-id="90b21-141">**잠금** 옵션을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 잠금에 사용하는 메모리 양을 제한하는 최대 사용 가능 잠금 수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-141">Use the **locks** option to set the maximum number of available locks, thereby limiting the amount of memory [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses for them.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="90b21-142">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="90b21-142">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-locks-option"></a><span data-ttu-id="90b21-143">잠금 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="90b21-143">To configure the locks option</span></span>  
  
1.  <span data-ttu-id="90b21-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-144">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="90b21-145">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-145">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="90b21-146">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-146">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="90b21-147">이 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 통해 `locks` 옵션 값을 `20000`으로 설정하여 모든 사용자가 사용할 수 있는 잠금 수를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-147">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `locks` option to set the number of locks available for all users to `20000`.</span></span>  
  
```sql  
Use AdventureWorks2012 ;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'locks', 20000;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="90b21-148">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-148">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-locks-option"></a><a name="FollowUp"></a> <span data-ttu-id="90b21-149">후속 작업: 잠금 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="90b21-149">Follow Up: After you configure the locks option</span></span>  
 <span data-ttu-id="90b21-150">설정을 적용하려면 서버를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b21-150">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b21-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="90b21-151">See Also</span></span>  
 <span data-ttu-id="90b21-152">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90b21-152">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="90b21-153">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="90b21-153">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="90b21-154">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90b21-154">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
