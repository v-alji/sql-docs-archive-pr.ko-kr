---
title: Showplan XML Statistics Profile 이벤트를 개별적으로 저장(SQL Server Profiler) | Microsoft 문서
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
ms.assetid: df393f13-d538-4d94-8155-9c2fdf5f755d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: be0c02f8396df81af803c365b9ede42610353ed3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732607"
---
# <a name="save-showplan-xml-statistics-profile-events-separately-sql-server-profiler"></a><span data-ttu-id="23472-102">Showplan XML Statistics Profile 이벤트를 개별적으로 저장(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="23472-102">Save Showplan XML Statistics Profile Events Separately (SQL Server Profiler)</span></span>
  <span data-ttu-id="23472-103">이 항목에서는 추적에서 캡처된 **Showplan XML Statistics Profile** 이벤트를 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 개별적인 .SQLPlan 파일로 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-103">This topic describes how to save **Showplan XML Statistics Profile** events that are captured in traces into separate .SQLPlan files by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="23472-104">**에서** Showplan XML Statistics Profile [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]이벤트 파일을 열어 각 이벤트에 대한 그래픽 실행 계획을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23472-104">You can open the **Showplan XML Statistics Profile** event files in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], which enables you to view the graphical execution plan for each event.</span></span>  
  
### <a name="to-save-showplan-xml-statistics-events-separately"></a><span data-ttu-id="23472-105">Showplan XML Statistics Profile 이벤트를 개별적으로 저장하려면</span><span class="sxs-lookup"><span data-stu-id="23472-105">To save Showplan XML statistics events separately</span></span>  
  
1.  <span data-ttu-id="23472-106">**파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-106">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="23472-107">**추적 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="23472-107">The **Trace Properties** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23472-108">**연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="23472-108">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box does not appear and the trace begins instead.</span></span> <span data-ttu-id="23472-109">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="23472-110">**추적 속성** 대화 상자에서 **추적 이름** 입력란에 추적의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-110">In the **Trace Properties** dialog box, type a name for the trace in the **Trace name** box.</span></span>  
  
3.  <span data-ttu-id="23472-111">**템플릿 사용** 목록에서 추적의 기반이 되는 추적 템플릿을 선택하거나 템플릿을 사용하지 않을 경우 **비어 있음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-111">In the **Use the template** list, select a trace template to base the trace on, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="23472-112">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="23472-113">추적을 데이터베이스 테이블에 캡처하려면**파일에 저장**을 클릭하면 추적이 파일에 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="23472-113">Click**Save to file**to capture the trace to a file.</span></span> <span data-ttu-id="23472-114">**최대 파일 크기 설정**에 대한 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-114">Specify a value for **Set maximum file size**.</span></span>  
  
         <span data-ttu-id="23472-115">필요에 따라 **파일 롤오버 사용** 및 **서버에서 추적 데이터 처리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-115">Optionally select **Enable file rollover** and **Server processes trace data**.</span></span>  
  
    -   <span data-ttu-id="23472-116">추적을 데이터베이스 테이블에 캡처하려면**테이블에 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-116">Click**Save to table** to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="23472-117">필요에 따라 **최대 행 수 설정**을 클릭하고 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-117">Optionally click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="23472-118">필요에 따라 **추적 중지 시간 설정** 확인란을 선택 하 고 중지 날짜 및 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-118">Optionally select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="23472-119">**이벤트 선택**탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="23472-120">**Events**데이터 열에서 **Performance**이벤트 범주를 확장한 다음 **Showplan XML Statistics Profile**확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-120">In the **Events**data column, expand the **Performance**event category, and then select the **Showplan XML Statistics Profile**check box.</span></span> <span data-ttu-id="23472-121">**Performance** 이벤트 범주가 나타나지 않는 경우 **모든 이벤트 표시** 를 선택하여 이 범주를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-121">If the **Performance** event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="23472-122">**이벤트 추출 설정**탭이 **추적 속성**대화 상자에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="23472-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog.</span></span>  
  
8.  <span data-ttu-id="23472-123">**이벤트 추출 설정**탭에서 **별도로 XML 실행 계획 이벤트 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-123">On the **Events Extraction Settings**tab, click **Save XML Showplan events separately**.</span></span>  
  
9. <span data-ttu-id="23472-124">**다른 이름으로 저장** 대화 상자에서 **Showplan XML Statistics Profile** 이벤트를 저장할 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-124">In the **Save As** dialog box, enter the file name to store the **Showplan XML Statistics Profile** events.</span></span>  
  
10. <span data-ttu-id="23472-125">추적을 데이터베이스 테이블에 캡처하려면 **모든 XML 실행 계획 일괄 처리를 단일 파일로 저장** 을 클릭하여 모든 **Showplan XML Statistics Profile** 이벤트를 단일 XML 파일에 저장하거나 **각 XML 실행 계획 일괄 처리를 개별 파일로 저장**을 클릭하여 각 **Showplan XML Statistics Profile** 이벤트에 대해 새 XML 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23472-125">Click **All batches in a single file** to save all **Showplan XML Statistics Profile** events in a single XML file, or click **Each XML Showplan batch in a distinct file**to create a new XML file for each **Showplan XML Statistics Profile** event.</span></span>  
  
11. <span data-ttu-id="23472-126">SQL Server Management Studio에서 **Showplan XML Statistics Profile** 이벤트 파일을 보려면 **파일** 메뉴에서 **열기**를 가리킨 다음 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23472-126">To view the **Showplan XML Statistics Profile** event file in SQL Server Management Studio, on the **File** menu, point to **Open**, and click **File**.</span></span> <span data-ttu-id="23472-127">**Showplan XML Statistics Profile** 이벤트 파일을 저장한 디렉터리로 이동한 다음 파일을 선택하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="23472-127">Navigate to the directory where you saved the **Showplan XML Statistics Profile** event file or files to select one and open it.</span></span> <span data-ttu-id="23472-128">**Showplan XML Statistics Profile** 이벤트 파일의 확장명은 .SQLPlan입니다.</span><span class="sxs-lookup"><span data-stu-id="23472-128">**Showplan XML Statistics Profile** event files have a .SQLPlan file extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23472-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23472-129">See Also</span></span>  
 [<span data-ttu-id="23472-130">SQL Server Profiler에서 SHOWPLAN 결과로 쿼리 분석</span><span class="sxs-lookup"><span data-stu-id="23472-130">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
