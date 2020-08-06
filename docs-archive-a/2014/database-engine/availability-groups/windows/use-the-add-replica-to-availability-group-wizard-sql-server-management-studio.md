---
title: 가용성 그룹에 복제본 추가 마법사 사용(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], wizards
ms.assetid: 60d962b6-2af4-4394-9190-61939a102bc0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4d75372cd2388e88fcb3d3ce95975bdefa54c5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648592"
---
# <a name="use-the-add-replica-to-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="e4cef-102">가용성 그룹에 복제본 추가 마법사 사용(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e4cef-102">Use the Add Replica to Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e4cef-103">복제본을 가용성 그룹에 추가 마법사를 사용하여 기존 AlwaysOn 가용성 그룹에 새 보조 복제본을 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-103">Use the Add Replica to Availability Group Wizard to help you a add new secondary replica to an existing AlwaysOn availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4cef-104">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 PowerShell을 사용하여 가용성 그룹에 보조 복제본을 추가하는 방법은 [가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-104">For information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to add a secondary replica to an availability group, see [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e4cef-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e4cef-105">Before You Begin</span></span>  
 <span data-ttu-id="e4cef-106">가용성 그룹에 가용성 복제본을 추가 하지 않은 경우 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;에 대 한 필수 조건, 제한 사항 및 권장 사항 ](prereqs-restrictions-recommendations-always-on-availability.md)에서 "서버 인스턴스" 및 "가용성 그룹 및 복제본" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-106">If you have never added any availability replica to an availability group, see the "Server instances" and "Availability groups and replicas" sections in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="e4cef-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="e4cef-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="e4cef-108">현재 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-108">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="e4cef-109">보조 복제본을 추가하기 전에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 호스트 인스턴스가 기존 복제본과 동일한 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터 내의 다른 클러스터 노드에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-109">Before adding a secondary replica, verify that the host instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is in the same Windows Server Failover Clustering (WSFC) cluster as the existing replicas but resides on a different cluster node.</span></span> <span data-ttu-id="e4cef-110">또한 이 서버 인스턴스가 다른 모든 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 사전 요구 사항과 일치하는지도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-110">Also, verify that this server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="e4cef-111">자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-111">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="e4cef-112">가용성 복제본을 호스팅하도록 선택한 서버 인스턴스가 도메인 사용자 계정으로 실행되고 있고 아직 데이터베이스 미러링 엔드포인트를 가지고 있지 않은 경우, 마법사가 엔드포인트를 만들고 서버 인스턴스 서비스 계정에 CONNECT 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-112">If a server instance that you select to host an availability replica is running under a domain user account and does not yet have a database mirroring endpoint, the wizard can create the endpoint and grant CONNECT permission to the server instance service account.</span></span> <span data-ttu-id="e4cef-113">그러나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스가 로컬 시스템, 로컬 서비스 또는 네트워크 서비스와 같은 기본 제공 계정이나 비도메인 계정으로 실행 중인 경우에는 사용자가 엔드포인트 인증을 위한 인증서를 사용해야 하며 마법사를 통해 서버 인스턴스에 대한 데이터베이스 미러링 엔드포인트를 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-113">However, if the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running as a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication, and the wizard will be unable to create a database mirroring endpoint on the server instance.</span></span> <span data-ttu-id="e4cef-114">이 경우 가용성 그룹에 복제본 추가 마법사를 시작하기 전에 데이터 미러링 엔드포인트를 수동으로 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-114">In this case, we recommend that you create the database mirroring endpoints manually before you launch the Add Replica to Availability Group Wizard.</span></span>  
  
     `To use certificates for a database mirroring endpoint:`  
  
     [<span data-ttu-id="e4cef-115">CREATE ENDPOINT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e4cef-115">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
     [<span data-ttu-id="e4cef-116">데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e4cef-116">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   <span data-ttu-id="e4cef-117">**전체 초기 데이터 동기화를 사용하기 위한 사전 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="e4cef-117">**Prerequisites for using full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="e4cef-118">모든 데이터베이스 파일 경로는 가용성 그룹에 대한 복제본을 호스팅하는 모든 서버 인스턴스에서 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-118">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="e4cef-119">보조 복제본을 호스팅하는 서버 인스턴스에 주 데이터베이스 이름이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-119">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="e4cef-120">즉, 새 보조 데이터베이스가 아직 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-120">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="e4cef-121">마법사에서 백업을 만들고 액세스하려면 네트워크 공유를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-121">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="e4cef-122">주 복제본의 경우 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 을 시작하는 데 사용되는 계정은 네트워크 공유에 대한 읽기 및 쓰기 파일 시스템 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-122">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="e4cef-123">보조 복제본에 대한 계정은 네트워크 공유에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-123">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="e4cef-124">마법사를 사용하여 전체 초기 데이터 동기화를 수행할 수 없는 경우에는 보조 데이터베이스를 수동으로 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-124">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="e4cef-125">마법사를 실행하기 전이나 후에 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-125">You can do this before or after running the wizard.</span></span> <span data-ttu-id="e4cef-126">자세한 내용은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-126">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e4cef-127">보안</span><span class="sxs-lookup"><span data-stu-id="e4cef-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e4cef-128">권한</span><span class="sxs-lookup"><span data-stu-id="e4cef-128">Permissions</span></span>  
 <span data-ttu-id="e4cef-129">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-129">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="e4cef-130">가용성 그룹에 복제본 추가 마법사에서 데이터베이스 미러링 엔드포인트를 관리할 수 있도록 하려면 CONTROL ON ENDPOINT 권한도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-130">Also requires CONTROL ON ENDPOINT permission if you want to allow Add Replica to Availability Group Wizard to manage the database mirroring endpoint.</span></span>  
  

  
##  <a name="using-the-add-replica-to-availability-group-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e4cef-131">복제본을 가용성 그룹에 추가 마법사 사용(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e4cef-131">Using the Add Replica to Availability Group Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="e4cef-132">**복제본을 가용성 그룹에 추가 마법사를 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="e4cef-132">**To Use the Add Replica to Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="e4cef-133">개체 탐색기에서 가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-133">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="e4cef-134">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-134">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="e4cef-135">보조 복제본을 추가할 가용성 그룹을 마우스 오른쪽 단추로 클릭하고 **복제본 추가** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-135">Right-click the availability group to which you are adding a secondary replica, and select the **Add Replica** command.</span></span> <span data-ttu-id="e4cef-136">그러면 복제본을 가용성 그룹에 추가 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-136">This launches the Add Replica to Availability Group Wizard.</span></span>  
  
4.  <span data-ttu-id="e4cef-137">**기존 보조 복제본에 연결** 페이지에서 가용성 그룹의 모든 보조 복제본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-137">On the **Connect to Existing Secondary Replicas** page, connect to every secondary replica in the availability group.</span></span> <span data-ttu-id="e4cef-138">자세한 내용은 [기존 보조 복제본에 연결 페이지 &#40;복제본 추가 마법사 및 데이터베이스 추가 마법사&#41;](connect-to-existing-secondary-replicas-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-138">For more information, see [Connect to Existing Secondary Replicas Page &#40;Add Replica Wizard and Add Databases Wizard&#41;](connect-to-existing-secondary-replicas-page.md).</span></span>  
  
5.  <span data-ttu-id="e4cef-139">**복제본 선택** 페이지에서 가용성 그룹에 대해 하나 이상의 새 보조 복제본을 지정하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-139">On the **Specify Replicas** page, specify and configure one or more new secondary replicas for the availability group.</span></span> <span data-ttu-id="e4cef-140">이 페이지에는 세 개의 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-140">This page contains three tabs.</span></span> <span data-ttu-id="e4cef-141">다음 표에서는 이러한 탭을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-141">The following table introduces these tabs.</span></span> <span data-ttu-id="e4cef-142">자세한 내용은 [복제본 페이지 지정&#40;새 가용성 그룹 마법사: 복제본 추가 마법사&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-142">For more information, see [Specify Replicas Page &#40;New Availability Group Wizard: Add Replica Wizard&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).</span></span>  
  
    |<span data-ttu-id="e4cef-143">탭</span><span class="sxs-lookup"><span data-stu-id="e4cef-143">Tab</span></span>|<span data-ttu-id="e4cef-144">간략한 설명</span><span class="sxs-lookup"><span data-stu-id="e4cef-144">Brief Description</span></span>|  
    |---------|-----------------------|  
    |<span data-ttu-id="e4cef-145">**복제본**</span><span class="sxs-lookup"><span data-stu-id="e4cef-145">**Replicas**</span></span>|<span data-ttu-id="e4cef-146">이 탭에서는 새 보조 복제본을 호스팅할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 각 인스턴스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-146">Use this tab to specify each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host a new secondary replica.</span></span>|  
    |<span data-ttu-id="e4cef-147">**엔드포인트**</span><span class="sxs-lookup"><span data-stu-id="e4cef-147">**Endpoints**</span></span>|<span data-ttu-id="e4cef-148">이 탭에서는 각 새 보조 복제본에 대한 기존 데이터베이스 미러링 엔드포인트(있는 경우)를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-148">Use this tab to verify the existing database mirroring endpoint, if any, for each new secondary replica.</span></span> <span data-ttu-id="e4cef-149">이 엔드포인트가 서버 계정에서 Windows 인증을 사용하는 서버 인스턴스에 없는 경우 마법사가 엔드포인트를 자동으로 만들도록 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-149">If this endpoint is lacking on a server instance whose service accounts use Windows Authentication, the wizard will attempt to create the endpoint automatically.</span></span> <span data-ttu-id="e4cef-150">**참고:**  서버 인스턴스가 도메인 사용자 계정이 아닌 계정으로 실행 중인 경우 마법사를 계속 하려면 먼저 서버 인스턴스를 수동으로 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-150">**Note:**  If any server instance is running under a non-domain user account, you need to do make a manual change to your server instance before you can proceed in the wizard.</span></span> <span data-ttu-id="e4cef-151">자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소](#Prerequisites)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-151">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>|  
    |<span data-ttu-id="e4cef-152">**백업 기본 설정**</span><span class="sxs-lookup"><span data-stu-id="e4cef-152">**Backup Preferences**</span></span>|<span data-ttu-id="e4cef-153">이 탭에서는 현재 설정을 수정하려는 경우 가용성 그룹 전체에 대한 백업 기본 설정을 지정하고 개별 가용성 복제본에 대한 백업 우선 순위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-153">Use this tab to specify your backup preference for the availability group as a whole, if you wish to modify the current setting, and to specify your backup priorities for the individual availability replicas.</span></span>|  
  
6.  <span data-ttu-id="e4cef-154">**초기 데이터 동기화 선택** 페이지에서 새 보조 복제본을 만들고 가용성 그룹에 조인할 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-154">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="e4cef-155">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-155">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="e4cef-156">**전체**</span><span class="sxs-lookup"><span data-stu-id="e4cef-156">**Full**</span></span>  
  
         <span data-ttu-id="e4cef-157">현재 환경이 초기 데이터 동기화 자동 시작을 위한 요구 사항을 충족하는 경우에 이 옵션을 선택합니다. 자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소, 제한 사항 및 권장 사항](#Prerequisites)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-157">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#Prerequisites), earlier in this topic).</span></span>  
  
         <span data-ttu-id="e4cef-158">**전체**를 선택한 후 가용성 그룹을 만들면 마법사에서 모든 주 데이터베이스와 해당 트랜잭션 로그를 네트워크 공유에 백업하고 새 보조 복제본을 호스팅하는 모든 서버 인스턴스에서 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-158">If you select **Full**, after creating the availability group, the wizard will back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts a new secondary replica.</span></span> <span data-ttu-id="e4cef-159">그런 다음 모든 새 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-159">The wizard will then join every new secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="e4cef-160">**모든 복제본에서 액세스할 수 있는 공유 네트워크 위치 지정:** 필드에서 복제본을 호스팅하는 모든 서버 인스턴스에 읽기/쓰기 액세스 권한이 있는 백업 공유를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-160">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="e4cef-161">로그 백업이 로그 백업 체인의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-161">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="e4cef-162">로그 백업 파일을 적절히 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-162">Store the log backup files appropriately.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="e4cef-163">필요한 파일 시스템 권한에 대한 자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소](#Prerequisites)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-163">For information about the required file-system permissions, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="e4cef-164">**조인만**</span><span class="sxs-lookup"><span data-stu-id="e4cef-164">**Join only**</span></span>  
  
         <span data-ttu-id="e4cef-165">새 보조 복제본을 호스팅할 서버 인스턴스에서 보조 데이터베이스를 수동으로 준비하는 경우 이 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-165">If you have manually prepared secondary databases on the server instances that will host the new secondary replicas, you can select this option.</span></span> <span data-ttu-id="e4cef-166">마법사에서 이러한 새 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-166">The wizard will join these new secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="e4cef-167">**초기 데이터 동기화 건너뛰기**</span><span class="sxs-lookup"><span data-stu-id="e4cef-167">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="e4cef-168">주 데이터베이스의 로그 백업과 사용자 데이터베이스를 사용하려는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-168">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="e4cef-169">자세한 내용은 [AlwaysOn 보조 데이터베이스에서 데이터 이동 시작&#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-169">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
7.  <span data-ttu-id="e4cef-170">**유효성 검사** 페이지에서는 이 마법사에서 지정한 값이 가용성 그룹에 복제본 추가 마법사의 요구 사항을 충족하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-170">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the Add Replica to Availability Group Wizard.</span></span> <span data-ttu-id="e4cef-171">변경하려면 **이전** 을 클릭하여 이전 마법사 페이지로 돌아가서 하나 이상의 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-171">To make a change, click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="e4cef-172">**다음** 을 클릭하여 **유효성 검사** 페이지로 돌아가서 **유효성 검사 다시 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-172">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
8.  <span data-ttu-id="e4cef-173">**요약** 페이지에서 새 가용성 그룹에 대한 선택 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-173">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="e4cef-174">변경하려면 **이전** 을 클릭하여 관련 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-174">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="e4cef-175">변경 후에는 **다음** 을 클릭하여 **요약** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-175">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
     <span data-ttu-id="e4cef-176">선택이 완료되었으면 필요에 따라 스크립트를 클릭하여 마법사에서 실행할 단계에 대한 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-176">If you are satisfied with your selections, optionally click Script to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="e4cef-177">새 가용성 그룹을 만들어 구성하려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-177">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
9. <span data-ttu-id="e4cef-178">**진행률** 페이지에 가용성 그룹을 만들기 위한 단계(엔드포인트 구성, 가용성 그룹 만들기 및 가용성 그룹에 보조 복제본 조인)의 진행 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-178">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
10. <span data-ttu-id="e4cef-179">이러한 단계가 완료되면 **결과** 페이지에 각 단계의 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-179">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="e4cef-180">단계가 모두 성공하면 새 가용성 그룹이 완전히 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-180">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="e4cef-181">단계에서 오류가 발생한 경우 구성을 수동으로 완료해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-181">If any of the steps result in an error, you might need to manually complete the configuration.</span></span> <span data-ttu-id="e4cef-182">주어진 오류의 원인에 대한 자세한 내용을 보려면 **결과** 열에서 연결된 "오류" 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-182">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="e4cef-183">마법사가 완료되면 **닫기** 를 클릭하여 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cef-183">When the wizard completes, click **Close** to exit.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e4cef-184">복제본을 추가한 후 "후속 작업: [가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)의 복제본 추가 후" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cef-184">After adding a replica, see the "Follow Up: After Adding a Replica" section in [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e4cef-185">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e4cef-185">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e4cef-186">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e4cef-186">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="e4cef-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4cef-187">See Also</span></span>  
 <span data-ttu-id="e4cef-188">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4cef-188">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e4cef-189">[AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="e4cef-189">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 [<span data-ttu-id="e4cef-190">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e4cef-190">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
