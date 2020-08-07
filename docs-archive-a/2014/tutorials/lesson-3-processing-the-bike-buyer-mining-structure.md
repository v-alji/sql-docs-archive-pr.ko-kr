---
title: '3 단원: 자전거 구매자 마이닝 구조 처리 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e3f85016b32884b9a6b809e28d20d9985f97cd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734695"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a><span data-ttu-id="16fde-102">3단원: Bike Buyer 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="16fde-102">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="16fde-103">이 단원에서는 INSERT INTO 문과 예제 데이터베이스의 vTargetMail 뷰를 사용 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 하 여 [1 단원: 자전거 구매자 마이닝 구조 만들기](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) 및 [2 단원: 자전거 구매자 마이닝 구조에 마이닝 모델 추가](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)에서 만든 마이닝 구조 및 마이닝 모델을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-103">In this lesson, you will use the INSERT INTO statement and the vTargetMail view from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database to process the mining structures and mining models that you created in [Lesson 1: Creating the Bike Buyer Mining Structure](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) and [Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).</span></span>  
  
 <span data-ttu-id="16fde-104">마이닝 구조를 처리하면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 원본 데이터를 읽은 다음 마이닝 모델을 지원하는 구조를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="16fde-105">마이닝 모델을 처리하면 마이닝 구조에서 정의한 데이터가 사용자가 선택한 데이터 마이닝 알고리즘을 통해 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-105">When you process a mining model, the data defined by the mining structure is passed through the data mining algorithm that you choose.</span></span> <span data-ttu-id="16fde-106">이 알고리즘에서는 경향 및 패턴을 검색한 다음 마이닝 모델에 이 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-106">The algorithm searches for trends and patterns, and then stores this information in the mining model.</span></span> <span data-ttu-id="16fde-107">따라서 마이닝 모델은 실제 원본 데이터 대신 알고리즘에서 발견한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-107">The mining model, therefore, does not contain the actual source data, but instead contains the information that was discovered by the algorithm.</span></span> <span data-ttu-id="16fde-108">마이닝 모델 처리에 대 한 자세한 내용은 [데이터 마이닝&#41;&#40;처리 요구 사항 및 고려 ](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)사항을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="16fde-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
 <span data-ttu-id="16fde-109">구조 열이나 원본 데이터를 변경하는 경우에만 마이닝 구조를 다시 처리하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-109">You need to reprocess a mining structure only if you change a structure column or change the source data.</span></span> <span data-ttu-id="16fde-110">이미 처리된 마이닝 구조에 마이닝 모델을 추가하는 경우에는 INSERT INTO MINING MODEL 문을 사용하여 새 마이닝 모델을 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-110">If you add a mining model to a mining structure that has already been processed, you can use the INSERT INTO MINING MODEL statement to train the new mining model.</span></span>  
  
## <a name="train-structure-template"></a><span data-ttu-id="16fde-111">구조 템플릿의 학습</span><span class="sxs-lookup"><span data-stu-id="16fde-111">Train Structure Template</span></span>  
 <span data-ttu-id="16fde-112">마이닝 구조 및 연결 된 마이닝 모델을 학습 하려면 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-112">In order to train the mining structure and its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="16fde-113">이 문의 코드는 다음 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-113">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="16fde-114">마이닝 구조 식별</span><span class="sxs-lookup"><span data-stu-id="16fde-114">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="16fde-115">마이닝 구조의 열 나열</span><span class="sxs-lookup"><span data-stu-id="16fde-115">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="16fde-116">학습 데이터 정의</span><span class="sxs-lookup"><span data-stu-id="16fde-116">Defining the training data</span></span>  
  
 <span data-ttu-id="16fde-117">다음은 INSERT INTO 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-117">The following is a generic example of the INSERT INTO statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 <span data-ttu-id="16fde-118">코드의 첫 번째 줄에서는 학습할 마이닝 구조를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-118">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="16fde-119">코드의 다음 줄에서는 마이닝 구조에서 정의한 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-119">The next line of the code specifies the columns that are defined by the mining structure.</span></span> <span data-ttu-id="16fde-120">마이닝 구조의 각 열을 나열해야 하며 각 열을 원본 쿼리 데이터 내에 포함된 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-120">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span>  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 <span data-ttu-id="16fde-121">코드의 마지막 줄에서는 마이닝 구조의 학습에 사용할 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-121">The final line of the code defines the data that will be used to train the mining structure:</span></span>  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 <span data-ttu-id="16fde-122">이 단원에서는 `OPENQUERY`를 사용하여 원본 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-122">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="16fde-123">원본 쿼리를 정의 하는 다른 방법에 대 한 자세한 내용은 [&#60;원본 데이터 쿼리&#62;](/sql/dmx/source-data-query)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="16fde-123">For information about other methods of defining the source query, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="16fde-124">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="16fde-124">Lesson Tasks</span></span>  
 <span data-ttu-id="16fde-125">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-125">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="16fde-126">Bike Buyer 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="16fde-126">Process the Bike Buyer mining structure</span></span>  
  
## <a name="processing-the-predictive-mining-structure"></a><span data-ttu-id="16fde-127">예측 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="16fde-127">Processing the Predictive Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a><span data-ttu-id="16fde-128">INSERT INTO를 사용하여 마이닝 구조를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="16fde-128">To process the mining structure by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="16fde-129">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-129">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="16fde-130">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-130">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="16fde-131">INSERT INTO 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-131">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="16fde-132">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="16fde-132">Replace the following:</span></span>  
  
    ```  
    [<mining structure name>]   
    ```  
  
     <span data-ttu-id="16fde-133">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-133">with:</span></span>  
  
    ```  
    Bike Buyer  
    ```  
  
4.  <span data-ttu-id="16fde-134">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="16fde-134">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    ```  
  
     <span data-ttu-id="16fde-135">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-135">with:</span></span>  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
    [Commute Distance],  
    [Education],  
    [Gender],  
    [House Owner Flag],  
    [Marital Status],  
    [Number Cars Owned],  
    [Number Children At Home],  
    [Occupation],  
    [Region],  
    [Total Children],  
    [Yearly Income]  
    ```  
  
5.  <span data-ttu-id="16fde-136">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="16fde-136">Replace the following:</span></span>  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     <span data-ttu-id="16fde-137">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-137">with:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     <span data-ttu-id="16fde-138">OPENQUERY 문은 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 데이터 원본을 참조하여 vTargetMail 뷰에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-138">The OPENQUERY statement references the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source to access the view vTargetMail.</span></span> <span data-ttu-id="16fde-139">이 뷰에는 마이닝 모델의 학습에 사용할 원본 데이터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-139">The view contains the source data that will be used to train the mining models.</span></span>  
  
     <span data-ttu-id="16fde-140">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-140">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]     
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  <span data-ttu-id="16fde-141">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-141">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="16fde-142">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Process Bike Buyer Structure.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-142">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Process Bike Buyer Structure.dmx`.</span></span>  
  
8.  <span data-ttu-id="16fde-143">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-143">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="16fde-144">다음 단원에서는 이 단원에서 마이닝 구조에 추가한 마이닝 모델의 내용을 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="16fde-144">In the next lesson, you will explore content in the mining models you added to the mining structure in this lesson.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="16fde-145">다음 단원</span><span class="sxs-lookup"><span data-stu-id="16fde-145">Next Lesson</span></span>  
 [<span data-ttu-id="16fde-146">4단원: Bike Buyer 마이닝 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="16fde-146">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
