---
title: MSSQLSERVER_1406 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: adaa0084b875f720c477189e0e8e085af124f4cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734115"
---
# <a name="mssqlserver_1406"></a><span data-ttu-id="81698-102">MSSQLSERVER_1406</span><span class="sxs-lookup"><span data-stu-id="81698-102">MSSQLSERVER_1406</span></span>
    
## <a name="details"></a><span data-ttu-id="81698-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="81698-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81698-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="81698-104">Product Name</span></span>|<span data-ttu-id="81698-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="81698-105">SQL Server</span></span>|  
|<span data-ttu-id="81698-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="81698-106">Event ID</span></span>|<span data-ttu-id="81698-107">1406</span><span class="sxs-lookup"><span data-stu-id="81698-107">1406</span></span>|  
|<span data-ttu-id="81698-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="81698-108">Event Source</span></span>|<span data-ttu-id="81698-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="81698-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="81698-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="81698-110">Component</span></span>|<span data-ttu-id="81698-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="81698-111">SQLEngine</span></span>|  
|<span data-ttu-id="81698-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="81698-112">Symbolic Name</span></span>|<span data-ttu-id="81698-113">DBM_BADSTATEFORFORCESERVICE</span><span class="sxs-lookup"><span data-stu-id="81698-113">DBM_BADSTATEFORFORCESERVICE</span></span>|  
|<span data-ttu-id="81698-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="81698-114">Message Text</span></span>|<span data-ttu-id="81698-115">서비스를 안전하게 강제 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81698-115">Unable to force service safely.</span></span> <span data-ttu-id="81698-116">액세스하려면 데이터베이스 미러링을 제거한 다음 데이터베이스 "%.\*ls"을(를) 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="81698-116">Remove database mirroring and recover database "%.\*ls" to gain access.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="81698-117">설명</span><span class="sxs-lookup"><span data-stu-id="81698-117">Explanation</span></span>  
 <span data-ttu-id="81698-118">미러링 상태에서 강제 서비스 프로세스가 제대로 동작하는지 보장할 수 없기 때문에 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에서 서비스를 강제 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81698-118">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot force service because the mirroring state cannot guarantee that the force service process would work correctly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="81698-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="81698-119">User Action</span></span>  
 <span data-ttu-id="81698-120">데이터베이스 미러링을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="81698-120">Remove database mirroring.</span></span> <span data-ttu-id="81698-121">그런 다음 미러 데이터베이스를 복구하여 이 데이터베이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81698-121">You can then recover the mirror database to gain access to it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81698-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81698-122">See Also</span></span>  
 <span data-ttu-id="81698-123">[데이터베이스 미러링 세션에 서비스 강제 수행&#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="81698-123">[Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 [<span data-ttu-id="81698-124">데이터베이스 미러링 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="81698-124">Removing Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
