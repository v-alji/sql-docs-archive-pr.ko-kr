---
title: 리소스 관리자 속성 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties.f1
helpviewer_keywords:
- Resource Governor, properties
ms.assetid: de3510df-f792-4a9d-80fa-f198fd36cdc8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cd7af8f4f8eb3cd0531bc907011846f73f94f6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649465"
---
# <a name="view-resource-governor-properties"></a><span data-ttu-id="a6ae2-102">리소스 관리자 속성 보기</span><span class="sxs-lookup"><span data-stu-id="a6ae2-102">View Resource Governor Properties</span></span>
  <span data-ttu-id="a6ae2-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 리소스 관리자 속성 페이지를 사용하여 리소스 풀, 작업 그룹과 같은 리소스 관리자 엔터티를 만들거나 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-103">You can create or configure Resource Governor entities, such as resource pools and workload groups, by using the Resource Governor Properties page in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="a6ae2-104">**시작하기 전 주의 사항:**  [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="a6ae2-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
2.  <span data-ttu-id="a6ae2-105">**리소스 관리자 속성을 보려면**  [리소스 관리자 속성 페이지를 사용합니다.](#ViewRGProp)</span><span class="sxs-lookup"><span data-stu-id="a6ae2-105">**To view Resource Governor properties, using:**  [Resource Governor Properties page](#ViewRGProp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a6ae2-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a6ae2-106">Before You Begin</span></span>  
 <span data-ttu-id="a6ae2-107">리소스 관리자 엔터티 속성을 보는 것 이외에도, **리소스 관리자 속성** 페이지를 사용하여 몇 가지 구성 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-107">In addition to viewing the properties of Resource Governor entities, you can perform several configuration tasks using the **Resource Governor Properties** page.</span></span> <span data-ttu-id="a6ae2-108">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-108">For more information, see these topics:</span></span>  
  
-   [<span data-ttu-id="a6ae2-109">리소스 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="a6ae2-109">Enable Resource Governor</span></span>](enable-resource-governor.md)  
  
-   [<span data-ttu-id="a6ae2-110">리소스 관리자 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="a6ae2-110">Disable Resource Governor</span></span>](disable-resource-governor.md)  
  
-   [<span data-ttu-id="a6ae2-111">리소스 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="a6ae2-111">Create a Resource Pool</span></span>](create-a-resource-pool.md)  
  
-   [<span data-ttu-id="a6ae2-112">작업 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="a6ae2-112">Create a Workload Group</span></span>](create-a-workload-group.md)  
  
-   [<span data-ttu-id="a6ae2-113">리소스 풀 설정 변경</span><span class="sxs-lookup"><span data-stu-id="a6ae2-113">Change Resource Pool Settings</span></span>](change-resource-pool-settings.md)  
  
-   [<span data-ttu-id="a6ae2-114">작업 그룹 설정 변경</span><span class="sxs-lookup"><span data-stu-id="a6ae2-114">Change Workload Group Settings</span></span>](change-workload-group-settings.md)  
  
-   [<span data-ttu-id="a6ae2-115">작업 그룹 이동</span><span class="sxs-lookup"><span data-stu-id="a6ae2-115">Move a Workload Group</span></span>](move-a-workload-group.md)  
  
 <span data-ttu-id="a6ae2-116">작업 그룹 또는 리소스 풀을 추가, 삭제 또는 이동한 후에 **확인** 을 클릭하면 ALTER RESOURCE GOVERNOR RECONFIGURE 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-116">When you click **OK** after adding, deleting, or moving a workload group or resource pool, the ALTER RESOURCE GOVERNOR RECONFIGURE statement is executed.</span></span>  
  
 <span data-ttu-id="a6ae2-117">리소스 풀이나 작업 그룹의 생성 또는 재구성 작업이 실패하면 속성 페이지의 제목 아래에 요약 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-117">If the create or reconfigure operation for the resource pool or workload group fails, a summary error message appears below the title of the property page.</span></span> <span data-ttu-id="a6ae2-118">자세한 오류 메시지를 보려면 오류 메시지에 있는 아래쪽 화살표를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-118">To see a detailed error message, click the down arrow on the error message.</span></span>  
  
 <span data-ttu-id="a6ae2-119">[sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) 동적 관리 뷰를 쿼리해 is_configuration_pending의 현재 상태를 가져와서 보류 중인 구성이 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-119">You can determine whether there is a configuration pending by querying the [sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) dynamic management view to get the current status of is_configuration_pending.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a6ae2-120">권한</span><span class="sxs-lookup"><span data-stu-id="a6ae2-120">Permissions</span></span>  
 <span data-ttu-id="a6ae2-121">리소스 관리자 속성을 보려면 VIEW SERVER STATER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-121">Viewing resource governor properties requires VIEW SERVER STATER permission.</span></span> <span data-ttu-id="a6ae2-122">리소스 관리자 구성 작업을 하려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-122">The resource governor configuration tasks require CONTROL SERVER permission.</span></span>  
  
##  <a name="view-the-resource-governor-properties-page"></a><a name="ViewRGProp"></a><span data-ttu-id="a6ae2-123">Resource Governor 속성 페이지 보기</span><span class="sxs-lookup"><span data-stu-id="a6ae2-123">View the Resource Governor Properties Page</span></span>  
 <span data-ttu-id="a6ae2-124">**Resource Governor 속성 페이지를 사용하여 Resource Governor 속성을 보려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-124">**To view resource governor properties by using the Resource Governor Properties page in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="a6ae2-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **리소스 관리자** 까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="a6ae2-126">**Resource Governor** 를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다. 그러면 **Resource Governor** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-126">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="a6ae2-127">이 페이지의 필드에 대한 설명을 보려면 [리소스 관리자 속성](#RGProp)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-127">For descriptions of the fields in the page, see [Resource Governor Properties](#RGProp).</span></span>  
  
4.  <span data-ttu-id="a6ae2-128">변경 사항을 저장하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-128">To save any changes, click **OK**.</span></span>  
  
##  <a name="resource-governor-properties"></a><a name="RGProp"></a><span data-ttu-id="a6ae2-129">Resource Governor 속성</span><span class="sxs-lookup"><span data-stu-id="a6ae2-129">Resource Governor Properties</span></span>  
 <span data-ttu-id="a6ae2-130">**분류자 함수 이름**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-130">**Classifier function name**</span></span>  
 <span data-ttu-id="a6ae2-131">분류자 함수를 목록에서 선택하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-131">Specify the classifier function by selecting from the list.</span></span>  
  
 <span data-ttu-id="a6ae2-132">**리소스 관리자 사용**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-132">**Enable Resource Governor**</span></span>  
 <span data-ttu-id="a6ae2-133">확인란을 선택하거나 선택 취소하여 리소스 관리자를 사용하거나 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-133">Enable or disable Resource Governor by selecting or clearing the check box.</span></span>  
  
 <span data-ttu-id="a6ae2-134">**리소스 풀**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-134">**Resource pools**</span></span>  
 <span data-ttu-id="a6ae2-135">제공된 표를 사용하여 리소스 풀 구성을 만들거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-135">Create or change resource pool configuration by using the grid that is provided.</span></span> <span data-ttu-id="a6ae2-136">이 표는 미리 정의된 내부 풀 및 기본 풀에 대한 정보로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-136">This grid is populated with information for the predefined internal and default pools.</span></span> <span data-ttu-id="a6ae2-137">풀의 행에 있는 첫 번째 열을 클릭하여 작업할 풀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-137">Select a pool to work with by clicking the first column in the row for the pool.</span></span> <span data-ttu-id="a6ae2-138">새 리소스 풀을 만들려면 접두사로 별표( **&#42;** )가 붙은 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-138">To create a new resource pool, click the row that is prefixed by the asterisk (**&#42;**).</span></span>  
  
 <span data-ttu-id="a6ae2-139">**이름**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-139">**Name**</span></span>  
 <span data-ttu-id="a6ae2-140">리소스 풀의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-140">Specify the name of the resource pool.</span></span>  
  
 <span data-ttu-id="a6ae2-141">**최소 CPU(%)**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-141">**Minimum CPU %**</span></span>  
 <span data-ttu-id="a6ae2-142">CPU 충돌이 있을 때 리소스 풀의 모든 요청에 대해 보장되는 평균 CPU 대역폭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-142">Specify the guaranteed average CPU bandwidth for all requests in the resource pool when there is CPU contention.</span></span> <span data-ttu-id="a6ae2-143">범위는 0에서 100까지입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-143">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="a6ae2-144">**최대 CPU(%)**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-144">**Maximum CPU %**</span></span>  
 <span data-ttu-id="a6ae2-145">CPU 충돌이 있을 때 이 리소스 풀의 모든 요청이 받는 최대 평균 CPU 대역폭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-145">Specify the maximum average CPU bandwidth that all requests in this resource pool will receive when there is CPU contention.</span></span> <span data-ttu-id="a6ae2-146">범위는 0에서 100까지입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-146">Range is 0 to 100.</span></span> <span data-ttu-id="a6ae2-147">기본 설정은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-147">The default setting is 100.</span></span>  
  
 <span data-ttu-id="a6ae2-148">**최소 메모리(%)**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-148">**Minimum Memory %**</span></span>  
 <span data-ttu-id="a6ae2-149">다른 리소스 풀과 공유할 수 없으며 이 리소스 풀에 예약된 최소 메모리 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-149">Specify the minimum amount of memory reserved for this resource pool that can not be shared with other resource pools.</span></span> <span data-ttu-id="a6ae2-150">범위는 0에서 100까지입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-150">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="a6ae2-151">**최대 메모리(%)**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-151">**Maximum Memory %**</span></span>  
 <span data-ttu-id="a6ae2-152">이 리소스 풀의 요청에서 사용할 수 있는 총 서버 메모리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-152">Specify the total server memory that can be used by requests in this resource pool.</span></span> <span data-ttu-id="a6ae2-153">범위는 0에서 100까지입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-153">Range is 0 to 100.</span></span> <span data-ttu-id="a6ae2-154">기본 설정은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-154">The default setting is 100.</span></span>  
  
 <span data-ttu-id="a6ae2-155">자세한 내용은 [CREATE RESOURCE POOL &#40;transact-sql&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-155">For more information, see [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql).</span></span>  
  
 <span data-ttu-id="a6ae2-156">**리소스 풀의 작업 그룹**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-156">**Workload groups for resource pool**</span></span>  
 <span data-ttu-id="a6ae2-157">제공된 표를 사용하여 작업 그룹 구성을 만들거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-157">Create or change the workload group configuration by using the grid that is provided.</span></span> <span data-ttu-id="a6ae2-158">이 표는 미리 정의된 내부 그룹 및 기본 그룹에 대한 정보로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-158">This grid is populated with information for the predefined internal and default groups.</span></span> <span data-ttu-id="a6ae2-159">풀의 행에 있는 첫 번째 열을 클릭하여 작업할 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-159">Select a group to work with by clicking the first column in the row for the pool.</span></span> <span data-ttu-id="a6ae2-160">새 작업 그룹을 만들려면 접두사로 별표( **&#42;** )가 붙은 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-160">To create a new workload group, click the row that is prefixed by the asterisk (**&#42;**).</span></span>  
  
 <span data-ttu-id="a6ae2-161">**이름**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-161">**Name**</span></span>  
 <span data-ttu-id="a6ae2-162">작업 그룹의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-162">Specify the name of the workload group.</span></span>  
  
 <span data-ttu-id="a6ae2-163">**중요도**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-163">**Importance**</span></span>  
 <span data-ttu-id="a6ae2-164">작업 그룹에 있는 요청의 상대적 중요도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-164">Specify the relative importance of a request in the workload group.</span></span> <span data-ttu-id="a6ae2-165">사용 가능한 설정은 낮음, 보통 및 높음입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-165">Available settings are Low, Medium, and High.</span></span>  
  
 <span data-ttu-id="a6ae2-166">**최대 요청 수**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-166">**Maximum Requests**</span></span>  
 <span data-ttu-id="a6ae2-167">작업 그룹에서 실행할 수 있는 최대 동시 요청 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-167">Specify the maximum number of simultaneous requests that are allowed to execute in the workload group.</span></span> <span data-ttu-id="a6ae2-168">0 또는 양의 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-168">Must be 0 or a positive integer.</span></span>  
  
 <span data-ttu-id="a6ae2-169">**CPU 시간(초)**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-169">**CPU Time (sec)**</span></span>  
 <span data-ttu-id="a6ae2-170">요청이 사용할 수 있는 최대 CPU 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-170">Specify the maximum amount of CPU time that a request can use.</span></span> <span data-ttu-id="a6ae2-171">0 또는 양의 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-171">Must be 0 or a positive integer.</span></span> <span data-ttu-id="a6ae2-172">0이면 시간에 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-172">If 0, the time is unlimited.</span></span>  
  
 <span data-ttu-id="a6ae2-173">**메모리 부여(%)**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-173">**Memory Grant %**</span></span>  
 <span data-ttu-id="a6ae2-174">단일 요청이 풀에서 사용할 수 있는 최대 메모리 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-174">Specify the maximum amount of memory that a single request can take from the pool.</span></span> <span data-ttu-id="a6ae2-175">범위는 0에서 100까지입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-175">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="a6ae2-176">**부여 제한 시간(초)**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-176">**Grant Time-out (sec)**</span></span>  
 <span data-ttu-id="a6ae2-177">쿼리가 실패하기 전에 리소스를 사용할 수 있을 때까지 쿼리가 대기할 수 있는 최대 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-177">Specify the maximum time that a query can wait for a resource to become available before the query fails.</span></span> <span data-ttu-id="a6ae2-178">0 또는 양의 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-178">Must be 0 or a positive integer.</span></span>  
  
 <span data-ttu-id="a6ae2-179">**병렬 처리 수준**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-179">**Degree of Parallelism**</span></span>  
 <span data-ttu-id="a6ae2-180">병렬 요청의 최대 DOP(병렬 처리 수준)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-180">Specify the maximum degree of parallelism (DOP) for parallel requests.</span></span> <span data-ttu-id="a6ae2-181">범위는 0에서 64까지입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-181">Range is 0 to 64.</span></span>  
  
 <span data-ttu-id="a6ae2-182">자세한 내용은 [CREATE WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-182">For more information, see [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql).</span></span>  
  
## <a name="view-resource-governor-properties-by-using-transact-sql"></a><span data-ttu-id="a6ae2-183">Transact-SQL을 사용하여 리소스 관리자 속성 보기</span><span class="sxs-lookup"><span data-stu-id="a6ae2-183">View Resource Governor Properties by Using Transact-SQL</span></span>  
 <span data-ttu-id="a6ae2-184">**Transact-SQL을 사용하여 리소스 관리자 속성 보기**</span><span class="sxs-lookup"><span data-stu-id="a6ae2-184">**View resource governor properties by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="a6ae2-185">Resource Governor 엔터티의 정의를 보려면 [Resource Governor 카탈로그 뷰&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-185">To view the definitions of resource governor entities, use the [Resource Governor Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql).</span></span>  
  
2.  <span data-ttu-id="a6ae2-186">Resource Governor 엔터티의 현재 구성을 보려면 [Resource Governor 관련 동적 관리 뷰&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-186">To view the current configuration of resource governor entities, use the [Resource Governor Related Dynamic Management Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ae2-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6ae2-187">See Also</span></span>  
 <span data-ttu-id="a6ae2-188">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="a6ae2-188">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="a6ae2-189">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="a6ae2-189">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="a6ae2-190">[리소스 관리자 리소스 풀](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="a6ae2-190">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="a6ae2-191">[리소스 관리자 작업 그룹](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="a6ae2-191">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 [<span data-ttu-id="a6ae2-192">리소스 관리자 분류자 함수</span><span class="sxs-lookup"><span data-stu-id="a6ae2-192">Resource Governor Classifier Function</span></span>](resource-governor-classifier-function.md)  
  
  
