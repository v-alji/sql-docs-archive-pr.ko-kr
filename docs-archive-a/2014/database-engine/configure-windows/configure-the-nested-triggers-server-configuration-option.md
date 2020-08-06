---
title: min memory per query 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- nested triggers option
ms.assetid: 29d7372b-d406-4a5b-80c6-a2d231d25211
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b27e185b0833f2e51be16393ff4d59a81046970
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652341"
---
# <a name="configure-the-nested-triggers-server-configuration-option"></a><span data-ttu-id="24d2a-102">nested triggers 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="24d2a-102">Configure the nested triggers Server Configuration Option</span></span>
  <span data-ttu-id="24d2a-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 중첩 트리거 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-103">This topic describes how to configure the **nested triggers** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="24d2a-104">**중첩 트리거** 옵션은 AFTER 트리거가 캐스케이드될 수 있는지 여부를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-104">The **nested triggers** option controls whether an AFTER trigger can cascade.</span></span> <span data-ttu-id="24d2a-105">즉 한 동작이 다른 트리거를 시작하고, 이 트리거가 또 다른 트리거를 시작하는 과정이 반복될 수 있는지 여부를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-105">That is, perform an action that initiates another trigger, which initiates another trigger, and so on.</span></span> <span data-ttu-id="24d2a-106">**nested triggers** 를 0으로 설정하면 AFTER 트리거를 중첩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-106">When **nested triggers** is set to 0, AFTER triggers cannot cascade.</span></span> <span data-ttu-id="24d2a-107">**nested triggers** 를 1(기본값)로 설정하면 AFTER 트리거를 32 수준까지 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-107">When **nested triggers** is set to 1 (the default), AFTER triggers can cascade to as many as 32 levels.</span></span> <span data-ttu-id="24d2a-108">INSTEAD OF 트리거는 이 옵션 설정에 관계없이 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-108">INSTEAD OF triggers can be nested regardless of the setting of this option.</span></span>  
  
 <span data-ttu-id="24d2a-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="24d2a-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="24d2a-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="24d2a-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="24d2a-111">보안</span><span class="sxs-lookup"><span data-stu-id="24d2a-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="24d2a-112">**중첩 트리거 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="24d2a-112">**To configure the nested triggers option, using:**</span></span>  
  
     [<span data-ttu-id="24d2a-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="24d2a-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="24d2a-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="24d2a-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="24d2a-115">**후속 작업:**  [중첩 트리거 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="24d2a-115">**Follow Up:**  [After you configure the nested triggers option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="24d2a-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="24d2a-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="24d2a-117">보안</span><span class="sxs-lookup"><span data-stu-id="24d2a-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="24d2a-118">권한</span><span class="sxs-lookup"><span data-stu-id="24d2a-118">Permissions</span></span>  
 <span data-ttu-id="24d2a-119">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-119">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="24d2a-120">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-120">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="24d2a-121">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-121">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="24d2a-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="24d2a-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-nested-triggers-option"></a><span data-ttu-id="24d2a-123">중첩 트리거 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="24d2a-123">To configure the nested triggers option</span></span>  
  
1.  <span data-ttu-id="24d2a-124">**개체 탐색기**에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-124">In **Object Explorer**, right-click a server, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="24d2a-125">**고급** 페이지에서 **다른 트리거를 발생시키는 트리거 허용** 옵션을 **True** (기본값) 또는 **False**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-125">On the **Advanced** page, set the **Allow Triggers to Fire Others** option to **True** (the default) or **False**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="24d2a-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="24d2a-126">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-nested-triggers-option"></a><span data-ttu-id="24d2a-127">중첩 트리거 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="24d2a-127">To configure the nested triggers option</span></span>  
  
1.  <span data-ttu-id="24d2a-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="24d2a-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="24d2a-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="24d2a-131">다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `nested triggers` 옵션의 값을 `0`(으)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-131">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `nested triggers` option to `0`.</span></span>  
  
```wmimof  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'nested triggers', 0 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="24d2a-132">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-132">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-nested-triggers-option"></a><a name="FollowUp"></a> <span data-ttu-id="24d2a-133">후속 작업: 중첩 트리거 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="24d2a-133">Follow Up: After you configure the nested triggers option</span></span>  
 <span data-ttu-id="24d2a-134">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d2a-134">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d2a-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24d2a-135">See Also</span></span>  
 <span data-ttu-id="24d2a-136">[중첩 트리거 만들기](../../relational-databases/triggers/create-nested-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="24d2a-136">[Create Nested Triggers](../../relational-databases/triggers/create-nested-triggers.md) </span></span>  
 <span data-ttu-id="24d2a-137">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="24d2a-137">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="24d2a-138">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="24d2a-138">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="24d2a-139">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="24d2a-139">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
