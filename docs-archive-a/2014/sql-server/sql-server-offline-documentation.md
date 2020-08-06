---
title: SQL Server 2014에 대 한 오프 라인 문서
description: SQL Server 2014에 대 한 오프 라인 설명서를 설치 하는 방법을 알아봅니다. SSMS(SQL Server Management Studio)를 사용하여 오프라인 콘텐츠를 볼 수 있습니다.
ms.prod: sql
ms.technology: install
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: markingmyname
ms.author: maghan
ms.reviewer: carlrab
ms.date: 07/19/2020
ms.openlocfilehash: bfd4adc658a203f8e2d22ef77ce0381084e36363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650369"
---
# <a name="install-sql-server-2014-offline-documentation"></a><span data-ttu-id="d1bba-104">SQL Server 2014 오프 라인 설명서 설치</span><span class="sxs-lookup"><span data-stu-id="d1bba-104">Install SQL Server 2014 offline documentation</span></span>

<span data-ttu-id="d1bba-105">이 문서에서는 오프 라인 SQL Server 2014 콘텐츠를 다운로드 하 여 보는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-105">This article describes how to download and view offline SQL Server 2014 content.</span></span> <span data-ttu-id="d1bba-106">오프라인 콘텐츠를 사용하면 인터넷에 연결되어 있지 않아도 설명서에 액세스할 수 있습니다(처음에 다운로드할 때는 인터넷 연결이 필요함).</span><span class="sxs-lookup"><span data-stu-id="d1bba-106">Offline content enables you to access the documentation without an internet connection (although an internet connection is initially required to download it).</span></span>

<span data-ttu-id="d1bba-107">이 기술은 SQL Server Management Studio (SSMS)의 **도움말** 메뉴를 사용 하 여 도움말 뷰어 유틸리티 (HlpViewer.exe)에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-107">The technique involves using the **Help** menu of SQL Server Management Studio (SSMS), to access the Help Viewer utility (HlpViewer.exe).</span></span>

<span data-ttu-id="d1bba-108">오프 라인 설명서는 2012-2019 범위의 SQL Server 버전에 사용할 수 있으며 이후 버전의 추가 버전에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-108">Offline documentation is available for versions of SQL Server in the range of 2012-2019, and perhaps for additional later versions too.</span></span> <span data-ttu-id="d1bba-109">[온라인으로 이전 버전의 콘텐츠를 볼](https://docs.microsoft.com/previous-versions/sql/) 수 있지만 오프라인 옵션을 사용하면 이전 콘텐츠에 편리하게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-109">Although you can view content for [previous versions online](https://docs.microsoft.com/previous-versions/sql/), an offline option provides a convenient way to access the older content.</span></span>

- [<span data-ttu-id="d1bba-110">SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="d1bba-110">SQL Server 2014</span></span>](#sql-server-2014-offline-content)
- [<span data-ttu-id="d1bba-111">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="d1bba-111">SQL Server 2012</span></span>](#sql-server-2012-offline-content)

<span data-ttu-id="d1bba-112">SQL Server 2016 이상 버전의 경우 해당 버전 관련 설명서를 참조 하 여 해당 버전의 오프 라인 설명서를 어떻게 처리 하는지 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="d1bba-112">For SQL Server 2016 and later versions, see their version-specific documentation to learn how those versions handle their offline documentation.</span></span>

## <a name="sql-server-2014-offline-content"></a><span data-ttu-id="d1bba-113">SQL Server 2014 오프라인 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="d1bba-113">SQL Server 2014 offline content</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1bba-114">SQL 2014 Transact-SQL 콘텐츠는 오프라인에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-114">SQL 2014 Transact-SQL content is only available offline.</span></span>

<span data-ttu-id="d1bba-115">다음 단계에서는 SQL Server 2014에 대한 오프라인 콘텐츠를 로드하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-115">The following steps explain how to load offline content for SQL Server 2014.</span></span>

1. <span data-ttu-id="d1bba-116">다운로드 센터에서 [방화벽 및 프록시로 제한된 환경의 Microsoft SQL Server 2014 제품 설명서](https://www.microsoft.com/download/details.aspx?id=42557)를 다운로드하여 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-116">Download the [Product Documentation for Microsoft SQL Server 2014 for firewall and proxy restricted environments](https://www.microsoft.com/download/details.aspx?id=42557) content from the download center and save it to a folder.</span></span>

2. <span data-ttu-id="d1bba-117">파일의 압축을 풀어 *. msha* 파일을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-117">Unzip the file to view the *.msha* file.</span></span>

   ![SQL Server 2014 도움말 설명서 설치 파일](../sql-server/media/sql-server-offline-documentation/sql-2014-help-content-setup-msha.png)

3. <span data-ttu-id="d1bba-119">SSMS의 도움말 메뉴에서 **도움말 콘텐츠 추가 및 제거**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-119">In SSMS, select **Add and Remove Help Content** on the Help menu.</span></span>

   ![도움말 뷰어 콘텐츠 추가 제거](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   <span data-ttu-id="d1bba-121">도움말 뷰어에서 콘텐츠 관리 탭이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-121">The Help Viewer opens to the Manage Content tab.</span></span>

4. <span data-ttu-id="d1bba-122">최신 도움말 콘텐츠를 설치하려면 설치 원본에서 **디스크**를 선택한 다음 줄임표(...)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-122">To install the latest help content, choose **Disk** under Installation source and then the ellipses (...).</span></span>

   ![도움말 뷰어 콘텐츠 관리 디스크 원본](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > <span data-ttu-id="d1bba-124">콘텐츠 관리 탭의 로컬 저장소 경로는 로컬 컴퓨터에서 콘텐츠가 설치된 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-124">The Local store path on the Manage Content tab shows where on the local computer the content is located.</span></span> <span data-ttu-id="d1bba-125">이 위치를 변경하려면 **이동**을 선택하고 **대상** 필드에 다른 폴더 경로를 입력한 다음, **확인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-125">To change the location, select **Move**, enter a different folder path in the **To** field, and then select **OK**.</span></span>
   <span data-ttu-id="d1bba-126">로컬 저장소 경로를 변경한 후 도움말 설치에 실패하면 도움말 뷰어를 닫았다가 다시 여세요.</span><span class="sxs-lookup"><span data-stu-id="d1bba-126">If the help installation fails after changing the Local store path, close and reopen the Help Viewer.</span></span> <span data-ttu-id="d1bba-127">로컬 저장소 경로에 새 경로가 보이는지 확인한 후 다시 설치해보세요.</span><span class="sxs-lookup"><span data-stu-id="d1bba-127">Ensure the new location appears in the Local store path and then try the installation again.</span></span>

5. <span data-ttu-id="d1bba-128">콘텐츠의 압축을 푼 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-128">Locate the folder where you unzipped the content.</span></span> <span data-ttu-id="d1bba-129">폴더에서 **HelpContentSetup.msha** 파일을 선택한 다음 **열기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-129">Select the **HelpContentSetup.msha** file in the folder then select **Open**.</span></span>

   ![SQL Server 2014 Help Content Setup.msha 파일 열기](../sql-server/media/sql-server-offline-documentation/sql-2014-open-msha.png)

6. <span data-ttu-id="d1bba-131">검색 창에 *sql server 2014*를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-131">Type in *sql server 2014* in the search bar.</span></span> <span data-ttu-id="d1bba-132">2014 콘텐츠가 사용 가능하다고 표시되면 도움말 뷰어에 설치하려는 각 콘텐츠 패키지(책) 옆의 **추가**를 선택한 다음 **업데이트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-132">Once you see the 2014 content available, select **Add** next to each content package (book) that you want to install to Help Viewer and then select **Update**.</span></span>

   ![도움말 뷰어에서 SQL Server 2014 책 검색](../sql-server/media/sql-server-offline-documentation/sql-2014-search.png)

   ![도움말 뷰어에서 SQL Server 2014 책 추가 및 업데이트](../sql-server/media/sql-server-offline-documentation/sql-2014-add-update.png)

    > [!NOTE]
    > <span data-ttu-id="d1bba-135">콘텐츠를 추가 하는 동안 도움말 뷰어가 고정 (중지) 하는 경우 \<mm/dd/yyyy> %localappdata%\microsoft\helpviewer2.x\ HlpViewer_SSMSx_en-us. 설정 또는 HlpViewer_VisualStudiox_en-us. 설정 파일의 캐시 LastRefreshed 고침 = "00:00:00" 줄을 나중에 날짜로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-135">If the Help Viewer freezes (hangs) while adding content, change the Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" line in the %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings file to some date in the future.</span></span> <span data-ttu-id="d1bba-136">이 문제에 대한 자세한 내용은 [Visual Studio 도움말 뷰어가 중단됨](/visualstudio/welcome-to-visual-studio)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1bba-136">For more information about this issue, see [Visual Studio Help Viewer freezes](/visualstudio/welcome-to-visual-studio).</span></span>

7. <span data-ttu-id="d1bba-137">왼쪽에 있는 콘텐츠 창에서 *sql server 2014*를 검색하여 SQL Server 2014 콘텐츠가 로드되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-137">You can verify that the SQL Server 2014 content installed by searching under the content pane on the left for *sql server 2014*.</span></span>

   ![SQL Server 2014 책이 자동으로 업데이트됨](../sql-server/media/sql-server-offline-documentation/sql-2014-content.png)

## <a name="sql-server-2012-offline-content"></a><span data-ttu-id="d1bba-139">SQL Server 2012 오프라인 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="d1bba-139">SQL Server 2012 offline content</span></span>

<span data-ttu-id="d1bba-140">다음 단계에서는 SQL Server 2012에 대한 오프라인 콘텐츠를 로드하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-140">The following steps explain how to load offline content for SQL Server 2012</span></span>

1. <span data-ttu-id="d1bba-141">다운로드 센터에서 [방화벽 및 프록시로 제한된 환경의 Microsoft SQL Server 2012 제품 설명서](https://www.microsoft.com/download/details.aspx?id=35750)를 다운로드하여 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-141">Download the [Product Documentation for Microsoft SQL Server 2012 for firewall and proxy restricted environments](https://www.microsoft.com/download/details.aspx?id=35750) content from the download center and save it to a folder.</span></span>

2. <span data-ttu-id="d1bba-142">파일의 압축을 풀어 *. msha* 파일을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-142">Unzip the file to view the *.msha* file.</span></span>

   ![SQL Server 2012 도움말 콘텐츠 설치 파일](../sql-server/media/sql-server-offline-documentation/sql-2012-help-content-setup-msha.png)

3. <span data-ttu-id="d1bba-144">SSMS의 도움말 메뉴에서 **도움말 콘텐츠 추가 및 제거**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-144">In SSMS, select **Add and Remove Help Content** on the Help menu.</span></span>

   ![도움말 뷰어 콘텐츠 추가 제거](../sql-server/media/sql-server-offline-documentation/add-remove-content.png)

   <span data-ttu-id="d1bba-146">도움말 뷰어에서 콘텐츠 관리 탭이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-146">The Help Viewer opens to the Manage Content tab.</span></span>

4. <span data-ttu-id="d1bba-147">최신 도움말 콘텐츠를 설치하려면 설치 원본에서 **디스크**를 선택한 다음 줄임표(...)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-147">To install the latest help content, choose **Disk** under Installation source and then the ellipses (...).</span></span>

   ![도움말 뷰어 콘텐츠 관리 디스크 원본](../sql-server/media/sql-server-offline-documentation/install-source-disk.png)

   > [!NOTE]
   > <span data-ttu-id="d1bba-149">콘텐츠 관리 탭의 로컬 저장소 경로는 로컬 컴퓨터에서 콘텐츠가 설치된 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-149">The Local store path on the Manage Content tab shows where on the local computer the content is located.</span></span> <span data-ttu-id="d1bba-150">이 위치를 변경하려면 **이동**을 선택하고 **대상** 필드에 다른 폴더 경로를 입력한 다음, **확인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-150">To change the location, select **Move**, enter a different folder path in the **To** field, and then select **OK**.</span></span>
   <span data-ttu-id="d1bba-151">로컬 저장소 경로를 변경한 후 도움말 설치에 실패하면 도움말 뷰어를 닫았다가 다시 여세요.</span><span class="sxs-lookup"><span data-stu-id="d1bba-151">If the help installation fails after changing the Local store path, close and reopen the Help Viewer.</span></span> <span data-ttu-id="d1bba-152">로컬 저장소 경로에 새 경로가 보이는지 확인한 후 다시 설치해보세요.</span><span class="sxs-lookup"><span data-stu-id="d1bba-152">Ensure the new location appears in the Local store path and then try the installation again.</span></span>

5. <span data-ttu-id="d1bba-153">콘텐츠의 압축을 푼 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-153">Locate the folder where you unzipped the content.</span></span> <span data-ttu-id="d1bba-154">폴더에서 **HelpContentSetup.msha** 파일을 선택한 다음 **열기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-154">Select the **HelpContentSetup.msha** file in the folder then select **Open**.</span></span>

   ![SQL Server 2012 Help Content Setup.msha 파일 열기](../sql-server/media/sql-server-offline-documentation/sql-2012-open-msha.png)

6. <span data-ttu-id="d1bba-156">검색 창에 *sql server 2012*를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-156">Type in *sql server 2012* in the search bar.</span></span> <span data-ttu-id="d1bba-157">2012 콘텐츠가 사용 가능하다고 표시되면 도움말 뷰어에 설치하려는 각 콘텐츠 패키지(책) 옆의 **추가**를 선택한 다음 **업데이트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-157">Once you see the 2012 content available, select **Add** next to each content package (book) that you want to install to Help Viewer and then select **Update**.</span></span>

   ![도움말 뷰어에서 SQL Server 2012 책 검색](../sql-server/media/sql-server-offline-documentation/sql-2012-search.png)

   ![도움말 뷰어에서 SQL Server 2012 책 추가 및 업데이트](../sql-server/media/sql-server-offline-documentation/sql-2012-add-update.png)

    > [!NOTE]
    > <span data-ttu-id="d1bba-160">콘텐츠를 추가 하는 동안 도움말 뷰어가 고정 (중지) 하는 경우 \<mm/dd/yyyy> %localappdata%\microsoft\helpviewer2.x\ HlpViewer_SSMSx_en-us. 설정 또는 HlpViewer_VisualStudiox_en-us. 설정 파일의 캐시 LastRefreshed 고침 = "00:00:00" 줄을 나중에 날짜로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-160">If the Help Viewer freezes (hangs) while adding content, change the Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" line in the %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings or HlpViewer_VisualStudiox_en-US.settings file to some date in the future.</span></span> <span data-ttu-id="d1bba-161">이 문제에 대한 자세한 내용은 [Visual Studio 도움말 뷰어가 중단됨](/visualstudio/welcome-to-visual-studio)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1bba-161">For more information about this issue, see [Visual Studio Help Viewer freezes](/visualstudio/welcome-to-visual-studio).</span></span>

7. <span data-ttu-id="d1bba-162">왼쪽에 있는 콘텐츠 창에서 *sql server 2012*을 검색하여 SQL Server 2012 콘텐츠가 로드되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-162">You can verify that the SQL Server 2012 content is loaded by searching under the content pane on the left for *sql server 2012*.</span></span>

   ![SQL Server 2012 설명서가 자동으로 업데이트됨](../sql-server/media/sql-server-offline-documentation/sql-2012-content.png)

## <a name="view-offline-documentation"></a><span data-ttu-id="d1bba-164">오프라인 설명서 보기</span><span class="sxs-lookup"><span data-stu-id="d1bba-164">View offline documentation</span></span>

<span data-ttu-id="d1bba-165">최신 버전의 SSMS (SQL Server Management Studio)에서 **도움말** 메뉴를 사용 하 여 SQL Server 도움말 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-165">You can view SQL Server help content using the **HELP** menu in the latest version of SQL Server Management Studio (SSMS).</span></span>

### <a name="view-offline-help-content-in-ssms"></a><span data-ttu-id="d1bba-166">SSMS에서 오프라인 도움말 콘텐츠 보기</span><span class="sxs-lookup"><span data-stu-id="d1bba-166">View offline help content in SSMS</span></span>

<span data-ttu-id="d1bba-167">SSMS에서 설치된 도움말을 보려면 도움말 메뉴에서 **도움말 뷰어에서 시작**을 선택하여 도움말 뷰어를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-167">To view the installed help in SSMS, select **Launch in Help Viewer** from the Help menu, to launch the Help Viewer.</span></span>

   ![도움말 뷰어에서 시작](../sql-server/media/sql-server-offline-documentation/helpviewer-view-offline.png)  

<span data-ttu-id="d1bba-169">도움말 뷰어에서 콘텐츠 관리 탭이 열리고, 왼쪽 창에 설치된 도움말 목차가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-169">Help Viewer opens to the Manage Content tab, with the installed help table of contents in the left pane.</span></span> <span data-ttu-id="d1bba-170">목차에서 항목을 선택하면 오른쪽 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-170">select articles in the table of contents to display them in the right pane.</span></span>

> [!Important]
> <span data-ttu-id="d1bba-171">콘텐츠 창이 표시되지 않으면 왼쪽 여백에서 콘텐츠를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-171">If the contents pane is not visible, select Contents on the left margin.</span></span> <span data-ttu-id="d1bba-172">압정 아이콘을 선택하면 콘텐츠 창이 계속 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bba-172">select the pushpin icon to keep the contents pane open.</span></span>  

   ![콘텐츠가 포함된 도움말 뷰어](../sql-server/media/sql-server-offline-documentation/view-offline-all.png)
