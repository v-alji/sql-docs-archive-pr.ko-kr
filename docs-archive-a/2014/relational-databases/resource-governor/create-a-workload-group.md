---
title: 작업 그룹 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group create
- workload groups [SQL Server], create
ms.assetid: 072868ec-ceff-4db6-941b-281af731a067
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 144bcef57b3d6e191b03b1539e9e7382a9085c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649469"
---
# <a name="create-a-workload-group"></a><span data-ttu-id="e907e-102">작업 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="e907e-102">Create a Workload Group</span></span>
  <span data-ttu-id="e907e-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 작업 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-103">You can create a workload group by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="e907e-104">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="e907e-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="e907e-105">**작업 그룹을 만들려면 다음을 사용합니다.**  [SQL Server Management Studio](#CreWGProp), [Transact-SQL](#CreWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="e907e-105">**To create a workload group, using:**  [SQL Server Management Studio](#CreWGProp), [Transact-SQL](#CreWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e907e-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e907e-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="e907e-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e907e-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e907e-108">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="e907e-108">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span></span>  
  
 <span data-ttu-id="e907e-109">정렬되지 않은 분할된 테이블에서 인덱스 생성에 사용되는 메모리는 관련된 파티션 수에 비례합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-109">The memory consumed by index creation on a non-aligned partitioned table is proportional to the number of partitions involved.</span></span> <span data-ttu-id="e907e-110">필요한 총 메모리가 작업 그룹 설정에서 지정한 쿼리당 제한(REQUEST_MAX_MEMORY_GRANT_PERCENT)을 초과하면 이 인덱스 생성이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-110">If the total required memory exceeds the per-query limit, (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposed by the workload group setting, this index creation may fail.</span></span> <span data-ttu-id="e907e-111">기본 작업 그룹에서는 쿼리가 SQL Server 2005 호환성을 유지하며 시작하는 데 필요한 최소 메모리에 대한 쿼리당 제한을 초과할 수 있으므로 기본 리소스 풀에 이러한 쿼리를 실행할 수 있는 총 메모리가 충분히 구성되어 있는 경우 사용자가 기본 작업 그룹에서 동일한 인덱스 생성을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-111">Because the default workload group allows a query to exceed the per-query limit with the minimum required memory to start for SQL Server 2005 compatibility, the user may be able to run the same index creation in the default workload group, if the default resource pool has enough total memory configured to run such a query.</span></span>  
  
 <span data-ttu-id="e907e-112">인덱스를 만들 때 처음에 부여된 것 이상의 메모리 작업 영역을 사용하여 성능을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-112">Index creation is allowed to use more memory workspace than initially granted for performance.</span></span> <span data-ttu-id="e907e-113">이 특수 처리는 리소스 관리자에서 지원되지만 초기 부여 및 추가 메모리 부여는 작업 그룹 및 리소스 풀 설정에 따라 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-113">This special handling is supported by Resource Governor, however, the initial grant and any additional memory grant are limited by the workload group and resource pool settings.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e907e-114">권한</span><span class="sxs-lookup"><span data-stu-id="e907e-114">Permissions</span></span>  
 <span data-ttu-id="e907e-115">작업 그룹을 만들려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-115">Creating a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="create-a-workload-group-using-sql-server-management-studio"></a><a name="CreWGProp"></a> <span data-ttu-id="e907e-116">SQL Server Management Studio를 사용하여 작업 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="e907e-116">Create a Workload Group Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e907e-117">**다음을 사용하여 작업 그룹을 만들기: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="e907e-117">**To create a workload group by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="e907e-118">개체 탐색기에서 수정할 작업 그룹이 포함된 리소스 풀이 나타날 때까지 **관리** 노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-118">In Object Explorer, recursively expand the **Management** node down to and including the resource pool that contains the workload group to be modified.</span></span>  
  
2.  <span data-ttu-id="e907e-119">**Workload Groups** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 작업 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-119">Right-click the **Workload Groups** folder, and then click **New Workload Group**.</span></span>  
  
3.  <span data-ttu-id="e907e-120">**리소스 풀** 표에 작업 그룹을 추가하려는 리소스 풀이 강조 표시되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-120">In the **Resource pools** grid, ensure the resource pool where you want to add the workload group is highlighted.</span></span>  
  
4.  <span data-ttu-id="e907e-121">**리소스 풀의 작업 그룹** 표에 빈 이름이 포함된 새 줄이 나타나고 다른 열에는 기본 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-121">The **Workload groups for resource pool** grid will have a new line with a blank name and default values in the other columns.</span></span>  
  
5.  <span data-ttu-id="e907e-122">**이름** 셀을 클릭하고 작업 그룹의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-122">Click the **Name** cell and enter a name for the workload group.</span></span>  
  
6.  <span data-ttu-id="e907e-123">기본 설정에서 변경하려는 행의 다른 셀을 클릭 또는 두 번 클릭한 다음 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-123">Click or double-click any other cells in the row you want to change from their default settings, and enter the new values.</span></span>  
  
7.  <span data-ttu-id="e907e-124">**확인**을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-124">To save the changes, click **OK**</span></span>  
  
##  <a name="create-a-workload-group-using-transact-sql"></a><a name="CreWGTSQL"></a> <span data-ttu-id="e907e-125">Transact-SQL을 사용하여 작업 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="e907e-125">Create a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="e907e-126">**다음을 사용하여 작업 그룹을 만들기: [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="e907e-126">**To create a workload group by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="e907e-127">설정할 속성 값을 지정하여 CREATE WORKLOAD GROUP 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-127">Run the CREATE WORKLOAD GROUP statement specifying the property values to be set.</span></span>  
  
2.  <span data-ttu-id="e907e-128">ALTER RESOURCE GOVERNOR RECONFIGURE 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-128">Run the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="e907e-129">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e907e-129">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="e907e-130">다음 예에서는 `groupAdhoc` 이라는 리소스 풀에 있는 `poolAdhoc`이라는 작업 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e907e-130">The following example creates a workload group named `groupAdhoc` in the resource pool named `poolAdhoc`.</span></span>  
  
```  
CREATE WORKLOAD GROUP groupAdhoc  
USING poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e907e-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e907e-131">See Also</span></span>  
 <span data-ttu-id="e907e-132">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="e907e-132">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="e907e-133">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="e907e-133">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="e907e-134">[리소스 풀 만들기](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="e907e-134">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="e907e-135">[작업 그룹 설정 변경](change-workload-group-settings.md) </span><span class="sxs-lookup"><span data-stu-id="e907e-135">[Change Workload Group Settings](change-workload-group-settings.md) </span></span>  
 <span data-ttu-id="e907e-136">[분류자 사용자 정의 함수 만들기 및 테스트](create-and-test-a-classifier-user-defined-function.md) </span><span class="sxs-lookup"><span data-stu-id="e907e-136">[Create and Test a Classifier User-Defined Function](create-and-test-a-classifier-user-defined-function.md) </span></span>  
 <span data-ttu-id="e907e-137">[CREATE WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e907e-137">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 [<span data-ttu-id="e907e-138">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e907e-138">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
