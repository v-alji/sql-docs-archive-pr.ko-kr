---
title: 작업 그룹 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], delete
- Resource Governor, workload group delete
ms.assetid: d5902c46-5c28-4ac1-8b56-cb4ca2b072d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 801a731db6c5b31bc479d1a3f6079c45ad9a7c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731487"
---
# <a name="delete-a-workload-group"></a><span data-ttu-id="68832-102">작업 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="68832-102">Delete a Workload Group</span></span>
  <span data-ttu-id="68832-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 Transact-SQL을 사용하여 작업 그룹 또는 리소스 풀을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68832-103">You can delete a workload group or resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="68832-104">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="68832-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="68832-105">**작업 그룹을 삭제하려면 다음을 사용합니다.**  [개체 탐색기](#DelWGObjEx), [Resource Governor 속성](#DelWGRGProp) 또는 [Transact-SQL](#DelWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="68832-105">**To delete a workload group, using:**  [Object Explorer](#DelWGObjEx), [Resource Governor Properties](#DelWGRGProp), [Transact-SQL](#DelWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="68832-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="68832-106">Before You Begin</span></span>  
 <span data-ttu-id="68832-107">활성 세션이 들어 있는 작업 그룹은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68832-107">You cannot delete a workload group if it contains active sessions.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="68832-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="68832-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="68832-109">작업 그룹에 활성 세션이 있으면 변경 내용을 적용하기 위해 ALTER RESOURCE GOVERNOR RECONFIGURE 문이 호출될 경우 작업 그룹을 삭제하거나 다른 리소스 풀에 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68832-109">If a workload group contains active sessions, deleting or moving the workload group to a different resource pool will fail when the ALTER RESOURCE GOVERNOR RECONFIGURE statement is called to apply the change.</span></span> <span data-ttu-id="68832-110">다음 동작 중 하나를 수행하여 이 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68832-110">To avoid this problem, you can take one of the following actions:</span></span>  
  
-   <span data-ttu-id="68832-111">적용된 그룹에서 모든 세션의 연결이 끊어질 때까지 기다린 후 ALTER RESOURCE GOVERNOR RECONFIGURE 문을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-111">Wait until all the sessions from the affected group have disconnected, and then rerun the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
-   <span data-ttu-id="68832-112">KILL 명령을 사용하여 적용된 그룹의 세션을 명시적으로 중지한 후 ALTER RESOURCE GOVERNOR RECONFIGURE 문을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-112">Explicitly stop sessions in the affected group by using the KILL command, and then rerun the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span> <span data-ttu-id="68832-113">**삭제** 를 사용한 후 활성 세션을 중지하기 전에 세션을 명시적으로 중지하지 않으려는 경우 원래 이름을 사용하여 그룹을 다시 만든 다음 이 그룹을 원래 리소스 풀로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-113">If you decide that you do not want to explicitly stop sessions after you use **Delete** but before you stop active sessions, re-create the group by using the original name and move the group to the original resource pool.</span></span>  
  
-   <span data-ttu-id="68832-114">서버를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-114">Restart the server.</span></span> <span data-ttu-id="68832-115">다시 시작 프로세스가 완료되면 삭제한 그룹은 생성되지 않고 이동한 그룹은 새 리소스 풀 할당을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-115">After the restart process is completed, the deleted group will not be created, and a moved group will use the new resource pool assignment.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="68832-116">권한</span><span class="sxs-lookup"><span data-stu-id="68832-116">Permissions</span></span>  
 <span data-ttu-id="68832-117">작업 그룹을 삭제하려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-117">Deleting a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="delete-a-workload-group-using-object-explorer"></a><a name="DelWGObjEx"></a> <span data-ttu-id="68832-118">개체 탐색기를 사용하여 작업 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="68832-118">Delete a Workload Group Using Object Explorer</span></span>  
 <span data-ttu-id="68832-119">**개체 탐색기를 사용하여 작업 그룹을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="68832-119">**To delete a workload group by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="68832-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **리소스 풀** 이 나타날 때까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-120">In[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="68832-121">삭제할 작업 그룹이 포함된 리소스 풀의 **작업 그룹** 노드가 나타날 때까지 **리소스 풀** 을 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-121">Recursively expand **Resource Pools** down to and including the **Workload Groups** node in the resource pool that contains the workload group to be deleted.</span></span>  
  
3.  <span data-ttu-id="68832-122">작업 그룹을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-122">Right-click the workload group, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="68832-123">**개체 삭제** 창의 **삭제할 개체** 목록에 작업 그룹이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="68832-123">In the **Delete Object** window, the workload group is listed in the **Object to be deleted** list.</span></span> <span data-ttu-id="68832-124">작업 그룹을 삭제하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-124">To delete the workload group, click **OK**.</span></span>  
  
##  <a name="delete-a-workload-group-using-resource-governor-properties"></a><a name="DelWGRGProp"></a> <span data-ttu-id="68832-125">리소스 관리자 속성을 사용하여 작업 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="68832-125">Delete a Workload Group Using Resource Governor Properties</span></span>  
 <span data-ttu-id="68832-126">**리소스 관리자 속성 페이지를 사용하여 작업 그룹을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="68832-126">**To delete a workload group by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="68832-127">개체 탐색기에서 **리소스 풀** 이 나타날 때까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-127">In Object Explorer, recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="68832-128">삭제할 작업 그룹이 포함된 리소스 풀을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-128">Right-click the resource pool that contains the workload group to be deleted, and then click **Properties**.</span></span> <span data-ttu-id="68832-129">**리소스 관리자 속성** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="68832-129">This opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="68832-130">**리소스 풀의 작업 그룹** 창에서 삭제할 작업 그룹의 줄을 클릭한 다음 줄 왼쪽에 있는 오른쪽 화살표를 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-130">In the **Workload groups for resource pool** window, click the line for the workload group to be deleted, then right-click the right arrow on the left side of the line, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="68832-131">작업 그룹을 삭제하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-131">To delete the workload group, click **OK**.</span></span>  
  
##  <a name="delete-a-workload-group-using-transact-sql"></a><a name="DelWGTSQL"></a> <span data-ttu-id="68832-132">Transact-SQL을 사용하여 작업 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="68832-132">Delete a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="68832-133">**Transact-SQL을 사용하여 작업 그룹을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="68832-133">**To delete a workload group by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="68832-134">삭제할 작업 그룹의 이름을 지정하여 `DROP WORKLOAD GROUP` 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-134">Run the `DROP WORKLOAD GROUP` statement specifying the name of the workload group to delete.</span></span>  
  
2.  <span data-ttu-id="68832-135">`ALTER RESOURCE GOVERNOR RECONFIGURE` 문을 실행하기 전에 삭제할 작업 그룹에 활성 요청이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-135">Before you issue the `ALTER RESOURCE GOVERNOR RECONFIGURE` statement, verify that there are no active requests in the workload group being deleted.</span></span> <span data-ttu-id="68832-136">활성 요청이 있으면 `ALTER RESOURCE GOVERNOR`가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-136">If there are active requests, `ALTER RESOURCE GOVERNOR` will fail.</span></span> <span data-ttu-id="68832-137">이 문제를 방지하려면 다음 동작 중 하나를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="68832-137">To avoid this issue, you can take one of the following actions:</span></span>  
  
    -   <span data-ttu-id="68832-138">작업 그룹에서 모든 세션의 연결이 끊어질 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="68832-138">Wait until all the sessions from the workload group have disconnected.</span></span>  
  
    -   <span data-ttu-id="68832-139">`KILL` 명령을 사용하여 작업 그룹에 있는 세션을 명시적으로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-139">Explicitly stop sessions in the workload group by using the `KILL` command.</span></span>  
  
    -   <span data-ttu-id="68832-140">서버를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-140">Restart the server.</span></span> <span data-ttu-id="68832-141">작업 그룹은 다시 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68832-141">The workload group will not be re-created.</span></span>  
  
    -   <span data-ttu-id="68832-142">`DROP WORKLOAD GROUP` 문을 실행했지만 변경 내용을 적용하기 위해 세션을 명시적으로 중지하지 않으려는 경우 DROP 문을 실행하기 이전의 이름을 사용하여 그룹을 다시 만든 다음 해당 그룹을 원래 리소스 풀로 이동하십시오.</span><span class="sxs-lookup"><span data-stu-id="68832-142">In a scenario in which you have issued the `DROP WORKLOAD GROUP` statement but decide that you do not want to explicitly stop sessions to apply the change, you can re-create the group by using the same name that it had before you issued the DROP statement, and then move the group to the original resource pool.</span></span>  
  
3.  <span data-ttu-id="68832-143">문을 실행 `ALTER RESOURCE GOVERNOR RECONFIGURE` 합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-143">Run the `ALTER RESOURCE GOVERNOR RECONFIGURE` statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="68832-144">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="68832-144">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="68832-145">다음 예에서는 `groupAdhoc`이라는 작업 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="68832-145">The following example drops a workload group named `groupAdhoc`.</span></span>  
  
```  
DROP WORKLOAD GROUP groupAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="68832-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68832-146">See Also</span></span>  
 <span data-ttu-id="68832-147">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="68832-147">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="68832-148">[리소스 풀 만들기](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="68832-148">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="68832-149">[작업 그룹 만들기](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="68832-149">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="68832-150">[리소스 풀 삭제](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="68832-150">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="68832-151">[DROP WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="68832-151">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="68832-152">[DROP RESOURCE POOL&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="68832-152">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="68832-153">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="68832-153">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
