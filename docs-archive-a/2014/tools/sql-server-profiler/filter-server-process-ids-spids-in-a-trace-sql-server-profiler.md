---
title: 추적의 SPID(서버 프로세스 ID) 필터링(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
author: stevestein
ms.author: sstein
ms.openlocfilehash: 99ae7eac6f19bd942a04f97b0a7da580eadc9dbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739021"
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a><span data-ttu-id="7af02-102">추적의 SPID(서버 프로세스 ID) 필터링(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="7af02-102">Filter Server Process IDs (SPIDs) in a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="7af02-103">이 항목은 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적에서 SPID(서버 프로세스 식별자)를 필터링하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-103">This topic describes how to filter server process identifiers (SPIDs) in a trace by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-system-ids-in-a-trace"></a><span data-ttu-id="7af02-104">추적에서 시스템 ID를 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="7af02-104">To filter system IDs in a trace</span></span>  
  
1.  <span data-ttu-id="7af02-105">**파일** 메뉴에서 **새 추적**을 클릭한 다음 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-105">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="7af02-106">**추적 속성**대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7af02-107">연결한 **후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-107">if **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="7af02-108">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="7af02-109">**추적 이름** 입력란에 추적의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="7af02-110">**템플릿 사용**이름 목록에서 추적 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-110">In the **Use the template**name list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="7af02-111">필요에 따라 추적 결과를 저장할 대상 파일이나 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-111">Optionally, specify a destination file or table in which to save the trace results.</span></span>  
  
5.  <span data-ttu-id="7af02-112">**이벤트 선택**탭에서 **SPID**열 머리글을 클릭하여 **필터 편집** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-112">On the **Events Selection**tab, click the **SPID**column heading to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="7af02-113">또는 열 머리글을 마우스 오른쪽 단추로 클릭하고 **열 필터 편집**을 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-113">You can also right-click the column heading and choose **Edit Column Filter**.</span></span> <span data-ttu-id="7af02-114">**SPID** 열이 표시되지 않는 경우에는 **모든 열 표시** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-114">If the **SPID** column does not appear, check the **Show all columns** box.</span></span>  
  
6.  <span data-ttu-id="7af02-115">**필터 편집** 대화 상자에서 적절한 비교 연산자를 확장한 다음 비교할 값으로 SPID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7af02-115">In the **Edit Filter** dialog box, expand the appropriate comparison operator, and enter a SPID as a value for the comparison.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af02-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7af02-116">See Also</span></span>  
 [<span data-ttu-id="7af02-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="7af02-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
