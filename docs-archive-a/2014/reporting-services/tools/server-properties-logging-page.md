---
title: 서버 속성(로깅 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a04c27fd790a1ad5c4ba453b43af5983a6440e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652009"
---
# <a name="server-properties-logging-page"></a><span data-ttu-id="62f6d-102">서버 속성(로깅 페이지)</span><span class="sxs-lookup"><span data-stu-id="62f6d-102">Server Properties (Logging Page)</span></span>
  <span data-ttu-id="62f6d-103">이 페이지를 사용하여 보고서 서버에서 수집한 보고서 실행 데이터에 대한 제한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-103">Use this page to set limits on the report execution data that is collected by a report server.</span></span> <span data-ttu-id="62f6d-104">실행 데이터는 보고서 서버 데이터베이스에 내부적으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-104">Execution data is stored internally in the report server database.</span></span> <span data-ttu-id="62f6d-105">기본 모드 또는 SharePoint 통합 모드로 실행되는 보고서 서버에 대한 보고서 작업을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-105">You can track report activity for report server that runs in native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="62f6d-106">보고서 서버가 스케일 아웃 배포에 포함되는 경우 보고서 실행 로그는 단일 로그 파일에 전체 배포에 대한 모든 보고서 작업 기록을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-106">If the report server is part of a scale-out deployment, the report execution log maintains a record of all report activity for the entire deployment in a single log file.</span></span>  
  
 <span data-ttu-id="62f6d-107">이 페이지를 열려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 열고 보고서 서버에 연결한 다음 보고서 서버 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-107">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="62f6d-108">**로깅** 을 클릭하여 이 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-108">Click **Logging** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="62f6d-109">옵션</span><span class="sxs-lookup"><span data-stu-id="62f6d-109">Options</span></span>  
 <span data-ttu-id="62f6d-110">**보고서 실행 로깅 사용**</span><span class="sxs-lookup"><span data-stu-id="62f6d-110">**Enable report execution logging**</span></span>  
 <span data-ttu-id="62f6d-111">서버의 보고서 작업에 대한 정보를 작성하고 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-111">Click to create and store information about report activity on the server.</span></span> <span data-ttu-id="62f6d-112">이 옵션을 설정하면 보고서 서버는 사용된 보고서, 보고서 처리 빈도, 수행된 보고서 작업의 유형, 출력 형식 및 보고서를 실행한 사용자를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-112">If this option is enabled, the report server will track which reports are used, the frequency of report processing, the type of report operation that was performed, the output format, and who ran the report.</span></span> <span data-ttu-id="62f6d-113">로그에 캡처되는 추가 데이터 요소에 대 한 자세한 내용은 [보고서 서버 실행 로그 및 ExecutionLog3 뷰](../report-server/report-server-executionlog-and-the-executionlog3-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="62f6d-113">For more information about additional data points that are captured in the log, see [Report Server Execution Log and the ExecutionLog3 View](../report-server/report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
 <span data-ttu-id="62f6d-114">**다음 일 수보다 오래된 로그 항목 제거**</span><span class="sxs-lookup"><span data-stu-id="62f6d-114">**Remove log entries older than this number of days**</span></span>  
 <span data-ttu-id="62f6d-115">보고서 실행 로그에서 로그 항목을 지우기 전에 경과해야 하는 일 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-115">Specify the number of days after which log entries will be trimmed from the report execution log.</span></span> <span data-ttu-id="62f6d-116">기본값은 60일입니다.</span><span class="sxs-lookup"><span data-stu-id="62f6d-116">The default value is 60 days.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f6d-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62f6d-117">See Also</span></span>  
 <span data-ttu-id="62f6d-118">[보고서 서버 속성 &#40;Management Studio&#41;설정](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="62f6d-118">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="62f6d-119">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="62f6d-119">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="62f6d-120">[Reporting Services 로그 파일 및 소스](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="62f6d-120">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 <span data-ttu-id="62f6d-121">[Management Studio F1 도움말의 보고서 서버](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="62f6d-121">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="62f6d-122">보고서 서버 실행 로그 및 ExecutionLog3 뷰</span><span class="sxs-lookup"><span data-stu-id="62f6d-122">Report Server Execution Log and the ExecutionLog3 View</span></span>](../report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
