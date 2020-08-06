---
title: MSSQLSERVER_2575 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2575 (Database Engine error)
ms.assetid: 92dfe449-a122-4730-942b-e1d319862d20
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 461d2b57b5ace98ca624f8dc3717c98f3e9e4d67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646521"
---
# <a name="mssqlserver_2575"></a><span data-ttu-id="85a33-102">MSSQLSERVER_2575</span><span class="sxs-lookup"><span data-stu-id="85a33-102">MSSQLSERVER_2575</span></span>
    
## <a name="details"></a><span data-ttu-id="85a33-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="85a33-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85a33-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="85a33-104">Product Name</span></span>|<span data-ttu-id="85a33-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="85a33-105">SQL Server</span></span>|  
|<span data-ttu-id="85a33-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="85a33-106">Event ID</span></span>|<span data-ttu-id="85a33-107">2575</span><span class="sxs-lookup"><span data-stu-id="85a33-107">2575</span></span>|  
|<span data-ttu-id="85a33-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="85a33-108">Event Source</span></span>|<span data-ttu-id="85a33-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="85a33-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="85a33-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="85a33-110">Component</span></span>|<span data-ttu-id="85a33-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="85a33-111">SQLEngine</span></span>|  
|<span data-ttu-id="85a33-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="85a33-112">Symbolic Name</span></span>|<span data-ttu-id="85a33-113">DBCC_IAM_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="85a33-113">DBCC_IAM_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="85a33-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="85a33-114">Message Text</span></span>|<span data-ttu-id="85a33-115">IAM 페이지 P_ID1이(가) 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)에 있는 IAM 페이지 P_ID2의 다음 포인터에 의해 지정되었으나 검색 시 감지되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="85a33-115">IAM page P_ID1 is pointed to by the next pointer of IAM page P_ID2 in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) but was not detected in the scan.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="85a33-116">설명</span><span class="sxs-lookup"><span data-stu-id="85a33-116">Explanation</span></span>  
 <span data-ttu-id="85a33-117">지정한 인덱스에 대한 IAM(Index Allocation Map) 페이지를 찾았지만 해당 인덱스의 다음 페이지 포인터에 대한 IAM 페이지를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85a33-117">An Index Allocation Map (IAM) page was found for the specified index; however, the IAM page for its next-page pointer was not found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="85a33-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="85a33-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="85a33-119">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="85a33-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="85a33-120">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="85a33-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="85a33-121">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="85a33-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="85a33-122">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="85a33-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="85a33-123">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="85a33-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="85a33-124">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="85a33-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="85a33-125">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="85a33-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="85a33-126">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85a33-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="85a33-127">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="85a33-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="85a33-128">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="85a33-128">Restore from Backup</span></span>  
 <span data-ttu-id="85a33-129">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="85a33-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="85a33-130">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="85a33-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="85a33-131">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="85a33-131">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="85a33-132">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="85a33-132">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="85a33-133">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="85a33-133">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="85a33-134">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="85a33-134">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="85a33-135">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="85a33-135">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="85a33-136">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="85a33-136">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="85a33-137">DBCC에서 인덱스를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="85a33-137">DBCC will rebuild the index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a33-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85a33-138">See Also</span></span>  
 [<span data-ttu-id="85a33-139">DBCC CHECKDB&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85a33-139">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
