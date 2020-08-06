---
title: 예측 구조 수정 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9acf410fe04c53493e559257832e5e21727bc45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639170"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="ac11a-102">예측 구조 수정(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="ac11a-102">Modifying the Forecasting Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="ac11a-103">이전 태스크에서 만든 마이닝 구조에는 단일 예측 모델이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-103">The mining structure that you created in the previous task contains a single forecasting model.</span></span> <span data-ttu-id="ac11a-104">모델을 처리하고 탐색하기 전에 해당 구조를 약간 변경하고 속성 중 하나를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-104">Before you process and explore the model, you must change its structure slightly and modify one of its properties.</span></span>  
  
## <a name="modifying-the-mining-structure"></a><span data-ttu-id="ac11a-105">마이닝 구조 수정</span><span class="sxs-lookup"><span data-stu-id="ac11a-105">Modifying the Mining Structure</span></span>  
 <span data-ttu-id="ac11a-106">데이터 마이닝 디자이너의 **마이닝 구조** 탭을 사용 하 여 마이닝 구조를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-106">You can change the mining structure by using the **Mining Structure** tab of Data Mining Designer.</span></span> <span data-ttu-id="ac11a-107">데이터 마이닝 마법사로 모델을 만들 때에는 ReportingDate, ModelRegion 및 Quantity라는 3개의 열을 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-107">When you created the model with the Data Mining Wizard, you used three columns: ReportingDate, ModelRegion, and Quantity.</span></span> <span data-ttu-id="ac11a-108">그러나 **예측** 테이블에는 판매 금액을 예측 하는 데 사용할 수 있는 amount 열도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-108">However, the **Forecasting** table also contains an Amount column, which you can use to forecast the amount of sales.</span></span> <span data-ttu-id="ac11a-109">**마이닝 구조** 탭을 사용 하 여 데이터 원본 뷰의이 열을 마이닝 구조에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-109">By using the **Mining Structure** tab, you can add this column from the data source view to the mining structure.</span></span>  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a><span data-ttu-id="ac11a-110">Forecasting 마이닝 구조에 Amount 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ac11a-110">To add the Amount column to the Forecasting mining structure</span></span>  
  
1.  <span data-ttu-id="ac11a-111">데이터 마이닝 디자이너의 **마이닝 구조** 탭에 있는 **데이터 원본 뷰** 창에서 vTimeSeries 테이블의 Amount 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-111">On the **Mining Structure** tab of Data Mining Designer, in the **Data Source View** pane, select the Amount column in the vTimeSeries table.</span></span>  
  
2.  <span data-ttu-id="ac11a-112">**데이터 원본 뷰** 창에서 **예측** 구조의 열 목록으로 Amount 열을 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-112">Drag the Amount column from the **Data Source View** pane into the list of columns for the **Forecasting** structure.</span></span>  
  
     <span data-ttu-id="ac11a-113">이제 Amount 열이 **예측** 마이닝 구조에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-113">The Amount column is now included in the **Forecasting** mining structure.</span></span>  
  
## <a name="modifying-the-columns-in-the-mining-model"></a><span data-ttu-id="ac11a-114">마이닝 모델에서 열 수정</span><span class="sxs-lookup"><span data-stu-id="ac11a-114">Modifying the Columns in the Mining Model</span></span>  
 <span data-ttu-id="ac11a-115">구조에 새 열을 추가했기 때문에 모델에서 열을 사용할 방법을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-115">Because you added a new column to the structure, you must define how the model will use the column.</span></span> <span data-ttu-id="ac11a-116">데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 열이 사용 되는 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-116">You can specify how the column will be used on the **Mining Models** tab of Data Mining Designer.</span></span>  
  
 <span data-ttu-id="ac11a-117">마이닝 **모델** 탭에는 표의 **구조** 열에 마이닝 구조에 포함 된 열이 나열 되며 모델 이름이 있는 열 (이 경우 **예측**)에는 마이닝 모델에 포함 된 열이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-117">The **Mining Models** tab lists the columns that the mining structure contains in the **Structure** column of the grid, and lists the columns that the mining model contains in the column that has the name of the model, in this case **Forecasting**.</span></span> <span data-ttu-id="ac11a-118">열의 이름을 클릭하여 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-118">Click the names of the columns to make modifications.</span></span> <span data-ttu-id="ac11a-119">**예측** 마이닝 모델에서 Amount 열은 입력 열로 사용 되 고 향후 판매를 예측 하는 데도 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-119">In the **Forecasting** mining model, the Amount column is used as an input column and is also used to forecast future sales.</span></span> <span data-ttu-id="ac11a-120">따라서 열의 속성을 설정해야 입력 열과 예측 가능한 열 모두로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-120">Therefore, you must set the properties of the column so that it can be used as both an input column and a predictable column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac11a-121">**마이닝 모델** 탭에서는 동일한 구조를 기반으로 새 모델을 만들 수도 있으며 각 모델에 대 한 알고리즘 및 열 속성을 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-121">In the **Mining Models** tab, you can also create new models based on the same structure, and you can adjust the algorithm and column properties for each model.</span></span> <span data-ttu-id="ac11a-122">그러나 해당 변경 내용을 적용하기 전에 모델을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-122">However, you must process the model before these changes take effect.</span></span>  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a><span data-ttu-id="ac11a-123">판매액 열을 사용할 방법을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="ac11a-123">To define how the Amount column will be used</span></span>  
  
1.  <span data-ttu-id="ac11a-124">**마이닝 모델** 탭에 있는 표의 **예측** 열에서 Amount 행의 셀을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-124">In the **Forecasting** column of the grid on the **Mining Models** tab, click the cell in the Amount row.</span></span>  
  
2.  <span data-ttu-id="ac11a-125">목록에서 **예측** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-125">Select **Predict** from the list.</span></span>  
  
     <span data-ttu-id="ac11a-126">이제 Amount 열은 입력 열과 예측 가능한 열 모두로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-126">The Amount column is now both an input column and a predictable column.</span></span>  
  
 <span data-ttu-id="ac11a-127">열을 선택 하 고 **속성** 창을 열어 개별 열의 속성을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-127">You can also change the properties of individual columns by selecting the column and opening the **Properties** window.</span></span> <span data-ttu-id="ac11a-128">**속성** 창을 열려면 열 이름을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-128">To open the **Properties** window, right-click the column name, and then select **Properties**.</span></span> <span data-ttu-id="ac11a-129">개별 모델의 열 내에서 속성을 변경하면 해당 모델에 대해서만 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-129">If you change a property within the column for an individual model, you can change the properties only for that model.</span></span> <span data-ttu-id="ac11a-130">그러나 **구조** 열 내에서 속성을 변경 하면 해당 구조와 연결 된 모든 모델에 변경 내용이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-130">However, when you change a property within the **Structure** column, the change affects every model that is associated with the structure.</span></span> <span data-ttu-id="ac11a-131">모델 또는 구조를 변경할 때마다 효과를 확인하려면 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac11a-131">Whenever you make changes to the model or structure, you must reprocess to see the effects.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ac11a-132">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="ac11a-132">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ac11a-133">&#40;중급 데이터 마이닝 자습서를 통해 예측 모델 사용자 지정 및 처리&#41;</span><span class="sxs-lookup"><span data-stu-id="ac11a-133">Customizing and Processing the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="ac11a-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac11a-134">See Also</span></span>  
 <span data-ttu-id="ac11a-135">[마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ac11a-135">[Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="ac11a-136">마이닝 모델&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="ac11a-136">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
