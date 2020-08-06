---
title: MSSQLSERVER_5233 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5233 (Database Engine error)
ms.assetid: 7a855afa-2d3b-49b7-adef-197b99fc98b1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a5e2c603652534a6d3093a01da0a926a7195954
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653885"
---
# <a name="mssqlserver_5233"></a><span data-ttu-id="d0c0b-102">MSSQLSERVER_5233</span><span class="sxs-lookup"><span data-stu-id="d0c0b-102">MSSQLSERVER_5233</span></span>
    
## <a name="details"></a><span data-ttu-id="d0c0b-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d0c0b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d0c0b-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d0c0b-104">Product Name</span></span>|<span data-ttu-id="d0c0b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d0c0b-105">SQL Server</span></span>|  
|<span data-ttu-id="d0c0b-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d0c0b-106">Event ID</span></span>|<span data-ttu-id="d0c0b-107">5233</span><span class="sxs-lookup"><span data-stu-id="d0c0b-107">5233</span></span>|  
|<span data-ttu-id="d0c0b-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d0c0b-108">Event Source</span></span>|<span data-ttu-id="d0c0b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d0c0b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d0c0b-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d0c0b-110">Component</span></span>|<span data-ttu-id="d0c0b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d0c0b-111">SQLEngine</span></span>|  
|<span data-ttu-id="d0c0b-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d0c0b-112">Symbolic Name</span></span>|<span data-ttu-id="d0c0b-113">DBCC4_INCORRECT_VALUE_IN_PAGE_HEADER_NO_METADATA</span><span class="sxs-lookup"><span data-stu-id="d0c0b-113">DBCC4_INCORRECT_VALUE_IN_PAGE_HEADER_NO_METADATA</span></span>|  
|<span data-ttu-id="d0c0b-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d0c0b-114">Message Text</span></span>|<span data-ttu-id="d0c0b-115">테이블 오류: 할당 단위 ID A_ID, 페이지 P_ID.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-115">Table error: alloc unit ID A_ID, page P_ID.</span></span> <span data-ttu-id="d0c0b-116">테스트(TEST)에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-116">The test (TEST) failed.</span></span> <span data-ttu-id="d0c0b-117">값은 VAL1과(와) VAL2입니다.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-117">The values are VAL1 and VAL2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d0c0b-118">설명</span><span class="sxs-lookup"><span data-stu-id="d0c0b-118">Explanation</span></span>  
 <span data-ttu-id="d0c0b-119">페이지 머리글이 손상되어 페이지 *P_ID* 감사에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-119">Page *P_ID* has failed auditing due to a corruption in its page header.</span></span> <span data-ttu-id="d0c0b-120">TEST의 문자열로 실패한 실제 테스트를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-120">The string in TEST gives the actual test that failed.</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="d0c0b-121">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="d0c0b-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="d0c0b-122">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="d0c0b-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="d0c0b-124">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d0c0b-125">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="d0c0b-126">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="d0c0b-127">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="d0c0b-128">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="d0c0b-129">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="d0c0b-130">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="d0c0b-130">Restore from Backup</span></span>  
 <span data-ttu-id="d0c0b-131">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="d0c0b-132">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="d0c0b-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="d0c0b-133">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="d0c0b-133">Not applicable.</span></span> <span data-ttu-id="d0c0b-134">이 오류를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-134">This error cannot be repaired.</span></span> <span data-ttu-id="d0c0b-135">백업에서 데이터베이스를 복원할 수 없으면 Microsoft CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0c0b-135">If you cannot restore the database from a backup, contact Microsoft Customer Service and Support (CSS).</span></span>  
  
  
