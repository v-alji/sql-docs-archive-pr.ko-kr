---
title: 추적 일시 중지 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
author: stevestein
ms.author: sstein
ms.openlocfilehash: cdc9dbbd01099b1d33787a72b0bd59b65cea722e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727568"
---
# <a name="pause-a-trace-sql-server-profiler"></a><span data-ttu-id="1359d-102">추적 일시 중지(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="1359d-102">Pause a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="1359d-103">추적을 일시 중지하면 다시 시작할 때까지는 이벤트 데이터가 더 이상 캡처되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1359d-103">Pausing a trace prevents further event data from being captured until the trace is restarted.</span></span>  
  
 <span data-ttu-id="1359d-104">추적을 일시 중지하면 다시 시작할 때까지는 이벤트 데이터가 더 이상 캡처되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1359d-104">When you pause a trace, you prevent event data from being captured until the trace is restarted.</span></span> <span data-ttu-id="1359d-105">추적을 다시 시작하면 추적 작업이 재개됩니다.</span><span class="sxs-lookup"><span data-stu-id="1359d-105">Restarting a trace lets trace operations resume.</span></span> <span data-ttu-id="1359d-106">다시 시작한 후 이전에 캡처한 데이터는 손실되지 않으며</span><span class="sxs-lookup"><span data-stu-id="1359d-106">No previously captured data is lost after a restart.</span></span> <span data-ttu-id="1359d-107">추적이 다시 시작되면 데이터 캡처는 일시 중지되었던 시점부터 재개됩니다.</span><span class="sxs-lookup"><span data-stu-id="1359d-107">When the trace is restarted, data capturing resumes from that point onward.</span></span> <span data-ttu-id="1359d-108">추적이 일시 중지된 동안 이름, 이벤트, 열 및 필터를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1359d-108">While a trace is paused, you can change the name, events, columns, and filters.</span></span> <span data-ttu-id="1359d-109">하지만 추적 데이터를 보낼 대상을 변경하거나 서버 연결을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1359d-109">However, you cannot change the destinations to which you are sending the trace data, nor change the server connection.</span></span>  
  
### <a name="to-pause-a-trace"></a><span data-ttu-id="1359d-110">추적을 일시 중지하려면</span><span class="sxs-lookup"><span data-stu-id="1359d-110">To pause a trace</span></span>  
  
1.  <span data-ttu-id="1359d-111">실행 중인 추적이 포함된 창을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1359d-111">Select a window that contains a running trace.</span></span>  
  
2.  <span data-ttu-id="1359d-112">**파일** 메뉴에서 **추적 일지 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1359d-112">On the **File** menu, click **Pause Trace**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1359d-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1359d-113">See Also</span></span>  
 [<span data-ttu-id="1359d-114">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="1359d-114">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
