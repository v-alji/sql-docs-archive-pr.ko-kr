---
title: 이벤트 로그 창에서 로그 항목 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], viewing
- Integration Services packages, logs
- packages [Integration Services], logs
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16b6f11758d7de2c833731cd007426000a01d8ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728435"
---
# <a name="view-log-entries-in-the-log-events-window"></a><span data-ttu-id="d80ee-102">이벤트 로그 창에서 로그 항목 보기</span><span class="sxs-lookup"><span data-stu-id="d80ee-102">View Log Entries in the Log Events Window</span></span>
  <span data-ttu-id="d80ee-103">이 절차에서는 패키지를 실행하고 패키지에서 작성한 로그 항목을 보는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-103">This procedure describes how to run a package and view the log entries it writes.</span></span> <span data-ttu-id="d80ee-104">로그 항목은 실시간으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-104">You can view the log entries in real time.</span></span> <span data-ttu-id="d80ee-105">**이벤트 로그** 창에 기록된 로그 항목을 상세히 분석할 수 있게 복사하여 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-105">The log entries that are written to the **Log Events** window can also be copied and saved for further analysis.</span></span>  
  
 <span data-ttu-id="d80ee-106">항목을 **이벤트 로그** 창에 쓰기 위해 로그 항목을 로그에 쓰지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-106">It is not necessary to write the log entries to a log to write the entries to the **Log Events** window.</span></span>  
  
### <a name="to-view-log-entries"></a><span data-ttu-id="d80ee-107">로그 항목을 보려면</span><span class="sxs-lookup"><span data-stu-id="d80ee-107">To view log entries</span></span>  
  
1.  <span data-ttu-id="d80ee-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="d80ee-109">**SSIS** 메뉴에서 **이벤트 로그**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-109">On the **SSIS** menu, click **Log Events**.</span></span> <span data-ttu-id="d80ee-110">필요한 경우 View.LogEvents 명령을 **옵션** 대화 상자의 **키보드** 페이지에서 선택한 키 조합에 매핑하여 **이벤트 로그** 창을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-110">You can optionally display the **Log Events** window by mapping the View.LogEvents command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
3.  <span data-ttu-id="d80ee-111">**디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-111">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="d80ee-112">로깅하도록 설정한 이벤트 및 사용자 지정 메시지가 런타임에 발생하면 각 이벤트나 메시지의 로그 항목이 **이벤트 로그** 창에 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-112">As the runtime encounters the events and custom messages that are enabled for logging, log entries for each event or message are written to the **Log Events** window.</span></span>  
  
4.  <span data-ttu-id="d80ee-113">**디버그** 메뉴에서 **디버깅 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-113">On the **Debug** menu, click **Stop Debugging**.</span></span>  
  
     <span data-ttu-id="d80ee-114">패키지를 반환하거나, 다른 패키지를 실행하거나, **를 닫을 때까지 로그 항목은** 이벤트 로그 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]창에서 사용할 수 있는 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-114">The log entries remain available in the **Log Events** window until you rerun the package, run a different package, or close [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
5.  <span data-ttu-id="d80ee-115">**이벤트 로그** 창에서 로그 항목을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-115">View the log entries in the **Log Events** window.</span></span>  
  
6.  <span data-ttu-id="d80ee-116">필요에 따라 복사할 로그 항목을 클릭하고 마우스 오른쪽 단추를 클릭한 다음 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-116">Optionally, click the log entries to copy, right-click, and then click **Copy**.</span></span>  
  
7.  <span data-ttu-id="d80ee-117">필요에 따라 로그 항목을 두 번 클릭하고 **로그 항목** 대화 상자에서 단일 로그 항목에 대한 세부 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-117">Optionally, double-click a log entry, and in the **Log Entry** dialog box, view the details for a single log entry.</span></span>  
  
8.  <span data-ttu-id="d80ee-118">**로그 항목** 대화 상자에서 위쪽 및 아래쪽 화살표를 클릭하여 이전 또는 다음 로그 항목을 표시하고 복사 아이콘을 클릭하여 로그 항목을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-118">In the **Log Entry** dialog box, click the up and down arrows to display the previous or next log entry, and click the copy icon to copy the log entry.</span></span>  
  
9. <span data-ttu-id="d80ee-119">텍스트 편집기를 열고 로그 항목을 텍스트 파일에 붙여넣은 다음 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d80ee-119">Open a text editor, paste, and then save the log entry to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d80ee-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d80ee-120">See Also</span></span>  
 [<span data-ttu-id="d80ee-121">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="d80ee-121">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
