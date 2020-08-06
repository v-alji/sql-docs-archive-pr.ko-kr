---
title: '2 단원: 시장 바구니 마이닝 구조에 마이닝 모델 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d96a7a7d-35d7-4b34-abb5-f0822c256253
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b9573d9359983e33cf23533787c26039572710ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733375"
---
# <a name="lesson-2-adding-mining-models-to-the-market-basket-mining-structure"></a><span data-ttu-id="7ecf6-102">2단원: Market Basket 마이닝 구조에 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="7ecf6-102">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>
  <span data-ttu-id="7ecf6-103">이 단원에서는 [1 단원: 시장 바구니 마이닝 구조 만들기](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)에서 만든 시장 바구니 마이닝 구조에 두 개의 마이닝 모델을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-103">In this lesson, you will add two mining models to the Market Basket mining structure that you created in [Lesson 1: Creating the Market Basket Mining Structure](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="7ecf6-104">이러한 마이닝 모델을 사용하여 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-104">These mining models will allow you to create predictions.</span></span>  
  
 <span data-ttu-id="7ecf6-105">고객이 동시에 구입하는 경향이 있는 제품 유형을 예측하기 위해 [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) 및 *MINIMUM_PROBABILTY* 매개 변수에 대한 서로 다른 두 값을 사용하여 두 개의 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-105">To predict the types of products that customers tend to purchase at the same time, you will create two mining models using the [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) and two different values for the *MINIMUM_PROBABILTY* parameter.</span></span>  
  
 <span data-ttu-id="7ecf6-106">*MINIMUM_PROBABILTY* 는 규칙에 있어야 할 최소 확률을 지정하여 마이닝 모델이 포함할 규칙 수를 결정하는 데 도움이 되는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 연결 알고리즘 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-106">*MINIMUM_PROBABILTY* is a [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm parameter that helps to determine the number of rules that a mining model will contain by specifying the minimum probability that a rule must have.</span></span> <span data-ttu-id="7ecf6-107">예를 들어 이 값을 0.4로 설정하면 규칙에서 설명하는 제품 조합의 발생 확률이 40% 이상인 경우에만 규칙을 생성할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-107">For example, setting this value to 0.4 specifies that a rule can be generated only if the combination of products that the rule describes has at least a forty percent probability of occurring.</span></span>  
  
 <span data-ttu-id="7ecf6-108">*MINIMUM_PROBABILTY* 매개 변수 변경의 결과는 이후 단원에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-108">You will view the effect of changing the *MINIMUM_PROBABILTY* parameter in a later lesson.</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="7ecf6-109">ALTER MINING STRUCTURE 문</span><span class="sxs-lookup"><span data-stu-id="7ecf6-109">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="7ecf6-110">마이닝 구조에 중첩 테이블을 포함 하는 마이닝 모델을 추가 하려면 [ALTER 마이닝 structure &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-110">To add a mining model that contains a nested table to a mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="7ecf6-111">이 문의 코드는 다음 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-111">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="7ecf6-112">마이닝 구조 식별</span><span class="sxs-lookup"><span data-stu-id="7ecf6-112">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="7ecf6-113">마이닝 모델 이름 지정</span><span class="sxs-lookup"><span data-stu-id="7ecf6-113">Naming the mining model</span></span>  
  
-   <span data-ttu-id="7ecf6-114">키 열 정의</span><span class="sxs-lookup"><span data-stu-id="7ecf6-114">Defining the key column</span></span>  
  
-   <span data-ttu-id="7ecf6-115">입력 및 예측 가능한 열 정의</span><span class="sxs-lookup"><span data-stu-id="7ecf6-115">Defining the input and predictable columns</span></span>  
  
-   <span data-ttu-id="7ecf6-116">중첩 테이블 열 정의</span><span class="sxs-lookup"><span data-stu-id="7ecf6-116">Defining the nested table columns</span></span>  
  
-   <span data-ttu-id="7ecf6-117">알고리즘 및 매개 변수 변경 내용 식별</span><span class="sxs-lookup"><span data-stu-id="7ecf6-117">Identifying the algorithm and parameter changes</span></span>  
  
 <span data-ttu-id="7ecf6-118">다음은 구조에 중첩 테이블 열을 포함하는 마이닝 모델을 추가하는 `ALTER MINING STRUCTURE` 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-118">The following is a generic example of the `ALTER MINING STRUCTURE` statement that adds a mining model to a structure that includes nested table columns:</span></span>  
  
```  
ALTER MINING STRUCTURE [<Mining Structure Name>]  
ADD MINING MODEL [<Mining Model Name>]  
(  
    [<key column>],  
    <mining model column> <usage>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
) USING <algorithm>( <algorithm parameters> )  
```  
  
 <span data-ttu-id="7ecf6-119">코드의 첫 번째 줄에서는 마이닝 모델을 추가할 기존 마이닝 구조를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-119">The first line of the code identifies the existing mining structure to which the mining model will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="7ecf6-120">코드의 다음 줄에서는 마이닝 구조에 추가할 마이닝 모델의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-120">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="7ecf6-121">DMX (데이터 마이닝 확장)에서 개체의 이름을 지정 하는 방법에 대 한 자세한 내용은 [id &#40;dmx&#41;](/sql/dmx/identifiers-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-121">For information about naming an object in Data Mining Extensions (DMX), see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="7ecf6-122">코드의 다음 줄에서는 마이닝 모델에서 사용할 마이닝 구조의 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-122">The next lines of the code define the columns in the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key column>],  
<mining model columns> <usage>,  
```  
  
 <span data-ttu-id="7ecf6-123">마이닝 구조에 이미 있는 열만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-123">You can only use columns that already exist in the mining structure.</span></span>  
  
 <span data-ttu-id="7ecf6-124">마이닝 모델 열 목록의 첫 번째 열은 마이닝 구조의 키 열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-124">The first column in the list of mining model columns must be the key column in the mining structure.</span></span> <span data-ttu-id="7ecf6-125">그러나 `KEY` 사용을 지정 하기 위해 키 열 뒤에를 입력할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-125">However, you do not have to type `KEY` after the key column to specify usage.</span></span> <span data-ttu-id="7ecf6-126">이는 마이닝 구조를 만들 때 해당 열을 키로 이미 정의했기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-126">That is because you have already defined the column as a key when you created the mining structure.</span></span>  
  
 <span data-ttu-id="7ecf6-127">나머지 줄에서는 새 마이닝 모델에서의 열 사용법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-127">The remaining lines specify the usage of the columns in the new mining model.</span></span> <span data-ttu-id="7ecf6-128">다음 구문을 사용하여 마이닝 모델의 열이 예측에 사용되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-128">You can specify that a column in the mining model will be used for prediction by using the following syntax:</span></span>  
  
```  
<column name> PREDICT,  
```  
  
 <span data-ttu-id="7ecf6-129">사용법을 지정하지 않는 경우 목록에 데이터 마이닝 구조 열을 포함할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-129">If you do not specify usage, you do not have to include a data mining structure column in the list.</span></span> <span data-ttu-id="7ecf6-130">참조된 데이터 마이닝 구조에 사용되는 모든 열은 해당 구조를 기반으로 하는 마이닝 모델에서 자동으로 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-130">All columns that are used by the referenced data mining structure are automatically available for use by the mining models that are based on that structure.</span></span> <span data-ttu-id="7ecf6-131">그러나 사용자가 사용법을 지정하지 않는 한 모델에서는 학습에 해당 열을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-131">However, the model will not use the columns for training unless you specify the usage.</span></span>  
  
 <span data-ttu-id="7ecf6-132">코드의 마지막 줄에서는 마이닝 모델 생성에 사용할 알고리즘 및 알고리즘 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-132">The last line in the code defines the algorithm and algorithm parameters that will be used to generate the mining model.</span></span>  
  
```  
) USING <algorithm>( <algorithm parameters> )  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="7ecf6-133">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="7ecf6-133">Lesson Tasks</span></span>  
 <span data-ttu-id="7ecf6-134">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-134">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="7ecf6-135">기본 확률을 사용하여 구조에 연결 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="7ecf6-135">Add an association mining model to the structure using the default probability</span></span>  
  
-   <span data-ttu-id="7ecf6-136">수정된 확률을 사용하여 구조에 연결 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="7ecf6-136">Add an association mining model to the structure using a modified probability</span></span>  
  
## <a name="adding-an-association-mining-model-to-the-structure-using-the-default-minimum_probability"></a><span data-ttu-id="7ecf6-137">MINIMUM_PROBABILITY의 기본값을 사용하여 구조에 연결 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="7ecf6-137">Adding an Association Mining Model to the Structure Using the Default MINIMUM_PROBABILITY</span></span>  
 <span data-ttu-id="7ecf6-138">첫 번째 태스크는 [!INCLUDE[msCoName](../includes/msconame-md.md)] *MINIMUM_PROBABILITY*의 기본값을 사용 하 여 연결 알고리즘을 기반으로 시장 바구니 마이닝 구조에 새 마이닝 모델을 추가 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-138">The first task is to add a new mining model to the Market Basket mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm using the default value for *MINIMUM_PROBABILITY*.</span></span>  
  
#### <a name="to-add-an-association-mining-model"></a><span data-ttu-id="7ecf6-139">연결 마이닝 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="7ecf6-139">To add an Association mining model</span></span>  
  
1.  <span data-ttu-id="7ecf6-140">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-140">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="7ecf6-141">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-141">Query Editor opens and contains a new, blank query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7ecf6-142">특정 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 대해 DMX 쿼리를 만들려면 인스턴스 대신 데이터베이스를 마우스 오른쪽 단추로 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-142">To create a DMX query against a specific [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, right-click the database instead of the instance.</span></span>  
  
2.  <span data-ttu-id="7ecf6-143">`ALTER MINING STRUCTURE` 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-143">Copy the generic example of the `ALTER MINING STRUCTURE` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="7ecf6-144">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="7ecf6-144">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="7ecf6-145">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-145">with:</span></span>  
  
    ```  
    [Market Basket]  
    ```  
  
4.  <span data-ttu-id="7ecf6-146">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="7ecf6-146">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="7ecf6-147">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-147">with:</span></span>  
  
    ```  
    [Default Association]  
    ```  
  
5.  <span data-ttu-id="7ecf6-148">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="7ecf6-148">Replace the following:</span></span>  
  
    ```  
    [<key column>],  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     <span data-ttu-id="7ecf6-149">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-149">with:</span></span>  
  
    ```  
    OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     <span data-ttu-id="7ecf6-150">이 경우 `[Products]` 테이블을 예측 가능한 열로 지정했습니다.`.` 또한 `[Model]` 열은 중첩 테이블의 키 열이므로 중첩 테이블 열 목록에 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-150">In this case, the `[Products]` table has been designated as the predictable column`.` Also, the `[Model]` column is included in the list of nested table columns because it is the key column of the nested table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7ecf6-151">중첩 키는 사례 키와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-151">Remember that a nested key is different from a case key.</span></span> <span data-ttu-id="7ecf6-152">사례 키는 사례의 고유 식별자인 반면 중첩 키는 모델링할 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-152">A case key is a unique identifier of the case, whereas the nested key is an attribute that you want to model.</span></span>  
  
6.  <span data-ttu-id="7ecf6-153">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="7ecf6-153">Replace the following:</span></span>  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="7ecf6-154">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-154">with:</span></span>  
  
    ```  
    Using Microsoft_Association_Rules  
    ```  
  
     <span data-ttu-id="7ecf6-155">이제 결과 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-155">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Default Association]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    Using Microsoft_Association_Rules  
    ```  
  
7.  <span data-ttu-id="7ecf6-156">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-156">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="7ecf6-157">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Default_Association_Model.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-157">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Default_Association_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="7ecf6-158">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-158">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-an-association-mining-model-to-the-structure-changing-the-default-minimum_probability"></a><span data-ttu-id="7ecf6-159">MINIMUM_PROBABILITY의 기본값을 변경하여 구조에 연결 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="7ecf6-159">Adding an Association Mining Model to the Structure Changing the Default MINIMUM_PROBABILITY</span></span>  
 <span data-ttu-id="7ecf6-160">다음 태스크는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 연결 알고리즘을 기반으로 Market Basket 마이닝 구조에 새 마이닝 모델을 추가하고 MINIMUM_PROBABILITY의 기본값을 0.01로 변경하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-160">The next task is to add a new mining model to the Market Basket mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm, and change the default value for MINIMUM_PROBABILITY to 0.01.</span></span> <span data-ttu-id="7ecf6-161">매개 변수를 변경하면 [!INCLUDE[msCoName](../includes/msconame-md.md)] 연결 알고리즘에서 더 많은 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-161">Changing the parameter will cause the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm to create more rules.</span></span>  
  
#### <a name="to-add-an-association-mining-model"></a><span data-ttu-id="7ecf6-162">연결 마이닝 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="7ecf6-162">To add an Association mining model</span></span>  
  
1.  <span data-ttu-id="7ecf6-163">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-163">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="7ecf6-164">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-164">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="7ecf6-165">`ALTER MINING STRUCTURE` 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-165">Copy the generic example of the `ALTER MINING STRUCTURE` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="7ecf6-166">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="7ecf6-166">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="7ecf6-167">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-167">with:</span></span>  
  
    ```  
    Market Basket  
    ```  
  
4.  <span data-ttu-id="7ecf6-168">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="7ecf6-168">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="7ecf6-169">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-169">with:</span></span>  
  
    ```  
    [Modified Association]  
    ```  
  
5.  <span data-ttu-id="7ecf6-170">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="7ecf6-170">Replace the following:</span></span>  
  
    ```  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     <span data-ttu-id="7ecf6-171">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-171">with:</span></span>  
  
    ```  
    OrderNumber,  
    [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     <span data-ttu-id="7ecf6-172">이 경우 `[Products]` 테이블을 예측 가능한 열로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-172">In this case, the `[Products]` table has been designated as the predictable column.</span></span> <span data-ttu-id="7ecf6-173">또한 `[MODEL]` 열은 중첩 테이블의 키 열이므로 목록에 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-173">Also, the `[MODEL]` column is included in the list because it is the key column in the nested table.</span></span>  
  
6.  <span data-ttu-id="7ecf6-174">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="7ecf6-174">Replace the following:</span></span>  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="7ecf6-175">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-175">with:</span></span>  
  
    ```  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
     <span data-ttu-id="7ecf6-176">이제 결과 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-176">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Modified Assocation]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
7.  <span data-ttu-id="7ecf6-177">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-177">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="7ecf6-178">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Modified Association_Model.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-178">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Modified Association_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="7ecf6-179">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-179">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="7ecf6-180">다음 단원에서는 Market Basket 마이닝 구조를 연결된 해당 마이닝 모델과 함께 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7ecf6-180">In this next lesson you will process the Market Basket mining structure together with its associated mining models.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="7ecf6-181">다음 단원</span><span class="sxs-lookup"><span data-stu-id="7ecf6-181">Next Lesson</span></span>  
 [<span data-ttu-id="7ecf6-182">3단원: Market Basket 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="7ecf6-182">Lesson 3: Processing the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
  
  
