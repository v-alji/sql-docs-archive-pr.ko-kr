---
title: Distributed Replay 요구 사항 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 6fffee7d-891f-4d9d-b2c3-dd19855a1c2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 66be93534756360e722fcccaf405815e14ffa7ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650321"
---
# <a name="distributed-replay-requirements"></a><span data-ttu-id="36d05-102">Distributed Replay Requirements</span><span class="sxs-lookup"><span data-stu-id="36d05-102">Distributed Replay Requirements</span></span>
  <span data-ttu-id="36d05-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 기능을 사용하기 전에 이 항목에서 설명하는 제품 요구 사항을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="36d05-103">Before using the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay feature, consider the product requirements that are outlined in this topic.</span></span>  
  
## <a name="input-trace-requirements"></a><span data-ttu-id="36d05-104">입력 추적 요구 사항</span><span class="sxs-lookup"><span data-stu-id="36d05-104">Input Trace Requirements</span></span>  
 <span data-ttu-id="36d05-105">추적 데이터를 재생하려면 데이터가 버전 및 형식 요구 사항을 충족해야 하고 필요한 이벤트 및 열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-105">To successfully replay trace data, it must meet the requirements for version and format, and contain the required events and columns.</span></span>  
  
### <a name="input-trace-versions"></a><span data-ttu-id="36d05-106">입력 추적 버전</span><span class="sxs-lookup"><span data-stu-id="36d05-106">Input Trace Versions</span></span>  
 <span data-ttu-id="36d05-107">Distributed Replay는 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 수집된 입력 추적 데이터를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-107">Distributed Replay supports input trace data that is collected on the following versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
### <a name="input-trace-formats"></a><span data-ttu-id="36d05-108">입력 추적 형식</span><span class="sxs-lookup"><span data-stu-id="36d05-108">Input Trace Formats</span></span>  
 <span data-ttu-id="36d05-109">입력 추적 데이터는 다음 형식 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-109">The input trace data can be in any of the following formats:</span></span>  
  
-   <span data-ttu-id="36d05-110">확장명이 `.trc` 인 단일 추적 파일</span><span class="sxs-lookup"><span data-stu-id="36d05-110">A single trace file that has the `.trc` extension.</span></span>  
  
-   <span data-ttu-id="36d05-111">파일 롤오버 명명 규칙을 따르는 일련의 롤오버 추적 파일은 예를 들면 `<TraceFile>.trc`, `<TraceFile>_1.trc`, `<TraceFile>_2.trc`, `<TraceFile>_3.trc`, `<TraceFile>_n.trc`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-111">A set of rollover trace files that follow the file rollover naming convention, for example: `<TraceFile>.trc`, `<TraceFile>_1.trc`, `<TraceFile>_2.trc`, `<TraceFile>_3.trc`, ... `<TraceFile>_n.trc`.</span></span>  
  
### <a name="input-trace-events-and-columns"></a><span data-ttu-id="36d05-112">입력 추적 이벤트 및 열</span><span class="sxs-lookup"><span data-stu-id="36d05-112">Input Trace Events and Columns</span></span>  
 <span data-ttu-id="36d05-113">Distributed Replay에서 입력 추적 데이터를 재생하려면 데이터가 특정 이벤트 및 열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-113">The input trace data must contain specific events and columns to be replayed by Distributed Replay.</span></span> <span data-ttu-id="36d05-114">**의** TSQL_Replay [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 템플릿에 필요한 모든 이벤트 및 열과 추가 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-114">The **TSQL_Replay** template in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] contains all of the required events and columns, in addition to extra information.</span></span> <span data-ttu-id="36d05-115">이 템플릿에 대한 자세한 내용은 [Replay Requirements](../sql-server-profiler/replay-requirements.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="36d05-115">For more information about that template, see [Replay Requirements](../sql-server-profiler/replay-requirements.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="36d05-116">**TSQL_Replay** 템플릿을 사용하여 입력 추적 데이터를 캡처하지 않거나 입력 추적 요구 사항이 충족되지 않은 경우 예기치 않은 재생 결과가 수신될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-116">If you do not use the **TSQL_Replay** template to capture the input trace data, or if the input trace requirements are not satisfied, you may receive unexpected replay results.</span></span>  
  
 <span data-ttu-id="36d05-117">사용자 지정 추적 템플릿을 만들고 이를 통해 Distributed Replay를 사용하여 이벤트를 재생할 수도 있습니다. 이 경우 사용자 지정 추적 템플릿에 다음 이벤트가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-117">You can also create a custom trace template and use it to replay events with Distributed Replay, as long as it contains the following events:</span></span>  
  
-   <span data-ttu-id="36d05-118">로그인 감사</span><span class="sxs-lookup"><span data-stu-id="36d05-118">Audit Login</span></span>  
  
-   <span data-ttu-id="36d05-119">로그아웃 감사</span><span class="sxs-lookup"><span data-stu-id="36d05-119">Audit Logout</span></span>  
  
-   <span data-ttu-id="36d05-120">ExistingConnection</span><span class="sxs-lookup"><span data-stu-id="36d05-120">ExistingConnection</span></span>  
  
-   <span data-ttu-id="36d05-121">RPC Output Parameter</span><span class="sxs-lookup"><span data-stu-id="36d05-121">RPC Output Parameter</span></span>  
  
-   <span data-ttu-id="36d05-122">RPC:Completed</span><span class="sxs-lookup"><span data-stu-id="36d05-122">RPC:Completed</span></span>  
  
-   <span data-ttu-id="36d05-123">RPC:Starting</span><span class="sxs-lookup"><span data-stu-id="36d05-123">RPC:Starting</span></span>  
  
-   <span data-ttu-id="36d05-124">SQL:BatchCompleted</span><span class="sxs-lookup"><span data-stu-id="36d05-124">SQL:BatchCompleted</span></span>  
  
-   <span data-ttu-id="36d05-125">SQL:BatchStarting</span><span class="sxs-lookup"><span data-stu-id="36d05-125">SQL:BatchStarting</span></span>  
  
 <span data-ttu-id="36d05-126">서버 쪽 커서를 재생하는 경우 다음 이벤트도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-126">If you are replaying server-side cursors, the following events are also required:</span></span>  
  
-   <span data-ttu-id="36d05-127">CursorClose</span><span class="sxs-lookup"><span data-stu-id="36d05-127">CursorClose</span></span>  
  
-   <span data-ttu-id="36d05-128">CursorExecute</span><span class="sxs-lookup"><span data-stu-id="36d05-128">CursorExecute</span></span>  
  
-   <span data-ttu-id="36d05-129">CursorOpen</span><span class="sxs-lookup"><span data-stu-id="36d05-129">CursorOpen</span></span>  
  
-   <span data-ttu-id="36d05-130">CursorPrepare</span><span class="sxs-lookup"><span data-stu-id="36d05-130">CursorPrepare</span></span>  
  
-   <span data-ttu-id="36d05-131">CursorUnprepare</span><span class="sxs-lookup"><span data-stu-id="36d05-131">CursorUnprepare</span></span>  
  
 <span data-ttu-id="36d05-132">서버 쪽 준비된 SQL 문을 재생하는 경우 다음 이벤트도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-132">If you are replaying server-side prepared SQL statements, the following events are also required:</span></span>  
  
-   <span data-ttu-id="36d05-133">Exec Prepared SQL</span><span class="sxs-lookup"><span data-stu-id="36d05-133">Exec Prepared SQL</span></span>  
  
-   <span data-ttu-id="36d05-134">Prepare SQL</span><span class="sxs-lookup"><span data-stu-id="36d05-134">Prepare SQL</span></span>  
  
 <span data-ttu-id="36d05-135">모든 입력 추적 데이터는 다음 열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-135">All input trace data must contain the following columns:</span></span>  
  
-   <span data-ttu-id="36d05-136">Event Class</span><span class="sxs-lookup"><span data-stu-id="36d05-136">Event Class</span></span>  
  
-   <span data-ttu-id="36d05-137">EventSequence</span><span class="sxs-lookup"><span data-stu-id="36d05-137">EventSequence</span></span>  
  
-   <span data-ttu-id="36d05-138">TextData</span><span class="sxs-lookup"><span data-stu-id="36d05-138">TextData</span></span>  
  
-   <span data-ttu-id="36d05-139">애플리케이션 이름</span><span class="sxs-lookup"><span data-stu-id="36d05-139">Application Name</span></span>  
  
-   <span data-ttu-id="36d05-140">LoginName</span><span class="sxs-lookup"><span data-stu-id="36d05-140">LoginName</span></span>  
  
-   <span data-ttu-id="36d05-141">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="36d05-141">DatabaseName</span></span>  
  
-   <span data-ttu-id="36d05-142">데이터베이스 ID</span><span class="sxs-lookup"><span data-stu-id="36d05-142">Database ID</span></span>  
  
-   <span data-ttu-id="36d05-143">HostName</span><span class="sxs-lookup"><span data-stu-id="36d05-143">HostName</span></span>  
  
-   <span data-ttu-id="36d05-144">이진 데이터</span><span class="sxs-lookup"><span data-stu-id="36d05-144">Binary Data</span></span>  
  
-   <span data-ttu-id="36d05-145">SPID</span><span class="sxs-lookup"><span data-stu-id="36d05-145">SPID</span></span>  
  
-   <span data-ttu-id="36d05-146">시작 시간</span><span class="sxs-lookup"><span data-stu-id="36d05-146">Start Time</span></span>  
  
-   <span data-ttu-id="36d05-147">EndTime</span><span class="sxs-lookup"><span data-stu-id="36d05-147">EndTime</span></span>  
  
-   <span data-ttu-id="36d05-148">IsSystem</span><span class="sxs-lookup"><span data-stu-id="36d05-148">IsSystem</span></span>  
  
## <a name="supported-input-trace-and-target-server-combinations"></a><span data-ttu-id="36d05-149">지원되는 입력 추적 및 대상 서버의 조합</span><span class="sxs-lookup"><span data-stu-id="36d05-149">Supported Input Trace and Target Server Combinations</span></span>  
 <span data-ttu-id="36d05-150">다음 표에서는 지원되는 추적 데이터 버전과 버전마다 데이터 재생이 지원되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-150">The following table lists the supported versions of trace data, and for each, the supported versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that data can be replayed against.</span></span>  
  
|<span data-ttu-id="36d05-151">입력 추적 데이터 버전</span><span class="sxs-lookup"><span data-stu-id="36d05-151">Version of Input Trace Data</span></span>|<span data-ttu-id="36d05-152">대상 서버 인스턴스에 대해 지원되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전</span><span class="sxs-lookup"><span data-stu-id="36d05-152">Supported Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the Target Server Instance</span></span>|  
|---------------------------------|------------------------------------------------------------------------------------|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="36d05-153">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d05-153">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="36d05-154">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d05-154">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="36d05-155">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d05-155">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<span data-ttu-id="36d05-156">, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d05-156">, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
  
## <a name="operating-system-requirements"></a><span data-ttu-id="36d05-157">운영 체제 요구 사항</span><span class="sxs-lookup"><span data-stu-id="36d05-157">Operating System Requirements</span></span>  
 <span data-ttu-id="36d05-158">관리 도구, 컨트롤러 및 클라이언트 서비스를 실행할 수 있는 운영 체제는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-158">Supported operating systems for running the administration tool and the controller and client services is the same as your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="36d05-159">인스턴스에 대해 지원 되는 운영 체제에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014를 설치 하기 위한 하드웨어 및 소프트웨어 요구 사항](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36d05-159">For more information about which operating systems are supported for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
 <span data-ttu-id="36d05-160">Distributed Replay 기능은 x86 기반 및 x64 기반 운영 체제 모두에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-160">Distributed Replay features are supported on both x86-based and x64-based operating systems.</span></span> <span data-ttu-id="36d05-161">x64 기반 운영 체제의 경우 WOW(Windows on Windows) 모드만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-161">For x64-based operating systems, only Windows on Windows (WOW) mode is supported.</span></span>  
  
## <a name="installation-limitations"></a><span data-ttu-id="36d05-162">설치 제한 사항</span><span class="sxs-lookup"><span data-stu-id="36d05-162">Installation Limitations</span></span>  
 <span data-ttu-id="36d05-163">컴퓨터당 각 Distributed Replay 기능의 단일 인스턴스를 한 번만 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-163">Any one computer can only have a single instance of each Distributed Replay feature installed.</span></span> <span data-ttu-id="36d05-164">다음 표에서는 단일 환경에서 허용되는 각 Distributed Replay 기능의 설치 횟수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-164">The following table lists how many installations of each feature are allowed in a single Distributed Replay environment.</span></span>  
  
|<span data-ttu-id="36d05-165">Distributed Replay 기능</span><span class="sxs-lookup"><span data-stu-id="36d05-165">Distributed Replay Feature</span></span>|<span data-ttu-id="36d05-166">재생 환경당 최대 설치 횟수</span><span class="sxs-lookup"><span data-stu-id="36d05-166">Maximum Installations Per Replay Environment</span></span>|  
|--------------------------------|--------------------------------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="36d05-167">Distributed Replay Controller 서비스</span><span class="sxs-lookup"><span data-stu-id="36d05-167">Distributed Replay controller service</span></span>|<span data-ttu-id="36d05-168">1</span><span class="sxs-lookup"><span data-stu-id="36d05-168">1</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="36d05-169">Distributed Replay Client 서비스</span><span class="sxs-lookup"><span data-stu-id="36d05-169">Distributed Replay client service</span></span>|<span data-ttu-id="36d05-170">16(실제 또는 가상 컴퓨터)</span><span class="sxs-lookup"><span data-stu-id="36d05-170">16 (physical or virtual computers)</span></span>|  
|<span data-ttu-id="36d05-171">Administration Tool</span><span class="sxs-lookup"><span data-stu-id="36d05-171">Administration tool</span></span>|<span data-ttu-id="36d05-172">제한 없음</span><span class="sxs-lookup"><span data-stu-id="36d05-172">Unlimited</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="36d05-173">관리 도구는 단일 컴퓨터에 한 번만 설치할 수 있지만 관리 도구의 여러 인스턴스를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-173">Although only one instance of the administration tool can be installed on a single computer, you can start multiple instances of the administration tool.</span></span> <span data-ttu-id="36d05-174">여러 관리 도구에서 실행한 명령은 명령을 받은 순서대로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-174">Commands issued from multiple administration tools are resolved in the order in which they are received.</span></span>  
  
## <a name="data-access-provider"></a><span data-ttu-id="36d05-175">데이터 액세스 공급자</span><span class="sxs-lookup"><span data-stu-id="36d05-175">Data Access Provider</span></span>  
 <span data-ttu-id="36d05-176">Distributed Replay는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 데이터 액세스 공급자만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-176">Distributed Replay only supports the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC data access provider.</span></span>  
  
## <a name="target-server-preparation-requirements"></a><span data-ttu-id="36d05-177">대상 서버 준비 요구 사항</span><span class="sxs-lookup"><span data-stu-id="36d05-177">Target Server Preparation Requirements</span></span>  
 <span data-ttu-id="36d05-178">테스트 환경에 대상 서버를 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-178">We recommend that the target server be located in a test environment.</span></span> <span data-ttu-id="36d05-179">데이터가 원래 기록되었던 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 아닌 다른 인스턴스에서 추적 데이터를 재생하려면 대상 서버에서 다음 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-179">To replay trace data against a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] than it was originally recorded, make sure that the following has been done to the target server:</span></span>  
  
-   <span data-ttu-id="36d05-180">추적 데이터에 포함된 모든 로그인 및 사용자가 대상 서버에서 동일한 데이터베이스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-180">All logins and users that are contained in the trace data must be present in the same database on the target server.</span></span>  
  
-   <span data-ttu-id="36d05-181">대상 서버에 있는 모든 로그인 및 사용자가 원래 서버에서 가진 권한과 같은 권한을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-181">All logins and users on the target server must have the same permissions they had on the original server.</span></span>  
  
-   <span data-ttu-id="36d05-182">대상에 있는 데이터베이스 ID가 원본에 있는 데이터베이스 ID와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-182">The database IDs on the target ideally should be the same as those on the source.</span></span> <span data-ttu-id="36d05-183">그러나 두 ID가 서로 다르다면 **DatabaseName** 이 추적에 있을 경우 이를 기준으로 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-183">However, if they are not the same, matching can be performed based on **DatabaseName** if it is present in the trace.</span></span>  
  
-   <span data-ttu-id="36d05-184">추적 데이터에 포함된 각 로그인의 기본 데이터베이스가 대상 서버에서 로그인의 각 대상 데이터베이스로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-184">The default database for each login that is contained in the trace data must be set (on the target server) to the respective target database of the login.</span></span> <span data-ttu-id="36d05-185">예를 들어 재생할 추적 데이터가 원래 **인스턴스의**Fred_Db **데이터베이스에 있는** Fred [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]라는 로그인에 대한 작업을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-185">For example, the trace data to be replayed contains activity for the login, **Fred**, in the database **Fred_Db** on the original instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="36d05-186">따라서 대상 서버에서 **Fred**로그인에 대한 기본 데이터베이스는 **Fred_Db** 와 일치하는 데이터베이스로 설정되어야 합니다. 데이터베이스 이름이 다르더라도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-186">Therefore, on the target server, the default database for the login, **Fred**, must be set to the database that matches **Fred_Db** (even if the database name is different).</span></span> <span data-ttu-id="36d05-187">로그인의 기본 데이터베이스를 설정하려면 `sp_defaultdb` 시스템 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-187">To set the default database of the login, use the `sp_defaultdb` system stored procedure.</span></span>  
  
 <span data-ttu-id="36d05-188">누락되거나 잘못된 로그인과 연관된 이벤트를 재생하면 재생 오류가 발생하지만 재생 작업은 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="36d05-188">Replaying events associated with missing or incorrect logins results in replay errors, but the replay operation continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d05-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36d05-189">See Also</span></span>  
 <span data-ttu-id="36d05-190">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="36d05-190">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="36d05-191">[Distributed Replay 보안](distributed-replay-security.md) </span><span class="sxs-lookup"><span data-stu-id="36d05-191">[Distributed Replay Security](distributed-replay-security.md) </span></span>  
 [<span data-ttu-id="36d05-192">Distributed Replay 설치</span><span class="sxs-lookup"><span data-stu-id="36d05-192">Install Distributed Replay</span></span>](install-distributed-replay-overview.md)  
  
  
