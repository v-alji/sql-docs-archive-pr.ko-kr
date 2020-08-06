---
title: 여러 TCP 포트에서 수신 대기하도록 데이터베이스 엔진 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- ports [SQL Server], multiple
- TDS
- listen on multiple ports
- endpoints [SQL Server], TDS
- adding ports
- tabular data stream
- multiple ports
ms.assetid: 8e955033-06ef-403f-b813-3d8241b62f1f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab803bcaa5ab6b6187c1a994abef02f81ae105c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647237"
---
# <a name="configure-the-database-engine-to-listen-on-multiple-tcp-ports"></a><span data-ttu-id="e16da-102">여러 TCP 포트에서 수신하도록 데이터베이스 엔진 구성</span><span class="sxs-lookup"><span data-stu-id="e16da-102">Configure the Database Engine to Listen on Multiple TCP Ports</span></span>
  <span data-ttu-id="e16da-103">이 항목에서는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 여러 TCP 포트로 수신하도록 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-103">This topic describes how to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on multiple TCP ports in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="e16da-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 TCP/IP가 설정된 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)]은 IP 주소와 TCP 포트 번호로 구성된 연결 지점에서 들어오는 연결을 수신합니다. 다음 절차에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 추가 TCP 포트에서 수신할 수 있도록 TDS(Tabular Data Stream) 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-104">When TCP/IP is enabled for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will listen for incoming connections on a connection point consisting of an IP address and TCP port number.The following procedures create a tabular data stream (TDS) endpoint, so that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will listen on an additional TCP port.</span></span>  
  
 <span data-ttu-id="e16da-105">두 번째 TDS 엔드포인트를 만드는 이유는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-105">Possible reasons to create a second TDS endpoint include:</span></span>  
  
-   <span data-ttu-id="e16da-106">특정 서브넷 상에서 로컬 클라이언트 컴퓨터의 기본 엔드포인트에 대한 액세스를 제한하도록 방화벽을 구성하여 보안을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-106">Increase security by configuring the firewall to restrict access to the default endpoint to local client computers on a specific subnet.</span></span> <span data-ttu-id="e16da-107">방화벽이 인터넷에 노출시키는 새로운 엔드포인트를 만들고 이 엔드포인트에 대한 연결 권한을 해당 서버 지원 팀으로만 제한하여 지원 팀이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 인터넷으로 액세스할 수 있도록 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-107">Maintain Internet access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for your support team by creating a new endpoint that the firewall exposes to the Internet, and restricting connection rights to this endpoint to your server support team.</span></span>  
  
-   <span data-ttu-id="e16da-108">NUMA(Non-Uniform Memory Access)를 사용할 때 특정 프로세서에 대한 연결의 선호도를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-108">Affinitizing connections to specific processors when using Non-Uniform Memory Access (NUMA).</span></span>  
  
 <span data-ttu-id="e16da-109">TDS 엔드포인트 구성은 실행 순서에 관계없이 다음 단계들로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-109">Configuring a TDS endpoint consists of the following steps, which can be done in any order:</span></span>  
  
-   <span data-ttu-id="e16da-110">TCP 포트에 대한 TDS 엔드포인트를 만들고 적합한 경우 기본 엔드포인트에 대한 액세스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-110">Create the TDS endpoint for the TCP port, and restore access to the default endpoint if appropriate.</span></span>  
  
-   <span data-ttu-id="e16da-111">원하는 서버 보안 주체에 엔드포인트에 대한 액세스를 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-111">Grant access to the endpoint to the desired server principals.</span></span>  
  
-   <span data-ttu-id="e16da-112">선택한 IP 주소에 대한 TCP 포트 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-112">Specify the TCP port number for the selected IP address.</span></span>  
  
 <span data-ttu-id="e16da-113">기본 Windows 방화벽 설정 방법과 데이터베이스 엔진, Analysis Services, Reporting Services 및 Integration Services에 영향을 주는 TCP 포트에 대한 설명은 [SQL Server 액세스를 허용하도록 Windows 방화벽 구성](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e16da-113">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-create-a-tds-endpoint"></a><span data-ttu-id="e16da-114">TDS 엔드포인트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="e16da-114">To create a TDS endpoint</span></span>  
  
-   <span data-ttu-id="e16da-115">다음 문을 실행하여 서버에서 사용 가능한 모든 TCP 주소에 대해 포트 1500의 **CustomConnection** 이라는 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-115">Issue the following statement to create an endpoint named **CustomConnection** for port 1500 for all available TCP addresses on the server.</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE ENDPOINT [CustomConnection]  
    STATE = STARTED  
    AS TCP  
       (LISTENER_PORT = 1500, LISTENER_IP =ALL)  
    FOR TSQL() ;  
    GO  
    ```  
  
 <span data-ttu-id="e16da-116">새로운 [!INCLUDE[tsql](../../includes/tsql-md.md)] 엔드포인트를 만들 때 **public** 에 대한 연결 권한은 기본 TDS 엔드포인트에 대해 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-116">When you create a new [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoint, connect permissions for **public** are revoked for the default TDS endpoint.</span></span> <span data-ttu-id="e16da-117">**public** 그룹에 대한 액세스에 기본 엔드포인트가 필요한 경우 `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` 문을 사용하여 이 권한을 다시 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-117">If access to the **public** group is needed for the default endpoint, reapply this permission by using the `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` statement.</span></span>  
  
#### <a name="to-grant-access-to-the-endpoint"></a><span data-ttu-id="e16da-118">엔드포인트에 액세스를 부여하려면</span><span class="sxs-lookup"><span data-stu-id="e16da-118">To grant access to the endpoint</span></span>  
  
-   <span data-ttu-id="e16da-119">다음 문을 실행하여 **CustomConnection** 엔드포인트에 대한 액세스를 회사 도메인의 SQLSupport 그룹에 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-119">Issue the following statement to grant access to the **CustomConnection** endpoint to the SQLSupport group in the corp domain.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[CustomConnection] to [corp\SQLSupport] ;  
    GO  
    ```  
  
#### <a name="to-configure-the-sql-server-database-engine-to-listen-on-an-additional-tcp-port"></a><span data-ttu-id="e16da-120">추가 TCP 포트로 수신하도록 SQL Server 데이터베이스 엔진을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="e16da-120">To configure the SQL Server Database Engine to listen on an additional TCP port</span></span>  
  
1.  <span data-ttu-id="e16da-121">SQL Server 구성 관리자에서 **SQL Server 네트워크 구성**을 확장한 다음 _<instance_name>_ **에 대한 프로토콜**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-121">In SQL Server Configuration Manager, expand **SQL Server Network Configuration**, and then click **Protocols for**_<instance_name>_.</span></span>  
  
2.  <span data-ttu-id="e16da-122">_<instance_name>_ **에 대한 프로토콜**을 확장한 다음 **TCP/IP**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-122">Expand **Protocols for**_<instance_name>_, and then click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="e16da-123">오른쪽 창에서 설정하려는 해제된 각 IP 주소를 마우스 오른쪽 단추로 클릭한 다음 **설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-123">In the right pane, right-click each disabled IP address that you want to enable, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="e16da-124">**IPAll**을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-124">Right-click **IPAll**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e16da-125">**TCP 포트** 상자에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 수신하려는 포트를 쉼표로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-125">In the **TCP Port** box, type the ports that you want the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on, separated by commas.</span></span> <span data-ttu-id="e16da-126">이 예에서는 기본 포트 1433이 표시 되는 경우 `,1500` 상자에를 입력 하 `1433,1500` 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-126">In our example, if the default port 1433 is listed, type `,1500` so the box reads `1433,1500`, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e16da-127">모든 IP 주소에 대한 포트를 설정하지 않으려면 원하는 주소에 대해서만 속성 상자에서 추가 포트로 구성하세요.</span><span class="sxs-lookup"><span data-stu-id="e16da-127">If you are not enabling the port on all IP addresses, configure the additional port in the property box for only for the desired address.</span></span> <span data-ttu-id="e16da-128">그런 다음 콘솔 창에서 **TCP/IP**를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭한 다음 **모두 수신합니다** 상자에서 **아니요**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-128">Then, in the console pane, right-click **TCP/IP**, click **Properties**, and in the **Listen All** box, select **No**.</span></span>  
  
6.  <span data-ttu-id="e16da-129">왼쪽 창에서 **SQL Server 서비스**를 클릭하고</span><span class="sxs-lookup"><span data-stu-id="e16da-129">In the left pane, click **SQL Server Services**.</span></span>  
  
7.  <span data-ttu-id="e16da-130">오른쪽 창에서 **SQL Server** _<instance_name>_ 을 마우스 오른쪽 단추로 클릭한 다음 **다시 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-130">In the right pane, right-click **SQL Server**_<instance_name>_, and then click **Restart**.</span></span>  
  
     <span data-ttu-id="e16da-131">[!INCLUDE[ssDE](../../includes/ssde-md.md)]이 다시 시작하면 오류 로그에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 수신 중인 포트 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-131">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] restarts, the Error log will list the ports on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening.</span></span>  
  
#### <a name="to-connect-to-the-new-endpoint"></a><span data-ttu-id="e16da-132">새 엔드포인트에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="e16da-132">To connect to the new endpoint</span></span>  
  
-   <span data-ttu-id="e16da-133">다음 문을 실행하여 ACCT 서버에서 SQL Server의 기본 인스턴스에 대한 **CustomConnection** 엔드포인트에 신뢰할 수 있는 연결을 사용하여 연결합니다. 이때 사용자는 [corp\SQLSupport] 그룹의 멤버인 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e16da-133">Issue the following statement to connect to the **CustomConnection** endpoint of the default instance of SQL Server on the server named ACCT, using a trusted connection, and assuming the user is a member of the [corp\SQLSupport] group.</span></span>  
  
    ```  
    sqlcmd -SACCT,1500  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e16da-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e16da-134">See Also</span></span>  
 <span data-ttu-id="e16da-135">[CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e16da-135">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="e16da-136">[DROP ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e16da-136">[DROP ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="e16da-137">[GRANT 엔드포인트 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e16da-137">[GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span></span>  
 [<span data-ttu-id="e16da-138">NUMA 노드에 TCP IP 포트 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e16da-138">Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;</span></span>](map-tcp-ip-ports-to-numa-nodes-sql-server.md)  
  
  
