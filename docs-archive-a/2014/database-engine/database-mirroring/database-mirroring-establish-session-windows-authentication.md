---
title: Windows 인증을 사용 하 여 데이터베이스 미러링 세션 설정 (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 143c68a5-589f-4e7f-be59-02707e1a430a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3088333fbfd4babd209df07f8880c838ce626d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647225"
---
# <a name="establish-a-database-mirroring-session-using-windows-authentication-transact-sql"></a><span data-ttu-id="a67b8-102">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a67b8-102">Establish a Database Mirroring Session Using Windows Authentication (Transact-SQL)</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="a67b8-103">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-103">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="a67b8-104">미러 데이터베이스를 준비한 후( [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)참조) 데이터베이스 미러링 세션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-104">After the mirror database is prepared (see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)), you can establish a database mirroring session.</span></span> <span data-ttu-id="a67b8-105">주 서버, 미러 서버 및 미러링 모니터 서버 인스턴스는 다른 호스트 시스템에 있는 별도의 서버 인스턴스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-105">The principal, mirror, and witness server instances must be separate server instances, which should be on separate host systems.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a67b8-106">미러링 구성은 성능에 영향을 줄 수 있으므로 사용률이 낮은 시간에 데이터베이스 미러링을 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-106">We recommend that you configure database mirroring during off-peak hours because configuring mirroring can impact performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a67b8-107">지정된 서버 인스턴스는 같은 파트너 또는 다른 파트너에 있는 여러 개의 동시 데이터베이스 미러링 세션에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-107">A given server instance can participate in multiple concurrent database mirroring sessions with the same or different partners.</span></span> <span data-ttu-id="a67b8-108">서버 인스턴스는 한 세션에서는 파트너가 되고, 다른 세션에서는 미러링 모니터 서버가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-108">A server instance can be a partner in some sessions and a witness in other sessions.</span></span> <span data-ttu-id="a67b8-109">미러 서버 인스턴스는 주 서버 인스턴스와 동일한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-109">The mirror server instance must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as the principal server instance.</span></span> <span data-ttu-id="a67b8-110">일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서는 데이터베이스 미러링을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-110">Database mirroring is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a67b8-111">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-111">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="a67b8-112">또한 서버 인스턴스는 동일한 작업을 처리할 수 있는 동등한 시스템에서 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-112">Also, we strongly recommend that they run on comparable systems that can handle identical workloads.</span></span>  
  
### <a name="to-establish-a-database-mirroring-session"></a><span data-ttu-id="a67b8-113">데이터베이스 미러링 세션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="a67b8-113">To establish a database mirroring session</span></span>  
  
1.  <span data-ttu-id="a67b8-114">미러 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-114">Create the mirror database.</span></span> <span data-ttu-id="a67b8-115">자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-115">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="a67b8-116">각 서버 인스턴스에서 보안을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-116">Set up security on each server instance.</span></span>  
  
     <span data-ttu-id="a67b8-117">데이터베이스 미러링 세션의 각 서버 인스턴스에는 데이터베이스 미러링 엔드포인트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-117">Each server instance in a database mirroring session requires a database mirroring endpoint.</span></span> <span data-ttu-id="a67b8-118">따라서 엔드포인트가 없으면 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-118">If the endpoint does not exist, you must create it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a67b8-119">서버 인스턴스에서 데이터베이스 미러링에 사용하는 인증 형식은 데이터베이스 미러링 엔드포인트의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-119">The form of authentication used for database mirroring by a server instance is a property of its database mirroring endpoint.</span></span> <span data-ttu-id="a67b8-120">데이터베이스 미러링에서 사용할 수 있는 두 가지 전송 보안 유형으로 Windows 인증과 인증서 기반 인증이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-120">Two types of transport security are available for database mirroring: Windows Authentication or certificate-based authentication.</span></span> <span data-ttu-id="a67b8-121">자세한 내용은 [데이터베이스 미러링에 대 한 전송 보안 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-121">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="a67b8-122">각 파트너 서버에서 데이터베이스 미러링의 엔드포인트가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-122">On each partner server, ensure that an endpoint exists for database mirroring.</span></span> <span data-ttu-id="a67b8-123">지원할 미러링 세션의 수에 관계없이 서버 인스턴스에는 데이터베이스 미러링 엔드포인트가 하나만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-123">Regardless of the number of mirroring sessions to be supported, the server instance can have only one database mirroring endpoint.</span></span> <span data-ttu-id="a67b8-124">이 서버 인스턴스를 데이터베이스 미러링 세션의 파트너 전용으로 사용하려면 엔드포인트에 파트너 역할을 할당합니다(ROLE **=** PARTNER).</span><span class="sxs-lookup"><span data-stu-id="a67b8-124">If you intend to use this server instance exclusively for partners in database mirroring sessions, you can assign the role of partner to the endpoint (ROLE**=** PARTNER).</span></span> <span data-ttu-id="a67b8-125">이 서버를 다른 데이터베이스 미러링 세션에서 미러링 모니터 서버로도 사용하려면 엔드포인트 역할을 ALL로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-125">If you intend also to use this server for the witness in other database mirroring sessions, assign the role of the endpoint as ALL.</span></span>  
  
     <span data-ttu-id="a67b8-126">SET PARTNER 문을 실행하려면 두 파트너의 엔드포인트에 대한 STATE가 STARTED로 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-126">To execute a SET PARTNER statement, the STATE of the endpoints of both partners must be set to STARTED.</span></span>  
  
     <span data-ttu-id="a67b8-127">서버 인스턴스에 데이터베이스 미러링 엔드포인트가 있는지 확인하고 그 역할과 상태를 확인하려면 해당 인스턴스에 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-127">To learn whether a server instance has a database mirroring endpoint and to learn its role and state, on that instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a67b8-128">사용 중인 데이터베이스 미러링 엔드포인트는 다시 구성하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-128">Do not reconfigure an in-use database mirroring endpoint.</span></span> <span data-ttu-id="a67b8-129">데이터베이스 미러링 엔드포인트가 있으며 이미 사용 중인 경우 서버 인스턴스의 모든 세션에 이 엔드포인트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-129">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint for every session on the server instance.</span></span> <span data-ttu-id="a67b8-130">사용 중인 엔드포인트를 삭제하면 엔드포인트가 다시 시작되어 기존 세션의 연결이 끊어지므로 다른 서버 인스턴스에서 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-130">Dropping an in-use endpoint can cause the endpoint to restart, disrupting the connections of the existing sessions, which can appear to be an error to the other server instances.</span></span> <span data-ttu-id="a67b8-131">이는 특히 파트너에 엔드포인트를 다시 구성하면 장애 조치(Failover) 오류가 발생할 수 있는 자동 장애 조치(Failover)가 있는 보호 우선 모드에서 중요한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-131">This is particularly important in high-safety mode with automatic failover, in which reconfiguring the endpoint on a partner could cause a failover to occur.</span></span> <span data-ttu-id="a67b8-132">또한 세션에 미러링 모니터 서버가 설정된 경우 데이터베이스 미러링 엔드포인트를 삭제하면 해당 세션의 주 서버에서 쿼럼이 손실될 수 있습니다. 이 경우 데이터베이스는 오프라인 상태가 되며 해당 사용자의 연결이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-132">Also, if a witness has been set for a session, dropping the database mirroring endpoint can cause the principal server of that session to lose quorum; if that occurs, the database is taken offline and its users are disconnected.</span></span> <span data-ttu-id="a67b8-133">자세한 내용은 [쿼럼: 미러링 모니터 서버가 데이터베이스 가용성에 미치는 영향&#40;데이터베이스 미러링&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-133">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="a67b8-134">파트너 중 하나에 엔드포인트가 없는 경우 [Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)버전에서는 데이터베이스 미러링을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-134">If either partner lacks an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
3.  <span data-ttu-id="a67b8-135">서버 인스턴스가 여러 도메인 사용자 계정으로 실행되는 경우 각 인스턴스는 다른 인스턴스의 **master** 데이터베이스에서 로그인을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-135">If server instances are running under different domain user accounts, each requires a login in the **master** database of the others.</span></span> <span data-ttu-id="a67b8-136">따라서 로그인이 없으면 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-136">If the login does not exist, you must create it.</span></span> <span data-ttu-id="a67b8-137">자세한 내용은 [Windows 인증을 사용하여 데이터베이스 미러링 엔드포인트에 대한 네트워크 액세스 허용&#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-137">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
4.  <span data-ttu-id="a67b8-138">미러 데이터베이스에서 주 서버를 파트너로 설정하려면 미러 서버에 연결하여 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-138">To set the principal server as partner on the mirror database, connect to the mirror server, and issue the following statement:</span></span>  
  
     <span data-ttu-id="a67b8-139">ALTER DATABASE *<database_name>* SET PARTNER **=** _<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="a67b8-139">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span></span>  
  
     <span data-ttu-id="a67b8-140">여기서 *<database_name>* 은 미러링할 데이터베이스의 이름 (두 파트너에서이 이름은 동일)이 고 *<server_network_address>* 는 주 서버의 서버 네트워크 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-140">where *<database_name>* is the name of the database to be mirrored (this name is the same on both partners), and *<server_network_address>* is the server network address of the principal server.</span></span>  
  
     <span data-ttu-id="a67b8-141">서버 네트워크 주소 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-141">The syntax for a server network address is as follows:</span></span>  
  
     <span data-ttu-id="a67b8-142">TCP:<strong>//</strong> \<*system-address> \*<strong>:</strong> \<*port> \*</span><span class="sxs-lookup"><span data-stu-id="a67b8-142">TCP<strong>://</strong>\<*system-address>*<strong>:</strong>\<*port>*</span></span>  
  
     <span data-ttu-id="a67b8-143">여기서 \<*system-address>*는 대상 컴퓨터 시스템을 명확하게 식별하는 문자열이고 \<*port>*는 파트너 서버 인스턴스의 미러링 엔드포인트에 사용되는 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-143">where \<*system-address>\* is a string that unambiguously identifies the destination computer system, and \<*port>\* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="a67b8-144">자세햔 내용은 [서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](specify-a-server-network-address-database-mirroring.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-144">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="a67b8-145">예를 들어 미러 서버 인스턴스에서 다음 ALTER DATABASE 문은 파트너를 원래 주 서버 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-145">For example, on the mirror server instance, the following ALTER DATABASE statement sets the partner as the original principal server instance.</span></span> <span data-ttu-id="a67b8-146">데이터베이스 이름은 **AdventureWorks**이고 시스템 주소는 DBSERVER1(파트너 시스템의 이름)이며 파트너의 데이터베이스 미러링 엔드포인트에서 사용되는 포트는 7022입니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-146">The database name is **AdventureWorks**, the system address is DBSERVER1-the name of the partner's system-and the port used by the partner's database mirroring endpoint is 7022:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
       SET PARTNER = 'TCP://DBSERVER1:7022'  
    ```  
  
     <span data-ttu-id="a67b8-147">이 문은 주 서버에서 접속할 때 세션을 구성하도록 미러 서버를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-147">This statement prepares the mirror server to form a session when it is contacted by the principal server.</span></span>  
  
5.  <span data-ttu-id="a67b8-148">주 데이터베이스에서 미러 서버를 파트너로 설정하려면 주 서버에 연결하여 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-148">To set the mirror server as partner on the principal database, connect to the principal server, and issue the following statement:</span></span>  
  
     <span data-ttu-id="a67b8-149">ALTER DATABASE *<database_name>* SET PARTNER **=** _<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="a67b8-149">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span></span>  
  
     <span data-ttu-id="a67b8-150">자세한 내용은 4단계를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a67b8-150">For more information, see step 4.</span></span>  
  
     <span data-ttu-id="a67b8-151">예를 들어 주 서버 인스턴스에서 다음 ALTER DATABASE 문은 파트너를 원래 미러 서버 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-151">For example, on the principal server instance, the following ALTER DATABASE statement sets the partner as the original mirror server instance.</span></span> <span data-ttu-id="a67b8-152">데이터베이스 이름은 **AdventureWorks**이고 시스템 주소는 DBSERVER2(파트너 시스템의 이름)이며 파트너의 데이터베이스 미러링 엔드포인트에서 사용되는 포트는 7025입니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-152">The database name is **AdventureWorks**, the system address is DBSERVER2-the name of the partner's system-and the port used by the partner's database mirroring endpoint is 7025:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks SET PARTNER = 'TCP://DBSERVER2:7022'  
    ```  
  
     <span data-ttu-id="a67b8-153">주 서버에서 이 문을 입력하면 데이터베이스 미러링 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-153">Entering this statement on the principal server begins the database mirroring session.</span></span>  
  
6.  <span data-ttu-id="a67b8-154">기본적으로 세션은 전체 트랜잭션 보안으로 설정되므로(SAFETY가 FULL로 설정됨) 자동 장애 조치를 지원하지 않는 동기 보호 우선 모드로 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-154">By default a session is set to full transaction safety (SAFETY is set to FULL), which starts the session in synchronous, high-safety mode without automatic failover.</span></span> <span data-ttu-id="a67b8-155">이러한 세션을 다음과 같이 자동 장애 조치(Failover)가 있는 보호 우선 모드나 비동기 성능 우선 모드에서 실행되도록 다시 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-155">You can reconfigure the session to run in high-safety mode with automatic failover or in asynchronous, high-performance mode, as follows:</span></span>  
  
    -   <span data-ttu-id="a67b8-156">**자동 장애 조치 있는 보호 우선 모드**</span><span class="sxs-lookup"><span data-stu-id="a67b8-156">**High-safety mode with automatic failover**</span></span>  
  
         <span data-ttu-id="a67b8-157">자동 장애 조치(Failover)가 있는 보호 우선 모드로 세션을 실행하려면 미러링 모니터 서버 인스턴스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-157">If you want a high-safety mode session to support automatic failover, add a witness server instance.</span></span> <span data-ttu-id="a67b8-158">자세한 내용은 [Windows 인증을 사용하여 데이터베이스 미러링 모니터 추가&#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-158">For more information, see [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md).</span></span>  
  
    -   <span data-ttu-id="a67b8-159">**성능 우선 모드**</span><span class="sxs-lookup"><span data-stu-id="a67b8-159">**High-performance mode**</span></span>  
  
         <span data-ttu-id="a67b8-160">자동 장애 조치 기능을 지원하지 않고 가용성보다 성능을 우선하려면 트랜잭션 보안을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-160">Alternatively, if you do not want automatic failover and you prefer to emphasize performance over availability, turn off transaction safety.</span></span> <span data-ttu-id="a67b8-161">자세한 내용은 [데이터베이스 미러링 세션에서 트랜잭션 보안 변경&#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-161">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a67b8-162">성능 우선 모드에서는 WITNESS를 OFF로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-162">In high-performance mode, WITNESS should be set to OFF.</span></span> <span data-ttu-id="a67b8-163">자세한 내용은 [쿼럼: 미러링 모니터 서버가 데이터베이스 가용성에 미치는 영향&#40;데이터베이스 미러링&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-163">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a67b8-164">예제</span><span class="sxs-lookup"><span data-stu-id="a67b8-164">Example</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a67b8-165">다음 예에서는 기존 미러 데이터베이스의 파트너 간에 데이터베이스 미러링 세션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-165">The following example establishes a database mirroring session between partners for an existing mirror database.</span></span> <span data-ttu-id="a67b8-166">미러 데이터베이스를 만드는 방법은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-166">For information on creating a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)=.</span></span>  
  
 <span data-ttu-id="a67b8-167">이 예에서는 미러링 모니터 서버 없이 데이터베이스 미러링 세션을 만드는 기본 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-167">The example shows the basic steps for creating a database mirroring session without a witness.</span></span> <span data-ttu-id="a67b8-168">두 파트너는 두 컴퓨터 시스템(PARTNERHOST1 및 PARTNERHOST5)의 기본 서버 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-168">The two partners are the default server instances on two computer systems (PARTNERHOST1 and PARTNERHOST5).</span></span> <span data-ttu-id="a67b8-169">두 파트너 인스턴스는 동일한 Windows 도메인 사용자 계정(MYDOMAIN\dbousername)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-169">The two partner instances run the same Windows domain user account (MYDOMAIN\dbousername).</span></span>  
  
1.  <span data-ttu-id="a67b8-170">주 서버 인스턴스(PARTNERHOST1의 기본 인스턴스)에서 포트 7022를 사용하여 모든 역할을 지원하는 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-170">On the principal server instance (default instance on PARTNERHOST1), create an endpoint that supports all roles using port 7022:</span></span>  
  
    ```  
    --create an endpoint for this instance  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="a67b8-171">로그인을 설정하는 방법의 예제는 [Windows 인증을 사용하여 데이터베이스 미러링 엔드포인트에 대한 네트워크 액세스 허용&#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)버전에서는 데이터베이스 미러링을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-171">For an example of how to setup a login, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
2.  <span data-ttu-id="a67b8-172">미러 서버 인스턴스(PARTNERHOST5의 기본 인스턴스)에서 포트 7022를 사용하여 모든 역할을 지원하는 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-172">On the mirror server instance (default instance on PARTNERHOST5), create an endpoint that supports all roles using port 7022:</span></span>  
  
    ```  
    --create an endpoint for this instance  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    ```  
  
3.  <span data-ttu-id="a67b8-173">PARTNERHOST1의 주 서버 인스턴스에서 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-173">On the principal server instance (on PARTNERHOST1), back up the database:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdvWorks_dbmirror.bak'   
        WITH FORMAT  
    GO  
    ```  
  
4.  <span data-ttu-id="a67b8-174">`PARTNERHOST5`의 미러 서버 인스턴스에서 데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-174">On the mirror server instance (on `PARTNERHOST5`), restore the database:</span></span>  
  
    ```  
    RESTORE DATABASE AdventureWorks   
        FROM DISK = 'Z:\AdvWorks_dbmirror.bak'   
        WITH NORECOVERY  
    GO  
    ```  
  
5.  <span data-ttu-id="a67b8-175">전체 데이터베이스 백업을 만든 후 주 데이터베이스에서 로그 백업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-175">After you create the full database backup, you must create a log backup on the principal database.</span></span> <span data-ttu-id="a67b8-176">예를 들어 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 앞의 데이터베이스 백업에 사용된 동일한 파일에 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-176">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement backs up the log to the same file used by the preceding database backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="a67b8-177">미러링을 시작하기 전에 필수 로그 백업 및 모든 후속 로그 백업을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-177">Before you can start mirroring, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="a67b8-178">예를 들어 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 C:\AdventureWorks.bak로부터 첫 번째 로그를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-178">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores the first log from C:\AdventureWorks.bak:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\ AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="a67b8-179">미러 서버 인스턴스에서 PARTNERHOST1의 서버 인스턴스를 파트너로 설정하여 초기 주 서버로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-179">On the mirror server instance, set the server instance on PARTNERHOST1 as the partner (making it the initial principal server):</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
        SET PARTNER =   
        'TCP://PARTNERHOST1:7022'  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a67b8-180">기본적으로 데이터베이스 미러링 세션은 전체 트랜잭션 보안(SAFETY가 FULL로 설정됨)에 따라 달라지는 동기 모드로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-180">default, a database mirroring session runs in synchronous mode, which depends on having full transaction safety (SAFETY is set to FULL).</span></span> <span data-ttu-id="a67b8-181">비동기 성능 우선 모드로 세션을 실행하려면 SAFETY를 OFF로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-181">To cause a session to run in asynchronous, high-performance mode, set SAFETY to OFF.</span></span> <span data-ttu-id="a67b8-182">자세한 내용은 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-182">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
8.  <span data-ttu-id="a67b8-183">주 서버 인스턴스에서 `PARTNERHOST5` 의 서버 인스턴스를 파트너로 설정하여 초기 미러 서버로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-183">On the principal server instance, set the server instance on `PARTNERHOST5` as the partner (making it the initial mirror server):</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://PARTNERHOST5:7022'  
    GO  
    ```  
  
9. <span data-ttu-id="a67b8-184">필요에 따라 자동 장애 조치(Failover)가 있는 보호 우선 모드를 사용하려면 미러링 모니터 서버 인스턴스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a67b8-184">Optionally, if you intend to use high-safety mode with automatic failover, set up the witness server instance.</span></span> <span data-ttu-id="a67b8-185">자세한 내용은 [Windows 인증을 사용하여 데이터베이스 미러링 모니터 추가&#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-185">For more information, see [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a67b8-186">보안 설정 표시, 미러 데이터베이스 준비, 파트너 설정 및 미러링 모니터 서버 추가 등의 작업을 수행하는 전체 예제는 [데이터베이스 미러링 설정&#40;SQL Server&#41;](database-mirroring-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a67b8-186">For a complete example showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a67b8-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a67b8-187">See Also</span></span>  
 <span data-ttu-id="a67b8-188">[데이터베이스 미러링 설정&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a67b8-188">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="a67b8-189">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a67b8-189">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="a67b8-190">[Windows 인증을 사용하여 데이터베이스 미러링 엔드포인트에 대한 네트워크 액세스 허용&#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="a67b8-190">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span></span>  
 <span data-ttu-id="a67b8-191">[미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a67b8-191">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="a67b8-192">[Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="a67b8-192">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="a67b8-193">[데이터베이스 미러링 및 로그 전달&#40;SQL Server&#41;](database-mirroring-and-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a67b8-193">[Database Mirroring and Log Shipping &#40;SQL Server&#41;](database-mirroring-and-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="a67b8-194">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a67b8-194">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="a67b8-195">[데이터베이스 미러링 및 복제&#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a67b8-195">[Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span></span>  
 <span data-ttu-id="a67b8-196">[데이터베이스 미러링 설정&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a67b8-196">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="a67b8-197">[서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="a67b8-197">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 [<span data-ttu-id="a67b8-198">데이터베이스 미러링 운영 모드</span><span class="sxs-lookup"><span data-stu-id="a67b8-198">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
