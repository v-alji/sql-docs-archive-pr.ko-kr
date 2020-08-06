---
title: MSSQLSERVER_2576 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2576 (Database Engine error)
ms.assetid: b727cc2f-c76c-46f8-bbbe-5e7a05a6eabf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f378051c7844bf08d617db56666d69b22ecf732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649080"
---
# <a name="mssqlserver_2576"></a><span data-ttu-id="a8883-102">MSSQLSERVER_2576</span><span class="sxs-lookup"><span data-stu-id="a8883-102">MSSQLSERVER_2576</span></span>
    
## <a name="details"></a><span data-ttu-id="a8883-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="a8883-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8883-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a8883-104">Product Name</span></span>|<span data-ttu-id="a8883-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a8883-105">SQL Server</span></span>|  
|<span data-ttu-id="a8883-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a8883-106">Event ID</span></span>|<span data-ttu-id="a8883-107">2576</span><span class="sxs-lookup"><span data-stu-id="a8883-107">2576</span></span>|  
|<span data-ttu-id="a8883-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a8883-108">Event Source</span></span>|<span data-ttu-id="a8883-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a8883-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a8883-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a8883-110">Component</span></span>|<span data-ttu-id="a8883-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a8883-111">SQLEngine</span></span>|  
|<span data-ttu-id="a8883-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a8883-112">Symbolic Name</span></span>|<span data-ttu-id="a8883-113">DBCC_IAM_PARENT_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="a8883-113">DBCC_IAM_PARENT_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="a8883-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a8883-114">Message Text</span></span>|<span data-ttu-id="a8883-115">IAM(Index Allocation Map) 페이지 P_ID1이(가) 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)에 있는 IAM 페이지 P_ID2의 이전 포인터에 의해 지정되었으나 검색 시 감지되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a8883-115">The Index Allocation Map (IAM) page P_ID1 is pointed to by the previous pointer of IAM page P_ID2 in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) but was not detected in the scan.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a8883-116">설명</span><span class="sxs-lookup"><span data-stu-id="a8883-116">Explanation</span></span>  
 <span data-ttu-id="a8883-117">페이지에 대한 참조가 IAM 체인의 다른 IAM 페이지에 이전 페이지 링크로 존재하지만 이 IAM(Index Allocation Map) 페이지 또는 메타데이터 항목을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8883-117">An Index Allocation Map (IAM) page or metadata entry was not located, even though a reference to the page exists as the previous page link on another IAM page in an IAM chain.</span></span> <span data-ttu-id="a8883-118">*P_ID1* 페이지가 (0:0)이면 IAM 페이지 *P_ID2*는 IAM 체인의 시작이며 IAM 체인에 대한 메타데이터 항목이 누락되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8883-118">If the *P_ID1* page is (0:0), the IAM page, *P_ID2*, is the start of an IAM chain, and the metadata entry for the IAM chain is missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a8883-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a8883-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="a8883-120">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="a8883-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="a8883-121">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8883-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="a8883-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8883-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="a8883-123">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8883-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="a8883-124">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8883-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="a8883-125">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="a8883-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="a8883-126">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8883-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="a8883-127">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8883-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="a8883-128">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8883-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="a8883-129">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="a8883-129">Restore from Backup</span></span>  
 <span data-ttu-id="a8883-130">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="a8883-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="a8883-131">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="a8883-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="a8883-132">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8883-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="a8883-133">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="a8883-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="a8883-134">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8883-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a8883-135">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="a8883-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="a8883-136">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="a8883-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="a8883-137">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="a8883-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="a8883-138">REPAIR는 *P_ID2* 페이지와 관련된 IAM 체인을 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="a8883-138">REPAIR will try to rebuild the IAM chain involving the *P_ID2* page.</span></span> <span data-ttu-id="a8883-139">체인을 다시 작성하기 위해 체인에서 페이지를 제거하거나 메타데이터가 손상된 경우 전체 체인을 제거해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8883-139">Rebuilding the chain may involve removing pages from the chain, or removing the whole chain if the metadata is corrupted.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a8883-140">이 복구로 인해 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8883-140">This repair may cause data loss.</span></span>  
  
  
