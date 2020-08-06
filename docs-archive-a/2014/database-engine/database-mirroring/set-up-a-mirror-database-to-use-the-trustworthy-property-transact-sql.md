---
title: Trustworthy 속성을 사용하도록 미러 데이터베이스 설정(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database option
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6cd46a08037bcb6eee178a96d84bdab358e5350d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733048"
---
# <a name="set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql"></a><span data-ttu-id="93394-102">Trustworthy 속성을 사용하도록 미러 데이터베이스 설정(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="93394-102">Set Up a Mirror Database to Use the Trustworthy Property (Transact-SQL)</span></span>
  <span data-ttu-id="93394-103">데이터베이스를 백업하면 TRUSTWORTHY 데이터베이스 속성이 OFF로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="93394-103">When a database is backed up, the TRUSTWORTHY database property is set to OFF.</span></span> <span data-ttu-id="93394-104">따라서 새 미러 데이터베이스의 TRUSTWORTHY는 항상 OFF입니다.</span><span class="sxs-lookup"><span data-stu-id="93394-104">Therefore, on a new mirror database TRUSTWORTHY is always OFF.</span></span> <span data-ttu-id="93394-105">장애 조치(Failover) 후 데이터베이스를 신뢰할 수 있어야 하는 경우에는 미러링이 시작된 다음 추가 설정 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="93394-105">If the database needs to be trustworthy after a failover, extra setup steps are necessary after mirroring begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93394-106">이 데이터베이스 속성에 대한 자세한 내용은 [TRUSTWORTHY 데이터베이스 속성](../../relational-databases/security/trustworthy-database-property.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93394-106">For information about this database property, see [TRUSTWORTHY Database Property](../../relational-databases/security/trustworthy-database-property.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="93394-107">절차</span><span class="sxs-lookup"><span data-stu-id="93394-107">Procedure</span></span>  
  
#### <a name="to-setup-a-mirror-database-to-use-the-trustworthy-property"></a><span data-ttu-id="93394-108">Trustworthy 속성을 사용하도록 미러 데이터베이스를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="93394-108">To setup a mirror database to use the Trustworthy Property</span></span>  
  
1.  <span data-ttu-id="93394-109">주 서버 인스턴스에서 주 데이터베이스의 Trustworthy 속성이 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="93394-109">On the principal server instance, verify that the principal database has the Trustworthy property turned on.</span></span>  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     <span data-ttu-id="93394-110">자세한 내용은 [sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93394-110">For more information, see [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).</span></span>  
  
2.  <span data-ttu-id="93394-111">미러링을 시작한 후 데이터베이스가 현재 주 데이터베이스이고 세션에서 동기 운영 모드를 사용 중이며 세션이 이미 동기화되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="93394-111">After starting mirroring, verify that the database is currently the principal database, the session is using a synchronous operating mode, and the session is already synchronized.</span></span>  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     <span data-ttu-id="93394-112">자세한 내용은 [sys.database_mirroring&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93394-112">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
3.  <span data-ttu-id="93394-113">미러링 세션이 동기화되면 수동으로 미러 데이터베이스에 대한 장애 조치를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="93394-113">Once the mirroring session is synchronized, manually fail over to the mirror database.</span></span>  
  
     <span data-ttu-id="93394-114">SQL Server Management Studio 또는 Transact-SQL을 사용하여 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93394-114">This can be done in either SQL Server Management Studio or using Transact-SQL:</span></span>  
  
    -   [<span data-ttu-id="93394-115">데이터베이스 미러링 세션 수동 장애 조치(failover)&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="93394-115">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="93394-116">데이터베이스 미러링 세션 수동 장애 조치(failover)&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93394-116">Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  <span data-ttu-id="93394-117">다음 ALTER DATABASE 명령을 사용하여 Trustworthy 데이터베이스 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="93394-117">Turn on the trustworthy database property using the following ALTER DATABASE command:</span></span>  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     <span data-ttu-id="93394-118">자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93394-118">For more information, see[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
5.  <span data-ttu-id="93394-119">필요에 따라 수동으로 다시 장애 조치를 수행하여 원래 주 서버로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="93394-119">Optionally, manually failover again to return to the original principal.</span></span>  
  
6.  <span data-ttu-id="93394-120">필요에 따라 SAFETY를 OFF로 설정하고 WITNESS도 OFF로 설정되었는지 확인하여 비동기 성능 우선 모드로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="93394-120">Optionally, switch to asynchronous, high-performance mode by setting SAFETY to OFF and ensuring that WITNESS is also set to OFF.</span></span>  
  
     <span data-ttu-id="93394-121">Transact-SQL을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="93394-121">In Transact-SQL:</span></span>  
  
    -   [<span data-ttu-id="93394-122">데이터베이스 미러링 세션에서 트랜잭션 보안 변경&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93394-122">Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [<span data-ttu-id="93394-123">데이터베이스 미러링 세션에서 미러링 모니터 서버 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="93394-123">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     <span data-ttu-id="93394-124">SQL Server Management Studio를 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="93394-124">In SQL Server Management Studio:</span></span>  
  
    -   [<span data-ttu-id="93394-125">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="93394-125">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="93394-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93394-126">See Also</span></span>  
 <span data-ttu-id="93394-127">[TRUSTWORTHY 데이터베이스 속성](../../relational-databases/security/trustworthy-database-property.md) </span><span class="sxs-lookup"><span data-stu-id="93394-127">[TRUSTWORTHY Database Property](../../relational-databases/security/trustworthy-database-property.md) </span></span>  
 [<span data-ttu-id="93394-128">암호화된 미러 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="93394-128">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
  
