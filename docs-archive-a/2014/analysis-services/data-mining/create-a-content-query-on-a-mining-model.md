---
title: 마이닝 모델에 대 한 내용 쿼리 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: a0ce837a-89ed-46cf-9ce1-801ccb75fa04
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26af1100d6ba80185c1cc4de18548df0e387824c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727480"
---
# <a name="create-a-content-query-on-a-mining-model"></a><span data-ttu-id="815b7-102">마이닝 모델에 내용 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="815b7-102">Create a Content Query on a Mining Model</span></span>
  <span data-ttu-id="815b7-103">AMO 또는 XML/A를 사용하여 프로그래밍 방식으로 마이닝 모델 콘텐츠를 쿼리할 수 있지만 DMX를 사용하여 쿼리를 만드는 편이 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-103">You can query the mining model content programmatically by using AMO or XML/A, but it is easier to create queries by using DMX.</span></span> <span data-ttu-id="815b7-104">또한 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 연결을 설정하고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 제공하는 DMV를 사용해 쿼리를 작성하는 방식으로 데이터 마이닝 스키마 행 집합에 대한 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-104">You can also create queries against the data mining schema rowsets by establishing a connection to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and creating a query using the DMVs provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="815b7-105">다음 절차에서는 DMX를 사용하여 마이닝 모델에 대한 쿼리를 만드는 방법과 데이터 마이닝 스키마 행 집합을 쿼리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-105">The following procedures demonstrate how to create queries against a mining model by using DMX, and how to query the data mining schema rowsets.</span></span>  
  
 <span data-ttu-id="815b7-106">XML/A를 사용하여 비슷한 쿼리를 만드는 방법에 대한 예는 [XMLA를 사용하여 데이터 마이닝 쿼리 만들기](create-a-data-mining-query-by-using-xmla.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="815b7-106">For an example of how to create a similar query by using XML/A, see [Create a Data Mining Query by Using XMLA](create-a-data-mining-query-by-using-xmla.md).</span></span>  
  
## <a name="querying-data-mining-model-content-by-using-dmx"></a><span data-ttu-id="815b7-107">DMX를 사용하여 데이터 마이닝 모델 내용 쿼리</span><span class="sxs-lookup"><span data-stu-id="815b7-107">Querying Data Mining Model Content by Using DMX</span></span>  
  
#### <a name="to-create-a-dmx-model-content-query"></a><span data-ttu-id="815b7-108">DMX 모델 내용 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="815b7-108">To create a DMX model content query</span></span>  
  
1.  <span data-ttu-id="815b7-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **템플릿 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="815b7-110">**템플릿 탐색기** 창에서 큐브 아이콘을 클릭하여 목록을 변경하고 Analysis Services 템플릿을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-110">In the **Template Explorer** pane, click the cube icon to change the list and display Analysis Services templates.</span></span>  
  
3.  <span data-ttu-id="815b7-111">템플릿 범주 목록에서 **DMX**, **모델 콘텐츠**를 차례로 확장하고 **내용 쿼리**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-111">In the list of template categories, expand **DMX**, expand **Model Content**, and double-click **Content Query**.</span></span>  
  
4.  <span data-ttu-id="815b7-112">**Analysis Services에 연결** 대화 상자에서 쿼리할 마이닝 모델이 포함된 인스턴스를 선택하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-112">In the **Connect to Analysis Services** dialog box, select the instance that contains the mining model you want to query, and click **Connect**.</span></span>  
  
     <span data-ttu-id="815b7-113">적절한 코드 편집기에서 **내용 쿼리** 템플릿이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-113">The **Content Query** template opens in the appropriate code editor.</span></span> <span data-ttu-id="815b7-114">메타데이터 창에는 현재 데이터베이스에서 사용할 수 있는 모델의 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-114">The metadata pane lists the models that are available in the current database.</span></span> <span data-ttu-id="815b7-115">데이터베이스를 변경하려면 **사용 가능한 데이터베이스** 목록에서 다른 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-115">To change the database, select a different database from the **Available Databases** list.</span></span>  
  
5.  <span data-ttu-id="815b7-116">[] 줄에 마이닝 모델의 이름을 입력 `FROM` *\<mining model, name, MyModel>* `.CONTENT` 합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-116">Enter the name of a mining model in the line, `FROM` [*\<mining model, name, MyModel>*]`.CONTENT`.</span></span> <span data-ttu-id="815b7-117">마이닝 모델 이름에 공백이 포함된 경우 이름을 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-117">If the mining model name contains spaces, you must enclose the name in brackets.</span></span>  
  
     <span data-ttu-id="815b7-118">이름을 입력하기가 불편하면 **개체 탐색기** 에서 마이닝 모델을 선택하고 템플릿에 끌어다 놓으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-118">If you don't want to type the name, you can select a mining model in **Object Explorer** and drag it into the template.</span></span>  
  
6.  <span data-ttu-id="815b7-119">줄에 `SELECT` *\<select list, expr list, \*>* 마이닝 모델 콘텐츠 스키마 행 집합의 열 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-119">In the line, `SELECT`*\<select list, expr list, \*>*, type the names of columns in the mining model content schema rowset.</span></span>  
  
     <span data-ttu-id="815b7-120">마이닝 모델 내용 쿼리에서 반환할 수 있는 열의 목록을 보려면 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)에서 제공하는 DMV를 사용해 쿼리를 작성하는 방식으로 데이터 마이닝 스키마 행 집합에 대한 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-120">To view a list of columns that you can return in mining model content queries, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
7.  <span data-ttu-id="815b7-121">필요에 따라 템플릿의 WHERE 절에 조건을 입력하여 특정 노드 또는 값으로 반환되는 행을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-121">Optionally, type a condition in the WHERE clause of the template to restrict the rows returned to specific nodes or values.</span></span>  
  
8.  <span data-ttu-id="815b7-122">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-122">Click **Execute**.</span></span>  
  
## <a name="querying-the-data-mining-schema-rowsets"></a><span data-ttu-id="815b7-123">데이터 마이닝 스키마 행 집합 쿼리</span><span class="sxs-lookup"><span data-stu-id="815b7-123">Querying the Data Mining Schema Rowsets</span></span>  
  
#### <a name="to-create-a-query-against-the-data-mining-schema-rowset"></a><span data-ttu-id="815b7-124">데이터 마이닝 스키마 행 집합에 대한 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="815b7-124">To create a query against the data mining schema rowset</span></span>  
  
1.  <span data-ttu-id="815b7-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **새 쿼리** 도구 모음에서 **Analysis Services DMX 쿼리**또는 **Analysis Services MDX 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **New Query** toolbar, click **Analysis Services DMX Query**, or **Analysis Services MDX query**.</span></span>  
  
2.  <span data-ttu-id="815b7-126">**Analysis Services에 연결** 대화 상자에서 쿼리할 개체가 포함된 인스턴스를 선택하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-126">In the **Connect to Analysis Services** dialog box, select the instance that contains the objects you want to query, and click **Connect**.</span></span>  
  
     <span data-ttu-id="815b7-127">적절한 코드 편집기에서 **내용 쿼리** 템플릿이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-127">The **Content Query** template opens in the appropriate code editor.</span></span> <span data-ttu-id="815b7-128">메타데이터 창에는 현재 데이터베이스에서 사용할 수 있는 개체의 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-128">The metadata pane lists the objects that are available in the current database.</span></span> <span data-ttu-id="815b7-129">데이터베이스를 변경하려면 **사용 가능한 데이터베이스** 목록에서 다른 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-129">To change the database, select a different database from the **Available Databases** list.</span></span>  
  
3.  <span data-ttu-id="815b7-130">쿼리 편집기에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-130">In the query editor, type the following:</span></span>  
  
     `SELECT *`  
  
     `FROM $system.DMSCHEMA_MINING_MODEL_CONTENT`  
  
     `WHERE MODEL_NAME = '<model name>'`  
  
4.  <span data-ttu-id="815b7-131">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-131">Click **Execute**.</span></span>  
  
     <span data-ttu-id="815b7-132">결과 창에 모델의 콘텐츠가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-132">The Results pane displays the contents of the model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="815b7-133">현재 인스턴스에서 쿼리할 수 있는 모든 스키마 행 집합의 목록을 보려면 `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="815b7-133">To view a list of all the schema rowsets that you can query on the current instance, use this query: `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS.</span></span> <span data-ttu-id="815b7-134">또는 데이터 마이닝과 관련된 스키마 행 집합의 목록은 [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="815b7-134">Or, for a list of schema rowsets specific to data mining, see [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815b7-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="815b7-135">See Also</span></span>  
 <span data-ttu-id="815b7-136">[마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="815b7-136">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="815b7-137">Data Mining Schema Rowsets</span><span class="sxs-lookup"><span data-stu-id="815b7-137">Data Mining Schema Rowsets</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
