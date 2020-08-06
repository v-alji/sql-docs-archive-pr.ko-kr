---
title: 데이터베이스 미러링 설정(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
ms.assetid: da45efed-55eb-4c71-be34-ac2589dfce8d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7e55e973ffbb888394d13578f21e08a08ae9d03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651879"
---
# <a name="setting-up-database-mirroring-sql-server"></a><span data-ttu-id="95bae-102">데이터베이스 미러링 설정(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="95bae-102">Setting Up Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="95bae-103">이 섹션에서는 데이터베이스 미러링을 설정하기 위한 사전 요구 사항, 권장 사항 및 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-103">This section describes the prerequisites, recommendations, and steps for setting up database mirroring.</span></span> <span data-ttu-id="95bae-104">데이터베이스 미러링에 대한 소개는 [데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-104">For an introduction to database mirroring, see [Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="95bae-105">구성이 성능에 영향을 줄 수 있으므로 사용률이 낮은 시간에 데이터베이스 미러링을 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-105">We recommend that you configure database mirroring during off-peak hours because configuration can impact performance.</span></span>  
  
 
  
##  <a name="preparing-a-server-instance-to-host-a-mirror-server"></a><a name="PrepareInstances"></a> <span data-ttu-id="95bae-106">미러 서버를 호스팅하도록 서버 인스턴스 준비</span><span class="sxs-lookup"><span data-stu-id="95bae-106">Preparing a Server Instance to Host a Mirror Server</span></span>  
 <span data-ttu-id="95bae-107">각 데이터베이스 미러링 세션에 대해 다음을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-107">For each database mirroring session:</span></span>  
  
1.  <span data-ttu-id="95bae-108">주 서버, 미러 서버 및 미러링 모니터 서버(있는 경우)는 별도의 호스트 시스템에 있는 개별 서버 인스턴스로 호스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-108">The principal server, mirror server, and witness, if any, must be hosted by separate server instances, which should be on separate host systems.</span></span> <span data-ttu-id="95bae-109">각 서버 인스턴스에는 데이터베이스 미러링 엔드포인트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-109">Each of the server instances requires a database mirroring endpoint.</span></span> <span data-ttu-id="95bae-110">데이터베이스 미러링 엔드포인트를 만들어야 할 경우 다른 서버 인스턴스에 액세스할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-110">If you need to create a database mirroring endpoint, ensure that it is accessible to the other server instances.</span></span>  
  
     <span data-ttu-id="95bae-111">서버 인스턴스에서 데이터베이스 미러링에 사용하는 인증 형식은 데이터베이스 미러링 엔드포인트의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-111">The form of authentication used for database mirroring by a server instance is a property of its database mirroring endpoint.</span></span> <span data-ttu-id="95bae-112">데이터베이스 미러링에서 사용할 수 있는 두 가지 전송 보안 유형으로 Windows 인증과 인증서 기반 인증이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-112">Two types of transport security are available for database mirroring: Windows Authentication or certificate-based authentication.</span></span> <span data-ttu-id="95bae-113">자세한 내용은 [데이터베이스 미러링에 대 한 전송 보안 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-113">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="95bae-114">네트워크 액세스에 대한 요구 사항은 다음과 같은 인증 형태에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-114">The requirements for network access are specific to the form of authentication, as follows:</span></span>  
  
    -   <span data-ttu-id="95bae-115">**Windows 인증을 사용하는 경우**</span><span class="sxs-lookup"><span data-stu-id="95bae-115">**If using Windows Authentication**</span></span>  
  
         <span data-ttu-id="95bae-116">서버 인스턴스가 여러 도메인 사용자 계정으로 실행되는 경우 각 인스턴스는 다른 인스턴스의 **master** 데이터베이스에서 로그인을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-116">If server instances are running under different domain user accounts, each requires a login in the **master** database of the others.</span></span> <span data-ttu-id="95bae-117">따라서 로그인이 없으면 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-117">If the login does not exist, you must create it.</span></span> <span data-ttu-id="95bae-118">자세한 내용은 [Windows 인증을 사용하여 데이터베이스 미러링 엔드포인트에 대한 네트워크 액세스 허용&#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-118">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
    -   <span data-ttu-id="95bae-119">**인증서를 사용하는 경우**</span><span class="sxs-lookup"><span data-stu-id="95bae-119">**If using certificates**</span></span>  
  
         <span data-ttu-id="95bae-120">지정된 서버 인스턴스에서 데이터베이스 미러링에 인증서 인증을 사용하려면 시스템 관리자가 아웃바운드 및 인바운드 연결 모두에 인증서를 사용하도록 각 서버 인스턴스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-120">To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span> <span data-ttu-id="95bae-121">이 경우 아웃바운드 연결을 먼저 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-121">Outbound connections must be configured first.</span></span> <span data-ttu-id="95bae-122">자세한 내용은 [데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-122">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="95bae-123">미러 서버에 모든 데이터베이스 사용자에 대한 로그인이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="95bae-123">Make sure that logins exist on the mirror server for all the database users.</span></span> <span data-ttu-id="95bae-124">자세한 내용은 [데이터베이스 미러링에 대 한 로그인 계정 설정 또는&#41;SQL Server &#40;AlwaysOn 가용성 그룹 ](set-up-login-accounts-database-mirroring-always-on-availability.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-124">For more information, see [Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md).</span></span>  
  
3.  <span data-ttu-id="95bae-125">미러 데이터베이스를 호스팅하는 서버 인스턴스에서 미러링된 데이터베이스에 필요한 환경의 남은 부분을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-125">On the server instance that will host the mirror database, set up the rest of the environment that is required for the mirrored database.</span></span> <span data-ttu-id="95bae-126">자세한 내용은 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-126">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="overview-establishing-a-database-mirroring-session"></a><a name="EstablishUsingWinAuthentication"></a> <span data-ttu-id="95bae-127">개요: 데이터베이스 미러링 세션 설정</span><span class="sxs-lookup"><span data-stu-id="95bae-127">Overview: Establishing a Database Mirroring Session</span></span>  
 <span data-ttu-id="95bae-128">미러링 세션을 설정하는 기본 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-128">The basic steps for establishing a mirroring session are as follows:</span></span>  
  
1.  <span data-ttu-id="95bae-129">모든 복원 작업에서 RESTORE WITH NORECOVERY를 사용하여 다음 백업을 복원해서 미러 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-129">Create the mirror database by restoring the following backups, using RESTORE WITH NORECOVERY on every restore operation:</span></span>  
  
    1.  <span data-ttu-id="95bae-130">백업을 수행할 때 주 데이터베이스가 이미 전체 복구 모델을 사용 중이었는지 확인한 후 주 데이터베이스의 최근 전체 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-130">Restore a recent full database backup of the principal database, after making sure that the principal database was already using the full recovery model when the backup was taken.</span></span> <span data-ttu-id="95bae-131">미러 데이터베이스는 주 데이터베이스와 이름이 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-131">The mirror database must have the same name as the principal database.</span></span>  
  
    2.  <span data-ttu-id="95bae-132">복원된 전체 백업 이후 데이터베이스에 대해 차등 백업을 수행한 경우 가장 최근의 차등 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-132">If you have taken any differential backups of the database since the restored full backup, restore your most recent differential backup.</span></span>  
  
    3.  <span data-ttu-id="95bae-133">전체 또는 차등 데이터베이스 백업 이후 수행된 모든 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-133">Restore all the log backups done since the full or differential database backup.</span></span>  
  
     <span data-ttu-id="95bae-134">자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-134">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="95bae-135">주 데이터베이스의 백업을 수행한 다음 가능한 빨리 남은 설정 단계를 완료하십시오.</span><span class="sxs-lookup"><span data-stu-id="95bae-135">Complete the remaining setup steps as soon as you can after taking the backup of the principal database.</span></span> <span data-ttu-id="95bae-136">파트너에서 미러링을 시작할 수 있으려면 먼저 원래 데이터베이스에서 현재 로그 백업을 만든 다음 후속 미러 데이터베이스로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-136">Before you can start mirroring on the partners, you should create a current log backup on the original database and restore it to the future mirror database.</span></span>  
  
2.  <span data-ttu-id="95bae-137">[!INCLUDE[tsql](../../includes/tsql-md.md)] 또는 데이터베이스 미러링 마법사를 사용하여 미러링을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-137">You can set up mirroring by using either [!INCLUDE[tsql](../../includes/tsql-md.md)] or the Database Mirroring Wizard.</span></span> <span data-ttu-id="95bae-138">자세한 내용은 다음 중 하나를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="95bae-138">For more information, see one of the following:</span></span>  
  
    -   [<span data-ttu-id="95bae-139">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-139">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
    -   [<span data-ttu-id="95bae-140">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-140">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
3.  <span data-ttu-id="95bae-141">기본적으로 세션은 전체 트랜잭션 보안으로 설정되므로(SAFETY가 FULL로 설정됨) 자동 장애 조치를 지원하지 않는 동기 보호 우선 모드로 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-141">By default a session is set to full transaction safety (SAFETY is set to FULL), which starts the session in synchronous, high-safety mode without automatic failover.</span></span> <span data-ttu-id="95bae-142">이러한 세션을 다음과 같이 자동 장애 조치(Failover)가 있는 보호 우선 모드나 비동기 성능 우선 모드에서 실행되도록 다시 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-142">You can reconfigure the session to run in high-safety mode with automatic failover or in asynchronous, high-performance mode, as follows:</span></span>  
  
    -   <span data-ttu-id="95bae-143">**자동 장애 조치 있는 보호 우선 모드**</span><span class="sxs-lookup"><span data-stu-id="95bae-143">**High-safety mode with automatic failover**</span></span>  
  
         <span data-ttu-id="95bae-144">자동 장애 조치(Failover)가 있는 보호 우선 모드로 세션을 실행하려면 미러링 모니터 서버 인스턴스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-144">If you want a high-safety mode session to support automatic failover, add a witness server instance.</span></span>  
  
         <span data-ttu-id="95bae-145">**미러링 모니터 서버를 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="95bae-145">**To add a witness**</span></span>  
  
        -   [<span data-ttu-id="95bae-146">Windows 인증을 사용하여 데이터베이스 미러링 모니터 추가&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-146">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
        -   [<span data-ttu-id="95bae-147">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-147">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
        > [!NOTE]  
        >  <span data-ttu-id="95bae-148">데이터베이스 소유자는 언제든지 데이터베이스의 미러링 모니터를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-148">The database owner can turn off the witness for a database at any time.</span></span> <span data-ttu-id="95bae-149">미러링 모니터를 해제하면 미러링 모니터가 없는 것과 마찬가지로 자동 장애 조치가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-149">Turning off the witness is equivalent to having no witness, and automatic failover cannot occur.</span></span>  
  
    -   <span data-ttu-id="95bae-150">**성능 우선 모드**</span><span class="sxs-lookup"><span data-stu-id="95bae-150">**High-performance mode**</span></span>  
  
         <span data-ttu-id="95bae-151">자동 장애 조치 기능을 지원하지 않고 가용성보다 성능을 우선하려면 트랜잭션 보안을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-151">Alternatively, if you do not want automatic failover and you prefer to emphasize performance over availability, turn off transaction safety.</span></span> <span data-ttu-id="95bae-152">자세한 내용은 [데이터베이스 미러링 세션에서 트랜잭션 보안 변경&#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-152">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="95bae-153">성능 우선 모드에서는 WITNESS를 OFF로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-153">In high-performance mode, WITNESS needs to be set to OFF.</span></span> <span data-ttu-id="95bae-154">자세한 내용은 [쿼럼: 미러링 모니터 서버가 데이터베이스 가용성에 미치는 영향&#40;데이터베이스 미러링&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-154">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95bae-155">Microsoft Windows 인증을 사용하여 데이터베이스 미러링을 설정하기 위해 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하는 예는 [예제: Windows 인증을 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-155">For an example of using [!INCLUDE[tsql](../../includes/tsql-md.md)] to set up database mirroring using Microsoft Windows Authentication, see [Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md).</span></span>  
>   
>  <span data-ttu-id="95bae-156">인증서 기반 보안을 사용하여 데이터베이스 미러링을 설정하기 위해 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하는 예는 [예제: 인증서를 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95bae-156">For an example of using [!INCLUDE[tsql](../../includes/tsql-md.md)] to set up database mirroring using certificate-based security, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
 
  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="95bae-157">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="95bae-157">In This Section</span></span>  
 [<span data-ttu-id="95bae-158">미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-158">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
 <span data-ttu-id="95bae-159">일시 중단된 세션을 재개하기 전에 미러 데이터베이스를 만들거나 준비하는 단계를 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-159">Summarizes the steps for creating a mirror database or preparing a mirror database before resuming a suspended session.</span></span> <span data-ttu-id="95bae-160">또한 방법 도움말 항목에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-160">Also provides links to how-to topics.</span></span>  
  
 [<span data-ttu-id="95bae-161">서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-161">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
 <span data-ttu-id="95bae-162">서버 네트워크 주소의 구문, 주소로 서버 인스턴스의 데이터베이스 미러링 엔드포인트를 식별하는 방법 및 시스템의 정규화된 도메인 이름을 찾는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-162">Describes the syntax of a server network address, how the address identifies the database mirroring endpoint of the server instance, and how to find the fully-qualified domain name of a system.</span></span>  
  
 [<span data-ttu-id="95bae-163">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-163">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
 <span data-ttu-id="95bae-164">데이터베이스 미러링 보안 구성 마법사를 사용하여 데이터베이스에서 데이터베이스 미러링을 시작하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-164">Describes how to use the Configure Database Mirroring Security Wizard to start database mirroring on a database.</span></span>  
  
 [<span data-ttu-id="95bae-165">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-165">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
 <span data-ttu-id="95bae-166">데이터베이스 미러링을 설정하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-166">Describes the [!INCLUDE[tsql](../../includes/tsql-md.md)] steps for setting up database mirroring.</span></span>  
  
 [<span data-ttu-id="95bae-167">예: Windows 인증을 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-167">Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)  
 <span data-ttu-id="95bae-168">Windows 인증을 사용하여 미러링 모니터 서버가 있는 데이터베이스 미러링 세션을 만드는 데 필요한 모든 단계의 예를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-168">Contains an example of all the stages required to create a database mirroring session with a witness, using Windows Authentication.</span></span>  
  
 [<span data-ttu-id="95bae-169">예: 인증서를 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-169">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
 <span data-ttu-id="95bae-170">인증서 기반 인증을 사용하여 미러링 모니터 서버가 있는 데이터베이스 미러링 세션을 만드는 데 필요한 모든 단계의 예를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-170">Contains an example of all the stages required to create a database mirroring session with a witness, using certificate-based authentication.</span></span>  
  
 [<span data-ttu-id="95bae-171">데이터베이스 미러링을 위한 로그인 계정을 설정 하거나 &#40;SQL Server를 AlwaysOn 가용성 그룹&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-171">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](set-up-login-accounts-database-mirroring-always-on-availability.md)  
 <span data-ttu-id="95bae-172">로컬 서버 인스턴스가 아닌 다른 계정을 사용하는 원격 서버 인스턴스의 로그인을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="95bae-172">Describes creating a login for a remote server instance that is using a different account than the local server instance.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="95bae-173">관련 작업</span><span class="sxs-lookup"><span data-stu-id="95bae-173">Related Tasks</span></span>  
 <span data-ttu-id="95bae-174">**SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="95bae-174">**SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="95bae-175">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-175">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
-   [<span data-ttu-id="95bae-176">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-176">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
 <span data-ttu-id="95bae-177">**Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="95bae-177">**Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="95bae-178">Windows 인증을 사용하여 데이터베이스 미러링 엔드포인트에 대한 네트워크 액세스 허용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-178">Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;</span></span>](../database-mirroring-allow-network-access-windows-authentication.md)  
  
-   [<span data-ttu-id="95bae-179">데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-179">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="95bae-180">데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-180">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="95bae-181">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-181">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="95bae-182">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-182">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="95bae-183">Windows 인증을 사용하여 데이터베이스 미러링 모니터 추가&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-183">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="95bae-184">Trustworthy 속성을 사용하도록 미러 데이터베이스 설정&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-184">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
 <span data-ttu-id="95bae-185">**Transact-SQL/SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="95bae-185">**Transact-SQL/SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="95bae-186">서버 인스턴스 업그레이드 시 미러된 데이터베이스의 작동 중단 최소화</span><span class="sxs-lookup"><span data-stu-id="95bae-186">Minimize Downtime for Mirrored Databases When Upgrading Server Instances</span></span>](upgrading-mirrored-instances.md)  
  
-   [<span data-ttu-id="95bae-187">미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-187">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="95bae-188">데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-188">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="95bae-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95bae-189">See Also</span></span>  
 <span data-ttu-id="95bae-190">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="95bae-190">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="95bae-191">[데이터베이스 미러링: 상호 운용성 및 공존성&#40;SQL Server&#41;](database-mirroring-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="95bae-191">[Database Mirroring: Interoperability and Coexistence &#40;SQL Server&#41;](database-mirroring-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="95bae-192">[데이터베이스 미러링 및 AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 전송 보안&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="95bae-192">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 [<span data-ttu-id="95bae-193">서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;</span><span class="sxs-lookup"><span data-stu-id="95bae-193">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
  
