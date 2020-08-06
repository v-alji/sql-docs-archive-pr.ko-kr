---
title: 데이터 원본 뷰에서 스키마 새로 고침 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services], schema updates
- refreshing data source views
- data source views [Analysis Services], refreshing
ms.assetid: 634b0504-1437-43e7-8ac7-3248ac7989a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 808f6ea431592aaecadf6f20a1ae16850cdb20e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647941"
---
# <a name="refresh-the-schema-in-a-data-source-view-analysis-services"></a><span data-ttu-id="ba4b4-102">데이터 원본 뷰에서 스키마 새로 고침(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="ba4b4-102">Refresh the Schema in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="ba4b4-103">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 프로젝트나 데이터베이스에 데이터 원본 뷰(DSV)를 정의한 후 기본 데이터 원본의 스키마가 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-103">After defining a data source view (DSV) in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] project or database, the schema in an underlying data source may change.</span></span> <span data-ttu-id="ba4b4-104">이러한 변경 내용은 배포 프로젝트에서 자동으로 감지되거나 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-104">These changes are not automatically detected or updated in a development project.</span></span> <span data-ttu-id="ba4b4-105">또한 프로젝트를 서버에 배포했을 경우 Analysis Services에서 더 이상 외부 데이터 원본에 연결할 수 없다는 처리 오류가 발생하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-105">Moreover, if you deployed the project to a server, you will now encounter processing errors if Analysis Services can no longer connect to the external data source.</span></span>

 <span data-ttu-id="ba4b4-106">외부 데이터 원본과 일치하도록 DSV를 업데이트하려면 BIDS(Business Intelligence Development Studio)에서 DSV를 새로 고치면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-106">To update the DSV so that it matches the external data source, you can refresh the DSV in Business Intelligence Development Studio (BIDS).</span></span> <span data-ttu-id="ba4b4-107">DSV를 새로 고치면 DSV가 기반으로 하는 외부 데이터 원본에 대한 변경 내용이 검색되어 외부 데이터 원본의 추가 및 삭제를 열거하는 변경 목록이 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-107">Refreshing the DSV detects changes to the external data sources upon which the DSV is based, and builds a change list that enumerates the additions or deletions in the external data source.</span></span> <span data-ttu-id="ba4b4-108">이 변경 내용 집합을 기본 데이터 원본과 맞게 다시 조정할 DSV에 적용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-108">You can then apply the set of changes to the DSV that will realign it to the underlying data source.</span></span> <span data-ttu-id="ba4b4-109">추가 작업 시 프로젝트에서 해당 DSV를 사용하는 큐브와 차원을 추가로 업데이트해야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-109">Note that additional work is often required to further update the cubes and dimensions in the project that use the DSV.</span></span>

 <span data-ttu-id="ba4b4-110">이 항목에는 다음 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-110">This topic includes the following sections:</span></span>

 [<span data-ttu-id="ba4b4-111">새로 고침에서 지원 변경</span><span class="sxs-lookup"><span data-stu-id="ba4b4-111">Changes Supported in Refresh</span></span>](#bkmk_changlist)

 [<span data-ttu-id="ba4b4-112">SQL Server Data Tools에서 DSV 새로 고침</span><span class="sxs-lookup"><span data-stu-id="ba4b4-112">Refresh a DSV in SQL Server Data Tools</span></span>](#bkmk_DSVrefresh)

##  <a name="changes-supported-in-refresh"></a><a name="bkmk_changlist"></a><span data-ttu-id="ba4b4-113">새로 고칠 때 지원 되는 변경 내용</span><span class="sxs-lookup"><span data-stu-id="ba4b4-113">Changes Supported in Refresh</span></span>
 <span data-ttu-id="ba4b4-114">DSV 새로 고침에는 다음과 같은 동작이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-114">DSV Refresh can include any of the following the actions:</span></span>

-   <span data-ttu-id="ba4b4-115">테이블, 열 및 관계 삭제</span><span class="sxs-lookup"><span data-stu-id="ba4b4-115">Deletion of tables, columns, and relationships</span></span>

-   <span data-ttu-id="ba4b4-116">DSV에 이미 포함된 테이블에 적용된 대로 열 및 관계 추가</span><span class="sxs-lookup"><span data-stu-id="ba4b4-116">Addition of columns and relationships, as applied to tables that are already included in the DSV</span></span>

-   <span data-ttu-id="ba4b4-117">UNIQUE 제약 조건 새로 추가.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-117">Addition of new unique constraints.</span></span> <span data-ttu-id="ba4b4-118">DSV의 테이블에 논리적 기본 키가 있는 경우 데이터 원본의 테이블에 물리적 키를 추가하면 논리적 키가 제거되고 물리적 키로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-118">If a logical primary key exists for a table in the DSV and a physical key is added to the table in the data source, the logical key is removed and replaced by the physical key.</span></span>

 <span data-ttu-id="ba4b4-119">새로 고침은 DSV에 새 테이블을 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-119">Refresh never adds new tables to a DSV.</span></span> <span data-ttu-id="ba4b4-120">새 테이블을 추가하려면 수동으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-120">If you want to add a new table, you must add it manually.</span></span> <span data-ttu-id="ba4b4-121">자세한 내용은 [데이터 원본 뷰에서 테이블이나 뷰 추가 또는 제거&#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)의 서버 탐색기에서 데이터 원본 뷰 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-121">For more information, see [Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md).</span></span>

##  <a name="refresh-a-dsv-in-sql-server-data-tools"></a><a name="bkmk_DSVrefresh"></a><span data-ttu-id="ba4b4-122">SQL Server Data Tools에서 DSV 새로 고침</span><span class="sxs-lookup"><span data-stu-id="ba4b4-122">Refresh a DSV in SQL Server Data Tools</span></span>
 <span data-ttu-id="ba4b4-123">DSV를 새로 고치려면 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 DSV를 두 번 클릭한 다음 데이터 원본 뷰 새로 고침 단추를 클릭하거나 데이터 원본 뷰 메뉴에서 **새로 고침** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-123">To refresh a DSV, double-click the DSV from Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then click the Refresh Data Source View button or choose **Refresh** from the Data Source View menu.</span></span>

 <span data-ttu-id="ba4b4-124">새로 고침 작업을 수행하는 동안 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 에서는 기본 관계형 데이터 원본을 모두 쿼리하여 DSV에 포함된 테이블/뷰에 변경 내용이 있었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-124">During refresh, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] queries all underlying relational data sources to determine whether there have been changes in tables/views which are included in the DSV.</span></span> <span data-ttu-id="ba4b4-125">모든 기본 데이터 원본에 연결할 수 있으며 변경 내용이 있는 경우 **데이터 원본 뷰 새로 고침** 대화 상자에 해당 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-125">If connections can be established to all underlying data sources and there have been any changes, you will see them in the **Refresh Data Source View** dialog box.</span></span>

 <span data-ttu-id="ba4b4-126">![데이터 원본 뷰 새로 고침 대화 상자](../media/ssas-olapdsv-refresh.gif "데이터 원본 뷰 새로 고침 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="ba4b4-126">![Refresh Data Source View dialog box](../media/ssas-olapdsv-refresh.gif "Refresh Data Source View dialog box")</span></span>

 <span data-ttu-id="ba4b4-127">이 대화 상자에는 DSV에서 삭제 또는 추가될 테이블, 열, 제약 조건 및 관계를 나열되며</span><span class="sxs-lookup"><span data-stu-id="ba4b4-127">The dialog box lists tables, columns, constraints, and relationships that will be deleted or added in the DSV.</span></span> <span data-ttu-id="ba4b4-128">성공적으로 준비할 수 없는 명명된 쿼리 또는 계산도 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-128">The report also lists any named query or calculation that cannot be successfully prepared.</span></span> <span data-ttu-id="ba4b4-129">영향을 받는 개체는 트리 뷰로 나열되며 테이블에 열 및 관계가 중첩되고 변경 유형(삭제 또는 추가)이 각 개체에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-129">The affected objects are listed in a tree view with columns and relationships nested under tables and the type of change (deletion or addition) indicated for each object.</span></span> <span data-ttu-id="ba4b4-130">영향을 받는 개체 유형은 표준 데이터 원본 뷰 개체 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-130">The standard data source view object icons indicate the type of object affected.</span></span>

 <span data-ttu-id="ba4b4-131">새로 고침은 전적으로 원본 개체의 이름을 기반으로 하기 때문에</span><span class="sxs-lookup"><span data-stu-id="ba4b4-131">Refresh is based completely on the names of the underlying objects.</span></span> <span data-ttu-id="ba4b4-132">따라서 데이터 원본에서 원본 개체의 이름을 바꾸면 데이터 원본 뷰 디자이너에서 이름이 바뀐 개체를 두 개의 별도 작업 (삭제 및 추가)으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-132">Therefore, if an underlying object is renamed in the data source, Data Source View Designer treats the renamed object as two separate operations-a deletion and an addition.</span></span> <span data-ttu-id="ba4b4-133">이러한 경우 이름을 바꾼 개체를 데이터 원본 뷰에 수동으로 다시 추가해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-133">In this case, you may have to manually add the renamed object back to the data source view.</span></span> <span data-ttu-id="ba4b4-134">관계 또는 논리적 기본 키를 다시 만들어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-134">You may also have to re-create relationships or logical primary keys.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ba4b4-135">데이터 원본에서 테이블 이름이 바꼈다는 사실을 인지한 경우 데이터 원본 뷰를 새로 고치기 전에 **테이블 바꾸기** 명령을 사용하여 테이블을 이름이 변경된 테이블로 바꾸는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-135">If you are aware that a table has been renamed in a data source, you may want to use the **Replace Table** command to replace the table with the renamed table before you refresh the data source view.</span></span> <span data-ttu-id="ba4b4-136">자세한 내용은 [데이터 원본 뷰의 테이블 또는 명명된 쿼리 바꾸기&#40;Analysis Services&#41;](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-136">For more information, see [Replace a Table or a Named Query in a Data Source View &#40;Analysis Services&#41;](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md).</span></span>

 <span data-ttu-id="ba4b4-137">보고서를 확인한 후 변경 내용을 적용하거나 업데이트를 취소하여 변경 내용을 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-137">After you examine the report, you can either accept the changes or cancel the update to reject any changes.</span></span> <span data-ttu-id="ba4b4-138">모든 변경 내용은 함께 수락하거나 거부해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-138">All changes must be accepted or rejected together.</span></span> <span data-ttu-id="ba4b4-139">목록에서 개별 항목을 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-139">You cannot choose individual items in the list.</span></span> <span data-ttu-id="ba4b4-140">변경 내용에 대한 보고서를 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba4b4-140">You can also save a report of the changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba4b4-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba4b4-141">See Also</span></span>
 [<span data-ttu-id="ba4b4-142">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="ba4b4-142">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)


