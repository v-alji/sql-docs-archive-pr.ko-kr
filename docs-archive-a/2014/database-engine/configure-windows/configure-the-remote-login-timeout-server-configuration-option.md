---
title: remote login timeout 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote login timeout option
ms.assetid: 077adebe-0e3f-42a5-a75e-5e6d04847e2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58b3405f9b0e51bd43edcaa31e84c8ebbcc48547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647227"
---
# <a name="configure-the-remote-login-timeout-server-configuration-option"></a><span data-ttu-id="93285-102">remote login timeout 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="93285-102">Configure the remote login timeout Server Configuration Option</span></span>
  <span data-ttu-id="93285-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 원격 로그인 제한 시간 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-103">This topic describes how to configure the **remote login timeout** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="93285-104">**원격 로그인 제한 시간** 옵션은 원격 서버에 대한 로그인에 실패하여 원래 상태로 되돌아오기까지 기다리는 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-104">The **remote login timeout** option specifies the number of seconds to wait before returning from a failed attempt to log in to a remote server.</span></span> <span data-ttu-id="93285-105">예를 들어 원격 서버에 로그인을 시도하고 있는데 해당 서버가 다운된 경우 **원격 로그인 제한 시간** 을 사용하면 컴퓨터가 로그인 시도를 중단할 때까지 무한정 기다리지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93285-105">For example, if you are trying to log in to a remote server and that server is down, **remote login timeout** helps make sure that you do not have to wait indefinitely before your computer stops trying to log in.</span></span> <span data-ttu-id="93285-106">이 옵션의 기본값은 10초입니다.</span><span class="sxs-lookup"><span data-stu-id="93285-106">The default value for this option is 10 seconds.</span></span> <span data-ttu-id="93285-107">값을 0으로 설정하면 무한정 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93285-107">A value of 0 allows for an infinite wait.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93285-108">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서 이 옵션의 기본값은 20초입니다.</span><span class="sxs-lookup"><span data-stu-id="93285-108">The default value for this option is 20 seconds in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="93285-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="93285-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="93285-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="93285-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="93285-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="93285-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="93285-112">보안</span><span class="sxs-lookup"><span data-stu-id="93285-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="93285-113">**원격 로그인 제한 시간 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="93285-113">**To configure the remote login timeout option, using:**</span></span>  
  
     [<span data-ttu-id="93285-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="93285-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="93285-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="93285-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="93285-116">**후속 작업:**  [원격 로그인 제한 시간 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="93285-116">**Follow Up:**  [After you configure the remote login timeout option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="93285-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="93285-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="93285-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="93285-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="93285-119">**원격 로그인 제한 시간** 옵션은 유형이 다른 쿼리를 위해 만든 OLE DB Provider에 대한 연결에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="93285-119">The **remote login timeout** option affects connections to OLE DB providers made for heterogeneous queries.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="93285-120">보안</span><span class="sxs-lookup"><span data-stu-id="93285-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="93285-121">권한</span><span class="sxs-lookup"><span data-stu-id="93285-121">Permissions</span></span>  
 <span data-ttu-id="93285-122">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="93285-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="93285-123">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="93285-124">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93285-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="93285-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="93285-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a><span data-ttu-id="93285-126">원격 로그인 제한 시간 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="93285-126">To configure the remote login timeout option</span></span>  
  
1.  <span data-ttu-id="93285-127">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="93285-128">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-128">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="93285-129">**네트워크**아래에서 **원격 로그인 제한 시간** 상자의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-129">Under **Network**, select a value for the **Remote Login Timeout** box.</span></span>  
  
     <span data-ttu-id="93285-130">**원격 로그인 제한 시간** 옵션을 사용하여 원격 로그인에 실패하여 원래 상태로 되돌아오기까지 기다리는 시간(초)을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93285-130">Use the **remote login timeout** option to specify the number of seconds to wait before returning from a failed remote login attempt.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="93285-131">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="93285-131">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a><span data-ttu-id="93285-132">원격 로그인 제한 시간 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="93285-132">To configure the remote login timeout option</span></span>  
  
1.  <span data-ttu-id="93285-133">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="93285-134">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="93285-135">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="93285-136">이 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `remote login timeout` 옵션 값을 `35` 초로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="93285-136">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote login timeout` option to `35` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote login timeout', 35 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="93285-137">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="93285-137">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-login-timeout-option"></a><a name="FollowUp"></a> <span data-ttu-id="93285-138">후속 작업: 원격 로그인 제한 시간 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="93285-138">Follow Up: After you configure the remote login timeout option</span></span>  
 <span data-ttu-id="93285-139">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="93285-139">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93285-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93285-140">See Also</span></span>  
 <span data-ttu-id="93285-141">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="93285-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="93285-142">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="93285-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="93285-143">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93285-143">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
