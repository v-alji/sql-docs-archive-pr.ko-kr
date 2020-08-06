---
title: MSSQLSERVER_2512 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2512 (Database Engine error)
ms.assetid: 989b527f-5b02-403c-9b7f-51580f4e7688
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da121c8b49ab8290c494d33f0f2a0ba6fded9e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730712"
---
# <a name="mssqlserver_2512"></a><span data-ttu-id="0448d-102">MSSQLSERVER_2512</span><span class="sxs-lookup"><span data-stu-id="0448d-102">MSSQLSERVER_2512</span></span>
    
## <a name="details"></a><span data-ttu-id="0448d-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="0448d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0448d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="0448d-104">Product Name</span></span>|<span data-ttu-id="0448d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0448d-105">SQL Server</span></span>|  
|<span data-ttu-id="0448d-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="0448d-106">Event ID</span></span>|<span data-ttu-id="0448d-107">2512</span><span class="sxs-lookup"><span data-stu-id="0448d-107">2512</span></span>|  
|<span data-ttu-id="0448d-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="0448d-108">Event Source</span></span>|<span data-ttu-id="0448d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0448d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0448d-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0448d-110">Component</span></span>|<span data-ttu-id="0448d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0448d-111">SQLEngine</span></span>|  
|<span data-ttu-id="0448d-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="0448d-112">Symbolic Name</span></span>|<span data-ttu-id="0448d-113">DBCC_DUPLICATE_KEYS</span><span class="sxs-lookup"><span data-stu-id="0448d-113">DBCC_DUPLICATE_KEYS</span></span>|  
|<span data-ttu-id="0448d-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="0448d-114">Message Text</span></span>|<span data-ttu-id="0448d-115">테이블 오류: 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형).</span><span class="sxs-lookup"><span data-stu-id="0448d-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="0448d-116">페이지 P_ID1, 슬롯 SLOT1과(와) 페이지 P_ID2, 슬롯 P_ID2의 키가 중복되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0448d-116">Duplicate keys on page P_ID1 slot SLOT1 and page P_ID2 slot SLOT2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0448d-117">설명</span><span class="sxs-lookup"><span data-stu-id="0448d-117">Explanation</span></span>  
 <span data-ttu-id="0448d-118">두 개의 지정된 슬롯에 `uniqueifiers`를 포함하는 동일한 키가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0448d-118">The two specified slots have identical keys, including any `uniqueifiers`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0448d-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="0448d-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="0448d-120">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="0448d-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="0448d-121">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="0448d-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="0448d-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="0448d-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="0448d-123">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="0448d-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="0448d-124">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="0448d-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="0448d-125">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0448d-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="0448d-126">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="0448d-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="0448d-127">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0448d-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="0448d-128">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0448d-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="0448d-129">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="0448d-129">Restore from Backup</span></span>  
 <span data-ttu-id="0448d-130">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="0448d-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="0448d-131">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="0448d-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="0448d-132">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="0448d-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="0448d-133">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="0448d-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="0448d-134">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="0448d-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="0448d-135">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="0448d-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="0448d-136">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="0448d-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="0448d-137">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="0448d-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="0448d-138">레코드가 삭제되었거나 인덱스가 고유하지 않은 경우 DBCC는 인덱스를 다시 작성하여 이 문제를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0448d-138">If either record is a ghost or the index is nonunique, DBCC can repair this problem by rebuilding the index.</span></span> <span data-ttu-id="0448d-139">그렇지 않으면 필요한 경우 REPAIR는 *P_ID2* 페이지의 *SLOT2* 슬롯을 삭제하거나 해당 슬롯을 삭제한 것으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0448d-139">Otherwise, if necessary, REPAIR will delete slot *SLOT2* on page *P_ID2* or mark the slot as a ghost.</span></span>  
  
  
