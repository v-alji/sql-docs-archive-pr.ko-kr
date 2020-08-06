---
title: 주 서버 인스턴스(데이터베이스 미러링 보안 구성 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.principalsrvr.f1
ms.assetid: 58af27d7-c5dd-4669-be6b-b472bc2c8ef4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2632b5ffd5355065b4b5c1f905b3b6e5c5b6204d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733100"
---
# <a name="principal-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="15565-102">주 서버 인스턴스(데이터베이스 미러링 보안 구성 마법사)</span><span class="sxs-lookup"><span data-stu-id="15565-102">Principal Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="15565-103">이 페이지를 사용하여 주 데이터베이스의 서버 인스턴스에 대한 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15565-103">Use this page to specify information about the server instance of the principal database.</span></span> <span data-ttu-id="15565-104">주 데이터베이스는 미러링 세션을 시작하는 데이터베이스의 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="15565-104">The principal database is the copy of the database that begins the mirroring session.</span></span> <span data-ttu-id="15565-105">세션이 시작된 후 주 데이터베이스는 사용자 변경 내용을 받아들이는 데이터베이스의 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="15565-105">After the session has begun, the principal database is the copy of the database that accepts user changes.</span></span> <span data-ttu-id="15565-106">장애 조치(Failover)가 일어나면 주 역할과 미러링 역할이 서로 바뀌므로 처음의 주 데이터베이스가 주 데이터베이스로 유지되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15565-106">(When a failover occurs, the principal and mirroring roles are swapped; therefore, the initial principal database might not remain the principal database.)</span></span>  
  
 <span data-ttu-id="15565-107">**SQL Server Management Studio를 사용하여 데이터베이스 미러링을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="15565-107">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="15565-108">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="15565-108">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="15565-109">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="15565-109">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="15565-110">옵션</span><span class="sxs-lookup"><span data-stu-id="15565-110">Options</span></span>  
 <span data-ttu-id="15565-111">**주 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="15565-111">**Principal server instance**</span></span>  
 <span data-ttu-id="15565-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 의 데이터베이스 미러링은 항상 주 서버에서 구성하기 때문에 현재 서버 인스턴스는 항상 주 서버 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="15565-112">Because database mirroring in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is always configured from the principal server, the current server instance is always the principal server instance.</span></span>  
  
 <span data-ttu-id="15565-113">**수신기 포트**</span><span class="sxs-lookup"><span data-stu-id="15565-113">**Listener Port**</span></span>  
 <span data-ttu-id="15565-114">이 서버 인스턴스의 미러링 엔드포인트가 있는지 여부에 따라 이 옵션의 동작은 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="15565-114">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="15565-115">이 서버 인스턴스에 대한 수신기 포트가 없으면 **포트** 입력란에 포트 번호 5022가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15565-115">If the listener port does not exist for this server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="15565-116">7022와 같은 사용 가능한 임의의 포트 번호를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15565-116">You can use any available port number, such as, 7022.</span></span>  
  
-   <span data-ttu-id="15565-117">미러링 엔드포인트가 있으면 해당 엔드포인트의 포트 번호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15565-117">When the mirroring endpoint already exists, the port number from the endpoint is displayed.</span></span> <span data-ttu-id="15565-118">포트를 변경해야 하는 경우 ALTER ENDPOINT 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15565-118">If you need to change the port, use an ALTER ENDPOINT command.</span></span> <span data-ttu-id="15565-119">자세한 내용은 [ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15565-119">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15565-120">포트 번호는 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15565-120">A port number is required.</span></span>  
  
 <span data-ttu-id="15565-121">**끝점 이름**</span><span class="sxs-lookup"><span data-stu-id="15565-121">**Endpoint name**</span></span>  
 <span data-ttu-id="15565-122">이 서버 인스턴스의 미러링 엔드포인트가 있으면 여기에 엔드포인트 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15565-122">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="15565-123">엔드포인트가 없으면 엔드포인트 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15565-123">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="15565-124">**이 엔드포인트로 보낸 데이터 암호화**</span><span class="sxs-lookup"><span data-stu-id="15565-124">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="15565-125">암호화는 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="15565-125">By default, encryption is enabled.</span></span> <span data-ttu-id="15565-126">확인란을 선택하면 암호화가 단순히 지원되는 차원을 넘어 필수 항목이 되며 모든 암호화 옵션에 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15565-126">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="15565-127">자세한 내용은 [CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)과 함께 작동하도록 Service Broker를 구성하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15565-127">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="15565-128">암호화를 사용하지 않으려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="15565-128">To disable encryption, clear the check box.</span></span> <span data-ttu-id="15565-129">암호화를 다시 사용하려면 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15565-129">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15565-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15565-130">See Also</span></span>  
 <span data-ttu-id="15565-131">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15565-131">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="15565-132">[데이터베이스 속성&#40;미러링 페이지&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="15565-132">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="15565-133">[Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="15565-133">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="15565-134">[데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="15565-134">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="15565-135">데이터베이스 미러링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="15565-135">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
