---
title: MSSQLSERVER_8974 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8974 (Database Engine error)
ms.assetid: 52098678-0858-4a14-ad07-37ebbafca5fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff3107f5b62caf04e232532c2d2b93d5da19fb53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661665"
---
# <a name="mssqlserver_8974"></a><span data-ttu-id="2f54a-102">MSSQLSERVER_8974</span><span class="sxs-lookup"><span data-stu-id="2f54a-102">MSSQLSERVER_8974</span></span>
    
## <a name="details"></a><span data-ttu-id="2f54a-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="2f54a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f54a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="2f54a-104">Product Name</span></span>|<span data-ttu-id="2f54a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2f54a-105">SQL Server</span></span>|  
|<span data-ttu-id="2f54a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="2f54a-106">Event ID</span></span>|<span data-ttu-id="2f54a-107">8974</span><span class="sxs-lookup"><span data-stu-id="2f54a-107">8974</span></span>|  
|<span data-ttu-id="2f54a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="2f54a-108">Event Source</span></span>|<span data-ttu-id="2f54a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2f54a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2f54a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="2f54a-110">Component</span></span>|<span data-ttu-id="2f54a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2f54a-111">SQLEngine</span></span>|  
|<span data-ttu-id="2f54a-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="2f54a-112">Symbolic Name</span></span>|<span data-ttu-id="2f54a-113">DBCC3_OFF_ROW_DATA_NODE_HAS_TWO_PARENTS</span><span class="sxs-lookup"><span data-stu-id="2f54a-113">DBCC3_OFF_ROW_DATA_NODE_HAS_TWO_PARENTS</span></span>|  
|<span data-ttu-id="2f54a-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="2f54a-114">Message Text</span></span>|<span data-ttu-id="2f54a-115">테이블 오류: 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형).</span><span class="sxs-lookup"><span data-stu-id="2f54a-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="2f54a-116">페이지 P_ID1, 슬롯 S_ID1, 텍스트 ID TEXT_ID의 행 밖 데이터 노드를 페이지 P_ID2, 슬롯 S_ID2 및 페이지 P_ID3, 슬롯 P_ID3에서 가리키고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f54a-116">The off-row data node at page P_ID1, slot S_ID1, text ID TEXT_ID is pointed to by page P_ID2, slot S_ID2 and by page P_ID3, slot P_ID3.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2f54a-117">설명</span><span class="sxs-lookup"><span data-stu-id="2f54a-117">Explanation</span></span>  
 <span data-ttu-id="2f54a-118">행 밖 데이터 노드에 이를 자식 노드로 나열하는 두 개의 데이터 또는 인덱스 레코드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f54a-118">An off-row data node has two data or index records that list it as a child node.</span></span> <span data-ttu-id="2f54a-119">노드에는 부모 노드가 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f54a-119">A node can have only one parent node.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2f54a-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="2f54a-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="2f54a-121">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="2f54a-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="2f54a-122">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f54a-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="2f54a-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f54a-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="2f54a-124">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f54a-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="2f54a-125">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f54a-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="2f54a-126">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2f54a-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="2f54a-127">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f54a-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="2f54a-128">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f54a-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="2f54a-129">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f54a-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="2f54a-130">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="2f54a-130">Restore from Backup</span></span>  
 <span data-ttu-id="2f54a-131">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="2f54a-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="2f54a-132">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="2f54a-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="2f54a-133">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f54a-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="2f54a-134">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="2f54a-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="2f54a-135">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f54a-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2f54a-136">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="2f54a-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="2f54a-137">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="2f54a-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="2f54a-138">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="2f54a-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="2f54a-139">페이지 *P_ID1*의 행 밖 데이터 노드가 삭제되고 페이지 *P_ID2* 및 *P_ID3*의 참조가 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f54a-139">The off-row data node on page *P_ID1* will be deleted and both references on pages *P_ID2* and *P_ID3* will be deleted.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2f54a-140">이 복구로 인해 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f54a-140">This repair might cause data loss.</span></span>  
  
  
