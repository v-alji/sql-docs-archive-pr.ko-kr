---
title: 성능 카운터 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], performance counters
- performance counters [Integration Services]
- data flow [Integration Services], performance
- counters [Integration Services]
- data flow engine [Integration Services]
ms.assetid: 11e17f4e-72ed-44d7-a71d-a68937a78e4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b20ac056894066114883153030943bec1c05963
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650156"
---
# <a name="performance-counters"></a><span data-ttu-id="f2a9f-102">성능 카운터</span><span class="sxs-lookup"><span data-stu-id="f2a9f-102">Performance Counters</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="f2a9f-103">는 데이터 흐름 엔진의 성능을 모니터링하는 데 사용할 수 있는 성능 카운터 집합을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-103">installs a set of performance counters that you can use to monitor the performance of the data flow engine.</span></span> <span data-ttu-id="f2a9f-104">예를 들어 "Buffers spooled" 카운터를 보면 패키지가 실행되는 동안 데이터 버퍼가 디스크에 임시로 기록되는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-104">For example, you can watch the "Buffers spooled" counter to determine whether data buffers are being written to disk temporarily while a package is running.</span></span> <span data-ttu-id="f2a9f-105">이러한 스와핑은 성능을 저하시키고 컴퓨터에 메모리가 부족함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-105">This swapping reduces performance and indicates that the computer has insufficient memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2a9f-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 을 실행하는 컴퓨터에 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]를 설치한 다음 해당 컴퓨터를 [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]로 업그레이드하는 경우 업그레이드 프로세스는 컴퓨터에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 성능 카운터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-106">If you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on a computer that is running [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], and then upgrade that computer to [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)], the upgrade process removes the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] performance counters from the computer.</span></span> <span data-ttu-id="f2a9f-107">컴퓨터에 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 성능 카운터를 복원하려면 복원 모드에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-107">To restore the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] performance counters on the computer, run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup in repair mode.</span></span>  
  
 <span data-ttu-id="f2a9f-108">다음 표에서는 성능 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-108">The following table describes the performance counters.</span></span>  
  
|<span data-ttu-id="f2a9f-109">성능 카운터</span><span class="sxs-lookup"><span data-stu-id="f2a9f-109">Performance counter</span></span>|<span data-ttu-id="f2a9f-110">Description</span><span class="sxs-lookup"><span data-stu-id="f2a9f-110">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="f2a9f-111">BLOB bytes read</span><span class="sxs-lookup"><span data-stu-id="f2a9f-111">BLOB bytes read</span></span>|<span data-ttu-id="f2a9f-112">데이터 흐름 엔진이 모든 원본에서 읽어 온 BLOB(Binary Large Object) 데이터의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-112">The number of bytes of binary large object (BLOB) data that the data flow engine has read from all sources.</span></span>|  
|<span data-ttu-id="f2a9f-113">BLOB bytes written</span><span class="sxs-lookup"><span data-stu-id="f2a9f-113">BLOB bytes written</span></span>|<span data-ttu-id="f2a9f-114">데이터 흐름 엔진이 모든 대상에 기록한 전체 BLOB 데이터의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-114">The number of bytes of BLOB data that the data flow engine has written to all destinations.</span></span>|  
|<span data-ttu-id="f2a9f-115">BLOB files in use</span><span class="sxs-lookup"><span data-stu-id="f2a9f-115">BLOB files in use</span></span>|<span data-ttu-id="f2a9f-116">데이터 흐름 엔진이 현재 스풀링을 위해 사용하고 있는 BLOB 파일 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-116">The number of BLOB files that the data flow engine currently is using for spooling.</span></span>|  
|<span data-ttu-id="f2a9f-117">Buffer memory</span><span class="sxs-lookup"><span data-stu-id="f2a9f-117">Buffer memory</span></span>|<span data-ttu-id="f2a9f-118">현재 사용 중인 메모리의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-118">The amount of memory that is in use.</span></span> <span data-ttu-id="f2a9f-119">여기에는 실제 메모리와 가상 메모리가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-119">This may include both physical and virtual memory.</span></span> <span data-ttu-id="f2a9f-120">이 값이 물리적 메모리 양보다 크면 **Buffers Spooled** 는 증가하며 이는 메모리 스와핑이 늘어남을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-120">When this number is larger than the amount of physical memory, the **Buffers Spooled** count rises as an indication that memory swapping is increasing.</span></span> <span data-ttu-id="f2a9f-121">메모리 스와핑이 늘어나면 데이터 흐름 엔진의 성능이 느려집니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-121">Increased memory swapping slows performance of the data flow engine.</span></span>|  
|<span data-ttu-id="f2a9f-122">Buffers in use</span><span class="sxs-lookup"><span data-stu-id="f2a9f-122">Buffers in use</span></span>|<span data-ttu-id="f2a9f-123">모든 데이터 흐름 구성 요소 및 데이터 흐름 엔진이 현재 사용 중인 모든 유형의 버퍼 개체 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-123">The number of buffer objects, of all types, that all data flow components and the data flow engine is currently using.</span></span>|  
|<span data-ttu-id="f2a9f-124">Buffers Spooled</span><span class="sxs-lookup"><span data-stu-id="f2a9f-124">Buffers spooled</span></span>|<span data-ttu-id="f2a9f-125">디스크에 현재 기록된 버퍼 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-125">The number of buffers currently written to the disk.</span></span> <span data-ttu-id="f2a9f-126">데이터 흐름 엔진에 물리적 메모리가 부족하면 현재 사용되지 않은 버퍼는 디스크에 쓰여지고 필요에 따라 다시 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-126">If the data flow engine runs low on physical memory, buffers not currently used are written to disk and then reloaded when needed.</span></span>|  
|<span data-ttu-id="f2a9f-127">Flat buffer memory</span><span class="sxs-lookup"><span data-stu-id="f2a9f-127">Flat buffer memory</span></span>|<span data-ttu-id="f2a9f-128">모든 플랫 버퍼가 사용하는 전체 메모리(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-128">The total amount of memory, in bytes, that all flat buffers use.</span></span> <span data-ttu-id="f2a9f-129">플랫 버퍼는 구성 요소가 데이터 저장에 사용하는 메모리 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-129">Flat buffers are blocks of memory that a component uses to store data.</span></span> <span data-ttu-id="f2a9f-130">플랫 버퍼는 바이트의 큰 블록이며 바이트 단위로 액세스됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-130">A flat buffer is a large block of bytes that is accessed byte by byte.</span></span>|  
|<span data-ttu-id="f2a9f-131">Flat buffers in use</span><span class="sxs-lookup"><span data-stu-id="f2a9f-131">Flat buffers in use</span></span>|<span data-ttu-id="f2a9f-132">데이터 흐름 엔진이 사용하는 플랫 버퍼 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-132">The number of flat buffers that the Data flow engine uses.</span></span> <span data-ttu-id="f2a9f-133">모든 플랫 버퍼는 프라이빗 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-133">All flat buffers are private buffers.</span></span>|  
|<span data-ttu-id="f2a9f-134">Private buffer memory</span><span class="sxs-lookup"><span data-stu-id="f2a9f-134">Private buffer memory</span></span>|<span data-ttu-id="f2a9f-135">모든 프라이빗 버퍼가 사용하는 전체 메모리 양입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-135">The total amount of memory in use by all private buffers.</span></span> <span data-ttu-id="f2a9f-136">데이터 흐름 엔진이 데이터 흐름을 지원하기 위해 만드는 버퍼는 프라이빗 버퍼가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-136">A buffer is not private if the data flow engine creates it to support data flow.</span></span> <span data-ttu-id="f2a9f-137">프라이빗 버퍼는 변환 작업에서 임시 작업용으로만 사용하는 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-137">A private buffer is a buffer that a transformation uses for temporary work only.</span></span> <span data-ttu-id="f2a9f-138">예를 들어 집계 변환은 프라이빗 버퍼를 사용하여 내부 계산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-138">For example, the Aggregation transformation uses private buffers to do its work.</span></span>|  
|<span data-ttu-id="f2a9f-139">Private buffers in use</span><span class="sxs-lookup"><span data-stu-id="f2a9f-139">Private buffers in use</span></span>|<span data-ttu-id="f2a9f-140">변환 작업에서 사용하는 버퍼 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-140">The number of buffers that transformations use.</span></span>|  
|<span data-ttu-id="f2a9f-141">Rows read</span><span class="sxs-lookup"><span data-stu-id="f2a9f-141">Rows read</span></span>|<span data-ttu-id="f2a9f-142">원본에서 생성하는 행 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-142">The number of rows that a source produces.</span></span> <span data-ttu-id="f2a9f-143">조회 변환이 참조 테이블에서 읽은 행은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-143">The number does not include rows read from reference tables by the Lookup transformation.</span></span>|  
|<span data-ttu-id="f2a9f-144">Rows written</span><span class="sxs-lookup"><span data-stu-id="f2a9f-144">Rows written</span></span>|<span data-ttu-id="f2a9f-145">대상에 제공된 행 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-145">The number of rows offered to a destination.</span></span> <span data-ttu-id="f2a9f-146">대상 데이터 저장소에 쓰여진 행은 반영되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-146">The number does not reflect rows written to the destination data store.</span></span>|  
  
 <span data-ttu-id="f2a9f-147">성능 MMC(Microsoft Management Console) 스냅인을 사용하여 성능 카운터를 캡처하는 로그를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-147">You use the Performance Microsoft Management Console (MMC) snap-in to create a log that captures performance counters.</span></span>  
  
 <span data-ttu-id="f2a9f-148">성능을 향상시키는 방법에 대한 자세한 내용은 [데이터 흐름 성능 기능](../data-flow/data-flow-performance-features.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-148">For information about how to improve performance, see [Data Flow Performance Features](../data-flow/data-flow-performance-features.md).</span></span>  
  
## <a name="obtain-performance-counter-statistics"></a><span data-ttu-id="f2a9f-149">성능 카운터 통계 가져오기</span><span class="sxs-lookup"><span data-stu-id="f2a9f-149">Obtain Performance Counter Statistics</span></span>  
 <span data-ttu-id="f2a9f-150">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트의 경우 [dm_execution_performance_counters&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/functions-dm-execution-performance-counters) 함수를 사용하여 성능 카운터 통계를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-150">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you can obtain performance counter statistics by using the [dm_execution_performance_counters &#40;SSISDB Database&#41;](/sql/integration-services/functions-dm-execution-performance-counters) function.</span></span>  
  
 <span data-ttu-id="f2a9f-151">다음 예에서는 이 함수가 ID가 34인 실행 인스턴스에 대한 통계를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-151">In the following example, the function returns statistics for a running execution with an ID of 34.</span></span>  
  
```  
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
 <span data-ttu-id="f2a9f-152">다음 예에서는 이 함수가 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에서 실행 중인 모든 실행 인스턴스에 대한 통계를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-152">In the following example, the function returns statistics for all the executions running on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
```  
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f2a9f-153">`ssis_admin` 데이터베이스 역할의 멤버에게는 진행 중인 모든 실행에 대한 성능 통계가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-153">If you are a member of the `ssis_admin` database role, performance statistics for all running executions are returned.</span></span>  <span data-ttu-id="f2a9f-154">`ssis_admin` 데이터베이스 역할이 아닌 멤버에게는 읽기 권한이 있는 진행 중인 실행에 대한 성능 통계가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a9f-154">If you are not a member of the `ssis_admin` database role, performance statistics for the running executions for which you have read permissions, are returned.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="f2a9f-155">관련 내용</span><span class="sxs-lookup"><span data-stu-id="f2a9f-155">Related Content</span></span>  
  
-   <span data-ttu-id="f2a9f-156">codeplex.com의 도구, [SSIS Performance Visualization for Business Intelligence Development Studio(CodePlex 프로젝트)](https://go.microsoft.com/fwlink/?LinkId=146626)</span><span class="sxs-lookup"><span data-stu-id="f2a9f-156">Tool, [SSIS Performance Visualization for Business Intelligence Development Studio (CodePlex Project)](https://go.microsoft.com/fwlink/?LinkId=146626), on codeplex.com.</span></span>  
  
-   <span data-ttu-id="f2a9f-157">msdn.microsoft.com의 비디오, [기업에서 SSIS 패키지의 성능 측정 및 이해(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=150497)</span><span class="sxs-lookup"><span data-stu-id="f2a9f-157">Video, [Measuring and Understanding the Performance of Your SSIS Packages in the Enterprise (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=150497), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="f2a9f-158">support.microsoft.com의 지원 문서, [Windows Server 2008로 업그레이드한 후 성능 모니터에서 SSIS 성능 카운터를 더 이상 사용할 수 없다.](https://go.microsoft.com/fwlink/?LinkId=235319)</span><span class="sxs-lookup"><span data-stu-id="f2a9f-158">Support article, [The SSIS performance counter is no longer available in the Performance Monitor after you upgrade to Windows Server 2008](https://go.microsoft.com/fwlink/?LinkId=235319), on support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a9f-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2a9f-159">See Also</span></span>  
 [<span data-ttu-id="f2a9f-160">프로젝트 및 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="f2a9f-160">Execution of Projects and Packages</span></span>](../packages/run-integration-services-ssis-packages.md)  
  
  
