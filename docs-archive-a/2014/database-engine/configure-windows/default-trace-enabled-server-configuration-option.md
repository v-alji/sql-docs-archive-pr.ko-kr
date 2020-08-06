---
title: default trace enabled 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], traces
- traces [SQL Server], logs
- default trace enabled option
ms.assetid: 1322d668-44f4-469e-8fd6-e0d02a81c8f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d40305de7375f2ae10d563871fd40b7acfa463f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740420"
---
# <a name="default-trace-enabled-server-configuration-option"></a><span data-ttu-id="88f9b-102">default trace enabled 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="88f9b-102">default trace enabled Server Configuration Option</span></span>
  <span data-ttu-id="88f9b-103">**default trace enabled** 옵션을 사용하여 기본 추적 로그 파일을 설정하거나 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-103">Use the **default trace enabled** option to enable or disable the default trace log files.</span></span> <span data-ttu-id="88f9b-104">기본 추적 기능은 주로 구성 옵션과 관련된 변경 내용과 작업에 대한 다양하고 영구적인 로그를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-104">The default trace functionality provides a rich, persistent log of activity and changes primarily related to the configuration options.</span></span>  
  
> [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="88f9b-105">확장 이벤트를 대신 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="88f9b-105">Use Extended Events instead.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="88f9b-106">목적</span><span class="sxs-lookup"><span data-stu-id="88f9b-106">Purpose</span></span>  
 <span data-ttu-id="88f9b-107">기본 추적 기능은 데이터베이스 관리자가 처음 문제 발생 시 문제 진단에 필요한 로그 데이터를 가지고 있는지 확인하여 문제를 해결하도록 도와 줍니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-107">Default trace provides troubleshooting assistance to database administrators by ensuring that they have the log data necessary to diagnose problems the first time they occur.</span></span>  
  
## <a name="viewing"></a><span data-ttu-id="88f9b-108">보기</span><span class="sxs-lookup"><span data-stu-id="88f9b-108">Viewing</span></span>  
 <span data-ttu-id="88f9b-109">기본 추적 로그는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에서 열어서 검사하거나 [!INCLUDE[tsql](../../includes/tsql-md.md)] 시스템 함수를 사용하여 `fn_trace_gettable` 로 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-109">The default trace logs can be opened and examined by [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or queried with [!INCLUDE[tsql](../../includes/tsql-md.md)] by using the `fn_trace_gettable` system function.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="88f9b-110">에서는 일반 추적 출력 파일을 여는 것과 똑같이 기본 추적 로그 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-110">can open the default trace log files just as it does normal trace output files.</span></span> <span data-ttu-id="88f9b-111">기본 추적 로그는 기본적으로 롤오버 추적 파일을 사용하여 `\MSSQL\LOG` 디렉터리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-111">The default trace log is stored by default in the `\MSSQL\LOG` directory using a rollover trace file.</span></span> <span data-ttu-id="88f9b-112">기본 추적 로그 파일의 기본 파일 이름은 `log.trc`입니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-112">The base file name for the default trace log file is `log.trc`.</span></span> <span data-ttu-id="88f9b-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]일반 설치에서는 기본 추적이 설정되므로 TraceID는 1이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-113">In a typical installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the default trace is enabled and thus becomes TraceID 1.</span></span> <span data-ttu-id="88f9b-114">설치 후와 다른 추적 생성 후에 기본 추적이 설정되면 TraceID가 더 큰 숫자가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-114">If enabled after installation and after creating other traces, the TraceID can become a larger number.</span></span>  
  
 <span data-ttu-id="88f9b-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로파일러를 사용하여 이 추적 파일을 보는 방법은 [추적 파일 열기&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88f9b-115">For more information about using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler to view this trace file, see [Open a Trace File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)</span></span>  
  
### <a name="example"></a><span data-ttu-id="88f9b-116">예제:</span><span class="sxs-lookup"><span data-stu-id="88f9b-116">Example:</span></span>  
 <span data-ttu-id="88f9b-117">다음 문은 기본 위치에 있는 기본 추적 로그를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-117">The following statement opens the default trace log in the default location:</span></span>  
  
```  
SELECT *   
FROM fn_trace_gettable  
('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG\log.trc', default);  
GO  
  
```  
  
## <a name="configuring"></a><span data-ttu-id="88f9b-118">구성</span><span class="sxs-lookup"><span data-stu-id="88f9b-118">Configuring</span></span>  
 <span data-ttu-id="88f9b-119">**default trace enabled** 옵션을 1로 설정하면 **기본 추적**을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-119">When set to 1, the **default trace enabled** option enables **Default Trace**.</span></span> <span data-ttu-id="88f9b-120">이 옵션의 기본 설정은 1(설정)입니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-120">The default setting for this option is 1 (ON).</span></span> <span data-ttu-id="88f9b-121">값이 0이면 추적 기능은 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-121">A value of 0 turns off the trace.</span></span>  
  
 <span data-ttu-id="88f9b-122">**default trace enabled** 옵션은 고급 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-122">The **default trace enabled** option is an advanced option.</span></span> <span data-ttu-id="88f9b-123">**sp_configure** 시스템 저장 프로시저를 사용하여 설정을 변경하는 경우 **고급 옵션 표시** 를 1로 설정한 경우에만 **기본 추적 설정** 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-123">If you are using the **sp_configure** system stored procedure to change the setting, you can change the **default trace enabled** option only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="88f9b-124">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="88f9b-124">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f9b-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88f9b-125">See Also</span></span>  
 <span data-ttu-id="88f9b-126">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="88f9b-126">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="88f9b-127">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="88f9b-127">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="88f9b-128">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="88f9b-128">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
