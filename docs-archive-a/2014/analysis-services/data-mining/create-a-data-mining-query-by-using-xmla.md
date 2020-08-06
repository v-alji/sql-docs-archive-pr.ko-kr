---
title: XMLA를 사용 하 여 데이터 마이닝 쿼리 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 8f6b6008-006c-4792-9bd1-64c30dc3fd41
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0e85b17db0781671fab0874706f12fdac95b30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660216"
---
# <a name="create-a-data-mining-query-by-using-xmla"></a><span data-ttu-id="132d3-102">XMLA를 사용하여 데이터 마이닝 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="132d3-102">Create a Data Mining Query by Using XMLA</span></span>
  <span data-ttu-id="132d3-103">AMO, DMX 또는 XML/A를 사용하여 데이터 마이닝 개체에 대한 다양한 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-103">You can create a variety of queries against data mining objects by using AMO, DMX, or XML/A.</span></span>  
  
 <span data-ttu-id="132d3-104">XML은 Analysis Services 서버와 모든 클라이언트 간의 통신에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-104">XML is used for communication between the Analysis Services server and all clients.</span></span> <span data-ttu-id="132d3-105">따라서 일반적으로 DMX를 사용하면 내용 쿼리를 보다 쉽게 만들 수 있지만 SOAP 프로토콜을 지원하는 클라이언트를 사용하거나 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 XML/A 쿼리를 만들어 XML/A의 DISCOVER 및 COMMAND 문을 통해 쿼리를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-105">Therefore, although it is generally much easier to create content queries by using DMX, you can write queries by using the DISCOVER and COMMAND statements in XML/A, either by using a client that supports the SOAP protocol, or by creating an XML/A query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="132d3-106">이 항목에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 사용할 수 있는 XML/A 템플릿을 사용하여 현재 서버에 저장된 마이닝 모델에 대한 모델 내용 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-106">This topic explains how to use the XML/A templates that are available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a model content query against a mining model stored on the current server.</span></span>  
  
## <a name="querying-data-mining-schema-rowsets-by-using-xmla"></a><span data-ttu-id="132d3-107">XML/A를 사용하여 데이터 마이닝 스키마 행 집합 쿼리</span><span class="sxs-lookup"><span data-stu-id="132d3-107">Querying Data Mining Schema Rowsets by Using XML/A</span></span>  
  
#### <a name="to-open-an-xmla-template"></a><span data-ttu-id="132d3-108">XML/A 템플릿을 열려면</span><span class="sxs-lookup"><span data-stu-id="132d3-108">To open an XML/A template</span></span>  
  
1.  <span data-ttu-id="132d3-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **템플릿 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="132d3-110">큐브 아이콘을 클릭하여 Analysis Services 템플릿 목록을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-110">Click the cube icon to open the list of Analysis Services templates.</span></span>  
  
3.  <span data-ttu-id="132d3-111">템플릿 범주 목록에서 **XMLA**, **스키마 행 집합**을 차례로 확장하고 **스키마 행 집합 검색** 을 두 번 클릭하여 해당 템플릿을 적절한 코드 편집기에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-111">In the list of template categories, expand **XMLA**, expand **Schema Rowsets**, and double-click **Discover Schema Rowsets** to open the template in the appropriate code editor.</span></span>  
  
4.  <span data-ttu-id="132d3-112">**Analysis Services에 연결** 대화 상자에서 연결 정보를 지정한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-112">In the **Connect to Analysis Services** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="132d3-113">**스키마 행 집합 검색** 템플릿으로 채워진 새 쿼리 편집기 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-113">A new query editor window opens, populated with the **Discover Schema Rowsets** template.</span></span>  
  
#### <a name="to-discover-column-names-from-the-mining-model-content-schema-rowset"></a><span data-ttu-id="132d3-114">MINING MODEL CONTENT 스키마 행 집합에서 열 이름을 검색하려면</span><span class="sxs-lookup"><span data-stu-id="132d3-114">To discover column names from the MINING MODEL CONTENT schema rowset</span></span>  
  
1.  <span data-ttu-id="132d3-115">**스키마 행 집합 검색** 템플릿이 열려 있는 상태에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-115">With the **Discover Schema Rowsets** template open, click **Execute**.</span></span>  
  
     <span data-ttu-id="132d3-116">현재 인스턴스에서 사용할 수 있는 모든 행 집합에 대한 행 집합 이름 및 행 집합 열이 포함된 스키마 행 집합 목록이 **결과** 창에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-116">A list of schema rowsets is returned in the **Results** pane that contains the rowset names and rowset columns for all rowsets available on the current instance.</span></span>  
  
2.  <span data-ttu-id="132d3-117">**쿼리** 창에서 뒤에 커서를 놓고 **\<Restriction List>** enter 키를 눌러 새 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-117">In the **Query** pane, place the cursor after **\<Restriction List>** and press ENTER to add a new line.</span></span>  
  
3.  <span data-ttu-id="132d3-118">빈 줄에 커서를 놓고 형식 \*\* \<SchemaName> DMSCHEMA_MINING_MODEL_CONTENT \</SchemaName> \*\*</span><span class="sxs-lookup"><span data-stu-id="132d3-118">Place the cursor on the blank line and type **\<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT\</SchemaName>**</span></span>  
  
     <span data-ttu-id="132d3-119">제한에 대한 전체 섹션은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-119">The complete section for restrictions should appear as follows:</span></span>  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  <span data-ttu-id="132d3-120">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-120">Click **Execute**.</span></span>  
  
     <span data-ttu-id="132d3-121">**결과** 창에 지정한 스키마 행 집합의 열 이름 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-121">The **Results** pane shows a list of column names for the specified schema rowset.</span></span>  
  
#### <a name="to-create-a-content-query-using-the-mining-model-content-schema-rowset"></a><span data-ttu-id="132d3-122">MINING MODEL CONTENT 스키마 행 집합을 사용하여 내용 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="132d3-122">To create a content query using the MINING MODEL CONTENT schema rowset</span></span>  
  
1.  <span data-ttu-id="132d3-123">**스키마 행 집합 검색** 템플릿에서 요청 유형 태그 내의 텍스트를 바꿔서 요청 유형을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-123">In the **Discover Schema Rowsets** template, change the request type by replacing the text inside the request type tags.</span></span>  
  
     <span data-ttu-id="132d3-124">다음 줄을</span><span class="sxs-lookup"><span data-stu-id="132d3-124">Replace this line:</span></span>  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     <span data-ttu-id="132d3-125">다음 줄로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-125">with the following line:</span></span>  
  
     <span data-ttu-id="132d3-126">**\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**</span><span class="sxs-lookup"><span data-stu-id="132d3-126">**\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**</span></span>  
  
2.  <span data-ttu-id="132d3-127">제한 목록에 새 조건을 추가하여 이름으로 마이닝 모델을 지정하도록 제한 목록을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-127">Change the restriction list to specify a mining model by name, by adding a new condition to the restriction lists.</span></span>  
  
3.  <span data-ttu-id="132d3-128">템플릿에서 `<Restriction List>` 뒤에 커서를 놓고 Enter 키를 눌러 새 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-128">In the template, place the cursor after `<Restriction List>` and press ENTER to add a new line.</span></span>  
  
4.  <span data-ttu-id="132d3-129">빈 줄에 커서를 놓고 **<MODEL_NAME>내 모델 이름</MODEL_NAME>** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-129">Place the cursor on the blank line and type **<MODEL_NAME>My model name</MODEL_NAME>**</span></span>  
  
     <span data-ttu-id="132d3-130">제한에 대한 전체 섹션은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-130">The complete section for restrictions should appear as follows:</span></span>  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  <span data-ttu-id="132d3-131">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-131">Click **Execute**.</span></span>  
  
     <span data-ttu-id="132d3-132">결과 창에 지정한 모델의 값과 함께 스키마 정의가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="132d3-132">The Results pane displays the schema definition, together with the values for the specified model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="132d3-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="132d3-133">See Also</span></span>  
 <span data-ttu-id="132d3-134">[마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="132d3-134">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="132d3-135">Data Mining Schema Rowsets</span><span class="sxs-lookup"><span data-stu-id="132d3-135">Data Mining Schema Rowsets</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
