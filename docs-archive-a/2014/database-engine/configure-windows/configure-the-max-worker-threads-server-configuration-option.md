---
title: max worker threads 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- worker threads [SQL Server]
- max worker threads option
ms.assetid: abeadfa4-a14d-469a-bacf-75812e48fac1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4881cefee350d34d93b539c56be6f43866d3ddfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652340"
---
# <a name="configure-the-max-worker-threads-server-configuration-option"></a><span data-ttu-id="3260b-102">max worker threads 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="3260b-102">Configure the max worker threads Server Configuration Option</span></span>
  <span data-ttu-id="3260b-103">이 항목에서는 **또는**을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]max worker threads[!INCLUDE[tsql](../../includes/tsql-md.md)] 서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-103">This topic describes how to configure the **max worker threads** server configuration option in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3260b-104">**max worker threads** 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에 사용할 수 있는 작업자 스레드 수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-104">The **max worker threads** option configures the number of worker threads that are available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3260b-105">는 운영 체제의 네이티브 스레드 서비스를 사용하여 하나 이상의 스레드가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 지원하는 각 네트워크를 동시에 지원하고 또 다른 스레드가 데이터베이스 검사점을 처리하고 스레드 풀이 모든 사용자를 처리하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-105">uses the native thread services of the operating systems so that one or more threads support each network that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports simultaneously, another thread handles database checkpoints, and a pool of threads handles all users.</span></span> <span data-ttu-id="3260b-106">**max worker threads** 의 기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-106">The default value for **max worker threads** is 0.</span></span> <span data-ttu-id="3260b-107">이 값을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작할 때 작업자 스레드 수가 자동으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-107">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to automatically configure the number of worker threads at startup.</span></span> <span data-ttu-id="3260b-108">기본 설정은 대부분의 시스템에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-108">The default setting is best for most systems.</span></span> <span data-ttu-id="3260b-109">그러나 시스템 구성에 따라 **max worker threads** 를 특정 값으로 설정하면 성능이 향상되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-109">However, depending on your system configuration, setting **max worker threads** to a specific value sometimes improves performance.</span></span>  
  
 <span data-ttu-id="3260b-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="3260b-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3260b-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="3260b-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3260b-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="3260b-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3260b-113">권장 사항</span><span class="sxs-lookup"><span data-stu-id="3260b-113">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="3260b-114">보안</span><span class="sxs-lookup"><span data-stu-id="3260b-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3260b-115">**최대 작업자 스레드 수 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="3260b-115">**To configure the max worker threads option, using:**</span></span>  
  
     [<span data-ttu-id="3260b-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3260b-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3260b-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3260b-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="3260b-118">**후속 작업:**  [최대 작업자 스레드 수 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="3260b-118">**Follow Up:**  [After you configure the max worker threads option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3260b-119">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3260b-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3260b-120">제한 사항</span><span class="sxs-lookup"><span data-stu-id="3260b-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3260b-121">실제 쿼리 요청 수가 **max worker threads**에 설정된 값보다 적으면 각 쿼리 요청마다 스레드 하나가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-121">When the actual number of query requests is less than the amount set in **max worker threads**, one thread handles each query request.</span></span> <span data-ttu-id="3260b-122">그러나 실제 쿼리 요청 수가 **max worker threads**에 설정 된 크기를 초과 하는 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 다음에 사용할 수 있는 작업자 스레드가 요청을 처리할 수 있도록 작업자 스레드를 풀링합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-122">However, if the actual number of query request exceeds the amount set in **max worker threads**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pools the worker threads so that the next available worker thread can handle the request.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="3260b-123">권장 사항</span><span class="sxs-lookup"><span data-stu-id="3260b-123">Recommendations</span></span>  
  
-   <span data-ttu-id="3260b-124">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-124">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="3260b-125">스레드 풀링을 사용하면 많은 클라이언트가 서버에 연결되어 있을 때 성능이 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-125">Thread pooling helps optimize performance when large numbers of clients are connected to the server.</span></span> <span data-ttu-id="3260b-126">보통 각 쿼리 요청마다 별도의 운영 체제 스레드가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-126">Usually, a separate operating system thread is created for each query request.</span></span> <span data-ttu-id="3260b-127">그러나 서버에 대한 연결 수가 수백 개인 경우 쿼리 요청별로 스레드를 하나씩 사용하면 시스템 리소스를 상당히 많이 소비하게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-127">However, with hundreds of connections to the server, using one thread per query request can consume large amounts of system resources.</span></span> <span data-ttu-id="3260b-128">**max worker threads** 옵션을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 작업자 스레드 풀을 만들어 많은 쿼리 요청을 처리할 수 있으므로 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-128">The **max worker threads** option enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create a pool of worker threads to service a larger number of query requests, which improves performance.</span></span>  
  
-   <span data-ttu-id="3260b-129">다음 표에서는 다양한 CPU 조합과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에 대해 자동으로 구성되는 최대 작업자 스레드 수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-129">The following table shows the automatically configured number of max worker threads for various combinations of CPUs and versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    |<span data-ttu-id="3260b-130">CPU 수</span><span class="sxs-lookup"><span data-stu-id="3260b-130">Number of CPUs</span></span>|<span data-ttu-id="3260b-131">32비트 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="3260b-131">32-bit computer</span></span>|<span data-ttu-id="3260b-132">64비트 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="3260b-132">64-bit computer</span></span>|  
    |--------------------|----------------------|----------------------|  
    |<span data-ttu-id="3260b-133">\<4개 이하 프로세서</span><span class="sxs-lookup"><span data-stu-id="3260b-133">\<= 4 processors</span></span>|<span data-ttu-id="3260b-134">256</span><span class="sxs-lookup"><span data-stu-id="3260b-134">256</span></span>|<span data-ttu-id="3260b-135">512</span><span class="sxs-lookup"><span data-stu-id="3260b-135">512</span></span>|  
    |<span data-ttu-id="3260b-136">8개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="3260b-136">8 processors</span></span>|<span data-ttu-id="3260b-137">288</span><span class="sxs-lookup"><span data-stu-id="3260b-137">288</span></span>|<span data-ttu-id="3260b-138">576</span><span class="sxs-lookup"><span data-stu-id="3260b-138">576</span></span>|  
    |<span data-ttu-id="3260b-139">16개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="3260b-139">16 processors</span></span>|<span data-ttu-id="3260b-140">352</span><span class="sxs-lookup"><span data-stu-id="3260b-140">352</span></span>|<span data-ttu-id="3260b-141">704</span><span class="sxs-lookup"><span data-stu-id="3260b-141">704</span></span>|  
    |<span data-ttu-id="3260b-142">32개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="3260b-142">32 processors</span></span>|<span data-ttu-id="3260b-143">480</span><span class="sxs-lookup"><span data-stu-id="3260b-143">480</span></span>|<span data-ttu-id="3260b-144">960</span><span class="sxs-lookup"><span data-stu-id="3260b-144">960</span></span>|  
    |<span data-ttu-id="3260b-145">64개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="3260b-145">64 processors</span></span>|<span data-ttu-id="3260b-146">736</span><span class="sxs-lookup"><span data-stu-id="3260b-146">736</span></span>|<span data-ttu-id="3260b-147">1472</span><span class="sxs-lookup"><span data-stu-id="3260b-147">1472</span></span>|  
    |<span data-ttu-id="3260b-148">128개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="3260b-148">128 processors</span></span>|<span data-ttu-id="3260b-149">4224</span><span class="sxs-lookup"><span data-stu-id="3260b-149">4224</span></span>|<span data-ttu-id="3260b-150">4480</span><span class="sxs-lookup"><span data-stu-id="3260b-150">4480</span></span>|  
    |<span data-ttu-id="3260b-151">256개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="3260b-151">256 processors</span></span>|<span data-ttu-id="3260b-152">8320</span><span class="sxs-lookup"><span data-stu-id="3260b-152">8320</span></span>|<span data-ttu-id="3260b-153">8576</span><span class="sxs-lookup"><span data-stu-id="3260b-153">8576</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="3260b-154">64개가 넘는 CPU 사용에 대한 권장 사항은 [64개를 초과하는 CPU가 있는 컴퓨터에서 SQL Server를 실행하기 위한 최선의 방법](https://technet.microsoft.com/library/ee210547\(SQL.105\).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3260b-154">For recommendations on using more than 64 CPUs, refer to [Best Practices for Running SQL Server on Computers That Have More Than 64 CPUs](https://technet.microsoft.com/library/ee210547\(SQL.105\).aspx).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="3260b-155">32비트 컴퓨터에서 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 최대 작업자 스레드 수는 1024로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-155">We recommend 1024 as the maximum number of worker threads for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on a 32-bit computer.</span></span>  
  
-   <span data-ttu-id="3260b-156">장기 실행 쿼리의 모든 작업자 스레드가 활성 상태이면 작업자 스레드가 완료되어 사용 가능 상태가 되기 전에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 응답하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-156">When all worker threads are active with long running queries, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might appear unresponsive until a worker thread completes and becomes available.</span></span> <span data-ttu-id="3260b-157">이는 오류는 아니지만 바람직한 상태는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-157">Although this is not a defect, it can sometimes be undesirable.</span></span> <span data-ttu-id="3260b-158">프로세스가 응답할 수 없고 새 쿼리를 처리할 수 없으면 DAC(관리자 전용 연결)를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결한 다음 해당 프로세스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-158">If a process appears to be unresponsive and no new queries can be processed, then connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the dedicated administrator connection (DAC), and kill the process.</span></span> <span data-ttu-id="3260b-159">이를 방지하려면 max worker threads 수를 증가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-159">To prevent this, increase the number of max worker threads.</span></span>  
  
 <span data-ttu-id="3260b-160">**최대 작업자 스레드 수** 서버 구성 옵션은 가용성 그룹, Service Broker, 잠금 관리자 등의 모든 시스템 태스크에 필요한 스레드 수를 고려하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-160">The **max worker threads** server configuration option does not take into account threads that are required for all the system tasks such as Availibility Groups, Service Broker, Lock Manager, and others.</span></span>  <span data-ttu-id="3260b-161">다음 쿼리는 구성된 스레드 수를 초과할 경우 추가 스레드를 생성한 시스템 태스크에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-161">If the number of threads configured are being exceeded, the following query will provide information about the system tasks that have spawned the additional threads.</span></span>  
  
```  
SELECT  
s.session_id,  
r.command,  
r.status,  
r.wait_type,  
r.scheduler_id,  
w.worker_address,  
w.is_preemptive,  
w.state,  
t.task_state,  
t.session_id,  
t.exec_context_id,  
t.request_id  
FROM sys.dm_exec_sessions AS s  
INNERJOIN sys.dm_exec_requests AS r  
    ON s.session_id = r.session_id  
INNER JOIN sys.dm_os_tasks AS t  
    ON r.task_address = t.task_address  
INNER JOIN sys.dm_os_workers AS w  
    ON t.worker_address = w.worker_address  
WHERE s.is_user_process = 0;  
  
```  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3260b-162">보안</span><span class="sxs-lookup"><span data-stu-id="3260b-162">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3260b-163">권한</span><span class="sxs-lookup"><span data-stu-id="3260b-163">Permissions</span></span>  
 <span data-ttu-id="3260b-164">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-164">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="3260b-165">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-165">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="3260b-166">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-166">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3260b-167">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3260b-167">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-worker-threads-option"></a><span data-ttu-id="3260b-168">최대 작업자 스레드 수 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="3260b-168">To configure the max worker threads option</span></span>  
  
1.  <span data-ttu-id="3260b-169">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-169">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="3260b-170">**프로세서** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-170">Click the **Processors** node.</span></span>  
  
3.  <span data-ttu-id="3260b-171">**최대 작업자 스레드** 상자에 128에서 32767 까지의 값을 입력 하거나 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-171">In the **Max worker threads** box, type or select a value from 128 through 32767.</span></span>  
  
     <span data-ttu-id="3260b-172">**max worker threads** 옵션을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에 사용할 수 있는 작업자 스레드 수를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-172">Use the **max worker threads** option to configure the number of worker threads available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes.</span></span> <span data-ttu-id="3260b-173">대부분의 시스템에는 **max worker threads** 의 기본 설정을 사용하는 것이 최상의 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-173">The default setting for **max worker threads** is best for most systems.</span></span> <span data-ttu-id="3260b-174">그러나 시스템 구성에 따라 **max worker threads** 를 더 작은 값으로 설정하면 성능이 향상되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-174">However, depending on your system configuration, setting **max worker threads** to a smaller value sometimes improves performance.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3260b-175">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="3260b-175">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-worker-threads-option"></a><span data-ttu-id="3260b-176">최대 작업자 스레드 수 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="3260b-176">To configure the max worker threads option</span></span>  
  
1.  <span data-ttu-id="3260b-177">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-177">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3260b-178">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-178">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3260b-179">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-179">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="3260b-180">이 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `max worker threads` 옵션을 `900`으로 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-180">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max worker threads` option to `900`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'max worker threads', 900 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="3260b-181">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-181">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-worker-threads-option"></a><a name="FollowUp"></a> <span data-ttu-id="3260b-182">후속 작업: 최대 작업자 스레드 수 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="3260b-182">Follow Up: After you configure the max worker threads option</span></span>  
 <span data-ttu-id="3260b-183">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 다시 시작할 필요 없이 변경 사항이 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3260b-183">The change will take effect immediately without requiring the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3260b-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3260b-184">See Also</span></span>  
 <span data-ttu-id="3260b-185">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3260b-185">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="3260b-186">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3260b-186">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="3260b-187">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3260b-187">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="3260b-188">데이터베이스 관리자를 위한 진단 연결</span><span class="sxs-lookup"><span data-stu-id="3260b-188">Diagnostic Connection for Database Administrators</span></span>](diagnostic-connection-for-database-administrators.md)  
  
  
