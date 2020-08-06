---
title: 보고서 미리 보기
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: fb068937efff71667d7f73c8e7ecd4d9ebfa576b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648282"
---
# <a name="preview-reports-in-sql-server-reporting-services-ssrs"></a><span data-ttu-id="39cbd-102">SSRS(SQL Server Reporting Services)의 보고서 미리 보기</span><span class="sxs-lookup"><span data-stu-id="39cbd-102">Preview Reports in SQL Server Reporting Services (SSRS)</span></span>

  <span data-ttu-id="39cbd-103">보고서를 디자인할 때 프로덕션 환경에 게시하기 전에 보고서를 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-103">When you design a report, you may want to view it before publishing it to a production environment.</span></span> <span data-ttu-id="39cbd-104">이 작업은 보고서 디자이너에서 미리 보기 모드로 전환하거나, 보고서 디자이너에서 미리 보기 창을 사용하거나, 테스트 환경의 보고서 서버에 보고서를 게시하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-104">You can do this in several ways: by switching to Preview mode in Report Designer, by using the preview window in Report Designer, and by publishing the report to a report server in a test environment.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="39cbd-105">보고서를 미리 보면 보고서의 데이터가 로컬 컴퓨터의 파일에 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-105">When you preview a report, the data for the report is cached to a file on the local computer.</span></span> <span data-ttu-id="39cbd-106">동일한 쿼리, 매개 변수 및 자격 증명을 사용하여 동일한 보고서를 다시 미리 보면 보고서 디자이너는 쿼리를 다시 실행하지 않고 캐시된 복사본을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-106">When you preview the same report again using the same query, parameters, and credentials, Report Designer retrieves the cached copy rather than rerunning the query.</span></span> <span data-ttu-id="39cbd-107">데이터 파일은 *\<reportname>* 보고서 정의 파일과 같은 디렉터리에 .rdl 데이터로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-107">The data file is saved as *\<reportname>*.rdl.data in the same directory as the report definition file.</span></span> <span data-ttu-id="39cbd-108">이 파일은 보고서 디자이너를 닫아도 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-108">The file is not deleted when you close Report Designer.</span></span>  
  
## <a name="preview-mode"></a><span data-ttu-id="39cbd-109">미리 보기 모드</span><span class="sxs-lookup"><span data-stu-id="39cbd-109">Preview Mode</span></span>

 <span data-ttu-id="39cbd-110">**미리 보기**를 클릭 하 여 보고서 디자이너 보고서를 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-110">You can preview a report in Report Designer by clicking **Preview**.</span></span> <span data-ttu-id="39cbd-111">이때 보고서는 로컬로 실행되며 보고서 서버에 제공되는 동일한 보고서 처리 및 렌더링 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-111">This runs the report locally, using the same report processing and rendering functionality that is provided with the report server.</span></span> <span data-ttu-id="39cbd-112">표시되는 보고서는 대화형 이미지이므로 매개 변수를 선택하고, 링크를 클릭하고, 문서 구조를 보고, 보고서의 숨겨진 영역을 확대 및 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-112">The report that is displayed is an interactive image; you can select parameters, click links, view the document map, and expand and collapse hidden areas of the report.</span></span> <span data-ttu-id="39cbd-113">또한 설치된 렌더링 형식으로 보고서를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-113">You can also export the report to any of the installed rendering formats.</span></span>  
  
## <a name="standalone-preview"></a><span data-ttu-id="39cbd-114">독립 실행형 미리 보기</span><span class="sxs-lookup"><span data-stu-id="39cbd-114">Standalone Preview</span></span>

 <span data-ttu-id="39cbd-115">디버그 구성 등에서 보고서 프로젝트를 실행하여 사용자가 작성하는 사용자 지정 어셈블리를 디버깅하여 보고서를 미리 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-115">Another way to preview a report is to run the report project in a debug configuration, for example, to debug custom assemblies that you write.</span></span> <span data-ttu-id="39cbd-116">프로젝트를 실행하는 방법에는 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-116">There are three ways to run a project:</span></span>  
  
- <span data-ttu-id="39cbd-117">**디버그** 메뉴에서 **시작** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-117">By clicking **Start** on the **Debug** menu.</span></span>  
  
- <span data-ttu-id="39cbd-118">표준 도구 모음에서 **시작** 단추를 클릭 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-118">By clicking the **Start** button on the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] standard toolbar.</span></span>  
  
- <span data-ttu-id="39cbd-119">F5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-119">By pressing F5.</span></span>  
  
 <span data-ttu-id="39cbd-120">보고서를 작성은 하지만 배포하지 않는 프로젝트 구성을 사용하면 현재 구성의 `StartItem` 속성에 지정된 보고서는 별도의 미리 보기 창에 열립니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-120">If you use a project configuration that builds the report but does not deploy it, the report that is specified in the `StartItem` property of the current configuration opens in a separate preview window.</span></span> <span data-ttu-id="39cbd-121">미리 보기 창에서 보고서는 미리 보기 모드와 동일한 방식으로 표시되고 동일한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-121">The preview window displays the report in the same way and has the same functionality as Preview mode.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="39cbd-122">보고서를 디버깅하려면 먼저 시작 항목을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-122">Before debugging a report, you must set a start item.</span></span> <span data-ttu-id="39cbd-123">시작 항목을 설정 하려면 솔루션 탐색기에서 보고서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 클릭 한 다음에서 `StartItem` 표시할 보고서의 이름을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-123">To set a start item, in Solution Explorer, right-click the report project, click **Properties**, and then in `StartItem`, select the name of the report to display.</span></span>  
  
 <span data-ttu-id="39cbd-124">프로젝트의 시작 항목이 아닌 특정 보고서를 미리 보려면 보고서를 작성하지만 배포하지 않는 구성(예: DebugLocal 구성)을 선택하고 보고서를 마우스 오른쪽 단추로 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-124">If you wish to preview a particular report that is not the start item for the project, select a configuration that builds the report but does not deploy it (for example, the DebugLocal configuration), right-click the report, and then click **Run**.</span></span> <span data-ttu-id="39cbd-125">보고서를 배포하지 않는 구성을 선택해야 합니다. 그렇지 않으면 보고서는 로컬 컴퓨터의 미리 보기 창에 표시되지 않고 보고서 서버에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-125">You must choose a configuration that does not deploy the report; otherwise, the report will be published to the report server instead of displayed locally in a preview window.</span></span>  
  
## <a name="print-preview"></a><span data-ttu-id="39cbd-126">인쇄 미리 보기</span><span class="sxs-lookup"><span data-stu-id="39cbd-126">Print Preview</span></span>

 <span data-ttu-id="39cbd-127">미리 보기 모드 또는 미리 보기 창에서 보고서를 처음으로 보면 해당 보고서가 HTML 렌더링 확장 프로그램에서 생성된 보고서와 유사하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-127">When you first view a report on in Preview mode or in the preview window, the view of the report resembles a report produced by the HTML rendering extension.</span></span> <span data-ttu-id="39cbd-128">미리 보기는 HTML 형식은 아니지만 보고서의 레이아웃 및 페이지 매기기는 HTML 출력과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-128">The preview is not HTML, but the layout and pagination of the report is similar to HTML output.</span></span>  
  
 <span data-ttu-id="39cbd-129">인쇄 미리 보기 모드로 전환하여 인쇄될 보고서를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-129">You can change the view to represent a printed report by switching to print preview mode.</span></span> <span data-ttu-id="39cbd-130">미리 보기 도구 모음에서 **인쇄 미리 보기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-130">Click the **Print Preview** button on the preview toolbar.</span></span> <span data-ttu-id="39cbd-131">보고서는 실제 인쇄된 페이지처럼 표시되며</span><span class="sxs-lookup"><span data-stu-id="39cbd-131">The report will display as though it were on a physical page.</span></span> <span data-ttu-id="39cbd-132">이미지 및 PDF 렌더링 확장 프로그램에서 생성된 출력과도 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-132">This view resembles the output produced by the Image and PDF rendering extensions.</span></span> <span data-ttu-id="39cbd-133">인쇄 미리 보기는 이미지나 PDF 파일 형식은 아니지만 보고서의 레이아웃 및 페이지 매기기는 해당 형식의 출력과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-133">Print preview is not an image or PDF file, but the layout and pagination of the report is similar the output in those formats.</span></span>  
  
## <a name="publish-to-a-test-server"></a><span data-ttu-id="39cbd-134">테스트 서버에 게시</span><span class="sxs-lookup"><span data-stu-id="39cbd-134">Publish to a Test Server</span></span>

 <span data-ttu-id="39cbd-135">테스트 서버에 게시하여 보고서를 테스트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-135">You can also test reports by publishing them to a test server.</span></span> <span data-ttu-id="39cbd-136">테스트 서버와 프로덕션 서버에 보고서를 게시하는 방법은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="39cbd-136">Publishing a report to a test server is the same as publishing to a production server.</span></span> <span data-ttu-id="39cbd-137">보고서 게시에 대한 자세한 내용은 [보고서 서버에 보고서 게시](publishing-reports-to-a-report-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39cbd-137">For information about publishing a report, see [Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="39cbd-138">다음 단계</span><span class="sxs-lookup"><span data-stu-id="39cbd-138">Next steps</span></span>

 - [<span data-ttu-id="39cbd-139">보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="39cbd-139">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-reports-report-builder-and-ssrs.md)
 - [<span data-ttu-id="39cbd-140">보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="39cbd-140">Print a Report &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-a-report-report-builder-and-ssrs.md)
 - [<span data-ttu-id="39cbd-141">보고서 게시</span><span class="sxs-lookup"><span data-stu-id="39cbd-141">Publish Reports</span></span>](../publish-reports.md)
 - [<span data-ttu-id="39cbd-142">보고서에서 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="39cbd-142">Using Custom Assemblies with Reports</span></span>](../custom-assemblies/using-custom-assemblies-with-reports.md)