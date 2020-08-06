---
title: 장애 조치(Failover) 클러스터에서 FILESTREAM 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 29541bbcfd323a85a3fa751f60904fd1a26e1199
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728363"
---
# <a name="set-up-filestream-on-a-failover-cluster"></a><span data-ttu-id="06797-102">장애 조치(Failover) 클러스터에서 FILESTREAM 설정</span><span class="sxs-lookup"><span data-stu-id="06797-102">Set Up FILESTREAM on a Failover Cluster</span></span>
  <span data-ttu-id="06797-103">이 항목에서는 장애 조치(Failover) 클러스터에서 FILESTREAM을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-103">This topic describes how to enable FILESTREAM on a failover cluster.</span></span> <span data-ttu-id="06797-104">이 절차를 시도하기 전에 [장애 조치(Failover) 클러스터링](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) 을 이해하고 FILESTREAM을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-104">Before you try this procedure, you should understand [failover clustering](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) and have FILESTREAM enabled.</span></span> <span data-ttu-id="06797-105">FILESTREAM을 사용하도록 설정하는 방법은 [FILESTREAM 사용 및 구성](enable-and-configure-filestream.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="06797-105">For information about how to enable FILESTREAM, see [Enable and Configure FILESTREAM](enable-and-configure-filestream.md).</span></span>  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a><span data-ttu-id="06797-106">장애 조치 클러스터에서 FILESTREAM을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="06797-106">To set up FILESTREAM on a failover cluster</span></span>  
  
1.  <span data-ttu-id="06797-107">장애 조치 클러스터의 주 노드를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-107">Set up the primary node for the failover cluster.</span></span>  
  
     <span data-ttu-id="06797-108">설정을 마치면 **SQL Server 구성 관리자**를 사용하여 주 노드에서 FILESTREAM을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-108">After the setup finishes, enable FILESTREAM on the primary node by using **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="06797-109">이렇게 하면 Windows 관리자 권한이 필요한 설정이 가능해집니다.</span><span class="sxs-lookup"><span data-stu-id="06797-109">This enables the settings that require Windows Admin privileges.</span></span> <span data-ttu-id="06797-110">원격 액세스가 필요한 경우 **원격 클라이언트가 FILESTREAM 데이터에 대한 스트리밍 액세스를 가질 수 있도록 허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-110">If remote access is required, select **Allow remote clients to have streaming access to FILESTREAM data**.</span></span> <span data-ttu-id="06797-111">이렇게 하면 파일 공유 클러스터 리소스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="06797-111">This will create a file-share cluster resource.</span></span>  
  
2.  <span data-ttu-id="06797-112">수동 노드를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-112">Set up a passive node.</span></span>  
  
     <span data-ttu-id="06797-113">설정을 마치면 **SQL Server 구성 관리자**를 사용하여 수동 노드에서 FILESTREAM을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-113">After the setup finishes, enable FILESTREAM on the passive node by using **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="06797-114">**Windows 공유 이름** 에 지정하는 이름은 클러스터의 모든 노드에서 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-114">The name that you specify for **Windows Share Name** must be the same across all nodes in the cluster.</span></span>  
  
3.  <span data-ttu-id="06797-115">수동 노드를 더 추가하려면 2단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-115">To add more passive nodes, repeat step 2.</span></span>  
  
4.  <span data-ttu-id="06797-116">노드가 모두 추가되면 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 sp_configure 저장 프로시저를 실행하여 프로세스를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-116">After all the nodes are added, complete the process by executing the sp_configure stored procedure on each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="06797-117">클러스터에서 노드를 더 추가하고 사용하도록 설정하려면 언제든지 2, 3 및 4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="06797-117">To add and enable additional nodes to the cluster at any time, you can repeat steps 2, 3, and 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06797-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06797-118">See Also</span></span>  
 <span data-ttu-id="06797-119">[서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="06797-119">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="06797-120">[새 SQL Server 장애 조치(failover) 클러스터 만들기&#40;설치 프로그램&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) </span><span class="sxs-lookup"><span data-stu-id="06797-120">[Create a New SQL Server Failover Cluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) </span></span>  
 <span data-ttu-id="06797-121">[SQL Server 장애 조치(failover) 클러스터 인스턴스 제거&#40;설치 프로그램&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md) </span><span class="sxs-lookup"><span data-stu-id="06797-121">[Remove a SQL Server Failover Cluster Instance &#40;Setup&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md) </span></span>  
 [<span data-ttu-id="06797-122">SQL Server 장애 조치(Failover) 클러스터에서 노드 추가 또는 제거&#40;설치&#41;</span><span class="sxs-lookup"><span data-stu-id="06797-122">Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;</span></span>](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
