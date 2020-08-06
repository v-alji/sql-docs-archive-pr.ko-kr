---
title: SQL Server 복제 '게시자 설정' 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a9a5ca5b0d7bfae895287708af159f3316e4474
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740811"
---
# <a name="sql-server-replication-publisher-settings-dialog-box"></a><span data-ttu-id="1b7cf-102">SQL Server 복제 '게시자 설정' 대화 상자</span><span class="sxs-lookup"><span data-stu-id="1b7cf-102">SQL Server Replication 'Publisher Settings' dialog box</span></span>
  <span data-ttu-id="1b7cf-103">**게시자 설정** 대화 상자에서 복제 모니터의 왼쪽 창에 추가된 게시자에 대한 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-103">The **Publisher Settings** dialog box allows you to change settings for Publishers that have been added to the left pane in Replication Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1b7cf-104">옵션</span><span class="sxs-lookup"><span data-stu-id="1b7cf-104">Options</span></span>  
 <span data-ttu-id="1b7cf-105">**게시자 연결**</span><span class="sxs-lookup"><span data-stu-id="1b7cf-105">**Publisher Connection**</span></span>  
 <span data-ttu-id="1b7cf-106">복제 모니터에서 게시자에 연결하기 위해 사용하는 연결 속성 및 자격 증명을 보고 변경할 수 있는 **서버에 연결** 대화 상자를 시작하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-106">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to a Publisher.</span></span>  
  
 <span data-ttu-id="1b7cf-107">**배포자 연결**</span><span class="sxs-lookup"><span data-stu-id="1b7cf-107">**Distributor Connection**</span></span>  
 <span data-ttu-id="1b7cf-108">게시자가 원격 배포자를 사용하는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-108">Displayed only if the Publisher uses a remote Distributor.</span></span> <span data-ttu-id="1b7cf-109">복제 모니터에서 원격 배포자에 연결하기 위해 사용하는 연결 속성 및 자격 증명을 보고 변경할 수 있는 **서버에 연결** 대화 상자를 시작하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-109">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to the remote Distributor.</span></span>  
  
 <span data-ttu-id="1b7cf-110">**복제 모니터가 시작될 때 자동으로 연결**</span><span class="sxs-lookup"><span data-stu-id="1b7cf-110">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="1b7cf-111">복제 모니터가 자동으로 배포자에 연결하여 대화 상자 상단의 표에 선택된 게시자의 상태 정보를 검색하도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-111">Select to allow Replication Monitor to automatically connect to the Distributor and retrieve status information for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="1b7cf-112">이 확인란의 선택을 취소하면 복제 모니터를 시작한 후 복제 모니터의 왼쪽 창에서 게시자를 마우스 오른쪽 단추로 클릭한 다음 **연결**을 클릭하여 수동으로 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-112">If this checkbox is cleared, you must manually connect after launching Replication Monitor: right-click the Publisher in the left pane of Replication Monitor, and click **Connect**.</span></span>  
  
 <span data-ttu-id="1b7cf-113">**이 게시자 및 해당 게시의 상태를 자동으로 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="1b7cf-113">**Automatically refresh the status of this Publisher and its publications**</span></span>  
 <span data-ttu-id="1b7cf-114">복제 모니터가 대화 상자 상단의 표에 선택된 게시자의 상태를 자동으로 새로 고치도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-114">Select to allow Replication Monitor to automatically refresh status for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="1b7cf-115">이 옵션을 선택하면 복제 모니터가 배포자를 폴링하여 게시자 및 해당 게시에 대한 상태 정보를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-115">If this option is selected, Replication Monitor polls the Distributor for status information on the Publisher and its publications.</span></span> <span data-ttu-id="1b7cf-116">폴링 간격은 **새로 고침 빈도** 옵션으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-116">The polling interval is set by the **Refresh rate** option.</span></span> <span data-ttu-id="1b7cf-117">복제 모니터에서의 새로 고침에 대한 자세한 내용은 [캐싱, 새로 고침 및 복제 모니터 성능](monitor/caching-refresh-and-replication-monitor-performance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-117">For more information on refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="1b7cf-118">**새로 고침 빈도**</span><span class="sxs-lookup"><span data-stu-id="1b7cf-118">**Refresh rate**</span></span>  
 <span data-ttu-id="1b7cf-119">복제 모니터가 상태를 얻기 위해 배포자를 폴링하는 빈도를 지정하는 값(초)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-119">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="1b7cf-120">값이 낮을수록 폴링이 자주 수행되며 많은 게시자를 모니터링하는 경우 배포자에서의 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-120">Lower values result in more frequent polling, which can affect performance at the Distributor if you are monitoring a large number of Publishers.</span></span> <span data-ttu-id="1b7cf-121">시스템을 테스트하여 적절한 값을 결정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-121">It is recommended that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="1b7cf-122">**새로 고침 빈도** 설정은 복제 모니터의 세부 정보 창에서 **자동 새로 고침** 을 선택한 경우에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-122">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="1b7cf-123">**이 게시자를 다음 그룹에 표시**</span><span class="sxs-lookup"><span data-stu-id="1b7cf-123">**Show this Publisher in the following group**</span></span>  
 <span data-ttu-id="1b7cf-124">목록에서 게시자 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-124">Select a Publisher group from the list.</span></span> <span data-ttu-id="1b7cf-125">게시자는 왼쪽 창에서 이 그룹 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-125">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="1b7cf-126">그룹을 사용하면 게시자를 구성할 수 있으며 이로 인해 복제 기능이 영향을 받지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-126">Groups provide a way to organize Publishers and have no effect on how replication functions.</span></span>  
  
 <span data-ttu-id="1b7cf-127">**새 그룹**</span><span class="sxs-lookup"><span data-stu-id="1b7cf-127">**New Group**</span></span>  
 <span data-ttu-id="1b7cf-128">새 게시자 그룹을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-128">Click to create a new Publisher group.</span></span> <span data-ttu-id="1b7cf-129">게시자 그룹을 사용하면 복제 모니터 내에서 게시자를 편리하게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-129">A Publisher group provides a convenient way to organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="1b7cf-130">그룹은 데이터 복제 또는 복제 토폴로지의 서버 간 관계에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b7cf-130">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7cf-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1b7cf-131">See Also</span></span>  
 <span data-ttu-id="1b7cf-132">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="1b7cf-132">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="1b7cf-133">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="1b7cf-133">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
