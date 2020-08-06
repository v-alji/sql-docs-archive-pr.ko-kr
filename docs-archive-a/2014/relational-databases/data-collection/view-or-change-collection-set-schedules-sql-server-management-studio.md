---
title: 컬렉션 집합 일정 보기 또는 변경(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.collectionsetprop.uploads.f1
- sql12.swb.dc.collectionsetprop.general.f1
- sql12.swb.dc.collectionsetprop.description.f1
helpviewer_keywords:
- collection sets [SQL Server], changing schedules
- schedules [SQL Server], changing collection set
- collection sets [SQL Server], viewing schedules
- schedules [SQL Server], viewing collection set
ms.assetid: 26336c98-78c5-414f-8d6a-574fc3af60c4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2eb1acf0346b3e16bd1d54829abbc070e1d9d63b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659476"
---
# <a name="view-or-change-collection-set-schedules-sql-server-management-studio"></a><span data-ttu-id="025b4-102">컬렉션 집합 일정 보기 또는 변경(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="025b4-102">View or Change Collection Set Schedules (SQL Server Management Studio)</span></span>
  <span data-ttu-id="025b4-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 컬렉션 집합 일정을 보거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-103">You can view or change collection set schedules by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="025b4-104">컬렉션 모드가 캐시되거나 캐시되지 않은지에 따라 일정을 변경할 수 있는 방법이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-104">The collection mode, cached or non-cached, determines how you can make changes to a schedule.</span></span> <span data-ttu-id="025b4-105">캐시된 모드에서는 컬렉션과 업로드에 별도의 일정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-105">Cached mode uses separate schedules for collection and upload.</span></span> <span data-ttu-id="025b4-106">캐시되지 않은 모드에서는 컬렉션과 업로드에 동일한 일정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-106">Non-cached mode uses the same schedule for collection and upload.</span></span> <span data-ttu-id="025b4-107">각 시스템 데이터 컬렉션 집합에 대한 컬렉션 모드의 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-107">The type of collection mode for each of the System Datacollection sets is as follows:</span></span>  
  
-   <span data-ttu-id="025b4-108">**디스크 사용** 은 캐시되지 않은 컬렉션 모드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-108">**Disk Usage** uses non-cached collection mode.</span></span>  
  
-   <span data-ttu-id="025b4-109">**쿼리 통계** 는 캐시된 컬렉션 모드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-109">**Query Statistics** uses cached collection mode.</span></span>  
  
-   <span data-ttu-id="025b4-110">**서버 작업** 은 캐시된 컬렉션 모드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-110">**Server Activity** uses cached collection mode.</span></span>  
  
### <a name="to-view-collection-set-schedules"></a><span data-ttu-id="025b4-111">컬렉션 집합 일정을 보려면</span><span class="sxs-lookup"><span data-stu-id="025b4-111">To view collection set schedules</span></span>  
  
1.  <span data-ttu-id="025b4-112">개체 탐색기에서 **관리** 노드, **데이터 컬렉션**, **시스템 데이터 컬렉션 집합**을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-112">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="025b4-113">컬렉션 집합 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성** 을 클릭하여 [데이터 컬렉션 집합 속성](#CollectionSet) 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-113">Right-click a collection set name, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
### <a name="to-change-the-schedules-for-a-cached-mode-collection-set"></a><span data-ttu-id="025b4-114">캐시된 모드 컬렉션 집합의 일정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="025b4-114">To change the schedules for a cached mode collection set</span></span>  
  
1.  <span data-ttu-id="025b4-115">개체 탐색기에서 **관리** 노드, **데이터 컬렉션**, **시스템 데이터 컬렉션 집합**을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-115">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="025b4-116">캐시된 모드를 사용하는 컬렉션 집합(예: **쿼리 통계**)을 마우스 오른쪽 단추로 클릭한 다음 **속성** 을 클릭하여 [데이터 컬렉션 집합 속성](#CollectionSet) 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-116">Right-click a collection set that uses cached mode, such as **Query Statistics**, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
3.  <span data-ttu-id="025b4-117">**일반** 페이지에서 컬렉션 빈도를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-117">You can change the collection frequency on the **General** page.</span></span> <span data-ttu-id="025b4-118">이렇게 하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="025b4-118">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="025b4-119">세부 정보 창에서 **컬렉션 항목** 테이블의 **컬렉션 빈도(초)** 열에 표시된 숫자를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-119">In the details pane, double-click the number that is displayed for the **Collection Frequency (sec)** column in the **Collection items** table.</span></span>  
  
    2.  <span data-ttu-id="025b4-120">컬렉션 빈도를 높이거나 낮추려면 더 작거나 큰 숫자를 입력한 후 Enter 키를 눌러 새 값을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-120">To increase or decrease the collection frequency, type a lower or higher number, and then press ENTER to store the new value.</span></span>  
  
4.  <span data-ttu-id="025b4-121">컬렉션 집합의 기존 업로드 일정을 변경하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-121">To change the existing upload schedule for the collection set, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="025b4-122">**업로드** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-122">Click the **Uploads** page.</span></span>  
  
    2.  <span data-ttu-id="025b4-123">세부 정보 창에서 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-123">In the details pane, click **Pick**.</span></span>  
  
         <span data-ttu-id="025b4-124">**작업 일정 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-124">The **Pick Schedule for Job** dialog box opens.</span></span> <span data-ttu-id="025b4-125">사용 가능한 일정이 표 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-125">The available schedules appear as a table.</span></span>  
  
    3.  <span data-ttu-id="025b4-126">원하는 일정의 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-126">Click the row with the schedule that you want.</span></span> <span data-ttu-id="025b4-127">예를 들어, 일정을 5분 간격으로 변경하려면 일정 이름이 **CollectorSchedule_Every_5min**인 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-127">For example, to change the schedule to every 5 minutes, click the row where the schedule name is **CollectorSchedule_Every_5min.**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="025b4-128">**속성** 을 클릭하여 일정에 대한 **작업 일정 속성** 대화 상자를 연 후 선택한 일정의 속성을 보고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-128">You can view and edit the properties for the selected schedule by clicking **Properties** to open the **Job Schedule Properties** dialog box for the schedule.</span></span> <span data-ttu-id="025b4-129">이 대화 상자를 사용하여 빈도와 같은 일정 정보를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-129">You can use this dialog box to change schedule information, such as the frequency.</span></span>  
        >   
        >  <span data-ttu-id="025b4-130">기존 일정을 수정하는 대신 **업로드** 페이지의 **새로 만들기** 를 클릭하여 새 업로드 일정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-130">As an alternative to modifying an existing schedule, you can create a new upload schedule by clicking **New** on the **Uploads** page.</span></span> <span data-ttu-id="025b4-131">이렇게 하면 사용자 지정 일정을 만드는 데 사용할 수 있는 **새 작업 일정** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-131">This action opens the **New Job Schedule** dialog box, which you can use to create a custom schedule.</span></span>  
  
    4.  <span data-ttu-id="025b4-132">일정 구성을 마쳤으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-132">When you are finished configuring the schedule, click **OK**.</span></span>  
  
         <span data-ttu-id="025b4-133">변경한 내용이 **업로드** 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-133">The changes that you made appear on the **Uploads** page.</span></span>  
  
5.  <span data-ttu-id="025b4-134">**확인** 을 클릭하면 컬렉션 빈도 및 업로드 일정에 대한 변경 내용이 저장되고 **데이터 컬렉션 집합 속성** 대화 상자가 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-134">Click **OK** to save the changes to the collection frequency and the upload schedule, and to close the **Data Collection Set Properties** dialog box.</span></span>  
  
### <a name="to-change-the-schedule-for-a-non-cached-mode-collection-set"></a><span data-ttu-id="025b4-135">캐시되지 않은 모드 컬렉션 집합의 일정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="025b4-135">To change the schedule for a non-cached mode collection set</span></span>  
  
1.  <span data-ttu-id="025b4-136">개체 탐색기에서 **관리** 노드, **데이터 컬렉션**, **시스템 데이터 컬렉션 집합**을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-136">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="025b4-137">캐시되지 않은 모드를 사용하는 컬렉션 집합(예: **디스크 사용**)을 마우스 오른쪽 단추로 클릭한 다음 **속성** 을 클릭하여 [데이터 컬렉션 집합 속성](#CollectionSet) 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-137">Right-click a collection set that uses non-cached mode, such as **Disk Usage**, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
     <span data-ttu-id="025b4-138">**데이터 컬렉션 집합 속성** 대화 상자에 컬렉션 집합 속성의 페이지된 뷰가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-138">The **Data Collection Set Properties** dialog box displays a paged view of the collection set properties.</span></span>  
  
3.  <span data-ttu-id="025b4-139">컬렉션 집합의 일정을 변경하려면 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-139">To change the schedule for the collection set, click **Pick**.</span></span>  
  
     <span data-ttu-id="025b4-140">**작업 일정 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-140">The **Pick Schedule for Job** dialog box opens.</span></span> <span data-ttu-id="025b4-141">사용 가능한 일정이 표 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-141">The available schedules are displayed as a table.</span></span>  
  
4.  <span data-ttu-id="025b4-142">원하는 일정의 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-142">Click the row with the schedule that you want.</span></span> <span data-ttu-id="025b4-143">예를 들어, 일정을 5분 간격으로 변경하려면 일정 이름이 **CollectorSchedule_Every_5min**인 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-143">For example, to change the schedule to every 5 minutes, click the row where the schedule name is **CollectorSchedule_Every_5min**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="025b4-144">**속성** 을 클릭하여 일정에 대한 **작업 일정 속성** 대화 상자를 연 후 선택한 일정의 속성을 보고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-144">You can view and edit the properties for the selected schedule by clicking **Properties** to open the **Job Schedule Properties** dialog box for the schedule.</span></span> <span data-ttu-id="025b4-145">이 대화 상자를 사용하여 빈도와 같은 일정 정보를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-145">You can use this dialog box to change schedule information, such as the frequency.</span></span>  
    >   
    >  <span data-ttu-id="025b4-146">기존 일정을 수정하는 대신 **일반** 페이지의 **새로 만들기** 를 클릭하여 수집 및 업로드 일정을 새로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-146">As an alternative to modifying an existing schedule, you can create a new collect and upload schedule by clicking **New** on the **General** page.</span></span> <span data-ttu-id="025b4-147">이렇게 하면 **새 작업 일정** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-147">This action opens the **New Job Schedule** dialog box.</span></span>  
  
5.  <span data-ttu-id="025b4-148">일정 구성을 마쳤으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-148">When you are finished configuring the schedule, click **OK**.</span></span>  
  
6.  <span data-ttu-id="025b4-149">**확인** 을 클릭하면 변경 내용이 저장되고 **데이터 컬렉션 집합 속성** 대화 상자가 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-149">Click **OK** to save the changes and to close the **Data Collection Set Properties** dialog box.</span></span>  
  
####  <a name="data-collection-set-properties-dialog-box"></a><a name="CollectionSet"></a> <span data-ttu-id="025b4-150">데이터 컬렉션 집합 속성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="025b4-150">Data Collection Set Properties Dialog Box</span></span>  
 <span data-ttu-id="025b4-151">**일반 페이지**</span><span class="sxs-lookup"><span data-stu-id="025b4-151">**General Page**</span></span>  
  
 <span data-ttu-id="025b4-152">이 페이지를 사용하여 관리 데이터 웨어하우스에서 데이터를 수집하고 업로드하는 방법, 일정 및 데이터 보존 기간을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-152">Use this page to configure how data is collected and uploaded, configure schedules, and configure data retention periods in the management data warehouse.</span></span> <span data-ttu-id="025b4-153">또한 이 페이지를 사용하면 수집기 유형과 컬렉션 빈도 같은 컬렉션 집합에 대한 정보뿐 아니라 컬렉션 집합에 사용되는 입력 매개 변수도 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-153">This page also provides information about collection sets, such as collector types and collection frequencies, as well as the input parameters that are used for a collection set.</span></span>  
  
 <span data-ttu-id="025b4-154">**이름**</span><span class="sxs-lookup"><span data-stu-id="025b4-154">**Name**</span></span>  
 <span data-ttu-id="025b4-155">이 페이지가 참조하는 컬렉션 집합의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-155">Displays the name of the collection set that this page refers to.</span></span>  
  
 <span data-ttu-id="025b4-156">**데이터 컬렉션 및 업로드**</span><span class="sxs-lookup"><span data-stu-id="025b4-156">**Data collection and upload**</span></span>  
 <span data-ttu-id="025b4-157">데이터를 수집하고 관리 데이터 웨어하우스에 업로드하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-157">Specifies how data is collected and uploaded to the management data warehouse.</span></span> <span data-ttu-id="025b4-158">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-158">Pick one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="025b4-159">**캐시되지 않음. 동일한 일정에 따라 데이터를 수집 및 업로드합니다.**</span><span class="sxs-lookup"><span data-stu-id="025b4-159">**Non-cached. Collection and data upload on the same schedule.**</span></span>|<span data-ttu-id="025b4-160">이 옵션을 선택할 경우 다음 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-160">When selected, specify one of the following:</span></span><br /><br /> <span data-ttu-id="025b4-161">**요청 시**.</span><span class="sxs-lookup"><span data-stu-id="025b4-161">**On-demand**.</span></span> <span data-ttu-id="025b4-162">요청 시 데이터가 수집되고 업로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-162">Data is collected and uploaded on demand.</span></span><br /><br /> <span data-ttu-id="025b4-163">**일정**.</span><span class="sxs-lookup"><span data-stu-id="025b4-163">**Schedule**.</span></span> <span data-ttu-id="025b4-164">일정에 따라 데이터가 수집되고 업로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-164">Data is collected and uploaded according to a schedule.</span></span> <span data-ttu-id="025b4-165">**선택** 을 클릭하여 미리 정의된 일정 목록에서 선택하거나 **새로 만들기** 를 클릭하여 새 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-165">Click **Pick** to select from a predefined list of schedules, or click **New** to create a new schedule.</span></span>|  
|<span data-ttu-id="025b4-166">**캐시됨. 컬렉션 빈도 집합에 따라 데이터를 수집 및 캐시합니다. 캐시된 데이터는 별도의 일정에 따라 업로드합니다.**</span><span class="sxs-lookup"><span data-stu-id="025b4-166">**Cached. Collect and cache data at a set of collection frequencies. Upload cached data on a separate schedule.**</span></span>|<span data-ttu-id="025b4-167">지정된 컬렉션 빈도에 따라 데이터를 수집 및 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-167">Collect and cache data for a specified collection frequency.</span></span> <span data-ttu-id="025b4-168">수집된 데이터는 별도의 일정에 따라 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-168">Upload the collected data on a separate schedule.</span></span>|  
  
 <span data-ttu-id="025b4-169">**컬렉션 빈도(초)**</span><span class="sxs-lookup"><span data-stu-id="025b4-169">**Collection items**</span></span>  
 <span data-ttu-id="025b4-170">컬렉션 집합에 있는 컬렉션 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-170">Displays the collection items in the collection set.</span></span> <span data-ttu-id="025b4-171">각 컬렉션 항목에 대해 다음과 같은 정보가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-171">The following information is provided for each collection item:</span></span>  
  
-   <span data-ttu-id="025b4-172">**이름**</span><span class="sxs-lookup"><span data-stu-id="025b4-172">**Name**</span></span>  
  
-   <span data-ttu-id="025b4-173">**수집기 유형**</span><span class="sxs-lookup"><span data-stu-id="025b4-173">**Collector Type**</span></span>  
  
-   <span data-ttu-id="025b4-174">**컬렉션 빈도** (초).</span><span class="sxs-lookup"><span data-stu-id="025b4-174">**Collection Frequency** (secs).</span></span> <span data-ttu-id="025b4-175">**데이터 컬렉션 및 업로드** 가 캐시된 것으로 구성되면 이 필드를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-175">This field is editable if **Data collection and upload** is configured as cached.</span></span> <span data-ttu-id="025b4-176">컬렉션 빈도를 설정하려면 이 셀을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-176">Double-click this cell to set the collection frequency.</span></span>  
  
 <span data-ttu-id="025b4-177">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="025b4-177">**Input parameters**</span></span>  
 <span data-ttu-id="025b4-178">컬렉션 집합에 사용되는 입력 매개 변수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-178">Displays the input parameters used for the collection set.</span></span>  
  
 <span data-ttu-id="025b4-179">**다음 계정으로 실행**</span><span class="sxs-lookup"><span data-stu-id="025b4-179">**Run as**</span></span>  
 <span data-ttu-id="025b4-180">컬렉션 집합을 실행하는 데 사용되는 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-180">Specifies the account used to run the collection set.</span></span> <span data-ttu-id="025b4-181">기본적으로 이 계정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-181">By default this is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service Account.</span></span> <span data-ttu-id="025b4-182">프록시 계정이 정의된 경우 이 목록에 사용 가능한 프록시 계정의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-182">If proxy accounts are defined, this list includes the names of the available proxy accounts.</span></span>  
  
 <span data-ttu-id="025b4-183">**수집된 데이터를 관리 데이터 웨어하우스에 보유할 기간 지정**</span><span class="sxs-lookup"><span data-stu-id="025b4-183">**Set how long collected data will be retained in the management data warehouse.**</span></span>  
 <span data-ttu-id="025b4-184">수집된 데이터의 보유 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-184">Specifies how long collected data is retained.</span></span> <span data-ttu-id="025b4-185">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-185">Pick one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="025b4-186">**데이터 보유 기간**</span><span class="sxs-lookup"><span data-stu-id="025b4-186">**Retain data for**</span></span>|<span data-ttu-id="025b4-187">이 옵션은 기본적으로 선택되어 있으며 기본 보유 기간은 14일입니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-187">This option is selected by default, and the default retention period is 14 days.</span></span>|  
|<span data-ttu-id="025b4-188">**데이터 무기한 보유**</span><span class="sxs-lookup"><span data-stu-id="025b4-188">**Retain data indefinitely**</span></span>|<span data-ttu-id="025b4-189">데이터 보유 기간에 시간 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-189">There is no time limit on the length of time that data is retained.</span></span>|  
  
 <span data-ttu-id="025b4-190">**업로드 페이지**</span><span class="sxs-lookup"><span data-stu-id="025b4-190">**Uploads Page**</span></span>  
  
 <span data-ttu-id="025b4-191">이 페이지를 사용하여 이 컬렉션 집합에 의해 수집되는 데이터의 업로드 일정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-191">Use this page to configure the upload schedule for data that is collected by this collection set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="025b4-192">이 탭은 **데이터 컬렉션 및 업로드** 에 **캐시됨**옵션이 구성된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-192">This tab is only enabled if the **Cached** option is configured for **Data collection and upload**.</span></span>  
  
 <span data-ttu-id="025b4-193">**Server**</span><span class="sxs-lookup"><span data-stu-id="025b4-193">**Server**</span></span>  
 <span data-ttu-id="025b4-194">관리 데이터 웨어하우스를 호스팅하는 서버의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-194">Displays the name of the server that hosts the management data warehouse.</span></span> <span data-ttu-id="025b4-195">자세한 내용은 [관리 데이터 웨어하우스 구성&#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="025b4-195">For more information, see [Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="025b4-196">**관리 데이터 웨어하우스**</span><span class="sxs-lookup"><span data-stu-id="025b4-196">**Management data warehouse**</span></span>  
 <span data-ttu-id="025b4-197">관리 데이터 웨어하우스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-197">Displays the name of the management data warehouse.</span></span> <span data-ttu-id="025b4-198">자세한 내용은 [관리 데이터 웨어하우스 구성&#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="025b4-198">For more information, see [Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="025b4-199">**마지막 업로드**</span><span class="sxs-lookup"><span data-stu-id="025b4-199">**Last upload**</span></span>  
 <span data-ttu-id="025b4-200">컬렉션 집합을 마지막으로 업로드한 날짜와 시간 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-200">Displays date and time information for the last upload done for the collection set.</span></span>  
  
 <span data-ttu-id="025b4-201">**업로드 일정**</span><span class="sxs-lookup"><span data-stu-id="025b4-201">**Upload schedule**</span></span>  
 <span data-ttu-id="025b4-202">컬렉션 집합에 대한 업로드 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-202">Specifies the upload schedule for the collection set.</span></span> <span data-ttu-id="025b4-203">이 옵션을 사용하는 경우 **선택** 을 클릭하여 미리 정의된 일정 목록에서 선택하거나 **새로 만들기** 를 클릭하여 새 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-203">If enabled, Click **Pick** to select from a predefined list of schedules, or click **New** to create a new schedule.</span></span>  
  
 <span data-ttu-id="025b4-204">**설명 페이지**</span><span class="sxs-lookup"><span data-stu-id="025b4-204">**Description Page**</span></span>  
  
 <span data-ttu-id="025b4-205">이 페이지를 사용하여 이 속성 페이지가 참조하는 컬렉션 집합에 대한 설명을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025b4-205">Use this page to view a description of the collection set that this properties page refers to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="025b4-206">참고 항목</span><span class="sxs-lookup"><span data-stu-id="025b4-206">See Also</span></span>  
 <span data-ttu-id="025b4-207">[데이터 컬렉션 관리](manage-data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="025b4-207">[Manage Data Collection](manage-data-collection.md) </span></span>  
 [<span data-ttu-id="025b4-208">데이터 컬렉션</span><span class="sxs-lookup"><span data-stu-id="025b4-208">Data Collection</span></span>](data-collection.md)  
  
  
