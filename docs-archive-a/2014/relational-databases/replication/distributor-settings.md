---
title: "' 배포자 설정 ' 대화 상자 | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.DistributorSettings.f1
helpviewer_keywords:
- Distributor Settings dialog box
ms.assetid: 8276a521-bdd1-4783-bdb6-7ab43499c0ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b864620f155e899868c95f58350f98e2b659c4e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646913"
---
# <a name="sql-server-replication-distributor-settings-dialog-box"></a><span data-ttu-id="ab183-102">SQL Server 복제 ' 배포자 설정 ' 대화 상자</span><span class="sxs-lookup"><span data-stu-id="ab183-102">SQL Server Replication 'Distributor Settings' dialog box</span></span>
  <span data-ttu-id="ab183-103">**배포자 설정** 대화 상자에서는 복제 모니터의 왼쪽 창에 추가된 배포자에 대한 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-103">The **Distributor Settings** dialog box enables you to change settings for Distributors that were added to the left pane in Replication Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ab183-104">옵션</span><span class="sxs-lookup"><span data-stu-id="ab183-104">Options</span></span>  
 <span data-ttu-id="ab183-105">**복제 모니터가 시작될 때 자동으로 연결**</span><span class="sxs-lookup"><span data-stu-id="ab183-105">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="ab183-106">복제 모니터에서 배포자에 연결하고 상태 정보를 검색하도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-106">Select to let Replication Monitor connect to the Distributor and retrieve status information.</span></span>  
  
 <span data-ttu-id="ab183-107">**연결**</span><span class="sxs-lookup"><span data-stu-id="ab183-107">**Connection**</span></span>  
 <span data-ttu-id="ab183-108">**서버에 연결** 대화 상자를 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-108">Click to display the **Connect to Server** dialog box.</span></span> <span data-ttu-id="ab183-109">이 대화 상자를 통해 복제 모니터에서 배포자에 연결하기 위해 사용하는 연결 속성 및 자격 증명을 보고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-109">This enables you to view and change the connection properties and credentials that Replication Monitor uses to connect to the Distributor.</span></span>  
  
 <span data-ttu-id="ab183-110">**이 배포자 및 해당 게시의 상태를 자동으로 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="ab183-110">**Automatically refresh the status of this Distributor and its publications**</span></span>  
 <span data-ttu-id="ab183-111">복제 모니터에서 배포자의 상태를 자동으로 새로 고치도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-111">Select to let Replication Monitor automatically refresh the status for the Distributor.</span></span> <span data-ttu-id="ab183-112">이 옵션을 선택하면 복제 모니터가 **새로 고침 빈도** 옵션에 설정된 폴링 간격에 따라 배포자를 폴링하여 상태 정보를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-112">If this option is selected, Replication Monitor polls the Distributor for status information based on the polling interval set by the **Refresh rate** option.</span></span> <span data-ttu-id="ab183-113">복제 모니터에서의 새로 고침에 대한 자세한 내용은 [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ab183-113">For more information about refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="ab183-114">**새로 고침 빈도**</span><span class="sxs-lookup"><span data-stu-id="ab183-114">**Refresh rate**</span></span>  
 <span data-ttu-id="ab183-115">복제 모니터가 상태를 얻기 위해 배포자를 폴링하는 빈도를 지정하는 값(초)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-115">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="ab183-116">값이 낮을수록 폴링이 자주 수행되며</span><span class="sxs-lookup"><span data-stu-id="ab183-116">Lower values result in more frequent polling.</span></span> <span data-ttu-id="ab183-117">많은 게시자를 모니터링하는 경우 배포자에서의 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-117">This can affect performance at the Distributor if you are monitoring many Publishers.</span></span> <span data-ttu-id="ab183-118">시스템을 테스트하여 적절한 값을 결정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-118">We recommend that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="ab183-119">**새로 고침 빈도** 설정은 복제 모니터의 세부 정보 창에서 **자동 새로 고침** 을 선택한 경우에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-119">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="ab183-120">**다음 그룹에 있는 이 배포자의 모든 게시자 표시**</span><span class="sxs-lookup"><span data-stu-id="ab183-120">**Show all Publishers of this Distributor in the following group**</span></span>  
 <span data-ttu-id="ab183-121">목록에서 게시자 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-121">Select a Publisher group from the list.</span></span> <span data-ttu-id="ab183-122">게시자는 왼쪽 창에서 이 그룹 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-122">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="ab183-123">그룹을 사용하면 게시자를 구성할 수 있으며 이로 인해 복제 기능이 영향을 받지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-123">Groups provide a way for you to organize Publishers and do not affect how replication functions.</span></span>  
  
 <span data-ttu-id="ab183-124">**새 그룹**</span><span class="sxs-lookup"><span data-stu-id="ab183-124">**New Group**</span></span>  
 <span data-ttu-id="ab183-125">새 게시자 그룹을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-125">Click to create a new Publisher group.</span></span> <span data-ttu-id="ab183-126">게시자 그룹을 사용하면 복제 모니터 내에서 게시자를 편리하게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-126">A Publisher group provides a way for you to conveniently organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="ab183-127">그룹은 데이터 복제 또는 복제 토폴로지의 서버 간 관계에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab183-127">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab183-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab183-128">See Also</span></span>  
 <span data-ttu-id="ab183-129">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="ab183-129">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="ab183-130">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="ab183-130">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
