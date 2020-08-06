---
title: 새 OLAP 마이닝 구조 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], OLAP
- mining structures [Analysis Services], creating
- OLAP [Analysis Services], mining models
ms.assetid: 368f4273-a016-4748-bcb6-505a3e745af3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2851fe6180254b129471c442297c419fd594e123
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727467"
---
# <a name="create-a-new-olap-mining-structure"></a><span data-ttu-id="6ef7e-102">새 OLAP 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="6ef7e-102">Create a New OLAP Mining Structure</span></span>
  <span data-ttu-id="6ef7e-103">의 데이터 마이닝 마법사를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 다차원 모델의 데이터를 사용 하는 마이닝 구조를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-103">You can use the Data Mining Wizard in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create a mining structure that uses data from a multidimensional model.</span></span> <span data-ttu-id="6ef7e-104">OLAP 큐브를 기반으로 하는 마이닝 모델은 팩트 테이블의 열과 값, 차원 및 측정값 그룹을 분석 특성으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-104">Mining models that are based on OLAP cubes can use the column and values in fact tables, dimensions, and measure groups as attributes for analysis.</span></span>  
  
### <a name="to-create-a-new-olap-mining-structure"></a><span data-ttu-id="6ef7e-105">새 OLAP 마이닝 구조를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6ef7e-105">To create a new OLAP mining structure</span></span>  
  
1.  <span data-ttu-id="6ef7e-106">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 **프로젝트의** 마이닝 구조 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 폴더를 마우스 오른쪽 단추로 클릭하고 **새 마이닝 구조** 를 클릭하여 데이터 마이닝 마법사를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-106">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **Mining Structures** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then click **New Mining Structure** to open the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="6ef7e-107">**데이터 마이닝 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="6ef7e-108">**정의 방법 선택** 페이지에서 **기존 큐브 사용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-108">On the **Select the Definition Method** page, select **From existing cube**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="6ef7e-109">지원되는 데이터 마이닝 알고리즘 목록을 검색할 수 없습니다.라는 오류 메시지가 나타나면 **프로젝트 속성** 대화 상자를 열고 다차원 모델을 지원하는 Analysis Services 인스턴스 이름을 지정했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-109">If you get an error with the message, Unable to retrieve a list of supported data mining algorithms, open the **Project Properties** dialog box and verify that you have specified the name of an Analysis Services instance that supports multidimensional models.</span></span> <span data-ttu-id="6ef7e-110">테이블 형식 모델링을 지원하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에는 마이닝 모델을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-110">You cannot create mining models on an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that supports tabular modeling.</span></span>  
  
4.  <span data-ttu-id="6ef7e-111">**데이터 마이닝 구조 만들기** 페이지에서 마이닝 구조만 만들지 아니면 마이닝 구조와 관련 마이닝 모델 하나를 함께 만들지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-111">On the **Create the Data Mining Structure** page, decide whether you will create a mining structure only, or a mining structure plus one related mining model.</span></span> <span data-ttu-id="6ef7e-112">일반적으로 필요한 열을 포함할지 묻는 메시지가 나타나도록 동시에 마이닝 모델을 만드는 편이 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-112">Generally it is easier to create a mining model at the same time, so that you can be prompted to include necessary columns.</span></span>  
  
     <span data-ttu-id="6ef7e-113">마이닝 모델을 만들려면 사용할 데이터 마이닝 알고리즘을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-113">If you will create a mining model, select the data mining algorithm that you want to use, and then click **Next**.</span></span> <span data-ttu-id="6ef7e-114">알고리즘을 선택하는 방법에 대한 자세한 내용은 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-114">For more information about how to choose an algorithm, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
5.  <span data-ttu-id="6ef7e-115">**원본 큐브 차원 선택** 페이지의 **원본 큐브 차원 선택**에서 대부분의 사례 데이터가 포함된 차원을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-115">On the **Select the Source Cube Dimension** page, under **Select a Source Cube Dimension**, locate the dimension that contains the majority of your case data.</span></span>  
  
     <span data-ttu-id="6ef7e-116">예를 들어 고객 그룹화를 식별하려는 경우 Customer 차원을 선택할 수 있고, 트랜잭션 간 구매를 분석하려는 경우 Internet Sales Order Details 차원을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-116">For example, if you are trying to identify customer groupings, you might choose the Customer dimension; if you are trying to analyze purchases across transactions, you might choose the Internet Sales Order Details dimension.</span></span> <span data-ttu-id="6ef7e-117">이 차원의 데이터만 사용하도록 제한되지는 않지만 해당 차원은 분석에 사용할 중요 특성을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-117">You are not restricted to using only the data in this dimension, but it should contain important attributes to use in analysis.</span></span>  
  
     <span data-ttu-id="6ef7e-118">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="6ef7e-119">**사례 키 선택** 페이지의 **특성**에서 마이닝 구조의 키로 사용할 특성을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-119">On the **Select the Case Key** page, under **Attributes**, select the attribute that will be the key of the mining structure, and then click **Next**.</span></span>  
  
     <span data-ttu-id="6ef7e-120">일반적으로 마이닝 구조의 키로 사용하는 특성은 차원의 키이기도 하며 미리 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-120">Typically the attribute that you use as key for the mining structure is also a key for the dimension and will be pre-selected.</span></span>  
  
7.  <span data-ttu-id="6ef7e-121">**사례 수준 열 선택** 페이지의 **관련 특성 및 측정값**에서 마이닝 구조에 추가할 값이 들어 있는 특성과 측정값을 사례 데이터로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-121">On the **Select Case Level Columns** page, under **Related Attributes and Measures**, select the attributes and measures that contain values you want to add to the mining structure as case data.</span></span> <span data-ttu-id="6ef7e-122">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-122">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="6ef7e-123">**마이닝 모델 열 사용법 지정** 페이지의 **마이닝 모델 구조**에서 먼저 예측 가능한 열을 설정한 다음 입력으로 사용할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-123">On the **Specify Mining Model Column Usage** page, under **Mining model structure**, first set the predictable column, and then choose columns to use as inputs.</span></span>  
  
    -   <span data-ttu-id="6ef7e-124">마이닝 구조의 데이터를 포함할 맨 왼쪽 열의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-124">Select the checkbox in the leftmost column to include the data in the mining structure.</span></span> <span data-ttu-id="6ef7e-125">구조의 열 중에서 분석에 사용할 열이 아닌 참조에 사용할 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-125">You can include columns in the structure that you will use for reference, but not use them for analysis.</span></span>  
  
    -   <span data-ttu-id="6ef7e-126">**입력** 열의 확인란을 선택하여 특성을 분석의 변수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-126">Select the checkbox in the **Input** column to use the attribute as a variable in analysis.</span></span>  
  
    -   <span data-ttu-id="6ef7e-127">예측 가능한 특성에 대해서만 **예측** 열의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-127">Select the checkbox in the **Predict** column only for predictable attributes.</span></span>  
  
     <span data-ttu-id="6ef7e-128">키로 지정한 열은 입력이나 예측에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-128">Note that columns you have designated as keys cannot be used for input or prediction.</span></span>  
  
     <span data-ttu-id="6ef7e-129">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-129">Click **Next**.</span></span>  
  
9. <span data-ttu-id="6ef7e-130">**마이닝 모델 열 사용법 지정** 페이지에서는 **중첩 테이블 추가** 및 **중첩 테이블**을 사용하여 중첩 테이블을 마이닝 구조에 추가하거나 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-130">On the **Specify Mining Model Column Usage** page, you can also add and remove nested tables to the mining structure, using **Add Nested Tables** and **Nested Tables**.</span></span>  
  
     <span data-ttu-id="6ef7e-131">OLAP 마이닝 구조에서 중첩 테이블은 케이스 특성을 나타내는 차원을 가진 일 대 다 관계가 포함된 큐브 내의 또 다른 데이터 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-131">In an OLAP mining model, a nested table is another set of data within the cube that has a one-to-many relationship with the dimension that represents the case attributes.</span></span> <span data-ttu-id="6ef7e-132">따라서 대화 상자를 열면 케이스 테이블로 선택한 차원과 이미 관련되어 있는 측정값 그룹이 미리 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-132">Therefore, when the dialog box opens, it pre-selects measure groups that are already related to the dimension you selected as the case table.</span></span> <span data-ttu-id="6ef7e-133">이때 분석에 유용한 추가 정보가 포함되어 있는 다른 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-133">At this point, you would choose a different dimension that contains additional information useful for analysis.</span></span>  
  
     <span data-ttu-id="6ef7e-134">예를 들어 고객을 분석하는 경우 [Customer] 차원을 케이스 테이블로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-134">For example, if you are analyzing customers, you would use the [Customer] dimension as the case table.</span></span> <span data-ttu-id="6ef7e-135">중첩 테이블의 경우 고객이 구매할 때 제시한 이유를 추가할 수 있습니다. 이 이유는 [Sales Reason] 차원에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-135">For the nested table, you might add the reason customers cited when making a purchase, which is included in the [Sales Reason] dimension.</span></span>  
  
     <span data-ttu-id="6ef7e-136">중첩된 데이터를 추가하는 경우 다음과 같은 두 개의 추가 열을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-136">If you add nested data, you must specify two additional columns:</span></span>  
  
    -   <span data-ttu-id="6ef7e-137">중첩 테이블의 키: 이 열은 **중첩 테이블 키 선택**페이지에서 미리 선택되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-137">The key of the nested table: This should be pre-selected on the page, **Select Nested Table Key**.</span></span>  
  
    -   <span data-ttu-id="6ef7e-138">분석에 사용할 특성: **중첩 테이블 열 선택**페이지에서 중첩 테이블 선택 항목의 특성 및 측정값 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-138">The attributes or attributes to use for analysis: The page, **Select Nested Table Columns**, provides a list of measures and attributes in the nested table selection.</span></span>  
  
        -   <span data-ttu-id="6ef7e-139">모델에 포함하는 각 특성에 대해 왼쪽 열의 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-139">For each attribute that you include in the model, check the box in the left column.</span></span>  
  
        -   <span data-ttu-id="6ef7e-140">특성을 분석에만 사용하려는 경우 **입력**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-140">If you want to use the attribute for analysis only, check **Input**.</span></span>  
  
        -   <span data-ttu-id="6ef7e-141">열을 모델의 예측 가능한 특성 중 하나로만 포함하려는 경우 **예측**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-141">If you want to include the column as one of the predictable attributes for the model, select **Predict**.</span></span>  
  
        -   <span data-ttu-id="6ef7e-142">구조에 포함하되 입력 또는 예측 가능한 특성으로 지정하지 않는 항목은 모두 `Ignore` 플래그와 함께 구조에 추가됩니다. 이는 모델을 작성할 때 데이터가 처리되지만 해당 데이터는 분석에 사용되지 않으며 드릴스루용으로만 사용 가능함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-142">Any item that you include in the structure but do not specify as an input or predictable attribute is added to the structure with the flag `Ignore`; this means that the data is processed when you build the model but is not used in analysis, and is available only for drillthrough.</span></span> <span data-ttu-id="6ef7e-143">고객 이름과 같은 세부 정보를 포함 하 되 분석에 사용 하지 않으려는 경우이를 편리 하 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-143">This can be handy if you want to include details such as customer names but don't want to use them in analysis.</span></span>  
  
     <span data-ttu-id="6ef7e-144">**마침** 를 클릭하여 중첩 테이블을 사용하는 마법사 부분을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-144">Click **Finish** to close the part of the wizard that works with nested tables.</span></span> <span data-ttu-id="6ef7e-145">프로세스를 반복하여 여러 중첩 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-145">You can repeat the process to add multiple nested columns.</span></span>  
  
10. <span data-ttu-id="6ef7e-146">**열 내용 및 데이터 형식 지정** 페이지의 **마이닝 모델 구조**에서 각 열의 내용 유형과 데이터 형식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-146">On the **Specify Columns' Content and Data Type** page, under **Mining model structure**, set the content type and data type for each column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6ef7e-147"> OLAP 마이닝 모델에서는 **검색** 기능을 사용하여 열에 연속 데이터나 불연속 데이터가 있는지 자동으로 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-147">OLAP mining models do not support using the **Detect** feature to automatically detect whether a column contains continuous or discrete data.</span></span>  
  
     <span data-ttu-id="6ef7e-148">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-148">Click **Next**.</span></span>  
  
11. <span data-ttu-id="6ef7e-149">**원본 큐브 조각화** 페이지에서 마이닝 구조를 만드는 데 사용되는 데이터를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-149">On the **Slice Source Cube** page, you can filter the data that is used to create the mining structure.</span></span>  
  
     <span data-ttu-id="6ef7e-150">큐브를 조각화하면 모델을 작성하는 데 사용되는 데이터를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-150">Slicing the cube lets you restrict the data that is used to build the model.</span></span> <span data-ttu-id="6ef7e-151">예를 들어 Geography 계층을 조각화하여 각 지역에 대해 별도의 모델을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-151">For example, you could build separate models for each region by slicing on the Geography hierarchy and</span></span>  
  
    -   <span data-ttu-id="6ef7e-152">**차원**: 드롭다운 목록에서 관련된 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-152">**Dimension**: Choose a related dimension from the dropdown list.</span></span>  
  
    -   <span data-ttu-id="6ef7e-153">**계층**: 필터를 적용하려는 차원 계층의 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-153">**Hierarchy**:  Select the level of the dimension hierarchy at which you want to apply the filter.</span></span> <span data-ttu-id="6ef7e-154">예를 들어 [Geography] 차원을 기준으로 조각화하는 경우에는 [Region Country Name]과 같은 계층 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-154">For example, if you are slicing by the [Geography] dimension, you would choose a hierarchy level such as [Region Country Name] .</span></span>  
  
    -   <span data-ttu-id="6ef7e-155">**연산자**: 목록에서 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-155">**Operator**: Choose an operator from the list.</span></span>  
  
    -   <span data-ttu-id="6ef7e-156">**필터 식**: 필터 조건으로 사용할 값 또는 식을 입력하거나 드롭다운 목록을 사용하여 지정된 계층 수준의 멤버 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-156">**Filter Expression**: Type a value or expression to serve as the filter condition, or use the dropdown list to select a value from the list of members at the specified level of the hierarchy.</span></span>  
  
         <span data-ttu-id="6ef7e-157">예를 들어 [Geography]를 차원으로 선택 하 고 [Region Country Name]을 계층 수준으로 선택한 경우 드롭다운 목록에는 필터 조건으로 사용할 수 있는 모든 유효한 국가/지역이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-157">For example, if you selected [Geography] as the dimension and [Region Country Name] as the hierarchy level, the dropdown list contains all the valid countries/regions that you can use as a filter condition.</span></span> <span data-ttu-id="6ef7e-158">여러 항목을 선택 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-158">You can make multiple selections.</span></span> <span data-ttu-id="6ef7e-159">결과적으로 마이닝 구조의 데이터가 이러한 지리적인 영역의 큐브 데이터로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-159">As a result, the data in the mining structure will be limited to cube data from these geographical areas.</span></span>  
  
    -   <span data-ttu-id="6ef7e-160">**매개 변수**: 이 확인란을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-160">**Parameters**: Ignore this check box.</span></span> <span data-ttu-id="6ef7e-161">이 대화 상자에서는 여러 큐브 필터링 시나리오를 지원하며 이 옵션은 마이닝 구조 작성과 관련되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-161">This dialog box supports multiple cube filtering scenarios and this option is not relevant to building a mining structure.</span></span>  
  
     <span data-ttu-id="6ef7e-162">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-162">Click **Next**.</span></span>  
  
12. <span data-ttu-id="6ef7e-163">**학습 및 테스트 집합으로 데이터 분할** 페이지에서 테스트용으로 예약할 마이닝 구조 데이터의 비율을 지정하거나 테스트 사례의 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-163">On the **Split data into training and testing sets** page, specify a percentage of the mining structure data to reserve for testing, or specify the maximum number of test cases.</span></span> <span data-ttu-id="6ef7e-164">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-164">Click **Next**.</span></span>  
  
     <span data-ttu-id="6ef7e-165">두 값을 모두 지정하면 더 낮은 쪽을 사용하도록 두 제한이 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-165">If you specify both values, the limits are combined to use whichever is lowest.</span></span>  
  
13. <span data-ttu-id="6ef7e-166">**마법사 완료** 페이지에서 새 OLAP 마이닝 구조의 이름과 초기 마이닝 모델을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-166">On the **Completing the Wizard** page, provide a name for the new OLAP mining structure and the initial mining model.</span></span>  
  
14. <span data-ttu-id="6ef7e-167">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-167">Click **Finish**.</span></span>  
  
15. <span data-ttu-id="6ef7e-168">**마법사 완료** 페이지에는 마이닝 모델 차원을 사용하여 마이닝 모델 차원이나 큐브를 만들 수 있는 옵션도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-168">On the **Completing the Wizard** page, you also have the option to create a mining model dimension and/or a cube using the mining model dimension.</span></span> <span data-ttu-id="6ef7e-169">이러한 옵션은 다음 알고리즘을 사용하여 작성된 모델에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-169">These options are supported only for models built using the following algorithms:</span></span>  
  
    -   <span data-ttu-id="6ef7e-170">Microsoft 클러스터링 알고리즘</span><span class="sxs-lookup"><span data-stu-id="6ef7e-170">Microsoft Clustering algorithm</span></span>  
  
    -   <span data-ttu-id="6ef7e-171">Microsoft 의사 결정 트리 알고리즘</span><span class="sxs-lookup"><span data-stu-id="6ef7e-171">Microsoft Decision Trees algorithm</span></span>  
  
    -   <span data-ttu-id="6ef7e-172">Microsoft 연결 규칙 알고리즘</span><span class="sxs-lookup"><span data-stu-id="6ef7e-172">Microsoft Association Rules algorithm</span></span>  
  
     <span data-ttu-id="6ef7e-173">**마이닝 모델 차원 만들기**: 이 확인란을 선택하고 마이닝 모델 차원의 형식 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-173">**Create mining model dimension**: Select this check box and provide a type name for the mining model dimension.</span></span> <span data-ttu-id="6ef7e-174">이 옵션을 사용하면 마이닝 구조를 작성하는 데 사용된 원본 큐브 내에 새 차원이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-174">When you use this option, a new dimension is created within the original cube that was used to build the mining structure.</span></span> <span data-ttu-id="6ef7e-175">이 차원을 사용하여 드릴다운 및 추가 분석을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-175">You can use this dimension to drill down and conduct further analysis.</span></span> <span data-ttu-id="6ef7e-176">차원은 큐브 내에 있으므로 사례 데이터 차원에 자동으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-176">Because the dimension is located within the cube, the dimension is automatically mapped to the case data dimension.</span></span>  
  
     <span data-ttu-id="6ef7e-177">**마이닝 모델 차원을 사용하여 큐브 만들기**: 이 확인란을 선택하고 새 큐브의 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-177">**Create cube using mining model dimension**: Select this check box, and provide a name for the new cube.</span></span> <span data-ttu-id="6ef7e-178">이 옵션을 사용하면 구조를 작성하는 데 사용된 기존 차원과 모델의 결과가 포함된 새 데이터 마이닝 차원이 모두 포함된 새 큐브가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6ef7e-178">When you use this option, a new cube is created that contains both the existing dimensions that were used in building the structure, and the new data mining dimension that contains the results from the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef7e-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ef7e-179">See Also</span></span>  
 [<span data-ttu-id="6ef7e-180">마이닝 구조 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="6ef7e-180">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
