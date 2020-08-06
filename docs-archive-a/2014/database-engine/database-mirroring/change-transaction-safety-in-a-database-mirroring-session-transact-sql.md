---
title: 데이터베이스 미러링 세션에서 트랜잭션 보안 변경(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d8bc9d0fb639770d33507c29a6ec67f60bd0434a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648579"
---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="6a46d-102">데이터베이스 미러링 세션에서 트랜잭션 보안 변경(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6a46d-102">Change Transaction Safety in a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="6a46d-103">트랜잭션 보안은 세션의 운영 모드를 제어하는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-103">Transaction safety is the attribute that controls the operating mode of the session.</span></span> <span data-ttu-id="6a46d-104">그러나 데이터베이스 소유자는 언제든지 트랜잭션 보안을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-104">At any time, however, the database owner can change the transaction safety.</span></span> <span data-ttu-id="6a46d-105">기본적으로 트랜잭션 보안의 수준은 FULL(동기 운영 모드)로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-105">By default, the level of transaction safety is set to FULL (synchronous operating mode).</span></span>  
  
 <span data-ttu-id="6a46d-106">트랜잭션 보안을 해제하면 세션이 비동기 운영 모드로 바뀌므로 성능이 최대화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-106">Turning off transaction safety shifts the session into asynchronous operating mode, which maximizes performance.</span></span> <span data-ttu-id="6a46d-107">주 서버를 사용할 수 없는 경우 미러 서버가 중지되지만 웜 대기로 사용할 수 있습니다. 장애 조치(Failover)를 수행하려면 서비스를 강제 적용해야 하며 이 경우 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-107">If the principal becomes unavailable, the mirror stops but is available as a warm standby (failover requires forcing service with possible data loss).</span></span>  
  
### <a name="to-turn-on-transaction-safety"></a><span data-ttu-id="6a46d-108">트랜잭션 보안을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="6a46d-108">To turn on transaction safety</span></span>  
  
1.  <span data-ttu-id="6a46d-109">주 서버를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-109">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="6a46d-110">다음 Transact-SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-110">Issue the following Transact-SQL statement:</span></span>  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     <span data-ttu-id="6a46d-111">여기서 *\<database>* 는 미러된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-111">where *\<database>* is the name of the mirrored database.</span></span>  
  
### <a name="to-turn-off-transaction-safety"></a><span data-ttu-id="6a46d-112">트랜잭션 보안을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="6a46d-112">To turn off transaction safety</span></span>  
  
1.  <span data-ttu-id="6a46d-113">주 서버를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-113">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="6a46d-114">다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-114">Issue the following statement:</span></span>  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     <span data-ttu-id="6a46d-115">여기서 *\<database>* 는 미러된 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="6a46d-115">where *\<database>* is the mirrored database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a46d-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a46d-116">See Also</span></span>  
 <span data-ttu-id="6a46d-117">[ALTER DATABASE 데이터베이스 미러링&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="6a46d-117">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 [<span data-ttu-id="6a46d-118">데이터베이스 미러링 운영 모드</span><span class="sxs-lookup"><span data-stu-id="6a46d-118">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
