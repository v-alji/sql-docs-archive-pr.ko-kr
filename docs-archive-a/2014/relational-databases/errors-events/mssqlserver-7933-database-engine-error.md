---
title: MSSQLSERVER_7933 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7933 (Database Engine error)
ms.assetid: 722bd2c6-0fb9-4838-954a-439744c6ac4b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7ff25201d56b1bf55a0ecafbba7fbc787dc2fb64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651696"
---
# <a name="mssqlserver_7933"></a><span data-ttu-id="2596b-102">MSSQLSERVER_7933</span><span class="sxs-lookup"><span data-stu-id="2596b-102">MSSQLSERVER_7933</span></span>
    
## <a name="details"></a><span data-ttu-id="2596b-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="2596b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2596b-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="2596b-104">Product Name</span></span>|<span data-ttu-id="2596b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2596b-105">SQL Server</span></span>|  
|<span data-ttu-id="2596b-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="2596b-106">Event ID</span></span>|<span data-ttu-id="2596b-107">7933</span><span class="sxs-lookup"><span data-stu-id="2596b-107">7933</span></span>|  
|<span data-ttu-id="2596b-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="2596b-108">Event Source</span></span>|<span data-ttu-id="2596b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2596b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2596b-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="2596b-110">Component</span></span>|<span data-ttu-id="2596b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2596b-111">SQLEngine</span></span>|  
|<span data-ttu-id="2596b-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="2596b-112">Symbolic Name</span></span>|<span data-ttu-id="2596b-113">DBCC2_FS_ORPHANED_ROWSET_DIRECTORY</span><span class="sxs-lookup"><span data-stu-id="2596b-113">DBCC2_FS_ORPHANED_ROWSET_DIRECTORY</span></span>|  
|<span data-ttu-id="2596b-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="2596b-114">Message Text</span></span>|<span data-ttu-id="2596b-115">테이블 오류: 파티션에 대한 Filestream 디렉터리 ID F_ID이(가) 있지만 해당 파티션이 데이터베이스에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-115">Table error: A Filestream directory ID F_ID exists for a partition, but the corresponding partition does not exist in the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2596b-116">설명</span><span class="sxs-lookup"><span data-stu-id="2596b-116">Explanation</span></span>  
 <span data-ttu-id="2596b-117">DBCC CHECKDB를 실행하는 동안 FILESTREAM 데이터 공간에서 행 집합 디렉터리를 찾았지만 해당 파티션이 데이터베이스에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-117">During DBCC CHECKDB, a rowset directory was found in the FILESTREAM dataspace; however, its corresponding partition is missing in the database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2596b-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="2596b-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="2596b-119">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="2596b-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="2596b-120">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="2596b-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="2596b-121">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2596b-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="2596b-122">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="2596b-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="2596b-123">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="2596b-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="2596b-124">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2596b-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="2596b-125">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="2596b-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="2596b-126">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="2596b-127">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="2596b-128">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="2596b-128">Restore from Backup</span></span>  
 <span data-ttu-id="2596b-129">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="2596b-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="2596b-130">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="2596b-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="2596b-131">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="2596b-131">Not applicable.</span></span> <span data-ttu-id="2596b-132">이 오류는 자동으로 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2596b-132">This error cannot be repaired automatically.</span></span> <span data-ttu-id="2596b-133">백업에서 데이터베이스를 복원할 수 없으면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="2596b-133">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
