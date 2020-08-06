---
title: '1 단원: 시장 바구니 마이닝 구조 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6a6e123e525512a72d70bcc8ca2eba549d1347e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734708"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a><span data-ttu-id="3b321-102">1단원: Market Basket 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="3b321-102">Lesson 1: Creating the Market Basket Mining Structure</span></span>
  <span data-ttu-id="3b321-103">이 단원에서는 고객이 동시에 구입하는 경향이 있는 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 제품을 예측할 수 있는 마이닝 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-103">In this lesson, you will create a mining structure that allows you to predict what [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] products a customer tends to purchase at the same time.</span></span> <span data-ttu-id="3b321-104">마이닝 구조 및 데이터 마이닝의 해당 역할에 익숙하지 않은 경우 [마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3b321-104">If you are unfamiliar with mining structures and their role in data mining, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="3b321-105">이 단원에서 만들 연결 마이닝 구조는 [Microsoft 연결 알고리즘](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)기반 마이닝 모델 추가 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-105">The association mining structure that you will create in this lesson supports adding mining models based on the [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md).</span></span> <span data-ttu-id="3b321-106">이후 단원에서는 마이닝 모델을 사용하여 고객이 동시에 구입하는 경향이 있는 제품 유형을 예측합니다. 이를 시장 바구니 분석이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-106">In later lessons, you will use the mining models to predict the type of products a customer tends to purchase at the same time, which is called a market basket analysis.</span></span> <span data-ttu-id="3b321-107">예를 들어 고객이 산악 자전거, 자전거 타이어 및 헬멧을 동시에 구입하는 경향이 있음을 알게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-107">For example, you may find that customers tend to buy mountain bikes, bike tires, and helmets at the same time.</span></span>  
  
 <span data-ttu-id="3b321-108">이 단원에서는 중첩 테이블을 사용하여 마이닝 구조를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-108">In this lesson, the mining structure is defined by using nested tables.</span></span> <span data-ttu-id="3b321-109">구조에서 정의하는 데이터 도메인이 두 개의 다른 원본 테이블 내에 있으므로 중첩 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-109">Nested tables are used because the data domain that will be defined by the structure is contained within two different source tables.</span></span> <span data-ttu-id="3b321-110">중첩 테이블에 대 한 자세한 내용은 [데이터 마이닝&#41;Analysis Services &#40;중첩 테이블 ](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b321-110">For more information on nested tables, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
## <a name="create-mining-structure-statement"></a><span data-ttu-id="3b321-111">CREATE MINING STRUCTURE 문</span><span class="sxs-lookup"><span data-stu-id="3b321-111">CREATE MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="3b321-112">중첩 테이블이 포함 된 마이닝 구조를 만들려면 [CREATE 마이닝 structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-112">In order to create a mining structure containing a nested table, you use the [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) statement.</span></span> <span data-ttu-id="3b321-113">이 문의 코드는 다음 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-113">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="3b321-114">구조 이름 지정</span><span class="sxs-lookup"><span data-stu-id="3b321-114">Naming the structure</span></span>  
  
-   <span data-ttu-id="3b321-115">키 열 정의</span><span class="sxs-lookup"><span data-stu-id="3b321-115">Defining the key column</span></span>  
  
-   <span data-ttu-id="3b321-116">마이닝 열 정의</span><span class="sxs-lookup"><span data-stu-id="3b321-116">Defining the mining columns</span></span>  
  
-   <span data-ttu-id="3b321-117">중첩 테이블 열 정의</span><span class="sxs-lookup"><span data-stu-id="3b321-117">Defining the nested table columns</span></span>  
  
 <span data-ttu-id="3b321-118">다음은 CREATE MINING STRUCTURE 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-118">The following is a generic example of the CREATE MINING STRUCTURE statement:</span></span>  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 <span data-ttu-id="3b321-119">코드의 첫 번째 줄에서는 구조의 이름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-119">The first line of the code defines the name of the structure:</span></span>  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 <span data-ttu-id="3b321-120">DMX에서 개체의 이름을 지정 하는 방법에 대 한 자세한 내용은 [id &#40;dmx&#41;](/sql/dmx/identifiers-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3b321-120">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="3b321-121">코드의 다음 줄에서는 원본 데이터의 엔터티를 고유하게 식별하는 마이닝 구조에 대한 키 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-121">The next line of the code defines the key column for the mining structure, which uniquely identifies an entity in the source data:</span></span>  
  
```  
<key column>  
```  
  
 <span data-ttu-id="3b321-122">코드의 다음 줄은 마이닝 구조와 연결된 마이닝 모델에서 사용할 마이닝 열을 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-122">The next line of the code is used to define the mining columns that will be used by the mining models associated with the mining structure:</span></span>  
  
```  
<mining structure columns>  
```  
  
 <span data-ttu-id="3b321-123">코드의 다음 줄에서는 중첩 테이블 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-123">The next lines of the code define the nested table columns:</span></span>  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 <span data-ttu-id="3b321-124">정의할 수 있는 마이닝 구조 열 유형에 대한 자세한 내용은 [Mining Structure Columns](../../2014/analysis-services/data-mining/mining-structure-columns.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b321-124">For information about the types of mining structure columns that you can define, see [Mining Structure Columns](../../2014/analysis-services/data-mining/mining-structure-columns.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b321-125">기본적으로 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에서는 각 마이닝 구조에 대해 30%의 홀드아웃 데이터 집합을 만들지만 DMX를 사용하여 마이닝 구조를 만들 때 필요한 경우 홀드아웃 데이터 집합을 수동으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-125">By default, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] creates a 30 percent holdout data set for each mining structure; however, when you use DMX to create a mining structure, you must manually add the holdout data set, if desired.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="3b321-126">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="3b321-126">Lesson Tasks</span></span>  
 <span data-ttu-id="3b321-127">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-127">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="3b321-128">비어 있는 새 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="3b321-128">Create a new blank query</span></span>  
  
-   <span data-ttu-id="3b321-129">마이닝 구조를 만들기 위해 쿼리 변경</span><span class="sxs-lookup"><span data-stu-id="3b321-129">Alter the query to create the mining structure</span></span>  
  
-   <span data-ttu-id="3b321-130">쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="3b321-130">Execute the query</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="3b321-131">쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="3b321-131">Creating the Query</span></span>  
 <span data-ttu-id="3b321-132">첫 번째 단계는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결하고 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 새 DNX 쿼리를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-132">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="3b321-133">SQL Server Management Studio에서 새 DMX 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="3b321-133">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="3b321-134">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-134">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="3b321-135">**서버에 연결** 대화 상자에서 **서버 유형**으로 **Analysis Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-135">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="3b321-136">**서버 이름**,를 입력 `LocalHost` 하거나이 단원에서 연결할 인스턴스의 이름을 입력 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-136">In **Server name**, type `LocalHost`, or the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="3b321-137">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-137">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="3b321-138">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-138">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="3b321-139">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-139">Query Editor opens and contains a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="3b321-140">쿼리 변경</span><span class="sxs-lookup"><span data-stu-id="3b321-140">Altering the Query</span></span>  
 <span data-ttu-id="3b321-141">다음 단계는 Market Basket 마이닝 구조를 만들기 위해 위에서 설명한 CREATE MINING STRUCTURE 문을 수정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-141">The next step is to modify the CREATE MINING STRUCTURE statement described above to create the Market Basket mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a><span data-ttu-id="3b321-142">CREATE MINING STRUCTURE 문을 사용자 지정하려면</span><span class="sxs-lookup"><span data-stu-id="3b321-142">To customize the CREATE MINING STRUCTURE statement</span></span>  
  
1.  <span data-ttu-id="3b321-143">쿼리 편집기에서 CREATE MINING STRUCTURE 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-143">In Query Editor, copy the generic example of the CREATE MINING STRUCTURE statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="3b321-144">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="3b321-144">Replace the following:</span></span>  
  
    ```  
    [mining structure name]   
    ```  
  
     <span data-ttu-id="3b321-145">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-145">with:</span></span>  
  
    ```  
    [Market Basket]  
    ```  
  
3.  <span data-ttu-id="3b321-146">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="3b321-146">Replace the following:</span></span>  
  
    ```  
    <key column>  
    ```  
  
     <span data-ttu-id="3b321-147">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-147">with:</span></span>  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  <span data-ttu-id="3b321-148">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="3b321-148">Replace the following:</span></span>  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     <span data-ttu-id="3b321-149">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-149">with:</span></span>  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     <span data-ttu-id="3b321-150">TEXT KEY 언어는 Model 열이 중첩 테이블에 대한 키 열임을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-150">The TEXT KEY language specifies that the Model column is the key column for the nested table.</span></span>  
  
     <span data-ttu-id="3b321-151">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-151">The complete mining structure statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  <span data-ttu-id="3b321-152">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="3b321-153">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Market Basket Structure.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Market Basket Structure.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="3b321-154">쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="3b321-154">Executing the Query</span></span>  
 <span data-ttu-id="3b321-155">마지막 단계는 쿼리를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-155">The final step is to execute the query.</span></span> <span data-ttu-id="3b321-156">쿼리를 만들어 저장한 다음 서버에 마이닝 구조를 만들려면 해당 쿼리를 실행해야 합니다. 즉, 해당 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-156">After a query is created and saved, it needs to be executed (that is, the statement needs to be run) in order to create the mining structure on the server.</span></span> <span data-ttu-id="3b321-157">쿼리 편집기에서 쿼리를 실행 하는 방법에 대 한 자세한 내용은 [데이터베이스 엔진 쿼리 편집기 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3b321-157">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="3b321-158">쿼리를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="3b321-158">To execute the query</span></span>  
  
-   <span data-ttu-id="3b321-159">쿼리 편집기의 도구 모음에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-159">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="3b321-160">문의 실행이 끝나면 쿼리 상태가 쿼리 편집기 아래쪽의 **메시지** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-160">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="3b321-161">메시지는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-161">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="3b321-162">이제 **Market Basket** 이라는 새 구조가 서버에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-162">A new structure named **Market Basket** now exists on the server.</span></span>  
  
 <span data-ttu-id="3b321-163">다음 단원에서는 방금 만든 Market Basket 마이닝 구조에 마이닝 모델을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3b321-163">In the next lesson, you will add mining models to the Market Basket mining structure you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="3b321-164">다음 단원</span><span class="sxs-lookup"><span data-stu-id="3b321-164">Next Lesson</span></span>  
 [<span data-ttu-id="3b321-165">2단원: Market Basket 마이닝 구조에 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="3b321-165">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
