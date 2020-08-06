---
title: 샘플 데이터 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- holdout
- testing cases
- training cases
- partitioning data [data mining]
- mining models, testing
ms.assetid: 35907ae6-887f-4cb3-a750-cff3d7683d90
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17da9a42f4d76f5c271d5b225cf897a8ac2e97ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647924"
---
# <a name="sample-data-sql-server-data-mining-add-ins"></a><span data-ttu-id="08547-102">데이터 샘플링(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="08547-102">Sample Data (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="08547-103">![데이터 마이닝 리본의 데이터 분할 마법사](media/dmc-partition.gif "데이터 마이닝 리본의 데이터 분할 마법사")</span><span class="sxs-lookup"><span data-stu-id="08547-103">![Partition Data wizard in Data Mining ribbon](media/dmc-partition.gif "Partition Data wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="08547-104">**데이터 샘플링** 마법사를 사용 하면 모델을 작성 (학습) 하 고 모델을 테스트 하기 위한 두 개의 집합으로 원본 데이터를 쉽게 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-104">The **Sample Data** wizard makes it easy to divide your source data into two sets, one for building (training) the model and one for testing the model.</span></span> <span data-ttu-id="08547-105">이 마법사에서는 대상을 더욱 잘 나타내는 새 데이터 집합을 작성할 수 있도록 데이터를 다시 샘플링하는 옵션도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-105">This wizard also provides an option for resampling the data to build a new data set that better represents your target.</span></span>  
  
 <span data-ttu-id="08547-106">모델을 학습하고 테스트하기 위해 적합한 종류의 데이터를 만드는 것은 데이터 마이닝에서 중요한 부분이지만 적합한 도구 없이는 힘든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="08547-106">Creating the right kind of data for training and testing your models is an important part of data mining, but one that can be tedious without the right tools.</span></span> <span data-ttu-id="08547-107">마법사는 층별 샘플링을 수행하여 학습 및 테스트 집합의 균형이 잘 잡히도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-107">The wizard performs stratified sampling to make sure that training and testing sets are well balanced.</span></span>  
  
## <a name="random-sampling-and-oversampling"></a><span data-ttu-id="08547-108">무작위 샘플링 및 과다 샘플링</span><span class="sxs-lookup"><span data-stu-id="08547-108">Random Sampling and Oversampling</span></span>  
 <span data-ttu-id="08547-109">.</span><span class="sxs-lookup"><span data-stu-id="08547-109">.</span></span> <span data-ttu-id="08547-110">무작위 샘플링은 모델을 테스트하는 데 사용하는 데이터가 모델을 만드는 데 사용하는 데이터를 잘 나타내는지 확인할 수 있는 가장 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="08547-110">Random sampling is the best way to ensure that the data you use for testing a model fairly represents the data that you use for creating the model.</span></span> <span data-ttu-id="08547-111">Excel 또는 외부 데이터 원본에 저장된 데이터를 무작위로 샘플링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-111">You can randomly sample data that is stored in Excel or in an external data source</span></span>  
  
 <span data-ttu-id="08547-112">무작위 샘플링 옵션을 사용 하면 **데이터 샘플링** 마법사에서 자동으로 학습 및 테스트 데이터 집합을 만들고 나중에 참조할 수 있도록 개별 Excel 워크시트로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-112">If you use the random sampling option, the **Sample Data** wizard automatically creates training and test data sets and outputs them into separate Excel worksheets for later reference.</span></span>  
  
 <span data-ttu-id="08547-113">데이터가 외부 데이터 원본이 아닌 Excel 통합 문서에 저장 되어 있는 경우 *과다 샘플링*를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-113">If your data is stored in an Excel workbook, and not an external data source, you also have the option to use *oversampling*.</span></span> <span data-ttu-id="08547-114">이 옵션을 사용할 때 데이터에서 부족할 수 있는 대상 값을 지정합니다. 이렇게 하면 마법사는 대상 값이 더 포함된 균형이 잡힌 집합을 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-114">With this option, you specify a target value that might be scarce in your data, and the wizard will collect a balanced set that includes more of the target value.</span></span> <span data-ttu-id="08547-115">마법사에 목표 백분율을 달성하거나 특정 개수의 행을 만들도록 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-115">You can direct the wizard to achieve a targeted percentage, or to create a certain number of rows.</span></span>  
  
 <span data-ttu-id="08547-116">과다 샘플링 옵션을 사용 하는 경우 **데이터 샘플링** 마법사는 새로 균형이 조정 된 예제 데이터를 포함 하는 새 워크시트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08547-116">If you use the oversampling option, the **Sample Data** wizard creates a new worksheet that contains the newly balanced sample data.</span></span>  
  
## <a name="using-the-sample-data-wizard"></a><span data-ttu-id="08547-117">데이터 샘플링 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="08547-117">Using the Sample Data Wizard</span></span>  
  
#### <a name="to-separate-data-into-training-and-testing-sets"></a><span data-ttu-id="08547-118">데이터를 학습 집합 및 테스트 집합으로 나누려면</span><span class="sxs-lookup"><span data-stu-id="08547-118">To separate data into training and testing sets</span></span>  
  
1.  <span data-ttu-id="08547-119">**데이터 마이닝** 리본에서 **샘플 데이터**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-119">In the **Data Mining** ribbon, click **Sample Data**.</span></span>  
  
2.  <span data-ttu-id="08547-120">**원본 데이터 선택** 페이지에서 분할할 **데이터가** Excel 범위 또는 테이블에 있는지 아니면 외부 데이터 원본에 있는지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-120">On the **Select Source Data** page, specify whether the **data** that you want to partition is in an Excel range or table, or in an external data source.</span></span>  
  
3.  <span data-ttu-id="08547-121">**샘플링 유형 선택** 페이지에서 무작위 샘플링을 통해 학습 및 테스트 데이터 집합을 만들지 아니면 과다 샘플링로 새 데이터 집합을 만들지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-121">On the **Select Sampling Type** page, specify whether you want to create training and test data sets by random sampling, or create a new data set by oversampling.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08547-122">외부 데이터 원본을 사용할 경우 무작위 샘플링 옵션만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-122">If you are using an external data source, only the random sampling option is available.</span></span> <span data-ttu-id="08547-123">외부 데이터로 과다 샘플링을 사용하려면 Excel 데이터 연결을 사용하여 Excel 워크시트로 데이터를 가져온 다음 데이터 샘플링 마법사를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="08547-123">If you want to use oversampling with external data, you can import the data to an Excel workbook by using an Excel data connection, and then use the Sample Data wizard.</span></span>  
  
4.  <span data-ttu-id="08547-124">선택한 샘플링 방법에 따라 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-124">Set options specific to the sampling method that you selected.</span></span>  
  
    -   <span data-ttu-id="08547-125">무작위 샘플링의 경우 테스트에 사용할 원래 데이터의 비율 또는 테스트 데이터 집합에 사용할 총 행 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-125">For random sampling, specify either a percentage of the original data to use for testing, or the total number of rows to use in the test data set.</span></span>  
  
    -   <span data-ttu-id="08547-126">과다 샘플링의 경우 강조할 열과 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-126">For oversampling, select the column and value that you want to emphasize.</span></span> <span data-ttu-id="08547-127">그런 다음 새 데이터 집합의 총 행 개수와 대상 값에 포함해야 할 새 데이터 집합의 행 비율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-127">Then, specify the total number of rows in the new data set, and the percentage of rows in the new data set that should include the target value.</span></span>  
  
         <span data-ttu-id="08547-128">과다 샘플링의 대상 값은 불연속 값이어야 합니다. 연속 숫자 데이터는 과다 샘플링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-128">The target value for oversampling must be a discrete value; you cannot oversample continuous numeric data.</span></span>  
  
5.  <span data-ttu-id="08547-129">**마침 페이지**에서 새 데이터 집합의 기본 이름을 그대로 적용 하거나 새 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-129">On the **Finish page**, accept the default names for the new data sets, or type a new name.</span></span>  
  
     <span data-ttu-id="08547-130">마법사에서 각 데이터 집합에 대한 새 워크시트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08547-130">The wizard creates new worksheets for each set of data.</span></span>  
  
 <span data-ttu-id="08547-131">Excel용 데이터 마이닝 클라이언트에서 제공되는 대부분의 마법사에는 데이터를 무작위로 학습 집합과 테스트 집합으로 구분하는 옵션도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-131">Most of the wizards in the Data Mining Client for Excel also provide an option to randomly separate your data into training and testing sets.</span></span> <span data-ttu-id="08547-132">그러나 마법사를 사용하는 경우 데이터가 같은 워크시트나 다른 데이터 원본에 유지되며 특정 행이 테스트 사례인지 또는 학습 사례인지에 대한 정보는 내부적으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="08547-132">However, if you use the wizards, your data stays in the same worksheet (or other data source), and the information about whether a particular row is a test case or training case is stored internally.</span></span> <span data-ttu-id="08547-133">이와 대조적으로 **데이터 샘플링** 마법사를 사용 하면 쉽게 참조할 수 있도록 테스트 및 학습 데이터가 개별 워크시트로 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="08547-133">In contrast, when you use the **Sample Data** wizard, the testing and training data are output to separate worksheets for easy reference.</span></span>  
  
## <a name="related-options"></a><span data-ttu-id="08547-134">관련 옵션</span><span class="sxs-lookup"><span data-stu-id="08547-134">Related Options</span></span>  
 <span data-ttu-id="08547-135">마법사를 진행하면서 다음과 같은 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-135">As you progress through the wizard, you will have these options:</span></span>  
  
|<span data-ttu-id="08547-136">옵션</span><span class="sxs-lookup"><span data-stu-id="08547-136">Options</span></span>|<span data-ttu-id="08547-137">주석</span><span class="sxs-lookup"><span data-stu-id="08547-137">Comments</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="08547-138">원본 데이터 선택 대화 상자(Excel용 데이터 마이닝 클라이언트)</span><span class="sxs-lookup"><span data-stu-id="08547-138">Select Source Data Dialog Box (Data Mining Client for Excel)</span></span>|<span data-ttu-id="08547-139">데이터를 포함하는 Excel 범위 또는 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-139">Select an Excel range or table that contains the data.</span></span> <span data-ttu-id="08547-140">외부 데이터를 사용하려는 경우 데이터는 관계형일 수 있지만 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터 원본에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-140">If you want to use external data, the data can be relational, but it must be included in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="08547-141">T</span><span class="sxs-lookup"><span data-stu-id="08547-141">T</span></span>|  
|<span data-ttu-id="08547-142">샘플링 유형 선택 페이지(Excel용 데이터 마이닝 클라이언트)</span><span class="sxs-lookup"><span data-stu-id="08547-142">Select Sampling Type Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="08547-143">외부 데이터 원본을 사용할 경우 무작위 샘플링 옵션만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-143">If you use an external data source, you are limited to using the random sampling option.</span></span> <span data-ttu-id="08547-144">또한 **행 개수** 옵션을 사용 하 여 최종 데이터 집합에 만들 행 수를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-144">Also, you must specify the number of rows to create in the final data set, by using the **Row count** option.</span></span> <span data-ttu-id="08547-145">원본 데이터의 비율은 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-145">You cannot specify a percentage of the source data.</span></span>|  
|<span data-ttu-id="08547-146">임의 샘플링 페이지(Excel용 데이터 마이닝 클라이언트)</span><span class="sxs-lookup"><span data-stu-id="08547-146">Random Sampling Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="08547-147">원본 또는 특정 수의 행에서 특정 비율의 행을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-147">You can copy a percentage of rows from the source, or a specific number of rows.</span></span>|  
|<span data-ttu-id="08547-148">과다 샘플링 페이지(Excel용 데이터 마이닝 클라이언트)</span><span class="sxs-lookup"><span data-stu-id="08547-148">Oversampling Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="08547-149">**대상 상태**</span><span class="sxs-lookup"><span data-stu-id="08547-149">**Target state**</span></span><br /><br /> <span data-ttu-id="08547-150">원래 데이터 집합에서 실제보다 과소 표시된 목록의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-150">Select a value from the list that is underrepresented in the original data set.</span></span> <span data-ttu-id="08547-151">과다 샘플링하면 이 상태를 포함하는 데이터 행의 비율이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="08547-151">Oversampling will increase the proportion of data rows that include this state.</span></span><br /><br /> <span data-ttu-id="08547-152">**샘플 크기**</span><span class="sxs-lookup"><span data-stu-id="08547-152">**Sample size**</span></span><br /><br /> <span data-ttu-id="08547-153">추출할 행의 총 수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08547-153">Select the total number of rows to extract.</span></span> <span data-ttu-id="08547-154">이 값은 최종 데이터 집합의 크기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="08547-154">This value represents the size of the final data set.</span></span>|  
  
## <a name="other-sampling-options"></a><span data-ttu-id="08547-155">기타 샘플링 옵션</span><span class="sxs-lookup"><span data-stu-id="08547-155">Other Sampling Options</span></span>  
 <span data-ttu-id="08547-156">이 마법사의 샘플링 옵션이 필요에 맞지 않지 않으면 SSIS(SQL Server Integration Services)의 샘플링 변환을 사용하여 여러 데이터 원본의 행을 샘플링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08547-156">If the sampling options in this wizard do not meet your needs, you can use the sampling transformation in SQL Server Integration Services (SSIS) to sample rows from multiple data sources.</span></span>  
  
 <span data-ttu-id="08547-157">자세한 내용은 [행 샘플링 변환](../integration-services/data-flow/transformations/row-sampling-transformation.md) 및 [백분율 샘플링 변환](../integration-services/data-flow/transformations/percentage-sampling-transformation.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08547-157">For more information, see [Row Sampling Transformation](../integration-services/data-flow/transformations/row-sampling-transformation.md) and [Percentage Sampling Transformation](../integration-services/data-flow/transformations/percentage-sampling-transformation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08547-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08547-158">See Also</span></span>  
 [<span data-ttu-id="08547-159">데이터 마이닝 준비 검사 목록</span><span class="sxs-lookup"><span data-stu-id="08547-159">Checklist of Preparation for Data Mining</span></span>](checklist-of-preparation-for-data-mining.md)  
  
  
