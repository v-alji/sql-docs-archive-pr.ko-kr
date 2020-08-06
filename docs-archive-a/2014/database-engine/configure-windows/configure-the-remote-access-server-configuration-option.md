---
title: remote access 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], stored procedure execution
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eef18ec48ede59544b13545e49dc105909cfac16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647230"
---
# <a name="configure-the-remote-access-server-configuration-option"></a><span data-ttu-id="bcaab-102">remote access 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="bcaab-102">Configure the remote access Server Configuration Option</span></span>
  <span data-ttu-id="bcaab-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote access [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-103">This topic describes how to configure the **remote access** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="bcaab-104">**remote access** 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 실행되고 있는 로컬 또는 원격 서버에서 저장 프로시저 실행을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-104">The **remote access** option controls the execution of stored procedures from local or remote servers on which instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are running.</span></span> <span data-ttu-id="bcaab-105">이 옵션의 기본값은 1이며</span><span class="sxs-lookup"><span data-stu-id="bcaab-105">This default value for this option is 1.</span></span> <span data-ttu-id="bcaab-106">원격 서버에서 로컬 저장 프로시저를 실행하거나 로컬 서버에서 원격 저장 프로시저를 실행할 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-106">This grants permission to run local stored procedures from remote servers or remote stored procedures from the local server.</span></span> <span data-ttu-id="bcaab-107">원격 서버에서 로컬 저장 프로시저를 실행할 수 없거나 로컬 서버에서 원격 저장 프로시저를 실행할 수 없게 하려면 옵션을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-107">To prevent local stored procedures from being run from a remote server or remote stored procedures from being run on the local server, set the option to 0.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]<span data-ttu-id="bcaab-108">[sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)를 대신 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="bcaab-108">Use [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) instead.</span></span>  
  
 <span data-ttu-id="bcaab-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="bcaab-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bcaab-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="bcaab-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bcaab-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="bcaab-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="bcaab-112">보안</span><span class="sxs-lookup"><span data-stu-id="bcaab-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bcaab-113">**remote access 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="bcaab-113">**To configure the remote access option, using:**</span></span>  
  
     [<span data-ttu-id="bcaab-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bcaab-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bcaab-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bcaab-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="bcaab-116">**후속 작업:**  [remote access 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="bcaab-116">**Follow Up:**  [After you configure the remote access option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bcaab-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="bcaab-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bcaab-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="bcaab-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="bcaab-119">**remote access** 옵션은 [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)를 사용하여 추가한 서버에만 적용되며 이전 버전과의 호환성을 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-119">The **remote access** option only applies to servers that are added by using [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), and is included for backward compatibility.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bcaab-120">보안</span><span class="sxs-lookup"><span data-stu-id="bcaab-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bcaab-121">권한</span><span class="sxs-lookup"><span data-stu-id="bcaab-121">Permissions</span></span>  
 <span data-ttu-id="bcaab-122">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="bcaab-123">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="bcaab-124">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bcaab-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="bcaab-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-access-option"></a><span data-ttu-id="bcaab-126">remote access 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="bcaab-126">To configure the remote access option</span></span>  
  
1.  <span data-ttu-id="bcaab-127">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="bcaab-128">**연결** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-128">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="bcaab-129">**원격 서버 연결**에서 **이 서버에 대한 원격 연결 허용** 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-129">Under **Remote server connections**, select or clear the **Allow remote connections to this server** check box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bcaab-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="bcaab-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-access-option"></a><span data-ttu-id="bcaab-131">remote access 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="bcaab-131">To configure the remote access option</span></span>  
  
1.  <span data-ttu-id="bcaab-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bcaab-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bcaab-134">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="bcaab-135">다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `remote access` 옵션의 값을 `0`(으)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-135">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote access` option to `0`.</span></span>  
  
```sql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="bcaab-136">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-136">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-access-option"></a><a name="FollowUp"></a> <span data-ttu-id="bcaab-137">후속 작업: remote access 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="bcaab-137">Follow Up: After you configure the remote access option</span></span>  
 <span data-ttu-id="bcaab-138">이 설정은 SQL Server를 다시 시작할 때까지 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bcaab-138">This setting does not take effect until you restart SQL Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcaab-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bcaab-139">See Also</span></span>  
 <span data-ttu-id="bcaab-140">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bcaab-140">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="bcaab-141">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bcaab-141">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="bcaab-142">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bcaab-142">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
