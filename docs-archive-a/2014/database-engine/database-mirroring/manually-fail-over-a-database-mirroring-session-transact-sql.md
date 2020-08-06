---
title: 데이터베이스 미러링 세션 수동 장애 조치(Transact-SQL) | Microsoft Docs
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
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c04ea4908ccbc4cfe4f6bb3606347dd444ef416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647191"
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="189fe-102">데이터베이스 미러링 세션 수동 장애 조치(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="189fe-102">Manually Fail Over a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="189fe-103">미러된 데이터베이스가 동기화되면, 즉 데이터베이스가 SYNCHRONIZED 상태인 경우 데이터베이스 소유자가 미러 서버에 수동 장애 조치(failover)를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189fe-103">When the mirrored database is synchronized (that is, when the database is in the SYNCHRONIZED state), the database owner can initiate manual failover to the mirror server.</span></span> <span data-ttu-id="189fe-104">수동 장애 조치는 주 서버에서만 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="189fe-104">Manual failover can be initiated only from the principal server.</span></span>  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a><span data-ttu-id="189fe-105">데이터베이스 미러링 세션을 수동 장애 조치하려면</span><span class="sxs-lookup"><span data-stu-id="189fe-105">To manually fail over a database mirroring session</span></span>  
  
1.  <span data-ttu-id="189fe-106">주 서버를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="189fe-106">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="189fe-107">데이터베이스 컨텍스트를 **master** 데이터베이스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="189fe-107">Set the database context to the **master** database:</span></span>  
  
     `USE master;`  
  
3.  <span data-ttu-id="189fe-108">주 서버에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="189fe-108">Issue the following statement on the principal server:</span></span>  
  
     <span data-ttu-id="189fe-109">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET PARTNER FAILOVER, 여기서 *database_name*은 미러된 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="189fe-109">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET PARTNER FAILOVER, where *database_name* is the mirrored database.</span></span>  
  
     <span data-ttu-id="189fe-110">이렇게 하면 미러 서버가 주 역할로 즉시 전환하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="189fe-110">This initiates an immediate transition of the mirror server to the principal role.</span></span>  
  
 <span data-ttu-id="189fe-111">이전 주 서버에서 클라이언트는 데이터베이스에서 연결이 끊어지고 진행 중인 트랜잭션은 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="189fe-111">On the former principal, clients are disconnected from the database and in-flight transactions are rolled back.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="189fe-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] DTC(Distributed Transaction Coordinator)를 사용하여 준비되었지만 장애 조치가 발생했을 때 커밋되지 않은 트랜잭션은 데이터베이스에 장애 조치를 취한 다음 중단된 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="189fe-112">Transactions that have been prepared by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator but are still not committed when a failover occurs are considered aborted after the database has failed over.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="189fe-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="189fe-113">See Also</span></span>  
 <span data-ttu-id="189fe-114">[ALTER DATABASE 데이터베이스 미러링&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="189fe-114">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="189fe-115">[데이터베이스 미러링 세션을 수동으로 장애 조치 (Failover) &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="189fe-115">[Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="189fe-116">데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="189fe-116">Role Switching During a Database Mirroring Session &#40;SQL Server&#41;</span></span>](role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
