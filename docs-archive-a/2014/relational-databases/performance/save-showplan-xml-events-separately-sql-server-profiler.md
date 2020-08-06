---
title: Showplan XML 이벤트를 개별적으로 저장(SQL Server Profiler) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: 33320a7a-36e8-401c-876d-5b82c49abd85
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 240fb408bb3ed8585ecc915ba4829ac21285d241
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660504"
---
# <a name="save-showplan-xml-events-separately-sql-server-profiler"></a><span data-ttu-id="fc84f-102">Showplan XML 이벤트를 개별적으로 저장(SQL Server 프로파일러)</span><span class="sxs-lookup"><span data-stu-id="fc84f-102">Save Showplan XML Events Separately (SQL Server Profiler)</span></span>
  <span data-ttu-id="fc84f-103">이 항목에서는 **를 사용하여 추적에서 캡처된** Showplan XML [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]이벤트를 개별 .SQLPLan 파일에 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-103">This topic describes how to save **Showplan XML** events that are captured in traces into separate .SQLPlan files by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="fc84f-104">**에서** Showplan XML [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]이벤트 파일을 열면 각 이벤트에 대한 그래픽 실행 계획을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-104">You can open the **Showplan XML** event files in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], which enables you to view the graphical execution plan for each event.</span></span>  
  
### <a name="to-save-showplan-xml-events-separately"></a><span data-ttu-id="fc84f-105">Showplan XML 이벤트를 개별적으로 저장하려면</span><span class="sxs-lookup"><span data-stu-id="fc84f-105">To save Showplan XML events separately</span></span>  
  
1.  <span data-ttu-id="fc84f-106">**파일** 메뉴에서 **새 추적**을 클릭한 다음 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-106">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="fc84f-107">**추적 속성**대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-107">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc84f-108">**연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-108">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="fc84f-109">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="fc84f-110">**추적 속성** 대화 상자에서 **추적 이름** 입력란에 추적의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-110">In the **Trace Properties** dialog box, type a name for the trace in the **Trace name** box.</span></span>  
  
3.  <span data-ttu-id="fc84f-111">**템플릿 사용** 목록에서 추적의 기반이 되는 추적 템플릿을 선택하거나 템플릿을 사용하지 않을 경우 **비어 있음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-111">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="fc84f-112">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="fc84f-113">추적을 데이터베이스 테이블에 캡처하려면**파일에 저장** 확인란을 선택하면 추적이 파일에 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-113">Select the**Save to file** check box to capture the trace to a file.</span></span> <span data-ttu-id="fc84f-114">**최대 파일 크기 설정**에 대한 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-114">Specify a value for **Set maximum file size**.</span></span> <span data-ttu-id="fc84f-115">또는 **파일 롤오버 사용** 및 **서버에서 추적 데이터 처리** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-115">Optionally, select the **Enable file rollover** and **Server processes trace data** check boxes.</span></span>  
  
    -   <span data-ttu-id="fc84f-116">추적을 데이터베이스 테이블에 캡처하려면**테이블에 저장** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-116">Select the**Save to table** check box to capture the trace to a database table.</span></span> <span data-ttu-id="fc84f-117">필요에 따라 **최대 행 수 설정**을 클릭하고 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-117">Optionally click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="fc84f-118">필요에 따라 **추적 중지 시간 설정** 확인란을 선택하여 중지 날짜 및 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-118">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="fc84f-119">**이벤트 선택**탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="fc84f-120">**Events**데이터 열에서 **Performance**이벤트 범주를 확장한 다음 **Showplan XML**확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-120">In the **Events**data column, expand the **Performance**event category, and then select the **Showplan XML**check box.</span></span> <span data-ttu-id="fc84f-121">**Performance** 이벤트 범주가 나타나지 않는 경우 **모든 이벤트 표시** 를 선택하여 이 범주를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-121">If the **Performance** event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="fc84f-122">**이벤트 추출 설정**탭이 **추적 속성**대화 상자에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog box.</span></span>  
  
8.  <span data-ttu-id="fc84f-123">**이벤트 추출 설정**탭에서 **별도로 XML 실행 계획 이벤트 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-123">On the **Events Extraction Settings**tab, click **Save XML Showplan events separately**.</span></span>  
  
9. <span data-ttu-id="fc84f-124">**다른 이름으로 저장** 대화 상자에 **Showplan XML** 이벤트를 저장할 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-124">In the **Save As** dialog box, enter the name of the file in which to store the **Showplan XML** events.</span></span>  
  
10. <span data-ttu-id="fc84f-125">**모든 XML 실행 계획 일괄 처리를 단일 파일로 저장** 을 클릭하여 모든 **Showplan XML** 이벤트를 단일 XML 파일에 저장하거나 **각 XML 실행 계획 일괄 처리를 개별 파일로 저장**을 클릭하여 **Showplan XML** 이벤트마다 새 XML 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-125">Click **All XML Showplan batches in a single file** to save all **Showplan XML** events in a single XML file, or click **Each XML Showplan batch in a distinct file**to create a new XML file for each **Showplan XML** event.</span></span>  
  
11. <span data-ttu-id="fc84f-126">SQL Server Management Studio의 **Showplan XML** 이벤트 파일을 보려면 **파일** 메뉴에서 **열기**를 가리키고 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-126">To view the **Showplan XML** event file in SQL Server Management Studio, on the **File** menu, point to **Open**, and click **File**.</span></span> <span data-ttu-id="fc84f-127">**Showplan XML** 이벤트 파일을 저장한 디렉터리를 탐색하여 하나를 선택한 다음 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-127">Navigate to the directory where you saved the **Showplan XML** event file or files to select one and open it.</span></span> <span data-ttu-id="fc84f-128">**Showplan XML** 이벤트 파일의 파일 확장자는 .SQLPlan입니다.</span><span class="sxs-lookup"><span data-stu-id="fc84f-128">**Showplan XML** event files have a .SQLPlan file extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc84f-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc84f-129">See Also</span></span>  
 [<span data-ttu-id="fc84f-130">SQL Server Profiler에서 SHOWPLAN 결과로 쿼리 분석</span><span class="sxs-lookup"><span data-stu-id="fc84f-130">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
