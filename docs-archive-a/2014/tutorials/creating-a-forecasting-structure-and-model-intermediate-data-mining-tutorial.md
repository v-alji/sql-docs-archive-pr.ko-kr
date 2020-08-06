---
title: 예측 구조 및 모델 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d77b15a9a8efe9a9c6faec49a2274ee182706992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727528"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="d28f7-102">예측 구조 및 모델 만들기(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="d28f7-102">Creating a Forecasting Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="d28f7-103">다음으로 데이터 마이닝 마법사를 사용하여 방금 만든 데이터 원본 뷰를 기반으로 하는 새 마이닝 구조와 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-103">Next, you will use the Data Mining Wizard to create a new mining structure and mining model based on the data source view that you just created.</span></span> <span data-ttu-id="d28f7-104">이 태스크에서는 마이닝 모델에 [!INCLUDE[msCoName](../includes/msconame-md.md)] 시계열 알고리즘을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-104">In this task you will specify that the mining model should use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
### <a name="to-create-a-forecasting-mining-structure"></a><span data-ttu-id="d28f7-105">예측 마이닝 구조를 만들려면</span><span class="sxs-lookup"><span data-stu-id="d28f7-105">To create a forecasting mining structure</span></span>  
  
1.  <span data-ttu-id="d28f7-106">의 솔루션 탐색기에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] **마이닝 구조** 를 마우스 오른쪽 단추로 클릭 하 고 **새 마이닝 구조**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-106">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="d28f7-107">**데이터 마이닝 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="d28f7-108">**정의 방법 선택** 페이지에서 **기존 관계형 데이터베이스 또는 데이터 웨어하우스** 를 선택 했는지 확인 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-108">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="d28f7-109">**데이터 마이닝 구조 만들기** 페이지에서 **사용 하려는 데이터 마이닝 기술**에 대해 **Microsoft 시계열**을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-109">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Time Series**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="d28f7-110">**데이터 원본 뷰 선택** 페이지의 **사용 가능한 데이터 원본 뷰**에서 **salesbyregion**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-110">On the **Select Data Source View** page, under **Available data source views**, select **SalesByRegion**.</span></span>  
  
6.  <span data-ttu-id="d28f7-111">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-111">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="d28f7-112">**테이블 유형 지정** 페이지에서 vTimeSeries 테이블의 **사례** 열에 있는 확인란이 선택 되어 있는지 확인 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-112">On the **Specify Table Types** page, ensure that the check box in the **Case** column for the vTimeSeries table is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="d28f7-113">**학습 데이터 지정** 페이지에서 modelregion 및 ReportingDate 열에 대 한 **키** 열의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-113">On the **Specify the Training Data** page, select the check boxes in the **Key** column for the ModelRegion and ReportingDate columns.</span></span>  
  
     <span data-ttu-id="d28f7-114">데이터 원본 뷰를 만들 때 이 열을 논리적 기본 키로 지정했으므로 ReportingDate를 기본적으로 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-114">ReportingDate should be selected by default, because you specified this column as the logical primary key when you created the data source view.</span></span> <span data-ttu-id="d28f7-115">ModelRegion을 두 번째 키로 추가하면 알고리즘에 이 필드에 나열된 모델 및 지역의 각 조합에 대해 별도의 시계열을 만들도록 지시하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-115">By adding ModelRegion as a second key, you are telling the algorithm to create a separate time series for each combination of model and region listed in this field.</span></span>  
  
9. <span data-ttu-id="d28f7-116">수량, 열에 대 한 **입력** 및 **예측 가능한** 열의 확인란을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-116">Select the check boxes in the **Input** and **Predictable** columns for the Quantity, column, and then click **Next**.</span></span>  
  
     <span data-ttu-id="d28f7-117">**예측**가능을 선택 하 여이 열의 데이터에 대 한 예측을 만들려고 함을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-117">By selecting **Predictable**, you indicate that you want to create forecasts on the data in this column.</span></span> <span data-ttu-id="d28f7-118">그러나 이전 데이터에 대한 예측을 기반으로 하므로 열을 입력으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-118">However, because you want to base the forecasts on past data, you must also add the column as an input.</span></span>  
  
10. <span data-ttu-id="d28f7-119">**열 내용 및 데이터 형식 지정**페이지에서 선택 사항을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-119">On the page **Specify Columns' Content and Data Type**, review the selections.</span></span>  
  
     <span data-ttu-id="d28f7-120">ModelRegion 열은 **키** 열로 지정 되 고 ReportingDate 열은 **key Time** 열로 자동으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-120">The ModelRegion column is designated as a **Key** column and the ReportingDate column is automatically designated as a **Key Time** column.</span></span> <span data-ttu-id="d28f7-121">각 키 유형 중 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-121">You can have only one of each type of key.</span></span>  
  
11. <span data-ttu-id="d28f7-122">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-122">Click **Next**.</span></span>  
  
12. <span data-ttu-id="d28f7-123">**마법사 완료** 페이지에서 **마이닝 구조 이름**에을 입력 `Forecasting` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-123">On the **Completing the Wizard** page, for **Mining structure name**, type `Forecasting`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d28f7-124">드릴스루를 사용하는 옵션은 시계열 모델에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-124">The option to enable drillthrough is not available for time series models.</span></span>  
  
13. <span data-ttu-id="d28f7-125">**마이닝 모델 이름**에를 입력 한 `Forecasting` 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-125">In **Mining model name**, type `Forecasting`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="d28f7-126">데이터 마이닝 디자이너가 열리고 `Forecasting` 방금 만든 마이닝 구조가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d28f7-126">Data Mining Designer opens to display the `Forecasting` mining structure that you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d28f7-127">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="d28f7-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d28f7-128">&#40;중급 데이터 마이닝 자습서&#41;예측 구조 수정</span><span class="sxs-lookup"><span data-stu-id="d28f7-128">Modifying the Forecasting Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="d28f7-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d28f7-129">See Also</span></span>  
 <span data-ttu-id="d28f7-130">[데이터 마이닝 디자이너](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="d28f7-130">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="d28f7-131">Microsoft Time Series 알고리즘</span><span class="sxs-lookup"><span data-stu-id="d28f7-131">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
