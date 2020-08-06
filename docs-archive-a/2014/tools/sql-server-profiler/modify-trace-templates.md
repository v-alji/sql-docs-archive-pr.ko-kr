---
title: 추적 템플릿 수정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a26d0a70f65b6ff60dcf42ffb98e67dc0d2b52d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646777"
---
# <a name="modify-trace-templates"></a><span data-ttu-id="62636-102">추적 템플릿 수정</span><span class="sxs-lookup"><span data-stu-id="62636-102">Modify Trace Templates</span></span>
  <span data-ttu-id="62636-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 실행 중인 로컬 컴퓨터에서 파일에 저장된 템플릿을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62636-103">You can modify templates that are saved in a file on the local computer on which [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is running.</span></span> <span data-ttu-id="62636-104">이런 파일에서 파생된 템플릿도 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62636-104">You can also modify templates derived from those files.</span></span> <span data-ttu-id="62636-105">기존 템플릿을 수정할 때 **추적 속성** 대화 상자의 **이벤트 선택** 탭에서 속성이 원래 설정된 순서와 동일한 순서대로 이벤트 클래스나 데이터 열 같은 템플릿 속성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="62636-105">When you modify existing templates, you edit template properties such as event classes and data columns, in the same order that the properties were set originally, on the **Events Selection** tab of the **Trace Properties** dialog box.</span></span> <span data-ttu-id="62636-106">이벤트 클래스 및 데이터 열을 추가 또는 제거할 수도 있고 필터도 같은 방법으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62636-106">Event classes and data columns can be added or removed, and filters can be changed.</span></span> <span data-ttu-id="62636-107">템플릿을 수정하면 사용자 특정 템플릿이 만들어지고 원래 시스템 템플릿은 그대로 남습니다.</span><span class="sxs-lookup"><span data-stu-id="62636-107">After the template is modified, a user-specific template is created and the original system template is left intact.</span></span> <span data-ttu-id="62636-108">자세한 내용은 [추적 및 추적 템플릿 저장](save-traces-and-trace-templates.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62636-108">For more information, see [Save Traces and Trace Templates](save-traces-and-trace-templates.md).</span></span>  
  
 <span data-ttu-id="62636-109">추적을 만들 때 사용한 원래 템플릿을 기억할 수 없거나 나중에 같은 추적을 실행하려는 경우 기존 추적 파일에서 템플릿을 파생해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62636-109">You may need to derive a template from an existing trace file if you cannot remember (or have not saved) the original template that was used to create the trace, or if you want to run the same trace at a later date.</span></span> <span data-ttu-id="62636-110">기존의 추적으로 작업하면 속성을 볼 수는 있지만 수정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62636-110">When working with existing traces, you can view the properties, but you cannot modify the properties.</span></span> <span data-ttu-id="62636-111">속성을 수정하려면 추적을 시작하거나 일시 중지하십시오.</span><span class="sxs-lookup"><span data-stu-id="62636-111">To modify the properties, stop or pause the trace.</span></span> <span data-ttu-id="62636-112">자세한 내용은 [추적 파일 또는 추적 테이블에서 템플릿 파생&#40;SQL Server Profiler&#41;](sql-server-profiler.md) 및 [실행 중인 추적으로부터 템플릿 파생&#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62636-112">For more information, see [Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](sql-server-profiler.md) and [Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="62636-113">**추적 템플릿을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="62636-113">**To create a trace template**</span></span>  
  
 [<span data-ttu-id="62636-114">추적 템플릿 만들기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="62636-114">Create a Trace Template &#40;SQL Server Profiler&#41;</span></span>](create-a-trace-template-sql-server-profiler.md)  
  
 <span data-ttu-id="62636-115">**추적 템플릿에서 추적을 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="62636-115">**To run a trace from a trace template**</span></span>  
  
 [<span data-ttu-id="62636-116">추적 만들기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="62636-116">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](create-a-trace-sql-server-profiler.md)  
  
 <span data-ttu-id="62636-117">**추적 템플릿을 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="62636-117">**To modify a trace template**</span></span>  
  
 [<span data-ttu-id="62636-118">SQL Server Profiler 사용</span><span class="sxs-lookup"><span data-stu-id="62636-118">Using SQL Server Profiler</span></span>](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
 [<span data-ttu-id="62636-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="62636-119">Using Transact-SQL</span></span>](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 <span data-ttu-id="62636-120">**추적 템플릿 또는 추적 파일에서 이벤트를 추가하거나 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="62636-120">**To add or remove events from a trace template or trace file**</span></span>  
  
 [<span data-ttu-id="62636-121">SQL Server Profiler 사용</span><span class="sxs-lookup"><span data-stu-id="62636-121">Using SQL Server Profiler</span></span>](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="62636-122">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="62636-122">Using Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="62636-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62636-123">See Also</span></span>  
 [<span data-ttu-id="62636-124">추적 시작</span><span class="sxs-lookup"><span data-stu-id="62636-124">Start a Trace</span></span>](start-a-trace.md)  
  
  
