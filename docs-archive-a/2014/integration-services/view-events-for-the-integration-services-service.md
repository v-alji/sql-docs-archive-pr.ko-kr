---
title: Integration Services 서비스에 대 한 이벤트 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- events [Integration Services]
- service [Integration Services], events
- Integration Services service, events
ms.assetid: 37e23946-10d1-4116-8568-8fd24067102e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a513c8fc917da2987f3619c8eb9011e1170f7dcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659521"
---
# <a name="view-events-for-the-integration-services-service"></a><span data-ttu-id="9dad0-102">Integration Services 서비스의 뷰 이벤트</span><span class="sxs-lookup"><span data-stu-id="9dad0-102">View Events for the Integration Services Service</span></span>
  <span data-ttu-id="9dad0-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스의 이벤트는 다음 두 도구를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-103">There are two tools in which you can view events for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service:</span></span>  
  
-   <span data-ttu-id="9dad0-104">**의** 로그 파일 뷰어 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]대화 상자.</span><span class="sxs-lookup"><span data-stu-id="9dad0-104">The **Log File Viewer** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9dad0-105">**로그 파일 뷰어** 대화 상자에는 로그를 내보내고 필터링하고 검색하는 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-105">The **Log File Viewer** dialog box includes options to export, filter, and search the log.</span></span> <span data-ttu-id="9dad0-106">**로그 파일 뷰어**의 옵션에 대한 자세한 내용은 [로그 파일 뷰어 F1 도움말](../relational-databases/logs/log-file-viewer-f1-help.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9dad0-106">For more information about the options in the **Log File Viewer**, see [Log File Viewer F1 Help](../relational-databases/logs/log-file-viewer-f1-help.md).</span></span>  
  
-   <span data-ttu-id="9dad0-107">Windows 이벤트 뷰어</span><span class="sxs-lookup"><span data-stu-id="9dad0-107">The Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="9dad0-108">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 의해 기록된 이벤트에 대한 설명은 [Integration Services 서비스에서 기록하는 이벤트](service/events-logged-by-the-integration-services-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9dad0-108">For descriptions of the events logged by the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, see [Events Logged by the Integration Services Service](service/events-logged-by-the-integration-services-service.md).</span></span>  
  
### <a name="to-view-service-events-for-integration-services-in-sql-server-management-studio"></a><span data-ttu-id="9dad0-109">SQL Server Management Studio에서 Integration Services의 서비스 이벤트를 보려면</span><span class="sxs-lookup"><span data-stu-id="9dad0-109">To view service events for Integration Services in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="9dad0-110">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-110">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="9dad0-111">**파일** 메뉴에서 **개체 탐색기 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-111">On the **File** menu, click **Connect Object Explorer**.</span></span>  
  
3.  <span data-ttu-id="9dad0-112">**서버에 연결** 대화 상자에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버 유형을 선택하고 연결할 서버를 선택하거나 찾은 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-112">In the **Connect to Server** dialog box, select the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server type, select or locate the server to connect to, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="9dad0-113">개체 탐색기에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 를 마우스 오른쪽 단추로 클릭하고 **로그 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-113">In Object Explorer, right-click [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and click **View Logs**.</span></span>  
  
5.  <span data-ttu-id="9dad0-114">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 이벤트를 보려면 **SQL Server Integration Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-114">To view [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] events, select **SQL Server Integration Services**.</span></span> <span data-ttu-id="9dad0-115">**NT 이벤트** 옵션은 **SQL Server Integration Services** 옵션에 따라 자동으로 선택 및 선택 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-115">The **NT Events** option is automatically selected and cleared with the **SQL Server Integration Services** option.</span></span>  
  
### <a name="to-view-service-events-for-integration-services-in-windows-event-viewer"></a><span data-ttu-id="9dad0-116">Windows 이벤트 뷰어에서 Integration Services의 서비스 이벤트를 보려면</span><span class="sxs-lookup"><span data-stu-id="9dad0-116">To view service events for Integration Services in Windows Event Viewer</span></span>  
  
1.  <span data-ttu-id="9dad0-117">클래식 보기를 사용할 경우에는 **제어판**에서 **관리 도구**를 클릭하고 종류별 보기를 사용할 경우에는 제어판에서 **성능 및 유지 관리** 를 클릭한 후 **관리 도구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-117">In **Control Panel**, if you are using Classic View, click **Administrative Tools**, or, if you are using Category View, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="9dad0-118">**이벤트 뷰어**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-118">Click **Event Viewer**.</span></span>  
  
3.  <span data-ttu-id="9dad0-119">**이벤트 뷰어** 대화 상자에서 **애플리케이션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-119">In the **Event Viewer** dialog box, click **Application**.</span></span>  
  
4.  <span data-ttu-id="9dad0-120">**애플리케이션** 스냅인의 **원본** 열 값이 **SQLISService**인 항목을 찾아 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-120">In the **Application** snap-in, locate an entry in the **Source** column that has the value **SQLISService**, right-click the entry, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="9dad0-121">필요에 따라 위쪽 또는 아래쪽 화살표를 클릭하여 이전 또는 다음 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-121">Optionally, click the up or down arrow to show the previous or next event.</span></span>  
  
6.  <span data-ttu-id="9dad0-122">필요에 따라 클립보드로 복사 아이콘을 클릭하여 이벤트 정보를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-122">Optionally, click the Copy to Clipboard icon to copy the event information.</span></span>  
  
7.  <span data-ttu-id="9dad0-123">바이트 또는 워드를 사용하여 이벤트 데이터를 표시하도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-123">Choose to display event data using bytes or words.</span></span>  
  
8.  <span data-ttu-id="9dad0-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-124">Click **OK**.</span></span>  
  
9. <span data-ttu-id="9dad0-125">**파일** 메뉴에서 **끝내기** 를 클릭하여 **이벤트 뷰어** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9dad0-125">On the **File** menu, click **Exit** to close the **Event Viewer** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dad0-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9dad0-126">See Also</span></span>  
 <span data-ttu-id="9dad0-127">[Integration Services 서비스 관리](../../2014/integration-services/manage-the-integration-services-service.md) </span><span class="sxs-lookup"><span data-stu-id="9dad0-127">[Manage the Integration Services Service](../../2014/integration-services/manage-the-integration-services-service.md) </span></span>  
 [<span data-ttu-id="9dad0-128">데이터 흐름 성능 카운터에 대한 로그 추가</span><span class="sxs-lookup"><span data-stu-id="9dad0-128">Add a Log for Data Flow Performance Counters</span></span>](performance/performance-counters.md)  
  
  
