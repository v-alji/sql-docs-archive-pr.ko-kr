---
title: 파일 저장소 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Income property
- InitialBonus property
- PercentScanPerPrice property
- FileStore properties
- BackgroundTrimCost property
- Tax property
- PerformanceTrace property
- MinimumBalance property
- UnbufferedThreshold property
- BackgroundTrimAmount property
- MaximumBalance property
- MemoryLimitMin property
- MemoryLimit property
ms.assetid: 580cf0aa-7425-4d48-aa8d-128f5b488fcd
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc81273b55dea5820ef80f34c22d293492eb8055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743500"
---
# <a name="filestore-properties"></a><span data-ttu-id="d1f03-102">FileStore 속성</span><span class="sxs-lookup"><span data-stu-id="d1f03-102">Filestore Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d1f03-103">에서는 다음 표에 나열된 파일 저장소 서버 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-103">supports the filestore server properties listed in the following tables.</span></span> <span data-ttu-id="d1f03-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 이 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-104">These are all advanced properties that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span> <span data-ttu-id="d1f03-105">추가 서버 속성 및 해당 속성 설정 방법은 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1f03-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="d1f03-106">**적용 대상:** 다차원 및 테이블 형식 서버 모드</span><span class="sxs-lookup"><span data-stu-id="d1f03-106">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d1f03-107">속성</span><span class="sxs-lookup"><span data-stu-id="d1f03-107">Properties</span></span>  
 `MemoryLimit`  
 <span data-ttu-id="d1f03-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-108">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryLimitMin`  
 <span data-ttu-id="d1f03-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PercentScanPerPrice`  
 <span data-ttu-id="d1f03-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PerformanceTrace`  
 <span data-ttu-id="d1f03-111">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-111">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `RandomFileAccessMode`  
 <span data-ttu-id="d1f03-112">데이터베이스 파일 및 캐시된 파일을 임의 파일 액세스 모드로 액세스하는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-112">A Boolean property that indicates whether database files and cached files are accessed in random file access mode.</span></span> <span data-ttu-id="d1f03-113">이 속성은 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-113">This property is off by default.</span></span> <span data-ttu-id="d1f03-114">기본적으로 읽기 액세스를 위해 파티션 데이터 파일을 열 때 Analysis Services는 임의 파일 액세스 플래그를 설정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-114">By default, Analysis Services does not set the random file access flag when opening partition data files for read access.</span></span>  
  
 <span data-ttu-id="d1f03-115">특히 대용량 리소스 및 여러 NUMA 노드가 있는 고성능 시스템에서는 임의 파일 액세스를 사용하는 편이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-115">On high-end systems, particularly those with large memory resources and multiple NUMA nodes, it can be advantageous to use random file access.</span></span> <span data-ttu-id="d1f03-116">임의 액세스 모드에서 Windows는 디스크에서 시스템 파일 캐시로 데이터를 읽는 페이지 매핑 작업을 건너뛰므로 캐시 경합을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-116">In random access mode, Windows bypasses page mapping operations that read data from disk into the system file cache, thereby lowering contention on the cache.</span></span>  
  
 <span data-ttu-id="d1f03-117">이 속성을 변경한 결과로 쿼리 성능이 향상되는지 여부를 확인하려면 비교 테스트를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-117">You will need to run comparison tests to determine whether query performance is improved as the result of changing this property.</span></span> <span data-ttu-id="d1f03-118">캐시를 지우고 일반적인 실수를 피하는 등 비교 테스트 실행에 대한 최상의 방법을 보려면 [SQL Server 2008 R2 Analysis Services 작업 가이드](https://go.microsoft.com/fwlink/?LinkID=225539)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d1f03-118">For best practices on running comparison tests, including clearing the cache and avoiding common mistakes, see the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span> <span data-ttu-id="d1f03-119">이 속성을 사용할 때의 장단점에 대 한 자세한 내용은을 참조 하십시오 [https://support.microsoft.com/kb/2549369](https://support.microsoft.com/kb/2549369) .</span><span class="sxs-lookup"><span data-stu-id="d1f03-119">For additional information on the tradeoffs of using this property, see [https://support.microsoft.com/kb/2549369](https://support.microsoft.com/kb/2549369).</span></span>  
  
 <span data-ttu-id="d1f03-120">Management Studio에서 이 속성을 보거나 수정하려면 서버 속성 페이지에서 고급 설정 목록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-120">To view or modify this property in Management Studio, enable the advanced properties list in the server properties page.</span></span> <span data-ttu-id="d1f03-121">msmdsrv.ini 파일에서 속성을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-121">You can also change the property in the msmdsrv.ini file.</span></span> <span data-ttu-id="d1f03-122">이 속성을 설정한 후 서버를 다시 시작하는 것이 좋습니다. 그렇지 않으면 이미 열려 있는 파일이 이전 모드로 계속 액세스됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-122">Restarting the server is recommended after setting this property; otherwise files that are already open will continue to be accessed in the previous mode.</span></span>  
  
 `UnbufferedThreshold`  
 <span data-ttu-id="d1f03-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-123">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="memory-model-category"></a><span data-ttu-id="d1f03-124">메모리 모델 범주</span><span class="sxs-lookup"><span data-stu-id="d1f03-124">Memory Model Category</span></span>  
 `MemoryModel\Tax`  
 <span data-ttu-id="d1f03-125">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-125">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\Income`  
 <span data-ttu-id="d1f03-126">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-126">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\MaximumBalance`  
 <span data-ttu-id="d1f03-127">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-127">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\MinimumBalance`  
 <span data-ttu-id="d1f03-128">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-128">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryModel\InitialBonus`  
 <span data-ttu-id="d1f03-129">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1f03-129">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f03-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1f03-130">See Also</span></span>  
 <span data-ttu-id="d1f03-131">[Analysis Services에서 서버 속성 구성](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d1f03-131">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="d1f03-132">Analysis Services 인스턴스의 서버 모드 확인</span><span class="sxs-lookup"><span data-stu-id="d1f03-132">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
