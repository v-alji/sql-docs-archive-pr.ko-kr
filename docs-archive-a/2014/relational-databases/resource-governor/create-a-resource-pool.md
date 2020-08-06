---
title: 리소스 풀 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5abd2e60f4f9bb5290b47f95349782f8b26ad8bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660995"
---
# <a name="create-a-resource-pool"></a><span data-ttu-id="d6637-102">리소스 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="d6637-102">Create a Resource Pool</span></span>
  <span data-ttu-id="d6637-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 리소스 풀을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-103">You can create a resource pool by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="d6637-104">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="d6637-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="d6637-105">**리소스 풀을 만들려면 다음을 사용합니다.**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="d6637-105">**To create a resource pool, using:**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d6637-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d6637-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="d6637-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d6637-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="d6637-108">최대 CPU 비율은 최소 CPU 비율보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-108">The maximum CPU percentage must be equal to or higher than the minimum CPU percentage.</span></span> <span data-ttu-id="d6637-109">최대 메모리 비율은 최소 메모리 비율보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-109">The maximum memory percentage must be equal to or higher than the minimum memory percentage.</span></span>  
  
 <span data-ttu-id="d6637-110">모든 리소스 풀에 대한 최대 CPU 비율과 최소 CPU 비율의 합은 100을 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-110">The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d6637-111">권한</span><span class="sxs-lookup"><span data-stu-id="d6637-111">Permissions</span></span>  
 <span data-ttu-id="d6637-112">리소스 풀을 만들려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-112">Creating a resource pool requires CONTROL SERVER permission.</span></span>  
  
##  <a name="create-a-resource-pool-using-sql-server-management-studio"></a><a name="CreRPProp"></a> <span data-ttu-id="d6637-113">SQL Server Management Studio를 사용하여 리소스 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="d6637-113">Create a Resource Pool Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d6637-114">**다음을 사용하여 리소스 풀 만들기: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="d6637-114">**To create a resource pool by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="d6637-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **리소스 관리자** 가 나타날 때까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="d6637-116">**Resource Governor**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-116">Right-click **Resource Governor**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d6637-117">**리소스 풀** 표에서 빈 행의 첫 번째 열을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-117">In the **Resource pools** grid, click the first column in the empty row.</span></span> <span data-ttu-id="d6637-118">이 열에는 별표(\*)가 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-118">This column is labeled with an asterisk (\*).</span></span>  
  
4.  <span data-ttu-id="d6637-119">**이름** 열의 빈 셀을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-119">Double-click the empty cell in the **Name** column.</span></span> <span data-ttu-id="d6637-120">리소스 풀에 사용할 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-120">Type in the name that you want to use for the resource pool.</span></span>  
  
5.  <span data-ttu-id="d6637-121">변경할 행의 다른 셀을 클릭 또는 두 번 클릭한 다음 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-121">Click or double-click any other cells in the row you want to change, and enter the new values.</span></span>  
  
6.  <span data-ttu-id="d6637-122">**확인**을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-122">To save the changes, click **OK**</span></span>  
  
##  <a name="create-a-resource-pool-using-transact-sql"></a><a name="CreRPTSQL"></a> <span data-ttu-id="d6637-123">Transact-SQL을 사용하여 리소스 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="d6637-123">Create a Resource Pool Using Transact-SQL</span></span>  
 <span data-ttu-id="d6637-124">**다음을 사용하여 리소스 풀 만들기: [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="d6637-124">**To create a resource pool by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="d6637-125">설정할 속성 값을 지정하여 `CREATE RESOURCE POOL` 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-125">Run the `CREATE RESOURCE POOL` statement specifying the property values to be set.</span></span>  
  
2.  <span data-ttu-id="d6637-126">**ALTER RESOURCE GOVERNOR RECONFIGURE** 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-126">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="d6637-127">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d6637-127">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="d6637-128">다음 예에서는 `poolAdhoc`이라는 리소스 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d6637-128">The following example creates a resource pool named `poolAdhoc`.</span></span>  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6637-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6637-129">See Also</span></span>  
 <span data-ttu-id="d6637-130">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="d6637-130">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="d6637-131">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="d6637-131">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="d6637-132">[리소스 관리자 리소스 풀](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="d6637-132">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="d6637-133">[리소스 풀 설정 변경](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="d6637-133">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="d6637-134">[리소스 풀 삭제](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="d6637-134">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="d6637-135">[템플릿을 사용하여 리소스 관리자 구성](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="d6637-135">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 <span data-ttu-id="d6637-136">[리소스 관리자 작업 그룹](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="d6637-136">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="d6637-137">[리소스 관리자 분류자 함수](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="d6637-137">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="d6637-138">[CREATE RESOURCE POOL&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d6637-138">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="d6637-139">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6637-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
