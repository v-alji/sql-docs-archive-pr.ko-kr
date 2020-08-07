---
title: MSSQLSERVER_2574 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2574 (Database Engine error)
ms.assetid: efba507a-b5ad-4f1d-b0c8-f73b663a0562
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44fd103f8c651ca968ae997ae9c3d544b41cbf3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729511"
---
# <a name="mssqlserver_2574"></a><span data-ttu-id="038e7-102">MSSQLSERVER_2574</span><span class="sxs-lookup"><span data-stu-id="038e7-102">MSSQLSERVER_2574</span></span>
    
## <a name="details"></a><span data-ttu-id="038e7-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="038e7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="038e7-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="038e7-104">Product Name</span></span>|<span data-ttu-id="038e7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="038e7-105">SQL Server</span></span>|  
|<span data-ttu-id="038e7-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="038e7-106">Event ID</span></span>|<span data-ttu-id="038e7-107">2574</span><span class="sxs-lookup"><span data-stu-id="038e7-107">2574</span></span>|  
|<span data-ttu-id="038e7-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="038e7-108">Event Source</span></span>|<span data-ttu-id="038e7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="038e7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="038e7-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="038e7-110">Component</span></span>|<span data-ttu-id="038e7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="038e7-111">SQLEngine</span></span>|  
|<span data-ttu-id="038e7-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="038e7-112">Symbolic Name</span></span>|<span data-ttu-id="038e7-113">DBCC_EMPTY_INDEX_TREE_LEVEL_PAGE</span><span class="sxs-lookup"><span data-stu-id="038e7-113">DBCC_EMPTY_INDEX_TREE_LEVEL_PAGE</span></span>|  
|<span data-ttu-id="038e7-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="038e7-114">Message Text</span></span>|<span data-ttu-id="038e7-115">테이블 오류: 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)에서 페이지 P_ID이(가) 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038e7-115">Table error: Page P_ID is empty in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="038e7-116">이는 B-트리 수준 LEVEL에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="038e7-116">This is not permitted at level LEVEL of the B-tree.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="038e7-117">설명</span><span class="sxs-lookup"><span data-stu-id="038e7-117">Explanation</span></span>  
 <span data-ttu-id="038e7-118">지정된 인덱스의 리프 수준 위 B-트리 페이지가 비어 있습니다. 즉, 행이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="038e7-118">A B-tree page above the leaf level of the specified index is empty, that is it has no rows.</span></span> <span data-ttu-id="038e7-119">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 리프 수준 페이지에 대해 이런 동작이 가능하지만 트리 수준에서는 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="038e7-119">This behavior is possible for leaf-level pages in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], but has never been possible in tree levels.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="038e7-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="038e7-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="038e7-121">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="038e7-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="038e7-122">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="038e7-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="038e7-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="038e7-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="038e7-124">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="038e7-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="038e7-125">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="038e7-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="038e7-126">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="038e7-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="038e7-127">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="038e7-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="038e7-128">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038e7-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="038e7-129">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="038e7-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="038e7-130">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="038e7-130">Restore from Backup</span></span>  
 <span data-ttu-id="038e7-131">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="038e7-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="038e7-132">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="038e7-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="038e7-133">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="038e7-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="038e7-134">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="038e7-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="038e7-135">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="038e7-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="038e7-136">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="038e7-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="038e7-137">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="038e7-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="038e7-138">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="038e7-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="038e7-139">DBCC에서 인덱스를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="038e7-139">DBCC will rebuild the index.</span></span>  
  
  
