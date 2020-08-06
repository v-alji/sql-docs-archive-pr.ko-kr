---
title: SharePoint 통합의 보고서 뷰어 웹 파트 프로그래밍 기능 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 494ebc3e6668e4d95480019e522caf46b83a6c4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734992"
---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a><span data-ttu-id="aec77-102">SharePoint 통합의 보고서 뷰어 웹 파트 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="aec77-102">Report Viewer Web Part Programmability in SharePoint Integration</span></span>
  <span data-ttu-id="aec77-103">보고서 뷰어 웹 파트는 `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` 서버 컨트롤로, 개발자가 사용자 지정 SharePoint 애플리케이션을 만드는 데 사용할 수 있는 공용 API(응용 프로그래밍 인터페이스) 집합을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-103">The Report Viewer Web Part is a `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` server control, which contains a set of public application programming interfaces (API) that enables developers to create custom SharePoint applications.</span></span> <span data-ttu-id="aec77-104">웹 파트 연결을 사용하여 보고서 뷰어 웹 파트에 보고서 경로 및 매개 변수를 제공하는 사용자 지정 웹 파트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-104">You can create custom Web Parts that supply report path and parameters to Report Viewer Web Part using Web Part connections.</span></span> <span data-ttu-id="aec77-105">사용자 지정 SharePoint 웹 파트 페이지 내에 웹 파트를 포함하고 공용 API를 사용하여 웹 파트를 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-105">You can also embed the Web Part in a custom SharePoint Web Part page and customize it using the public API.</span></span>  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a><span data-ttu-id="aec77-106">사용자 지정 웹 파트를 사용하여 보고서 뷰어 웹 파트에 연결</span><span class="sxs-lookup"><span data-stu-id="aec77-106">Connecting to Report Viewer Web Part with Custom Web Parts</span></span>  
 <span data-ttu-id="aec77-107">보고서 뷰어 웹 파트는 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 또는 `T:Microsoft.SharePoint.WebPartPages.IFilterValues`를 구현하는 SharePoint 웹 파트에 대한 연결 소비자입니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-107">The Report Viewer Web Part is a connection consumer to SharePoint Web Parts that implement <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> or `T:Microsoft.SharePoint.WebPartPages.IFilterValues`.</span></span> <span data-ttu-id="aec77-108">**문서** 웹 파트와 같은 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 웹 파트는 보고서 뷰어 웹 파트와 동일한 웹 파트 페이지에 배치되는 경우 보고서 뷰어 웹 파트에 보고서 경로를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-108">An <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part, such as the **Documents** Web Part can supply a report path to a Report Viewer Web Part when placed on the same Web Part page as the Report Viewer Web Part.</span></span> <span data-ttu-id="aec77-109">마찬가지로, `T:Microsoft.SharePoint.WebPartPages.IFilterValues` **텍스트 필터** 또는 **선택 필터**와 같은 웹 파트는 보고서 뷰어 웹 파트와 동일한 웹 파트 페이지에 배치 될 때 보고서 뷰어 웹 파트에 보고서 매개 변수를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-109">Likewise, an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part, such as the **Text Filter** or the **Choice Filter**, can supply a report parameter to a Report Viewer Web Part when placed on the same Web Part page as the Report Viewer Web Part.</span></span>  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a><span data-ttu-id="aec77-110">IWebPartRow를 사용하여 보고서 경로 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="aec77-110">Implementing a Report Path Provider with IWebPartRow</span></span>  
 <span data-ttu-id="aec77-111">웹 파트 연결을 통해 보고서 뷰어 웹 파트에 보고서 경고를 제공하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="aec77-111">To supply a report path to the Report Viewer Web Part through Web Part connections, do the following:</span></span>  
  
1.  <span data-ttu-id="aec77-112"><xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 인터페이스를 구현하는 웹 파트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-112">Create a Web Part that implements the <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> interface.</span></span>  
  
2.  <span data-ttu-id="aec77-113">이 웹 파트를 보고서 뷰어 웹 파트와 동일한 웹 파트 페이지에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-113">Add the Web Part to the same Web Part page as the Report Viewer Web Part.</span></span>  
  
3.  <span data-ttu-id="aec77-114">웹 기반 웹 파트 디자인 사용자 인터페이스에서 웹 파트를 보고서 뷰어 웹 파트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-114">Connect your Web Part to the Report Viewer Web Part in the Web-based Web Part design user interface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aec77-115">보고서 뷰어 웹 파트에는 한 번에 하나의 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 웹 파트만 연결할 수 있으며, <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 웹 파트와 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 웹 파트를 동시에 모두 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-115">You can only connect one <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part to the Report Viewer Web Part at a time, and you cannot connect both an <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part and an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part at the same time.</span></span>  
  
 <span data-ttu-id="aec77-116"><xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 웹 파트가 `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`와 함께 올바르게 작동하려면 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> 메서드에서 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-116">For your <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part to work properly with the `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`, you must do the following in the <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> method:</span></span>  
  
-   <span data-ttu-id="aec77-117">입력 매개 변수로 <xref:System.Data.DataRowView> 개체를 사용하여 콜백 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-117">Invoke the callback method with a <xref:System.Data.DataRowView> object as the input parameter.</span></span>  
  
-   <span data-ttu-id="aec77-118"><xref:System.Data.DataRowView> 개체에 보고서 경로를 포함하는 "DocUrl"이라는 열이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-118">Make sure that the <xref:System.Data.DataRowView> object contains a column called "DocUrl" that contains the report path.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aec77-119">[!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010용 추가 기능의 보고서 뷰어 웹 파트에서도 "FileRef" 열을 사용한 보고서 경로 받기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-119">The Report Viewer Web Part in the add-in for [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 also supports receiving the report path using the "FileRef" column.</span></span>  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a><span data-ttu-id="aec77-120">IFilterValues를 사용하여 보고서 매개 변수 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="aec77-120">Implementing a Report Parameter Provider with IFilterValues</span></span>  
 <span data-ttu-id="aec77-121">`T:Microsoft.SharePoint.WebPartPages.IFilterValues`를 구현하는 웹 파트는 보고서 뷰어 웹 파트에 하나의 매개 변수 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-121">A Web Part that implements `T:Microsoft.SharePoint.WebPartPages.IFilterValues` can provide one parameter value to the Report Viewer Web Part.</span></span> <span data-ttu-id="aec77-122">보고서 뷰어 웹 파트로 전달되는 이 매개 변수 값에는 보고서 정의에서 보고서 매개 변수에 대해 설정된 것과 동일한 제한(예: 데이터 형식, 유효한 값 등)이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-122">The parameter value sent to the Report Viewer Web Part is subject to the same restrictions placed on the report parameter as specified in the report definition, such as data type, valid values, and so on</span></span>  
  
 <span data-ttu-id="aec77-123">보고서 뷰어 웹 파트에 보고서 매개 변수를 제공하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="aec77-123">To supply a report parameter to the Report Viewer Web Part, do the following:</span></span>  
  
1.  <span data-ttu-id="aec77-124">`T:Microsoft.SharePoint.WebPartPages.IFilterValues` 인터페이스를 구현하는 웹 파트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-124">Create a Web Part that implements the `T:Microsoft.SharePoint.WebPartPages.IFilterValues` interface.</span></span>  
  
2.  <span data-ttu-id="aec77-125">이 웹 파트를 `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`와 동일한 페이지에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-125">Add the Web Part to the same page as the `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`.</span></span>  
  
3.  <span data-ttu-id="aec77-126">웹 기반 웹 파트 디자인 사용자 인터페이스에서 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 웹 파트를 보고서 뷰어 웹 파트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-126">Connect your `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part in the Web-based Web Part design user interface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aec77-127">보고서 뷰어 웹 파트에는 한 번에 여러 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 웹 파트를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-127">You can connect multiple `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Parts to the Report Viewer Web Part at a time.</span></span> <span data-ttu-id="aec77-128">그러나 보고서 뷰어 웹 파트에 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 웹 파트와 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` 웹 파트를 동시에 모두 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aec77-128">However, you cannot connect both an <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part and an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part at the same time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec77-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aec77-129">See Also</span></span>  
 <span data-ttu-id="aec77-130">[IFilterValues 인터페이스](https://msdn.microsoft.com/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)</span><span class="sxs-lookup"><span data-stu-id="aec77-130">[IFilterValues interface](https://msdn.microsoft.com/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)</span></span>  
  
  
