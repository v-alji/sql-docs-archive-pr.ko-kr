---
title: 예측을 위한 데이터 원본 뷰 추가 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9424988efa6a9856f4ef0d558992fc90ac303861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735672"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a><span data-ttu-id="91623-102">예측할 데이터 원본 뷰 추가(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="91623-102">Adding a Data Source View for Forecasting (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="91623-103">이 태스크에서 예측 시나리오에 사용할 데이터 원본 뷰를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-103">In this task, you add a data source view that will be used for the forecasting scenario.</span></span> <span data-ttu-id="91623-104">예측 모델을 사용하려면 데이터에 시계열의 단계를 식별하는 데 사용할 수 있는 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-104">A forecasting model requires that the data contains a column that can be used to identify steps in a time series.</span></span> <span data-ttu-id="91623-105">여러 데이터 계열을 분석하려는 경우 모든 계열이 같은 날짜 또는 시간 단계에서 종료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-105">If you plan to analyze multiple series of data, all series must end on the same date or time step.</span></span>  
  
### <a name="to-add-a-data-source-view"></a><span data-ttu-id="91623-106">데이터 원본 뷰를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="91623-106">To add a data source view</span></span>  
  
1.  <span data-ttu-id="91623-107">솔루션 탐색기에서 **데이터 원본 뷰**를 마우스 오른쪽 단추로 클릭 한 다음 **새 데이터 원본 뷰**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-107">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="91623-108">**데이터 원본 뷰 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-108">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="91623-109">**데이터 원본 선택** 페이지의 **관계형 데이터**원본에서 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 데이터 원본을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-109">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source.</span></span> <span data-ttu-id="91623-110">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-110">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91623-111">이 데이터 원본이 없는 경우 [기본 데이터 마이닝 자습서](../../2014/tutorials/basic-data-mining-tutorial.md)에서 데이터 원본을 만드는 단계를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91623-111">If you do not have this data source, you can find the steps to create the data source in the [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span>  
  
4.  <span data-ttu-id="91623-112">**테이블 및 뷰 선택** 페이지에서 vTimeSeries (dbo) 테이블을 선택한 다음 오른쪽 화살표를 클릭 하 여 데이터 원본 뷰에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-112">On the **Select Tables and Views** page, select the table, vTimeSeries (dbo), and then click the right arrow to add it to the data source view.</span></span>  
  
5.  <span data-ttu-id="91623-113">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-113">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="91623-114">**마법사 완료** 페이지에서는 기본적으로 데이터 원본 뷰의 이름이로 지정 됩니다 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="91623-114">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="91623-115">이름을 **Salesbyregion**으로 변경한 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-115">Change the name to **SalesByRegion**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="91623-116">데이터 원본 뷰 디자이너가 열리고 **Salesbyregion** 데이터 원본 뷰가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="91623-116">Data Source View Designer opens and the **SalesByRegion** data source view appears.</span></span>  
  
## <a name="working-with-the-data-source-view"></a><span data-ttu-id="91623-117">데이터 원본 뷰 작업</span><span class="sxs-lookup"><span data-stu-id="91623-117">Working with the Data Source View</span></span>  
 <span data-ttu-id="91623-118">데이터 원본 뷰를 만든 후 다음과 같은 방법으로 데이터를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91623-118">After you have created the data source view, you can explore the data in the following ways:</span></span>  
  
-   <span data-ttu-id="91623-119">디자이너에서 vTimeSeries 테이블을 마우스 오른쪽 단추로 클릭 하 고 **데이터 탐색** 을 선택 하 여 표에서 선택한 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="91623-119">Right-click the table vTimeSeries in the designer, and select **Explore Data** to open the selected table in a grid.</span></span>  
  
-   <span data-ttu-id="91623-120">**샘플링 옵션** 을 클릭 한 다음 **데이터 탐색 옵션** 대화 상자를 사용 하 여 샘플링 방법을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-120">Click **Sampling options** and then use the **Data Exploration Options** dialog box to change the sampling method.</span></span> <span data-ttu-id="91623-121">새 옵션 설정을 사용 하 여 테이블에 데이터를 로드 하려면 **새로 고침** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-121">Click **Refresh** to load data in the table using the new option settings.</span></span> <span data-ttu-id="91623-122">예를 들어 샘플에서 출력할 행 수를 지정 하거나 상위 n 개 행을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91623-122">For example, you could specify the number of rows to output in the sample, or choose the top n rows.</span></span>  
  
-   <span data-ttu-id="91623-123">VTimeSeries 테이블을 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 하 여 테이블에 새 이름을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-123">Right-click the table vTimeSeries and select **Properties** to assign a new name to the table.</span></span> <span data-ttu-id="91623-124">데이터 원본 뷰에서 개별 열을 선택하고 열 속성을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91623-124">You can also select individual columns from the data source view, and the modify the column properties.</span></span>  
  
-   <span data-ttu-id="91623-125">데이터 원본 뷰 디자인 영역 안을 클릭하여 새 쿼리를 만들고 쿼리에 이름을 할당하거나, 테이블 간의 관계를 만들거나, 디자인 영역의 레이아웃을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-125">Click anywhere in the data source view design area to create a new query and assign a name to it, to create relationships between tables, or to change the layout of the design area.</span></span>  
  
-   <span data-ttu-id="91623-126">테이블을 마우스 오른쪽 단추로 클릭 하 고 **새 명명 된 계산** 을 선택 하 여 집계를 포함 한 파생 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91623-126">Right-click a table and select **New Named Calculation** to create derived columns, including aggregations.</span></span> <span data-ttu-id="91623-127">이 뷰의 데이터 원본에서 새 테이블과 뷰를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91623-127">You can also add new tables and views from the data source in this view.</span></span>  
  
 <span data-ttu-id="91623-128">다음 태스크에서는 시계열 데이터를 탐색하고 시계열 식별자로 사용할 최상의 열을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="91623-128">In the next task, you will explore the time series data and determine the best column to use as the time series identifier.</span></span> <span data-ttu-id="91623-129">시계열 데이터의 간격을 처리하는 방법도 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="91623-129">You will also learn how to handle gaps in time series data.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="91623-130">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="91623-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="91623-131">시계열 모델에 대 한 요구 사항 이해 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="91623-131">Understanding the Requirements for a Time Series Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="91623-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91623-132">See Also</span></span>  
 [<span data-ttu-id="91623-133">Microsoft Time Series 알고리즘</span><span class="sxs-lookup"><span data-stu-id="91623-133">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
