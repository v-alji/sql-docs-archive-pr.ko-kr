---
title: MSSQLSERVER_7905 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7905 (Database Engine error)
ms.assetid: cf19fbbb-7158-45f2-8778-8f3cad7f574a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 253bf03c1bfacccfd809cd417163eb9d54644f28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651002"
---
# <a name="mssqlserver_7905"></a><span data-ttu-id="aac81-102">MSSQLSERVER_7905</span><span class="sxs-lookup"><span data-stu-id="aac81-102">MSSQLSERVER_7905</span></span>
    
## <a name="details"></a><span data-ttu-id="aac81-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="aac81-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aac81-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="aac81-104">Product Name</span></span>|<span data-ttu-id="aac81-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aac81-105">SQL Server</span></span>|  
|<span data-ttu-id="aac81-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="aac81-106">Event ID</span></span>|<span data-ttu-id="aac81-107">7905</span><span class="sxs-lookup"><span data-stu-id="aac81-107">7905</span></span>|  
|<span data-ttu-id="aac81-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="aac81-108">Event Source</span></span>|<span data-ttu-id="aac81-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aac81-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aac81-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="aac81-110">Component</span></span>|<span data-ttu-id="aac81-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aac81-111">SQLEngine</span></span>|  
|<span data-ttu-id="aac81-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="aac81-112">Symbolic Name</span></span>|<span data-ttu-id="aac81-113">DBCC2_FS_INVALID_ROWSET_DIRECTORY</span><span class="sxs-lookup"><span data-stu-id="aac81-113">DBCC2_FS_INVALID_ROWSET_DIRECTORY</span></span>|  
|<span data-ttu-id="aac81-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="aac81-114">Message Text</span></span>|<span data-ttu-id="aac81-115">데이터베이스 오류: 디렉터리 'DIRECTORY'이(가) 잘못된 FileStream 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="aac81-115">Database error: The directory 'DIRECTORY' is not a valid Filestream directory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aac81-116">설명</span><span class="sxs-lookup"><span data-stu-id="aac81-116">Explanation</span></span>  
 <span data-ttu-id="aac81-117">'ghost'와 같은 특수한 행 집합 디렉터리 이름을 제외하고, 행 집합 디렉터리의 이름은 파티션의 파티션 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="aac81-117">The name of a rowset directory is the partition ID of the partition, except for the special rowset directory names such as 'ghost'.</span></span> <span data-ttu-id="aac81-118">행 집합 디렉터리 이름을 파티션 ID로 변환할 수 없는 경우 이 디렉터리는 잘못된 열 집합 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="aac81-118">If a rowset directory name cannot be converted to a partition ID, the directory is not a valid rowset directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aac81-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="aac81-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="aac81-120">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="aac81-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="aac81-121">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="aac81-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="aac81-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="aac81-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="aac81-123">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="aac81-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="aac81-124">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="aac81-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="aac81-125">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="aac81-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="aac81-126">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="aac81-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="aac81-127">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aac81-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="aac81-128">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aac81-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="aac81-129">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="aac81-129">Restore from Backup</span></span>  
 <span data-ttu-id="aac81-130">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="aac81-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="aac81-131">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="aac81-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="aac81-132">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="aac81-132">Not applicable.</span></span> <span data-ttu-id="aac81-133">이 오류를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aac81-133">This error cannot be repaired.</span></span> <span data-ttu-id="aac81-134">백업에서 데이터베이스를 복원할 수 없으면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="aac81-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
