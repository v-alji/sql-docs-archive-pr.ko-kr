---
title: Transact-SQL 스크립트 재생(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5abf22a1201ac927f12ef9e4cfdd1f6d3026d00a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737246"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a><span data-ttu-id="1d69a-102">Transact-SQL 스크립트 재생(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="1d69a-102">Replay a Transact-SQL Script (SQL Server Profiler)</span></span>
  <span data-ttu-id="1d69a-103">성능 문제에 대해 가능한 해결 방법을 테스트하는 경우 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 재생하고 변경 전후의 성능을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="1d69a-103">When you test possible solutions to a performance problem, use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to replay [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, and compare performance before and after your changes.</span></span>  
  
### <a name="to-replay-a-transact-sql-script"></a><span data-ttu-id="1d69a-104">Transact-SQL 스크립트를 재생하려면</span><span class="sxs-lookup"><span data-stu-id="1d69a-104">To replay a Transact-SQL script</span></span>  
  
1.  <span data-ttu-id="1d69a-105">**파일** 메뉴에서 **열기**를 가리킨 다음 **스크립트 파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d69a-105">On the **File** menu, point to **Open**, and then click **Script File**.</span></span>  
  
2.  <span data-ttu-id="1d69a-106">열려는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d69a-106">Select the [!INCLUDE[tsql](../../includes/tsql-md.md)] script file you want to open.</span></span> <span data-ttu-id="1d69a-107">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트가 재생에 필요한 이벤트를 포함하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d69a-107">Make sure that the [!INCLUDE[tsql](../../includes/tsql-md.md)] script contains events necessary for replay.</span></span> <span data-ttu-id="1d69a-108">자세한 내용은 [Replay Requirements](replay-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d69a-108">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
3.  <span data-ttu-id="1d69a-109">**재생** 메뉴에서 **시작**을 클릭하고 스크립트를 재생하려는 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1d69a-109">On the **Replay** menu, click **Start**, and connect to the server where you want to replay the script.</span></span>  
  
4.  <span data-ttu-id="1d69a-110">**재생 구성** 대화 상자에서 설정을 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1d69a-110">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d69a-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d69a-111">See Also</span></span>  
 <span data-ttu-id="1d69a-112">[추적 재생](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="1d69a-112">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="1d69a-113">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="1d69a-113">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
