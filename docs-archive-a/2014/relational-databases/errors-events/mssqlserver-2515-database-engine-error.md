---
title: MSSQLSERVER_2515 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2515 (Database Engine error)
ms.assetid: af93aa29-70c9-4923-90af-aafadb20c1c6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73b2d8b8ff01b97428ba6149f537d96044c6ae3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729519"
---
# <a name="mssqlserver_2515"></a><span data-ttu-id="6d107-102">MSSQLSERVER_2515</span><span class="sxs-lookup"><span data-stu-id="6d107-102">MSSQLSERVER_2515</span></span>
    
## <a name="details"></a><span data-ttu-id="6d107-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="6d107-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6d107-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="6d107-104">Product Name</span></span>|<span data-ttu-id="6d107-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6d107-105">SQL Server</span></span>|  
|<span data-ttu-id="6d107-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="6d107-106">Event ID</span></span>|<span data-ttu-id="6d107-107">2515</span><span class="sxs-lookup"><span data-stu-id="6d107-107">2515</span></span>|  
|<span data-ttu-id="6d107-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="6d107-108">Event Source</span></span>|<span data-ttu-id="6d107-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6d107-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6d107-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6d107-110">Component</span></span>|<span data-ttu-id="6d107-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6d107-111">SQLEngine</span></span>|  
|<span data-ttu-id="6d107-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="6d107-112">Symbolic Name</span></span>|<span data-ttu-id="6d107-113">DBCC_DIFF_MAP_OUT_OF_SYNC</span><span class="sxs-lookup"><span data-stu-id="6d107-113">DBCC_DIFF_MAP_OUT_OF_SYNC</span></span>|  
|<span data-ttu-id="6d107-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="6d107-114">Message Text</span></span>|<span data-ttu-id="6d107-115">페이지 P_ID, 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)이(가) 수정되었지만 차등 백업 비트맵에서 수정된 것으로 표시되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="6d107-115">Page P_ID, object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID type TYPE has been modified but is not marked modified in the differential backup bitmap.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6d107-116">설명</span><span class="sxs-lookup"><span data-stu-id="6d107-116">Explanation</span></span>  
 <span data-ttu-id="6d107-117">지정된 페이지에 있는 LSN(로그 시퀀스 번호)은 어느 것이 더 최근 값인지에 관계없이 데이터베이스의 BackupManager에 있는 차등 참조 LSN이나 파일의 파일 제어 블록의 차등 기반 LSN보다 높은 값을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="6d107-117">The page specified has a log sequence number (LSN) that is higher than the differential reference LSN in the BackupManager of the database, or the differential base LSN in the file control block of the file, whichever is more recent.</span></span> <span data-ttu-id="6d107-118">그러나 페이지는 차등 백업 비트맵에서 변경된 것으로 표시되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="6d107-118">However, the page is not marked as changed in the differential backup bitmap.</span></span>  
  
 <span data-ttu-id="6d107-119">이 검사는 차등 비트맵에 오류가 없는 경우에만 수행되므로 데이터베이스당 한 페이지만 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d107-119">Only one page per database will be reported, because this check is only performed when the differential bitmap is known to be error free.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6d107-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="6d107-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="6d107-121">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="6d107-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="6d107-122">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d107-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="6d107-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d107-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="6d107-124">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d107-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="6d107-125">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d107-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="6d107-126">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="6d107-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="6d107-127">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d107-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="6d107-128">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d107-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="6d107-129">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d107-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="6d107-130">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="6d107-130">Restore from Backup</span></span>  
 <span data-ttu-id="6d107-131">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="6d107-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="6d107-132">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="6d107-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="6d107-133">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d107-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="6d107-134">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="6d107-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="6d107-135">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d107-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6d107-136">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="6d107-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="6d107-137">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="6d107-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="6d107-138">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="6d107-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="6d107-139">REPAIR를 실행하면 차등 비트맵이 무효화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d107-139">Running REPAIR will invalidate the differential bitmap.</span></span> <span data-ttu-id="6d107-140">전체 데이터베이스 백업이 수행되기까지 차등 백업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d107-140">You cannot perform a differential backup until a full database backup is taken.</span></span> <span data-ttu-id="6d107-141">전체 데이터베이스 백업은 차등 비트맵을 다시 작성하기 위한 기준점이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d107-141">The full database backup provides a baseline for the differential bitmap to be rebuilt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d107-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d107-142">See Also</span></span>  
 <span data-ttu-id="6d107-143">[전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6d107-143">[Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="6d107-144">MSSQLSERVER_2516</span><span class="sxs-lookup"><span data-stu-id="6d107-144">MSSQLSERVER_2516</span></span>](mssqlserver-2516-database-engine-error.md)  
  
  
