---
title: '2 단원: 데이터 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 13c3a8cc-b1db-4aba-ad9b-038b7971be8d
author: minewiskan
ms.author: owend
ms.openlocfilehash: c844ea6558949407ca9b8206601ff7fe802ec399
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648661"
---
# <a name="lesson-2-add-data"></a><span data-ttu-id="e27c1-102">2단원: 데이터 추가</span><span class="sxs-lookup"><span data-stu-id="e27c1-102">Lesson 2: Add Data</span></span>
  <span data-ttu-id="e27c1-103">이 섹션에서는 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 의 테이블 가져오기 마법사를 사용하여 AdventureWorksDW SQL Database에 연결하고, 데이터를 선택하고, 미리 보고 필터링한 다음 해당 데이터를 모델 작업 영역으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-103">In this lesson, you will use the Table Import Wizard in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to connect to the AdventureWorksDW SQL database, select data, preview, and filter the data, and then import the data into your model workspace.</span></span>  
  
 <span data-ttu-id="e27c1-104">테이블 가져오기 마법사를 사용하여 Access, SQL, Oracle, Sybase, Informix, DB2, Teradata 등 다양한 관계형 원본에서 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-104">By using the Table Import Wizard, you can import data from a variety of relational sources: Access, SQL, Oracle, Sybase, Informix, DB2, Teradata, and more.</span></span> <span data-ttu-id="e27c1-105">이러한 각 관계형 원본에서 데이터를 가져오는 단계는 아래에 설명된 과정과 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-105">The steps for importing data from each of these relational sources are very similar to what is described below.</span></span> <span data-ttu-id="e27c1-106">또한 저장 프로시저를 사용하여 데이터를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-106">Additionally, data can be selected using a stored procedure.</span></span>  
  
 <span data-ttu-id="e27c1-107">데이터를 가져오는 방법 및 데이터를 가져올 수 있는 다양한 종류의 데이터 원본에 대한 자세한 내용은 [데이터 원본&#40;SSAS 테이블 형식&#41;](data-sources-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e27c1-107">To learn more about importing data and the different types of data sources you can import from, see [Data Sources &#40;SSAS Tabular&#41;](data-sources-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="e27c1-108">이 단원을 완료하기 위한 예상 시간: **20분**</span><span class="sxs-lookup"><span data-stu-id="e27c1-108">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e27c1-109">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e27c1-109">Prerequisites</span></span>  
 <span data-ttu-id="e27c1-110">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="e27c1-111">이 단원의 작업을 수행 하기 전에 이전 단원인 [1 단원: 새 테이블 형식 모델 프로젝트 만들기](lesson-1-create-a-new-tabular-model-project.md)를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).</span></span>  
  
## <a name="create-a-connection"></a><span data-ttu-id="e27c1-112">연결 만들기</span><span class="sxs-lookup"><span data-stu-id="e27c1-112">Create a Connection</span></span>  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2012-database"></a><span data-ttu-id="e27c1-113">AdventureWorksDW2012 데이터베이스에 대한 연결을 만들려면</span><span class="sxs-lookup"><span data-stu-id="e27c1-113">To create a connection to a the AdventureWorksDW2012 database</span></span>  
  
1.  <span data-ttu-id="e27c1-114">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-114">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
     <span data-ttu-id="e27c1-115">그러면 데이터 원본에 대한 연결을 설정하는 과정을 안내하는 테이블 가져오기 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-115">This launches the Table Import Wizard which guides you through setting up a connection to a data source.</span></span> <span data-ttu-id="e27c1-116">**데이터 원본에서 가져오기** 가 회색으로 나타나면 **솔루션 탐색기** 에서 **Model.bim** 을 두 번 클릭하여 디자이너에서 모델을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-116">If **Import from Data Source** is greyed out, double click **Model.bim** in **Solution Explorer** to open the model in the designer.</span></span>  
  
2.  <span data-ttu-id="e27c1-117">**테이블 가져오기 마법사**의 **관계형 데이터베이스**에서 **Microsoft SQL Server**를 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-117">In the **Table Import Wizard**, under **Relational Databases**, click **Microsoft SQL Server**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="e27c1-118">**Microsoft SQL Server 데이터베이스에 연결** 페이지의 **연결 이름**에을 입력 `Adventure Works DB from SQL` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-118">In the **Connect to a Microsoft SQL Server Database** page, in **Friendly Connection Name**, type `Adventure Works DB from SQL`.</span></span>  
  
4.  <span data-ttu-id="e27c1-119">**서버 이름**에 AdventureWorksDW 데이터베이스가 설치되어 있는 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-119">In **Server name**, type the name of the server you installed the AdventureWorksDW database.</span></span>  
  
5.  <span data-ttu-id="e27c1-120">**데이터베이스 이름** 필드에서 아래쪽 화살표를 클릭하고 **AdventureWorksDW**를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-120">In the **Database name** field, click the down arrow and select **AdventureWorksDW**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="e27c1-121">**가장 정보** 페이지에서 데이터를 가져와 처리할 때 Analysis Services가 데이터 원본에 연결하는 데 사용할 자격 증명을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-121">In the **Impersonation Information** page, you need to specify the credentials Analysis Services will use to connect to the data source when importing and processing data.</span></span> <span data-ttu-id="e27c1-122">**특정 Windows 사용자 이름 및 암호** 가 선택되어 있는지 확인하고 **사용자 이름** 및 **암호**에 Windows 로그온 자격 증명을 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-122">Verify **Specific Windows user name and password** is selected, and then in **User Name** and **Password**, enter your Windows logon credentials, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e27c1-123">Windows 사용자 계정과 암호를 사용하면 데이터 원본에 가장 안전하게 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-123">Using a Windows user account and password provides the most secure method of connecting to a data source.</span></span> <span data-ttu-id="e27c1-124">자세한 내용은 [가장&#40;SSAS 테이블 형식&#41;](tabular-models/impersonation-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e27c1-124">For more information, see [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).</span></span>  
  
7.  <span data-ttu-id="e27c1-125">**데이터를 가져오는 방법 선택** 페이지에서 **데이터를 가져올 테이블 및 뷰를 목록에서 선택** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-125">In the **Choose How to Import the Data** page, verify **Select from a list of tables and views to choose the data to import** is selected.</span></span> <span data-ttu-id="e27c1-126">**다음** 을 클릭하여 원본 데이터베이스에 있는 모든 원본 테이블 목록을 표시할 수 있도록 테이블 및 뷰를 목록에서 선택하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-126">You want to select from a list of tables and views, so click **Next** to display a list of all the source tables in the source database.</span></span>  
  
8.  <span data-ttu-id="e27c1-127">**테이블 및 뷰 선택** 페이지에서 **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**및 **FactInternetSales**테이블의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-127">In the **Select Tables and Views** page, select the check box for the following tables: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, and **FactInternetSales**.</span></span>  
  
9. <span data-ttu-id="e27c1-128">모델의 테이블에 알아보기 쉬운 이름을 지정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-128">We want to give the tables in the model more easily understood names.</span></span> <span data-ttu-id="e27c1-129">**DimCustomer** 의 **이름**열에서 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-129">Click on the cell in the **Friendly Name** column for **DimCustomer**.</span></span> <span data-ttu-id="e27c1-130">나이 고객에서 "Dim"을 제거 하 여 테이블의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-130">Rename the table by removing "Dim" from DimCustomer.</span></span>  
  
10. <span data-ttu-id="e27c1-131">다른 테이블의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-131">Rename the other tables:</span></span>  
  
    |<span data-ttu-id="e27c1-132">원본 이름</span><span class="sxs-lookup"><span data-stu-id="e27c1-132">Source name</span></span>|<span data-ttu-id="e27c1-133">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="e27c1-133">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e27c1-134">FactOnlineSales</span><span class="sxs-lookup"><span data-stu-id="e27c1-134">DimDate</span></span>|<span data-ttu-id="e27c1-135">Date</span><span class="sxs-lookup"><span data-stu-id="e27c1-135">Date</span></span>|  
    |<span data-ttu-id="e27c1-136">DimGeography</span><span class="sxs-lookup"><span data-stu-id="e27c1-136">DimGeography</span></span>|<span data-ttu-id="e27c1-137">Geography</span><span class="sxs-lookup"><span data-stu-id="e27c1-137">Geography</span></span>|  
    |<span data-ttu-id="e27c1-138">DimProduct</span><span class="sxs-lookup"><span data-stu-id="e27c1-138">DimProduct</span></span>|<span data-ttu-id="e27c1-139">제품</span><span class="sxs-lookup"><span data-stu-id="e27c1-139">Product</span></span>|  
    |<span data-ttu-id="e27c1-140">DimProductCategory</span><span class="sxs-lookup"><span data-stu-id="e27c1-140">DimProductCategory</span></span>|<span data-ttu-id="e27c1-141">제품 범주</span><span class="sxs-lookup"><span data-stu-id="e27c1-141">Product Category</span></span>|  
    |<span data-ttu-id="e27c1-142">DimProductSubcategory</span><span class="sxs-lookup"><span data-stu-id="e27c1-142">DimProductSubcategory</span></span>|<span data-ttu-id="e27c1-143">Product Subcategory</span><span class="sxs-lookup"><span data-stu-id="e27c1-143">Product Subcategory</span></span>|  
    |<span data-ttu-id="e27c1-144">FactInternetSales</span><span class="sxs-lookup"><span data-stu-id="e27c1-144">FactInternetSales</span></span>|<span data-ttu-id="e27c1-145">Internet Sales</span><span class="sxs-lookup"><span data-stu-id="e27c1-145">Internet Sales</span></span>|  
  
     <span data-ttu-id="e27c1-146">**마침** 을 클릭하지 **마십시오**.</span><span class="sxs-lookup"><span data-stu-id="e27c1-146">**DO NOT** click **Finish**.</span></span>  
  
 <span data-ttu-id="e27c1-147">데이터베이스에 연결하여 가져올 테이블을 선택하고 테이블에 이름을 지정했으므로 다음 섹션인 [가져오기 전에 테이블 데이터 필터링](#FilterData)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-147">Now that you have connected to the database, selected the tables to import, and given the tables friendly names, go to the next section, [Filter the Table Data prior to Importing](#FilterData).</span></span>  
  
##  <a name="filter-the-table-data"></a><a name="FilterData"></a><span data-ttu-id="e27c1-148">테이블 데이터 필터링</span><span class="sxs-lookup"><span data-stu-id="e27c1-148">Filter the Table Data</span></span>  
 <span data-ttu-id="e27c1-149">데이터베이스에서 가져온 DimCustomer 테이블에는 원래 SQL Server Adventure Works 데이터베이스의 데이터 하위 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-149">The DimCustomer table that you are importing from the database contains a subset of the data from the original SQL Server Adventure Works database.</span></span> <span data-ttu-id="e27c1-150">필요 하지 않은 행 중 일부는 행 필터를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-150">You will filter out some of the columns from the DimCustomer table that aren't necessary.</span></span> <span data-ttu-id="e27c1-151">가능하면 모델에 사용되는 메모리 내 공간을 절약하기 위해 사용하지 않을 데이터는 필터링하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-151">When possible, you will want to filter out data that will not be used in order to save in-memory space used by the model.</span></span>  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a><span data-ttu-id="e27c1-152">가져오기 전에 테이블 데이터를 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="e27c1-152">To filter the table data prior to importing</span></span>  
  
1.  <span data-ttu-id="e27c1-153">**Customer** 테이블에 대한 행을 선택하고 **미리 보기 및 필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-153">Select the row for the **Customer** table, and then click **Preview & Filter**.</span></span> <span data-ttu-id="e27c1-154">DimCustomer 원본 테이블의 모든 열이 표시된 상태로 **선택한 테이블 미리 보기** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-154">The **Preview Selected Table** window opens with all the columns in the DimCustomer source table displayed.</span></span>  
  
2.  <span data-ttu-id="e27c1-155">다음 열의 맨 위에 있는 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-155">Clear the checkbox at the top of the following columns:</span></span>  
  
    |<span data-ttu-id="e27c1-156">Customer</span><span class="sxs-lookup"><span data-stu-id="e27c1-156">Customer</span></span>|  
    |--------------|  
    |<span data-ttu-id="e27c1-157">**SpanishEducation**</span><span class="sxs-lookup"><span data-stu-id="e27c1-157">**SpanishEducation**</span></span>|  
    |<span data-ttu-id="e27c1-158">**FrenchEducation**</span><span class="sxs-lookup"><span data-stu-id="e27c1-158">**FrenchEducation**</span></span>|  
    |<span data-ttu-id="e27c1-159">**SpanishOccupation**</span><span class="sxs-lookup"><span data-stu-id="e27c1-159">**SpanishOccupation**</span></span>|  
    |<span data-ttu-id="e27c1-160">**FrenchOccupation**</span><span class="sxs-lookup"><span data-stu-id="e27c1-160">**FrenchOccupation**</span></span>|  
  
     <span data-ttu-id="e27c1-161">이러한 열의 값은 인터넷 매출 분석과 관련이 없으므로 가져올 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-161">Since the values for these columns are not relevant to Internet sales analysis, there is no need to import these columns.</span></span> <span data-ttu-id="e27c1-162">필요 없는 열을 제거하면 모델의 크기가 작아집니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-162">Eliminating unnecessary columns will make your model smaller.</span></span>  
  
3.  <span data-ttu-id="e27c1-163">이외의 다른 열이 모두 선택되어 있는지 확인하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-163">Verify that all other columns are checked, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e27c1-164">이제 적용 된 **필터** 라는 단어가 **Customer** 행의 **필터 세부 정보** 열에 표시 되는지 확인 합니다. 이 링크를 클릭 하면 방금 적용 한 필터에 대 한 텍스트 설명이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-164">Notice the words **Applied filters** are now displayed in the **Filter Details** column in the **Customer** row; if you click on that link you'll see a text description of the filters you just applied.</span></span>  
  
4.  <span data-ttu-id="e27c1-165">나머지 각 테이블에서 다음 열에 대한 확인란의 선택을 취소하여 테이블을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-165">Filter the remaining tables by clearing the checkboxes for the following columns in each table:</span></span>  
  
    |<span data-ttu-id="e27c1-166">Date</span><span class="sxs-lookup"><span data-stu-id="e27c1-166">Date</span></span>|  
    |----------|  
    |<span data-ttu-id="e27c1-167">**DateKey**</span><span class="sxs-lookup"><span data-stu-id="e27c1-167">**DateKey**</span></span>|  
    |<span data-ttu-id="e27c1-168">**SpanishDayNameOfWeek**</span><span class="sxs-lookup"><span data-stu-id="e27c1-168">**SpanishDayNameOfWeek**</span></span>|  
    |<span data-ttu-id="e27c1-169">**FrenchDayNameOfWeek**</span><span class="sxs-lookup"><span data-stu-id="e27c1-169">**FrenchDayNameOfWeek**</span></span>|  
    |<span data-ttu-id="e27c1-170">**SpanishMonthName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-170">**SpanishMonthName**</span></span>|  
    |<span data-ttu-id="e27c1-171">**FrenchMonthName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-171">**FrenchMonthName**</span></span>|  
  
    |<span data-ttu-id="e27c1-172">Geography</span><span class="sxs-lookup"><span data-stu-id="e27c1-172">Geography</span></span>|  
    |---------------|  
    |<span data-ttu-id="e27c1-173">**SpanishCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-173">**SpanishCountryRegionName**</span></span>|  
    |<span data-ttu-id="e27c1-174">**FrenchCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-174">**FrenchCountryRegionName**</span></span>|  
    |<span data-ttu-id="e27c1-175">**IpAddressLocator**</span><span class="sxs-lookup"><span data-stu-id="e27c1-175">**IpAddressLocator**</span></span>|  
  
    |<span data-ttu-id="e27c1-176">제품</span><span class="sxs-lookup"><span data-stu-id="e27c1-176">Product</span></span>|  
    |-------------|  
    |<span data-ttu-id="e27c1-177">**SpanishProductName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-177">**SpanishProductName**</span></span>|  
    |<span data-ttu-id="e27c1-178">**FrenchProductName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-178">**FrenchProductName**</span></span>|  
    |<span data-ttu-id="e27c1-179">**FrenchDescription**</span><span class="sxs-lookup"><span data-stu-id="e27c1-179">**FrenchDescription**</span></span>|  
    |<span data-ttu-id="e27c1-180">**ChineseDescription**</span><span class="sxs-lookup"><span data-stu-id="e27c1-180">**ChineseDescription**</span></span>|  
    |<span data-ttu-id="e27c1-181">**ArabicDescription**</span><span class="sxs-lookup"><span data-stu-id="e27c1-181">**ArabicDescription**</span></span>|  
    |<span data-ttu-id="e27c1-182">**HebrewDescription**</span><span class="sxs-lookup"><span data-stu-id="e27c1-182">**HebrewDescription**</span></span>|  
    |<span data-ttu-id="e27c1-183">**ThaiDescription**</span><span class="sxs-lookup"><span data-stu-id="e27c1-183">**ThaiDescription**</span></span>|  
    |<span data-ttu-id="e27c1-184">**GermanDescription**</span><span class="sxs-lookup"><span data-stu-id="e27c1-184">**GermanDescription**</span></span>|  
    |<span data-ttu-id="e27c1-185">**JapaneseDescription**</span><span class="sxs-lookup"><span data-stu-id="e27c1-185">**JapaneseDescription**</span></span>|  
    |<span data-ttu-id="e27c1-186">**TurkishDescription**</span><span class="sxs-lookup"><span data-stu-id="e27c1-186">**TurkishDescription**</span></span>|  
  
    |<span data-ttu-id="e27c1-187">제품 범주</span><span class="sxs-lookup"><span data-stu-id="e27c1-187">Product Category</span></span>|  
    |----------------------|  
    |<span data-ttu-id="e27c1-188">**SpanishProductCategoryName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-188">**SpanishProductCategoryName**</span></span>|  
    |<span data-ttu-id="e27c1-189">**FrenchProductCategoryName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-189">**FrenchProductCategoryName**</span></span>|  
  
    |<span data-ttu-id="e27c1-190">Product Subcategory</span><span class="sxs-lookup"><span data-stu-id="e27c1-190">Product Subcategory</span></span>|  
    |-------------------------|  
    |<span data-ttu-id="e27c1-191">**SpanishProductSubcategoryName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-191">**SpanishProductSubcategoryName**</span></span>|  
    |<span data-ttu-id="e27c1-192">**FrenchProductSubcategoryName**</span><span class="sxs-lookup"><span data-stu-id="e27c1-192">**FrenchProductSubcategoryName**</span></span>|  
  
    |<span data-ttu-id="e27c1-193">Internet Sales</span><span class="sxs-lookup"><span data-stu-id="e27c1-193">Internet Sales</span></span>|  
    |--------------------|  
    |<span data-ttu-id="e27c1-194">**OrderDateKey**</span><span class="sxs-lookup"><span data-stu-id="e27c1-194">**OrderDateKey**</span></span>|  
    |<span data-ttu-id="e27c1-195">**DueDateKey**</span><span class="sxs-lookup"><span data-stu-id="e27c1-195">**DueDateKey**</span></span>|  
    |<span data-ttu-id="e27c1-196">**ShipDateKey**</span><span class="sxs-lookup"><span data-stu-id="e27c1-196">**ShipDateKey**</span></span>|  
  
 <span data-ttu-id="e27c1-197">데이터를 미리 보고 필요 없는 데이터를 필터링했으므로 이제 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-197">Now that you have previewed and filtered out unnecessary data, you can import the data.</span></span> <span data-ttu-id="e27c1-198">다음 섹션인 **선택한 테이블 및 열 데이터 가져오기**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-198">Go to the next section **Import the Selected Tables and Column Data**.</span></span>  
  
##  <a name="import-the-selected-tables-and-column-data"></a><a name="Import"></a><span data-ttu-id="e27c1-199">선택한 테이블 및 열 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="e27c1-199">Import the Selected Tables and Column Data</span></span>  
 <span data-ttu-id="e27c1-200">이제 선택한 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-200">You can now import the selected data.</span></span> <span data-ttu-id="e27c1-201">마법사에서는 테이블 데이터와 함께 테이블 간 관계를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-201">The wizard imports the table data along with any relationships between tables.</span></span> <span data-ttu-id="e27c1-202">앞에서 지정한 이름의 새 테이블과 열이 모델에 생성되고 필터링한 데이터는 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-202">New tables and columns are created in the model using the friendly names you specified, and data that you filtered out will not be imported.</span></span>  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a><span data-ttu-id="e27c1-203">선택한 테이블 및 열 데이터를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="e27c1-203">To import the selected tables and column data</span></span>  
  
1.  <span data-ttu-id="e27c1-204">선택 항목을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-204">Review your selections.</span></span> <span data-ttu-id="e27c1-205">잘못된 항목이 없으면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-205">If everything looks OK, click **Finish**.</span></span>  
  
     <span data-ttu-id="e27c1-206">데이터를 가져오는 동안 인출된 행의 수가 마법사에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-206">While importing the data, the wizard displays how many rows have been fetched.</span></span> <span data-ttu-id="e27c1-207">데이터를 모두 가져오면 성공을 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-207">When all the data has been imported, a message indicating success is displayed.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="e27c1-208"> 가져온 테이블 간에 자동으로 생성된 관계를 보려면 **데이터 준비** 행에서 **자세히**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-208">To see the relationships that were automatically created between the imported tables, on the **Data preparation** row, click **Details**.</span></span>  
  
2.  <span data-ttu-id="e27c1-209">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-209">Click **Close**.</span></span>  
  
     <span data-ttu-id="e27c1-210">마법사가 닫히고 모델 디자이너가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-210">The wizard closes and the model designer is visible.</span></span> <span data-ttu-id="e27c1-211">각 테이블이 모델 디자이너에 새 테이블로 추가되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-211">Each table has been added as a new tab in the model designer.</span></span>  
  
## <a name="save-the-model-project"></a><span data-ttu-id="e27c1-212">모델 프로젝트를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-212">Save the Model Project</span></span>  
 <span data-ttu-id="e27c1-213">모델 프로젝트를 자주 저장하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-213">It is important to frequently save your model project.</span></span>  
  
#### <a name="to-save-the-model-project"></a><span data-ttu-id="e27c1-214">모델 프로젝트를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="e27c1-214">To save the model project</span></span>  
  
-   <span data-ttu-id="e27c1-215">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **파일** 메뉴를 클릭한 다음 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e27c1-215">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **File** menu, and then click **Save All**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="e27c1-216">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e27c1-216">Next Step</span></span>  
 <span data-ttu-id="e27c1-217">이 자습서를 계속하려면 다음 단원인 [3단원: 열 이름 바꾸기](rename-columns.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="e27c1-217">To continue this tutorial, go to the next lesson: [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
  
