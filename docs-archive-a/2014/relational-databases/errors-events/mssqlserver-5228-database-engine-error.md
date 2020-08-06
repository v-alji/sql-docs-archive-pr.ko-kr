---
title: MSSQLSERVER_5228 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5228 (Database Engine error)
ms.assetid: 5e83c617-4aa2-4755-bcc5-a798c46b97e4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eef59e62f00a44aad7bfefb1719a6d8d2b3d0290
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646517"
---
# <a name="mssqlserver_5228"></a><span data-ttu-id="b1ebb-102">MSSQLSERVER_5228</span><span class="sxs-lookup"><span data-stu-id="b1ebb-102">MSSQLSERVER_5228</span></span>
    
## <a name="details"></a><span data-ttu-id="b1ebb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="b1ebb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1ebb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="b1ebb-104">Product Name</span></span>|<span data-ttu-id="b1ebb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b1ebb-105">SQL Server</span></span>|  
|<span data-ttu-id="b1ebb-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="b1ebb-106">Event ID</span></span>|<span data-ttu-id="b1ebb-107">5228</span><span class="sxs-lookup"><span data-stu-id="b1ebb-107">5228</span></span>|  
|<span data-ttu-id="b1ebb-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="b1ebb-108">Event Source</span></span>|<span data-ttu-id="b1ebb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b1ebb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b1ebb-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b1ebb-110">Component</span></span>|<span data-ttu-id="b1ebb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b1ebb-111">SQLEngine</span></span>|  
|<span data-ttu-id="b1ebb-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="b1ebb-112">Symbolic Name</span></span>|<span data-ttu-id="b1ebb-113">DBCC4_ANTIMATTER_COLUMN_DETECTED</span><span class="sxs-lookup"><span data-stu-id="b1ebb-113">DBCC4_ANTIMATTER_COLUMN_DETECTED</span></span>|  
|<span data-ttu-id="b1ebb-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="b1ebb-114">Message Text</span></span>|<span data-ttu-id="b1ebb-115">테이블 오류: 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형), 페이지 PG_ID, 행 R_ID.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), page PG_ID, row R_ID.</span></span> <span data-ttu-id="b1ebb-116">DBCC가 온라인 인덱스 작성 작업에서 완료되지 않은 정리를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-116">DBCC detected incomplete cleanup from an online index build operation.</span></span> <span data-ttu-id="b1ebb-117">anti-matter 열 값은 VALUE입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-117">(Antimatter column value is VALUE.)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b1ebb-118">설명</span><span class="sxs-lookup"><span data-stu-id="b1ebb-118">Explanation</span></span>  
 <span data-ttu-id="b1ebb-119">개체 *O_ID*, 인덱스 *I_ID* 및 파티션 *PN_ID*에 대해 완료되지 않은 온라인 인덱스 작성이 감지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-119">An unfinished online index build was detected for object *O_ID*, index *I_ID*, and partition *PN_ID*.</span></span> <span data-ttu-id="b1ebb-120">이는 행 *R_ID*의 anti-matter 열로 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-120">This is manifested by the presence of an antimatter column on the row *R_ID*.</span></span> <span data-ttu-id="b1ebb-121">anti-matter 열은 온라인으로 인덱스를 작성하는 동안 여러 원본의 레코드를 조정할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-121">An antimatter column is used when reconciling records from multiple sources during an online index build.</span></span> <span data-ttu-id="b1ebb-122">오류 메시지에는 anti-matter 열의 값도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-122">The error message also indicates the value of the antimatter column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b1ebb-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="b1ebb-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="b1ebb-124">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="b1ebb-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="b1ebb-125">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="b1ebb-126">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="b1ebb-127">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="b1ebb-128">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="b1ebb-129">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="b1ebb-130">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="b1ebb-131">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="b1ebb-132">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="b1ebb-133">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="b1ebb-133">Restore from Backup</span></span>  
 <span data-ttu-id="b1ebb-134">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="b1ebb-135">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="b1ebb-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="b1ebb-136">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-136">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="b1ebb-137">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="b1ebb-137">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="b1ebb-138">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-138">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b1ebb-139">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-139">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="b1ebb-140">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-140">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="b1ebb-141">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="b1ebb-141">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="b1ebb-142">REPAIR 실행으로 인해 지정한 인덱스 및 모든 종속 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ebb-142">Running REPAIR will cause the specified index and all its dependent indexes to be rebuilt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ebb-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1ebb-143">See Also</span></span>  
 [<span data-ttu-id="b1ebb-144">DBCC CHECKDB&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1ebb-144">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
