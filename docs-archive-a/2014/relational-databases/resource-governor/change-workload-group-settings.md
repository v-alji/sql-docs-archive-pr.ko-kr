---
title: 작업 그룹 설정 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], alter
- Resource Governor, workload group alter
ms.assetid: 73b6109c-2ad0-4915-b11b-d40d5a0fdc25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 579aad71d32a629d75f1eecd76e7dacfe32d94f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638637"
---
# <a name="change-workload-group-settings"></a><span data-ttu-id="d0782-102">작업 그룹 설정 변경</span><span class="sxs-lookup"><span data-stu-id="d0782-102">Change Workload Group Settings</span></span>
  <span data-ttu-id="d0782-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]을 사용하여 작업 그룹 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-103">You can change workload group settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="d0782-104">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="d0782-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="d0782-105">**작업 그룹에 대한 설정을 변경하려면 다음을 사용합니다.**  [SQL Server Management Studio](#ChgWGProp), [Transact-SQL](#ChgWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="d0782-105">**To change the settings for a workload group, using:**  [SQL Server Management Studio](#ChgWGProp), [Transact-SQL](#ChgWGTSQL)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="d0782-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d0782-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="d0782-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d0782-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="d0782-108">기본 작업 그룹 및 사용자 정의 작업 그룹의 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-108">You can change the settings of the default workload group and user-defined workload groups.</span></span>  
  
 <span data-ttu-id="d0782-109">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="d0782-109">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span></span>  
  
 <span data-ttu-id="d0782-110">정렬되지 않은 분할된 테이블에서 인덱스 생성에 사용되는 메모리는 관련된 파티션 수에 비례합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-110">The memory consumed by index creation on a non-aligned partitioned table is proportional to the number of partitions involved.</span></span> <span data-ttu-id="d0782-111">필요한 총 메모리가 작업 그룹 설정에서 지정한 쿼리당 제한(REQUEST_MAX_MEMORY_GRANT_PERCENT)을 초과하면 이 인덱스 생성이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-111">If the total required memory exceeds the per-query limit, (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposed by the workload group setting, this index creation may fail.</span></span> <span data-ttu-id="d0782-112">기본 작업 그룹에서는 쿼리가 SQL Server 2005 호환성을 유지하며 시작하는 데 필요한 최소 메모리에 대한 쿼리당 제한을 초과할 수 있으므로 기본 리소스 풀에 이러한 쿼리를 실행할 수 있는 총 메모리가 충분히 구성되어 있는 경우 사용자가 기본 작업 그룹에서 동일한 인덱스 생성을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-112">Because the default workload group allows a query to exceed the per-query limit with the minimum required memory to start for SQL Server 2005 compatibility, the user may be able to run the same index creation in the default workload group, if the default resource pool has enough total memory configured to run such a query.</span></span>  
  
 <span data-ttu-id="d0782-113">인덱스를 만들 때 처음에 부여된 것 이상의 메모리 작업 영역을 사용하여 성능을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-113">Index creation is allowed to use more memory workspace than initially granted for performance.</span></span> <span data-ttu-id="d0782-114">이 특수 처리는 리소스 관리자에서 지원되지만 초기 부여 및 추가 메모리 부여는 작업 그룹 및 리소스 풀 설정에 따라 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-114">This special handling is supported by Resource Governor, however, the initial grant and any additional memory grant are limited by the workload group and resource pool settings.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d0782-115">권한</span><span class="sxs-lookup"><span data-stu-id="d0782-115">Permissions</span></span>  
 <span data-ttu-id="d0782-116">작업 그룹 설정을 변경하려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-116">Changing workload group settings requires CONTROL SERVER permission.</span></span>  
  
##  <a name="change-workload-group-settings-using-sql-server-management-studio"></a><a name="ChgWGProp"></a> <span data-ttu-id="d0782-117">SQL Server Management Studio를 사용하여 작업 그룹 설정 변경</span><span class="sxs-lookup"><span data-stu-id="d0782-117">Change Workload Group Settings Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d0782-118">**다음을 사용하여 작업 그룹 설정을 변경하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="d0782-118">**To change workload group settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="d0782-119">개체 탐색기에서 수정할 작업 그룹이 포함된 **작업 그룹** 폴더가 나타날 때까지 **관리** 노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-119">In Object Explorer, recursively expand the **Management** node down to and including the **Workload Groups** folder that contains the workload group to be modified.</span></span>  
  
2.  <span data-ttu-id="d0782-120">수정할 작업 그룹을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-120">Right-click the workload group to be modified, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d0782-121">**리소스 관리자 속성** 페이지의 **리소스 풀의 작업 그룹** 표에서 작업 그룹의 행이 자동으로 선택되어 있지 않으면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-121">In the **Resource Governor Properties** page, select the row for the workload group in the **Workload groups for resource pool** grid if it is not automatically selected.</span></span>  
  
4.  <span data-ttu-id="d0782-122">변경할 행의 셀을 클릭 또는 두 번 클릭한 다음 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-122">Click or double-click the cells in the row to be changed, and enter the new values.</span></span>  
  
5.  <span data-ttu-id="d0782-123">**확인**을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-123">To save the changes, click **OK**</span></span>  
  
##  <a name="change-workload-group-settings-using-transact-sql"></a><a name="ChgWGTSQL"></a> <span data-ttu-id="d0782-124">Transact-SQL을 사용하여 작업 그룹 설정 변경</span><span class="sxs-lookup"><span data-stu-id="d0782-124">Change Workload Group Settings Using Transact-SQL</span></span>  
 <span data-ttu-id="d0782-125">**Transact-SQL을 사용하여 작업 그룹 설정을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="d0782-125">**To change workload group settings by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="d0782-126">변경할 속성 값을 지정하여 ALTER WORKLOAD GROUP 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-126">Run the ALTER WORKLOAD GROUP statement specifying the property values to be changed.</span></span>  
  
2.  <span data-ttu-id="d0782-127">ALTER RESOURCE GOVERNOR RECONFIGURE 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-127">Run the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="d0782-128">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d0782-128">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="d0782-129">다음 예에서는 `groupAdhoc`이라는 작업 그룹에 대한 최대 메모리 부여 비율 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d0782-129">The following example changes the max memory grant percent setting for the workload group named `groupAdhoc`.</span></span>  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
WITH (REQUEST_MAX_MEMORY_GRANT_PERCENT = 30);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0782-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0782-130">See Also</span></span>  
 <span data-ttu-id="d0782-131">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="d0782-131">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="d0782-132">[작업 그룹 만들기](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="d0782-132">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="d0782-133">[리소스 풀 만들기](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="d0782-133">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="d0782-134">[리소스 풀 설정 변경](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="d0782-134">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="d0782-135">[ALTER WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0782-135">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="d0782-136">[ALTER RESOURCE POOL&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0782-136">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="d0782-137">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d0782-137">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
