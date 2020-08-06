---
title: 문서 구조 만들기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c200a97b-67f2-499f-8374-3ed1ebe3f33c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a9dad0f8e6ee1d9b9ada44fda0eec5908f27cfcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649437"
---
# <a name="create-a-document-map-report-builder-and-ssrs"></a><span data-ttu-id="2d044-102">문서 구조 만들기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2d044-102">Create a Document Map (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2d044-103">문서 구조는 렌더링된 보고서의 보고서 항목에 대한 탐색 링크 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-103">A document map provides a set of navigational links to report items in a rendered report.</span></span> <span data-ttu-id="2d044-104">문서 구조가 포함된 보고서를 열면 보고서 옆에 별도의 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-104">When you view a report that includes a document map, a separate side pane appears next to the report.</span></span> <span data-ttu-id="2d044-105">사용자는 문서 구조의 링크를 클릭하여 해당 항목을 표시하는 보고서 페이지로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-105">A user can click links in the document map to jump to the report page that displays that item.</span></span> <span data-ttu-id="2d044-106">보고서 섹션 및 그룹은 링크 계층에 정렬되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-106">Report sections and groups are arranged in a hierarchy of links.</span></span> <span data-ttu-id="2d044-107">이 문서 구조에서 항목을 클릭하면 보고서가 새로 고쳐진 다음 항목에 해당하는 보고서 영역을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-107">Clicking items in the document map refreshes the report and displays the area of the report that corresponds to the item in the document map.</span></span>  
  
 <span data-ttu-id="2d044-108">문서 구조에 링크를 추가하려면 보고서 항목의 `DocumentMapLabel` 속성을 만들 텍스트로 설정하거나 문서 구조에 표시할 텍스트로 계산되는 식으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-108">To add links to the document map, you set the `DocumentMapLabel` property of the report item to text that you create or to an expression that evaluates to the text that you want display in the document map.</span></span> <span data-ttu-id="2d044-109">또한 테이블 또는 행렬 그룹에 대한 고유한 값을 문서 구조에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-109">You can also add the unique values for a table or matrix group to the document map.</span></span> <span data-ttu-id="2d044-110">예를 들어 색을 기반으로 하는 그룹의 경우 각 고유 색은 해당 색에 대한 그룹 인스턴스를 표시하는 보고서 페이지에 대한 링크입니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-110">For example, for a group based on color, each unique color is a link to the report page that displays the group instance for that color.</span></span>  
  
 <span data-ttu-id="2d044-111">또한 문서 구조를 표시하지 않고 보고서를 실행할 수 있도록 문서 구조 표시를 재정의하는 보고서에 대한 URL을 만든 다음 보고서 뷰어 도구 모음의 **문서 구조 표시/숨기기** 단추를 클릭하여 표시를 설정/해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-111">You can also create a URL to a report that overrides the display of the document map, so that you can run the report without displaying the document map, and then click the **Show/Hide Document Map** button on the report viewer toolbar to toggle the display.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="document-maps-and-rendering-extensions"></a><a name="DocMapRenderExtensions"></a> <span data-ttu-id="2d044-112">문서 구조 및 렌더링 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="2d044-112">Document Maps and Rendering Extensions</span></span>  
 <span data-ttu-id="2d044-113">문서 구조는 미리 보기 및 보고서 뷰어와 같은 HTML 렌더링 확장 프로그램용입니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-113">The document map is intended for use in the HTML rendering extension-for example, in Preview and the Report Viewer.</span></span> <span data-ttu-id="2d044-114">다른 렌더링 확장 프로그램에서는 다음과 같은 방법으로 문서 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-114">Other rendering extensions have different ways of articulating a document map:</span></span>  
  
-   <span data-ttu-id="2d044-115">PDF는 문서 구조를 책갈피 창으로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-115">PDF renders a document map as the Bookmarks pane.</span></span>  
  
-   <span data-ttu-id="2d044-116">Excel은 문서 구조를 링크 계층이 포함된 명명된 워크시트로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-116">Excel renders a document map as a named worksheet that includes a hierarchy of links.</span></span> <span data-ttu-id="2d044-117">보고서 섹션은 문서 구조와 함께 동일한 통합 문서에 포함되는 별도의 워크시트로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-117">Report sections are rendered in separate worksheets that are included with the document map in the same workbook.</span></span>  
  
-   <span data-ttu-id="2d044-118">Word에는 목차 형식의 문서 구조가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-118">Word includes a document map as the table of contents.</span></span>  
  
-   <span data-ttu-id="2d044-119">Atom, TIFF, XML 및 CSV는 문서 구조를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-119">Atom, TIFF, XML, and CSV ignore document maps.</span></span>  
  
 <span data-ttu-id="2d044-120">자세한 내용은 [여러 보고서 렌더링 확장 프로그램의 대화형 기능&#40;보고서 작성기 및 SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d044-120">For more information, see [Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md).</span></span>  
  
##  <a name="AddRptItemToMap"></a>   
#### <a name="to-add-a-report-item-to-a-document-map"></a><span data-ttu-id="2d044-121">문서 구조에 보고서 항목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2d044-121">To add a report item to a document map</span></span>  
  
1.  <span data-ttu-id="2d044-122">디자인 뷰에서 문서 구조에 추가할 테이블, 행렬 또는 계기와 같은 보고서 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-122">In Design view, select the report item such as a table, matrix, or gauge that you want to add to the document map.</span></span> <span data-ttu-id="2d044-123">보고서 항목 속성이 속성 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-123">The report item properties appear in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2d044-124">테이블릭스 데이터 영역을 선택하려면 아무 셀이나 클릭하여 행 및 열 핸들을 표시한 다음 모퉁이 핸들을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-124">To select a tablix data region, click in any cell to display the row and column handles, and then click the corner handle.</span></span>  
  
2.  <span data-ttu-id="2d044-125">속성 창에서 문서 구조에 표시할 텍스트를 속성에 입력 `DocumentMapLabel` 하거나 레이블로 계산 되는 식을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-125">In the Properties pane, type the text that you want to appear in the document map in the `DocumentMapLabel` property, or enter an expression that evaluates to a label.</span></span> <span data-ttu-id="2d044-126">예를 들어 **Sales Chart**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-126">For example, type **Sales Chart**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2d044-127">속성 창이 표시되지 않는 경우 **보기** 탭의 **표시/숨기기** 그룹에서 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-127">If you do not see the Properties pane, on the **View** tab, in the **Show/Hide** group, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="2d044-128">문서 구조에 표시할 각 보고서 항목에 대해 1단계와 2단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-128">Repeat steps 1 and 2 for every report item that you want to appear in the document map.</span></span>  
  
4.  <span data-ttu-id="2d044-129">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-129">Click **Run**.</span></span> <span data-ttu-id="2d044-130">보고서가 실행되고 문서 구조에 사용자가 만든 레이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-130">The report runs and the document map displays the labels you created.</span></span> <span data-ttu-id="2d044-131">해당 항목이 있는 보고서 페이지로 이동하는 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-131">Click any link to jump to the report page with that item.</span></span>  
  
 
  
##  <a name="AddUniqueValuesToMap"></a>   
#### <a name="to-add-unique-group-values-to-a-document-map"></a><span data-ttu-id="2d044-132">문서 구조에 고유한 그룹 값을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2d044-132">To add unique group values to a document map</span></span>  
  
1.  <span data-ttu-id="2d044-133">디자인 뷰에서 문서 구조에 표시할 그룹을 포함하는 테이블, 행렬 또는 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-133">In Design view, select the table, matrix, or list that contains the group that you want to display in the document map.</span></span> <span data-ttu-id="2d044-134">그룹화 창에 행 및 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-134">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="2d044-135">행 그룹 창에서 그룹을 마우스 오른쪽 단추로 클릭한 다음 **그룹 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-135">In the Row Groups pane, right-click the group, and then click **Edit Group**.</span></span> <span data-ttu-id="2d044-136">**테이블릭스 그룹 속성** 대화 상자의 **일반** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-136">The **General** page of the **Tablix Group Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="2d044-137">**고급**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-137">Click **Advanced**.</span></span>  
  
4.  <span data-ttu-id="2d044-138">**문서 구조** 목록 상자에서 그룹 식과 일치하는 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-138">In the **Document map** list box, type or select an expression that matches the group expression.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="2d044-139">문서 구조에 표시할 각 그룹에 대해 1-4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-139">Repeat steps 1-4 for every group that you want to appear in the document map.</span></span>  
  
7.  <span data-ttu-id="2d044-140">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-140">Click **Run**.</span></span> <span data-ttu-id="2d044-141">보고서가 실행되고 문서 구조에 그룹 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-141">The report runs and the document map displays the group values.</span></span> <span data-ttu-id="2d044-142">해당 항목이 있는 보고서 페이지로 이동하는 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-142">Click any link to jump to the report page with that item.</span></span>  
  
 
  
##  <a name="HideMapWhenViewRpt"></a>   
#### <a name="to-hide-the-document-map-when-you-view-a-report"></a><span data-ttu-id="2d044-143">보고서를 볼 때 문서 구조를 숨기려면</span><span class="sxs-lookup"><span data-stu-id="2d044-143">To hide the document map when you view a report</span></span>  
  
1.  <span data-ttu-id="2d044-144">보고서 관리자에서 문서 구조를 포함하는 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-144">In Report Manager, browse to the report that has the document map.</span></span>  
  
     <span data-ttu-id="2d044-145">예를 들어 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 예제 보고서의 경우 다음 URL에서 Product Catalog라는 보고서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-145">For example, for the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] sample reports, the following URL specifies the report named Product Catalog.</span></span>  
  
    ```  
    http://localhost/Reports/Pages/Report.aspx?ItemPath=%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    ```  
  
2.  <span data-ttu-id="2d044-146">서버의 보고서 경로를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-146">Copy the report path on the server.</span></span> <span data-ttu-id="2d044-147">예에서 보고서 경로는 `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`입니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-147">In the example, the report path is `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`.</span></span>  
  
3.  <span data-ttu-id="2d044-148">다음 3개의 구성 요소를 사용하여 새 URL을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-148">Create a new URL with the following three components:</span></span>  
  
    -   <span data-ttu-id="2d044-149">보고서 서버의 보고서 뷰어: `http://localhost/ReportServer/Pages/ReportViewer.aspx?`</span><span class="sxs-lookup"><span data-stu-id="2d044-149">The report viewer on the report server: `http://localhost/ReportServer/Pages/ReportViewer.aspx?`</span></span>  
  
    -   <span data-ttu-id="2d044-150">1단계에서 복사한 보고서 이름. 예를 들면 다음과 같습니다. `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`</span><span class="sxs-lookup"><span data-stu-id="2d044-150">The name of the report you copied in step 1, for example: `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`</span></span>  
  
    -   <span data-ttu-id="2d044-151">문서 구조를 숨기도록 지정하는 디바이스 정보 매개 변수: `&rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False`</span><span class="sxs-lookup"><span data-stu-id="2d044-151">The device information parameters that specify hiding the document map: `&rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False`</span></span>  
  
     <span data-ttu-id="2d044-152">다음 URL에서는 이러한 3개의 구성 요소가 나열되는 순서대로 추가하여 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-152">The following URL consists of these three components appended in the order they are listed.</span></span>  
  
    ```  
    http://localhost/ReportServer/Pages/ReportViewer.aspx?  
    %2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    &rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False  
    ```  
  
     <span data-ttu-id="2d044-153">이 URL을 사용하려면 해당 URL을 복사하고 모든 줄 바꿈을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-153">To use this URL, copy it and remove all line breaks.</span></span>  
  
4.  <span data-ttu-id="2d044-154">보고서 관리자에 URL을 붙여넣은 다음 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-154">Paste the URL in Report Manager, and then press ENTER.</span></span> <span data-ttu-id="2d044-155">보고서가 실행되고 문서 구조가 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="2d044-155">The report runs, and the document map is hidden.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d044-156">예제 보고서를 다운로드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d044-156">For more information about downloading sample reports, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
>   
>  <span data-ttu-id="2d044-157">자세한 내용은 SQL Server 온라인 설명서의 [Reporting Services 설명서](https://go.microsoft.com/fwlink/?linkid=121312) 에 있는 "URL 액세스"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2d044-157">For more information, see "URL Access" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="2d044-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d044-158">See Also</span></span>  
 [<span data-ttu-id="2d044-159">보고서 관리자에서 보고서 찾기 및 보기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2d044-159">Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)  
  
  
