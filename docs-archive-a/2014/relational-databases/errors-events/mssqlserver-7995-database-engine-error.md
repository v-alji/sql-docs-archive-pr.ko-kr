---
title: MSSQLSERVER_7995 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7995 (Database Engine error)
ms.assetid: af6d6322-3cba-43d8-be97-e6ef15f8c933
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c65cf2b16c4d7a0dcf40272f8280205a111d08e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651689"
---
# <a name="mssqlserver_7995"></a><span data-ttu-id="9e49a-102">MSSQLSERVER_7995</span><span class="sxs-lookup"><span data-stu-id="9e49a-102">MSSQLSERVER_7995</span></span>
    
## <a name="details"></a><span data-ttu-id="9e49a-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9e49a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e49a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9e49a-104">Product Name</span></span>|<span data-ttu-id="9e49a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9e49a-105">SQL Server</span></span>|  
|<span data-ttu-id="9e49a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9e49a-106">Event ID</span></span>|<span data-ttu-id="9e49a-107">7995</span><span class="sxs-lookup"><span data-stu-id="9e49a-107">7995</span></span>|  
|<span data-ttu-id="9e49a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9e49a-108">Event Source</span></span>|<span data-ttu-id="9e49a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9e49a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9e49a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9e49a-110">Component</span></span>|<span data-ttu-id="9e49a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9e49a-111">SQLEngine</span></span>|  
|<span data-ttu-id="9e49a-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9e49a-112">Symbolic Name</span></span>|<span data-ttu-id="9e49a-113">DBCC2_SYSTEM_CATALOGS_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="9e49a-113">DBCC2_SYSTEM_CATALOGS_CORRUPT</span></span>|  
|<span data-ttu-id="9e49a-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9e49a-114">Message Text</span></span>|<span data-ttu-id="9e49a-115">데이터베이스 'DBNAME': 시스템 카탈로그의 일관성 오류로 인해 DBCC CHECKNAME 프로세스를 계속 진행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-115">Database 'DBNAME': consistency errors in system catalogs prevent further DBCC CHECKNAME processing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9e49a-116">설명</span><span class="sxs-lookup"><span data-stu-id="9e49a-116">Explanation</span></span>  
 <span data-ttu-id="9e49a-117">DBCC CHECKDB 프로세스는 다음 세 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-117">The DBCC CHECKDB process consists of the following three stages:</span></span>  
  
1.  <span data-ttu-id="9e49a-118">할당을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-118">Allocation checks.</span></span> <span data-ttu-id="9e49a-119">이는 DBCC CHECKALLOC을 실행하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-119">This is equivalent to running DBCC CHECKALLOC.</span></span>  
  
2.  <span data-ttu-id="9e49a-120">시스템 테이블의 일관성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-120">System tables consistency checks.</span></span> <span data-ttu-id="9e49a-121">이는 몇몇 필수적인 시스템 기본 테이블에 대해 DBCC CHECKTABLE을 실행하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-121">This is equivalent to running DBCC CHECKTABLE on a small list of necessary system base tables.</span></span>  
  
3.  <span data-ttu-id="9e49a-122">데이터베이스 일관성 검사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-122">Complete database consistency checks.</span></span>  
  
 <span data-ttu-id="9e49a-123">MSSQLEngine_7995 오류는 2단계에서 발생하며 DBCC CHECKDB에서 명령으로 복구할 수 없거나 REPAIR가 지정되지 않은 오류를 발견했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-123">MSSQLEngine_7995 is raised in stage 2 to indicate that DBCC CHECKDB has found errors that the command cannot repair or that REPAIR has not been specified.</span></span> <span data-ttu-id="9e49a-124">검사 중인 시스템 기본 테이블에 데이터베이스의 모든 개체에 대한 메타데이터가 저장되어 있거나 시스템 기본 테이블이 손상되어 DBCC CHECKDB는 3단계로 계속 진행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-124">DBCC CHECKDB cannot continue with stage 3 because either the system base tables in question store the metadata for all objects in the database or the system base tables are corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9e49a-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9e49a-125">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="9e49a-126">하드웨어 오류 찾기</span><span class="sxs-lookup"><span data-stu-id="9e49a-126">Look for Hardware Failure</span></span>  
 <span data-ttu-id="9e49a-127">하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e49a-127">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="9e49a-128">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e49a-128">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="9e49a-129">로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e49a-129">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="9e49a-130">데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e49a-130">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="9e49a-131">시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="9e49a-131">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="9e49a-132">쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e49a-132">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="9e49a-133">마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-133">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="9e49a-134">여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e49a-134">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="9e49a-135">백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="9e49a-135">Restore from Backup</span></span>  
 <span data-ttu-id="9e49a-136">하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="9e49a-136">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="9e49a-137">DBCC CHECKDB 실행</span><span class="sxs-lookup"><span data-stu-id="9e49a-137">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="9e49a-138">정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e49a-138">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="9e49a-139">DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면</span><span class="sxs-lookup"><span data-stu-id="9e49a-139">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="9e49a-140">적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e49a-140">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="9e49a-141">REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="9e49a-141">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="9e49a-142">REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="9e49a-142">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="9e49a-143">REPAIR 옵션의 실행 결과</span><span class="sxs-lookup"><span data-stu-id="9e49a-143">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="9e49a-144">오류 목록을 검사하여 REPAIR가 각각에 대해 수행할 작업을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e49a-144">Examine the list of errors to see what REPAIR will do for each.</span></span>  
  
  
