---
title: Microsoft Surface 장치 및 Apple iOS 장치에서 Reporting Services 보고서 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: db52ed500559969ae52eb9477caa6b410889c1d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653201"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a><span data-ttu-id="149b5-102">Microsoft Surface 디바이스 및 Apple iOS 디바이스에서 Reporting Services 보고서 보기</span><span class="sxs-lookup"><span data-stu-id="149b5-102">View Reporting Services Reports on Microsoft Surface Devices and  Apple iOS Devices</span></span>
  <span data-ttu-id="149b5-103">이 문서에서는 Microsoft Surface 디바이스 및 iPad와 같은 Apple iOS 6 및 Apple Safari 디바이스에서 지원되는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능 및 워크플로를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-103">This article describes the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features and workflows supported for Microsoft Surface devices, and devices with Apple iOS 6 and Apple Safari such as the iPad.</span></span>

## <a name="view-and-interact-with-reports"></a><span data-ttu-id="149b5-104">보고서 보기 및 상호 작용</span><span class="sxs-lookup"><span data-stu-id="149b5-104">View and Interact With Reports</span></span>
 <span data-ttu-id="149b5-105">[!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]부터 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 는 Microsoft Surface 디바이스 및 iPad와 같은 Apple iOS 6 및 Apple Safari 브라우저 디바이스에서 보고서 보기 및 기본 상호 작용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-105">Starting with [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supports viewing and basic interactivity with reports on Microsoft Surface devices, and devices with Apple iOS 6 and Apple Safari browser such as the iPad.</span></span> <span data-ttu-id="149b5-106">Microsoft Surface 디바이스를 사용하는 보고서를 게시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-106">You can also publish reports using Microsoft Surface devices.</span></span>

 <span data-ttu-id="149b5-107">![IPad 데스크톱](media/videothumbnail.jpg "IPad 바탕 화면") IPad에서 보고서를 보는 방법에 대 한 데모를 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="149b5-107">![IPad Desktop](media/videothumbnail.jpg "IPad Desktop") Watch a demonstration of viewing reports on an iPad.</span></span>

 <span data-ttu-id="149b5-108">Windows Phone 8 디바이스에서 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서를 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-108">You can also view [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports on a Windows Phone 8 device.</span></span>

 <span data-ttu-id="149b5-109">이 항목에서 설명하는 기능을 활용하려면 다음 중 하나를 설치하세요.</span><span class="sxs-lookup"><span data-stu-id="149b5-109">To utilize the features described in this topic, install one of the following:</span></span>

-   <span data-ttu-id="149b5-110">기본 모드 보고서 서버의 경우 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 이상을 설치하세요.</span><span class="sxs-lookup"><span data-stu-id="149b5-110">For a native mode report server, install [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] or later.</span></span>

     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]<span data-ttu-id="149b5-111">는 [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=35575)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-111">is available for download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=35575).</span></span>

-   <span data-ttu-id="149b5-112">SharePoint 모드 보고서 서버의 경우 SharePoint 제품용 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 추가 기능( [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 이상)을 설치하세요.</span><span class="sxs-lookup"><span data-stu-id="149b5-112">For a SharePoint mode report server, install [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] or later of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>

 <span data-ttu-id="149b5-113">**iPad 디바이스 또는 Microsoft Surface 디바이스에서 보고서를 보고 상호 작용하려면**</span><span class="sxs-lookup"><span data-stu-id="149b5-113">**To view and interact with a report on an iPad device or Microsoft Surface device**</span></span>

1.  <span data-ttu-id="149b5-114">보고서 서버 또는 보고서가 있는 SharePoint 사이트에 연결할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-114">Make sure that you can connect to the report server or SharePoint site where the report resides.</span></span>

2.  <span data-ttu-id="149b5-115">다음 중 하나를 수행하여 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-115">Open the report by doing one of the following.</span></span>

    -   <span data-ttu-id="149b5-116">**전자 메일에서 시작:**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 구독으로 만들어진 전자 메일에서 보고서의 URL을 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-116">**Start from e-mail:** From an e-mail that is created by a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] subscription, tap the URL of the report.</span></span> <span data-ttu-id="149b5-117">보고서가 브라우저에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-117">The report will open in the browser.</span></span>

    -   <span data-ttu-id="149b5-118">**보고서 서버에서 시작:**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버에 있는 디렉터리를 찾은 다음 보고서 이름을 탭하여 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-118">**Start from Report Server:** Browse the directory on the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server, and then tap the report name to open the report.</span></span>

    -   <span data-ttu-id="149b5-119">**SharePoint 문서 라이브러리에서 시작:**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서가 포함된 SharePoint 문서 라이브러리를 찾은 다음 보고서 이름을 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-119">**Start from a SharePoint document library:** Browse to a SharePoint document library that contains [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports, and then tap the report name.</span></span> <span data-ttu-id="149b5-120">보고서를 보고 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-120">You can view and interact with the report.</span></span>

        > [!IMPORTANT]
        >  <span data-ttu-id="149b5-121">iPad의 경우 Safari의 **Private 브라우징** 속성이 해제되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-121">For the iPad, ensure that the **Private Browsing** property for Safari is turned off.</span></span>

    -   <span data-ttu-id="149b5-122">**SharePoint 웹 파트:** SharePoint 페이지에 웹 파트가 추가된 경우 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-122">**SharePoint web part:** If the web part has been added to a SharePoint page, you can view [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports.</span></span>

3.  <span data-ttu-id="149b5-123">Microsoft Surface 디바이스에서 보고서 관리자를 사용하여 보고서를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-123">On your Microsoft Surface device, you can also open the report by using Report Manager.</span></span> <span data-ttu-id="149b5-124">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 관리자에 있는 디렉터리를 찾은 다음 보고서 이름을 눌러 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-124">Browse the directory in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Manager, and then tap the report name to open the report.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="149b5-125">보고서 관리자에서 보고서 보기는 iPad에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-125">Viewing reports in Report Manager is not supported on an iPad.</span></span>

4.  <span data-ttu-id="149b5-126">다음과 같은 방법으로 스크롤 및 확대/축소합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-126">Scroll and zoom by doing the following.</span></span>

    -   <span data-ttu-id="149b5-127">보고서를 스크롤하려면 스크린에서 위쪽, 아래쪽, 왼쪽 또는 오른쪽으로 손가락을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-127">To scroll the report, drag your finger across the screen (up, down, left or right).</span></span> <span data-ttu-id="149b5-128">살짝 밀기입니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-128">This is the swipe gesture.</span></span>

    -   <span data-ttu-id="149b5-129">확대하려면 화면에 두 손가락을 놓고 손가락 사이를 벌립니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-129">To zoom in, place two fingers on the screen and separate the fingers.</span></span> <span data-ttu-id="149b5-130">축소하려면 화면에 두 손가락을 놓고 손가락 사이를 좁힙니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-130">To zoom out, place two fingers on the screen and move the fingers together.</span></span> <span data-ttu-id="149b5-131">축소 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-131">This is the pinch gesture.</span></span>

5.  <span data-ttu-id="149b5-132">다음과 같은 방법으로 보고서를 탐색하고 상호작용합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-132">Navigate and interact with the report by doing the following.</span></span>

    -   <span data-ttu-id="149b5-133">축소하려면 더하기 기호(+)를 누르고 확장하려면 빼기 기호(-)를 눌러 그룹과 관련된 행과 열 및 보고서 항목을 축소하고 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-133">Collapse and expand report items, and rows and columns that are associated with groups, by taping the plus (+) sign to collapse and the minus (-) sign to expand.</span></span>

    -   <span data-ttu-id="149b5-134">정렬 단추를 눌러 행렬의 행과 열 또는 테이블 행의 순서를 오름차순이나 내림차순으로 설정/해제합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-134">Toggle between ascending and descending order for rows in a table or for rows and columns in a matrix, by tapping the sort button.</span></span> <span data-ttu-id="149b5-135">정렬 단추는 일반적으로 열 머리글에 위치합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-135">The sort button is usually located in the column header.</span></span>

    -   <span data-ttu-id="149b5-136">보고서 위쪽의 화살표 단추를 눌러 매개 변수 창을 확장하고 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-136">Expand and collapse the parameter pane, by tapping the arrow button near the top of the report.</span></span>

    -   <span data-ttu-id="149b5-137">매개 변수 옆에 있는 상자 또는 컨트롤을 눌러 매개 변수 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-137">Select a parameter value by tapping the box or control next to the parameter.</span></span> <span data-ttu-id="149b5-138">**보고서 보기** 를 눌러 보고서에 매개 변수 값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-138">Tap **View Report** to apply the parameter value to the report.</span></span>

    -   <span data-ttu-id="149b5-139">**찾기** 옆에 있는 상자를 눌러 검색 용어를 입력한 다음 **찾기**를 눌러 보고서 내용을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-139">Search the report content by taping the box next to **Find**, typing a search term, and then taping **Find**.</span></span>

    -   <span data-ttu-id="149b5-140">탐색 단추를 누르거나 단추 옆 입력란을 누르고 페이지 번호를 입력하여 보고서 페이지를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-140">Navigate the report pages by tapping the navigation buttons, or tapping the text box next to the buttons and typing the page number.</span></span>

    -   <span data-ttu-id="149b5-141">텍스트 상자, 이미지, 차트 및 계기와 같은 보고서 항목에 추가된 하이퍼링크를 눌러 URL로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-141">Navigate to URLs by taping hyperlinks that have been added to report items such as text boxes, images, charts, and gauges.</span></span>

    -   <span data-ttu-id="149b5-142">**드롭다운 메뉴 내보내기** 아이콘을 누른 다음 파일 형식을 눌러서 보고서를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-142">Export the report by tapping the icon for the **Export drop down menu** and then tapping a file format.</span></span>

        -   <span data-ttu-id="149b5-143">Microsoft Surface 장치에서 보고서를 보는 경우 다음 형식 중 하나로 보고서를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-143">If you're viewing the report on a Microsoft Surface device, you can export the report to one of the following formats.</span></span>

            -   <span data-ttu-id="149b5-144">보고서 데이터를 가진 XML 파일</span><span class="sxs-lookup"><span data-stu-id="149b5-144">XML file with report data</span></span>

            -   <span data-ttu-id="149b5-145">CSV(쉼표로 분리)</span><span class="sxs-lookup"><span data-stu-id="149b5-145">CSV (comma delimited)</span></span>

            -   <span data-ttu-id="149b5-146">PDF</span><span class="sxs-lookup"><span data-stu-id="149b5-146">PDF</span></span>

            -   <span data-ttu-id="149b5-147">MHTML(웹 보관 파일)</span><span class="sxs-lookup"><span data-stu-id="149b5-147">MHTML (web archive)</span></span>

            -   <span data-ttu-id="149b5-148">Excel</span><span class="sxs-lookup"><span data-stu-id="149b5-148">Excel</span></span>

            -   <span data-ttu-id="149b5-149">TIFF</span><span class="sxs-lookup"><span data-stu-id="149b5-149">TIFF</span></span>

            -   <span data-ttu-id="149b5-150">단어</span><span class="sxs-lookup"><span data-stu-id="149b5-150">Word</span></span>

        -   <span data-ttu-id="149b5-151">IPad에서 보고서를 볼 때 보고서를 TIFF 또는 PDF 파일로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-151">If you're viewing the report on an iPad, you can export the report as a TIFF or PDF file.</span></span>

## <a name="authentication"></a><span data-ttu-id="149b5-152">인증</span><span class="sxs-lookup"><span data-stu-id="149b5-152">Authentication</span></span>
 <span data-ttu-id="149b5-153">RSWindowsNTLM 인증 및 RSWindowsBasic 인증은 기본 모드 및 iPad에서 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 와 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-153">RSWindowsNTLM authentication and RSWindowsBasic authentication work with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in native mode and the iPad.</span></span>

 <span data-ttu-id="149b5-154">일반적으로 RSWindowsBasic은 인증 유형이 전송된 자격 증명에 대한 기밀성을 제공하지 않기 때문에 https가 아닌 환경에서 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-154">In general, it is recommended that RSWindowsBasic is not used in non-https environments because this type of authentication provides no confidentiality for the transmitted credentials.</span></span>

 <span data-ttu-id="149b5-155">RSWindowsNTLM 및 RSWindowsBasic 인증에 대한 자세한 내용은 [Authentication with the Report Server](security/authentication-with-the-report-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="149b5-155">For more information about RSWindowsNTLM and RSWindowsBasic authentication, see [Authentication with the Report Server](security/authentication-with-the-report-server.md).</span></span>

## <a name="uploading-reports"></a><span data-ttu-id="149b5-156">보고서 업로드</span><span class="sxs-lookup"><span data-stu-id="149b5-156">Uploading Reports</span></span>
 <span data-ttu-id="149b5-157">적절한 권한이 있는 경우 다음 방법 중 하나를 사용하여 Microsoft Surface 디바이스에서 보고서를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-157">You can publish reports from a Microsoft Surface device using one of the following methods, if you have the appropriate permissions.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="149b5-158">이러한 방법은 iPad에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-158">These methods are not supported on the iPad.</span></span>

-   <span data-ttu-id="149b5-159">라이브러리를 열고 **문서 업로드**를 눌러 SharePoint 문서 라이브러리에 보고서 정의 파일(.rdl)을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-159">Upload a report definition file (.rdl) to a SharePoint document library by opening the library and tapping **Upload Document**.</span></span>

-   <span data-ttu-id="149b5-160">보고서 관리자를 열고 **파일 업로드**를 눌러 보고서 서버 데이터베이스에 보고서 정의 파일을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="149b5-160">Upload a report definition file to the report server database by opening Report Manager and tapping **Upload File**.</span></span>

## <a name="additional-information"></a><span data-ttu-id="149b5-161">추가 정보</span><span class="sxs-lookup"><span data-stu-id="149b5-161">Additional Information</span></span>
 <span data-ttu-id="149b5-162">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 및 지원되는 브라우저에 대한 자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="149b5-162">For more information on [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and supported browsers, see:</span></span>

-   [<span data-ttu-id="149b5-163">Reporting Services 및 파워 뷰 브라우저 지원 계획 &#40;Reporting Services 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="149b5-163">Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;</span></span>](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)

 <span data-ttu-id="149b5-164">Microsoft Business Intelligence 및 모바일 디바이스에 대한 자세한 내용을 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="149b5-164">For more information on Microsoft Business Intelligence and Mobile devices, see the following:</span></span>

-   <span data-ttu-id="149b5-165">[모바일 장치 및 SharePoint 2013 개요](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) ( https://technet.microsoft.com/library/fp161351(v=office.15).aspx) .</span><span class="sxs-lookup"><span data-stu-id="149b5-165">[Overview of mobile devices and SharePoint 2013](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161351(v=office.15).aspx).</span></span>

-   <span data-ttu-id="149b5-166">[SharePoint 2013에서 지원 되는 모바일 장치 브라우저](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) ( https://technet.microsoft.com/library/fp161353(v=office.15).aspx) .</span><span class="sxs-lookup"><span data-stu-id="149b5-166">[Supported mobile device browsers in SharePoint 2013](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161353(v=office.15).aspx).</span></span>

-   <span data-ttu-id="149b5-167">[Apple iPad 장치에서 보고서 및 성과 기록표 보기 (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) ( https://technet.microsoft.com/library/hh697482.aspx) .</span><span class="sxs-lookup"><span data-stu-id="149b5-167">[Viewing reports and scorecards on Apple iPad devices (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx).</span></span>

-   <span data-ttu-id="149b5-168">[IPad에서 Reporting Services 보고서 보기 (비디오)](https://technet.microsoft.com/sqlserver/jj873792.aspx) () https://technet.microsoft.com/sqlserver/jj873792.aspx)</span><span class="sxs-lookup"><span data-stu-id="149b5-168">[Viewing Reporting Services Reports on an iPad (video)](https://technet.microsoft.com/sqlserver/jj873792.aspx) (https://technet.microsoft.com/sqlserver/jj873792.aspx).</span></span>

-   [<span data-ttu-id="149b5-169">Microsoft Surface RT 디바이스에서 Reporting Services 보고서 보기(비디오)</span><span class="sxs-lookup"><span data-stu-id="149b5-169">Viewing Reporting Services Reports on a Microsoft Surface RT Device (video)</span></span>](https://technet.microsoft.com/sqlserver/dn146017)


