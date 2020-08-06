---
title: 보고서 인쇄(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b96936c9-c387-41a9-8c19-6eb325769ffd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe029019cdf9739153256db399cfa1426d3ba632
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648827"
---
# <a name="print-a-report-report-builder-and-ssrs"></a><span data-ttu-id="62cb3-102">보고서 인쇄(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="62cb3-102">Print a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="62cb3-103">보고서 서버에 보고서를 저장한 후에는 내보낸 보고서를 보는 데 사용되는 애플리케이션, 보고서 관리자 또는 브라우저에서 보고서를 보고 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-103">After you save a report to a report server, you can view and print the report from a browser, Report Manager, or any application that you use to view an exported report.</span></span> <span data-ttu-id="62cb3-104">보고서를 저장하기 전 미리 볼 때 해당 보고서를 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-104">Before saving a report, you can print it when you preview it.</span></span>  
  
 <span data-ttu-id="62cb3-105">보고서를 인쇄할 때 사용할 용지 크기를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-105">When you print a report, you can specify the size of the paper to use.</span></span> <span data-ttu-id="62cb3-106">용지 크기에 따라 보고서의 페이지 수와 각 페이지에 맞는 보고서 데이터가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-106">The size of the paper determines the number of pages in a report and which report data fits on each page.</span></span> <span data-ttu-id="62cb3-107">용지 크기는 PDF, 이미지 및 인쇄 하드 페이지 나누기 렌더러로 렌더링되는 보고서에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-107">Paper size affects only reports that are rendered with hard page-break renders: PDF, Image, and Print.</span></span> <span data-ttu-id="62cb3-108">용지 크기 설정 작업은 다른 렌더러에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-108">Setting the paper size has no effect on other renderers.</span></span> <span data-ttu-id="62cb3-109">자세한 내용은 [렌더링 동작&#40;보고서 작성기 및 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62cb3-109">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="62cb3-110">보고서 관리자의 보고서 뷰어 도구 모음 또는 보고서 작성기의 미리 보기에서 보고서를 하드 페이지 나누기 렌더러로 내보내거나 인쇄 단추를 클릭하여 보고서의 복사본을 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-110">From the report viewer toolbar in Report Manager or in preview in Report Builder, you can export a report to a hard page-break renderer or click the Print button to print a copy of the report.</span></span> <span data-ttu-id="62cb3-111">용지 크기 또는 다른 페이지 설정 속성을 지정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-111">You might need to set the paper size or other page setup properties.</span></span> <span data-ttu-id="62cb3-112">용지 크기를 비롯한 페이지 설정 속성을 변경하려면 **보고서 속성** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-112">Use the **Report Properties** dialog box to change page setup properties, including paper size.</span></span>  
  
 <span data-ttu-id="62cb3-113">인쇄 페이지 여백은 디자인 모드와 실행 모드에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-113">You can specify print page margins in two different locations: in design mode and in run mode.</span></span>  
  
-   <span data-ttu-id="62cb3-114">**디자인 모드.**</span><span class="sxs-lookup"><span data-stu-id="62cb3-114">**Design mode.**</span></span> <span data-ttu-id="62cb3-115">디자인 모드에서 페이지 여백을 설정하면 보고서를 저장할 때 해당 설정이 보고서 정의에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-115">When you set page margins in design mode, these settings are saved in the report definition when you save the report.</span></span>  
  
-   <span data-ttu-id="62cb3-116">**실행 모드입니다.**</span><span class="sxs-lookup"><span data-stu-id="62cb3-116">**Run mode.**</span></span> <span data-ttu-id="62cb3-117">실행 모드에서 페이지 여백을 설정하면 해당 정보가 보고서 정의에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-117">When you set page margins in run mode, this information is not saved in the report definition.</span></span> <span data-ttu-id="62cb3-118">다음에 보고서를 인쇄할 때는 인쇄 여백을 다시 지정하지 않는 한 보고서 정의에서 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-118">The next time you print the report, you will get the settings from the report definition, unless you indicate your print margins again.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62cb3-119">인쇄 여백은 디자인 모드나 실행 모드에서 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-119">Print margins are not displayed in design or run modes.</span></span> <span data-ttu-id="62cb3-120">보고서의 디자인 화면 영역과 인쇄 영역 간에는 어떠한 관계도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-120">There is no relationship between the design surface area and the print area of your report.</span></span> <span data-ttu-id="62cb3-121">실행 모드에서 인쇄 여백을 확인하려면 리본 메뉴의 **실행** 탭에서 인쇄 레이아웃을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-121">To see print margins, in run mode, click Print Layout on the **Run** tab on the Ribbon.</span></span>  
  
 <span data-ttu-id="62cb3-122">보고서 페이지 매김에 대한 자세한 내용은 [Reporting Services의 페이지 매김&#40;보고서 작성기 및 SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62cb3-122">For more information about report paging, see [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-print-a-report-in-report-builder"></a><span data-ttu-id="62cb3-123">보고서 작성기에서 보고서를 인쇄하려면</span><span class="sxs-lookup"><span data-stu-id="62cb3-123">To print a report in Report Builder</span></span>  
  
1.  <span data-ttu-id="62cb3-124">보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-124">Open a report.</span></span>  
  
2.  <span data-ttu-id="62cb3-125">홈 탭에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-125">On the Home tab, click **Run**.</span></span>  
  
3.  <span data-ttu-id="62cb3-126">(옵션) **인쇄 레이아웃** 을 클릭하여 보고서가 인쇄되었을 때의 모양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-126">(optional) Click **Print Layout** to see how the report will look when it is printed.</span></span>  
  
4.  <span data-ttu-id="62cb3-127">(옵션) **페이지 설정** 을 클릭하여 용지, 방향 및 여백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-127">(optional) Click **Page Setup** to set paper, orientation, and margins.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62cb3-128">이러한 값은 디자인 뷰에서 설정한 보고서 속성의 값을 기본값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-128">The default values for these come from the report properties, which are set in Design view.</span></span> <span data-ttu-id="62cb3-129">**페이지 설정** 대화 상자의 이 부분에서 설정하는 값은 이 세션에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-129">The values you set here in the **Page Setup** dialog box are for this session only.</span></span> <span data-ttu-id="62cb3-130">이 보고서를 닫은 후 다시 열면 기본값으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-130">When you close this report and reopen it, it will have the default values again.</span></span>  
  
5.  <span data-ttu-id="62cb3-131">**인쇄**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-131">Click **Print**.</span></span>  
  
6.  <span data-ttu-id="62cb3-132">**인쇄** 대화 상자에서 프린터를 선택하고 다른 인쇄 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-132">In the **Print** dialog box, select a printer and specify other printing options.</span></span>  
  
### <a name="to-print-a-report-from-a-web-browser-application"></a><span data-ttu-id="62cb3-133">웹 브라우저 애플리케이션에서 보고서를 인쇄하려면</span><span class="sxs-lookup"><span data-stu-id="62cb3-133">To print a report from a Web browser application</span></span>  
  
1.  <span data-ttu-id="62cb3-134">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-134">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="62cb3-135">보고서 관리자에서 인쇄할 보고서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-135">In Report Manager, navigate to the report that you want to print.</span></span> <span data-ttu-id="62cb3-136">보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-136">Open the report.</span></span>  
  
3.  <span data-ttu-id="62cb3-137">보고서 맨 위의 도구 모음에서 **인쇄**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-137">On the toolbar at the top of the report, click **Print**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62cb3-138">HTML 보고서를 처음 인쇄하는 경우에는 보고서 서버에서 인쇄에 사용할 ActiveX 컨트롤을 설치하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-138">The first time you print an HTML report, the report server prompts you to install an ActiveX control used for printing.</span></span> <span data-ttu-id="62cb3-139">인쇄하려면 컨트롤을 설치하고 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-139">You must install and configure the control to print.</span></span>  
  
4.  <span data-ttu-id="62cb3-140">**인쇄** 대화 상자에서 프린터를 선택한 후 **인쇄**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-140">In the **Print** dialog box, select a printer, and then click **Prin**t.</span></span>  
  
### <a name="to-print-a-report-from-other-applications"></a><span data-ttu-id="62cb3-141">다른 애플리케이션에서 보고서를 인쇄하려면</span><span class="sxs-lookup"><span data-stu-id="62cb3-141">To print a report from other applications</span></span>  
  
1.  <span data-ttu-id="62cb3-142">보고서 관리자에서 인쇄할 보고서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-142">In Report Manager, navigate to the report that you want to print.</span></span> <span data-ttu-id="62cb3-143">보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-143">Open the report.</span></span>  
  
2.  <span data-ttu-id="62cb3-144">보고서 맨 위의 도구 모음에서 렌더링 형식을 선택하고 **내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-144">On the toolbar at the top of the report, select a rendering format, and then click **Export**.</span></span> <span data-ttu-id="62cb3-145">렌더링 형식에 맞는 뷰어 애플리케이션에서 보고서가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-145">The report opens in a viewer application that corresponds to the rendering format.</span></span>  
  
     <span data-ttu-id="62cb3-146">예를 들어 PDF를 선택한 경우 Adobe Acrobat Reader에서 보고서가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-146">For example, if you select PDF, the report opens in Adobe Acrobat Reader.</span></span>  
  
3.  <span data-ttu-id="62cb3-147">해당 프로그램의 **파일** 메뉴에서 **인쇄**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-147">On the **File** menu in that program, click **Print**.</span></span>  
  
### <a name="to-change-paper-size"></a><span data-ttu-id="62cb3-148">용지 크기를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="62cb3-148">To change paper size</span></span>  
  
1.  <span data-ttu-id="62cb3-149">보고서 본문 바깥쪽을 마우스 오른쪽 단추로 클릭하고 **보고서 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-149">Right-click outside of the report body and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="62cb3-150">**페이지 설정**의 **용지 크기** 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-150">In **Page Setup**, select a value from the **Paper Size** list.</span></span> <span data-ttu-id="62cb3-151">각 옵션은 **너비** 및 **높이** 속성을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-151">Each option populates the **Width** and **Height** properties.</span></span> <span data-ttu-id="62cb3-152">**너비** 및 **높이** 상자에 숫자 값을 입력하여 사용자 지정 크기를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-152">You can also specify a custom size by typing numeric values in the **Width** and **Height** boxes.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="62cb3-153">크기 값에는 사용자의 로캘 설정을 기반으로 하는 기본 단위가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-153">Size values have a default unit based on the user's locale settings.</span></span> <span data-ttu-id="62cb3-154">다른 단위를 지정하려면 숫자 값 뒤에 cm, mm, pt 또는 pc 등의 물리적 단위 지정자를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-154">To designate a different unit, type a physical unit designator such as cm, mm, pt, or pc after the numeric value.</span></span>  
  
### <a name="to-set-page-margins-in-design-mode"></a><span data-ttu-id="62cb3-155">디자인 모드에서 페이지 여백을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="62cb3-155">To set page margins in design mode</span></span>  
  
-   <span data-ttu-id="62cb3-156">디자인 화면 주변의 파란색 영역을 마우스 오른쪽 단추로 클릭하고 **보고서 속성**을 클릭한 다음 **페이지 설정** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-156">Right-click the blue area around the design surface, click **Report Properties**, and then click the **Page Setup** page.</span></span>  
  
### <a name="to-set-page-margins-in-run-mode"></a><span data-ttu-id="62cb3-157">실행 모드에서 페이지 여백을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="62cb3-157">To set page margins in run mode</span></span>  
  
-   <span data-ttu-id="62cb3-158">**실행** 탭에서 **페이지 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62cb3-158">Click **Page Setup** on the **Run** tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62cb3-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62cb3-159">See Also</span></span>  
 <span data-ttu-id="62cb3-160">[보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;](print-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="62cb3-160">[Print Reports &#40;Report Builder and SSRS&#41;](print-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="62cb3-161">[보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="62cb3-161">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="62cb3-162">[보고서 속성 대화 상자, 페이지 설정&#40;보고서 작성기&#41;](../report-properties-dialog-box-page-setup-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="62cb3-162">[Report Properties Dialog Box, Page Setup &#40;Report Builder&#41;](../report-properties-dialog-box-page-setup-report-builder.md) </span></span>  
 [<span data-ttu-id="62cb3-163">보고서 디자인 뷰&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="62cb3-163">Report Design View &#40;Report Builder&#41;</span></span>](report-design-view-report-builder.md)  
  
  
