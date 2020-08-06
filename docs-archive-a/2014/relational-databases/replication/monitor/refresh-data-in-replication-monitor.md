---
title: 복제 모니터에서 데이터 새로 고침 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2f097dea21b06540293e9b60b7de9315323b4168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741831"
---
# <a name="refresh-data-in-replication-monitor"></a><span data-ttu-id="04924-102">복제 모니터에서 데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="04924-102">Refresh Data in Replication Monitor</span></span>
  <span data-ttu-id="04924-103">복제 모니터에서는 주 창 및 세부 정보 창(주 창에서 시작되는 창)을 자동으로 또는 수동으로 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04924-103">In Replication Monitor, the main window and detail windows (those windows launched from the main window) can be refreshed automatically or manually.</span></span> <span data-ttu-id="04924-104">창을 수동으로 새로 고치려면 F5 키를 누르면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04924-104">To refresh a window manually, press F5.</span></span> <span data-ttu-id="04924-105">기본적으로 주 창은 5분마다 자동으로 새로 고쳐집니다. 이러한 새로 고침 빈도는 게시자별로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04924-105">By default, the main window is refreshed automatically every five seconds; the rate can be customized for each Publisher.</span></span>  
  
 <span data-ttu-id="04924-106">복제 모니터에 표시된 데이터는 캐시에서 쿼리됩니다. 캐시와 복제 모니터 새로 고침의 관계에 대한 자세한 내용은 [캐싱, 새로 고침 및 복제 모니터 성능](caching-refresh-and-replication-monitor-performance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04924-106">The data displayed in Replication Monitor is queried from a cache; for information about the relationship between the cache and refreshing Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span> <span data-ttu-id="04924-107">복제 모니터를 시작하는 방법은 [복제 모니터 시작](start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04924-107">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a><span data-ttu-id="04924-108">복제 모니터에 대한 새로 고침 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="04924-108">To set refresh options for Replication Monitor</span></span>  
  
1.  <span data-ttu-id="04924-109">복제 모니터의 왼쪽 창에서 게시자를 마우스 오른쪽 단추로 클릭한 다음 **게시자 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04924-109">Right-click a Publisher in the left pane of Replication Monitor, and then click **Publisher Settings**.</span></span>  
  
2.  <span data-ttu-id="04924-110">**게시자 설정** 대화 상자에서 **자동 새로 고침** 및 **새로 고침 빈도** 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="04924-110">In the **Publisher Settings** dialog box, set the **Auto refresh** and **Refresh rate** options.</span></span> <span data-ttu-id="04924-111">**자동 새로 고침** 설정은 복제 모니터의 주 창에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04924-111">The **Auto refresh** setting affects the main window in Replication Monitor.</span></span> <span data-ttu-id="04924-112">**새로 고침 빈도** 설정은 자동으로 새로 고치도록 설정된 세부 정보 창에도 영향을 줍니다. 이러한 설정을 변경하면 변경 후 열린 세부 정보 창에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04924-112">The **Refresh rate** setting also affects any detail windows that are set to refresh automatically (changes to the setting only affect the detail windows opened after the change).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a><span data-ttu-id="04924-113">세부 정보 창이 자동으로 새로 고쳐지도록 지정하려면</span><span class="sxs-lookup"><span data-stu-id="04924-113">To specify that a detail window should automatically refresh</span></span>  
  
1.  <span data-ttu-id="04924-114">다음과 같이</span><span class="sxs-lookup"><span data-stu-id="04924-114">Open a detail window in Replication Monitor.</span></span> <span data-ttu-id="04924-115">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04924-115">For example:</span></span>  
  
    1.  <span data-ttu-id="04924-116">왼쪽 창에서 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04924-116">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
    2.  <span data-ttu-id="04924-117">**모든 구독** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04924-117">Click the **All Subscriptions** tab.</span></span>  
  
    3.  <span data-ttu-id="04924-118">구독을 마우스 오른쪽 단추로 클릭한 다음 **자세히 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04924-118">Right-click a subscription, and then click **View Details**.</span></span>  
  
2.  <span data-ttu-id="04924-119">**구독\<SubscriptionName>** 세부 정보 창에서 **동작**을 클릭한 다음, **자동 새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04924-119">In the **Subscription \<SubscriptionName>** detail window, click **Action**, and then click **Auto Refresh**.</span></span> <span data-ttu-id="04924-120">새로 고침 빈도는 **게시자 설정** 대화 상자의 **새로 고침 빈도** 설정에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="04924-120">The refresh rate is determined by the **Refresh rate** setting in the **Publisher Settings** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04924-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04924-121">See Also</span></span>  
 [<span data-ttu-id="04924-122">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="04924-122">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
