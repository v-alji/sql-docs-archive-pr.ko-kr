---
title: SQL Server Profiler-성능 카운터 제한 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 27bda135abaf9d91b078e36a69a87098a734acbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736699"
---
# <a name="sql-server-profiler---performance-counters-limit"></a><span data-ttu-id="6097d-102">SQL Server 프로파일러 - 성능 카운터 제한</span><span class="sxs-lookup"><span data-stu-id="6097d-102">SQL Server Profiler - Performance Counters Limit</span></span>
  <span data-ttu-id="6097d-103">성능 카운터 제한 대화 상자를 사용하여 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 추적과 상관 관계를 지정할 시스템 모니터 성능 로그 파일의 정보를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6097d-103">Use the Performance Counters Limit dialog box to limit the information from a System Monitor performance log file when correlating it with a [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace.</span></span> <span data-ttu-id="6097d-104">이 대화 상자를 사용하여 상관 관계를 지정하는 데 사용하도록 표시할 카운터를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6097d-104">You can use this dialog box to select counters that should be displayed and used for correlation.</span></span>  
  
 <span data-ttu-id="6097d-105">**성능 카운터 제한** 대화 상자에는 성능 로그 파일에 포함된 성능 개체 및 카운터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="6097d-105">The **Performance Counters Limit** dialog box is populated with the performance objects and counters that the performance log file contains.</span></span>  
  
### <a name="to-select-performance-objects-and-counters-to-correlate-with-a-trace"></a><span data-ttu-id="6097d-106">추적과 상관 관계를 지정할 성능 개체 및 카운터를 선택하려면</span><span class="sxs-lookup"><span data-stu-id="6097d-106">To select performance objects and counters to correlate with a trace</span></span>  
  
1.  <span data-ttu-id="6097d-107">성능 개체를 확장하여 성능 로그 파일에 포함된 카운터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6097d-107">Expand a performance object to see which counters are included in the performance log file.</span></span>  
  
2.  <span data-ttu-id="6097d-108">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 추적 파일과 상관 관계를 지정할 카운터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6097d-108">Check the counters that you want to correlate with the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace file.</span></span>  
  
     <span data-ttu-id="6097d-109">특정 성능 개체에 해당하는 모든 카운터를 선택하려면 성능 개체 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6097d-109">If you want to select all counters for a performance object, check the box that is adjacent to the performance object.</span></span> <span data-ttu-id="6097d-110">컴퓨터를 나타내는 최상위 노드를 선택하면 성능 로그 파일에 포함되어 있는 모든 성능 개체와 카운터가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="6097d-110">Checking the topmost node, which indicates the computer, selects all performance objects and counters contained in the performance log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6097d-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6097d-111">See Also</span></span>  
 [<span data-ttu-id="6097d-112">추적과 Windows 성능 로그 데이터의 상관 관계 지정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6097d-112">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
  
