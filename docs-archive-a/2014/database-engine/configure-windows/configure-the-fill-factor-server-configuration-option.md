---
title: fill factor 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fill factor option [SQL Server]
ms.assetid: b920ec34-ba8b-4bb8-af53-a3ffd06bafa6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 02258c92b4a09277d371e605fd4729ba9fda3461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651900"
---
# <a name="configure-the-fill-factor-server-configuration-option"></a><span data-ttu-id="0e7f1-102">fill factor 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="0e7f1-102">Configure the fill factor Server Configuration Option</span></span>
  <span data-ttu-id="0e7f1-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 채우기 비율 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-103">This topic describes how to configure the **fill factor** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0e7f1-104">채우기 비율은 미세 조정 인덱스 데이터 스토리지와 성능을 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-104">Fill factor is provided for fine-tuning index data storage and performance.</span></span> <span data-ttu-id="0e7f1-105">인덱스를 만들거나 다시 작성할 때 채우기 비율에 따라 각 리프 수준 페이지에서 데이터로 채울 공간의 비율이 결정되므로 나머지 부분을 이후 인덱스 증가에 대비한 여유 공간으로 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-105">When an index is created or rebuilt, the fill-factor value determines the percentage of space on each leaf-level page to be filled with data, reserving the rest as free space for future growth.</span></span> <span data-ttu-id="0e7f1-106">자세한 내용은 [인덱스의 채우기 비율 지정](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-106">For more information, see [Specify Fill Factor for an Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).</span></span>  
  
 <span data-ttu-id="0e7f1-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0e7f1-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0e7f1-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="0e7f1-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0e7f1-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="0e7f1-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="0e7f1-110">보안</span><span class="sxs-lookup"><span data-stu-id="0e7f1-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0e7f1-111">**채우기 비율 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="0e7f1-111">**To configure the fill factor option, using:**</span></span>  
  
     [<span data-ttu-id="0e7f1-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0e7f1-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0e7f1-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0e7f1-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="0e7f1-114">**후속 작업:**  [채우기 비율 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="0e7f1-114">**Follow Up:**  [After you configure the fill factor option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0e7f1-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0e7f1-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0e7f1-116">권장 사항</span><span class="sxs-lookup"><span data-stu-id="0e7f1-116">Recommendations</span></span>  
  
-   <span data-ttu-id="0e7f1-117">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-117">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0e7f1-118">보안</span><span class="sxs-lookup"><span data-stu-id="0e7f1-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0e7f1-119">권한</span><span class="sxs-lookup"><span data-stu-id="0e7f1-119">Permissions</span></span>  
 <span data-ttu-id="0e7f1-120">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-120">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="0e7f1-121">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-121">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="0e7f1-122">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-122">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0e7f1-123">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="0e7f1-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-fill-factor-option"></a><span data-ttu-id="0e7f1-124">채우기 비율 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="0e7f1-124">To configure the fill factor option</span></span>  
  
1.  <span data-ttu-id="0e7f1-125">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-125">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="0e7f1-126">**데이터베이스 설정** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-126">Click the **Database Settings** node.</span></span>  
  
3.  <span data-ttu-id="0e7f1-127">**기본 인덱스 채우기 비율** 입력란에 원하는 인덱스 채우기 비율을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-127">In the **Default index fill factor** box, type or select the index fill factor that you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0e7f1-128">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="0e7f1-128">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-fill-factor-option"></a><span data-ttu-id="0e7f1-129">채우기 비율 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="0e7f1-129">To configure the fill factor option</span></span>  
  
1.  <span data-ttu-id="0e7f1-130">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-130">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0e7f1-131">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0e7f1-132">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-132">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0e7f1-133">다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `fill factor` 옵션의 값을 `100`(으)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-133">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `fill factor` option to `100`.</span></span>  
  
```sql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="0e7f1-134">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-134">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-fill-factor-option"></a><a name="FollowUp"></a> <span data-ttu-id="0e7f1-135">후속 작업: 채우기 비율 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="0e7f1-135">Follow Up: After you configure the fill factor option</span></span>  
 <span data-ttu-id="0e7f1-136">설정을 적용하려면 서버를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-136">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e7f1-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e7f1-137">See Also</span></span>  
 <span data-ttu-id="0e7f1-138">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e7f1-138">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="0e7f1-139">[ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e7f1-139">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="0e7f1-140">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e7f1-140">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="0e7f1-141">[인덱스의 채우기 비율 지정](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="0e7f1-141">[Specify Fill Factor for an Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) </span></span>  
 <span data-ttu-id="0e7f1-142">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e7f1-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="0e7f1-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0e7f1-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="0e7f1-144">sys.indexes&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e7f1-144">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
  
