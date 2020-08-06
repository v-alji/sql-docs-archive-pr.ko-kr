---
title: 가용성 복제본에 대한 읽기 전용 액세스 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- connection access to availability replicas
- Availability Groups [SQL Server], readable secondary replicas
- active secondary replicas [SQL Server], read-only access to
- Availability Groups [SQL Server], read-only routing
- Availability Groups [SQL Server], client connectivity
ms.assetid: 22387419-22c4-43fa-851c-5fecec4b049b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab13081396aff46d193c1b0449d6b93042ee60d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729832"
---
# <a name="configure-read-only-access-on-an-availability-replica-sql-server"></a><span data-ttu-id="4254d-102">가용성 복제본에 대한 읽기 전용 액세스 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4254d-102">Configure Read-Only Access on an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="4254d-103">기본적으로 주 복제본에 대한 읽기/쓰기 및 읽기 전용 액세스가 모두 허용되며 AlwaysOn 가용성 그룹의 보조 복제본에 대한 연결은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-103">By default both read-write and read-intent access are allowed to the primary replica and no connections are allowed to secondary replicas of an AlwaysOn availability group.</span></span> <span data-ttu-id="4254d-104">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹의 가용성 복제본에 대한 연결 액세스를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-104">This topic describes how to configure connection access on an availability replica of an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
 <span data-ttu-id="4254d-105">보조 복제본에 대해 읽기 전용 액세스를 사용하도록 설정할 경우의 영향에 대한 자세한 내용과 연결 액세스 소개는 [가용성 복제본에 대한 클라이언트 연결 액세스 정보&#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) 및 [활성 보조: 읽기 가능한 보조 복제본&#40;AlwaysOn 가용성 그룹&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4254d-105">For information about the implications of enabling read-only access for a secondary replica and for an introduction to connection access, see [About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) and [Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4254d-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4254d-106">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="4254d-107">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="4254d-107">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="4254d-108">다른 연결 액세스를 구성하려면 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-108">To configure different connection access, you must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4254d-109">보안</span><span class="sxs-lookup"><span data-stu-id="4254d-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4254d-110">권한</span><span class="sxs-lookup"><span data-stu-id="4254d-110">Permissions</span></span>  
  
|<span data-ttu-id="4254d-111">Task</span><span class="sxs-lookup"><span data-stu-id="4254d-111">Task</span></span>|<span data-ttu-id="4254d-112">사용 권한</span><span class="sxs-lookup"><span data-stu-id="4254d-112">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="4254d-113">가용성 그룹을 만들 때 복제본을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="4254d-113">To configure replicas when creating an availability group</span></span>|<span data-ttu-id="4254d-114">CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-114">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="4254d-115">가용성 복제본을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="4254d-115">To modify an availability replica</span></span>|<span data-ttu-id="4254d-116">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-116">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4254d-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4254d-117">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4254d-118">**가용성 복제본에 대한 액세스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="4254d-118">**To configure access on an availability replica**</span></span>  
  
1.  <span data-ttu-id="4254d-119">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-119">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="4254d-120">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-120">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="4254d-121">복제본을 변경할 가용성 그룹을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-121">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="4254d-122">가용성 복제본을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-122">Right-click the availability replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="4254d-123">**가용성 복제본 속성** 대화 상자에서 다음과 같이 주 역할 및 보조 역할에 대한 연결 액세스를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-123">In the **Availability Replica Properties** dialog box, you can change the connection access for the primary role and for the secondary role, as follows:</span></span>  
  
    -   <span data-ttu-id="4254d-124">보조 역할의 경우 **읽기용 보조** 드롭 목록의 다음 값 중에서 새 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-124">For the secondary role, select a new value from the **Readable secondary** drop list, as follows:</span></span>  
  
         <span data-ttu-id="4254d-125">**아니요**</span><span class="sxs-lookup"><span data-stu-id="4254d-125">**No**</span></span>  
         <span data-ttu-id="4254d-126">이 복제본의 보조 데이터베이스에 대한 사용자 연결이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-126">No user connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="4254d-127">즉, 읽기 액세스가 가능하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-127">They are not available for read access.</span></span> <span data-ttu-id="4254d-128">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-128">This is the default setting.</span></span>  
  
         <span data-ttu-id="4254d-129">**읽기 전용만**</span><span class="sxs-lookup"><span data-stu-id="4254d-129">**Read-intent only**</span></span>  
         <span data-ttu-id="4254d-130">이 복제본의 보조 데이터베이스에 대한 읽기 전용 연결만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-130">Only read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="4254d-131">즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-131">The secondary database(s) are all available for read access.</span></span>  
  
         <span data-ttu-id="4254d-132">**예**</span><span class="sxs-lookup"><span data-stu-id="4254d-132">**Yes**</span></span>  
         <span data-ttu-id="4254d-133">이 복제본의 보조 데이터베이스에 대한 모든 연결이 허용되지만 읽기 액세스만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-133">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="4254d-134">즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-134">The secondary database(s) are all available for read access.</span></span>  
  
    -   <span data-ttu-id="4254d-135">주 역할의 경우 **주 역할의 연결 모드** 드롭 목록의 다음 값 중에서 새 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-135">For the primary role, select a new value from the **Connections in primary role** drop list, as follows:</span></span>  
  
         <span data-ttu-id="4254d-136">**모든 연결 허용**</span><span class="sxs-lookup"><span data-stu-id="4254d-136">**Allow all connections**</span></span>  
         <span data-ttu-id="4254d-137">주 복제본의 데이터베이스에 대한 모든 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-137">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="4254d-138">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-138">This is the default setting.</span></span>  
  
         <span data-ttu-id="4254d-139">**읽기/쓰기 연결 허용**</span><span class="sxs-lookup"><span data-stu-id="4254d-139">**Allow read/write connections**</span></span>  
         <span data-ttu-id="4254d-140">애플리케이션 의도 속성이 **ReadWrite** 로 설정되었거나 애플리케이션 의도 연결 속성이 설정되지 않은 경우에는 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-140">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="4254d-141">애플리케이션 의도 연결 속성이 **ReadOnly** 로 설정된 연결은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-141">Connections where the Application Intent connection property is set to **ReadOnly** are not allowed.</span></span> <span data-ttu-id="4254d-142">따라서 고객이 읽기 전용 작업을 실수로 주 복제본에 연결하는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-142">This can help prevent customers from connecting a read-intent work load to the primary replica by mistake.</span></span> <span data-ttu-id="4254d-143">애플리케이션 의도 연결 속성에 대한 자세한 내용은 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4254d-143">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4254d-144">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4254d-144">Using Transact-SQL</span></span>  
 <span data-ttu-id="4254d-145">**가용성 복제본에 대한 액세스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="4254d-145">**To configure access on an availability replica**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4254d-146">이 절차에 대한 예는 이 섹션의 뒷부분에 나오는 [예제(Transact-SQL)](#TsqlExample)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4254d-146">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="4254d-147">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-147">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="4254d-148">새 가용성 그룹에 대한 복제본을 지정하려는 경우 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-148">If you are specifying a replica for a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="4254d-149">기존 가용성 그룹의 복제본을 추가하거나 수정하려는 경우에는 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-149">If you are adding or modifying a replica of an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="4254d-150">보조 역할에 대한 연결 액세스를 구성하려면 ADD REPLICA 또는 MODIFY REPLICA WITH 절에서 다음과 같이 SECONDARY_ROLE 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-150">To configure connection access for the secondary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the SECONDARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="4254d-151">SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**</span><span class="sxs-lookup"><span data-stu-id="4254d-151">SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**</span></span>  
  
         <span data-ttu-id="4254d-152">각 항목이 나타내는 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-152">where,</span></span>  
  
         <span data-ttu-id="4254d-153">아니요</span><span class="sxs-lookup"><span data-stu-id="4254d-153">NO</span></span>  
         <span data-ttu-id="4254d-154">이 복제본의 보조 데이터베이스에 대한 직접 연결이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-154">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="4254d-155">즉, 읽기 액세스가 가능하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-155">They are not available for read access.</span></span> <span data-ttu-id="4254d-156">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-156">This is the default setting.</span></span>  
  
         <span data-ttu-id="4254d-157">READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="4254d-157">READ_ONLY</span></span>  
         <span data-ttu-id="4254d-158">이 복제본의 보조 데이터베이스에 대한 읽기 전용 연결만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-158">Only read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="4254d-159">즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-159">The secondary database(s) are all available for read access.</span></span>  
  
         <span data-ttu-id="4254d-160">ALL</span><span class="sxs-lookup"><span data-stu-id="4254d-160">ALL</span></span>  
         <span data-ttu-id="4254d-161">이 복제본의 보조 데이터베이스에 대한 모든 연결이 허용되지만 읽기 액세스만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-161">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="4254d-162">즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-162">The secondary database(s) are all available for read access.</span></span>  
  
3.  <span data-ttu-id="4254d-163">주 역할에 대한 연결 액세스를 구성하려면 ADD REPLICA 또는 MODIFY REPLICA WITH 절에서 다음과 같이 PRIMARY_ROLE 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-163">To configure connection access for the primary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the PRIMARY_ROLE option, as follows:</span></span>  
  
     <span data-ttu-id="4254d-164">PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**</span><span class="sxs-lookup"><span data-stu-id="4254d-164">PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**</span></span>  
  
     <span data-ttu-id="4254d-165">각 항목이 나타내는 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-165">where,</span></span>  
  
     <span data-ttu-id="4254d-166">READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="4254d-166">READ_WRITE</span></span>  
     <span data-ttu-id="4254d-167">애플리케이션 의도 연결 속성이 **ReadOnly** 로 설정된 연결은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-167">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span>  <span data-ttu-id="4254d-168">애플리케이션 의도 속성이 **ReadWrite** 로 설정되었거나 애플리케이션 의도 연결 속성이 설정되지 않은 경우에는 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-168">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="4254d-169">애플리케이션 의도 연결 속성에 대한 자세한 내용은 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4254d-169">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
     <span data-ttu-id="4254d-170">ALL</span><span class="sxs-lookup"><span data-stu-id="4254d-170">ALL</span></span>  
     <span data-ttu-id="4254d-171">주 복제본의 데이터베이스에 대한 모든 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-171">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="4254d-172">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-172">This is the default setting.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="4254d-173">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4254d-173">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="4254d-174">다음 예제에서는 *AG2*라는 가용성 그룹에 보조 복제본을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-174">The following example adds a secondary replica to an availability group named *AG2*.</span></span> <span data-ttu-id="4254d-175">독립 실행형 서버 인스턴스인 *COMPUTER03\HADR_INSTANCE*가 새 가용성 복제본을 호스트하도록 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-175">A stand-alone server instance, *COMPUTER03\HADR_INSTANCE*, is specified to host the new availability replica.</span></span> <span data-ttu-id="4254d-176">이 복제본은 주 역할에 대해 읽기/쓰기 연결만 허용하고 보조 역할에 대해 읽기 전용 연결만 허용하도록 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-176">This replica configured to allow only read-write connections for the primary role and to allow only read-intent connections for secondary role.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP AG2   
   ADD REPLICA ON   
      'COMPUTER03\HADR_INSTANCE' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:7022',  
         PRIMARY_ROLE ( ALLOW_CONNECTIONS = READ_WRITE ),  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY )  
         );   
GO  
```  
  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="4254d-177">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="4254d-177">Using PowerShell</span></span>  

### <a name="to-configure-access-on-an-availability-replica"></a><span data-ttu-id="4254d-178">가용성 복제본에 대한 액세스를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="4254d-178">To configure access on an availability replica</span></span>
  
> [!NOTE]  
>  <span data-ttu-id="4254d-179">코드 예제를 보려면이 섹션의 뒷부분에 나오는 PowerShell 예제를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4254d-179">For a code example, see the PowerShell examples later in this section.</span></span>  
  
1.  <span data-ttu-id="4254d-180">주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-180">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="4254d-181">가용성 그룹에 가용성 복제본을 추가하는 경우 `New-SqlAvailabilityReplica` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-181">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="4254d-182">기존 가용성 복제본을 수정하는 경우 `Set-SqlAvailabilityReplica` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-182">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="4254d-183">관련 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-183">The relevant parameters are as follows:</span></span>  
  
    -   <span data-ttu-id="4254d-184">보조 역할에 대 한 연결 액세스를 구성 하려면 `ConnectionModeInSecondaryRole` *secondary_role_keyword* 매개 변수를 지정 합니다. 여기서 *secondary_role_keyword* 는 다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-184">To configure connection access for the secondary role, specify the `ConnectionModeInSecondaryRole`*secondary_role_keyword* parameter, where *secondary_role_keyword* equals one of the following values:</span></span>  
  
         `AllowNoConnections`  
         <span data-ttu-id="4254d-185">보조 복제본의 데이터베이스에 대한 직접 연결이 허용되지 않으며 읽기 액세스를 위해 데이터베이스에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-185">No direct connections are allowed to the databases in the secondary replica and the databases are not available for read access.</span></span> <span data-ttu-id="4254d-186">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-186">This is the default setting.</span></span>  
  
         `AllowReadIntentConnectionsOnly`  
         <span data-ttu-id="4254d-187">애플리케이션 의도 속성이 **ReadOnly**로 설정된 경우에만 보조 복제본의 데이터베이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-187">Connections are allowed only to the databases in the secondary replica where the Application Intent property is set to **ReadOnly**.</span></span> <span data-ttu-id="4254d-188">이 속성에 대한 자세한 내용은 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4254d-188">For more information about this property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
         `AllowAllConnections`  
         <span data-ttu-id="4254d-189">보조 복제본의 데이터베이스에 대해 읽기 전용 액세스를 위한 모든 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-189">All connections are allowed to the databases in the secondary replica for read-only access.</span></span>  
  
    -   <span data-ttu-id="4254d-190">주 역할에 대 한 연결 액세스를 구성 하려면 `ConnectionModeInPrimaryRole` *primary_role_keyword*를 지정 합니다. 여기서 *primary_role_keyword* 는 다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-190">To configure connection access for the primary role, specify `ConnectionModeInPrimaryRole`*primary_role_keyword*, where *primary_role_keyword* equals one of the following values:</span></span>  
  
         `AllowReadWriteConnections`  
         <span data-ttu-id="4254d-191">애플리케이션 의도 연결 속성이 ReadOnly로 설정된 연결은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-191">Connections where the Application Intent connection property is set to ReadOnly are disallowed.</span></span> <span data-ttu-id="4254d-192">애플리케이션 의도 속성이 ReadWrite로 설정되었거나 애플리케이션 의도 연결 속성이 설정되지 않은 경우에는 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-192">When the Application Intent property is set to ReadWrite or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="4254d-193">애플리케이션 의도 연결 속성에 대한 자세한 내용은 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4254d-193">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
         `AllowAllConnections`  
         <span data-ttu-id="4254d-194">주 복제본의 데이터베이스에 대한 모든 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-194">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="4254d-195">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-195">This is the default setting.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4254d-196">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-196">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="4254d-197">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4254d-197">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="4254d-198">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4254d-198">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
<span data-ttu-id="4254d-199">다음 예에서는 `ConnectionModeInSecondaryRole` 및 `ConnectionModeInPrimaryRole` 매개 변수를 모두 `AllowAllConnections`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-199">The following example, sets the both the `ConnectionModeInSecondaryRole` and `ConnectionModeInPrimaryRole` parameters to `AllowAllConnections`.</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  

Set-SqlAvailabilityReplica -ConnectionModeInSecondaryRole "AllowAllConnections" `
 -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ConnectionModeInPrimaryRole "AllowAllConnections" `
-InputObject $primaryReplica
```  

##  <a name="follow-up-after-configuring-read-only-access-for-an-availability-replica"></a><a name="FollowUp"></a> <span data-ttu-id="4254d-200">후속 작업: 가용성 복제본에 대한 읽기 전용 액세스를 구성한 후</span><span class="sxs-lookup"><span data-stu-id="4254d-200">Follow Up: After Configuring Read-Only Access for an Availability Replica</span></span>  
 <span data-ttu-id="4254d-201">**읽을 수 있는 보조 복제본에 대한 읽기 전용 액세스**</span><span class="sxs-lookup"><span data-stu-id="4254d-201">**Read-only access to a readable secondary replica**</span></span>  
  
-   <span data-ttu-id="4254d-202">[Bcp 유틸리티](../../../tools/bcp-utility.md) 또는 [sqlcmd 유틸리티](../../../tools/sqlcmd-utility.md)를 사용 하는 경우 스위치를 지정 하 여 읽기 전용 액세스를 사용 하도록 설정 된 보조 복제본에 대 한 읽기 전용 액세스를 지정할 수 있습니다 `-K ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="4254d-202">When using the [bcp Utility](../../../tools/bcp-utility.md) or [sqlcmd Utility](../../../tools/sqlcmd-utility.md), you can specify read-only access to any secondary replica that is enabled for read-only access by specifying the `-K ReadOnly` switch.</span></span>  
  
-   <span data-ttu-id="4254d-203">클라이언트 애플리케이션을 읽을 수 있는 보조 복제본에 연결할 수 있도록 설정하려면:</span><span class="sxs-lookup"><span data-stu-id="4254d-203">To enable client applications to connect to readable secondary replicas:</span></span>  
  
    ||<span data-ttu-id="4254d-204">필수 요소</span><span class="sxs-lookup"><span data-stu-id="4254d-204">Prerequisite</span></span>|<span data-ttu-id="4254d-205">링크</span><span class="sxs-lookup"><span data-stu-id="4254d-205">Link</span></span>|  
    |-|------------------|----------|  
    |<span data-ttu-id="4254d-206">![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")</span><span class="sxs-lookup"><span data-stu-id="4254d-206">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="4254d-207">가용성 그룹에 수신기가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-207">Ensure that the availability group has a listener.</span></span>|[<span data-ttu-id="4254d-208">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4254d-208">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)|  
    |<span data-ttu-id="4254d-209">![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")</span><span class="sxs-lookup"><span data-stu-id="4254d-209">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="4254d-210">가용성 그룹에 대한 읽기 전용 라우팅을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-210">Configure read-only routing for the availability group.</span></span>|[<span data-ttu-id="4254d-211">가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4254d-211">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)|  
  
 <span data-ttu-id="4254d-212">**장애 조치(Failover) 후 트리거 및 작업에 영향을 줄 수 있는 요소**</span><span class="sxs-lookup"><span data-stu-id="4254d-212">**Factors that might affect triggers and jobs after a failover**</span></span>  
  
 <span data-ttu-id="4254d-213">읽을 수 없는 보조 데이터베이스 또는 읽을 수 있는 보조 데이터베이스에서 실행할 때 실패하는 트리거 및 작업이 있는 경우 트리거와 작업을 스크립팅하여 지정된 복제본에서 데이터베이스가 주 데이터베이스인지 읽을 수 있는 보조 데이터베이스인지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-213">If you have triggers and jobs that will fail when running on a non-readable secondary database or on a readable secondary database, you need to script the triggers and jobs to check on a given replica to determine whether the database is a primary database or is a readable secondary database.</span></span> <span data-ttu-id="4254d-214">이 정보를 얻으려면 [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) 함수를 사용하여 데이터베이스의 **Updatability** 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-214">To obtain this information, use the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **Updatability** property of the database.</span></span> <span data-ttu-id="4254d-215">읽기 전용 데이터베이스를 식별하려면 다음과 같이 READ_ONLY를 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-215">To identify a read-only database, specify READ_ONLY as the value, as follows:</span></span>  
  
```  
DATABASEPROPERTYEX([db name],'Updatability') = N'READ_ONLY'  
```  
  
 <span data-ttu-id="4254d-216">쓰기 전용 데이터베이스를 식별하려면 READ_WRITE를 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4254d-216">To identify a read-write database, specify READ_WRITE as the value.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4254d-217">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4254d-217">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4254d-218">가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4254d-218">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="4254d-219">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4254d-219">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="4254d-220">관련 내용</span><span class="sxs-lookup"><span data-stu-id="4254d-220">Related Content</span></span>  
  
-   [<span data-ttu-id="4254d-221">Always On: 읽기 가능한 보조의 값 위치 지정</span><span class="sxs-lookup"><span data-stu-id="4254d-221">Always On: Value Proposition of Readable Secondary</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-value-proposition-of-readable-secondary)  
  
-   [<span data-ttu-id="4254d-222">Always On: 읽기 작업에 보조 복제본을 설정하는 옵션이 2개인 이유는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="4254d-222">Always On: Why there are two options to enable a secondary replica for read workload?</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-why-there-are-two-options-to-enable-a-secondary-replica-for-read-workload)  
  
-   [<span data-ttu-id="4254d-223">Always On: 읽기 가능한 보조 복제본 설정</span><span class="sxs-lookup"><span data-stu-id="4254d-223">Always On: Setting up Readable Secondary Replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-setting-up-readable-seconary-replica)  
  
-   [<span data-ttu-id="4254d-224">Always On: 읽기 가능한 보조 복제본을 설정했지만 내 쿼리가 차단됨</span><span class="sxs-lookup"><span data-stu-id="4254d-224">Always On: I just enabled Readable Secondary but my query is blocked?</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-i-just-enabled-readable-secondary-but-my-query-is-blocked)  
  
-   [<span data-ttu-id="4254d-225">Always On: 읽기 가능한 보조, 읽기 전용 데이터베이스 및 데이터베이스 스냅샷에서 최신 통계를 사용할 수 있도록 함</span><span class="sxs-lookup"><span data-stu-id="4254d-225">Always On: Making latest statistics available on Readable Secondary, Read-Only database and Database Snapshot</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-making-latest-statistics-available-on-readable-secondary-read-only-database-and-database-snapshot)  
  
-   [<span data-ttu-id="4254d-226">Always On: 읽기 전용 데이터베이스, 데이터베이스 스냅샷 및 보조 복제본에서 통계 사용 시 문제점</span><span class="sxs-lookup"><span data-stu-id="4254d-226">Always On: Challenges with statistics on ReadOnly database, Database Snapshot and Secondary Replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-challenges-with-statistics-on-readonly-database-database-snapshot-and-secondary-replica)  
  
-   [<span data-ttu-id="4254d-227">Always On: 보조 복제본에서 보고 작업을 실행할 때 주 작업에 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="4254d-227">Always On: Impact on the primary workload when you run reporting workload on the secondary replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-on-the-primary-workload-when-you-run-reporting-workload-on-the-secondary-replica)  
  
-   [<span data-ttu-id="4254d-228">Always On: 읽기 가능한 보조 복제본의 보고 작업을 스냅샷 격리로 매핑의 영향</span><span class="sxs-lookup"><span data-stu-id="4254d-228">Always On: Impact of mapping reporting workload on Readable Secondary to Snapshot Isolation</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-of-mapping-reporting-workload-on-readable-secondary-to-snapshot-isolation)  
  
-   [<span data-ttu-id="4254d-229">Always On: 보조 복제본에서 보고 작업을 실행하는 경우 REDO 스레드 차단 최소화</span><span class="sxs-lookup"><span data-stu-id="4254d-229">Always On: Minimizing blocking of REDO thread when running reporting workload on Secondary Replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-minimizing-blocking-of-redo-thread-when-running-reporting-workload-on-secondary-replica)  
  
-   [<span data-ttu-id="4254d-230">Always On: 읽기 가능한 보조 및 데이터 대기 시간</span><span class="sxs-lookup"><span data-stu-id="4254d-230">Always On: Readable Secondary and data latency</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-readable-secondary-and-data-latency)  
  
## <a name="see-also"></a><span data-ttu-id="4254d-231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4254d-231">See Also</span></span>  
 <span data-ttu-id="4254d-232">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4254d-232">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="4254d-233">활성 보조: 읽기 가능한 보조 복제본 &#40;AlwaysOn 가용성 그룹&#41;</span><span class="sxs-lookup"><span data-stu-id="4254d-233">Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)  
 [<span data-ttu-id="4254d-234">가용성 복제본에 대한 클라이언트 연결 액세스 정보&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4254d-234">About Client Connection Access to Availability Replicas &#40;SQL Server&#41;</span></span>](about-client-connection-access-to-availability-replicas-sql-server.md)  
