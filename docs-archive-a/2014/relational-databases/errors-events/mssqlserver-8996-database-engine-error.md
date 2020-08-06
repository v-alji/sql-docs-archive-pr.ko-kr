---
title: MSSQLSERVER_8996 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8996 (Database Engine error)
ms.assetid: 4e655cdc-945a-4a18-95dd-75f050563d26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d0cb5f0294ea471a6e300adbabc0f7b55632994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653874"
---
# <a name="mssqlserver_8996"></a><span data-ttu-id="167a6-102">MSSQLSERVER_8996</span><span class="sxs-lookup"><span data-stu-id="167a6-102">MSSQLSERVER_8996</span></span>
    
## <a name="details"></a><span data-ttu-id="167a6-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="167a6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="167a6-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="167a6-104">Product Name</span></span>|<span data-ttu-id="167a6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="167a6-105">SQL Server</span></span>|  
|<span data-ttu-id="167a6-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="167a6-106">Event ID</span></span>|<span data-ttu-id="167a6-107">8996</span><span class="sxs-lookup"><span data-stu-id="167a6-107">8996</span></span>|  
|<span data-ttu-id="167a6-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="167a6-108">Event Source</span></span>|<span data-ttu-id="167a6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="167a6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="167a6-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="167a6-110">Component</span></span>|<span data-ttu-id="167a6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="167a6-111">SQLEngine</span></span>|  
|<span data-ttu-id="167a6-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="167a6-112">Symbolic Name</span></span>|<span data-ttu-id="167a6-113">DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP</span><span class="sxs-lookup"><span data-stu-id="167a6-113">DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP</span></span>|  
|<span data-ttu-id="167a6-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="167a6-114">Message Text</span></span>|<span data-ttu-id="167a6-115">개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)의 IAM 페이지 P_ID이(가) 파일 그룹 FG_ID1의 페이지를 제어합니다. 이 페이지는 파일 그룹 FG_ID2에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="167a6-115">IAM page P_ID for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) controls pages in filegroup FG_ID1, that should be in filegroup FG_ID2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="167a6-116">설명</span><span class="sxs-lookup"><span data-stu-id="167a6-116">Explanation</span></span>  
 <span data-ttu-id="167a6-117">파일 그룹 *FG_ID1*의 IAM(Index Allocation Map) 페이지 *P_ID*에 파일 그룹 *FG_ID2*의 익스텐트가 잘못 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="167a6-117">The index allocation map (IAM) page *P_ID* in filegroup *FG_ID1* incorrectly includes extents from filegroup *FG_ID2*.</span></span> <span data-ttu-id="167a6-118">IAM 페이지에 대한 모든 익스텐트는 IAM 페이지와 같은 파일 그룹에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="167a6-118">All extents for an IAM page should be in the same filegroup as the IAM page itself.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="167a6-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="167a6-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="167a6-120">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="167a6-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="167a6-121">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="167a6-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="167a6-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="167a6-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="167a6-123">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="167a6-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="167a6-124">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="167a6-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="167a6-125">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="167a6-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="167a6-126">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="167a6-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="167a6-127">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="167a6-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="167a6-128">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="167a6-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="167a6-129">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="167a6-129">Restore from Backup</span></span>  
 <span data-ttu-id="167a6-130">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="167a6-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="167a6-131">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="167a6-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="167a6-132">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="167a6-132">Not applicable.</span></span> <span data-ttu-id="167a6-133">이 오류를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="167a6-133">This error cannot be repaired.</span></span> <span data-ttu-id="167a6-134">백업에서 데이터베이스를 복원할 수 없으면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="167a6-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
