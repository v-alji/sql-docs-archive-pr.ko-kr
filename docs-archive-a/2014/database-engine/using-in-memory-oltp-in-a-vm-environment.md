---
title: VM 환경에서 메모리 내 OLTP 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 27ec7eb3-3a24-41db-aa65-2f206514c6f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83cf785fbcd2df9449d61e328e3bf8e374a6656d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732007"
---
# <a name="using-in-memory-oltp-in-a-vm-environment"></a><span data-ttu-id="71cda-102">VM 환경에서 메모리 내 OLTP 사용</span><span class="sxs-lookup"><span data-stu-id="71cda-102">Using In-Memory OLTP in a VM Environment</span></span>
  <span data-ttu-id="71cda-103">서버 가상화 기술을 사용하면 IT 자본 및 운영 비용을 줄이고 향상된 애플리케이션 프로비전, 유지 관리, 가용성 및 백업/복구 프로세스를 통해 IT 효율성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-103">Server virtualization can help you lower IT capital and operational costs and attain greater IT efficiency with improved application provisioning, maintenance, availability, and backup/recovery processes.</span></span> <span data-ttu-id="71cda-104">최근의 기술적 진보에 따라 가상화를 사용하면 복잡한 데이터베이스 작업도 보다 쉽고 간단하게 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-104">With recent technological advances, complex database workloads can be more readily consolidated using virtualization.</span></span> <span data-ttu-id="71cda-105">이 항목에서는 가상화된 환경에서 [!INCLUDE[hek_1](../includes/hek-1-md.md)] 를 사용하기 위한 모범 사례에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-105">This topic covers best practices for using [!INCLUDE[hek_1](../includes/hek-1-md.md)] in a virtualized environment.</span></span>  
  
##  <a name="memory-pre-allocation"></a><a name="bkmk_memoryPreAllocation"></a><span data-ttu-id="71cda-106">메모리 사전 할당</span><span class="sxs-lookup"><span data-stu-id="71cda-106">Memory pre-allocation</span></span>  
 <span data-ttu-id="71cda-107">가상화된 환경의 메모리에 대해 필수적으로 고려해야 할 사항은 더 나은 성능과 향상된 지원 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-107">For memory in a virtualized environment, better performance and enhanced support are essential considerations.</span></span> <span data-ttu-id="71cda-108">요구 사항(최대 및 최소 부하)에 따라 가상 컴퓨터에 메모리를 신속하게 할당하면서도 메모리가 낭비되지 않도록 방지하는 두 마리 토끼를 모두 잡아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-108">You must be able to both quickly allocate memory to virtual machines depending on their requirements (peak and off-peak loads) and ensure that the memory is not wasted.</span></span> <span data-ttu-id="71cda-109">Hyper-V 동적 메모리 기능을 사용하면 호스트에서 실행되는 가상 컴퓨터 간에 메모리를 할당하고 관리하는 작업을 신속하게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-109">The Hyper-V Dynamic Memory feature increases agility in how the memory is allocated and managed between virtual machines running on a host.</span></span>  
  
 <span data-ttu-id="71cda-110">메모리 최적화 테이블이 포함된 데이터베이스를 가상화할 때는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가상화 및 관리를 위한 일부 모범 사례에 대한 수정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-110">Some best practices for virtualizing and managing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] need to be modified when virtualizing a database with memory-optimized tables.</span></span> <span data-ttu-id="71cda-111">메모리 최적화 테이블이 없는 경우의 모범 사례 중 두 가지는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-111">Without memory-optimized tables, two of the best practices are:</span></span>  
  
-   <span data-ttu-id="71cda-112">MIN_SERVER_MEMORY를 사용하는 경우에는 다른 프로세스용으로 메모리가 충분히 남아 있도록 필요한 양의 메모리만 할당하여 페이징이 수행되지 않도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-112">If you use MIN_SERVER_MEMORY, it is better to assign only the amount of memory that is required so sufficient memory remains for other processes (thereby avoiding paging).</span></span>  
  
-   <span data-ttu-id="71cda-113">메모리 미리 할당 값은 너무 높게 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="71cda-113">Do not set the memory pre-allocation value too high.</span></span> <span data-ttu-id="71cda-114">그렇지 않으면 다른 프로세스에 메모리가 필요할 때 충분한 메모리를 사용하지 못하게 되어 메모리 페이징이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-114">Otherwise, other processes may not get sufficient memory at the time when they require it, and this can result in memory paging.</span></span>  
  
 <span data-ttu-id="71cda-115">메모리 최적화 테이블이 포함된 데이터베이스에서 위와 같은 방식을 따를 경우 데이터베이스 복구에 사용할 수 있는 메모리가 충분하더라도 데이터베이스를 복원 및 복구하려고 하면 데이터베이스가 "복구 보류 중" 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-115">If you follow the above practices for a database with memory-optimized tables, an attempt to restore and recover a database could result in the database being in a "Recovery Pending" state, even if you have sufficient memory to recover the database.</span></span> <span data-ttu-id="71cda-116">그 이유는 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 는 시작 시 동적 메모리 할당이 데이터베이스에 메모리를 할당하는 것보다 더 많은 데이터를 메모리로 가져오기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="71cda-116">The reason for this is that, when starting up, [!INCLUDE[hek_2](../includes/hek-2-md.md)] brings data into memory more aggressively than dynamic memory allocation allocates memory to the database.</span></span>  
  
 <span data-ttu-id="71cda-117">**해결 방법**</span><span class="sxs-lookup"><span data-stu-id="71cda-117">**Resolution**</span></span>  
  
 <span data-ttu-id="71cda-118">이 문제를 완화하기 위해서는 필요할 때 추가 메모리를 제공하기 위한 동적 메모리에 따라 달라지는 최소 값이 아니라 데이터베이스를 복구 또는 다시 시작하기 위한 충분한 메모리를 데이터베이스에 미리 할당하십시오.</span><span class="sxs-lookup"><span data-stu-id="71cda-118">To mitigate this, pre-allocate sufficient memory to the database to recover or restart the database, not a minimum value relying on dynamic memory to provide the additional memory when needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71cda-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71cda-119">See Also</span></span>  
 [<span data-ttu-id="71cda-120">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="71cda-120">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
