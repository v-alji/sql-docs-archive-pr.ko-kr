---
title: 리소스 풀 설정 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool alter
- resource pools [SQL Server], alter
ms.assetid: 49438285-a011-4dac-bd4f-f35cd90fda61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2183cceaaf8a3e183d96c154075f9a922942c2c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730460"
---
# <a name="change-resource-pool-settings"></a><span data-ttu-id="c4e94-102">리소스 풀 설정 변경</span><span class="sxs-lookup"><span data-stu-id="c4e94-102">Change Resource Pool Settings</span></span>
  <span data-ttu-id="c4e94-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 리소스 풀 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-103">You can change resource pool settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="c4e94-104">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="c4e94-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="c4e94-105">**리소스 풀 설정을 변경하려면 다음을 사용합니다.**  [SQL Server Management Studio](#ChgRPProp), [Transact-SQL](#ChgRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="c4e94-105">**To change the settings for a resource pool, using:**  [SQL Server Management Studio](#ChgRPProp), [Transact-SQL](#ChgRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c4e94-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c4e94-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="c4e94-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c4e94-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c4e94-108">최대 CPU 비율은 최소 CPU 비율보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-108">The maximum CPU percentage must be equal to or higher than the minimum CPU percentage.</span></span> <span data-ttu-id="c4e94-109">최대 메모리 비율은 최소 메모리 비율보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-109">The maximum memory percentage must be equal to or higher than the minimum memory percentage.</span></span>  
  
 <span data-ttu-id="c4e94-110">모든 리소스 풀에 대한 최대 CPU 비율과 최소 CPU 비율의 합은 100을 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-110">The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c4e94-111">권한</span><span class="sxs-lookup"><span data-stu-id="c4e94-111">Permissions</span></span>  
 <span data-ttu-id="c4e94-112">리소스 풀 설정을 변경하려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-112">Changing resource pool settings requires CONTROL SERVER permission.</span></span>  
  
##  <a name="change-resource-pool-settings-using-sql-server-management-studio"></a><a name="ChgRPProp"></a> <span data-ttu-id="c4e94-113">SQL Server Management Studio를 사용하여 리소스 풀 설정 변경</span><span class="sxs-lookup"><span data-stu-id="c4e94-113">Change Resource Pool Settings Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="c4e94-114">**을 사용하여 리소스 풀 설정을 변경하려면(!!) [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="c4e94-114">**To change resource pool settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="c4e94-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **리소스 풀** 이 나타날 때까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="c4e94-116">수정할 리소스 풀을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-116">Right-click the resource pool to be modified, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="c4e94-117">**리소스 관리자 속성** 페이지의 **리소스 풀** 표에서 리소스 풀의 행이 자동으로 선택되어 있지 않으면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-117">In the **Resource Governor Properties** page, select the row for the resource pool in the **Resource pools** grid if it is not automatically selected.</span></span>  
  
4.  <span data-ttu-id="c4e94-118">변경할 행의 셀을 클릭 또는 두 번 클릭한 다음 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-118">Click or double-click the cells in the row to be changed, and enter the new values.</span></span>  
  
5.  <span data-ttu-id="c4e94-119">**확인**을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-119">To save the changes, click **OK**</span></span>  
  
##  <a name="change-resource-pool-settings-using-transact-sql"></a><a name="ChgRPTSQL"></a> <span data-ttu-id="c4e94-120">Transact-SQL을 사용하여 리소스 풀 설정 변경</span><span class="sxs-lookup"><span data-stu-id="c4e94-120">Change Resource Pool Settings Using Transact-SQL</span></span>  
 <span data-ttu-id="c4e94-121">**을 사용하여 리소스 풀 설정을 변경하려면(!!) [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="c4e94-121">**To change resource pool settings by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="c4e94-122">변경할 속성 값을 지정하여 `ALTER RESOURCE POOL` 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-122">Run the `ALTER RESOURCE POOL` statement specifying the property values to be changed.</span></span>  
  
2.  <span data-ttu-id="c4e94-123">**ALTER RESOURCE GOVERNOR RECONFIGURE** 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-123">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="c4e94-124">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c4e94-124">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="c4e94-125">다음 예에서는 `poolAdhoc`이라는 리소스 풀에 대한 최대 CPU 비율 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e94-125">The following example changes the max CPU percentage setting for the resource pool named `poolAdhoc`.</span></span>  
  
```  
ALTER RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4e94-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c4e94-126">See Also</span></span>  
 <span data-ttu-id="c4e94-127">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c4e94-127">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="c4e94-128">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c4e94-128">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="c4e94-129">[리소스 풀 만들기](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="c4e94-129">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="c4e94-130">[리소스 풀 삭제](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="c4e94-130">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="c4e94-131">[리소스 관리자 작업 그룹](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="c4e94-131">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="c4e94-132">[리소스 관리자 분류자 함수](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="c4e94-132">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="c4e94-133">[ALTER RESOURCE POOL&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4e94-133">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="c4e94-134">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c4e94-134">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
