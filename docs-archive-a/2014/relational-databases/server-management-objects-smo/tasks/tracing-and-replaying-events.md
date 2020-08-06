---
title: 이벤트 추적 및 재생 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7f0d570c70ef1cba080217e6c3a0f9b6055a4d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732496"
---
# <a name="tracing-and-replaying-events"></a><span data-ttu-id="29e30-102">이벤트 추적 및 재생</span><span class="sxs-lookup"><span data-stu-id="29e30-102">Tracing and Replaying Events</span></span>
  <span data-ttu-id="29e30-103">SMO에서 <xref:Microsoft.SqlServer.Management.Trace> 네임스페이스의 `Trace` 및 `Replay` 개체는 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 기능에 대한 프로그래밍 방식 액세스를 제공합니다. 이 기능은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스를 모니터링하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-103">In SMO, the `Trace` and `Replay` objects in the <xref:Microsoft.SqlServer.Management.Trace> namespace provide programmatic access to the [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] functionality, which is used for monitoring an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="29e30-104">각 이벤트에 대한 데이터를 캡처하고 파일이나 테이블에 저장하여 나중에 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-104">You can capture and save data about each event to a file or table to analyze later.</span></span> <span data-ttu-id="29e30-105">예를 들어 프로덕션 환경을 모니터링하여 어느 프로시저가 너무 늦게 실행되어 성능 저하를 유발하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-105">For example, you can monitor a production environment to see which procedures are impeding performance by executing too slowly.</span></span>  
  
 <span data-ttu-id="29e30-106">`Trace` 및 `Replay` 개체는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 추적을 만드는 데 사용할 수 있는 개체 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-106">The `Trace` and `Replay` objects provide a set of objects that can be used to create traces on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="29e30-107">이러한 개체는 사용자의 애플리케이션에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에 대한 추적을 수동으로 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-107">These objects can be used from within your own applications to create traces manually for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="29e30-108">또한 SMO `Trace` 개체를 사용하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 또는 DTS 로깅을 모니터링하여 만든 SQL 추적 파일 및 테이블을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-108">Additionally, SMO `Trace` objects can be used to read SQL Trace files and tables that were created by monitoring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], or DTS logging.</span></span>  
  
 <span data-ttu-id="29e30-109">SMO `Trace` 개체를 사용하면 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-109">SMO `Trace` objects let you perform the following functions:</span></span>  
  
-   <span data-ttu-id="29e30-110">추적을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-110">Create a trace.</span></span>  
  
-   <span data-ttu-id="29e30-111">추적에 대한 필터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-111">Set filters on the trace.</span></span>  
  
-   <span data-ttu-id="29e30-112">추적할 이벤트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-112">Set the events that are being traced.</span></span>  
  
-   <span data-ttu-id="29e30-113">추적을 중지하거나 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-113">Stop or start a trace.</span></span>  
  
-   <span data-ttu-id="29e30-114">추적 파일과 추적 테이블을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-114">Read trace files, and trace tables.</span></span>  
  
-   <span data-ttu-id="29e30-115">추적 관련 이벤트에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-115">Get information about events on a trace.</span></span>  
  
-   <span data-ttu-id="29e30-116">추적 관련 필터에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-116">Get information about filters on a trace.</span></span>  
  
-   <span data-ttu-id="29e30-117">추적 데이터를 프로그래밍 방식으로 조작합니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-117">Manipulate trace data programmatically.</span></span>  
  
-   <span data-ttu-id="29e30-118">추적 테이블과 추적 파일을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-118">Write trace tables and trace files.</span></span>  
  
-   <span data-ttu-id="29e30-119">추적 파일 또는 추적 테이블을 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-119">Replay trace files or trace tables.</span></span>  
  
 <span data-ttu-id="29e30-120">및 개체의 추적 데이터 `Trace` 는 `Replay` SMO 응용 프로그램에서 사용 하거나 [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md)를 사용 하 여 수동으로 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-120">The trace data from the `Trace` and `Replay` objects can be used by the SMO application, or it can be examined manually by using [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md).</span></span> <span data-ttu-id="29e30-121">추적 데이터는 추적 기능을 제공하는 [SQL Trace](../../sql-trace/sql-trace.md) 저장 프로시저에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-121">The trace data is also compatible with the [SQL Trace](../../sql-trace/sql-trace.md) stored procedures that also provide tracing capabilities.</span></span>  
  
 <span data-ttu-id="29e30-122">SMO 추적 개체는 Microsoft.SQLServer.ConnectionInfo.dll 파일에 대한 참조가 필요한 <xref:Microsoft.SqlServer.Management.Trace> 네임스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-122">The SMO trace objects reside in the <xref:Microsoft.SqlServer.Management.Trace> namespace, which requires a reference to the Microsoft.SQLServer.ConnectionInfo.dll file.</span></span>  
  
 <span data-ttu-id="29e30-123">`Trace` 및 `Replay` 개체에는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 인스턴스와의 연결을 설정할 <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 개체가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-123">The `Trace` and `Replay` objects require a <xref:Microsoft.SqlServer.Management.Common.ServerConnection><xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> object to establish a connection with the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="29e30-124"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체는 Microsoft.SQLServer.ConnectionInfo.dll 파일에 대한 참조가 필요한 <xref:Microsoft.SqlServer.Management.Common> 네임스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-124">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object resides in the <xref:Microsoft.SqlServer.Management.Common> namespace, which requires a reference to the Microsoft.SQLServer.ConnectionInfo.dll file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29e30-125">64비트 플랫폼에서는 `Trace` 및 `Replay` 개체가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29e30-125">The `Trace` and `Replay` objects are not supported on a 64-bit platform.</span></span>  
  
  
