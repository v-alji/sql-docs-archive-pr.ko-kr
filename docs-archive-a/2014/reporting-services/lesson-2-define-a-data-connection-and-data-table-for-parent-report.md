---
title: '2단원: 부모 보고서에 대한 데이터 연결 및 데이터 테이블 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f02dee0c-85ad-45d4-b707-10e9e8541db9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 045ff576061bf12d163668cb9a57651e591768a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646830"
---
# <a name="lesson-2-define-a-data-connection-and-data-table-for-parent-report"></a><span data-ttu-id="6f542-102">2단원: 부모 보고서에 대한 데이터 연결 및 데이터 테이블 정의</span><span class="sxs-lookup"><span data-stu-id="6f542-102">Lesson 2: Define a Data Connection and Data Table for Parent Report</span></span>
  <span data-ttu-id="6f542-103">Visual C#용 ASP.NET 웹 사이트 템플릿을 사용하여 새 웹 사이트 프로젝트를 만든 후에는 부모 보고서에 대한 데이터 연결 및 데이터 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-103">After you create a new website project using the ASP.NET website template for Visual C#, your next step is to create a data connection and a data table for the parent report.</span></span> <span data-ttu-id="6f542-104">이 자습서에서 데이터 연결은 AdventureWorks2008 데이터베이스에 대한 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-104">In this tutorial the data connection is to the AdventureWorks2008 database.</span></span> <span data-ttu-id="6f542-105">AdventureWorks2012 데이터베이스에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-105">You also have the option of connecting to the AdventureWorks2012 database.</span></span>  
  
### <a name="to-define-a-data-connection-and-data-table-by-adding-a-dataset-for-parent-report"></a><span data-ttu-id="6f542-106">DataSet을 추가하여 자식 보고서에 대한 데이터 연결 및 데이터 테이블을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="6f542-106">To define a data connection and Data Table by adding a DataSet (for parent report)</span></span>  
  
1.  <span data-ttu-id="6f542-107">**웹 사이트** 메뉴에서 **새 항목 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-107">On the **Website** menu, select **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="6f542-108">**새 항목 추가** 대화 상자에서 **DataSet**을 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-108">In the **Add New Item** dialog box, select **DataSet** and click **Add**.</span></span> <span data-ttu-id="6f542-109">메시지가 표시되면 **예** 를 클릭하여 **App_Code**폴더에 항목을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-109">When prompted you should add the item to the **App_Code** folder by clicking **Yes**.</span></span>  
  
     <span data-ttu-id="6f542-110">그러면 프로젝트에 새 XSD 파일 **DataSet1.xsd**가 추가되고 데이터 세트 디자이너가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-110">This adds a new XSD file **DataSet1.xsd** to the project and opens the DataSet Designer.</span></span>  
  
3.  <span data-ttu-id="6f542-111">도구 상자 창에서 **[TableAdapter](https://msdn.microsoft.com/library/bz9tthwx\(v=vs.100\).aspx)** 컨트롤을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-111">From the Toolbox window, drag a **[TableAdapter](https://msdn.microsoft.com/library/bz9tthwx\(v=vs.100\).aspx)** control to the design surface.</span></span> <span data-ttu-id="6f542-112">그러면 **TableAdapter** 구성 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-112">This launches the **TableAdapter** Configuration Wizard.</span></span>  
  
4.  <span data-ttu-id="6f542-113">**데이터 연결 선택** 페이지에서 **새 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-113">On the **Choose Your Data Connection** page, click **New Connection**.</span></span>  
  
5.  <span data-ttu-id="6f542-114">Visual Studio에서 데이터 원본을 처음 만든 경우 **데이터 원본 선택** 페이지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-114">If this is the first time you've created a data source in Visual Studio, you will see the **Choose Data Source** page.</span></span> <span data-ttu-id="6f542-115">**데이터 원본** 상자에서 **Microsoft SQL Server**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-115">In the **Data Source** box, select **Microsoft SQL Server**.</span></span>  
  
6.  <span data-ttu-id="6f542-116">**연결 추가** 대화 상자에서 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-116">In the **Add Connection** dialog box, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="6f542-117">**서버 이름** 상자에 **AdventureWorks2008** 데이터베이스가 있는 서버를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-117">In the **Server name** box, enter the server where the **AdventureWorks2008** database is located.</span></span>  
  
         <span data-ttu-id="6f542-118">기본 SQL Server Express 인스턴스는 **(local)\sqlexpress**입니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-118">The default SQL Server Express instance is **(local)\sqlexpress**.</span></span>  
  
    2.  <span data-ttu-id="6f542-119">**서버에 로그온** 섹션에서 데이터에 액세스할 수 있는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-119">In the **Log on to the server** section, select the option that provides you access to the data.</span></span> <span data-ttu-id="6f542-120">**Windows 인증 사용** 이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-120">**Use Windows Authentication** is the default.</span></span>  
  
    3.  <span data-ttu-id="6f542-121">**데이터베이스 이름 선택 또는 입력** 드롭다운 목록에서 **AdventureWorks2008**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-121">From the **Select or enter a database name** drop-down list, click **AdventureWorks2008**.</span></span>  
  
    4.  <span data-ttu-id="6f542-122">**확인**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-122">Click **OK**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="6f542-123">6단계 (b)에서 **SQL Server 인증 사용** 을 선택한 경우 문자열에 중요한 데이터를 포함할지 애플리케이션 코드에 정보를 설정할지 여부에 대한 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-123">If you selected **Use SQL Server Authentication** in the Step 6 (b), select the option whether to include the sensitive data in the string or set the information in your application code.</span></span>  
  
8.  <span data-ttu-id="6f542-124">**애플리케이션 구성 파일에 연결 문자열 저장** 페이지에서 연결 문자열의 이름을 입력하거나 기본 **AdventureWorks2008ConnectionString**을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-124">On the **Save the Connection String to the Application Configuration File** page, type in the name for the connection string or accept the default **AdventureWorks2008ConnectionString**.</span></span> <span data-ttu-id="6f542-125">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-125">Click **Next**.</span></span>  
  
9. <span data-ttu-id="6f542-126">**명령 유형을 선택하십시오.** 페이지에서 **SQL 문 사용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-126">On the **Choose a Command Type** page, select **Use SQL Statements**, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="6f542-127">**SQL 문 입력** 페이지에서 다음 Transact-SQL 쿼리를 입력하여 **AdventureWorks2008** 데이터베이스에서 데이터를 검색하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-127">On the **Enter a SQL Statement** page, enter the following Transact-SQL query to retrieve data from the **AdventureWorks2008** database, and then click **Next**.</span></span>  
  
    ```  
    SELECT ProductID, Name, ProductNumber, SafetyStockLevel, ReorderPoint FROM  Production.Product Order By ProductID  
    ```  
  
     <span data-ttu-id="6f542-128">**쿼리 작성기**를 클릭하여 쿼리를 만든 다음 **쿼리 실행**을 클릭하여 쿼리를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-128">You can also create the query by clicking **Query Builder**, and then verify the query by clicking **Execute Query**.</span></span> <span data-ttu-id="6f542-129">쿼리에서 예상된 데이터가 반환되지 않는 경우 이전 버전의 AdventureWorks를 사용하고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-129">If the query does not return the expected data, you might be using an earlier version of AdventureWorks.</span></span> <span data-ttu-id="6f542-130">**AdventureWorks2008** 버전의 AdventureWorks를 설치하는 방법에 대한 자세한 내용은 [연습: AdventureWorks 데이터베이스 설치](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f542-130">For more information about installing the **AdventureWorks2008** version of AdventureWorks, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).</span></span>  
  
11. <span data-ttu-id="6f542-131">**생성할 메서드 선택** 페이지에서 **업데이트를 데이터베이스로 직접 보내는 메서드 만들기(GenerateDBDirectMethods)** 의 선택을 취소한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-131">On the **Choose Methods to Generate** page, be sure to uncheck **Create methods to send updates directly to the database (GenerateDBDirectMethods)**, and then click **Finish**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="6f542-132">만들기 선택을 취소해야 함</span><span class="sxs-lookup"><span data-stu-id="6f542-132">Be sure to uncheck Create</span></span>  
  
     <span data-ttu-id="6f542-133">이제 ADO.NET DataTable 개체를 보고서의 데이터 원본으로 구성하는 작업을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-133">You have now completed configuring the ADO.NET DataTable object as the data source for your report.</span></span> <span data-ttu-id="6f542-134">Visual Studio의 데이터 세트 디자이너 페이지에서 추가한 DataTable 개체가 표시되며 쿼리에 지정한 열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-134">On the DataSet Designer page in Visual Studio, you should see the DataTable object you added, listing the columns specified in the query.</span></span> <span data-ttu-id="6f542-135">DataSet1에는 Product 테이블에서 쿼리를 기반으로 하는 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-135">DataSet1 contains the data from the Product table, based on the query.</span></span>  
  
12. <span data-ttu-id="6f542-136">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-136">Save the file.</span></span>  
  
13. <span data-ttu-id="6f542-137">데이터를 미리 보려면 **데이터** 메뉴에서 **데이터 미리 보기** 를 클릭한 다음 **미리 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-137">To preview the data, click **Preview Data** on the **Data** menu, and then click **Preview**.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="6f542-138">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="6f542-138">Next Task</span></span>  
 <span data-ttu-id="6f542-139">부모 보고서에 대한 데이터 연결 및 데이터 테이블을 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-139">You have successfully created a data connection and a data table for the parent report.</span></span> <span data-ttu-id="6f542-140">이제 보고서 마법사를 사용하여 부모 보고서를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="6f542-140">Next, you will design the parent report using the Report Wizard.</span></span>  
  
  
