---
title: 데이터베이스 미러링 세션 수동 장애 조치(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 4ecf9c63-b3a4-4c54-b553-5bc37973232b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f7f4547058b2dfd4229142dca73a7d9b4bdb239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742556"
---
# <a name="manually-fail-over-a-database-mirroring-session-sql-server-management-studio"></a><span data-ttu-id="da2b1-102">데이터베이스 미러링 세션 수동 장애 조치(failover)(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="da2b1-102">Manually Fail Over a Database Mirroring Session (SQL Server Management Studio)</span></span>
  <span data-ttu-id="da2b1-103">미러된 데이터베이스가 동기화되면, 즉 데이터베이스가 SYNCHRONIZED 상태인 경우 데이터베이스 소유자가 미러 서버에 수동 장애 조치(failover)를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-103">When the mirrored database is synchronized (that is, when the database is in the SYNCHRONIZED state), the database owner can initiate manual failover to the mirror server.</span></span>  
  
 <span data-ttu-id="da2b1-104">수동 장애 조치 중에는 장애 조치가 발생하는 데이터베이스에 대해 주 서버와 미러 서버 역할이 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-104">During a manual failover, the principal and mirror server roles are swapped for the database on which the failover occurs.</span></span> <span data-ttu-id="da2b1-105">미러 데이터베이스는 주 데이터베이스가 되고 주 데이터베이스는 미러 데이터베이스가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-105">The mirror database becomes the principal database and the principal database becomes the mirror.</span></span> <span data-ttu-id="da2b1-106">예를 들어, 다음 표에서는 수동 장애 조치가 두 개의 미러링 파트너인 `SQLDBENGINE0_1` 및 `SQLDBENGINE0_2`의 역할을 바꾸는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-106">For example, the following table shows the how a manual failover swaps the roles of two mirroring partners: `SQLDBENGINE0_1` and `SQLDBENGINE0_2`.</span></span>  
  
|<span data-ttu-id="da2b1-107">서버</span><span class="sxs-lookup"><span data-stu-id="da2b1-107">Server</span></span>|<span data-ttu-id="da2b1-108">장애 조치(failover) 전</span><span class="sxs-lookup"><span data-stu-id="da2b1-108">Before failover</span></span>|<span data-ttu-id="da2b1-109">장애 조치(failover) 후</span><span class="sxs-lookup"><span data-stu-id="da2b1-109">After failover</span></span>|  
|------------|---------------------|--------------------|  
|`SQLDBENGINE0_1`|<span data-ttu-id="da2b1-110">PRINCIPAL</span><span class="sxs-lookup"><span data-stu-id="da2b1-110">PRINCIPAL</span></span>|<span data-ttu-id="da2b1-111">MIRROR</span><span class="sxs-lookup"><span data-stu-id="da2b1-111">MIRROR</span></span>|  
|`SQLDBENGINE0_2`|<span data-ttu-id="da2b1-112">MIRROR</span><span class="sxs-lookup"><span data-stu-id="da2b1-112">MIRROR</span></span>|<span data-ttu-id="da2b1-113">PRINCIPAL</span><span class="sxs-lookup"><span data-stu-id="da2b1-113">PRINCIPAL</span></span>|  
  
 <span data-ttu-id="da2b1-114">다른 데이터베이스 미러링 세션의 서버 역할은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-114">Note that the server roles for other database mirroring sessions are not affected.</span></span> <span data-ttu-id="da2b1-115">자세한 내용은 [데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-115">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
### <a name="to-manually-fail-over-database-mirroring"></a><span data-ttu-id="da2b1-116">데이터베이스 미러링에 수동으로 장애 조치를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="da2b1-116">To manually fail over database mirroring</span></span>  
  
1.  <span data-ttu-id="da2b1-117">주 서버 인스턴스에 연결한 다음 **개체 탐색기** 창에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-117">Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="da2b1-118">**데이터베이스**를 확장하고 장애 조치를 수행할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-118">Expand **Databases**, and select the database to be failed over.</span></span>  
  
3.  <span data-ttu-id="da2b1-119">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 선택한 다음 **미러**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-119">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="da2b1-120">**데이터베이스 속성** 대화 상자의 **미러링** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-120">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="da2b1-121">**장애 조치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-121">Click **Failover**.</span></span>  
  
     <span data-ttu-id="da2b1-122">확인 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-122">A confirmation box appears.</span></span>  <span data-ttu-id="da2b1-123">먼저 주 서버가 Windows 인증을 사용하여 미러 서버에 대한 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-123">The principal server begins by trying to connect to the mirror server by using Windows Authentication.</span></span> <span data-ttu-id="da2b1-124">Windows 인증을 사용할 수 없는 경우 주 서버는 **서버에 연결** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-124">If Windows Authentication does not work, the principal server displays the **Connect to Server** dialog box.</span></span> <span data-ttu-id="da2b1-125">미러 서버가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 **인증** 상자에서 **SQL Server 인증** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-125">If the mirror server uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, select **SQL Server Authentication** in the **Authentication** box.</span></span> <span data-ttu-id="da2b1-126">**로그인** 입력란에 미러 서버에서 연결에 사용할 로그인 계정을 지정하고 **암호** 입력란에 해당 계정의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-126">In the **Login** text box, specify the login account to connect with on the mirror server, and in the **Password** text box, specify the password for that account.</span></span>  
  
     <span data-ttu-id="da2b1-127">장애 조치가 성공할 경우 **데이터베이스 속성** 대화 상자가 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-127">If failover succeeds, the **Database Properties** dialog box closes.</span></span> <span data-ttu-id="da2b1-128">미러 데이터베이스는 주 데이터베이스가 되고 주 데이터베이스는 미러 데이터베이스가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-128">The mirror database becomes the principal database and the principal database becomes the mirror.</span></span>  
  
     <span data-ttu-id="da2b1-129">장애 조치가 실패할 경우 오류 메시지가 표시되고 대화 상자는 열린 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-129">If failover fails, an error message is displayed and the dialog box remains open.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="da2b1-130">**미러링** 페이지를 연 이후 속성을 수정한 경우에는 해당 변경 내용이 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-130">If you have modified any properties since opening the **Mirroring** page, those changes will not be saved.</span></span>  
  
     <span data-ttu-id="da2b1-131">대화 상자가 자동으로 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="da2b1-131">The dialog box closes automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da2b1-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da2b1-132">See Also</span></span>  
 <span data-ttu-id="da2b1-133">[데이터베이스 속성&#40;미러링 페이지&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="da2b1-133">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="da2b1-134">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="da2b1-134">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="da2b1-135">[데이터베이스 미러링 세션 수동 장애 조치&#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="da2b1-135">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="da2b1-136">[데이터베이스 미러링 세션 일시 중지 또는 재개&#40;SQL Server&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="da2b1-136">[Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="da2b1-137">데이터베이스 미러링 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="da2b1-137">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
  
