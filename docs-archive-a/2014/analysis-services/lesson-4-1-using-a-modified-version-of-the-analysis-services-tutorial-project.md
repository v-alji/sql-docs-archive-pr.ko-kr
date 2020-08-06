---
title: Analysis Services Tutorial 프로젝트의 수정 된 버전 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 685aa217-de1b-4df2-bf22-095228c40775
author: minewiskan
ms.author: owend
ms.openlocfilehash: b833a05a567f37443cf89f7356a0855e0827ea73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652421"
---
# <a name="using-a-modified-version-of-the-analysis-services-tutorial-project"></a><span data-ttu-id="4c703-102">Analysis Services Tutorial 프로젝트의 수정된 버전 사용</span><span class="sxs-lookup"><span data-stu-id="4c703-102">Using a Modified Version of the Analysis Services Tutorial Project</span></span>
  <span data-ttu-id="4c703-103">이 자습서의 나머지 단원은 처음 세 단원에서 완료한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트의 향상된 버전을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-103">The remaining lessons in this tutorial are based on an enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons.</span></span> <span data-ttu-id="4c703-104">추가 테이블과 명명된 계산이 **Adventure Works DW 2012** 데이터 원본 뷰에 추가되고 추가 차원이 프로젝트에 추가되었으며 이러한 새 차원이 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-104">Additional tables and named calculations have been added to the **Adventure Works DW 2012** data source view, additional dimensions have been added to the project, and these new dimensions have been added to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="4c703-105">또한 두 번째 팩트 테이블에서 가져온 측정값을 포함하는 두 번째 측정값 그룹이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-105">In addition, a second measure group has been added, which contains measures from a second fact table.</span></span> <span data-ttu-id="4c703-106">이 향상된 프로젝트를 사용하면 이미 배운 기술을 반복하지 않아도 비즈니스 인텔리전스 애플리케이션에 기능을 추가하는 방법을 계속 익힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-106">This enhanced project will enable you to continue learning how to add functionality to your business intelligence application without having to repeat the skills you have already learned.</span></span>  
  
 <span data-ttu-id="4c703-107">자습서를 계속 진행하려면 먼저 향상된 버전의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트를 다운로드하고 압축을 풀고 로드하고 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-107">Before you can continue with the tutorial, you must download, extract, load and process the enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span>  <span data-ttu-id="4c703-108">이 단원의 지침을 사용하여 모든 단계를 수행했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-108">Use the instructions in this lesson to ensure you have performed all the steps.</span></span>  
  
## <a name="downloading-and-extracting-the-project-file"></a><span data-ttu-id="4c703-109">프로젝트 파일 다운로드 및 압축 풀기</span><span class="sxs-lookup"><span data-stu-id="4c703-109">Downloading and Extracting the Project File</span></span>  
  
1.  <span data-ttu-id="4c703-110">이 자습서와 함께 제공되는 샘플 프로젝트를 제공하는 다운로드 페이지로 이동하려면[여기를 클릭](https://go.microsoft.com/fwlink/?LinkID=221866) 하세요.</span><span class="sxs-lookup"><span data-stu-id="4c703-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to go to the download page that provides the sample projects that go with this tutorial.</span></span> <span data-ttu-id="4c703-111">자습서 프로젝트는 **Analysis Services Tutorial SQL Server 2012** 다운로드에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-111">The tutorial projects are included in the **Analysis Services Tutorial SQL Server 2012** download.</span></span>  
  
2.  <span data-ttu-id="4c703-112">**Analysis Services Tutorial SQL Server 2012** 를 클릭하여 이 자습서에 사용할 프로젝트가 포함되어 있는 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-112">Click **Analysis Services Tutorial SQL Server 2012** to download the package that contains the projects for this tutorial.</span></span>  
  
     <span data-ttu-id="4c703-113">기본적으로 .zip 파일은 Downloads 폴더에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-113">By default, a .zip file is saved to the Downloads folder.</span></span> <span data-ttu-id="4c703-114">.zip 파일을 짧은 경로 위치로 이동해야 합니다. 예를 들어 파일을 저장할 C:\Tutorials 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-114">You must move the .zip file to a location that has a shorter path (for example, create a C:\Tutorials folder to store the files).</span></span>  <span data-ttu-id="4c703-115">그런 다음 .zip 파일에 포함된 파일의 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-115">You can then extract the files contained in the .zip file.</span></span> <span data-ttu-id="4c703-116">Downloads 폴더에 있는 긴 경로 파일의 압축을 풀면 1단원만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-116">If you attempt to unzip the files from the Downloads folder, which has a longer path, you will only get Lesson 1.</span></span>  
  
3.  <span data-ttu-id="4c703-117">루트 드라이브 또는 루트 드라이브 근처에 하위 폴더(예: C:\Tutorial)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-117">Create a subfolder at or near the root drive, for example, C:\Tutorial.</span></span>  
  
4.  <span data-ttu-id="4c703-118">**Analysis Services Tutorial SQL Server 2012.zip** 파일을 하위 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-118">Move the **Analysis Services Tutorial SQL Server 2012.zip** file to the subfolder.</span></span>  
  
5.  <span data-ttu-id="4c703-119">이 파일을 마우스 오른쪽 단추로 클릭하고 **압축 풀기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-119">Right-click the file and select **Extract All**.</span></span>  
  
6.  <span data-ttu-id="4c703-120">**Lesson 4 Start** 폴더로 이동하여 **Analysis Services Tutorial.sln** 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-120">Browse to the **Lesson 4 Start** folder to find the **Analysis Services Tutorial.sln** file.</span></span>  
  
## <a name="loading-and-processing-the-enhanced-project"></a><span data-ttu-id="4c703-121">향상된 프로젝트 로드 및 처리</span><span class="sxs-lookup"><span data-stu-id="4c703-121">Loading and Processing the Enhanced Project</span></span>  
  
1.  <span data-ttu-id="4c703-122">의 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] **파일** 메뉴에서 **솔루션 닫기** 를 클릭 하 여 사용 하지 않을 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-122">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **File** menu, click **Close Solution** to close files you won't be using.</span></span>  
  
2.  <span data-ttu-id="4c703-123">**파일** 메뉴에서 **열기**를 가리킨 다음 **프로젝트/솔루션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-123">On the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="4c703-124">자습서 프로젝트 파일의 압축을 푼 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-124">Browse to the location where you extracted the tutorial project files.</span></span>  
  
     <span data-ttu-id="4c703-125">**Lesson 4 Start**폴더를 찾은 다음 Analysis Services Tutorial.sln을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-125">Find the folder named **Lesson 4 Start**, and then double-click Analysis Services Tutorial.sln.</span></span>  
  
4.  <span data-ttu-id="4c703-126">향상된 버전의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트를 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 로컬 인스턴스나 다른 인스턴스에 배포하고 처리가 제대로 완료되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-126">Deploy the enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project to the local instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], or to another instance, and verify that processing completes successfully.</span></span>  
  
## <a name="understanding-the-enhancements-to-the-project"></a><span data-ttu-id="4c703-127">프로젝트의 향상된 기능 이해</span><span class="sxs-lookup"><span data-stu-id="4c703-127">Understanding the Enhancements to the Project</span></span>  
 <span data-ttu-id="4c703-128">향상된 버전의 프로젝트는 처음 세 단원에서 완료한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트 버전과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-128">The enhanced version of the project is different from the version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons.</span></span> <span data-ttu-id="4c703-129">그 차이에 대해서는 다음 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-129">The differences are described in the following sections.</span></span> <span data-ttu-id="4c703-130">자습서의 나머지 단원을 계속 진행하기 전에 이 내용을 검토해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="4c703-130">Review this information before continuing with the remaining lessons in the tutorial.</span></span>  
  
### <a name="data-source-view"></a><span data-ttu-id="4c703-131">데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="4c703-131">Data Source View</span></span>  
 <span data-ttu-id="4c703-132">향상된 프로젝트의 데이터 원본 뷰에는 추가 팩트 테이블 하나와 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 데이터베이스에서 가져온 추가 차원 테이블 4개가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-132">The data source view in the enhanced project contains one additional fact table and four additional dimension tables from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="4c703-133">데이터 원본 뷰의 테이블이 10개가 되면 \<All Tables> 다이어그램이 복잡해지기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-133">Notice that with ten tables in the data source view, the \<All Tables> diagram is becoming crowded.</span></span> <span data-ttu-id="4c703-134">이렇게 되면 테이블 간의 관계를 파악하고 특정 테이블을 찾기가 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-134">This makes it difficult to easily understand the relationships between the tables and to locate specific tables.</span></span> <span data-ttu-id="4c703-135">이 문제를 해결하기 위해 테이블은 두 개의 논리적 다이어그램인 **Internet Sales** 다이어그램과 **Reseller Sales** 다이어그램으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-135">To solve this problem, the tables are organized into two logical diagrams, the **Internet Sales** diagram and the **Reseller Sales** diagram.</span></span> <span data-ttu-id="4c703-136">이러한 다이어그램은 하나의 팩트 테이블 주위에 각각 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-136">These diagrams are each organized around a single fact table.</span></span> <span data-ttu-id="4c703-137">논리적 다이어그램을 만들면 항상 하나의 다이어그램에서 모든 테이블과 관계를 보는 대신 데이터 원본 뷰에서 특정 테이블 하위 집합을 보면서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-137">Creating logical diagrams lets you view and work with a specific subset of the tables in a data source view instead of always viewing all the tables and their relationships in a single diagram.</span></span>  
  
#### <a name="internet-sales-diagram"></a><span data-ttu-id="4c703-138">Internet Sales 다이어그램</span><span class="sxs-lookup"><span data-stu-id="4c703-138">Internet Sales Diagram</span></span>  
 <span data-ttu-id="4c703-139">**Internet Sales** 다이어그램에는 인터넷을 통해 고객과 직접 이루어지는 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 제품 판매와 관련된 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-139">The **Internet Sales** diagram contains the tables that are related to the sale of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] products directly to customers through the Internet.</span></span> <span data-ttu-id="4c703-140">다이어그램의 테이블은 1단원에서 **Adventure Works DW 2012** 데이터 원본 뷰에 추가한 차원 테이블 4개와 팩트 테이블 1개입니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-140">The tables in the diagram are the four dimension tables and one fact table that you added to the **Adventure Works DW 2012** data source view in Lesson 1.</span></span> <span data-ttu-id="4c703-141">이러한 테이블은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-141">These tables are as follows:</span></span>  
  
-   <span data-ttu-id="4c703-142">**지리**</span><span class="sxs-lookup"><span data-stu-id="4c703-142">**Geography**</span></span>  
  
-   <span data-ttu-id="4c703-143">**고객**</span><span class="sxs-lookup"><span data-stu-id="4c703-143">**Customer**</span></span>  
  
-   <span data-ttu-id="4c703-144">**날짜**</span><span class="sxs-lookup"><span data-stu-id="4c703-144">**Date**</span></span>  
  
-   <span data-ttu-id="4c703-145">**Product**</span><span class="sxs-lookup"><span data-stu-id="4c703-145">**Product**</span></span>  
  
-   <span data-ttu-id="4c703-146">**InternetSales**</span><span class="sxs-lookup"><span data-stu-id="4c703-146">**InternetSales**</span></span>  
  
#### <a name="reseller-sales-diagram"></a><span data-ttu-id="4c703-147">Reseller Sales 다이어그램</span><span class="sxs-lookup"><span data-stu-id="4c703-147">Reseller Sales Diagram</span></span>  
 <span data-ttu-id="4c703-148">**Reseller Sales** 다이어그램에는 대리점을 통한 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 제품 판매와 관련된 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-148">The **Reseller Sales** diagram contains the tables that are related to the sale of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] products by resellers.</span></span> <span data-ttu-id="4c703-149">이 다이어그램에는 다음과 같이 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 데이터베이스에서 가져온 차원 테이블 7개와 팩트 테이블 1개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-149">This diagram contains the following seven dimension tables and one fact table from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database:</span></span>  
  
-   <span data-ttu-id="4c703-150">**Reseller**</span><span class="sxs-lookup"><span data-stu-id="4c703-150">**Reseller**</span></span>  
  
-   <span data-ttu-id="4c703-151">**홍보 행사**</span><span class="sxs-lookup"><span data-stu-id="4c703-151">**Promotion**</span></span>  
  
-   <span data-ttu-id="4c703-152">**SalesTerritory**</span><span class="sxs-lookup"><span data-stu-id="4c703-152">**SalesTerritory**</span></span>  
  
-   <span data-ttu-id="4c703-153">**지리**</span><span class="sxs-lookup"><span data-stu-id="4c703-153">**Geography**</span></span>  
  
-   <span data-ttu-id="4c703-154">**날짜**</span><span class="sxs-lookup"><span data-stu-id="4c703-154">**Date**</span></span>  
  
-   <span data-ttu-id="4c703-155">**Product**</span><span class="sxs-lookup"><span data-stu-id="4c703-155">**Product**</span></span>  
  
-   <span data-ttu-id="4c703-156">**Employee**</span><span class="sxs-lookup"><span data-stu-id="4c703-156">**Employee**</span></span>  
  
-   <span data-ttu-id="4c703-157">**ResellerSales**</span><span class="sxs-lookup"><span data-stu-id="4c703-157">**ResellerSales**</span></span>  
  
 <span data-ttu-id="4c703-158">**DimGeography**, **DimDate**및 **DimProduct** 테이블은 **Internet Sales** 다이어그램과 **Reseller Sales** 다이어그램 둘 다에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-158">Notice that the **DimGeography**, **DimDate**, and **DimProduct** tables are used in both the **Internet Sales** diagram and the **Reseller Sales** diagram.</span></span> <span data-ttu-id="4c703-159">차원 테이블을 여러 팩트 테이블에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-159">Dimension tables can be linked to multiple fact tables.</span></span>  
  
### <a name="database-and-cube-dimensions"></a><span data-ttu-id="4c703-160">데이터베이스 및 큐브 차원</span><span class="sxs-lookup"><span data-stu-id="4c703-160">Database and Cube Dimensions</span></span>  
 <span data-ttu-id="4c703-161">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트에는 새 데이터베이스 차원 5개가 있고 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에는 큐브 차원과 동일한 차원 5개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-161">The [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project contains five new database dimensions, and the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube contains these same five dimensions as cube dimensions.</span></span> <span data-ttu-id="4c703-162">이러한 차원은 명명된 계산, 컴퍼지션 멤버 키 및 표시 폴더를 사용하여 수정된 사용자 계층과 특성을 갖도록 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-162">These dimensions have been defined to have user hierarchies and attributes that were modified by using named calculations, composition member keys, and display folders.</span></span> <span data-ttu-id="4c703-163">새로운 차원에 대해서는 다음 목록에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-163">The new dimensions are described in the following list.</span></span>  
  
 <span data-ttu-id="4c703-164">Reseller 차원</span><span class="sxs-lookup"><span data-stu-id="4c703-164">Reseller Dimension</span></span>  
 <span data-ttu-id="4c703-165">Reseller 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **Reseller** 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-165">The Reseller dimension is based on the **Reseller** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="4c703-166">Promotion 차원</span><span class="sxs-lookup"><span data-stu-id="4c703-166">Promotion Dimension</span></span>  
 <span data-ttu-id="4c703-167">Promotion 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **Promotion** 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-167">The Promotion dimension is based on the **Promotion** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="4c703-168">Sales Territory 차원</span><span class="sxs-lookup"><span data-stu-id="4c703-168">Sales Territory Dimension</span></span>  
 <span data-ttu-id="4c703-169">Sales Territory 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **SalesTerritory** 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-169">The Sales Territory dimension is based on the **SalesTerritory** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="4c703-170">Employee 차원</span><span class="sxs-lookup"><span data-stu-id="4c703-170">Employee Dimension</span></span>  
 <span data-ttu-id="4c703-171">Employee 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **Employee** 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-171">The Employee dimension is based on the **Employee** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="4c703-172">Geography 차원</span><span class="sxs-lookup"><span data-stu-id="4c703-172">Geography Dimension</span></span>  
 <span data-ttu-id="4c703-173">Geography 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **Geography** 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-173">The Geography dimension is based on the **Geography** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
#### <a name="analysis-services-cube"></a><span data-ttu-id="4c703-174">Analysis Services 큐브</span><span class="sxs-lookup"><span data-stu-id="4c703-174">Analysis Services Cube</span></span>  
 <span data-ttu-id="4c703-175">이제 **Analysis Services Tutorial** 큐브에는 두 개의 측정값 그룹, 즉 **InternetSales** 테이블을 기반으로 하는 원래의 측정값 그룹과 **Adventure Works DW 2012** 데이터 원본 뷰의 **ResellerSales** 테이블을 기반으로 하는 두 번째 측정값 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c703-175">The **Analysis Services Tutorial** cube now contains two measure groups, the original measure group based on the **InternetSales** table and a second measure group based on the **ResellerSales** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4c703-176">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="4c703-176">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4c703-177">부모-자식 계층의 부모 특성 속성 정의</span><span class="sxs-lookup"><span data-stu-id="4c703-177">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>](lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md) 
  
## <a name="see-also"></a><span data-ttu-id="4c703-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4c703-178">See Also</span></span>  
 [<span data-ttu-id="4c703-179">Analysis Services 프로젝트 배포</span><span class="sxs-lookup"><span data-stu-id="4c703-179">Deploying an Analysis Services Project</span></span>](lesson-2-5-deploying-an-analysis-services-project.md)  
  
  
