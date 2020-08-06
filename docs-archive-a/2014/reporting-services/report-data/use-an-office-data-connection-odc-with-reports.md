---
title: 보고서에 Office 데이터 연결 (.odc) 사용 (SharePoint 통합 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Office Data Connection (.odc) files
- SharePoint integration [Reporting Services], shared data sources
- .odc files
ms.assetid: e8d6896d-f886-4390-8b5d-96f0a50c250c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d795c46f46b45511079ac03add2d18214ac54489
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639317"
---
# <a name="use-an-office-data-connection-odc-with-reports-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="10109-102">보고서에 Office 데이터 연결(.odc) 사용(SharePoint 통합 모드의 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="10109-102">Use an Office Data Connection (.odc) with Reports (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="10109-103">제한된 시나리오에서 기존 Office 데이터 연결 파일(.odc)을 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서에 연결 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-103">For limited scenarios, you can use an existing Office Data Connection (.odc) file to provide connection information to a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report.</span></span> <span data-ttu-id="10109-104">공유 데이터 원본을 만들 때 .rsds 파일 대신 .odc 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-104">An .odc file can be used in place of an .rsds file when you create a shared data source.</span></span> <span data-ttu-id="10109-105">보고서 서버는 .rsds 파일과 같은 방식으로 .odc 파일을 사용합니다. 즉, 이 파일을 읽어 데이터 원본 유형, 연결 문자열 및 자격 증명 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-105">The report server uses an .odc file in the same way it uses an .rsds file; it reads the file for the data source type, a connection string, and credential information.</span></span>  
  
 <span data-ttu-id="10109-106">모든 .odc 파일을 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서에 사용할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="10109-106">Not all .odc files can be used with a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report.</span></span> <span data-ttu-id="10109-107">보고서 및 .odc 파일의 데이터 처리 확장 프로그램과 특징에 따라 .odc의 사용 가능 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="10109-107">The data processing extension and characteristics of the report and .odc file determine whether an .odc can be used:</span></span>  
  
-   <span data-ttu-id="10109-108">보고서가 OLE DB 또는 ODBC 데이터 공급자에서 작동하도록 디자인되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-108">The report must be designed to work with an OLE DB or ODBC data provider.</span></span> <span data-ttu-id="10109-109">다른 데이터 처리 확장 프로그램을 사용하여 보고서를 만든 경우 보고서나 해당 쿼리에 OLE DB 또는 ODBC 데이터 공급자가 지원하지 않는 기능이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-109">If you used a different data processing extension to create the report, the report or its queries might include functionality that is not supported by the OLE DB or ODBC data provider.</span></span>  
  
-   <span data-ttu-id="10109-110">.odc 파일에 필요한 요소와 구조가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-110">The .odc file must have the expected elements and structure.</span></span> <span data-ttu-id="10109-111">데이터 공급자 및 자격 증명 설정이 보고서 서버에서 읽을 수 있도록 파일에 명시적으로 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-111">The data provider and credential settings must be set explicitly in the file so that they can be read by the report server.</span></span> <span data-ttu-id="10109-112">이러한 값을 설정하는 최상의 방법은 .odc 파일을 SharePoint 라이브러리로 업로드하기 전에 이 파일을 내보내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="10109-112">The best way to set these values is to export the .odc file before uploading it to the SharePoint library.</span></span>  
  
-   <span data-ttu-id="10109-113">.odc 파일에서 OLE DB 또는 ODBC 연결 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-113">The .odc file must specify a connection type of OLE DB or ODBC.</span></span>  
  
-   <span data-ttu-id="10109-114">.odc 파일에서 연결 문자열을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-114">The .odc file must specify a connection string.</span></span>  
  
-   <span data-ttu-id="10109-115">자격 증명은 `None`, `Stored` 또는 `Integrated`로 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-115">Credentials can be set to `None`, `Stored`, or `Integrated`.</span></span> <span data-ttu-id="10109-116">자격 증명 방법을 `Stored`로 설정하면 보고서 서버가 저장된 자격 증명을 사용하는 대신 사용자에게 자격 증명을 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-116">If the credentials method is set to `Stored`, the report server will prompt the user for credentials instead of using the stored credentials.</span></span> <span data-ttu-id="10109-117">보고서 서버는 .odc 파일에 정의된 대로 저장된 자격 증명을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-117">The report server cannot use stored credentials as defined in the .odc file.</span></span>  
  
-   <span data-ttu-id="10109-118">보고서를 만드는 데 사용된 스키마와 동일한 스키마가 데이터 원본에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-118">The data source must have schema that is identical to the one used to create the report.</span></span> <span data-ttu-id="10109-119">데이터 구조가 다른 경우 보고서가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-119">If the data structures are different, the report will not run.</span></span>  
  
-   <span data-ttu-id="10109-120">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 2007에서 만든 .odc 파일이어야 합니다. 이전 버전의 .odc는 보고서 정의 파일과 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-120">The .odc file must be created in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 2007 (older versions of .odc are not compatible with report definition files).</span></span>  
  
 <span data-ttu-id="10109-121">.odc 데이터 원본 유형이 지원되는 데이터 원본 유형과 비슷해 보이지만 보고서 서버에서 처리할 수 없는 데이터 원본에 대한 연결을 지정하는 .odc 파일은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-121">You cannot use .odc files that specify connections to data sources that cannot be processed on a report server, even if the .odc data source types look similar to supported data source types.</span></span> <span data-ttu-id="10109-122">특히 Microsoft Excel 2007에서 Microsoft Access, 웹 또는 텍스트 파일의 데이터를 검색하는 .odc 파일을 만든 경우 이 .odc 파일을 사용하여 보고서에 데이터를 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-122">Specifically, if you created an .odc file in Microsoft Excel 2007 that retrieves data from Microsoft Access, the Web, or a text file, you cannot use that .odc file to provide data to a report.</span></span>  
  
 <span data-ttu-id="10109-123">보고서 작성기 보고서와 모델은 .odc 파일에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-123">Report Builder reports and models do not work with .odc file.</span></span> <span data-ttu-id="10109-124">.odc 파일을 사용하여 모델을 생성할 수 없으며 .odc 파일에 연결된 공유 데이터 원본을 사용하도록 모델을 구성할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-124">You cannot use an .odc file to generate a model, and you cannot configure the model to use a shared data source that links to an .odc file.</span></span>  
  
 <span data-ttu-id="10109-125">.odc 파일에 익숙하지 않을 경우 다음 지침을 사용하여 .odc 파일을 만들고 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-125">If you are not familiar with .odc files, you can use the following instructions to create and export one.</span></span> <span data-ttu-id="10109-126">OLE DB 데이터 원본에 사용할 .odc 파일을 만드는 한 가지 쉬운 방법은 Excel 2007과 데이터 연결 마법사를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="10109-126">One easy way to create an .odc file for an OLE DB data source is to use Excel 2007 and the Data Connection Wizard.</span></span> <span data-ttu-id="10109-127">이때 마법사에서 데이터 원본을 만들지 않으며 이미 정의된 외부 데이터 원본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-127">Note that the wizard does not create a data source; you must have an external data source that is already defined.</span></span>  
  
 <span data-ttu-id="10109-128">기존 .odc 파일은 보고서 및 쿼리와 완전히 호환되는 경우에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-128">An existing .odc file should only be used if it is fully compatible with the report and queries.</span></span> <span data-ttu-id="10109-129">보고서나 .odc 파일을 완전히 수정해야 하는 오류가 발생하면 보고서에 대해 새 .rsds 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-129">If you run into errors that require significant modifications to either the report or to the .odc file, you should create a new .rsds file for the report.</span></span> <span data-ttu-id="10109-130">.rsds 파일을 사용하는 공유 데이터 원본을 만드는 방법은 [공유 데이터 원본 만들기 및 관리&#40;SharePoint 통합 모드의 Reporting Services&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10109-130">For more information about how to create a shared data source that uses an .rsds file, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
### <a name="to-create-and-export-an-odc-file"></a><span data-ttu-id="10109-131">.odc 파일을 만들고 내보내려면</span><span class="sxs-lookup"><span data-stu-id="10109-131">To create and export an .odc file</span></span>  
  
1.  <span data-ttu-id="10109-132">Excel 2007을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-132">Start Excel 2007.</span></span>  
  
2.  <span data-ttu-id="10109-133">**데이터** 탭의 **외부 데이터 가져오기** 그룹에서 **기타 원본**을 클릭한 다음 **데이터 연결 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-133">On the **Data** tab, in the **Get External Data** group, click **From Other Sources**, and then click **From Data Connection Wizard**.</span></span>  
  
3.  <span data-ttu-id="10109-134">**기타/고급**을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-134">Select **Other/Advanced**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="10109-135">**Microsoft OLE DB Provider for SQL Server**를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-135">Select **Microsoft OLE DB Provider for SQL Server**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="10109-136">서버의 이름(기본적으로 컴퓨터의 네트워크 이름) 및 유효한 로그인과 데이터베이스 사용 권한을 가진 사용자 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-136">Enter the name of the server (by default, it is the network name of the computer) and a user account that has a valid login and database permissions.</span></span> <span data-ttu-id="10109-137">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-137">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="10109-138">데이터베이스를 선택한 다음 **확인** 을 클릭하여 **데이터 연결** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-138">Select a database, and then click **OK** to close the **Data Link** dialog box.</span></span>  
  
7.  <span data-ttu-id="10109-139">**특정 테이블에 연결** 확인란은 기본적으로 선택되어 있으며</span><span class="sxs-lookup"><span data-stu-id="10109-139">The **Connect to specific table** check box is selected by default.</span></span> <span data-ttu-id="10109-140">특정 테이블에서 데이터를 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="10109-140">It is used to retrieve data from a specific table.</span></span> <span data-ttu-id="10109-141">보고서 서버는 .odc 파일의 모든 쿼리를 무시하므로 이 확인란의 선택 여부는 상관이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-141">The report server ignores all queries in an .odc file, so it does not matter whether you select or clear the check box.</span></span> <span data-ttu-id="10109-142">보고서 데이터를 검색하는 쿼리는 외부 파일이 아닌 보고서 정의에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-142">Queries that retrieve data for a report are included in a report definition file and not in external files.</span></span>  
  
8.  <span data-ttu-id="10109-143">연결이 열려 있는 동안 속성을 편집하여 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-143">While the connection is open, you can edit properties and export it.</span></span> <span data-ttu-id="10109-144">**데이터** 탭의 **연결** 그룹에서 **속성**을 클릭한 다음 연결 이름 옆에 있는 **연결 속성** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-144">On the **Data** tab, in the **Connections** group, click **Properties**, and then click the **Connection Properties** button next to the connection name.</span></span>  
  
9. <span data-ttu-id="10109-145">**정의** 탭에서 **연결 파일 내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-145">On the **Definition** tab, click **Export Connection File**.</span></span>  
  
10. <span data-ttu-id="10109-146">파일 이름을 입력한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-146">Enter a name for the file, and then click **Save**.</span></span> <span data-ttu-id="10109-147">애플리케이션과 열려 있는 모든 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-147">Close the application and all open files.</span></span>  
  
### <a name="to-upload-and-use-an-odc-file"></a><span data-ttu-id="10109-148">.odc 파일을 업로드하고 사용하려면</span><span class="sxs-lookup"><span data-stu-id="10109-148">To upload and use an .odc file</span></span>  
  
1.  <span data-ttu-id="10109-149">연결 파일을 업로드할 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="10109-149">Open the library into which you want to upload the connection file.</span></span>  
  
2.  <span data-ttu-id="10109-150">**업로드** 메뉴에서 **문서 업로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-150">On the **Upload** menu, click **Upload document**.</span></span>  
  
3.  <span data-ttu-id="10109-151">**찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-151">Click **Browse**.</span></span>  
  
4.  <span data-ttu-id="10109-152">직접 만든 .odc 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-152">Select the .odc file you created.</span></span> <span data-ttu-id="10109-153">기본적으로 .odc 파일은 My Documents 폴더의 My Data Sources에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-153">By default, the .odc file is in the My Documents folder, in My Data Sources.</span></span>  
  
5.  <span data-ttu-id="10109-154">**열기** 를 클릭하여 파일을 선택하고 **확인** 을 클릭하여 선택 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-154">Click **Open** to select the file, click **OK** to save the selection.</span></span> <span data-ttu-id="10109-155">새 항목의 속성 페이지가 자동으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="10109-155">The properties page for the new item opens automatically.</span></span>  
  
6.  <span data-ttu-id="10109-156">콘텐츠 형식에서 **보고서 데이터 원본**을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-156">In Content Type, select **Report Data Source**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="10109-157">보고서를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="10109-157">Point to a report.</span></span>  
  
8.  <span data-ttu-id="10109-158">아래쪽 화살표를 클릭하고 **데이터 원본 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-158">Click the down arrow, and select **Manage Data Sources**.</span></span>  
  
9. <span data-ttu-id="10109-159">데이터 원본 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-159">Click the data source name.</span></span>  
  
10. <span data-ttu-id="10109-160">보고서에서 사용자 지정 데이터 원본 정보를 사용하는 경우 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-160">If the report uses custom data source information, click **Shared**.</span></span>  
  
11. <span data-ttu-id="10109-161">**데이터 원본 연결**에서 찾아보기( **...** ) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-161">In **Data Source Link**, click the browse (**...**) button.</span></span>  
  
12. <span data-ttu-id="10109-162">방금 업로드한 .odc 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-162">Select the .odc file you just uploaded.</span></span>  
  
13. <span data-ttu-id="10109-163">**확인** 을 클릭하여 파일을 선택한 다음 **확인** 을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="10109-163">Click **OK** to select the file, and then click **OK** to save your changes.</span></span>  
  
     <span data-ttu-id="10109-164">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스와 예제 보고서를 사용하여 이러한 단계를 수행하는 경우 Company Sales 보고서만 .odc 파일에서 추가 작업 없이 작동한다는 사실에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="10109-164">If you are trying these steps with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database and sample reports, be aware that only the Company Sales report will work out-of-the-box with an .odc file.</span></span> <span data-ttu-id="10109-165">다른 예제 보고서에는 OLE DB 공급자에서 작동하지 않는 쿼리 매개 변수와 기능이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-165">The other sample reports contain query parameters and features that do not work with the OLE DB provider.</span></span> <span data-ttu-id="10109-166">하지만 먼저 보고서 디자이너에서 이러한 보고서를 수정하면 OLE DB 공급자에서 작동하도록 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10109-166">However, you can make the reports work with the OLE DB provider if you modify them first in Report Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10109-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10109-167">See Also</span></span>  
 [<span data-ttu-id="10109-168">공유 데이터 원본 만들기, 수정 및 삭제&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="10109-168">Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;</span></span>](create-modify-and-delete-shared-data-sources-ssrs.md)  
  
  
