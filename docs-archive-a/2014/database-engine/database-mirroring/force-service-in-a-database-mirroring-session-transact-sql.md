---
title: 데이터베이스 미러링 세션에 서비스 강제 수행(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- forced service [SQL Server]
- database mirroring [SQL Server], forcing service
ms.assetid: 8b6ffe77-35f3-4e2a-a658-8a38a8e1c794
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b909f3602a78f3244ab3cf4479b8745956a7bd62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742568"
---
# <a name="force-service-in-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="56834-102">데이터베이스 미러링 세션에 서비스 강제 수행(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="56834-102">Force Service in a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="56834-103">성능 우선 모드 및 장애 조치를 지원하지 않는 보호 우선 모드에서 미러 서버는 사용할 수 있는데 주 서버는 실패하는 경우 데이터베이스 소유자는 서비스가 미러 데이터베이스로 장애 조치(데이터 손실 가능)되도록 강제 적용하여 데이터베이스를 사용 가능하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56834-103">In high-performance mode and high-safety mode without automatic failover, if the principal server fails while the mirror server is available, the database owner can make the database available by forcing service to fail over (with possible data loss) to the mirror database.</span></span> <span data-ttu-id="56834-104">이 옵션은 다음 조건이 모두 충족된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56834-104">This option is available only under all the following conditions:</span></span>  
  
-   <span data-ttu-id="56834-105">주 서버가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="56834-105">The principal server is down.</span></span>  
  
-   <span data-ttu-id="56834-106">WITNESS가 OFF로 설정되거나 미러 서버에 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56834-106">WITNESS is set to OFF or is connected to the mirror server.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="56834-107">엄밀히 말하면 강제 서비스는 재해 복구 수단이라 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56834-107">Forced service is strictly a disaster recovery method.</span></span> <span data-ttu-id="56834-108">서비스를 강제 적용하면 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56834-108">Forcing service may involve some data loss.</span></span> <span data-ttu-id="56834-109">따라서 데이터베이스로 서비스를 즉시 복원하기 위해 일부 데이터가 손실되는 위험을 감수하려는 경우에만 서비스를 강제 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="56834-109">Therefore, force service only if you are willing to risk losing some data in order to restore service to the database immediately.</span></span> <span data-ttu-id="56834-110">강제 서비스로 인해 중요한 데이터가 손실될 위험이 있는 경우에는 미러링을 중지하고 데이터베이스를 수동으로 다시 동기화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="56834-110">If forcing service risks losing significant data, we recommend that you stop mirroring and manually resynchronize the databases.</span></span> <span data-ttu-id="56834-111">강제 서비스의 위험성에 대한 자세한 내용은 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="56834-111">For more information about the risks of forcing service, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="56834-112">서비스를 강제 적용하면 세션이 일시 중지되고 새 복구 분기가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="56834-112">Forcing service suspends the session and starts a new recovery fork.</span></span> <span data-ttu-id="56834-113">서비스를 강제 적용하는 것은 미러링을 제거하고 이전 주 데이터베이스를 복구하는 것과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="56834-113">The effect of forcing service is similar to removing mirroring and recovering the former principal database.</span></span> <span data-ttu-id="56834-114">그러나 강제 서비스의 경우 미러링을 재개할 때 데이터베이스를 다시 동기화하기 때문에 데이터가 손실될 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56834-114">However, forcing service facilitates resynchronizing the databases (with possible data loss) when mirroring resumes.</span></span>  
  
### <a name="to-force-service-in-a-database-mirroring-session"></a><span data-ttu-id="56834-115">데이터베이스 미러링 세션에서 서비스를 강제 수행하려면</span><span class="sxs-lookup"><span data-stu-id="56834-115">To force service in a database mirroring session</span></span>  
  
1.  <span data-ttu-id="56834-116">미러 서버로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="56834-116">Connect to the mirror server.</span></span>  
  
2.  <span data-ttu-id="56834-117">다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="56834-117">Issue the following statement:</span></span>  
  
     <span data-ttu-id="56834-118">ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS</span><span class="sxs-lookup"><span data-stu-id="56834-118">ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS</span></span>  
  
     <span data-ttu-id="56834-119">여기서 *<database_name>* 은 미러 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="56834-119">where *<database_name>* is the mirrored database.</span></span>  
  
     <span data-ttu-id="56834-120">미러 서버는 주 서버로 바로 전환되고 미러링은 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="56834-120">The mirror server immediately transitions to principal server, and mirroring is suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56834-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56834-121">See Also</span></span>  
 <span data-ttu-id="56834-122">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="56834-122">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="56834-123">데이터베이스 미러링 운영 모드</span><span class="sxs-lookup"><span data-stu-id="56834-123">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
