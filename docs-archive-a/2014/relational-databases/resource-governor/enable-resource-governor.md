---
title: 리소스 관리자 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b1b0f780457aa5a4d26cbb463c9f31a94185f0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731472"
---
# <a name="enable-resource-governor"></a><span data-ttu-id="1df6f-102">리소스 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="1df6f-102">Enable Resource Governor</span></span>
  <span data-ttu-id="1df6f-103">리소스 관리자는 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-103">The Resource Governor is turned off by default.</span></span> <span data-ttu-id="1df6f-104">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 Transact-SQL을 사용하여 리소스 관리자를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-104">You can enable the Resource Governor by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="1df6f-105">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="1df6f-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="1df6f-106">**Resource Governor를 사용하도록 설정하려면 다음을 사용합니다.**  [개체 탐색기](#RGOnObjEx), [Resource Governor 속성](#RGOnProp) 또는 [Transact-SQL](#RGOnTSQL)</span><span class="sxs-lookup"><span data-stu-id="1df6f-106">**To enable Resource Governorn, using:**  [Object Explorer](#RGOnObjEx), [Resource Governor Properties](#RGOnProp), [Transact-SQL](#RGOnTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1df6f-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1df6f-107">Before You Begin</span></span>  
 <span data-ttu-id="1df6f-108">리소스 관리자를 사용하도록 설정하면 다음과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-108">Enabling the resource governor has the following results:</span></span>  
  
-   <span data-ttu-id="1df6f-109">작업 그룹에 해당 작업을 할당할 수 있도록 새 연결에 대해 분류자 함수가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-109">The classifier function is run for new connections so that their workloads can be assigned to workload groups.</span></span>  
  
-   <span data-ttu-id="1df6f-110">리소스 관리자 구성에 지정된 리소스 제한이 강제로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-110">The resource limits that are specified in the Resource Governor configuration are honored and enforced.</span></span>  
  
-   <span data-ttu-id="1df6f-111">리소스 관리자를 사용하도록 설정하기 전부터 있었던 요청은 리소스 관리자를 사용하지 않도록 설정했을 때 변경한 구성에 의해 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-111">Requests that existed before enabling Resource Governor are affected by any configuration changes that were made when the Resource Governor was disabled.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="1df6f-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1df6f-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1df6f-113">사용자 트랜잭션에 있을 때에는 `ALTER RESOURCE GOVERNOR` 문을 사용하여 리소스 관리자를 사용하도록 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-113">You cannot use the `ALTER RESOURCE GOVERNOR` statement to enable Resource Governor when in a user transaction.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1df6f-114">권한</span><span class="sxs-lookup"><span data-stu-id="1df6f-114">Permissions</span></span>  
 <span data-ttu-id="1df6f-115">리소스 관리자를 사용하도록 설정하려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-115">Enabling the Resource Governor requires CONTROL SERVER permission.</span></span>  
  
##  <a name="enable-resource-governor-using-object-explorer"></a><a name="RGOnObjEx"></a> <span data-ttu-id="1df6f-116">개체 탐색기를 사용하여 리소스 관리자를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="1df6f-116">Enable Resource Governor Using Object Explorer</span></span>  
 <span data-ttu-id="1df6f-117">**개체 탐색기를 사용하여 리소스 관리자를 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="1df6f-117">**To enable the Resource Governor by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="1df6f-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **리소스 관리자** 까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="1df6f-119">**Resource Governor**를 마우스 오른쪽 단추로 클릭한 다음 **사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-119">Right-click **Resource Governor**, and then click **Enable**.</span></span>  
  
##  <a name="enable-resource-governor-using-resource-governor-properties"></a><a name="RGOnProp"></a> <span data-ttu-id="1df6f-120">리소스 관리자 속성을 사용하여 리소스 관리자를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="1df6f-120">Enable Resource Governor Using Resource Governor Properties</span></span>  
 <span data-ttu-id="1df6f-121">**리소스 관리자 속성 페이지를 사용하여 리소스 관리자를 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="1df6f-121">**To enable the Resource Governor by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="1df6f-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **리소스 관리자** 까지 **관리**노드를 계속 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="1df6f-123">**Resource Governor** 를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다. 그러면 **Resource Governor** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-123">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="1df6f-124">**리소스 관리자 사용** 확인란을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-124">Click the **Enable Resource Governor** check box, and then click **OK**.</span></span>  
  
##  <a name="enable-resource-governor-using-transact-sql"></a><a name="RGOnTSQL"></a> <span data-ttu-id="1df6f-125">Transact-SQL을 사용하여 리소스 관리자를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="1df6f-125">Enable Resource Governor Using Transact-SQL</span></span>  
 <span data-ttu-id="1df6f-126">**Transact-SQL을 사용하여 리소스 관리자를 사용하도록 설정**</span><span class="sxs-lookup"><span data-stu-id="1df6f-126">**To enable the Resource Governor by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="1df6f-127">**ALTER RESOURCE GOVERNOR RECONFIGURE** 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-127">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="1df6f-128">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1df6f-128">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="1df6f-129">다음 예에서는 리소스 관리자를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1df6f-129">The following example enables the Resource Governor.</span></span>  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="1df6f-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1df6f-130">See Also</span></span>  
 <span data-ttu-id="1df6f-131">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="1df6f-131">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="1df6f-132">[리소스 관리자 사용 안 함](disable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="1df6f-132">[Disable Resource Governor](disable-resource-governor.md) </span></span>  
 <span data-ttu-id="1df6f-133">[리소스 관리자 리소스 풀](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="1df6f-133">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="1df6f-134">[리소스 관리자 작업 그룹](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="1df6f-134">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="1df6f-135">[리소스 관리자 분류자 함수](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="1df6f-135">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 [<span data-ttu-id="1df6f-136">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1df6f-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
