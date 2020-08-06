---
title: 컬렉션 집합 시작 또는 중지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection sets [SQL Server], stopping
- collection sets [SQL Server], starting
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e37d4b2edcd7a6e048c405b072bcbf9b1fef78c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659487"
---
# <a name="start-or-stop-a-collection-set"></a><span data-ttu-id="8a6e1-102">컬렉션 집합 시작 또는 중지</span><span class="sxs-lookup"><span data-stu-id="8a6e1-102">Start or Stop a Collection Set</span></span>
  <span data-ttu-id="8a6e1-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 컬렉션 집합을 시작 또는 중지하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-103">This topic describes how to start or stop a collection set in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8a6e1-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="8a6e1-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8a6e1-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="8a6e1-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8a6e1-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8a6e1-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8a6e1-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="8a6e1-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="8a6e1-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="8a6e1-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="8a6e1-109">보안</span><span class="sxs-lookup"><span data-stu-id="8a6e1-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8a6e1-110">**다음을 사용하여 컬렉션 집합을 시작하거나 중지합니다.**</span><span class="sxs-lookup"><span data-stu-id="8a6e1-110">**To start or stop a collection set, using:**</span></span>  
  
     [<span data-ttu-id="8a6e1-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8a6e1-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8a6e1-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8a6e1-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8a6e1-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8a6e1-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8a6e1-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8a6e1-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8a6e1-115">데이터 수집기 저장 프로시저와 카탈로그 뷰는 **msdb** 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-115">Data Collector stored procedures and catalog views are stored in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="8a6e1-116">일반적인 저장 프로시저와 달리 데이터 수집기 저장 프로시저에 대한 매개 변수는 형식이 엄격하게 지정되어 있으며 데이터 형식 자동 변환을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-116">Unlike regular stored procedures, the parameters for data collector stored procedures are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="8a6e1-117">이러한 매개 변수를 인수 설명에 지정된 올바른 입력 매개 변수 데이터 형식으로 호출하지 않으면 저장 프로시저가 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-117">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="8a6e1-118">필수 조건</span><span class="sxs-lookup"><span data-stu-id="8a6e1-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="8a6e1-119">SQL Server 에이전트가 시작되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-119">SQL Server Agent must be started.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="8a6e1-120">권장 사항</span><span class="sxs-lookup"><span data-stu-id="8a6e1-120">Recommendations</span></span>  
  
-   <span data-ttu-id="8a6e1-121">컬렉션 집합에 대한 정보를 얻으려면 [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) 카탈로그 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-121">To obtain information about collection sets, query the [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) catalog view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8a6e1-122">보안</span><span class="sxs-lookup"><span data-stu-id="8a6e1-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8a6e1-123">권한</span><span class="sxs-lookup"><span data-stu-id="8a6e1-123">Permissions</span></span>  
 <span data-ttu-id="8a6e1-124">**dc_operator** 고정 데이터베이스 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-124">Requires membership in the **dc_operator** fixed database role.</span></span> <span data-ttu-id="8a6e1-125">컬렉션 집합에 프록시 계정이 없는 경우에는 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다. 예</span><span class="sxs-lookup"><span data-stu-id="8a6e1-125">If the collection set does not have a proxy account, membership in the **sysadmin** fixed server role is required.Examples</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8a6e1-126">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="8a6e1-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-start-a-collection-set"></a><span data-ttu-id="8a6e1-127">컬렉션 집합을 시작하려면</span><span class="sxs-lookup"><span data-stu-id="8a6e1-127">To start a collection set</span></span>  
  
1.  <span data-ttu-id="8a6e1-128">개체 탐색기에서 **관리** 노드, **데이터 컬렉션**, **시스템 데이터 컬렉션 집합**을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-128">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="8a6e1-129">시작할 컬렉션 집합을 마우스 오른쪽 단추로 클릭한 다음 **데이터 컬렉션 집합 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-129">Right-click the collection set that you want to start, and then click **Start Data Collection Set**.</span></span>  
  
     <span data-ttu-id="8a6e1-130">메시지 상자에 이 동작의 결과가 표시되며, 컬렉션 집합의 아이콘에 초록색 화살표가 표시되어 컬렉션 집합이 시작되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-130">A message box displays the results of this action, and a green arrow on the icon for the collection set indicates that the collection set has started.</span></span>  
  
#### <a name="to-stop-a-collection-set"></a><span data-ttu-id="8a6e1-131">컬렉션 집합을 중지하려면</span><span class="sxs-lookup"><span data-stu-id="8a6e1-131">To stop a collection set</span></span>  
  
1.  <span data-ttu-id="8a6e1-132">개체 탐색기에서 **관리** 노드, **데이터 컬렉션**, **시스템 데이터 컬렉션 집합**을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-132">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="8a6e1-133">중지할 컬렉션 집합을 마우스 오른쪽 단추로 클릭한 다음 **데이터 컬렉션 집합 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-133">Right-click the collection set that you want to stop, and then click **Stop Data Collection Set**.</span></span>  
  
     <span data-ttu-id="8a6e1-134">메시지 상자에 이 동작의 결과가 표시되며, 컬렉션 집합의 아이콘에 빨간색 원이 표시되어 컬렉션 집합이 중지되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-134">A message box displays the results of this action, and a red circle on the icon for the collection set indicates that the collection set has stopped.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8a6e1-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="8a6e1-135">Using Transact-SQL</span></span>  
  
#### <a name="to-start-a-collection-set"></a><span data-ttu-id="8a6e1-136">컬렉션 집합을 시작하려면</span><span class="sxs-lookup"><span data-stu-id="8a6e1-136">To start a collection set</span></span>  
  
1.  <span data-ttu-id="8a6e1-137">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8a6e1-138">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8a6e1-139">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="8a6e1-140">이 예제에서는 [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) 를 사용하여 ID가 `1`인 컬렉션 집합을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-140">This example uses [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) to start the collection set that has the ID of `1`.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### <a name="to-stop-a-collection-set"></a><span data-ttu-id="8a6e1-141">컬렉션 집합을 중지하려면</span><span class="sxs-lookup"><span data-stu-id="8a6e1-141">To stop a collection set</span></span>  
  
1.  <span data-ttu-id="8a6e1-142">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-142">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8a6e1-143">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-143">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8a6e1-144">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-144">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="8a6e1-145">이 예제에서는 [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) 를 사용하여 ID가 `1`인 컬렉션 집합을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-145">This example uses [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) to stop the collection set that has the ID of `1`.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a6e1-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a6e1-146">See Also</span></span>  
 <span data-ttu-id="8a6e1-147">[데이터 수집기 뷰&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a6e1-147">[Data Collector Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql) </span></span>  
 [<span data-ttu-id="8a6e1-148">데이터 컬렉션</span><span class="sxs-lookup"><span data-stu-id="8a6e1-148">Data Collection</span></span>](data-collection.md)  
  
  
