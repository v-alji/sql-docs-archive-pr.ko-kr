---
title: 추적 테이블에 최대 테이블 크기 설정(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f48efbe02e300e06faf857ed0fb36ae340ad979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727559"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a><span data-ttu-id="25356-102">추적 테이블에 최대 테이블 크기 설정(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="25356-102">Set a Maximum Table Size for a Trace Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="25356-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적 테이블의 최대 테이블 크기를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-103">This topic describes how to set a maximum table size for trace tables by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a><span data-ttu-id="25356-104">추적 테이블에 최대 테이블 크기를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="25356-104">To set a maximum table size for a trace table</span></span>  
  
1.  <span data-ttu-id="25356-105">**파일** 메뉴에서 **새 추적**을 클릭한 다음 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-105">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="25356-106">**추적 속성**대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25356-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="25356-107">**연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="25356-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="25356-108">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="25356-109">**추적 이름** 입력란에 추적의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="25356-110">**템플릿 이름**목록에서 추적 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-110">In the **Template name**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="25356-111">**테이블에 저장**확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-111">Select the **Save to table**check box.</span></span>  
  
5.  <span data-ttu-id="25356-112">추적을 저장하려는 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-112">Connect to the server on which you want the trace to be stored.</span></span>  
  
     <span data-ttu-id="25356-113">**대상 테이블** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25356-113">The **Destination Table** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="25356-114">**데이터베이스** 목록에서 추적할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-114">Select a database for the trace from the **Database** list.</span></span>  
  
7.  <span data-ttu-id="25356-115">**테이블** 입력란에 테이블 이름을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-115">In the **Table** box, type or select a table name.</span></span>  
  
8.  <span data-ttu-id="25356-116">**최대 행 수 설정** 확인란을 선택하고 추적 테이블의 최대 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25356-116">Select the **Set maximum rows** check box, and specify a maximum number of rows for the trace table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="25356-117">테이블의 행 수가 지정한 최대 값을 초과하면 추적 이벤트는 더 이상 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25356-117">When the number of rows in the table exceeds the maximum that you have specified, the trace events are no longer recorded.</span></span> <span data-ttu-id="25356-118">하지만 추적은 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="25356-118">However, tracing continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25356-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25356-119">See Also</span></span>  
 <span data-ttu-id="25356-120">[SQL Server 프로파일러](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="25356-120">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="25356-121">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="25356-121">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
