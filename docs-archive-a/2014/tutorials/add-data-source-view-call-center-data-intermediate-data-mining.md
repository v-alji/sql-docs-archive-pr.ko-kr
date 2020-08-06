---
title: 콜 센터 데이터에 대 한 데이터 원본 뷰 추가 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a448e7e4-dbd1-4d31-90bc-4d4a1c23b352
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6d3d9aa3153b39b9ef7f4a92af20e0e8791780bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735688"
---
# <a name="adding-a-data-source-view-for-call-center-data-intermediate-data-mining-tutorial"></a><span data-ttu-id="0fed5-102">콜 센터 데이터의 데이터 원본 뷰 추가(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="0fed5-102">Adding a Data Source View for Call Center Data (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="0fed5-103">이 태스크에서는 콜 센터 데이터에 액세스하는 데 사용할 데이터 원본 뷰를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-103">In this task, you add a data source view that will be used to access the call center data.</span></span> <span data-ttu-id="0fed5-104">탐색을 위한 초기 신경망 모델과 권장하는 데 사용할 로지스틱 회귀 모델 모두를 작성하는 데 동일한 데이터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-104">The same data will be used to build both the initial neural network model for exploration, and the logistic regression model that you will use to make recommendations.</span></span>  
  
 <span data-ttu-id="0fed5-105">또한 데이터 원본 뷰 디자이너를 사용하여 요일에 대한 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-105">You will also use the Data Source View Designer to add a column for the day of the week.</span></span> <span data-ttu-id="0fed5-106">이는 원본 데이터가 콜 센터 데이터를 날짜별로 추적하더라도 해당 요일이 평일 또는 주중인지 여부에 따라 호출량 및 서비스 품질 측면 모두에 경험적으로 되풀이되는 패턴이 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-106">That is because, although the source data tracks call center data by dates, your experience tells you that there are recurring patterns both in terms of call volume and service quality, depending on whether the day is a weekend or a weekday.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0fed5-107">프로시저</span><span class="sxs-lookup"><span data-stu-id="0fed5-107">Procedures</span></span>  
  
#### <a name="to-add-a-data-source-view"></a><span data-ttu-id="0fed5-108">데이터 원본 뷰를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="0fed5-108">To add a data source view</span></span>  
  
1.  <span data-ttu-id="0fed5-109">**솔루션 탐색기**에서 **데이터 원본 뷰**를 마우스 오른쪽 단추로 클릭하고 **새 데이터 원본 뷰**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-109">In **Solution Explorer**, right-click **Data Source Views**, and select **New Data Source View**.</span></span>  
  
     <span data-ttu-id="0fed5-110">데이터 원본 뷰 마법사가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-110">The Data Source View Wizard opens.</span></span>  
  
2.  <span data-ttu-id="0fed5-111">**데이터 원본 뷰 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-111">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="0fed5-112">**데이터 원본 선택** 페이지의 **관계형 데이터**원본에서 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 데이터 원본을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-112">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source.</span></span> <span data-ttu-id="0fed5-113">이 데이터 원본이 없는 경우 [기본 데이터 마이닝 자습서](../../2014/tutorials/basic-data-mining-tutorial.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0fed5-113">If you do not have this data source, see [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="0fed5-114">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-114">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="0fed5-115">**테이블 및 뷰 선택** 페이지에서 다음 테이블을 선택 하 고 오른쪽 화살표를 클릭 하 여 데이터 원본 뷰에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-115">On the **Select Tables and Views** page, select the following table and then click the right arrow to add it to the data source view:</span></span>  
  
    -   <span data-ttu-id="0fed5-116">**FactCallCenter(dbo)**</span><span class="sxs-lookup"><span data-stu-id="0fed5-116">**FactCallCenter (dbo)**</span></span>  
  
    -   <span data-ttu-id="0fed5-117">**DimDate**</span><span class="sxs-lookup"><span data-stu-id="0fed5-117">**DimDate**</span></span>  
  
5.  <span data-ttu-id="0fed5-118">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="0fed5-119">**마법사 완료** 페이지에서는 기본적으로 데이터 원본 뷰의 이름이로 지정 됩니다 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0fed5-119">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="0fed5-120">이름을 **Callcenter**로 변경한 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-120">Change the name to **CallCenter**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="0fed5-121">데이터 원본 뷰 디자이너가 열리면서 **Callcenter** 데이터 원본 뷰가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-121">Data Source View Designer opens to display the **CallCenter** data source view.</span></span>  
  
7.  <span data-ttu-id="0fed5-122">데이터 원본 뷰 창 내부를 마우스 오른쪽 단추로 클릭 하 고 **테이블 추가/제거**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-122">Right-click inside the Data Source View pane, and select **Add/Remove Tables**.</span></span> <span data-ttu-id="0fed5-123">테이블, 나이 **날짜** 를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-123">Select the table, **DimDate** and click **OK**.</span></span>  
  
     <span data-ttu-id="0fed5-124">각 테이블의 열 간에 관계를 자동으로 추가 해야 합니다 `DateKey` .</span><span class="sxs-lookup"><span data-stu-id="0fed5-124">A relationship should be automatically added between the `DateKey` columns in each table.</span></span> <span data-ttu-id="0fed5-125">이 관계를 사용 하 여 **EnglishDayNameOfWeek** **테이블에서** 열을 가져오고 모델에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-125">You will use this relationship to get the column, **EnglishDayNameOfWeek**, from the **DimDate** table and use it in your model.</span></span>  
  
8.  <span data-ttu-id="0fed5-126">데이터 원본 뷰 디자이너에서 **FactCallCenter**테이블을 마우스 오른쪽 단추로 클릭 하 고 **새 명명 된 계산**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-126">In the Data Source View designer, right-click the table, **FactCallCenter**, and select **New Named Calculation**.</span></span>  
  
     <span data-ttu-id="0fed5-127">**명명 된 계산 만들기** 대화 상자에서 다음 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-127">In the **Create Named Calculation** dialog box, type the following values:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="0fed5-128">**열 이름**</span><span class="sxs-lookup"><span data-stu-id="0fed5-128">**Column name**</span></span>|<span data-ttu-id="0fed5-129">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="0fed5-129">DayOfWeek</span></span>|  
    |<span data-ttu-id="0fed5-130">**설명**</span><span class="sxs-lookup"><span data-stu-id="0fed5-130">**Description**</span></span>|<span data-ttu-id="0fed5-131">DimDate 테이블에서 요일을 얻음</span><span class="sxs-lookup"><span data-stu-id="0fed5-131">Get day of week from DimDate table</span></span>|  
    |<span data-ttu-id="0fed5-132">**식**</span><span class="sxs-lookup"><span data-stu-id="0fed5-132">**Expression**</span></span>|`(SELECT EnglishDayNameOfWeek AS DayOfWeek FROM DimDate where FactCallCenter.DateKey = DimDate.DateKey)`|  
  
     <span data-ttu-id="0fed5-133">식이 필요한 데이터를 생성 하는지 확인 하려면 **FactCallCenter**테이블을 마우스 오른쪽 단추로 클릭 한 다음 **데이터 탐색**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-133">To verify that the expression creates the data you need, right-click the table **FactCallCenter**, and then select **Explore Data**.</span></span>  
  
9. <span data-ttu-id="0fed5-134">데이터가 사용 가능한지 검토하는 데에 1분 정도 소요되며, 이를 통해 데이터 마이닝에 해당 데이터가 어떻게 사용되는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-134">Take a minute to review the data that is available, so that you can understand how it is used in data mining:</span></span>  
  
|<span data-ttu-id="0fed5-135">열 이름</span><span class="sxs-lookup"><span data-stu-id="0fed5-135">Column name</span></span>|<span data-ttu-id="0fed5-136">포함</span><span class="sxs-lookup"><span data-stu-id="0fed5-136">Contains</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="0fed5-137">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="0fed5-137">FactCallCenterID</span></span>|<span data-ttu-id="0fed5-138">데이터를 데이터 웨어하우스로 가져올 때 만든 임의 키입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-138">An arbitrary key created when the data was imported to the data warehouse.</span></span><br /><br /> <span data-ttu-id="0fed5-139">이 열은 고유 레코드를 식별하며 데이터 마이닝 모델에 대한 사례 키로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-139">This column identifies unique records and should be used as the case key for the data mining model.</span></span>|  
|<span data-ttu-id="0fed5-140">DateKey</span><span class="sxs-lookup"><span data-stu-id="0fed5-140">DateKey</span></span>|<span data-ttu-id="0fed5-141">콜 센터 운영 날짜로, 정수로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-141">The date of the call center operation, expressed as an integer.</span></span> <span data-ttu-id="0fed5-142">정수 날짜 키는 데이터 웨어하우스에서 종종 사용되지만, 날짜 값으로 그룹화하려는 경우 날짜/시간 형식으로 날짜를 구할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-142">Integer date keys are often used in data warehouses, but you might want to obtain the date in date/time format if you were going to group by date values.</span></span><br /><br /> <span data-ttu-id="0fed5-143">공급업체에서 각 운영일의 각 교대조에 대해 별도의 보고서를 제공하기 때문에 날짜는 고유하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-143">Note that dates are not unique because the vendor provides a separate report for each shift in each day of operation.</span></span>|  
|<span data-ttu-id="0fed5-144">WageType</span><span class="sxs-lookup"><span data-stu-id="0fed5-144">WageType</span></span>|<span data-ttu-id="0fed5-145">날짜가 평일인지, 아니면 주말 또는 공휴일인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-145">Indicates whether the day was a weekday, a weekend, or a holiday.</span></span><br /><br /> <span data-ttu-id="0fed5-146">주말 대비 고객 서비스 품질에 차이가 있을 수 있으므로이 열을 입력으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-146">It is possible that there is a difference in quality of customer service on weekends vs. weekdays so you will use this column as an input.</span></span>|  
|<span data-ttu-id="0fed5-147">Shift</span><span class="sxs-lookup"><span data-stu-id="0fed5-147">Shift</span></span>|<span data-ttu-id="0fed5-148">통화를 기록한 교대조를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-148">Indicates the shift for which calls are recorded.</span></span> <span data-ttu-id="0fed5-149">이 콜 센터는 영업일을 4개의 교대조인 오전, 오후 1, 오후 2 및 자정으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-149">This call center divides the working day into four shifts: AM, PM1, PM2, and Midnight.</span></span><br /><br /> <span data-ttu-id="0fed5-150">교대조가 고객 서비스 품질에 영향을 줄 수 있으므로 이를 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-150">It is possible that the shift influences the quality of customer service so you will use this as an input.</span></span>|  
|<span data-ttu-id="0fed5-151">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="0fed5-151">LevelOneOperators</span></span>|<span data-ttu-id="0fed5-152">근무 중인 첫 번째 수준의 전화 상담원 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-152">Indicates the number of Level 1 operators on duty.</span></span><br /><br /> <span data-ttu-id="0fed5-153">콜 센터 직원은 첫 번째 수준부터 시작하므로 이러한 직원은 덜 숙련되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-153">Call center employees start at Level 1 so these employees are less experienced.</span></span>|  
|<span data-ttu-id="0fed5-154">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="0fed5-154">LevelTwoOperators</span></span>|<span data-ttu-id="0fed5-155">근무 중인 두 번째 수준의 전화 상담원 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-155">Indicates the number of Level 2 operators on duty.</span></span><br /><br /> <span data-ttu-id="0fed5-156">직원이 두 번째 수준의 전화 상담원이 되기 위해서는 특정 서비스 시간을 기록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-156">An employee must log a certain number of service hours to qualify as a Level 2 operator.</span></span>|  
|<span data-ttu-id="0fed5-157">TotalOperators</span><span class="sxs-lookup"><span data-stu-id="0fed5-157">TotalOperators</span></span>|<span data-ttu-id="0fed5-158">교대조 동안 근무하는 총 전화 상담원 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-158">The total number of operators present during the shift.</span></span>|  
|<span data-ttu-id="0fed5-159">호출</span><span class="sxs-lookup"><span data-stu-id="0fed5-159">Calls</span></span>|<span data-ttu-id="0fed5-160">교대조 동안 받은 호출 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-160">Number of calls received during the shift.</span></span>|  
|<span data-ttu-id="0fed5-161">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="0fed5-161">AutomaticResponses</span></span>|<span data-ttu-id="0fed5-162">자동 호출 처리 시스템인 IVR(Interactive Voice Response)을 통해 완전히 처리된 호출 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-162">The number of calls that were handled entirely by automated call processing (Interactive Voice Response, or IVR).</span></span>|  
|<span data-ttu-id="0fed5-163">Orders</span><span class="sxs-lookup"><span data-stu-id="0fed5-163">Orders</span></span>|<span data-ttu-id="0fed5-164">호출 결과로 발생한 주문 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-164">The number of orders that resulted from calls.</span></span>|  
|<span data-ttu-id="0fed5-165">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="0fed5-165">IssuesRaised</span></span>|<span data-ttu-id="0fed5-166">호출로 인해 생성된 후속 작업이 필요한 문제 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-166">The number of issues requiring follow-up that were generated by calls.</span></span>|  
|<span data-ttu-id="0fed5-167">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="0fed5-167">AverageTimePerIssue</span></span>|<span data-ttu-id="0fed5-168">들어오는 호출에 응답하는 데 필요한 평균 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-168">The average time required to respond to an incoming call.</span></span>|  
|<span data-ttu-id="0fed5-169">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="0fed5-169">ServiceGrade</span></span>|<span data-ttu-id="0fed5-170">전체 이동에 대 한 *중단 율* 로 측정 된 일반 서비스 품질을 나타내는 메트릭입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-170">A metric that indicates the general quality of service, measured as the *abandon rate* for the entire shift.</span></span> <span data-ttu-id="0fed5-171">중단율이 높을수록 고객이 불만을 느끼며 잠재 주문 기회를 놓칠 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-171">The higher the abandon rate, the more likely it is that customers are dissatisfied and that potential orders are being lost.</span></span>|  
  
 <span data-ttu-id="0fed5-172">데이터에는 단일 날짜 열 `WageType` ( **DayOfWeek**, 및)을 기반으로 하는 네 개의 열이 포함 되어 있습니다 `Shift` `DateKey` .</span><span class="sxs-lookup"><span data-stu-id="0fed5-172">Note that the data includes four different columns that are based on a single date column: `WageType`, **DayOfWeek**, `Shift`, and `DateKey`.</span></span> <span data-ttu-id="0fed5-173">일반적으로 데이터 마이닝에서는 동일한 데이터로부터 파생된 여러 열을 사용하는 것이 바람직하지 않습니다. 이는 값들이 서로 너무 강한 상관 관계를 갖고 있으며 기타 패턴을 명확하게 나타내지 못할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-173">Ordinarily in data mining it is not a good idea to use multiple columns that are derived from the same data, as the values correlate with each other too strongly and can obscure other patterns.</span></span>  
  
 <span data-ttu-id="0fed5-174">그러나 `DateKey` 모델에는 너무 많은 고유 값이 포함 되어 있으므로 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-174">However, we will not use `DateKey` in the model because it contains too many unique values.</span></span> <span data-ttu-id="0fed5-175">와 Dayofweek 사이에는 직접적인 관계가 없으며 및 `Shift` **DayOfWeek** `WageType` **dayofweek** 는 부분적 으로만 관련 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-175">There is no direct relationship between `Shift` and **DayOfWeek**, and `WageType` and **DayOfWeek** are only partly related.</span></span> <span data-ttu-id="0fed5-176">공선성에 대해 염려되는 경우 사용 가능한 전체 열을 사용하여 구조를 만든 다음 각 모델의 서로 다른 열을 무시하고 그 영향을 시험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fed5-176">If you were worried about collinearity, you could create the structure using all of the available columns, and then ignore different columns in each model and test the effect.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="0fed5-177">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="0fed5-177">Next Task in Lesson</span></span>  
 [<span data-ttu-id="0fed5-178">&#40;중급 데이터 마이닝 자습서&#41;신경망 구조 및 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="0fed5-178">Creating a Neural Network Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="0fed5-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fed5-179">See Also</span></span>  
 [<span data-ttu-id="0fed5-180">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="0fed5-180">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
