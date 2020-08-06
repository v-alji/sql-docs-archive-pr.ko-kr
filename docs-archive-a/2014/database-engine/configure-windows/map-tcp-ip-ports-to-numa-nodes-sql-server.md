---
title: NUMA 노드에 TCP IP 포트 매핑(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- memory [SQL Server], NUMA
- affinity NUMA
- ports [SQL Server], working with NUMA
- CPU [SQL Server], NUMA support
- NUMA, How to map a port to a NUMA node
- NUMA affinity
- TCP/IP [SQL Server], NUMA support
- non-uniform memory access
ms.assetid: 07727642-0266-4cbc-8c55-3c367e4458ca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf4a1bd7e02719d3884011ad3faa20a1ccc6466a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728692"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a><span data-ttu-id="ba3e7-102">NUMA 노드에 TCP IP 포트 매핑(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ba3e7-102">Map TCP IP Ports to NUMA Nodes (SQL Server)</span></span>
  <span data-ttu-id="ba3e7-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 TCP/IP 포트를 NUMA(Non-Uniform Memory Access) 노드로 매핑하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-103">This topic describes how to map TCP/IP ports to non-uniform memory access (NUMA) nodes by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="ba3e7-104">시작할 때 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 오류 로그에 노드 정보를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-104">On startup, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] writes the node information to the error log.</span></span>  
  
 <span data-ttu-id="ba3e7-105">사용할 노드의 번호를 확인하려면 오류 로그나 **sys.dm_os_schedulers** 뷰의 노드 정보를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-105">To determine the node number of the node you want to use, either read the node information from the error log, or from the **sys.dm_os_schedulers** view.</span></span> <span data-ttu-id="ba3e7-106">한 개 또는 여러 개의 노드에 TCP/IP 주소와 포트를 설정하려면 포트 번호 뒤에서 괄호 안에 노드 확인 비트맵(선호도 마스크)을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-106">To set a TCP/IP address and port to single or multiple nodes, append a node identification bitmap (an affinity mask) in brackets after the port number.</span></span> <span data-ttu-id="ba3e7-107">십진수나 16진수 형식으로 노드를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-107">Nodes can be specified in either decimal or hexadecimal format.</span></span> <span data-ttu-id="ba3e7-108">비트맵을 만들려면 먼저 76543210처럼 0부터 시작하여 오른쪽에서 왼쪽으로 노드 번호를 매깁니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-108">To create the bitmap, first number the nodes from right to left starting with zero, as in 76543210.</span></span> <span data-ttu-id="ba3e7-109">사용할 노드에 1을 지정하고 사용하지 않을 노드에 0을 지정하여 노드 목록의 이진 표현을 만드세요.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-109">Create a binary representation of the node list, providing 1 for nodes you want to use, and 0 for nodes you do not want to use.</span></span> <span data-ttu-id="ba3e7-110">예를 들어 NUMA 노드 0, 2, 5를 사용하려면 00100101을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-110">For example, to use NUMA nodes 0, 2, and 5, specify 00100101.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ba3e7-111">NUMA 노드 번호</span><span class="sxs-lookup"><span data-stu-id="ba3e7-111">NUMA node number</span></span>|<span data-ttu-id="ba3e7-112">76543210</span><span class="sxs-lookup"><span data-stu-id="ba3e7-112">76543210</span></span>|  
|<span data-ttu-id="ba3e7-113">오른쪽에서부터 0, 2, 5 숫자에 마스크 설정</span><span class="sxs-lookup"><span data-stu-id="ba3e7-113">Mask for 0, 2, and 5 counting from right</span></span>|<span data-ttu-id="ba3e7-114">00100101</span><span class="sxs-lookup"><span data-stu-id="ba3e7-114">00100101</span></span>|  
  
 <span data-ttu-id="ba3e7-115">이진 표현(00100101)을 십진수 `[37]`또는 16진수 `[0x25]`로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-115">Convert the binary representation (00100101), into decimal `[37]`, or hexadecimal `[0x25]`.</span></span> <span data-ttu-id="ba3e7-116">모든 노드에서 수신하려면 노드 식별자를 제공하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-116">To listen on all nodes, provide no node identifier.</span></span>  
  
 <span data-ttu-id="ba3e7-117">포트가 둘 이상의 NUMA 노드에 매핑되어 있으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 노드에서 로드 균형을 조정하지 않고 라운드 로빈 방식으로 노드에 연결을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-117">If a port is mapped to more than one NUMA node, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns connections to nodes in a round-robin fashion without attempting to balance load across the nodes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba3e7-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 각 IP 주소에 대해 여러 TCP 포트에서 수신할 수 있게 하려면 [여러 TCP 포트에서 수신하도록 데이터베이스 엔진 구성](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-118">To enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on multiple TCP ports for each IP address, see [Configure the Database Engine to Listen on Multiple TCP Ports](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ba3e7-119">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="ba3e7-119">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a><span data-ttu-id="ba3e7-120">NUMA 노드에 TCP/IP 포트를 매핑하려면</span><span class="sxs-lookup"><span data-stu-id="ba3e7-120">To map a TCP/IP port to a NUMA node</span></span>  
  
1.  <span data-ttu-id="ba3e7-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 **SQL Server 네트워크 구성**을 확장한 다음 *\<instance name>* 에 대한 **프로토콜**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-121">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Network Configuration**, and then click **Protocols for** *\<instance name>*.</span></span>  
  
2.  <span data-ttu-id="ba3e7-122">세부 정보 창에서 **TCP/IP**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-122">In the details pane, double-click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="ba3e7-123">**IP 주소** 탭을 선택하여 구성할 IP 주소에 해당하는 섹션의 **TCP 포트** 입력란에서 포트 번호 뒤에 NUMA 노드 식별자를 대괄호 안에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-123">On the **IP Addresses** tab, in the section corresponding to the IP address to configure, in the **TCP Port** box, add the NUMA node identifier in brackets after the port number.</span></span> <span data-ttu-id="ba3e7-124">예를 들어 TCP 포트 1500과 노드 0, 2, 5의 경우 `1500[37]` 또는 `1500[0x25]`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ba3e7-124">For example, for TCP port 1500 and nodes 0, 2, and 5, use `1500[37]`, or `1500[0x25]`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba3e7-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba3e7-125">See Also</span></span>  
 [<span data-ttu-id="ba3e7-126">소프트 NUMA &#40;SQL Server를 사용 하도록 SQL Server 구성&#41;</span><span class="sxs-lookup"><span data-stu-id="ba3e7-126">Configure SQL Server to Use Soft-NUMA &#40;SQL Server&#41;</span></span>](soft-numa-sql-server.md)  
  
  
