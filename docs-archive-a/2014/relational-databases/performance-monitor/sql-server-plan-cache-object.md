---
title: SQL Server, Plan Cache 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Plan Cache object
- SQLServer:Plan Cache
ms.assetid: 225e2b02-8d2f-4f29-9eba-f5847c36ea99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 002cbe261c531c18bdbb2170da9694cc8abde89d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729404"
---
# <a name="sql-server-plan-cache-object"></a><span data-ttu-id="edd84-102">SQL Server, Plan Cache 개체</span><span class="sxs-lookup"><span data-stu-id="edd84-102">SQL Server, Plan Cache Object</span></span>
  <span data-ttu-id="edd84-103">**Plan Cache** 개체는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 저장 프로시저, 임시 및 준비된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문, 트리거와 같은 개체를 저장하기 위해 메모리를 사용하는 방법을 모니터링하는 카운터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-103">The **Plan Cache** object provides counters to monitor how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses memory to store objects such as stored procedures, ad hoc and prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, and triggers.</span></span> <span data-ttu-id="edd84-104">**Plan Cache** 개체의 여러 인스턴스를 한 번에 모니터링할 수 있으며 각 인스턴스는 모니터링할 다양한 유형의 계획을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-104">Multiple instances of the **Plan Cache** object can be monitored at the same time, with each instance representing a different type of plan to monitor.</span></span>  
  
 <span data-ttu-id="edd84-105">다음 표에서는 **SQLServer:Plan Cache**카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-105">This table describes are the **SQLServer:Plan Cache**counters.</span></span>  
  
|<span data-ttu-id="edd84-106">SQL Server Plan Cache 카운터</span><span class="sxs-lookup"><span data-stu-id="edd84-106">SQL Server Plan Cache counters</span></span>|<span data-ttu-id="edd84-107">Description</span><span class="sxs-lookup"><span data-stu-id="edd84-107">Description</span></span>|  
|------------------------------------|-----------------|  
|<span data-ttu-id="edd84-108">**Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="edd84-108">**Cache Hit Ratio**</span></span>|<span data-ttu-id="edd84-109">캐시 적중 횟수와 조회 간 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-109">Ratio between cache hits and lookups.</span></span>|  
|<span data-ttu-id="edd84-110">**Cache Object Counts**</span><span class="sxs-lookup"><span data-stu-id="edd84-110">**Cache Object Counts**</span></span>|<span data-ttu-id="edd84-111">캐시에 있는 캐시 개체 수입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-111">Number of cache objects in the cache.</span></span>|  
|<span data-ttu-id="edd84-112">**Cache Pages**</span><span class="sxs-lookup"><span data-stu-id="edd84-112">**Cache Pages**</span></span>|<span data-ttu-id="edd84-113">캐시 개체에 의해 사용되는 8KB 페이지 수입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-113">Number of 8-kilobyte (KB) pages used by cache objects.</span></span>|  
|<span data-ttu-id="edd84-114">**Cache Objects in use**</span><span class="sxs-lookup"><span data-stu-id="edd84-114">**Cache Objects in use**</span></span>|<span data-ttu-id="edd84-115">사용 중인 캐시 개체의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-115">Number of cache objects in use.</span></span>|  
  
 <span data-ttu-id="edd84-116">개체의 각 카운터는 다음 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-116">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="edd84-117">Plan Cache 인스턴스</span><span class="sxs-lookup"><span data-stu-id="edd84-117">Plan Cache instance</span></span>|<span data-ttu-id="edd84-118">Description</span><span class="sxs-lookup"><span data-stu-id="edd84-118">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="edd84-119">**_Total**</span><span class="sxs-lookup"><span data-stu-id="edd84-119">**_Total**</span></span>|<span data-ttu-id="edd84-120">모든 유형의 캐시 인스턴스에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-120">Information for all types of cache instances.</span></span>|  
|<span data-ttu-id="edd84-121">**Sql Plans**</span><span class="sxs-lookup"><span data-stu-id="edd84-121">**Sql Plans**</span></span>|<span data-ttu-id="edd84-122">자동으로 매개 변수가 있는 쿼리를 포함하여 임시 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리에서 생성되는 쿼리 계획이거나 [!INCLUDE[tsql](../../includes/tsql-md.md)] sp_prepare **또는** sp_cursorprepare **를 사용하여 준비된**문으로 생성되는 쿼리 계획입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-122">Query plans produced from an ad hoc [!INCLUDE[tsql](../../includes/tsql-md.md)] query, including auto-parameterized queries, or from [!INCLUDE[tsql](../../includes/tsql-md.md)] statements prepared using **sp_prepare** or **sp_cursorprepare**.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="edd84-123">에서는 동일한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 나중에 실행되는 경우 다시 사용하기 위해 임시 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 대한 계획을 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-123">caches the plans for ad hoc [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for later reuse if the identical [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is later executed.</span></span> <span data-ttu-id="edd84-124">사용자가 매개 변수가 있는 쿼리(명시적으로 준비하지 않은 경우 포함)도 Prepared SQL Plans로 모니터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-124">User-parameterized queries (even if not explicitly prepared) are also monitored as Prepared SQL Plans.</span></span>|  
|<span data-ttu-id="edd84-125">**Object Plans**</span><span class="sxs-lookup"><span data-stu-id="edd84-125">**Object Plans**</span></span>|<span data-ttu-id="edd84-126">저장 프로시저, 함수 또는 트리거를 만들 때 생성되는 쿼리 계획입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-126">Query plans generated by creating a stored procedure, function, or trigger.</span></span>|  
|<span data-ttu-id="edd84-127">**Bound Trees**</span><span class="sxs-lookup"><span data-stu-id="edd84-127">**Bound Trees**</span></span>|<span data-ttu-id="edd84-128">뷰, 규칙, 계산 열 및 CHECK 제약 조건에 대한 정규화된 트리입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-128">Normalized trees for views, rules, computed columns, and check constraints.</span></span>|  
|<span data-ttu-id="edd84-129">**확장 저장 프로시저**</span><span class="sxs-lookup"><span data-stu-id="edd84-129">**Extended Stored Procedures**</span></span>|<span data-ttu-id="edd84-130">확장 저장 프로시저에 대한 카탈로그 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-130">Catalog information for extended stores procedures.</span></span>|  
|<span data-ttu-id="edd84-131">**Temporary Tables & Table Variables**</span><span class="sxs-lookup"><span data-stu-id="edd84-131">**Temporary Tables & Table Variables**</span></span>|<span data-ttu-id="edd84-132">임시 테이블 및 테이블 변수와 관련된 캐시 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="edd84-132">Cache information related to temporary tables and table variables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="edd84-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="edd84-133">See Also</span></span>  
 <span data-ttu-id="edd84-134">[서버 메모리 서버 구성 옵션](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="edd84-134">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="edd84-135">[SQL Server, Buffer Manager 개체](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="edd84-135">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="edd84-136">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="edd84-136">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
