---
title: 리소스 관리자 사용 안 함 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 172f01bdde0f792cd9ed72ad371e5811b8de8885
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731476"
---
# <a name="disable-resource-governor"></a><span data-ttu-id="c3da5-102">리소스 관리자 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="c3da5-102">Disable Resource Governor</span></span>
  <span data-ttu-id="c3da5-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 Transact-SQL을 사용하여 리소스 관리자를 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-103">You can disable the Resource Governor by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="c3da5-104">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="c3da5-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="c3da5-105">**Resource Governor를 사용하지 않도록 설정하려면 다음을 사용합니다.**  [개체 탐색기](#RGOffObjEx), [Resource Governor 속성](#RGOffProp) 또는 [Transact-SQL](#RGOffTSQL)</span><span class="sxs-lookup"><span data-stu-id="c3da5-105">**To disable Resource Governorn, using:**  [Object Explorer](#RGOffObjEx), [Resource Governor Properties](#RGOffProp), [Transact-SQL](#RGOffTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c3da5-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c3da5-106">Before You Begin</span></span>  
 <span data-ttu-id="c3da5-107">리소스 관리자를 사용하지 않도록 설정하면 다음과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-107">Disabling the Resource Governor has the following results:</span></span>  
  
-   <span data-ttu-id="c3da5-108">분류자 함수가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-108">The classifier function is not run.</span></span>  
  
-   <span data-ttu-id="c3da5-109">모든 새 연결이 자동으로 기본 작업 그룹으로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-109">All new connections are automatically classified into the default workload group.</span></span>  
  
-   <span data-ttu-id="c3da5-110">시스템에서 시작한 요청이 내부 작업 그룹으로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-110">System-initiated requests are classified into the internal workload group.</span></span>  
  
-   <span data-ttu-id="c3da5-111">기존의 모든 작업 그룹 및 리소스 풀 설정이 해당 기본값으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-111">All existing workload group and resource pool settings are reset to their default values.</span></span> <span data-ttu-id="c3da5-112">이 경우 제한에 도달해도 이벤트가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-112">In this case, no events are fired when limits are reached.</span></span>  
  
-   <span data-ttu-id="c3da5-113">정상적인 시스템 모니터링은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-113">Normal system monitoring is not affected.</span></span>  
  
-   <span data-ttu-id="c3da5-114">구성을 변경할 수 있지만 리소스 관리자를 사용하도록 설정할 때까지 변경 내용이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-114">Configuration changes can be made, but the changes do not take effect until the Resource Governor is enabled.</span></span>  
  
-   <span data-ttu-id="c3da5-115">SQL Server를 다시 시작하면 리소스 관리자가 구성을 로드하지 않고 기본 및 내부 작업 그룹과 리소스 풀만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-115">Upon restarting SQL Server, the Resource Governor will not load its configuration, but instead will have only the default and internal workload groups and resource pools.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="c3da5-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c3da5-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c3da5-117">사용자 트랜잭션에 있을 때에는 `ALTER RESOURCE GOVERNOR` 문을 사용하여 리소스 관리자를 사용하지 않도록 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-117">You cannot use the `ALTER RESOURCE GOVERNOR` statement to disable Resource Governor when in a user transaction.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c3da5-118">권한</span><span class="sxs-lookup"><span data-stu-id="c3da5-118">Permissions</span></span>  
 <span data-ttu-id="c3da5-119">리소스 관리자를 사용하지 않도록 설정하려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-119">Disabling the Resource Governor requires CONTROL SERVER permission.</span></span>  
  
##  <a name="disable-resource-governor-using-object-explorer"></a><a name="RGOffObjEx"></a> <span data-ttu-id="c3da5-120">개체 탐색기를 사용하여 리소스 관리자를 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="c3da5-120">Disable Resource Governor Using Object Explorer</span></span>  
 <span data-ttu-id="c3da5-121">**개체 탐색기를 사용하여 리소스 관리자를 사용하지 않도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="c3da5-121">**To disable the Resource Governor by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="c3da5-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **리소스 관리자** 까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="c3da5-123">**Resource Governor**를 마우스 오른쪽 단추로 클릭한 다음 **사용 안 함**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-123">Right-click **Resource Governor**, and then click **Disable**.</span></span>  
  
##  <a name="disable-resource-governor-using-resource-governor-properties"></a><a name="RGOffProp"></a> <span data-ttu-id="c3da5-124">리소스 관리자 속성을 사용하여 리소스 관리자를 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="c3da5-124">Disable Resource Governor Using Resource Governor Properties</span></span>  
 <span data-ttu-id="c3da5-125">**리소스 관리자 속성 페이지를 사용하여 리소스 관리자를 사용하지 않도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="c3da5-125">**To disable the Resource Governor by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="c3da5-126">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **리소스 관리자** 까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-126">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="c3da5-127">**Resource Governor** 를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다. 그러면 **Resource Governor** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-127">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="c3da5-128">**리소스 관리자 사용** 확인란을 클릭해서 상자를 선택 해제한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-128">Click the **Enable Resource Governor** check box, ensure that the box is not selected, and then click **OK**.</span></span>  
  
##  <a name="disable-resource-governor-using-transact-sql"></a><a name="RGOffTSQL"></a> <span data-ttu-id="c3da5-129">Transact-SQL을 사용하여 리소스 관리자를 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="c3da5-129">Disable Resource Governor Using Transact-SQL</span></span>  
 <span data-ttu-id="c3da5-130">**Transact-SQL을 사용하여 리소스 관리자를 사용하지 않도록 설정**</span><span class="sxs-lookup"><span data-stu-id="c3da5-130">**To disable the Resource Governor by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="c3da5-131">**ALTER RESOURCE GOVERNOR DISABLE** 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-131">Run the **ALTER RESOURCE GOVERNOR DISABLE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="c3da5-132">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c3da5-132">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="c3da5-133">다음 예에서는 리소스 관리자를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3da5-133">The following example enables the Resource Governor.</span></span>  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3da5-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3da5-134">See Also</span></span>  
 <span data-ttu-id="c3da5-135">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c3da5-135">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="c3da5-136">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c3da5-136">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="c3da5-137">[리소스 관리자 리소스 풀](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="c3da5-137">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="c3da5-138">[리소스 관리자 작업 그룹](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="c3da5-138">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="c3da5-139">[리소스 관리자 분류자 함수](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="c3da5-139">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 [<span data-ttu-id="c3da5-140">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c3da5-140">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
