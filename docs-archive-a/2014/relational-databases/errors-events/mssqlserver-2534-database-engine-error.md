---
title: MSSQLSERVER_2534 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2534 (Database Engine error)
ms.assetid: 121cf99d-0722-494c-be24-3369c1a0badc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 409c429f961cd8357bfa2e40663c33f3c1f2e36d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653918"
---
# <a name="mssqlserver_2534"></a><span data-ttu-id="14d19-102">MSSQLSERVER_2534</span><span class="sxs-lookup"><span data-stu-id="14d19-102">MSSQLSERVER_2534</span></span>
    
## <a name="details"></a><span data-ttu-id="14d19-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="14d19-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14d19-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="14d19-104">Product Name</span></span>|<span data-ttu-id="14d19-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="14d19-105">SQL Server</span></span>|  
|<span data-ttu-id="14d19-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="14d19-106">Event ID</span></span>|<span data-ttu-id="14d19-107">2534</span><span class="sxs-lookup"><span data-stu-id="14d19-107">2534</span></span>|  
|<span data-ttu-id="14d19-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="14d19-108">Event Source</span></span>|<span data-ttu-id="14d19-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="14d19-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="14d19-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="14d19-110">Component</span></span>|<span data-ttu-id="14d19-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="14d19-111">SQLEngine</span></span>|  
|<span data-ttu-id="14d19-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="14d19-112">Symbolic Name</span></span>|<span data-ttu-id="14d19-113">DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="14d19-113">DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT</span></span>|  
|<span data-ttu-id="14d19-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="14d19-114">Message Text</span></span>|<span data-ttu-id="14d19-115">테이블 오류: 페이지 머리글에는 페이지 P_ID이(가) 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)에 할당되었다고 나타나 있지만 이 페이지는 다른 개체에 의해 할당되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14d19-115">Table error: Page P_ID, whose header indicates it as being allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), is allocated by another object.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="14d19-116">설명</span><span class="sxs-lookup"><span data-stu-id="14d19-116">Explanation</span></span>  
 <span data-ttu-id="14d19-117">페이지 머리글에는 할당 단위 ID *A_ID*가 포함되어 있지만 할당 단위의 IAM(Index Allocation Map) 페이지는 이 페이지를 할당하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14d19-117">The header of the page contains the allocation unit ID, *A_ID*, but none of the Index Allocation Map (IAM) pages of that allocation unit allocates the page.</span></span> <span data-ttu-id="14d19-118">따라서 페이지 머리글에 잘못된 할당 단위 ID가 포함되며 해당 페이지에는 페이지가 실제로 할당된 할당 단위 ID에 대한 MSSQLServer_2533 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="14d19-118">Therefore, the header of the page contains the wrong allocation unit ID, and the page will have a matching MSSQLServer_2533 error that corresponds to the allocation unit ID to which the page is actually allocated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="14d19-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="14d19-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="14d19-120">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="14d19-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="14d19-121">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="14d19-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="14d19-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="14d19-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="14d19-123">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="14d19-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="14d19-124">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="14d19-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="14d19-125">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="14d19-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="14d19-126">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="14d19-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="14d19-127">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14d19-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="14d19-128">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="14d19-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="14d19-129">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="14d19-129">Restore from Backup</span></span>  
 <span data-ttu-id="14d19-130">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="14d19-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="14d19-131">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="14d19-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="14d19-132">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="14d19-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="14d19-133">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="14d19-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="14d19-134">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="14d19-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="14d19-135">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="14d19-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="14d19-136">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="14d19-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="14d19-137">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="14d19-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="14d19-138">인덱스가 있는 경우 REPAIR에서 인덱스를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="14d19-138">REPAIR will rebuild the index if an index exists.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="14d19-139">해당하는 [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md) 오류에 대해 REPAIR를 실행하면 페이지의 할당이 취소된 후 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="14d19-139">Running REPAIR for the matching [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md) error deallocates the page before the rebuild.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="14d19-140">이 복구로 인해 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14d19-140">This repair may cause data loss.</span></span>  
  
  
