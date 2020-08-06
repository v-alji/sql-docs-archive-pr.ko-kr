---
title: SharePoint용 PowerPivot 설치 확인 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 855bd055-5ad3-493f-9c5b-1f5297b2e6e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f45e1aa1d48dd5a50b7ce38dc364089d438f215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653042"
---
# <a name="verify-a-powerpivot-for-sharepoint-installation"></a><span data-ttu-id="efc29-102">SharePoint용 PowerPivot 설치 확인</span><span class="sxs-lookup"><span data-stu-id="efc29-102">Verify a PowerPivot for SharePoint Installation</span></span>
  <span data-ttu-id="efc29-103">SharePoint 팜에 설치하는 SharePoint용 PowerPivot 인스턴스는 SharePoint 중앙 관리를 통해 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-103">A PowerPivot for SharePoint instance that you install in a SharePoint farm is administered through SharePoint Central Administration.</span></span> <span data-ttu-id="efc29-104">최소한 중앙 관리와 SharePoint 사이트에서 페이지를 검사하여 PowerPivot 서버 구성 요소 및 기능이 사용 가능한지를 확인할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-104">At a minimum, you can check pages in Central Administration and on SharePoint sites to verify that PowerPivot server components and features are available.</span></span> <span data-ttu-id="efc29-105">그러나 설치를 전체적으로 확인하려면 SharePoint에 게시하여 라이브러리에서 액세스할 수 있는 PowerPivot 통합 문서가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-105">However, to fully verify an installation, you must have a PowerPivot workbook that you can publish to SharePoint and access from a library.</span></span> <span data-ttu-id="efc29-106">테스트를 위해 이미 PowerPivot 데이터가 포함된 예제 통합 문서를 게시하여 SharePoint 통합이 올바르게 구성되어 있는지 확인하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-106">For testing purposes, you can publish a sample workbook that already contains PowerPivot data and use it to confirm that SharePoint integration is correctly configured.</span></span>  
  
##  <a name="verify-central-administration-integration"></a><a name="verifyinstall"></a> <span data-ttu-id="efc29-107">중앙 관리 통합을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="efc29-107">Verify Central Administration Integration</span></span>  
 <span data-ttu-id="efc29-108">중앙 관리와 PowerPivot의 통합을 확인하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="efc29-108">To verify PowerPivot integration with Central Administration, do the following:</span></span>  
  
1.  <span data-ttu-id="efc29-109">시작 메뉴에서 **모든 프로그램**을 클릭 하 고 Microsoft Sharepoint 2010 제품을 연 다음 **Sharepoint 2010 중앙 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-109">On the Start menu, click **All Programs**, open Microsoft SharePoint 2010 Products, and click **SharePoint 2010 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="efc29-110">사용자 이름과 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-110">Enter your user name and password, and then click **OK**.</span></span>  
  
     <span data-ttu-id="efc29-111">원하는 경우 중앙 관리를 열 때마다 사용자 이름 및 암호를 입력하지 않아도 되도록 브라우저 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-111">Optionally, you can modify browser settings to avoid having to enter a user name and password each time you open Central Administration.</span></span> <span data-ttu-id="efc29-112">중앙 관리를 신뢰할 수 있는 사이트로 추가하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="efc29-112">To add Central Administration as a trusted site, do the following.</span></span>  
  
    1.  <span data-ttu-id="efc29-113">Internet Explorer의 도구 메뉴에서 **인터넷 옵션**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-113">In Internet Explorer, on the Tools menu, click **Internet options**.</span></span>  
  
    2.  <span data-ttu-id="efc29-114">보안 탭의 **보안 설정을 보거나 변경할 영역을 선택하십시오.** 섹션에서 신뢰할 수 있는 사이트를 클릭하고 사이트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-114">On the Security tab, in the **Select a zone to view or change security settings** section, click Trusted Sites, and then click Sites.</span></span>  
  
    3.  <span data-ttu-id="efc29-115">**이 영역에 있는 모든 사이트에 대해 서버 확인(https:)을 요청** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-115">Clear the **Require server verification (https:) for all sites in this zone** checkbox.</span></span>  
  
    4.  <span data-ttu-id="efc29-116">**영역에 웹 사이트 추가**에 사이트 URL을 입력하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-116">In **Add this Web site to the zone**, type the URL to your site, and then click **Add**.</span></span>  
  
    5.  <span data-ttu-id="efc29-117">**닫기**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-117">Click **Close**, and then click **OK**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="efc29-118">SharePoint 설치 설명서에는 프록시 서버 오류를 해결하고 업데이트를 다운로드 및 설치할 수 있도록 Internet Explorer의 강화된 보안 구성을 해제하기 위한 추가 지침이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-118">SharePoint installation documentation includes additional instructions for working around proxy server errors and for disabling Internet Explorer Enhanced Security Configuration so that you can download and install updates.</span></span> <span data-ttu-id="efc29-119">자세한 내용은 Microsoft 웹 사이트의 **SQL Server와 함께 단일 서버 배포** 에서 [추가 태스크 수행](https://go.microsoft.com/fwlink/?LinkId=177754) 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="efc29-119">For more information, see the **Perform additional tasks** section in [Deploy a single server with SQL Server](https://go.microsoft.com/fwlink/?LinkId=177754) on the Microsoft web site.</span></span>  
  
3.  <span data-ttu-id="efc29-120">중앙 관리의 시스템 설정에서 **팜 기능 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-120">In Central Administration, in System Settings, click **Manage farm features**.</span></span>  
  
4.  <span data-ttu-id="efc29-121">**PowerPivot 통합 기능** 이 **활성**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-121">Verify that **PowerPivot Integration Feature** is **Active**.</span></span>  
  
5.  <span data-ttu-id="efc29-122">중앙 관리의 시스템 설정에서 **서버의 서비스 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-122">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
6.  <span data-ttu-id="efc29-123">**SQL Server Analysis Services** 및 **SQL Server PowerPivot 시스템 서비스** 가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-123">Verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** are started.</span></span>  
  
7.  <span data-ttu-id="efc29-124">중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-124">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
8.  <span data-ttu-id="efc29-125">**기본 Powerpivot 서비스 응용 프로그램** 을 클릭 하 여이 응용 프로그램에 대 한 Powerpivot 관리 대시보드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-125">Click **Default PowerPivot Service Application** to open PowerPivot Management Dashboard for this application.</span></span> <span data-ttu-id="efc29-126">처음 사용하는 경우 대시보드는 로드하는 데 몇 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-126">On first use, the dashboard takes several minutes to load.</span></span>  
  
     <span data-ttu-id="efc29-127">또는 **기본 PowerPivot 서비스 응용 프로그램** 옆의 빈 공간을 클릭 하 여 행을 선택 하 고 **속성** 을 클릭 하 여이 서비스 응용 프로그램의 구성 설정을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-127">Alternatively, click the empty space next to **Default PowerPivot Service Application** to select the row, and click **Properties** to view the configuration settings for this service application.</span></span> <span data-ttu-id="efc29-128">구성 설정과 애플리케이션 속성을 모두 수정하여 서버 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-128">You can modify both configuration settings and application properties to change your server configuration.</span></span> <span data-ttu-id="efc29-129">이러한 설정에 대 한 자세한 내용은 [중앙 관리에서 PowerPivot 서비스 응용 프로그램 만들기 및 구성](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="efc29-129">For more information about these settings, see [Create and Configure a PowerPivot Service Application in Central Administration](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).</span></span>  
  
## <a name="verify-integration-at-the-site-level"></a><span data-ttu-id="efc29-130">사이트 수준에서 통합 확인</span><span class="sxs-lookup"><span data-stu-id="efc29-130">Verify Integration at the Site Level</span></span>  
 <span data-ttu-id="efc29-131">SharePoint 사이트와 PowerPivot의 통합을 확인하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="efc29-131">To verify PowerPivot integration with a SharePoint site, do the following:</span></span>  
  
1.  <span data-ttu-id="efc29-132">앞서 만든 웹 애플리케이션을 브라우저에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-132">In a browser, open the Web application you created.</span></span> <span data-ttu-id="efc29-133">기본값을 사용한 경우 URL 주소에 http://를 지정할 수 있습니다 \<your computer name> .</span><span class="sxs-lookup"><span data-stu-id="efc29-133">If you used default values, you can specify http://\<your computer name> in the URL address.</span></span>  
  
2.  <span data-ttu-id="efc29-134">PowerPivot 데이터 액세스 및 처리 기능을 애플리케이션에서 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-134">Verify that PowerPivot data access and processing features are available in the application.</span></span> <span data-ttu-id="efc29-135">이렇게 하려면 PowerPivot 제공 라이브러리 템플릿이 있는지 확인하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-135">You can do this by verifying the presence of PowerPivot-provided library templates:</span></span>  
  
    1.  <span data-ttu-id="efc29-136">사이트 작업에서 **기타 옵션...** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-136">On Site Actions, click **More Options..**.</span></span>  
  
    2.  <span data-ttu-id="efc29-137">라이브러리에 **데이터 피드 라이브러리** 와 **PowerPivot 갤러리**가 모두 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-137">In Libraries, you should see **Data Feed Library** and **PowerPivot Gallery**.</span></span> <span data-ttu-id="efc29-138">이러한 라이브러리 템플릿은 PowerPivot 기능에서 제공하는 것이며 기능이 올바르게 통합되는 경우 라이브러리 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-138">These library templates are provided by the PowerPivot feature and will be visible in the Libraries list if the feature is integrated correctly.</span></span>  
  
## <a name="verify-data-access-on-the-server"></a><span data-ttu-id="efc29-139">서버의 데이터 액세스 확인</span><span class="sxs-lookup"><span data-stu-id="efc29-139">Verify Data Access on the Server</span></span>  
 <span data-ttu-id="efc29-140">서버에서 PowerPivot 데이터 액세스를 확인하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="efc29-140">To verify PowerPivot data access on the server, do the following:</span></span>  
  
1.  <span data-ttu-id="efc29-141">Reporting Services 자습서와 함께 제공되는 Picnic 데이터 예제를[다운로드](https://go.microsoft.com/fwlink/?LinkID=219108) 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-141">[Download](https://go.microsoft.com/fwlink/?LinkID=219108) the Picnic data sample that accompanies a Reporting Services tutorial.</span></span> <span data-ttu-id="efc29-142">이 다운로드에 포함된 예제 통합 문서를 사용하여 PowerPivot 데이터 액세스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-142">You will use the sample workbook in this download to verify PowerPivot data access.</span></span> <span data-ttu-id="efc29-143">파일의 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-143">Extract the files.</span></span>  
  
2.  <span data-ttu-id="efc29-144">Excel 통합 문서(.xlsx)를 공유 문서로 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-144">Upload the Excel workbook (.xlsx) to Shared Documents.</span></span> <span data-ttu-id="efc29-145">통합 문서에는 포함된 PowerPivot 데이터가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-145">The workbook contains embedded PowerPivot data.</span></span>  
  
3.  <span data-ttu-id="efc29-146">문서를 클릭하여 라이브러리에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-146">Click on the document to open it from the library.</span></span>  
  
4.  <span data-ttu-id="efc29-147">통합 문서의 맨 위에서 슬라이서 또는 필터를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-147">Click on a slicer or filter at the top of the workbook.</span></span> <span data-ttu-id="efc29-148">이 통합 문서에서는 월, 색 및 형식이 슬라이서입니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-148">Month, color, and type are slicers in this workbook.</span></span> <span data-ttu-id="efc29-149">슬라이서를 클릭하면 PowerPivot 쿼리가 시작되어 서버가 작동 중인지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-149">Clicking a slicer starts a PowerPivot query and proves that your server is operational.</span></span> <span data-ttu-id="efc29-150">서버에서 PowerPivot 데이터가 백그라운드로 로드되고 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-150">The server will load PowerPivot data in the background and return the results.</span></span>  
  
5.  <span data-ttu-id="efc29-151">라이브러리로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-151">Go back to the library.</span></span> <span data-ttu-id="efc29-152">통합 문서 오른쪽의 아래쪽 화살표를 선택한 다음 **Power View 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-152">Select the down arrow to the right of the workbook, and then click **Launch Power View**.</span></span> <span data-ttu-id="efc29-153">이 단계에서는 Reporting Services의 [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] 기능이 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-153">This step confirms that the [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] feature in Reporting Services is operational.</span></span> <span data-ttu-id="efc29-154">Reporting Services를 설치하지 않은 경우에는 이 단계를 건너뛰십시오.</span><span class="sxs-lookup"><span data-stu-id="efc29-154">If you did not install Reporting Services, skip this step.</span></span>  
  
     <span data-ttu-id="efc29-155">다음 단계에서는 Management Studio의 서버에 연결하여 데이터가 로드되고 캐시되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-155">In the next step, you will connect to the server in Management Studio to verify the data is loaded and cached.</span></span>  
  
6.  <span data-ttu-id="efc29-156">시작 메뉴의 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 프로그램 그룹에서 SQL Server Management Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-156">Start SQL Server Management Studio from the [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] program group in the Start menu.</span></span> <span data-ttu-id="efc29-157">이 도구가 서버에 설치되어 있지 않으면 마지막 단계로 건너뛰어 캐시된 파일이 있는지 확인하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-157">If this tool is not installed on your server, you can skip ahead to the last step to confirm the presence of cached files.</span></span>  
  
7.  <span data-ttu-id="efc29-158">서버 유형에서 **Analysis Services**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-158">In Server Type, select **Analysis Services**.</span></span>  
  
8.  <span data-ttu-id="efc29-159">서버 이름에 \*\* \<server-name> \powerpivot)\*\* 을 입력 **\<server-name>** 합니다. 여기서은 SharePoint용 PowerPivot 설치 된 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-159">In Server Name, enter **\<server-name>\powerpivot**, where **\<server-name>** is the name of the computer that has the PowerPivot for SharePoint installation.</span></span>  
  
9. <span data-ttu-id="efc29-160">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-160">Click **Connect**.</span></span> <span data-ttu-id="efc29-161">Analysis Services 서버를 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-161">This verifies that the Analysis Services server is available.</span></span>  
  
10. <span data-ttu-id="efc29-162">개체 탐색기에서 **데이터베이스** 를 클릭 하 여 로드 된 PowerPivot 데이터 파일 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-162">In Object Explorer, you can click **Databases** to view the list of PowerPivot data files that are loaded.</span></span>  
  
11. <span data-ttu-id="efc29-163">컴퓨터 파일 시스템의 다음 폴더에서 파일이 디스크로 캐시되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-163">On the computer file system, check the following folder to determine whether files are cached to disk.</span></span> <span data-ttu-id="efc29-164">배포가 작동하는지 확인하려면 캐시된 파일이 있는지도 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-164">The presence of cached files is further verification that your deployment is operational.</span></span> <span data-ttu-id="efc29-165">파일 캐시를 보려면 \<drive> : FILES\MICROSOFT SQL Server\MSAS11.로 이동 합니다. POWERPIVOT\OLAP\Backup\Sandboxes\Default PowerPivot 서비스 응용 프로그램 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-165">To view the file cache, go to the \<drive>:\Program Files\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup\Sandboxes\Default PowerPivot Service Application folder.</span></span> <span data-ttu-id="efc29-166">캐시된 각 데이터베이스는 고유 이름을 사용하도록 GUID 기반 명명 규칙을 사용하여 고유 폴더에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc29-166">Each cached database is stored in its own folder, using a GUID-based naming convention to ensure a unique name.</span></span>  
  
  
