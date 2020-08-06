---
title: "' 게시자 추가 ' 대화 상자"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.addpublisher.f1
helpviewer_keywords:
- Add Publisher dialog box
ms.assetid: 4b57e298-655f-42c2-82bc-25cdad94a194
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c7e607c04aa74db7e5facf13051bf0c47c9dae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646957"
---
# <a name="sql-server-replication-add-publisher-dialog-box"></a><span data-ttu-id="e46d6-102">' 게시자 추가 ' 대화 상자 SQL Server 복제</span><span class="sxs-lookup"><span data-stu-id="e46d6-102">SQL Server Replication 'Add Publisher' dialog box</span></span> 
  <span data-ttu-id="e46d6-103">**게시자 추가** 대화 상자를 사용하여 복제 모니터의 왼쪽 창에 하나 이상의 게시자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-103">The **Add Publisher** dialog box allows you to add to one or more Publishers to the left pane of Replication Monitor.</span></span> <span data-ttu-id="e46d6-104">게시자를 추가한 후 왼쪽 창에서 게시자를 선택하면 오른쪽 창에 해당 게시자에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-104">After adding a Publisher, selecting the Publisher in the left pane shows information on the Publisher in the right pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e46d6-105">옵션</span><span class="sxs-lookup"><span data-stu-id="e46d6-105">Options</span></span>  
 <span data-ttu-id="e46d6-106">**추가**</span><span class="sxs-lookup"><span data-stu-id="e46d6-106">**Add**</span></span>  
 <span data-ttu-id="e46d6-107">추가할 게시자 유형을 선택하려면 클릭합니다. **서버에 연결** 대화 상자가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-107">Click to select a type of Publisher to add, which launches the **Connect to Server** dialog box.</span></span> <span data-ttu-id="e46d6-108">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-108">The options are:</span></span>  
  
-   <span data-ttu-id="e46d6-109">**SQL Server 게시자 추가 ...**</span><span class="sxs-lookup"><span data-stu-id="e46d6-109">**Add SQL Server Publisher...**</span></span>  
  
     <span data-ttu-id="e46d6-110">**서버에 연결** 대화 상자를 사용하여 게시자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-110">Connect to the Publisher using the **Connect to Server** dialog box.</span></span>  
  
-   <span data-ttu-id="e46d6-111">**Oracle 게시자 추가 ...**</span><span class="sxs-lookup"><span data-stu-id="e46d6-111">**Add Oracle Publisher...**</span></span>  
  
     <span data-ttu-id="e46d6-112">**서버에 연결** 대화 상자를 사용하여 Oracle 게시자에 연결된 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 배포자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-112">Connect to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor associated with the Oracle Publisher using the **Connect to Server** dialog box.</span></span>  
  
-   <span data-ttu-id="e46d6-113">**배포자를 지정 하 고 해당 게시자 추가 ...**</span><span class="sxs-lookup"><span data-stu-id="e46d6-113">**Specify a Distributor and Add Its Publishers...**</span></span>  
  
     <span data-ttu-id="e46d6-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서버에 연결 **대화 상자를 사용하여 하나 이상의 게시자에 연결된** 배포자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-114">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor associated with one or more Publishers using the **Connect to Server** dialog box.</span></span>  
  
 <span data-ttu-id="e46d6-115">게시자 또는 배포자에 성공적으로 연결하면 각 게시자 및 해당 배포자의 이름이 대화 상자 상단의 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-115">After successfully connecting to the Publisher or Distributor, the name of each Publisher and its Distributor are displayed in the grid at the top of the dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e46d6-116">배포자 및 게시자가 동일한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 실행되는 경우가 많지만 배포자는 다른 인스턴스에서 실행될 수 있으며 이러한 구성을 원격 배포자라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-116">The Distributor and Publisher often run on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the Distributor can run on another instance (this configuration is referred to as a remote Distributor).</span></span>  
  
 <span data-ttu-id="e46d6-117">**제거**</span><span class="sxs-lookup"><span data-stu-id="e46d6-117">**Remove**</span></span>  
 <span data-ttu-id="e46d6-118">대화 상자 상단의 표에서 게시자를 선택하고 **제거** 를 클릭하여 추가할 게시자 목록에서 해당 게시자를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-118">Select a Publisher in the grid at the top of the dialog box, and click **Remove** to remove the Publisher from the list of Publishers to be added.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e46d6-119">이 단추를 사용하여 이미 복제 모니터에 표시된 게시자를 제거할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-119">This button cannot be used to remove a Publisher that is already displayed in Replication Monitor.</span></span> <span data-ttu-id="e46d6-120">이미 표시된 게시자를 제거하려면 복제 모니터의 왼쪽 창에서 해당 게시자를 마우스 오른쪽 단추로 클릭한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-120">To remove a Publisher that is already displayed right-click the Publisher in the left pane of Replication Monitor and click **Remove**.</span></span>  
  
 <span data-ttu-id="e46d6-121">**복제 모니터가 시작될 때 자동으로 연결**</span><span class="sxs-lookup"><span data-stu-id="e46d6-121">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="e46d6-122">복제 모니터가 자동으로 배포자에 연결하여 대화 상자 상단의 표에 선택된 게시자의 상태 정보를 검색하도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-122">Select to allow Replication Monitor to automatically connect to the Distributor and retrieve status information for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="e46d6-123">이 확인란의 선택을 취소하면 복제 모니터를 시작한 후 복제 모니터의 왼쪽 창에서 게시자를 마우스 오른쪽 단추로 클릭한 다음 **연결**을 클릭하여 수동으로 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-123">If this checkbox is cleared, you must manually connect after launching Replication Monitor: right-click the Publisher in the left pane of Replication Monitor, and click **Connect**.</span></span>  
  
 <span data-ttu-id="e46d6-124">**이 게시자 및 해당 게시의 상태를 자동으로 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="e46d6-124">**Automatically refresh the status of this Publisher and its publications**</span></span>  
 <span data-ttu-id="e46d6-125">복제 모니터가 대화 상자 상단의 표에 선택된 게시자의 상태를 자동으로 새로 고치도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-125">Select to allow Replication Monitor to automatically refresh status for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="e46d6-126">이 옵션을 선택하면 복제 모니터가 배포자를 폴링하여 게시자 및 해당 게시에 대한 상태 정보를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-126">If this option is selected, Replication Monitor polls the Distributor for status information on the Publisher and its publications.</span></span> <span data-ttu-id="e46d6-127">폴링 간격은 **새로 고침 빈도** 옵션으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-127">The polling interval is set by the **Refresh rate** option.</span></span> <span data-ttu-id="e46d6-128">복제 모니터에서의 새로 고침에 대한 자세한 내용은 [캐싱, 새로 고침 및 복제 모니터 성능](monitor/caching-refresh-and-replication-monitor-performance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e46d6-128">For more information on refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="e46d6-129">**새로 고침 빈도**</span><span class="sxs-lookup"><span data-stu-id="e46d6-129">**Refresh rate**</span></span>  
 <span data-ttu-id="e46d6-130">복제 모니터가 상태를 얻기 위해 배포자를 폴링하는 빈도를 지정하는 값(초)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-130">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="e46d6-131">값이 낮을수록 폴링이 자주 수행되며 많은 게시자를 모니터링하는 경우 배포자에서의 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-131">Lower values result in more frequent polling, which can affect performance at the Distributor if you are monitoring a large number of Publishers.</span></span> <span data-ttu-id="e46d6-132">시스템을 테스트하여 적절한 값을 결정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-132">It is recommended that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="e46d6-133">**새로 고침 빈도** 설정은 복제 모니터의 세부 정보 창에서 **자동 새로 고침** 을 선택한 경우에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-133">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="e46d6-134">**이 게시자를 다음 그룹에 표시**</span><span class="sxs-lookup"><span data-stu-id="e46d6-134">**Show this Publisher in the following group**</span></span>  
 <span data-ttu-id="e46d6-135">목록에서 게시자 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-135">Select a Publisher group from the list.</span></span> <span data-ttu-id="e46d6-136">게시자는 왼쪽 창에서 이 그룹 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-136">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="e46d6-137">그룹을 사용하면 게시자를 구성할 수 있으며 이로 인해 복제 기능이 영향을 받지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-137">Groups provide a way to organize Publishers and have no effect on how replication functions.</span></span> <span data-ttu-id="e46d6-138">정의된 그룹이 없거나 새 그룹을 만들려면 **새 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-138">If no groups are defined or you want to create a new one, click **New Group**.</span></span>  
  
 <span data-ttu-id="e46d6-139">**새 그룹**</span><span class="sxs-lookup"><span data-stu-id="e46d6-139">**New Group**</span></span>  
 <span data-ttu-id="e46d6-140">새 게시자 그룹을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-140">Click to create a new Publisher group.</span></span> <span data-ttu-id="e46d6-141">게시자 그룹을 사용하면 복제 모니터 내에서 게시자를 편리하게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-141">A Publisher group provides a convenient way to organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="e46d6-142">그룹은 데이터 복제 또는 복제 토폴로지의 서버 간 관계에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e46d6-142">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46d6-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e46d6-143">See Also</span></span>  
 <span data-ttu-id="e46d6-144">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="e46d6-144">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="e46d6-145">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="e46d6-145">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
