---
title: 보고서 캐시(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e359e6c7a40b267979137ef2b3a285667a6fdb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652606"
---
# <a name="cache-a-report-report-manager"></a><span data-ttu-id="612a5-102">보고서 캐시(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="612a5-102">Cache a Report (Report Manager)</span></span>
  <span data-ttu-id="612a5-103">성능을 향상시키는 한 가지 방법은 보고서의 캐싱 속성을 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-103">One way to improve performance is to configure caching properties for a report.</span></span> <span data-ttu-id="612a5-104">보고서가 캐시되면 렌더링된 보고서의 복사본이 짧은 시간 동안 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-104">When a report is cached, a copy of the rendered report is saved for a short period of time.</span></span> <span data-ttu-id="612a5-105">보고서를 요청하는 첫 번째 사용자는 모든 처리가 완료될 때까지 기다려야 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-105">The first user who requests the report must wait for all processing to complete before viewing the report.</span></span> <span data-ttu-id="612a5-106">캐싱 기간 내에 보고서를 요청하는 이후 사용자는 처리가 이미 발생했기 때문에 보고서를 바로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-106">Subsequent users who request the report within the caching period can view it right away because processing has already occurred.</span></span>  
  
 <span data-ttu-id="612a5-107">캐시할 수 있는 보고서 유형은 제한되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-107">There are restrictions on the types of reports that you can cache.</span></span> <span data-ttu-id="612a5-108">예를 들어 사용자 ID에 따라 보고서 출력이 달라지는 경우 또는 보고서를 요청하는 사용자의 보안 토큰을 사용하여 데이터가 검색되는 경우 보고서를 캐시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-108">For example, a report cannot be cached if report output varies based on the user identity or if data is retrieved using the security token of the user who requests the report.</span></span> <span data-ttu-id="612a5-109">자세한 내용은 [보고서 캐시&#40;SSRS&#41;](caching-reports-ssrs.md)버전에서 캐시를 미리 로드할 수 있는 유일한 방법이었습니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-109">For more information, see [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a><span data-ttu-id="612a5-110">캐시된 보고서의 만료를 예약하려면</span><span class="sxs-lookup"><span data-stu-id="612a5-110">To schedule the expiration of a cached report</span></span>  
  
1.  <span data-ttu-id="612a5-111">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-111">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="612a5-112">보고서 관리자에서 **내용** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-112">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="612a5-113">캐싱 속성을 설정할 보고서로 이동하고 항목 위로 마우스를 이동한 다음 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-113">Navigate to the report for which you want to set caching properties, hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="612a5-114">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-114">In the drop-down menu, click **Manage**.</span></span>  
  
4.  <span data-ttu-id="612a5-115">왼쪽 프레임에서 **처리 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-115">In the left frame, click the **Processing Options**.</span></span>  
  
5.  <span data-ttu-id="612a5-116">해당 페이지에서 **항상 최신 데이터로 이 보고서 실행**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-116">On the page, select **Always run this report with the most recent data**.</span></span>  
  
6.  <span data-ttu-id="612a5-117">다음 두 캐시 옵션 중에서 하나를 선택하고 만료 시간을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-117">Select one of the following two cache options and configure expiration as follows:</span></span>  
  
    -   <span data-ttu-id="612a5-118">캐시된 복사본이 특정 시간 후에 만료되도록 구성하려면 **보고서의 임시 복사본을 캐시합니다. 보고서 복사본은 다음 분 후에 만료됩니다.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-118">To configure a cached copy to expire after a particular time period, click **Cache a temporary copy of the report. Expire copy of report after a number of minutes**.</span></span> <span data-ttu-id="612a5-119">보고서 만료 시간(분)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-119">Type the number of minutes for report expiration.</span></span>  
  
    -   <span data-ttu-id="612a5-120">일정에 따라 캐시된 복사본이 만료되도록 구성하려면 **보고서의 임시 복사본을 캐시합니다. 보고서 복사본은 다음 일정으로 만료됩니다.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-120">To configure a cached copy to expire on a schedule, click **Cache a temporary copy of the report. Expire copy of report on the following schedule.**</span></span> <span data-ttu-id="612a5-121">**구성**을 클릭하거나 공유 일정을 선택하여 보고서 만료를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-121">Click **Configure**, or select a shared schedule to control report expiration</span></span>  
  
7.  <span data-ttu-id="612a5-122">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="612a5-122">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612a5-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="612a5-123">See Also</span></span>  
 <span data-ttu-id="612a5-124">[보고서 처리 속성 설정](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="612a5-124">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="612a5-125">보고서 캐시&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="612a5-125">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
  
  
