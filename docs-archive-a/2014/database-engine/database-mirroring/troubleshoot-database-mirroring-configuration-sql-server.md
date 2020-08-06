---
title: 데이터베이스 미러링 구성 문제 해결(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- endpoints [SQL Server], database mirroring
- database mirroring [SQL Server], troubleshooting
- troubleshooting [SQL Server], database mirroring
ms.assetid: 87d3801b-dc52-419e-9316-8b1f1490946c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0dafd98f721bfc2d2d0dd64a9f97689466529407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649684"
---
# <a name="troubleshoot-database-mirroring-configuration-sql-server"></a><span data-ttu-id="63c28-102">데이터베이스 미러링 구성 문제 해결(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63c28-102">Troubleshoot Database Mirroring Configuration (SQL Server)</span></span>
  <span data-ttu-id="63c28-103">이 항목에서는 데이터베이스 미러링 세션을 설정할 때 발생하는 문제를 해결하는 데 도움이 되는 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-103">This topic provides information to help you troubleshoot problems in setting up a database mirroring session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63c28-104">[데이터베이스 미러링을 위한 선행 조건](prerequisites-restrictions-and-recommendations-for-database-mirroring.md)을 모두 충족하는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-104">Ensure that you are meeting all the [prerequisites for database mirroring](prerequisites-restrictions-and-recommendations-for-database-mirroring.md).</span></span>  
  
|<span data-ttu-id="63c28-105">문제</span><span class="sxs-lookup"><span data-stu-id="63c28-105">Issue</span></span>|<span data-ttu-id="63c28-106">요약</span><span class="sxs-lookup"><span data-stu-id="63c28-106">Summary</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="63c28-107">오류 메시지 1418</span><span class="sxs-lookup"><span data-stu-id="63c28-107">Error Message 1418</span></span>|<span data-ttu-id="63c28-108">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메시지는 서버 네트워크 주소가 없거나 도달할 수 없음을 나타내며 네트워크 주소 이름을 확인한 후 명령을 다시 실행하도록 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-108">This [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message indicates that the server network address cannot be reached or does not exist, and it suggests that you verify the network address name and reissue the command.</span></span> <span data-ttu-id="63c28-109">자세한 내용은 [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-109">For more information, see the [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md) topic.</span></span>|  
|[<span data-ttu-id="63c28-110">계정</span><span class="sxs-lookup"><span data-stu-id="63c28-110">Accounts</span></span>](#Accounts)|<span data-ttu-id="63c28-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행되고 있는 계정을 올바르게 구성하기 위한 요구 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-111">Discusses requirements for correctly configuring the accounts under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>|  
|[<span data-ttu-id="63c28-112">엔드포인트</span><span class="sxs-lookup"><span data-stu-id="63c28-112">Endpoints</span></span>](#Endpoints)|<span data-ttu-id="63c28-113">각 서버 인스턴스의 데이터베이스 미러링 엔드포인트를 올바르게 구성하기 위한 요구 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-113">Discusses requirements for correctly configuring the database mirroring endpoint of each server instance.</span></span>|  
|[<span data-ttu-id="63c28-114">SystemAddress</span><span class="sxs-lookup"><span data-stu-id="63c28-114">SystemAddress</span></span>](#SystemAddress)|<span data-ttu-id="63c28-115">데이터베이스 미러링 구성에서 서버 인스턴스의 시스템 이름을 지정하는 대체 방법을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-115">Summarizes the alternatives for specifying the system name of a server instance in a database mirroring configuration.</span></span>|  
|[<span data-ttu-id="63c28-116">네트워크 액세스</span><span class="sxs-lookup"><span data-stu-id="63c28-116">Network access</span></span>](#NetworkAccess)|<span data-ttu-id="63c28-117">각 서버 인스턴스에서 TCP를 통해 다른 서버 인스턴스의 포트에 액세스할 수 있어야 한다는 요구 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-117">Documents the requirement that each the server instance be able to access the ports of the other server instance or instances over TCP.</span></span>|  
|[<span data-ttu-id="63c28-118">미러 데이터베이스 준비</span><span class="sxs-lookup"><span data-stu-id="63c28-118">Mirror database preparation</span></span>](#MirrorDbPrep)|<span data-ttu-id="63c28-119">미러링이 시작될 수 있도록 미러 데이터베이스를 준비하기 위한 요구 사항을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-119">Summarizes the requirements for preparing the mirror database to enable mirroring to start.</span></span>|  
|[<span data-ttu-id="63c28-120">파일 생성 작업 실패</span><span class="sxs-lookup"><span data-stu-id="63c28-120">Failed create-file operation</span></span>](#FailedCreateFileOp)|<span data-ttu-id="63c28-121">파일 생성 작업이 실패할 경우의 대처 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-121">Describes how to respond to a failed create-file operation.</span></span>|  
|[<span data-ttu-id="63c28-122">Transact-SQL을 사용하여 미러링 시작</span><span class="sxs-lookup"><span data-stu-id="63c28-122">Starting mirroring by Using Transact-SQL</span></span>](#StartDbm)|<span data-ttu-id="63c28-123">ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** 문의 필요한 순서에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-123">Describes the required order for ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** statements.</span></span>|  
|[<span data-ttu-id="63c28-124">데이터베이스 간 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="63c28-124">Cross-Database Transactions</span></span>](#CrossDbTxns)|<span data-ttu-id="63c28-125">자동 장애 조치(Failover)를 사용할 경우 미결 트랜잭션이 자동으로 잘못 해결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-125">An automatic failover could lead to automatic and possibly incorrect resolution of in-doubt transactions.</span></span> <span data-ttu-id="63c28-126">이러한 이유로 데이터베이스 미러링은 데이터베이스 간 트랜잭션을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-126">For this reason database mirroring does not support cross-database transactions.</span></span>|  
  
##  <a name="accounts"></a><a name="Accounts"></a> <span data-ttu-id="63c28-127">계정</span><span class="sxs-lookup"><span data-stu-id="63c28-127">Accounts</span></span>  
 <span data-ttu-id="63c28-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 실행하고 있는 계정이 올바르게 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-128">The accounts under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running must be correctly configured.</span></span>  
  
1.  <span data-ttu-id="63c28-129">계정에 올바른 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-129">Do the accounts have the correct permissions?</span></span>  
  
    1.  <span data-ttu-id="63c28-130">계정이 동일한 도메인 계정에서 실행되는 경우 잘못 구성할 가능성이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-130">If the accounts are running in the same domain accounts, the chances of misconfiguration are reduced.</span></span>  
  
    2.  <span data-ttu-id="63c28-131">계정이 서로 다른 도메인에서 실행되거나 도메인 계정이 아닐 경우 다른 컴퓨터의 **master** 에 한 계정의 로그인을 만들고 엔드포인트에 대한 CONNECT 권한을 해당 로그인에 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-131">If the accounts are running in different domains or are not domain accounts, the login of one account must be created in **master** on the other computer, and that login must be granted CONNECT permissions on the endpoint.</span></span> <span data-ttu-id="63c28-132">자세한 내용은 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-132">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span> <span data-ttu-id="63c28-133">여기에는 네트워크 서비스 계정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-133">This includes the Network Service account.</span></span>  
  
2.  <span data-ttu-id="63c28-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 로컬 시스템 계정을 사용하는 서비스로 실행되는 경우 인증서를 사용하여 인증해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-134">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running as a service that is using the local system account, you must use certificates for authentication.</span></span> <span data-ttu-id="63c28-135">자세한 내용은 [데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-135">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
##  <a name="endpoints"></a><a name="Endpoints"></a> <span data-ttu-id="63c28-136">엔드포인트</span><span class="sxs-lookup"><span data-stu-id="63c28-136">Endpoints</span></span>  
 <span data-ttu-id="63c28-137">엔드포인트를 올바르게 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-137">Endpoints must be correctly configured.</span></span>  
  
1.  <span data-ttu-id="63c28-138">각 서버 인스턴스(주 서버, 미러 서버 및 미러링 모니터 서버)에는 데이터베이스 미러링 엔드포인트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-138">Make sure that each server instance (the principal server, mirror server, and witness, if any) has a database mirroring endpoint.</span></span> <span data-ttu-id="63c28-139">자세한 내용은 [sys.database_mirroring_endpoints&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) 및 인증 형식에 따라 [Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) 또는 [데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-139">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) and, depending on the form of authentication, either [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) or [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="63c28-140">포트 번호가 정확한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-140">Check that the port numbers are correct.</span></span>  
  
     <span data-ttu-id="63c28-141">서버 인스턴스의 데이터베이스 미러링 엔드포인트와 현재 연결된 포트를 식별하려면 [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) 및 [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) 카탈로그 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-141">To identify the port currently associated with database mirroring endpoint of a server instance, use the [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) and [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) catalog views.</span></span>  
  
3.  <span data-ttu-id="63c28-142">설명하기 어려운 데이터베이스 미러링 설치 문제의 경우 각 서버 인스턴스를 조사하여 올바른 포트에서 수신하고 있는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-142">For database mirroring setup issues that are difficult to explain, we recommend that you inspect each server instance to determine whether it is listening on the correct ports.</span></span> <span data-ttu-id="63c28-143">포트 가용성 확인에 대한 자세한 내용은 [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-143">For information about verifying port availability, see [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md).</span></span>  
  
4.  <span data-ttu-id="63c28-144">엔드포인트가 시작되었는지 확인합니다(STATE=STARTED).</span><span class="sxs-lookup"><span data-stu-id="63c28-144">Make sure that the endpoints are started (STATE=STARTED).</span></span> <span data-ttu-id="63c28-145">각 서버 인스턴스에서 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-145">On each server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
     <span data-ttu-id="63c28-146">**state_desc** 열에 대한 자세한 내용은 [sys.database_mirroring_endpoints&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-146">For more information about the **state_desc** column, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
     <span data-ttu-id="63c28-147">엔드포인트를 시작하려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-147">To start an endpoint, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    ALTER ENDPOINT Endpoint_Mirroring   
    STATE = STARTED   
    AS TCP (LISTENER_PORT = <port_number>)  
    FOR database_mirroring (ROLE = ALL);  
    GO  
    ```  
  
     <span data-ttu-id="63c28-148">자세한 내용은 [ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-148">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
5.  <span data-ttu-id="63c28-149">ROLE이 정확한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-149">Check that the ROLE is correct.</span></span> <span data-ttu-id="63c28-150">각 서버 인스턴스에서 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-150">On each server instance use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT role FROM sys.database_mirroring_endpoints;  
    GO  
    ```  
  
     <span data-ttu-id="63c28-151">자세한 내용은 [sys.database_mirroring_endpoints&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-151">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
6.  <span data-ttu-id="63c28-152">다른 서버 인스턴스에서 서비스 계정에 로그인하려면 CONNECT 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-152">The login for the service account from the other server instance requires CONNECT permission.</span></span> <span data-ttu-id="63c28-153">다른 서버에서 로그인할 경우 CONNECT 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-153">Make sure that the login from the other server has CONNECT permission.</span></span> <span data-ttu-id="63c28-154">엔드포인트에 대한 CONNECT 권한이 있는 사용자를 파악하려면 각 서버 인스턴스에서 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-154">To determine who has CONNECT permission for an endpoint, on each server instance use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT 'Metadata Check';  
    SELECT EP.name, SP.STATE,   
       CONVERT(nvarchar(38), suser_name(SP.grantor_principal_id))   
          AS GRANTOR,   
       SP.TYPE AS PERMISSION,  
       CONVERT(nvarchar(46),suser_name(SP.grantee_principal_id))   
          AS GRANTEE   
       FROM sys.server_permissions SP , sys.endpoints EP  
       WHERE SP.major_id = EP.endpoint_id  
       ORDER BY Permission,grantor, grantee;   
    GO  
  
    ```  
  
##  <a name="system-address"></a><a name="SystemAddress"></a> <span data-ttu-id="63c28-155">시스템 주소</span><span class="sxs-lookup"><span data-stu-id="63c28-155">System Address</span></span>  
 <span data-ttu-id="63c28-156">데이터베이스 미러링 구성에서 서버 인스턴스의 시스템 이름에는 시스템을 명확하게 식별하는 모든 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-156">For the system name of a server instance in a database mirroring configuration, you can use any name that unambiguously identifies the system.</span></span> <span data-ttu-id="63c28-157">서버 주소는 시스템 이름(시스템이 같은 도메인에 있는 경우), 정규화된 도메인 이름 또는 IP 주소(가급적 고정 IP 주소)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-157">The server address can be a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address (preferably, a static IP address).</span></span> <span data-ttu-id="63c28-158">정규화된 도메인 이름을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-158">Using the fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="63c28-159">자세햔 내용은 [서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](specify-a-server-network-address-database-mirroring.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-159">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
##  <a name="network-access"></a><a name="NetworkAccess"></a> <span data-ttu-id="63c28-160">Network Access</span><span class="sxs-lookup"><span data-stu-id="63c28-160">Network Access</span></span>  
 <span data-ttu-id="63c28-161">각 서버 인스턴스에서 TCP를 통해 다른 서버 인스턴스의 포트에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-161">Each server instance must be able to access the ports of the other server instance or instances over TCP.</span></span> <span data-ttu-id="63c28-162">이는 서버 인스턴스가 서로 트러스트하지 않는 다른 도메인(트러스트되지 않은 도메인)에 있을 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-162">This is especially important if the server instances are in different domains that do not trust each other (untrusted domains).</span></span> <span data-ttu-id="63c28-163">이 경우 서버 인스턴스 간의 통신은 대부분 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-163">This restricts much of the communication between the server instances.</span></span>  
  
##  <a name="mirror-database-preparation"></a><a name="MirrorDbPrep"></a> <span data-ttu-id="63c28-164">Mirror Database Preparation</span><span class="sxs-lookup"><span data-stu-id="63c28-164">Mirror Database Preparation</span></span>  
 <span data-ttu-id="63c28-165">처음으로 미러링을 시작하는 것이든 미러링을 제거한 후 다시 시작하는 것이든 관계없이 미러 데이터베이스가 미러링을 위한 준비를 완료했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-165">Whether starting mirroring for the first time or starting it again after mirroring was removed, verify that the mirror database is prepared for mirroring.</span></span>  
  
 <span data-ttu-id="63c28-166">미러 서버에 미러 데이터베이스를 만들 때는 WITH NORECOVERY로 동일한 데이터베이스 이름을 지정하여 주 데이터베이스의 백업을 복원하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-166">When you create the mirror database on the mirror server, make sure that you restore the backup of the principal database specifying the same database name WITH NORECOVERY.</span></span> <span data-ttu-id="63c28-167">백업 후에 생성된 모든 로그 백업도 WITH NORECOVERY를 사용하여 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-167">Also, all log backups created after that backup was taken must also be applied, again WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="63c28-168">또한 가능한 경우 드라이브 문자를 포함한 미러 데이터베이스의 파일 경로가 주 데이터베이스의 경로와 동일한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-168">Also, we recommend that, if it is possible, the file path (including the drive letter) of the mirror database be identical to the path of the principal database.</span></span> <span data-ttu-id="63c28-169">주 데이터베이스는 'F:' 드라이브에 있는데 미러 시스템에는 F: 드라이브가 없는 경우 등 파일 경로가 달라야 하는 경우에는 RESTORE 문에 MOVE 옵션을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-169">If the file paths must differ, for example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive, you must include the MOVE option in the RESTORE statement.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="63c28-170">미러 데이터베이스를 만들 때 데이터베이스 파일을 이동한 경우 나중에 데이터베이스에 파일을 추가하려면 미러링을 일시 중지해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-170">If you move the database files when you are creating the mirror database, you might be unable to add files to the database later without mirroring being suspended.</span></span>  
  
 <span data-ttu-id="63c28-171">데이터베이스 미러링이 중지된 경우 주 데이터베이스에서 수행된 모든 후속 로그 백업을 미러 데이터베이스에 적용해야만 미러링을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-171">If database mirroring has been stopped, all subsequent log backups taken on the principal database must be applied to the mirror database before mirroring can be restarted.</span></span>  
  
 <span data-ttu-id="63c28-172">자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-172">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
##  <a name="failed-create-file-operation"></a><a name="FailedCreateFileOp"></a> <span data-ttu-id="63c28-173">Failed Create-File Operation</span><span class="sxs-lookup"><span data-stu-id="63c28-173">Failed Create-File Operation</span></span>  
 <span data-ttu-id="63c28-174">미러링 세션에 영향을 주지 않고 파일을 추가하려면 파일의 경로가 두 서버 모두에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-174">Adding a file without impacting a mirroring session requires that the path of the file exist on both servers.</span></span> <span data-ttu-id="63c28-175">따라서 미러 데이터베이스를 만들 때 데이터베이스 파일을 이동하면 나중에 미러 데이터베이스에 파일을 추가할 수 없고 미러링이 일시 중지될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-175">Therefore, if you move the database files when creating the mirror database, a later add-file operation might fail on the mirror database and cause mirroring to be suspended.</span></span>  
  
 <span data-ttu-id="63c28-176">이 문제를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="63c28-176">To fix the problem:</span></span>  
  
1.  <span data-ttu-id="63c28-177">데이터베이스 소유자가 미러링 세션을 제거하고 추가된 파일이 들어 있는 파일 그룹의 전체 백업을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-177">The database owner must remove the mirroring session and restore a full backup of the filegroup that contains the added file.</span></span>  
  
2.  <span data-ttu-id="63c28-178">그러 다음 소유자가 주 서버에서 파일 추가 작업이 포함된 로그를 백업하고 WITH NORECOVERY 및 WITH MOVE 옵션을 사용하여 미러 데이터베이스에 로그 백업을 수동으로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-178">The owner must then back up the log containing the add-file operation on the principal server and manually restore the log backup on the mirror database using the WITH NORECOVERY and WITH MOVE options.</span></span> <span data-ttu-id="63c28-179">이렇게 하면 미러 서버에 지정된 파일 경로가 만들어지고 새 파일이 이 위치에 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-179">Doing this creates the specified file path on the mirror server and restores the new file to that location.</span></span>  
  
3.  <span data-ttu-id="63c28-180">새 미러링 세션에 대비해서 데이터베이스를 준비하려면 소유자가 주 서버에서 WITH NO RECOVERY 및 기타 처리 중인 로그 백업도 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-180">To prepare the database for a new mirroring session, the owner must also restore WITH NO RECOVERY any other outstanding log backups from the principal server.</span></span>  
  
 <span data-ttu-id="63c28-181">자세한 내용은 [데이터베이스 미러링 제거&#40;SQL Server&#41;](database-mirroring-sql-server.md), [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md), [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md), [데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) 또는 [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-181">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md), [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md), [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md), [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md), or [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
##  <a name="starting-mirroring-by-using-transact-sql"></a><a name="StartDbm"></a><span data-ttu-id="63c28-182">Transact-sql을 사용 하 여 미러링 시작</span><span class="sxs-lookup"><span data-stu-id="63c28-182">Starting mirroring by Using Transact-SQL</span></span>  
 <span data-ttu-id="63c28-183">ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** 문을 실행하는 순서는 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-183">The order in which the ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** statements are issued is very important.</span></span>  
  
1.  <span data-ttu-id="63c28-184">미러 서버에서 첫 번째 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-184">The first statement must be run on the mirror server.</span></span> <span data-ttu-id="63c28-185">이 문을 실행할 때는 미러 서버에서 다른 서버 인스턴스에 연결하지 않고</span><span class="sxs-lookup"><span data-stu-id="63c28-185">When this statement is issued, the mirror server does not try to contact any other server instance.</span></span> <span data-ttu-id="63c28-186">대신 주 서버가 미러 서버에 접속할 때까지 기다리도록 해당 데이터베이스에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-186">Instead, the mirror server instructs its database to wait until the mirror server has been contacted by the principal server.</span></span>  
  
2.  <span data-ttu-id="63c28-187">주 서버에서 두 번째 ALTER DATABASE 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-187">The second ALTER DATABASE statement must be run on the principal server.</span></span> <span data-ttu-id="63c28-188">이 문을 실행하면 주 서버가 미러 서버에 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-188">This statement causes the principal server to try to connect to the mirror server.</span></span> <span data-ttu-id="63c28-189">이 연결이 생성되면 미러 서버는 다른 연결을 통해 주 서버에 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-189">After that connection is created, the mirror then tries to connect to the principal server on another connection.</span></span>  
  
 <span data-ttu-id="63c28-190">자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-190">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63c28-191">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 미러링을 시작하는 방법은 [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-191">For information about using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to start mirroring, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
##  <a name="cross-database-transactions"></a><a name="CrossDbTxns"></a><span data-ttu-id="63c28-192">데이터베이스 간 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="63c28-192">Cross-Database Transactions</span></span>  
 <span data-ttu-id="63c28-193">자동 장애 조치(Failover) 있는 보호 우선 모드로 데이터베이스를 미러링하는 경우 자동 장애 조치로 인해 미결 트랜잭션이 자동으로 잘못 해결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-193">When a database is being mirrored in high-safety mode with automatic failover, an automatic failover could lead to automatic and possibly incorrect resolution of in-doubt transactions.</span></span> <span data-ttu-id="63c28-194">데이터베이스 간 트랜잭션을 커밋하는 동안 두 데이터베이스 중 하나에서 자동 장애 조치가 수행되면 데이터베이스 간에 논리적 불일치가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-194">If an automatic failover occurs on either database while a cross-database transaction is being committed, logical inconsistencies can occur between the databases.</span></span>  
  
 <span data-ttu-id="63c28-195">자동 장애 조치의 영향을 받을 수 있는 데이터베이스 간 트랜잭션 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="63c28-195">The types of cross-database transactions that can be affected by an automatic failover include the following:</span></span>  
  
-   <span data-ttu-id="63c28-196">동일한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 여러 데이터베이스를 업데이트하는 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="63c28-196">A transaction that is updating multiple databases in the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="63c28-197">MS DTC( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator)를 사용하는 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="63c28-197">Transactions that use a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).</span></span>  
  
 <span data-ttu-id="63c28-198">자세한 내용은 [데이터베이스 미러링 또는 AlwaysOn 가용성 그룹에 대해 지원되지 않는 데이터베이스 간 트랜잭션&#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c28-198">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c28-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63c28-199">See Also</span></span>  
 <span data-ttu-id="63c28-200">[데이터베이스 미러링 설정&#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63c28-200">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="63c28-201">데이터베이스 미러링 및 AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 전송 보안&#41;</span><span class="sxs-lookup"><span data-stu-id="63c28-201">Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](transport-security-database-mirroring-always-on-availability.md)  
  
  
