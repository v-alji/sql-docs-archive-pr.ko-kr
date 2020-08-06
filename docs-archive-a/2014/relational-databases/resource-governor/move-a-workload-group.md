---
title: 작업 그룹 이동 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties_moveworkloadgroup.f1
helpviewer_keywords:
- workload groups [SQL Server], move
- Resource Governor, workload group move
ms.assetid: f2068636-6e53-486a-a6fc-c12de2a38424
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f73b48f0ec2255760b4ee55acfaf91dc02af7cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731468"
---
# <a name="move-a-workload-group"></a><span data-ttu-id="5322f-102">작업 그룹 이동</span><span class="sxs-lookup"><span data-stu-id="5322f-102">Move a Workload Group</span></span>
  <span data-ttu-id="5322f-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 Transact-SQL을 사용하여 리소스 관리자 작업 그룹을 다른 리소스 풀로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-103">You can move a Resource Governor workload group to a different resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="5322f-104">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="5322f-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="5322f-105">**작업 그룹을 이동하려면 다음을 사용합니다.**  [SQL Server Management Studio](#MoveWGSSMS), [Transact-SQL](#MoveWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="5322f-105">**To move a workload group, using:**  [SQL Server Management Studio](#MoveWGSSMS), [Transact-SQL](#MoveWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5322f-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5322f-106">Before You Begin</span></span>  
 <span data-ttu-id="5322f-107">보류 중인 리소스 관리자 구성 작업이 있으면 작업 그룹을 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-107">You cannot move a workload group if there is a pending Resource Governor configuration operation.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="5322f-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5322f-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="5322f-109">보류 중인 리소스 관리자 구성 작업이 있으면 작업 그룹을 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-109">You cannot move a workload group if there is a pending Resource Governor configuration operation.</span></span> <span data-ttu-id="5322f-110">[sys.dm_resource_governor_configuration&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) 동적 관리 뷰를 쿼리해 is_configuration_pending의 현재 상태를 가져와서 보류 중인 구성이 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-110">You can determine whether there is a configuration pending by querying the [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) dynamic management view to get the current status of is_configuration_pending.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5322f-111">권한</span><span class="sxs-lookup"><span data-stu-id="5322f-111">Permissions</span></span>  
 <span data-ttu-id="5322f-112">작업 그룹을 이동하려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-112">Moving a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="move-a-workload-group-using-sql-server-management-studio"></a><a name="MoveWGSSMS"></a> <span data-ttu-id="5322f-113">SQL Server Management Studio를 사용하여 작업 그룹 이동</span><span class="sxs-lookup"><span data-stu-id="5322f-113">Move a Workload Group Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="5322f-114">**다음을 사용하여 작업 그룹을 이동하려면 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="5322f-114">**To move a workload group by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**</span></span>  
  
1.  <span data-ttu-id="5322f-115">개체 탐색기에서 **리소스 관리자** 까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-115">In Object Explorer, recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="5322f-116">**Resource Governor** 를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다. 그러면 **Resource Governor** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-116">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="5322f-117">**리소스 풀** 창에서 이동할 작업 그룹이 들어 있는 리소스 풀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-117">In the **Resource Pools** window, click the resource pool containing the workload group to be moved.</span></span> <span data-ttu-id="5322f-118">**작업 그룹** 창에 해당 리소스 풀의 작업 그룹이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-118">The **Workload Groups** window now lists the workload groups in that resource pool.</span></span>  
  
4.  <span data-ttu-id="5322f-119">**작업 그룹** 창에서 이동할 작업 그룹의 왼쪽에 있는 오른쪽 화살표를 마우스 오른쪽 단추로 클릭하고 **이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-119">In the **Workload Groups** window, right-click the right arrow to the left of the workload group to be moved, and click **Move to**.</span></span> <span data-ttu-id="5322f-120">**작업 그룹 이동** 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-120">This displays a **Move Workload Group** window.</span></span>  
  
5.  <span data-ttu-id="5322f-121">사용 가능한 리소스 풀이 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-121">Available resource pools are displayed in the window.</span></span> <span data-ttu-id="5322f-122">작업 그룹을 이동하려는 리소스 풀의 이름을 클릭한 다음 **확인** 을 클릭하여 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-122">Click the name of the resource pool that you want to move the workload group to, and then click **OK** to carry out this action.</span></span>  
  
6.  <span data-ttu-id="5322f-123">**확인**을 클릭하지 않으면 이 동작이 완료되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-123">This action is not completed until after you click **OK**.</span></span> <span data-ttu-id="5322f-124">**확인**을 클릭하면 ALTER RESOURCE GOVERNOR RECONFIGURE 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-124">When you click **OK**, the ALTER RESOURCE GOVERNOR RECONFIGURE statement is executed.</span></span>  
  
7.  <span data-ttu-id="5322f-125">리소스 풀이나 작업 그룹의 생성 또는 재구성 작업이 실패하면 속성 페이지의 제목 아래에 요약 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-125">If the create or reconfigure operation fails for the resource pool or workload group, a summary error message appears below the title of the property page.</span></span> <span data-ttu-id="5322f-126">자세한 오류 메시지를 보려면 오류 메시지에 있는 아래쪽 화살표를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="5322f-126">To see a detailed error message, click the down arrow on the error message.</span></span>  
  
##  <a name="move-a-workload-group-using-transact-sql"></a><a name="MoveWGTSQL"></a> <span data-ttu-id="5322f-127">Transact-SQL을 사용하여 작업 그룹 이동</span><span class="sxs-lookup"><span data-stu-id="5322f-127">Move a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="5322f-128">**Transact-SQL을 사용하여 작업 그룹을 이동하려면**</span><span class="sxs-lookup"><span data-stu-id="5322f-128">**To move a workload group by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="5322f-129">이동할 작업 그룹 및 이동 대상 리소스 풀의 이름을 지정하여 `ALTER WORKLOAD GROUP` 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-129">Run the `ALTER WORKLOAD GROUP` statement specifying the name of the workload group to be moved and the resource pool to which it should be moved.</span></span>  
  
2.  <span data-ttu-id="5322f-130">**ALTER RESOURCE GOVERNOR RECONFIGURE** 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-130">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="5322f-131">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5322f-131">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="5322f-132">다음 예에서는 `groupAdhoc` 이라는 작업 그룹을 기본 리소스 풀로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5322f-132">The following example moves a workload group named `groupAdhoc` to the default resource pool.</span></span>  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="5322f-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5322f-133">See Also</span></span>  
 <span data-ttu-id="5322f-134">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="5322f-134">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="5322f-135">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="5322f-135">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="5322f-136">[리소스 풀 만들기](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="5322f-136">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="5322f-137">[작업 그룹 만들기](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="5322f-137">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="5322f-138">[ALTER WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5322f-138">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 [<span data-ttu-id="5322f-139">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5322f-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
