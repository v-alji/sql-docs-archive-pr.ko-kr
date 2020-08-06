---
title: '자습서: 드릴스루 보고서 및 주 보고서 만들기(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7168c8d3-cef5-4c4a-a0bf-fff1ac5b8b71
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7d30b59a0c5523ed50df06f8587bbd701ae4c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737809"
---
# <a name="tutorial-creating-drillthrough-and-main-reports-report-builder"></a><span data-ttu-id="81a88-102">자습서: 드릴스루 보고서 및 주 보고서 만들기(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="81a88-102">Tutorial: Creating Drillthrough and Main Reports (Report Builder)</span></span>
  <span data-ttu-id="81a88-103">이 자습서에서는 두 종류의 보고서인 드릴스루 보고서와 주 보고서를 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-103">This tutorial teaches you how to create two kinds of reports: a drillthrough report and a main report.</span></span> <span data-ttu-id="81a88-104">이러한 보고서에서 사용되는 샘플 판매 데이터는 Analysis Services 큐브에서 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-104">The sample sales data used in these reports is retrieved from an Analysis Services cube.</span></span> <span data-ttu-id="81a88-105">다음 그림에서는 만들려는 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-105">The following illustration shows the reports you will create.</span></span>  
  
 <span data-ttu-id="81a88-106">![rs_DrillthroughCubeTutorial](../../2014/tutorials/media/rs-drillthroughcubetutorial.gif "rs_DrillthroughCubeTutorial")</span><span class="sxs-lookup"><span data-stu-id="81a88-106">![rs_DrillthroughCubeTutorial](../../2014/tutorials/media/rs-drillthroughcubetutorial.gif "rs_DrillthroughCubeTutorial")</span></span>  
  
 <span data-ttu-id="81a88-107">다음 그림에서는 주 보고서의 필드 값, 게임 및 장난감이 드릴스루 보고서의 제목에 표시 되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-107">The following illustration shows how the field value, Games and Toys, in the main report displays in the drillthrough report's title.</span></span> <span data-ttu-id="81a88-108">드릴스루의 데이터는 Games and Toys 제품 범주에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-108">The data in the drillthrough pertains to the Games and Toys product category.</span></span>  
  
 <span data-ttu-id="81a88-109">![rs_DrillthroughCubeTutorialParmExpr](../../2014/tutorials/media/rs-drillthroughcubetutorialparmexpr.gif "rs_DrillthroughCubeTutorialParmExpr")</span><span class="sxs-lookup"><span data-stu-id="81a88-109">![rs_DrillthroughCubeTutorialParmExpr](../../2014/tutorials/media/rs-drillthroughcubetutorialparmexpr.gif "rs_DrillthroughCubeTutorialParmExpr")</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="81a88-110">학습 내용</span><span class="sxs-lookup"><span data-stu-id="81a88-110">What You Will Learn</span></span>  
 <span data-ttu-id="81a88-111">**드릴스루 보고서에서는 다음 작업 방법을 배웁니다.**</span><span class="sxs-lookup"><span data-stu-id="81a88-111">**In the drillthrough report you will learn how to:**</span></span>  
  
1.  [<span data-ttu-id="81a88-112">테이블 또는 행렬 마법사에서 드릴스루 행렬 보고서 및 데이터 세트 만들기</span><span class="sxs-lookup"><span data-stu-id="81a88-112">Create a Drillthrough Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#DMatrixAndDataset)  
  
    1.  [<span data-ttu-id="81a88-113">데이터 연결 지정</span><span class="sxs-lookup"><span data-stu-id="81a88-113">Specify a Data Connection</span></span>](#DConnection)  
  
    2.  [<span data-ttu-id="81a88-114">MDX 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="81a88-114">Create an MDX Query</span></span>](#DMDXQuery)  
  
    3.  [<span data-ttu-id="81a88-115">데이터를 그룹 스타일로 구성</span><span class="sxs-lookup"><span data-stu-id="81a88-115">Organize Data into Groups Style</span></span>](#DLayout)  
  
    4.  [<span data-ttu-id="81a88-116">부분합 및 합계 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-116">Add Subtotals and Totals</span></span>](#DTotals)  
  
    5.  [<span data-ttu-id="81a88-117">스타일 선택</span><span class="sxs-lookup"><span data-stu-id="81a88-117">Choose a Style</span></span>](#DStyle)  
  
2.  [<span data-ttu-id="81a88-118">데이터 형식을 통화로 지정</span><span class="sxs-lookup"><span data-stu-id="81a88-118">Format Data as Currency</span></span>](#DFormat)  
  
3.  [<span data-ttu-id="81a88-119">스파크 라인에 판매 값을 표시 하는 열 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-119">Add columns to Show Sales Values in Sparklines</span></span>](#DSparkline)  
  
4.  [<span data-ttu-id="81a88-120">제품 범주 이름의 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-120">Add Report Title with Product Category Name</span></span>](#DReportTitle)  
  
5.  [<span data-ttu-id="81a88-121">매개 변수 속성 업데이트</span><span class="sxs-lookup"><span data-stu-id="81a88-121">Update Parameter Properties</span></span>](#DParameter)  
  
6.  [<span data-ttu-id="81a88-122">SharePoint 라이브러리에 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="81a88-122">Save the Report to a SharePoint Library</span></span>](#DSave)  
  
 <span data-ttu-id="81a88-123">**주 보고서에서는 다음 작업 방법을 배웁니다.**</span><span class="sxs-lookup"><span data-stu-id="81a88-123">**In the main report you will learn how to:**</span></span>  
  
1.  [<span data-ttu-id="81a88-124">테이블 또는 행렬 마법사에서 주 행렬 보고서 및 데이터 세트 만들기</span><span class="sxs-lookup"><span data-stu-id="81a88-124">Create the Main Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#MMatrixAndDataset)  
  
    1.  [<span data-ttu-id="81a88-125">데이터 연결 지정</span><span class="sxs-lookup"><span data-stu-id="81a88-125">Specify a Data Connection</span></span>](#MConnection)  
  
    2.  [<span data-ttu-id="81a88-126">MDX 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="81a88-126">Create an MDX Query</span></span>](#MMDXQuery)  
  
    3.  [<span data-ttu-id="81a88-127">데이터를 그룹으로 구성</span><span class="sxs-lookup"><span data-stu-id="81a88-127">Organize Data into Groups</span></span>](#MLayout)  
  
    4.  [<span data-ttu-id="81a88-128">부분합 및 합계 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-128">Add Subtotals and Totals</span></span>](#MTotals)  
  
    5.  [<span data-ttu-id="81a88-129">스타일 선택</span><span class="sxs-lookup"><span data-stu-id="81a88-129">Choose a Style</span></span>](#MStyle)  
  
2.  [<span data-ttu-id="81a88-130">총합계 행 제거</span><span class="sxs-lookup"><span data-stu-id="81a88-130">Remove the Grand Total Row</span></span>](#MGrandTotal)  
  
3.  [<span data-ttu-id="81a88-131">드릴스루에 대한 입력란 동작 구성</span><span class="sxs-lookup"><span data-stu-id="81a88-131">Configure Text Box Action for Drillthrough</span></span>](#MDrillthrough)  
  
4.  [<span data-ttu-id="81a88-132">숫자 값을 표시기로 바꾸기</span><span class="sxs-lookup"><span data-stu-id="81a88-132">Replace Numeric Values with Indicators</span></span>](#MIndicators)  
  
5.  [<span data-ttu-id="81a88-133">매개 변수 속성 업데이트</span><span class="sxs-lookup"><span data-stu-id="81a88-133">Update Parameter Properties</span></span>](#MParameter)  
  
6.  [<span data-ttu-id="81a88-134">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-134">Add a Report Title</span></span>](#MTitle)  
  
7.  [<span data-ttu-id="81a88-135">SharePoint 라이브러리에 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="81a88-135">Save the Report to a SharePoint Library</span></span>](#MSave)  
  
8.  [<span data-ttu-id="81a88-136">주 보고서 및 드릴스루 보고서 실행</span><span class="sxs-lookup"><span data-stu-id="81a88-136">Run the Main and Drillthrough Reports</span></span>](#MRunReports)  
  
 <span data-ttu-id="81a88-137">이 자습서에 소요되는 예상 시간: 30분</span><span class="sxs-lookup"><span data-stu-id="81a88-137">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a88-138">요구 사항</span><span class="sxs-lookup"><span data-stu-id="81a88-138">Requirements</span></span>  
 <span data-ttu-id="81a88-139">이 자습서를 실행하려면 Contoso Sales 큐브에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-139">This tutorial requires access to the Contoso Sales cube.</span></span> <span data-ttu-id="81a88-140">이 요구 사항은 드릴스루 보고서와 주 보고서 모두에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-140">This requirement applies to both the drillthrough and the main reports.</span></span> <span data-ttu-id="81a88-141">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81a88-141">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-drillthrough-report-from-the-table-or-matrix-wizard"></a><a name="DMatrixAndDataset"></a><span data-ttu-id="81a88-142">1. 테이블 또는 행렬 마법사에서 드릴스루 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="81a88-142">1. Create a Drillthrough Report from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="81a88-143">시작 대화 상자에서 **테이블 또는 행렬 마법사**를 사용하여 행렬 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-143">From the Getting Started dialog box, create a matrix report by using the **Table or Matrix Wizard**.</span></span> <span data-ttu-id="81a88-144">마법사에서는 두 가지 모드인 보고서 디자인 모드와 공유 데이터 세트 디자인 모드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-144">There are two modes available in the wizard: report design and shared dataset design.</span></span> <span data-ttu-id="81a88-145">이 자습서에서는 보고서 디자인 모드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-145">In this tutorial, you will use the report design mode.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="81a88-146">새 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-146">To create a new report</span></span>  
  
1.  <span data-ttu-id="81a88-147">**시작**을 클릭 하 고 **프로그램**, 보고서 작성기을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**다음 **보고서 작성기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-147">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="81a88-148">**시작** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-148">The **Getting Started** dialog box opens.</span></span> <span data-ttu-id="81a88-149">표시 되지 않는 경우 **보고서 작성기** 단추에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-149">If it does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="81a88-150">왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-150">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="81a88-151">오른쪽 창에서 **테이블 또는 행렬 마법사** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-151">In the right pane, verify that **Table or Matrix Wizard** is selected.</span></span>  
  
##  <a name="1a-specify-a-data-connection"></a><a name="DConnection"></a><span data-ttu-id="81a88-152">a.</span><span class="sxs-lookup"><span data-stu-id="81a88-152">1a.</span></span> <span data-ttu-id="81a88-153">데이터 연결 지정</span><span class="sxs-lookup"><span data-stu-id="81a88-153">Specify a Data Connection</span></span>  
 <span data-ttu-id="81a88-154">데이터 연결은 Analysis Services 큐브 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스와 같은 외부 데이터 원본에 연결하는 데 필요한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-154">A data connection contains the information necessary to connect to an external data source such as an Analysis Services cube or a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="81a88-155">데이터 연결을 지정하기 위해 보고서 서버의 공유 데이터 원본을 사용하거나 이 보고서에만 사용되는 포함된 데이터 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-155">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in this report.</span></span> <span data-ttu-id="81a88-156">이 자습서에서는 포함된 데이터 원본을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-156">In this tutorial, you will use an embedded data source.</span></span> <span data-ttu-id="81a88-157">공유 데이터 원본 사용 방법에 대한 자세한 내용은 [데이터에 연결하는 다른 방법&#40;보고서 작성기&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81a88-157">To learn more about using a shared data source, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="81a88-158">포함된 데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-158">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="81a88-159">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 선택한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-159">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="81a88-160">**데이터 원본에 대한 연결 선택** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-160">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="81a88-161">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-161">Click **New**.</span></span> <span data-ttu-id="81a88-162">**데이터 원본 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-162">The **Data Source Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="81a88-163">**이름**에 데이터 원본 이름으로 **Online and Reseller Sales Detail** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-163">In **Name**, type **Online and Reseller Sales Detail** as the name for the data source.</span></span>  
  
4.  <span data-ttu-id="81a88-164">**연결 형식 선택**에서 **Microsoft SQL Server Analysis Services**를 선택한 다음 **빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-164">In **Select a connection type**, select **Microsoft SQL Server Analysis Services**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="81a88-165">**데이터 원본**에서 데이터 원본이 **Microsoft SQL Server Analysis Services(AdomdClient)** 인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-165">In **Data source**, verify that the data source is **Microsoft SQL Server Analysis Services (AdomdClient)**.</span></span>  
  
6.  <span data-ttu-id="81a88-166">**서버 이름**에 Analysis Services 인스턴스가 설치된 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-166">In **Server name**, type the name of a server where an instance of Analysis Services is installed.</span></span>  
  
7.  <span data-ttu-id="81a88-167">**데이터베이스 이름 선택 또는 입력**에서 Contoso 큐브를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-167">In **Select or enter a database name**, select the Contoso cube.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="81a88-168">**연결 문자열** 에 다음 구문이 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-168">Verify that **Connection string** contains the following syntax:</span></span>  
  
    ```  
    Data Source=<servername>; Initial Catalog = Contoso  
    ```  
  
     <span data-ttu-id="81a88-169">`<servername>` 은 Analysis Services가 설치된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-169">The `<servername>` is the name of an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with Analysis Services installed.</span></span>  
  
10. <span data-ttu-id="81a88-170">**자격 증명 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-170">Click **Credentials type**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81a88-171">데이터 원본에서 사용 권한이 구성된 방법에 따라 기본 인증 옵션을 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-171">Depending on how permissions are configured on the data source, you might need to change the default authentication options.</span></span> <span data-ttu-id="81a88-172">자세한 내용은 [보안&#40;보고서 작성기&#41;](report-builder/security-report-builder.md)에서 만드는 모바일 보고서에서 보고서 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-172">For more information, see [Security &#40;Report Builder&#41;](report-builder/security-report-builder.md).</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="81a88-173">**데이터 원본에 대한 연결 선택** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-173">The **Choose a connection to a data source** page appears.</span></span>  
  
12. <span data-ttu-id="81a88-174">데이터 원본에 연결할 수 있는지 확인하려면 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-174">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="81a88-175">**성공적으로 만들어진 메시지 연결이** 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-175">The message **Connection created successfully** appears.</span></span>  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
14. <span data-ttu-id="81a88-176">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-176">Click **Next**.</span></span>  
  
##  <a name="1b-create-an-mdx-query"></a><a name="DMDXQuery"></a><span data-ttu-id="81a88-177">1b.</span><span class="sxs-lookup"><span data-stu-id="81a88-177">1b.</span></span> <span data-ttu-id="81a88-178">MDX 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="81a88-178">Create an MDX Query</span></span>  
 <span data-ttu-id="81a88-179">보고서에서는 미리 정의된 쿼리가 포함된 공유 데이터 세트를 사용하거나 해당 보고서에만 사용할 포함된 데이터 세트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-179">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="81a88-180">이 자습서에서는 포함된 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-180">In this tutorial, you will create an embedded dataset.</span></span>  
  
#### <a name="to-create-query-filters"></a><span data-ttu-id="81a88-181">쿼리 필터를 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-181">To create query filters</span></span>  
  
1.  <span data-ttu-id="81a88-182">**쿼리 디자인** 페이지의 메타 데이터 창에서 단추 **(...)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-182">On the **Design a query** page, in the Metadata pane, click the button **(...)**.</span></span>  
  
2.  <span data-ttu-id="81a88-183">**큐브 선택** 대화 상자에서 Sales를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-183">In the **Cube Selection** dialog box, click Sales, and then click **OK**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="81a88-184">MDX 쿼리를 수동으로 작성하지 않을 경우 ![디자인 모드로 전환](media/rsqdicon-designmode.gif "디자인 모드로 전환") 아이콘을 클릭하고, 쿼리 디자이너를 쿼리 모드로 토글하고, 완료된 MDX를 쿼리 디자이너로 붙여넣은 다음, [데이터 세트를 만들려면](#DSkip)의 6단계를 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-184">If you do not want to build the MDX query manually, click the ![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode") icon, toggle the query designer to Query mode, paste the completed MDX to the query designer, and then proceed to step 6 in [To create the dataset](#DSkip).</span></span>  
  
    ```  
    SELECT NON EMPTY { [Measures].[Sales Amount], [Measures].[Sales Return Amount] } ON COLUMNS, NON EMPTY { ([Channel].[Channel Name].[Channel Name].ALLMEMBERS * [Product].[Product Category Name].[Product Category Name].ALLMEMBERS * [Product].[Product Subcategory Name].[Product Subcategory Name].ALLMEMBERS ) } DIMENSION PROPERTIES MEMBER_CAPTION, MEMBER_UNIQUE_NAME ON ROWS FROM ( SELECT ( { [Date].[Calendar Year].&[2009] } ) ON COLUMNS FROM ( SELECT ( { [Sales Territory].[Sales Territory Group].&[North America] } ) ON COLUMNS FROM ( SELECT ( STRTOSET(@ProductProductCategoryName, CONSTRAINED) ) ON COLUMNS FROM ( SELECT ( { [Channel].[Channel Name].&[2], [Channel].[Channel Name].&[4] } ) ON COLUMNS FROM [Sales])))) WHERE ( [Sales Territory].[Sales Territory Group].&[North America], [Date].[Calendar Year].&[2009] ) CELL PROPERTIES VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS  
    ```  
  
3.  <span data-ttu-id="81a88-185">측정값 그룹 창에서 Channel을 확장한 다음 Channel Name을 필터 창의 **계층** 열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-185">In the Measure Group pane, expand Channel, and then drag Channel Name to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="81a88-186">Channel이라는 차원 이름이 자동으로 **차원** 열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-186">The dimension name, Channel, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="81a88-187">**차원** 또는 **연산자** 열을 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="81a88-187">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
4.  <span data-ttu-id="81a88-188">**필터 식** 목록을 열려면 **필터 식** 열의 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-188">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
5.  <span data-ttu-id="81a88-189">필터 식 목록에서 **All Channel**을 확장하고, **Online**, **Reseller**를 차례로 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-189">In the filter expression list, expand **All Channel**, click **Online**, click **Reseller**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="81a88-190">이제 쿼리에는 온라인과 대리점 채널만 포함할 필터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-190">The query now includes a filter to include only these channels: Online and Reseller.</span></span>  
  
6.  <span data-ttu-id="81a88-191">Sales Territory 차원을 확장한 다음 Sales Territory Group을 **Channel Name** 아래에 있는 **계층**열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-191">Expand the Sales Territory dimension, and then drag Sales Territory Group to the **Hierarchy** column (below **Channel Name**).</span></span>  
  
7.  <span data-ttu-id="81a88-192">**필터 식** 목록을 열고 **All Sales Territory**를 확장한 다음 **North America**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-192">Open the **Filter Expression** list, expand **All Sales Territory**, click **North America**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="81a88-193">이제 쿼리에는 북아메리카의 판매만 포함할 필터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-193">The query now has a filter to include only sales in North America.</span></span>  
  
8.  <span data-ttu-id="81a88-194">측정값 그룹 창에서 Date를 확장한 다음 Calendar Year를 필터 창의 **계층** 열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-194">In the Measure Group pane, expand Date, and then drag Calendar Year to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="81a88-195">Date라는 차원 이름이 자동으로 **차원** 열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-195">The dimension name, Date, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="81a88-196">**차원** 또는 **연산자** 열을 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="81a88-196">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
9. <span data-ttu-id="81a88-197">**필터 식** 목록을 열려면 **필터 식** 열의 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-197">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
10. <span data-ttu-id="81a88-198">필터 식 목록에서 **All Date**를 확장하고, **Year 2009**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-198">In the filter expression list, expand **All Date**, click **Year 2009**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="81a88-199">이제 쿼리에는 2009년만 포함할 필터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-199">The query now includes a filter to include only the calendar year 2009.</span></span>  
  
#### <a name="to-create-the-parameter"></a><span data-ttu-id="81a88-200">매개 변수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-200">To create the parameter</span></span>  
  
1.  <span data-ttu-id="81a88-201">Product 차원을 확장한 다음 Product Category Name 멤버를 **Calendar Year** 아래의 **계층**열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-201">Expand the Product dimension, and then drag the Product Category Name member to the **Hierarchy** column below **Calendar Year**.</span></span>  
  
2.  <span data-ttu-id="81a88-202">**필터 식** 목록에서 **All Products**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-202">Open the **Filter Expression** list, click **All Products**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="81a88-203">**매개 변수** 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-203">Click the **Parameter** checkbox.</span></span> <span data-ttu-id="81a88-204">쿼리에는 이제 ProductProductCategoryName 매개 변수가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-204">The query now includes the parameter ProductProductCategoryName.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81a88-205">매개 변수에는 제품 범주의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-205">The parameter contains the names of product categories.</span></span> <span data-ttu-id="81a88-206">주 보고서에서 제품 범주 이름을 클릭하면 해당 이름이 이 매개 변수를 사용하여 드릴스루 보고서로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-206">When you click a product category name in the main report, its name is passed to the drillthrough report by using this parameter.</span></span>  
  
###  <a name="to-create-the-dataset"></a><a name="DSkip"></a><span data-ttu-id="81a88-207">데이터 집합을 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-207">To create the dataset</span></span>  
  
1.  <span data-ttu-id="81a88-208">Channel 차원에서 Channel Name을 데이터 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-208">From the Channel dimension, drag Channel Name to the data pane.</span></span>  
  
2.  <span data-ttu-id="81a88-209">Product 차원에서 Product Category Name을 데이터 창으로 끌어 Channel Name의 오른쪽에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-209">From the Product dimension, drag Product Category Name to the data pane, and then place it to the right of Channel Name.</span></span>  
  
3.  <span data-ttu-id="81a88-210">Product 차원에서 Product Subcategory Name을 데이터 창으로 끌어 Product Category Name의 오른쪽에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-210">From the Product dimension, drag Product Subcategory Name to the data pane, and then place it to the right of Product Category Name.</span></span>  
  
4.  <span data-ttu-id="81a88-211">메타데이터 창에서 **측정값**을 확장한 다음 Sales를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-211">In the Metadata pane, expand **Measure**, and then expand Sales.</span></span>  
  
5.  <span data-ttu-id="81a88-212">Sales Amount 측정값을 데이터 창으로 끌어 Product Subcategory Name의 오른쪽에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-212">Drag the Sales Amount measure to the data pane, and then place it to the right of Product Subcategory Name.</span></span>  
  
6.  <span data-ttu-id="81a88-213">쿼리 디자이너 도구 모음에서 **실행(!)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-213">On the query designer toolbar, click **Run (!)**.</span></span>  
  
7.  <span data-ttu-id="81a88-214">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-214">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups"></a><a name="DLayout"></a><span data-ttu-id="81a88-215">1c.</span><span class="sxs-lookup"><span data-stu-id="81a88-215">1c.</span></span> <span data-ttu-id="81a88-216">데이터를 그룹으로 구성</span><span class="sxs-lookup"><span data-stu-id="81a88-216">Organize Data into Groups</span></span>  
 <span data-ttu-id="81a88-217">데이터를 그룹화할 필드를 선택할 때 세부 데이터와 집계 데이터가 표시되는 행과 열이 포함된 행렬을 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-217">When you select the fields on which to group the data, you design a matrix with rows and columns that displays detail and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="81a88-218">데이터를 그룹으로 구성하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-218">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="81a88-219">디자인 뷰로 전환하려면 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-219">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="81a88-220">**필드 정렬** 페이지에서 Product_Subcategory_Name을 **행 그룹**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-220">On the **Arrange fields** page, drag Product_Subcategory_Name to **Row groups**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81a88-221">이름의 공백이 밑줄(_)로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-221">The spaces in the names are replaced with underscores (_).</span></span> <span data-ttu-id="81a88-222">예를 들어 Product Category Name이 Product_Category_Name이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-222">For example Product Category Name is Product_Category_Name.</span></span>  
  
3.  <span data-ttu-id="81a88-223">Channel_Name을 **열 그룹**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-223">Drag Channel_Name to **Column groups**.</span></span>  
  
4.  <span data-ttu-id="81a88-224">Sales_Amount를 **값**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-224">Drag Sales_Amount to **Values**.</span></span>  
  
     <span data-ttu-id="81a88-225">Sales_Amount는 숫자 필드에 대한 기본 집계 함수인 Sum 함수를 통해 자동으로 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-225">Sales_Amount is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="81a88-226">이때 값은 `[Sum(Sales_Amount)]`입니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-226">The value is `[Sum(Sales_Amount)]`.</span></span>  
  
     <span data-ttu-id="81a88-227">사용 가능한 다른 집계 함수를 보려면 집계 함수를 변경하지 않고 드롭다운 목록을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-227">To view the other aggregate functions available, open the drop-down list (do not change the aggregate function).</span></span>  
  
5.  <span data-ttu-id="81a88-228">Sales_Return_Amount를 **값**으로 끌어 `[Sum(Sales_Amount)]`아래에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-228">Drag Sales_Return_Amount to **Values**, and then place it below `[Sum(Sales_Amount)]`.</span></span>  
  
     <span data-ttu-id="81a88-229">4 ~ 5단계에서는 행렬에 표시할 데이터를 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-229">Steps 4 and 5 specify the data to display in the matrix.</span></span>  
  
6.  <span data-ttu-id="81a88-230">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-230">Click **Next**.</span></span>  
  
##  <a name="1d-add-subtotals-and-totals"></a><a name="DTotals"></a><span data-ttu-id="81a88-231">차원.</span><span class="sxs-lookup"><span data-stu-id="81a88-231">1d.</span></span> <span data-ttu-id="81a88-232">부분합 및 합계 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-232">Add Subtotals and Totals</span></span>  
 <span data-ttu-id="81a88-233">그룹을 만든 후 필드에 대한 집계 값을 표시할 행을 추가하고 행 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-233">After you create groups, you can add and format rows where the aggregate values for the fields will display.</span></span> <span data-ttu-id="81a88-234">또한 모든 데이터를 표시할지 또는 사용자가 그룹화된 데이터를 대화형으로 확장하거나 축소할 수 있도록 할지 여부를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-234">You can also choose whether to show all the data or to let a user expand and collapse grouped data interactively.</span></span>  
  
#### <a name="to-add-subtotals-and-totals"></a><span data-ttu-id="81a88-235">부분합 및 합계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-235">To add subtotals and totals</span></span>  
  
1.  <span data-ttu-id="81a88-236">**레이아웃 선택** 페이지의 **옵션**에서 **부분합 및 총합계 표시** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-236">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="81a88-237">마법사 미리 보기 창에 4개의 행이 있는 행렬이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-237">The wizard Preview pane displays a matrix with four rows.</span></span>  
  
2.  <span data-ttu-id="81a88-238">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-238">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style"></a><a name="DStyle"></a><span data-ttu-id="81a88-239">e.</span><span class="sxs-lookup"><span data-stu-id="81a88-239">1e.</span></span> <span data-ttu-id="81a88-240">스타일 선택</span><span class="sxs-lookup"><span data-stu-id="81a88-240">Choose a Style</span></span>  
 <span data-ttu-id="81a88-241">스타일은 글꼴 스타일, 색 집합 및 테두리 스타일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-241">A style specifies a font style, a set of colors, and a border style.</span></span>  
  
#### <a name="to-specify-a-style"></a><span data-ttu-id="81a88-242">스타일을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-242">To specify a style</span></span>  
  
1.  <span data-ttu-id="81a88-243">**스타일 선택** 페이지의 스타일 창에서 슬레이트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-243">On the **Choose a Style** page, in the Styles pane, select Slate.</span></span>  
  
2.  <span data-ttu-id="81a88-244">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-244">Click **Finish**.</span></span>  
  
     <span data-ttu-id="81a88-245">디자인 화면에 테이블이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-245">The table is added to the design surface.</span></span>  
  
3.  <span data-ttu-id="81a88-246">보고서를 미리 보려면 **실행(!)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-246">To preview the report, click **Run (!)**.</span></span>  
  
##  <a name="2-format-data-as-currency"></a><a name="DFormat"></a><span data-ttu-id="81a88-247">2. 데이터 서식을 통화로 지정</span><span class="sxs-lookup"><span data-stu-id="81a88-247">2. Format Data as Currency</span></span>  
 <span data-ttu-id="81a88-248">드릴스루 보고서의 판매량 필드에 통화 서식을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-248">Apply currency formatting to the sales amount fields in the drillthrough report.</span></span>  
  
#### <a name="to-format-data-as-currency"></a><span data-ttu-id="81a88-249">데이터 서식을 통화로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-249">To format data as currency</span></span>  
  
1.  <span data-ttu-id="81a88-250">디자인 뷰로 전환하려면 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-250">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="81a88-251">한 번에 여러 셀을 선택하고 서식 지정하려면 Ctrl 키를 누른 다음 숫자 판매 데이터가 들어 있는 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-251">To select and format multiple cells at one time, press the Ctrl key, and then select the cells that contain the numeric sales data.</span></span>  
  
3.  <span data-ttu-id="81a88-252">**홈** 탭의 **숫자** 그룹에서 **통화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-252">On the **Home** tab, in the **Number** group, click **Currency**.</span></span>  
  
##  <a name="3-add-columns-to-show-sales-values-in-sparklines"></a><a name="DSparkline"></a><span data-ttu-id="81a88-253">3. 스파크 라인에 판매 값을 표시 하는 열 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-253">3. Add Columns to Show Sales Values in Sparklines</span></span>  
 <span data-ttu-id="81a88-254">보고서는 판매량 및 판매 수익을 통화 값으로 표시하는 대신 스파크라인에서 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-254">Instead of showing sales and sales returns as currency values, the report shows the values in a sparkline.</span></span>  
  
#### <a name="to-add-sparklines-to-columns"></a><span data-ttu-id="81a88-255">열에 스파크라인을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-255">To add sparklines to columns</span></span>  
  
1.  <span data-ttu-id="81a88-256">디자인 뷰로 전환하려면 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-256">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="81a88-257">행렬의 Total 그룹에서 **Sales Amount** 열을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 클릭한 다음 **오른쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-257">In the Total group of the matrix, right-click the **Sales Amount** column, click **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="81a88-258">**Sales Amount**의 오른쪽에 빈 열이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-258">An empty column is added to the right of **Sales Amount**.</span></span>  
  
3.  <span data-ttu-id="81a88-259">리본에서 **사각형**을 클릭한 다음 [Product_Subcategory] 행 그룹의 `[Sum(Sales_Amount)]` 셀 오른쪽에 있는 빈 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-259">On the ribbon, click **Rectangle**, and then click the empty cell to the right of the `[Sum(Sales_Amount)]` cell in the [Product_Subcategory] row group.</span></span>  
  
4.  <span data-ttu-id="81a88-260">리본에서 **스파크라인** 아이콘을 클릭한 다음 사각형이 추가된 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-260">On the ribbon, click the **Sparkline** icon, and then click the cell where the rectangle was added.</span></span>  
  
5.  <span data-ttu-id="81a88-261">**스파크라인 유형 선택** 대화 상자에서 **열** 유형이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-261">In the **Select Sparkline Type** dialog box, verify that **Column** type is selected.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="81a88-262">스파크라인을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-262">Right-click the sparkline.</span></span>  
  
8.  <span data-ttu-id="81a88-263">차트 데이터 창에서 **필드 추가** 아이콘을 클릭한 다음 Sales_Amount를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-263">In the Chart Data pane, click the **Add field** icon, and then click Sales_Amount.</span></span>  
  
9. <span data-ttu-id="81a88-264">`Sales_Return_Amount` 열을 마우스 오른쪽 단추로 클릭한 다음 이 열의 오른쪽에 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-264">Right-click the `Sales_Return_Amount` column, and then add a column to the right of it.</span></span>  
  
10. <span data-ttu-id="81a88-265">2 ~ 6단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-265">Repeat steps 2 through 6.</span></span>  
  
11. <span data-ttu-id="81a88-266">스파크라인을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-266">Right-click the sparkline.</span></span>  
  
12. <span data-ttu-id="81a88-267">차트 데이터 창에서 **필드 추가** 아이콘을 클릭한 다음 Sales_Return_Amount를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-267">In the Chart Data pane, click the **Add field** icon, and then click Sales_Return_Amount.</span></span>  
  
13. <span data-ttu-id="81a88-268">보고서를 미리 보려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-268">To preview the report, click **Run**.</span></span>  
  
##  <a name="4-add-report-title-with-product-category-name"></a><a name="DReportTitle"></a><span data-ttu-id="81a88-269">4. 제품 범주 이름을 사용 하 여 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-269">4. Add Report Title with Product Category Name</span></span>  
 <span data-ttu-id="81a88-270">보고서 제목은 보고서 맨 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-270">A report title appears at the top of the report.</span></span> <span data-ttu-id="81a88-271">보고서 제목을 보고서 머리글에 배치하거나, 보고서 머리글이 사용되지 않을 경우 보고서 본문의 맨 위에 있는 입력란에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-271">You can place the report title in a report header or, if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="81a88-272">이 자습서에서는 보고서 본문의 맨 위에 자동으로 표시되는 입력란을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-272">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="81a88-273">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-273">To add a report title</span></span>  
  
1.  <span data-ttu-id="81a88-274">디자인 뷰로 전환하려면 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-274">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="81a88-275">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-275">On the design surface, click **Click to add title**.</span></span>  
  
3.  <span data-ttu-id="81a88-276">**Sales and Returns for Category:** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-276">Type **Sales and Returns for Category:**.</span></span>  
  
4.  <span data-ttu-id="81a88-277">마우스 오른쪽 단추를 클릭한 다음 **자리 표시자 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-277">Right-click, and then click **Create Placeholder**.</span></span>  
  
5.  <span data-ttu-id="81a88-278">**값** 목록의 오른쪽에 있는 **(fx)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-278">Click the **(fx)** button to the right of the **Value** list.</span></span>  
  
6.  <span data-ttu-id="81a88-279">**식** 대화 상자의 범주 창에서 **데이터 세트**를 클릭한 다음, **값** 목록에서 `First(Product_Category_Name)`를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-279">In the **Expression** dialog box, in the Category pane, click **Dataset**, and then in the **Values** list double-click `First(Product_Category_Name)`.</span></span>  
  
     <span data-ttu-id="81a88-280">**식** 입력란에 다음 식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-280">The **Expression** box contains the following expression:</span></span>  
  
    ```  
    =First(Fields!Product_Category_Name.Value, "DataSet1")  
    ```  
  
7.  <span data-ttu-id="81a88-281">보고서를 미리 보려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-281">To preview the report, click **Run**.</span></span>  
  
 <span data-ttu-id="81a88-282">보고서 제목에 첫 번째 제품 범주의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-282">The report title includes the name of the first product category.</span></span> <span data-ttu-id="81a88-283">나중에 이 보고서를 드릴스루 보고서로 실행하면 제품 범주 이름이 주 보고서에서 클릭된 제품 범주의 이름을 반영하도록 동적으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-283">Later, after you run this report as a drillthrough report, the product category name will dynamically change to reflect the name of the product category that was clicked in the main report.</span></span>  
  
##  <a name="5-update-parameter-properties"></a><a name="DParameter"></a><span data-ttu-id="81a88-284">5. 매개 변수 속성 업데이트</span><span class="sxs-lookup"><span data-stu-id="81a88-284">5. Update Parameter Properties</span></span>  
 <span data-ttu-id="81a88-285">기본적으로 매개 변수가 표시되는데 이는 이 보고서의 경우 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-285">By default parameters are visible, which is not appropriate for this report.</span></span> <span data-ttu-id="81a88-286">따라서 드릴스루 보고서에 대한 매개 변수 속성을 업데이트할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-286">You will update the parameter properties for the drillthrough report.</span></span>  
  
#### <a name="to-hide-a-parameter"></a><span data-ttu-id="81a88-287">매개 변수를 숨기려면</span><span class="sxs-lookup"><span data-stu-id="81a88-287">To hide a parameter</span></span>  
  
1.  <span data-ttu-id="81a88-288">보고서 데이터 창에서 **매개 변수**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-288">In the Report Data pane, expand **Parameters**.</span></span>  
  
2.  <span data-ttu-id="81a88-289">제품 제품 범주를 마우스 오른쪽 단추로 클릭 한 \@ 다음 **매개 변수 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-289">Right-click \@ProductProductCategoryName, and then click **Parameter Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81a88-290">이름 옆에 있는 \@ 문자는 이것이 매개 변수임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-290">The \@ character next to the name indicates that this is a parameter.</span></span>  
  
3.  <span data-ttu-id="81a88-291">**일반** 탭에서 **숨김**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-291">On the **General** tab, click **Hidden**.</span></span>  
  
4.  <span data-ttu-id="81a88-292">**프롬프트** 상자에 **Product Category**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-292">In the **Prompt** box, type **Product Category**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81a88-293">매개 변수가 숨겨져 있기 때문이 이 프롬프트는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-293">Because the parameter is hidden, this prompt is never used.</span></span>  
  
5.  <span data-ttu-id="81a88-294">필요에 따라 **사용 가능한 값** 및 **기본값** 을 클릭하고 해당 옵션을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-294">Optionally, click **Available Values** and **Default Values** and review their options.</span></span> <span data-ttu-id="81a88-295">이러한 탭에 대한 어떤 옵션도 변경하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="81a88-295">Do not change any options on these tabs.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-save-the-report-to-a-sharepoint-library"></a><a name="DSave"></a><span data-ttu-id="81a88-296">6. SharePoint 라이브러리에 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="81a88-296">6. Save the Report to a SharePoint Library</span></span>  
 <span data-ttu-id="81a88-297">보고서를 SharePoint 라이브러리, 보고서 서버 또는 컴퓨터에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-297">You can save the report to a SharePoint library, report server, or your computer.</span></span> <span data-ttu-id="81a88-298">보고서를 컴퓨터에 저장하면 보고서 파트 및 하위 보고서와 같은 여러 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-298">If you save the report to your computer, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span> <span data-ttu-id="81a88-299">이 자습서에서는 이 보고서를 SharePoint 라이브러리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-299">In this tutorial, you will save the report to a SharePoint library.</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="81a88-300">보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-300">To save the report</span></span>  
  
1.  <span data-ttu-id="81a88-301">보고서 작성기 단추에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-301">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="81a88-302">**보고서로 저장** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-302">The **Save As Report** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81a88-303">보고서를 다시 저장하는 경우 보고서가 이전 위치에 자동으로 다시 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-303">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="81a88-304">위치를 변경하려면 **다른 이름으로 저장** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-304">To change the location, use the **Save As** option.</span></span>  
  
2.  <span data-ttu-id="81a88-305">최근에 사용한 보고서 서버와 SharePoint 사이트의 목록을 표시하려면 **최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-305">To show a list of recently used report servers and SharePoint sites, click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="81a88-306">보고서를 저장할 수 있는 권한을 가진 SharePoint 사이트의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-306">Select or type the name of the SharePoint site where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="81a88-307">SharePoint 라이브러리의 URL에 다음 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-307">The URL of the SharePoint library has the following syntax:</span></span>  
  
    ```  
    Http://<ServerName>/<Sites>/  
    ```  
  
4.  <span data-ttu-id="81a88-308">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-308">Click **Save**.</span></span>  
  
     <span data-ttu-id="81a88-309">**최근에 사용한 사이트 및 서버** 는 SharePoint 사이트의 라이브러리를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-309">**Recent Sites and Servers** lists the libraries on the SharePoint site.</span></span>  
  
5.  <span data-ttu-id="81a88-310">보고서를 저장할 라이브러리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-310">Navigate to the library where you will save the report.</span></span>  
  
6.  <span data-ttu-id="81a88-311">**이름** 상자에서 기본 이름을 **ResellerVSOnlineDrillthrough**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-311">In the **Name** box, replace the default name with **ResellerVSOnlineDrillthrough**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81a88-312">주 보고서를 동일한 위치에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-312">You will save the main report to the same location.</span></span> <span data-ttu-id="81a88-313">주 보고서 및 드릴스루 보고서를 다른 사이트 또는 라이브러리에 저장할 경우 주 보고서에서 **보고서로 이동** 동작의 경로를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-313">If you want to save the main and drillthrough reports to different sites or libraries, you must update the path of the **Go to report** action in the main report.</span></span>  
  
7.  <span data-ttu-id="81a88-314">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-314">Click **Save**.</span></span>  
  
##  <a name="1-create-a-new-report-from-the-table-or-matrix-wizard"></a><a name="MMatrixAndDataset"></a><span data-ttu-id="81a88-315">1. 테이블 또는 행렬 마법사에서 새 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="81a88-315">1. Create a New Report from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="81a88-316">**시작** 대화 상자에서 **테이블 또는 행렬 마법사**를 사용하여 행렬 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-316">From the **Getting Started** dialog box, create a matrix report by using the **Table or Matrix Wizard**.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="81a88-317">새 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-317">To create a new report</span></span>  
  
1.  <span data-ttu-id="81a88-318">**시작**을 클릭 하 고 **프로그램**, 보고서 작성기을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**다음 **보고서 작성기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-318">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**, and then click **Report Builder**.</span></span>  
  
2.  <span data-ttu-id="81a88-319">**시작** 대화 상자에서 **새 보고서** 가 선택되어 있는지 확인한 다음 **테이블 또는 행렬 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-319">In the **Getting Started** dialog box, verify that **New Report** is selected, and then click **Table or Matrix Wizard**.</span></span>  
  
##  <a name="1a-specify-a-data-connection"></a><a name="MConnection"></a><span data-ttu-id="81a88-320">a.</span><span class="sxs-lookup"><span data-stu-id="81a88-320">1a.</span></span> <span data-ttu-id="81a88-321">데이터 연결 지정</span><span class="sxs-lookup"><span data-stu-id="81a88-321">Specify a Data Connection</span></span>  
 <span data-ttu-id="81a88-322">포함된 데이터 원본을 주 보고서에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-322">You will add an embedded data source to the main report.</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="81a88-323">포함된 데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-323">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="81a88-324">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 선택한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-324">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="81a88-325">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-325">Click **New**.</span></span>  
  
3.  <span data-ttu-id="81a88-326">**이름**에 데이터 원본 이름으로 **Online and Reseller Sales Main** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-326">In **Name**, type **Online and Reseller Sales Main** as the name for the data source.</span></span>  
  
4.  <span data-ttu-id="81a88-327">**연결 형식 선택**에서 **Microsoft SQL Server Analysis Services**를 선택한 다음 **빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-327">In **Select a connection type**, select **Microsoft SQL Server Analysis Services**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="81a88-328">**데이터 원본**에서 데이터 원본이 **Microsoft SQL Server Analysis Services(AdomdClient)** 인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-328">In **Data source**, verify that the data source is **Microsoft SQL Server Analysis Services (AdomdClient)**.</span></span>  
  
6.  <span data-ttu-id="81a88-329">**서버 이름**에 인스턴스가 설치 된 서버의 이름을 입력 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-329">In **Server name**, type the name of a server where an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is installed.</span></span>  
  
7.  <span data-ttu-id="81a88-330">**데이터베이스 이름 선택 또는 입력**에서 Contoso 큐브를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-330">In **Select or enter a database name**, select the Contoso cube.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="81a88-331">**연결 문자열** 에 다음 구문이 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-331">Verify that the **Connection string** contains the following syntax:</span></span>  
  
    ```  
    Data Source=<servername>; Initial Catalog = Contoso  
    ```  
  
10. <span data-ttu-id="81a88-332">**자격 증명 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-332">Click **Credentials type**.</span></span>  
  
     <span data-ttu-id="81a88-333">데이터 원본에서 사용 권한이 구성된 방법에 따라 기본 인증을 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-333">Depending on how permissions are configured on the data source, you might need to change the default authentication.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="81a88-334">데이터 원본에 연결할 수 있는지 확인하려면 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-334">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
14. <span data-ttu-id="81a88-335">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-335">Click **Next**.</span></span>  
  
##  <a name="1b-create-an-mdx-query"></a><a name="MMDXQuery"></a><span data-ttu-id="81a88-336">1b.</span><span class="sxs-lookup"><span data-stu-id="81a88-336">1b.</span></span> <span data-ttu-id="81a88-337">MDX 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="81a88-337">Create an MDX Query</span></span>  
 <span data-ttu-id="81a88-338">다음으로, 포함된 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-338">Next, create an embedded dataset.</span></span> <span data-ttu-id="81a88-339">이렇게 하려면 쿼리 디자이너를 사용하여 필터, 매개 변수 및 계산 멤버는 물론 데이터 세트 자체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-339">To do so, you will use the query designer to create filters, parameters, and calculated members as well as the dataset itself.</span></span>  
  
#### <a name="to-create-query-filters"></a><span data-ttu-id="81a88-340">쿼리 필터를 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-340">To create query filters</span></span>  
  
1.  <span data-ttu-id="81a88-341">**쿼리 디자인** 페이지의 메타 데이터 창에 있는 큐브 섹션에서 줄임표 **(...)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-341">On the **Design a query** page, in the Metadata pane, in the cube section, click the ellipsis **(...)**.</span></span>  
  
2.  <span data-ttu-id="81a88-342">**큐브 선택** 대화 상자에서 Sales를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-342">In the **Cube Selection** dialog box, click Sales, and then click **OK**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="81a88-343">MDX 쿼리를 수동으로 작성하지 않을 경우 ![디자인 모드로 전환](media/rsqdicon-designmode.gif "디자인 모드로 전환") 아이콘을 클릭하고, 쿼리 디자이너를 쿼리 모드로 토글하고, 완료된 MDX를 쿼리 디자이너로 붙여넣은 다음, [데이터 세트를 만들려면](#MSkip)의 5단계를 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-343">If you do not want to build the MDX query manually, click the ![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode") icon, toggle the query designer to Query mode, paste the completed MDX to the query designer, and then proceed to step 5 in [To create the dataset](#MSkip).</span></span>  
  
    ```  
    WITH MEMBER [Measures].[Net QTY] AS [Measures].[Sales Quantity] -[Measures].[Sales Return Quantity] MEMBER [Measures].[Net Sales] AS [Measures].[Sales Amount] - [Measures].[Sales Return Amount] SELECT NON EMPTY { [Measures].[Net QTY], [Measures].[Net Sales] } ON COLUMNS, NON EMPTY { ([Channel].[Channel Name].[Channel Name].ALLMEMBERS * [Product].[Product Category Name].[Product Category Name].ALLMEMBERS ) } DIMENSION PROPERTIES MEMBER_CAPTION, MEMBER_UNIQUE_NAME ON ROWS FROM ( SELECT ( { [Date].[Calendar Year].&[2009] } ) ON COLUMNS FROM ( SELECT ( STRTOSET(@ProductProductCategoryName, CONSTRAINED) ) ON COLUMNS FROM ( SELECT ( { [Sales Territory].[Sales Territory Group].&[North America] } ) ON COLUMNS FROM ( SELECT ( { [Channel].[Channel Name].&[2], [Channel].[Channel Name].&[4] } ) ON COLUMNS FROM [Sales])))) WHERE ( [Sales Territory].[Sales Territory Group].&[North America], [Date].[Calendar Year].&[2009] ) CELL PROPERTIES VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGSQuery text: Code.  
    ```  
  
3.  <span data-ttu-id="81a88-344">측정값 그룹 창에서 Channel을 확장한 다음 Channel Name을 필터 창의 **계층** 열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-344">In the Measure Group pane, expand Channel, and then drag Channel Name to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="81a88-345">Channel이라는 차원 이름이 자동으로 **차원** 열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-345">The dimension name, Channel, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="81a88-346">**차원** 또는 **연산자** 열을 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="81a88-346">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
4.  <span data-ttu-id="81a88-347">**필터 식** 목록을 열려면 **필터 식** 열의 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-347">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
5.  <span data-ttu-id="81a88-348">필터 식 목록에서 **All Channel**을 확장하고, **Online** , **Reseller**를 차례로 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-348">In the filter expression list, expand **All Channel**, click **Online** and **Reseller**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="81a88-349">이제 쿼리에는 온라인과 대리점 채널만 포함할 필터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-349">The query now includes a filter to include only these channels: Online and Reseller.</span></span>  
  
6.  <span data-ttu-id="81a88-350">Sales 영토 차원을 확장 한 다음 Sales 영토 그룹을 **Channel Name**아래에 있는 **계층** 열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-350">Expand the Sales Territory dimension, and then drag Sales Territory Group to the **Hierarchy** column, below **Channel Name**.</span></span>  
  
7.  <span data-ttu-id="81a88-351">**필터 식** 목록을 열고 **All Sales Territory**를 확장한 다음 **North America**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-351">Open the **Filter Expression** list, expand **All Sales Territory**, click **North America**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="81a88-352">이제 쿼리에는 북아메리카의 판매만 포함할 필터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-352">The query now has a filter to include only sales in North America.</span></span>  
  
8.  <span data-ttu-id="81a88-353">측정값 그룹 창에서 Date를 확장한 다음 Calendar Year를 필터 창의 **계층** 열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-353">In the Measure Group pane, expand Date, and drag Calendar Year to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="81a88-354">Date라는 차원 이름이 자동으로 **차원** 열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-354">The dimension name, Date, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="81a88-355">**차원** 또는 **연산자** 열을 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="81a88-355">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
9. <span data-ttu-id="81a88-356">**필터 식** 목록을 열려면 **필터 식** 열의 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-356">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
10. <span data-ttu-id="81a88-357">필터 식 목록에서 **All Date**를 확장하고, **Year 2009**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-357">In the filter expression list, expand **All Date**, click **Year 2009**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="81a88-358">이제 쿼리에는 2009년만 포함할 필터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-358">The query now includes a filter to include only the calendar year 2009.</span></span>  
  
#### <a name="to-create-the-parameter"></a><span data-ttu-id="81a88-359">매개 변수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-359">To create the parameter</span></span>  
  
1.  <span data-ttu-id="81a88-360">Product 차원을 확장한 다음 Product Category Name 멤버를 **Sales Territory Group** 아래의 **계층**열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-360">Expand the Product dimension, and then drag the Product Category Name member to the **Hierarchy** column below **Sales Territory Group**.</span></span>  
  
2.  <span data-ttu-id="81a88-361">**필터 식** 목록에서 **All Products**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-361">Open the **Filter Expression** list, click **All Products**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="81a88-362">**매개 변수** 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-362">Click the **Parameter** checkbox.</span></span> <span data-ttu-id="81a88-363">쿼리에는 이제 ProductProductCategoryName 매개 변수가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-363">The query now includes the parameter ProductProductCategoryName.</span></span>  
  
#### <a name="to-create-calculated-members"></a><span data-ttu-id="81a88-364">계산 멤버를 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-364">To create calculated members</span></span>  
  
1.  <span data-ttu-id="81a88-365">계산 멤버 창 내에 커서를 놓고 마우스 오른쪽 단추를 클릭한 다음 **새 계산 멤버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-365">Place the cursor inside the Calculated Members pane, right-click, and then click **New Calculated Member**.</span></span>  
  
2.  <span data-ttu-id="81a88-366">메타 데이터 창에서 **측정값** 을 확장 한 다음 Sales를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-366">In the Metadata pane, expand **Measures** and then expand Sales.</span></span>  
  
3.  <span data-ttu-id="81a88-367">Sales Quantity 측정값을 **식** 상자로 끌고, 빼기 문자(-)를 입력한 다음 Sales Return Quantity 측정값을 **식** 상자로 끌어 빼기 문자 뒤에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-367">Drag the Sales Quantity measure to the **Expression** box, type the subtraction character (-), and then drag the Sales Return Quantity measure to the **Expression** box; place it after the subtraction character.</span></span>  
  
     <span data-ttu-id="81a88-368">다음 코드에서는 식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-368">The following code shows the expression:</span></span>  
  
    ```  
    [Measures].[Sales Quantity] - [Measures].[Sales Return Quantity]  
    ```  
  
4.  <span data-ttu-id="81a88-369">이름 상자에 **Net QTY**를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-369">In the Name box, type **Net QTY**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="81a88-370">계산 멤버 창에 **Net QTY** 계산 멤버가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-370">The Calculated Members pane lists the **Net QTY** calculated member.</span></span>  
  
5.  <span data-ttu-id="81a88-371">**계산 멤버**를 마우스 오른쪽 단추로 클릭한 다음 **새 계산 멤버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-371">Right-click **Calculated Members**, and then click **New Calculated Member**.</span></span>  
  
6.  <span data-ttu-id="81a88-372">메타데이터 창에서 **측정값**을 확장한 다음 Sales를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-372">In the Metadata pane, expand **Measures**, and then expand Sales.</span></span>  
  
7.  <span data-ttu-id="81a88-373">Sales Amount 측정값을 **식** 상자로 끌고, 빼기 문자(-)를 입력한 다음 Sales Return Amount 측정값을 **식** 상자로 끌어 빼기 문자 뒤에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-373">Drag the Sales Amount measure to the **Expression** box, type the subtraction character (-), and then drag the Sales Return Amount measure to the **Expression** box; place it after the subtraction character.</span></span>  
  
     <span data-ttu-id="81a88-374">다음 코드에서는 식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-374">The following code shows the expression:</span></span>  
  
    ```  
    [Measures].[Sales Amount] - [Measures].[Sales Return Amount]  
    ```  
  
8.  <span data-ttu-id="81a88-375">**이름** 상자에  **Net Sales**를 입력한 다음 **확인**을 클릭합니다. 계산 멤버 창에 **Net Sales** 계산 멤버가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-375">In the **Name** box, type  **Net Sales**, and then click **OK**.The Calculated Members pane lists the **Net Sales** calculated member.</span></span>  
  
###  <a name="to-create-the-dataset"></a><a name="MSkip"></a><span data-ttu-id="81a88-376">데이터 집합을 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-376">To create the dataset</span></span>  
  
1.  <span data-ttu-id="81a88-377">Channel 차원에서 Channel Name을 데이터 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-377">From the Channel dimension, drag Channel Name to the data pane.</span></span>  
  
2.  <span data-ttu-id="81a88-378">Product 차원에서 Product Category Name을 데이터 창으로 끌어 Channel Name의 오른쪽에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-378">From the Product dimension, drag Product Category Name to the data pane, and then place it to the right of Channel Name.</span></span>  
  
3.  <span data-ttu-id="81a88-379">**계산 멤버**에서 `Net QTY` 를 데이터 창으로 끌어 Product Category Name의 오른쪽에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-379">From **Calculated Members**, drag `Net QTY` to the data pane, and then place it to the right of Product Category Name.</span></span>  
  
4.  <span data-ttu-id="81a88-380">계산 멤버에서 Net Sales를 데이터 창으로 끌어 `Net QTY`의 오른쪽에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-380">From Calculated Members, drag Net Sales to the data pane, and then place it to the right of `Net QTY`.</span></span>  
  
5.  <span data-ttu-id="81a88-381">쿼리 디자이너 도구 모음에서 **실행(!)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-381">On the query designer toolbar, click **Run (!)**.</span></span>  
  
     <span data-ttu-id="81a88-382">쿼리 결과 집합을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-382">Review the query result set.</span></span>  
  
6.  <span data-ttu-id="81a88-383">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-383">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups"></a><a name="MLayout"></a><span data-ttu-id="81a88-384">1c.</span><span class="sxs-lookup"><span data-stu-id="81a88-384">1c.</span></span> <span data-ttu-id="81a88-385">데이터를 그룹으로 구성</span><span class="sxs-lookup"><span data-stu-id="81a88-385">Organize Data into Groups</span></span>  
 <span data-ttu-id="81a88-386">데이터를 그룹화할 필드를 선택할 때 세부 데이터와 집계 데이터가 표시되는 행과 열이 포함된 행렬을 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-386">When you select the fields on which to group data, you design a matrix with rows and columns that displays detail and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="81a88-387">데이터를 그룹으로 구성하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-387">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="81a88-388">**필드 정렬** 페이지에서 Product_Category_Name을 **행 그룹**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-388">On the **Arrange fields** page, drag Product_Category_Name to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="81a88-389">Channel_Name을 **열 그룹**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-389">Drag Channel_Name to **Column groups**.</span></span>  
  
3.  <span data-ttu-id="81a88-390">`Net_QTY` 를 **값**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-390">Drag `Net_QTY` to **Values**.</span></span>  
  
     <span data-ttu-id="81a88-391">`Net_QTY` 는 숫자 필드에 대한 기본 집계 함수인 Sum 함수를 통해 자동으로 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-391">`Net_QTY` is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="81a88-392">이때 값은 `[Sum(Net_QTY)]`입니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-392">The value is `[Sum(Net_QTY)]`.</span></span>  
  
     <span data-ttu-id="81a88-393">사용 가능한 다른 집계 함수를 보려면 드롭다운 목록을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-393">To view the other aggregate functions available, open the drop-down list.</span></span> <span data-ttu-id="81a88-394">집계 함수를 변경하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="81a88-394">Do not change the aggregate function.</span></span>  
  
4.  <span data-ttu-id="81a88-395">`Net_Sales_Return` 을 **값** 으로 끌어 `[Sum(Net_QTY)]`아래에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-395">Drag `Net_Sales_Return` to **Values** and then place it below `[Sum(Net_QTY)]`.</span></span>  
  
     <span data-ttu-id="81a88-396">3 ~ 4단계에서는 행렬에 표시할 데이터를 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-396">Steps 3 and 4 specify the data to display in the matrix.</span></span>  
  
##  <a name="1d-add-subtotals-and-totals"></a><a name="MTotals"></a><span data-ttu-id="81a88-397">차원.</span><span class="sxs-lookup"><span data-stu-id="81a88-397">1d.</span></span> <span data-ttu-id="81a88-398">부분합 및 합계 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-398">Add Subtotals and Totals</span></span>  
 <span data-ttu-id="81a88-399">보고서에서 부분합 및 총합계를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-399">You can show subtotals and grand totals in reports.</span></span> <span data-ttu-id="81a88-400">주 보고서의 데이터가 표시기로 표시됩니다. 사용자는 마법사를 완료한 후 총합계를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-400">The data in the main report displays as an indicator; you will remove the grand total after you complete the wizard.</span></span>  
  
#### <a name="to-add-subtotals-and-grand-totals"></a><span data-ttu-id="81a88-401">부분합 및 총합계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-401">To add subtotals and grand totals</span></span>  
  
1.  <span data-ttu-id="81a88-402">**레이아웃 선택** 페이지의 **옵션**에서 **부분합 및 총합계 표시** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-402">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="81a88-403">마법사 미리 보기 창에 4개의 행이 있는 행렬이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-403">The wizard Preview pane displays a matrix with four rows.</span></span>  <span data-ttu-id="81a88-404">보고서를 실행하면 각 행이 다음과 같은 방식으로 표시됩니다. 첫 번째 행은 열 그룹이며, 두 번째 행은 열 제목을 포함하며, 세 번째 행은 제품 범주 데이터(`[Sum(Net_ QTY)]` 및 `[Sum(Net_Sales)]`)를 포함하며, 네 번째 행은 합계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-404">When you run the report, each row will display in the following way: The first row is the column group, the second row contains the column headings, the third row contains the product category data (`[Sum(Net_ QTY)]` and `[Sum(Net_Sales)]`, and the fourth row contains the totals.</span></span>  
  
2.  <span data-ttu-id="81a88-405">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-405">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style"></a><a name="MStyle"></a><span data-ttu-id="81a88-406">e.</span><span class="sxs-lookup"><span data-stu-id="81a88-406">1e.</span></span> <span data-ttu-id="81a88-407">스타일 선택</span><span class="sxs-lookup"><span data-stu-id="81a88-407">Choose a Style</span></span>  
 <span data-ttu-id="81a88-408">Slate 스타일을 보고서에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-408">Apply the Slate style to the report.</span></span> <span data-ttu-id="81a88-409">이는 드릴스루 보고서가 사용하는 동일한 스타일입니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-409">This is the same style that the drillthrough report uses.</span></span>  
  
#### <a name="to-specify-a-style"></a><span data-ttu-id="81a88-410">스타일을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-410">To specify a style</span></span>  
  
1.  <span data-ttu-id="81a88-411">**스타일 선택** 페이지의 스타일 창에서 슬레이트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-411">On the **Choose a Style** page, in the Styles pane, select Slate.</span></span>  
  
2.  <span data-ttu-id="81a88-412">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-412">Click **Finish**.</span></span>  
  
3.  <span data-ttu-id="81a88-413">보고서를 미리 보려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-413">To preview the report, click **Run**.</span></span>  
  
##  <a name="2-remove-the-grand-total-row"></a><a name="MGrandTotal"></a><span data-ttu-id="81a88-414">2. 총합계 행 제거</span><span class="sxs-lookup"><span data-stu-id="81a88-414">2. Remove the Grand Total Row</span></span>  
 <span data-ttu-id="81a88-415">데이터 값은 열 그룹 합계를 포함하여 표시기 상태로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-415">The data values are shown as indictor states, including the column group totals.</span></span> <span data-ttu-id="81a88-416">총합계를 표시하는 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-416">Remove the row that displays the grand total.</span></span>  
  
#### <a name="to-remove-the-grand-total-row"></a><span data-ttu-id="81a88-417">총합계 행을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-417">To remove the grand total row</span></span>  
  
1.  <span data-ttu-id="81a88-418">디자인 뷰로 전환하려면 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-418">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="81a88-419">행렬의 마지막 행인 합계 행을 클릭하고 마우스 오른쪽 단추를 클릭한 다음 **행 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-419">Click the Total row (the last row in the matrix), right-click, and then click **Delete Rows**.</span></span>  
  
3.  <span data-ttu-id="81a88-420">보고서를 미리 보려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-420">To preview the report, click **Run**.</span></span>  
  
##  <a name="3-configure-text-box-action-for-drillthrough"></a><a name="MDrillthrough"></a><span data-ttu-id="81a88-421">3. 드릴스루에 대 한 텍스트 상자 작업 구성</span><span class="sxs-lookup"><span data-stu-id="81a88-421">3. Configure Text Box Action for Drillthrough</span></span>  
 <span data-ttu-id="81a88-422">드릴스루를 활성화하려면 주 보고서에서 입력란에 대한 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-422">To enable the drillthrough, specify an action on a text box in the main report.</span></span>  
  
#### <a name="to-enable-an-action"></a><span data-ttu-id="81a88-423">동작을 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-423">To enable an action</span></span>  
  
1.  <span data-ttu-id="81a88-424">디자인 뷰로 전환하려면 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-424">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="81a88-425">Product_Category_Name이 들어 있는 셀을 마우스 오른쪽 단추로 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-425">Right-click the cell that contains Product_Category_Name, and then click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="81a88-426">**작업** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-426">Click the **Action** tab.</span></span>  
  
4.  <span data-ttu-id="81a88-427">**보고서로 이동을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="81a88-427">Select **Go to report.**</span></span>  
  
5.  <span data-ttu-id="81a88-428">**보고서 지정**에서 **찾아보기**를 클릭한 다음 이름이 ResellerVSOnlineDrillthrough인 드릴스루 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-428">In **Specify a report**, click **Browse**, and then locate the drillthrough report named ResellerVSOnlineDrillthrough.</span></span>  
  
6.  <span data-ttu-id="81a88-429">드릴스루 보고서를 실행할 매개 변수를 추가하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-429">To add a parameter to run the drillthrough report, click **Add**.</span></span>  
  
7.  <span data-ttu-id="81a88-430">**이름** 목록에서 ProductProductCategoryName을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-430">In the **Name** list, select ProductProductCategoryName.</span></span>  
  
8.  <span data-ttu-id="81a88-431">**값**에서`[Product_Category_Name.UniqueName]`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-431">In **Value**, type `[Product_Category_Name.UniqueName]`.</span></span>  
  
     <span data-ttu-id="81a88-432">Product_Category_Name은 데이터 세트의 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-432">Product_Category_Name is a field in the dataset.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="81a88-433">드릴스루 동작의 경우 고유한 값이 필요하므로 `UniqueName` 속성을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-433">You must include the `UniqueName` property because the drillthrough action requires a unique value.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-format-the-drillthrough-field"></a><span data-ttu-id="81a88-434">드릴스루 필드의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-434">To format the drillthrough field</span></span>  
  
1.  <span data-ttu-id="81a88-435">`Product_Category_Name`이 들어 있는 셀을 마우스 오른쪽 단추로 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-435">Right-click the cell that contains the `Product_Category_Name`, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="81a88-436">**글꼴** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-436">Click the **Font** tab.</span></span>  
  
3.  <span data-ttu-id="81a88-437">**효과** 목록에서 **밑줄**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-437">In the **Effects** list, select **Underline**.</span></span>  
  
4.  <span data-ttu-id="81a88-438">**색** 목록에서 **파랑**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-438">In the **Color** list, select **Blue**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="81a88-439">보고서를 미리 보려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-439">To preview your report, click **Run**.</span></span>  
  
 <span data-ttu-id="81a88-440">제품 범주 이름은 파랑의 밑줄이 지정된 공통적인 링크 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-440">The product category names are in the common link format (blue and underlined).</span></span>  
  
##  <a name="4-replace-numeric-values-with-indicators"></a><a name="MIndicators"></a><span data-ttu-id="81a88-441">4. 숫자 값을 표시기로 바꾸기</span><span class="sxs-lookup"><span data-stu-id="81a88-441">4. Replace Numeric Values with Indicators</span></span>  
 <span data-ttu-id="81a88-442">표시기를 사용하여 온라인 및 대리점 채널에 대한 수량 및 판매 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-442">Use indicators to show the state of quantities and sales for Online and Reseller channels.</span></span>  
  
#### <a name="to-add-an-indicator-for-net-qty-values"></a><span data-ttu-id="81a88-443">Net QTY 값에 대한 표시기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-443">To add an indicator for Net QTY values</span></span>  
  
1.  <span data-ttu-id="81a88-444">디자인 뷰로 전환하려면 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-444">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="81a88-445">리본에서 **사각형** 아이콘을 클릭한 다음 `[Sum(Net QTY)]` 열 그룹의 `[Product_Category_Name]` 행 그룹에 있는 `Channel_Name` 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-445">On the ribbon, click the **Rectangle** icon, and then click in the `[Sum(Net QTY)]` cell in the `[Product_Category_Name]` row group in the `Channel_Name` column group.</span></span>  
  
3.  <span data-ttu-id="81a88-446">리본에서 **표시기** 아이콘을 클릭한 다음 사각형 내부를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-446">On the ribbon, click the **Indicator** icon, and then click inside the rectangle.</span></span> <span data-ttu-id="81a88-447">**방향** 표시기가 선택된 **표시기 유형 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-447">The **Select Indicator Type** dialog box opens with the **Directional** indicator selected.</span></span>  
  
4.  <span data-ttu-id="81a88-448">**3가지 모양** 유형을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-448">Click the **3 Signs** type, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="81a88-449">표시기를 마우스 오른쪽 단추로 클릭하고 계기 데이터 창에서 **(지정하지 않음)** 옆에 있는 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-449">Right-click the indicator and in the Gauge Data pane, click the down arrow next to **(Unspecified)**.</span></span> <span data-ttu-id="81a88-450">`Net_QTY`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-450">Select `Net_QTY`.</span></span>  
  
6.  <span data-ttu-id="81a88-451">`[Sum(Net QTY)]` Total `[Product_Category_Name]` 내의 **행 그룹에 있는**셀에 대해 2 ~ 5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-451">Repeat steps 2 through 5 for the `[Sum(Net QTY)]` cell in the `[Product_Category_Name]` row group within **Total**.</span></span>  
  
#### <a name="to-add-an-indicator-for-net-sales-values"></a><span data-ttu-id="81a88-452">Net Sales 값에 대한 표시기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-452">To add an indicator for Net Sales values</span></span>  
  
1.  <span data-ttu-id="81a88-453">리본에서 **사각형** 아이콘을 클릭한 다음 `[Sum(Net_Sales)]` 열 그룹의 `[Product_Category_Name]` 행 그룹에 있는 `Channel_Name` 셀 안쪽을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-453">On the ribbon, click the **Rectangle** icon, and then click inside the `[Sum(Net_Sales)]` cell in the `[Product_Category_Name]` row group in the `Channel_Name` column group.</span></span>  
  
2.  <span data-ttu-id="81a88-454">리본에서 **표시기** 아이콘을 클릭한 다음 사각형 내부를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-454">On the ribbon, click the **Indicator** icon, and then click inside the rectangle.</span></span>  
  
3.  <span data-ttu-id="81a88-455">**3가지 모양** 유형을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-455">Click the **3 Signs** type, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="81a88-456">표시기를 마우스 오른쪽 단추로 클릭하고 계기 데이터 창에서 **(지정하지 않음)** 옆에 있는 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-456">Right-click the indicator and in the Gauge Data pane, click the down arrow next to **(Unspecified)**.</span></span> <span data-ttu-id="81a88-457">`Net_Sales`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-457">Select `Net_Sales`.</span></span>  
  
5.  <span data-ttu-id="81a88-458">`[Sum(Net_Sales)]` Total `[Product_Category_Name]` 내의 **행 그룹에 있는**셀에 대해 1 ~ 4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-458">Repeat steps 1 through 4 for the `[Sum(Net_Sales)]` cell in the `[Product_Category_Name]` row group within **Total**.</span></span>  
  
6.  <span data-ttu-id="81a88-459">보고서를 미리 보려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-459">To preview your report, click **Run**.</span></span>  
  
##  <a name="5-update-parameter-properties"></a><a name="MParameter"></a><span data-ttu-id="81a88-460">5. 매개 변수 속성 업데이트</span><span class="sxs-lookup"><span data-stu-id="81a88-460">5. Update Parameter Properties</span></span>  
 <span data-ttu-id="81a88-461">기본적으로 매개 변수가 표시되는데 이는 이 보고서의 경우 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-461">By default, parameters are visible, which is not appropriate for this report.</span></span> <span data-ttu-id="81a88-462">매개 변수를 내부 매개 변수로 만들도록 매개 변수 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-462">You will update the parameter properties to make the parameter internal.</span></span>  
  
#### <a name="to-make-the-parameter-internal"></a><span data-ttu-id="81a88-463">매개 변수를 내부 매개 변수로 만들려면</span><span class="sxs-lookup"><span data-stu-id="81a88-463">To make the parameter internal</span></span>  
  
1.  <span data-ttu-id="81a88-464">보고서 데이터 창에서 **매개 변수**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-464">In the Report Data pane, expand **Parameters**.</span></span>  
  
2.  <span data-ttu-id="81a88-465">`@ProductProductCategoryName,` 을 마우스 오른쪽 단추로 클릭한 다음 **매개 변수 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-465">Right-click `@ProductProductCategoryName,` and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="81a88-466">**일반** 탭에서 **내부**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-466">On the **General** tab, click **Internal**.</span></span>  
  
4.  <span data-ttu-id="81a88-467">필요에 따라 **사용 가능한 값** 및 **기본값** 탭을 클릭하고 해당 옵션을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-467">Optionally, click the **Available Values** and **Default Values** tabs and review their options.</span></span> <span data-ttu-id="81a88-468">이러한 탭에 대한 어떤 옵션도 변경하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="81a88-468">Do not change any options on these tabs.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-add-a-report-title"></a><a name="MTitle"></a><span data-ttu-id="81a88-469">6. 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="81a88-469">6. Add a Report Title</span></span>  
 <span data-ttu-id="81a88-470">주 보고서에 제목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-470">Add a title to the main report.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="81a88-471">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-471">To add a report title</span></span>  
  
1.  <span data-ttu-id="81a88-472">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-472">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="81a88-473">**2009 Product Category Sales: Online and Reseller Category:** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-473">Type **2009 Product Category Sales: Online and Reseller Category:**.</span></span>  
  
3.  <span data-ttu-id="81a88-474">입력한 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-474">Select the text you typed.</span></span>  
  
4.  <span data-ttu-id="81a88-475">리본의 **홈** 탭에 있는 글꼴 그룹에서 **Times New Roman** 글꼴, **16pt** 크기, **굵게** 및 **기울임꼴** 스타일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-475">On the **Home** tab of the ribbon, in the Font group, select the **Times New Roman** font, **16pt** size, and the **Bold** and **Italic** styles.</span></span>  
  
5.  <span data-ttu-id="81a88-476">보고서를 미리 보려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-476">To preview your report, click **Run**.</span></span>  
  
##  <a name="7-save-the-main-report-to-a-sharepoint-library"></a><a name="MSave"></a><span data-ttu-id="81a88-477">7. SharePoint 라이브러리에 주 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="81a88-477">7. Save the Main Report to a SharePoint Library</span></span>  
 <span data-ttu-id="81a88-478">SharePoint 라이브러리에 주 보고서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-478">Save the main report to a SharePoint library.</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="81a88-479">보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-479">To save the report</span></span>  
  
1.  <span data-ttu-id="81a88-480">디자인 뷰로 전환하려면 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-480">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="81a88-481">보고서 작성기 단추에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-481">From the Report Builder button, click **Save**.</span></span>  
  
3.  <span data-ttu-id="81a88-482">필요한 경우 최근에 사용한 보고서 서버와 SharePoint 사이트의 목록을 표시하려면 **최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-482">Optionally, to show a list of recently used report servers and SharePoint sites, click **Recent Sites and Servers**.</span></span>  
  
4.  <span data-ttu-id="81a88-483">보고서를 저장할 수 있는 권한을 가진 SharePoint 사이트의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-483">Select or type the name of the SharePoint site where you have permission to save reports.</span></span> <span data-ttu-id="81a88-484">SharePoint 라이브러리의 URL에 다음 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-484">The URL of the SharePoint library has the following syntax:</span></span>  
  
    ```  
    Http://<ServerName>/<Sites>/  
    ```  
  
5.  <span data-ttu-id="81a88-485">보고서를 저장할 라이브러리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-485">Navigate to the library where you want to save the report.</span></span>  
  
6.  <span data-ttu-id="81a88-486">**이름**에서 기본 이름을 **ResellerVSOnlineMain**으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-486">In **Name**, replace the default name with **ResellerVSOnlineMain**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="81a88-487">드릴스루 보고서를 저장한 동일한 위치에 주 보고서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-487">Save the main report to the same location where you saved the drillthrough report.</span></span> <span data-ttu-id="81a88-488">주 보고서 및 드릴스루 보고서를 다른 사이트 또는 라이브러리에 저장하려면 주 보고서의 **보고서로 이동** 동작이 드릴스루 보고서의 올바른 위치를 가리키는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-488">To save the main and drillthrough reports to different sites or libraries, confirm that the **Go to report** action in the main report, points to the correct location of the drillthrough report.</span></span>  
  
7.  <span data-ttu-id="81a88-489">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-489">Click **Save**.</span></span>  
  
##  <a name="8-run-the-main-and-drillthrough-reports"></a><a name="MRunReports"></a><span data-ttu-id="81a88-490">8. 주 보고서 및 드릴스루 보고서 실행</span><span class="sxs-lookup"><span data-stu-id="81a88-490">8. Run the Main and Drillthrough Reports</span></span>  
 <span data-ttu-id="81a88-491">주 보고서를 실행한 다음 제품 범주 열의 값을 클릭하여 드릴스루 보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-491">Run the main report, and then click values in the product category column to run the drillthrough report.</span></span>  
  
#### <a name="to-run-the-reports"></a><span data-ttu-id="81a88-492">보고서를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="81a88-492">To run the reports</span></span>  
  
1.  <span data-ttu-id="81a88-493">보고서가 저장된 SharePoint 라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-493">Open the SharePoint library where the reports are saved.</span></span>  
  
2.  <span data-ttu-id="81a88-494">ResellerVSOnlineMain을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-494">Double-click ResellerVSOnlineMain.</span></span>  
  
     <span data-ttu-id="81a88-495">보고서에서 제품 범주 판매 정보를 실행하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-495">The report runs and displays product category sales information.</span></span>  
  
3.  <span data-ttu-id="81a88-496">제품 범주 이름이 들어 있는 열에서 **Games and Toys** 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-496">Click the **Games and Toys** link in the column that contains product category names.</span></span>  
  
     <span data-ttu-id="81a88-497">드릴스루 보고서가 실행되어 Games and Toys 제품 범주에 대한 값만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-497">The drillthrough report runs, displaying only the values for the Games and Toys product category.</span></span>  
  
4.  <span data-ttu-id="81a88-498">주 보고서로 돌아가려면 Internet Explorer에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-498">To return to the main report, click the Internet Explorer back button.</span></span>  
  
5.  <span data-ttu-id="81a88-499">필요에 따라 다른 제품 범주의 이름을 클릭하여 해당 제품 범주를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="81a88-499">Optionally, explore other product categories by clicking their names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a88-500">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81a88-500">See Also</span></span>  
 [<span data-ttu-id="81a88-501">자습서 &#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="81a88-501">Tutorials &#40;Report Builder&#41;</span></span>](report-builder-tutorials.md)  
  
  
