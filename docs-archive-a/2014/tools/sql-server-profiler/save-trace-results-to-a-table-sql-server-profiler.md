---
title: 테이블에 추적 결과 저장(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 08acfb4e7136f8b28d1c990d508b8578f96a57b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737186"
---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a><span data-ttu-id="4ffa9-102">테이블에 추적 결과 저장(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="4ffa9-102">Save Trace Results to a Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="4ffa9-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적 결과를 데이터베이스 테이블에 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-103">This topic describes how to save trace results to a database table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-save-trace-results-to-a-table"></a><span data-ttu-id="4ffa9-104">추적 결과를 테이블에 저장하려면</span><span class="sxs-lookup"><span data-stu-id="4ffa9-104">To save trace results to a table</span></span>  
  
1.  <span data-ttu-id="4ffa9-105">**파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="4ffa9-106">**추적 속성**대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4ffa9-107">**연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="4ffa9-108">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="4ffa9-109">**추적 이름** 입력란에 추적 이름을 입력한 다음 **테이블에 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-109">In the **Trace name** box, type a name for the trace, and then click **Save to table**.</span></span>  
  
3.  <span data-ttu-id="4ffa9-110">**서버에 연결** 대화 상자에서 추적 테이블을 포함할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-110">In the **Connect to server** dialog box, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that will contain the trace table.</span></span>  
  
4.  <span data-ttu-id="4ffa9-111">**대상 테이블** 대화 상자의 **데이터베이스**목록에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-111">In the **Destination Table** dialog box, select a database from the **Database**list.</span></span>  
  
5.  <span data-ttu-id="4ffa9-112">**소유자** 목록에서 추적의 소유자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-112">In the **Owner** list, select the owner for the trace.</span></span>  
  
6.  <span data-ttu-id="4ffa9-113">**테이블** 목록에서 추적 결과에 대한 테이블 이름을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-113">In the **Table** list, type or select the table name for the trace results.</span></span> <span data-ttu-id="4ffa9-114">**확인.**</span><span class="sxs-lookup"><span data-stu-id="4ffa9-114">Click **OK.**</span></span>  
  
7.  <span data-ttu-id="4ffa9-115">**추적 속성** 대화 상자에서 **최대 행 수 설정 (천 단위)** 확인란을 선택 하 여 저장할 최대 행 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-115">In the **Trace Properties** dialog box, select the **Set maximum rows (in thousands)** check box to specify the maximum number of rows to save.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ffa9-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ffa9-116">See Also</span></span>  
 [<span data-ttu-id="4ffa9-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="4ffa9-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
