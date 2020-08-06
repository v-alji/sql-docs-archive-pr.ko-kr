---
title: MSSQLSERVER_7935 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7935 (Database Engine error)
ms.assetid: 45ab21a3-024a-4523-9bd9-1175d01f9c8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a798438213fecf7a6867056c5fe1db033bc6beb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651691"
---
# <a name="mssqlserver_7935"></a><span data-ttu-id="d6af9-102">MSSQLSERVER_7935</span><span class="sxs-lookup"><span data-stu-id="d6af9-102">MSSQLSERVER_7935</span></span>
    
## <a name="details"></a><span data-ttu-id="d6af9-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d6af9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6af9-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d6af9-104">Product Name</span></span>|<span data-ttu-id="d6af9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d6af9-105">SQL Server</span></span>|  
|<span data-ttu-id="d6af9-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d6af9-106">Event ID</span></span>|<span data-ttu-id="d6af9-107">7935</span><span class="sxs-lookup"><span data-stu-id="d6af9-107">7935</span></span>|  
|<span data-ttu-id="d6af9-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d6af9-108">Event Source</span></span>|<span data-ttu-id="d6af9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d6af9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d6af9-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d6af9-110">Component</span></span>|<span data-ttu-id="d6af9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d6af9-111">SQLEngine</span></span>|  
|<span data-ttu-id="d6af9-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d6af9-112">Symbolic Name</span></span>|<span data-ttu-id="d6af9-113">DBCC2_FS_MISSING_COLUMN</span><span class="sxs-lookup"><span data-stu-id="d6af9-113">DBCC2_FS_MISSING_COLUMN</span></span>|  
|<span data-ttu-id="d6af9-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d6af9-114">Message Text</span></span>|<span data-ttu-id="d6af9-115">테이블 오류: 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID의 열에 대한 Filestream 디렉터리 ID F_ID이(가) 있지만 해당 열이 파티션에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6af9-115">Table error: A Filestream directory ID F_ID exists for a column of object ID O_ID, index ID I_ID, partition ID PN_ID, but that column does not exist in the partition.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d6af9-116">설명</span><span class="sxs-lookup"><span data-stu-id="d6af9-116">Explanation</span></span>  
 <span data-ttu-id="d6af9-117">DBCC CHECKDB를 실행하는 동안 지정된 개체의 열에 대한 FILESTREAM 디렉터리를 찾았지만 파티션의 해당 메타데이터에는 이 열이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6af9-117">During DBCC CHECKDB, a FILESTREAM directory was found for a column in the specified object; however, the column was not found in the corresponding metadata of the partition.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d6af9-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d6af9-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="d6af9-119">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="d6af9-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="d6af9-120">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6af9-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="d6af9-121">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6af9-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="d6af9-122">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6af9-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d6af9-123">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6af9-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="d6af9-124">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d6af9-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="d6af9-125">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6af9-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="d6af9-126">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6af9-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="d6af9-127">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6af9-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="d6af9-128">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="d6af9-128">Restore from Backup</span></span>  
 <span data-ttu-id="d6af9-129">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="d6af9-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="d6af9-130">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="d6af9-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="d6af9-131">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="d6af9-131">Not applicable.</span></span> <span data-ttu-id="d6af9-132">이 오류는 자동으로 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6af9-132">This error cannot be repaired automatically.</span></span> <span data-ttu-id="d6af9-133">백업에서 데이터베이스를 복원할 수 없으면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6af9-133">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
