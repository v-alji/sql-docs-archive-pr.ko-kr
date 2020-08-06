---
title: MSSQLSERVER_7906 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7906 (Database Engine error)
ms.assetid: 9638a764-4ac1-40ae-a614-2726ebcc6ba4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57485a8f330f186a4abd83182c6035168ed38e0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651000"
---
# <a name="mssqlserver_7906"></a><span data-ttu-id="0a52d-102">MSSQLSERVER_7906</span><span class="sxs-lookup"><span data-stu-id="0a52d-102">MSSQLSERVER_7906</span></span>
    
## <a name="details"></a><span data-ttu-id="0a52d-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="0a52d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a52d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="0a52d-104">Product Name</span></span>|<span data-ttu-id="0a52d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0a52d-105">SQL Server</span></span>|  
|<span data-ttu-id="0a52d-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="0a52d-106">Event ID</span></span>|<span data-ttu-id="0a52d-107">7906</span><span class="sxs-lookup"><span data-stu-id="0a52d-107">7906</span></span>|  
|<span data-ttu-id="0a52d-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="0a52d-108">Event Source</span></span>|<span data-ttu-id="0a52d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0a52d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0a52d-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0a52d-110">Component</span></span>|<span data-ttu-id="0a52d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0a52d-111">SQLEngine</span></span>|  
|<span data-ttu-id="0a52d-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="0a52d-112">Symbolic Name</span></span>|<span data-ttu-id="0a52d-113">DBCC2_FS_INVALID_TOP_LEVEL_FILE</span><span class="sxs-lookup"><span data-stu-id="0a52d-113">DBCC2_FS_INVALID_TOP_LEVEL_FILE</span></span>|  
|<span data-ttu-id="0a52d-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="0a52d-114">Message Text</span></span>|<span data-ttu-id="0a52d-115">데이터베이스 오류: 파일 'FILE'이 잘못된 Filestream 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-115">Database error: The file 'FILE' is not a valid Filestream file.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0a52d-116">설명</span><span class="sxs-lookup"><span data-stu-id="0a52d-116">Explanation</span></span>  
 <span data-ttu-id="0a52d-117">Filestream 데이터 공간 바로 아래에는 'filestream.hdr'과 같은 일부 특수한 파일을 제외한 다른 파일이 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-117">Except for some special files such as, 'filestream.hdr', no files should be found directly under the Filestream dataspace.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0a52d-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="0a52d-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="0a52d-119">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="0a52d-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="0a52d-120">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a52d-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="0a52d-121">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a52d-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="0a52d-122">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a52d-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="0a52d-123">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a52d-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="0a52d-124">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0a52d-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="0a52d-125">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a52d-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="0a52d-126">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="0a52d-127">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="0a52d-128">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="0a52d-128">Restore from Backup</span></span>  
 <span data-ttu-id="0a52d-129">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="0a52d-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="0a52d-130">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="0a52d-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="0a52d-131">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="0a52d-131">Not applicable.</span></span> <span data-ttu-id="0a52d-132">이 오류를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-132">This error cannot be repaired.</span></span> <span data-ttu-id="0a52d-133">백업에서 데이터베이스를 복원할 수 없으면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a52d-133">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
