---
title: 보고서 데이터 창
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: fc09c100cc8391bb1fd025b4bb5ac5f3b5e4379a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639323"
---
# <a name="report-data-pane-in-sql-server-reporting-services-ssrs"></a><span data-ttu-id="e2537-102">SSRS(SQL Server Reporting Services)의 보고서 데이터 창</span><span class="sxs-lookup"><span data-stu-id="e2537-102">Report Data pane in SQL Server Reporting Services (SSRS)</span></span>

  <span data-ttu-id="e2537-103">**보고서 데이터** 창을 사용하여 보고서의 현재 정의된 매개 변수, 데이터 원본, 데이터 세트, 필드 컬렉션 및 이미지를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-103">Use the **Report Data** pane to view the currently defined parameters, data sources, datasets, field collections, and images in your report.</span></span> <span data-ttu-id="e2537-104">보고서 데이터는 보고서의 데이터를 나타내는 항목의 계층 뷰를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-104">The Report Dane displays a hierarchical view of the items that represent data in your report.</span></span> <span data-ttu-id="e2537-105">최상위 노드는 기본 제공 필드, 매개 변수, 이미지 및 데이터 원본 참조를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-105">The top level nodes represent built-in fields, parameters, images, and data source references.</span></span> <span data-ttu-id="e2537-106">각 노드를 확장하여 데이터 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-106">Expand each node to view the data items.</span></span> <span data-ttu-id="e2537-107">예를 들어 데이터 원본 노드를 확장하면 해당 데이터 원본에 대해 정의된 데이터 세트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-107">For example, when you expand a data source node, the datasets defined for that data source appear.</span></span> <span data-ttu-id="e2537-108">데이터 세트를 확장하면 필드 컬렉션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-108">When you expand a dataset, its field collection appears.</span></span> <span data-ttu-id="e2537-109">데이터를 보고서 페이지의 보고서 항목에 연결하려면 항목을 끌어서 보고서 디자인 화면에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-109">Drag items to the report design surface to link data with report items on the report page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2537-110">옵션</span><span class="sxs-lookup"><span data-stu-id="e2537-110">Options</span></span>

 <span data-ttu-id="e2537-111">**기본 제공 필드**</span><span class="sxs-lookup"><span data-stu-id="e2537-111">**Built-in Fields**</span></span>  
 <span data-ttu-id="e2537-112">보고서 이름이나 페이지 번호와 같이 보고서에서 일반적으로 사용되는 Reporting Services에서 제공하는 필드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-112">Represents fields provided by Reporting Services that are commonly used in a report, such as the report name or page number.</span></span> <span data-ttu-id="e2537-113">자세한 내용은 [식의 기본 제공 컬렉션&#40;보고서 작성기 및 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2537-113">For more information, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
 <span data-ttu-id="e2537-114">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="e2537-114">**Parameters**</span></span>  
 <span data-ttu-id="e2537-115">각각 단일값 또는 다중값일 수 있는 보고서 매개 변수 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-115">Represents the collection of report parameters, each of which can be single-valued or multivalued.</span></span> <span data-ttu-id="e2537-116">자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-116">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
 <span data-ttu-id="e2537-117">**이미지**</span><span class="sxs-lookup"><span data-stu-id="e2537-117">**Images**</span></span>  
 <span data-ttu-id="e2537-118">보고서에 사용되는 이미지 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-118">Represents the set of images used in the report.</span></span> <span data-ttu-id="e2537-119">자세한 내용은 [이미지&#40;보고서 작성기 및 SSRS&#41;](../report-design/images-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2537-119">For more information, see [Images &#40;Report Builder and SSRS&#41;](../report-design/images-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e2537-120">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="e2537-120">**Data source**</span></span>  
 <span data-ttu-id="e2537-121">포함된 데이터 원본이나 공유 데이터 원본에 대한 단일 데이터 원본 참조를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-121">Represents a single data source reference to an embedded data source or to a shared data source.</span></span> <span data-ttu-id="e2537-122">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 공유 데이터 원본은 솔루션 탐색기의 공유 데이터 원본 폴더에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-122">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], shared data sources appear in Solution Explorer under the Shared Data Sources folder.</span></span> <span data-ttu-id="e2537-123">데이터 원본은 Reporting Services에서 지원하는 데이터 원본 유형 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-123">A data source specifies one of the data source types supported by Reporting Services.</span></span> <span data-ttu-id="e2537-124">데이터 원본은 데이터 세트 컬렉션이 기반을 두는 부모 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-124">A data source is the parent node for the collection of datasets based on it.</span></span> <span data-ttu-id="e2537-125">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2537-125">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) .</span></span>  
  
 <span data-ttu-id="e2537-126">**데이터 세트**</span><span class="sxs-lookup"><span data-stu-id="e2537-126">**Dataset**</span></span>  
 <span data-ttu-id="e2537-127">단일 데이터 세트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-127">Represents a single dataset.</span></span> <span data-ttu-id="e2537-128">데이터 세트는 쿼리에 의해 지정된 필드 컬렉션의 부모 노드이며 계산 필드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-128">A dataset is the parent node for the collection of fields specified by the query and including any calculated fields.</span></span> <span data-ttu-id="e2537-129">Reporting Services는 쿼리를 지정할 수 있도록 쿼리 디자이너를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e2537-129">Reporting Services supports query designers to help you specify a query.</span></span> <span data-ttu-id="e2537-130">자세한 내용은 [보고서에 데이터 추가 &#40;보고서 작성기 및 ssrs&#41;](report-datasets-ssrs.md) 및 [보고서 디자이너 SQL Server Data Tools &#40;Ssrs&#41;의 쿼리 디자인 도구 ](query-design-tools-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2537-130">For more information, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) and [Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e2537-131">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e2537-131">Next steps</span></span>

 - [<span data-ttu-id="e2537-132">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e2537-132">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)
 - [<span data-ttu-id="e2537-133">그룹화 창</span><span class="sxs-lookup"><span data-stu-id="e2537-133">Grouping Pane</span></span>](../tools/grouping-pane.md)