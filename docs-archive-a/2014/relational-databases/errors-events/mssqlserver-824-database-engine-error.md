---
title: MSSQLSERVER_824 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
ms.assetid: 2aa22246-2712-4fdb-9744-36e7e6f3175e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d57b19bc8c837b92b65728fbb0046039b862d31a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650988"
---
# <a name="mssqlserver_824"></a><span data-ttu-id="c7d76-102">MSSQLSERVER_824</span><span class="sxs-lookup"><span data-stu-id="c7d76-102">MSSQLSERVER_824</span></span>
    
## <a name="details"></a><span data-ttu-id="c7d76-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="c7d76-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7d76-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="c7d76-104">Product Name</span></span>|<span data-ttu-id="c7d76-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c7d76-105">SQL Server</span></span>|  
|<span data-ttu-id="c7d76-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="c7d76-106">Event ID</span></span>|<span data-ttu-id="c7d76-107">824</span><span class="sxs-lookup"><span data-stu-id="c7d76-107">824</span></span>|  
|<span data-ttu-id="c7d76-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="c7d76-108">Event Source</span></span>|<span data-ttu-id="c7d76-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c7d76-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c7d76-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c7d76-110">Component</span></span>|<span data-ttu-id="c7d76-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c7d76-111">SQLEngine</span></span>|  
|<span data-ttu-id="c7d76-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="c7d76-112">Symbolic Name</span></span>|<span data-ttu-id="c7d76-113">B_HARDSSERR</span><span class="sxs-lookup"><span data-stu-id="c7d76-113">B_HARDSSERR</span></span>|  
|<span data-ttu-id="c7d76-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="c7d76-114">Message Text</span></span>|<span data-ttu-id="c7d76-115">SQL Server에서 일관성 기반의 논리적인 I/O 오류가 검색되었습니다. %ls.</span><span class="sxs-lookup"><span data-stu-id="c7d76-115">SQL Server detected a logical consistency-based I/O error: %ls.</span></span> <span data-ttu-id="c7d76-116">파일 '%ls'의 오프셋 %#016I64x에서 데이터베이스 ID %d에 있는 페이지 %S_PGID의 %S_MSG 중 이 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-116">It occurred during a %S_MSG of page %S_PGID in database ID %d at offset %#016I64x in file '%ls'.</span></span>  <span data-ttu-id="c7d76-117">자세한 내용은 SQL Server 오류 로그 또는 시스템 이벤트 로그의 추가 메시지에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-117">Additional messages in the SQL Server error log or system event log may provide more detail.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c7d76-118">설명</span><span class="sxs-lookup"><span data-stu-id="c7d76-118">Explanation</span></span>  
 <span data-ttu-id="c7d76-119">이 오류는 Windows가 디스크에서 페이지를 성공적으로 읽었음을 보고하지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 해당 페이지에서 잘못된 내용을 발견했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-119">This error indicates that Windows reports that the page is successfully read from disk, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has discovered something wrong with the page.</span></span> <span data-ttu-id="c7d76-120">이 오류는 Windows에서 오류를 감지하지 못한다는 점만 제외하면 오류 823과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-120">This error is similar to error 823 except that Windows did not detect the error.</span></span> <span data-ttu-id="c7d76-121">일반적으로 이 오류는 디스크 드라이브 실패, 디스크 펌웨어 문제, 잘못된 디바이스 드라이버 등 I/O 하위 시스템의 문제를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-121">This usually indicates a problem in the I/O subsystem, such as a failing disk drive, disk firmware problems, faulty device driver, and so on.</span></span> <span data-ttu-id="c7d76-122">I/O 오류에 대한 자세한 내용은 [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))(Microsoft SQL Server I/O 기본 사항, 2장)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-122">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c7d76-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="c7d76-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="c7d76-124">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="c7d76-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="c7d76-125">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7d76-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="c7d76-126">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7d76-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred because of hardware failure.</span></span> <span data-ttu-id="c7d76-127">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7d76-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="c7d76-128">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7d76-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="c7d76-129">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="c7d76-130">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7d76-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="c7d76-131">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="c7d76-132">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="c7d76-133">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="c7d76-133">Restore from Backup</span></span>  
 <span data-ttu-id="c7d76-134">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하십시오.</span><span class="sxs-lookup"><span data-stu-id="c7d76-134">If the problem is not hardware-related and a known clean backup is available, restore the database from the backup.</span></span>  
  
 <span data-ttu-id="c7d76-135">PAGE_VERIFY CHECKSUM 옵션을 사용하도록 데이터베이스를 변경해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="c7d76-135">Consider changing the databases to use the PAGE_VERIFY CHECKSUM option.</span></span> <span data-ttu-id="c7d76-136">PAGE_VERIFY에 대한 자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-136">For information about PAGE_VERIFY, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d76-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7d76-137">See Also</span></span>  
 [<span data-ttu-id="c7d76-138">suspect_pages 테이블 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c7d76-138">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
