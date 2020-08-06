---
title: SQL Server Management Studio |에서 DMX 쿼리 만들기 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- templates [Analysis Services], queries
- SQL Server Management Studio [Analysis Services], DMX queries
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- prediction queries [DMX]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: 568ce40a-1f53-47eb-8c79-14347cdfde83
author: minewiskan
ms.author: owend
ms.openlocfilehash: d20fc7a618f4977058203d8f35d235b543609dd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652454"
---
# <a name="create-a-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="3a98b-102">SQL Server Management Studio에서 DMX 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="3a98b-102">Create a DMX Query in SQL Server Management Studio</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3a98b-103">에는 마이닝 모델 및 마이닝 구조에 대해 예측 쿼리, 내용 쿼리 및 데이터 정의 쿼리를 작성하는 데 유용한 기능 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-103">provides a set of features to help you create prediction queries, content queries, and data definition queries against mining models and mining structures.</span></span>  
  
-   <span data-ttu-id="3a98b-104">그래픽 예측 쿼리 작성기는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 및 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 예측 쿼리를 작성하고 데이터 집합을 모델에 매핑하는 프로세스를 간소화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-104">The graphical Prediction Query Builder is available in both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], to simplify the process of writing prediction queries and mapping data sets to a model.</span></span>  
  
-   <span data-ttu-id="3a98b-105">템플릿 탐색기에서 제공되는 쿼리 템플릿을 사용하면 다양한 유형의 예측 쿼리를 비롯하여 많은 종류의 DMX 쿼리를 빠르게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-105">The query templates provided in the Template Explorer jump-start the creation of many kinds of DMX queries, including many types of prediction queries.</span></span> <span data-ttu-id="3a98b-106">내용 쿼리, 중첩된 데이터 집합에 사용되는 쿼리, 마이닝 구조에서 사례를 반환하는 쿼리 및 데이터 정의 쿼리에 대한 템플릿이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-106">Templates are provided for content queries, queries used nested data sets, queries that return cases from the mining structure, and even data definition queries.</span></span>  
  
-   <span data-ttu-id="3a98b-107">MDX 및 DMX 쿼리 창의 메타데이터 탐색기는 쿼리 작성기에 끌어 놓을 수 있는 사용 가능한 모델 및 구조 목록과 DMX 함수 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-107">The Metadata Explorer in the MDX and DMX query panes provides a list of available models and structures that you can drag and drop into the query builder, as well as a list of DMX functions.</span></span> <span data-ttu-id="3a98b-108">이 기능을 사용하면 입력하지 않고도 개체 이름을 즉시 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-108">This feature makes it easy to get object names right, without typing.</span></span>  
  
 <span data-ttu-id="3a98b-109">이 항목에서는 메타데이터 탐색기 및 DMX 쿼리 편집기를 사용하여 DMX 쿼리를 작성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-109">This topic describes how to build a DMX query by using the Metadata Explorer and the DMX query editor.</span></span>  
  
##  <a name="dmx-query-templates"></a><a name="BKMK_Templates"></a><span data-ttu-id="3a98b-110">DMX 쿼리 템플릿</span><span class="sxs-lookup"><span data-stu-id="3a98b-110">DMX Query Templates</span></span>  
 <span data-ttu-id="3a98b-111">기본 DMX 쿼리를 만들기 위한 템플릿은 템플릿 탐색기에서 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-111">Templates for creating basic DMX queries are available in Template Explorer.</span></span> <span data-ttu-id="3a98b-112">**DMX** 폴더에는 다음 범주로 나누어진 데이터 마이닝 템플릿이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-112">The **DMX** folder contains data mining templates, which are divided into these categories:</span></span>  
  
-   <span data-ttu-id="3a98b-113">**모델 콘텐츠**</span><span class="sxs-lookup"><span data-stu-id="3a98b-113">**Model Content**</span></span>  
  
-   <span data-ttu-id="3a98b-114">**모델 관리**</span><span class="sxs-lookup"><span data-stu-id="3a98b-114">**Model Management**</span></span>  
  
-   <span data-ttu-id="3a98b-115">**예측 쿼리**</span><span class="sxs-lookup"><span data-stu-id="3a98b-115">**Prediction Queries**</span></span>  
  
-   <span data-ttu-id="3a98b-116">**구조 콘텐츠**</span><span class="sxs-lookup"><span data-stu-id="3a98b-116">**Structure Content**</span></span>  
  
 <span data-ttu-id="3a98b-117">자주 실행하는 쿼리나 명령에 대한 사용자 지정 템플릿을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-117">You can also create custom templates, for queries or commands that you run frequently.</span></span>  
  
## <a name="xmla-query-templates"></a><span data-ttu-id="3a98b-118">XMLA 쿼리 템플릿</span><span class="sxs-lookup"><span data-stu-id="3a98b-118">XMLA Query Templates</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="3a98b-119">에서는 XMLA 쿼리에 대한 템플릿도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-119">also provides templates for XMLA queries.</span></span>  
  
 <span data-ttu-id="3a98b-120">XMLA와 DMX를 사용하여 수행할 수 있는 쿼리 유형은 일부 중첩됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-120">There is some overlap between the types of queries that you can perform by using XMLA and DMX.</span></span> <span data-ttu-id="3a98b-121">예를 들어 DMX 또는 데이터 마이닝 스키마 행 집합을 사용하여 몇 가지 모델 내용 쿼리를 만들 수 있지만 스키마 행 집합에 DMX 내용 쿼리에 노출되지 않는 정보가 포함되어 있는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-121">For example, you can create some model content queries by using either DMX or the data mining schema rowsets, but the schema rowsets sometimes contain information that is not exposed in DMX content queries.</span></span>  
  
 <span data-ttu-id="3a98b-122">DMX와 XMLA의 작업 처리 방식에는 몇 가지 중요한 차이점도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-122">There are also some key differences in the way that operations are handled in DMX and in XMLA.</span></span> <span data-ttu-id="3a98b-123">예를 들어 XMLA를 사용하여 전체 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 백업과 같은 관리 작업을 수행할 수 있지만 단일 마이닝 모델을 백업하려면 DMX에서 제공하는 간단한 명령인 [EXPORT&#40;DMX&#41;](/sql/dmx/export-dmx)를 사용하는 것이 보다 적절합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-123">For example, you can use XMLA to perform administrative operations such as backup of an entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, but if you want to back up a single mining model, DMX provides a simple command, [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx), that is better suited to that purpose.</span></span>  
  
##  <a name="build-and-run-a-dmx-query"></a><a name="BKMK_Building_Queries"></a><span data-ttu-id="3a98b-124">DMX 쿼리 작성 및 실행</span><span class="sxs-lookup"><span data-stu-id="3a98b-124">Build and Run a DMX Query</span></span>  
  
#### <a name="open-a-new-dmx-query-window"></a><span data-ttu-id="3a98b-125">새 DMX 쿼리 창 열기</span><span class="sxs-lookup"><span data-stu-id="3a98b-125">Open a new DMX Query window</span></span>  
  
1.  <span data-ttu-id="3a98b-126">**에서** 새 쿼리 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 클릭한 다음 **새 Analysis Server DMX 쿼리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-126">Click **New Query** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then select **New Analysis Server DMX Query**.</span></span>  
  
2.  <span data-ttu-id="3a98b-127">**서버에 연결** 대화 상자가 나타나면 작업할 마이닝 모델이 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-127">When the **Connect to Server** dialog box appears, select the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining models you want to work with.</span></span>  
  
#### <a name="open-template-explorer"></a><span data-ttu-id="3a98b-128">템플릿 탐색기 열기</span><span class="sxs-lookup"><span data-stu-id="3a98b-128">Open Template Explorer</span></span>  
  
1.  <span data-ttu-id="3a98b-129">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **템플릿 탐색기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-129">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, select **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="3a98b-130">**에 적용되는 템플릿을 트리 뷰로 보려면** Analysis Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-130">Click **Analysis Server** to see a tree view of the templates that apply to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
#### <a name="apply-a-template-to-build-a-query"></a><span data-ttu-id="3a98b-131">쿼리를 작성할 템플릿을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-131">Apply a template to build a query</span></span>  
  
-   <span data-ttu-id="3a98b-132">적절한 쿼리 유형을 마우스 오른쪽 단추로 클릭하고 **열기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-132">Right-click the appropriate query type and select **Open**.</span></span>  
  
-   <span data-ttu-id="3a98b-133">또는 템플릿을 쿼리 편집기로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-133">Or, drag the template into the query editor.</span></span>  
  
-   <span data-ttu-id="3a98b-134">**쿼리**메뉴에서 **템플릿 매개 변수 값 지정** 옵션을 사용하여 쿼리 매개 변수를 채울 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a98b-134">You can also fill in the parameters for the query by using the option, **Specify Values for Parameters**, from the **Query** menu.</span></span>  
  
 <span data-ttu-id="3a98b-135">템플릿에서 특정 쿼리 유형을 만드는 방법에 대한 예는 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3a98b-135">For examples of how to create specific types of queries from templates, see the following topics:</span></span>  
  
 [<span data-ttu-id="3a98b-136">템플릿에서 단일 예측 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="3a98b-136">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
  
 [<span data-ttu-id="3a98b-137">마이닝 모델에 내용 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="3a98b-137">Create a Content Query on a Mining Model</span></span>](create-a-content-query-on-a-mining-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="3a98b-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a98b-138">See Also</span></span>  
 <span data-ttu-id="3a98b-139">[데이터 마이닝 쿼리 인터페이스](data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3a98b-139">[Data Mining Query Interfaces](data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="3a98b-140">DMX&#40;Data Mining Extensions&#41; 참조</span><span class="sxs-lookup"><span data-stu-id="3a98b-140">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
