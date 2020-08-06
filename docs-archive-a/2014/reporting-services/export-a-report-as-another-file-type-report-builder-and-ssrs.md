---
title: 다른 파일 형식으로 보고서 내보내기 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b577568b-ecbd-44c3-be88-31dab6fc38a2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 240d3266b7b8c9a445658a9fd21fb9ea18a4c113
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728080"
---
# <a name="export-a-report-as-another-file-type-report-builder-and-ssrs"></a><span data-ttu-id="48db0-102">다른 파일 형식으로 보고서 내보내기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="48db0-102">Export a Report as Another File Type (Report Builder and SSRS)</span></span>
  <span data-ttu-id="48db0-103">보고서 작성기 또는 보고서 디자이너에서 보고서를 미리 보면서 CSV, 이미지, PDF, [!INCLUDE[ofprword](../includes/ofprword-md.md)]또는 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]같은 다른 파일 형식으로 보고서를 렌더링할 수도 있고, 보고서 서버에서 보고서를 보면서 보고서를 렌더링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-103">You can render a report to another file format, such as CSV, Image, PDF, [!INCLUDE[ofprword](../includes/ofprword-md.md)], or [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], while previewing your report in Report Builder or Report Designer, or you can render the report while viewing the report on the report server.</span></span> <span data-ttu-id="48db0-104">보고서를 특정 형식으로 렌더링하면 보고서를 보고서 서버에 게시하지 않고서 보고서를 다른 파일 형식으로 즉시 저장하려는 경우나 보고서를 읽는 사람에게 특정 형식으로 배달된 보고서의 디자인이 어떤 모양일지 미리 확인하려는 경우에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-104">Rendering the report in a specific format in is helpful when you want to immediately save the report as another file type without publishing the report to the report server or when you want to see how your report design will appear when delivered to your report readers in a specific format.</span></span> <span data-ttu-id="48db0-105">보고서 서버에서 보고서를 렌더링하면 구독을 설정하려는 경우나 전자 메일을 통해 보고서를 배달하려는 경우 또는 보고서 서버에서 사용할 수 있도록 보고서를 저장하려는 경우에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-105">Rendering the report on the report server is useful when you set up subscriptions or deliver your reports via e-mail, or if you want to save a report that is available on the report server.</span></span> <span data-ttu-id="48db0-106">자세한 내용은 [구독 및 배달&#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="48db0-106">For more information, see [Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-export-a-report-as-another-file-type-in-report-builder"></a><span data-ttu-id="48db0-107">보고서 작성기에서 보고서를 다른 파일 형식으로 내보내려면</span><span class="sxs-lookup"><span data-stu-id="48db0-107">To export a report as another file type in Report Builder</span></span>  
  
1.  <span data-ttu-id="48db0-108">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-108">Preview the report.</span></span>  
  
2.  <span data-ttu-id="48db0-109">리본에서 **내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-109">On the ribbon, click **Export**.</span></span>  
  
3.  <span data-ttu-id="48db0-110">사용할 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-110">Select the format that you want to use.</span></span>  
  
     <span data-ttu-id="48db0-111">**다른 이름으로 저장** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-111">The **Save As** dialog box opens.</span></span> <span data-ttu-id="48db0-112">기본적으로 파일 이름은 내보낸 보고서의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-112">By default, the file name is that of the report that you exported.</span></span> <span data-ttu-id="48db0-113">필요한 경우 파일 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-113">Optionally, you can change the file name.</span></span>  
  
4.  <span data-ttu-id="48db0-114">내보낸 보고서를 저장한 위치로 이동하여 해당 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-114">Navigate to the location where you saved the exported report and open it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48db0-115">해당 파일 형식과 연결된 프로그램이 없기 때문에 선택한 형식으로 보고서를 열 수 없는 경우에는 내보낸 보고서를 저장하거나 보고서를 열기 위한 프로그램을 온라인으로 찾으라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-115">If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
### <a name="to-export-a-report-as-another-file-type-in-report-manager"></a><span data-ttu-id="48db0-116">보고서 관리자에서 보고서를 다른 파일 형식으로 내보내려면</span><span class="sxs-lookup"><span data-stu-id="48db0-116">To export a report as another file type in Report Manager</span></span>  
  
1.  <span data-ttu-id="48db0-117">보고서 관리자 **홈** 페이지에서 내보낼 보고서를 찾아 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-117">From the Report Manager **Home** page, navigate to the report that you want to export.</span></span>  
  
2.  <span data-ttu-id="48db0-118">보고서를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-118">Click the report.</span></span>  
  
     <span data-ttu-id="48db0-119">보고서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-119">The report is generated.</span></span>  
  
3.  <span data-ttu-id="48db0-120">보고서 뷰어 도구 모음에서 **형식 선택** 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-120">On the Report Viewer toolbar, click the **Select a format** drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="48db0-121">사용할 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-121">Select the format that you want to use.</span></span>  
  
5.  <span data-ttu-id="48db0-122">클릭 **내보내기**합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-122">Click **Export**.</span></span>  
  
     <span data-ttu-id="48db0-123">파일을 열지 저장할지 확인하는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-123">A message appears asking you if you want to open or save the file.</span></span>  
  
6.  <span data-ttu-id="48db0-124">선택한 내보내기 형식으로 보고서를 보려면 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-124">To view the report in the selected export format, click **Open**.</span></span>  
  
     <span data-ttu-id="48db0-125">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="48db0-125">\- or -</span></span>  
  
     <span data-ttu-id="48db0-126">선택한 내보내기 형식으로 보고서를 즉시 저장하려면 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-126">To immediately save the report in the selected export format, click **Save**.</span></span>  
  
     <span data-ttu-id="48db0-127">선택한 형식에 연결되어 있는 애플리케이션을 사용하여 보고서가 표시 또는 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-127">Using the application that is associated with the format that you chose, the report is either displayed or saved.</span></span> <span data-ttu-id="48db0-128">**저장**을 클릭하면 보고서를 저장할 위치를 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-128">If you click **Save**, you will be prompted for a location where you can save your report.</span></span>  
  
     <span data-ttu-id="48db0-129">**참고** 선택한 파일 형식에 연결된 프로그램이 없어서 지정된 형식으로 보고서를 열 수 없는 경우에는 내보낸 보고서를 저장하거나 보고서를 여는 데 필요한 프로그램을 온라인으로 찾으라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-129">**Note** If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
### <a name="to-export-a-report-as-another-file-type-in-a-sharepoint-library"></a><span data-ttu-id="48db0-130">SharePoint 라이브러리에서 보고서를 다른 파일 형식으로 내보내려면</span><span class="sxs-lookup"><span data-stu-id="48db0-130">To export a report as another file type in a SharePoint library</span></span>  
  
1.  <span data-ttu-id="48db0-131">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-131">Preview the report.</span></span>  
  
2.  <span data-ttu-id="48db0-132">도구 모음에서 **동작**을 클릭하고 **내보내기**를 가리킨 다음 사용할 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-132">On the toolbar, click **Actions**, point to **Export**, and then select the format that you want to use.</span></span>  
  
     <span data-ttu-id="48db0-133">**파일 다운로드** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-133">The **File Download** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="48db0-134">선택한 내보내기 형식으로 보고서를 보려면 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-134">To view the report in the selected export format, click **Open**.</span></span>  
  
     <span data-ttu-id="48db0-135">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="48db0-135">\- or -</span></span>  
  
     <span data-ttu-id="48db0-136">선택한 내보내기 형식으로 보고서를 즉시 저장하려면 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-136">To immediately save the report in the selected export format, click **Save**.</span></span>  
  
     <span data-ttu-id="48db0-137">선택한 형식에 연결되어 있는 애플리케이션을 사용하여 보고서가 표시 또는 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-137">Using the application that is associated with the format that you chose, the report is either displayed or saved.</span></span> <span data-ttu-id="48db0-138">**저장**을 클릭하면 보고서를 저장할 위치를 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-138">If you click **Save**, you will be prompted for a location where you can save your report.</span></span>  
  
     <span data-ttu-id="48db0-139">필요한 경우 내보낸 보고서의 파일 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-139">Optionally, change the file name of the exported report.</span></span>  
  
     <span data-ttu-id="48db0-140">**참고** 선택한 파일 형식에 연결된 프로그램이 없어서 지정된 형식으로 보고서를 열 수 없는 경우에는 내보낸 보고서를 저장하거나 보고서를 여는 데 필요한 프로그램을 온라인으로 찾으라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="48db0-140">**Note** If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48db0-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48db0-141">See Also</span></span>  
 <span data-ttu-id="48db0-142">[보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기](report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="48db0-142">[Exporting Reports &#40;Report Builder and SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="48db0-143">[Reporting Services &#40;보고서 작성기 및 SSRS의 페이지 매김&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="48db0-143">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="48db0-144">여러 보고서 렌더링 확장 프로그램의 대화형 기능&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="48db0-144">Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;</span></span>](report-builder/interactive-functionality-different-report-rendering-extensions.md)  
  
  
