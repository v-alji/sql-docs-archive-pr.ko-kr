---
title: 작업 속성 대화 상자 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.action.f1
- "10413"
- "10504"
- sql12.rtp.rptdesigner.calculatedseriesproperties.action.f1
- sql12.rtp.rptdesigner.pictureproperties.action.f1
- sql12.rtp.rptdesigner.actionproperties.f1
- sql12.rtp.rptdesigner.charttitleproperties.action.f1
- "10133"
- "10052"
- "10147"
- sql12.rtp.rptdesigner.chartproperties.action.f1
- "10122"
- sql12.rtp.rptdesigner.serieslabelproperties.action.f1
- sql12.rtp.rptdesigner.textboxproperties.action.f1
- "10162"
- "10168"
- sql12.rtp.rptdesigner.textproperties.action.f1
- sql12.rtp.rptdesigner.placeholderproperties.action.f1
- "10250"
- "10129"
- "10244"
- sql12.rtp.rptdesigner.seriesproperties.action.f1
ms.assetid: 2c5d915b-4f97-42cf-b8f1-49ca3ff3d0f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77b51af0763010676b95fcedb433ab963fc7fcdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652658"
---
# <a name="action-properties-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="ead65-102">동작 속성 대화 상자(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ead65-102">Action Properties Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ead65-103">**동작** 대화 상자를 사용하여 링크를 지원하는 차트, 계기 및 지도 요소에 대한 하이퍼링크 옵션을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-103">The **Action** dialog box can be used to enable hyperlink options for a chart, gauge, and map elements that support links.</span></span> <span data-ttu-id="ead65-104">사용자가 보고서를 클릭하여 URL로 이동하거나, 동일한 보고서 서버 또는 보고서 서버와 통합된 SharePoint 사이트에 있는 다른 보고서로 이동하거나, 동일한 보고서 내의 다른 위치로 이동할 수 있는 동작을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-104">Define an action so that a user can click on the report and link to a URL, to a different report on the same report server or on a SharePoint site that is integrated with a report server, or to a different location in the same report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ead65-105">옵션</span><span class="sxs-lookup"><span data-stu-id="ead65-105">Options</span></span>  
 <span data-ttu-id="ead65-106">**동작으로 사용:**</span><span class="sxs-lookup"><span data-stu-id="ead65-106">**Enable as an action**</span></span>  
 <span data-ttu-id="ead65-107">사용자가 항목을 클릭할 때 수행할 동작을 나타내려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-107">Select an option to indicate the action to perform when the user clicks the item.</span></span>  
  
 <span data-ttu-id="ead65-108">**없음**</span><span class="sxs-lookup"><span data-stu-id="ead65-108">**None**</span></span>  
 <span data-ttu-id="ead65-109">항목을 클릭했을 때 아무런 동작도 수행하지 않도록 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-109">Choose this option to indicate that the item has no action.</span></span>  
  
 <span data-ttu-id="ead65-110">**보고서로 이동**</span><span class="sxs-lookup"><span data-stu-id="ead65-110">**Go to report**</span></span>  
 <span data-ttu-id="ead65-111">보고서 서버에 있는 드릴스루 보고서에 대한 링크를 만들려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-111">Choose this option to create a link to a drillthrough report that is located on a report server.</span></span> <span data-ttu-id="ead65-112">**보고서로 이동**을 선택하면 다음 옵션이 추가로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-112">The following additional options appear when you select **Go to report**.</span></span>  
  
 <span data-ttu-id="ead65-113">**보고서 지정**</span><span class="sxs-lookup"><span data-stu-id="ead65-113">**Specify a report**</span></span>  
 <span data-ttu-id="ead65-114">드릴스루 보고서로 사용할 보고서 이름을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-114">Type or select the name of the report that you want to use as a drillthrough report.</span></span> <span data-ttu-id="ead65-115">드릴스루 보고서는 이 보고서와 동일한 보고서 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-115">Drillthrough reports must be on the same report server as this report.</span></span>  
  
 <span data-ttu-id="ead65-116">기본 모드로 구성된 보고서 서버에 게시된 보고서의 경우 파일 이름 확장명 없이 전체 경로나 상대 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-116">For a report published to a report server configured for native mode, use a full or relative path without the file name extension.</span></span> <span data-ttu-id="ead65-117">보고서가 현재 보고서와 같은 폴더에 있으면 보고서 이름만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-117">If the report is in the same folder as the current report, use the name of the report only.</span></span> <span data-ttu-id="ead65-118">보고서가 동일한 보고서 서버의 다른 폴더에 있으면 상대 경로 또는 전체 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-118">If the report is in a different folder on the same report server, use a relative path or a full path.</span></span> <span data-ttu-id="ead65-119">상대 경로는 현재 폴더에서 시작하여 폴더 계층의 위로 이동합니다(예: ../Folder2/Report1).</span><span class="sxs-lookup"><span data-stu-id="ead65-119">A relative path starts from the current folder and moves up the folder hierarchy, for example, ../Folder2/Report1.</span></span> <span data-ttu-id="ead65-120">전체 경로는 홈 폴더인 /에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-120">A full path starts from /, the Home folder.</span></span> <span data-ttu-id="ead65-121">예를 들면 /Reports/Report1과 같은 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-121">For example, /Reports/Report1.</span></span>  
  
 <span data-ttu-id="ead65-122">SharePoint 통합 모드로 구성된 보고서 서버에 게시된 보고서의 경우 파일 이름 확장명(.rdl)을 포함하여 정규화된 URL을 사용합니다(예:</span><span class="sxs-lookup"><span data-stu-id="ead65-122">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL including the file name extension (.rdl).</span></span> <span data-ttu-id="ead65-123">예: http:// *\<SharePointservername>/\<site>* /documents/report1.rdl).</span><span class="sxs-lookup"><span data-stu-id="ead65-123">For example, http://*\<SharePointservername>/\<site>*/Documents/Report1.rdl.</span></span> <span data-ttu-id="ead65-124">상대 경로는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-124">Relative paths are not supported.</span></span>  
  
 <span data-ttu-id="ead65-125">자세한 내용은 msdn.microsoft.com의 [보고서 작성기 설명서](https://go.microsoft.com/fwlink/?LinkId=154494)에서 [외부 항목에 대한 경로 지정&#40;보고서 작성기 및 SSRS&#41;](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ead65-125">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="ead65-126">**이러한 매개 변수를 사용하여 보고서 실행**</span><span class="sxs-lookup"><span data-stu-id="ead65-126">**Use these parameters to run the report**</span></span>  
 <span data-ttu-id="ead65-127">드릴스루 보고서에 전달할 매개 변수 목록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-127">Add a list of parameters to pass to the drillthrough report.</span></span> <span data-ttu-id="ead65-128">매개 변수 이름은 대상 보고서에 대해 정의된 매개 변수와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-128">The parameter names must match the parameters defined for the target report.</span></span> <span data-ttu-id="ead65-129">**추가** 단추와 **삭제** 단추를 사용하여 매개 변수를 추가 및 제거하고 위쪽 화살표와 아래쪽 화살표를 사용하여 매개 변수 목록의 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-129">Use the **Add** and **Delete** buttons to add and remove parameters and use the up and down arrows to order the list of parameters.</span></span>  
  
 <span data-ttu-id="ead65-130">**추가**</span><span class="sxs-lookup"><span data-stu-id="ead65-130">**Add**</span></span>  
 <span data-ttu-id="ead65-131">드릴스루 보고서에 전달할 새 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-131">Add a new parameter to pass to the drillthrough report.</span></span>  
  
 <span data-ttu-id="ead65-132">**삭제**</span><span class="sxs-lookup"><span data-stu-id="ead65-132">**Delete**</span></span>  
 <span data-ttu-id="ead65-133">드릴스루 보고서의 매개 변수를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-133">Delete a parameter for the drillthrough report.</span></span>  
  
 <span data-ttu-id="ead65-134">**위쪽 화살표**</span><span class="sxs-lookup"><span data-stu-id="ead65-134">**Up arrow**</span></span>  
 <span data-ttu-id="ead65-135">매개 변수를 목록에서 위로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-135">Move the parameter up in the list.</span></span>  
  
 <span data-ttu-id="ead65-136">**아래쪽 화살표**</span><span class="sxs-lookup"><span data-stu-id="ead65-136">**Down arrow**</span></span>  
 <span data-ttu-id="ead65-137">매개 변수를 목록에서 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-137">Move the parameter down in the list.</span></span>  
  
 <span data-ttu-id="ead65-138">**이름**</span><span class="sxs-lookup"><span data-stu-id="ead65-138">**Name**</span></span>  
 <span data-ttu-id="ead65-139">드릴스루 보고서에 정의된 매개 변수의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-139">Type text that is the name of a parameter defined in the drillthrough report.</span></span>  
  
 <span data-ttu-id="ead65-140">**값**</span><span class="sxs-lookup"><span data-stu-id="ead65-140">**Value**</span></span>  
 <span data-ttu-id="ead65-141">드릴스루 보고서의 명명된 매개 변수에 전달할 값을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-141">Type or select a value to pass for the named parameter in the drillthrough report.</span></span> <span data-ttu-id="ead65-142">식을 편집 하려면 **식** 단추 (*fx*)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-142">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="ead65-143">**생략**</span><span class="sxs-lookup"><span data-stu-id="ead65-143">**Omit**</span></span>  
 <span data-ttu-id="ead65-144">매개 변수가 실행되지 않도록 하려면 이를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-144">Select to prevent the parameter from running.</span></span> <span data-ttu-id="ead65-145">기본적으로 이 확인란은 선택 취소하여 비활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-145">By default, this check box is cleared and not active.</span></span> <span data-ttu-id="ead65-146">확인란을 선택하려면 **식** 단추(*fx*)를 클릭하고 **True** 을 입력하거나 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-146">To select the check box, click the **Expression** (*fx*) button and either type **True** or create an expression.</span></span> <span data-ttu-id="ead65-147">**식** 대화 상자에서 **확인** 을 클릭하면 확인란이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-147">The check box is selected when you click **OK** in the **Expression** dialog box.</span></span>  
  
 <span data-ttu-id="ead65-148">**책갈피로 이동**</span><span class="sxs-lookup"><span data-stu-id="ead65-148">**Go to bookmark**</span></span>  
 <span data-ttu-id="ead65-149">현재 보고서에서 책갈피 링크를 정의하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-149">Choose this option to define a link to a bookmark in the current report.</span></span> <span data-ttu-id="ead65-150">**책갈피로 이동**을 선택하면 다음 옵션이 추가로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-150">The following additional option appears when you select **Go to bookmark**.</span></span>  
  
 <span data-ttu-id="ead65-151">**책갈피 선택**</span><span class="sxs-lookup"><span data-stu-id="ead65-151">**Select bookmark**</span></span>  
 <span data-ttu-id="ead65-152">사용자가 링크를 클릭할 때 이동할 보고서의 책갈피 ID를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-152">Type or select the bookmark ID for the report to jump to when the user clicks the link.</span></span> <span data-ttu-id="ead65-153">식을 변경하려면 식 단추(**fx**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-153">Click the Expression (**fx**) button to change the expression.</span></span> <span data-ttu-id="ead65-154">책갈피 ID는 정적 ID이거나 책갈피 ID를 반환하는 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-154">The bookmark ID can be either a static ID or an expression that evaluates to a bookmark ID.</span></span> <span data-ttu-id="ead65-155">식은 책갈피 ID가 들어 있는 필드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-155">The expression can include a field that contains a bookmark ID.</span></span>  
  
 <span data-ttu-id="ead65-156">책갈피에 연결하려면 먼저 보고서 항목의 책갈피 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-156">To link to a bookmark, you must first set the Bookmark property of a report item.</span></span> <span data-ttu-id="ead65-157">책갈피 속성을 설정하려면 보고서 항목을 선택하고 속성 창에서 SalesChart 또는 5TopSales와 같이 책갈피 ID에 대한 값이나 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-157">To set the Bookmark property, select a report item, and in the Properties pane, type a value or expression for the bookmark ID; for example, SalesChart or 5TopSales.</span></span>  
  
 <span data-ttu-id="ead65-158">**URL로 이동**</span><span class="sxs-lookup"><span data-stu-id="ead65-158">**Go to URL**</span></span>  
 <span data-ttu-id="ead65-159">웹 페이지에 대한 링크를 정의하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-159">Choose this option to define a link to a Web page.</span></span> <span data-ttu-id="ead65-160">웹 페이지의 URL 또는 이를 반환하는 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-160">Type or select the URL of a Web page or an expression that evaluates to the URL of a Web page.</span></span> <span data-ttu-id="ead65-161">식을 변경하려면 **식** 단추(*fx*)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-161">Click the **Expression** (*fx*) button to change the expression.</span></span> <span data-ttu-id="ead65-162">식은 URL이 들어 있는 필드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-162">This expression can include a field that contains a URL.</span></span> <span data-ttu-id="ead65-163">**URL로 이동**을 선택하면 다음 옵션이 추가로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-163">The following additional option appears when you select **Go to URL**.</span></span>  
  
 <span data-ttu-id="ead65-164">**URL 선택**</span><span class="sxs-lookup"><span data-stu-id="ead65-164">**Select URL**</span></span>  
 <span data-ttu-id="ead65-165">항목의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-165">Type or enter the URL of the item.</span></span> <span data-ttu-id="ead65-166">기본 모드로 구성된 보고서 서버에 게시된 항목의 경우 전체 경로나 상대 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-166">For an item published to a report server configured for native mode, use a full or relative path.</span></span> <span data-ttu-id="ead65-167">예를 들어 http:// *\<servername>* /images/image1.jpg 합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-167">For example, http://*\<servername>*/images/image1.jpg.</span></span> <span data-ttu-id="ead65-168">SharePoint 통합 모드로 구성 된 보고서 서버에 게시 된 항목의 경우 정규화 된 URL (예: http:// *\<SharePointservername>/\<site>* /Documents/images/image1.jpg)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ead65-168">For an item published to a report server configured in SharePoint integrated mode, use a fully qualified URL (for example, http://*\<SharePointservername>/\<site>*/Documents/images/image1.jpg).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead65-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ead65-169">See Also</span></span>  
 <span data-ttu-id="ead65-170">[차트 &#40;보고서 작성기 및 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ead65-170">[Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ead65-171">[대화 상자, 창 및 마법사에 대 한 보고서 작성기 도움말](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="ead65-171">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="ead65-172">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="ead65-172">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="ead65-173">[보고서 작성기 및 SSRS &#40;하위 보고서 및 매개 변수를 추가&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ead65-173">[Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ead65-174">대화형 정렬, 문서 구조 및 링크&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ead65-174">Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;</span></span>](report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
  
