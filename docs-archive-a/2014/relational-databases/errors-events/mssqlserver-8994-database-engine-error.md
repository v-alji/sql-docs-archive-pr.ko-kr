---
title: MSSQLSERVER_8994 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8994 (Database Engine error)
ms.assetid: 8f4b0e2f-04c0-46e4-9208-20a7085d7a1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0bcc0b1db100b70390c09e9c825dbfd068d968af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646512"
---
# <a name="mssqlserver_8994"></a><span data-ttu-id="162e8-102">MSSQLSERVER_8994</span><span class="sxs-lookup"><span data-stu-id="162e8-102">MSSQLSERVER_8994</span></span>
    
## <a name="details"></a><span data-ttu-id="162e8-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="162e8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="162e8-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="162e8-104">Product Name</span></span>|<span data-ttu-id="162e8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="162e8-105">SQL Server</span></span>|  
|<span data-ttu-id="162e8-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="162e8-106">Event ID</span></span>|<span data-ttu-id="162e8-107">8994</span><span class="sxs-lookup"><span data-stu-id="162e8-107">8994</span></span>|  
|<span data-ttu-id="162e8-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="162e8-108">Event Source</span></span>|<span data-ttu-id="162e8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="162e8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="162e8-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="162e8-110">Component</span></span>|<span data-ttu-id="162e8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="162e8-111">SQLEngine</span></span>|  
|<span data-ttu-id="162e8-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="162e8-112">Symbolic Name</span></span>|<span data-ttu-id="162e8-113">DBCC3_MISSING_FORWARDING_ROW</span><span class="sxs-lookup"><span data-stu-id="162e8-113">DBCC3_MISSING_FORWARDING_ROW</span></span>|  
|<span data-ttu-id="162e8-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="162e8-114">Message Text</span></span>|<span data-ttu-id="162e8-115">전달 행 페이지 P_ID2, 슬롯 S_ID2에서 개체 ID O_ID, 전달되는 행 페이지 P_ID1, 슬롯 S_ID1을(를) 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="162e8-115">Object ID O_ID, forwarded row page P_ID1, slot S_ID1 should be pointed to by forwarding row page P_ID2, slot S_ID2.</span></span> <span data-ttu-id="162e8-116">전달 행이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="162e8-116">Did not encounter forwarding row.</span></span> <span data-ttu-id="162e8-117">할당 오류인 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="162e8-117">Possible allocation error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="162e8-118">설명</span><span class="sxs-lookup"><span data-stu-id="162e8-118">Explanation</span></span>  
 <span data-ttu-id="162e8-119">힙의 전달되는 행에 이 행을 가리켜야 하는 전달 행이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="162e8-119">A forwarded row in a heap is missing the forwarding row that should point to it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="162e8-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="162e8-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="162e8-121">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="162e8-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="162e8-122">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="162e8-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="162e8-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="162e8-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="162e8-124">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="162e8-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="162e8-125">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="162e8-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="162e8-126">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="162e8-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="162e8-127">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="162e8-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="162e8-128">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="162e8-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="162e8-129">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="162e8-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="162e8-130">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="162e8-130">Restore from Backup</span></span>  
 <span data-ttu-id="162e8-131">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="162e8-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="162e8-132">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="162e8-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="162e8-133">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="162e8-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="162e8-134">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="162e8-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="162e8-135">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="162e8-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="162e8-136">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="162e8-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="162e8-137">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="162e8-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="162e8-138">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="162e8-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="162e8-139">전달되는 행이 일반 데이터 행으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="162e8-139">The forwarded row will be converted to a regular data row.</span></span>  
  
  
