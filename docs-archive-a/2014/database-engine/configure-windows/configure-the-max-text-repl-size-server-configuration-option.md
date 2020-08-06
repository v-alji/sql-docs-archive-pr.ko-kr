---
title: max text repl size 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- max text repl size option
ms.assetid: 3056cf64-621d-4996-9162-3913f6bc6d5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af0cf426583ee328f0a484de1c3539836c0d8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652339"
---
# <a name="configure-the-max-text-repl-size-server-configuration-option"></a><span data-ttu-id="78e9f-102">max text repl size 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="78e9f-102">Configure the max text repl size Server Configuration Option</span></span>
  <span data-ttu-id="78e9f-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 최대 텍스트 복제 크기 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-103">This topic describes how to configure the **max text repl size** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="78e9f-104">**Max text repl size** 옵션은 `text` `ntext` `varchar(max)` `nvarchar(max)` `varbinary(max)` `xml` `image` 단일 INSERT, UPDATE, WRITETEXT 또는 UPDATETEXT 문에서 복제 된 열 또는 캡처된 열에 추가할 수 있는,,,,, 및 데이터의 최대 크기 (바이트)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-104">The **max text repl size** option specifies the maximum size (in bytes) of `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, `xml`, and `image` data that can be added to a replicated column or captured column in a single INSERT, UPDATE, WRITETEXT, or UPDATETEXT statement.</span></span> <span data-ttu-id="78e9f-105">기본값은 65536바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-105">The default value is 65536 bytes.</span></span> <span data-ttu-id="78e9f-106">값이 -1이면 데이터 형식에서 요구하는 한도 이외의 크기 제한이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-106">A value of -1 indicates that there is no size limit, other than the limit imposed by the data type.</span></span>  
  
 <span data-ttu-id="78e9f-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="78e9f-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="78e9f-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="78e9f-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="78e9f-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="78e9f-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="78e9f-110">보안</span><span class="sxs-lookup"><span data-stu-id="78e9f-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="78e9f-111">**최대 텍스트 복제 크기 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="78e9f-111">**To configure the max text repl size option, using:**</span></span>  
  
     [<span data-ttu-id="78e9f-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="78e9f-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="78e9f-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="78e9f-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="78e9f-114">**후속 작업:**  [최대 텍스트 복제 크기 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="78e9f-114">**Follow Up:**  [After you configure the max text repl size option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="78e9f-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="78e9f-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="78e9f-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="78e9f-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="78e9f-117">이 옵션은 트랜잭션 복제와 변경 데이터 캡처에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-117">This option applies to transactional replication and Change Data Capture.</span></span> <span data-ttu-id="78e9f-118">서버에 트랜잭션 복제 및 변경 데이터 캡처가 모두 구성되어 있는 경우 지정한 값이 두 기능에 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-118">When a server is configured for both transactional replication and Change Data Capture, the specified value applies to both features.</span></span> <span data-ttu-id="78e9f-119">이 옵션은 스냅샷 복제 및 병합 복제에서는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-119">This option is ignored by snapshot replication and merge replication.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="78e9f-120">보안</span><span class="sxs-lookup"><span data-stu-id="78e9f-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="78e9f-121">권한</span><span class="sxs-lookup"><span data-stu-id="78e9f-121">Permissions</span></span>  
 <span data-ttu-id="78e9f-122">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="78e9f-123">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="78e9f-124">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="78e9f-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="78e9f-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a><span data-ttu-id="78e9f-126">최대 텍스트 복제 크기 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="78e9f-126">To configure the max text repl size option</span></span>  
  
1.  <span data-ttu-id="78e9f-127">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="78e9f-128">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-128">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="78e9f-129">**기타**에서 **최대 텍스트 복제 크기** 옵션을 원하는 값으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-129">Under **Miscellaneous**, change the **Max Text Replication Size** option to the desired value.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="78e9f-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="78e9f-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a><span data-ttu-id="78e9f-131">최대 텍스트 복제 크기 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="78e9f-131">To configure the max text repl size option</span></span>  
  
1.  <span data-ttu-id="78e9f-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="78e9f-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="78e9f-134">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="78e9f-135">이 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `max text repl size` 옵션을 `-1`으로 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-135">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max text repl size` option to `-1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;   
RECONFIGURE ;   
GO  
EXEC sp_configure 'max text repl size', -1 ;   
GO  
RECONFIGURE;   
GO  
  
```  
  
 <span data-ttu-id="78e9f-136">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-136">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-text-repl-size-option"></a><a name="FollowUp"></a> <span data-ttu-id="78e9f-137">후속 작업: 최대 텍스트 복제 크기 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="78e9f-137">Follow Up: After you configure the max text repl size option</span></span>  
 <span data-ttu-id="78e9f-138">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="78e9f-138">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e9f-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78e9f-139">See Also</span></span>  
 <span data-ttu-id="78e9f-140">[SQL Server 복제](../../relational-databases/replication/sql-server-replication.md) </span><span class="sxs-lookup"><span data-stu-id="78e9f-140">[SQL Server Replication](../../relational-databases/replication/sql-server-replication.md) </span></span>  
 <span data-ttu-id="78e9f-141">[INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="78e9f-141">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="78e9f-142">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="78e9f-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="78e9f-143">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="78e9f-143">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="78e9f-144">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="78e9f-144">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="78e9f-145">[UPDATE&#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="78e9f-145">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span></span>  
 <span data-ttu-id="78e9f-146">[UPDATETEXT&#40;Transact-SQL&#41;](/sql/t-sql/queries/updatetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="78e9f-146">[UPDATETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/updatetext-transact-sql) </span></span>  
 [<span data-ttu-id="78e9f-147">WRITETEXT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="78e9f-147">WRITETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/writetext-transact-sql)  
  
  
