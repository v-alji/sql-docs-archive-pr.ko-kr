---
title: SQL Server 2014 설치 복구 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 90c11b28-892b-44d6-978e-0eee48c75b7d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e382137a971b3f8b23cf1d814bff9908f04150
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732903"
---
# <a name="drop-a-sql-server-2014-installation"></a><span data-ttu-id="34d5a-102">SQL Server 2014 설치 삭제</span><span class="sxs-lookup"><span data-stu-id="34d5a-102">Drop a SQL Server 2014 Installation</span></span>
  <span data-ttu-id="34d5a-103">복구 작업은 다음 시나리오에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-103">Repair operation can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="34d5a-104">성공적으로 설치된 후 손상된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 복구</span><span class="sxs-lookup"><span data-stu-id="34d5a-104">Repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is corrupted after it was successfully installed.</span></span>  
  
-   <span data-ttu-id="34d5a-105">인스턴스 이름을 새로 업그레이드한 인스턴스에 매핑한 후 업그레이드 작업을 취소하거나 업그레이드 작업에 실패한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 복구</span><span class="sxs-lookup"><span data-stu-id="34d5a-105">Repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if the upgrade operation is cancelled or fails after the instance name is mapped to the newly-upgraded instance.</span></span>  
  
    -   <span data-ttu-id="34d5a-106">요약 로그에 다음 메시지가 표시되면 실패한 업그레이드 인스턴스를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-106">If you see the following message in the summary log, you can repair the failed upgrade instance:</span></span>  
  
         <span data-ttu-id="34d5a-107">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 업그레이드하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-107">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade failed.</span></span> <span data-ttu-id="34d5a-108">계속하려면 실패 이유를 조사하고 문제를 해결한 다음 설치를 복구하십시오."</span><span class="sxs-lookup"><span data-stu-id="34d5a-108">To continue, investigate the reason for the failure, correct the problem, and then repair your installation."</span></span>  
  
    -   <span data-ttu-id="34d5a-109">요약 로그에 다음 메시지가 표시되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제거한 후 다시 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-109">If you see the following message in the summary log, you need to uninstall and reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="34d5a-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-110">You cannot repair the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
         <span data-ttu-id="34d5a-111">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 업그레이드하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-111">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade failed.</span></span> <span data-ttu-id="34d5a-112">계속하려면 실패 이유를 조사하고 문제를 해결하십시오."</span><span class="sxs-lookup"><span data-stu-id="34d5a-112">To continue, investigate the reason for the failure, correct the problem."</span></span>  
  
 <span data-ttu-id="34d5a-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 복구하는 경우</span><span class="sxs-lookup"><span data-stu-id="34d5a-113">When you repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="34d5a-114">없거나 손상된 파일을 모두 대체한 경우</span><span class="sxs-lookup"><span data-stu-id="34d5a-114">All missing or corrupt files are replaced.</span></span>  
  
-   <span data-ttu-id="34d5a-115">없거나 손상된 레지스트리 키를 모두 대체한 경우</span><span class="sxs-lookup"><span data-stu-id="34d5a-115">All missing or corrupt registry keys are replaced.</span></span>  
  
-   <span data-ttu-id="34d5a-116">없거나 잘못된 구성 값을 모두 기본값으로 설정한 경우</span><span class="sxs-lookup"><span data-stu-id="34d5a-116">All missing or invalid configuration values are set to default values.</span></span>  
  
 <span data-ttu-id="34d5a-117">계속하기 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터의 경우 다음 중요 정보를 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="34d5a-117">Before you continue, for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover clusters, review the following important information:</span></span>  
  
-   <span data-ttu-id="34d5a-118">복구는 개별 클러스터 노드에서 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-118">Repair must be run on individual cluster nodes.</span></span>  
  
-   <span data-ttu-id="34d5a-119">준비 작업에 실패한 후 장애 조치(Failover) 클러스터 노드를 복구하려면 **노드 제거** 를 사용한 다음 준비 단계를 다시 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-119">To repair a failover cluster node after a failed Prepare operation, use **Remove node** and then perform the Prepare step again.</span></span> <span data-ttu-id="34d5a-120">자세한 내용은 [SQL Server 장애 조치(failover) 클러스터에서 노드 추가 또는 제거&#40;설치 프로그램&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34d5a-120">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
### <a name="to-repair-a-failed-installation-of-ssnoversion-from-the-installation-center"></a><span data-ttu-id="34d5a-121">설치 센터에서 실패한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치를 복구하려면</span><span class="sxs-lookup"><span data-stu-id="34d5a-121">To repair a failed installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the Installation Center</span></span>  
  
1.  <span data-ttu-id="34d5a-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 미디어를 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램(setup.exe)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-122">Launch the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program (setup.exe) from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span>  
  
2.  <span data-ttu-id="34d5a-123">필수 구성 요소 및 시스템 확인이 끝나면 설치 프로그램에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 센터 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-123">After prerequisites and system verification, the Setup program will display the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center page.</span></span>  
  
3.  <span data-ttu-id="34d5a-124">왼쪽의 탐색 영역에서 **유지 관리** 를 클릭한 다음 **복구** 를 클릭하여 복구 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-124">Click **Maintenance** in the left-hand navigation area, and then click **Repair** to start the repair operation.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="34d5a-125">시작 메뉴를 사용하여 설치 센터를 시작한 경우 지금은 설치 미디어의 위치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-125">If the Installation Center was launched using the start menu, you will need to provide the location of the installation media at this time.</span></span>  
  
4.  <span data-ttu-id="34d5a-126">시스템에 필수 구성 요소가 설치되어 있고 컴퓨터가 설치 유효성 검사 규칙을 통과하는지 확인하기 위해 설치 지원 규칙 및 파일 루틴이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-126">Setup support rule and file routines will run to ensure that your system has prerequisites installed and that the computer passes Setup validation rules.</span></span> <span data-ttu-id="34d5a-127">계속하려면 **확인** 또는 **설치** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-127">Click **OK** or **Install** to continue.</span></span>  
  
5.  <span data-ttu-id="34d5a-128">인스턴스 선택 페이지에서 복구할 인스턴스를 선택한 후 **다음** 을 클릭하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-128">On the Select Instance page, select the instance to repair, and then click **Next** to continue.</span></span>  
  
6.  <span data-ttu-id="34d5a-129">작업이 유효한지 검사하는 복구 규칙이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-129">The repair rules will run to validate the operation.</span></span> <span data-ttu-id="34d5a-130">계속하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-130">To continue, click **Next**.</span></span>  
  
7.  <span data-ttu-id="34d5a-131">복구 준비 페이지에서 작업을 진행할 준비가 되었음을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-131">The Ready to Repair page indicates that the operation is ready to proceed.</span></span> <span data-ttu-id="34d5a-132">계속하려면 **복구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-132">To continue, click **Repair**.</span></span>  
  
8.  <span data-ttu-id="34d5a-133">복구 진행률 페이지에 복구 작업 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-133">The Repair Progress page shows the status of the repair operation.</span></span> <span data-ttu-id="34d5a-134">완료 페이지에서 작업이 완료되었음을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-134">The Complete page indicates that the operation is finished.</span></span>  
  
### <a name="to-repair-a-failed-installation-of-ssnoversion-using-command-prompt"></a><span data-ttu-id="34d5a-135">명령 프롬프트를 사용하여 실패한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치를 복구하려면</span><span class="sxs-lookup"><span data-stu-id="34d5a-135">To repair a failed installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Command Prompt</span></span>  
  
1.  <span data-ttu-id="34d5a-136">명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="34d5a-136">Run the following command at a command prompt:</span></span>  
  
    ```  
    Setup.exe /q /ACTION=Repair /INSTANCENAME=instancename  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="34d5a-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34d5a-137">See Also</span></span>  
 <span data-ttu-id="34d5a-138">[SQL Server 설치 로그 파일 보기 및 읽기](view-and-read-sql-server-setup-log-files.md) </span><span class="sxs-lookup"><span data-stu-id="34d5a-138">[View and Read SQL Server Setup Log Files](view-and-read-sql-server-setup-log-files.md) </span></span>  
 [<span data-ttu-id="34d5a-139">설치 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="34d5a-139">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
  
  
