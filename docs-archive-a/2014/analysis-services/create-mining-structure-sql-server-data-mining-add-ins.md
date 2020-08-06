---
title: 마이닝 구조 만들기 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: b8b1eedc-4d6d-4429-a578-e629ec573934
author: minewiskan
ms.author: owend
ms.openlocfilehash: c75712a893c6271da291693f46771aa71263280e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649282"
---
# <a name="create-mining-structure-sql-server-data-mining-add-ins"></a><span data-ttu-id="553fb-102">마이닝 구조 만들기(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="553fb-102">Create Mining Structure (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="553fb-103">![데이터 마이닝 리본, 마이닝 구조 만들기 단추](media/dmc-createstruct.gif "데이터 마이닝 리본, 마이닝 구조 만들기 단추")</span><span class="sxs-lookup"><span data-stu-id="553fb-103">![Create Mining Structure button, Data Mining ribbon](media/dmc-createstruct.gif "Create Mining Structure button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="553fb-104">모델을 만들 필요 없이 분석에 사용 되는 데이터 집합을 만들려면 **데이터 모델링** 그룹의 **고급** 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-104">Use the **Advanced** option in the **Data Modeling** group when you want to create a data set used for analysis without necessarily creating a model.</span></span> <span data-ttu-id="553fb-105">이 옵션은 여러 가지 알고리즘을 시험해 보려는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-105">This is useful when you want to experiment with different algorithms.</span></span>  
  
 <span data-ttu-id="553fb-106">마이닝 구조를 만든 후 [구조에 모델 추가](add-model-to-structure-data-mining-add-ins-for-excel.md) 마법사를 사용 하 여 해당 구조를 기반으로 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-106">After you have created the mining structure, use the [Add Model to Structure](add-model-to-structure-data-mining-add-ins-for-excel.md) wizard to create a model based on that structure.</span></span> <span data-ttu-id="553fb-107">**데이터 마이닝 고급 쿼리 편집기**를 사용 하 여 새 모델을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-107">You can also create new models by using the **Data Mining Advanced Query Editor**.</span></span>  
  
 <span data-ttu-id="553fb-108">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 지원되지만 마법사를 통해 사용할 수 없는 선형 회귀, 시퀀스 클러스터링 등의 고급 알고리즘 중 하나를 사용하거나 사용자 지정 알고리즘을 사용하여 모델을 작성하려는 경우에도 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-108">You can also use this option when you intend to build models using one of the advanced algorithms, which are supported by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] but not available through a wizard, such as linear regression or sequence clustering, or if you are using a custom algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="553fb-109">마이닝 구조를 만들 때 모든 모델의 유효성을 검사하는 데 사용할 수 있는 임의로 선택된 테스트 데이터 집합을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-109">When you create the mining structure, you can also establish a randomly selected testing data set that you can use to validate all your models.</span></span> <span data-ttu-id="553fb-110">이렇게 하면 모델 정확도를 일반 데이터 집합과 손쉽게 비교할 수 있기 때문에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-110">This is handy because you can easily compare model accuracy against a common data set.</span></span> <span data-ttu-id="553fb-111">**학습 및 테스트 집합으로 데이터 분할** 옵션을 선택 하 고 테스트용으로 예약할 적절 한 비율의 데이터 (일반적으로 약 30%)를 지정 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-111">Just select the option, **Split data into training and testing sets** and specify an appropriate percentage of data to reserve for testing, usually around 30 percent.</span></span>  
  
## <a name="use-the-wizard-to-create-a-mining-structure"></a><span data-ttu-id="553fb-112">마법사를 사용하여 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="553fb-112">Use the wizard to create a mining structure</span></span>  
  
1.  <span data-ttu-id="553fb-113">**데이터 마이닝** 리본에서 **고급**을 클릭 하 고 **구조 만들기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-113">In the **Data Mining** ribbon, click **Advanced**, and select **Create Structure**.</span></span>  
  
2.  <span data-ttu-id="553fb-114">**원본 데이터 선택** 대화 상자에서 분석에 사용할 데이터를 포함 하는 excel 범위, excel 데이터 테이블 또는 외부 데이터 원본을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-114">In the **Select source data** dialog box, specify the Excel range, Excel data table, or external data source that contains the data you want to use for analysis.</span></span>  
  
     <span data-ttu-id="553fb-115">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-115">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="553fb-116">**열 선택** 대화 상자에서 선택한 데이터 원본에서 사용할 수 있는 열 목록을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-116">In the **Select Columns** dialog box, review the list of columns available in the selected data source.</span></span>  
  
4.  <span data-ttu-id="553fb-117">열 이름 오른쪽에 있는 화살표를 클릭 하 여 열 **사용** 을 변경 하 고 다음 값 중에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-117">Click the arrow to the right of the column name to change the **usage** of the column, choosing from these values:</span></span>  
  
    -   <span data-ttu-id="553fb-118">**Key**.</span><span class="sxs-lookup"><span data-stu-id="553fb-118">**Key**.</span></span> <span data-ttu-id="553fb-119">각 모델에는 적어도 하나의 키가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-119">At least one key is required for each model.</span></span>  
  
    -   <span data-ttu-id="553fb-120">**키 시간**입니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-120">**Key time**.</span></span> <span data-ttu-id="553fb-121">이 옵션은 예측 모델에만 사용할 수 있으며 예측 모델에서 이 옵션은 필수 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-121">This option is available only for forecasting models, where it is required.</span></span>  
  
    -   <span data-ttu-id="553fb-122">**포함**.</span><span class="sxs-lookup"><span data-stu-id="553fb-122">**Include**.</span></span> <span data-ttu-id="553fb-123">열이 마이닝 구조에서 사용 가능해야 하지만 키 열이 아님을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-123">Indicates that the column should be made available in the mining structure but is not a key column.</span></span>  
  
    -   <span data-ttu-id="553fb-124">**사용 하지 마십시오**.</span><span class="sxs-lookup"><span data-stu-id="553fb-124">**Do not use**.</span></span> <span data-ttu-id="553fb-125">열이 마이닝 구조에 포함되지 않도록 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-125">Indicates that the column should not be included in the mining structure.</span></span>  
  
     <span data-ttu-id="553fb-126">모델을 작성할 때 항상 열을 무시할 수 있지만 이후에 열을 추가하려면 구조와 모델을 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-126">Remember that you can always ignore columns when you build the model, but to add columns later requires that you reprocess the structure and model.</span></span>  
  
5.  <span data-ttu-id="553fb-127">찾아보기 **(...)** 단추를 클릭 하 여 내용 유형, 데이터 형식 및 모델링 플래그를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-127">Click the browse **(...)** button to set the content type, data type, and modeling flags.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="553fb-128">열에 숫자 데이터가 포함된 경우 항상 이 대화 상자를 열어 올바른 데이터 형식이 선택되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-128">If the column contains numeric data, you should always open this dialog box to ensure that the correct data type is chosen.</span></span> <span data-ttu-id="553fb-129">입력 데이터가 숫자이더라도 연속 숫자 대신 범주 변수나 불연속 값으로 처리하려는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-129">In some cases, even if the input data is a number, you will want to treat it as a categorical variable, or discrete value, instead of a continuous number.</span></span>  
    >   
    >  <span data-ttu-id="553fb-130">예를 들어 우편 번호 열은 기본적으로 연속된 Long 데이터 형식으로 나열될 수 있지만 더 좋은 결과를 얻기 위해 이 열을 불연속 텍스트 값으로 처리하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-130">For example, a postal code column might be listed by default as a continuous long data type, but to get better results, you can specify that it be handled as a discrete text value.</span></span>  
    >   
    >  <span data-ttu-id="553fb-131">자세한 내용은 [데이터 마이닝을 위한 데이터 선택](choosing-data-for-data-mining.md)에서 콘텐츠 형식에 대 한 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="553fb-131">For more information, see the section on content types in [Choosing Data for Data Mining](choosing-data-for-data-mining.md).</span></span>  
  
     <span data-ttu-id="553fb-132">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-132">Click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="553fb-133">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-133">Click **Next**.</span></span>  
  
     <span data-ttu-id="553fb-134">사용 중인 데이터의 형식에 따라 이 단계를 수행한 후 마법사를 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-134">Depending on what type of data you are using, you might complete the wizard after this step.</span></span> <span data-ttu-id="553fb-135">이 경우 **마침** 페이지로 이동 하 여 마이닝 구조의 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-135">In that case, jump ahead to the **Finish** page to name your mining structure.</span></span>  
  
     <span data-ttu-id="553fb-136">다른 모델의 경우 테스트 데이터 집합을 만드는 추가 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-136">For other models, you have the additional option to create a testing data set.</span></span>  
  
7.  <span data-ttu-id="553fb-137">**학습 및 테스트 데이터 집합으로 데이터 분할** 대화 상자에서 데이터를 분할 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-137">In the **Split data into training and testing data sets** dialog box, specify how you want your data partitioned.</span></span> <span data-ttu-id="553fb-138">기본적으로 30%의 데이터가 테스트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-138">By default, 30 percent of data is used for testing.</span></span>  
  
     <span data-ttu-id="553fb-139">필요한 경우 테스트에 사용할 최대 행 수를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-139">Optionally, type the maximum number of rows to use for testing.</span></span>  
  
     <span data-ttu-id="553fb-140">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-140">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="553fb-141">**마침** 대화 상자에서 새 마이닝 구조의 이름 및 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-141">In the **Finish** dialog, type a name and description for the new mining structure.</span></span>  
  
9. <span data-ttu-id="553fb-142">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-142">Click **Finish**.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="553fb-143">관련 옵션</span><span class="sxs-lookup"><span data-stu-id="553fb-143">Related Options</span></span>  
  
|<span data-ttu-id="553fb-144">옵션</span><span class="sxs-lookup"><span data-stu-id="553fb-144">Option</span></span>|<span data-ttu-id="553fb-145">주석</span><span class="sxs-lookup"><span data-stu-id="553fb-145">Comments</span></span>|  
|------------|--------------|  
|<span data-ttu-id="553fb-146">**원본 데이터 선택** 대화 상자</span><span class="sxs-lookup"><span data-stu-id="553fb-146">**Select Source Data** dialog box</span></span>|<span data-ttu-id="553fb-147">Excel 테이블을 선택할 때 데이터에 이미 머리글이 있는지 여부를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-147">When you select an Excel table, you should indicate whether the data already has headers.</span></span> <span data-ttu-id="553fb-148">이 작업을 생략하는 경우 데이터의 첫 번째 행이 열 이름으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-148">If you skip this, the first row of data will be used as the column name.</span></span><br /><br /> <span data-ttu-id="553fb-149">**외부 데이터 원본**옵션을 사용 하는 경우 데이터 원본에 정의할 수 있는 모든 종류의 데이터를 사용할 수 있습니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="553fb-149">If you use the option, **External data source**, you can use any kind of data that can be defined in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="553fb-150">그러나 새로운 데이터 원본을 만들기 위한 추가 기능에 있는 대화 상자에는 Analysis Services에서 지원하는 데이터 원본의 전체 범위가 포함되어 있지 않으므로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에서 미리 데이터 원본을 만든 다음 추가 기능을 사용하여 연결하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-150">However, the dialog box in the add-in for creating new data sources does not include the full range of data sources supported by Analysis Services, so we recommend that you create the data sources on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server in advance and then connect using the add-ins.</span></span>|  
|<span data-ttu-id="553fb-151">**데이터 원본 쿼리 편집기** 대화 상자</span><span class="sxs-lookup"><span data-stu-id="553fb-151">**Data Source Query Editor** dialog box</span></span>|<span data-ttu-id="553fb-152">지정된 데이터 원본에 연결한 후 열을 추가하거나 사용자 지정 열을 생성하기 위해 사용자 지정 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-152">After you have connected to the specified data source, you can add columns, or create a custom query to generate custom columns.</span></span>|  
|<span data-ttu-id="553fb-153">**데이터를 학습 및 테스트 집합으로 분할합니다.**</span><span class="sxs-lookup"><span data-stu-id="553fb-153">**Split data into training and testing data sets**</span></span>|<span data-ttu-id="553fb-154">학습 및 테스트 집합에 권장 되는 값은 교육의 경우 70%이 고 테스트의 경우 30%입니다. 그러나 데이터가 많은 경우에는 테스트를 위해 최대 행 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-154">A recommended value for training vs. testing sets is 70 percent for training and 30 percent for testing; however, if you have a lot of data, you can specify a maximum number of rows for testing.</span></span>|  
|<span data-ttu-id="553fb-155">마침 대화 상자</span><span class="sxs-lookup"><span data-stu-id="553fb-155">Finish dialog box</span></span>|<span data-ttu-id="553fb-156">드릴스루 옵션은 일부 모델 유형에서 사용할 수 있으며 마이닝 구조에 세부 정보 열을 포함한 경우 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-156">The options for drillthrough are available on some model types and are very useful if you included detail columns in your mining structure.</span></span> <span data-ttu-id="553fb-157">예를 들어 클러스터링 모델을 만드는 경우 특정 클러스터에서 보다 쉽게 고객에게 연락하기 위해 분석이 아니라 드릴스루를 위한 이름 또는 전자 메일 주소 등의 세부 정보를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-157">For example, if you create a clustering model, you can include details such as name or email address for drillthrough but not analysis, to make it easier to contact customers in a particular cluster.</span></span>|  
  
###  <a name="setting-column-usage-in-the-create-mining-structure-wizard"></a><a name="Bkmk_strctcolumn"></a><span data-ttu-id="553fb-158">마이닝 구조 만들기 마법사에서 열 사용법 설정</span><span class="sxs-lookup"><span data-stu-id="553fb-158">Setting Column Usage in the Create Mining Structure Wizard</span></span>  
 <span data-ttu-id="553fb-159">마이닝 구조를 새로 만들 때 마이닝 구조에 포함할 데이터 원본 열과 해당 열의 사용법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-159">When you create a new mining structure, you can specify which columns in the data source should be included in the mining structure, and how those columns should be used.</span></span> <span data-ttu-id="553fb-160">마이닝 구조는 여러 마이닝 모델을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-160">Remember that a mining structure can support multiple mining models.</span></span>  
  
|<span data-ttu-id="553fb-161">값</span><span class="sxs-lookup"><span data-stu-id="553fb-161">Values</span></span>|<span data-ttu-id="553fb-162">Description</span><span class="sxs-lookup"><span data-stu-id="553fb-162">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="553fb-163">**포함**</span><span class="sxs-lookup"><span data-stu-id="553fb-163">**Include**</span></span>|<span data-ttu-id="553fb-164">분석이나 예측에 사용할 수 있는 데이터가 열에 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-164">Specifies that the column contains data that can be used for analysis or prediction.</span></span>|  
|<span data-ttu-id="553fb-165">**Key**</span><span class="sxs-lookup"><span data-stu-id="553fb-165">**Key**</span></span>|<span data-ttu-id="553fb-166">열에 처리에 필요한 트랜잭션 ID, 계열 ID 또는 다른 키를 포함되어 있음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-166">Specifies that the column contains a transaction ID, a series ID, or another key required for processing.</span></span><br /><br /> <span data-ttu-id="553fb-167">모든 알고리즘에는 Key 열이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-167">All algorithms require a Key column.</span></span> <span data-ttu-id="553fb-168">그러나 단일 키만 허용하는 알고리즘이 있고 여러 키를 허용하는 알고리즘도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-168">However, some algorithms permit only a single key, while others permit multiple keys.</span></span><br /><br /> <span data-ttu-id="553fb-169">열에 키가 포함 되어 있지만 처리 하는 데 필요 하지 않은 경우 **사용 안 함**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-169">If the column contains a key but is not required for processing, select **Do Not Use**.</span></span>|  
|<span data-ttu-id="553fb-170">**Key Time**</span><span class="sxs-lookup"><span data-stu-id="553fb-170">**Key Time**</span></span>|<span data-ttu-id="553fb-171">시계열의 항목을 고유하게 식별하는 데 사용할 수 있는 날짜나 기타 숫자 값이 열에 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-171">Specifies that the column contains a date or other numeric value that can be used to uniquely identify items in a time series.</span></span>|  
|<span data-ttu-id="553fb-172">**사용 안 함**</span><span class="sxs-lookup"><span data-stu-id="553fb-172">**Do Not Use**</span></span>|<span data-ttu-id="553fb-173">열을 무시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-173">Specifies that the column should be ignored.</span></span> <span data-ttu-id="553fb-174">해당 열의 열 데이터는 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-174">The data in the column will not be processed.</span></span>|  
  
 <span data-ttu-id="553fb-175">모델을 올바르게 처리하려면 각 행을 고유하게 식별하는 키 열, 예측 가능한 모델을 만드는 경우 예측을 만들 대상 열, 그리고 대상 열을 예측하는 관계를 만들기 위해 입력 열로 사용할 열을 알고리즘에서 파악해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-175">To process a model correctly, the algorithm must know which column is the key column that uniquely identifies each row, which column is the target column for creating predictions if you are creating a predictable model, and which columns to use as input columns to create the relationships that predict the target column.</span></span>  
  
-   <span data-ttu-id="553fb-176">**사용 안 함** 으로 지정 된 열은 마이닝 구조에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-176">Columns that are specified as **Do not use** will not be present in the mining structure.</span></span>  
  
     <span data-ttu-id="553fb-177">불필요한 열이나 잘못된 값이 포함된 열을 추가할 경우 분석 결과에 부정적인 영향을 줄 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="553fb-177">If you add columns that are unnecessary or have bad values, it can adversely affect the results of analysis.</span></span> <span data-ttu-id="553fb-178">반드시 관련 열만 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-178">Therefore, be sure to include only those columns that are relevant.</span></span> <span data-ttu-id="553fb-179">그러나 마이닝 구조에 사용되지 않는 열은 쿼리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-179">However, remember that the columns that you do not use in the mining structure will not be available for querying.</span></span>  
  
-   <span data-ttu-id="553fb-180">**포함** 유형으로 지정 된 열은 마이닝 구조에 포함 되며 나중에 마이닝 모델의 분석 또는 예측에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-180">Columns that are specified as the **Include** type will be included in the mining structure and later can be used for either analysis or prediction in the mining models.</span></span>  
  
     <span data-ttu-id="553fb-181">사용해야 할지 여부를 확실히 알 수 없는 열은 항상 마이닝 구조에 포함한 다음 해당 열을 사용하지 않는 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-181">If you are not sure whether you will need to use the column, you can always include the column in the mining structure and then create a mining model that does not use that column.</span></span> <span data-ttu-id="553fb-182">예를 들어 나중에 참조할 수 있도록 데이터에 전화 번호 열을 포함하되 전화 번호를 무시하는 클러스터링 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-182">For example, you might include a phone number column in your data for later reference, but create a clustering model that ignores phone numbers.</span></span> <span data-ttu-id="553fb-183">클러스터를 만든 후에는 특정 클러스터에 속하는 사람의 전화 번호를 반환하는 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-183">After the clusters have been created, you can create a query that returns the phone numbers of people who belong to a particular cluster.</span></span>  
  
-   <span data-ttu-id="553fb-184">모든 알고리즘에는 **키** 열이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-184">All algorithms require a **Key** column.</span></span> <span data-ttu-id="553fb-185">Key 열의 값은 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-185">The values in the Key column must be unique.</span></span> <span data-ttu-id="553fb-186">**Key time** 열은 예측 또는 시계열 모델에만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-186">A **Key Time** column is required only for forecasting or time series models.</span></span> <span data-ttu-id="553fb-187">.</span><span class="sxs-lookup"><span data-stu-id="553fb-187">.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="553fb-188">요구 사항</span><span class="sxs-lookup"><span data-stu-id="553fb-188">Requirements</span></span>  
 <span data-ttu-id="553fb-189">데이터 마이닝 구조를 만들려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-189">To create a data mining structure, you must have a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="553fb-190">임시 구조를 사용하는 경우에도 연결이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="553fb-190">A connection is required even if you are working with temporary structures.</span></span> <span data-ttu-id="553fb-191">연결을 만들거나 변경 하는 방법에 대 한 자세한 내용은 [Excel 용 데이터 마이닝 클라이언트&#41;&#40;원본 데이터에 연결 ](connect-to-source-data-data-mining-client-for-excel.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="553fb-191">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="553fb-192">참고 항목</span><span class="sxs-lookup"><span data-stu-id="553fb-192">See Also</span></span>  
 [<span data-ttu-id="553fb-193">데이터 마이닝 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="553fb-193">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
