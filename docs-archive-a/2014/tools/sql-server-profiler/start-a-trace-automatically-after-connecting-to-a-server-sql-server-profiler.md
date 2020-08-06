---
title: 서버 연결 후 자동으로 추적 시작(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- automatic trace start
- traces [SQL Server], starting
- starting trace automatically
ms.assetid: d74b848d-e796-49af-a8c5-dd69230f3a78
author: stevestein
ms.author: sstein
ms.openlocfilehash: a2c8cae3e47a6f48014cbafe588dde782c097260
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734752"
---
# <a name="start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler"></a><span data-ttu-id="e17cd-102">서버 연결 후 자동으로 추적 시작(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="e17cd-102">Start a Trace Automatically after Connecting to a Server (SQL Server Profiler)</span></span>
  <span data-ttu-id="e17cd-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]인스턴스에 연결한 후 추적을 자동으로 시작하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e17cd-103">This topic describes how to start traces automatically after connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-start-a-trace-automatically-after-connecting-to-a-server-with-sql-server-profiler"></a><span data-ttu-id="e17cd-104">SQL Server Profiler를 사용하여 서버에 연결한 후 추적을 자동으로 시작하려면</span><span class="sxs-lookup"><span data-stu-id="e17cd-104">To start a trace automatically after connecting to a server with SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="e17cd-105">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e17cd-105">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="e17cd-106">**연결한 후 즉시 추적 시작** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e17cd-106">Select the **Start tracing immediately after making a connection** check box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e17cd-107">**연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e17cd-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="e17cd-108">추적 속성을 편집하려면 먼저 이 옵션을 선택 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e17cd-108">To edit trace properties, you must first turn this setting off.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e17cd-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e17cd-109">See Also</span></span>  
 [<span data-ttu-id="e17cd-110">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="e17cd-110">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
