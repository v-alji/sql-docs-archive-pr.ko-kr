---
title: 브라우저를 사용하여 보고서 찾기 및 보기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: edf4843a-2a0a-486f-be25-14a3c1c6bc72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b864188fc5152a11ad66ac9cd986891b88849a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739447"
---
# <a name="finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs"></a><span data-ttu-id="74e4b-102">브라우저를 사용하여 보고서 찾기 및 보기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="74e4b-102">Finding and Viewing Reports with a Browser (Report Builder and SSRS)</span></span>
  <span data-ttu-id="74e4b-103">지원되는 웹 브라우저에서 보고서 서버에 직접 연결하여 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-103">You can use any supported Web browser to view a report through a direct connection to a report server.</span></span> <span data-ttu-id="74e4b-104">모든 보고서에는 보고서 서버에 대한 URL 주소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-104">Every report has a URL address on a report server.</span></span> <span data-ttu-id="74e4b-105">보고서의 웹 주소를 입력하여 웹 애플리케이션과는 상관없이 브라우저 창에 보고서를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-105">You can enter the Web address of a report to open it in a browser window independently of a Web application.</span></span> <span data-ttu-id="74e4b-106">보고서는 HTML 형식으로 열리고 페이지를 탐색하거나 보고서 내의 데이터 값을 검색하는 데 사용할 수 있는 보고서 도구 모음이 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-106">The report opens in HTML format and includes the report toolbar so that you can navigate pages or search on data values within the report.</span></span> <span data-ttu-id="74e4b-107">URL에 매개 변수를 설정하여 도구 모음을 숨기거나 보고서의 출력 형식을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-107">You can set parameters on the URL to hide the toolbar or select the output format of the report.</span></span>  
  
 <span data-ttu-id="74e4b-108">해당 웹 주소를 통해 보고서를 여는 방법은 보고서를 보는 데 적합하지만 보고서를 관리하는 데는 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-108">Opening a report through its Web address is suitable for viewing a report, but not managing a report.</span></span> <span data-ttu-id="74e4b-109">이 경우 항목의 속성 페이지나 구독 정의 페이지에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-109">You cannot access an item's property pages or subscription definition pages.</span></span> <span data-ttu-id="74e4b-110">이러한 태스크에는 보고서 관리자나 SharePoint 사이트를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-110">You must use Report Manager or a SharePoint site for those tasks.</span></span>  
  
 <span data-ttu-id="74e4b-111">보고서의 웹 주소를 모르는 경우 보고서 서버의 웹 주소를 연 다음 보고서 서버의 폴더 계층 구조를 탐색하여 원하는 보고서를 선택하고 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-111">If you do not know the Web address of a report, you can open the Web address of the report server and then browse the report server folder hierarchy to select the report you want to view.</span></span> <span data-ttu-id="74e4b-112">다음 다이어그램에서는 브라우저 창에 표시되는 폴더 계층을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-112">The following diagram illustrates a folder hierarchy as it appears in a browser window.</span></span>  
  
 <span data-ttu-id="74e4b-113">![브라우저의 폴더](../media/rs-browserfolder.GIF "브라우저의 폴더")</span><span class="sxs-lookup"><span data-stu-id="74e4b-113">![Folders in a browser](../media/rs-browserfolder.GIF "Folders in a browser")</span></span>  
<span data-ttu-id="74e4b-114">브라우저의 폴더</span><span class="sxs-lookup"><span data-stu-id="74e4b-114">Folders in a browser</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74e4b-115">핸드헬드 디바이스에서 보고서에 액세스할 경우 브라우저를 사용하여 보고서를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-115">If you are accessing a report from a handheld device, you must use a browser to open a report.</span></span> <span data-ttu-id="74e4b-116">보고서 관리자는 핸드헬드 디바이스에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-116">Report Manager is not scaled for handheld devices.</span></span>  
  
 <span data-ttu-id="74e4b-117">사용할 수 있는 브라우저 종류에 대한 자세한 내용은 SQL Server 온라인 설명서의 [Reporting Services 설명서](https://go.microsoft.com/fwlink/?linkid=121312) 에 있는 "Reporting Services에서 지원하는 브라우저 종류(Browser Types Supported by Reporting Services)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="74e4b-117">For more information about types of browsers that you can use, see "Browser Types Supported by Reporting Services" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="navigating-report-server-folders-in-a-web-browser"></a><span data-ttu-id="74e4b-118">웹 브라우저에서 보고서 서버 폴더 탐색</span><span class="sxs-lookup"><span data-stu-id="74e4b-118">Navigating Report Server Folders in a Web Browser</span></span>  
 <span data-ttu-id="74e4b-119">웹 브라우저를 사용하여 보고서 서버 폴더를 탐색하고 보고서를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-119">You can use a Web browser to navigate report server folders and run reports.</span></span> <span data-ttu-id="74e4b-120">보고서와 항목은 폴더 계층에서 링크로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-120">Reports and items are displayed as links in the folder hierarchy.</span></span> <span data-ttu-id="74e4b-121">링크를 클릭하여 보고서, 리소스 또는 폴더를 열거나 공유 데이터 원본의 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-121">You can click links to open a report, resource, or folder, or view the contents of a shared data source.</span></span> <span data-ttu-id="74e4b-122">폴더 계층 탐색은 보고서의 URL을 모르는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-122">Navigating the folder hierarchy is useful if you do not know the URL of a report.</span></span> <span data-ttu-id="74e4b-123">보고서 서버 웹 주소를 지정하여 폴더 계층 구조의 루트 노드에서 브라우저 연결을 연 다음 폴더 링크를 클릭하여 계층 구조를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-123">You can specify the report server Web address to open a browser connection at the root node of the folder hierarchy, and then click folder links to navigate through the hierarchy.</span></span>  
  
 <span data-ttu-id="74e4b-124">보고서 서버 가상 디렉터리에 액세스하면 사용자가 액세스할 수 있는 폴더, 보고서 및 업로드된 항목만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-124">When you access a report server virtual directory, you see only the folders, reports, and uploaded items to which you have access.</span></span> <span data-ttu-id="74e4b-125">사용자 인터페이스에는 폴더 계층과 기본 정보만 표시됩니다. 기본 정보의 예에는 만든 날짜, 수정한 날짜, 파일 크기 및 개별 항목의 항목 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-125">The user interface shows only the folder hierarchy and basic information, such as creation or modification date, file size, and item type for individual items:</span></span>  
  
-   <span data-ttu-id="74e4b-126">별도의 표시가 없는 링크는 보고서나 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-126">A link with no other indicator is a report or a model.</span></span>  
  
-   <span data-ttu-id="74e4b-127">태그는 \<ds> 공유 데이터 원본을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-127">The tag \<ds> indicates a shared data source.</span></span>  
  
-   <span data-ttu-id="74e4b-128">태그는 \<dir> 폴더 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-128">The tag \<dir> indicates a folder item.</span></span>  
  
-   <span data-ttu-id="74e4b-129">파일 이름 확장명은 리소스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-129">A file name extension indicates a resource.</span></span> <span data-ttu-id="74e4b-130">파일 이름 확장명은 리소스의 MIME 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-130">The file name extension identifies the MIME type of the resource.</span></span> <span data-ttu-id="74e4b-131">예를 들어 .jpg는 JPEG 형식의 이미지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-131">For example, .jpg indicates an image in JPEG format.</span></span>  
  
## <a name="typing-the-url-address-of-a-report"></a><span data-ttu-id="74e4b-132">보고서의 URL 주소 입력</span><span class="sxs-lookup"><span data-stu-id="74e4b-132">Typing the URL Address of a Report</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="74e4b-133">에서는 보고서 서버의 특정 항목에 대한 URL 액세스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-133">supports URL access to specific items on a report server.</span></span> <span data-ttu-id="74e4b-134">이 URL에는 보고서의 정규화된 경로와 보고서를 렌더링하기 위한 명령이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-134">The URL must include a fully qualified path to the report and commands to render the report.</span></span> <span data-ttu-id="74e4b-135">보고서에 매개 변수가 포함되어 있으면 보고서를 여는 데 필요한 값도 모두 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-135">If the report includes parameters, you must also specify any values that are required to open the report.</span></span> <span data-ttu-id="74e4b-136">경로, 매개 변수 값 또는 렌더링 확장 프로그램에 공백이 포함된 보고서의 URL을 입력할 경우 원하는 결과를 얻으려면 URL 인코딩된 문자를 URL에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-136">If you are typing a URL for a report that includes spaces in the path, parameter values, or a rendering extension, you must incorporate URL encoded characters into the URL to get the results you expect.</span></span> <span data-ttu-id="74e4b-137">다음 예에서는 경로 이름, 매개 변수 및 렌더링 확장 프로그램에 공백에 대한 인코딩을 포함하는 보고서 URL을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-137">The following example illustrates a report URL that includes encoding for spaces in the path name, parameters, and a rendering extension:</span></span>  
  
 `http://<Webservername>/reportserver?/<reportfolder>/employee+sales+summary&ReportYear=2004&ReportMonth=06&EmpID=24&rs:Command=Render&rs:Format=HTML4.0`  
  
 <span data-ttu-id="74e4b-138">Internet Explorer에서 URL에 사용할 수 있는 문자는 최대 2,083자까지입니다.</span><span class="sxs-lookup"><span data-stu-id="74e4b-138">The maximum limit for a URL in Internet Explorer is 2,083 characters.</span></span> <span data-ttu-id="74e4b-139">자세한 내용은 [Internet Explorer의 최대 URL 길이(Maximum URL length in Internet Explorer)](https://support.microsoft.com/kb/208427)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="74e4b-139">For more information, see [Maximum URL length in Internet Explorer](https://support.microsoft.com/kb/208427).</span></span>  
  
 <span data-ttu-id="74e4b-140">URL을 통해 보고서에 액세스하는 방법은 SQL Server 온라인 설명서의 [Reporting Services 설명서](https://go.microsoft.com/fwlink/?linkid=121312) 에 있는 "URL 액세스(URL Access)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="74e4b-140">For more information about how to access a report through a URL, including information on how a URL is constructed, see "URL Access" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e4b-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74e4b-141">See Also</span></span>  
 [<span data-ttu-id="74e4b-142">보고서 관리자에서 보고서 찾기 및 보기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="74e4b-142">Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;</span></span>](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)  
  
  
