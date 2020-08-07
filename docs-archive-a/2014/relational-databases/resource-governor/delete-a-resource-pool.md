---
title: 리소스 풀 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a67b0e2262fa3007597091b6087cc937bb0f3276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731479"
---
# <a name="delete-a-resource-pool"></a><span data-ttu-id="4a903-102">리소스 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="4a903-102">Delete a Resource Pool</span></span>
  <span data-ttu-id="4a903-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 Transact-SQL을 사용하여 리소스 풀을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-103">You can delete a resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="4a903-104">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="4a903-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="4a903-105">**리소스 풀을 삭제하려면 다음을 사용합니다.** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="4a903-105">**To delete a resource pool, using:** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4a903-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4a903-106">Before You Begin</span></span>  
 <span data-ttu-id="4a903-107">작업 그룹이 들어 있는 리소스 풀은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-107">You cannot delete a resource pool if it contains workload groups.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="4a903-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4a903-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="4a903-109">리소스 관리자 기본 풀 또는 내부 리소스 풀을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-109">You cannot delete the Resource Governor default or internal resource pools.</span></span> <span data-ttu-id="4a903-110">작업 그룹이 들어 있는 리소스 풀은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-110">You cannot delete a resource pool if it contains workload groups.</span></span> <span data-ttu-id="4a903-111">자세한 내용은 [Delete a Workload Group](delete-a-workload-group.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a903-111">For more information, see [Delete a Workload Group](delete-a-workload-group.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4a903-112">권한</span><span class="sxs-lookup"><span data-stu-id="4a903-112">Permissions</span></span>  
 <span data-ttu-id="4a903-113">리소스 풀을 삭제하려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-113">Deleting a resource pool requires CONTROL SERVER permission.</span></span>  
  
##  <a name="delete-a-resource-pool-using-object-explorer"></a><a name="DelRPSSMS"></a> <span data-ttu-id="4a903-114">개체 탐색기를 사용하여 리소스 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="4a903-114">Delete a Resource Pool Using Object Explorer</span></span>  
 <span data-ttu-id="4a903-115">**SQL Server Management Studio를 사용하여 리소스 풀을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="4a903-115">**To delete a resource pool by using SQL Server Management Studio**</span></span>  
  
1.  <span data-ttu-id="4a903-116">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **리소스 관리자** 가 나타날 때까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-116">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="4a903-117">삭제할 리소스 풀을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-117">Right-click the resource pool to be deleted, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="4a903-118">**개체 삭제** 창의 **삭제할 개체** 목록에 리소스 풀이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-118">In the **Delete Object** window, the resource pool is listed in the **Object to be deleted** list.</span></span> <span data-ttu-id="4a903-119">리소스 풀을 삭제하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-119">To delete the resource pool, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a903-120">삭제하려고 하는 리소스 풀에 작업 그룹이 들어 있으면 해당 리소스 풀을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-120">If the resource pool that you are trying to delete contains a workload group, this action will fail.</span></span>  
  
##  <a name="delete-a-resource-pool-using-transact-sql"></a><a name="DelRPTSQL"></a> <span data-ttu-id="4a903-121">Transact-SQL을 사용하여 리소스 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="4a903-121">Delete a Resource Pool Using Transact-SQL</span></span>  
 <span data-ttu-id="4a903-122">**Transact-SQL을 사용하여 리소스 풀을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="4a903-122">**To delete a resource pool by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="4a903-123">삭제할 리소스의 이름을 지정하는 `DROP RESOURCE POOL` 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-123">Run the `DROP RESOURCE POOL` statement specifying the name of the resource pool to delete.</span></span>  
  
2.  <span data-ttu-id="4a903-124">**ALTER RESOURCE GOVERNOR RECONFIGURE** 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-124">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="4a903-125">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4a903-125">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="4a903-126">다음 예에서는 `poolAdhoc`이라는 작업 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4a903-126">The following example drops a workload group named `poolAdhoc`.</span></span>  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a903-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a903-127">See Also</span></span>  
 <span data-ttu-id="4a903-128">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="4a903-128">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="4a903-129">[리소스 관리자 리소스 풀](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="4a903-129">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="4a903-130">[리소스 풀 만들기](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="4a903-130">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="4a903-131">[리소스 풀 설정 변경](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="4a903-131">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="4a903-132">[리소스 관리자 작업 그룹](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="4a903-132">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="4a903-133">[리소스 관리자 분류자 함수](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="4a903-133">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="4a903-134">[DROP WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4a903-134">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="4a903-135">[DROP RESOURCE POOL&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4a903-135">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="4a903-136">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4a903-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
