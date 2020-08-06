---
title: Windows 인증을 사용하여 데이터베이스 미러링 모니터 서버 추가(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- Windows authentication [SQL Server]
- database mirroring [SQL Server], witness
ms.assetid: bf5e87df-91a4-49f9-ae88-2a6dcf644510
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 88684c3a1ca12ea579859759ed804ca281647fa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648585"
---
# <a name="add-a-database-mirroring-witness-using-windows-authentication-transact-sql"></a><span data-ttu-id="8ed2d-102">Windows 인증을 사용하여 데이터베이스 미러링 모니터 추가(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8ed2d-102">Add a Database Mirroring Witness Using Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="8ed2d-103">데이터베이스에 미러링 모니터를 설정하려면 데이터베이스 소유자는 데이터베이스 엔진 인스턴스를 미러링 모니터 서버의 역할로 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-103">To set up a witness for a database, the database owner assigns a Database Engine instance to the role of witness server.</span></span> <span data-ttu-id="8ed2d-104">미러링 모니터 서버 인스턴스는 주 서버 인스턴스 또는 미러 서버 인스턴스와 동일한 컴퓨터에서 실행될 수 있으나 이 경우 자동 장애 조치(Failover)의 효과가 크게 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-104">The witness server instance can run on the same computer as the principal or mirror server instance, but this substantially reduces the robustness of automatic failover.</span></span>  
  
 <span data-ttu-id="8ed2d-105">그러므로 미러링 모니터를 동일한 컴퓨터에서 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-105">We strongly recommend that the witness reside on a separate computer.</span></span> <span data-ttu-id="8ed2d-106">지정된 서버는 같은 파트너 또는 다른 파트너에 있는 여러 개의 동시 데이터베이스 미러링 세션에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-106">A given server can participate in multiple concurrent database mirroring sessions with the same or different partners.</span></span> <span data-ttu-id="8ed2d-107">지정된 서버는 한 세션에서는 파트너가 되고, 다른 세션에서는 미러링 모니터가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-107">A given server can be a partner in some sessions and a witness in other sessions.</span></span>  
  
 <span data-ttu-id="8ed2d-108">미러링 모니터는 자동 장애 조치가 있는 보호 우선 모드에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-108">The witness is intended exclusively for high-safety mode with automatic failover.</span></span> <span data-ttu-id="8ed2d-109">미러링 모니터를 설정하기 전에 현재 SAFETY 속성이 FULL로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-109">Before you set a witness, we strongly recommend that you ensure that the SAFETY property is currently set to FULL.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8ed2d-110">구성이 성능에 영향을 줄 수 있으므로 사용률이 낮은 시간에 데이터베이스 미러링을 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-110">We recommend that you configure database mirroring during off-peak hours because configuration can impact performance.</span></span>  
  
### <a name="to-establish-a-witness"></a><span data-ttu-id="8ed2d-111">미러링 모니터를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="8ed2d-111">To establish a witness</span></span>  
  
1.  <span data-ttu-id="8ed2d-112">미러링 모니터 서버 인스턴스에 데이터베이스 미러링을 위한 하나의 엔드포인트가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-112">On the witness server instance, ensure that an endpoint exists for database mirroring.</span></span> <span data-ttu-id="8ed2d-113">지원할 미러링 세션 수에 관계없이 서버 인스턴스는 데이터베이스 미러링 엔드포인트가 하나만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-113">Regardless of the number of mirroring session to be supported, the server instance must have only one database mirroring endpoint.</span></span> <span data-ttu-id="8ed2d-114">이 서버 인스턴스를 데이터베이스 미러링 세션에서 미러링 모니터로만 사용 하려면 미러링 모니터 역할을 끝점 (역할 **=** 미러링 모니터 서버)에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-114">If you intend to use this server instance exclusively as a witness in database mirroring sessions, assign the role of witness to the endpoint (ROLE **=** WITNESS).</span></span> <span data-ttu-id="8ed2d-115">이 서버 인스턴스를 하나 이상의 다른 데이터베이스 미러링 세션에서 파트너로 사용하려면 엔드포인트의 역할을 ALL로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-115">If you intend to use this server instance as a partner in one or more other database mirroring sessions, assign the role of the endpoint as ALL.</span></span>  
  
     <span data-ttu-id="8ed2d-116">SET WITNESS 문을 실행하려면 파트너 간에 데이터베이스 미러링 세션이 시작되어 있고 미러링 모니터 엔드포인트의 STATE가 STARTED로 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-116">To execute a SET WITNESS statement, the database mirroring session must already be started (between the partners), and the STATE of the endpoint of the witness must be set to STARTED.</span></span>  
  
     <span data-ttu-id="8ed2d-117">미러링 모니터 서버 인스턴스에 데이터베이스 미러링 엔드포인트가 있는지 여부와 해당 인스턴스에서의 역할 및 상태를 확인하려면 다음 Transact-SQL 문을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-117">To learn whether the witness server instance has its database mirroring endpoint and to learn its role and state, on that instance, use the following Transact-SQL statement:</span></span>  
  
    ```  
    SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8ed2d-118">데이터베이스 미러링 엔드포인트가 있으며 이미 사용 중인 경우 서버 인스턴스의 모든 세션에 이 엔드포인트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-118">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint for every session on the server instance.</span></span> <span data-ttu-id="8ed2d-119">사용 중인 엔드포인트를 삭제하면 기존 세션의 연결이 손상됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-119">Dropping an in-use endpoint disrupts the connections of the existing sessions.</span></span> <span data-ttu-id="8ed2d-120">세션에 미러링 모니터가 설정된 경우 데이터베이스 미러링 엔드포인트를 삭제하면 해당 세션의 주 서버에서 쿼럼이 손실될 수 있습니다. 이 경우 데이터베이스는 오프라인 상태가 되며 해당 사용자의 연결이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-120">If a witness has been set for a session, dropping the database mirroring endpoint can cause the principal server of that session to lose quorum; if that occurs, the database is taken offline and its users are disconnected.</span></span> <span data-ttu-id="8ed2d-121">자세한 내용은 [쿼럼: 미러링 모니터 서버가 데이터베이스 가용성에 미치는 영향&#40;데이터베이스 미러링&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-121">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="8ed2d-122">미러링 모니터 서버에 엔드포인트가 없는 경우 [Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-122">If the witness lacks an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="8ed2d-123">파트너 인스턴스가 여러 도메인 사용자 계정으로 실행되는 경우 각 인스턴스의 master 데이터베이스에서 여러 계정에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-123">If the partner instances are running under different domain user accounts, create a login for the different accounts in the master database of each instance.</span></span> <span data-ttu-id="8ed2d-124">자세한 내용은 [Windows 인증을 사용하여 데이터베이스 미러링 엔드포인트에 대한 네트워크 액세스 허용&#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-124">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
3.  <span data-ttu-id="8ed2d-125">주 서버에 연결하여 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-125">Connect to the principal server and issue the following statement:</span></span>  
  
     <span data-ttu-id="8ed2d-126">ALTER DATABASE *<database_name>* 미러링 모니터 서버 **=** _<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="8ed2d-126">ALTER DATABASE *<database_name>* SET WITNESS **=** _<server_network_address>_</span></span>  
  
     <span data-ttu-id="8ed2d-127">여기서 *<database_name>* 은 미러링할 데이터베이스의 이름(두 파트너에서 이 이름은 동일함)이고 *<server_network_address>* 는 미러링 모니터 서버 인스턴스의 서버 네트워크 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-127">where *<database_name>* is the name of the database to be mirrored (this name is the same on both partners), and *<server_network_address>* is the server network address of the witness server instance.</span></span>  
  
     <span data-ttu-id="8ed2d-128">서버 네트워크 주소 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-128">The syntax for a server network address is as follows:</span></span>  
  
     <span data-ttu-id="8ed2d-129">TCP:**//** \<_system-address> _**:**\<*port>\*</span><span class="sxs-lookup"><span data-stu-id="8ed2d-129">TCP **://**\<_system-address>_**:**\<*port>\*</span></span>  
  
     <span data-ttu-id="8ed2d-130">여기서 \<*system-address>*는 대상 컴퓨터 시스템을 명확하게 식별하는 문자열이고 \<*port>*는 파트너 서버 인스턴스의 미러링 엔드포인트에 사용되는 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-130">where \<*system-address>\* is a string that unambiguously identifies the destination computer system, and \<*port>\* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="8ed2d-131">자세햔 내용은 [서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](specify-a-server-network-address-database-mirroring.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-131">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="8ed2d-132">예를 들어 주 서버 인스턴스에서 다음 ALTER DATABASE 문은 미러링 모니터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-132">For example, on the principal server instance, the following ALTER DATABASE statement sets the witness.</span></span> <span data-ttu-id="8ed2d-133">데이터베이스 이름은 **AdventureWorks**이고 시스템 주소는 DBSERVER3(미러링 모니터 시스템의 이름)이며 미러링 모니터의 데이터베이스 미러링 엔드포인트에 사용되는 포트는 `7022`입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-133">The database name is **AdventureWorks**, the system address is DBSERVER3-the name of the witness system, and the port used by the database mirroring endpoint of the witness is `7022`:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
      SET WITNESS = 'TCP://DBSERVER3:7022'  
    ```  
  
## <a name="example"></a><span data-ttu-id="8ed2d-134">예제</span><span class="sxs-lookup"><span data-stu-id="8ed2d-134">Example</span></span>  
 <span data-ttu-id="8ed2d-135">다음 예에서는 데이터 미러링 모니터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-135">The following example establishes a data mirroring witness.</span></span> <span data-ttu-id="8ed2d-136">미러링 모니터 서버 인스턴스( `WITNESSHOST4`의 기본 인스턴스)에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-136">On the witness server instance (default instance on `WITNESSHOST4`):</span></span>  
  
1.  <span data-ttu-id="8ed2d-137">포트 `7022`만 사용하여 WITNESS 역할에 대한 이 서버 인스턴스의 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-137">Create an endpoint for this server instance for the WITNESS role only using port `7022`.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    ```  
  
2.  <span data-ttu-id="8ed2d-138">서로 다른 경우 파트너 인스턴스의 도메인 사용자 계정에 대한 로그인을 만듭니다. 예를 들어 미러링 모니터는 `SOMEDOMAIN\witnessuser`로 실행되고 있고 파트너는 `MYDOMAIN\dbousername`으로 실행되고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-138">Create a login for domain user account of partner instances, if different; for example, assume that the witness is running as `SOMEDOMAIN\witnessuser`, but the partners are running as `MYDOMAIN\dbousername`.</span></span> <span data-ttu-id="8ed2d-139">다음과 같이 파트너에 대한 로그인을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-139">Create a login for the partners, as follows:</span></span>  
  
    ```  
    --Create a login for the partner server instances,  
    --which are both running as MYDOMAIN\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [MYDOMAIN\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [MYDOMAIN\dbousername];  
    GO  
    ```  
  
3.  <span data-ttu-id="8ed2d-140">각 파트너 서버 인스턴스에서 미러링 모니터 서버 인스턴스에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-140">On each of the partner server instances, create a login for the witness server instance:</span></span>  
  
    ```  
    --Create a login for the witness server instance,  
    --which is running as SOMEDOMAIN\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [SOMEDOMAIN\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [SOMEDOMAIN\witnessuser];  
    GO  
    ```  
  
4.  <span data-ttu-id="8ed2d-141">주 서버에서 `WITNESSHOST4`에 있는 미러링 모니터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-141">On the principal server, set the witness (which is on `WITNESSHOST4`):</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4:7022'  
    GO  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="8ed2d-142">서버 네트워크 주소는 포트 번호로 대상 서버 인스턴스를 나타내며, 대상 서버 인스턴스는 인스턴스의 미러링 엔드포인트로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-142">The server network address indicates the target server instance by the port number, which maps to the mirroring endpoint of the instance.</span></span>  
  
 <span data-ttu-id="8ed2d-143">보안 설정 표시, 미러 데이터베이스 준비, 파트너 설정 및 미러링 모니터 서버 추가 등의 작업을 수행하는 전체 예제는 [데이터베이스 미러링 설정&#40;SQL Server&#41;](database-mirroring-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ed2d-143">For a complete example showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed2d-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ed2d-144">See Also</span></span>  
 <span data-ttu-id="8ed2d-145">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8ed2d-145">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="8ed2d-146">[Windows 인증을 사용하여 데이터베이스 미러링 엔드포인트에 대한 네트워크 액세스 허용&#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="8ed2d-146">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span></span>  
 <span data-ttu-id="8ed2d-147">[Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="8ed2d-147">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="8ed2d-148">[Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="8ed2d-148">[Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md) </span></span>  
 <span data-ttu-id="8ed2d-149">[데이터베이스 미러링 세션에서 미러링 모니터 서버 제거&#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8ed2d-149">[Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="8ed2d-150">데이터베이스 미러링 모니터 서버</span><span class="sxs-lookup"><span data-stu-id="8ed2d-150">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
