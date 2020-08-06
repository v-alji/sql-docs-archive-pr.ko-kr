---
title: 비관리자의 복제 모니터 사용 허용 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4a7699c555086d627e4c3a52ea70acf931ea1af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648937"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a><span data-ttu-id="5650a-102">비관리자의 복제 모니터 사용 허용</span><span class="sxs-lookup"><span data-stu-id="5650a-102">Allow Non-Administrators to Use Replication Monitor</span></span>
  <span data-ttu-id="5650a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 비관리자가 복제 모니터를 사용할 수 있도록 허용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-103">This topic describes how to allow non-administrators to use Replication Monitor in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5650a-104">복제 모니터는 다음 역할의 멤버인 사용자가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-104">Replication Monitor can be used by users who are members of the following roles:</span></span>  
  
-   <span data-ttu-id="5650a-105">**sysadmin** 고정 서버 역할</span><span class="sxs-lookup"><span data-stu-id="5650a-105">The **sysadmin** fixed server role.</span></span>  
  
     <span data-ttu-id="5650a-106">이러한 사용자는 복제를 모니터링할 수 있으며 에이전트 일정, 에이전트 프로필 등의 복제 속성 변경을 완벽하게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-106">These users can monitor replication and have full control over changing replication properties such as agent schedules, agent profiles, and so on.</span></span>  
  
-   <span data-ttu-id="5650a-107">`replmonitor`배포 데이터베이스의 데이터베이스 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-107">The `replmonitor` database role in the distribution database.</span></span>  
  
     <span data-ttu-id="5650a-108">이러한 사용자는 복제를 모니터링할 수만 있고 복제 속성을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-108">These users can monitor replication, but cannot change any replication properties.</span></span>  
  
 <span data-ttu-id="5650a-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5650a-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5650a-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5650a-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5650a-111">보안</span><span class="sxs-lookup"><span data-stu-id="5650a-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5650a-112">**비관리자의 복제 모니터 사용을 허용하려면:**</span><span class="sxs-lookup"><span data-stu-id="5650a-112">**To allow non-administrators to use Replication Monitor, using:**</span></span>  
  
     [<span data-ttu-id="5650a-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5650a-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5650a-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5650a-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5650a-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5650a-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5650a-116">보안</span><span class="sxs-lookup"><span data-stu-id="5650a-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5650a-117">권한</span><span class="sxs-lookup"><span data-stu-id="5650a-117">Permissions</span></span>  
 <span data-ttu-id="5650a-118">비관리자가 복제 모니터를 사용할 수 있도록 하려면 **sysadmin** 고정 서버 역할의 멤버가 사용자를 배포 데이터베이스에 추가 하 고 해당 사용자를 역할에 할당 해야 합니다 `replmonitor` .</span><span class="sxs-lookup"><span data-stu-id="5650a-118">To allow non-administrators to use Replication Monitor, a member of the **sysadmin** fixed server role must add the user to the distribution database and assign that user to the `replmonitor` role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5650a-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5650a-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a><span data-ttu-id="5650a-120">비관리자의 복제 모니터 사용을 허용하려면</span><span class="sxs-lookup"><span data-stu-id="5650a-120">To allow non-administrators to use Replication Monitor</span></span>  
  
1.  <span data-ttu-id="5650a-121">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 배포자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-121">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the Distributor, and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="5650a-122">**데이터베이스**, **시스템 데이터베이스**를 차례로 확장한 다음 배포 데이터베이스(기본적으로 이름이 **distribution** 으로 지정됨)를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-122">Expand **Databases**, expand **System Databases**, and then expand the distribution database (named **distribution** by default).</span></span>  
  
3.  <span data-ttu-id="5650a-123">**보안**을 확장하고 **사용자**를 마우스 오른쪽 단추로 클릭한 다음 **새 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-123">Expand **Security**, right-click **Users**, and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="5650a-124">해당 사용자의 사용자 이름과 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-124">Enter a user name and login for the user.</span></span>  
  
5.  <span data-ttu-id="5650a-125">의 기본 스키마를 선택 `replmonitor` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-125">Select a default schema of `replmonitor`.</span></span>  
  
6.  <span data-ttu-id="5650a-126">`replmonitor` **데이터베이스 역할 멤버 자격** 표에서 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-126">Select the `replmonitor` check box in the **Database role membership** grid.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5650a-127">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="5650a-127">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a><span data-ttu-id="5650a-128">replmonitor 고정 데이터베이스 역할에 사용자를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5650a-128">To add a user to the replmonitor fixed database role</span></span>  
  
1.  <span data-ttu-id="5650a-129">배포 데이터베이스의 배포자에서 [sp_helpuser&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-129">At the Distributor on the distribution database, execute [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql).</span></span> <span data-ttu-id="5650a-130">사용자가 결과 집합의에 나열 되어 있지 않은 경우 `UserName` [CREATE User &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql) 문을 사용 하 여 배포 데이터베이스에 대 한 액세스 권한을 사용자에 게 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-130">If the user is not listed in `UserName` in the result set, the user must be granted access to the distribution database using the [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) statement.</span></span>  
  
2.  <span data-ttu-id="5650a-131">배포 데이터베이스의 배포자에서 매개 변수의 값을 지정 하 여 [sp_helprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)를 실행 `replmonitor` **@rolename** 합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-131">At the Distributor on the distribution database, execute [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql), specifying a value of `replmonitor` for the **@rolename** parameter.</span></span> <span data-ttu-id="5650a-132">사용자가 결과 집합의에 나열 되어 있으면 `MemberName` 사용자가 이미이 역할에 속해 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-132">If the user is listed in `MemberName` in the result set, the user already belongs to this role.</span></span>  
  
3.  <span data-ttu-id="5650a-133">사용자가 역할에 속해 있지 않으면 `replmonitor` 배포 데이터베이스의 배포자에서 [transact-sql&#41;&#40;sp_addrolemember](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) 를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-133">If the user does not belong to the `replmonitor` role, execute [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="5650a-134">에 값을 지정 `replmonitor` **@rolename** 하 고에 추가할 데이터베이스 사용자 또는 Windows 로그인의 이름을 지정 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] **@membername** 합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-134">Specify a value of `replmonitor` for **@rolename** and the name of the database user or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows login being added for **@membername**.</span></span>  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a><span data-ttu-id="5650a-135">replmonitor 고정 데이터베이스 역할에서 사용자를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="5650a-135">To remove a user from the replmonitor fixed database role</span></span>  
  
1.  <span data-ttu-id="5650a-136">사용자가 역할에 속하는지 확인 하려면 `replmonitor` 배포 데이터베이스의 배포자에서 [transact-sql&#41;&#40;sp_helprolemember](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) 을 실행 하 고에 값을 지정 `replmonitor` **@rolename** 합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-136">To verify that the user belongs to the `replmonitor` role, execute [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) at the Distributor on the distribution database, and specify a value of `replmonitor` for **@rolename**.</span></span> <span data-ttu-id="5650a-137">사용자가 결과 집합의 `MemberName`에 나열되어 있지 않으면 해당 사용자는 현재 이 역할에 속해 있지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-137">If the user is not listed in `MemberName` in the result set, the user does not currently belong to this role.</span></span>  
  
2.  <span data-ttu-id="5650a-138">사용자가 역할에 속해 있는 경우 `replmonitor` 배포 데이터베이스의 배포자에서 [transact-sql&#41;&#40;sp_droprolemember](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) 를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-138">If the user does belong to the `replmonitor` role, execute [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="5650a-139">에 값을 지정 `replmonitor` **@rolename** 하 고에 대해 제거할 데이터베이스 사용자 또는 Windows 로그인의 이름을 지정 **@membername** 합니다.</span><span class="sxs-lookup"><span data-stu-id="5650a-139">Specify a value of `replmonitor` for **@rolename** and the name of the database user or the Windows login being removed for **@membername**.</span></span>  
  
  
