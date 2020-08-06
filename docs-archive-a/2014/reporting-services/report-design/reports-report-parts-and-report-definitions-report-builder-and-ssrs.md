---
title: 보고서, 보고서 파트 및 보고서 정의(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report definitions
- reports
ms.assetid: 2d746550-f8cc-4e97-8a06-d0f03cffc18d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0926de326d0b5859e895d69da4dd2ad7863ccd2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659816"
---
# <a name="reports-report-parts-and-report-definitions-report-builder-and-ssrs"></a><span data-ttu-id="f6fa5-102">보고서, 보고서 파트 및 보고서 정의(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f6fa5-102">Reports, Report Parts, and Report Definitions (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="f6fa5-103">는 다양 한 용어를 사용 하 여 사용자에 게 표시 되는 초기 정의, 게시 된 보고서 및 표시 된 보고서를 비롯 한 여러 상태의 보고서를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-103">uses a variety of terms to describe a report in different states, including the initial definition, the published report, and the viewed report as it appears to the user.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-definition-rdl-files"></a><span data-ttu-id="f6fa5-104">보고서 정의 파일(.rdl)</span><span class="sxs-lookup"><span data-stu-id="f6fa5-104">Report Definition (.rdl) Files</span></span>  
 <span data-ttu-id="f6fa5-105">보고서 정의는 보고서 작성기나 보고서 디자이너에서 만든 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-105">A report definition is a file that you create in Report Builder or Report Designer.</span></span> <span data-ttu-id="f6fa5-106">이 파일은 데이터 원본 연결에 대한 완전한 설명, 데이터 검색에 사용되는 쿼리, 식, 매개 변수, 이미지, 입력란, 테이블 및 보고서에 포함할 수 있는 기타 디자인 타임 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-106">It provides a complete description of data source connections, queries used to retrieve data, expressions, parameters, images, text boxes, tables, and any other design-time elements that you might include in a report.</span></span> <span data-ttu-id="f6fa5-107">보고서 정의는 복잡할 수도 있지만 기본적으로 쿼리 및 기타 보고서 내용, 보고서 속성 및 보고서 레이아웃을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-107">Although report definitions can be complex, at a minimum they specify a query and other report content, report properties, and a report layout.</span></span>  
  
 <span data-ttu-id="f6fa5-108">보고서 정의는 런타임에 처리된 보고서로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-108">Report definitions are rendered at run time as a processed report.</span></span> <span data-ttu-id="f6fa5-109">이 시점에서 데이터가 데이터 원본에서 검색되고 보고서 정의의 명령에 따라 형식이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-109">At that time, the data is retrieved from the data source and formatted according to the instructions in the report definition.</span></span> <span data-ttu-id="f6fa5-110">보고서 정의는 컴퓨터에서 직접 실행하고 로컬에 저장할 수 있으며 보고서 서버에 게시하여 다른 사람이 실행하도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-110">A report definition can be run directly from your computer and saved locally, or it can be published to a report server for others to run as well.</span></span>  
  
 <span data-ttu-id="f6fa5-111">보고서 정의는 RDL(Report Definition Language)이라는 XML 문법에 맞는 XML로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-111">Report definitions are written in XML that conforms to an XML grammar called Report Definition Language (RDL).</span></span> <span data-ttu-id="f6fa5-112">RDL은 보고서에서 가정할 수 있는 모든 변형을 포함하는 XML 요소를 기술합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-112">RDL describes the XML elements, encompassing all possible variations that a report can assume.</span></span>  
  
## <a name="client-report-definition-rdlc-files"></a><span data-ttu-id="f6fa5-113">클라이언트 보고서 정의 파일(.rdlc)</span><span class="sxs-lookup"><span data-stu-id="f6fa5-113">Client Report Definition (.rdlc) Files</span></span>  
 <span data-ttu-id="f6fa5-114">Visual Studio 보고서 디자이너는 ReportViewer 컨트롤에 사용할 클라이언트 보고서 정의 파일(.rdlc)을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-114">The Visual Studio Report Designer produces client report definition (.rdlc) files for use with the ReportViewer control.</span></span> <span data-ttu-id="f6fa5-115">.rdlc 파일을 .rdl 파일로 변환하여 Reporting Services 보고서 디자이너에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-115">The .rdlc files can be converted to .rdl files for use with Reporting Services Report Designer.</span></span>  
  
## <a name="report-part-rsc-files"></a><span data-ttu-id="f6fa5-116">보고서 파트 파일(.rsc)</span><span class="sxs-lookup"><span data-stu-id="f6fa5-116">Report Part (.rsc) Files</span></span>  
 <span data-ttu-id="f6fa5-117">보고서 파트 정의는 보고서 정의 파일의 XML 조각입니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-117">A report part definition is an XML fragment of a report definition file.</span></span> <span data-ttu-id="f6fa5-118">보고서 정의를 만든 다음 보고서의 보고서 항목을 선택하여 별도의 보고서 파트로 게시하는 방법으로 보고서 파트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-118">You create report parts by creating a report definition, and then selecting report items in the report to publish separately as report parts.</span></span> <span data-ttu-id="f6fa5-119">보고서 파트에는 데이터 영역, 사각형과 이에 포함된 항목 및 이미지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-119">Report parts include data regions, rectangles and their contained items, and images.</span></span> <span data-ttu-id="f6fa5-120">보고서 파트를 종속 데이터 세트 및 공유 데이터 원본 참조와 함께 저장하여 다른 보고서에서 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-120">You can save a report part with its dependent datasets and shared data source references so it can be reused in other reports.</span></span>  
  
 [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
## <a name="published-reports"></a><span data-ttu-id="f6fa5-121">게시된 보고서</span><span class="sxs-lookup"><span data-stu-id="f6fa5-121">Published Reports</span></span>  
 <span data-ttu-id="f6fa5-122">.rdl 파일을 만든 후에는 로컬에 저장하거나 보고서 서버의 내 보고서 폴더와 같은 개인 폴더에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-122">After you create an .rdl file, you can save it locally, or save it to a personal folder (such as the My Reports folder) on the report server.</span></span> <span data-ttu-id="f6fa5-123">다른 사용자가 볼 수 있도록 보고서를 설정하려면 보고서 작성기에서 보고서 서버의 공용 폴더로 저장하거나, 보고서 관리자로 업로드하거나, 보고서 디자이너에서 보고서 프로젝트 솔루션을 배포하여 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-123">When the report is ready for others to see, you publish it by saving it from Report Builder to a public folder on the report server, uploading it through Report Manager, or deploying a report project solution from Report Designer.</span></span> <span data-ttu-id="f6fa5-124">게시된 보고서는 보고서 서버 데이터베이스에 저장되고 보고서 서버 또는 SharePoint 사이트에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-124">A published report is an item that is stored in a report server database and managed on a report server or SharePoint site.</span></span>  
  
 <span data-ttu-id="f6fa5-125">게시된 보고서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 역할 기반 보안 모델을 사용하여 역할 할당을 통해 보안이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-125">A published report is secured through role assignments using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] role-based security model.</span></span> <span data-ttu-id="f6fa5-126">게시된 보고서는 URL, SharePoint 웹 파트 또는 보고서 관리자를 통해 액세스하거나 보고서 작성기에서 해당 보고서를 찾아서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-126">Published reports are accessed through URLs, SharePoint Web parts, or Report Manager, or you can navigate to and open them in Report Builder.</span></span>  
  
### <a name="report-snapshots"></a><span data-ttu-id="f6fa5-127">보고서 스냅샷</span><span class="sxs-lookup"><span data-stu-id="f6fa5-127">Report Snapshots</span></span>  
 <span data-ttu-id="f6fa5-128">보고서는 보고서를 처음 실행했을 때의 레이아웃 정보와 데이터가 모두 포함된 스냅샷으로 게시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-128">A report can also be published as a snapshot that contains both layout information and data as of the time the report was initially run.</span></span> <span data-ttu-id="f6fa5-129">보고서 스냅샷은 특정 렌더링 형식으로 저장되지 않으며</span><span class="sxs-lookup"><span data-stu-id="f6fa5-129">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="f6fa5-130">사용자나 애플리케이션이 보고서 스냅샷을 요청할 때만 HTML과 같은 최종 보기 형식으로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-130">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="f6fa5-131">자세한 내용은 [보고서 관리자에서 보고서 찾기 및 보기&#40;보고서 작성기 및 SSRS&#41;](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-131">For more information, see [Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).</span></span>  
  
## <a name="rendered-reports"></a><span data-ttu-id="f6fa5-132">렌더링된 보고서</span><span class="sxs-lookup"><span data-stu-id="f6fa5-132">Rendered Reports</span></span>  
 <span data-ttu-id="f6fa5-133">렌더링된 보고서는 데이터와 레이아웃 정보가 HTML과 같은 적합한 표시 형식으로 포함되어 있는 완전히 처리된 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-133">A rendered report is a fully processed report that contains both data and layout information in a format suitable for viewing (such as HTML).</span></span> <span data-ttu-id="f6fa5-134">출력 형식으로 렌더링되지 않은 보고서는 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-134">Until a report is rendered into an output format, it cannot be viewed.</span></span> <span data-ttu-id="f6fa5-135">다음 중 하나를 수행하여 보고서를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-135">You can render a report by doing one of the following:</span></span>  
  
-   <span data-ttu-id="f6fa5-136">보고서 작성기 또는 보고서 디자이너에서 보고서를 만들거나 열고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-136">Create or open a report in Report Builder or Report Designer and run it.</span></span>  
  
-   <span data-ttu-id="f6fa5-137">보고서 관리자에서 보고서를 찾아 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-137">Find and run a report in Report Manager.</span></span>  
  
-   <span data-ttu-id="f6fa5-138">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버와 통합된 SharePoint 사이트에서 보고서를 찾고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-138">Find and run a report on a SharePoint site that is integrated with a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span>  
  
-   <span data-ttu-id="f6fa5-139">사용자가 지정한 출력 형식으로 전자 메일 받은 편지함이나 파일 공유 위치로 배달되는 보고서를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-139">Subscribe to a report, which is delivered to an e-mail inbox or a file share in an output format that you specify.</span></span>  
  
 <span data-ttu-id="f6fa5-140">사용자가 지정한 출력 형식으로 전자 메일 받은 편지함이나 파일 공유 위치로 배달되는 보고서를 구독합니다. 보고서의 기본 렌더링 형식은 HTML 4.0입니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-140">Subscribe to a report, which is delivered to an e-mail inbox or a file share in an output format that you specify.The default rendering format for a report is HTML 4.0.</span></span> <span data-ttu-id="f6fa5-141">보고서는 HTML 외에도 Excel, Word, XML, PDF, TIFF 및 CSV를 비롯한 다양한 출력 형식으로 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-141">In addition to HTML, reports can be rendered in a variety of output formats, including Excel, Word, XML, PDF, TIFF, and CSV.</span></span> <span data-ttu-id="f6fa5-142">게시된 보고서와 마찬가지로 렌더링된 보고서는 편집하거나 보고서 서버에 다시 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-142">As with published reports, rendered reports cannot be edited or saved back to a report server.</span></span> <span data-ttu-id="f6fa5-143">자세한 내용은 [보고서 작성기 및 SSRS&#41;&#40;보고서 내보내기 ](../report-builder/export-reports-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fa5-143">For more information, see [Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fa5-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6fa5-144">See Also</span></span>  
 <span data-ttu-id="f6fa5-145">[보고서 작성기 및 SSRS &#40;보고서 제작 개념&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6fa5-145">[Report Authoring Concepts &#40;Report Builder and SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f6fa5-146">[2014 SQL Server의 보고서 작성기](../report-builder/report-builder-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="f6fa5-146">[Report Builder in SQL Server 2014](../report-builder/report-builder-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="f6fa5-147">[설치, 제거 및 보고서 작성기 지원](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="f6fa5-147">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="f6fa5-148">[보고서 작성기 및 SSRS &#40;보고서 찾기, 보기 및 관리 &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6fa5-148">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f6fa5-149">보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기</span><span class="sxs-lookup"><span data-stu-id="f6fa5-149">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
