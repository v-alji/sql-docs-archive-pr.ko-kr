---
title: 추적 중지 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], stopping
- stopping traces
ms.assetid: 47c4f33d-63e0-4444-bec8-4c1c91f8e25c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 501ea4a4838f8e2ea42fc475c486466d48020a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734740"
---
# <a name="stop-a-trace-sql-server-profiler"></a><span data-ttu-id="e812a-102">추적 중지(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="e812a-102">Stop a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="e812a-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 실행 중인 추적을 중지하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e812a-103">This topic describes how to stop a trace that is running by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="e812a-104">추적을 중지하면 데이터 캡처가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e812a-104">Stopping a trace stops data from being captured.</span></span> <span data-ttu-id="e812a-105">추적을 중지한 후에 추적을 다시 시작하면 이전에 캡처한 데이터가 손실됩니다. 단, 데이터를 추적 파일 또는 추적 테이블로 캡처해 두었던 경우에는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e812a-105">After a trace is stopped, it cannot be restarted without losing previously captured data, unless the data has been captured to a trace file or trace table.</span></span> <span data-ttu-id="e812a-106">또한 추적을 중지한 후 수집된 데이터를 테이블이나 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e812a-106">You can also save the collected data to a table or file after stopping a trace.</span></span> <span data-ttu-id="e812a-107">추적이 중지될 때 이전에 선택한 모든 추적 속성은 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="e812a-107">All trace properties that were previously selected are preserved when a trace is stopped.</span></span> <span data-ttu-id="e812a-108">추적이 중지되면 이름, 이벤트, 열 및 필터를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e812a-108">When a trace is stopped, you can change the name, events, columns, and filters.</span></span>  
  
### <a name="to-stop-a-trace"></a><span data-ttu-id="e812a-109">추적을 중지하려면</span><span class="sxs-lookup"><span data-stu-id="e812a-109">To stop a trace</span></span>  
  
1.  <span data-ttu-id="e812a-110">실행 중인 추적을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e812a-110">Select a trace that is running.</span></span>  
  
2.  <span data-ttu-id="e812a-111">**파일** 메뉴에서 **추적 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e812a-111">On the **File** menu, click **Stop Trace**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e812a-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e812a-112">See Also</span></span>  
 [<span data-ttu-id="e812a-113">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="e812a-113">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
