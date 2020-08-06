---
title: 추적 파일 또는 추적 테이블에서 템플릿 파생(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
ms.assetid: 305817b7-4d23-49fb-9e6c-4d34359877bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: c36ff25c87dd834862d28b9fcdceecfbd38e59f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727572"
---
# <a name="derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler"></a><span data-ttu-id="7762f-102">추적 파일 또는 추적 테이블에서 템플릿 파생(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="7762f-102">Derive a Template from a Trace File or Trace Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="7762f-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 기존 추적 파일이나 테이블에서 추적 템플릿을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7762f-103">This topic describes how to create a trace template from an existing trace file or table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-derive-a-template-from-a-trace-file-or-trace-table"></a><span data-ttu-id="7762f-104">추적 파일 또는 추적 테이블에서 템플릿을 파생시키려면</span><span class="sxs-lookup"><span data-stu-id="7762f-104">To derive a template from a trace file or trace table</span></span>  
  
1.  <span data-ttu-id="7762f-105">템플릿의 기반이 될 추적 파일이나 추적 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7762f-105">Open the trace file or trace table on which you want to base your template.</span></span> <span data-ttu-id="7762f-106">자세한 내용은 [추적 파일 열기&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 열기&#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)에서 제공되는 사전 정의된 튜닝 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7762f-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="7762f-107">**파일** 메뉴에서 **다른 이름으로 저장**을 가리킨 다음 **추적 템플릿**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7762f-107">On the **File** menu, point to **Save As**, and then click **Trace Template**.</span></span>  
  
3.  <span data-ttu-id="7762f-108">이름을 입력하거나 목록에서 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7762f-108">Type a name or select one from the list.</span></span> <span data-ttu-id="7762f-109">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7762f-109">Click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7762f-110">기존 템플릿 파일을 선택하면 파일을 덮어쓸 것인지를 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7762f-110">If you select an existing template file, you are asked if you want to overwrite the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7762f-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7762f-111">See Also</span></span>  
 <span data-ttu-id="7762f-112">[추적 템플릿 만들기&#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7762f-112">[Create a Trace Template &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7762f-113">[추적 템플릿 수정&#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7762f-113">[Modify a Trace Template &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7762f-114">[실행 중인 추적으로부터 템플릿 파생&#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7762f-114">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="7762f-115">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="7762f-115">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
