---
title: DataSources 및 DataSets 컬렉션 참조(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f951a4aa-da55-4e43-8579-4a5d4480d11f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 560a42daf4d4580adde5b6100fe23f2c646fff08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659842"
---
# <a name="datasources-and-datasets-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="5ea75-102">DataSources 및 DataSets 컬렉션 참조(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="5ea75-102">DataSources and DataSets Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5ea75-103">`DataSources` 컬렉션은 보고서에 사용되는 모든 데이터 원본을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-103">The `DataSources` collection represents all the data sources used in a report.</span></span> <span data-ttu-id="5ea75-104">마찬가지로 `DataSets` 컬렉션은 보고서의 모든 데이터 원본에 대한 모든 데이터 세트을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-104">Similarly, the `DataSets` collection represents all the datasets for all the data sources in a report.</span></span> <span data-ttu-id="5ea75-105">**보고서 데이터** 창을 사용하여 참조하는 데이터 원본 아래에 구성된 보고서 데이터 세트를 계층적으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-105">Use the **Report Data** pane for a hierarchical view of report datasets organized under the data source they reference.</span></span> <span data-ttu-id="5ea75-106">이러한 컬렉션에 대한 참조를 추가할 경우 보고서를 미리 볼 때 값이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-106">If you include references to these collections, you will not see values when previewing your report.</span></span> <span data-ttu-id="5ea75-107">이러한 컬렉션은 보고서가 보고서 서버에 게시된 다음에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-107">These collections are only available after the report has been published to a report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="datasources"></a><span data-ttu-id="5ea75-108">DataSources</span><span class="sxs-lookup"><span data-stu-id="5ea75-108">DataSources</span></span>  
 <span data-ttu-id="5ea75-109">`DataSources` 컬렉션은 게시된 보고서 정의에 참조되는 데이터 원본을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-109">The `DataSources` collection represents the data sources referenced in a published report definition.</span></span> <span data-ttu-id="5ea75-110">이 정보를 보고서에 포함하도록 선택하여 보고서 데이터의 원본을 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-110">You may choose to include this information in your report to document the source of the report data.</span></span> <span data-ttu-id="5ea75-111">이 컬렉션은 **미리 보기** 모드에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-111">This collection is not available in **Preview** mode.</span></span> <span data-ttu-id="5ea75-112">다음 표에서는 `DataSources` 컬렉션 내의 변수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-112">The following table describes the variables within the `DataSources` collection.</span></span>  
  
|<span data-ttu-id="5ea75-113">**변수**</span><span class="sxs-lookup"><span data-stu-id="5ea75-113">**Variable**</span></span>|`Type`|<span data-ttu-id="5ea75-114">**설명**</span><span class="sxs-lookup"><span data-stu-id="5ea75-114">**Description**</span></span>|  
|------------------|--------------|---------------------|  
|`DataSourceReference`|`String`|<span data-ttu-id="5ea75-115">보고서 서버에 있는 데이터 원본 정의의 전체 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-115">The full path of the data source definition on the report server.</span></span> <span data-ttu-id="5ea75-116">예를 들어 보고서 기록의 일부로 보고서에 사용된 모든 데이터 원본 목록을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-116">For example, you might include a list of all the data sources a report used as part of a report history.</span></span> <span data-ttu-id="5ea75-117">다음 예에서는 AdventureWorks2012라는 데이터 원본의 전체 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-117">The following example shows the full path for the data source named AdventureWorks2012:</span></span><br /><br /> <span data-ttu-id="5ea75-118">`/DataSources/AdventureWorks2012`.</span><span class="sxs-lookup"><span data-stu-id="5ea75-118">`/DataSources/AdventureWorks2012`.</span></span>|  
|`Type`|`String`|<span data-ttu-id="5ea75-119">데이터 원본의 데이터 공급자 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-119">The type of data provider for the data source.</span></span> <span data-ttu-id="5ea75-120">예들 들어 `SQL`입니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-120">For example, `SQL`.</span></span>|  
  
## <a name="datasets"></a><span data-ttu-id="5ea75-121">DataSets</span><span class="sxs-lookup"><span data-stu-id="5ea75-121">DataSets</span></span>  
 <span data-ttu-id="5ea75-122">`DataSets` 컬렉션은 보고서 정의에 참조되는 데이터 세트을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-122">The `DataSets` collection represents the datasets referenced in a report definition.</span></span> <span data-ttu-id="5ea75-123">보고서에 입력란으로 쿼리를 포함하면 보고서에 정확히 어떤 데이터가 있는지 알고자 하는 사용자가 원본 명령 텍스트를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-123">You may choose to include the query in the report in a text box, so a user interested in exactly which data is in the report can see the original command text.</span></span> <span data-ttu-id="5ea75-124">이 컬렉션은 **미리 보기** 모드에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-124">This collection is not available in **Preview** mode.</span></span> <span data-ttu-id="5ea75-125">다음 표에서는 `DataSets` 컬렉션의 멤버를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-125">The following table describes the members of the `DataSets` collection.</span></span>  
  
|<span data-ttu-id="5ea75-126">**Member**</span><span class="sxs-lookup"><span data-stu-id="5ea75-126">**Member**</span></span>|`Type`|<span data-ttu-id="5ea75-127">**설명**</span><span class="sxs-lookup"><span data-stu-id="5ea75-127">**Description**</span></span>|  
|----------------|--------------|---------------------|  
|`CommandText`|`String`|<span data-ttu-id="5ea75-128">데이터베이스 데이터 원본의 경우 이 멤버는 데이터 원본에서 데이터를 검색하는 데 사용되는 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-128">For database data sources, this is the query used to retrieve data from the data source.</span></span> <span data-ttu-id="5ea75-129">쿼리가 식인 경우 이 멤버는 평가 식입니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-129">If the query is an expression, this is the evaluated expression.</span></span>|  
|`RewrittenCommandText`|`String`|<span data-ttu-id="5ea75-130">데이터 공급자의 확장 CommandText 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-130">The data provider's expanded CommandText value.</span></span> <span data-ttu-id="5ea75-131">일반적으로 이 값은 보고서 매개 변수에 매핑된 쿼리 매개 변수가 있는 보고서에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-131">This is typically used for reports with query parameters that are mapped to report parameters.</span></span> <span data-ttu-id="5ea75-132">데이터 공급자는 명령 텍스트 매개 변수 참조를 매핑된 보고서 매개 변수에 대해 선택된 상수 값으로 확장할 때 이 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-132">The data provider sets this property when expanding the command text parameter references into the constant values selected for the mapped report parameters.</span></span>|  
  
### <a name="using-query-expressions"></a><span data-ttu-id="5ea75-133">쿼리 식 사용</span><span class="sxs-lookup"><span data-stu-id="5ea75-133">Using Query Expressions</span></span>  
 <span data-ttu-id="5ea75-134">식을 사용하여 데이터 세트에 포함된 쿼리를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-134">You can use expressions to define the query that is contained in a dataset.</span></span> <span data-ttu-id="5ea75-135">이 기능을 사용하면 사용자의 입력, 다른 데이터 세트의 데이터 또는 다른 변수를 기반으로 쿼리가 변경되는 보고서를 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea75-135">You can use this feature to design reports in which the query changes based on input from the user, data in other datasets, or other variables.</span></span> <span data-ttu-id="5ea75-136">쿼리에 대한 자세한 내용은 [보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ea75-136">For more information about queries, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea75-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ea75-137">See Also</span></span>  
 <span data-ttu-id="5ea75-138">[식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5ea75-138">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5ea75-139">식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5ea75-139">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
