---
title: MSSQLSERVER_7984 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7984 (Database Engine error)
ms.assetid: e3192f56-e4e2-41da-b132-65f1e7540b1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7f92fe4f3751621e0cc636ffcd2d4de73b348d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653421"
---
# <a name="mssqlserver_7984"></a><span data-ttu-id="873ec-102">MSSQLSERVER_7984</span><span class="sxs-lookup"><span data-stu-id="873ec-102">MSSQLSERVER_7984</span></span>
    
## <a name="details"></a><span data-ttu-id="873ec-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="873ec-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="873ec-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="873ec-104">Product Name</span></span>|<span data-ttu-id="873ec-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="873ec-105">SQL Server</span></span>|  
|<span data-ttu-id="873ec-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="873ec-106">Event ID</span></span>|<span data-ttu-id="873ec-107">7984</span><span class="sxs-lookup"><span data-stu-id="873ec-107">7984</span></span>|  
|<span data-ttu-id="873ec-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="873ec-108">Event Source</span></span>|<span data-ttu-id="873ec-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="873ec-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="873ec-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="873ec-110">Component</span></span>|<span data-ttu-id="873ec-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="873ec-111">SQLEngine</span></span>|  
|<span data-ttu-id="873ec-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="873ec-112">Symbolic Name</span></span>|<span data-ttu-id="873ec-113">DBCC2_PRE_CHECKS_BAD_PAGE_TYPE</span><span class="sxs-lookup"><span data-stu-id="873ec-113">DBCC2_PRE_CHECKS_BAD_PAGE_TYPE</span></span>|  
|<span data-ttu-id="873ec-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="873ec-114">Message Text</span></span>|<span data-ttu-id="873ec-115">시스템 테이블 사전 검사: 개체 ID가 O_ID입니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-115">System table pre-checks: Object ID O_ID.</span></span> <span data-ttu-id="873ec-116">페이지 P_ID에 예기치 않은 페이지 유형 PAGETYPE이(가) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-116">Page P_ID has unexpected page type PAGETYPE.</span></span> <span data-ttu-id="873ec-117">오류로 인해 검사 문이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-117">Check statement terminated because of an irreparable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="873ec-118">설명</span><span class="sxs-lookup"><span data-stu-id="873ec-118">Explanation</span></span>  
 <span data-ttu-id="873ec-119">지정된 개체의 데이터 수준에서 페이지 유형이 DATA_PAGE가 아닌 페이지를 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-119">A page with a type other than DATA_PAGE was found in the data level of the specified object.</span></span> <span data-ttu-id="873ec-120">이 오류는 DBCC CHECKDB 명령의 첫 번째 단계 검사 중에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-120">This error is raised during the first phase of the DBCC CHECKDB command checks.</span></span> <span data-ttu-id="873ec-121">이 단계에서 DBCC CHECKDB는 중요 시스템 기본 테이블의 데이터 페이지에 대한 기본 검사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-121">During this phase, DBCC CHECKDB performs primitive checks on the data pages of critical system base tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="873ec-122">시스템 테이블에서 발견된 오류는 복구할 수 없으므로 DBCC CHECKDB 명령이 즉시 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-122">If any errors are found in the system tables, the errors cannot be repaired; therefore, the DBCC CHECKDB command ends immediately.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="873ec-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="873ec-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="873ec-124">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="873ec-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="873ec-125">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="873ec-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="873ec-126">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="873ec-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="873ec-127">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="873ec-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="873ec-128">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="873ec-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="873ec-129">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="873ec-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="873ec-130">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="873ec-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="873ec-131">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="873ec-132">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="873ec-133">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="873ec-133">Restore from Backup</span></span>  
 <span data-ttu-id="873ec-134">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="873ec-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="873ec-135">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="873ec-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="873ec-136">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="873ec-136">Not applicable.</span></span> <span data-ttu-id="873ec-137">이 오류는 자동으로 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="873ec-137">This error cannot be repaired automatically.</span></span> <span data-ttu-id="873ec-138">백업에서 데이터베이스를 복원할 수 없으면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="873ec-138">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service and Support (CSS).</span></span>  
  
  
