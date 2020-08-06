---
title: 추적 파일 및 테이블 크기 제한 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- traces [SQL Server], file size
- size [SQL Server], tables
- file rollover option [SQL Server]
- size [SQL Server], files
ms.assetid: 88c31b02-f44c-4a14-be8b-437f2097de12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7795dfdadb8fb3bbaa1b55dcd5c962d24a7ba29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652758"
---
# <a name="limit-trace-file-and-table-sizes"></a><span data-ttu-id="bdba6-102">추적 파일 및 테이블 크기 제한</span><span class="sxs-lookup"><span data-stu-id="bdba6-102">Limit Trace File and Table Sizes</span></span>
  <span data-ttu-id="bdba6-103">SQL 추적 파일의 크기는 추적에 포함된 이벤트 클래스와 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 사용되는 방식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-103">SQL Trace results vary in size depending on the event classes that are included in the trace and the way in which the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is used.</span></span> <span data-ttu-id="bdba6-104">자주 발생하는 이벤트 클래스를 추적하는 경우 최대 파일 크기나 최대 행 수를 설정하여 추적을 통해 수집되는 데이터의 양을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-104">If you trace event classes that occur frequently, you can minimize the amount of data that the trace collects by setting the maximum file size or the maximum number of rows.</span></span> <span data-ttu-id="bdba6-105">최대 파일 크기나 최대 행 수를 지정하면 추적 파일이나 테이블의 크기가 지정된 한도를 초과하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-105">By specifying the maximum file size or rows, you ensure that the trace file or table will not grow beyond the specified limit.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdba6-106">추적 데이터를 기존 파일에 저장할 때는 데이터를 파일 끝에 추가하거나 기존 파일을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-106">If you save trace data to a file that already exists, you can append data to the file or overwrite the file.</span></span> <span data-ttu-id="bdba6-107">데이터를 파일에 추가할 때 추적 파일이 지정된 최대 크기에 도달하거나 이 크기를 넘어서면 최대 파일 크기를 늘리거나 새 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-107">If you choose to append data to the file, and the trace file already meets or exceeds the specified maximum file size, you are notified and given the opportunity either to increase the maximum file size or specify a new file.</span></span> <span data-ttu-id="bdba6-108">추적 테이블에서도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-108">The same is true for trace tables.</span></span>  
  
## <a name="maximum-file-size"></a><span data-ttu-id="bdba6-109">최대 파일 크기</span><span class="sxs-lookup"><span data-stu-id="bdba6-109">Maximum File Size</span></span>  
 <span data-ttu-id="bdba6-110">추적 파일의 최대 크기가 지정된 경우 최대 파일 크기에 도달하면 추적 정보가 더 이상 파일로 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-110">A trace that has a maximum file size stops saving trace information to the file after the maximum file size has been reached.</span></span> <span data-ttu-id="bdba6-111">이 옵션을 사용하면 이벤트를 더 작고 관리하기 쉬운 파일로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-111">This option allows you to group events into smaller, more manageable files.</span></span> <span data-ttu-id="bdba6-112">또한 파일 크기를 제한하면 최대 파일 크기에 도달할 때 추적이 중지되므로 무인 추적을 안전하게 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-112">In addition, limiting file size makes it safer to run unattended traces, because the trace stops when the maximum file size is reached.</span></span> <span data-ttu-id="bdba6-113">Transact-SQL 저장 프로시저나 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 만든 추적 파일의 최대 크기를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-113">You can set the maximum file size for traces created by means of Transact-SQL stored procedures or by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="bdba6-114">최대 파일 크기 옵션은 최대 1GB로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-114">There is an upper limit of 1 gigabyte (GB) for the maximum file size option.</span></span> <span data-ttu-id="bdba6-115">최대 파일 크기의 기본값은 5MB입니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-115">The default maximum file size is 5 megabytes (MB).</span></span>  
  
### <a name="enabling-file-rollover"></a><span data-ttu-id="bdba6-116">파일 롤오버 사용</span><span class="sxs-lookup"><span data-stu-id="bdba6-116">Enabling File Rollover</span></span>  
 <span data-ttu-id="bdba6-117">파일 롤오버 옵션을 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 최대 파일 크기에 도달하면 현재 파일을 닫고 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-117">The file rollover option causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to close the current file and create a new file when the maximum file size is reached.</span></span> <span data-ttu-id="bdba6-118">새 파일은 이전 파일과 같은 이름을 갖지만 순서를 나타내는 정수가 이름에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-118">The new file has the same name as the previous file, but an integer is appended to the name to indicate its sequence.</span></span> <span data-ttu-id="bdba6-119">예를 들어 원래 추적 파일 이름이 filename_1.trc이면 다음 추적 파일 이름은 filename_2.trc가 되는 식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-119">For example, if the original trace file is named filename_1.trc, the next trace file is filename_2.trc, and so on.</span></span> <span data-ttu-id="bdba6-120">새 롤오버 파일에 지정된 이름이 기존 파일 이름과 같을 경우 기존 파일이 읽기 전용이 아니면 이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-120">If the name assigned to a new rollover file is already used by an existing file, the existing file is overwritten unless it is read only.</span></span> <span data-ttu-id="bdba6-121">추적 데이터를 파일로 저장할 때 파일 롤오버 옵션이 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-121">The file rollover option is enabled by default when you are saving trace data to a file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdba6-122">파일 롤오버 옵션이 설정되어 있으면 추적은 다른 방법으로 중단되기 전까지 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-122">With the file rollover option on, the trace continues until it is stopped by some other means.</span></span> <span data-ttu-id="bdba6-123">파일 크기 제한에 도달한 후 추적을 중지하려면 파일 롤오버 옵션을 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="bdba6-123">To stop the trace after you have reached the file size limit, disable the file rollover option.</span></span>  
  
 <span data-ttu-id="bdba6-124">**추적 파일에 최대 파일 크기를 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="bdba6-124">**To set a maximum file size for a trace file**</span></span>  
  
 [<span data-ttu-id="bdba6-125">추적 파일에 최대 파일 크기 설정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="bdba6-125">Set a Maximum File Size for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
## <a name="maximum-number-of-rows"></a><span data-ttu-id="bdba6-126">최대 행 수</span><span class="sxs-lookup"><span data-stu-id="bdba6-126">Maximum Number of Rows</span></span>  
 <span data-ttu-id="bdba6-127">최대 행 수가 설정된 추적은 최대 행 수에 도달할 경우 추적 정보를 테이블로 저장하는 작업이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-127">A trace with a maximum number of rows stops saving trace information to a table after the maximum number of rows has been reached.</span></span> <span data-ttu-id="bdba6-128">각 이벤트는 한 행으로 구성되므로 이 매개 변수는 수집되는 이벤트 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-128">Each event constitutes one row, so this parameter sets a limit on the number of events that are gathered.</span></span> <span data-ttu-id="bdba6-129">최대 행 수를 설정하면 무인 추적을 쉽게 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-129">Setting the maximum number of rows makes it easier to run unattended traces.</span></span> <span data-ttu-id="bdba6-130">예를 들어 테이블에 추적 데이터를 저장하는 추적을 시작하고 테이블이 너무 커지면 추적을 중지하는 과정을 자동으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-130">For example, if you need to start a trace that saves trace data to a table, but you want to stop the trace if the table becomes too large, you can do so automatically.</span></span>  
  
 <span data-ttu-id="bdba6-131">최대 행 수를 지정한 경우 행 수가 이 값에 도달하면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 실행 중인 경우에는 계속 추적하지만 추적 정보는 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-131">When the maximum number of rows is specified and the maximum number of rows has been reached, the trace continues to run while [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is running, but the trace information is no longer recorded.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="bdba6-132">는 추적이 중지될 때까지 추적 결과를 계속 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bdba6-132">continues to display the trace results until the trace stops.</span></span>  
  
 <span data-ttu-id="bdba6-133">**추적의 최대 행 수를 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="bdba6-133">**To set a maximum number of rows for a trace**</span></span>  
  
 [<span data-ttu-id="bdba6-134">추적 테이블에 최대 테이블 크기 설정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="bdba6-134">Set a Maximum Table Size for a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
## <a name="see-also"></a><span data-ttu-id="bdba6-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bdba6-135">See Also</span></span>  
 [<span data-ttu-id="bdba6-136">sp_trace_create&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bdba6-136">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)  
  
  
