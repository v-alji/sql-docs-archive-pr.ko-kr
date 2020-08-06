---
title: '3 단원: 시장 바구니 마이닝 구조 처리 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095a043f-cf6f-45bb-a021-ae4e1b535c65
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce2c2e6944d524a38edc331d2cd128ca7cf7d419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727519"
---
# <a name="lesson-3-processing-the-market-basket-mining-structure"></a><span data-ttu-id="eee89-102">3단원: Market Basket 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="eee89-102">Lesson 3: Processing the Market Basket Mining Structure</span></span>
  <span data-ttu-id="eee89-103">이 단원에서는 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) 문을 사용 하 고 샘플 데이터베이스의 VAssocSeqLineItems 및 vAssocSeqOrders를 사용 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 하 여 [1 단원: 시장 바구니 마이닝 구조 만들기](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md) 및 [2 단원: 시장 바구니 마이닝 구조에 마이닝 모델 추가](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)에서 만든 마이닝 구조 및 마이닝 모델을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-103">In this lesson, you will use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement and the vAssocSeqLineItems and vAssocSeqOrders from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database to process the mining structures and mining models that you created in [Lesson 1: Creating the Market Basket Mining Structure](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md) and [Lesson 2: Adding Mining Models to the Market Basket Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span>  
  
 <span data-ttu-id="eee89-104">마이닝 구조를 처리하면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 원본 데이터를 읽은 다음 마이닝 모델을 지원하는 구조를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="eee89-105">마이닝 모델을 처리하면 마이닝 구조에서 정의한 데이터가 사용자가 선택한 데이터 마이닝 알고리즘을 통해 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-105">When you process a mining model, the data defined by the mining structure is passed through the data mining algorithm that you chose.</span></span> <span data-ttu-id="eee89-106">이 알고리즘에서는 경향 및 패턴을 검색한 다음 마이닝 모델에 이 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-106">The algorithm searches for trends and patterns, and then stores this information in the mining model.</span></span> <span data-ttu-id="eee89-107">따라서 마이닝 모델은 실제 원본 데이터 대신 알고리즘에서 발견한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-107">The mining model, therefore, does not contain the actual source data, but instead contains the information that was discovered by the algorithm.</span></span> <span data-ttu-id="eee89-108">마이닝 모델 처리에 대 한 자세한 내용은 [데이터 마이닝&#41;&#40;처리 요구 사항 및 고려 ](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)사항을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eee89-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
 <span data-ttu-id="eee89-109">구조 열이나 원본 데이터를 변경하는 경우에만 마이닝 구조를 다시 처리하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-109">You only have to reprocess a mining structure if you change a structure column or change the source data.</span></span> <span data-ttu-id="eee89-110">이미 처리된 마이닝 구조에 마이닝 모델을 추가하는 경우에는 `INSERT INTO MINING MODEL` 문을 사용하여 기존 데이터를 기반으로 새 마이닝 모델을 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-110">If you add a mining model to a mining structure that has already been processed, you can use the `INSERT INTO MINING MODEL` statement to train the new mining model on the existing data.</span></span>  
  
 <span data-ttu-id="eee89-111">Market Basket 마이닝 구조에 중첩 테이블이 있으므로 중첩 테이블 구조를 사용하여 학습할 마이닝 열을 정의하고 `SHAPE` 명령을 사용하여 원본 테이블에서 학습 데이터를 가져오는 쿼리를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-111">Because the Market Basket mining structure contains a nested table, you will have to define the mining columns to be trained using the nested table structure, and use the `SHAPE` command to define the queries that pull the training data from the source tables.</span></span>  
  
## <a name="insert-into-statement"></a><span data-ttu-id="eee89-112">INSERT INTO 문</span><span class="sxs-lookup"><span data-stu-id="eee89-112">INSERT INTO Statement</span></span>  
 <span data-ttu-id="eee89-113">시장 바구니 마이닝 구조와 연결 된 마이닝 모델을 학습 하려면 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-113">In order to train the Market Basket mining structure and its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="eee89-114">이 문의 코드는 다음 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-114">The code in the statement can be broken into the following parts.</span></span>  
  
-   <span data-ttu-id="eee89-115">마이닝 구조 식별</span><span class="sxs-lookup"><span data-stu-id="eee89-115">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="eee89-116">마이닝 구조의 열 나열</span><span class="sxs-lookup"><span data-stu-id="eee89-116">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="eee89-117">`SHAPE`을 사용하여 학습 데이터 정의</span><span class="sxs-lookup"><span data-stu-id="eee89-117">Defining the training data using `SHAPE`</span></span>  
  
 <span data-ttu-id="eee89-118">다음은 `INSERT INTO` 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-118">The following is a generic example of the `INSERT INTO` statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],'<nested SELECT statement>')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 <span data-ttu-id="eee89-119">코드의 첫 번째 줄에서는 학습할 마이닝 구조를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-119">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="eee89-120">코드의 다음 줄에서는 마이닝 구조에서 정의한 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-120">The next lines of the code specify the columns that are defined by the mining structure.</span></span> <span data-ttu-id="eee89-121">마이닝 구조의 각 열을 나열해야 하며 각 열을 원본 쿼리 데이터 내에 포함된 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-121">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span> <span data-ttu-id="eee89-122">`SKIP`을 사용하여 원본 데이터에는 있지만 마이닝 구조에는 없는 열을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-122">You can use `SKIP` to ignore columns that exist in the source data but do not exist in the mining structure.</span></span> <span data-ttu-id="eee89-123">를 사용 하는 방법에 대 한 자세한 내용은 `SKIP` [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eee89-123">For more information about how to use `SKIP`, see [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx).</span></span>  
  
```  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
```  
  
 <span data-ttu-id="eee89-124">코드의 마지막 줄에서는 마이닝 구조의 학습에 사용할 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-124">The final lines of the code define the data that will be used to train the mining structure.</span></span> <span data-ttu-id="eee89-125">원본 데이터가 두 개의 테이블에 포함되어 있으므로 `SHAPE`을 사용하여 테이블을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-125">Because the source data is contained within two tables, you will use `SHAPE` to relate the tables.</span></span>  
  
```  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],''<nested SELECT statement>'')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 <span data-ttu-id="eee89-126">이 단원에서는 `OPENQUERY`를 사용하여 원본 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-126">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="eee89-127">원본 데이터에 대 한 쿼리를 정의 하는 다른 방법에 대 한 자세한 내용은 [&#60;원본 데이터 쿼리&#62;](/sql/dmx/source-data-query)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eee89-127">For information about other methods of defining a query on the source data, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="eee89-128">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="eee89-128">Lesson Tasks</span></span>  
 <span data-ttu-id="eee89-129">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-129">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="eee89-130">Market Basket 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="eee89-130">Process the Market Basket mining structure</span></span>  
  
## <a name="processing-the-market-basket-mining-structure"></a><span data-ttu-id="eee89-131">Market Basket 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="eee89-131">Processing the Market Basket Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a><span data-ttu-id="eee89-132">INSERT INTO를 사용하여 마이닝 구조를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="eee89-132">To process the mining structure by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="eee89-133">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-133">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="eee89-134">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-134">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="eee89-135">INSERT INTO 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-135">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="eee89-136">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="eee89-136">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]  
    ```  
  
     <span data-ttu-id="eee89-137">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-137">with:</span></span>  
  
    ```  
    Market Basket  
    ```  
  
4.  <span data-ttu-id="eee89-138">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="eee89-138">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    [<nested table>]  
    ( SKIP, <skipped column> )  
    ```  
  
     <span data-ttu-id="eee89-139">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-139">with:</span></span>  
  
    ```  
    [OrderNumber],  
    [Products]   
    (SKIP, [Model])  
    ```  
  
     <span data-ttu-id="eee89-140">구문 중 `Products`는 SHAPE 문에 의해 정의된 Products 테이블을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-140">In the statement, `Products` refers to the Products table defined by the SHAPE statement.</span></span> <span data-ttu-id="eee89-141">`SKIP`은 원본 데이터에 키로 존재하는 Model 열을 무시하는 데 사용되지만 마이닝 구조에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-141">`SKIP` is used to ignore the Model column, which exists in the source data as a key, but is not used by the mining structure.</span></span>  
  
5.  <span data-ttu-id="eee89-142">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="eee89-142">Replace the following:</span></span>  
  
    ```  
    SHAPE {  
      OPENQUERY([<datasource>],'<SELECT statement>') }  
    APPEND  
    (   
      {OPENQUERY([<datasource>],'<nested SELECT statement>')  
    }  
    RELATE [<case key>] TO [<foreign key>]  
    ) AS [<nested table>]  
    ```  
  
     <span data-ttu-id="eee89-143">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-143">with:</span></span>  
  
    ```  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
     <span data-ttu-id="eee89-144">원본 쿼리는 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 샘플 프로젝트에 정의 된 데이터 원본을 참조 합니다 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="eee89-144">The source query references the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source defined in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample project.</span></span> <span data-ttu-id="eee89-145">이 쿼리는 이 데이터 원본을 사용하여 vAssocSeqLineItems 및 vAssocSeqOrders 뷰에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-145">It uses this data source to access the vAssocSeqLineItems and vAssocSeqOrders views.</span></span> <span data-ttu-id="eee89-146">이러한 뷰에는 마이닝 모델의 학습에 사용할 원본 데이터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-146">These views contain the source data that will be used to train the mining model.</span></span> <span data-ttu-id="eee89-147">이 프로젝트 또는 이러한 뷰를 만들지 않은 경우 [기본 데이터 마이닝 자습서](../../2014/tutorials/basic-data-mining-tutorial.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eee89-147">If you have not created this project or these views, see [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span>  
  
     <span data-ttu-id="eee89-148">`SHAPE` 명령 내에서 `OPENQUERY`를 사용하여 두 개의 쿼리를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-148">Within the `SHAPE` command, you will use `OPENQUERY` to define two queries.</span></span> <span data-ttu-id="eee89-149">첫 번째 쿼리는 부모 테이블을 정의하고 두 번째 쿼리는 중첩 테이블을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-149">The first query defines the parent table, and the second query defines the nested table.</span></span> <span data-ttu-id="eee89-150">이 두 개의 테이블은 두 테이블 모두에 있는 OrderNumber 열을 사용하여 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-150">The two tables are related using the OrderNumber column, which exists in both tables.</span></span>  
  
     <span data-ttu-id="eee89-151">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-151">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Market Basket]  
    (  
       [OrderNumber],[Products] (SKIP, [Model])  
    )  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
6.  <span data-ttu-id="eee89-152">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="eee89-153">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Process Market Basket.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Process Market Basket.dmx`.</span></span>  
  
8.  <span data-ttu-id="eee89-154">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-154">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="eee89-155">쿼리 실행이 종료된 다음에는 찾은 패턴 및 항목 집합을 보고 연결을 보며 항목 집합, 확률 또는 중요도별로 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-155">After the query has finished running, you can view the patterns and itemsets that were found, view associations, or filter by itemset, probability, or importance.</span></span> <span data-ttu-id="eee89-156">이 정보를 보려면에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 데이터 모델의 이름을 마우스 오른쪽 단추로 클릭 한 다음 **찾아보기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-156">To view this information, in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click the name of the data model, and then click **Browse**.</span></span>  
  
 <span data-ttu-id="eee89-157">다음 단원에서는 Market Basket 구조에 추가한 마이닝 모델을 기반으로 여러 예측을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eee89-157">In the next lesson, you will create several predictions based on the mining models that you added to the Market Basket structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="eee89-158">다음 단원</span><span class="sxs-lookup"><span data-stu-id="eee89-158">Next Lesson</span></span>  
 [<span data-ttu-id="eee89-159">4단원: Market Basket 예측 실행</span><span class="sxs-lookup"><span data-stu-id="eee89-159">Lesson 4: Executing Market Basket Predictions</span></span>](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
  
  
