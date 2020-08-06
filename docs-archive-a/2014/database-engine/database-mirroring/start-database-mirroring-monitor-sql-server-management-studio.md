---
title: 데이터베이스 미러링 모니터 시작(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- Database Mirroring Monitor [SQL Server], starting
- database mirroring [SQL Server], monitoring
ms.assetid: 53165335-97ca-4f88-8e78-22f1839dee98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67c7b393b28d4d400535281c18c637146a5d8da7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638990"
---
# <a name="start-database-mirroring-monitor-sql-server-management-studio"></a><span data-ttu-id="6b272-102">데이터베이스 미러링 모니터 시작(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6b272-102">Start Database Mirroring Monitor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6b272-103">데이터베이스 미러링 모니터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 시작한 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]모니터의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-103">The Database Mirroring Monitor is part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Monitor, which is launched from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b272-104">일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서는 데이터베이스 미러링 모니터를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-104">Database Mirroring Monitor is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6b272-105">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b272-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
### <a name="to-launch-the-database-mirroring-monitor"></a><span data-ttu-id="6b272-106">데이터베이스 미러링 모니터를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="6b272-106">To launch the Database Mirroring Monitor</span></span>  
  
1.  <span data-ttu-id="6b272-107">주 서버 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-107">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="6b272-108">**데이터베이스**를 확장하고 모니터링할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-108">Expand **Databases**, and select the database to be monitored.</span></span>  
  
3.  <span data-ttu-id="6b272-109">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 선택한 다음 **데이터베이스 미러링 모니터 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-109">Right-click the database, select **Tasks**, and then click **Launch Database Mirroring Monitor**.</span></span>  
  
4.  <span data-ttu-id="6b272-110">**데이터베이스 미러링 모니터** 대화 상자에서 **미러된 데이터베이스 등록** 을 클릭하여 미러된 데이터베이스를 하나 이상 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-110">In the **Database Mirroring Monitor** dialog box, click **Register Mirrored Database** to register one or more mirrored database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b272-111">한 파트너에서 데이터베이스를 등록하면 다른 파트너에서 해당 데이터베이스가 자동으로 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-111">When you register a database at one partner, the database is automatically registered at the other partner.</span></span> <span data-ttu-id="6b272-112">모니터에 이미 다른 파트너 인스턴스에 대한 연결 자격 증명이 있으면 연결 시 해당 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-112">If the monitor already has connection credentials for the other partner instance, those are used to connect.</span></span> <span data-ttu-id="6b272-113">그렇지 않으면 모니터는 Windows 인증을 사용하여 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-113">Otherwise the monitor attempts to connect using Windows Authentication.</span></span> <span data-ttu-id="6b272-114">서버 인스턴스 중 하나에 연결하는 데 사용되는 자격 증명을 변경하려는 경우 **[확인]을 클릭할 때 [서버 연결 관리] 대화 상자 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6b272-114">If you want to change the credentials used to connect to either server instance, click **Show the Manage Server Connections dialog box when I click OK**.</span></span>  
  
 <span data-ttu-id="6b272-115">데이터베이스 미러링 모니터에 대한 자세한 내용은 [데이터베이스 미러링 모니터 개요](database-mirroring-monitor-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b272-115">For more information about Database Mirroring Monitor, see [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b272-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b272-116">See Also</span></span>  
 <span data-ttu-id="6b272-117">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6b272-117">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="6b272-118">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6b272-118">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
  
