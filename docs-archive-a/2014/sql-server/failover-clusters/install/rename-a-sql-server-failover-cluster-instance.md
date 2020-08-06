---
title: SQL Server 장애 조치(Failover) 클러스터 인스턴스 이름 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], virtual servers
- renaming virtual servers
- virtual servers [SQL Server], failover clustering
- failover clustering [SQL Server], virtual servers
ms.assetid: 2a49d417-25fb-4760-8ae5-5871bfb1e6f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 397e36931e446861db0fcb899cad30e8c7b1ffc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650586"
---
# <a name="rename-a-sql-server-failover-cluster-instance"></a><span data-ttu-id="3b235-102">SQL Server 장애 조치(Failover) 클러스터 인스턴스 이름 변경</span><span class="sxs-lookup"><span data-stu-id="3b235-102">Rename a SQL Server Failover Cluster Instance</span></span>
  <span data-ttu-id="3b235-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 장애 조치 클러스터의 일부인 경우 가상 서버의 이름을 바꾸는 방법은 독립 실행형 인스턴스의 이름을 바꾸는 방법과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-103">When a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance is part of a failover cluster, the process of renaming the virtual server differs from that of renaming a stand-alone instance.</span></span> <span data-ttu-id="3b235-104">자세한 내용은 [SQL Server의 독립 실행형 인스턴스를 호스팅하는 컴퓨터 이름 바꾸기](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b235-104">For more information, see [Rename a Computer that Hosts a Stand-Alone Instance of SQL Server](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="3b235-105">가상 서버의 이름은 항상 SQL 네트워크 이름(SQL 가상 서버 네트워크 이름)과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-105">The name of the virtual server is always the same as the name of the SQL Network Name (the SQL Virtual Server Network Name).</span></span> <span data-ttu-id="3b235-106">가상 서버의 이름은 바꿀 수 있지만 인스턴스 이름은 바꿀 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-106">Although you can change the name of the virtual server, you cannot change the instance name.</span></span> <span data-ttu-id="3b235-107">예를 들어 VS1\instance1이라는 가상 서버 이름을 SQL35\instance1과 같은 다른 이름으로 바꿀 수 있지만 이름 중 인스턴스 부분인 instance1은 바뀌지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-107">For example, you can change a virtual server named VS1\instance1 to some other name, such as SQL35\instance1, but the instance portion of the name, instance1, will remain unchanged.</span></span>  
  
 <span data-ttu-id="3b235-108">이름 바꾸기 프로세스를 시작하기 전에 아래 항목을 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b235-108">Before you begin the renaming process, review the items below.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="3b235-109">는 복제와 함께 로그 전달을 사용하는 경우를 제외하고 복제 시 서버 이름 바꾸기를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-109">does not support renaming servers involved in replication, except in the case of using log shipping with replication.</span></span> <span data-ttu-id="3b235-110">주 서버가 영구적으로 손실되면 로그 전달의 보조 서버 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-110">The secondary server in log shipping can be renamed if the primary server is permanently lost.</span></span> <span data-ttu-id="3b235-111">자세한 내용은 [로그 전달 및 복제&#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b235-111">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="3b235-112">데이터베이스 미러링을 사용하도록 구성된 가상 서버 이름을 바꿀 때는 이름 바꾸기 작업을 수행하기 전에 데이터베이스 미러링을 해제한 다음 새로운 가상 서버 이름으로 데이터베이스 미러링을 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-112">When renaming a virtual server that is configured to use database mirroring, you must turn off database mirroring before the renaming operation, and then re-establish database mirroring with the new virtual server name.</span></span> <span data-ttu-id="3b235-113">데이터베이스 미러링의 메타데이터는 새로운 가상 서버 이름을 반영하도록 자동으로 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-113">Metadata for database mirroring will not be updated automatically to reflect the new virtual server name.</span></span>  
  
### <a name="to-rename-a-virtual-server"></a><span data-ttu-id="3b235-114">가상 서버 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="3b235-114">To rename a virtual server</span></span>  
  
1.  <span data-ttu-id="3b235-115">클러스터 관리자를 사용하여 SQL 네트워크 이름을 새 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-115">Using Cluster Administrator, change the SQL Network Name to the new name.</span></span>  
  
2.  <span data-ttu-id="3b235-116">네트워크 이름 리소스를 오프라인으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-116">Take the network name resource offline.</span></span> <span data-ttu-id="3b235-117">이 작업을 수행하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 리소스와 다른 종속된 리소스도 오프라인이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-117">This takes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource and other dependent resources offline as well.</span></span>  
  
3.  <span data-ttu-id="3b235-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 리소스를 다시 온라인으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-118">Bring the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource back online.</span></span>  
  
## <a name="verify-the-renaming-operation"></a><span data-ttu-id="3b235-119">이름 바꾸기 작업 확인</span><span class="sxs-lookup"><span data-stu-id="3b235-119">Verify the Renaming Operation</span></span>  
 <span data-ttu-id="3b235-120">가상 서버 이름을 바꾼 후 이전 이름을 사용하던 연결은 새 이름을 사용하여 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-120">After a virtual server has been renamed, any connections that used the old name must now connect using the new name.</span></span>  
  
 <span data-ttu-id="3b235-121">이러한 남은 작업이 완료되었는지 확인하기 위해 `@@servername` 또는 `sys.servers`에서 정보를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-121">To verify that the renaming operation has completed, select information from either `@@servername` or `sys.servers`.</span></span> <span data-ttu-id="3b235-122">`@@servername` 함수는 새로운 가상 서버 이름을 반환하며 `sys.servers` 테이블은 새로운 가상 서버 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-122">The `@@servername` function will return the new virtual server name, and the `sys.servers` table will show the new virtual server name.</span></span> <span data-ttu-id="3b235-123">또한 장애 조치 프로세스가 새 이름으로 제대로 작동하는지 확인하기 위해 다른 노드에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 리소스에 오류를 발생시켜 봐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-123">To verify that the failover process is working correctly with the new name, the user should also try to fail the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource over to the other nodes.</span></span>  
  
 <span data-ttu-id="3b235-124">클러스터 노드로부터의 연결에서는 새 이름을 거의 즉시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-124">For connections from any node in the cluster, the new name can be used almost immediately.</span></span> <span data-ttu-id="3b235-125">하지만 클라이언트 컴퓨터의 새 이름을 사용하는 연결에서는 새 이름이 클라이언트 컴퓨터에 표시되기 전까지 새 이름을 사용하여 서버에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-125">However, for connections using the new name from a client computer, the new name cannot be used to connect to the server until the new name is visible to that client computer.</span></span> <span data-ttu-id="3b235-126">새 이름이 네트워크를 통해 전파되는 데 필요한 시간은 몇 초 정도 걸릴 수 있으며 네트워크 구성에 따라 3-5분까지 걸릴 수도 있습니다. 이전 가상 서버 이름이 네트워크에서 사라지는 데에도 추가 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-126">The length of time required for the new name to be propagated across a network can be a few seconds, or as long as 3 to 5 minutes, depending on the network configuration; additional time may be required before the old virtual server name is no longer visible on the network.</span></span>  
  
 <span data-ttu-id="3b235-127">가상 서버 이름 바꾸기 작업에 따른 네트워크 전파 지연을 최소화하려면 다음과 같은 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b235-127">To minimize network propagation delay of a virtual server renaming operation, use the following steps:</span></span>  
  
#### <a name="to-minimize-network-propagation-delay"></a><span data-ttu-id="3b235-128">네트워크 전파 지연을 최소화하려면</span><span class="sxs-lookup"><span data-stu-id="3b235-128">To minimize network propagation delay</span></span>  
  
1.  <span data-ttu-id="3b235-129">서버 노드의 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-129">Issue the following commands from a command prompt on the server node:</span></span>  
  
    ```  
    ipconfig /flushdns  
    ipconfig /registerdns  
    nbtstat -RR  
    ```  
  
## <a name="additional-considerations-after-the-renaming-operation"></a><span data-ttu-id="3b235-130">이름 바꾸기 작업 후 추가 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3b235-130">Additional considerations after the Renaming Operation</span></span>  
 <span data-ttu-id="3b235-131">장애 조치(Failover) 클러스터의 네트워크 이름을 바꾼 후에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 및 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서 모든 시나리오를 지원하기 위해 다음 지침을 확인하고 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-131">After we rename the network name of failover cluster we need to verify and perform the following instructions to enable all scenarios in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3b235-132">\*\* [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] :\*\* [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] Windows 클러스터 관리자 도구를 사용 하 여 장애 조치 (failover) 클러스터 인스턴스의 네트워크 이름을 변경한 후에는 이후 업그레이드 또는 제거 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-132">**[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:** After you change the network name of a [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] failover cluster instance using Windows Cluster Administrator tool, the future upgrade or uninstall operation might fail.</span></span> <span data-ttu-id="3b235-133">이 문제를 해결 하려면 [이](https://go.microsoft.com/fwlink/?LinkId=244002) 문서의 해결 방법 섹션에 있는 지침에 따라 **ClusterName** 레지스트리 항목을 업데이트 https://go.microsoft.com/fwlink/?LinkId=244002) 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-133">To resolve this issue update the **ClusterName** registry entry following the instructions in the resolution section of [this](https://go.microsoft.com/fwlink/?LinkId=244002) (https://go.microsoft.com/fwlink/?LinkId=244002).</span></span>  
  
 <span data-ttu-id="3b235-134">\*\* [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 서비스:\*\* 아래의 추가 작업 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 확인 하 고 수행 합니다. 에이전트 서비스:</span><span class="sxs-lookup"><span data-stu-id="3b235-134">**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Service:** Verify and perform the below additional actions for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Service:</span></span>  
  
-   <span data-ttu-id="3b235-135">SQL 에이전트가 이벤트를 전달하도록 구성된 경우 레지스트리 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-135">Fix the registry settings if SQL Agent is configured for event forwarding.</span></span> <span data-ttu-id="3b235-136">자세한 내용은 [이벤트 전달 서버 지정&#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b235-136">For more information, see [Designate an Events Forwarding Server &#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="3b235-137">컴퓨터/클러스터 네트워크 이름을 바꿀 때 마스터 서버(MSX) 및 대상 서버(TSX) 인스턴스 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-137">Fix the master server (MSX) and target servers (TSX) instance names when machines / cluster network name is renamed.</span></span> <span data-ttu-id="3b235-138">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b235-138">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="3b235-139">마스터 서버에서 여러 대상 서버 제거</span><span class="sxs-lookup"><span data-stu-id="3b235-139">Defect Multiple Target Servers from a Master Server</span></span>](../../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
    -   [<span data-ttu-id="3b235-140">다중 서버 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="3b235-140">Create a Multiserver Environment</span></span>](../../../ssms/agent/create-a-multiserver-environment.md)  
  
-   <span data-ttu-id="3b235-141">업데이트된 서버 이름을 사용하여 로그를 백업 및 복원할 수 있도록 로그 전달을 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-141">Reconfigure the Log Shipping so that updated server name is used to backup and restore logs.</span></span> <span data-ttu-id="3b235-142">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b235-142">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="3b235-143">로그 전달 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b235-143">Configure Log Shipping &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
    -   [<span data-ttu-id="3b235-144">로그 전달 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b235-144">Remove Log Shipping &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   <span data-ttu-id="3b235-145">서버 이름을 기반으로 하는 작업 단계를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="3b235-145">Update the Jobsteps that depend on server name.</span></span> <span data-ttu-id="3b235-146">자세한 내용은 [Manage Job Steps](../../../ssms/agent/manage-job-steps.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b235-146">For more information, see [Manage Job Steps](../../../ssms/agent/manage-job-steps.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b235-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b235-147">See Also</span></span>  
 [<span data-ttu-id="3b235-148">SQL Server의 독립 실행형 인스턴스를 호스팅하는 컴퓨터 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="3b235-148">Rename a Computer that Hosts a Stand-Alone Instance of SQL Server</span></span>](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)  
  
  
