---
title: 리소스 관리자를 사용하여 백업 압축을 통해 CPU 사용량 제한(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup compression [SQL Server], Resource Governor
- backup compression [SQL Server], CPU usage
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- Resource Governor, backup compression
ms.assetid: 01796551-578d-4425-9b9e-d87210f7ba72
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19a95cfa5c6780fbdf71ae58bd141aa9aa351efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742312"
---
# <a name="use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql"></a><span data-ttu-id="908e0-102">리소스 관리자를 사용하여 백업 압축을 통해 CPU 사용량 제한(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="908e0-102">Use Resource Governor to Limit CPU Usage by Backup Compression (Transact-SQL)</span></span>
  <span data-ttu-id="908e0-103">기본적으로 압축을 사용하여 백업하면 CPU 사용량이 크게 늘어나고 압축 프로세스로 사용되는 추가 CPU는 동시 작업에 악영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-103">By default, backing up using compression significantly increases CPU usage, and the additional CPU consumed by the compression process can adversely impact concurrent operations.</span></span> <span data-ttu-id="908e0-104">따라서 CPU 경합이 발생하면 CPU 사용량이[Resource Governor](../resource-governor/resource-governor.md) 로 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-104">Therefore, you might want to create a low-priority compressed backup in a session whose CPU usage is limited by[Resource Governor](../resource-governor/resource-governor.md) when CPU contention occurs.</span></span> <span data-ttu-id="908e0-105">이 항목에서는 이와 같은 경우에 CPU 사용량을 제한하는 리소스 관리자 작업 그룹에 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자의 세션을 매핑하는 방법으로 이러한 세션을 분류하는 시나리오를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-105">This topic presents a scenario that classifies the sessions of a particular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user by mapping them to a Resource Governor workload group that limits CPU usage in such cases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="908e0-106">주어진 리소스 관리자 시나리오에서 사용자 이름, 애플리케이션 이름을 비롯해 연결을 차별화하는 어떠한 요소라도 세션 분류의 기준이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-106">In a given Resource Governor scenario, session classification might be based on a user name, an application name, or anything else that can differentiate a connection.</span></span> <span data-ttu-id="908e0-107">자세한 내용은 [Resource Governor Classifier Function](../resource-governor/resource-governor-classifier-function.md) 및 [Resource Governor Workload Group](../resource-governor/resource-governor-workload-group.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="908e0-107">For more information, see [Resource Governor Classifier Function](../resource-governor/resource-governor-classifier-function.md) and [Resource Governor Workload Group](../resource-governor/resource-governor-workload-group.md).</span></span>  
  
##  <a name="this-topic-contains-the-following-set-of-scenarios-which-are-presented-in-sequence"></a><a name="Top"></a> <span data-ttu-id="908e0-108">이 항목에서는 다음과 같은 시나리오를 순서대로 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-108">This topic contains the following set of scenarios, which are presented in sequence:</span></span>  
  
1.  [<span data-ttu-id="908e0-109">우선 순위가 낮은 작업에 대한 로그인 및 사용자 설정</span><span class="sxs-lookup"><span data-stu-id="908e0-109">Setting Up a Login and User for Low-Priority Operations</span></span>](#setup_login_and_user)  
  
2.  [<span data-ttu-id="908e0-110">CPU 사용량을 제한하도록 리소스 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="908e0-110">Configuring Resource Governor to Limit CPU Usage</span></span>](#configure_RG)  
  
3.  [<span data-ttu-id="908e0-111">현재 세션의 분류 확인(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="908e0-111">Verifying the Classification of the Current Session (Transact-SQL)</span></span>](#verifying)  
  
4.  [<span data-ttu-id="908e0-112">CPU가 제한된 세션을 사용하여 백업 압축</span><span class="sxs-lookup"><span data-stu-id="908e0-112">Compressing Backups Using a Session with Limited CPU</span></span>](#creating_compressed_backup)  
  
##  <a name="setting-up-a-login-and-user-for-low-priority-operations"></a><a name="setup_login_and_user"></a> <span data-ttu-id="908e0-113">우선 순위가 낮은 작업에 대한 로그인 및 사용자 설정</span><span class="sxs-lookup"><span data-stu-id="908e0-113">Setting Up a Login and User for Low-Priority Operations</span></span>  
 <span data-ttu-id="908e0-114">이 항목의 시나리오에는 우선 순위가 낮은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 및 사용자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-114">The scenario in this topic requires a low-priority [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user.</span></span> <span data-ttu-id="908e0-115">사용자 이름은 이 로그인에서 실행되는 세션을 분류하고 CPU 사용량을 제한하는 리소스 관리자 작업 그룹으로 이러한 세션을 라우팅하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-115">The user name will be used to classify sessions running in the login and route them to a Resource Governor workload group that limits CPU usage.</span></span>  
  
 <span data-ttu-id="908e0-116">다음 절차에서는 이러한 목적에 맞게 로그인 및 사용자를 설정하는 단계를 설명하며, 그다음에는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 예로 “예제 A: 로그인 및 사용자 설정(Transact-SQL)”이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-116">The following procedure describes the steps for setting up a login and user for this purpose, followed by a [!INCLUDE[tsql](../../includes/tsql-md.md)] example, "Example A: Setting Up a Login and User (Transact-SQL)."</span></span>  
  
### <a name="to-set-up-a-login-and-database-user-for-classifying-sessions"></a><span data-ttu-id="908e0-117">세션 분류를 위한 로그인 및 데이터베이스 사용자를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="908e0-117">To set up a login and database user for classifying sessions</span></span>  
  
1.  <span data-ttu-id="908e0-118">우선 순위가 낮은 압축된 백업을 만들기 위한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-118">Create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for creating low-priority compressed backups.</span></span>  
  
     <span data-ttu-id="908e0-119">**로그인을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="908e0-119">**To create a login**</span></span>  
  
    -   [<span data-ttu-id="908e0-120">로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="908e0-120">Create a Login</span></span>](../security/authentication-access/create-a-login.md)  
  
    -   [<span data-ttu-id="908e0-121">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="908e0-121">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
2.  <span data-ttu-id="908e0-122">필요에 따라 이 로그인에 VIEW SERVER STATE를 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-122">Optionally, grant VIEW SERVER STATE to this login.</span></span>  
  
    -   [<span data-ttu-id="908e0-123">GRANT 시스템 개체 사용 권한&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="908e0-123">GRANT System Object Permissions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/grant-system-object-permissions-transact-sql)  
  
     <span data-ttu-id="908e0-124">자세한 내용은 [GRANT 데이터베이스 보안 주체 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="908e0-124">For more information, see [GRANT Database Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).</span></span>  
  
3.  <span data-ttu-id="908e0-125">이 로그인의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-125">Create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user for this login.</span></span>  
  
     <span data-ttu-id="908e0-126">**사용자를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="908e0-126">**To create a user**</span></span>  
  
    -   [<span data-ttu-id="908e0-127">데이터베이스 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="908e0-127">Create a Database User</span></span>](../security/authentication-access/create-a-database-user.md)  
  
    -   [<span data-ttu-id="908e0-128">CREATE USER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="908e0-128">CREATE USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-user-transact-sql)  
  
4.  <span data-ttu-id="908e0-129">이 로그인 및 사용자의 세션에서 지정된 데이터베이스를 백업하도록 하려면 해당 데이터베이스의 db_backupoperator 데이터베이스 역할에 사용자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-129">To enable sessions of this login and user to back up a given database, add the user to the db_backupoperator database role of that database.</span></span> <span data-ttu-id="908e0-130">이 사용자가 백업할 각 데이터베이스에 대해 이를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-130">Do this for each database that this user will back up.</span></span> <span data-ttu-id="908e0-131">필요에 따라 다른 고정 데이터베이스 역할에 사용자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-131">Optionally, add the user to other fixed database roles.</span></span>  
  
     <span data-ttu-id="908e0-132">**고정 데이터베이스 역할에 사용자를 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="908e0-132">**To add a user to a fixed database role**</span></span>  
  
    -   [<span data-ttu-id="908e0-133">sp_addrolemember&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="908e0-133">sp_addrolemember &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)  
  
     <span data-ttu-id="908e0-134">자세한 내용은 [GRANT 데이터베이스 보안 주체 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="908e0-134">For more information, see [GRANT Database Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).</span></span>  
  
### <a name="example-a-setting-up-a-login-and-user-transact-sql"></a><span data-ttu-id="908e0-135">예제 A: 로그인 및 사용자 설정(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="908e0-135">Example A: Setting Up a Login and User (Transact-SQL)</span></span>  
 <span data-ttu-id="908e0-136">다음 예는 우선 순위가 낮은 백업을 위한 새 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 및 사용자를 만들도록 선택한 경우에만 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-136">The following example is relevant only if you choose to create a new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user for low-priority backups.</span></span> <span data-ttu-id="908e0-137">또는 적절한 기존의 로그인 및 사용자가 있는 경우 이를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-137">Alternatively, you can use an existing login and user, if an appropriate one exists.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="908e0-138">다음 예제에서는 샘플 로그인 및 사용자 이름 *domain_name*`\MAX_CPU`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-138">The following example uses a sample login and user name, *domain_name*`\MAX_CPU`.</span></span> <span data-ttu-id="908e0-139">이를 우선 순위가 낮은 압축된 백업을 만들 때 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 및 사용자로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-139">Replace these with the names of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user that you plan to use when creating your low-priority compressed backups.</span></span>  
  
 <span data-ttu-id="908e0-140">이 예제에서는 *domain_name*`\MAX_CPU` Windows 계정의 로그인을 만든 다음 이 로그인에 VIEW SERVER STATE 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-140">This example creates a login for the *domain_name*`\MAX_CPU` Windows account and then grants VIEW SERVER STATE permission to the login.</span></span> <span data-ttu-id="908e0-141">이 권한을 통해 로그인 세션의 리소스 관리자 분류를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-141">This permission enables you to verify the Resource Governor classification of sessions of the login.</span></span> <span data-ttu-id="908e0-142">그런 다음 *domain_name*`\MAX_CPU` 의 사용자를 만들어 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 샘플 데이터베이스에 대한 db_backupoperator 고정 데이터베이스 역할에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-142">The example then creates a user for *domain_name*`\MAX_CPU` and adds it to the db_backupoperator fixed database role for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="908e0-143">이 사용자 이름은 리소스 관리자 분류자 함수에 의해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-143">This user name will be used by the Resource Governor classifier function.</span></span>  
  
```sql  
-- Create a SQL Server login for low-priority operations  
USE master;  
CREATE LOGIN [domain_name\MAX_CPU] FROM WINDOWS;  
GRANT VIEW SERVER STATE TO [domain_name\MAX_CPU];  
GO  
-- Create a SQL Server user in AdventureWorks2012 for this login  
USE AdventureWorks2012;  
CREATE USER [domain_name\MAX_CPU] FOR LOGIN [domain_name\MAX_CPU];  
EXEC sp_addrolemember 'db_backupoperator', 'domain_name\MAX_CPU';  
GO  
  
```  
  
 [<span data-ttu-id="908e0-144">&#91;맨 위로 이동&#93;</span><span class="sxs-lookup"><span data-stu-id="908e0-144">&#91;Top&#93;</span></span>](#Top)  
  
##  <a name="configuring-resource-governor-to-limit-cpu-usage"></a><a name="configure_RG"></a> <span data-ttu-id="908e0-145">CPU 사용량을 제한하도록 리소스 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="908e0-145">Configuring Resource Governor to Limit CPU Usage</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="908e0-146">리소스 관리자가 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-146">Ensure that Resource Governor is enabled.</span></span> <span data-ttu-id="908e0-147">자세한 내용은 [Resource Governor 사용](../resource-governor/enable-resource-governor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="908e0-147">For more information, see [Enable Resource Governor](../resource-governor/enable-resource-governor.md).</span></span>  
  
 <span data-ttu-id="908e0-148">이 리소스 관리자 시나리오는 다음과 같은 기본 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-148">In this Resource Governor scenario, configuration comprises the following basic steps:</span></span>  
  
1.  <span data-ttu-id="908e0-149">CPU 충돌이 발생하면 리소스 풀의 요청에 지정되는 최대 평균 CPU 대역폭을 제한하는 리소스 관리자 리소스 풀을 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-149">Create and configure a Resource Governor resource pool that limits the maximum average CPU bandwidth that will be given to requests in the resource pool when CPU contention occurs.</span></span>  
  
2.  <span data-ttu-id="908e0-150">이 풀을 사용하는 리소스 관리자 작업 그룹을 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-150">Create and configure a Resource Governor workload group that uses this pool.</span></span>  
  
3.  <span data-ttu-id="908e0-151">*분류자 함수*를 만듭니다. 분류자 함수는 UDF(사용자 정의 함수)로, Resource Governor는 세션을 적절한 작업 그룹으로 라우팅되도록 분류하기 위해 이 함수의 반환 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-151">Create a *classifier function*, which is a user-defined function (UDF) whose return values are used by Resource Governor for classifying sessions so that they are routed to the appropriate workload group.</span></span>  
  
4.  <span data-ttu-id="908e0-152">분류자 함수를 리소스 관리자에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-152">Register the classifier function with Resource Governor.</span></span>  
  
5.  <span data-ttu-id="908e0-153">변경 내용을 리소스 관리자 메모리 내 구성에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-153">Apply the changes to the Resource Governor in-memory configuration.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="908e0-154">Resource Governor 리소스 풀, 작업 그룹 및 분류에 대한 자세한 내용은 [Resource Governor](../resource-governor/resource-governor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="908e0-154">For information about Resource Governor resource pools, workload groups, and classification, see [Resource Governor](../resource-governor/resource-governor.md).</span></span>  
  
 <span data-ttu-id="908e0-155">이러한 단계를 위한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 "CPU 사용량을 제한하도록 리소스 관리자를 구성하려면" 절차에 설명되어 있습니다. 그 다음에는 이 절차의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 예가 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-155">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for these steps are described in the procedure, "To configure Resource Governor for limiting CPU usage," which is followed by a [!INCLUDE[tsql](../../includes/tsql-md.md)] example of the procedure.</span></span>  
  
 <span data-ttu-id="908e0-156">**리소스 관리자를 구성하려면(SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="908e0-156">**To configure Resource Governor (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="908e0-157">템플릿을 사용하여 리소스 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="908e0-157">Configure Resource Governor Using a Template</span></span>](../resource-governor/configure-resource-governor-using-a-template.md)  
  
-   [<span data-ttu-id="908e0-158">리소스 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="908e0-158">Create a Resource Pool</span></span>](../resource-governor/create-a-resource-pool.md)  
  
-   [<span data-ttu-id="908e0-159">작업 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="908e0-159">Create a Workload Group</span></span>](../resource-governor/create-a-workload-group.md)  
  
### <a name="to-configure-resource-governor-for-limiting-cpu-usage-transact-sql"></a><span data-ttu-id="908e0-160">CPU 사용량을 제한하도록 리소스 관리자를 구성하려면(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="908e0-160">To configure Resource Governor for limiting CPU usage (Transact-SQL)</span></span>  
  
1.  <span data-ttu-id="908e0-161">[CREATE RESOURCE POOL](/sql/t-sql/statements/create-resource-pool-transact-sql) 문을 실행하여 리소스 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-161">Issue a [CREATE RESOURCE POOL](/sql/t-sql/statements/create-resource-pool-transact-sql) statement to create a resource pool.</span></span> <span data-ttu-id="908e0-162">이 절차에 대한 예에서는 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-162">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="908e0-163">*CREATE RESOURCE POOL pool_name* WITH ( MAX_CPU_PERCENT = *value* );</span><span class="sxs-lookup"><span data-stu-id="908e0-163">*CREATE RESOURCE POOL pool_name* WITH ( MAX_CPU_PERCENT = *value* );</span></span>  
  
     <span data-ttu-id="908e0-164">*Value* 는 최대 평균 CPU 대역폭의 비율을 나타내는 1에서 100까지의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-164">*Value* is an integer from 1 to 100 that indicates the percentage of maximum average CPU bandwidth.</span></span> <span data-ttu-id="908e0-165">적절한 값은 해당 환경에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-165">The appropriate value depends on your environment.</span></span> <span data-ttu-id="908e0-166">이 항목의 예에서는 설명을 위해 20% 비율을 사용합니다(MAX_CPU_PERCENT = 20).</span><span class="sxs-lookup"><span data-stu-id="908e0-166">For the purpose of illustration, the example in this topic uses 20%  percent (MAX_CPU_PERCENT = 20.)</span></span>  
  
2.  <span data-ttu-id="908e0-167">[CREATE WORKLOAD GROUP](/sql/t-sql/statements/create-workload-group-transact-sql) 문을 실행하여 CPU 사용량을 관리하려는 우선 순위가 낮은 작업에 대한 작업 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-167">Issue a [CREATE WORKLOAD GROUP](/sql/t-sql/statements/create-workload-group-transact-sql) statement to create a workload group for low-priority operations whose CPU usage you want to govern.</span></span> <span data-ttu-id="908e0-168">이 절차에 대한 예에서는 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-168">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="908e0-169">CREATE WORKLOAD GROUP *group_name* USING *pool_name*;</span><span class="sxs-lookup"><span data-stu-id="908e0-169">CREATE WORKLOAD GROUP *group_name* USING *pool_name*;</span></span>  
  
3.  <span data-ttu-id="908e0-170">[CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) 문을 실행하여 이전 단계에서 만든 작업 그룹을 우선 순위가 낮은 로그인의 사용자에 매핑하는 분류자 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-170">Issue a [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) statement to create a classifier function that maps the workload group created in the preceding step to the user of the low-priority login.</span></span> <span data-ttu-id="908e0-171">이 절차에 대한 예에서는 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-171">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="908e0-172">CREATE FUNCTION [*schema_name*.]*function_name*() RETURNS sysname</span><span class="sxs-lookup"><span data-stu-id="908e0-172">CREATE FUNCTION [*schema_name*.]*function_name*() RETURNS sysname</span></span>  
  
     <span data-ttu-id="908e0-173">WITH SCHEMABINDING</span><span class="sxs-lookup"><span data-stu-id="908e0-173">WITH SCHEMABINDING</span></span>  
  
     <span data-ttu-id="908e0-174">AS</span><span class="sxs-lookup"><span data-stu-id="908e0-174">AS</span></span>  
  
     <span data-ttu-id="908e0-175">BEGIN</span><span class="sxs-lookup"><span data-stu-id="908e0-175">BEGIN</span></span>  
  
     <span data-ttu-id="908e0-176">DECLARE @workload_group_name AS *sysname*</span><span class="sxs-lookup"><span data-stu-id="908e0-176">DECLARE @workload_group_name AS *sysname*</span></span>  
  
     <span data-ttu-id="908e0-177">IF (SUSER_NAME() = '*user_of_low_priority_login*')</span><span class="sxs-lookup"><span data-stu-id="908e0-177">IF (SUSER_NAME() = '*user_of_low_priority_login*')</span></span>  
  
     <span data-ttu-id="908e0-178">SET @workload_group_name = '*workload_group_name*'</span><span class="sxs-lookup"><span data-stu-id="908e0-178">SET @workload_group_name = '*workload_group_name*'</span></span>  
  
     <span data-ttu-id="908e0-179">RETURN @workload_group_name</span><span class="sxs-lookup"><span data-stu-id="908e0-179">RETURN @workload_group_name</span></span>  
  
     <span data-ttu-id="908e0-180">End</span><span class="sxs-lookup"><span data-stu-id="908e0-180">END</span></span>  
  
     <span data-ttu-id="908e0-181">이 CREATE FUNCTION 문의 구성 요소에 대한 자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="908e0-181">For information about the components of this CREATE FUNCTION statement, see:</span></span>  
  
    -   [<span data-ttu-id="908e0-182">DECLARE @local_variable&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="908e0-182">DECLARE @local_variable &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
    -   [<span data-ttu-id="908e0-183">SUSER_SNAME&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="908e0-183">SUSER_SNAME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/suser-sname-transact-sql)  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="908e0-184">SUSER_NAME은 분류자 함수에 사용할 수 있는 여러 시스템 함수 중 하나일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-184">SUSER_NAME is just one of several system functions that can be used in a classifier function.</span></span> <span data-ttu-id="908e0-185">자세한 내용은 [분류자 사용자 정의 함수 만들기 및 테스트](../resource-governor/create-and-test-a-classifier-user-defined-function.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="908e0-185">For more information, see [Create and Test a Classifier User-Defined Function](../resource-governor/create-and-test-a-classifier-user-defined-function.md).</span></span>  
  
    -   <span data-ttu-id="908e0-186">[SET @local_variable&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="908e0-186">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql).</span></span>  
  
4.  <span data-ttu-id="908e0-187">[ALTER RESOURCE GOVERNOR](/sql/t-sql/statements/alter-resource-governor-transact-sql) 문을 실행하여 리소스 관리자에 분류자 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-187">Issue an [ALTER RESOURCE GOVERNOR](/sql/t-sql/statements/alter-resource-governor-transact-sql) statement to register the classifier function with Resource Governor.</span></span> <span data-ttu-id="908e0-188">이 절차에 대한 예에서는 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-188">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="908e0-189">ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *schema_name*.*function_name*);</span><span class="sxs-lookup"><span data-stu-id="908e0-189">ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *schema_name*.*function_name*);</span></span>  
  
5.  <span data-ttu-id="908e0-190">두 번째 ALTER RESOURCE GOVERNOR 문을 실행하여 다음과 같이 변경 내용을 리소스 관리자 메모리 내 구성에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-190">Issue a second ALTER RESOURCE GOVERNOR statement to apply the changes to the Resource Governor in-memory configuration, as follows:</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE;  
    ```  
  
### <a name="example-b-configuring-resource-governor-transact-sql"></a><span data-ttu-id="908e0-191">예제 B: Resource Governor 구성(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="908e0-191">Example B: Configuring Resource Governor (Transact-SQL)</span></span>  
 <span data-ttu-id="908e0-192">다음 예에서는 하나의 트랜잭션 내에서 다음과 같은 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-192">The following example performs the following steps within a single transaction:</span></span>  
  
1.  <span data-ttu-id="908e0-193">`pMAX_CPU_PERCENT_20` 리소스 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-193">Creates the `pMAX_CPU_PERCENT_20` resource pool.</span></span>  
  
2.  <span data-ttu-id="908e0-194">`gMAX_CPU_PERCENT_20` 작업 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-194">Creates the `gMAX_CPU_PERCENT_20` workload group.</span></span>  
  
3.  <span data-ttu-id="908e0-195">이전 예에서 만든 사용자 이름을 사용하는 `rgclassifier_MAX_CPU()` 분류자 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-195">Creates the `rgclassifier_MAX_CPU()` classifier function, which uses the user name created in the preceding example.</span></span>  
  
4.  <span data-ttu-id="908e0-196">분류자 함수를 리소스 관리자에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-196">Registers the classifier function with Resource Governor.</span></span>  
  
 <span data-ttu-id="908e0-197">트랜잭션을 커밋한 후 예에서는 ALTER WORKLOAD GROUP 또는 ALTER RESOURCE POOL 문에 요청된 구성 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-197">After committing the transaction, the example applies the configuration changes requested in the ALTER WORKLOAD GROUP or ALTER RESOURCE POOL statements.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="908e0-198">다음 예제에서는 “예제 A: 로그인 및 사용자 설정(Transact-SQL)”에서 만든 샘플 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자의 사용자 이름인 *domain_name*`\MAX_CPU`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-198">The following example uses the user name of the sample [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user created in "Example A: Setting Up a Login and User (Transact-SQL)," *domain_name*`\MAX_CPU`.</span></span> <span data-ttu-id="908e0-199">이 이름을 우선 순위가 낮은 압축된 백업을 만드는 데 사용할 로그인 사용자의 이름으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-199">Replace this with the name of the user of the login that you plan to use for creating low-priority compressed backups.</span></span>  
  
```sql  
-- Configure Resource Governor.  
BEGIN TRAN  
USE master;  
-- Create a resource pool that sets the MAX_CPU_PERCENT to 20%.   
CREATE RESOURCE POOL pMAX_CPU_PERCENT_20  
   WITH  
      (MAX_CPU_PERCENT = 20);  
GO  
-- Create a workload group to use this pool.   
CREATE WORKLOAD GROUP gMAX_CPU_PERCENT_20  
USING pMAX_CPU_PERCENT_20;  
GO  
-- Create a classification function.  
-- Note that any request that does not get classified goes into   
-- the 'Default' group.  
CREATE FUNCTION dbo.rgclassifier_MAX_CPU() RETURNS sysname   
WITH SCHEMABINDING  
AS  
BEGIN  
    DECLARE @workload_group_name AS sysname  
      IF (SUSER_NAME() = 'domain_name\MAX_CPU')  
          SET @workload_group_name = 'gMAX_CPU_PERCENT_20'  
    RETURN @workload_group_name  
END;  
GO  
  
-- Register the classifier function with Resource Governor.  
ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION= dbo.rgclassifier_MAX_CPU);  
COMMIT TRAN;  
GO  
-- Start Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
  
```  
  
 [<span data-ttu-id="908e0-200">&#91;맨 위로 이동&#93;</span><span class="sxs-lookup"><span data-stu-id="908e0-200">&#91;Top&#93;</span></span>](#Top)  
  
##  <a name="verifying-the-classification-of-the-current-session-transact-sql"></a><a name="verifying"></a> <span data-ttu-id="908e0-201">현재 세션의 분류 확인(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="908e0-201">Verifying the Classification of the Current Session (Transact-SQL)</span></span>  
 <span data-ttu-id="908e0-202">필요에 따라 분류자 함수에 지정한 사용자로 로그인한 후 개체 탐색기에서 다음 [SELECT](/sql/t-sql/queries/select-transact-sql) 문을 실행하여 세션 분류를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-202">Optionally, log in as the user that you specified in your classifier function, and verify the session classification by issuing the following [SELECT](/sql/t-sql/queries/select-transact-sql) statement in Object Explorer:</span></span>  
  
```sql  
USE master;  
SELECT sess.session_id, sess.login_name, sess.group_id, grps.name   
FROM sys.dm_exec_sessions AS sess   
JOIN sys.dm_resource_governor_workload_groups AS grps   
    ON sess.group_id = grps.group_id  
WHERE session_id > 50;  
GO  
```  
  
 <span data-ttu-id="908e0-203">결과 창의 **name** 열에는 분류자 함수에서 지정한 작업 그룹 이름에 대한 하나 이상의 세션이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-203">In the results pane, the **name** column should list one or more sessions for the workload-group name that you specified in your classifier function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="908e0-204">이 SELECT 문에서 호출하는 동적 관리 뷰에 대한 자세한 내용은 [sys.dm_exec_sessions&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 및 [sys.dm_resource_governor_workload_groups&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="908e0-204">For information about the dynamic management views called by this SELECT statement, see [sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) and [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql).</span></span>  
  
 [<span data-ttu-id="908e0-205">&#91;맨 위로 이동&#93;</span><span class="sxs-lookup"><span data-stu-id="908e0-205">&#91;Top&#93;</span></span>](#Top)  
  
##  <a name="compressing-backups-using-a-session-with-limited-cpu"></a><a name="creating_compressed_backup"></a> <span data-ttu-id="908e0-206">CPU가 제한된 세션을 사용하여 백업 압축</span><span class="sxs-lookup"><span data-stu-id="908e0-206">Compressing Backups Using a Session with Limited CPU</span></span>  
 <span data-ttu-id="908e0-207">최대 CPU가 제한된 세션에서 압축된 백업을 만들려면 분류자 함수에 지정된 사용자로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-207">To create a compressed backup in a session with a limited maximum CPU, log in as the user specified in your classifier function.</span></span> <span data-ttu-id="908e0-208">백업 명령에 WITH COMPRESSION ()을 지정 [!INCLUDE[tsql](../../includes/tsql-md.md)] 하거나 **백업 압축** ()을 선택 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-208">In your backup command, either specify WITH COMPRESSION ([!INCLUDE[tsql](../../includes/tsql-md.md)]) or select **Compress backup** ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]).</span></span> <span data-ttu-id="908e0-209">압축된 데이터베이스 백업을 만들려면 [전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="908e0-209">To create a compressed database backup, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
### <a name="example-c-creating-a-compressed-backup-transact-sql"></a><span data-ttu-id="908e0-210">예제 C: 압축된 백업 만들기(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="908e0-210">Example C: Creating a Compressed Backup (Transact-SQL)</span></span>  
 <span data-ttu-id="908e0-211">다음 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 예에서는 새로 형식이 지정된 백업 파일인 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 에 `Z:\SQLServerBackups\AdvWorksData.bak`데이터베이스의 압축된 전체 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="908e0-211">The following [BACKUP](/sql/t-sql/statements/backup-transact-sql) example creates a compressed full backup of the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database in a newly formatted backup file, `Z:\SQLServerBackups\AdvWorksData.bak`.</span></span>  
  
```sql  
--Run backup statement in the gBackup session.  
BACKUP DATABASE AdventureWorks2012 TO DISK='Z:\SQLServerBackups\AdvWorksData.bak'   
WITH   
   FORMAT,   
   MEDIADESCRIPTION='AdventureWorks2012 Compressed Data Backups'  
   DESCRIPTION='First database backup on AdventureWorks2012 Compressed Data Backups media set'  
   COMPRESSION;  
GO  
```  
  
 [<span data-ttu-id="908e0-212">&#91;맨 위로 이동&#93;</span><span class="sxs-lookup"><span data-stu-id="908e0-212">&#91;Top&#93;</span></span>](#Top)  
  
## <a name="see-also"></a><span data-ttu-id="908e0-213">참고 항목</span><span class="sxs-lookup"><span data-stu-id="908e0-213">See Also</span></span>  
 <span data-ttu-id="908e0-214">[분류자 사용자 정의 함수 만들기 및 테스트](../resource-governor/create-and-test-a-classifier-user-defined-function.md) </span><span class="sxs-lookup"><span data-stu-id="908e0-214">[Create and Test a Classifier User-Defined Function](../resource-governor/create-and-test-a-classifier-user-defined-function.md) </span></span>  
 [<span data-ttu-id="908e0-215">리소스 관리자</span><span class="sxs-lookup"><span data-stu-id="908e0-215">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
