---
title: 구조에 모델 추가 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, creating
ms.assetid: 8efd5bf4-4e6a-4ee8-971a-6efaed5f3b76
author: minewiskan
ms.author: owend
ms.openlocfilehash: b42cecafc2e3d676465e372e00fe472132f06a3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648239"
---
# <a name="add-model-to-structure-data-mining-add-ins-for-excel"></a><span data-ttu-id="f83fe-102">구조에 모델 추가(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="f83fe-102">Add Model to Structure (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="f83fe-103">![구조에 모델 추가 단추](media/dmc-addmodel.gif "구조에 모델 추가 단추")</span><span class="sxs-lookup"><span data-stu-id="f83fe-103">![Add Model to Structure button](media/dmc-addmodel.gif "Add Model to Structure button")</span></span>  
  
 <span data-ttu-id="f83fe-104">**구조에 모델 추가**를 클릭 하면 기존 마이닝 구조와 함께 사용할 새 마이닝 모델을 만드는 데 도움이 되는 마법사가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-104">When you click **Add Model to Structure**, a wizard starts that helps you create a new mining model to use with an existing mining structure.</span></span> <span data-ttu-id="f83fe-105">이 옵션은 동일한 데이터를 기반으로 하는 모델을 비교하거나 사용자 지정된 모델을 만들 수 있도록 하기 때문에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-105">This option is useful because it lets you compare models that are based on the same data, or create customized models.</span></span>  
  
 <span data-ttu-id="f83fe-106">Analysis Services 인스턴스에 필요한 데이터가 포함 되어 있지 않은 경우에는 [마이닝 구조 만들기 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) 마법사를 사용 하 여 마이닝 구조를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-106">If the instance of Analysis Services does not already contain the data you need, use the [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) wizard to set up a mining structure.</span></span> <span data-ttu-id="f83fe-107">또는 모델링 마법사 중 하나를 실행한 다음 마법사로 만든 구조에 새 모델을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-107">Or, you can launch one of the modeling wizards, and then add a new model to the structure created by the wizard.</span></span>  
  
 <span data-ttu-id="f83fe-108">마법사에서 지원 하지 않는 알고리즘을 사용 하 여 고급 모델을 만들려면 마이닝 구조를 만든 다음 **데이터 마이닝 고급 쿼리 편집기**를 사용 하 여 모델을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-108">To create advanced models using algorithms not supported by the wizards, create a mining structure and then add a model using the **Data Mining Advanced Query Editor**.</span></span>  
  
## <a name="add-a-new-model-to-an-existing-structure"></a><span data-ttu-id="f83fe-109">기존 구조에 새 모델 추가</span><span class="sxs-lookup"><span data-stu-id="f83fe-109">Add a new model to an existing structure</span></span>  
  
1.  <span data-ttu-id="f83fe-110">**데이터 마이닝** 리본에서 **고급**아래에 있는 화살표를 클릭 한 다음 **구조에 모델 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-110">On the **Data Mining** ribbon, click the arrow under **Advanced**, and then select **Add Model to Structure**.</span></span>  
  
2.  <span data-ttu-id="f83fe-111">**구조 선택** 대화 상자에서 사용할 데이터가 포함 된 구조를 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-111">In the **Select Structure** dialog box, choose the structure that contains the data you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="f83fe-112">**팁**: 필요한 데이터가 포함 된 마이닝 구조를 잘 모르겠으면 **모델 문서화** 마법사를 사용 하 여 데이터에 대 한 열 및 기본 통계를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-112">**Tip**: If you are not sure which mining structure contains the data you need, use the **Document Model** wizard to view the columns and basic statistics about the data.</span></span>  
  
     <span data-ttu-id="f83fe-113">마이닝 구조를 찾을 수 없는 경우 현재 사용 중인 연결을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-113">If you can't find a mining structure, check the connection that you are currently using.</span></span> <span data-ttu-id="f83fe-114">다른 서버에 대한 연결을 열어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-114">You might need to open a connection to a different server.</span></span>  
  
3.  <span data-ttu-id="f83fe-115">**마이닝 알고리즘 선택** 대화 상자에서 새 마이닝 모델에 사용할 마이닝 알고리즘을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-115">In the **Select Mining Algorithm** dialog box, choose a mining algorithm to use in the new mining model.</span></span>  
  
     <span data-ttu-id="f83fe-116">대화 상자에는 마법사에 표시 되는 것 보다 훨씬 더 많은 옵션이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-116">Notice that the dialog box provides a lot more options than you'll see in the wizards.</span></span> <span data-ttu-id="f83fe-117">데이터가 호환되는 경우 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에서 지원되는 어떠한 알고리즘이라도 사용하여 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-117">You can create a model using any algorithm supported on your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, provided your data is compatible.</span></span>  
  
4.  <span data-ttu-id="f83fe-118">**매개** 변수 단추를 클릭 하 여 **알고리즘 매개 변수** 대화 상자를 열고 알고리즘의 매개 변수를 사용자 지정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-118">We recommend that you also click the **Parameters** button to open the **Algorithm Parameters** dialog box and customize parameters on the algorithm.</span></span> <span data-ttu-id="f83fe-119">이 옵션은 사용자 지정 마이닝 모델을 만들 수 있는 가장 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-119">This option is the easiest way to create custom mining models.</span></span>  
  
5.  <span data-ttu-id="f83fe-120">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-120">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="f83fe-121">**열 선택** 대화 상자에서 열 목록을 검토 하 고 필요한 경우 열 사용을 다음 값 중 하나로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-121">In the **Select Columns** dialog box, review the list of columns, and if necessary, change the usage of the columns to one of these values:</span></span>  
  
    -   <span data-ttu-id="f83fe-122">**입력**.</span><span class="sxs-lookup"><span data-stu-id="f83fe-122">**Input**.</span></span> <span data-ttu-id="f83fe-123">열이 결과에 영향을 미칠 수 있는 변수를 포함하고 있으며 모델에 대한 입력으로 사용되도록 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-123">Indicates that the column contains variables that may affect the outcome and should be used as inputs to the model.</span></span>  
  
    -   <span data-ttu-id="f83fe-124">**입력 및 예측**.</span><span class="sxs-lookup"><span data-stu-id="f83fe-124">**Input and Predict**.</span></span> <span data-ttu-id="f83fe-125">데이터가 입력으로 사용되어야 하고 이러한 값을 예측하려고 한다고 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-125">Indicates that the data should be used as an input, and that you also want to predict these values.</span></span>  
  
    -   <span data-ttu-id="f83fe-126">**예측만**</span><span class="sxs-lookup"><span data-stu-id="f83fe-126">**Predict only**.</span></span> <span data-ttu-id="f83fe-127">데이터가 모델에 대한 입력으로 사용되지 않도록 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-127">Indicates that the data should not be used as an input for the model.</span></span>  
  
    -   <span data-ttu-id="f83fe-128">**Key**.</span><span class="sxs-lookup"><span data-stu-id="f83fe-128">**Key**.</span></span> <span data-ttu-id="f83fe-129">각 모델에는 적어도 하나의 키가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-129">Each model requires at least one key.</span></span> <span data-ttu-id="f83fe-130">모델 유형에 따라 **SequenceKey** 또는 **timekey**와 같은 특수 키를 추가로 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-130">Depending on the model type, you might also have the option to additional special keys, such as the **SequenceKey** or **TimeKey**.</span></span>  
  
    -   <span data-ttu-id="f83fe-131">**사용 하지 마십시오**.</span><span class="sxs-lookup"><span data-stu-id="f83fe-131">**Do not use**.</span></span> <span data-ttu-id="f83fe-132">데이터가 구조에 있는 경우에도 모델에서 사용되지 않도록 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-132">Indicates that the data should not be used in the model, even if present in the structure.</span></span>  
  
7.  <span data-ttu-id="f83fe-133">찾아보기 **(...)** 단추를 클릭 하 여 **열 모델 플래그 설정** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-133">Click the browse **(...)** button to open the **Set Column Model Flags** dialog box.</span></span>  
  
     <span data-ttu-id="f83fe-134">각 데이터 열의 사용법이 모델에 적합한지 확인하는 데 1분 정도 소요됩니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-134">Take a minute to verify that the usage of each data column is appropriate for the model.</span></span> <span data-ttu-id="f83fe-135">이 단계는 모델을 처리하려고 할 때 오류를 방지하기 위한 중요한 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-135">This is an important step for preventing errors when you try to process the model.</span></span>  
  
     <span data-ttu-id="f83fe-136">예를 들어 의사 결정 트리 모델용으로 만들어진 구조를 다시 사용하고 Naïve Bayes 알고리즘을 이 구조에 적용하는 경우 데이터 형식이 `Numeric`이고 내용 유형이 `Continuous`인 열이 불연속 변수로 범주화되거나 변경되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-136">For example, if you re-use a structure that was created for a decision trees model and apply the Naïve Bayes algorithm to it, columns that have the data type `Numeric` and the content type `Continuous` will need to be binned or changed to discrete variables.</span></span>  
  
     <span data-ttu-id="f83fe-137">구조에 있는 열이 새 알고리즘에 적용 되지 않는 경우 **사용 안 함**을 선택 하 여 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-137">If columns in the structure are not applicable to the new algorithm, you can bypass them by selecting **Do not use**.</span></span>  
  
8.  <span data-ttu-id="f83fe-138">**열 모델 플래그 설정** 대화 상자에서 모델링 플래그 (있는 경우)를 검토 하거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-138">In the **Set Column Model Flags** dialog box, review or set the modeling flags, if any.</span></span>  
  
     <span data-ttu-id="f83fe-139">모델링 플래그를 사용하여 null 처리 방법 등을 제어할 수 잇습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-139">Modeling flags let you control the way that nulls are handled, among other things.</span></span> <span data-ttu-id="f83fe-140">자세한 내용은 [모델링 플래그&#40;데이터 마이닝&#41;](data-mining/modeling-flags-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f83fe-140">For more information, see [Modeling Flags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).</span></span>  
  
     <span data-ttu-id="f83fe-141">완료 되 면 **확인** 을 클릭 하 여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-141">Click **OK** when done to close the dialog box.</span></span>  
  
9. <span data-ttu-id="f83fe-142">**마침** 대화 상자에서 새 마이닝 모델의 이름과 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-142">In the **Finish** dialog box, type a name and description for the new mining model.</span></span>  
  
     <span data-ttu-id="f83fe-143">작성한 모델의 유형에 따라 다음과 같은 옵션을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-143">Depending on the type of model you built, you might also have these options:</span></span>  
  
    -   <span data-ttu-id="f83fe-144">마이닝 모델을 작성한 후 완성된 마이닝 모델을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-144">Browse the completed mining model after it is built.</span></span>  
  
    -   <span data-ttu-id="f83fe-145">모델에서 원본 데이터로 드릴스루를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-145">Use drillthrough from the model to the source data.</span></span>  
  
         <span data-ttu-id="f83fe-146">자세한 내용은 [마이닝 모델에 대 한 드릴스루](data-mining/drillthrough-on-mining-models.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f83fe-146">For more information, see [Drillthrough on Mining Models](data-mining/drillthrough-on-mining-models.md).</span></span>  
  
10. <span data-ttu-id="f83fe-147">**마침**을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-147">Click **Finish** to save your changes.</span></span> <span data-ttu-id="f83fe-148">이렇게 하면 새 모델이 서버에 배포되고 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-148">As you do so the new model is deployed to the server and processed.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="f83fe-149">관련 옵션</span><span class="sxs-lookup"><span data-stu-id="f83fe-149">Related Options</span></span>  
  
|<span data-ttu-id="f83fe-150">옵션</span><span class="sxs-lookup"><span data-stu-id="f83fe-150">Option</span></span>|<span data-ttu-id="f83fe-151">주석</span><span class="sxs-lookup"><span data-stu-id="f83fe-151">Comments</span></span>|  
|------------|--------------|  
|<span data-ttu-id="f83fe-152">**구조 또는 모델 선택** 대화 상자</span><span class="sxs-lookup"><span data-stu-id="f83fe-152">**Select Structure or Model** dialog box</span></span>|<span data-ttu-id="f83fe-153">새로운 모델을 작성하기 위한 기반으로 사용할 기존 마이닝 구조를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-153">Choose en existing mining structure to use as the basis for building a new model.</span></span>  <span data-ttu-id="f83fe-154">선택한 구조는 현재 연결에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-154">The structure you pick must be located on the current connection.</span></span> <span data-ttu-id="f83fe-155">그렇지 않은 경우에는 [원본 데이터에 연결 &#40;Excel 용 데이터 마이닝 클라이언트&#41;](connect-to-source-data-data-mining-client-for-excel.md) 도구를 사용 하 여 연결을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-155">If not, change connections using the [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) tool.</span></span>|  
|<span data-ttu-id="f83fe-156">**마이닝 알고리즘 선택** 대화 상자</span><span class="sxs-lookup"><span data-stu-id="f83fe-156">**Select Mining Algorithm** dialog Box</span></span>|<span data-ttu-id="f83fe-157">데이터 마이닝 알고리즘의 목록은 연결되어 있는 서버에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-157">The list of data mining algorithms depends on which server you are connected to.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="f83fe-158">는 Standard 및 Enterprise 버전에서 서로 다른 알고리즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-158">provides different algorithms in the Standard and Enterprise editions.</span></span> <span data-ttu-id="f83fe-159">관리자가 사용자 지정 알고리즘을 추가했을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-159">Your administrator also might have added custom algorithms.</span></span><br /><br /> <span data-ttu-id="f83fe-160">알고리즘이 표시 되지 않으면 인스턴스에 연결 되어 있는지 확인 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-160">If you can't see any algorithms, verify that you are connected to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>|  
|<span data-ttu-id="f83fe-161">**알고리즘 매개 변수** 대화 상자</span><span class="sxs-lookup"><span data-stu-id="f83fe-161">**Algorithm Parameters** Dialog Box</span></span>|<span data-ttu-id="f83fe-162">이러한 설정에서 분석 방법과 관련된 매개 변수를 사용하여 각 알고리즘을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-162">In these settings, you can customize each algorithm using parameters specific to the analytical method.</span></span> <span data-ttu-id="f83fe-163">또한 모델의 결과가 여러 학습 패스에서 재현될 수 있도록 하기 위해 초기값을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-163">You can also set a seed to ensure that the results of the model can be reproduced across multiple training passes.</span></span><br /><br /> <span data-ttu-id="f83fe-164">자세한 내용은 [데이터 마이닝 추가 기능을&#41;SQL Server &#40;알고리즘 매개 변수 ](algorithm-parameters-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f83fe-164">For more information, see [Algorithm Parameters &#40;SQL Server Data Mining Add-ins&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md).</span></span>|  
|<span data-ttu-id="f83fe-165">**열 모델 플래그 설정** 대화 상자</span><span class="sxs-lookup"><span data-stu-id="f83fe-165">**Set Column Model Flags** Dialog Box</span></span>|<span data-ttu-id="f83fe-166">모델링 플래그는 누락된 데이터가 처리될 방법을 지정하여 모델을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-166">Modeling flags can improve your model by specifying how missing data is to be handled.</span></span> <span data-ttu-id="f83fe-167">자세한 내용은 [모델링 플래그&#40;데이터 마이닝&#41;](data-mining/modeling-flags-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f83fe-167">For more information, see [Modeling Flags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).</span></span>|  
  
###  <a name="setting-column-usage"></a><a name="Bkmk_mdlcolumn"></a><span data-ttu-id="f83fe-168">열 사용법 설정</span><span class="sxs-lookup"><span data-stu-id="f83fe-168">Setting Column Usage</span></span>  
 <span data-ttu-id="f83fe-169">기존 마이닝 구조에 새 모델을 추가할 때 마이닝 구조에 있는 각 데이터 열의 사용법을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-169">When you add a new model to an existing mining structure, you must specify how the model will use each of the columns of data in the mining structure.</span></span> <span data-ttu-id="f83fe-170">이 마법사의 옵션이 마이닝 구조의 옵션 보다 훨씬 더 자세히 관찰 되는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-170">You'll probably observe that the options in this wizard are far more detailed than the options on the mining structure.</span></span> <span data-ttu-id="f83fe-171">이유</span><span class="sxs-lookup"><span data-stu-id="f83fe-171">Why?</span></span>  
  
 <span data-ttu-id="f83fe-172">마법사를 사용하여 모델과 구조를 함께 만들 때 알고리즘에서 데이터를 사용하는 방식을 제어하는 많은 옵션이 자동으로 설정되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-172">The reason is that when you create a model and a structure together using a wizard, many of the options that control how data is used by the algorithm are set automatically.</span></span> <span data-ttu-id="f83fe-173">그러나 기존 구조에 새 모델을 추가할 때는 이러한 옵션을 수동으로 확인하고 데이터가 분석에 사용되어야 하는지 여부, 데이터 형식이 올바른지 여부 등을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-173">However, when you add a new model to an existing, you need to see these options manually, and specify whether data should be used for analysis, whether the data type is correct, and so forth.</span></span>  
  
 <span data-ttu-id="f83fe-174">기존 데이터에 새로운 알고리즘을 적용할 때 오류 메시지가 나타날 수도 있지만, 일반적으로 이러한 메시지는 모델이 처리될 수 있도록 허용하기 위해 필요한 수정에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-174">You might get error messages when applying new algorithms to existing data, but these messages generally provide detailed information about the corrections you need to make to allow the model to be processed.</span></span> <span data-ttu-id="f83fe-175">일반적인 문제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-175">Typical problems include the following:</span></span>  
  
-   <span data-ttu-id="f83fe-176">구조에 포함된 데이터 형식과 다른 데이터 형식이 모델에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-176">The model expects a different data type than the structure contains.</span></span>  
  
     <span data-ttu-id="f83fe-177">숫자만 사용할 수 있는 알고리즘도 있고 텍스트만 사용할 수 있는 알고리즘도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-177">Some algorithms can only work with numbers; some can only work with text.</span></span> <span data-ttu-id="f83fe-178">데이터의 형식이 새 모델에 적합하지 않은 경우 모델이 처리될 수 있도록 하기 위해 구조를 수정해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-178">If your data is the wrong type for the new model, you might need to modify the structure to enable the model to process.</span></span>  
  
-   <span data-ttu-id="f83fe-179">마이닝 구조에는 예측 가능한 특성이 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-179">The mining structure contains no predictable attribute.</span></span>  
  
     <span data-ttu-id="f83fe-180">클러스터링 모델은 예측 가능한 값을 사용하지 않고 작성할 수 있지만, 다른 모델의 경우 일반적으로 예측에 대한 단일 열을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-180">Clustering models can be built with no predictable value, but other models generally require that you specify a single column for prediction.</span></span>  
  
-   <span data-ttu-id="f83fe-181">데이터의 컴포지션이 선택한 알고리즘과 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-181">The composition of the data is incompatible with the algorithm you've chosen.</span></span>  
  
     <span data-ttu-id="f83fe-182">고유한 규칙에 따라 신중하게 구조화된 데이터가 필요한 분석 유형도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-182">Some types of analysis require data that is carefully structured according to unique rules.</span></span> <span data-ttu-id="f83fe-183">해당하는 예로 예측 모델과 연결 모델이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-183">Examples are forecasting models and association models.</span></span> <span data-ttu-id="f83fe-184">사용자 지정 등을 사용하여 동일한 유형의 새 모델을 쉽게 추가할 수 있지만, 데이터가 다른 알고리즘과 작동하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-184">You can easily add new models of the same type, perhaps with customizations, but the data might not work with other algorithms.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="f83fe-185">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f83fe-185">Requirements</span></span>  
 <span data-ttu-id="f83fe-186">데이터 마이닝 모델을 만들려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-186">To create data mining models, you must have a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="f83fe-187">연결을 만들거나 변경 하는 방법에 대 한 자세한 내용은 [Excel 용 데이터 마이닝 클라이언트&#41;&#40;원본 데이터에 연결 ](connect-to-source-data-data-mining-client-for-excel.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f83fe-187">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="f83fe-188">원하는 데이터 마이닝 구조를 찾을 수 없는 경우 해당 구조가 다른 인스턴스 또는 다른 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 저장되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f83fe-188">If you cannot see the data mining structure that you want, it could be that the structure was saved to a different instance or different [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="f83fe-189">다른 데이터 마이닝 연결을 변경 하는 방법에 대 한 자세한 내용은 [데이터 마이닝 서버에 연결](connect-to-a-data-mining-server.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f83fe-189">For information about how to change to a different data mining connection, see [Connect to a Data Mining Server](connect-to-a-data-mining-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f83fe-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f83fe-190">See Also</span></span>  
 [<span data-ttu-id="f83fe-191">데이터 마이닝 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="f83fe-191">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)   
