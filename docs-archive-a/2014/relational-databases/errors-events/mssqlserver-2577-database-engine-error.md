---
title: MSSQLSERVER_2577 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2577 (Database Engine error)
ms.assetid: f53256a2-2fb0-47fd-9ed9-c45389104145
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9e4b7b85f59ba721eae6b4a0ac8db1b2d288422d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653905"
---
# <a name="mssqlserver_2577"></a><span data-ttu-id="1d56b-102">MSSQLSERVER_2577</span><span class="sxs-lookup"><span data-stu-id="1d56b-102">MSSQLSERVER_2577</span></span>
    
## <a name="details"></a><span data-ttu-id="1d56b-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1d56b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1d56b-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1d56b-104">Product Name</span></span>|<span data-ttu-id="1d56b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1d56b-105">SQL Server</span></span>|  
|<span data-ttu-id="1d56b-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1d56b-106">Event ID</span></span>|<span data-ttu-id="1d56b-107">2577</span><span class="sxs-lookup"><span data-stu-id="1d56b-107">2577</span></span>|  
|<span data-ttu-id="1d56b-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1d56b-108">Event Source</span></span>|<span data-ttu-id="1d56b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1d56b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1d56b-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1d56b-110">Component</span></span>|<span data-ttu-id="1d56b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1d56b-111">SQLEngine</span></span>|  
|<span data-ttu-id="1d56b-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1d56b-112">Symbolic Name</span></span>|<span data-ttu-id="1d56b-113">DBCC_IAM_CHAIN_SEQUENCE_OUT_OF_ORDER</span><span class="sxs-lookup"><span data-stu-id="1d56b-113">DBCC_IAM_CHAIN_SEQUENCE_OUT_OF_ORDER</span></span>|  
|<span data-ttu-id="1d56b-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1d56b-114">Message Text</span></span>|<span data-ttu-id="1d56b-115">개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)의 IAM(Index Allocation Map) 체인에서 체인 시퀀스 번호가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-115">Chain sequence numbers out of order in the Index Allocation Map (IAM) chain for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="1d56b-116">시퀀스 번호 SEQUENCE1의 페이지 P_ID1이(가) 시퀀스 번호 SEQUENCE2의 페이지 P_ID2을(를) 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-116">Page P_ID1 with sequence number SEQUENCE1 points to page P_ID2 with sequence number SEQUENCE2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1d56b-117">설명</span><span class="sxs-lookup"><span data-stu-id="1d56b-117">Explanation</span></span>  
 <span data-ttu-id="1d56b-118">모든 IAM(Index Allocation Map) 페이지에는 시퀀스 번호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-118">Every Index Allocation Map (IAM) page has a sequence number.</span></span> <span data-ttu-id="1d56b-119">시퀀스 번호는 IAM 체인 내에서의 IAM 페이지 위치이며</span><span class="sxs-lookup"><span data-stu-id="1d56b-119">The sequence number is the position of the IAM page within the IAM chain.</span></span> <span data-ttu-id="1d56b-120">각 IAM 페이지에 대해 시퀀스 번호가 1씩 증가하는 것이 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-120">The rule is that sequence numbers increase by one for each IAM page.</span></span> <span data-ttu-id="1d56b-121">IAM 페이지 *P_ID2*의 시퀀스 번호가 이 규칙에 어긋납니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-121">IAM page, *P_ID2*, has a sequence number that does not follow this rule.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1d56b-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1d56b-122">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="1d56b-123">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="1d56b-123">Look for Hardware Failure</span></span>  
 <span data-ttu-id="1d56b-124">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d56b-124">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="1d56b-125">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d56b-125">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="1d56b-126">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d56b-126">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="1d56b-127">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d56b-127">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="1d56b-128">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="1d56b-128">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="1d56b-129">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d56b-129">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="1d56b-130">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-130">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="1d56b-131">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-131">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="1d56b-132">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="1d56b-132">Restore from Backup</span></span>  
 <span data-ttu-id="1d56b-133">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="1d56b-133">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="1d56b-134">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="1d56b-134">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="1d56b-135">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d56b-135">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="1d56b-136">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="1d56b-136">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="1d56b-137">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d56b-137">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="1d56b-138">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="1d56b-138">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="1d56b-139">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="1d56b-139">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="1d56b-140">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="1d56b-140">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="1d56b-141">REPAIR을 실행하여 IAM 체인을 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-141">Running REPAIR will rebuild the IAM chain.</span></span> <span data-ttu-id="1d56b-142">REPAIR는 먼저 기존 IAM 체인을 반으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-142">REPAIR first splits the existing IAM chain in two halves.</span></span> <span data-ttu-id="1d56b-143">체인의 첫 번째 절반은 IAM 페이지 *P_ID1*로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-143">The first half of the chain will end with IAM page, *P_ID1*.</span></span> <span data-ttu-id="1d56b-144">*P_ID1* 페이지의 다음 페이지 포인터는 (0:0)으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-144">The next page pointer of the *P_ID1* page will be set to (0:0).</span></span> <span data-ttu-id="1d56b-145">체인의 두 번째 절반은 IAM 페이지 *P_ID2*로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-145">The second half of the chain will start with IAM page, *P_ID2*.</span></span> <span data-ttu-id="1d56b-146">*P_ID2* 페이지의 이전 페이지 포인터는 (0:0)으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-146">The previous page pointer of the *P_ID2* page will be set to (0:0).</span></span>  
  
 <span data-ttu-id="1d56b-147">그런 다음 REPAIR에서 이 둘을 연결하고 IAM 체인의 시퀀스 번호를 다시 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-147">REPAIR will then connect the two haves of the chain together and regenerate the sequence numbers for the IAM chain.</span></span> <span data-ttu-id="1d56b-148">복구할 수 없는 IAM 페이지는 할당이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-148">Any IAM pages that cannot be repaired will be deallocated.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="1d56b-149">이 복구로 인해 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d56b-149">This repair may cause data loss.</span></span>  
  
  
