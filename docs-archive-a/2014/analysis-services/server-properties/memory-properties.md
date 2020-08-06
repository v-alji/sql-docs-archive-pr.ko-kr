---
title: 메모리 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LowMemoryLimit property
- MinimumAllocatedMemory property
- MidMemoryPrice property
- MemoryHeapType property
- memory [Analysis Services]
- DefaultPagesCountToReuse property
- TotalMemoryLimit property
- SessionMemoryLimit property
- VirtualMemoryLimit property
- WaitCountIfHighMemory property
- HighMemoryPrice property
- HeapTypeForObjects property
ms.assetid: 085f5195-7b2c-411a-9813-0ff5c6066d13
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f2d2e56c9a951cee27752bd57d55d185a9b6618
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743483"
---
# <a name="memory-properties"></a><span data-ttu-id="3a849-102">메모리 속성</span><span class="sxs-lookup"><span data-stu-id="3a849-102">Memory Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="3a849-103">에서는 다음 표에 나열된 서버 메모리 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-103">supports the server memory properties listed in the following table.</span></span> <span data-ttu-id="3a849-104">이 속성 설정에 대한 지침을 보려면 [SQL Server 2008 R2 Analysis Services 작업 가이드](https://go.microsoft.com/fwlink/?LinkID=225539)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a849-104">For guidance in setting these properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 <span data-ttu-id="3a849-105">1과 100 사이의 값은 **실제 총 메모리** 또는 **가상 주소 공간**중 더 작은 쪽의 백분율을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-105">Values between 1 and 100 represent percentages of **Total Physical Memory** or **Virtual Address Space**, whichever is less.</span></span> <span data-ttu-id="3a849-106">100을 초과하는 값은 메모리 제한(바이트)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-106">Values over 100 represent memory limits in bytes.</span></span>  
  
 <span data-ttu-id="3a849-107">**적용 대상:** 다차원 및 테이블 형식 서버 모드 (다르게 표시 되지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="3a849-107">**Applies to:** Multidimensional and Tabular server mode, unless noted otherwise.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3a849-108">속성</span><span class="sxs-lookup"><span data-stu-id="3a849-108">Properties</span></span>  
 `LowMemoryLimit`  
 <span data-ttu-id="3a849-109">서버에서 메모리가 부족한 시점을 총 실제 메모리의 백분율로 표시한 부호 있는 64비트 배정밀도 부동 소수점 숫자 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-109">A signed 64-bit double-precision floating-point number property that defines the point at which the server is low on memory, expressed as percentage of total physical memory.</span></span> <span data-ttu-id="3a849-110">이 제한에 도달하면 인스턴스는 만료된 세션을 닫고 사용되지 않는 계산을 언로드하여 천천히 캐시 메모리를 지우기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-110">When this limit is reached, the instance will start to slowly clear memory out of caches by closing expired sessions and unloading unused calculations.</span></span> <span data-ttu-id="3a849-111">서버는 이 제한 아래로 메모리를 해제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-111">The server will not release memory below this limit.</span></span> <span data-ttu-id="3a849-112">기본값은 65이며 이 경우 메모리 하한은 실제 메모리 또는 가상 주소 공간의 65% 중 더 작은 쪽으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-112">The default value is 65; which indicates the low memory limit is 65% of physical memory or the virtual address space, whichever is less.</span></span>  
  
 `TotalMemoryLimit`  
 <span data-ttu-id="3a849-113">서버가 더 적극적으로 메모리 할당을 취소하기 시작하는 임계값을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-113">Defines a threshold that when reached, causes the server to deallocate memory more aggressively.</span></span> <span data-ttu-id="3a849-114">기본값은 실제 메모리 또는 가상 주소 공간의 80% 중 더 작은 쪽입니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-114">The default value 80% of physical memory or the virtual address space, whichever is less.</span></span>  
  
 <span data-ttu-id="3a849-115">`TotalMemoryLimit`는 항상 `HardMemoryLimit`보다 작아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-115">Note that `TotalMemoryLimit` must always be less than `HardMemoryLimit`</span></span>  
  
 `HardMemoryLimit`  
 <span data-ttu-id="3a849-116">인스턴스가 메모리 사용량을 줄이기 위해 활성 사용자 세션을 적극적으로 종료하기 시작하는 메모리 임계값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-116">Specifies a memory threshold after which the instance aggressively terminates active user sessions to reduce memory usage.</span></span> <span data-ttu-id="3a849-117">종료된 모든 세션은 메모리 부족으로 인해 취소되고 있다는 오류를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-117">All terminated sessions will receive an error about being cancelled by memory pressure.</span></span> <span data-ttu-id="3a849-118">기본값 영(0)은 `HardMemoryLimit`이 `TotalMemoryLimit`과 시스템의 실제 총 메모리 사이의 중간 값으로 설정됨을 의미합니다. 시스템의 실제 메모리가 프로세스의 가상 주소 공간보다 큰 경우 `HardMemoryLimit`을 계산할 때 가상 주소 공간이 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-118">The default value, zero (0), means the `HardMemoryLimit` will be set to a midway value between `TotalMemoryLimit` and the total physical memory of the system; if the physical memory of the system is larger than the virtual address space of the process, then virtual address space will be used instead to calculate `HardMemoryLimit`.</span></span>  
  
 `VirtualMemoryLimit`  
 <span data-ttu-id="3a849-119">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-119">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `VertiPaqPagingPolicy`  
 <span data-ttu-id="3a849-120">서버의 메모리가 부족한 경우에 발생하는 페이징 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-120">Specifies the paging behavior in the event the server runs low on memory.</span></span> <span data-ttu-id="3a849-121">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-121">Valid values are as follows:</span></span>  
  
 <span data-ttu-id="3a849-122">0(**0**)은 페이징을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-122">Zero (**0**) disables paging.</span></span> <span data-ttu-id="3a849-123">메모리가 부족하면 메모리 부족 오류로 처리가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-123">If memory is insufficient, processing fails with an out-of-memory error.</span></span> <span data-ttu-id="3a849-124">페이징을 사용하지 않도록 설정한 경우 서비스 계정에 대한 권한을 Windows에 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-124">If you disable paging, you must grant Windows privileges to the service account.</span></span> <span data-ttu-id="3a849-125">자세한 내용은 [서비스 계정 구성&#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a849-125">See [Configure Service Accounts &#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md) for instructions.</span></span>  
  
 <span data-ttu-id="3a849-126">**1** 은 기본값이며</span><span class="sxs-lookup"><span data-stu-id="3a849-126">**1** is the default.</span></span> <span data-ttu-id="3a849-127">운영 체제 페이지 파일(pagefile.sys)을 통해 디스크로의 페이징을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-127">This property enables paging to disk using the operating system page file (pagefile.sys).</span></span>  
  
 <span data-ttu-id="3a849-128">`VertiPaqPagingPolicy`가 1로 설정될 경우 서버는 지정된 방법을 사용하여 디스크로 페이징을 시도하기 때문에 메모리 제약 조건으로 인해 처리가 실패할 가능성이 적습니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-128">When `VertiPaqPagingPolicy` is set to 1, processing is less likely to fail due to memory constraints because the server will try to page to disk using the method that you specified.</span></span> <span data-ttu-id="3a849-129">`VertiPaqPagingPolicy`속성을 설정한다고 해서 메모리 오류가 절대로 발생하지 않는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-129">Setting the `VertiPaqPagingPolicy` property does not guarantee that memory errors will never happen.</span></span> <span data-ttu-id="3a849-130">다음과 같은 상황에서 메모리 부족 오류가 여전히 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-130">Out of memory errors can still occur under the following conditions:</span></span>  
  
-   <span data-ttu-id="3a849-131">모든 사전에 대해 메모리가 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-131">There is not enough memory for all dictionaries.</span></span> <span data-ttu-id="3a849-132">처리 중 Analysis Services는 메모리의 각 열에 대해 사전을 잠그며 이 모든 합은 `VertiPaqMemoryLimit`에 대해 지정된 값보다 클 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-132">During processing, Analysis Services locks the dictionaries for each column in memory, and all of these together cannot be more than the value specified for `VertiPaqMemoryLimit`.</span></span>  
  
-   <span data-ttu-id="3a849-133">프로세스를 수용하기에 가상 주소 공간이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-133">There is insufficient virtual address space to accommodate the process.</span></span>  
  
 <span data-ttu-id="3a849-134">지속적인 메모리 오류를 해결하려면 처리해야 할 데이터의 양을 줄이도록 모델을 다시 디자인하거나, 컴퓨터에 메모리를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-134">To resolve persistent out of memory errors, you can either try to redesign the model to reduce the amount of data that needs processing, or you can add more physical memory to the computer.</span></span>  
  
 <span data-ttu-id="3a849-135">테이블 형식 서버 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-135">Applies to tabular server mode only.</span></span>  
  
 `VertiPaqMemoryLimit`  
 <span data-ttu-id="3a849-136">디스크로의 페이징이 허용되는 경우 이 속성은 페이징이 시작되는 메모리 소비 수준(총 메모리에 대한 백분율)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-136">If paging to disk is allowed, this property specifies the level of memory consumption (as a percentage of total memory) at which paging starts.</span></span> <span data-ttu-id="3a849-137">기본값은 60입니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-137">The default is 60.</span></span> <span data-ttu-id="3a849-138">메모리 소비가 60% 이하이면 서버가 디스크로 페이징하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-138">If memory consumption is less than 60 percent, the server will not page to disk.</span></span>  
  
 <span data-ttu-id="3a849-139">이 속성을 사용하려면 `VertiPaqPagingPolicyProperty`를 1로 설정하여 페이징이 발생할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-139">This property depends on the `VertiPaqPagingPolicyProperty`, which must be set to 1 in order for paging to occur.</span></span>  
  
 <span data-ttu-id="3a849-140">테이블 형식 서버 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-140">Applies to tabular server mode only.</span></span>  
  
 `HighMemoryPrice`  
 <span data-ttu-id="3a849-141">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryHeapType`  
 <span data-ttu-id="3a849-142">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="3a849-143">다차원 서버 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-143">Applies to multidimensional server mode only.</span></span>  
  
 `HeapTypeForObjects`  
 <span data-ttu-id="3a849-144">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-144">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="3a849-145">다차원 서버 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-145">Applies to multidimensional server mode only.</span></span>  
  
 `DefaultPagesCountToReuse`  
 <span data-ttu-id="3a849-146">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-146">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `HandleIA64AlignmentFaults`  
 <span data-ttu-id="3a849-147">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-147">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MidMemoryPrice`  
 <span data-ttu-id="3a849-148">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-148">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinimumAllocatedMemory`  
 <span data-ttu-id="3a849-149">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-149">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PreAllocate`  
 <span data-ttu-id="3a849-150">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SessionMemoryLimit`  
 <span data-ttu-id="3a849-151">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `WaitCountIfHighMemory`  
 <span data-ttu-id="3a849-152">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a849-152">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a849-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a849-153">See Also</span></span>  
 <span data-ttu-id="3a849-154">[Analysis Services에서 서버 속성 구성](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="3a849-154">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="3a849-155">Analysis Services 인스턴스의 서버 모드 확인</span><span class="sxs-lookup"><span data-stu-id="3a849-155">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
