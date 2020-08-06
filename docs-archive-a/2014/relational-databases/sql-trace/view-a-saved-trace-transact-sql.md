---
title: 저장된 추적 보기(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8b67760d575b651b089a6936adc945d74a1c62b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743143"
---
# <a name="view-a-saved-trace-transact-sql"></a><span data-ttu-id="5006f-102">저장된 추적 보기(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5006f-102">View a Saved Trace (Transact-SQL)</span></span>
  <span data-ttu-id="5006f-103">이 항목에서는 기본 제공 함수를 사용하여 저장된 추적을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5006f-103">This topic describes how to use built-in functions to view a saved trace.</span></span>  
  
### <a name="to-view-a-specific-trace"></a><span data-ttu-id="5006f-104">특정 추적을 보려면</span><span class="sxs-lookup"><span data-stu-id="5006f-104">To view a specific trace</span></span>  
  
1.  <span data-ttu-id="5006f-105">필요한 정보에 대한 추적 ID를 지정하여 **fn_trace_getinfo** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5006f-105">Execute **fn_trace_getinfo** by specifying the ID of the trace about which information is needed.</span></span> <span data-ttu-id="5006f-106">이 함수는 추적, 추적 속성, 속성 정보가 들어 있는 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5006f-106">This function returns a table that lists the trace, trace property, and information about the property.</span></span>  
  
     <span data-ttu-id="5006f-107">다음과 같이 이 함수를 호출하십시오.</span><span class="sxs-lookup"><span data-stu-id="5006f-107">Invoke the function this way:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a><span data-ttu-id="5006f-108">기존 추적을 모두 보려면</span><span class="sxs-lookup"><span data-stu-id="5006f-108">To view all existing traces</span></span>  
  
1.  <span data-ttu-id="5006f-109">**이나** 를 지정하여 `0` fn_trace_getinfo `default`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5006f-109">Execute **fn_trace_getinfo** by specifying `0` or `default`.</span></span> <span data-ttu-id="5006f-110">이 함수는 모든 추적, 추적 속성, 속성 정보가 들어 있는 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5006f-110">This function returns a table that lists all the traces, their properties, and information about these properties.</span></span>  
  
     <span data-ttu-id="5006f-111">다음과 같이 함수를 호출하십시오.</span><span class="sxs-lookup"><span data-stu-id="5006f-111">Invoke the function as follows:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a><span data-ttu-id="5006f-112">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="5006f-112">.NET Framework Security</span></span>  
 <span data-ttu-id="5006f-113">기본 제공 함수 **fn_trace_getinfo**를 실행하려면 사용자에게 다음과 같은 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5006f-113">To run the built-in function **fn_trace_getinfo**, the user needs the following permission:</span></span>  
  
 <span data-ttu-id="5006f-114">서버에 대한 ALTER TRACE</span><span class="sxs-lookup"><span data-stu-id="5006f-114">ALTER TRACE on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5006f-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5006f-115">See Also</span></span>  
 <span data-ttu-id="5006f-116">[sys.fn_trace_getinfo&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5006f-116">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span></span>  
 [<span data-ttu-id="5006f-117">SQL Server Profiler를 사용하여 추적 보기 및 분석</span><span class="sxs-lookup"><span data-stu-id="5006f-117">View and Analyze Traces with SQL Server Profiler</span></span>](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
