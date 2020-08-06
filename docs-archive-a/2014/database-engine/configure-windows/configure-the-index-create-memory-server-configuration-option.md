---
title: index create memory 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- index create memory option
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6cd0aeb93d3fb68089338335068fdaaae19919fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732019"
---
# <a name="configure-the-index-create-memory-server-configuration-option"></a><span data-ttu-id="e8b79-102">index create memory 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="e8b79-102">Configure the index create memory Server Configuration Option</span></span>
  <span data-ttu-id="e8b79-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 인덱스 생성 메모리 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-103">This topic describes how to configure the **index create memory** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e8b79-104">**인덱스 생성 메모리** 옵션은 인덱스를 만들기 위해 처음으로 할당되는 최대 메모리 양을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-104">The **index create memory** option controls the maximum amount of memory initially allocated for creating indexes.</span></span> <span data-ttu-id="e8b79-105">이 옵션의 기본값은 0(자체 구성)입니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-105">The default value for this option is 0 (self-configuring).</span></span> <span data-ttu-id="e8b79-106">나중에 인덱스 생성에 메모리가 더 필요하고 해당 메모리를 사용할 수 있는 경우 서버가 이 옵션의 설정 값을 초과하여 메모리를 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-106">If more memory is later needed for index creation and the memory is available, the server will use it; thereby, exceeding the setting of this option.</span></span> <span data-ttu-id="e8b79-107">추가 메모리를 사용할 수 없는 경우 이미 할당된 메모리를 계속 사용하여 인덱스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-107">If additional memory is not available, the index creation will continue using the memory already allocated.</span></span>  
  
 <span data-ttu-id="e8b79-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="e8b79-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e8b79-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="e8b79-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e8b79-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e8b79-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e8b79-111">권장 사항</span><span class="sxs-lookup"><span data-stu-id="e8b79-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="e8b79-112">보안</span><span class="sxs-lookup"><span data-stu-id="e8b79-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e8b79-113">**인덱스 생성 메모리 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="e8b79-113">**To configure the index create memory option, using:**</span></span>  
  
     [<span data-ttu-id="e8b79-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e8b79-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e8b79-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e8b79-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="e8b79-116">**후속 작업:**  [인덱스 생성 메모리 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="e8b79-116">**Follow Up:**  [After you configure the index create memory option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e8b79-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e8b79-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e8b79-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e8b79-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e8b79-119">**쿼리당 최소 메모리** 옵션의 설정이 **인덱스 생성 메모리** 옵션보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-119">The setting of the **min memory per query** option has precedence over the **index create memory** option.</span></span> <span data-ttu-id="e8b79-120">두 옵션을 변경할 때 **인덱스 생성 메모리** 가 **쿼리당 최소 메모리**보다 적은 경우 경고 메시지가 나타나지만 값은 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-120">If you change both options and the **index create memory** is less than **min memory per query**, you receive a warning message, but the value is set.</span></span> <span data-ttu-id="e8b79-121">쿼리를 실행하는 동안 유사한 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-121">During query execution, you receive a similar warning.</span></span>  
  
-   <span data-ttu-id="e8b79-122">분할된 테이블 및 인덱스를 사용할 때 분할된 인덱스가 정렬되지 않았고 병렬 처리 수준이 높은 경우 인덱스를 만드는 데 필요한 최소 메모리 요구 사항이 상당히 증가될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-122">When using partitioned tables and indexes, the minimum memory requirements for index creation may increase significantly if there are non-aligned partitioned indexes and a high degree of parallelism.</span></span> <span data-ttu-id="e8b79-123">이 옵션에 따라 단일 인덱스 생성 작업에서 모든 인덱스 파티션에 할당된 초기 총 메모리 양이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-123">This option controls the total initial amount of memory allocated for all index partitions in a single index creation operation.</span></span> <span data-ttu-id="e8b79-124">이 옵션으로 설정된 양이 쿼리 실행에 필요한 최소 양보다 적은 경우 오류 메시지가 나타나면서 쿼리가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-124">The query will terminate with an error message if the amount set by this option is less than the minimum required to run the query.</span></span>  
  
-   <span data-ttu-id="e8b79-125">이 옵션의 실행 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행 중인 운영 체제와 하드웨어 플랫폼에 사용할 수 있는 실제 메모리 양을 초과하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-125">The run value for this option will not exceed the actual amount of memory that can be used for the operating system and hardware platform on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="e8b79-126">32비트 운영 체제에서 실행 값은 3GB 미만입니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-126">On 32-bit operating systems, the run value will be less than 3 gigabytes (GB).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e8b79-127">권장 사항</span><span class="sxs-lookup"><span data-stu-id="e8b79-127">Recommendations</span></span>  
  
-   <span data-ttu-id="e8b79-128">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-128">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="e8b79-129">**index create memory** 옵션은 자체 구성되므로 대부분 조정이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-129">The **index create memory** option is self-configuring and usually works without requiring adjustment.</span></span> <span data-ttu-id="e8b79-130">그러나 인덱스를 만드는 데 문제가 있으면 이 옵션의 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-130">However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e8b79-131">보안</span><span class="sxs-lookup"><span data-stu-id="e8b79-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e8b79-132">권한</span><span class="sxs-lookup"><span data-stu-id="e8b79-132">Permissions</span></span>  
 <span data-ttu-id="e8b79-133">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="e8b79-134">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="e8b79-135">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e8b79-136">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e8b79-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-index-create-memory-option"></a><span data-ttu-id="e8b79-137">index create memory 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="e8b79-137">To configure the index create memory option</span></span>  
  
1.  <span data-ttu-id="e8b79-138">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="e8b79-139">**메모리** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-139">Click the **Memory** node.</span></span>  
  
3.  <span data-ttu-id="e8b79-140">**Index creation memory**에서 원하는 index create memory 옵션 값을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-140">Under **Index creation memory**, type or select the desired value for the index create memory option.</span></span>  
  
     <span data-ttu-id="e8b79-141">**index create memory** 옵션을 사용하여 인덱스 생성 정렬에 사용하는 메모리 양을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-141">Use the **index create memory** option to control the amount of memory used by index creation sorts.</span></span> <span data-ttu-id="e8b79-142">**index create memory** 옵션은 자체 구성이므로 대부분 조정이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-142">The **index create memory** option is self-configuring and should work in most cases without requiring adjustment.</span></span> <span data-ttu-id="e8b79-143">그러나 인덱스를 만드는 데 문제가 있으면 이 옵션의 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-143">However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value.</span></span> <span data-ttu-id="e8b79-144">쿼리 정렬은 **쿼리당 최소 메모리** 옵션을 통해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-144">Query sorts are controlled through the **min memory per query** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e8b79-145">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e8b79-145">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-index-create-memory-option"></a><span data-ttu-id="e8b79-146">index create memory 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="e8b79-146">To configure the index create memory option</span></span>  
  
1.  <span data-ttu-id="e8b79-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e8b79-148">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e8b79-149">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e8b79-150">다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `index create memory` 옵션의 값을 `4096`(으)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-150">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `index create memory` option to `4096`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
EXEC sp_configure 'index create memory', 4096  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="e8b79-151">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-151">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-index-create-memory-option"></a><a name="FollowUp"></a> <span data-ttu-id="e8b79-152">후속 작업: 인덱스 생성 메모리 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="e8b79-152">Follow Up: After you configure the index create memory option</span></span>  
 <span data-ttu-id="e8b79-153">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b79-153">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b79-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8b79-154">See Also</span></span>  
 <span data-ttu-id="e8b79-155">[sys.configurations&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8b79-155">[sys.configurations &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) </span></span>  
 <span data-ttu-id="e8b79-156">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8b79-156">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="e8b79-157">[서버 메모리 서버 구성 옵션](server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="e8b79-157">[Server Memory Server Configuration Options](server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="e8b79-158">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8b79-158">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="e8b79-159">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e8b79-159">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
