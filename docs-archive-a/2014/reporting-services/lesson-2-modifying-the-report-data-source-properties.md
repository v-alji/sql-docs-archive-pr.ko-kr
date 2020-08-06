---
title: '2단원: 보고서 데이터 원본 속성 수정 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c962b0ff-ce8a-4742-8262-dc730901afcf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05e56a58ce28ee1e1e450d3af012cbd1ffe668ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647522"
---
# <a name="lesson-2-modifying-the-report-data-source-properties"></a><span data-ttu-id="80050-102">Lesson 2: Modifying the Report Data Source Properties</span><span class="sxs-lookup"><span data-stu-id="80050-102">Lesson 2: Modifying the Report Data Source Properties</span></span>
  <span data-ttu-id="80050-103">이 단원에서는 보고서 관리자를 사용하여 받는 사람에게 배달될 보고서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-103">In this lesson, you will use Report Manager to select a report that will be delivered to recipients.</span></span> <span data-ttu-id="80050-104">사용자가 정의하는 데이터 기반 구독은 **기본 테이블 보고서 만들기&amp;#40;SSRS 자습서&amp;#41;** 자습서에서 만든 [기본 테이블 보고서 만들기&#40;SSRS 자습서&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)보고서를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-104">The data-driven subscription that you will define will distribute the **Sales Order** report created in the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md).</span></span> <span data-ttu-id="80050-105">다음 단계에서는 보고서에서 데이터를 가져오는 데 사용되는 데이터 원본 연결 정보를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-105">In the steps that follow, you will modify the data source connection information used by the report to get data.</span></span> <span data-ttu-id="80050-106">**저장된 자격 증명** 을 사용하여 보고서 데이터 원본에 액세스하는 보고서만 데이터 기반 구독을 통해 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80050-106">Only reports that use **stored credentials** to access a report data source can be distributed through a data-driven subscription.</span></span> <span data-ttu-id="80050-107">저장된 자격 증명은 무인 보고서 처리에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-107">Stored credentials are necessary for unattended report processing.</span></span>

 <span data-ttu-id="80050-108">또한 구독이 특정 주문 및 렌더링 형식에 대해 보고서의 서로 다른 인스턴스를 출력할 수 있도록 `[Order]` 에 대해 보고서를 필터링하는 매개 변수를 사용하기 위해 데이터 세트 및 보고서를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-108">You will also modify the dataset and report to use a parameter to filter the report on the `[Order]` so the subscription can output different instances of the report for specific orders and rendering formats.</span></span>

 <span data-ttu-id="80050-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="80050-109">**In this topic:**</span></span>

-   [<span data-ttu-id="80050-110">데이터 원본 속성을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="80050-110">To Modify the Data Source Properties</span></span>](#bkmk_modify_datasource)

-   [<span data-ttu-id="80050-111">AdventureWorksDataset을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="80050-111">To Modify the AdventureWorksDataset</span></span>](#bkmk_modify_dataset)

-   [<span data-ttu-id="80050-112">보고서 매개 변수를 추가하고 보고서를 다시 게시하려면</span><span class="sxs-lookup"><span data-stu-id="80050-112">To Add a Report Parameter and Republish the Report</span></span>](#bkmk_add_reportparameter)

-   [<span data-ttu-id="80050-113">보고서를 다시 게시하려면</span><span class="sxs-lookup"><span data-stu-id="80050-113">To Re-deploy the Report</span></span>](#bkmk_redeploy)

##  <a name="to-modify-the-data-source-properties"></a><a name="bkmk_modify_datasource"></a><span data-ttu-id="80050-114">데이터 원본 속성을 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="80050-114">To Modify the Data Source Properties</span></span>

1.  <span data-ttu-id="80050-115">예를 들어 Internet Explorer 아이콘을 마우스 오른쪽 단추로 클릭 하 고 관리자 권한으로 **실행**을 클릭 하 여 [SSRS 기본 모드&#41;&#40;보고서 관리자](../../2014/reporting-services/report-manager-ssrs-native-mode.md) 을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-115">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) with administrator privileges, for example, right-click the icon for Internet Explorer and click **Run as administrator**.</span></span>

2.  <span data-ttu-id="80050-116">**Sales Orders** 보고서가 포함된 폴더로 이동하고 보고서의 상황에 맞는 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-116">Browse to the folder containing the **Sales Orders** report and in the context menu of the report, click **Manage**.</span></span>

     <span data-ttu-id="80050-117">![보고서 상황에 맞는 메뉴 열기 및 관리 선택](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "보고서 상황에 맞는 메뉴 열기 및 관리 선택")</span><span class="sxs-lookup"><span data-stu-id="80050-117">![Open the report context menu and select manage](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "Open the report context menu and select manage")</span></span>

3.  <span data-ttu-id="80050-118">**데이터 원본** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-118">Click the **Data Sources** tab.</span></span>

4.  <span data-ttu-id="80050-119">**연결 유형**으로 **Microsoft SQL Server**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-119">For **Connection Type**, select **Microsoft SQL Server**.</span></span>

5.  <span data-ttu-id="80050-120">고객 데이터 원본 연결 문자열이 다음과 같고 샘플 데이터베이스가 로컬 데이터베이스 서버에 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-120">The custom data source connection string will be the following and it assumes that the sample database is on a local database server:</span></span>

    ```
    Data source=localhost; initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="80050-121">**보고서 서버에 안전하게 저장된 자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-121">Click **Credentials stored securely in the report server**.</span></span>

7.  <span data-ttu-id="80050-122">사용자 이름( *domain\user*형식 사용)과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-122">Type your user name (use the format *domain\user*) and password.</span></span> <span data-ttu-id="80050-123">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스에 액세스할 권한이 없으면 해당 권한이 있는 로그인을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-123">If you do not have permission to access the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database, specify a login that does.</span></span>

8.  <span data-ttu-id="80050-124">**데이터 원본에 연결할 때 Windows 자격 증명으로 사용**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-124">Click **Use as windows credentials when connecting to the data source**, and then click **OK**.</span></span> <span data-ttu-id="80050-125">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그인을 사용하는 경우와 같이 도메인 계정을 사용하지 않는 경우에는 이 확인란을 클릭하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="80050-125">If you are not using a domain account (for example, if you are using a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login), do not click this checkbox.</span></span>

9. <span data-ttu-id="80050-126">**연결 테스트** 를 클릭하여 데이터 원본에 연결할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-126">Click **Test Connection** to verify you can connect to the data source.</span></span>

10. <span data-ttu-id="80050-127">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-127">Click **Apply**.</span></span>

11. <span data-ttu-id="80050-128">보고서를 확인하여 지정한 자격 증명으로 보고서가 실행되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-128">View the report to verify that the report runs with the credentials you specified.</span></span> <span data-ttu-id="80050-129">보고서를 보려면 **보기** 탭을 클릭 합니다. 보고서를 연 후에는 직원 이름을 선택 하 고 **보고서 보기** 단추를 클릭 하 여 보고서를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-129">To view the report, click the **View** tab. Note that once the report is open, you must select an Employee name and then click the **View Report** button to view the report.</span></span>

##  <a name="to-modify-the-adventureworksdataset"></a><a name="bkmk_modify_dataset"></a><span data-ttu-id="80050-130">AdventureWorksDataset를 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="80050-130">To Modify the AdventureWorksDataset</span></span>

1.  <span data-ttu-id="80050-131">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 Sales Orders 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="80050-131">Open the Sales Orders report in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]</span></span>

2.  <span data-ttu-id="80050-132">`AdventureWorksDataset` 데이터 세트를 마우스 오른쪽 단추로 클릭하고 **데이터 세트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-132">Right-click the dataset `AdventureWorksDataset` and click **Dataset Properties**.</span></span>

3.  <span data-ttu-id="80050-133">`WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` 문 앞에 `Group By` 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-133">Add the statement `WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` before the `Group By` statement.</span></span> <span data-ttu-id="80050-134">전체 쿼리 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80050-134">The full query syntax is the following:</span></span>

    ```
    SELECT soh.OrderDate AS Date, soh.SalesOrderNumber AS [Order], pps.Name AS Subcat, pp.Name AS Product, SUM(sd.OrderQty) AS Qty, SUM(sd.LineTotal)  AS LineTotal
    FROM Sales.SalesPerson AS sp INNER JOIN
      Sales.SalesOrderHeader AS soh ON sp.BusinessEntityID = soh.SalesPersonID INNER JOIN
       Sales.SalesOrderDetail AS sd ON sd.SalesOrderID = soh.SalesOrderID INNER JOIN
       Production.Product AS pp ON sd.ProductID = pp.ProductID
    INNER JOIN
       Production.ProductSubcategory AS pps ON pp.ProductSubcategoryID = pps.ProductSubcategoryID 
    INNER JOIN
        Production.ProductCategory AS ppc ON ppc.ProductCategoryID = pps.ProductCategoryID

    WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)

    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name, soh.SalesPersonID
    HAVING (ppc.Name = 'Clothing')
    ```

4.  <span data-ttu-id="80050-135">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-135">Click **OK**</span></span>

##  <a name="to-add-a-report-parameter-and-republish-the-report"></a><a name="bkmk_add_reportparameter"></a><span data-ttu-id="80050-136">보고서 매개 변수를 추가 하 고 보고서를 다시 게시 하려면</span><span class="sxs-lookup"><span data-stu-id="80050-136">To Add a Report Parameter and Republish the Report</span></span>

1.  <span data-ttu-id="80050-137">**보고서 데이터** 창에서 **새로 만들기** 를 클릭한 후 **매개 변수...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-137">In the **Report Data** pane click **New** and then click **Parameter...**</span></span>

2.  <span data-ttu-id="80050-138">**이름**에서 `OrderNumber`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-138">In **Name**, type `OrderNumber`.</span></span>

3.  <span data-ttu-id="80050-139">**프롬프트**에 `OrderNumber`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-139">In **Prompt**, type `OrderNumber`.</span></span>

4.  <span data-ttu-id="80050-140">**빈 값("") 허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-140">Select **Allow blank value ("")**.</span></span>

5.  <span data-ttu-id="80050-141">**Null 값 허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-141">Select **Allow null value**.</span></span>

6.  <span data-ttu-id="80050-142">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-142">Click **OK**.</span></span> <span data-ttu-id="80050-143">매개 변수가 **보고서 데이터 창** 에 추가되고 다음 이미지와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="80050-143">The parameter will be added to the **Report Data pane** and it will look like the following image:</span></span>

     <span data-ttu-id="80050-144">![새 매개 변수가 보고서 데이터 창에 추가됩니다.](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "새 매개 변수가 보고서 데이터 창에 추가됩니다.")</span><span class="sxs-lookup"><span data-stu-id="80050-144">![The new parameter is added to the Report Data pane](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "The new parameter is added to the Report Data pane")</span></span>

7.  <span data-ttu-id="80050-145">**미리 보기** 탭을 클릭하여 보고서를 실행합니다. 매개 변수 입력 상자는 보고서 맨 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80050-145">Click the **Preview** tab to run the report.Note the parameter input box at the top of the report.</span></span> <span data-ttu-id="80050-146">다음 작업 중 하나를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80050-146">You can either:</span></span>

    -   <span data-ttu-id="80050-147">매개 변수를 사용하지 않고 보고서 보기를 클릭하여 전체 보고서를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="80050-147">Click View Report to see the full report without using a parameter.</span></span>

    -   <span data-ttu-id="80050-148">Null 옵션의 선택을 취소하고 주문 번호(예: so71949)를 입력하여 보고서에서 해당 주문 하나만 봅니다.</span><span class="sxs-lookup"><span data-stu-id="80050-148">Unselect the Null option and type an order number, for example so71949 to view only the one order in the report.</span></span>

         <span data-ttu-id="80050-149">![매개 변수 영역이 표시되는 보고서 뷰어](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "매개 변수 영역이 표시되는 보고서 뷰어")</span><span class="sxs-lookup"><span data-stu-id="80050-149">![Report viewer with parameter area visible](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "Report viewer with parameter area visible")</span></span>

8.  <span data-ttu-id="80050-150">다음 단원의 구독 구성에서 이 단원에 수행한 변경 내용을 활용할 수 있도록 보고서를 다시 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-150">Re-deploy the report so the subscription configuration in the next lesson can utilize the changes you made in this lesson.</span></span> <span data-ttu-id="80050-151">테이블 자습서에 사용된 프로젝트 속성에 대한 자세한 내용을 보려면 [6단원: 그룹화 및 합계 추가&#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)의 '보고서 서버에 보고서를 게시하려면(옵션)' 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80050-151">For more information on the project properties used in the table tutorial, see section 'To Publish the Report to the Report Server (Optional)' of [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>

##  <a name="to-re-deploy-the-report"></a><a name="bkmk_redeploy"></a><span data-ttu-id="80050-152">보고서를 다시 배포 하려면</span><span class="sxs-lookup"><span data-stu-id="80050-152">To Re-deploy the Report</span></span>

1.  <span data-ttu-id="80050-153">다음 단원의 구독 구성에서 이 단원에 수행한 변경 내용을 활용할 수 있도록 보고서를 다시 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-153">Re-deploy the report so the subscription configuration in the next lesson can utilize the changes you made in this lesson.</span></span> <span data-ttu-id="80050-154">테이블 자습서에 사용된 프로젝트 속성에 대한 자세한 내용을 보려면 [6단원: 그룹화 및 합계 추가&#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)의 '보고서 서버에 보고서를 게시하려면(옵션)' 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80050-154">For more information on the project properties used in the table tutorial, see section 'To Publish the Report to the Report Server (Optional)' of [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>

2.  <span data-ttu-id="80050-155">도구 모음에서 **빌드** 를 클릭한 후 **자습서 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-155">On the toolbar click **Build** and then click **Deploy tutorial**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="80050-156">다음 단계</span><span class="sxs-lookup"><span data-stu-id="80050-156">Next Steps</span></span>
 <span data-ttu-id="80050-157">저장된 자격 증명을 사용하여 데이터를 가져오도록 보고서를 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="80050-157">You successfully configured the report to get data using stored credentials.</span></span> <span data-ttu-id="80050-158">다음 단원에서는 보고서 관리자의 데이터 기반 구독 페이지를 사용하여 구독을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="80050-158">Next, you specify the subscription using the Data-Driven Subscription pages in Report Manager.</span></span> <span data-ttu-id="80050-159">[3단원: 데이터 기반 구독 정의](../reporting-services/lesson-3-defining-a-data-driven-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80050-159">See [Lesson 3: Defining a Data-Driven Subscription](../reporting-services/lesson-3-defining-a-data-driven-subscription.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80050-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80050-160">See Also</span></span>
 <span data-ttu-id="80050-161">[보고서 데이터 원본 관리](report-data/manage-report-data-sources.md) [보고서 데이터 원본에 대 한 자격 증명 및 연결 정보 지정](report-data/specify-credential-and-connection-information-for-report-data-sources.md) [데이터 기반 구독 만들기 &#40;Ssrs 자습서&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) [기본 테이블 보고서 &#40;ssrs 자습서를 만듭니다&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="80050-161">[Manage Report Data Sources](report-data/manage-report-data-sources.md) [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)</span></span>


