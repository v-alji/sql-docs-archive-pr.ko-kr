---
title: 전체 텍스트 검색 업그레이드 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- Full-Text Search
- Upgrade options, Full-Text Search
ms.assetid: 16c9376b-5fbb-4495-a429-06a2493849c9
author: rothja
ms.author: jroth
ms.openlocfilehash: ade7a05563598440c3fdc79dd4b3584f7f797d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730052"
---
# <a name="full-text-search-upgrade-options"></a><span data-ttu-id="ac8fe-102">전체 텍스트 검색 업그레이드 옵션</span><span class="sxs-lookup"><span data-stu-id="ac8fe-102">Full-Text Search Upgrade Options</span></span>
  <span data-ttu-id="ac8fe-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사의 전체 텍스트 검색 업그레이드 옵션 페이지에서 현재 업그레이드 중인 데이터베이스에 사용할 전체 텍스트 검색 업그레이드 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-103">Use the Full-Text Search Upgrade Options page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to select the full-text search upgrade option to use for the databases that you are upgrading at this time.</span></span>  
  
 <span data-ttu-id="ac8fe-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 에서는 각 전체 텍스트 인덱스가 파일 그룹에 속하는 전체 텍스트 카탈로그에 있고 실제 경로를 가지며 데이터베이스 파일로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-104">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] each full-text index resides in a full-text catalog that belongs to a filegroup, has a physical path, and is treated as a database file.</span></span> <span data-ttu-id="ac8fe-105">이제 전체 텍스트 카탈로그는 전체 텍스트 인덱스 그룹을 나타내는 논리적 개념 (가상 개체)입니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-105">Now, a full-text catalog is a logical concept-a virtual object-that refers to a group of full-text indexes.</span></span> <span data-ttu-id="ac8fe-106">따라서 새로운 전체 텍스트 카탈로그는 실제 경로가 있는 데이터베이스 파일로 취급되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-106">Therefore, a new full-text catalog is not treated as a database file with a physical path.</span></span> <span data-ttu-id="ac8fe-107">그러나 데이터 파일이 들어 있는 전체 텍스트 카탈로그를 업그레이드할 때는 같은 디스크에 새 파일 그룹이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-107">However, during upgrade of any full-text catalog that contains data files, a new filegroup is created on same disk.</span></span> <span data-ttu-id="ac8fe-108">따라서 업그레이드 후에도 이전의 디스크 I/O 동작이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-108">This maintains the old disk I/O behavior after upgrade.</span></span> <span data-ttu-id="ac8fe-109">루트 경로가 있으면 해당 카탈로그의 전체 텍스트 인덱스가 새 파일 그룹에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-109">Any full-text index from that catalog is placed in the new filegroup if the root path exists.</span></span> <span data-ttu-id="ac8fe-110">이전 전체 텍스트 카탈로그 경로가 유효하지 않으면 업그레이드 과정에서 전체 텍스트 인덱스가 기본 테이블과 같은 파일 그룹에 유지되며, 테이블이 분할된 경우에는 주 파일 그룹에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-110">If the old full-text catalog path is invalid, the upgrade keeps the full-text index in the same filegroup as base table or, for a partitioned table, in the primary filegroup.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ac8fe-111">옵션</span><span class="sxs-lookup"><span data-stu-id="ac8fe-111">Options</span></span>  
 <span data-ttu-id="ac8fe-112">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 때 다음과 같은 전체 텍스트 업그레이드 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-112">When you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], choose one of the following full-text upgrade options.</span></span>  
  
 <span data-ttu-id="ac8fe-113">**가져오기**</span><span class="sxs-lookup"><span data-stu-id="ac8fe-113">**Import**</span></span>  
 <span data-ttu-id="ac8fe-114">전체 텍스트 카탈로그를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-114">Full-text catalogs are imported.</span></span> <span data-ttu-id="ac8fe-115">일반적으로 가져오기가 다시 작성보다 훨씬 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-115">Typically, import is significantly faster than rebuild.</span></span> <span data-ttu-id="ac8fe-116">예를 들어 CPU를 하나만 사용하는 경우 가져오기가 다시 작성보다 10배 정도 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-116">For example, when using only one CPU, import runs about 10 times faster than rebuild.</span></span> <span data-ttu-id="ac8fe-117">그러나 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 에서 가져온 전체 텍스트 카탈로그에는 향상된 단어 분리기가 사용되지 않으므로 결국에는 전체 텍스트 카탈로그를 다시 작성해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-117">However, a full-text catalog imported from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] does not use the new and enhanced word breakers, so you might want to rebuild your full-text catalogs eventually.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac8fe-118">다시 작성은 다중 스레드 모드로 실행할 수 있으므로 CPU를 11개 이상 사용할 수 있는 경우 다시 작성에서 모든 CPU를 사용할 수 있게 설정하면 다시 작성이 가져오기보다 빠르게 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-118">Rebuild can run in multi-threaded mode, and if more than 10 CPUs are available, rebuild might run faster than import if you allow rebuild to use all of the CPUs.</span></span>  
  
 <span data-ttu-id="ac8fe-119">전체 텍스트 카탈로그를 사용할 수 없는 경우 연결된 전체 텍스트 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-119">If a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="ac8fe-120">이 옵션은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터베이스에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-120">This option is available for only [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] databases.</span></span>  
  
 <span data-ttu-id="ac8fe-121">전체 텍스트 인덱스를 가져오는 데 따르는 영향에 대한 자세한 내용은 이 항목의 뒷부분에 나오는 "전체 텍스트 업그레이드 옵션 선택 시 고려 사항"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-121">For information about the impact of importing full-text index, see "Considerations for Choosing a Full-Text Upgrade Option," later in this topic.</span></span>  
  
 <span data-ttu-id="ac8fe-122">**다시 빌드**</span><span class="sxs-lookup"><span data-stu-id="ac8fe-122">**Rebuild**</span></span>  
 <span data-ttu-id="ac8fe-123">향상된 새로운 단어 분리기를 사용하여 전체 텍스트 카탈로그를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-123">Full-text catalogs are rebuilt using the new and enhanced word breakers.</span></span> <span data-ttu-id="ac8fe-124">인덱스를 다시 작성하면 시간이 오래 걸릴 수 있으며 업그레이드 후 CPU 및 메모리가 많이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-124">Rebuilding indexes can take a lot of time, and a significant amount of CPU and memory might be required after the upgrade.</span></span>  
  
 <span data-ttu-id="ac8fe-125">**재설정**</span><span class="sxs-lookup"><span data-stu-id="ac8fe-125">**Reset**</span></span>  
 <span data-ttu-id="ac8fe-126">전체 텍스트 카탈로그를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-126">Full-text catalogs are reset.</span></span> <span data-ttu-id="ac8fe-127">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 업그레이드할 때는 전체 텍스트 카탈로그 파일이 제거되지만 전체 텍스트 카탈로그 및 전체 텍스트 인덱스의 메타데이터는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-127">When upgrading from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], full-text catalog files are removed, but the metadata for full-text catalogs and full-text indexes is retained.</span></span> <span data-ttu-id="ac8fe-128">업그레이드가 끝나면 모든 전체 텍스트 인덱스의 변경 내용 추적이 해제되고 탐색이 자동으로 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-128">After being upgraded, all full-text indexes are disabled for change tracking and crawls are not started automatically.</span></span> <span data-ttu-id="ac8fe-129">업그레이드가 완료된 후 전체 채우기를 수동으로 실행할 때까지 카탈로그가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-129">The catalog will remain empty until you manually issue a full population, after the upgrade completes.</span></span>  
  
 <span data-ttu-id="ac8fe-130">이러한 업그레이드 옵션을 사용하면 업그레이드된 데이터베이스에서 향상된 전체 텍스트 검색 성능을 완벽하게 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-130">All of these upgrade options ensure that upgraded databases benefit fully from full-text performance enhancements.</span></span>  
  
## <a name="considerations-for-choosing-a-full-text-upgrade-option"></a><span data-ttu-id="ac8fe-131">전체 텍스트 업그레이드 옵션 선택 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ac8fe-131">Considerations for Choosing a Full-Text Upgrade Option</span></span>  
 <span data-ttu-id="ac8fe-132">업그레이드 옵션을 선택할 때는 다음 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-132">When choosing the upgrade option for your upgrade, consider the following:</span></span>  
  
-   <span data-ttu-id="ac8fe-133">단어 분리기를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="ac8fe-133">How do you use word breakers?</span></span>  
  
     <span data-ttu-id="ac8fe-134">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 의 전체 텍스트 검색 서비스에는 단어 분리기 및 형태소 분석기가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-134">The full-text search service in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] includes word breakers and stemmers.</span></span> <span data-ttu-id="ac8fe-135">이로 인해 특정 텍스트 패턴이나 시나리오에 대한 전체 텍스트 쿼리 결과가 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 와 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-135">These might change the results of full-text queries from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] for a specific text pattern or scenario.</span></span> <span data-ttu-id="ac8fe-136">따라서 단어 분리기를 사용하는 방법을 고려하여 적합한 업그레이드 옵션을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-136">Therefore, how you use word breakers is important when choosing a suitable upgrade option:</span></span>  
  
    -   <span data-ttu-id="ac8fe-137">사용하는 전체 텍스트 언어의 단어 분리기가 변경되지 않았거나 회수 정확성이 크게 중요하지 않은 경우 가져오기 옵션이 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-137">If the word breakers of the full-text language you use did not change, or if recall accuracy is not critical to you, importing is suitable.</span></span> <span data-ttu-id="ac8fe-138">이후에 회수 관련 문제가 발생하면 전체 텍스트 카탈로그를 다시 작성하여 간편하게 새 단어 분리기로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-138">Later, if you experience any recall issues, you can upgrade to the new word breakers simply by rebuilding your full-text catalogs.</span></span>  
  
    -   <span data-ttu-id="ac8fe-139">회수 정확성이 중요하고 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]후에 추가된 단어 분리기 중 하나를 사용하는 경우에는 다시 작성 옵션이 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-139">If you care about recall accuracy and you use one of the word breakers that were added after [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], rebuilding is suitable.</span></span>  
  
-   <span data-ttu-id="ac8fe-140">정수 전체 텍스트 키 열에 작성된 전체 텍스트 인덱스가 있는지 여부</span><span class="sxs-lookup"><span data-stu-id="ac8fe-140">Were any full-text indexes built on integer full-text key columns?</span></span>  
  
     <span data-ttu-id="ac8fe-141">다시 작성할 때 내부 최적화가 수행되어 업그레이드된 전체 텍스트 인덱스의 쿼리 성능이 향상되는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-141">Rebuilding performs internal optimizations that improve the query performance of the upgraded full-text index in some cases.</span></span> <span data-ttu-id="ac8fe-142">특히 전체 텍스트 카탈로그에 기본 테이블의 전체 텍스트 키 열이 정수 데이터 형식인 전체 텍스트 인덱스가 있는 경우 다시 작성을 통해 업그레이드 후 전체 텍스트 쿼리의 성능을 극대화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-142">Specifically, if you have full-text catalogs that contain full-text indexes for which the full-text key column of the base table is an integer data type, rebuilding achieves ideal performance of full-text queries after upgrade.</span></span> <span data-ttu-id="ac8fe-143">이러한 경우 **다시 작성** 옵션을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-143">In this case, we highly recommend you to use the **Rebuild** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ac8fe-144">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 전체 텍스트 인덱스에서 전체 텍스트 키로 사용하는 열을 정수 데이터 형식으로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-144">For full-text indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that the column serving as the full-text key be an integer data type.</span></span> <span data-ttu-id="ac8fe-145">자세한 내용은 [전체 텍스트 인덱스 성능 향상](../../relational-databases/indexes/indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-145">For more information, see [Improve the Performance of Full-Text Indexes](../../relational-databases/indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="ac8fe-146">서버 인스턴스를 온라인 상태로 만들기의 중요도</span><span class="sxs-lookup"><span data-stu-id="ac8fe-146">What is the priority for getting your server instance online?</span></span>  
  
     <span data-ttu-id="ac8fe-147">업그레이드 도중 가져오기나 다시 작성을 수행할 경우 CPU 리소스가 많이 사용되어 서버 인스턴스의 나머지 부분을 업그레이드하고 온라인 상태로 만드는 작업이 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-147">Importing or rebuilding during upgrade takes a lot of CPU resources, which delays getting the rest of the server instance upgraded and online.</span></span> <span data-ttu-id="ac8fe-148">서버 인스턴스를 최대한 빨리 온라인 상태로 만들어야 하며 업그레이드 후 수동 채우기를 실행할 수 있는 경우 **다시 설정** 옵션이 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8fe-148">If getting the server instance online as soon as possible is important and if you are willing to run a manual population after the upgrade, **Reset** is suitable.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="ac8fe-149">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="ac8fe-149">Additional Resources</span></span>  
  
