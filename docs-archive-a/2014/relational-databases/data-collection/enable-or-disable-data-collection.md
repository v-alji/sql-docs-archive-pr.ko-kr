---
title: 데이터 컬렉션 설정 또는 해제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collector [SQL Server], disabling
- data collector [SQL Server], enabling
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af5cc647a63d3a9451086fc9e2211dec809e88fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647701"
---
# <a name="enable-or-disable-data-collection"></a><span data-ttu-id="eb9ff-102">데이터 컬렉션 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="eb9ff-102">Enable or Disable Data Collection</span></span>
  <span data-ttu-id="eb9ff-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터 컬렉션을 사용하거나 사용하지 않도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-103">This topic describes how to enable or disable data collection in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="eb9ff-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="eb9ff-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eb9ff-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="eb9ff-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eb9ff-106">보안</span><span class="sxs-lookup"><span data-stu-id="eb9ff-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="eb9ff-107">**데이터 컬렉션을 사용하거나 사용하지 않도록 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="eb9ff-107">**To enable or disable data collection, using:**</span></span>  
  
     [<span data-ttu-id="eb9ff-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb9ff-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eb9ff-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb9ff-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eb9ff-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="eb9ff-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eb9ff-111">보안</span><span class="sxs-lookup"><span data-stu-id="eb9ff-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eb9ff-112">권한</span><span class="sxs-lookup"><span data-stu-id="eb9ff-112">Permissions</span></span>  
 <span data-ttu-id="eb9ff-113">이 프로시저를 실행하려면 **dc_admin** 또는 **dc_operator** (EXECUTE 권한 있음) 고정 데이터베이스 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-113">Requires membership in the **dc_admin** or **dc_operator** (with EXECUTE permission) fixed database role to execute this procedure.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eb9ff-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="eb9ff-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-the-data-collector"></a><span data-ttu-id="eb9ff-115">데이터 수집기를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="eb9ff-115">To enable the data collector</span></span>  
  
1.  <span data-ttu-id="eb9ff-116">개체 탐색기에서 **관리** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-116">In Object Explorer, expand the **Management** node.</span></span>  
  
2.  <span data-ttu-id="eb9ff-117">**데이터 컬렉션**을 마우스 오른쪽 단추로 클릭한 다음 **데이터 컬렉션 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-117">Right-click **Data Collection**, and then click **Enable Data Collection**.</span></span>  
  
#### <a name="to-disable-the-data-collector"></a><span data-ttu-id="eb9ff-118">데이터 수집기를 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="eb9ff-118">To disable the data collector</span></span>  
  
1.  <span data-ttu-id="eb9ff-119">개체 탐색기에서 **관리** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-119">In Object Explorer, expand the **Management** node.</span></span>  
  
2.  <span data-ttu-id="eb9ff-120">**데이터 컬렉션**을 마우스 오른쪽 단추로 클릭한 다음 **데이터 컬렉션 사용 안 함**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-120">Right-click **Data Collection**, and then click **Disable Data Collection**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eb9ff-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="eb9ff-121">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-the-data-collector"></a><span data-ttu-id="eb9ff-122">데이터 수집기를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="eb9ff-122">To enable the data collector</span></span>  
  
1.  <span data-ttu-id="eb9ff-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb9ff-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eb9ff-125">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-125">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="eb9ff-126">이 예제에서는 [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) 를 사용하여 데이터 수집기를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-126">This example uses [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) to enable the data collector.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### <a name="to-disable-the-data-collector"></a><span data-ttu-id="eb9ff-127">데이터 수집기를 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="eb9ff-127">To disable the data collector</span></span>  
  
1.  <span data-ttu-id="eb9ff-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb9ff-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eb9ff-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="eb9ff-131">이 예제에서는 [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) 를 사용하여 데이터 수집기를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb9ff-131">This example uses [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) to disable the data collector.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb9ff-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb9ff-132">See Also</span></span>  
 <span data-ttu-id="eb9ff-133">[데이터 컬렉션](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="eb9ff-133">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="eb9ff-134">시스템 저장 프로시저&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb9ff-134">System Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)  
  
  
