---
title: 캐싱 페이지, 공유 데이터 집합 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eac372e9-d2a1-48a8-bbe5-09d101df16ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62d899964911a6f2d35e59d49d925ff80013af42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650807"
---
# <a name="caching-page-shared-datasets-report-manager"></a><span data-ttu-id="be034-102">캐싱 페이지, 공유 데이터 세트(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="be034-102">Caching Page, Shared Datasets (Report Manager)</span></span>
  <span data-ttu-id="be034-103">캐싱 속성 페이지를 사용하여 공유 데이터 세트의 캐시 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be034-103">Use the Caching properties page to set the cache options for a shared dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be034-104">이 기능은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be034-104">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="be034-105">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="be034-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="be034-106">탐색</span><span class="sxs-lookup"><span data-stu-id="be034-106">Navigation</span></span>  
 <span data-ttu-id="be034-107">사용자 인터페이스에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="be034-107">Use the following procedure to navigate to this location in the user interface.</span></span>  
  
### <a name="to-open-the-caching-properties-page-for-a-shared-dataset"></a><span data-ttu-id="be034-108">공유 데이터 세트의 캐싱 속성 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="be034-108">To open the Caching properties page for a shared dataset</span></span>  
  
1.  <span data-ttu-id="be034-109">보고서 관리자를 열고 공유 데이터 세트 속성을 구성할 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="be034-109">Open Report Manager, and locate the report for which you want to configure shared dataset properties.</span></span>  
  
2.  <span data-ttu-id="be034-110">공유 데이터 세트를 가리키고 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-110">Point to the shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="be034-111">드롭다운 목록에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-111">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="be034-112">보고서의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="be034-112">The General properties page for the report opens.</span></span>  
  
4.  <span data-ttu-id="be034-113">**캐싱** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-113">Click the **Caching** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="be034-114">옵션</span><span class="sxs-lookup"><span data-stu-id="be034-114">Options</span></span>  
 <span data-ttu-id="be034-115">**공유 데이터 세트 캐시**</span><span class="sxs-lookup"><span data-stu-id="be034-115">**Cache shared dataset**</span></span>  
 <span data-ttu-id="be034-116">사용자가 이 공유 데이터 세트를 사용하는 보고서를 처음에 열 때 캐시에 데이터를 임시로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-116">Places a temporary copy of the data in a cache when a user first opens a report that uses this shared dataset.</span></span> <span data-ttu-id="be034-117">캐싱 기간 내에 보고서를 실행하는 이후 사용자는 데이터의 캐시된 복사본을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be034-117">Subsequent users who run the report within the caching period receive the cached copy of the data.</span></span> <span data-ttu-id="be034-118">캐시를 사용하면 데이터 세트 쿼리를 다시 실행하지 않고 캐시에서 바로 가져오기 때문에 일반적으로 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="be034-118">Caching usually improves performance because the data is returned from the cache instead of running the dataset query again.</span></span>  
  
 <span data-ttu-id="be034-119">**다음 시간(분)이 지나면 캐시 만료**</span><span class="sxs-lookup"><span data-stu-id="be034-119">**Expire the cache after a number of minutes**</span></span>  
 <span data-ttu-id="be034-120">데이터의 캐시된 복사본을 저장할 시간(분)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-120">Specify the number of minutes to save the cached copy of the data.</span></span> <span data-ttu-id="be034-121">임시 복사본이 만료된 직후부터 더 이상 캐시에서 데이터가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be034-121">As soon as a temporary copy expires, the data is no longer returned from the cache.</span></span> <span data-ttu-id="be034-122">이후에 사용자가 이 공유 데이터 세트를 사용하는 보고서를 열면 데이터 세트 쿼리가 실행되고 보고서 서버가 새로 고친 데이터의 복사본을 캐시에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-122">The next time a user opens a report that uses this shared dataset, the dataset query runs and the report server places a copy of the refreshed data back in the cache.</span></span>  
  
 <span data-ttu-id="be034-123">**다음 일정에 따라 캐시 만료**</span><span class="sxs-lookup"><span data-stu-id="be034-123">**Expire the cache on the following schedule**</span></span>  
 <span data-ttu-id="be034-124">캐시된 데이터가 더 이상 유효하지 않게 되며 캐시에서 제거되는 시간을 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-124">Schedule the time when the cached data is no longer valid and is removed from the cache.</span></span> <span data-ttu-id="be034-125">일정을 공유 일정으로 지정하거나 현재 공유 데이터 세트 전용 일정으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be034-125">The schedule can be a shared schedule or one that is specific for only the current shared dataset.</span></span>  
  
 <span data-ttu-id="be034-126">**데이터 세트별 일정**</span><span class="sxs-lookup"><span data-stu-id="be034-126">**Dataset-specific schedule**</span></span>  
 <span data-ttu-id="be034-127">이 데이터 세트에서만 사용되는 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-127">Specify a schedule that is used only by this dataset.</span></span>  
  
 <span data-ttu-id="be034-128">**공유 일정**</span><span class="sxs-lookup"><span data-stu-id="be034-128">**Shared schedule**</span></span>  
 <span data-ttu-id="be034-129">보고서, 구독 및 기타 공유 데이터 세트에서 공유되는 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-129">Specify a schedule that is shared among reports, subscriptions, and other shared datasets.</span></span>  
  
 <span data-ttu-id="be034-130">**적용**</span><span class="sxs-lookup"><span data-stu-id="be034-130">**Apply**</span></span>  
 <span data-ttu-id="be034-131">변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="be034-131">Save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be034-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be034-132">See Also</span></span>  
 <span data-ttu-id="be034-133">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="be034-133">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="be034-134">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="be034-134">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="be034-135">[SSRS&#41;&#40;공유 데이터 집합 캐시](report-server/cache-shared-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="be034-135">[Cache Shared Datasets &#40;SSRS&#41;](report-server/cache-shared-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="be034-136">일정</span><span class="sxs-lookup"><span data-stu-id="be034-136">Schedules</span></span>](subscriptions/schedules.md)  
  
  
