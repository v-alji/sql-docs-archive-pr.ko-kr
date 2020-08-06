---
title: '11 단원: 파티션 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4db5edd5d47fe424ef6e6ad2a822106110209059
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639058"
---
# <a name="lesson-11-create-partitions"></a><span data-ttu-id="b434b-102">11단원: 파티션 만들기</span><span class="sxs-lookup"><span data-stu-id="b434b-102">Lesson 11: Create Partitions</span></span>
  <span data-ttu-id="b434b-103">이 단원에서는 다른 파티션과 독립적으로 처리(새로 고침)할 수 있도록 파티션을 만들어 Internet Sales 테이블을 더 작은 논리적 부분으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-103">In this lesson, you will create partitions to divide the Internet Sales table into smaller logical parts that can be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="b434b-104">기본적으로 모델에 포함 된 모든 테이블에는 테이블의 열과 행이 모두 포함 된 하나의 파티션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-104">By default, every table you include in your model has one partition which includes all of the table's columns and rows.</span></span> <span data-ttu-id="b434b-105">Internet Sales 테이블의 경우 데이터를 연도별로 나누려고 합니다. 각 테이블의 5 년에 대해 하나의 파티션입니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-105">For the Internet Sales table, we want to divide the data by year; one partition for each of the table's five years.</span></span>  <span data-ttu-id="b434b-106">이렇게 하면 각 파티션을 독립적으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-106">Each partition can then be processed independently.</span></span> <span data-ttu-id="b434b-107">자세한 내용은 [파티션&#40;SSAS 테이블 형식&#41;](tabular-models/partitions-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b434b-107">To learn more, see [Partitions &#40;SSAS Tabular&#41;](tabular-models/partitions-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="b434b-108">이 단원을 완료하기 위한 예상 시간: **15분**</span><span class="sxs-lookup"><span data-stu-id="b434b-108">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b434b-109">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b434b-109">Prerequisites</span></span>  
 <span data-ttu-id="b434b-110">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="b434b-111">이 단원의 태스크를 수행하려면 이전 단원인 [10단원: 계층 만들기](lesson-9-create-hierarchies.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 10: Create Hierarchies](lesson-9-create-hierarchies.md).</span></span>  
  
## <a name="create-partitions"></a><span data-ttu-id="b434b-112">파티션 만들기</span><span class="sxs-lookup"><span data-stu-id="b434b-112">Create Partitions</span></span>  
  
#### <a name="to-create-partitions-in-the-internet-sales-table"></a><span data-ttu-id="b434b-113">Internet Sales 테이블에서 파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="b434b-113">To create partitions in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="b434b-114">모델 디자이너에서 **Internet Sales** 테이블을 클릭한 다음 **테이블** 메뉴와 **파티션**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-114">In the model designer, click on the **Internet Sales** table, then click on the **Table** menu, and then click **Partitions**.</span></span>  
  
     <span data-ttu-id="b434b-115">**파티션 관리자** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-115">The **Partition Manager** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="b434b-116">**파티션 관리자** 대화 상자의 **파티션**에서 **Internet Sales** 파티션을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-116">In the **Partition Manager** dialog box, in **Partitions**, click the **Internet Sales** partition.</span></span>  
  
3.  <span data-ttu-id="b434b-117">**파티션 이름**에서 이름을로 변경 `Internet Sales 2005` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-117">In **Partition Name**, change the name to `Internet Sales 2005`.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="b434b-118">다음 단계로 진행하기 전에 테이블 미리 보기 창을 보면 열 이름에 모델 테이블(선택됨)에 포함된 열이 원본의 열 이름과 함께 표시되는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-118">Before continuing to the next step, notice the column names in the Table Preview window display those columns included in the model table (checked) with the column names from the source.</span></span> <span data-ttu-id="b434b-119">이는 테이블 미리 보기 창에 모델 테이블의 열이 아니라 원본 테이블의 열이 표시되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-119">This is because the Table Preview window displays columns from the source table, not from the model table.</span></span>  
  
4.  <span data-ttu-id="b434b-120">미리 보기 창의 오른쪽 바로 위에 있는 **쿼리 편집기** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-120">Select the **Query Editor** button just above the right side of the preview window.</span></span>  
  
     <span data-ttu-id="b434b-121">파티션에 특정 기간에 해당하는 행만 포함하려고 하므로 WHERE 절을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-121">Because you want the partition to include only those rows within a certain period, you must include a WHERE clause.</span></span> <span data-ttu-id="b434b-122">WHERE 절은 SQL 문을 사용해서만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-122">You can only create a WHERE clause by using a SQL Statement.</span></span>  
  
5.  <span data-ttu-id="b434b-123">**SQL 문** 필드에서 다음 문을 붙여넣어 기존 문을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-123">In the **SQL Statement** field, replace the existing statement by pasting in the following statement:</span></span>  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2005-01-01 00:00:00') AND ([OrderDate] < N'2006-01-01 00:00:00'))  
    ```  
  
     <span data-ttu-id="b434b-124">이 문은 WHERE 절에 지정된 대로 OrderDate가 2005년인 행의 데이터를 모두 파티션에 포함하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-124">This statement specifies the partition should include all of the data in those rows where the OrderDate is for the 2005 calendar year as specified in the WHERE clause.</span></span>  
  
6.  <span data-ttu-id="b434b-125">**유효성 검사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-125">Click **Validate**.</span></span>  
  
     <span data-ttu-id="b434b-126">특정 열이 원본에 없음을 나타내는 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-126">Notice a warning is displayed stating that certain columns are not present in source.</span></span> <span data-ttu-id="b434b-127">이는 [3 단원: 열 이름 바꾸기](rename-columns.md)에서 모델의 Internet Sales 테이블에 있는 해당 열의 이름을 원본의 동일한 열과 다른 것 이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-127">This is because in [Lesson 3: Rename Columns](rename-columns.md), you renamed those columns in the Internet Sales table in the model to be different from those same columns at the source.</span></span>  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a><span data-ttu-id="b434b-128">Internet Sales 테이블에서 2006 년에 대 한 파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="b434b-128">To create a partition for the 2006 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="b434b-129">**파티션 관리자** 대화 상자의 **파티션에서** `Internet Sales 2005` 방금 만든 파티션을 클릭 한 다음 **복사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-129">In the **Partition Manager** dialog box, in **Partitions**, click the `Internet Sales 2005` partition you just created, and then **Copy**.</span></span>  
  
2.  <span data-ttu-id="b434b-130">**파티션 이름**에을 입력 `Internet Sales 2006` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-130">In **Partition Name**, type `Internet Sales 2006`.</span></span>  
  
3.  <span data-ttu-id="b434b-131">SQL 문에서 파티션에 2006 년에 해당 하는 행만 포함 하도록 하려면 WHERE 절을 다음과 같이 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-131">In the SQL Statement, in-order for the partition to include only those rows for the 2006 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a><span data-ttu-id="b434b-132">Internet Sales 테이블에서 2007 년에 대 한 파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="b434b-132">To create a partition for the 2007 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="b434b-133">**파티션 관리자** 대화 상자에서 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-133">In the **Partition Manager** dialog box, click **Copy**.</span></span>  
  
2.  <span data-ttu-id="b434b-134">**파티션 이름**에을 입력 `Internet Sales 2007` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-134">In **Partition Name**, type `Internet Sales 2007`.</span></span>  
  
3.  <span data-ttu-id="b434b-135">**전환 대상**에서 **쿼리 편집기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-135">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="b434b-136">SQL 문에서 파티션에 2007 년에 해당 하는 행만 포함 하도록 하려면 WHERE 절을 다음과 같이 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-136">In the SQL Statement, in-order for the partition to include only those rows for the 2007 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a><span data-ttu-id="b434b-137">Internet Sales 테이블에서 2008 년에 대 한 파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="b434b-137">To create a partition for the 2008 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="b434b-138">**파티션 관리자** 대화 상자에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-138">In the **Partition Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="b434b-139">**파티션 이름**에을 입력 `Internet Sales 2008` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-139">In **Partition Name**, type `Internet Sales 2008`.</span></span>  
  
3.  <span data-ttu-id="b434b-140">**전환 대상**에서 **쿼리 편집기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-140">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="b434b-141">SQL 문에서 파티션에 2008 년에 해당 하는 행만 포함 하도록 하려면 WHERE 절을 다음과 같이 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-141">In the SQL Statement, in-order for the partition to include only those rows for the 2008 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2008-01-01 00:00:00') AND ([OrderDate] < N'2009-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2009-year-in-the-internet-sales-table"></a><span data-ttu-id="b434b-142">Internet Sales 테이블에서 2009년에 대한 파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="b434b-142">To create a partition for the 2009 year in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="b434b-143">**파티션 관리자** 대화 상자에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-143">In the **Partition Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="b434b-144">**파티션 이름**에을 입력 `Internet Sales 2009` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-144">In **Partition Name**, type `Internet Sales 2009`.</span></span>  
  
3.  <span data-ttu-id="b434b-145">**전환 대상**에서 **쿼리 편집기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-145">In **Switch To**, select **Query Editor**.</span></span>  
  
4.  <span data-ttu-id="b434b-146">2009년에 해당하는 행만 파티션에 포함되도록 SQL 문에서 WHERE 절을 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-146">In the SQL Statement, in-order for the partition to include only those rows for the 2009 year, replace the WHERE clause with the following:</span></span>  
  
    ```  
    WHERE (([OrderDate] >= N'2009-01-01 00:00:00') AND ([OrderDate] < N'2010-01-01 00:00:00'))  
    ```  
  
## <a name="process-partitions"></a><span data-ttu-id="b434b-147">파티션 처리</span><span class="sxs-lookup"><span data-stu-id="b434b-147">Process Partitions</span></span>  
 <span data-ttu-id="b434b-148">**파티션 관리자** 대화 상자에서 방금 만든 새 파티션 각각의 파티션 이름 옆에 별표(**\***)가 표시되는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-148">In the **Partition Manager** dialog box, notice the asterisk (**\***) next to the partition names for each of the new partitions you just created.</span></span> <span data-ttu-id="b434b-149">별표는 파티션이 처리되지 않았음을, 즉 새로 고쳐지지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-149">This indicates that the partition has not been processed (refreshed).</span></span> <span data-ttu-id="b434b-150">새 파티션을 만들면 파티션 처리 또는 테이블 처리 작업을 실행하여 해당 파티션의 데이터를 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-150">When you create new partitions, you should run a Process Partitions or Process Table operation to refresh the data in those partitions.</span></span>  
  
#### <a name="to-process-internet-sales-partitions"></a><span data-ttu-id="b434b-151">Internet Sales 파티션을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="b434b-151">To process Internet Sales partitions</span></span>  
  
1.  <span data-ttu-id="b434b-152">**확인** 을 클릭하여 **파티션 관리자** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-152">Click **OK** to close the **Partition Manager** dialog box.</span></span>  
  
2.  <span data-ttu-id="b434b-153">모델 디자이너에서 **Internet Sales** 테이블을 클릭하고 **모델** 메뉴를 클릭한 다음 **처리** (새로 고침)를 가리키고 **파티션 처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-153">In the model designer, click the **Internet Sales** table, then click the **Model** menu, then point to **Process** (Refresh), and then click **Process Partitions**.</span></span>  
  
3.  <span data-ttu-id="b434b-154">**파티션 처리** 대화 상자에서 **모드** 가 **기본값 처리**로 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-154">In the **Process Partitions** dialog box, verify the **Mode** is set to **Process Default**.</span></span>  
  
4.  <span data-ttu-id="b434b-155">생성한 5개의 파티션 각각에 대한 **처리** 열에서 확인란을 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-155">Select the checkbox in the **Process** column for each of the five partitions you created, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b434b-156">가장 자격 증명을 요청하는 메시지가 표시되면 2단원의 6단계에서 지정한 Windows 사용자 이름 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-156">If you are prompted for Impersonation credentials, enter the Windows user name and password you specified in Lesson 2, step 6.</span></span>  
  
     <span data-ttu-id="b434b-157">그러면 **데이터 처리** 대화 상자가 나타나고 각 파티션에 대 한 처리 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-157">The **Data Process** dialog box then appears and displays process details for each partition.</span></span> <span data-ttu-id="b434b-158">파티션마다 서로 다른 개수의 행이 전송되었음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-158">Notice that a different number of rows for each partition are transferred.</span></span> <span data-ttu-id="b434b-159">이는 각 파티션에 해당 SQL 문의 WHERE 절에 지정된 연도의 행만 포함되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-159">This is because each partition includes only those rows for the year specified in the WHERE clause in the SQL Statement.</span></span> <span data-ttu-id="b434b-160">2010년에는 해당하는 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b434b-160">There is no data for the 2010 year.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b434b-161">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b434b-161">Next Steps</span></span>  
 <span data-ttu-id="b434b-162">이 자습서를 계속하려면 다음 단원인 [12단원: 역할 만들기](lesson-11-create-roles.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="b434b-162">To continue this tutorial, go to the next lesson: Lesson: [Lesson 12: Create Roles](lesson-11-create-roles.md).</span></span>  
  
  
