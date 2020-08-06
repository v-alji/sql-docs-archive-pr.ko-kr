---
title: 가용성 그룹에 데이터베이스 추가 마법사 사용 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], databases
ms.assetid: 81e5e36d-735d-4731-8017-2654673abb88
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a093bb23687d4e49d311b46a7bb0bd211016a0ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646672"
---
# <a name="use-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="41290-102">가용성 그룹에 데이터베이스 추가 마법사 사용(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="41290-102">Use the Add Database to Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="41290-103">가용성 그룹에 데이터베이스 추가 마법사를 사용하여 기존 AlwaysOn 가용성 그룹에 하나 이상의 데이터베이스를 손쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-103">Use the Add Database to Availability Group Wizard to help you add one or more databases to an existing AlwaysOn availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41290-104">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 PowerShell을 사용하여 데이터베이스를 추가하는 방법은 [가용성 그룹에 데이터베이스 추가&#40;SQL Server&#41;](availability-group-add-a-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-104">For information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to add a database, see [Add a Database to an Availability Group &#40;SQL Server&#41;](availability-group-add-a-database.md).</span></span>  
  
 <span data-ttu-id="41290-105">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="41290-105">**In This Topic:**</span></span>  
  
-   <span data-ttu-id="41290-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="41290-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="41290-107">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="41290-107">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="41290-108">보안</span><span class="sxs-lookup"><span data-stu-id="41290-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="41290-109">**데이터베이스를 추가하려면:**  [가용성 그룹에 데이터베이스 추가 마법사 사용(SQL Server Management Studio)](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="41290-109">**To add a database, using:**  [Add Database to Availability Group Wizard (SQL Server Management Studio)](#SSMSProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="41290-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="41290-110">Before You Begin</span></span>  
 <span data-ttu-id="41290-111">가용성 그룹에 데이터베이스를 추가한 적이 없는 경우 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;에 대 한 필수 조건, 제한 사항 및 권장 사항 ](prereqs-restrictions-recommendations-always-on-availability.md)에서 "가용성 데이터베이스" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-111">If you have never added a database to an availability group, see the "Availability Databases" section in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="Prerequisites"></a><span data-ttu-id="41290-112">사전 요구 사항, 제한 사항 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="41290-112">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="41290-113">현재 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-113">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="41290-114">데이터가 암호화되었거나 심지어 DEK(데이터베이스 암호화 키)를 포함하는 경우 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 또는 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 를 사용하여 데이터베이스를 가용성 그룹에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-114">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="41290-115">암호화된 데이터베이스가 암호 해독된 경우라도 해당 로그 백업에는 암호화된 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-115">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="41290-116">이 경우 데이터베이스에서 전체 초기 데이터 동기화를 수행하면 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-116">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="41290-117">로그 복원 작업에는 DEK(데이터베이스 암호화 키)에서 사용된 인증서가 필요한데 이 인증서를 사용할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="41290-117">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="41290-118">**마법사를 사용하여 암호 해독된 데이터베이스를 가용성 그룹에 추가하기에 적합하도록 만들려면**</span><span class="sxs-lookup"><span data-stu-id="41290-118">**To make a decrypted database eligible to add to an availability group using the wizard:**</span></span>  
  
    1.  <span data-ttu-id="41290-119">주 데이터베이스의 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="41290-119">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="41290-120">주 데이터베이스의 전체 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="41290-120">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="41290-121">보조 복제본을 호스팅하는 서버 인스턴스에서 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-121">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="41290-122">주 데이터베이스에서 새 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="41290-122">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="41290-123">보조 데이터베이스에서 이 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-123">Restore this log backup on the secondary database.</span></span>  
  
-   <span data-ttu-id="41290-124">**전체 초기 데이터 동기화를 사용하기 위한 사전 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="41290-124">**Prerequisites for using full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="41290-125">모든 데이터베이스 파일 경로는 가용성 그룹에 대한 복제본을 호스팅하는 모든 서버 인스턴스에서 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-125">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="41290-126">보조 복제본을 호스팅하는 서버 인스턴스에 주 데이터베이스 이름이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-126">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="41290-127">즉, 새 보조 데이터베이스가 아직 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-127">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="41290-128">마법사에서 백업을 만들고 액세스하려면 네트워크 공유를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-128">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="41290-129">주 복제본의 경우 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 을 시작하는 데 사용되는 계정은 네트워크 공유에 대한 읽기 및 쓰기 파일 시스템 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-129">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="41290-130">보조 복제본에 대한 계정은 네트워크 공유에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-130">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="41290-131">마법사를 사용하여 전체 초기 데이터 동기화를 수행할 수 없는 경우에는 보조 데이터베이스를 수동으로 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-131">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="41290-132">마법사를 실행하기 전이나 후에 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-132">You can do this before or after running the wizard.</span></span> <span data-ttu-id="41290-133">자세한 내용은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-133">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="41290-134">보안</span><span class="sxs-lookup"><span data-stu-id="41290-134">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="41290-135">권한</span><span class="sxs-lookup"><span data-stu-id="41290-135">Permissions</span></span>  
 <span data-ttu-id="41290-136">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-136">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a><span data-ttu-id="41290-137">가용성 그룹에 데이터베이스 추가 마법사 사용 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="41290-137">Using the Add Database to Availability Group Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="41290-138">**가용성 그룹에 데이터베이스 추가 마법사를 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="41290-138">**To Use the Add Database to Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="41290-139">개체 탐색기에서 가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-139">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="41290-140">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-140">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="41290-141">데이터베이스를 추가할 가용성 그룹을 마우스 오른쪽 단추로 클릭하고 **데이터베이스 추가** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-141">Right-click the availability group to which you are adding a database, and select the **Add Database** command.</span></span> <span data-ttu-id="41290-142">이 명령은 가용성 그룹에 데이터베이스 추가 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-142">This command launches the Add Database to Availability Group Wizard.</span></span>  
  
4.  <span data-ttu-id="41290-143">**데이터베이스 선택** 페이지에서 하나 이상의 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-143">On the **Select Databases** page, select one or more databases.</span></span> <span data-ttu-id="41290-144">자세한 내용은 데이터베이스 [선택 페이지 &#40;새 가용성 그룹 마법사-데이터베이스 추가 마법사&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-144">For more information, see [Select Databases Page &#40;New Availability Group Wizard-Add Database Wizard&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md).</span></span>  
  
5.  <span data-ttu-id="41290-145">**초기 데이터 동기화 선택** 페이지에서 새 보조 복제본을 만들고 가용성 그룹에 조인할 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-145">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="41290-146">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-146">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="41290-147">**전체**</span><span class="sxs-lookup"><span data-stu-id="41290-147">**Full**</span></span>  
  
         <span data-ttu-id="41290-148">현재 환경이 초기 데이터 동기화 자동 시작을 위한 요구 사항을 충족하는 경우에 이 옵션을 선택합니다. 자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소, 제한 사항 및 권장 사항](#Prerequisites)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-148">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#Prerequisites), earlier in this topic).</span></span>  
  
         <span data-ttu-id="41290-149">**전체**를 선택한 후 가용성 그룹을 만들면 마법사에서 모든 주 데이터베이스와 해당 트랜잭션 로그를 네트워크 공유에 백업하고 보조 복제본을 호스팅하는 모든 서버 인스턴스에서 백업을 복원하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-149">If you select **Full**, after creating the availability group, the wizard will attempt to back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts an secondary replica.</span></span> <span data-ttu-id="41290-150">그런 다음 모든 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-150">The wizard will then join every secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="41290-151">**모든 복제본에서 액세스할 수 있는 공유 네트워크 위치 지정:** 필드에서 복제본을 호스팅하는 모든 서버 인스턴스에 읽기/쓰기 액세스 권한이 있는 백업 공유를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-151">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="41290-152">로그 백업이 로그 백업 체인의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="41290-152">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="41290-153">로그 백업 파일을 적절히 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-153">Store the log backup files appropriately.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="41290-154">필요한 파일 시스템 권한에 대한 자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소](#Prerequisites)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-154">For information about the required file-system permissions, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="41290-155">**조인만**</span><span class="sxs-lookup"><span data-stu-id="41290-155">**Join only**</span></span>  
  
         <span data-ttu-id="41290-156">보조 복제본을 호스팅할 서버 인스턴스에서 보조 데이터베이스를 수동으로 준비하는 경우 이 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-156">If you have manually prepared secondary databases on the server instances that will host the secondary replicas, you can select this option.</span></span> <span data-ttu-id="41290-157">마법사에서 기존 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-157">The wizard will join the existing secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="41290-158">**초기 데이터 동기화 건너뛰기**</span><span class="sxs-lookup"><span data-stu-id="41290-158">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="41290-159">주 데이터베이스의 로그 백업과 사용자 데이터베이스를 사용하려는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-159">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="41290-160">자세한 내용은 [AlwaysOn 보조 데이터베이스에서 데이터 이동 시작&#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-160">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
     <span data-ttu-id="41290-161">자세한 내용은 [AlwaysOn 가용성 그룹 마법사 &#40;초기 데이터 동기화 페이지 선택&#41;](select-initial-data-synchronization-page-always-on-availability-group-wizards.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-161">For more information, see [Select Initial Data Synchronization Page &#40;AlwaysOn Availability Group Wizards&#41;](select-initial-data-synchronization-page-always-on-availability-group-wizards.md).</span></span>  
  
6.  <span data-ttu-id="41290-162">**기존 보조 복제본에 연결** 페이지에서 이 가용성 그룹에 대한 가용성 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 모두 동일한 사용자 계정의 서비스로 실행 중인 경우 **모든 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-162">On the **Connect to Existing Secondary Replicas** page, if the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host the availability replicas for this availability group are all running as a service in the same user account, click **Connect all**.</span></span> <span data-ttu-id="41290-163">다른 계정에서 서비스로 실행 중인 서버 인스턴스가 있는 경우 각 서버 인스턴스 이름의 오른쪽에 있는 개별 **연결** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-163">If any of the server instances are running as a service under different accounts, click the individual **Connect** button to the right of each server instance name.</span></span>  
  
     <span data-ttu-id="41290-164">자세한 내용은 [기존 보조 복제본에 연결 페이지 &#40;복제본 추가 마법사 및 데이터베이스 추가 마법사&#41;](connect-to-existing-secondary-replicas-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-164">For more information, see [Connect to Existing Secondary Replicas Page &#40;Add Replica Wizard and Add Databases Wizard&#41;](connect-to-existing-secondary-replicas-page.md).</span></span>  
  
7.  <span data-ttu-id="41290-165">**유효성 검사** 페이지에서는 이 마법사에서 지정한 값이 새 가용성 그룹 마법사의 요구 사항을 충족하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-165">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the New Availability Group Wizard.</span></span> <span data-ttu-id="41290-166">변경하려면 **이전** 을 클릭하여 이전 마법사 페이지로 돌아가서 하나 이상의 값을 변경하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41290-166">To make a change, you can click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="41290-167">**다음** 을 클릭하여 **유효성 검사** 페이지로 돌아가서 **유효성 검사 다시 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-167">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
     <span data-ttu-id="41290-168">자세한 내용은 [&#40;AlwaysOn 가용성 그룹 마법사&#41;유효성 검사 페이지 ](validation-page-always-on-availability-group-wizards.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-168">For more information, see [Validation Page &#40;AlwaysOn Availability Group Wizards&#41;](validation-page-always-on-availability-group-wizards.md).</span></span>  
  
8.  <span data-ttu-id="41290-169">**요약** 페이지에서 새 가용성 그룹에 대한 선택 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-169">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="41290-170">변경하려면 **이전** 을 클릭하여 관련 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="41290-170">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="41290-171">변경 후에는 **다음** 을 클릭하여 **요약** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="41290-171">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
     <span data-ttu-id="41290-172">자세한 내용은 [&#41;AlwaysOn 가용성 그룹 마법사 &#40;요약 페이지 ](summary-page-always-on-availability-group-wizards.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-172">For more information, see [Summary Page &#40;AlwaysOn Availability Group Wizards&#41;](summary-page-always-on-availability-group-wizards.md).</span></span>  
  
     <span data-ttu-id="41290-173">선택이 완료되었으면 필요에 따라 스크립트를 클릭하여 마법사에서 실행할 단계에 대한 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-173">If you are satisfied with your selections, optionally click Script to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="41290-174">새 가용성 그룹을 만들어 구성하려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-174">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
9. <span data-ttu-id="41290-175">**진행률** 페이지에 가용성 그룹을 만들기 위한 단계(엔드포인트 구성, 가용성 그룹 만들기 및 가용성 그룹에 보조 복제본 조인)의 진행 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="41290-175">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
     <span data-ttu-id="41290-176">자세한 내용은 [&#41;&#40;AlwaysOn 가용성 그룹 마법사 진행률 페이지 ](progress-page-always-on-availability-group-wizards.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-176">For more information, see [Progress Page &#40;AlwaysOn Availability Group Wizards&#41;](progress-page-always-on-availability-group-wizards.md).</span></span>  
  
10. <span data-ttu-id="41290-177">이러한 단계가 완료되면 **결과** 페이지에 각 단계의 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="41290-177">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="41290-178">단계가 모두 성공하면 새 가용성 그룹이 완전히 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="41290-178">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="41290-179">단계에서 오류가 발생한 경우 구성을 수동으로 완료해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41290-179">If any of the steps result in an error, you might need to manually complete the configuration.</span></span> <span data-ttu-id="41290-180">주어진 오류의 원인에 대한 자세한 내용을 보려면 **결과** 열에서 연결된 "오류" 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-180">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="41290-181">마법사가 완료되면 **닫기** 를 클릭하여 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-181">When the wizard completes, click **Close** to exit.</span></span>  
  
     <span data-ttu-id="41290-182">자세한 내용은 [결과 페이지&#40;AlwaysOn 가용성 그룹 마법사&#41;](results-page-always-on-availability-group-wizards.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-182">For more information, see [Results Page &#40;AlwaysOn Availability Group Wizards&#41;](results-page-always-on-availability-group-wizards.md).</span></span>  
  
11. <span data-ttu-id="41290-183">모든 보조 데이터베이스에서 초기 데이터 동기화가 자동으로 시작되지 않은 경우 아직 조인되지 않은 모든 보조 데이터베이스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41290-183">If initial data synchronization was not automatically started on all of you secondary database, you need to configure any not-yet-joined secondary databases.</span></span> <span data-ttu-id="41290-184">자세한 내용은 [AlwaysOn 보조 데이터베이스에서 데이터 이동 시작&#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41290-184">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="41290-185">관련 작업</span><span class="sxs-lookup"><span data-stu-id="41290-185">Related Tasks</span></span>  
  
-   [<span data-ttu-id="41290-186">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41290-186">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="41290-187">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41290-187">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="41290-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="41290-188">See Also</span></span>  
 <span data-ttu-id="41290-189">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="41290-189">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="41290-190">[AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="41290-190">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="41290-191">[가용성 그룹에 데이터베이스 추가 &#40;SQL Server&#41;](availability-group-add-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="41290-191">[Add a Database to an Availability Group &#40;SQL Server&#41;](availability-group-add-a-database.md) </span></span>  
 <span data-ttu-id="41290-192">[AlwaysOn 보조 데이터베이스에서 데이터 이동을 시작 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="41290-192">[Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md) </span></span>  
 [<span data-ttu-id="41290-193">가용성 그룹에 데이터베이스 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41290-193">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
  
