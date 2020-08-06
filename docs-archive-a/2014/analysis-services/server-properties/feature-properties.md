---
title: 기능 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 08001a172c1b39fb912ef042ed85effd4f8ededa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743504"
---
# <a name="feature-properties"></a><span data-ttu-id="69b4a-102">기능 속성</span><span class="sxs-lookup"><span data-stu-id="69b4a-102">Feature Properties</span></span>
  <span data-ttu-id="69b4a-103">기능 속성은 서버 인스턴스 간 연결을 제어하는 속성을 비롯한 제품 기능(대부분 고급 기능)에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-103">Feature properties pertain to product features, most of them advanced, including properties that control links between server instances.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="69b4a-104">에서는 다음 표에 나열된 서버 속성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-104">supports the server properties listed in the following table.</span></span> <span data-ttu-id="69b4a-105">추가 서버 속성 및 해당 속성 설정 방법은 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69b4a-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="69b4a-106">**적용 대상:** 다차원 서버 모드에만 해당</span><span class="sxs-lookup"><span data-stu-id="69b4a-106">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="properties"></a><span data-ttu-id="69b4a-107">속성</span><span class="sxs-lookup"><span data-stu-id="69b4a-107">Properties</span></span>  
  
|<span data-ttu-id="69b4a-108">속성</span><span class="sxs-lookup"><span data-stu-id="69b4a-108">Property</span></span>|<span data-ttu-id="69b4a-109">기본값</span><span class="sxs-lookup"><span data-stu-id="69b4a-109">Default</span></span>|<span data-ttu-id="69b4a-110">Description</span><span class="sxs-lookup"><span data-stu-id="69b4a-110">Description</span></span>|  
|--------------|-------------|-----------------|  
|`ManagedCodeEnabled`|<span data-ttu-id="69b4a-111">1</span><span class="sxs-lookup"><span data-stu-id="69b4a-111">1</span></span>|<span data-ttu-id="69b4a-112">CLR 스토리지 프로시저가 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-112">A Boolean property that indicates whether CLR storage procedures are enabled.</span></span>|  
|`LinkInsideInstanceEnabled`|<span data-ttu-id="69b4a-113">1</span><span class="sxs-lookup"><span data-stu-id="69b4a-113">1</span></span>|<span data-ttu-id="69b4a-114">연결된 개체를 동일 서버 인스턴스 내에 만들 수 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-114">A Boolean property that indicates whether a linked object can be created inside the same server instance.</span></span>|  
|`LinkToOtherInstanceEnabled`|<span data-ttu-id="69b4a-115">0</span><span class="sxs-lookup"><span data-stu-id="69b4a-115">0</span></span>|<span data-ttu-id="69b4a-116">원격 서버의 개체를 연결할 수 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-116">A Boolean property that indicates whether objects on remote servers can be linked to.</span></span>|  
|`LinkFromOtherInstanceEnabled`|<span data-ttu-id="69b4a-117">0</span><span class="sxs-lookup"><span data-stu-id="69b4a-117">0</span></span>|<span data-ttu-id="69b4a-118">개체를 다른 서버 인스턴스로부터 연결할 수 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-118">A Boolean property that indicates whether objects can be linked to from other server instances.</span></span>|  
|`ConnStringEncryptionEnabled`|<span data-ttu-id="69b4a-119">1</span><span class="sxs-lookup"><span data-stu-id="69b4a-119">1</span></span>|<span data-ttu-id="69b4a-120">연결 문자열이 서버 구성 파일에 암호화되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-120">A Boolean property that indicates whether the connection string is encrypted in the server configuration file.</span></span>|  
|`UseCachedPageAllocators`|<span data-ttu-id="69b4a-121">0</span><span class="sxs-lookup"><span data-stu-id="69b4a-121">0</span></span>|<span data-ttu-id="69b4a-122">캐시된 페이지 할당자가 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-122">A Boolean property that indicates whether cached page allocators are enabled.</span></span>|  
|`ComUdfEnabled`|<span data-ttu-id="69b4a-123">0</span><span class="sxs-lookup"><span data-stu-id="69b4a-123">0</span></span>|<span data-ttu-id="69b4a-124">COM 개체로 정의된 사용자 정의 함수가 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-124">A Boolean property that indicates whether user-defined functions defined as COM objects are enabled.</span></span>|  
|`SQMSupportEnabled`|<span data-ttu-id="69b4a-125">1</span><span class="sxs-lookup"><span data-stu-id="69b4a-125">1</span></span>|<span data-ttu-id="69b4a-126">오류 및 기능 사용 보고서를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 로 자동으로 보낼지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-126">A Boolean property that indicates whether error and feature usage reports are sent to [!INCLUDE[msCoName](../../includes/msconame-md.md)] automatically.</span></span>|  
|`ResourceMonitoringEnabled`|<span data-ttu-id="69b4a-127">1</span><span class="sxs-lookup"><span data-stu-id="69b4a-127">1</span></span>|<span data-ttu-id="69b4a-128">내부 리소스 모니터링 카운터를 사용할 수 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-128">A Boolean property that indicates whether internal resource monitoring counters are enabled.</span></span> <span data-ttu-id="69b4a-129">이 속성은 기본적으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-129">This property is on by default.</span></span> <span data-ttu-id="69b4a-130">이 속성을 사용하도록 설정되어 있으면 카운터에서 CPU, 메모리 및 I/O 작업에 대한 사용량 현황 데이터를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-130">When enabled, this property allows counters to collect usage data about CPU, memory, and I/O activity.</span></span><br /><br /> <span data-ttu-id="69b4a-131">내부 리소스 모니터링 카운터는 리소스 사용률에 대해 보고하는 DMV(동적 관리 뷰)에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-131">Internal resource monitoring counters are used by Dynamic Management Views (DMV) that report on resource utilization.</span></span> <span data-ttu-id="69b4a-132">이 속성을 사용하지 않도록 설정하는 경우 DMV 쿼리는 계속 실행되지만 결과 집합은 유효하지 않은 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-132">If you disable this property, the DMV queries will still run, but the result set will be invalid.</span></span> <span data-ttu-id="69b4a-133">이 속성에 따라 달라지는 DMV는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-133">DMVs that depend on this property include the following:</span></span><br /><span data-ttu-id="69b4a-134">**DISCOVER_OBJECT_ACTIVITY**</span><span class="sxs-lookup"><span data-stu-id="69b4a-134">**DISCOVER_OBJECT_ACTIVITY**</span></span><br /><span data-ttu-id="69b4a-135">**DISCOVER_COMMAND_OBJECTS**</span><span class="sxs-lookup"><span data-stu-id="69b4a-135">**DISCOVER_COMMAND_OBJECTS**</span></span><br /><span data-ttu-id="69b4a-136">**DISCOVER_SESSIONS** (SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS의 경우)</span><span class="sxs-lookup"><span data-stu-id="69b4a-136">**DISCOVER_SESSIONS** (for SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)</span></span><br /><br /> <br /><br /> <span data-ttu-id="69b4a-137">NUMA 아키텍처를 사용하는 다중 코어 시스템에서 이 속성을 사용하지 않도록 설정하면 특히 다중 사용자 작업량이 많은 경우 쿼리 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-137">On a multi-core system that uses NUMA architecture, disabling this property can improve query performance, particularly for high multi-user workloads.</span></span> <span data-ttu-id="69b4a-138">이 속성을 변경한 결과로 쿼리 성능이 향상되는지 여부를 확인하려면 비교 테스트를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b4a-138">You will need to run comparison tests to determine whether query performance is improved as the result of changing this property.</span></span> <span data-ttu-id="69b4a-139">캐시를 지우고 일반적인 실수를 피하는 등 비교 테스트 실행에 대한 최상의 방법을 보려면 [SQL Server 2008 R2 Analysis Services 작업 가이드](https://go.microsoft.com/fwlink/?LinkID=225539)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="69b4a-139">For best practices on running comparison tests, including clearing the cache and avoiding common mistakes, see the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69b4a-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69b4a-140">See Also</span></span>  
 <span data-ttu-id="69b4a-141">[Analysis Services에서 서버 속성 구성](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="69b4a-141">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="69b4a-142">[Analysis Services 인스턴스의 서버 모드 확인](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="69b4a-142">[Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 [<span data-ttu-id="69b4a-143">DMV&#40;동적 관리 뷰&#41;를 사용하여 Analysis Services 모니터링</span><span class="sxs-lookup"><span data-stu-id="69b4a-143">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
