---
title: 필터 정보 보기 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 931b83f8087d446cfc7b08d9582cbad5b02cf671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648733"
---
# <a name="view-filter-information-sql-server-profiler"></a><span data-ttu-id="edf71-102">필터 정보 보기(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="edf71-102">View Filter Information (SQL Server Profiler)</span></span>
  <span data-ttu-id="edf71-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 이벤트 클래스의 데이터 열에서 필터를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="edf71-103">This topic describes how to view filters on data columns for event classes by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-view-filter-information"></a><span data-ttu-id="edf71-104">필터 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="edf71-104">To view filter information</span></span>  
  
1.  <span data-ttu-id="edf71-105">추적 파일, 추적 테이블 또는 SQL 스크립트를 열고 **파일** 메뉴에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="edf71-105">Open a trace file, trace table, or SQL script, and on the **File** menu, click **Properties**.</span></span> <span data-ttu-id="edf71-106">추적 템플릿을 편집하거나 새 추적을 만들 경우에는 이 단계를 건너뛰십시오.</span><span class="sxs-lookup"><span data-stu-id="edf71-106">If you are editing a trace template or creating a new trace, skip this step.</span></span>  
  
2.  <span data-ttu-id="edf71-107">**이벤트 선택** 탭에서 보려는 필터의 데이터 열 이름을 마우스 오른쪽 단추로 클릭하고 **열 필터 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="edf71-107">On the **Events Selection** tab, right-click the data column name for the filter you want to view, and click **Edit Column Filter**.</span></span>  
  
3.  <span data-ttu-id="edf71-108">**필터 편집** 대화 상자에서 필터 비교 연산자를 확장하여 지정된 조건에 할당된 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="edf71-108">In the **Edit Filter** dialog box, expand the filter comparison operators to see the assigned value for the specified criterion.</span></span> <span data-ttu-id="edf71-109">필터 정보를 보려는 모든 열에 대해 단계 2와 3을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="edf71-109">Repeat Steps 2 and 3 for all columns for which you want to view filter information.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="edf71-110">할당 값이 있는 비교 연산자는 굵게 서식이 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edf71-110">Comparison operators with assigned values are formatted bold.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf71-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="edf71-111">See Also</span></span>  
 [<span data-ttu-id="edf71-112">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="edf71-112">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
