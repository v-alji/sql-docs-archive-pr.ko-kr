---
title: 서버 인스턴스의 전체 텍스트 검색 관리 및 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], about
- full-text search [SQL Server], server management
ms.assetid: 2733ed78-6d33-4bf9-94da-60c3141b87c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1ba4b2f081047f25fa775e0c8754caa4ce643e70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733771"
---
# <a name="manage-and-monitor-full-text-search-for-a-server-instance"></a><span data-ttu-id="87b2d-102">서버 인스턴스의 전체 텍스트 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="87b2d-102">Manage and Monitor Full-Text Search for a Server Instance</span></span>
  <span data-ttu-id="87b2d-103">서버 인스턴스의 전체 텍스트 관리에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-103">Full-text administration for a server instance includes:</span></span>  
  
-   <span data-ttu-id="87b2d-104">FDHOST Launcher 서비스(MSSQLFDLauncher) 관리, 서비스 계정 자격 증명을 변경하는 경우 필터 데몬 호스트 프로세스 다시 시작, 서버 차원의 전체 텍스트 속성 구성, 전체 텍스트 카탈로그 백업 등의 시스템 관리 태스크.</span><span class="sxs-lookup"><span data-stu-id="87b2d-104">System management tasks such as managing the FDHOST Launcher service (MSSQLFDLauncher), restarting filter daemon host process if you change the service account credentials, configuring server-wide full-text properties, and backing up full-text catalogs.</span></span> <span data-ttu-id="87b2d-105">예를 들어 서버 수준에서 전반적으로 서버 인스턴스의 기본 언어와 다른 기본 전체 텍스트 언어를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-105">At the server level, for example, you can specify a default full-text language that differs from the default language of the server instance as a whole.</span></span>  
  
-   <span data-ttu-id="87b2d-106">전체 텍스트 언어 구성 요소 구성(단어 분리기, 형태소 분석기, 동의어 사전 파일, 중지 단어 및 중지 목록).</span><span class="sxs-lookup"><span data-stu-id="87b2d-106">Configuring full-text linguistic components (word breakers and stemmers, thesaurus file, and stopwords and stoplists).</span></span>  
  
-   <span data-ttu-id="87b2d-107">전체 텍스트 검색에 대한 사용자 데이터베이스 구성.</span><span class="sxs-lookup"><span data-stu-id="87b2d-107">Configuring a user database for full-text search.</span></span> <span data-ttu-id="87b2d-108">여기에는 데이터베이스에 대해 하나 이상의 전체 텍스트 카탈로그를 만들고 전체 텍스트 쿼리를 실행할 각 테이블 또는 인덱싱된 뷰에 대한 전체 텍스트 인덱스를 정의하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-108">This involves creating one or more full-text catalogs for the database and defining a full-text index on each table or indexed view on which you want to execute full-text queries.</span></span>  
  
##  <a name="viewing-or-changing-server-properties-for-full-text-search"></a><a name="props"></a> <span data-ttu-id="87b2d-109">전체 텍스트 검색의 서버 속성 보기 또는 변경</span><span class="sxs-lookup"><span data-stu-id="87b2d-109">Viewing or Changing Server Properties for Full-Text Search</span></span>  
 <span data-ttu-id="87b2d-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]인스턴스의 전체 텍스트 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-110">You can view the full-text properties of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-view-and-change-server-properties-for-full-text-search"></a><span data-ttu-id="87b2d-111">전체 텍스트 검색의 서버 속성을 보고 변경하려면</span><span class="sxs-lookup"><span data-stu-id="87b2d-111">To view and change server properties for full-text search</span></span>  
  
1.  <span data-ttu-id="87b2d-112">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-112">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="87b2d-113">**서버 속성** 대화 상자에서 **고급** 페이지를 클릭하여 전체 텍스트 검색에 대한 서버 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-113">In the **Server Properties** dialog box, click the **Advanced** page to view server information about full-text search.</span></span> <span data-ttu-id="87b2d-114">전체 텍스트 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-114">The full-text properties are as follows:</span></span>  
  
    -   <span data-ttu-id="87b2d-115">**기본 전체 텍스트 언어**</span><span class="sxs-lookup"><span data-stu-id="87b2d-115">**Default Full-Text Language**</span></span>  
  
         <span data-ttu-id="87b2d-116">전체 텍스트 인덱싱된 열에 대한 기본 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-116">Specifies a default language for full-text indexed columns.</span></span> <span data-ttu-id="87b2d-117">전체 텍스트 인덱싱된 데이터의 언어 분석은 데이터의 언어에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-117">Linguistic analysis of full-text indexed data is dependent on the language of the data.</span></span> <span data-ttu-id="87b2d-118">이 옵션의 기본값은 서버의 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-118">The default value of this option is the language of the server.</span></span> <span data-ttu-id="87b2d-119">표시되는 설정에 해당하는 언어에 대한 자세한 내용은 [sys.fulltext_languages&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87b2d-119">For the language that corresponds to the displayed setting, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span>  
  
    -   <span data-ttu-id="87b2d-120">**전체 텍스트 업그레이드 옵션**</span><span class="sxs-lookup"><span data-stu-id="87b2d-120">**Full-Text Upgrade Option**</span></span>  
  
         <span data-ttu-id="87b2d-121">이 서버 속성은 데이터베이스를 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 에서 이후 버전으로 업그레이드할 때 전체 텍스트 인덱스를 마이그레이션하는 방법을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-121">This server property controls how full-text indexes are migrated when upgrading a database from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] to a later version.</span></span> <span data-ttu-id="87b2d-122">이 속성은 데이터베이스 복사 마법사를 사용하여 데이터베이스를 연결하거나, 데이터베이스 백업 및 파일 백업을 복원하거나, 데이터베이스를 복사하여 업그레이드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-122">This property applies to upgrading by attaching a database, restoring a database backup, restoring a file backup, or copying the database by using the Copy Database Wizard.</span></span>  
  
         <span data-ttu-id="87b2d-123">대체 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-123">The alternatives are as follows:</span></span>  
  
         <span data-ttu-id="87b2d-124">**가져오기**</span><span class="sxs-lookup"><span data-stu-id="87b2d-124">**Import**</span></span>  
         <span data-ttu-id="87b2d-125">전체 텍스트 카탈로그를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-125">Full-text catalogs are imported.</span></span> <span data-ttu-id="87b2d-126">일반적으로 가져오기가 다시 작성보다 훨씬 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-126">Typically, import is significantly faster than rebuild.</span></span> <span data-ttu-id="87b2d-127">예를 들어 CPU를 하나만 사용하는 경우 가져오기가 다시 작성보다 10배 정도 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-127">For example, when using only one CPU, import runs about 10 times faster than rebuild.</span></span> <span data-ttu-id="87b2d-128">그러나 가져온 전체 텍스트 카탈로그에는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에 새로 도입된 향상된 단어 분리기가 사용되지 않으므로 결국에는 전체 텍스트 카탈로그를 다시 작성해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-128">However, an imported full-text catalog does not use the new and enhanced word breakers introduced in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], so you might want to rebuild your full-text catalogs eventually.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="87b2d-129">다시 작성은 다중 스레드 모드로 실행할 수 있으므로 CPU를 11개 이상 사용할 수 있는 경우 다시 작성에서 모든 CPU를 사용할 수 있게 설정하면 다시 작성이 가져오기보다 빠르게 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-129">Rebuild can run in multi-threaded mode, and if more than 10 CPUs are available, rebuild might run faster than import if you allow rebuild to use all of the CPUs.</span></span>  
  
         <span data-ttu-id="87b2d-130">전체 텍스트 카탈로그를 사용할 수 없는 경우 연결된 전체 텍스트 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-130">If a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="87b2d-131">이 옵션은 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 데이터베이스에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-131">This option is available for only [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] databases.</span></span>  
  
         <span data-ttu-id="87b2d-132">**다시 빌드**</span><span class="sxs-lookup"><span data-stu-id="87b2d-132">**Rebuild**</span></span>  
         <span data-ttu-id="87b2d-133">향상된 새로운 단어 분리기를 사용하여 전체 텍스트 카탈로그를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-133">Full-text catalogs are rebuilt using the new and enhanced word breakers.</span></span> <span data-ttu-id="87b2d-134">인덱스를 다시 작성하면 시간이 오래 걸릴 수 있으며 업그레이드 후 CPU 및 메모리가 많이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-134">Rebuilding indexes can take awhile, and a significant amount of CPU and memory might be required after the upgrade.</span></span>  
  
         <span data-ttu-id="87b2d-135">**재설정**</span><span class="sxs-lookup"><span data-stu-id="87b2d-135">**Reset**</span></span>  
         <span data-ttu-id="87b2d-136">전체 텍스트 카탈로그를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-136">Full-text catalogs are reset.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="87b2d-137">전체 텍스트 카탈로그 파일이 제거되지만 전체 텍스트 카탈로그 및 전체 텍스트 인덱스의 메타데이터는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-137">full-text catalog files are removed, but the metadata for full-text catalogs and full-text indexes is retained.</span></span> <span data-ttu-id="87b2d-138">업그레이드가 끝나면 모든 전체 텍스트 인덱스의 변경 내용 추적이 해제되고 탐색이 자동으로 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-138">After being upgraded, all full-text indexes are disabled for change tracking and crawls are not started automatically.</span></span> <span data-ttu-id="87b2d-139">업그레이드가 완료된 후 전체 채우기를 수동으로 실행할 때까지 카탈로그가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-139">The catalog will remain empty until you manually issue a full population, after the upgrade completes.</span></span>  
  
         <span data-ttu-id="87b2d-140">전체 텍스트 업그레이드 옵션을 선택 하는 방법에 대 한 자세한 내용은 [전체 텍스트 검색 업그레이드](upgrade-full-text-search.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="87b2d-140">For information about choosing a full-text upgrade option, see [Upgrade Full-Text Search](upgrade-full-text-search.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="87b2d-141">[sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)**upgrade_option** 동작을 사용하여 전체 텍스트 업그레이드 옵션을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-141">The full-text upgrade option can also be set by using the [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)**upgrade_option** action.</span></span>  
  
##  <a name="viewing-additional-full-text-server-properties"></a><a name="metadata"></a> <span data-ttu-id="87b2d-142">추가 전체 텍스트 서버 속성 보기</span><span class="sxs-lookup"><span data-stu-id="87b2d-142">Viewing Additional Full-Text Server Properties</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="87b2d-143">함수를 사용하여 전체 텍스트 검색의 다양한 서버 수준 속성 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-143">functions can be used to obtain the value of various server-level properties of full-text search.</span></span> <span data-ttu-id="87b2d-144">이 정보는 전체 텍스트 검색을 관리하고 이러한 검색에서 발생하는 문제를 해결하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-144">This information is useful for administrating and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="87b2d-145">다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서버 인스턴스의 전체 텍스트 속성 및 관련 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 함수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-145">The following table lists full-text properties of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server instance and their related [!INCLUDE[tsql](../../../includes/tsql-md.md)] functions.</span></span>  
  
|<span data-ttu-id="87b2d-146">속성</span><span class="sxs-lookup"><span data-stu-id="87b2d-146">Property</span></span>|<span data-ttu-id="87b2d-147">Description</span><span class="sxs-lookup"><span data-stu-id="87b2d-147">Description</span></span>|<span data-ttu-id="87b2d-148">함수</span><span class="sxs-lookup"><span data-stu-id="87b2d-148">Function</span></span>|  
|--------------|-----------------|--------------|  
|`IsFullTextInstalled`|<span data-ttu-id="87b2d-149">전체 텍스트 구성 요소가 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 설치되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-149">Whether the full-text component is installed with the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="87b2d-150">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="87b2d-150">FULLTEXTSERVICEPROPERTY</span></span>](/sql/t-sql/functions/fulltextserviceproperty-transact-sql)<br /><br /> [<span data-ttu-id="87b2d-151">SERVERPROPERTY</span><span class="sxs-lookup"><span data-stu-id="87b2d-151">SERVERPROPERTY</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)|  
|`LoadOSResources`|<span data-ttu-id="87b2d-152">운영 체제 단어 분리기 및 필터가 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스와 함께 등록되고 사용되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-152">Whether operating system word breakers and filters are registered and used with this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|<span data-ttu-id="87b2d-153">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="87b2d-153">FULLTEXTSERVICEPROPERTY</span></span>|  
|`VerifySignature`|<span data-ttu-id="87b2d-154">전체 텍스트 엔진이 서명된 이진 파일만 로드할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-154">Specifies whether only signed binaries are loaded by the Full-Text Engine.</span></span>|<span data-ttu-id="87b2d-155">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="87b2d-155">FULLTEXTSERVICEPROPERTY</span></span>|  
  
##  <a name="monitoring-full-text-search-activity"></a><a name="monitor"></a> <span data-ttu-id="87b2d-156">전체 텍스트 검색 작업 모니터링</span><span class="sxs-lookup"><span data-stu-id="87b2d-156">Monitoring Full-Text Search Activity</span></span>  
 <span data-ttu-id="87b2d-157">일부 동적 관리 뷰 및 함수는 서버 인스턴스의 전체 텍스트 검색 작업을 모니터링하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="87b2d-157">Several dynamic management views and functions are useful monitoring full-text search activity on a server instance.</span></span>  
  
 <span data-ttu-id="87b2d-158">**채우기 작업이 진행 중인 전체 텍스트 카탈로그에 대한 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="87b2d-158">**To view information about the full-text catalogs with in-progress population activity**</span></span>  
  
-   [<span data-ttu-id="87b2d-159">sys.dm_fts_active_catalogs&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87b2d-159">sys.dm_fts_active_catalogs &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-active-catalogs-transact-sql)  
  
 <span data-ttu-id="87b2d-160">**필터 데몬 호스트 프로세스의 현재 작업을 보려면**</span><span class="sxs-lookup"><span data-stu-id="87b2d-160">**To view current activity of a filter daemon host process**</span></span>  
  
-   [<span data-ttu-id="87b2d-161">sys.dm_fts_fdhosts&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87b2d-161">sys.dm_fts_fdhosts &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-fdhosts-transact-sql)  
  
 <span data-ttu-id="87b2d-162">**진행 중인 인덱스 채우기에 대한 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="87b2d-162">**To view information about in-progress index populations**</span></span>  
  
-   [<span data-ttu-id="87b2d-163">sys.dm_fts_index_population&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87b2d-163">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)  
  
 <span data-ttu-id="87b2d-164">**전체 텍스트 탐색이나 전체 텍스트 탐색 범위의 일부로 사용되는 메모리 풀의 메모리 버퍼를 보려면**</span><span class="sxs-lookup"><span data-stu-id="87b2d-164">**To view memory buffers in a memory pool that are used as part of a crawl or crawl range.**</span></span>  
  
-   [<span data-ttu-id="87b2d-165">sys.dm_fts_memory_buffers&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87b2d-165">sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)  
  
 <span data-ttu-id="87b2d-166">**전체 텍스트 탐색이나 전체 텍스트 탐색 범위에 대해 전체 텍스트 Gatherer 구성 요소에서 사용할 수 있는 공유 메모리 풀을 보려면**</span><span class="sxs-lookup"><span data-stu-id="87b2d-166">**To view the shared memory pools available to the full-text gatherer component for a full-text crawl or a full-text crawl range**</span></span>  
  
-   [<span data-ttu-id="87b2d-167">sys.dm_fts_memory_pools&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87b2d-167">sys.dm_fts_memory_pools &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)  
  
 <span data-ttu-id="87b2d-168">**각 전체 텍스트 인덱싱 일괄 처리에 대한 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="87b2d-168">**To view information about each full-text indexing batch**</span></span>  
  
-   [<span data-ttu-id="87b2d-169">sys.dm_fts_outstanding_batches&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87b2d-169">sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-outstanding-batches-transact-sql)  
  
 <span data-ttu-id="87b2d-170">**진행 중인 채우기와 관련된 특정 범위에 대한 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="87b2d-170">**To view information about the specific ranges related to an in-progress population**</span></span>  
  
-   [<span data-ttu-id="87b2d-171">sys.dm_fts_population_ranges&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87b2d-171">sys.dm_fts_population_ranges &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-population-ranges-transact-sql)  
  
  
