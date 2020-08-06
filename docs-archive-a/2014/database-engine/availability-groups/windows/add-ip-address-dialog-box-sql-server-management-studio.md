---
title: IP 주소 추가 대화 상자(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistener.addipaddress.f1
ms.assetid: 98c9ad3b-ff3c-4c1d-b344-59a72fca137c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5192e6414b34bee6de09d45a7284f25404235dc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647255"
---
# <a name="add-ip-address-dialog-box-sql-server-management-studio"></a><span data-ttu-id="900fe-102">IP 주소 추가 대화 상자(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="900fe-102">Add IP Address Dialog Box (SQL Server Management Studio)</span></span>
  <span data-ttu-id="900fe-103"> 이 F1 도움말 항목에서는 **IP 주소 추가** 대화 상자의 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-103">This F1 help topic describes the options of the **Add IP Address** dialog box.</span></span> <span data-ttu-id="900fe-104">이 대화 상자는 **새 가용성 그룹 수신기** 대화 상자 및 **의** 또는 **의** 복제본 선택 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 페이지에 있는 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] 수신기 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]탭에서 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-104">This dialog box accessed from the **New Availability Group Listener** dialog box and the **Listener** tab of the **Specify Replicas** page of the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="900fe-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="900fe-105">Prerequisites</span></span>  
 <span data-ttu-id="900fe-106">가용성 그룹 수신기에 서브넷을 추가하려면 각 서브넷의 IP 주소와 IPv4 주소의 서브넷 마스크를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-106">Before you begin to add subnets to an availability group listener, ensure that know the IP address for each subnet and, for an IPv4 address, the subnet mask.</span></span>  
  
##  <a name="add-ip-address-options"></a><a name="PageOptions"></a> <span data-ttu-id="900fe-107">IP 주소 추가 옵션</span><span class="sxs-lookup"><span data-stu-id="900fe-107">Add IP Address Options</span></span>  
 <span data-ttu-id="900fe-108">**서브넷**</span><span class="sxs-lookup"><span data-stu-id="900fe-108">**Subnet**</span></span>  
 <span data-ttu-id="900fe-109">이 드롭 목록을 사용하여 가용성 그룹 수신기에 추가할 서브넷 주소를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-109">Use the drop list to select an address for the subnet that you are adding to the availability group listener.</span></span> <span data-ttu-id="900fe-110">기본적으로 서브넷은 IPv4 주소와 IPv6 주소를 모두 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-110">By default a subnet possesses both an IPv4 address and an IPv6 address.</span></span> <span data-ttu-id="900fe-111">**IP 주소 추가** 대화 상자를 처음 사용하는 경우 **서브넷** 드롭 목록에 가용성 그룹의 복제본을 호스팅하는 각 서브넷에 대한 두 서브넷 주소가 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-111">The first time you use the **Add IP Address** dialog,  the **Subnet** drop list displays both subnet addresses for each subnet that hosts a replica for the availability group.</span></span> <span data-ttu-id="900fe-112">지정된 서브넷을 수신기에 추가하려면 서브넷 주소 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-112">To add a given subnet to the listener, select one of its subnet addresses.</span></span>  
  
 <span data-ttu-id="900fe-113">**IP 주소 추가** 대화 상자를 완료한 후 **확인** 을 클릭하여 선택한 서브넷 주소를 수신기에 추가하면 **서브넷** 드롭 목록에서 해당 서브넷 주소가 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-113">After you complete the **Add IP Address** dialog box and click **OK** to add a selected subnet address to the listener, the **Subnet** drop list filters out that subnet address.</span></span> <span data-ttu-id="900fe-114">선택하지 않은 서브넷 주소는 모두 드롭 목록에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-114">All unselected subnet addresses remain on the drop list.</span></span> <span data-ttu-id="900fe-115">서브넷당 하나의 서브넷 주소만 수신기에 추가해야 합니다. 그렇지 않으면 수신기를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-115">Be sure that you add one and only one subnet address per subnet to the listener, or listener creation will fail.</span></span>  
  
 <span data-ttu-id="900fe-116">**주소**</span><span class="sxs-lookup"><span data-stu-id="900fe-116">**Addresses**</span></span>  
 <span data-ttu-id="900fe-117">이 필드를 사용하여 선택한 서브넷 주소에 대한 고정 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-117">Use this field to enter a static IP address for the selected subnet address.</span></span> <span data-ttu-id="900fe-118">이 IP 주소는 네트워크 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="900fe-118">Contact your network administrator for this IP address.</span></span> <span data-ttu-id="900fe-119">선택한 서브넷 주소에 대한 올바른 주소를 입력해야 합니다. 그렇지 않으면 수신기를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-119">Ensure that you enter a valid address for the selected subnet address, or listener creation will fail.</span></span>  
  
 <span data-ttu-id="900fe-120">**IPv4 주소**</span><span class="sxs-lookup"><span data-stu-id="900fe-120">**IPv4 Address**</span></span>  
 <span data-ttu-id="900fe-121">서브넷의 IPv4 서브넷 주소를 선택한 경우 올바른 IPv4 정적 주소를 여기에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-121">If you selected the IPv4 subnet address of a subnet, enter a valid IPv4 static address here.</span></span>  
  
 <span data-ttu-id="900fe-122">**서브넷 마스크**</span><span class="sxs-lookup"><span data-stu-id="900fe-122">**Subnet Mask**</span></span>  
 <span data-ttu-id="900fe-123">IPv4 주소의 경우 이 읽기 전용 필드에 선택한 서브넷의 서브넷 마스크가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-123">For an IPv4 address, this read-only field displays the subnet mask of the selected subnet.</span></span>  
  
 <span data-ttu-id="900fe-124">**IPv6 주소**</span><span class="sxs-lookup"><span data-stu-id="900fe-124">**IPv6 Address**</span></span>  
 <span data-ttu-id="900fe-125">서브넷의 IPv6 서브넷 주소를 선택한 경우 올바른 IPv6 정적 주소를 여기에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-125">If you selected the IPv6 subnet address of a subnet, enter a valid IPv6 static address here.</span></span>  
  
 <span data-ttu-id="900fe-126">**확인**</span><span class="sxs-lookup"><span data-stu-id="900fe-126">**OK**</span></span>  
 <span data-ttu-id="900fe-127">지정한 고정 IP 주소와 함께 선택한 주소의 서브넷을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-127">Click to create add the subnet whose address you selected, along with the static IP address that you specified.</span></span> <span data-ttu-id="900fe-128">이러한 값을 포함하는 행이 **새 가용성 그룹 수신기** 또는 **복제본 선택** 대화 상자의 서브넷 표에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-128">A row containing these values will be added to the subnet grid of the **New Availability Group Listener** or **Specify Replicas** dialog box.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="900fe-129">**IP 주소 추가** 대화 상자에는 IP 주소가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-129">The **Add IP Address** dialog does not verify the IP address.</span></span> <span data-ttu-id="900fe-130">또한 가용성 그룹 수신기에 이미 추가한 서브넷에 대한 두 번째 서브넷 주소를 이 대화 상자에서 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-130">Also the dialog does not prevent you from adding the second subnet address for a subnet that you have already added to the availability group listener.</span></span>  
  
 <span data-ttu-id="900fe-131">**취소**</span><span class="sxs-lookup"><span data-stu-id="900fe-131">**Cancel**</span></span>  
 <span data-ttu-id="900fe-132">선택을 취소하고 서브넷에 대한 고정 IP 주소를 추가하지 않고 **새 가용성 그룹 수신기** 대화 상자 또는 **수신기** 탭으로 돌아가려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="900fe-132">Click to cancel your selections, and return to the **New Availability Group Listener** dialog box or **Listener** tab without adding a static IP address for any subnet.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="900fe-133">관련 작업</span><span class="sxs-lookup"><span data-stu-id="900fe-133">Related Tasks</span></span>  
  
-   [<span data-ttu-id="900fe-134">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="900fe-134">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="900fe-135">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="900fe-135">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="900fe-136">가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="900fe-136">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="900fe-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="900fe-137">See Also</span></span>  
 <span data-ttu-id="900fe-138">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="900fe-138">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="900fe-139">[가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="900fe-139">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="900fe-140">AlwaysOn 클라이언트 연결(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="900fe-140">AlwaysOn Client Connectivity (SQL Server)</span></span>](always-on-client-connectivity-sql-server.md)  
  
  
