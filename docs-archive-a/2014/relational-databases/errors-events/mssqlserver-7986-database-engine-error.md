---
title: MSSQLSERVER_7986 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7986 (Database Engine error)
ms.assetid: ae64276c-4e1e-4ef3-9ee9-ebeb2f61e565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f7d312987a2692c95f2cf6dbe0c86a4b2acbe6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734076"
---
# <a name="mssqlserver_7986"></a><span data-ttu-id="c666a-102">MSSQLSERVER_7986</span><span class="sxs-lookup"><span data-stu-id="c666a-102">MSSQLSERVER_7986</span></span>
    
## <a name="details"></a><span data-ttu-id="c666a-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="c666a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c666a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="c666a-104">Product Name</span></span>|<span data-ttu-id="c666a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c666a-105">SQL Server</span></span>|  
|<span data-ttu-id="c666a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="c666a-106">Event ID</span></span>|<span data-ttu-id="c666a-107">7986</span><span class="sxs-lookup"><span data-stu-id="c666a-107">7986</span></span>|  
|<span data-ttu-id="c666a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="c666a-108">Event Source</span></span>|<span data-ttu-id="c666a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c666a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c666a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c666a-110">Component</span></span>|<span data-ttu-id="c666a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c666a-111">SQLEngine</span></span>|  
|<span data-ttu-id="c666a-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="c666a-112">Symbolic Name</span></span>|<span data-ttu-id="c666a-113">DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE</span><span class="sxs-lookup"><span data-stu-id="c666a-113">DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE</span></span>|  
|<span data-ttu-id="c666a-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="c666a-114">Message Text</span></span>|<span data-ttu-id="c666a-115">시스템 테이블 사전 검사: 개체 ID O_ID에 개체 간 체인 연결이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c666a-115">System table pre-checks: Object ID O_ID has cross-object chain linkage.</span></span> <span data-ttu-id="c666a-116">페이지 P_ID1이(가) 할당 단위 ID A_ID1(A_ID2이어야 함)의 P_ID2을(를) 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c666a-116">Page P_ID1 points to P_ID2 in alloc unit ID A_ID1 (should be A_ID2).</span></span> <span data-ttu-id="c666a-117">복구할 수 없는 오류로 인해 검사 문이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="c666a-117">Check statement terminated due to unrepairable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c666a-118">설명</span><span class="sxs-lookup"><span data-stu-id="c666a-118">Explanation</span></span>  
 <span data-ttu-id="c666a-119">DBCC CHECKDB의 첫 번째 단계는 중요 시스템 테이블의 데이터 페이지에 대해 기본 검사를 수행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c666a-119">The first phase of a DBCC CHECKDB is to do primitive checks on the data pages of critical system tables.</span></span> <span data-ttu-id="c666a-120">오류가 발견되는 경우 이를 복구할 수 없으므로 DBCC CHECKDB가 즉시 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="c666a-120">If any errors are found, they cannot be repaired; therefore, the DBCC CHECKDB terminates immediately.</span></span> <span data-ttu-id="c666a-121">지정된 개체의 데이터 수준에 있는 *P_ID1* 페이지의 다음 페이지 포인터는 다른 개체의 *P_ID2* 페이지를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c666a-121">The next page pointer of page *P_ID1* in the data level of the specified object points to a page, *P_ID2*, in a different object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c666a-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="c666a-122">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="c666a-123">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="c666a-123">Look for Hardware Failure</span></span>  
 <span data-ttu-id="c666a-124">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="c666a-124">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="c666a-125">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="c666a-125">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="c666a-126">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="c666a-126">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="c666a-127">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="c666a-127">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="c666a-128">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="c666a-128">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="c666a-129">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="c666a-129">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="c666a-130">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c666a-130">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="c666a-131">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c666a-131">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="c666a-132">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="c666a-132">Restore from Backup</span></span>  
 <span data-ttu-id="c666a-133">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="c666a-133">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="c666a-134">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="c666a-134">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="c666a-135">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="c666a-135">Not applicable.</span></span> <span data-ttu-id="c666a-136">이 오류는 자동으로 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c666a-136">This error cannot be repaired automatically.</span></span> <span data-ttu-id="c666a-137">백업에서 데이터베이스를 복원할 수 없으면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="c666a-137">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
