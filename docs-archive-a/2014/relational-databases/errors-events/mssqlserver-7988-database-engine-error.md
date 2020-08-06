---
title: MSSQLSERVER_7988 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7988 (Database Engine error)
ms.assetid: 29b967b8-de30-4618-99a8-8b1155e69026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 984cb03aeb5feaa230762e200304f16cd8c5df08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731619"
---
# <a name="mssqlserver_7988"></a><span data-ttu-id="37ee8-102">MSSQLSERVER_7988</span><span class="sxs-lookup"><span data-stu-id="37ee8-102">MSSQLSERVER_7988</span></span>
    
## <a name="details"></a><span data-ttu-id="37ee8-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="37ee8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="37ee8-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="37ee8-104">Product Name</span></span>|<span data-ttu-id="37ee8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="37ee8-105">SQL Server</span></span>|  
|<span data-ttu-id="37ee8-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="37ee8-106">Event ID</span></span>|<span data-ttu-id="37ee8-107">7988</span><span class="sxs-lookup"><span data-stu-id="37ee8-107">7988</span></span>|  
|<span data-ttu-id="37ee8-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="37ee8-108">Event Source</span></span>|<span data-ttu-id="37ee8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="37ee8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="37ee8-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="37ee8-110">Component</span></span>|<span data-ttu-id="37ee8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="37ee8-111">SQLEngine</span></span>|  
|<span data-ttu-id="37ee8-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="37ee8-112">Symbolic Name</span></span>|<span data-ttu-id="37ee8-113">DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED</span><span class="sxs-lookup"><span data-stu-id="37ee8-113">DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED</span></span>|  
|<span data-ttu-id="37ee8-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="37ee8-114">Message Text</span></span>|<span data-ttu-id="37ee8-115">시스템 테이블 사전 검사: 개체 ID가 O_ID입니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-115">System table pre-checks: Object ID O_ID.</span></span> <span data-ttu-id="37ee8-116">P_ID에서 데이터 체인의 루프가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-116">Loop in data chain detected at P_ID.</span></span> <span data-ttu-id="37ee8-117">오류로 인해 검사 문이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-117">Check statement terminated because of an irreparable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="37ee8-118">설명</span><span class="sxs-lookup"><span data-stu-id="37ee8-118">Explanation</span></span>  
 <span data-ttu-id="37ee8-119">DBCC CHECKDB의 첫 번째 단계는 중요 시스템 테이블의 데이터 페이지에 대해 기본 검사를 수행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-119">The first phase of a DBCC CHECKDB is to do primitive checks on the data pages of critical system tables.</span></span> <span data-ttu-id="37ee8-120">오류가 발견되는 경우 이를 복구할 수 없으므로 DBCC CHECKDB가 즉시 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-120">If any errors are found, they cannot be repaired; therefore, DBCC CHECKDB terminates immediately.</span></span> <span data-ttu-id="37ee8-121">*P_ID* 페이지에서 페이지 연결 루프가 발견되었습니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-121">A page linkage loop has been detected on page *P_ID*.</span></span> <span data-ttu-id="37ee8-122">페이지의 다음 페이지 포인터가 결국 해당 페이지로 돌아가는 경우 페이지 연결 루프가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-122">A page linkage loop occurs when the next page pointers from a page eventually return to the page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="37ee8-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="37ee8-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="37ee8-124">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="37ee8-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="37ee8-125">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="37ee8-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="37ee8-126">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="37ee8-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="37ee8-127">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="37ee8-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="37ee8-128">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="37ee8-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="37ee8-129">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="37ee8-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="37ee8-130">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="37ee8-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="37ee8-131">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="37ee8-132">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="37ee8-133">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="37ee8-133">Restore from Backup</span></span>  
 <span data-ttu-id="37ee8-134">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="37ee8-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="37ee8-135">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="37ee8-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="37ee8-136">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="37ee8-136">Not applicable.</span></span> <span data-ttu-id="37ee8-137">이 오류는 자동으로 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37ee8-137">This error cannot be repaired automatically.</span></span> <span data-ttu-id="37ee8-138">백업에서 데이터베이스를 복원할 수 없으면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="37ee8-138">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service and Support (CSS).</span></span>  
  
  
