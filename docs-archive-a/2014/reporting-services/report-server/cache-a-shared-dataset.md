---
title: 공유 데이터 세트 캐시 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c2d8c81a-da1e-4a8a-9845-fff9a0903d24
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d4757d82425368efcb6a0a555c6cfe1deacf48c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652605"
---
# <a name="cache-a-shared-dataset"></a><span data-ttu-id="9462f-102">공유 데이터 세트 캐시</span><span class="sxs-lookup"><span data-stu-id="9462f-102">Cache a Shared Dataset</span></span>
  <span data-ttu-id="9462f-103">성능을 향상시키는 한 가지 방법은 공유 데이터 세트의 캐싱 속성을 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-103">One way to improve performance is to configure caching properties for a shared dataset.</span></span> <span data-ttu-id="9462f-104">공유 데이터 세트가 캐시되면 쿼리 결과의 복사본이 지정된 기간 동안 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-104">When a shared dataset is cached, a copy of the query results is saved for a specified period of time.</span></span> <span data-ttu-id="9462f-105">공유 데이터 세트를 사용하는 보고서를 요청하는 첫 번째 사용자는 쿼리 결과 및 모든 처리가 완료될 때까지 기다려야 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-105">The first user who requests a report that uses the shared dataset must wait for the query results and all processing to complete before viewing the report.</span></span> <span data-ttu-id="9462f-106">캐싱 기간 내에 보고서를 요청하는 이후 사용자는 쿼리 및 처리가 이미 발생했기 때문에 기다리지 않고 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-106">Subsequent users who request the report within the caching period will experience improved performance because the query and processing has already occurred.</span></span> <span data-ttu-id="9462f-107">또한 쿼리를 실행하고 지정된 캐시 만료 시점까지 결과를 캐시하기 위한 캐시 새로 고침 계획을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-107">You can also specify a cache refresh plan to run the query and cache the results until the specified cache expiration.</span></span>  
  
 <span data-ttu-id="9462f-108">공유 데이터 세트 또는 캐시 새로 고침 계획을 기반으로 보고서를 실행하는 사용자는 쿼리 캐시를 만들며 두 경우 모두 캐시 만료 옵션에 따라 캐시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-108">Users running reports based on a shared dataset or cache refresh plans create the query cache and in both cases, the cache is available based on the cache expiration options.</span></span>  
  
 <span data-ttu-id="9462f-109">캐시할 수 있는 공유 데이터 세트 유형은 제한되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-109">There are restrictions on the types of shared datasets that you can cache.</span></span> <span data-ttu-id="9462f-110">예를 들어 사용자 ID에 따라 데이터가 달라지는 경우 또는 보고서를 요청하는 사용자의 보안 토큰을 사용하여 데이터가 검색되는 경우 쿼리 결과를 캐시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-110">For example, the query results cannot be cached if the data varies based on the user identity or if data is retrieved using the security token of the user who requests the report.</span></span> <span data-ttu-id="9462f-111">자세한 내용은 [공유 데이터 세트 캐시&#40;SSRS&#41;](cache-shared-datasets-ssrs.md) 및 [보고서 캐시&#40;SSRS&#41;](caching-reports-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9462f-111">For more information, see [Cache Shared Datasets &#40;SSRS&#41;](cache-shared-datasets-ssrs.md) and [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a><span data-ttu-id="9462f-112">캐시된 보고서의 만료를 예약하려면</span><span class="sxs-lookup"><span data-stu-id="9462f-112">To schedule the expiration of a cached report</span></span>  
  
1.  <span data-ttu-id="9462f-113">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-113">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="9462f-114">보고서 관리자에서 캐싱 속성을 설정할 공유 데이터 세트로 이동하여 항목 위로 마우스를 이동하고 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-114">In Report Manager, navigate to the shared dataset for which you want to set caching properties, hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="9462f-115">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-115">In the drop-down menu, click **Manage**.</span></span>  
  
4.  <span data-ttu-id="9462f-116">왼쪽 프레임에서 **캐싱**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-116">In the left frame, click **Caching**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9462f-117">**공유 데이터 세트를 실행하는 데 사용되는 자격 증명이 저장되어 있지 않습니다**라는 오류가 표시되면 공유 데이터 세트 캐시 옵션이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-117">If you see the error **Credentials used to run the shared dataset are not stored**, the cache shared dataset option will be disabled.</span></span> <span data-ttu-id="9462f-118">데이터 원본을 수정하여 자격 증명을 저장하거나 공유 데이터 세트를 수정하여 자격 증명이 저장되어 있는 다른 데이터 원본을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-118">You need modify the data source to store credentials or modify the shared dataset to use a different data source that does store credentials.</span></span>  
  
5.  <span data-ttu-id="9462f-119">**공유 데이터 세트 캐시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-119">Select **Cache share dataset**.</span></span>  
  
6.  <span data-ttu-id="9462f-120">30분 후에 캐시가 만료되는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-120">Select the option to expire the cache after 30 minutes.</span></span> <span data-ttu-id="9462f-121">지정된 일정에 따라 캐시가 만료되는 옵션을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-121">You can also choose for the cache to expire on a specified schedule.</span></span>  
  
7.  <span data-ttu-id="9462f-122">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9462f-122">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9462f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9462f-123">See Also</span></span>  
 [<span data-ttu-id="9462f-124">공유 데이터 세트 관리</span><span class="sxs-lookup"><span data-stu-id="9462f-124">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
  
