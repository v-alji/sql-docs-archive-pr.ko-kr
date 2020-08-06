---
title: '8단원: 데이터 필터 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19ccbdba-e3da-40a4-b652-32c628cf32e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c11d4cf83619e53cd7e8f00091c66cc8e50ad76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647501"
---
# <a name="lesson-8-create-a-data-filter"></a><span data-ttu-id="5242e-102">8단원: 데이터 필터 만들기</span><span class="sxs-lookup"><span data-stu-id="5242e-102">Lesson 8: Create a Data Filter</span></span>
  <span data-ttu-id="5242e-103">부모 보고서에 드릴스루 동작을 추가한 후에는 자식 보고서에 대해 정의한 데이터 테이블에 대한 데이터 필터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-103">After you add a drillthrough action on the parent report, your next step is to create a data filter for the data table that you defined for the child report.</span></span>  
  
 <span data-ttu-id="5242e-104">드릴스루 보고서에 대한 테이블 기반 필터 **또는** 쿼리 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-104">You can create a table-based filter **or** a query filter for the drillthrough report.</span></span> <span data-ttu-id="5242e-105">이 단원에서는 두 옵션에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-105">This lesson provides instructions for both options.</span></span>  
  
## <a name="table-based-filter"></a><span data-ttu-id="5242e-106">테이블 기반 필터</span><span class="sxs-lookup"><span data-stu-id="5242e-106">Table-Based Filter</span></span>  
 <span data-ttu-id="5242e-107">테이블 기반 필터를 구현하려면 다음 태스크를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-107">You need to complete the following tasks to implement a table-based filter.</span></span>  
  
-   <span data-ttu-id="5242e-108">자식 보고서의 테이블릭스에 필터 식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-108">Add a filter expression to the tablix in the child report.</span></span>  
  
-   <span data-ttu-id="5242e-109">`PurchaseOrderDetail` 테이블에서 필터링되지 않은 데이터를 선택하는 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-109">Create a function that selects unfiltered data from the `PurchaseOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="5242e-110">자식 보고서에 `PurchaseOrderDetail` DataTable을 바인딩하는 이벤트 처리기를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-110">Add an event handler that binds the `PurchaseOrderDetail` DataTable to the child report.</span></span>  
  
#### <a name="to-add-a-filter-expression-to-the-tablix-in-the-child-report"></a><span data-ttu-id="5242e-111">자식 보고서의 테이블릭스에 필터 식을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5242e-111">To add a filter expression to the tablix in the child report</span></span>  
  
1.  <span data-ttu-id="5242e-112">자식 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-112">Open the child report.</span></span>  
  
2.  <span data-ttu-id="5242e-113">테이블 릭 스에서 열 머리글을 선택 하 고 열 머리글 위에 나타나는 회색 셀을 마우스 오른쪽 단추로 클릭 한 다음 **테이블 릭 스 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-113">Select a column heading in the tablix, right-click the gray cell that appears above the column heading, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="5242e-114">**필터** 페이지를 클릭 한 다음 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-114">Click on the **Filters** page, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="5242e-115">**식** 필드의 `ProductID` 드롭다운 목록에서를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-115">In the **Expression** filed, click `ProductID` from the drop-down list.</span></span> <span data-ttu-id="5242e-116">이는 필터를 적용할 열입니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-116">This is the column to which you apply the filter.</span></span>  
  
5.  <span data-ttu-id="5242e-117">**=** **연산자** 드롭다운 목록에서 같음 () 연산자를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-117">Click the equal (**=**) operator in the **Operator** drop-down list.</span></span>  
  
6.  <span data-ttu-id="5242e-118">**값** 필드 옆의 식 단추를 클릭 하 고 **범주** 영역에서 **매개 변수** 를 클릭 한 다음 `productid` **값** 영역을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-118">Click the expression button next to the **Value** field, click **Parameters** in the **Category** area, and then double-click `productid` in the **Values** area.</span></span> <span data-ttu-id="5242e-119">이제 **다음에 대한 식 설정: 값** 필드에 **=Parameters!productid.Value**와 비슷한 식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-119">The **Set expression for: Value** field should now contain expression similar to **=Parameters!productid.Value**.</span></span>  
  
7.  <span data-ttu-id="5242e-120">**확인을** 클릭 하 고 **테이블 릭 스 속성** 대화 상자에서 **확인** 을 다시 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-120">Click **OK,** and **OK** again in the **Tablix Properties** dialog box.</span></span>  
  
8.  <span data-ttu-id="5242e-121">.rdlc 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-121">Save the .rdlc file.</span></span>  
  
#### <a name="to-create-a-function-that-selects-unfiltered-data-from-the-purchaseordedetail-table"></a><span data-ttu-id="5242e-122">PurchaseOrdeDetail 테이블에서 필터링되지 않은 데이터를 선택하는 함수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5242e-122">To create a function that selects unfiltered data from the PurchaseOrdeDetail table</span></span>  
  
1.  <span data-ttu-id="5242e-123">솔루션 탐색기에서 Default.aspx를 확장하고 Default.aspx.cs를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-123">In Solution Explorer, expand Default.aspx, and then double click Default.aspx.cs.</span></span>  
  
2.  <span data-ttu-id="5242e-124">정수 형식의 `productid` 매개 변수를 허용하고 `datatable` 개체를 반환하고 다음을 수행하는 새 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-124">Create a new function that accepts a parameter, `productid`, of type Integer and returns a `datatable` object, and does the following.</span></span>  
  
    1.  <span data-ttu-id="5242e-125">`DataSet2` [4 단원: 자식 보고서에 대 한 데이터 연결 및 데이터 테이블 정의](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)의 2 단계에서 만든 데이터 집합의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-125">Creates an instance of the dataset, `DataSet2`, which was created in Step 2 of [Lesson 4: Define a Data Connection and Data Table for Child Report](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).</span></span>  
  
    2.  <span data-ttu-id="5242e-126">SqlServer 데이터베이스에 대한 연결을 만들어 **4단원: 자식 보고서에 대한 데이터 연결 및 데이터 테이블 정의**에서 정의된 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-126">Create a connection to the SqlServer database to execute the query defined in **Lesson 4: Define a Data Connection and DataTable for Child Report**.</span></span>  
  
    3.  <span data-ttu-id="5242e-127">쿼리는 필터링되지 않은 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-127">The query will return unfiltered data.</span></span>  
  
    4.  <span data-ttu-id="5242e-128">쿼리를 실행하여 필터링되지 않은 데이터로 DataSet 인스턴스를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-128">Fill the DataSet instance with the unfiltered data by executing the query.</span></span>  
  
    5.  <span data-ttu-id="5242e-129">`PurchaseOrderDetail` DataTable을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-129">Return the `PurchaseOrderDetail` DataTable.</span></span>  
  
         <span data-ttu-id="5242e-130">함수는 아래와 비슷하며 이는 단순히 참조용입니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-130">The function will look similar to the one below, (This is just for your reference.</span></span> <span data-ttu-id="5242e-131">원하는 패턴을 따라 자식 보고서에 필요한 데이터를 인출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-131">You can follow any pattern that you want, to fetch the necessary data for child report).</span></span>  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table, fetch the  
            /// unfiltered data and bind it with the Child report  
            /// </summary>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail()  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail ", sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-binds-the-purchaseorderdetail-datatable-to-the-child-report"></a><span data-ttu-id="5242e-132">자식 보고서에 PurchaseOrderDetail DataTable을 바인딩하는 이벤트 처리기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5242e-132">To add an event handler that binds the PurchaseOrderDetail DataTable to the child report</span></span>  
  
1.  <span data-ttu-id="5242e-133">Default.aspx를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-133">Open Default.aspx.</span></span>  
  
2.  <span data-ttu-id="5242e-134">ReportViewer 컨트롤을 마우스 오른쪽 단추로 클릭 한 다음 **속성을 클릭 합니다.**</span><span class="sxs-lookup"><span data-stu-id="5242e-134">Right click the ReportViewer control, and then click **Properties.**</span></span>  
  
3.  <span data-ttu-id="5242e-135">**속성** 페이지에서 **이벤트** 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-135">On the **Properties** page, click the **Events** icon.</span></span>  
  
4.  <span data-ttu-id="5242e-136">**드릴스루** 이벤트를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-136">Double click the **Drillthrough** event.</span></span>  
  
     <span data-ttu-id="5242e-137">그러면 코드에 아래 블록과 비슷한 이벤트 처리기 섹션이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-137">This will add an event handler section in the code, which will look similar to the below block.</span></span>  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  <span data-ttu-id="5242e-138">이벤트 처리기를 완성합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-138">Complete the event handler.</span></span> <span data-ttu-id="5242e-139">이벤트 처리기에는 다음 기능이 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-139">It should include the following functionalty.</span></span>  
  
    1.  <span data-ttu-id="5242e-140">*DrillthroughEventArgs* 매개 변수에서 자식 보고서 개체 참조를 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-140">Fetch the child report object reference from the *DrillthroughEventArgs* parameter.</span></span>  
  
    2.  <span data-ttu-id="5242e-141">함수를 호출 합니다.`GetPurchaseOrderDetail`</span><span class="sxs-lookup"><span data-stu-id="5242e-141">Call the function, `GetPurchaseOrderDetail`</span></span>  
  
    3.  <span data-ttu-id="5242e-142">`PurchaseOrderDetail` DataTable을 보고서의 해당 데이터 원본과 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-142">Bind the `PurchaseOrderDetail` DataTable with the report's corresponding data source.</span></span>  
  
         <span data-ttu-id="5242e-143">완성된 이벤트 처리기 코드는 다음과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-143">The completed event handler code will look similar to the following.</span></span>  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                     //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                     //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail()));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  <span data-ttu-id="5242e-144">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-144">Save the file.</span></span>  
  
## <a name="query-filter"></a><span data-ttu-id="5242e-145">쿼리 필터</span><span class="sxs-lookup"><span data-stu-id="5242e-145">Query Filter</span></span>  
 <span data-ttu-id="5242e-146">쿼리 필터를 구현하려면 다음 태스크를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-146">You need to complete the following tasks to implement a query filter.</span></span>  
  
-   <span data-ttu-id="5242e-147">`PurchaseOrderDetail` 테이블에서 필터링된 데이터를 선택하는 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-147">Create a function that selected filtered data from the `PurchaseOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="5242e-148">매개 변수 값을 검색하고 자식 보고서에 `PurchaseOrdeDetail` DataTable을 바인딩하는 이벤트 처리기를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-148">Add an event handler that retrieves parameter values and binds the `PurchaseOrdeDetail` DataTable to the child report.</span></span>  
  
#### <a name="to-create-a-function-that-selects-filtered-data-from-the-purchaseorderdetail-table"></a><span data-ttu-id="5242e-149">PurchaseOrderDetail 테이블에서 필터링된 데이터를 선택하는 함수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5242e-149">To create a function that selects filtered data from the PurchaseOrderDetail table</span></span>  
  
1.  <span data-ttu-id="5242e-150">솔루션 탐색기에서 Default.aspx를 확장하고 Default.aspx.cs를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-150">In Solution Explorer, expand Default.aspx, and then double click Default.aspx.cs.</span></span>  
  
2.  <span data-ttu-id="5242e-151">정수 형식의 `productid` 매개 변수를 허용하고 `datatable` 개체를 반환하고 다음을 수행하는 새 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-151">Create a new function that accepts a parameter, `productid`, of type Integer and returns a `datatable` object and does the following.</span></span>  
  
    1.  <span data-ttu-id="5242e-152">`DataSet2` [4 단원: 자식 보고서에 대 한 데이터 연결 및 데이터 테이블 정의](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)의 2 단계에서 만든 데이터 집합의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-152">Creates an instance of the dataset, `DataSet2`, which was created in Step 2 of [Lesson 4: Define a Data Connection and Data Table for Child Report](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).</span></span>  
  
    2.  <span data-ttu-id="5242e-153">SqlServer 데이터베이스에 대한 연결을 만들어 **4단원: 자식 보고서에 대한 데이터 연결 및 데이터 테이블 정의**에서 정의된 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-153">Create a connection to the SqlServer database to execute the query defined **Lesson 4: Define a Data Connection and DataTable for Child Report**.</span></span>  
  
    3.  <span data-ttu-id="5242e-154">쿼리에는 반환된 데이터가 부모 보고서에서 선택한 `productid`를 기반으로 필터링되어 있는지 확인하는 `ProductID` 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-154">The query will include a parameter, `productid`, to make sure the data returned is filtered based on the `ProductID` selected in the parent report.</span></span>  
  
    4.  <span data-ttu-id="5242e-155">쿼리를 실행하여 필터링된 데이터로 DataSet 인스턴스를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-155">Fill the DataSet instance with the filtered data by executing the query.</span></span>  
  
    5.  <span data-ttu-id="5242e-156">`PurchaseOrderDetail` DataTable을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-156">Return the `PurchaseOrderDetail` DataTable.</span></span>  
  
         <span data-ttu-id="5242e-157">함수는 아래와 비슷하며 이는 단순히 참조용입니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-157">The function will look similar to the one below, (This is just for your reference.</span></span> <span data-ttu-id="5242e-158">원하는 패턴을 따라 자식 보고서에 필요한 데이터를 인출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-158">You can follow any pattern that you want, to fetch the necessary data for child report).</span></span>  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table and filter the  
            /// data for a specific ProductID selected in the Parent report.  
            /// </summary>  
            /// <param name="productid">Parameter passed from the Parent report to filter data.</param>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail(int productid)  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail where ProductID = " + productid, sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-retrieves-parameter-values-and-binds-the-purchaseordedetail-datatable-to-the-child-report"></a><span data-ttu-id="5242e-159">매개 변수 값을 검색하고 자식 보고서에 PurchaseOrdeDetail DataTable을 바인딩하는 이벤트 처리기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5242e-159">To add an event handler that retrieves parameter values and binds the PurchaseOrdeDetail DataTable to the child report</span></span>  
  
1.  <span data-ttu-id="5242e-160">Default.aspx를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-160">Open Default.aspx.</span></span>  
  
2.  <span data-ttu-id="5242e-161">ReportViewer 컨트롤을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-161">Right-click the ReportViewer control, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5242e-162">**속성** 창에서 **이벤트** 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-162">On the **Properties** pane, click the **Events** icon.</span></span>  
  
4.  <span data-ttu-id="5242e-163">**드릴스루** 이벤트를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-163">Double click the **Drillthrough** event.</span></span>  
  
     <span data-ttu-id="5242e-164">그러면 코드에 다음과 비슷한 이벤트 처리기 섹션이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-164">This will add an event handler section in the code that will look similar to the following.</span></span>  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  <span data-ttu-id="5242e-165">이벤트 처리기를 완성합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-165">Complete the event handler.</span></span> <span data-ttu-id="5242e-166">이벤트 처리기에는 다음 기능이 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-166">It should include the following functionality.</span></span>  
  
    1.  <span data-ttu-id="5242e-167">*DrillthroughEventArgs* 매개 변수에서 자식 보고서 개체 참조를 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-167">Fetch the Child report object reference from the *DrillthroughEventArgs* parameter.</span></span>  
  
    2.  <span data-ttu-id="5242e-168">인출한 자식 보고서 개체에서 자식 보고서 매개 변수 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-168">Get the child report parameter list from the child report object fetched.</span></span>  
  
    3.  <span data-ttu-id="5242e-169">매개 변수 컬렉션을 반복 처리하고 부모 보고서에서 전달되는 `ProductID` 매개 변수 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-169">Iterate through the parameter's collection and retrieve the value for the parameter, `ProductID`, passed from the parent report.</span></span>  
  
    4.  <span data-ttu-id="5242e-170">`GetPurchaseOrderDetail` 함수를 호출하고 `ProductID` 매개 변수 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-170">Call the function, `GetPurchaseOrderDetail`, and pass the value for parameter `ProductID`.</span></span>  
  
    5.  <span data-ttu-id="5242e-171">`PurchaseOrderDetail` DataTable을 보고서의 해당 데이터 원본과 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-171">Bind the `PurchaseOrderDetail` DataTable with the Report's corresponding data source.</span></span>  
  
         <span data-ttu-id="5242e-172">완성된 이벤트 처리기 코드는 다음과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-172">The completed event handler code will look similar to the following.</span></span>  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                    //Variable to store the parameter value passed from the MainReport.  
                    int productid = 0;  
  
                    //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                    //Get all the parameters passed from the main report to the target report.  
                    //OriginalParametersToDrillthrough actually returns a Generic list of   
                    //type ReportParameter.  
                    IList<ReportParameter> list = report.OriginalParametersToDrillthrough;  
  
                    //Parse through each parameters to fetch the values passed along with them.  
                    foreach (ReportParameter param in list)  
                    {  
                        //Since we know the report has only one parameter and it is not a multivalued,   
                        //we can directly fetch the first value from the Values array.  
                        productid = Convert.ToInt32(param.Values[0].ToString());  
                    }  
  
                    //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail(productid)));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  <span data-ttu-id="5242e-173">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-173">Save the file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="5242e-174">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="5242e-174">Next Task</span></span>  
 <span data-ttu-id="5242e-175">자식 보고서에 대해 정의한 데이터 테이블에 대한 데이터 필터를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-175">You have successfully created a data filter for the data table that you defined for the child report.</span></span> <span data-ttu-id="5242e-176">이제 웹 사이트 애플리케이션을 빌드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5242e-176">Next, you will build and run the website application.</span></span>  
  
  
