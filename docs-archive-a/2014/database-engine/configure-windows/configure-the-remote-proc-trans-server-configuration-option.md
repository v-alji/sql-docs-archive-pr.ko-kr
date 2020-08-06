---
title: remote proc trans 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote proc trans option
- distributed transactions [SQL Server], enforcing
ms.assetid: cfbc6158-ab96-44b4-87eb-ea278c1b0c6b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54fcaafa51eef33acb1ae8d1e2f36022840b76a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649165"
---
# <a name="configure-the-remote-proc-trans-server-configuration-option"></a><span data-ttu-id="1ceb7-102">remote proc trans 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="1ceb7-102">Configure the remote proc trans Server Configuration Option</span></span>
  <span data-ttu-id="1ceb7-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 원격 프로시저 트랜잭션 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-103">This topic describes how to configure the **remote proc trans** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1ceb7-104">**remote proc trans** 옵션을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MS DTC(Distributed Transaction Coordinator) 트랜잭션을 통한 서버 간 프로시저 동작을 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-104">The **remote proc trans** option helps protect the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span>  
  
 <span data-ttu-id="1ceb7-105">**remote proc trans** 값을 1로 설정하면 트랜잭션의 ACID(원자성, 일관성, 격리성 및 내구성) 속성이 보호되는 MS DTC 통합 분산 트랜잭션을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-105">Set the value of **remote proc trans** to 1 to provide an MS DTC-coordinated distributed transaction that protects the ACID (atomic, consistent, isolated, and durable) properties of transactions.</span></span> <span data-ttu-id="1ceb7-106">이 옵션을 1로 설정한 후에 세션을 시작하면 이 구성 설정이 기본값으로 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-106">Sessions begun after setting this option to 1 inherit the configuration setting as their default.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
 <span data-ttu-id="1ceb7-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1ceb7-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1ceb7-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1ceb7-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1ceb7-109">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="1ceb7-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="1ceb7-110">권장 사항</span><span class="sxs-lookup"><span data-stu-id="1ceb7-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="1ceb7-111">보안</span><span class="sxs-lookup"><span data-stu-id="1ceb7-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1ceb7-112">**원격 프로시저 트랜잭션 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="1ceb7-112">**To configure the remote proc trans option, using:**</span></span>  
  
     [<span data-ttu-id="1ceb7-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1ceb7-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1ceb7-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1ceb7-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="1ceb7-115">**후속 작업:**  [원격 프로시저 트랜잭션 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="1ceb7-115">**Follow Up:**  [After you configure the remote proc trans option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1ceb7-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1ceb7-116">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="1ceb7-117">필수 조건</span><span class="sxs-lookup"><span data-stu-id="1ceb7-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="1ceb7-118">이 값을 설정하려면 먼저 원격 서버 연결이 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-118">Remote server connections must be allowed before this value can be set.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1ceb7-119">권장 사항</span><span class="sxs-lookup"><span data-stu-id="1ceb7-119">Recommendations</span></span>  
  
-   <span data-ttu-id="1ceb7-120">이 옵션은 원격 저장 프로시저를 사용하는 애플리케이션에 대해 이전 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전과의 호환성을 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-120">This option is provided for compatibility with earlier versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for applications that use remote stored procedures.</span></span> <span data-ttu-id="1ceb7-121">원격 저장 프로시저 호출을 실행하는 대신 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)를 사용하여 정의되는 연결된 서버를 참조하는 분산 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-121">Instead of issuing remote stored procedure calls, use distributed queries that reference linked servers, which are defined by using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1ceb7-122">보안</span><span class="sxs-lookup"><span data-stu-id="1ceb7-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1ceb7-123">권한</span><span class="sxs-lookup"><span data-stu-id="1ceb7-123">Permissions</span></span>  
 <span data-ttu-id="1ceb7-124">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="1ceb7-125">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="1ceb7-126">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1ceb7-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1ceb7-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a><span data-ttu-id="1ceb7-128">원격 프로시저 트랜잭션 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="1ceb7-128">To configure the remote proc trans option</span></span>  
  
1.  <span data-ttu-id="1ceb7-129">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="1ceb7-130">**연결** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-130">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="1ceb7-131">**원격 서버 연결**에서 **서버 간 통신에 분산 트랜잭션 필요** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-131">Under **Remote server connections**, select the **Require Distributed Transactions for server to server communication** check box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1ceb7-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1ceb7-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a><span data-ttu-id="1ceb7-133">원격 프로시저 트랜잭션 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="1ceb7-133">To configure the remote proc trans option</span></span>  
  
1.  <span data-ttu-id="1ceb7-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1ceb7-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1ceb7-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1ceb7-137">다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `remote proc trans` 옵션의 값을 `1`(으)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote proc trans` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote proc trans', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="1ceb7-138">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-proc-trans-option"></a><a name="FollowUp"></a> <span data-ttu-id="1ceb7-139">후속 작업: 원격 프로시저 트랜잭션 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="1ceb7-139">Follow Up: After you configure the remote proc trans option</span></span>  
 <span data-ttu-id="1ceb7-140">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ceb7-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ceb7-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ceb7-141">See Also</span></span>  
 <span data-ttu-id="1ceb7-142">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1ceb7-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="1ceb7-143">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1ceb7-143">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="1ceb7-144">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1ceb7-144">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
