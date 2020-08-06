---
title: Azure 복제본 추가 마법사 사용(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f7ee9e80f0511fe23aebb887b15b5e8b7e9cabf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728700"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a><span data-ttu-id="729ac-102">Azure 복제본 추가 마법사 사용(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="729ac-102">Use the Add Azure Replica Wizard (SQL Server)</span></span>
  <span data-ttu-id="729ac-103">Azure 복제본 추가 마법사를 사용 하 여 하이브리드 IT에서 새 Azure VM을 만들고 새로운 또는 기존 AlwaysOn 가용성 그룹에 대 한 보조 복제본으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-103">Use the Add Azure Replica Wizard to help you create a new Azure VM in hybrid IT and configure it as a secondary replica for a new or existing AlwaysOn availability group.</span></span>  
  
-   <span data-ttu-id="729ac-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="729ac-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="729ac-105">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="729ac-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="729ac-106">보안</span><span class="sxs-lookup"><span data-stu-id="729ac-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="729ac-107">**복제본을 추가하려면:**  [Azure 복제본 추가 마법사(SQL Server Management Studio)](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="729ac-107">**To add a replica, using:**  [Add Azure Replica Wizard (SQL Server Management Studio)](#SSMSProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="729ac-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="729ac-108">Before You Begin</span></span>  
 <span data-ttu-id="729ac-109">가용성 그룹에 가용성 복제본을 추가 하지 않은 경우 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;에 대 한 필수 조건, 제한 사항 및 권장 사항 ](prereqs-restrictions-recommendations-always-on-availability.md)에서 "서버 인스턴스" 및 "가용성 그룹 및 복제본" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="729ac-109">If you have never added any availability replica to an availability group, see the "Server instances" and "Availability groups and replicas" sections in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="729ac-110">필수 조건</span><span class="sxs-lookup"><span data-stu-id="729ac-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="729ac-111">현재 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-111">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="729ac-112">온-프레미스 서브넷에 Azure를 사용하는 사이트 간 VPN을 갖춘 하이브리드 IT 환경이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-112">You must have a hybrid-IT environment where your on-premise subnet has a site-to-site VPN with Azure.</span></span> <span data-ttu-id="729ac-113">자세한 내용은 [관리 포털에서 사이트 간 VPN 구성](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="729ac-113">For more information, see [Configure a Site-to-Site VPN in the Management Portal](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).</span></span>  
  
-   <span data-ttu-id="729ac-114">가용성 그룹은 온-프레미스 가용성 복제본을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-114">Your availability group must contain on-premise availability replicas.</span></span>  
  
-   <span data-ttu-id="729ac-115">가용성 그룹 수신기의 클라이언트는 가용성 그룹이 Azure 복제본으로 장애 조치될 때 수신기와 연결을 유지하려는 경우 인터넷에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-115">Clients to the availability group listener must have connectivity to the Internet if they want to maintain connectivity with the listener when the availability group is failed over to an Azure replica.</span></span>  
  
-   <span data-ttu-id="729ac-116">**전체 초기 데이터 동기화를 사용하기 위한 사전 요구 사항** 마법사에서 백업을 만들고 액세스하려면 네트워크 공유를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-116">**Prerequisites for using full initial data synchronization** You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="729ac-117">주 복제본의 경우 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 을 시작하는 데 사용되는 계정은 네트워크 공유에 대한 읽기 및 쓰기 파일 시스템 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-117">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="729ac-118">보조 복제본에 대한 계정은 네트워크 공유에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-118">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="729ac-119">마법사를 사용하여 전체 초기 데이터 동기화를 수행할 수 없는 경우에는 보조 데이터베이스를 수동으로 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-119">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="729ac-120">마법사를 실행하기 전이나 후에 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-120">You can do this before or after running the wizard.</span></span> <span data-ttu-id="729ac-121">자세한 내용은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-121">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="729ac-122">보안</span><span class="sxs-lookup"><span data-stu-id="729ac-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="729ac-123">권한</span><span class="sxs-lookup"><span data-stu-id="729ac-123">Permissions</span></span>  
 <span data-ttu-id="729ac-124">[Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="729ac-124">See [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)</span></span>  
  
##  <a name="using-the-add-azure-replica-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="729ac-125">Azure 복제본 추가 마법사 사용(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="729ac-125">Using the Add Azure Replica Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="729ac-126">[복제본 페이지 지정](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)에서 Azure 복제본 추가 마법사를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-126">The Add Azure Replica Wizard can be launched from the [Specify Replicas Page](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).</span></span> <span data-ttu-id="729ac-127">다음 두 가지 방법으로 이 페이지에 도달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-127">There are two ways to reach this page:</span></span>  
  
-   [<span data-ttu-id="729ac-128">가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="729ac-128">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="729ac-129">가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="729ac-129">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 <span data-ttu-id="729ac-130">Azure 복제본 추가 마법사를 시작한 후 아래 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-130">Once you have launched the Add Azure Replica Wizard, follow the steps below:</span></span>  
  
1.  <span data-ttu-id="729ac-131">먼저 Azure 구독의 관리 인증서를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-131">First, download a management certificate for your Azure subscription.</span></span> <span data-ttu-id="729ac-132">**다운로드** 를 클릭하여 로그인 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-132">Click **Download** to open the sign-in page.</span></span>  
  
2.  <span data-ttu-id="729ac-133">로그인 페이지에서 Azure 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-133">In the sign-in page, sign in to your Azure subscription.</span></span> <span data-ttu-id="729ac-134">로그인하면 마법사가 관리 인증서를 로컬 컴퓨터에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-134">Once you are signed in, the wizard installs a management certificate onto your local machine.</span></span> <span data-ttu-id="729ac-135">이 관리 인증서는 이 마법사를 다시 사용할 때 자동으로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-135">This management certificate is automatically loaded when you use this wizard again.</span></span> <span data-ttu-id="729ac-136">관리 인증서를 여러 개 다운로드한 경우 **...** 단추를 클릭하여 사용할 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-136">If you have downloaded multiple management certificates, you can click the **...** button to select the one you want to use.</span></span>  
  
3.  <span data-ttu-id="729ac-137">다음에는 **연결**을 클릭하여 구독에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-137">Next, connect to your subscription by clicking **Connect**.</span></span> <span data-ttu-id="729ac-138">연결되면 드롭다운 목록에 **가상 네트워크** 및 **가상 네트워크 서브넷**과 같은 Azure 매개 변수가 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-138">Once you are connected, the drop-down lists are populated with your Azure parameters, such as **Virtual Network** and **Virtual Network Subnet**.</span></span>  
  
4.  <span data-ttu-id="729ac-139">새 보조 복제본을 호스트할 Azure VM에 대한 설정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-139">Specify the settings for the Azure VM that will host the new secondary replica:</span></span>  
  
     <span data-ttu-id="729ac-140">이미지</span><span class="sxs-lookup"><span data-stu-id="729ac-140">Image</span></span>  
     <span data-ttu-id="729ac-141">Azure VM에 사용할 SQL Server 이미지의 이름</span><span class="sxs-lookup"><span data-stu-id="729ac-141">The name of the SQL Server image to use for the Azure VM</span></span>  
  
     <span data-ttu-id="729ac-142">VM 크기</span><span class="sxs-lookup"><span data-stu-id="729ac-142">VM Size</span></span>  
     <span data-ttu-id="729ac-143">Azure VM의 크기</span><span class="sxs-lookup"><span data-stu-id="729ac-143">The size of the Azure VM</span></span>  
  
     <span data-ttu-id="729ac-144">VM 이름</span><span class="sxs-lookup"><span data-stu-id="729ac-144">VM Name</span></span>  
     <span data-ttu-id="729ac-145">Azure VM의 DNS 이름</span><span class="sxs-lookup"><span data-stu-id="729ac-145">The DNS name of the Azure VM</span></span>  
  
     <span data-ttu-id="729ac-146">VM 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="729ac-146">VM Username</span></span>  
     <span data-ttu-id="729ac-147">Azure VM 기본 관리자의 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="729ac-147">The username of the default administrator for the Azure VM</span></span>  
  
     <span data-ttu-id="729ac-148">VM 관리자 암호(및 암호 확인)</span><span class="sxs-lookup"><span data-stu-id="729ac-148">VM Administrator Password (and Confirm Password)</span></span>  
     <span data-ttu-id="729ac-149">Azure VM 기본 관리자의 암호</span><span class="sxs-lookup"><span data-stu-id="729ac-149">The password for the default administrator for the Azure VM</span></span>  
  
     <span data-ttu-id="729ac-150">Virtual Network</span><span class="sxs-lookup"><span data-stu-id="729ac-150">Virtual Network</span></span>  
     <span data-ttu-id="729ac-151">Azure VM을 배치할 가상 네트워크</span><span class="sxs-lookup"><span data-stu-id="729ac-151">The virtual network in which to place the Azure VM</span></span>  
  
     <span data-ttu-id="729ac-152">가상 네트워크 서브넷</span><span class="sxs-lookup"><span data-stu-id="729ac-152">Virtual Network Subnet</span></span>  
     <span data-ttu-id="729ac-153">Azure VM을 배치할 가상 네트워크 서브넷</span><span class="sxs-lookup"><span data-stu-id="729ac-153">The virtual network subnet in which to place the Azure VM</span></span>  
  
     <span data-ttu-id="729ac-154">도메인</span><span class="sxs-lookup"><span data-stu-id="729ac-154">Domain</span></span>  
     <span data-ttu-id="729ac-155">Azure VM을 조인할 Active Directory(AD) 도메인</span><span class="sxs-lookup"><span data-stu-id="729ac-155">The Active Directory (AD) domain to join the Azure VM</span></span>  
  
     <span data-ttu-id="729ac-156">도메인 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="729ac-156">Domain Username</span></span>  
     <span data-ttu-id="729ac-157">Azure VM을 도메인에 조인하는 데 사용되는 AD 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="729ac-157">The AD username used to join the Azure VM to the domain</span></span>  
  
     <span data-ttu-id="729ac-158">암호</span><span class="sxs-lookup"><span data-stu-id="729ac-158">Password</span></span>  
     <span data-ttu-id="729ac-159">Azure VM을 도메인에 조인하는 데 사용되는 암호</span><span class="sxs-lookup"><span data-stu-id="729ac-159">The password used to join the Azure VM to the domain</span></span>  
  
5.  <span data-ttu-id="729ac-160">**확인** 을 클릭하여 설정을 커밋하고 Azure 복제본 추가 마법사를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-160">Click **OK** to commit your settings and exit the Add Azure Replica Wizard.</span></span>  
  
6.  <span data-ttu-id="729ac-161">새 복제본에 대해 수행하는 것과 같은 방법으로 [복제본 지정 페이지](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) 의 나머지 구성 단계를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-161">Continue with the rest of the configuration steps for [Specify Replicas Page](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) as you do for any new replica.</span></span>  
  
     <span data-ttu-id="729ac-162">가용성 그룹 마법사 또는 가용성 그룹에 복제본 추가 마법사를 마치면 구성 프로세스에서 Azure의 모든 작업을 수행 하 여 새 VM을 만들고, AD 도메인에 연결 하 고, Windows 클러스터에 추가 하 고, AlwaysOn 고가용성을 사용 하도록 설정 하 고, 가용성 그룹에 새 복제본을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="729ac-162">Once you are finished with the Availability Group Wizard or the Add Replica to Availability Group Wizard, the configuration process performs all operations in Azure to create the new VM, join it to the AD domain, add it to the Windows cluster, enable AlwaysOn High Availability, and add the new replica to the availability group.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="729ac-163">관련 작업</span><span class="sxs-lookup"><span data-stu-id="729ac-163">Related Tasks</span></span>  
  
-   [<span data-ttu-id="729ac-164">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="729ac-164">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="729ac-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="729ac-165">See Also</span></span>  
 <span data-ttu-id="729ac-166">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="729ac-166">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="729ac-167">[AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="729ac-167">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 [<span data-ttu-id="729ac-168">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="729ac-168">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
