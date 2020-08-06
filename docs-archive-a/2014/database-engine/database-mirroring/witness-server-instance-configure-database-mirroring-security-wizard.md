---
title: 미러링 모니터 서버 인스턴스(데이터베이스 미러링 보안 구성 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.witnsrvr.f1
ms.assetid: b5763663-984a-473b-93a3-6cd3322ad41c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fcea7d39e1bc2c6161b5c6e1edd4852d9fdeb073
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648563"
---
# <a name="witness-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="b5c4e-102">미러링 모니터 서버 인스턴스(데이터베이스 미러링 보안 구성 마법사)</span><span class="sxs-lookup"><span data-stu-id="b5c4e-102">Witness Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="b5c4e-103">이 페이지를 사용하여 세션의 미러링을 모니터링하는 서버 인스턴스에 대한 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-103">Use this page to specify information about the server instance that is to serve as the witness for the session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5c4e-104">미러링 모니터 서버 인스턴스는 일부 버전의 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-104">A witness server instance is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b5c4e-105">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="b5c4e-106">**SQL Server Management Studio를 사용하여 데이터베이스 미러링을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="b5c4e-106">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="b5c4e-107">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b5c4e-107">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="b5c4e-108">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b5c4e-108">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="b5c4e-109">옵션</span><span class="sxs-lookup"><span data-stu-id="b5c4e-109">Options</span></span>  
 <span data-ttu-id="b5c4e-110">**미러링 모니터 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="b5c4e-110">**Witness server instance**</span></span>  
 <span data-ttu-id="b5c4e-111">**데이터베이스 속성** 대화 상자의 **미러링** 페이지에 미러링 모니터 서버 인스턴스가 이미 지정되어 있으면 해당 인스턴스가 표시됩니다(자세한 내용은 [데이터베이스 속성&#40;미러링 페이지&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="b5c4e-111">If a witness server instance is already specified (on the **Mirroring** page of the **Database Properties** dialog box), that instance is displayed (for more information, see [Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)).</span></span>  
  
 <span data-ttu-id="b5c4e-112">미러링 모니터 서버 인스턴스가 지정되어 있지 않으면 목록 상자에 현재 서버의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-112">Otherwise, this list box displays the name of the current server.</span></span> <span data-ttu-id="b5c4e-113">주 서버 인스턴스 또는 미러 서버 인스턴스는 미러링 모니터 서버 인스턴스로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-113">Be aware that the witness server instance cannot be the same as the principal or mirror server instances.</span></span>  
  
 <span data-ttu-id="b5c4e-114">**연결**</span><span class="sxs-lookup"><span data-stu-id="b5c4e-114">**Connect**</span></span>  
 <span data-ttu-id="b5c4e-115">미러링 모니터 서버 인스턴스가 지정되어 있지 않으면 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-115">If a witness server instance has not been specified, click **Connect**.</span></span> <span data-ttu-id="b5c4e-116">그러면 서버 인스턴스를 지정하고 연결할 수 있는 **서버에 연결** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-116">This displays the **Connect to Server** dialog box in which you can specify the server instance and establish a connection.</span></span>  
  
 <span data-ttu-id="b5c4e-117">인스턴스를 지정했지만 엔드포인트가 있는지 확인할 수 있는 권한을 가진 연결이 없을 경우 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-117">If the instance has been specified, but the wizard lacks a connection with sufficient permission to check for the existence of the endpoint, click **Connect**.</span></span> <span data-ttu-id="b5c4e-118">그러면 서버 인스턴스가 미리 선택되어 있고 변경할 수 없는 **서버에 연결** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-118">This displays the **Connect to Server** dialog box with the server instance pre-selected and unchangeable.</span></span> <span data-ttu-id="b5c4e-119">충분한 사용 권한을 가진 도메인 계정을 지정하고 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-119">Specify a domain account with sufficient permission, and connect to the server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5c4e-120">데이터베이스 미러링 보안 구성 마법사는 서버 인스턴스에 연결할 때 **서버에 연결** 대화 상자에서 지정한 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-120">When connecting to the server instance, the Configure Database Mirroring Security Wizard uses the credentials provided in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="b5c4e-121">이 자격 증명은 서버 인스턴스가 서비스로 실행 중인 시작 계정의 자격 증명을 사용하는 미러링 세션의 자격 증명과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-121">These are different from the credentials of a mirroring session, which uses the credentials of the startup account where the server instance is running as a service.</span></span>  
  
 <span data-ttu-id="b5c4e-122">**수신기 포트**</span><span class="sxs-lookup"><span data-stu-id="b5c4e-122">**Listener Port**</span></span>  
 <span data-ttu-id="b5c4e-123">이 서버 인스턴스의 미러링 엔드포인트가 있는지 여부에 따라 이 옵션의 동작은 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-123">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="b5c4e-124">이 서버 인스턴스에 대한 수신기 포트가 없으면 **포트** 입력란에 포트 번호 5022가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-124">If the listener port does not exist for the server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="b5c4e-125">7022와 같은 사용 가능한 임의의 포트 번호를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-125">You can enter any available port number, such as, 7022.</span></span>  
  
-   <span data-ttu-id="b5c4e-126">미러링 엔드포인트가 있으면 해당 엔드포인트의 포트 번호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-126">When the mirroring endpoint already exists, the port number from the endpoint is displayed.</span></span> <span data-ttu-id="b5c4e-127">포트를 변경해야 하는 경우 ALTER ENDPOINT 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-127">If you need to change that port, use an ALTER ENDPOINT statement.</span></span> <span data-ttu-id="b5c4e-128">자세한 내용은 [ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-128">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b5c4e-129">포트 번호는 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-129">A port number is required.</span></span>  
  
 <span data-ttu-id="b5c4e-130">**끝점 이름**</span><span class="sxs-lookup"><span data-stu-id="b5c4e-130">**Endpoint name**</span></span>  
 <span data-ttu-id="b5c4e-131">이 서버 인스턴스의 미러링 엔드포인트가 있으면 여기에 엔드포인트 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-131">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="b5c4e-132">엔드포인트가 없으면 엔드포인트 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-132">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="b5c4e-133">**이 엔드포인트로 보낸 데이터 암호화**</span><span class="sxs-lookup"><span data-stu-id="b5c4e-133">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="b5c4e-134">암호화는 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-134">By default, encryption is enabled.</span></span> <span data-ttu-id="b5c4e-135">확인란을 선택하면 암호화가 단순히 지원되는 차원을 넘어 필수 항목이 되며 모든 암호화 옵션에 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-135">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="b5c4e-136">자세한 내용은 [CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)과 함께 작동하도록 Service Broker를 구성하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-136">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="b5c4e-137">암호화를 사용하지 않으려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-137">To disable encryption, clear the check box.</span></span> <span data-ttu-id="b5c4e-138">암호화를 다시 사용하려면 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c4e-138">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c4e-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5c4e-139">See Also</span></span>  
 <span data-ttu-id="b5c4e-140">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b5c4e-140">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="b5c4e-141">[데이터베이스 속성&#40;미러링 페이지&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="b5c4e-141">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="b5c4e-142">[Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="b5c4e-142">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="b5c4e-143">[데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b5c4e-143">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="b5c4e-144">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b5c4e-144">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="b5c4e-145">데이터베이스 미러링 모니터 서버</span><span class="sxs-lookup"><span data-stu-id="b5c4e-145">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
