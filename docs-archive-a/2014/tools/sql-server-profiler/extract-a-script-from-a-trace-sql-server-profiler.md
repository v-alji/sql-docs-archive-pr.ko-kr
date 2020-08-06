---
title: 추적에서 스크립트 추출(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6633fafb8a39b189093044ef39694afa601af7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727567"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a><span data-ttu-id="25da5-102">추적에서 스크립트 추출(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="25da5-102">Extract a Script from a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="25da5-103">이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 를 사용하여 추적 파일이나 테이블에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이벤트를 추출하고 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]스크립트 파일로 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="25da5-103">This topic describes how to extract [!INCLUDE[tsql](../../includes/tsql-md.md)] events from a trace file or table and save them as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a><span data-ttu-id="25da5-104">추적 파일이나 테이블에서 Transact-SQL 스크립트를 추출하려면</span><span class="sxs-lookup"><span data-stu-id="25da5-104">To extract a Transact-SQL script from a trace file or table</span></span>  
  
1.  <span data-ttu-id="25da5-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 파일로 저장할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이벤트를 포함하는 추적 파일이나 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="25da5-105">Open a trace file or table that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] events that you want to save to a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="25da5-106">자세한 내용은 [추적 파일 열기&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 열기&#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)에서 제공되는 사전 정의된 튜닝 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="25da5-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="25da5-107">**파일** 메뉴에서 **내보내기**, **SQL Server 이벤트 추출**을 차례로 가리킨 다음 **Transact-SQL 이벤트 추출**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25da5-107">On the **File** menu, point to **Export**, point to **Extract SQL Server Events**, and then click **Extract Transact-SQL Events**.</span></span>  
  
3.  <span data-ttu-id="25da5-108">**다른 이름으로 저장** 대화 상자에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 파일의 이름을 입력한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25da5-108">In the **Save As** dialog box, type a name for the [!INCLUDE[tsql](../../includes/tsql-md.md)] file, and click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25da5-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25da5-109">See Also</span></span>  
 [<span data-ttu-id="25da5-110">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="25da5-110">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
