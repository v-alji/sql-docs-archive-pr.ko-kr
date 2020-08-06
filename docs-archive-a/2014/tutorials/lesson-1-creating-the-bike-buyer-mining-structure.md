---
title: '1 단원: 자전거 구매자 마이닝 구조 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6384910858d87a80aa3c8f897bc88e45f4504fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734707"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a><span data-ttu-id="47b96-102">1단원: Bike Buyer 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="47b96-102">Lesson 1: Creating the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="47b96-103">이 단원에서는 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]의 잠재 고객이 자전거를 구입할 것인지 여부를 예측할 수 있는 마이닝 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-103">In this lesson, you will create a mining structure that allows you to predict whether a potential customer of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] will purchase a bicycle.</span></span> <span data-ttu-id="47b96-104">마이닝 구조 및 데이터 마이닝의 해당 역할에 익숙하지 않은 경우 [마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47b96-104">If you are unfamiliar with mining structures and their role in data mining, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="47b96-105">이 단원에서 만들 자전거 구매자 마이닝 구조는 [Microsoft 클러스터링 알고리즘](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft 의사 결정 트리 알고리즘](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)을 기반으로 마이닝 모델을 추가 하는 것을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-105">The Bike Buyer mining structure that you will create in this lesson supports adding mining models based on the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md).</span></span> <span data-ttu-id="47b96-106">이후 단원에서는 클러스터링 마이닝 모델을 사용하여 고객을 그룹화할 수 있는 다양한 방법을 탐색하고 의사 결정 트리 마이닝 모델을 사용하여 잠재 고객이 자전거를 구입할 것인지 여부를 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-106">In later lessons, you will use the clustering mining models to explore the different ways in which customers can be grouped, and will use decision tree mining models to predict whether or not a potential customer will purchase a bicycle.</span></span>  
  
## <a name="create-mining-structure-statement"></a><span data-ttu-id="47b96-107">CREATE MINING STRUCTURE 문</span><span class="sxs-lookup"><span data-stu-id="47b96-107">CREATE MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="47b96-108">마이닝 구조를 만들려면 [CREATE 마이닝 structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-108">To create a mining structure, you use the [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) statement.</span></span> <span data-ttu-id="47b96-109">이 문의 코드는 다음 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-109">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="47b96-110">구조 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-110">Naming the structure.</span></span>  
  
-   <span data-ttu-id="47b96-111">키 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-111">Defining the key column.</span></span>  
  
-   <span data-ttu-id="47b96-112">마이닝 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-112">Defining the mining columns.</span></span>  
  
-   <span data-ttu-id="47b96-113">선택적 테스트 데이터 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-113">Defining an optional testing data set.</span></span>  
  
 <span data-ttu-id="47b96-114">다음은 CREATE MINING STRUCTURE 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-114">The following is a generic example of the CREATE MINING STRUCTURE statement:</span></span>  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
(  
    <key column>,  
    <mining structure columns>  
)   
WITH HOLDOUT (<holdout specifier>)  
```  
  
 <span data-ttu-id="47b96-115">코드의 첫 번째 줄에서는 구조의 이름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-115">The first line of the code defines the name of the structure:</span></span>  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="47b96-116">DMX (데이터 마이닝 확장)에서 개체의 이름을 지정 하는 방법에 대 한 자세한 내용은 [id &#40;dmx&#41;](/sql/dmx/identifiers-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47b96-116">For information about naming an object in Data Mining Extensions (DMX), see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="47b96-117">코드의 다음 줄에서는 원본 데이터의 엔터티를 고유하게 식별하는 마이닝 구조에 대한 키 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-117">The next line of the code defines the key column for the mining structure, which uniquely identifies an entity in the source data:</span></span>  
  
```  
<key column>,  
```  
  
 <span data-ttu-id="47b96-118">마이닝 구조에서 원본 데이터의 엔터티를 정의하는 고객 식별자(`CustomerKey`)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-118">In the mining structure you will create, the customer identifier, `CustomerKey`, defines an entity in the source data.</span></span>  
  
 <span data-ttu-id="47b96-119">코드의 다음 줄은 마이닝 구조와 연결된 마이닝 모델에서 사용할 마이닝 열을 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-119">The next line of the code is used to define the mining columns that will be used by the mining models associated with the mining structure:</span></span>  
  
```  
<mining structure columns>  
```  
  
 <span data-ttu-id="47b96-120">다음 구문을 사용 하 여에서 불연속화 함수를 사용 \<mining structure columns> 하 여 연속 열을 불연속화 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-120">You can use the DISCRETIZE function within \<mining structure columns> to discretize continuous columns by using the following syntax:</span></span>  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 <span data-ttu-id="47b96-121">분할 열에 대 한 자세한 내용은 [데이터 마이닝&#41;&#40;분할 방법 ](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47b96-121">For more information about discretizing columns, see [Discretization Methods &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).</span></span> <span data-ttu-id="47b96-122">정의할 수 있는 마이닝 구조 열 유형에 대 한 자세한 내용은 [마이닝 구조 열](../../2014/analysis-services/data-mining/mining-structure-columns.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47b96-122">For more information about the types of mining structure columns that you can define, see [Mining Structure Columns](../../2014/analysis-services/data-mining/mining-structure-columns.md).</span></span>  
  
 <span data-ttu-id="47b96-123">코드의 마지막 줄에서는 마이닝 구조의 선택적 파티션을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-123">The final line of the code defines an optional partition in the mining structure:</span></span>  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 <span data-ttu-id="47b96-124">구조와 관련된 테스트 마이닝 모델에 사용할 일부 데이터를 지정하면 나머지 데이터는 모델 학습에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-124">You specify some portion of the data to use for testing mining models that are related to the structure, and the remaining data is used for training the models.</span></span> <span data-ttu-id="47b96-125">기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]는 모든 사례 데이터의 30%를 포함하는 테스트 데이터 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-125">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates a test data set that contains 30 percent of all case data.</span></span> <span data-ttu-id="47b96-126">테스트 데이터 집합이 사례의 30%(최대 1000개의 사례)를 포함해야 하는 사양을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-126">You will add the specification that the test data set should contain 30 percent of the cases up to a maximum of 1000 cases.</span></span> <span data-ttu-id="47b96-127">사례의 30%가 1000개보다 작으면 테스트 데이터 집합에 보다 적은 양이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-127">If 30 percent of the cases is less than 1000, the test data set will contain the smaller amount.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="47b96-128">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="47b96-128">Lesson Tasks</span></span>  
 <span data-ttu-id="47b96-129">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-129">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="47b96-130">비어 있는 새 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-130">Create a new blank query.</span></span>  
  
-   <span data-ttu-id="47b96-131">마이닝 구조를 만들기 위해 쿼리를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-131">Alter the query to create the mining structure.</span></span>  
  
-   <span data-ttu-id="47b96-132">쿼리 실행.</span><span class="sxs-lookup"><span data-stu-id="47b96-132">Execute the query.</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="47b96-133">쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="47b96-133">Creating the Query</span></span>  
 <span data-ttu-id="47b96-134">첫 번째 단계는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결하고 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 새 DNX 쿼리를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-134">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="47b96-135">SQL Server Management Studio에서 새 DMX 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="47b96-135">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="47b96-136">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-136">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="47b96-137">**서버에 연결** 대화 상자에서 **서버 유형**으로 **Analysis Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-137">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="47b96-138">**서버 이름**에을 입력 `LocalHost` 하거나이 단원에서 연결할 인스턴스의 이름을 입력 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-138">In **Server name**, type `LocalHost`, or type the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="47b96-139">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-139">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="47b96-140">**개체 탐색기**에서 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **새 쿼리**를 가리킨 다음 **DMX** 를 클릭 하 여 **쿼리 편집기** 와 비어 있는 새 쿼리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-140">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the **Query Editor** and a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="47b96-141">쿼리 변경</span><span class="sxs-lookup"><span data-stu-id="47b96-141">Altering the Query</span></span>  
 <span data-ttu-id="47b96-142">다음 단계는 Bike Buyer 마이닝 구조를 만들기 위해 위에서 설명한 CREATE MINING STRUCTURE 문을 수정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-142">The next step is to modify the CREATE MINING STRUCTURE statement described above to create the Bike Buyer mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a><span data-ttu-id="47b96-143">CREATE MINING STRUCTURE 문을 사용자 지정하려면</span><span class="sxs-lookup"><span data-stu-id="47b96-143">To customize the CREATE MINING STRUCTURE statement</span></span>  
  
1.  <span data-ttu-id="47b96-144">쿼리 편집기에서 CREATE MINING STRUCTURE 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-144">In the Query Editor, copy the generic example of the CREATE MINING STRUCTURE statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="47b96-145">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="47b96-145">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]   
    ```  
  
     <span data-ttu-id="47b96-146">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-146">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  <span data-ttu-id="47b96-147">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="47b96-147">Replace the following:</span></span>  
  
    ```  
    <key column>   
    ```  
  
     <span data-ttu-id="47b96-148">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-148">with:</span></span>  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  <span data-ttu-id="47b96-149">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="47b96-149">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>   
    ```  
  
     <span data-ttu-id="47b96-150">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-150">with:</span></span>  
  
    ```  
    [Age] LONG DISCRETIZED(Automatic,10),  
    [Bike Buyer] LONG DISCRETE,  
    [Commute Distance] TEXT DISCRETE,  
    [Education] TEXT DISCRETE,  
    [Gender] TEXT DISCRETE,  
    [House Owner Flag] TEXT DISCRETE,  
    [Marital Status] TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Number Children At Home] LONG DISCRETE,  
    [Occupation] TEXT DISCRETE,  
    [Region] TEXT DISCRETE,  
    [Total Children]LONG DISCRETE,  
    [Yearly Income] DOUBLE CONTINUOUS  
    ```  
  
5.  <span data-ttu-id="47b96-151">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="47b96-151">Replace the following:</span></span>  
  
    ```  
    WITH HOLDOUT (holdout specifier>)  
    ```  
  
     <span data-ttu-id="47b96-152">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-152">with:</span></span>  
  
    ```  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
    ```  
  
     <span data-ttu-id="47b96-153">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-153">The complete mining structure statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key] LONG KEY,  
       [Age]LONG DISCRETIZED(Automatic,10),  
       [Bike Buyer] LONG DISCRETE,  
       [Commute Distance] TEXT DISCRETE,  
       [Education] TEXT DISCRETE,  
       [Gender] TEXT DISCRETE,  
       [House Owner Flag] TEXT DISCRETE,  
       [Marital Status] TEXT DISCRETE,  
       [Number Cars Owned]LONG DISCRETE,  
       [Number Children At Home]LONG DISCRETE,  
       [Occupation] TEXT DISCRETE,  
       [Region] TEXT DISCRETE,  
       [Total Children]LONG DISCRETE,  
       [Yearly Income] DOUBLE CONTINUOUS  
    )  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
  
    ```  
  
6.  <span data-ttu-id="47b96-154">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-154">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="47b96-155">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Bike Buyer Structure.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-155">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Bike Buyer Structure.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="47b96-156">쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="47b96-156">Executing the Query</span></span>  
 <span data-ttu-id="47b96-157">마지막 단계는 쿼리를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-157">The final step is to execute the query.</span></span> <span data-ttu-id="47b96-158">쿼리를 만들고 저장한 다음에는 해당 쿼리를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-158">After a query is created and saved, it needs to be executed.</span></span> <span data-ttu-id="47b96-159">즉, 서버에 마이닝 구조를 만들려면 해당 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-159">That is, the statement needs to be run in order to create the mining structure on the server.</span></span> <span data-ttu-id="47b96-160">쿼리 편집기에서 쿼리를 실행 하는 방법에 대 한 자세한 내용은 [데이터베이스 엔진 쿼리 편집기 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47b96-160">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="47b96-161">쿼리를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="47b96-161">To execute the query</span></span>  
  
1.  <span data-ttu-id="47b96-162">쿼리 편집기의 도구 모음에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-162">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="47b96-163">문의 실행이 끝나면 쿼리 상태가 쿼리 편집기 아래쪽의 **메시지** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-163">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="47b96-164">메시지는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-164">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="47b96-165">이제 **자전거 구매자** 라는 새 구조가 서버에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-165">A new structure named **Bike Buyer** now exists on the server.</span></span>  
  
 <span data-ttu-id="47b96-166">다음 단원에서는 방금 만든 구조에 마이닝 모델을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="47b96-166">In the next lesson, you will add mining models to the structure you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="47b96-167">다음 단원</span><span class="sxs-lookup"><span data-stu-id="47b96-167">Next Lesson</span></span>  
 [<span data-ttu-id="47b96-168">2단원: Bike Buyer 마이닝 구조에 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="47b96-168">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
