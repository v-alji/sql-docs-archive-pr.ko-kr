---
title: 노출 영역 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- reducing attackable surface area
- upgrading SQL Server, security
- surface area configuration [SQL Server]
- surface area configuration [SQL Server], about surface area configuration
- attackable surface area [SQL Server]
- installing SQL Server, security
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ef64fbbeb2b8953ff3816db63572b499d42f012e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730300"
---
# <a name="surface-area-configuration"></a><span data-ttu-id="bb956-102">노출 영역 구성</span><span class="sxs-lookup"><span data-stu-id="bb956-102">Surface Area Configuration</span></span>
  <span data-ttu-id="bb956-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]새로 설치의 기본 구성에서는 많은 기능이 활성화되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-103">In the default configuration of new installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], many features are not enabled.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bb956-104">는 악의적인 사용자로부터 공격 대상이 될 수 있는 기능 수를 최소화하기 위해 주요 서비스와 기능만 필요에 따라 설치하고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-104">selectively installs and starts only key services and features, to minimize the number of features that can be attacked by a malicious user.</span></span> <span data-ttu-id="bb956-105">시스템 관리자는 설치 시 이러한 기본값을 변경할 수 있으며 필요에 따라 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 기능을 활성화 또는 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-105">A system administrator can change these defaults at installation time and also selectively enable or disable features of a running instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bb956-106">또한 다른 컴퓨터에서 연결하는 경우 일부 구성 요소는 프로토콜을 구성해야만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-106">Additionally, some components may not be available when connecting from other computers until protocols are configured.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb956-107">새로 설치와 달리 업그레이드 중에는 기존 서비스 또는 기능이 해제되지 않지만 추가 노출 영역 구성 옵션은 업그레이드가 완료된 후에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-107">Unlike new installations, no existing services or features are turned off during an upgrade, but additional surface area configuration options can be applied after the upgrade is completed.</span></span>  
  
## <a name="protocols-connection-and-startup-options"></a><span data-ttu-id="bb956-108">프로토콜, 연결 및 시작 옵션</span><span class="sxs-lookup"><span data-stu-id="bb956-108">Protocols, Connection, and Startup Options</span></span>  
 <span data-ttu-id="bb956-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 서비스를 시작/중지하고 시작 옵션을 구성하고 프로토콜 및 기타 연결 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-109">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to start and stop services, configure the startup options, and enable protocols and other connection options.</span></span>  
  
#### <a name="to-start-sql-server-configuration-manager"></a><span data-ttu-id="bb956-110">SQL Server 구성 관리자를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="bb956-110">To start SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="bb956-111">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-111">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    -   <span data-ttu-id="bb956-112">**SQL Server 서비스** 영역을 사용하여 구성 요소를 시작하고 자동 시작 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-112">Use the **SQL Server Services** area to start components and configure the automatic starting options.</span></span>  
  
    -   <span data-ttu-id="bb956-113">**SQL Server 네트워크 구성** 영역에서 연결 프로토콜, 고정 TCP/IP 포트와 같은 연결 옵션 또는 암호화 사용을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-113">Use the **SQL Server Network Configuration** area to enable connection protocols, and connection options such as fixed TCP/IP ports, or forcing encryption.</span></span>  
  
 <span data-ttu-id="bb956-114">자세한 내용은 [SQL Server Configuration Manager](../sql-server-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb956-114">For more information, see [SQL Server Configuration Manager](../sql-server-configuration-manager.md).</span></span> <span data-ttu-id="bb956-115">원격 연결도 올바른 방화벽 구성에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-115">Remote connectivity can also depend upon the correct configuration of a firewall.</span></span> <span data-ttu-id="bb956-116">자세한 내용은 [SQL Server 액세스를 허용하도록 Windows 방화벽 구성](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb956-116">For more information, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="enabling-and-disabling-features"></a><span data-ttu-id="bb956-117">기능 설정 및 해제</span><span class="sxs-lookup"><span data-stu-id="bb956-117">Enabling and Disabling Features</span></span>  
 <span data-ttu-id="bb956-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능의 설정 및 해제는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 패싯을 사용하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-118">Enabling and disabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features can be configured using facets in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-configure-surface-area-using-facets"></a><span data-ttu-id="bb956-119">패싯을 사용하여 노출 영역을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="bb956-119">To configure surface area using facets</span></span>  
  
1.  <span data-ttu-id="bb956-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-120">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] connect to a component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="bb956-121">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **패싯**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-121">In Object Explorer, right-click the server, and then click **Facets**.</span></span>  
  
3.  <span data-ttu-id="bb956-122">**패싯 보기** 대화 상자에서 **패싯** 목록을 확장하고 적절한 **노출 영역 구성** 패싯(**노출 영역 구성**, **Analysis Services에 대한 노출 영역 구성**또는 **Reporting Services에 대한 노출 영역 구성**)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-122">In the **View Facets** dialog box, expand the **Facet** list, and select the appropriate **Surface Area Configuration** facet (**Surface Area Configuration**, **Surface Area Configuration for Analysis Services**, or **Surface Area Configuration for Reporting Services**).</span></span>  
  
4.  <span data-ttu-id="bb956-123">**패싯 속성** 영역에서 각 속성에 대해 원하는 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-123">In the **Facet properties** area, select the values that you want for each property.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="bb956-124">정책 기반 관리를 사용하여 패싯 구성을 주기적으로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-124">To periodically check the configuration of a facet, use Policy-Based Management.</span></span> <span data-ttu-id="bb956-125">정책 기반 관리에 대한 자세한 내용은 [정책 기반 관리를 사용하여 서버 관리](../policy-based-management/administer-servers-by-using-policy-based-management.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb956-125">For more information about Policy-Based Management, see [Administer Servers by Using Policy-Based Management](../policy-based-management/administer-servers-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="bb956-126">`sp_configure` 저장 프로시저를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 옵션을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-126">You can also set [!INCLUDE[ssDE](../../includes/ssde-md.md)] options using the `sp_configure` stored procedure.</span></span> <span data-ttu-id="bb956-127">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-127">For more information, see [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
 <span data-ttu-id="bb956-128">**의** EnableIntegratedSecurity [!INCLUDE[ssRS](../../includes/ssrs.md)]속성을 변경하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 속성 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-128">To change the **EnableIntegrated Security** property of [!INCLUDE[ssRS](../../includes/ssrs.md)], use the property settings in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="bb956-129">**예약 이벤트 및 보고서 배달** 속성과 **웹 서비스 및 HTTP 액세스** 속성을 변경하려면 **RSReportServer.config** 구성 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-129">To change the **Schedule events and report delivery** property and the **Web service and HTTP access** property, edit the **RSReportServer.config** configuration file.</span></span>  
  
## <a name="command-prompt-options"></a><span data-ttu-id="bb956-130">명령 프롬프트 옵션</span><span class="sxs-lookup"><span data-stu-id="bb956-130">Command-prompt Options</span></span>  
 <span data-ttu-id="bb956-131">**Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell cmdlet을 사용하여 노출 영역 구성 정책을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-131">Use the **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell cmdlet to invoke Surface Area Configuration Policies.</span></span> <span data-ttu-id="bb956-132">자세한 내용은 [데이터베이스 엔진 cmdlet 사용](../../database-engine/use-the-database-engine-cmdlets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb956-132">For more information, see [Use the Database Engine cmdlets](../../database-engine/use-the-database-engine-cmdlets.md).</span></span>  
  
## <a name="soap-and-service-broker-endpoints"></a><span data-ttu-id="bb956-133">SOAP 및 Service Broker 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="bb956-133">SOAP and Service Broker Endpoints</span></span>  
 <span data-ttu-id="bb956-134">엔드포인트를 끄려면 정책 기반 관리를 사용하고</span><span class="sxs-lookup"><span data-stu-id="bb956-134">To turn endpoints off, use Policy-Based Management.</span></span> <span data-ttu-id="bb956-135">엔드포인트의 속성을 만들고 변경하려면 [CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) 및 [ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb956-135">To create and alter the properties of endpoints, use [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) and [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="bb956-136">관련 내용</span><span class="sxs-lookup"><span data-stu-id="bb956-136">Related Content</span></span>  
 [<span data-ttu-id="bb956-137">SQL Server 데이터베이스 엔진 및 Azure SQL Database 보안 센터</span><span class="sxs-lookup"><span data-stu-id="bb956-137">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [<span data-ttu-id="bb956-138">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb956-138">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
