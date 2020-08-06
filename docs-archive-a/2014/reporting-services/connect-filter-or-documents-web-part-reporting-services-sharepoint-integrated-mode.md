---
title: 필터 또는 문서 웹 파트 연결 (SharePoint 통합 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Filter Web Part [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
- Documents Web Part [Reporting Services]
ms.assetid: 6a303135-c0ef-44cd-a423-1cea8df3dcf3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5ea7b9f9aba128052ae6ac7f05ef40517eb50e6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648332"
---
# <a name="connect-filter-or-documents-web-part-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="72863-102">필터 또는 문서 웹 파트 연결(SharePoint 통합 모드의 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="72863-102">Connect Filter or Documents Web Part (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="72863-103">SharePoint 제품을 사용하는 경우 필터 웹 파트 또는 문서 웹 파트와 보고서 뷰어 웹 파트가 포함된 대시보드나 웹 파트 페이지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72863-103">If you are using a SharePoint product, you can create a dashboard or Web Part Page that includes a Filter Web Part or Documents Web part and a Report Viewer Web Part.</span></span> <span data-ttu-id="72863-104">선택한 버전은 [!INCLUDE[SPF2010](../includes/spf2010-md.md)] 또는 [!INCLUDE[SPS2010](../includes/sps2010-md.md)]입니다.</span><span class="sxs-lookup"><span data-stu-id="72863-104">Supported versions are [!INCLUDE[SPF2010](../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../includes/sps2010-md.md)].</span></span> <span data-ttu-id="72863-105">또한 지원되는 버전은 [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] 또는 [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007입니다.</span><span class="sxs-lookup"><span data-stu-id="72863-105">Also supported are [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] or [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007.</span></span> <span data-ttu-id="72863-106">필터 웹 파트를 연결하면 필터 웹 파트의 필터 값을 선택하여 같은 페이지의 매개 변수가 있는 보고서에 해당 값을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72863-106">By connecting a Filter Web Part, users who select filter values in a Filter Web Part can send the value to a parameterized report on the same page.</span></span> <span data-ttu-id="72863-107">문서 웹 파트를 연결하면 문서 라이브러리의 보고서를 클릭하여 인접 보고서 뷰어 웹 파트의 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72863-107">By connecting a Documents Web Part, users who click on reports in the Documents library can view the report in an adjacent Report Viewer Web Part.</span></span>  
  
 <span data-ttu-id="72863-108">필터 웹 파트는 보고서에 있는 하나 이상의 매개 변수에 값을 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="72863-108">The Filter Web Part is used to send values to one or more parameters on a report.</span></span> <span data-ttu-id="72863-109">필터 웹 파트를 사용하려면 보고서에 웹 파트가 보낸 값, 데이터 형식 및 서식과 호환되는 매개 변수가 정의되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-109">To use a Filter Web Part, the report must have parameters defined for it that are compatible with the values, data type, and format sent by the Web Part.</span></span>  
  
 <span data-ttu-id="72863-110">문서 웹 파트는 홈 사이트의 문서 라이브러리와 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72863-110">The Documents Web Part is associated with the Documents library of the Home site.</span></span> <span data-ttu-id="72863-111">문서 라이브러리에서 항목을 보거나, 추가하거나, 제거하려면 **모든 사이트 콘텐츠 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-111">To view, add, or remove items from the Documents library, click **View All Site Content**.</span></span> <span data-ttu-id="72863-112">그런 다음 라이브러리에서 **문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-112">In Libraries, click **Documents**.</span></span> <span data-ttu-id="72863-113">**새로 만들기**, **업로드**및 **동작** 메뉴를 사용하여 문서 라이브러리의 항목을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72863-113">You can use the **New**, **Upload**, and **Actions** menu to manage the items in the Documents library.</span></span>  
  
### <a name="to-connect-a-filter-web-part"></a><span data-ttu-id="72863-114">필터 웹 파트를 연결하려면</span><span class="sxs-lookup"><span data-stu-id="72863-114">To connect a Filter Web Part</span></span>  
  
1.  <span data-ttu-id="72863-115">웹 파트 페이지 또는 대시보드를 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="72863-115">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="72863-116">**사이트 작업** 메뉴에서 **페이지 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-116">On the **Site Actions** menu, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="72863-117">**웹 파트 추가를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-117">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="72863-118">**모든 웹 파트**의 **기타** 범주에서 **SQL Server Reporting Services 보고서 뷰어**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-118">In **All Web Parts**, in the **Miscellaneous** category, select **SQL Server Reporting Services Report Viewer**.</span></span>  
  
5.  <span data-ttu-id="72863-119">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-119">Click **Add**.</span></span> <span data-ttu-id="72863-120">영역의 맨 위에 웹 파트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="72863-120">The Web Part is added at the top of the zone.</span></span>  
  
6.  <span data-ttu-id="72863-121">동일한 웹 파트 페이지 또는 대시보드의 다른 영역에서 **웹 파트 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-121">On another zone in the same Web Part page or dashboard, click **Add a Web Part**.</span></span>  
  
7.  <span data-ttu-id="72863-122">**모든 웹 파트**의 **필터** 섹션에서 웹 파트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-122">In **All Web Parts**, in the **Filters** section, select a Web Part.</span></span>  
  
8.  <span data-ttu-id="72863-123">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-123">Click **Add**.</span></span> <span data-ttu-id="72863-124">영역의 맨 위에 웹 파트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="72863-124">The Web Part is added at the top of the zone.</span></span>  
  
9. <span data-ttu-id="72863-125">웹 파트가 포함된 영역에서 웹 파트 **편집** 메뉴를 클릭하고 **연결**, **필터 값 전송 대상**을 차례로 가리킨 다음 **보고서 뷰어** - *보고서 이름*을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-125">In the zone that contains the Web Part, click the Web Part **edit** menu, point to **Connections**, point to **Send Filter Values To**, and then select **Report Viewer** - *report name*.</span></span>  
  
10. <span data-ttu-id="72863-126">변경 내용을 체크 인하고 페이지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-126">Check in your changes and save the page.</span></span>  
  
### <a name="to-connect-a-documents-web-part"></a><span data-ttu-id="72863-127">문서 웹 파트를 연결하려면</span><span class="sxs-lookup"><span data-stu-id="72863-127">To connect a Documents Web Part</span></span>  
  
1.  <span data-ttu-id="72863-128">웹 파트 페이지 또는 대시보드를 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="72863-128">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="72863-129">**사이트 작업** 메뉴에서 **페이지 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-129">On the **Site Actions** menu, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="72863-130">**웹 파트 추가를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-130">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="72863-131">**모든 웹 파트**의 **목록 및 라이브러리** 섹션에서 **문서**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-131">In **All Web Parts**, in the **Lists and Library** section, select **Documents.**</span></span>  
  
5.  <span data-ttu-id="72863-132">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-132">Click **Add**.</span></span> <span data-ttu-id="72863-133">영역의 맨 위에 웹 파트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="72863-133">The Web Part is added at the top of the zone.</span></span>  
  
6.  <span data-ttu-id="72863-134">도구 창의 아래쪽에서 **적용** 을 클릭한 다음 **확인** 을 클릭하여 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="72863-134">Click **Apply** at the bottom of the tool pane, and then click **OK** to close the pane.</span></span>  
  
7.  <span data-ttu-id="72863-135">동일한 웹 파트 페이지 또는 대시보드의 다른 영역에서 **웹 파트 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-135">On another zone in the same Web Part page or dashboard, click **Add a Web Part**.</span></span>  
  
8.  <span data-ttu-id="72863-136">**모든 웹 파트**의 **기타** 범주에서 **SQL Server Reporting Services 보고서 뷰어.**</span><span class="sxs-lookup"><span data-stu-id="72863-136">In **All Web Parts**, in the **Miscellaneous** category, select **SQL Server Reporting Services Report Viewer.**</span></span>  
  
9. <span data-ttu-id="72863-137">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-137">Click **Add**.</span></span> <span data-ttu-id="72863-138">영역의 맨 위에 웹 파트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="72863-138">The Web Part is added at the top of the zone.</span></span>  
  
10. <span data-ttu-id="72863-139">웹 파트가 포함된 영역에서 웹 파트 **편집** 메뉴를 클릭하고 **연결**, **보고서 정의를 가져올 대상**을 차례로 가리킨 다음 **문서**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-139">In the zone that contains the Web Part, click the Web Part **edit** menu, point to **Connections**, point to **Get report definitions from**, and then select **Documents**.</span></span>  
  
11. <span data-ttu-id="72863-140">변경 내용을 체크 인하고 페이지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="72863-140">Check in your changes and save the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72863-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72863-141">See Also</span></span>  
 <span data-ttu-id="72863-142">[웹 페이지에 보고서 뷰어 웹 파트를 추가 하 여 SharePoint 통합 모드에서 Reporting Services &#40;&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="72863-142">[Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="72863-143">[SharePoint 사이트의 보고서 뷰어 웹 파트](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="72863-143">[Report Viewer Web Part on a SharePoint Site](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="72863-144">보고서 뷰어 웹 파트 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="72863-144">Customize the Report Viewer Web Part</span></span>](../../2014/reporting-services/customize-the-report-viewer-web-part.md)  
  
  
