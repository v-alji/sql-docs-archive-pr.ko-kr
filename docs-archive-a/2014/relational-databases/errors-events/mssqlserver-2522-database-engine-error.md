---
title: MSSQLSERVER_2522 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2522 (Database Engine error)
ms.assetid: 19b9b00c-330f-4dd3-9052-9d88bce83849
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60446c21599c02ee9c4bc96789b106b49b71582a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646524"
---
# <a name="mssqlserver_2522"></a><span data-ttu-id="12570-102">MSSQLSERVER_2522</span><span class="sxs-lookup"><span data-stu-id="12570-102">MSSQLSERVER_2522</span></span>
    
## <a name="details"></a><span data-ttu-id="12570-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="12570-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12570-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="12570-104">Product Name</span></span>|<span data-ttu-id="12570-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="12570-105">SQL Server</span></span>|  
|<span data-ttu-id="12570-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="12570-106">Event ID</span></span>|<span data-ttu-id="12570-107">2522</span><span class="sxs-lookup"><span data-stu-id="12570-107">2522</span></span>|  
|<span data-ttu-id="12570-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="12570-108">Event Source</span></span>|<span data-ttu-id="12570-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="12570-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="12570-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="12570-110">Component</span></span>|<span data-ttu-id="12570-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="12570-111">SQLEngine</span></span>|  
|<span data-ttu-id="12570-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="12570-112">Symbolic Name</span></span>|<span data-ttu-id="12570-113">DBCC_INDEX_FILEGROUP_IS_INVALID</span><span class="sxs-lookup"><span data-stu-id="12570-113">DBCC_INDEX_FILEGROUP_IS_INVALID</span></span>|  
|<span data-ttu-id="12570-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="12570-114">Message Text</span></span>|<span data-ttu-id="12570-115">파일 그룹 F_NAME이(가) 잘못되었으므로 테이블 O_NAME의 인덱스 I_NAME을(를) 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12570-115">Unable to process index I_NAME of table O_NAME because filegroup F_NAME is invalid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="12570-116">설명</span><span class="sxs-lookup"><span data-stu-id="12570-116">Explanation</span></span>  
 <span data-ttu-id="12570-117">이 정보 메시지는 인덱스의 메타데이터에 저장된 파일 그룹 ID 중 하나가 없기 때문에 인덱스를 검사할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="12570-117">This informational message indicates that the index cannot be checked because one of the filegroup IDs that is stored in the metadata of the index does not exist.</span></span> <span data-ttu-id="12570-118">잘못된 파일 그룹 ID가 데이터 자체, LOB(Large Object) 데이터 또는 행 오버플로 데이터에 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12570-118">The filegroup ID that is not valid might pertain to the data itself, or to the large object (LOB) data, or to the row-overflow data.</span></span>  
  
 <span data-ttu-id="12570-119">문제가 없으면 같은 개체에 대한 다른 인덱스를 모두 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="12570-119">If there are no problems, all other indexes of the same object will be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="12570-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="12570-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="12570-121">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="12570-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="12570-122">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="12570-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="12570-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="12570-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="12570-124">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="12570-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="12570-125">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="12570-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="12570-126">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="12570-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="12570-127">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="12570-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="12570-128">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12570-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="12570-129">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="12570-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="12570-130">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="12570-130">Restore from Backup</span></span>  
 <span data-ttu-id="12570-131">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="12570-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="12570-132">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="12570-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="12570-133">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="12570-133">Not applicable.</span></span> <span data-ttu-id="12570-134">이 오류는 자동으로 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12570-134">This error cannot be repaired automatically.</span></span>  
  
  
